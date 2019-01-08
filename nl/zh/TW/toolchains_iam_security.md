---

copyright:
  years:  2018
lastupdated: "2018-11-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 使用 Identity and Access Management 管理使用者對工具鏈的存取

{{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) 控制對帳戶內使用者資源群組中之工具鏈的存取。 

**附註**： 

* 工具鏈實例及 {{site.data.keyword.contdelivery_short}} 服務實例的使用者存取會分開進行管理。如需管理使用者對資源群組中 {{site.data.keyword.contdelivery_short}} 服務實例之存取的相關資訊，請參閱[使用 Identity and Access Management 管理使用者對 {{site.data.keyword.contdelivery_short}} 的存取](/docs/services/ContinuousDelivery/cd_iam_security.html){: new_window}。

* Cloud Foundry 組織中工具鏈的使用者存取，其管理方式與使用者對資源群組中 {{site.data.keyword.contdelivery_short}} 服務實例的存取不同。如需管理使用者對 Cloud Foundry 組織中工具鏈之存取的相關資訊，請參閱[管理對 Cloud Foundry 組織中工具鏈的存取](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs.html){: new_window}。

在您的帳戶中存取工具鏈的每位使用者，都必須獲指派已定義 IAM 使用者角色的存取原則。該原則會決定使用者可以在您選取之服務或實例的環境定義中執行哪些動作。{{site.data.keyword.Bluemix_notm}} 服務會將可容許的動作自訂及定義為容許對服務執行的作業。然後，這些動作會對映至 IAM 使用者角色。

原則可讓您在不同層次授與存取權，包括： 

* 跨您帳戶中的所有服務實例存取
* 存取您帳戶中的個別服務實例
* 存取實例內的特定資源
* 存取您帳戶中所有已啟用 IAM 功能的服務

在您定義存取原則的範圍之後，即可指派角色。請檢閱下列各表，其概述每個角色在工具鏈內所容許的動作。

下表詳述對映至平台管理角色的動作。平台管理角色可讓使用者對平台層次的服務資源執行作業，例如，指派服務的使用者存取、建立或刪除服務 ID、建立實例，以及將實例連結至應用程式。

| 平台管理角色 | 動作的說明 | 範例動作 |
|:-----------------|:-----------------|:-----------------|
| 檢視者、操作員 | 檢視工具鏈及交付管線。執行交付管線。| <ul><li>按一下工具鏈以開啟其「概觀」頁面。</li><li>按一下管線工作所在階段的**執行階段**圖示。</li></ul> |
| 編輯者、管理者 | 建立、檢視、更新及刪除工具鏈和交付管線。|<ul><li>在 DevOps 儀表板的**工具鏈**頁面上，按一下**建立工具鏈**。</li><li>在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。</li><li>在 DevOps 儀表板的**工具鏈**頁面上，按一下要刪除的工具鏈。按一下**檢視應用程式**旁的**其他動作**功能表。按一下**刪除**。</li></ul> |
{: caption="表 1. IAM 使用者角色及動作" caption-side="top"}

 對於工具鏈，存在下列動作：

| 動作 | 服務的作業 | 角色
|:-----------------|:-----------------|:--------------|
| create | 在資源群組中建立工具鏈。| 管理者、編輯者 |
| update | 更新資源群組中的工具鏈。例如，重新命名工具鏈。變更連結至資源群組中工具鏈的交付管線。| 管理者、編輯者 |
| update_plan | 不適用。| 管理者、編輯者 |
| delete | 從資源群組中刪除工具鏈。| 管理者、編輯者 |
| retrieve | 檢視資源群組中工具鏈的詳細資料。檢視及執行連結至資源群組中工具鏈的交付管線。| 管理者、編輯者、操作員、檢視者 |
| list-bindings | 檢視連結至資源群組中工具鏈的工具整合。| 管理者、編輯者、檢視者 |
| create-bindings | 將工具整合新增至資源群組中的工具鏈。| 管理者、編輯者 |
| delete-bindings | 從資源群組的工具鏈中移除工具整合。| 管理者、編輯者 |
{: caption="表 2. 服務動作及作業" caption-side="top"}

如需在使用者介面中指派使用者角色的相關資訊，請參閱[管理 IAM 存取](/docs/iam/mngiam.html#iammanidaccser)。

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
