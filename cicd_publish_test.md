---

copyright:
  years: 2019
lastupdated: "2019-07-26"

keywords: devops insights, publish, test, results, other ci/cd tools, code coverage, tests, verification, app, sonarqube, dashboard

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

# Publishing test results
{: #publish-test-cicd}

You can publish test results by using other continuous integration and continuous delivery (CI/CD) tools with the {{site.data.keyword.Bluemix}} command line interface (CLI) to integrate with {{site.data.keyword.DRA_full}}. Test results inform {{site.data.keyword.DRA_short}} about the tests that are run during the build process. These tests must generate some kind of JSON or XML-based file.
{:shortdesc}

The generated test file is published as a test record. Along with the test file, this record contains the application name, build number, types of test, and other fields. The application name and build ID in the test record must match the ones that are used in the build record for a specific build. After you run a test in your CI/CD tool, you can upload the results to {{site.data.keyword.DRA_short}}


## Before you begin
{: #prereq-test-cicd}

Before you publish test results, you must publish a deployment record. For more information, see [Publishing a deployment record by using other CI/CD tools](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-deploy-cicd).


## Publishing test results
{: #test-cicd}

Use the `publishtestrecord` command to upload a test record. The following example script uploads functional verification test (FVT) results to {{site.data.keyword.DRA_short}}:

```
# Run tests and generate a test results file here.

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Log in to IBM Cloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
ibmcloud login --apikey $API_KEY --no-region

ibmcloud doi publishtestrecord --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --filelocation fvttest.json --type fvt
```
{:codeblock}

In the example script, the `publishtestrecord` command specifies that the command uploads test records. The `--filelocation` flag indicates the location of the test results file relative to the root directory of the job. The `--type` flag indicates the type of test result.

The following example script runs tests and then uploads Mocha results and Istanbul code coverage results to {{site.data.keyword.DRA_short}}:

```
# Run tests and generate a test results file here.
istanbul cover --report lcov --report json-summary _mocha -- -R xunit -O output=./test/results/mocha.xml 'test/**/*.js'

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Log in to IBM Cloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
ibmcloud login --apikey $API_KEY --no-region

#Publish test results.  Assumes that MY_APP_NAME and MY_BUILD_NUMBER environment variables are already set
ibmcloud doi publishtestrecord --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --filelocation /test/results/mocha.xml --type unittest
ibmcloud doi publishtestrecord --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --filelocation ./coverage/coverage-summary.json --type code
```
{:codeblock}

The command supports the following `type` values:

| Type                  | Description                                                          |
|-----------------------|----------------------------------------------------------------------|
| `unittest`            | Unit test results                                                    |
| `fvt`                 | Functional verification test results                                 |
| `code`                | Code coverage results                                                |
| `sonarqube`           | SonarQube scan results                                               |
| `staticsecurityscan`  | Static security scan results from IBM Application Security on Cloud  |
| `dynamicsecurityscan` | Dynamic security scan results from IBM Application Security on Cloud |
{: caption="Table 1. Test record types" caption-side="top"}


Test records must provide data in one of the following supported formats:

| Test Type                    | Supported Formats                                                        |
|------------------------------|--------------------------------------------------------------------------|
| Functional verification test | Mocha, xUnit, Karma/Mocha                                                |
| Unit test                    | Mocha, xUnit, Karma/Mocha                                                |
| Code coverage                | Cobertura, Istanbul (json-summary report format), lcov, JaCoCo           |
| Static AppScan              | Static App Scans that are provided by IBM Application Security on Cloud  |
| Dynamic AppScan             | Dynamic App Scans that are provided by IBM Application Security on Cloud |
| SonarQube                    | Scan data that is provided by SonarQube scans                            |
{: caption="Table 2. Supported formats" caption-side="top"}


## Viewing test results
{: #view-test-cicd}

When your CI/CD tool runs, it publishes the test result data to {{site.data.keyword.DRA_short}}. To view the test result data in {{site.data.keyword.DRA_short}}, go to the Quality Dashboard page. For more information, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).


## Next steps
{: #next-test-cicd}

[Evaluate gates](/docs/ContinuousDelivery?topic=ContinuousDelivery-evaluate-gates-cicd) by using other CI/CD tools.