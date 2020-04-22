---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-20"

keywords: devops insights, publish, test, results, cli, code coverage, tests, verification, app, sonarqube, dashboard

subcollection: ContinuousDelivery

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
{: #publish-test-cli}

Test results inform {{site.data.keyword.DRA_short}} about the tests that are run during the build process. These tests must generate a JSON or XML-based file. The generated test file is published as a test record. Along with the test file, this record contains the application name, build number, types of test, and other fields.
{:shortdesc}


## Before you begin
{: #prereq-test-cli}

[Publish a build record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cli).


## Uploading test results
{: #test-cli}

The application name and build ID in the test record must match the ones that are used in the build record for a specific build. The following example script uploads functional verification test (FVT) results to {{site.data.keyword.DRA_short}}:

```
# Run tests and generate a test results file here.

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Login to IBMCloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
ibmcloud login --apikey $API_KEY --no-region

ibmcloud doi publishtestrecord --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --filelocation fvttest.json --type fvt
```
{:codeblock}

In the example script, `publishtestrecord` specifies that the command uploads test records. The `--filelocation` flag indicates the location of the test results file relative to the root directory of the job. The `--type` flag indicates the type of test result.

The following example script runs tests and then uploads Mocha results and Istanbul code coverage results to {{site.data.keyword.DRA_short}}:

```
# Run tests and generate a test results file here.
istanbul cover --report lcov --report json-summary _mocha -- -R xunit -O output=./test/results/mocha.xml 'test/**/*.js'

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Login to IBMCloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
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
| `vulnerabilityadvisor`| Vulnerability Advisor results from IBM Vulnerability Advisor on Cloud|
{: caption="Table 1. Test record types" caption-side="top"}


Test records must provide data in one of the following supported formats:

| Test Type                    | Supported Formats                                                        |
|------------------------------|--------------------------------------------------------------------------|
| Unit test                    | Mocha, xUnit, Karma/Mocha                                                |
| Functional verification test | Mocha, xUnit, Karma/Mocha                                                |
| Code coverage                | Cobertura, Istanbul (json-summary report format), lcov, JaCoCo           |
| SonarQube                    | Scan data that is provided by SonarQube scans                            |
| Static AppScan              | Static App Scans that are provided by IBM Application Security on Cloud  |
| Dynamic AppScan             | Dynamic App Scans that are provided by IBM Application Security on Cloud |
| Vulnerability Advisor Results| Vulnerability Advisor results from IBM Vulnerability Advisor on Cloud    |
{: caption="Table 2. Supported formats" caption-side="top"}


## Viewing test results
{: #view-test-cli}

When your pipeline runs, it publishes the test result data to {{site.data.keyword.DRA_short}}. You can view the test result data on the Quality Dashboard page. 

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **Resource List**.
2. Select your toolchain.
3. Click the **{{site.data.keyword.DRA_short}}** tile.
4. Click **Quality Dashboard** in the navigation to open the page.

For more information about the Quality Dashboard page, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).

## Next steps
{: #next-test-cli}

[Evaluate gates](/docs/ContinuousDelivery?topic=ContinuousDelivery-evaluate-gates-cli).
