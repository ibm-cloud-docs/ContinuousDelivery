---

copyright:
  years: 2015, 2023
lastupdated: "2023-04-19"

keywords: tool integrations, IBM Cloud Public, PagerDuty

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}} 

# Configuring PagerDuty
{: #pagerduty}

PagerDuty integrates data from multiple monitoring systems into a single view. When a problem occurs, PagerDuty ensures that the team member who is best able to fix it at the time is notified. If the team member does not respond to the problem, escalations can be configured to route it to secondary representatives or operations managers.
{: shortdesc}

You can now distribute event notifications by using the [{{site.data.keyword.en_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-integration) tool integration. {{site.data.keyword.en_full}} is the preferred method for distributing notifications to PagerDuty and other communication channels such as Slack, email, SMS, push notifications, webhook, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}. For more information about using {{site.data.keyword.en_short}}, see [Enabling event notifications for toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd).
{: tip}

Configure PagerDuty to send notifications when pipeline stage failures occur so that you can fix problems faster and reduce downtime:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **PagerDuty**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **PagerDuty**.

1. If you want to integrate PagerDuty at the account level by using an API key, click **Account**:

   a. Type the API access key for your PagerDuty account. If you don't have a PagerDuty account, [register for one](https://www.pagerduty.com/sign-up/){: external}. For instructions to find the key, see [Generating an API Key](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){: external}.

   b. Type the name of your PagerDuty service.

   c. Type the email address for the primary PagerDuty contact.

   d. Type the phone number for the primary PagerDuty contact.

1. If you want to integrate PagerDuty at the service level by using an integration key, click **Service**:

   a. Type the URL for the PagerDuty service that you want to post alerts to.

   b. Type your PagerDuty integration key. You can find your key or create a key in the Integrations section of your PagerDuty service page.

1. Click **Create Integration**.
1. On your Toolchain's Overview page, on the **Third-Party tools** card, click **PagerDuty** to go to pagerduty.com. You can view the events that are associated with the PagerDuty service that you specified when you configured this tool integration for your toolchain.

## Configuring PagerDuty by using the API
{: #pagerduty-config-parameters}

The PagerDuty tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `pagerduty` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| service_id | optional, updatable | String | service_id | The service ID of the PagerDuty service. |
| service_key | optional, updatable | Password | service_key | The PagerDuty service tool integration key. You can find or create this key in the Integrations section of the PagerDuty service page. |
| service_url | optional, updatable | String | service_url | The URL of the PagerDuty service to post alerts to. |
{: caption="Table 1. PagerDuty tool integration parameters" caption-side="bottom"}

## Learn more about PagerDuty
{: #learn_pagerduty}

To learn more about PagerDuty, see the [PagerDuty article](https://www.ibm.com/garage/method/practices/manage/tool_pagerduty/){: external} on the {{site.data.keyword.cloud_notm}} Garage Method.
