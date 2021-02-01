---

copyright:
  years: 2015, 2021
lastupdated: "2021-01-27"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Cloud Event Management

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}   

# Configuring Cloud Event Management
{: #cloudeventmanagement}

{{site.data.keyword.evtmgt_full}} provides a consolidated view of problems that occur with your services, applications, and infrastructure. You can set up real-time incident management to resolve the problems more efficiently.
{:shortdesc}

The Cloud Event Management tool integration uses a webhook URL to push notifications from your {{site.data.keyword.contdelivery_full}} toolchain to {{site.data.keyword.evtmgt_full}} as events. Cloud Event Management supports the `jobStarted`, `jobCompleted`, `stageStarted`, and `stageCompleted` event types. Cloud Event Management correlates these events incidents.
{: tip}

To help your DevOps team achieve reliable operational health, service quality, and continuous improvement goals, add the Cloud Event Management tool integration to your toolchain:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain that you want to add Cloud Event Management to. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **Cloud Event Management**.

1. Type the name that you want to display for this tool integration on the Cloud Event Management card in your toolchain.
1. Make sure that you save the generated webhook URL for later use. For example, you can save the URL in a file to use for further configuration.
1. Click **Create Integration**.
1. From your toolchain, click the **Event Management** tool card to create policies that determine when users receive incident notifications.

## Learn more about Cloud Event Management

To learn more about Cloud Event Management, see the [Cloud Event Management article](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){:external} on the IBM Cloud Garage Method.
