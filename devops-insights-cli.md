---

copyright:
  years: 2019, 2024
lastupdated: "2022-11-17"

keywords: doi, devops insights, cli, plug-in

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.DRA_short}} CLI
{: #CLI_devops-insights}

The {{site.data.keyword.DRA_full}} CLI provides a set of commands that you can use to integrate your build with {{site.data.keyword.DRA_short}}. Use two different types of commands: CLI usage commands and CLI commands to integrate with {{site.data.keyword.DRA_short}}.
{: shortdesc}


## Before you begin
{: #prerequisites}

* Install the {{site.data.keyword.cloud_notm}} CLI. See [Download {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started) for instructions.

* Add the {{site.data.keyword.cloud_notm}} CLI plug-in. Run the following command:

```text
ibmcloud plugin install doi
```
{: codeblock}

* Make sure that you can access a toolchain with the {{site.data.keyword.DRA_short}} tool that is configured for that toolchain. For more information about toolchains, see [Creating a toolchain from an app](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=ui#creating_a_toolchain_from_an_app).

* Specify the toolchain ID by using one of the following methods:
   - Specify the toolchain ID as a CLI parameter to the command.
   - Set the `TOOLCHAIN_ID` environment variable.
   - Your {{site.data.keyword.contdelivery_full}} pipeline might automatically set the `PIPELINE_TOOLCHAIN_ID` environment variable.

   The CLI needs the value of the toolchain ID. The value of the toolchain ID that is specified in the CLI parameter overrides the value of the environment variable.

   The toolchain ID is found in the toolchain URL that is shown in the browser. If you're using {{site.data.keyword.deliverypipelinelong}}, you can set the toolchain ID to send your build data to a different toolchain. For more information, see [Aggregating data from multiple sources into a single toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources).


## Login
{: #login}

Use this command to log in to {{site.data.keyword.cloud_notm}}. The API_KEY must have access to the toolchain.

```text
ibmcloud login --apikey API_KEY
```
{: codeblock}

## Log in to the CLI with a private endpoint
{: #login-cli-private-endpoint}

For enhanced control and security over your data when using CLI, you have the option of using private routes to {{site.data.keyword.cloud_notm}} endpoints. You must first enable virtual routing and forwarding in your account, and then you can enable the use of {{site.data.keyword.cloud_notm}} private service endpoints. For more information about setting up your account to support the private connectivity option, see [Enabling VRF and service endpoints](https://cloud.ibm.com/docs/account?topic=account-vrf-service-endpoint&interface=ui).

Use the following command to log in to a private endpoint by using the CLI. The API_KEY must have access to the toolchain.

```text
ibmcloud login -a private.cloud.ibm.com --apikey API_KEY
```
{: codeblock}


## CLI usage commands
{: #CLI-usage-commands}

### {{site.data.keyword.DRA_short}} help
{: #ibmcloud-help}

 The following command displays the list of {{site.data.keyword.DRA_short}} commands:

```text
 ibmcloud doi --help
```
{: codeblock}

### {{site.data.keyword.DRA_short}} command help
{: #ibmcloud-command-help}

The following command displays the details of the flags that are required for a command:

```text
 ibmcloud doi <command> --help
```
{: codeblock}

You can pass a `--region` parameter to any of the commands. By setting the value of this parameter to the `ibmcloud` region of the toolchain, the CLI does not need to determine which region the toolchain is in, making it more efficient and reliable. This parameter is optional for compatibility with earlier versions.
{: tip}

## Commands to integrate with {{site.data.keyword.DRA_short}}
{: #commands-integrate-insights}

When you use the CLI for a build, you must publish a [build record](#publishbuildrecord).

The value of the `logicalappname` and `buildnumber` parameters that are passed to the CLI must remain the same across all command invocations.

### Publishing a build record
{: #publishbuildrecord}

The following command publishes a build record to {{site.data.keyword.DRA_short}}:

```bash
 ibmcloud doi buildrecord-publish --branch BRANCH --repositoryurl REPOSITORYURL --commitid COMMITID --status STATUS --logicalappname LOGICALAPPNAME --buildnumber BUILDNUMBER --toolchainid TOOLCHAINID [--joburl JOBURL] [--region REGION]
```
{: codeblock}

The following are the command options for publishing a build record.

| Command Options                       | Required or Optional | Description                                                                                                             |
|---------------------------------------|----------------------|-------------------------------------------------------------------------------------------------------------------------|
| `-B`, `--branch`        | Required             | The repository branch that the build is being performed.                                                                |
| `-R`, `--repositoryurl` | Required             | The URL of the Git repository.                                                                                          |
| `-C`, `--commitid`      | Required             | The Git commit ID.                                                                                                      |
| `-S`, `--status`        | Required             | The build status. Acceptable values: `pass` and `fail`.                                                                 |
| `-L`, `--logicalappname`| Required             | Name of the application.                                                                                                |
| `-N`, `--buildnumber`   | Required             | Any string that identifies the build.                                                                                   |
| `-I`, `--toolchainid`   | Required             | If the TOOLCHAIN_ID environment variable is set, this flag is optional. If both the environment variable and the flag are provided, the value of the flag overrides the value of the environment variable. |
| `-J`, `--joburl`        | Optional             | The URL to the job's build logs that is automatically set by the CLI in the {{site.data.keyword.deliverypipelinelong}}. |
| `--region`              | Required             | The `ibmcloud` region of the toolchain. This value is required when using private endpoints. It is optional but good to have in case of public endpoints. |
{: caption="Command options for publishing a build record" caption-side="top"}

#### Example
{: #example1}

```bash
ibmcloud doi buildrecord-publish  -B master -R "https://github.com/oic/dlms.git" -C dff7884b9168168d91cb9e5aec78e93db0fa80d9 -S pass -L testapp -N master:199 -I b531487c-9c22-4f3b-9d20-5be408d57891 --region eu-gb
or
ibmcloud doi buildrecord-publish  --branch master --repositoryurl "https://github.com/oic/dlms.git" --commitid dff7884b9168168d91cb9e5aec78e93db0fa80d9 --status pass --logicalappname testapp --buildnumber master:199 --toolchainid b531487c-9c22-4f3b-9d20-5be408d57891
```
{: codeblock}

### Publishing a test record
{: #publishtestrecord}

 The following command publishes a test record to {{site.data.keyword.DRA_short}}:

```bash
 ibmcloud doi testrecord-publish --filelocation FILELOCATION --type TYPE --logicalappname LOGICALAPPNAME --buildnumber BUILDNUMBER --toolchainid TOOLCHAINID [--drilldownurl DRILLDOWNURL] [--env ENV] [--sqtoken SONARQUBE_TOKEN] [--tags TAGS] [--region REGION]
```
{: codeblock}

The following are the command options for publishing test records.

| Command Options                       | Required or Optional | Description                                                                                                                                     |
|---------------------------------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `-F`, `--filelocation`  | Required             | Location of the results you want to upload. It can be a single file, entire directory, or several files that match a wildcard expression.       |
| `-T`, `--type`          | Required             | The type of test results that you want to upload.                                                                                               |
| `-L`, `--logicalappname`| Required             | Name of the application.                                                                                                                        |
| `-N`, `--buildnumber`   | Required             | Any string that identifies the build.                                                                                                           |
| `-I`, `--toolchainid`   | Required             | If the TOOLCHAIN_ID environment variable is set, this flag is optional. If both the environment variable and the flag are provided, the value of the flag overrides the value of the environment variable. |
| `-U`, `--drilldownurl`  | Optional             | A URL where more information about the test results can be found. If this URL is invalid, the option is ignored.                                |
| `-E`, `--env`           | Optional             | The environment name to associate with the test results. This option is ignored for unit tests, code coverage tests, and static security scans. |
| `-K`, `--sqtoken`       | Optional             | This command is a SonarQube token. Valid only if the type specified is SonarQube. Used to pull more information from the SonarQube server.      |
| `--tags`                | Optional             | Specify a comma-separated list of tags to associate with this test result.      |
| `--region`              | Required             | The `ibmcloud` region of the toolchain. This value is required when using private endpoints. It is optional but good to have in case of public endpoints.|
{: caption="Command options for publishing a build record" caption-side="top"}

#### Example
{: #example2}

```bash
ibmcloud doi testrecord-publish -F "tests/fvt/*.json" -T fvt -L testapp -N master:199 -I b531487c-9c22-4f3b-9d20-5be408d57891 --tags "CC,app1"
or
ibmcloud doi testrecord-publish --filelocation "tests/fvt/*.json" --type fvt --logicalappname testapp --buildnumber master:199 --toolchainid b531487c-9c22-4f3b-9d20-5be408d57891 --region ca-tor
```
{: codeblock}

The following test types are supported:

| Type                   | Description                                                           |
|------------------------|-----------------------------------------------------------------------|
| `unittest`             | Unit test results                                                     |
| `fvt`                  | Functional verification test (FVT) results                            |
| `code`                 | Code coverage results                                                 |
| `sonarqube`            | SonarQube scan results                                                |
| `vulnerabilityadvisor` | Vulnerability Advisor results from IBM Vulnerability Advisor on Cloud |
| `cratf` | Terraform report generated by Code Risk Analyzer |
| `crabom` | Bill of Materials (BOM) report generated by Code Risk Analyzer |
| `cradeploy` | Deployment report generated by Code Risk Analyzer |
| `cracve` | Vulnerability report generated by Code Risk Analyzer |
| `zapscan` | OWASP Zed Attack Proxy (ZAP) scan reports |
{: caption="Test record types" caption-side="top"}

IBM Application Security on Cloud 1.0.0 is no longer published (`staticsecurityscan` and `dynamicsecurityscan` test types). All IBM Application Security on Cloud 1.0.0 support is provided by HCL. For more information, see the [HCL AppScan documentation](https://help.hcl-software.com/appscan/Welcome.html){: external}.
{: note}

### Publishing a deployment record
{: #publishdeployrecord}

 The following command publishes a deployment record to {{site.data.keyword.DRA_short}}:

```bash
 ibmcloud doi deployrecord-publish --env ENV --status STATUS --logicalappname LOGICALAPPNAME --buildnumber BUILDNUMBER --toolchainid TOOLCHAINID [--joburl JOBURL] [--appurl APPURL] [--region REGION]
```
{: codeblock}

| Command Options                       | Required or Optional | Description                                                                                                     |
|---------------------------------------|----------------------|-----------------------------------------------------------------------------------------------------------------|
| `-E`, `--env`           | Required             | The environment where the pipeline job deployed the app.                                                        |
| `-S`, `--status`        | Required             | The deployment status. This value must be either pass or fail.                                                  |
| `-L`, `--logicalappname`| Required             | Name of the application.                                                                                        |
| `-N`, `--buildnumber`   | Required             | Any string that identifies the build.                                                                           |
| `-I`, `--toolchainid`   | Required             | If the TOOLCHAIN_ID environment variable is set, this flag is optional. If both the environment variable and the flag are provided, the value of the flag overrides the value of the environment variable. |
| `-A`, `--appurl`        | Optional             | The URL where the deployed app is running.                                                                      |
| `-J`, `--joburl`        | Optional             | The URL to the job's build logs automatically set by the CLI in the {{site.data.keyword.deliverypipelinelong}}. |
| `--region`              | Required            | The `ibmcloud` region of the toolchain. This value is required when using private endpoints. It is optional but good to have in case of public endpoints.|
{: caption="Command options for publishing a deployment record" caption-side="top"}

#### Example
{: #example3}

```bash
ibmcloud doi deployrecord-publish -E "staging" -S pass -L testapp -N master:199 -I b531487c-9c22-4f3b-9d20-5be408d57891 --region au-syd
or
ibmcloud doi deployrecord-publish --env "staging" --status pass --logicalappname testapp --buildnumber master:199 --toolchainid b531487c-9c22-4f3b-9d20-5be408d57891
```
{: codeblock}

### Evaluating gates
{: #evaluategate}

 The following command evaluates a {{site.data.keyword.DRA_short}} gate:

```bash
 ibmcloud doi gate-evaluate --policy POLICY --logicalappname LOGICALAPPNAME --buildnumber BUILDNUMBER --toolchainid TOOLCHAINID [--forcedecision] [--ruletype RULETYPE] [--region REGION]
```
{: codeblock}

The following are command options for evaluating gates:

| Command Options                       | Required or Optional | Description                                                                                                                                  |
|---------------------------------------|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| `-P`, `--policy`        | Required             | The name of the policy that the gate uses to make its decision.                                                                              |
| `-L`, `--logicalappname`| Required             | Name of the application.                                                                                                                     |
| `-N`, `--buildnumber`   | Required             | Any string that identifies the build.                                                                                                        |
| `-I`, `--toolchainid`   | Required             | If the TOOLCHAIN_ID environment variable is set, this flag is optional. If both the environment variable and the flag are provided, the value of the flag overrides the value of the environment variable. |
| `-D`, `--forcedecision` | Optional             | Set the value to true to exit with an error code if the policy evaluation fails. The value defaults to false if this option isn't specified. |
| `-E`, `--ruletype`      | Optional             | A rule type to consider. If you include this option, only rules of this type are considered in the decision-making process.                  |
| `--region`              | Required             | The `ibmcloud` region of the toolchain. This value is required when using private endpoints. It is optional but good to have in case of public endpoints. |
{: caption="Command options for evaluating gates" caption-side="top"}

#### Example
{: #example4}

```bash
ibmcloud doi gate-evaluate -P "policyname" -D true -L testapp -N master:199 -I b531487c-9c22-4f3b-9d20-5be408d57891 --region br-sao
or
ibmcloud doi gate-evaluate --policy "policyname" --forcedecision true --logicalappname testapp --buildnumber master:199 --toolchainid b531487c-9c22-4f3b-9d20-5be408d57891
```
{: codeblock}

### Updating custom data sets and policies
{: #updatepolicies}

 The following command creates and updates custom data sets and policies for a toolchain:

```bash
 ibmcloud doi policies-update --file FILELOCATION --toolchainid TOOLCHAINID [--dryrun] [--region REGION]
```
{: codeblock}

The following are command options for updating custom data sets and policies:

| Command Options                       | Required or Optional | Description                                                                                                                                  |
|---------------------------------------|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| `-F`, `--file`          | Required             | The location of the JSON file that contains the list of custom data sets and policies to add or update. Both absolute and relative paths are accepted. |
| `-I`, `--toolchainid`   | Required             | If the TOOLCHAIN_ID environment variable is set, this flag is optional. If both the environment variable and the flag are provided, the value of the flag overrides the value of the environment variable. |
| `-D`, `--dryrun`        | Optional             | The option to simulate only the changes, with no updates. |
| `--region`              | Required             | The `ibmcloud` region of the toolchain. This value is required when using private endpoints. It is optional but good to have in case of public endpoints. |
{: caption="Command options for updating custom data sets and policies" caption-side="top"}

#### Example
{: #example5}

```bash
ibmcloud doi policies-update -F "policies/policy.json" -I b531487c-9c22-4f3b-9d20-5be408d57891 --region jp-tok
or
ibmcloud doi policies-update --file "policies/policy.json" --toolchainid b531487c-9c22-4f3b-9d20-5be408d57891
```
{: codeblock}

#### JSON file structure for the `updatepolicies` command
{: #json-updatepolicies}

A valid JSON file structure contains two fields:

```bash
{
      "custom_datasets": [],
      "policies": []
}
```
{: codeblock}

* You can specify any number of policies (and custom datasets) for the array.
* If the specified policy (and custom data set) exists for a toolchain, the policy is updated or created.
* Either the `custom_datasets` or `policies` array can be empty, or both can be empty.
* The only valid values for a `type_of_test` custom data set are `test` and `code`.
* If a custom data set exists for a toolchain, it can be used in the policy rules that are defined within the JSON file. You are not always required to define the custom data set within the JSON file.
* The sample JSON file that is provided for the `policies-update` command lists all of the possible rule types that you can specify in a policy. All of the fields in those rules are required.
* Use only one rule per data set.
* The name field within a rule is optional.

#### Sample JSON file for the `policies-update` command
{: #sample-policies-update}

This sample JSON file contains two custom datasets and two policies. The first policy `name: "Orders"` contains all of the rule types that you can use within a policy.

```bash
{
  "custom_datasets": [
 .  {
      "lifecycle_stage": "integrationtest",
      "type_of_test": "test",
      "label": "Integration Test"
    },
    {
      "lifecycle_stage": "covtest",
      "type_of_test": "code",
      "label": "Coverage Test"
    }
  ],
  "policies": [
    {
      "name": "Orders",
      "description": "Composite Policy.",
      "rules": [
        {
          "name": "rule1",
 .        "description": "Unit Test Rule with regression",
          "stage": "unittest",
          "percentPass": 100,
          "criticalTests": [
            "Get Weather with incomplete zip code"
          ],
          "regressionCheck": true
        },
        {
          "name": "rule2",
          "description": "Unit Test Rule without regression",
          "stage": "integrationtest",
          "percentPass": 98,
          "criticalTests": [
            "'Get Weather with incomplete zip code'"
          ],
        },
        {
          "name": "rule3",
          "description": "Functional test Rule",
          "stage": "fvt",
          "percentPass": 98,
          "criticalTests": [
            "'Get Weather with incomplete zip code'"
          ],
        },
        {
          "name": "rule4",
          "description": "Code Coverage rule",
          "stage": "code",
          "codeCoverage": 98,
        },
        {
          "name": "rule5",
          "description": "Custom dataset rule",
          "stage": "covtest",
          "codeCoverage": 60,
        },
        {
          "name": "rule6",
          "description": "Static Security Scan rule",
          "stage": "staticsecurityscan",
          "highSeverity": 40,
          "mediumSeverity": 5,
          "lowSeverity": 9
        },
        {
          "name": "rule7",
         "description": "Dynamic Security Scan rule",
          "stage": "dynamicsecurityscan",
          "highSeverity": 40,
          "mediumSeverity": 5,
          "lowSeverity": 9
        },
        {
          "name": "rule8",
          "description": "Sonarqube rule",
          "stage": "sonarqube"
        },
        {
          "name": "rule9",
          "description": "Vulnerability rule",
          "stage": "vulnerabilityadvisor"
        }
      ]
    },
    {
      "name": "UI",
      "description": "Policy to check Unit Test.",
      "rules": [
        {
          "name": "Unit Test Rule",
          "description": "Unit Test Rule",
          "stage": "integrationtest",
          "percentPass": 100,
          "criticalTests": []
        }
      ]
    }
  ]
}
```
{: codeblock}

## FAQs
{: #faq}

Get answers to frequently asked questions about using the {{site.data.keyword.DRA_short}} CLI.

### Why does the CLI fail with the "You do not have access to the toolchain" message?
{: #faq-no-toolchain-access}

The `API_KEY` environment variable that is used to log in to {{site.data.keyword.cloud_notm}} must be able to access the toolchain. Also, verify that you added the {{site.data.keyword.DRA_short}} tool integration to your toolchain.

### The CLI successfully ran, why doesn't the data show up on the dashboard?
{: #faq-no-data-dashboard}

Make sure that the value of the `logicalappname` and `buildnumber` parameters that are passed to the CLI are the same across all of the stages for the build. Also, verify that a build record is uploaded for the build. The data for test records that are uploaded for a specific build does not appear on the dashboard without a build record.

### The CLI times out communicating with the Sonarqube server, is there a way to increase the timeout period
{: #faq-cli-timeout-period}
The default timeout period is 60 seconds.
Before you call the {{site.data.keyword.DRA_short}} CLI, set the `IBMCLOUD_HTTP_TIMEOUT` environment variable. Its value is number of seconds.
```bash
    export IBMCLOUD_HTTP_TIMEOUT=120
```
{: codeblock}

### How can I determine why the CLI failed?
{: #faq-cli-debug}

Before you call the {{site.data.keyword.DRA_short}} CLI, set the `IBMCLOUD_TRACE` environment variable to true to turn on the debug log.

```bash
    export IBMCLOUD_TRACE=true
```
{: codeblock}

Observe the API calls and the responses that are shown in the log to determine the exact reason for failure.
