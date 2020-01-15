---

copyright:
  years: 2019
lastupdated: "2019-07-26"

keywords: devops insights, uploading data types, data types, test data format, test data, unit test, code coverage, test, tests, verification, app, sonarqube, dashboard

subcollection: DevOpsInsights

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# Publishing test data to {{site.data.keyword.DRA_short}}
{: #publishing-test-data}

Users can upload test results to {{site.data.keyword.DRA_full}} from any continuous integration and continuous delivery (CI/CD) tools and see all of those test results in the {{site.data.keyword.DRA_short}} Quality Dashboard page. A CI/CD tool refers to tools like Jenkins, Travis CI, and {{site.data.keyword.deliverypipelinelong}} that are used to create builds, run tests, and perform deployments.
{: shortdesc}

For more information about the Quality Dashboard page, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).


## Supported test data format in {{site.data.keyword.DRA_short}}
{: #supported-test-data}

The following table showed a list of supported tests and formats.

| Display Label                 | Data Type             | Supported Data Formats and File Extension                  |
|-------------------------------|-----------------------|------------------------------------------------------------|
| Unit Tests                    | Test Case             | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON) |
| Code Coverage                 | Code Coverage         | Cobertura (xml), lcov (info), Istanbul (JSON), JaCoCo (xml)|
| Functional Verification Tests | Test Case             | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON) |
| SonarQube                     | SonarQube             | SonarQube                                                  |
| Dynamic Security Scan         | Dynamic Security Scan | {{site.data.keyword.Bluemix}} Application Security (xml)   |
| Static Security Scan          | Static Security Scan  | {{site.data.keyword.Bluemix}} Application Security (xml)   |
| Vulnerability Advisor         | Vulnerability Advisor | Vulnerability Advisor (JSON)                               |
{: caption="Table 1. Default {{site.data.keyword.DRA_short}} data sets" caption-side="top"}


## Uploading test case results
{: #upload-test-case}

To upload unit tests, functional verification tests or custom test data, use the following command:

```
ibmcloud doi publishtestrecord --logicalappname "$MY_APP_NAME" --buildnumber "$MY_BUILD_NUMBER" --filelocation "./test-sample-folder/unit_test_mocha.json" --type=unittest
```
{:codeblock}

For a sample test result files that you can upload to DevOps Insights, see [this GitHub repository with dummy data](https://github.com/devops-insights/example-upload-data-format){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"). 


## Uploading Code Coverage Results
{: #upload-code-coverage}

To upload Code Coverage results or custom code data, use the following command:

```
ibmcloud doi publishtestrecord --logicalappname "$MY_APP_NAME" --buildnumber "$MY_BUILD_NUMBER" --filelocation "./test-sample-folder/code_coverage_cobertura.xml" --type=code
```
{:codeblock}

For a sample test result files that you can upload to DevOps Insights, see [this GitHub repository with dummy data](https://github.com/devops-insights/example-upload-data-format){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").


## Uploading IBM Application Scan reports
{: #upload-app-scan}

Users can get the report from the IBM AppScan CLI tool. Scan the application from the CLI to get the results in compressed file format.

```
appscan.sh get_result -i $job_id -d "$APPSCAN_SCAN_NAME.zip" -t zip
```
{:codeblock}

Unzip the results in a folder and go to that folder, then upload a file called Report-final.xml

```
ibmcloud doi publishtestrecord --logicalappname "$MY_APP_NAME" --buildnumber "$MY_BUILD_NUMBER" --filelocation "./Report-final.xml" --type staticsecurityscan
```
{:codeblock}

Change the type to `dynamicsecurityscan` if the report is from a dynamic scan.


## Uploading SonarQube results
{: #upload-sonarqube}

To upload data from SonarQube, you must provide the SonarQube server token by using `--token`. Your SonarQube server is required to be accessible from your CI/CD tool.

After you run a scan by using SonarQube, you can upload SonarQube results by running this command.

```
ibmcloud doi publishtestrecord --logicalappname "$MY_APP_NAME" --buildnumber "$MY_BUILD_NUMBER" --filelocation ".scannerwork/report-task.txt" --type=sonarqube --token=$SONARQUBE_TOKEN
```
{:codeblock}

report-task.txt is a file that is generated during the SonarQube scan.


## Uploading IBM Vulnerability Advisor results
{: #upload-vulnerability-advisor}

To get the result of the vulnerability advisor scan from the CLI, use the following command:

```
ibmcloud cr va ${PIPELINE_IMAGE_URL} -o json > vulnerability_advisor.json
```
{:codeblock}

You can get your image's repository and tag from the Vulnerability Advisor UI or in the CLI by using `ibmcloud cr image-list`. {{site.data.keyword.DRA_short}} accepts only the JSON output. You can upload Vulnerability Advisor output file to DevOps Insights by running this command.

```
ibmcloud doi publishtestrecord --logicalappname "${APP_NAME}" --buildnumber "${BUILD_NUMBER}" --filelocation "vulnerability_advisor.json" --type vulnerabilityadvisor
```
{:codeblock}