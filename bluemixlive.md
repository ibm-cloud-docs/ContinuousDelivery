---

copyright:
  years: 2015, 2022
lastupdated: "2022-07-08"

keywords: IBM Cloud Live Sync, Use IBM Cloud Live Sync, Web IDE, Live Edit

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

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

The Eclipse Orion {{site.data.keyword.webide}} feature in the {{site.data.keyword.contdelivery_full}} service is deprecated. The {{site.data.keyword.contdelivery_short}} service does not provide a direct replacement. As of 8 August 2022, new toolchains will not include the {{site.data.keyword.webide}} as a default tool. You cannot create and add instances of the {{site.data.keyword.webide}} tool integration to existing toolchains. Existing instances of the {{site.data.keyword.webide}} continue to operate normally. As of 7 October 2022, the {{site.data.keyword.webide}} tool integration will be removed from existing toolchains and the associated data will be deleted. It is recommended that you export your data from your {{site.data.keyword.webide}} workspace before this date, or commit and push all of your outstanding changes into a Git repository.
{: deprecated}

If you are building a Node.js application, you can use {{site.data.keyword.cloud}} Live Sync to quickly update the application instance on {{site.data.keyword.cloud_notm}} and develop without manually redeploying.   
{: shortdesc}

When you make a change, you can see that change in your running {{site.data.keyword.cloud_notm}} application immediately. {{site.data.keyword.cloud_notm}} Live Sync works in the Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}). 

## Live Edit
{: #live-edit}

You can edit a Node.js application that runs on {{site.data.keyword.cloud_notm}} and test it in your browser right away. Any changes that you make in the {{site.data.keyword.webide}} are propagated to the application’s file system immediately.

If you are building a Node.js application that runs on {{site.data.keyword.cloud_notm}}, the Live Edit feature of {{site.data.keyword.cloud_notm}} Live Sync can quickly update the application instance. Live Edit is available in the {{site.data.keyword.webide}} only. You can use Live Edit to develop as you would on the desktop without redeploying.

Live Edit is supported for Node.js applications only.
{: important}

In the {{site.data.keyword.webide}}, in the run bar, click **Live Edit**.

![Image of Run bar with live edit](images/cloud-live-sync-light.png){: caption="Figure 1. Run bar with Live Edit" caption-side="bottom"}

Use Live Edit to quickly preview changes to Node.js applications that run on {{site.data.keyword.cloud_notm}}. When you update your code with Live Edit turned on, you can refresh your web application's browser window to see those changes reflected seconds after you make them.

For a tutorial about using the Live Edit feature of {{site.data.keyword.cloud_notm}} Live Sync, see [Use {{site.data.keyword.cloud_notm}} Live Sync to develop, debug, and deploy your app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}.

When you change the files in your {{site.data.keyword.webide}}, they are automatically redeployed to your application instance on {{site.data.keyword.cloud_notm}}. If you need to restart the Node application, click the **Restart** button in the run bar.

For a more consistent experience, when you use the Live Edit feature of {{site.data.keyword.cloud_notm}} Live Sync, 256 MB of extra memory is required and is added.
{: tip}
