---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}   

# 配置工具整合
{: #integrations}

您可以在建立開放式工具鏈時配置可支援開發、部署及操作作業的工具整合，也可以新增及配置用來自訂現有工具鏈的工具整合。  
{:shortdesc}

可用來新增及配置工具鏈的工具整合，會視您是在 {{site.data.keyword.Bluemix_notm}} Public 還是在 {{site.data.keyword.Bluemix_notm}} Dedicated 上使用工具鏈而改變。如果您在 {{site.data.keyword.Bluemix_notm}} Public 上使用工具鏈，則可供您使用的工具整合取決於工具鏈的地區以及該地區中工具整合的可用性。如果您在 {{site.data.keyword.Bluemix_notm}} Dedicated 上使用工具鏈，則可供您使用的工具整合取決於 {{site.data.keyword.contdelivery_full}} 在特定環境上的設定方式。

|工具整合|可用於 {{site.data.keyword.Bluemix_notm}} Public|可用於 {{site.data.keyword.Bluemix_notm}} Dedicated（環境相依）|
|:----------|:------------------------------|:------------------|
|{{site.data.keyword.alertnotificationshort}}		|美國南部		|否		|
|Artifactory		|美國南部、德國、英國		|是		|
|Availability Monitoring		|美國南部		|否		|
|Bitbucket		|美國南部、德國、英國		|否		|
|Cloud Event Management		|美國南部		|否		|
|{{site.data.keyword.deliverypipeline}} 		|美國南部、德國、英國		|是  		|
|{{site.data.keyword.DRA_short}} 		|美國南部		|否			|
|Eclipse Orion {{site.data.keyword.webide}}		|美國南部、德國、英國		|是			|
|{{site.data.keyword.gitrepos}}	|美國南部、德國、英國		|否		|
|GitHub		|美國南部、德國、英國		|是		|
|Dedicated {{site.data.keyword.ghe_short}} 及 Issues|否		|是		|
|GitLab		|美國南部、德國、英國		|否		|
|Jenkins		|美國南部、德國、英國		|是		|
|JIRA		|美國南部、德國、英國		|是		|
|Nexus			|美國南部、德國、英國		|是		|
|其他工具		|美國南部、德國、英國		|是		|
|PagerDuty			|美國南部、德國、英國		|是		|
|Rational Team Concert|美國南部、德國、英國		|是		|
|Sauce Labs		|美國南部、德國、英國		|否		|
|Slack			|美國南部、德國、英國		|是		|
|SonarQube			|美國南部、德國、英國		|是		|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} Public 及 Dedicated 上工具鏈可用的工具整合" caption-side="top"}

如果您要在 {{site.data.keyword.Bluemix_notm}} Public 上開始使用原始碼進行開發，請先配置 GitHub 工具整合或 {{site.data.keyword.gitrepos}} 工具整合，再配置 {{site.data.keyword.deliverypipeline}}。如果您要在 {{site.data.keyword.Bluemix_notm}} Dedicated 上開始使用程式碼進行開發，請先配置 {{site.data.keyword.ghe_short}} 工具整合或 GitHub 工作整合，再配置 {{site.data.keyword.deliverypipeline}}。
{: tip}


## 配置 Alert Notification
{: #alertnotification}

{{site.data.keyword.alertnotificationfull}} 是一個混合式雲端型解決方案，可用來集中化及簡化通知策略。它與其他雲端型及內部部署應用程式搭配運作。使用安全 RESTful API，即可將警示轉遞給 {{site.data.keyword.alertnotificationshort}}。

配置 {{site.data.keyword.alertnotificationshort}} 以接收有關 DevOps 處理程序期間之問題的通知。

### 必要條件

1. 如果您沒有 {{site.data.keyword.alertnotificationshort}} 帳戶，請註冊一個帳戶：

 a. 在 IBM Marketplace 中，開啟 [IBM {{site.data.keyword.alertnotificationshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/us-en/marketplace/alert-notification){: new_window} 頁面。

 b. 購買訂閱，或註冊以取得免費 90 天試用。

1. 設定 {{site.data.keyword.alertnotificationshort}} 帳戶之後，請開啟[我的 IBM 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://myibm.ibm.com/dashboard/){: new_window}。
1. 按一下 IBM {{site.data.keyword.alertnotificationshort}} 旁的**啟動**。
1. 按一下**管理 API 金鑰**，然後按一下**建立 API 金鑰**。
1. 在**建立 API 金鑰**欄位中，鍵入說明。
1. 按一下**產生**。即會顯示新的 API 金鑰資訊（包括名稱及密碼）。您需要該資訊來進行工具整合配置，因此仍會開啟「新建 API 金鑰」視窗。基於安全目的，您之後無法擷取 API 金鑰密碼。

### 配置 Alert Notification

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **{{site.data.keyword.alertnotificationshort}}**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **{{site.data.keyword.alertnotificationshort}}**。

1. 鍵入您要使用之 {{site.data.keyword.alertnotificationshort}} API 的 URL。您可以在 {{site.data.keyword.alertnotificationshort}} 服務的「管理 API 金鑰」頁面上找到此 URL；例如，`https://ibmnotifybm.mybluemix.net/api/alerts/v1`。
1. 鍵入 {{site.data.keyword.alertnotificationshort}} 的 API 金鑰名稱。您可以在「新建 API 金鑰」視窗中找到 API 金鑰名稱。
1. 鍵入 {{site.data.keyword.alertnotificationshort}} 針對 API 金鑰所產生的密碼。您可以在「新建 API 金鑰」視窗中找到 API 金鑰密碼。
1. 按一下**建立整合**。
1. 從工具鏈中，按一下 **{{site.data.keyword.alertnotificationshort}}**。

### 進一步瞭解 Alert Notification

若要進一步瞭解 {{site.data.keyword.alertnotificationshort}}，請參閱 IBM Cloud Garage Method 上的 [IBM {{site.data.keyword.alertnotificationshort}} 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/manage/tool_alert_notification/){: new_window}，或採用下列指導教學：

  * [將工具整合新增至工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/add-a-tool-integration-to-a-toolchain){:new_window}

  * [使用 {{site.data.keyword.Bluemix_notm}} Availability Monitoring 及 Alert Notification 來管理 {{site.data.keyword.Bluemix_notm}} 應用程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:new_window}


## 配置 Artifactory
{: #artifactory}

配置 Artifactory 儲存庫管理員，以將建置構件儲存至 Artifactory 儲存庫：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Artifactory**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Artifactory**。

1. 鍵入當您按一下 Artifactory 卡片時所要開啟的 Artifactory 儲存庫 URL。
1. 選取您要連接的儲存庫類型。
1. 如果您使用的是 Artifactory npm 登錄，請遵循下列步驟：

 a. 鍵入與您的登錄相關聯的電子郵件位址。

 b. 鍵入與您的登錄相關聯的鑑別記號。

 c. 鍵入 Artifactory 版本儲存庫的 URL，這是您在 Artifactory 伺服器上的專用登錄。

 d. 鍵入您用來結合多個公用及專用 npm 登錄的「鏡映」或「公用」登錄 URL。例如，此 URL 可能是 Artifactory 伺服器上可存取專用登錄及 npm 廣域登錄快取的虛擬登錄 URL。

1. 如果您使用的是 Artifactory Maven 儲存庫，請遵循下列步驟：

 a. 鍵入與您的儲存庫相關聯的使用者 ID。

 b. 鍵入與您的儲存庫相關聯的密碼。

 c. 鍵入 Artifactory 版本儲存庫的 URL，這是您在 Artifactory 伺服器上的專用版本儲存庫。

 d. 鍵入 Artifactory Snapshot 儲存庫的 URL，這是您在 Artifactory 伺服器上的專用 Snapshot 儲存庫。

 e. 鍵入您用來結合多個公用及專用 Maven 儲存庫的「鏡映」或「公用」儲存庫 URL。例如，此 URL 可能是 Artifactory 伺服器上可存取專用儲存庫及 Maven 中央儲存庫快取的虛擬儲存庫 URL。

1. 按一下**建立整合**。
1. 按一下您要使用的 Artifactory 儲存庫卡片。即會開啟 Artifactory 網站，您可以在其中檢視儲存庫的內容。
1. 選用項目：如果您是在 {{site.data.keyword.Bluemix_notm}} Public 上使用工具鏈，並且想要透過搭配使用 Artifactory 與 npm 來建置應用程式，請配置管線來新增 npm 建置工作。如需配置建置工作的指示，請參閱[在管線中配置 Artifactory npm 建置工作](#config_artifactory_npm)一節。
1. 選用項目：如果您是在 {{site.data.keyword.Bluemix_notm}} Public 上使用工具鏈，並且想要透過搭配使用 Artifactory 與 Maven 來建置應用程式，請配置管線來新增 Maven 建置工作。如需配置建置工作的指示，請參閱[在管線中配置 Artifactory Maven 建置工作](#config_artifactory_maven)一節。

### 在管線中配置 Artifactory npm 建置工作
{: #config_artifactory_npm}

您必須具有可使用建置 SCM 儲存庫作為輸入的可運作管線，而且必須為工具鏈配置 Artifactory，然後才能在管線中配置 npm 建置工作。如需配置 Artifactory 的指示，請參閱 [Artifactory](#artifactory) 一節。

配置 {{site.data.keyword.deliverypipeline}} 來新增 npm 建置工作：

1. 建立階段，並設定適當 SCM 儲存庫的輸入。
1. 在此階段上，新增建置工作。
1. 配置建置工作：![npm 建置工作](images/artifactory_npm_job.png)

  a. 針對建置器類型，選取 **NPM 建置**。

  b. 如果您已配置多個 Artifactory 工具整合實例，請輸入您要為其配置 npm 建置工作之 Artifactory 工具整合的名稱。

  c. 針對工具整合類型，選取 **Artifactory**。

  d. 針對建置指令，輸入指令來建置 npm 模組或將它發佈至登錄。此範例顯示用來建置或發佈模組的指令。
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  您可以在 Artifactory 工具整合的配置設定中，找到用來連接至登錄的 URL 及使用者認證。
  {: tip}

  e. 如果您的建置工作發佈至 Artifactory 登錄，而且 Node 模組版本的格式為 `x.y.z-SNAPSHOT.w`，請選取**增加 Snapshot 模組版本**勾選框。建置工作會自動更新模組版本，然後才將工作發佈至 Artifactory 登錄。工作會從 npm 登錄及本端 `package.json` 檔案中選取最高版本的模組，並使用 semver 來增加模組版本。建置工作不會將變更遞送至 SCM 儲存庫。

1. 按一下**儲存**。只要管線執行，此建置工作就會使用 Artifactory 工具整合中的配置資訊來連接至 npm 登錄。

### 在管線中配置 Artifactory Maven 建置工作
{: #config_artifactory_maven}

您需要有可使用建置 SCM 儲存庫作為輸入的可運作管線，而且必須為工具鏈配置 Artifactory，然後才能在管線中配置 Maven 建置工作。如需配置 Artifactory 的指示，請參閱 [Artifactory](#artifactory) 一節。

配置 {{site.data.keyword.deliverypipeline}} 來新增 Maven 建置工作：

1. 建立階段，並設定適當 SCM 儲存庫的輸入。
1. 在此階段上，新增建置工作。
1. 配置建置工作：![Maven 建置工作](images/artifactory_maven_job.png)

  a. 針對建置器類型，選取 **Maven 建置**。

  b. 如果您已配置多個 Artifactory 工具整合實例，請輸入您要為其配置 Maven 建置工作之 Artifactory 工具整合的名稱。

  c. 針對工具整合類型，選取 **Artifactory**。

  d. 針對建置指令，輸入指令來建置 Maven 模組或將它發佈至 Snapshot 登錄。此範例顯示用來建置模組或將它發佈至 Snapshot 登錄的指令。
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  您可以在 Artifactory 工具整合的配置設定中，找到用來連接至登錄的 URL 及使用者認證。
  {: tip}

1. 按一下**儲存**。只要管線執行，此建置工作就會使用 Artifactory 工具整合中的配置資訊來連接至 Maven 儲存庫。

### 進一步瞭解 Artifactory

若要進一步瞭解 Artifactory，請參閱 IBM Cloud Garage Method 上的 [Artifactory 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/deliver/tool_artifactory/){: new_window}。


## 新增 Availability Monitoring
{: #availabilitymonitoring}

{{site.data.keyword.prf_hublong}} 可在影響使用者之前隔離問題、識別型樣，以及改善效能。您可以從世界各地測試應用程式、與各交付管線整合，以及瞭解如何持續最佳化程式碼。

這是預先配置的工具整合，且不需要任何配置參數。您無法重新配置此工具整合。
{: tip}

若要在建置應用程式時測試、監視及改善應用程式的性能，請新增 {{site.data.keyword.prf_hubshort}} 工具整合：

1. 在 DevOps 儀表板的「工具鏈」頁面上，按一下要新增 {{site.data.keyword.prf_hubshort}} 的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **{{site.data.keyword.prf_hubshort}}**。

1. 按一下**建立整合**。
1. 按一下 **{{site.data.keyword.prf_hubshort}}**，以開啟 {{site.data.keyword.prf_hubshort}} 儀表板、選取應用程式，以及配置監視應用程式。

### 進一步瞭解 Availability Monitoring

若要進一步瞭解 {{site.data.keyword.prf_hubshort}}，請參閱 IBM Cloud Garage Method 上的 [{{site.data.keyword.prf_hublong}} 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/manage/tool_bluemix_availability_monitoring/){: new_window}，或採用下列指導教學：

  * [使用 {{site.data.keyword.Bluemix_notm}} Availability Monitoring 及 Alert Notification 來管理 {{site.data.keyword.Bluemix_notm}} 應用程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:new_window}


## 配置 Bitbucket
{: #bitbucket}

在 bitbucket.org 的新的或現有儲存庫中儲存原始碼，並透過 Wiki、問題追蹤及取回要求來參與社交編碼。

配置 Bitbucket 以與團隊對程式碼進行分工合作：

1. 從 DevOps 儀表板中，按一下**工具鏈**。按一下要新增 Bitbucket 的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Bitbucket**。

   如果您要在 {{site.data.keyword.Bluemix_notm}} Public 上配置此工具整合，但未授權 {{site.data.keyword.Bluemix_notm}} 存取 Bitbucket，請按一下**授權**來移至 Bitbucket 網站。如果您沒有作用中的 Bitbucket 階段作業，則系統會提示您登入。按一下**授與存取權**，以容許「{{site.data.keyword.Bluemix_notm}} 工具鏈」存取 Bitbucket 帳戶的下列部分：
   
   * **讀取帳戶資訊**。取得基本使用者資訊來移入使用者介面。
   
   * **讀取及修改儲存庫的問題**。容許 {{site.data.keyword.contdelivery_short}} 更新問題，指出管線何時部署連接至這些問題的確定。 
   
   * **讀取團隊專案設定，並讀取團隊專案內所含的儲存庫**。容許 {{site.data.keyword.contdelivery_short}} 與團隊所擁有的儲存庫整合。
   
   * **讀取及修改儲存庫和其取回要求**。容許 {{site.data.keyword.contdelivery_short}} 在使用者要求程式碼時將範例程式碼推送至儲存庫。
   
   * **管理儲存庫**。容許 {{site.data.keyword.contdelivery_short}} 在使用者要求時建立新的儲存庫。
   
   * **讀取團隊成員資格資訊**。容許 {{site.data.keyword.contdelivery_short}} 在建立新儲存庫時所顯示的**擁有者**功能表中顯示團隊清單。
   
   * **讀取及修改儲存庫的 Webhook**。容許管線在將確定推送至儲存庫時觸發建置。
   {: tip}
   
   如果您有作用中的 Bitbucket 階段作業，但最近未輸入過密碼，則系統可能會提示您輸入 Bitbucket 密碼進行確認。

1. 按一下您要使用的 Bitbucket 伺服器。
1. 如果您有想要使用的 Bitbucket 儲存庫，請鍵入儲存庫的 URL。針對儲存庫類型，請按一下**現有**。
1. 如果您要使用新的 Bitbucket 儲存庫，請鍵入儲存庫的名稱，並鍵入您所複製或分出之儲存庫的 URL，然後選取儲存庫類型：

 a. 若要建立空的儲存庫，請按一下**新建**。

 b. 若要建立儲存庫的副本，請按一下**複製**。

 c. 若要分出儲存庫，以透過取回要求來提出變更，請按一下**分出**。

1. 若要在伺服器上建立專用儲存庫，請選取**將此儲存庫設為專用**勾選框。
1. 若要使用 Bitbucket Issues 進行問題追蹤，請選取**啟用 Bitbucket Issues** 勾選框。
1. 若要透過建立確定的標籤和註解以及確定所參照之問題的標籤和註解來追蹤程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。如需相關資訊，請參閱[使用工具鏈追蹤程式碼的部署位置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 按一下**建立整合**。
1. 從工具鏈中，按一下您要使用的 Bitbucket 儲存庫卡片。即會開啟 Bitbucket 網站，您可以在其中檢視儲存庫的內容。
1. 如果您已啟用 Bitbucket Issues，請按一下 **Bitbucket Issues** 將它開啟。您可以將此 Bitbucket Issues 實例用於整個工具鏈，即使工具鏈包含多個 Bitbucket 儲存庫也是一樣。    

如果您沒有要鏈結之儲存庫的擁有者或主要專用權，則整合會受到限制，因為您無法使用 Webhook。需要有 Webhook，才能在將確定推送至儲存庫時自動執行管線。如果沒有 Webhook，您必須手動啟動管線。
{: tip}

### 進一步瞭解 Bitbucket

若要進一步瞭解 Bitbucket，請參閱 IBM Cloud Garage Method 上的 [Bitbucket 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/code/tool_bitbucket/){: new_window}。


## 新增 Cloud Event Management
{: #cloudeventmanagement}

{{site.data.keyword.evtmgt_full}} 提供服務、應用程式及基礎架構所發生問題的合併視圖。您可以設定即時突發事件管理，以更有效率地解決問題。

這是預先配置的工具整合，且不需要任何配置參數。您無法重新配置。
{: tip}

若要協助 DevOps 團隊達成可靠的操作性能、服務品質及持續改善目標，請將 Cloud Event Management 新增至工具鏈：

1. 從 DevOps 儀表板中，按一下**工具鏈**。按一下要新增 Cloud Event Management 的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Cloud Event Management**。

1. 按一下**建立整合**。
1. 從工具鏈中，按一下下列任何工具卡片：

 * **Cloud Event Management**，以開始使用 Cloud Event Management。

 * **{{site.data.keyword.alertnotificationshort}}**，以建立原則來判斷使用者何時收到突發事件通知。

 * **Runbook Automation**，以在 Cloud Event Management 中管理 Runbook 型錄。

### 進一步瞭解 Cloud Event Management

若要進一步瞭解 Cloud Event Management，請參閱 IBM Cloud Garage Method 上的 [Cloud Event Management 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){: new_window}。


## 配置 Delivery Pipeline
{: #deliverypipeline}

{{site.data.keyword.deliverypipeline}} 會透過一系列擷取輸入並執行工作（例如建置、測試及部署）的階段，來自動進行專案的持續部署。

配置 {{site.data.keyword.deliverypipeline}} 來自動進行應用程式的持續建置、測試及部署：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **{{site.data.keyword.deliverypipeline}}**。視您使用的範本而定，可能會有不同的欄位。請檢閱預設欄位值，並在必要時變更那些設定。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **{{site.data.keyword.deliverypipeline}}**。

1. 指定新管線的名稱。
1. 如果您計劃使用管線來部署使用者介面，請選取**在「檢視應用程式」功能表中顯示應用程式**勾選框。管線所建立的所有應用程式都會顯示在工具鏈之「概觀」頁面的**檢視應用程式**清單中。
1. 按一下**建立整合**，以將 {{site.data.keyword.deliverypipeline}} 新增至您的工具鏈。
1. 按一下 **{{site.data.keyword.deliverypipeline}}**，以檢視管線並進行配置。若要瞭解如何配置管線的基本觀念，請參閱[建置及部署管線](/docs/services/ContinuousDelivery/pipeline_build_deploy.html){: new_window}。

  如果您要在將確定推送至 GitHub、{{site.data.keyword.ghe_short}} 或 Git 儲存庫時自動執行管線，請遵循下列步驟：

   a. 先配置工具鏈的 GitHub、{{site.data.keyword.ghe_short}} 或 {{site.data.keyword.gitrepos}}，然後再定義管線的階段。管線階段需要儲存庫的 Git URL。每一個管線階段都只能參照與您工具鏈相關聯的其中一個 GitHub、{{site.data.keyword.ghe_short}} 或 Git 儲存庫。如需配置 GitHub 的指示，請參閱 [GitHub](#github) 一節。如需配置 Dedicated {{site.data.keyword.ghe_short}} 的指示，請參閱[開始使用 {{site.data.keyword.ghe_long}}](/docs/services/ghededicated/index.html){: new_window}。如需配置 {{site.data.keyword.gitrepos}} 的指示，請參閱 [{{site.data.keyword.gitrepos}}](#gitbluemix) 一節。

   b. 使用 Webhook。如果沒有 Webhook，您只能手動執行管線。若要在鏈結至 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫時使用 Webhook，您需要管理者專用權。若要鏈結至 {{site.data.keyword.gitrepos}} 儲存庫，您需要「主要」或「擁有者」專用權。

1. 選用項目：如果您是在 {{site.data.keyword.Bluemix_notm}} Public 上使用工具鏈，並且想要 Sauce Labs 對您的應用程式執行測試，請配置 {{site.data.keyword.deliverypipeline}} 來新增 Sauce Labs 測試工作。如需配置測試工作的指示，請參閱[在管線中配置 Sauce Labs 測試工作](#config_saucelabs)一節。

### 在管線中配置 Sauce Labs 測試工作
{: #config_saucelabs}

您需要可運作的管線，其中包含階段可建置及部署應用程式，而且您必須為工具鏈配置 Sauce Labs，然後才在管線中配置 Sauce Labs 測試工作。如需配置 Sauce Labs 的指示，請參閱 [Sauce Labs](#saucelabs) 一節。

配置 {{site.data.keyword.deliverypipeline}} 來新增 Sauce Labs 測試工作：

1. 如果您沒有可部署您應用程式之測試版本的階段，請建立一個。
1. 在此階段上，於部署工作之後新增測試工作。將這些工作放在相同的階段中，它們即可存取一組相同的環境內容。
     
  ![測試工作](images/toolchain_test_job.png)

1. 配置階段。在**環境內容**標籤上，建立 CF_APP_NAME 內容。

  在與 SAUCE_USERNAME 及 SAUCE_ACCESS_KEY 環境變數相同的測試工作 Script 中，提供 Sauce Labs 使用者名稱及存取金鑰。當您撰寫測試時，必須使用這些環境變數向 Sauce Labs 進行鑑別。
  {: tip}

1. 配置部署工作。在**部署 Script** 欄位中，納入下列指令：`export CF_APP_NAME="$CF_APP"`。該指令會將應用程式名稱匯出為環境內容。
1. 配置測試工作。下列影像中的值是範例。**服務實例**、**目標**、**組織**及**空間**欄位會移入您正在使用的 Sauce Labs 使用者名稱、地區、組織及空間。
  
![配置工作](images/toolchain_configure_job.png)

  a. 針對測試器類型，選取 **Sauce Labs**。

  b. 針對服務實例，選取您為工具鏈配置 Sauce Labs 時所使用的 Sauce Labs 使用者名稱。

   若要查看您為工具鏈配置 Sauce Labs 時所使用的使用者名稱和存取金鑰，請按一下**配置**。
   {: tip}

  c. 在**測試執行指令**欄位中，輸入安裝測試所需相依關係的指令，然後執行測試。例如，針對 Node.js 應用程式，您可以輸入下列指令：
     ```
     npm install
     node_modules/grunt-cli/bin/grunt test:sauce:parallel
     ```

    d. 如果您要在測試工作日誌中查看測試報告，請選取**啟用測試報告**勾選框，然後將「測試結果檔案型樣」設為 `test/*.xml`。

1. 按一下**儲存**。只要執行管線，就會執行 Sauce Labs 測試。

### 進一步瞭解 Delivery Pipeline

若要進一步瞭解 {{site.data.keyword.deliverypipeline}}，請參閱[使用管線](/docs/services/ContinuousDelivery/pipeline_working.html){: new_window}以及 IBM Cloud Garage Method 上的 [Delivery Pipeline 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/deliver/tool_delivery_pipeline/){: new_window}，或採用下列指導教學：

  * [建立管線 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/create-a-pipeline){:new_window}

  * [使用「開發 Cloud Foundry 應用程式」工具鏈建立及使用您的第一個工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}


## 新增 DevOps Insights（測試版）
{: #dra}

{{site.data.keyword.DRA_full}} 會收集並分析單元測試、功能測試及程式碼涵蓋面工具的結果，來判定您的程式碼是否符合部署程序中所指定閘門的預先定義準則。如果程式碼不符合或超出準則，則會停止部署，以防止釋出風險。您可以使用 {{site.data.keyword.DRA_short}} 作為持續交付環境的安全網，或作為實作並改善品質標準的方法。

 此工具整合僅適用於 {{site.data.keyword.Bluemix_notm}} Public。它是預先配置的，且不需要任何配置參數。您無法重新配置此工具整合。
 {: tip}

新增 {{site.data.keyword.DRA_short}} 來維護及改善 {{site.data.keyword.Bluemix_notm}} 中的程式碼品質，方法是監視部署，以在釋出之前先找出風險。

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **{{site.data.keyword.DRA_short}}**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **{{site.data.keyword.DRA_short}}**。

1. 按一下**建立整合**。
1. 按一下 **{{site.data.keyword.DRA_short}}**，然後完成開始使用步驟：建立準則，並將準則連接至管線，然後執行管線。

### 進一步瞭解 DevOps Insights

若要進一步瞭解 {{site.data.keyword.DRA_short}}，請參閱 IBM Cloud Garage Method 上的 [{{site.data.keyword.DRA_short}} 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/learn/tool_devops_insights/){: new_window}，或採用下列指導教學：

  * [使用「開發及測試 Cloud Foundry 應用程式」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:new_window}

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [使用「搭配 GitHub 和 Jenkins 的 Deployment Risk Analytics」工具鏈確定品質部署 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}


## 新增 Eclipse Orion Web IDE
{: #webide}

Eclipse Orion {{site.data.keyword.webide}} 是一個整合的 Web 型環境，您可以在其中建立、編輯、執行、除錯以及完成來源控制作業。您可以平順地依序從編輯移至執行、提交、部署。

 這是預先配置的工具整合。它不需要任何配置參數，而且您無法重新配置它。
 {: tip}

若要完成來源控制作業，請新增 Eclipse Orion {{site.data.keyword.webide}} 工具整合：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Eclipse Orion {{site.data.keyword.webide}}**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Eclipse Orion {{site.data.keyword.webide}}**。

1. 按一下**建立整合**。
1. 按一下 **Eclipse Orion {{site.data.keyword.webide}}**。您的工作區會預先移入您的 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫。會強調顯示與現行工具鏈相關聯的儲存庫。

### 進一步瞭解 Eclipse Orion Web IDE

若要進一步瞭解 Eclipse Orion {{site.data.keyword.webide}}，請參閱[使用 Eclipse Orion {{site.data.keyword.webide}} 編輯程式碼](/docs/services/ContinuousDelivery/web_ide.html){: new_window}以及 IBM Cloud Garage Method 上的 [Eclipse Orion {{site.data.keyword.webide}} 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/code/tool_eclipse_orion_web_ide/){: new_window}，或採用下列指導教學：

  * [使用「開發 Cloud Foundry 應用程式」工具鏈建立及使用您的第一個工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}


## 配置 Git Repos and Issue Tracking
{: #gitbluemix}

{{site.data.keyword.gitrepos}} 工具整合是根據 GitLab Community Edition，其為 Git 儲存庫的 Web 型管理服務。您可以同時具有儲存庫的本端及遠端副本。若要進一步瞭解，請參閱 [{{site.data.keyword.gitrepos}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help){:new_window}。

如果您要在建立工具鏈時配置 {{site.data.keyword.gitrepos}}，請遵循下列步驟：    

1. 在「可配置的整合」區段中，按一下 **Git Repos and Issue Tracking**。
1. 檢閱 Git 儲存庫的預設目標位置。那些儲存庫是從範例儲存庫中複製而來。必要的話，請變更目標儲存庫的名稱。
 

如果您有工具鏈，並且要將工具鏈中的 Git 儲存庫移轉至 {{site.data.keyword.gitrepos}}，請遵循下列步驟：

這些指示適用於已包含您要移轉至 {{site.data.keyword.gitrepos}} 的 Git 儲存庫的工具鏈。如需將不同類型的 Git 儲存庫新增至工具鏈的相關資訊，請參閱[配置 GitHub](#github)、[在 {{site.data.keyword.Bluemix_notm}} Dedicated 上配置 GitHub Enterprise 及 Issues](#configghe) 及[配置 GitLab](#gitlab) 小節。
{: tip}

1. 在 DevOps 儀表板的「工具鏈」頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下**新增工具**。
1. 在「工具整合」區段中，按一下 **Git Repos and Issue Tracking**。
1. 若要建立 Git 儲存庫的副本，請針對儲存庫類型按一下**複製**。鍵入新的儲存庫名稱，以及來源儲存庫的 URL。
1. 如果您要使用 Issues 進行問題追蹤，請選取**啟用 Issues** 勾選框。
1. 如果您要透過建立確定的標籤和註解以及確定所參照之問題的標籤和註解來追蹤程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。如需相關資訊，請參閱[使用工具鏈追蹤程式碼的部署位置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 按一下**建立整合**。

在您複製 Git 儲存庫之後，即可從工具鏈中將它移除。
{: tip}

如果您有工具鏈，並要向其新增 {{site.data.keyword.gitrepos}}，請遵循下列步驟：    

1. 在 DevOps 儀表板的「工具鏈」頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下**新增工具**。
1. 在「工具整合」區段中，按一下 **Git Repos and Issue Tracking**。
1. 選取儲存庫類型：     

  a. 若要建立空的儲存庫，請針對儲存庫類型按一下**新建**，然後鍵入儲存庫名稱。    
  b. 若要分出 Git 儲存庫，以透過合併要求來提出變更，請針對儲存庫類型按一下**分出**。鍵入來源儲存庫的 URL。    
  c. 若要建立 Git 儲存庫的副本，請針對儲存庫類型按一下**複製**。鍵入新的儲存庫名稱，以及來源儲存庫的 URL。     
  d. 如果您有 Git 儲存庫並且想要使用它，請針對儲存庫類型按一下**現有**。鍵入 URL。    

1. 如果您要使用 Issues 進行問題追蹤，請選取**啟用 Issues** 勾選框。
1. 如果您要透過建立確定的標籤和註解以及確定所參照之問題的標籤和註解來追蹤程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。如需相關資訊，請參閱[使用工具鏈追蹤程式碼的部署位置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 按一下**建立整合**。
1. 按一下您要使用的 Git 儲存庫卡片。即會開啟您的專案概觀頁面。    

如果您沒有要鏈結之儲存庫的「主要」或「擁有者」專用權，則整合會受到限制，因為您無法使用 Webhook。需要有 Webhook，才能在將確定推送至儲存庫時自動執行管線。如果沒有 Webhook，您必須手動啟動管線。
{: tip}

### 進一步瞭解 Git Repos and Issue Tracking

若要進一步瞭解 {{site.data.keyword.gitrepos}}，請參閱 IBM Cloud Garage Method 上的 [{{site.data.keyword.gitrepos}}：IBM 所管理的社交編碼文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/code/tool_git_repos_and_issue_tracking/){: new_window}，或採用下列指導教學：

  * [使用「開發 Cloud Foundry 應用程式」工具鏈建立及使用您的第一個工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}


## 配置 GitHub
{: #github}

GitHub 是 Git 儲存庫的 Web 型管理服務。您可以同時具有儲存庫的本端和遠端副本，方便進行分工合作。

{{site.data.keyword.ghe_short}} 是 Git 儲存庫的內部部署 Web 型管理服務。

GitHub Issues 是一項追蹤工具，可將您的工作和方案都保留在一個位置。它與您的開發儲存庫整合，因此您可以專注於重要作業。

您可以將 GitHub 配置為工具鏈中的工具整合，以在 GitHub.com 或公司 {{site.data.keyword.ghe_short}} 實例的新或現有儲存庫中管理原始碼。透過 Wiki、問題追蹤及取回要求來參與社交編碼。

如果您要在建立工具鏈時配置此工具整合，請遵循下列步驟：

1. 如果您是將原始碼儲存至 GitHub 儲存庫，請按一下「可配置的整合」區段中的 **GitHub**。如果您要在 {{site.data.keyword.Bluemix_notm}} Public 上配置此工具整合，但未授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub，請按一下**授權**來移至 GitHub 網站。如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。如果您有作用中的 GitHub 階段作業，但最近未輸入過密碼，則系統可能會提示您輸入 GitHub 密碼進行確認。
1. 如果您要在自己的 {{site.data.keyword.ghe_short}} 伺服器上使用儲存庫，請按一下「可配置的整合」區段中的**新增自訂伺服器**。

 網路必須可以從 {{site.data.keyword.Bluemix_notm}} Dedicated 環境存取目標 Git 伺服器。如果您的 GitHub 伺服器無法在公用網際網路上使用，或在公用「網域名稱伺服器 (DNS)」上無法解析主機名稱，請[開立支援問題單](/docs/services/ContinuousDelivery/cd_support.html#support-ticket){: new_window}。您可以使用支援問題單來提交開啟網路路徑或更新 DNS 設定的要求。
 {: tip}

 鍵入自訂 GitHub 伺服器的標題，然後指定伺服器的根 URL。輸入個人存取記號，然後按一下**儲存自訂整合**。

  如果您沒有個人存取記號，則可以建立個人存取記號：

     a. 在任何 GitHub 頁面上，按一下設定檔圖示，然後按一下**設定**。

     b. 在資訊看板上，按一下**個人存取記號**。

     c. 按一下**產生新記號**。

     d. 新增記號的說明。

     e. 選取**儲存庫**及**使用者**勾選框，以定義個人記號的存取權。

     f. 按一下**產生記號**。

     g. 將記號複製到安全位置或密碼管理應用程式。基於安全考量，在您離開此頁面之後，就無法再看到記號。

1. 檢閱 GitHub 儲存庫的預設目標儲存庫位置。那些儲存庫是從範例儲存庫中複製而來。必要的話，請變更目標儲存庫的名稱。![預設目標儲存庫位置](images/toolchain_github_config.png)

如果您有工具鏈，並要向其新增此工具整合，請遵循下列步驟：

1. 在 DevOps 儀表板的「工具鏈」頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下**新增工具**。
1. 在「工具整合」區段中，按一下 **GitHub**。
1. 按一下您要使用的 GitHub 伺服器。
1. 如果您有 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫並且想要使用它，請針對儲存庫類型按一下**現有**，然後鍵入 URL。
1. 如果您要使用新的 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫，請鍵入儲存庫的名稱，並鍵入您所複製或分出之儲存庫的 URL，然後選取儲存庫類型：

 a. 若要建立空的儲存庫，請按一下**新建**。

 b. 若要建立 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫的副本，請按一下**複製**。

 c. 若要分出 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫，以透過取回要求來提出變更，請按一下**分出**。

1. 如果您是具有已升級帳戶的 GitHub.com 使用者，或已選取 {{site.data.keyword.ghe_short}} 伺服器，並且要在伺服器上製作新的專用儲存庫，請選取**將此儲存庫設為專用**勾選框。
1. 如果您要使用 GitHub Issues 進行問題追蹤，請選取**啟用 GitHub Issues** 勾選框。
1. 如果您要透過建立確定的標籤和註解以及確定所參照之問題的標籤和註解來追蹤程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。如需相關資訊，請參閱[使用工具鏈追蹤程式碼的部署位置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 按一下**建立整合**。
1. 按一下您要使用的 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫卡片。根據您已選取的儲存庫，會開啟 GitHub 網站或公司的 {{site.data.keyword.ghe_short}} 儲存庫，您可以在其中檢視儲存庫的內容。

  您可以使用 Eclipse Orion {{site.data.keyword.webide}} 中的整合原始碼管理工具來編輯 GitHub 儲存庫，以及從工作區中部署應用程式。
  {: tip}

1. 如果您已啟用 GitHub Issues，請按一下 **GitHub Issues** 將它開啟。您可以將此 GitHub Issues 實例用於整個工具鏈，即使工具鏈包含多個 GitHub 或 {{site.data.keyword.ghe_short}} 儲存庫。    

如果您沒有要鏈結之儲存庫的管理者專用權，則整合會受到限制，因為您無法使用 Webhook。需要有 Webhook，才能在將確定推送至儲存庫時自動執行管線。如果沒有 Webhook，您必須手動啟動管線。
{: tip}

### 進一步瞭解 GitHub

若要進一步瞭解 GitHub，請參閱 IBM Cloud Garage Method 上的 [GitHub 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/code/tool_github/){: new_window} 及 [GitHub Issues 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: new_window}，或採用下列指導教學：

 * [使用「開發及測試 Cloud Foundry 應用程式」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:new_window}

  * [使用「搭配 GitHub 和 Jenkins 的 Deployment Risk Analytics」工具鏈確定品質部署 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}

  * [建立自訂工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain){:new_window}
## 在 {{site.data.keyword.Bluemix_notm}} Dedicated 上配置 GitHub Enterprise 及 Issues
{: #configghe}

 這些指示適用於 {{site.data.keyword.Bluemix_notm}} Dedicated for {{site.data.keyword.ghe_short}}。如果您使用的是專屬受管理版本的 {{site.data.keyword.ghe_short}}，則視內部程序而定，有些步驟可能會有所不同。
 {: tip}

{{site.data.keyword.ghe_long}} 是 Git 儲存庫的內部部署 Web 型管理服務。Dedicated {{site.data.keyword.ghe_short}} 僅供 {{site.data.keyword.Bluemix_notm}} Dedicated 客戶使用。GitHub Issues 是一項追蹤工具，可將您的工作和方案都保留在一個位置。它與您的開發儲存庫整合，因此您可以專注於重要作業。如需 Dedicated {{site.data.keyword.ghe_short}} 及 GitHub Issues 的相關資訊，請參閱[開始使用 {{site.data.keyword.ghe_long}}](/docs/services/ghededicated/index.html){: new_window} 和 IBM Cloud Garage Method 上的 [GitHub Issues 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: new_window}。

您可以將 {{site.data.keyword.ghe_short}} 配置為工具鏈中的工具整合，以在公司的 [{{site.data.keyword.Bluemix_notm}} Dedicated](/docs/dedicated/index.html#dedicated){: new_window} 實例中管理原始碼。

1. 如果您要在建立工具鏈時配置此工具整合，請遵循下列步驟：

 a. 第一次登入 Dedicated {{site.data.keyword.ghe_short}} 之前，請要求公司的地區管理者使用 LDAP 將您的使用者 ID 從公司的使用者登錄新增至 {{site.data.keyword.Bluemix_notm}} Dedicated 實例。如需設定 {{site.data.keyword.ghe_short}} 帳戶的相關資訊，請參閱[開始使用 {{site.data.keyword.ghe_long}}](/docs/services/ghededicated/index.html){: new_window}。

 b. 在「可配置的整合」區段中，按一下 **{{site.data.keyword.ghe_short}}**。    

 c. 檢閱新 {{site.data.keyword.ghe_short}} 儲存庫的預設名稱。必要的話，請變更新儲存庫的名稱。下列影像顯示從範例儲存庫複製的儲存庫範例。您可以使用現有儲存庫或新儲存庫。若要使用新的儲存庫，您可以建立空的儲存庫、複製儲存庫，或分出儲存庫。![預設儲存庫位置](images/toolchain_ghe_config.png)

1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **{{site.data.keyword.ghe_short}}**。

1. 如果您有想要使用的 {{site.data.keyword.ghe_short}} 儲存庫，請鍵入儲存庫的 URL。針對儲存庫類型，請按一下**現有**。
1. 如果您要使用新的 {{site.data.keyword.ghe_short}} 儲存庫，請鍵入儲存庫的名稱，並鍵入您所複製或分出之儲存庫的 URL，然後選取儲存庫類型：

 a. 若要建立空的儲存庫，請按一下**新建**。

 b. 若要建立儲存庫的副本，請按一下**複製**。

 c. 若要分出儲存庫，以透過取回要求來提出變更，請按一下**分出**。

1. 若要使用 GitHub Issues 進行問題追蹤，請選取**啟用 GitHub Issues** 勾選框。
1. 按一下**建立整合**。
1. 按一下您要使用的 {{site.data.keyword.ghe_short}} 儲存庫卡片。即會開啟您公司的 {{site.data.keyword.ghe_short}} 儲存庫。

  您可以使用 Eclipse Orion {{site.data.keyword.webide}} 中的整合原始碼管理工具來編輯 {{site.data.keyword.ghe_short}} 儲存庫，以及從工作區中部署應用程式。
  {: tip}

1. 如果您已啟用 GitHub Issues，請按一下 **GitHub Issues**。您可以將此 GitHub Issues 實例用於整個工具鏈，即使工具鏈包含多個 GitHub 儲存庫。    

如果您沒有要鏈結之儲存庫的管理者專用權，則整合會受到限制，因為您無法使用 Webhook。需要有 Webhook，才能在將確定推送至儲存庫時自動執行管線。如果沒有 Webhook，您必須手動啟動管線。
{: tip}


## 配置 GitLab
{: #gitlab}

GitLab 是 Git 儲存庫的 Web 型管理服務。您可以同時具有儲存庫的本端和遠端副本，方便進行分工合作。

您可以將 GitLab 配置為工具鏈中的工具整合，以在 GitLab.com 或公司 GitLab 實例的新或現有儲存庫中管理原始碼。透過 Wiki、問題追蹤及合併要求來參與社交編碼。

如果您要在建立工具鏈時配置此工具整合，請遵循下列步驟：

1. 如果您是將原始碼儲存至 GitLab 儲存庫，請按一下「可配置的整合」區段中的 **GitLab**。如果您要在 {{site.data.keyword.Bluemix_notm}} Public 上配置此工具整合，但未授權 {{site.data.keyword.Bluemix_notm}} 存取 GitLab，請按一下**授權**來移至 GitLab 網站。如果您沒有作用中的 GitLab 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitLab 帳戶。如果您有作用中的 GitLab 階段作業，但最近未輸入過密碼，則系統可能會提示您輸入 GitLab 密碼進行確認。
1. 如果您要在自己的 GitLab 伺服器上使用儲存庫，請按一下「可配置的整合」區段中的**新增自訂伺服器**。

 網路必須可以從 {{site.data.keyword.Bluemix_notm}} Dedicated 環境存取目標 GitLab 伺服器。
 {: tip}

 鍵入自訂 GitLab 伺服器的標題，然後指定伺服器的根 URL。輸入個人存取記號，然後按一下**儲存自訂整合**。

  如果您沒有個人存取記號，則可以建立個人存取記號：

     a. 在任何 GitLab 頁面上，按一下設定檔圖示，然後按一下**設定**。

     b. 在「存取記號」頁面上，鍵入您要為其建立個人存取記號的應用程式名稱。

     c. 選用。選擇存取記號的到期日期。

     d. 選取 **api** 勾選框，以定義個人記號的存取權。

     e. 按一下**建立個人存取記號**。

     f. 將記號複製到安全位置或密碼管理應用程式。基於安全考量，在您離開此頁面之後，就無法再看到記號。

1. 檢閱 GitLab 儲存庫的預設目標儲存庫位置。那些儲存庫是從範例儲存庫中複製而來。必要的話，請變更目標儲存庫的名稱。
 

如果您有工具鏈，並要向其新增此工具整合，請遵循下列步驟：

1. 在 DevOps 儀表板的「工具鏈」頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下**新增工具**。
1. 在「工具整合」區段中，按一下 **GitLab**。
1. 按一下您要使用的 GitLab 伺服器。
1. 如果您有 GitLab 儲存庫並且想要使用它，請針對儲存庫類型按一下**現有**，然後鍵入 URL。
1. 如果您要使用新的 GitLab 儲存庫，請鍵入儲存庫的名稱，並鍵入您所複製或分出之儲存庫的 URL，然後選取儲存庫類型：

 a. 若要建立空的儲存庫，請按一下**新建**。

 b. 若要建立 GitLab 儲存庫的副本，請按一下**複製**。

 c. 若要分出 GitLab 儲存庫，以透過合併要求來提出變更，請按一下**分出**。

1. 如果您要在伺服器上建立公用儲存庫，請清除**將此儲存庫設為專用**勾選框。
1. 如果您要使用 GitLab Issues 進行問題追蹤，請選取**啟用 GitLab Issues** 勾選框。
1. 如果您要透過建立確定的標籤和註解以及確定所參照之問題的標籤和註解來追蹤程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。如需相關資訊，請參閱[使用工具鏈追蹤程式碼的部署位置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 按一下**建立整合**。
1. 按一下您要使用的 GitLab 儲存庫卡片。根據您已選取的儲存庫，會開啟 GitLab 網站或公司的 GitLab 儲存庫，您可以在其中檢視儲存庫的內容。

  您可以使用 Eclipse Orion {{site.data.keyword.webide}} 中的整合原始碼管理工具來編輯 GitLab 儲存庫，以及從工作區中部署應用程式。
  {: tip}

1. 如果您已啟用 GitLab Issues，請按一下 **GitLab Issues** 將它開啟。您可以將此 GitLab Issues 實例用於整個工具鏈，即使工具鏈包含多個 GitLab 儲存庫。    

如果您沒有要鏈結之儲存庫的擁有者或主要專用權，則整合會受到限制，因為您無法使用 Webhook。需要有 Webhook，才能在將確定推送至儲存庫時自動執行管線。如果沒有 Webhook，您必須手動啟動管線。
{: tip}

### 進一步瞭解 GitLab

若要進一步瞭解 GitLab，請參閱 IBM Cloud Garage Method 上的 [GitLab 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){: new_window}。


## 配置 Jenkins
{: #jenkins}

Jenkins 是一種可持續建置及測試軟體的開放程式碼、伺服器型工具，並支援持續整合及持續交付的作法。

您必須先有 Jenkins 伺服器，才能建立 Jenkins 工具整合。
{: tip}

使用 Jenkins 工具整合，您可以將 Jenkins 工作通知傳送至工具鏈中的其他工具（例如 Slack 及 PagerDuty）。若要在部署中追蹤程式碼，您可以將部署訊息新增至 Git 確定，以及相關的 Git 或 JIRA 問題。您也可以在「工具鏈連線」頁面上檢視部署。您可以將測試結果提供給 {{site.data.keyword.DRA_short}}，並新增自動化品質限制，然後追蹤部署風險。

配置 Jenkins 來自動進行應用程式的持續建置、測試及部署：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Jenkins**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Jenkins**。

1. 在工具鏈的 Jenkins 卡片上，鍵入要針對此工具整合顯示的名稱。
1. 鍵入當您從工具鏈按一下 Jenkins 卡片時所要開啟的 Jenkins 伺服器 URL。
1. 複製產生的工具鏈 Webhook。
1. 在 Jenkins 伺服器中，完成下列步驟：

 a. [安裝 IBM Cloud DevOps 外掛程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Installingtheplugin){: new_window}。

 b. [配置 Jenkins 通知工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Notifyingtoolchains){: new_window}。

 c. 回到 Jenkins 工具整合的「配置整合」頁面。

1. 按一下**建立整合**。
1. 從工具鏈中，按一下 **Jenkins** 以檢視 Jenkins 伺服器。  

### 進一步瞭解 Jenkins

若要進一步瞭解 Jenkins，請參閱 IBM Cloud Garage Method 上的 [Jenkins 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/deliver/tool_jenkins/){: new_window}，或採用下列指導教學：

  * [使用「搭配 GitHub 和 Jenkins 的 Deployment Risk Analytics」工具鏈確定品質部署 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}

## 配置 JIRA
{: #jira}

JIRA 是一個工具，可追蹤與您軟體相關的問題及錯誤。只要 Jenkins 或 {{site.data.keyword.deliverypipeline}} 執行部署，JIRA 工具整合就會更新專案的問題。若要讓 JIRA 工具整合追蹤問題，您必須在確定訊息中使用 JIRA Smart Commit。若要進一步瞭解 JIRA Smart Commit，請參閱[使用 Smart Commits ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://confluence.atlassian.com/fisheye/using-smart-commits-298976812.html){: new_window}。

配置 JIRA，以計劃、追蹤及交付優質程式碼：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **JIRA**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **JIRA**。

1. 如果您有 JIRA 專案，並且要與之連接，請針對 JIRA 類型按一下**現有**：

 a. 鍵入 JIRA 專案的 JIRA 專案索引鍵。您可以在 JIRA 專案的 URL 中找到專案索引鍵。

 b. 鍵入 JIRA 實例的基礎 API URL。您可以從 JIRA 實例的標頭中找到 API URL。按一下**管理**圖示，然後按一下**系統**。

 c. 如果您要連接至專用 JIRA 實例，或要接收來自公用 JIRA 實例的可追蹤性資訊，請輸入 JIRA 使用者名稱及密碼。

 d. 若要透過建立所參照問題的標籤及註解來追蹤專案的程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。請確定您使用 JIRA Smart Commit，以在 GitHub 確定中參照 JIRA Issues。如果您未選取此選項，則 JIRA 工具整合會忽略任何確定。

1. 如果您要建立 JIRA 專案，請針對 JIRA 類型按一下**新建**：

 a. 鍵入要用於新專案的 JIRA 專案索引鍵。此索引鍵用作專案 URL 中的唯一 ID。

 b. 鍵入 JIRA 專案的名稱。

 c. 鍵入 JIRA 實例的基礎 API URL。您可以從 JIRA 實例的標頭中找到 API URL。按一下**管理**圖示，然後按一下**系統**。

 d. 鍵入您要用於此專案之 JIRA 專案領導人的使用者名稱。若要將某個人指定為 JIRA 專案領導人，該人員必須具有 JIRA 中的專案領導人許可權。

 e. 鍵入此 JIRA 實例的管理者使用者名稱。

 f. 鍵入此 JIRA 實例的管理者密碼。

 g. 若要透過建立所參照問題的標籤及註解來追蹤專案的程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。請確定您使用 JIRA Smart Commit，以在 GitHub 確定中參照 JIRA Issues。如果您未選取此選項，則 JIRA 工具整合會忽略任何確定。

1. 按一下**建立整合**。
1. 從工具鏈中，按一下 **JIRA** 以檢視您已連接之 JIRA 專案的儀表板。

### 進一步瞭解 JIRA

若要進一步瞭解 JIRA，請參閱 IBM Cloud Garage Method 上的 [JIRA 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/code/tool_jira/){: new_window}，或採用下列指導教學：

  * [使用「搭配 GitHub 和 JIRA 的 Developer Insights 及 Team Dynamics」工具鏈進行瞭解 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain){:new_window}


## 配置 Nexus
{: #nexus}

配置「Nexus 儲存庫管理員」，以將建置構件儲存至 Nexus 儲存庫：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Nexus**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Nexus**。

1. 鍵入此 Nexus 工具整合實例的名稱。
1. 鍵入當您從工具鏈按一下 Nexus 卡片時所要開啟的 Nexus 儲存庫 URL。
1. 選取您要連接的儲存庫類型。
1. 如果您已選取 **npm 登錄**，請遵循下列步驟：

 a. 鍵入與您的登錄相關聯的電子郵件位址。

 b. 鍵入與您的登錄相關聯的鑑別記號。

 c. 鍵入 Nexus 版本儲存庫的 URL，這是您在 Nexus 伺服器上的專用登錄。

 d. 鍵入您用來結合多個公用及專用 npm 登錄的「鏡映」或「公用」登錄 URL。例如，此 URL 可能是 Nexus 伺服器上可存取專用登錄及 npm 廣域登錄快取的虛擬登錄 URL。

1. 如果您已選取 **Maven 儲存庫**，請遵循下列步驟：

 a. 鍵入與您的儲存庫相關聯的使用者 ID。

 b. 鍵入與您的儲存庫相關聯的密碼。

 c. 鍵入 Nexus 版本儲存庫的 URL，這是您在 Nexus 伺服器上的專用版本儲存庫。

 d. 鍵入 Nexus Snapshot 儲存庫的 URL，這是您在 Nexus 伺服器上的專用 Snapshot 儲存庫。

 e. 鍵入您用來結合多個公用及專用 Maven 儲存庫的「鏡映」或「公用」儲存庫 URL。例如，此 URL 可能是 Nexus 伺服器上可存取專用儲存庫及 Maven 中央儲存庫快取的虛擬儲存庫 URL。

1. 按一下**建立整合**。
1. 從工具鏈中，按一下您要使用的 Nexus 儲存庫卡片。即會開啟 Nexus 網站，您可以在其中檢視儲存庫的內容。
1. 選用項目：如果您是在 {{site.data.keyword.Bluemix_notm}} Public 上使用工具鏈，並且想要透過搭配使用 Nexus 與 npm 來建置應用程式，請配置管線來新增 npm 建置工作。如需配置建置工作的指示，請參閱[在管線中配置 Nexus npm 建置工作](#config_nexus_npm)一節。
1. 選用項目：如果您是在 {{site.data.keyword.Bluemix_notm}} Public 上使用工具鏈，並且想要透過搭配使用 Nexus 與 Maven 來建置應用程式，請配置管線來新增 Maven 建置工作。如需配置建置工作的指示，請參閱[在管線中配置 Nexus Maven 建置工作](#config_nexus_maven)一節。

### 在管線中配置 Nexus npm 建置工作
{: #config_nexus_npm}

您需要有可使用建置 SCM 儲存庫作為輸入的可運作管線，而且必須為工具鏈配置 Nexus，然後才能在管線中配置 npm 建置工作。如需配置 Nexus 的指示，請參閱 [Nexus](#nexus) 一節。

配置 {{site.data.keyword.deliverypipeline}} 來新增 npm 建置工作：

1. 建立階段，並設定適當 SCM 儲存庫的輸入。
1. 在此階段上，新增建置工作。
1. 配置建置工作：![npm 建置工作](images/nexus_npm_job.png)

  a. 針對建置器類型，選取 **NPM 建置**。

  b. 如果您已配置多個 Nexus 工具整合實例，請輸入您要配置 npm 建置工作之 Nexus 工具整合的名稱。

  c. 針對工具整合類型，選取 **Nexus**。

  d. 針對建置指令，輸入指令來建置 npm 模組或將它發佈至登錄。此範例顯示用來建置或發佈模組的指令。
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  **提示：**您可以在 Nexus 工具整合的配置設定中，找到用來連接至登錄的 URL 及使用者認證。



  e. 如果您的建置工作發佈至 Nexus 登錄，而且 Node 模組版本的格式為 `x.y.z-SNAPSHOT.w`，請選取**增加 Snapshot 模組版本**勾選框。建置工作會自動更新模組版本，然後才將工作發佈至 Nexus 登錄。建置工作會從 npm 登錄及本端 `package.json` 檔案中選取最高版本的模組，並使用 semver 來增加模組版本。建置工作不會將變更遞送至 SCM 儲存庫。

1. 按一下**儲存**。只要管線執行，此建置工作就會使用 Nexus 工具整合中的配置資訊來連接至 npm 登錄。

### 在管線中配置 Nexus Maven 建置工作
{: #config_nexus_maven}

您需要有可使用建置 SCM 儲存庫作為輸入的可運作管線，而且必須為工具鏈配置 Nexus，然後才能在管線中配置 Maven 建置工作。如需配置 Nexus 的指示，請參閱 [Nexus](#nexus) 一節。

配置 {{site.data.keyword.deliverypipeline}} 來新增 Maven 建置工作：

1. 建立階段，並設定適當 SCM 儲存庫的輸入。
1. 在此階段上，新增建置工作。
1. 配置建置工作：![Maven 建置工作](images/nexus_maven_job.png)

  a. 針對建置器類型，選取 **Maven 建置**。

  b. 如果您已配置多個 Nexus 工具整合實例，請輸入您要配置 Maven 建置工作之 Nexus 工具整合的名稱。

  c. 針對工具整合類型，選取 **Nexus**。

  d. 針對建置指令，輸入指令來建置 Maven 模組或將它發佈至 Snapshot 登錄。此範例顯示用來建置或發佈模組的指令。
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  您可以在 Nexus 工具整合的配置設定中，找到用來連接至登錄的 URL 及使用者認證。
  {: tip}

1. 按一下**儲存**。只要管線執行，此建置工作就會使用 Nexus 工具整合中的配置資訊來連接至 Maven 儲存庫。

### 進一步瞭解 Nexus

若要進一步瞭解 Nexus，請參閱 IBM Cloud Garage Method 上的 [Nexus 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/deliver/tool_nexus/){: new_window}。


## 配置自訂工具（其他工具）
{: #othertool}

如果您的團隊使用不包含在工具鏈整合清單中的工具，則您可以整合自訂工具。

配置自訂工具，使其可與工具鏈上的其他工具一起運作，且可供您的團隊使用：

1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下**其他工具**。

1. 鍵入工具名稱。
1. 選取與工具最密切關聯的生命週期階段。此選項可決定您的工具會列在「概觀」頁面的哪個種類下。
1. 新增圖示 URL。此圖示會顯示在工具整合卡片上。
1. 新增文件 URL。
1. 指定工具實例名稱。例如：我的團隊工具。
1. 新增工具實例 URL。只要按一下工具整合卡片，就會開啟此 URL。
1. 新增工具的說明。
1. （進階）必要的話，新增更多內容。例如，列出您的工具與工具鏈中的其他工具整合時所需的任何資訊或屬性。  
1. 按一下**建立整合**。

### 進一步瞭解自訂工具

若要進一步瞭解自訂工具，請參閱 [{{site.data.keyword.Bluemix_notm}} 工具鏈的自訂工具整合簡介 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2016/10/custom-tool-integration-with-bluemix-toolchains/){: new_window}，或採用下列指導教學：

  * [將自訂工具整合新增至工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/add-a-custom-tool-integration-to-a-toolchain){:new_window}


## 配置 PagerDuty
{: #pagerduty}

PagerDuty 會將多個監視系統中的資料整合至單一視圖。發生問題時，PagerDuty 可確保當時最有能力修正問題的團隊成員能收到通知。如果團隊成員未回應問題，則可以配置呈報，將它遞送給次要工程師或作業管理員。

配置 PagerDuty 在管線階段失敗時傳送通知，讓您可以更快速地修正問題，並減少關閉時間：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **PagerDuty**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **PagerDuty**。

1. 如果您要使用 API 金鑰整合帳戶層次的 PagerDuty，請按一下**帳戶**：

 a. 鍵入 PagerDuty 帳戶的 API 存取金鑰。如果您沒有 PagerDuty 帳戶，請[註冊一個帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://signup.pagerduty.com/accounts/new){: new_window}。如需尋找金鑰的指示，請參閱[產生 API 金鑰 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){: new_window}。

 b. 鍵入 PagerDuty 服務的名稱。

 c. 鍵入主要 PagerDuty 聯絡人的電子郵件位址。

 d. 鍵入主要 PagerDuty 聯絡人的電話號碼。

1. 如果您要使用整合金鑰整合服務層次的 PagerDuty，請按一下**服務**：

 a. 鍵入您要在其中張貼警示之 PagerDuty 服務的 URL。

 b. 鍵入 PagerDuty 整合金鑰。您可以在 PagerDuty 服務頁面的「整合」區段中找到金鑰或建立金鑰。

1. 按一下**建立整合**。
1. 按一下 **PagerDuty** 以移至 pagerduty.com。您可以檢視與 PagerDuty 服務相關聯的事件，而 PagerDuty 服務是您在配置工具鏈的這個工具整合時所指定。

### 進一步瞭解 PagerDuty

若要進一步瞭解 PagerDuty，請參閱 IBM Cloud Garage Method 上的 [PagerDuty 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/manage/tool_pagerduty/){: new_window}，或採用下列指導教學及 Garage Method 代言人課程：

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [成為 Garage Method 代言人 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:new_window}


## 配置 Rational Team Concert
{: #rationalteamconcert}

IBM Rational Team Concert&trade; 是一種團隊協同作業工具，可整合開發作業，包括：疊代規劃、變更管理、問題報告追蹤、來源控制、建置自動化，以及報告。

配置 Rational Team Concert 以在開發環境中實施 DevOps 方法及持續交付：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Rational Team Concert**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Rational Team Concert**。

1. 鍵入當您從工具鏈按一下 Rational Team Concert 卡片時所要開啟的 Rational Team Concert 伺服器 URL。
1. 鍵入用來存取 Rational Team Concert 伺服器的使用者 ID。
1. 鍵入用來存取 Rational Team Concert 伺服器的密碼。
1. 如果您想要將某個 Rational Team Concert 專案區域新增至工具鏈，請遵循下列步驟：

 a. 從**專案區域類型**清單中，選取**現有專案區域**。

 b. 鍵入要新增至工具鏈的專案區域名稱。

1. 如果您想要建立 Rational Team Concert 專案區域以便新增至工具鏈，請遵循下列步驟：

 a. 從**專案區域類型**清單中，選取**新的專案區域**。

 b. 鍵入要新增至工具鏈的新專案區域名稱。

 c. 鍵入 Rational Team Concert 處理程序範本名稱，以用來建立專案。

1. 若要透過建立工作項目的標籤及註解來追蹤專案的程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。
1. 按一下**建立整合**。
1. 從您的工具鏈，按一下 **Rational Team Concert**，以開啟您配置的 Rational Team Concert 儀表板。

### 進一步瞭解 Rational Team Concert

若要進一步瞭解 Rational Team Concert，請參閱 IBM Cloud Garage Method 上的 [IBM Rational Team Concert 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/think/tool_rtc/){: new_window}。


## 配置 Sauce Labs
{: #saucelabs}

Sauce Labs 會執行功能單元測試。在 {{site.data.keyword.deliverypipeline}} 中將 Sauce Labs 測試套組配置為測試工作時，測試套組可以在持續交付處理程序期間對 Web 或行動應用程式執行測試。這些測試可以為專案提供寶貴的流程控制，作為防止部署不當程式碼的閘門。

 此工具整合僅適用於 {{site.data.keyword.Bluemix_notm}} Public。
 {: tip}

配置 Sauce Labs 對多個作業系統和瀏覽器執行自動化功能測試，讓您模擬使用者可能使用網站或應用程式的方式：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Sauce Labs**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Sauce Labs**。

1. 鍵入與 Sauce Labs 帳戶相關聯的使用者名稱。您可以[在 Sauce Labs 帳戶頁面頂端的歡迎使用訊息中找到使用者名稱 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://saucelabs.com/account){: new_window}。
1. 鍵入 Sauce Labs 帳戶的存取金鑰。您可以[在 Sauce Labs 帳戶頁面上找到金鑰 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://saucelabs.com/account){: new_window}。
1. 按一下**建立整合**。
1. 按一下 **Sauce Labs** 以移至 saucelabs.com，然後檢視工具鏈的測試活動。

 如果您已將 Sauce Labs 測試工作新增至 {{site.data.keyword.deliverypipeline}}，則可以選取服務實例。如需在管線中配置測試工作的指示，請參閱[在管線中配置 Sauce Labs 測試工作](#config_saucelabs)一節。
 {: tip}

### 進一步瞭解 Sauce Labs

若要進一步瞭解 Sauce Labs，請參閱 IBM Cloud Garage Method 上的 [Sauce Labs 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/deliver/tool_sauce_labs/){: new_window}，或採用下列指導教學：

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}



## 配置 Slack
{: #slack}

團隊的所有人都可以看到張貼到公用 Slack 頻道的通知。請記住，您需要為您張貼的內容負責。
{: tip}

Slack 是一種雲端型、即時傳訊和通知系統。Slack 會提供持續性會談，這個替代方案在進行團隊協同作業時比電子郵件更具互動性。您可以透過專用頻道或與工作直接相關的一組頻道來與團隊進行通訊。您也可以透過頻道或兩位以上人員之間的直接訊息來共用檔案和影像。會保留透過直接訊息和頻道的通訊，讓您可以搜尋它們。

配置 Slack 接收來自工具整合有關工具鏈的通知（例如測試和部署活動）：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **Slack**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **Slack**。

1. 鍵入 Slack Webhook URL，這是由 Slack 產生作為送入 Webhook。您需要 Slack 頻道的 Slack Webhook URL，以接收來自工具整合之工具鏈的通知。如需建立或尋找 Webhook 的指示，請參閱[送入 Webhook ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://api.slack.com/incoming-webhooks){: new_window}。

 如果您已使用 API 金鑰，讓 Slack 頻道接收來自工具整合之工具鏈的通知，則必須更新配置以改用 Webhook。
 {: tip}

1. 鍵入您要傳送通知的目標 Slack 頻道名稱。此頻道必須存在，而且在 Slack 團隊中為作用中。
1. 鍵入 Slack 團隊的 URL 主機名稱，這是團隊 URL 中 `.slack.com` 前面的單字或詞組。例如，如果團隊 URL 是 `https://team.slack.com`，則主機名稱是 `team`。
1. 按一下**建立整合**。

 如果無法到達所指定的 Slack 頻道及團隊，則會在 Slack 卡片上顯示 `Setup Failed` 錯誤。將游標移至 `Setup Failed` 訊息上方，然後按一下**重新配置**。請確定您是針對 Slack 團隊的 Slack Webhook URL、Slack 頻道及 URL 主機名稱，使用有效的配置參數。視需要更新設定，然後按一下**儲存整合**。
 {: tip}

1. 按一下 **Slack**。您可以在已配置的 Slack 頻道中檢視工具鏈的所有活動。

### 進一步瞭解 Slack

若要進一步瞭解 Slack，請參閱 IBM Cloud Garage Method 上的 [Slack 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/culture/tool_slack/){: new_window}，或採用下列指導教學及 Garage Method 代言人課程：

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [成為 Garage Method 代言人 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:new_window}


## 配置 SonarQube
{: #sonarqube}

SonarQube 概述原始碼的整體性能及品質，以及強調顯示在新程式碼中找到的問題。程式碼分析器可偵測 20 種以上程式碼語言的難處理錯誤（例如空值指標解除參照、邏輯錯誤及資源洩漏）。

配置 SonarQube，以持續分析及測量原始碼的品質：

1. 從 DevOps 儀表板中，按一下**工具鏈**。按一下要新增 SonarQube 的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。  

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **SonarQube**。

1. 鍵入此 SonarQube 工具整合實例的名稱。
1. 鍵入當您從工具鏈按一下 SonarQube 卡片時所要開啟的 SonarQube 實例 URL。
1. 選用項目：鍵入您用來連接至 SonarQube 伺服器的使用者名稱。

 只有在您使用密碼來連接至 SonarQube 伺服器時，才需要指定使用者名稱。如果您使用鑑別記號進行連接，請讓此欄位保留為空欄位。
 {: tip}

1. 鍵入您用來連接至 SonarQube 伺服器的密碼或鑑別記號。
1. 按一下**建立整合**。
1. 從工具鏈中，按一下 **SonarQube** 以檢視您已連接之 SonarQube 實例的儀表板。

### 進一步瞭解 SonarQube

若要進一步瞭解 SonarQube，請參閱 IBM Cloud Garage Method 上的 [SonarQube 文章 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/content/learn/tool_sonarqube/){: new_window}。
