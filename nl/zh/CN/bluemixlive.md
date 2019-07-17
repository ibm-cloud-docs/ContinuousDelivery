---



copyright:
  years: 2015，2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

如果要构建 Node.js 应用程序，您可以使用 {{site.data.keyword.Bluemix}} Live Sync 来快速更新 {{site.data.keyword.Bluemix_notm}} 上的应用程序实例并进行开发，而无需手动重新部署。   
{: shortdesc}

执行更改后，您可以立即在运行中的 {{site.data.keyword.Bluemix_notm}} 应用程序中看到该更改。{{site.data.keyword.Bluemix_notm}} Live Sync 
<!--from both the command line and -->
在 Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}) 中运行。 

##实时编辑
{: #live-edit}

可以编辑在 {{site.data.keyword.Bluemix_notm}} 上运行的 Node.js 应用程序，然后立即在浏览器中对其进行测试。在 {{site.data.keyword.webide}} 中进行的任何更改都会立即传播到应用程序的文件系统。

如果要构建在 {{site.data.keyword.Bluemix_notm}} 上运行的 Node.js 应用程序，那么 {{site.data.keyword.Bluemix_notm}} Live Sync 的“实时编辑”功能可快速更新应用程序实例。“实时编辑”仅在 {{site.data.keyword.webide}} 中可用。您可以使用“实时编辑”，无需重新部署即可像在桌面上一样进行开发。

“实时编辑”仅支持用于 Node.js 应用程序。
{: important}

在 {{site.data.keyword.webide}} 中，单击运行栏中的**实时编辑**。

![带“实时编辑”的“运行”栏的图像](images/cloud-live-sync-light.png)

使用“实时编辑”，可以快速预览对在 {{site.data.keyword.Bluemix_notm}} 上运行的 Node.js 应用程序的更改。如果在开启“实时编辑”的情况下更新代码，那么在执行更改之后仅需几秒钟的时间，就可以通过刷新 Web 应用程序浏览器窗口看到这些更改反映出来。

有关使用 {{site.data.keyword.Bluemix_notm}} Live Sync 的“实时编辑”功能的教程，请参阅 [Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop, debug, and deploy your app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}。

在 {{site.data.keyword.webide}} 中更改文件时，这些文件将自动重新部署到 {{site.data.keyword.Bluemix_notm}} 上的应用程序实例。如果需要重新启动 Node 应用程序，请单击运行栏中的**重新启动**按钮。

为了在使用 {{site.data.keyword.Bluemix_notm}} Live Sync 的“实时编辑”功能时获得更一致的体验，需要并且已添加额外 256 MB 内存。
{: tip}
