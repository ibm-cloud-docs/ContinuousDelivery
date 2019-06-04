---



copyright:
  years: 2015，2019
lastupdated: "2019-06-04"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

If you are building a Node.js application, you can use {{site.data.keyword.Bluemix}} Live Sync to quickly update the application instance on {{site.data.keyword.Bluemix_notm}} and develop without manually redeploying.   
{: shortdesc}

When you make a change, you can see that change in your running {{site.data.keyword.Bluemix_notm}} application immediately. {{site.data.keyword.Bluemix_notm}} Live Sync works
<!--from both the command line and -->
in the Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}). 

##Live Edit
{: #live-edit}

You can edit a Node.js application that runs on {{site.data.keyword.Bluemix_notm}} and test it in your browser right away. Any changes that you make in the {{site.data.keyword.webide}} are propagated to the application’s file system immediately.

If you are building a Node.js application that runs on {{site.data.keyword.Bluemix_notm}}, the Live Edit feature of {{site.data.keyword.Bluemix_notm}} Live Sync can quickly update the application instance. Live Edit is available in the {{site.data.keyword.webide}} only. You can use Live Edit to develop as you would on the desktop without redeploying.

Live Edit is supported for Node.js applications only.
{: important}

In the {{site.data.keyword.webide}}, in the run bar, click **Live Edit**.

![Image of Run bar with live edit](images/cloud-live-sync-light.png)

Use Live Edit to quickly preview changes to Node.js applications that run on {{site.data.keyword.Bluemix_notm}}. When you update your code with Live Edit turned on, you can refresh your web application's browser window to see those changes reflected seconds after you make them.

For a tutorial about using the Live Edit feature of {{site.data.keyword.Bluemix_notm}} Live Sync, see [Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop, debug, and deploy your app ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window}.

When you change the files in your {{site.data.keyword.webide}}, they are automatically redeployed to your application instance on {{site.data.keyword.Bluemix_notm}}. If you need to restart the Node application, click the **Restart** button in the run bar.

For a more consistent experience, when you use the Live Edit feature of {{site.data.keyword.Bluemix_notm}} Live Sync, 256 MB of extra memory is required and is added.
{: tip}
