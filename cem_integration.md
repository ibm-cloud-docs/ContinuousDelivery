---

copyright:
  years: 2015, 2021
lastupdated: "2021-02-11"

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

## Prerequisites
{: #cem_prereq}

Before you can add the Cloud Event Management tool integration to your toolchain, you must generate a webhook URL. The tool integration uses this webhook URL to push notifications from your {{site.data.keyword.contdelivery_full}} toolchain to {{site.data.keyword.evtmgt_full}} as events. Cloud Event Management supports the `jobStarted`, `jobCompleted`, `stageStarted`, and `stageCompleted` event types and correlates these events into incidents.

1. Log in to {{site.data.keyword.cloud_notm}}.
1. From the Cloud Event Management service, click **Administration** > **Integrations** > **New Integration**.
1. On the {{site.data.keyword.contdelivery_full}} card, click **Configure**.
1. Type a name for the new integration and click **Copy** to copy the generated webhook URL to the clipboard. Save the webhook URL to a file for later use.
1. Make sure that **Enable event management from this source** is set to `On` to receive events, and click **Save**.

## Adding the Cloud Event Management tool integration
{: #cem_integration}

To help your DevOps team achieve reliable operational health, service quality, and continuous improvement goals, add the Cloud Event Management tool integration to your toolchain:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain that you want to add Cloud Event Management to. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **Event Management**.

1. In the **WebHook URL** field, paste the generated webhook URL that you previously saved.
1. Click **Create Integration**.
1. From your toolchain, click the **Event Management** tool card to open the Event Management Getting Started page. A notification is issued to alert you that an event source was added.
1. Click the link to view events and their incidents from {{site.data.keyword.contdelivery_short}}.

## Learn more about Cloud Event Management
{: #cem_learnmore}

To learn more about Cloud Event Management, see the [Cloud Event Management article](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){:external} on the IBM Cloud Garage Method. 
