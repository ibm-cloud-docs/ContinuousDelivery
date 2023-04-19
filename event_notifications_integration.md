---

copyright:
  years: 2023
lastupdated: "2023-04-19"

keywords: tool integrations, IBM Cloud Public, Event Notifications

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}   

# Configuring {{site.data.keyword.en_short}}
{: #event-notifications-integration}

You can use the {{site.data.keyword.en_full}} service to receive information about critical events that occur in your {{site.data.keyword.cloud}} account. You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like Toolchains, Monitoring, Security and Compliance Center, and Secrets Manager to communication channels like PagerDuty, Slack, email, SMS, push notifications, webhook, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}.
{: shortdesc}

Before you configure an {{site.data.keyword.en_short}} tool integration, make sure that you provision an instance of the [{{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-en-create-en-instance) service.
{: important}

By connecting a toolchain to an {{site.data.keyword.en_short}} service instance, the {{site.data.keyword.en_short}} tool integration enables the toolchain and its associated tool integration instances to send events to any of the destinations that are supported by the {{site.data.keyword.en_short}} service.

Make sure that the selected {{site.data.keyword.en_short}} service instance has an [IAM authorization policy](/iam/authorizations/grant) that allows the toolchain to send events to this service instance. For more information about granting authorization with the {{site.data.keyword.en_short}} service instance, see [Why am I denied permission to integrate an Event Notifications instance?](/docs/event-notifications?topic=event-notifications-troubleshoot-integrate).
{: important}

Configure {{site.data.keyword.en_short}} to send critical events from toolchains and tool integration instances:

1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.en_short}}**.

1. Type the name that you want to display for this tool integration on the {{site.data.keyword.en_short}} card in your toolchain. This name is used to identify the tool integration in your toolchain.
1. Select the instance of the **{{site.data.keyword.en_short}}** service that you want to use.
1. Click **Create Integration**.
1. On your Toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.en_short}}**.
 
## Configuring {{site.data.keyword.en_short}} by using the API
{: #event-notifications-config-parameters}

The {{site.data.keyword.en_short}} tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `eventnotifications` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| name | required, updatable | String | name | The name of this tool integration. |
| instance-crn  | required, updatable | String | instance_crn | The Cloud Resource Name (CRN) of the {{site.data.keyword.en_short}} service instance. |
{: caption="Table 1. {{site.data.keyword.en_short}} tool integration parameters" caption-side="bottom"}

## Learn more about {{site.data.keyword.en_short}}
{: #learn_event_notifications}

To learn more about {{site.data.keyword.en_short}}, see [Getting started with {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-getting-started).
