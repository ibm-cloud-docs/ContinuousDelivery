---

copyright:
  years: 2016, 2018
lastupdated: "2018-4-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 方案限制與使用
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}} 的使用，僅限於在 {{site.data.keyword.Bluemix_notm}} 平台或其他相容之平台即服務 (PaaS) 或基礎架構即服務 (IaaS) 供應項目上，建置、部署、測試及持續運作應用程式。

## 授權使用者
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} 服務方案是根據服務實例的授權使用者數目進行定義及定價。任何參與工作的人都必須計入授權使用者數目，包括：

 * 與 {{site.data.keyword.gitrepos}} 儲存庫中的問題、問題板、原始碼或其他構件互動的使用者。
 * 操作、觸發（直接在使用者介面中，或間接透過確定至儲存庫）或檢視交付管線狀態的使用者。
 * 與 Eclipse Orion {{site.data.keyword.webide}} 互動的使用者。
 
### 如何計算使用者數目？

查看包含 {{site.data.keyword.contdelivery_short}} 服務之 Cloud 組織中的所有使用者，以計算授權使用者數目。 

若要檢視組織中的使用者清單，請從功能表列中按一下**管理 > 帳戶 > Cloud Foundry 組織**。

您也可以檢視帳戶中的所有 {{site.data.keyword.contdelivery_short}} 服務實例，以及對每一個實例所報告的使用者數目。

1. 從功能表列中，按一下**管理 > 帳戶 > Cloud Foundry 組織**。
2. 按一下**用量儀表板**。

### 當您超過服務方案的限制時會發生什麼情況？ 

有些服務方案可能會有其他限制（例如可執行的 Delivery Pipeline 工作數目或儲存空間耗用量）。如需相關資訊，請參閱型錄中的方案說明。如果在計費期間超過任何方案限制，則可能會暫停服務。例如，在計費期間的其餘時間，可能未執行 Delivery Pipeline 工作。

## Delivery Pipeline 使用
{: #pipeline_usage}

可接受的使用行為，包括但不限於下列行為：

* 編譯及組合受支援程式設計語言的構件
* 自動化部署應用程式構件、配置及支援資源或服務
* 測試、驗證，以及因開發處理程序而觸發的其他開發事件產生之行為

不被允許的使用行為，包括但不限於下列行為：

* 將管線工作或工作者節點用於一般運算行為，例如 Bitcoin 採礦、分散式拒絕服務攻擊，以及針對 IBM Cloud 平台內的其他用戶端或使用者，或是針對一般網際網路使用者的惡意或冒犯性的行為
* 將一般開發處理程序，用於提倡仇恨言論之網站或服務或違反 IBM Business Conduct Guidelines 之其他活動
* 使用事件產生之行為，進行對 {{site.data.keyword.Bluemix_notm}} 或其他網站的惡意入侵或攻擊

IBM 得自行決定對違反 {{site.data.keyword.contdelivery_short}} 服務或 [IBM Business Conduct Guidelines ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} 可接受使用行為的使用者採取停權措施，而不另行通知。如果使用者在收到冒犯性動作通知之後更正其使用行為，IBM 得自行決定還原部分服務。否則，帳戶可能會被暫停或終止。

## Git Repos and Issue Tracking 限制
{: #git_limitations}

{{site.data.keyword.gitrepos}} 是以 GitLab Community Edition 為建置基礎，並由 IBM 於 {{site.data.keyword.Bluemix_notm}} 上進行管理，不過有一些 GitLab 選項無法使用：

 * 由於 {{site.data.keyword.deliverypipeline}} 提供 {{site.data.keyword.Bluemix_notm}} 的持續整合及持續交付，因此不支援 GitLab 中的持續整合特性。
 * 無法使用 GitLab 功能，因為它們是由 IBM 所管理。
 * 可能無法完整存取 {{site.data.keyword.gitrepos}}。

## Git Repos and Issue Tracking 使用者資訊及內容
{: #git_projects}

可用的 {{site.data.keyword.gitrepos}} 專案類型有三種：

  1. 所有網站造訪者都看得到公用專案。每個存取 {{site.data.keyword.contdelivery_short}} 的人都看得到公用專案中的內容，即使他們未受邀加入該專案。
  2. 僅選取的使用者看得到專用專案。如需授與使用者對專案之存取權的詳細資料，請參閱 [Project users ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}。
  3. 所有已登入的使用者都看得到內部專案。具有 {{site.data.keyword.Bluemix_notm}} 帳戶的任何使用者都可以檢視這些專案。

您可以在專案設定中修改專案類型。如需相關資訊，請參閱 [How to change project visibility ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}。

當您使用 {{site.data.keyword.gitrepos}} 時，您提供給專案的內容會依據該專案中指定的任何條款而授權。當您建立專案時，請包含說明適用於該內容之授權的檔案。當您提供內容給專案時，大眾可能看得到與您所確定內容相關聯的名稱及電子郵件位址。當您透過 {{site.data.keyword.gitrepos}} Web 介面建立確定內容時，會使用與您 {{site.data.keyword.Bluemix_notm}} 帳戶相關聯的電子郵件位址。

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
