---



copyright:
  years: 2015，2017
lastupdated: "2017-09-20"

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}

#Bluemix Live Sync
{: #live-sync}


如果您要建置 Node.js 應用程式，可以使用 {{site.data.keyword.Bluemix}} Live Sync 快速更新 {{site.data.keyword.Bluemix_notm}} 上的應用程式實例，而且只需開發，不需手動重新部署。   
{: shortdesc}

當您進行變更時，可以立即在執行中的 {{site.data.keyword.Bluemix_notm}} 應用程式看到該變更。{{site.data.keyword.Bluemix_notm}} Live Sync 會
<!--from both the command line and -->
在 Eclipse Orion Web IDE (Web IDE) 中運作。您可以使用 {{site.data.keyword.Bluemix_notm}} Live Sync，針對以 Node.js 撰寫的應用程式進行除錯。  

{{site.data.keyword.Bluemix_notm}} Live Sync 包含兩個特性。
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**即時編輯**

您可以編輯在 {{site.data.keyword.Bluemix_notm}} 上執行的 Node.js 應用程式，並立即在瀏覽器中進行測試。您在 Web IDE 中進行的任何變更，都會立即傳播到應用程式的檔案系統。  

**除錯**  

當 Node.js 應用程式處於「即時編輯」模式時，您可以使用 Shell 進入並對其進行除錯。您可以使用 Node Inspector 除錯器，以動態編輯程式碼、插入岔斷點、逐步執行程式碼、重新啟動運行環境等等。  


##即時編輯
{: #live-edit}

如果您要建置在 {{site.data.keyword.Bluemix_notm}} 上執行的 Node.js 應用程式，{{site.data.keyword.Bluemix_notm}} Live Sync 的「即時編輯」特性可以快速更新應用程式實例。只有 Web IDE 中才提供「即時編輯」。「即時編輯」可讓您就像在桌面上開發一樣，而無需重新部署。

僅 Node.js 應用程式才支援「即時編輯」。

在 Eclipse Orion Web IDE (Web IDE) 中，按一下執行列中的**即時編輯**。

![含有即時編輯的執行列影像](images/bluemix-live-sync-light.png)

「即時編輯」可讓您快速預覽在 {{site.data.keyword.Bluemix_notm}} 上執行之 Node.js 應用程式的變更。當您開啟「即時編輯」來更新程式碼時，可以重新整理 Web 應用程式的瀏覽器視窗，就能看到在進行變更幾秒後所反映的變更。

<!--
For a tutorial on using the Live Edit feature of {{site.data.keyword.Bluemix_notm}} Live Sync, see the tutorial [Test and debug a Node.js app with Bluemix Live Sync![External link icon](../icons/launch-glyph.svg "External link icon")](https://hub.jazz.net/tutorials/livesync){:new_window}.
-->

當您變更 Web IDE 中的檔案時，會自動將其重新部署至 {{site.data.keyword.Bluemix_notm}} 上的應用程式實例。如果您需要重新啟動 Node 應用程式，可以使用執行列中的**重新啟動**按鈕。

**附註：**為達到使用 {{site.data.keyword.Bluemix_notm}} Live Sync 的「即時編輯」特性時更一致的體驗，需要且會新增 256MB 的額外記憶體。

## Bluemix 即時除錯
{: #live-debug}

「{{site.data.keyword.Bluemix_notm}} Live Sync 除錯」使用 [Node Inspector ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/node-inspector/node-inspector){:new_window} 來提供除錯特性。您需要使用 Node 第 4 版才能使用除錯器，因為 Node.js 後續版本不包括 Node Inspector。

啟用 Node.js 應用程式的「{{site.data.keyword.Bluemix_notm}} 即時編輯」時，您可以存取「{{site.data.keyword.Bluemix_notm}} 即時除錯」。  

您可以使用除錯來動態編輯程式碼、插入岔斷點、逐步執行程式碼、重新啟動運行環境等等，這些全都可以在由 {{site.data.keyword.Bluemix_notm}} 為您的應用程式提供服務時執行。您可以靈活地以漸進方式開發應用程式，同時從龐大的 {{site.data.keyword.Bluemix_notm}} 服務清單進行選擇。

「{{site.data.keyword.Bluemix_notm}} 即時除錯」包括下列特性：

* 應用程式運行環境控制
* 使用 [Node Inspector ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/node-inspector/node-inspector){:new_window} 進行除錯
* Shell 存取

### 應用程式運行環境控制{: #app-runtime}

使用應用程式運行環境控制，您可以使用「除錯」來檢查應用程式在啟動時的狀態。當您對啟動時造成當機的應用程式進行疑難排解時，此功能很有用。

開發應用程式時，可以從下列動作選取：

* 執行應用程式的快速重新啟動
* 在任何應用程式碼執行之前先暫停應用程式

登入之後，即會開啟「{{site.data.keyword.Bluemix_notm}} 即時除錯」頁面。

![除錯使用者介面](images/live_sync_debug.png)


### 除錯 {: #debug}

**限制：**需要使用 Google Chrome。需要使用 Node 4。

「除錯」包括下列功能：  
* 在應用程式碼中設定岔斷點，以在特定行暫停執行。**附註：**主程式中不支援岔斷點，但進入點中提供支援。
* 編輯岔斷點條件，只在符合特定準則時暫停執行。
* 檢查區域變數及欄位的狀態。
* 立即檢視來自 `console.log()` 呼叫的除錯輸出。此動作的速度比監視 cf logs 還要快。
* 使用內建原始碼編輯器，對執行中應用程式碼進行立即但暫時的變更。

### Shell {: #shell}

此工具可讓您對應用程式執行所在的容器進行 Shell 存取。您可以使用此終端機，在遠端執行診斷 Shell 指令來管理應用程式。所有 Node.js 版本都支援 Shell 特性。

監視使用標準 Linux 指令（例如 **top**、**ps** 及 **kill**）之實例內的記憶體及 CPU 使用率。

### 配置應用程式，以啟用 {{site.data.keyword.Bluemix_notm}} 即時除錯 {: #configure_app_debug}

1. 「Bluemix 即時除錯器」使用 Node Inspector。您需要使用 Node 第 4 版。您也需要容許建置套件偵測 app start 指令。start 指令必須由建置套件自動偵測，而不是設定在 manifest.yml 檔案中。 
  
   支援「{{site.data.keyword.Bluemix_notm}} 即時除錯」的 `package.json` 檔案如下：
   
  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. 增加記憶體。  

    a. 在應用程式 `manifest.yml` 檔案中，在為記憶體屬性指定的值加上 128M 以上。

安裝「{{site.data.keyword.Bluemix_notm}} 即時除錯」之後，您可以使用除錯工具。

推送應用程式，然後瀏覽至 `https://_app-host.mybluemix.net_/bluemix-debug/manage`，以存取 {{site.data.keyword.Bluemix_notm}} 除錯使用者介面。系統提示您進行鑑別時，請輸入 IBM ID 使用者名稱和密碼或一次性密碼。    

**附註：**「除錯器」大約需要一分鐘才能起始設定。

<!--
   **Note**: Your user ID for DevOps Services can be either an IBMid or a federated ID (corporate ID). If you use federated authentication, to log in to your Bluemix Live Sync command-line client, you must use a personal access token instead of a password. If you don't use federated authentication, your IBMid and password work with all clients. For more information about creating a personal access token, see [What's federated authentication and how does it affect me?![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2016/06/23/whats-federated-authentication-and-how-does-it-affect-me/){:new_window}
   -->

### 還原應用程式配置並停用 {{site.data.keyword.Bluemix_notm}} 即時除錯 {: #restore_live_debug}

1. 還原應用程式的原始 Node.js 版本、start 指令及記憶體值。

2. 推送應用程式。

### 如需相關資訊

* 請參閱 [Eclipse Tools for Bluemix ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.bluemix.net/docs/manageapps/eclipsetools/eclipsetools.html){:new_window}
