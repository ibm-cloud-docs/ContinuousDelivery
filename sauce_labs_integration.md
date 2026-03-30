---

copyright:
  years: 2015, 2026
lastupdated: "2026-03-30"

keywords: tool integrations, IBM Cloud Public, Sauce Labs

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring Sauce Labs
{: #saucelabs}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 10 April 2026: **eu-es** and **jp-osa**.
This discontinuation also applies to any features provided within the service, including Code Risk Analyzer and {{site.data.keyword.DRA_short}}.
[Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 12 February 2027: **au-syd**, **ca-mon**, **ca-tor**, **us-east**. Code Risk Analyzer and {{site.data.keyword.DRA_short}} will also be deprecated in all regions on that date. However, if a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

Sauce Labs runs functional unit tests. When a Sauce Labs test suite is configured as a test job in the {{site.data.keyword.deliverypipeline}}, the test suite can run tests against your web or mobile app as part of your continuous delivery process. These tests can provide valuable flow control for your projects, acting as gates to prevent the deployment of bad code.
{: shortdesc}

This tool integration is available only on {{site.data.keyword.cloud_notm}} Public.
{: tip}

Configure Sauce Labs to run automated functional tests on multiple operating systems and browsers so that you can emulate the way that a user might use a website or an application:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **Sauce Labs**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page.

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **Sauce Labs**.

1. Type the user name that is associated with your Sauce Labs account. You can [find your user name in the welcome message on your Sauce Labs account page](https://app.saucelabs.com/user-settings){: external}.
1. Type the access key for your Sauce Labs account. You can [find the key on your Sauce Labs account page](https://app.saucelabs.com/user-settings){: external}.
1. Click **Create Integration**.
1. On your Toolchain's Overview page, on the **Third-Party tools** card, click **Sauce Labs** to go to saucelabs.com and view the test activity for the toolchain.

If you added a Sauce Labs test job to the {{site.data.keyword.deliverypipeline}}, you can select the service instance. For instructions to configure a test job in your pipeline, see the [Configuring a Sauce Labs test job in your pipeline](#config_saucelabs) section.
{: tip}

## Configuring Sauce Labs by using the API
{: #saucelabs-config-parameters}

The Sauce Labs tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `saucelabs` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| key | required, updatable | Password | access_key | The access key for the Sauce Labs account. You can use a toolchain secret reference for this parameter. For more information about secret references, see [Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| username | required, updatable | String | username | The username of the Sauce Labs account. |
{: caption="Sauce Labs tool integration parameters" caption-side="bottom"}
