---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# 方案限制與使用
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}} 的使用，僅限於在 {{site.data.keyword.Bluemix_notm}} 平台或其他相容之平台即服務 (PaaS) 或基礎架構即服務 (IaaS) 供應項目上，建置、部署、測試及持續運作應用程式。

## 服務實例的範圍
{: #service_scope}

您必須具有 {{site.data.keyword.contdelivery_short}} [服務實例](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}，才能建立及使用 DevOps 工具鏈。服務實例可能屬於 {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) [資源群組](/docs/services/resources?topic=resources-rgs)，或屬於 {{site.data.keyword.Bluemix_notm}} 組織。

您只能在資源群組中建立 {{site.data.keyword.contdelivery_short}} 服務的*新* 實例。目前不支援將組織中的工具鏈移轉至資源群組。如果您遺漏包含工具鏈之組織的 {{site.data.keyword.contdelivery_short}} 服務，則可以在資源群組中重新建立工具鏈，或與 [IBM 支援中心](https://cloud.ibm.com/unifiedsupport){:external}聯絡，以取得協助。

每個帳戶只能有一個「精簡」服務。如果您想要在多個組織或資源群組中，或在多個地區內使用工具鏈，建議您使用「專業」方案。
{: tip}


## 授權使用者
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [服務方案](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}是根據服務實例的授權使用者數目進行定義及定價。任何參與工作的人都必須計入授權使用者數目，包括：

 * 與 {{site.data.keyword.gitrepos}} 儲存庫中的問題、問題板、原始碼或其他構件互動的使用者。
 * 操作、觸發（直接在使用者介面中，或間接透過確定至儲存庫）或檢視交付管線狀態的使用者。
 * 與 Eclipse Orion {{site.data.keyword.webide}} 互動的使用者。
 
「精簡」方案容易受到限制。如需「精簡」方案及「專業」方案的相關資訊，請參閱[服務型錄](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}。
{: tip}
 
### 如何計算資源群組中 {{site.data.keyword.contdelivery_short}} 實例的使用者數目？

藉由查看授權使用者的清單，來取得計費及「精簡」方案限制，以計算每一個服務實例的授權使用者數目，並管理這些授權使用者。{{site.data.keyword.contdelivery_short}} 服務使用者會自動新增至此清單。您可以防止使用者存取工具鏈，以及自動新增至 {{site.data.keyword.contdelivery_short}} 服務實例。如需使用 IAM 從包含工具鏈的「資源群組」（或從工具鏈本身）中移除使用者存取的相關資訊，請參閱[使用 Identity and Access Management 管理使用者對 {{site.data.keyword.contdelivery_short}} 的存取](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security)。 

您用來在資源群組內組織工具鏈的方法，會直接影響使用者存取及計費。當使用者在多個資源群組中使用工具鏈時，會針對這些資源群組中的每一個服務，為這些工具鏈進行計數及計費。
{: tip}

在 {{site.data.keyword.contdelivery_short}} 服務實例內的**管理**標籤上，您可以管理授權使用者的清單。

1. 移至 {{site.data.keyword.Bluemix_notm}} 帳戶的[資源清單](https://cloud.ibm.com/resources){:external}。
2. 在**名稱**直欄的過濾器文字框中，鍵入 **Continuous Delivery** 以顯示現有的服務。
3. 對於每一個服務，按一下**名稱**直欄中的超鏈結。
4. 在**管理**標籤中，您可以視需要檢視、新增或移除「授權使用者」清單中的使用者。

當使用者使用 {{site.data.keyword.contdelivery_short}} 服務時，系統會自動新增或重新新增使用者。
{: tip}

### 如何計算組織中 {{site.data.keyword.contdelivery_short}} 實例的使用者數目？

查看包含 {{site.data.keyword.contdelivery_short}} 服務之 {{site.data.keyword.Bluemix_notm}} 組織中的所有使用者，以計算授權使用者數目。如需組織及空間的相關資訊，請參閱[建立組織及空間](/docs/cloud-foundry?topic=cloud-foundry-create_orgs)。

若要檢視 {{site.data.keyword.Bluemix_notm}} Public 環境之組織中的使用者清單，請從功能表列中按一下**管理 > 帳戶**。然後，按一下 **Cloud Foundry 組織**。

### 如何檢視計費及用量資訊？

您可以檢視帳戶中的所有 {{site.data.keyword.contdelivery_short}} 服務實例，以及對 {{site.data.keyword.Bluemix_notm}} Public 環境中每一個實例所報告的使用者數目及管線執行次數。

1. 從功能表列中，按一下**管理 > 計費及用量**。
2. 按一下**用量**。
3. 在**服務**區段中，按一下 {{site.data.keyword.contdelivery_short}} 服務的**檢視方案**。
4. 按一下您要檢視相關資訊的方案的**檢視詳細資料**。
5. 按一下您要檢視用量資訊的 {{site.data.keyword.contdelivery_short}} 實例的**檢視實例詳細資料**。

`AUTHORIZED_USERS_PER_MONTH` 度量是根據每日計算的每月平均使用者數目來計算。
{: tip}

### 當您超過服務方案的限制時會發生什麼情況？

「精簡」服務會有其他限制（例如可執行的 Delivery Pipeline 工作數目或儲存空間耗用量）。如需方案說明的相關資訊，請參閱[服務型錄](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}。如果在計費期間超過任何方案限制，則服務會暫停。例如，在計費期間的其餘時間，不會執行 Delivery Pipeline 工作。

## Delivery Pipeline 使用
{: #pipeline_usage}

可接受的使用行為，包括但不限於下列行為：

* 編譯及組合受支援程式設計語言的構件。
* 自動化部署應用程式構件、配置及支援資源或服務。
* 測試、驗證，以及因開發處理程序而觸發的其他開發事件產生之行為。

不被允許的使用行為，包括但不限於下列行為：

* 將管線工作或工作者節點用於一般運算行為，例如 Bitcoin 採礦、分散式拒絕服務攻擊，以及針對 {{site.data.keyword.Bluemix_notm}} 平台內的其他用戶端或使用者，或是針對一般網際網路使用者的惡意或冒犯性的行為。
* 將一般開發處理程序，用於提倡仇恨言論之網站或服務或違反 IBM Business Conduct Guidelines 之其他活動。
* 使用事件產生之行為，進行對 {{site.data.keyword.Bluemix_notm}} 或其他網站的惡意入侵或攻擊。

IBM 得自行決定對違反 {{site.data.keyword.contdelivery_short}} 服務或 [IBM Business Conduct Guidelines](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} 可接受使用行為的使用者採取停權措施，而不另行通知。如果使用者在收到冒犯性動作通知之後更正其使用行為，IBM 得自行決定還原部分服務。否則，帳戶可能會被暫停或終止。

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
  2. 僅選取的使用者看得到專用專案。如需授與使用者對專案之存取權的相關資訊，請參閱[專案使用者](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}。
  3. 所有已登入的使用者都看得到內部專案。具有 {{site.data.keyword.Bluemix_notm}} 帳戶的任何使用者都可以檢視這些專案。

您可以在專案設定中修改專案類型。如需專案設定的相關資訊，請參閱[如何變更專案可見性](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}。

當您使用 {{site.data.keyword.gitrepos}} 時，您提供給專案的內容會依據該專案中指定的任何條款而授權。當您建立專案時，請包含說明適用於該內容之授權的檔案。當您提供內容給專案時，大眾可能看得到與您所確定內容相關聯的名稱及電子郵件位址。當您透過 {{site.data.keyword.gitrepos}} Web 介面建立確定內容時，會使用與您 {{site.data.keyword.Bluemix_notm}} 帳戶相關聯的電子郵件位址。
