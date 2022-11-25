---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-22"

keywords: tool integrations, IBM Cloud Public, Sauce Labs

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring Sauce Labs
{: #saucelabs}

Sauce Labs runs functional unit tests. When a Sauce Labs test suite is configured as a test job in the {{site.data.keyword.deliverypipeline}}, the test suite can run tests against your web or mobile app as part of your continuous delivery process. These tests can provide valuable flow control for your projects, acting as gates to prevent the deployment of bad code.
{: shortdesc}

This tool integration is available only on {{site.data.keyword.cloud_notm}} Public.
{: tip}

Configure Sauce Labs to run automated functional tests on multiple operating systems and browsers so that you can emulate the way that a user might use a website or an application:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **Sauce Labs**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **Sauce Labs**.

1. Type the user name that is associated with your Sauce Labs account. You can [find your user name in the welcome message on your Sauce Labs account page](https://app.saucelabs.com/user-settings){: external}.
1. Type the access key for your Sauce Labs account. You can [find the key on your Sauce Labs account page](https://app.saucelabs.com/user-settings){: external}.
1. Click **Create Integration**.
1. On your Toolchain's Overview page, on the **Third-Party tools** card, click **Sauce Labs** to go to saucelabs.com and view the test activity for the toolchain.

If you added a Sauce Labs test job to the {{site.data.keyword.deliverypipeline}}, you can select the service instance. For instructions to configure a test job in your pipeline, see the [Configuring a Sauce Labs test job in your pipeline](#config_saucelabs) section.
{: tip}

## Configuring Sauce Labs by using the API
{: #config-parameters}

The Sauce Labs tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `saucelabs` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| key | required, updatable | Password | access_key | The access key for the Sauce Labs account. You can use a toolchain secret reference for this parameter. For more information about secret references, see [Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| username | required, updatable | String | username | The username of the Sauce Labs account. |
{: caption="Table 1. Sauce Labs tool integration parameters" caption-side="bottom"}

## Learn more about Sauce Labs
{: #learn_saucelabs}

To learn more about Sauce Labs, see the [Sauce Labs article](https://www.ibm.com/cloud/garage/content/deliver/tool_sauce_labs/){: external} on the {{site.data.keyword.cloud_notm}} Garage Method.
