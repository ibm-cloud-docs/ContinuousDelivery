---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-15"

keywords: devops insights, publish, test, results, idra, code coverage, tests, verification, app, sonarqube, dashboard

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Publishing test results (deprecated)
{: #publish-test-idra}

You can publish test results by using idra (deprecated) to integrate your {{site.data.keyword.deliverypipeline}} with {{site.data.keyword.DRA_short}}. Test results inform {{site.data.keyword.DRA_full}} about the tests that are run during the build process. These tests must generate some kind of JSON or XML-based file. The generated test file is published as a test record. Along with the test file, this record contains the application name, build number, types of test, and other fields. The application name and build ID in the test record must match the ones that are used in the build record for a specific build. After you run a test in a pipeline, you can upload the results to {{site.data.keyword.DRA_short}}.
{: shortdesc}


## Before you begin
{: #prereq-test-idra}

Before you publish test results, you must publish your build record. For more information, see [publishing a build record by using idra (deprecated)](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-idra).


## Publishing test results
{: #test-idra}

Test results must provide data in one of these supported formats:

| Test Type                    | Supported Formats                                                        |
|------------------------------|--------------------------------------------------------------------------|
| Functional verification test | Mocha, xUnit, Karma/Mocha                                                |
| Unit test                    | Mocha, xUnit, Karma/Mocha                                                |
| Code coverage                | Cobertura, Istanbul (json-summary report format), lcov, JaCoCo           |
| SonarQube                    | Scan data that is provided by SonarQube scans                            |
| Static AppScan              | Static App Scans that are provided by IBM Application Security on Cloud  |
| Dynamic AppScan             | Dynamic App Scans that are provided by IBM Application Security on Cloud |
| Vulnerability Advisor        | Vulnerability Advisor results from IBM Vulnerability Advisor on Cloud    |
{: caption="Table 1. Test type and format" caption-side="top"}

The following example script uploads FVT test results to {{site.data.keyword.DRA_short}}:

```text
# Run tests and generate a test results file here.
# Add user api key to stage environment variable as a secured property
export LOGICAL_APP_NAME="SampleApp"
export BUILD_PREFIX="master"

# node 4.x or above is needed
export PATH=/opt/IBM/node-v4.2/bin:$PATH
npm install -g grunt-idra3

idra --publishtestresult --filelocation=fvttest.json --type=fvt
```
{: codeblock}

In the example script, the `idra` command with the `--publishtestresult` flag specifies that the script uploads results. The `--filelocation` flag indicates the location of the test results file relative to the root directory of the job. The `--type` flag indicates the type of test result.

The following example script runs tests and then uploads Mocha results and Istanbul code coverage results to {{site.data.keyword.DRA_short}}:

```text
# Add user api key to stage environment variable as a secured property
export LOGICAL_APP_NAME="SampleApp"
export BUILD_PREFIX="master"

# Run tests and generate a test results file here.
istanbul cover --report lcov --report json-summary _mocha -- -R xunit -O output=./test/results/mocha.xml 'test/**/*.js'

# node 4.x or above is needed
export PATH=/opt/IBM/node-v4.2/bin:$PATH
npm install -g grunt-idra3

idra --publishtestresult --filelocation=./test/results/mocha.xml --type=unittest
idra --publishtestresult --filelocation=./coverage/coverage-summary.json --type=code
```
{: codeblock}

The `idra` command supports the following `type` values:

| Type                  | Description                                                          |
|-----------------------|----------------------------------------------------------------------|
| `unittest`            | Unit test results                                                    |
| `fvt`                 | Functional verification test results                                 |
| `code`                | Code coverage results                                                |
| `sonarqube`           | SonarQube scan results                                               |
| `staticsecurityscan`  | Static security scan results from IBM Application Security on Cloud  |
| `dynamicsecurityscan` | Dynamic security scan results from IBM Application Security on Cloud |
| `vulnerabilityadvisor`| Vulnerability Advisor results from IBM Vulnerability Advisor on Cloud|
{: caption="Table 2. idra command types" caption-side="top"}

To learn more about the `idra` command, see [the grunt-idra3 package's page on npm](https://www.npmjs.com/package/grunt-idra3).


## Viewing test results
{: #view-test-idra}

When your pipeline runs, it publishes the test result data to {{site.data.keyword.DRA_short}}. To view the test result data in {{site.data.keyword.DRA_short}}, go to the Quality Dashboard page. For more information, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).


## Next steps
{: #next-test-idra}

Learn how to [evaluate gates](/docs/ContinuousDelivery?topic=ContinuousDelivery-evaluating-gates-idra) by using idra (deprecated).
