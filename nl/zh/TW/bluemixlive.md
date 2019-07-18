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

如果您要建置 Node.js 應用程式，可以使用 {{site.data.keyword.Bluemix}} Live Sync 快速更新 {{site.data.keyword.Bluemix_notm}} 上的應用程式實例，而且只需開發，不需手動重新部署。   
{: shortdesc}

當您進行變更時，可以立即在執行中的 {{site.data.keyword.Bluemix_notm}} 應用程式看到該變更。{{site.data.keyword.Bluemix_notm}} Live Sync 會
<!--from both the command line and -->
在 Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}) 中運作。 

##即時編輯
{: #live-edit}

您可以編輯在 {{site.data.keyword.Bluemix_notm}} 上執行的 Node.js 應用程式，並立即在瀏覽器中進行測試。您在 {{site.data.keyword.webide}} 中進行的任何變更，都會立即傳播到應用程式的檔案系統。

如果您要建置在 {{site.data.keyword.Bluemix_notm}} 上執行的 Node.js 應用程式，{{site.data.keyword.Bluemix_notm}} Live Sync 的「即時編輯」特性可以快速更新應用程式實例。只有 {{site.data.keyword.webide}} 中才提供「即時編輯」。您可以使用「即時編輯」進行開發，就像在桌面上開發一樣，而無需重新部署。

僅 Node.js 應用程式才支援「即時編輯」。
{: important}

在 {{site.data.keyword.webide}} 中，按一下執行列中的**即時編輯**。

![含有即時編輯的執行列影像](images/cloud-live-sync-light.png)

請使用「即時編輯」快速預覽在 {{site.data.keyword.Bluemix_notm}} 上執行之 Node.js 應用程式的變更。當您開啟「即時編輯」來更新程式碼時，可以重新整理 Web 應用程式的瀏覽器視窗，就能看到在進行變更幾秒後所反映的變更。

如需使用 {{site.data.keyword.Bluemix_notm}} Live Sync 之「即時編輯」特性的指導教學，請參閱[使用 {{site.data.keyword.Bluemix_notm}} Live Sync 開發、除錯及部署應用程式](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}。

當您變更 {{site.data.keyword.webide}} 中的檔案時，會自動將其重新部署至 {{site.data.keyword.Bluemix_notm}} 上的應用程式實例。如果您需要重新啟動 Node 應用程式，請按一下執行列中的**重新啟動**按鈕。

為了達到更一致的體驗，在使用 {{site.data.keyword.Bluemix_notm}} Live Sync 的「即時編輯」特性時，需要且會新增 256 MB 的額外記憶體。
{: tip}
