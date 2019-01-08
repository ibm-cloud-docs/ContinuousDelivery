---

copyright:
  years:  2018
lastupdated: "2018-7-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 使用 Identity and Access Management 管理使用者對 Continuous Delivery 的存取

帳戶內使用者對於資源群組中 {{site.data.keyword.contdelivery_full}} 服務實例的存取，受到 {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) 控制。 

**附註**： 

* {{site.data.keyword.contdelivery_short}} 服務實例及工具鏈實例的使用者存取會分開進行管理。如需管理使用者對資源群組中工具鏈之存取的相關資訊，請參閱[使用 Identity and Access Management 管理使用者對工具鏈的存取](/docs/services/ContinuousDelivery/toolchains_iam_security.html){: new_window}。

* Cloud Foundry 組織中工具鏈的使用者存取，其管理方式與使用者對資源群組中工具鏈的存取不同。如需管理使用者對 Cloud Foundry 組織中工具鏈之存取的相關資訊，請參閱[管理對 Cloud Foundry 組織中工具鏈的存取](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}。

在您的帳戶中存取 {{site.data.keyword.contdelivery_short}} 服務的每位使用者，都必須獲指派已定義 IAM 使用者角色的存取原則。該原則會決定使用者可以在您選取之服務或實例的環境定義中執行哪些動作。{{site.data.keyword.Bluemix_notm}} 服務會將可容許的動作自訂及定義為容許對服務執行的作業。然後，這些動作會對映至 IAM 使用者角色。

原則可讓您在不同層次授與存取權。部分選項包括下列各項： 

* 跨您帳戶中的所有服務實例存取
* 存取您帳戶中的個別服務實例
* 存取實例內的特定資源
* 存取您帳戶中所有已啟用 IAM 功能的服務

在您定義存取原則的範圍之後，即可指派角色。請檢閱下列各表，其概述每個角色在 {{site.data.keyword.contdelivery_short}} 服務內所容許的動作。

下表詳述對映至平台管理角色的動作。平台管理角色可讓使用者對平台層次的服務資源執行作業，例如，指派服務的使用者存取、建立或刪除服務 ID、建立實例，以及將實例連結至應用程式。

| 平台管理角色 | 動作的說明 | 範例動作 |
|:-----------------|:-----------------|:-----------------|
| 檢視者、操作員 | 檢視 {{site.data.keyword.contdelivery_short}} 服務實例。| <ul><li>按一下 {{site.data.keyword.contdelivery_short}} 服務實例以開啟其儀表板。</li>|</ul>
| 編輯者、管理者 | 建立、檢視、更新、修改 {{site.data.keyword.contdelivery_short}} 服務的方案，以及刪除該服務的實例。|<ul><li>在資源群組中佈建 {{site.data.keyword.contdelivery_short}} 實例。</li><li>從資源群組中刪除 {{site.data.keyword.contdelivery_short}} 實例。</li><li>將 {{site.data.keyword.contdelivery_short}} 實例方案從「精簡」變更為「專業」。</li></ul> |
| 管理者 | 更新「授權使用者」清單。| <ul><li>將使用者新增至「授權使用者」清單。</li><li>從「授權使用者」清單移除使用者。</li></ul> |
{: caption="表 1. IAM 使用者角色及動作" caption-side="top"}

 對於 {{site.data.keyword.contdelivery_short}}，存在下列動作：

| 動作 | 服務的作業 | 角色
|:-----------------|:-----------------|:--------------|
| create | 在資源群組中佈建 {{site.data.keyword.contdelivery_short}} 服務實例。| 管理者、編輯者 |
| update | 更新資源群組中的 {{site.data.keyword.contdelivery_short}} 服務實例。例如，重新命名服務實例。| 管理者、編輯者 |
| update_plan | 變更資源群組中 {{site.data.keyword.contdelivery_short}} 服務實例的方案。| 管理者、編輯者 |
| delete | 從資源群組中刪除 {{site.data.keyword.contdelivery_short}} 服務實例。| 管理者、編輯者 |
| retrieve | 檢視資源群組中的 {{site.data.keyword.contdelivery_short}} 服務實例。| 管理者、編輯者、操作員、檢視者 |
| add-auth-users | 將項目新增至 {{site.data.keyword.contdelivery_short}} 服務實例內「管理」標籤的「授權使用者」清單。| 管理者、作者、管理員 |
| remove-auth-users | 從 {{site.data.keyword.contdelivery_short}} 服務實例內「管理」標籤的「授權使用者」清單中移除項目。| 管理者、作者、管理員 |
{: caption="表 2. 服務動作及作業" caption-side="top"}

下表詳述對映至服務存取角色的動作。服務存取角色可讓使用者存取 {{site.data.keyword.contdelivery_short}} 以及可以呼叫 {{site.data.keyword.contdelivery_short}} API。

| 服務存取角色 | 動作的說明 | 範例動作 |
|:-----------------|:-----------------|:-----------------|
| 作者、管理員 | 在 {{site.data.keyword.contdelivery_short}} 服務實例內「管理」標籤的「授權使用者」清單中新增及移除使用者。| <ul><li>新增授權使用者。</li><li>移除授權使用者。</li></ul>|
{: caption="表 3. IAM 服務存取角色及動作" caption-side="top"}

如需在使用者介面中指派使用者角色的相關資訊，請參閱[管理 IAM 存取](/docs/iam/mngiam.html#iammanidaccser)。

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
