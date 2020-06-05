---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-04"

keywords: devops insights, devops, insights, ibmcloud cli, idra, migrating, test, tests, gate, gate failure, install, app

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

# Migrating from grunt-idra3 (deprecated) CLI to the {{site.data.keyword.Bluemix_notm}} CLI 
{: #migration-ibmcloud-cli}

The grunt-idra3 CLI for {{site.data.keyword.DRA_full}} is deprecated and is replaced by {{site.data.keyword.cloud_notm}} CLI. To migrate to {{site.data.keyword.cloud_notm}} CLI, replace your call to idra with a call to the {{site.data.keyword.cloud_notm}} CLI. 
{:shortdesc}

grunt-idra3 CLI needs a node.js environment, but the {{site.data.keyword.cloud_notm}} CLI runs in any environment. It requires fewer environment variables, and also provides better assistance when you use the `--help` option.


## Switching to {{site.data.keyword.Bluemix_notm}} CLI 
{: #switch-cli}

To use the {{site.data.keyword.cloud_notm}} CLI, you must install it. Use the `-f` option to force install the CLI. After you install the {{site.data.keyword.cloud_notm}} CLI, review the following details and differences: 

* The {{site.data.keyword.cloud_notm}} CLI requires the `TOOLCHAIN_ID` environment variable, but this variable isn't required if the CLI is used in {{site.data.keyword.deliverypipelinelong}}. 
* The {{site.data.keyword.cloud_notm}} CLI needs the `API_KEY` variable to log in to {{site.data.keyword.cloud_notm}}. 
* You can log in with the `--no-region` option. 
* The {{site.data.keyword.cloud_notm}} CLI requires `--logicalappname` and `--buildnumber` parameters in addition to the idra parameters.

For more information about installing {{site.data.keyword.cloud_notm}} CLI, see [Installing the stand-alone {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli#install-ibmcloud-cli). 

Here is an example of a grunt-idra3 CLI command invocation: 
```
#!/bin/bash
export TOOLCHAIN_ID="toolchainid"
export LOGICAL_APP_NAME="SampleApp"
export BUILD_NUMBER="master:1"
export IBM_CLOUD_API_KEY="apikey"

export PATH=/opt/IBM/node-v4.2/bin:$PATH
npm install -g grunt-idra3

idra --publishbuildrecord --branch=$GIT_BRANCH --repositoryurl=$GIT_URL --commitid=$GIT_COMMIT --status=pass
```
{:codeblock}

Here is the same command invocation for the {{site.data.keyword.cloud_notm}} CLI:

```
#!/bin/bash
export TOOLCHAIN_ID="toolchainid"
export API_KEY="apikey"

ibmcloud login --apikey $API_KEY --no-region

ibmcloud plugin install doi

ibmcloud doi publishbuildrecord --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --branch $GIT_BRANCH --repositoryurl $GIT_URL --commitid $GIT_COMMIT --status pass
```
{:codeblock}


## Comparing CLIs
{: #comparing-cli-migration}

The commands and the parameters that are passed to the commands are similar between the two CLIs. However, there are differences that you need to review. The following two tables outline the differences.

The following table shows the differences of the command name. 

| Command Name              | grunt-idra3 CLI          | {{site.data.keyword.cloud_notm}} CLI |
|---------------------------|--------------------------|----------------------------------------|
| Publish build record      | `publishbuildrecord`     | `publishbuildrecord`                   |
| Publish test results      | `publishtest` **result** | `publishtest` **record**               |
| Publish deployment record | `publishdeployrecord`    | `publishdeployrecord`                  |
| Evaluate gate             | `evaluategate`           | `evaluategate`                         |
{: caption="Table 1. Command name differences" caption-side="top"}

The following table shows the differences between the command parameters. 

| Command Parameter         | Difference | grunt-idra3 CLI | {{site.data.keyword.cloud_notm}} CLI | Comment                               |
|---------------------------|------------|-----------------|----------------------------------------|---------------------------------------|
| Publish build record      | No         |                 |                                        |                                       |
| Publish test results      | Yes        | `token`         | `sqtoken`                              | Parameter name change in {{site.data.keyword.cloud_notm}} CLI |
| Publish deployment record | Yes        | `deployableid`  |                                        | Option not available in {{site.data.keyword.cloud_notm}} CLI  |
| Evaluate gate             | Yes        | `type`          | `ruletype`                             | Parameter name change in {{site.data.keyword.cloud_notm}} CLI |
{: caption="Table 2. Command parameter differences" caption-side="top"}
