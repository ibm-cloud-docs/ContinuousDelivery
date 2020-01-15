---

copyright:
  years: 2019
lastupdated: "2019-11-13"

keywords: devops insights, publish, test, results, jenkins, code coverage, tests, verification, app, sonarqube, dashboard

subcollection: DevOpsInsights

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Publishing test results
{: #publish-test-jenkins}

You can publish test results by using Jenkins to integrate your projects with {{site.data.keyword.DRA_full}}. Test results inform {{site.data.keyword.DRA_short}} about the tests that are run during the build process. These tests must generate some kind of JSON or XML-based file. 
{:shortdesc}

The generated test file is published as a test record. Along with the test file, this record contains the application name, build number, types of test, and other fields. The application name and build ID in the test record must match the ones that are used in the build record for a specific build. After you run a test in a pipeline, you can upload the results to {{site.data.keyword.DRA_short}}.

## Before you begin
{: #prereq-test-jenkins}

Before you publish test results, you must publish a build record. For more information, see [publishing a build record by using Jenkins](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-jenkins).


## Publishing test results
{: #test-jenkins}

The following are types of tests that can be used and the formats that are supported. 

| Type                                                 | Formats                                                            | 
|------------------------------------------------------|--------------------------------------------------------------------|
| Unit Test                                            | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON)         | 
| Function Tests                                       | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON)         | 
| Code Coverage                                        | Cobertura (xml), lcov, Istanbul (JSON), JaCoCo (xml)               |
| Sonarqube                                            | Sonarqube                                                          |
| Static Security Scan                                 | {{site.data.keyword.IBM_notm}} Application Security on Cloud (xml) |
| Dynamic Security Scan                                | {{site.data.keyword.IBM_notm}} Application Security on Cloud (xml) |
| {{site.data.keyword.IBM_notm}} Vulnerability Advisor | {{site.data.keyword.IBM_notm}} Vulnerability Advisor (JSON)        |
| Custom Data Sets - Tests                             | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON)         |
| Custom Data Sets - Code Coverage                     | Cobertura (xml), lcov, Istanbul (JSON), JaCoCo (xml)               |
{: caption="Table 1. Supported tools and formats" caption-side="top"}

Publish build records with the publishTestResult step. This step requires two parameters. It can also accept one optional parameter.

| Parameter         | |Definition                                                                                                                     |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------|
| `type`            | The type of test result.                                                                                                        |
| `fileLocation`    | The test result file's location.                                                                                                |
| `environment`     | The environment is only required for the functional verification tests (fvt) on your test runs.                                 |
| `buildNumber`     | Optional: Set value to any string to represent the version number.                                                              |
| `applicationName` | Optional: Set the application name. If this value is set, the environment variable `IBM_CLOUD_DEVOPS_APP_NAME` is ignored. |
{: caption="Table 2. Publishing build records parameters and definitions" caption-side="top"}

The following are the commands that are used to view the test results for a specific test. 

| Test Result           | Test Type                     |
|-----------------------|-------------------------------|
| `unittest`            | Unit Tests                    |
| `fvt`                 | Functional Verification Tests |
| `code`                | Code Coverage Tests           |
| `staticsecurityscan`  | Static Security Scan Result   | 
| `dynamicsecurityscan` | Dynamic Security Scan         | 
{: caption="Table 3. Test result and test types" caption-side="top"}

The following example commands include the parameters. The first command publishes Mocha unit test results, and the second command publishes code coverage test results.
```
publishTestResults type:'unittest', fileLocation: './mochatest.json'
publishTestResults type:'code', fileLocation: './tests/coverage/reports/coverage-summary.json'
publishTestResults type:'fvt', fileLocation: './mochafvt.json', environment: 'STAGING'
publishTestResults type:'staticsecurityscan', fileLocation: './static-result.xml'
publishTestResults type:'dynamicsecurityscan', fileLocation: './dynamic-result.xml'
publishTestResults type:'vulnerabilityadvisor', fileLocation: './vulnerability-advisor.json'
```
{:codeblock}

For each command, you need to specify the toolchain ID to export the environment variable. For more information, see [Environment variables and definitions](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-jenkins). 
{: note} 


## Publishing SonarQube results (optional)
{: #publishing-sonarqube-results}

After you configure a SonarQube scanner and server by following the instructions in the [SonarQube documentation](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-jenkins/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"), you can publish scan results to {{site.data.keyword.DRA_short}}.

To configure your Jenkins pipeline to accept these results, add the following parameters to it:

| Parameter         | Definition                                                                                                                     |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------|
| `SQHostURL`       | The host portion of your SonarQube scanner's URL from your SonarQube server.                                    |
| `SQAuthToken`     | Your SonarQube API authentication token from your SonarQube server.                                                  |
| `SQProjectKey`    | The project key of the SonarQube project you want to scan.                                                                     |
| `buildNumber`     | Optional: The set value to any string that represents version number.                                                             |
| `applicationName` | Optional: Set the application name. If this value is set, the environment variable `IBM_CLOUD_DEVOPS_APP_NAME` is ignored. |
{: caption="Table 4. Test result and test types" caption-side="top"}

Here are the SonarQube parameters that are used in a sample stage:
```
stage ('SonarQube analysis') {
    steps {
        script {
            def scannerHome = tool 'Default SQ Scanner';
            withSonarQubeEnv('Default SQ Server') {

                env.SQ_Host)URL = SONAR_HOST_URL;
                env.SQ_AUTHENTICATION_TOKEN = SONAR_AUTH_TOKEN;
                env.SQ_PROJECT_KEY = "My Project Key";

                run SonarQube scan...
            }
        }
    }
}
stage ("SonarQube Quality Gate") {
    steps {
        ...
    }
    post {
        always {
            publishSQResults SQHostURL: "${SQ_HOST_URL}", SQAuthToken: "${SQ_AUTHENTICATION_TOKEN}", SQProjectKey:"${SQ_PROJECT_KEY}"
        }
    }
}
```
{:codeblock}


## Viewing test results
{: #view-test-jenkins}

When your pipeline runs, it publishes the test result data to {{site.data.keyword.DRA_short}}. To view the test result data, go to the Quality Dashboard page. For more information, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).


## Next steps
{: #next-test-jenkins}

[Evaluate gates](/docs/ContinuousDelivery?topic=ContinuousDelivery-evaluate-gates-jenkins) by using Jenkins.