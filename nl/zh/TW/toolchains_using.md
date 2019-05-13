---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-26"

keywords: user management function, tool integrations, Cloud Foundry org

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:tip: .tip}
{:important: .important}

# 使用工具鏈
{: #toolchains-using}

開放式工具鏈適用於 {{site.data.keyword.Bluemix}} 的「公用」及「專用」環境。您可以在日常的開發、部署及操作工作中，使用工具鏈來提高生產力。設定工具鏈之後，即可新增、刪除或配置工具整合，以及管理對工具鏈的存取權。
{: shortdesc}

您可以使用資源群組來管理美國南部、美國東部、英國、德國及東京公用地區中的工具鏈。您可以使用 Cloud Foundry 組織來管理美國南部、英國及德國公用地區中的工具鏈。工具鏈的存取控制及授權使用者管理功能不同（視它們包含在資源群組還是 Cloud Foundry 組織而定）。
{: important}

## 配置工具整合
{: #configuring_a_tool_integration}

如果您已在建立工具鏈時延遲配置工具整合，則會在其卡片上顯示**配置**按鈕。如果您已在建立工具鏈時配置工具整合，則可以更新配置設定。

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 如果您第一次需要配置工具整合，請在其卡片上按一下**配置**。

  ![「配置」按鈕](images/toolchain_tile_configure.png)

 完成工具整合的配置後，請按一下**儲存整合**。

1. 如果您需要更新工具整合的配置，請在其卡片上按一下功能表來存取配置選項。

  ![「配置」功能表](images/toolchain_tile_menu.png)

 有一些工具整合已預先配置，且不需要任何配置參數。您只能更新您所配置之工具整合的配置設定。
 {: tip}

 完成設定的更新後，請按一下**儲存整合**。如需配置特定工具整合的相關資訊，請參閱[配置工具整合](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}。

## 新增工具整合
{: #adding_a_tool_integration}

您可以新增及配置工具鏈的工具整合。視您是使用 {{site.data.keyword.Bluemix_notm}} Public 還是 {{site.data.keyword.Bluemix_notm}} Dedicated 而定，可用的工具整合會有所不同。

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 若要查看要新增的工具整合清單，請按一下**新增工具**。
1. 按一下您要新增的工具整合。
1. 輸入用來配置工具整合的任何必要資訊。
1. 按一下**建立整合**，以將工具整合新增至您的工具鏈。

## 刪除工具整合
{: #deleting_a_tool_integration}

如果您從工具鏈中刪除工具整合，則無法復原刪除。

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 在您要刪除的工具整合卡片上，按一下功能表來存取配置選項。
1. 若要從工具鏈中刪除工具整合，請按一下**刪除**。
1. 按一下**刪除**來進行確認。  

## 管理對資源群組中工具鏈的存取
{: #managing_access_resource_groups}

您可以使用 Identity and Access Management (IAM) 服務，來管理使用者對工具鏈的存取。如需使用 IAM 管理存取控制的相關資訊，請參閱[使用 Identity and Access Management 管理使用者對工具鏈的存取](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}。 

只有屬於所選取 {{site.data.keyword.contdelivery_short}} 實例之授權使用者清單的使用者，才能使用 {{site.data.keyword.contdelivery_short}} 工具鏈的 Delivery Pipeline、Eclipse Orion {{site.data.keyword.webide}} 及 {{site.data.keyword.gitrepos}} 特性。您可以從所指定資源群組內所選取 {{site.data.keyword.contdelivery_short}} 實例的「管理」標籤中管理授權使用者授權。

若要存取工具鏈中 {{site.data.keyword.contdelivery_short}} 的主要特性（例如 Delivery Pipeline），使用者必須可存取 IAM 中的工具鏈，而使用者也必須屬於 {{site.data.keyword.contdelivery_short}} 實例的「授權使用者」清單。
{: important}

授權使用者授權會套用至與 {{site.data.keyword.contdelivery_short}} 實例相同之資源群組中所含的所有工具鏈。
{: tip}


## 管理對 Cloud Foundry 組織中工具鏈的存取
{: #managing_access_orgs}

將使用者新增至與工具鏈相關聯的組織以及工具鏈的存取控制清單，即可將工具鏈存取權授與使用者。每一個工具鏈都會與特定組織相關聯，而且任何屬於該組織成員的使用者都可以新增至任何相關聯工具鏈的存取控制清單。您目前在其中工作的組織會顯示在功能表列上。若要存取一組不同的工具鏈，請切換至不同的組織。

您必須將使用者新增至工具鏈管理所在地區的工具鏈組織。如果工具鏈配置成將應用程式部署至不同地區，則仍會將應用程式部署至該地區。
{: important}

如果您使用的是 {{site.data.keyword.Bluemix_notm}} Dedicated for {{site.data.keyword.ghe_short}}，則將使用者新增至 {{site.data.keyword.Bluemix_notm}} 組織及空間時，使用者可以使用其 {{site.data.keyword.Bluemix_notm}} ID 及密碼來登入 {{site.data.keyword.ghe_short}}。使用者登入時，就會建立他們的帳戶。將使用者新增至 {{site.data.keyword.Bluemix_notm}} 組織及空間時，並不會將他們自動新增至 {{site.data.keyword.ghe_short}} 儲存庫。必須由具有儲存庫管理專用權的人員來新增他們。如需相關資訊，請參閱[使用 Dedicated GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-getting-started){: new_window}。如果您使用的是專屬受管理版本的 {{site.data.keyword.ghe_short}}，請遵循內部程序。

###管理工具鏈存取權的提示

* 若要管理工具鏈存取權，請在 DevOps 儀表板的**工具鏈**頁面上，按一下要管理的工具鏈，然後按一下**管理**。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**管理**。

* 若要將存取權授與工具鏈組織的所有成員，請按一下**新增組織**。該組織的所有成員都可以檢視工具鏈。

* 您可以將管理者專用權授與組織或使用者。管理者可以修改及刪除工具鏈。若要授與管理者專用權，請選取組織或使用者的**管理**勾選框。

* 如果您選取組織的**管理**勾選框，則該組織的所有成員都會成為管理者。如果您在將管理者專用權授與組織之後，於組織中新增成員，則這些成員的存取權會與組織的其他成員相同。

* 若要將存取權授與具有工具鏈組織成員身分的使用者，請輸入使用者 ID，然後按一下**新增使用者**。使用者可以檢視工具鏈。

* 若要將存取權授與不具有工具鏈組織成員身分的使用者，請遵循下列步驟：

   a. 從功能表列，按一下**管理 > 存取 (IAM)**。

   b. 按一下**從使用者開始存取**。
   
   c. 從您要指派存取權之使用者的列中，選取**動作**功能表，然後按一下**指派存取權**。
   
   d. 選取**使用 Cloud Foundry 指派存取權**。

   e. 選取**指派組織**。

   f. 指派使用者存取權：

     * 選擇要在其中新增使用者的組織。

     * 指派組織角色。

     * 選擇地區。

     * 選擇空間。

     * 指派組織中所選取空間的角色。

     依預設，組織管理員會具有所有與組織相關聯之工具鏈的完整管理者專用權。若要將完整管理者專用權授與使用者，請選取**管理員**角色。「帳單管理員」及「審核員」角色不會影響工具鏈存取權。您稍後可以在「團隊目錄」頁面上變更角色。如需相關資訊，請參閱 [Cloud Foundry 角色](/docs/iam?topic=iam-cfaccess#cfaccess){: new_window}。
     {: tip}

   使用者成為組織成員之後，請回到工具鏈的「管理」頁面，並將使用者新增至工具鏈。  


## 刪除工具鏈
{: #deleting_a_toolchain}

您可以刪除工具鏈，以及指定您要刪除的相關聯工具整合。當您刪除工具鏈時，無法復原刪除。

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下要刪除的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。
1. 按一下**檢視應用程式**旁的**其他動作**功能表。
1. 按一下**刪除**。刪除工具鏈會移除其所有工具整合，這樣可能會刪除那些整合所管理的資源。
1. 鍵入工具鏈名稱，然後按一下**刪除**，來確認刪除。  

 當您刪除 GitHub、{{site.data.keyword.ghe_short}} 或 {{site.data.keyword.gitrepos}} 工具整合時，不會從 GitHub、{{site.data.keyword.ghe_short}} 或 {{site.data.keyword.gitrepos}} 刪除相關聯的儲存庫。您必須手動移除儲存庫。
 {: tip}

##使用指導教學：使用工具鏈
{: #toolchain-tutorial}

請參閱 [IBM&reg; Cloud Garage Method ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage){:new_window} 上的這些指導教學：

  * [使用「開發 Cloud Foundry 應用程式」工具鏈建立及使用您的第一個工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。

  * [將工具鏈新增至應用程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}。

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}。
