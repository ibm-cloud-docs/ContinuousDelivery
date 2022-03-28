---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-24"

keywords: devops insights, setting, values, cli, parameter values, consistent, test, tests, install, app, dashboard, risk, build.properties

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
{: #setting-values-cli}

As part of integrating {{site.data.keyword.deliverypipelinelong}} with {{site.data.keyword.DRA_full}}, you set consistent parameter values to publish data to {{site.data.keyword.DRA_short}}.
{: shortdesc}

{{site.data.keyword.DRA_short}} tracks deployment risk based on published test data. When you integrate {{site.data.keyword.DRA_short}} with your {{site.data.keyword.deliverypipeline}}, you are instrumenting {{site.data.keyword.DRA_short}} to gather information from the pipeline. Information that is gathered from the pipeline is presented in {{site.data.keyword.DRA_short}} dashboard to provide visibility into your DevOps process.


## Before you begin
{: #prereq-values-cli}

Configure {{site.data.keyword.deliverypipeline}} in your toolchain to build, test, and deploy. You must complete this step before you continue with the integration. For more information, see [Configuring {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline).

You need an API key to integrate with {{site.data.keyword.DRA_short}}. This API key has access to the toolchain, and is used to log in with the {{site.data.keyword.cloud}} command line interface (CLI). For more information, see [Managing user API keys](/docs/services/account?topic=account-userapikey).

Install the {{site.data.keyword.cloud_notm}} CLI. For more information, see [Getting started with the {{site.data.keyword.cloud_notm}} CLI and {{site.data.keyword.dev_cli_short}}](/docs/cli?topic=cli-getting-started).


## Setting environment properties
{: #setting-environment-properties}

Use the `logicalappname` and `buildnumber` parameters consistently for publishing data to {{site.data.keyword.DRA_short}} or for evaluating policies. To set `logicalappname` and `buildnumber` values consistently across pipeline stages, you need to set two properties in environment properties in the stage where you do the build.

The values of `MY_APP_NAME` and `MY_BUILD_NUMBER` are used in all stages. Use these values when you are integrating with {{site.data.keyword.contdelivery_short}}. For example, set `MY_APP_NAME` to `My First App` and set `MY_BUILD_NUMBER` to `$BRANCH:$BUILD_NUMBER`.

Configure your pipeline to use these properties across all stages. Save these properties to the `build.properties` file in your build job and use the following script.

```text
echo "MY_APP_NAME=${MY_APP_NAME}" >> $ARCHIVE_DIR/build.properties
echo "MY_BUILD_NUMBER=${MY_BUILD_NUMBER}" >> $ARCHIVE_DIR/build.properties
```
{: codeblock}


## Setting environment properties within your delivery pipeline
{: #setting-properties-pipeline}

Next, on the pipeline configuration page, set a property with name `buildProperties` and the value `build.properties`. You must set the property name and the value for each stage in your pipeline.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **Resource List**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **Delivery pipelines** card, click the pipeline that you want to use.
4. Click the **Settings** icon ![gear icon](images/settings.svg) > **Configure Stage**.
5. Select the **Environment properties** tab.
6. If your API key isn't listed, click **+ Add property** > **Secure property**, and add your API key.  
7. Click **+ Add property** > **Properties file**.
8. Enter `buildProperties` as the name and `build.properties` as the value.
9. Click **Save**.


## Next steps
{: #next-values-cli}

[Publish a build record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cli).
