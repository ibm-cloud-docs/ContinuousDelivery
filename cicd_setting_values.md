---

copyright:
  years: 2019, 2021
lastupdated: "2021-01-25"

keywords: devops insights, setting, values, cli, parameter values, consistent, other ci/cd tools, test, tests, install, app, risk

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Setting consistent parameter values
{: #setting-values-cicd}

You can set consistent parameter values by using other continuous integration and continuous delivery (CI/CD) tools to integrate with {{site.data.keyword.DRA_full}}. To publish build records, test records, deployment records, and to evaluate gate policies within the same pipeline, you must use the same app name and build number for each stage. You need to pass parameter values `logicalappname` and `buildnumber`, and export your toolchain ID to use consistently with {{site.data.keyword.DRA_short}}. To use consistent identifiers, set your properties as environment properties.
{: shortdesc}

{{site.data.keyword.DRA_short}} tracks deployment risk based on published test data. When you integrate {{site.data.keyword.DRA_short}} with your continuous integration and continuous delivery (CI/CD) tool, you're instrumenting {{site.data.keyword.DRA_short}} to gather information to provide you with important data for visibility of quality.


## Before you begin
{: #prereq-values-cicd}

Configure your CI/CD tool to build, test, and deploy. You must complete this step before you continue with the integration.

You need an API key for access to the toolchain, and to log in by using the `ibmcloud` commandline interface (CLI). For more information about creating and managing API keys, see [Managing user API keys](/docs/services/account?topic=account-userapikey).


## Exporting your toolchain ID
{: #export-id-cicd}

To set the toolchain ID as an environment variable, first identify and save the toolchain ID for the {{site.data.keyword.DRA_short}} instance you would like to aggregate the data. For more information about how to find your toolchain ID, see [Identifying your toolchain ID](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources). 

Use the following steps to go to the {{site.data.keyword.contdelivery_short}} pipeline in your toolchain and set the toolchain ID as an environment variable:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select a location to view your toolchains that contain instances of {{site.data.keyword.DRA_short}}. 
3. Select your toolchain. 
4. Select the **{{site.data.keyword.deliverypipeline}}** tile. 
5. Click the **Settings** icon ![gear icon](images/settings.svg) > **Configure Stage**.
6. Select the **Jobs** tab. 
7. Make your changes in the script section. For each stage where you use commands to send build, test, and deployment records, set TOOLCHAIN_ID as the environment variable to the toolchain ID. Export the toolchain ID before they call the command. 

```text
export TOOLCHAIN_ID="YOUR_TOOLCHAIN_ID_HERE"
```
{: codeblock}


## Setting environment properties
{: #setting-parameters-cicd}

Use the `logicalappname` and `buildnumber` parameters consistently for publishing data to {{site.data.keyword.DRA_short}} or for evaluating policies. Refer to your CI/CD tool documentation to set `logicalappname` and `buildnumber` across jobs consistently.


## Next steps
{: #next-values-cicd}

[Publish a build record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cicd) by using other CI/CD tools.
