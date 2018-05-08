---

Copyright:
  years: 2015, 2018
lastupdated: "2018-3-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 工具鏈可用性、範本及指導教學  
{: #cd_about}  

「{{site.data.keyword.Bluemix_notm}} 公用」及「專用」上都提供工具鏈。您可以使用範本作為起點來建立工具鏈。
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} 公用與 {{site.data.keyword.Bluemix_notm}} 專用的工具鏈可用性比較
{: #public_and_dedicated}

「{{site.data.keyword.Bluemix_notm}} 公用」是一種開放式標準雲端型平台，您可以在其中建置、執行及管理 [http://bluemix.net ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://bluemix.net){:new_window} 所存取的應用程式。「{{site.data.keyword.Bluemix_notm}} 專用」在專用 SoftLayer 環境中提供 {{site.data.keyword.Bluemix_notm}} 功能，該環境可安全地連接至「{{site.data.keyword.Bluemix_notm}} 公用」環境及網路。您公司的「{{site.data.keyword.Bluemix_notm}} 專用」環境可能未包含與「{{site.data.keyword.Bluemix_notm}} 公用」網站相同的工具整合。

對於原始碼管理及問題追蹤，「{{site.data.keyword.Bluemix_notm}} 公用」一般會使用 {{site.data.keyword.gitrepos}}（由 IBM 所管理並以 [GitLab Community Edition ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://about.gitlab.com/){:new_window} 為建置基礎）或 GitHub (github.com)。「{{site.data.keyword.Bluemix_notm}} 專用」也可以使用 github.com，但一般會使用公司所安裝或 IBM 所管理的 {{site.data.keyword.ghe_short}}。

在所選取地區的「{{site.data.keyword.Bluemix_notm}} 公用」上以及「{{site.data.keyword.Bluemix_notm}} 專用」上可以使用 {{site.data.keyword.contdelivery_short}}。視您是在「{{site.data.keyword.Bluemix_notm}} 公用」還是「{{site.data.keyword.Bluemix_notm}} 專用」上使用 {{site.data.keyword.contdelivery_short}} 而定，工具鏈會有所不同。

**提示**：雖然工具鏈目前無法在所有地區中使用，但是您可以配置工具鏈將應用程式部署至所有地區。若要進一步瞭解，請嘗試<a href="/docs/tutorials/multi-region-webapp.html#deploy-a-secure-web-application-across-multiple-regions" target="_blank">將安全 Web 應用程式部署至多個地區</a>指導教學。

|工具鏈|{{site.data.keyword.Bluemix_notm}} 公用|{{site.data.keyword.Bluemix_notm}} 專用|
|:----------|:------------------------------|:------------------|
|工具整合|如需所支援工具整合的清單，請參閱[配置工具整合](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}。|可用的工具整合取決於 {{site.data.keyword.contdelivery_short}} 在您環境中的設定方式。|
|從範本建立工具鏈|登入 [{{site.data.keyword.Bluemix_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://console.bluemix.net/devops){:new_window}|登入 {{site.data.keyword.Bluemix_notm}} 的「專用」環境。|
|從應用程式建立工具鏈|應用程式會配置成從已移入應用程式入門範本程式碼的新 GitHub 儲存庫進行持續交付。|應用程式會配置成從已移入應用程式入門範本程式碼的新 GitHub 或 GitHub Enterprise 儲存庫進行持續交付。|  
|交付管線部署地區|Cloud Foundry 部署工作可以使用所有「{{site.data.keyword.Bluemix_notm}} 公用」地區。|「{{site.data.keyword.Bluemix_notm}} 專用」地區可供使用。視 {{site.data.keyword.contdelivery_short}} 在您特定環境中的設定方式而定，也可使用相同客戶帳戶內的其他「專用」或「本端」地區。|
|交付管線部署工作|所有[工作類型](/docs/services/ContinuousDelivery/pipeline_about.html#deliverypipeline_jobs)都可供使用。|可能無法使用與「專用」環境中未安裝之 {{site.data.keyword.Bluemix_notm}} 服務相依的工作類型。例如，在沒有 {{site.data.keyword.Bluemix_notm}} Container 服務的環境中，可能無法使用容器建置及部署工作類型。|
{: caption="表 1.「{{site.data.keyword.Bluemix_notm}} 專用」及「{{site.data.keyword.Bluemix_notm}} 公用」上的工具鏈差異" caption-side="top"}


## 工具鏈範本
{: #templates}

您可以使用範本作為起點來[建立工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops/create){: new_window}。工具鏈範本包含可支援開發、部署及操作作業的特定工具整合集。

**提示**：您公司的「{{site.data.keyword.Bluemix_notm}} 專用」環境可能未包含與「{{site.data.keyword.Bluemix_notm}} 公用」網站相同的工具鏈範本。「{{site.data.keyword.Bluemix_notm}} 公用」及「{{site.data.keyword.Bluemix_notm}} 專用」上可用的工具鏈範本可能包含「{{site.data.keyword.Bluemix_notm}} 專用」上的不同工具整合集。

部分工具鏈範本包含 {{site.data.keyword.contdelivery_short}} 服務所屬的工具整合。如果組織中還沒有該服務的實例，則在按一下**建立**以建立工具鏈時，會使用所選取的免費「精簡」方案自動新增服務。如需相關資訊及術語，請參閱 [{{site.data.keyword.Bluemix_notm}} 型錄 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/continuous-delivery/){:new_window}。

「在 Cloud Foundry 上開發及測試微服務」工具鏈會部署具有 Cloudant 儲存庫所支援之型錄及訂單 API 的應用程式。部署應用程式時，會建立不需要成本的 Cloudant 服務實例。如需相關資訊及術語，請參閱 [{{site.data.keyword.Bluemix_notm}} 型錄 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/cloudant-nosql-db/){:new_window}。

預先定義的 DevOps 工具鏈範本是解決真實情境的建議範例，而且各包含一個範例應用程式。從範本建立工具鏈時，指定 git 儲存庫即可使用自己的應用程式。

<table valign="top" padding="2px">
  <caption>表 2. 工具鏈範本</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">範本及可用的地區</th>
    <th style="width:50%; text-align:left; vertical-align:top">說明及可用的指導教學</th>
    <th style="text-align:left; vertical-align:top">包含的工具</th>
  </tr>
  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">「開發 Cloud Foundry 應用程式」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

  </td><td>
運用此工具鏈，您可以開發及部署 Cloud Foundry 應用程式。根據預設值，此工具鏈會使用範例 Node.js "Hello world" 應用程式，但您可以改為鏈結至自己的 GitHub 儲存庫。已預先配置此工具鏈，以進行持續交付、來源控制、問題追蹤及線上編輯。<br><br>

  嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">使用「開發 Cloud Foundry 應用程式」工具鏈介紹工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 及 GitHub Issues</li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">「開發 Kubernetes 應用程式」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

  </td><td>
  使用此工具鏈，您可以安全地開發應用程式並將其部署至 {{site.data.keyword.Bluemix_notm}} Container Service 所管理的 Kubernetes 叢集。依預設，工具鏈會使用範例 Node.js "Hello World" 應用程式，但您可以改為鏈結至自己的 GitHub 儲存庫。已預先配置此工具鏈，以進行「漏洞警告器」的持續交付、來源控制、問題追蹤及線上編輯。<br><br>
  嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">使用「開發 Kubernetes 應用程式」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 及 GitHub Issues</li><li>{{site.data.keyword.Bluemix_notm}} Container（Kubernetes 叢集）
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">「使用 Helm 開發 Kubernetes 應用程式」工具鏈
   <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

  </td><td>
  使用此工具鏈，您可以在來源控制中一起開發 Docker 應用程式及其 Helm 圖表，並自動將它建置及部署至 Kubernetes 叢集。此工具鏈會在建置或部署之前執行煙霧測試，並使用專用容器登錄以及容器登錄和 Kubernetes 叢集的名稱空間來確定隱私權。此工具鏈也使用「漏洞警告器」來確定僅部署安全映像檔。<br><br>
  嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">使用「使用 Helm 開發 Kubernetes 應用程式」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>Git Repos and Issue Tracking</li><li>搭配 Helm 圖表的 {{site.data.keyword.Bluemix}} Container（Kurbernetes 叢集）
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">「開發及測試 Cloud Foundry 應用程式」工具鏈
   <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

  </td><td>
  使用此雲端原生工具鏈，您可以使用 DevOps Insights 來限制簡單 Cloud Foundry 應用程式的部署。依預設，此工具鏈會使用簡單 Node.js 天氣應用程式，或者您可以鏈結至自己的 GitHub 儲存庫。此工具鏈會使用 Mocha 來執行單元測試，並使用 Istanbul 來檢查程式碼涵蓋面。<br><br>
  嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/use-develop-test-cloud-foundry-app-toolchain" target="_blank">使用「開發及測試 Cloud Foundry 應用程式」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>Git Repos and Issue Tracking</li><li>{{site.data.keyword.DRA_full}}（僅限美國南部）
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  「在 Cloud Foundry 上開發及測試微服務」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

  </td><td>
使用此雲端原生工具鏈，您可以使用範例來建立包含三個微服務的線上商店：Catalog API、Orders API 以及呼叫這兩個 API 的使用者介面。已預先配置此工具鏈，以進行持續交付、來源控制、功能測試、問題追蹤、線上編輯及警示通知。<br><br>
  嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 及 GitHub Issues</li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}（僅限美國南部）
  </li><li>PagerDuty</li><li>Sauce Labs		</li><li>Slack</li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">
「搭配 Cloud Foundry 的 Garage Method 指導教學」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

</td><td>
此工具鏈示範 Garage Method 中所具備的 DevOps 作法。已預先配置此工具鏈，以進行持續交付、來源控制、測試自動化，以及自動化監視和作業。它會隨附以 Node.js Express 4 撰寫的範例應用程式，而且您可以進一步予以擴充。<br><br>嘗試課程：<a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">成為 Garage Method 代言人 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>。
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 及 GitHub Issues</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty</li><li>Sauce Labs		</li><li>Slack</li></ul>
</td></tr>

<tr><td>
<a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevopsinsights-toolchain" target="_blank">「搭配 GitHub 和 Jenkins 的 Deployment Risk Analytics」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部使用

</td><td>運用此工具鏈，您可以瞭解進行持續整合及交付的 Jenkins 處理程序。在 Jenkins 執行工作時，您可以配置 Jenkins 伺服器以將資料傳送至 {{site.data.keyword.DRA_short}}。您也可以實作品質限制，以根據原則來封鎖部署。您可以在 {{site.data.keyword.DRA_short}} 的「部署風險」儀表板上檢視結果。如果您配置 GitHub 儲存庫以指出 Jenkins 所使用的來源儲存庫，則可以使用變更可追蹤性。  
<br><br>
嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain" target="_blank">使用「搭配 GitHub 和 Jenkins 的 Deployment Risk Analytics」工具鏈確定品質部署 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>  <br><br>
</td><td><ul><li>
GitHub 及 GitHub Issues</li><li>Jenkins</li><li>{{site.data.keyword.DRA_full}}
</li><li>Slack</li></ul>
</td></tr>

<tr><td>
<a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevteaminsights-toolchain" target="_blank">「搭配 GitHub 和 JIRA 的 Developer Insights 及 Team Dynamics」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部使用

</td><td>
運用此工具鏈，您可以探索專案的開發風險，以及使用社交編碼分析來瞭解開發人員之間的互動型樣。您可以分析 GitHub 原始碼，以及 GitHub Issues、JIRA Issues 或這兩者。使用 Developer Insights 來識別很容易出錯的檔案，以及查看如何使用 DevOps 作法來編譯專案。Team Dynamics 中的社交編碼分析可識別團隊成員之間的互動層次，讓團隊可以修正不具生產力的作法。<br><br>
嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain" target="_blank">使用「搭配 GitHub 和 JIRA 的 Developer Insights 及 Team Dynamics」工具鏈進行瞭解 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>
</td><td><ul><li>
GitHub 及 GitHub Issues</li><li>{{site.data.keyword.DRA_full}}
</li><li>JIRA</li><li>Slack</li></ul>
</td></tr>


<tr><td>
<a href="(https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdeliveryinsights-toolchain" target="_blank">「搭配 IBM UrbanCode Deploy 的 Delivery Insights」工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部使用

</td><td>運用此工具鏈，您可以從 IBM UrbanCode Deploy 檢視部署度量。讓此工具鏈從 {{site.data.keyword.DRA_short}} 中的「設定」頁面下載及配置 DevOps Connect，以與 IBM UrbanCode Deploy 進行通訊。<br><br>
嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/view-metrics-delivery-insights-urbancode-deploy-toolchain" target="_blank">使用「搭配 IBM UrbanCode Deploy 的 Delivery Insights」工具鏈檢視度量值 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> 	
<br><br>
</td><td><ul><li>{{site.data.keyword.DRA_full}}
</li><li>UrbanCode Deploy
</li></ul>
</td></tr>

<tr><td>
<a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">建置您自己的工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a> <br><br>

  可以在美國南部、德國及英國使用

</td><td>
此工具鏈沒有預先配置的工具。如果您已熟悉工具鏈，則可以設定自己的工具鏈。<br><br>
嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">建立自訂工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>
</td><td> &nbsp;&nbsp; 無
</td></tr>

<tr><td>Continuous Delivery 工具鏈<br><br>

 可以在美國南部、德國及英國使用

</td><td>
當您啟用應用程式的持續交付時，就會使用此工具鏈。<br><br>
嘗試指導教學：

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">將工具鏈新增至應用程式 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">建立自訂工具鏈 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a></li>
<li><a href="/docs/tutorials/multi-region-webapp.html#deploy-a-secure-web-application-across-multiple-regions" target="_blank">將安全 Web 應用程式部署至多個地區</a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>
GitHub 及 GitHub Issues</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>自訂工具鏈範本<br><br>

 可以在美國南部、德國及英國使用

</td><td>
<br><br>
您可以建立可供其他人使用的自訂工具鏈範本。<br><br>

請參閱文件：
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">建立自訂工具鏈範本 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a>
<br><br>
嘗試指導教學：<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">建立自訂工具鏈的範本 <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示"></a></td>
<td>無
</td></tr>

</table>
