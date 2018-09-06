---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 在升級 {{site.data.keyword.jazzhub_short}} 專案之後開始使用工具鏈
{: #toolchains_post_upgrade}

已在 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}} 服務中，將 hub.jazz.net 中的 {{site.data.keyword.jazzhub}} 專案升級至工具鏈。 

hub.jazz.net 中的 {{site.data.keyword.jazzhub_short}} 已遭淘汰。 

對於 DevOps 專案，使用 [{{site.data.keyword.contdelivery_short}} 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops){:new_window}。如果您是 {{site.data.keyword.Bluemix_notm}} 新手，請務必參閱 [{{site.data.keyword.Bluemix_notm}} 概觀](/docs/overview/ibm-cloud.html#overview)。

{: shortdesc}

## 尋找已從專案中建立的工具鏈
{: #find_toolchain}

確認升級完成，方法是移至[工具鏈頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops/toolchains){: new_window}，並驗證您看到的工具鏈名稱符合 hub.jazz.net 專案的名稱。如果已自動升級您的專案，請記住下列警告：
   - 如果另一個工具鏈已在升級專案之前使用您專案的名稱，則為您的專案所建立的新工具鏈可能不會有您專案的確切名稱。 
   - 如果您看不到專案的工具鏈，請切換至您所屬的任何其他組織，並在該處檢查工具鏈。
   
## 工具鏈概觀
{: #compare_toolchains}

如果您在 hub.jazz.net 上有一個以上的專案，則除非升級失敗，否則會將它們自動升級至 {{site.data.keyword.contdelivery_short}} 服務中的工具鏈。因為 IBM Cloud 帳戶或組織無效，所以升級可能會失敗。已透過電子郵件通知這些帳戶及組織擁有者有關失敗以及處理它們所需的特定動作。如果您需要找到已升級專案之工具鏈的協助，請聯絡[支援中心 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}。 

工具鏈就像專案，但有一些重要差異：

- 專案只能有一個儲存庫及管線。視需要，工具鏈可以有任意數目的儲存庫及管線。
- 工具鏈可以包含專案中無法使用的工具（例如 Slack、Sauce Labs、PagerDuty 及 {{site.data.keyword.DRA_full}}）。

 {{site.data.keyword.DRA_short}} 只能在美國南部地區使用。
 {: tip}
 
- 在專案中，成員資格是在專案層次進行維護。工具鏈的存取權是透過 {{site.data.keyword.Bluemix_notm}} 組織及工具鏈進行管理。若要使用工具鏈，您必須是包含該工具鏈的組織成員。工具鏈擁有者可以進一步控制誰可以存取工具鏈及其可執行的作業。如需詳細資料，請參閱[開始使用工具鏈](#upgrade_next_steps)中的步驟 2。
- 根據您在 hub.jazz.net 的專案中使用的儲存庫類型，工具鏈可以包含 GitHub.com 儲存庫或 {{site.data.keyword.gitrepos}} 儲存庫。

您可以在 [YouTube ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://youtu.be/2SIPE1e7NJ4){: new_window} 上或從[開始使用 {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html) 中進一步瞭解工具鏈。

## 開始使用工具鏈
{: #upgrade_next_steps}

1. 將工具鏈的存取權授與團隊成員。
    - 每一個團隊成員都必須具有有效的 {{site.data.keyword.Bluemix_notm}} 帳戶。沒有帳戶的團隊成員必須進行[註冊 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/registration){:new_window}。
    - 從工具鏈「管理」頁面中，將工具鏈存取權授與組織成員。在升級處理程序中，會將現有專案成員新增為工具鏈成員。如需工具鏈存取控制的相關資訊，請參閱[管理存取權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}。
    - 如果使用者不是工具鏈所屬組織的成員，請從「管理組織」頁面中將他們新增至組織。
      
    - 如果您的工具鏈使用 {{site.data.keyword.gitrepos}}，則會將所有具有有效 {{site.data.keyword.Bluemix_notm}} ID 的 JazzHub 專案成員新增至 {{site.data.keyword.gitrepos}} 儲存庫，而他們對此儲存庫的專用權與在 JazzHub 專案中相同。如果您的 JazzHub 專案包括沒有有效 {{site.data.keyword.Bluemix_notm}} ID 的成員，則他們可以登錄一個。在他們登錄之後，您就可以將他們新增至儲存庫。如需管理組織的相關資訊，請參閱[管理組織及空間 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/account/orgs_spaces.html#orgsspacesusers){:new_window}。

2. 如果您使用的是 {{site.data.keyword.gitrepos}}，請使用個人存取記號或 SSH 金鑰進行鑑別。如需 SSH 金鑰的相關資訊，請參閱[建立個人存取記號或 SSH 金鑰來進行鑑別](/docs/services/ContinuousDelivery/git_working.html#git_authentication)。若要從外部 Git 用戶端透過 https 進行鑑別，請遵循下列步驟：
    1. 移至 {{site.data.keyword.gitrepos}} 使用者設定的[存取記號頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window}。
    2. 建立使用 **api** 作為範圍的個人存取記號。
    3. 移至[帳戶頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/profile/account){:new_window}，並針對 {{site.data.keyword.gitrepos}} 尋找您的使用者名稱。您的使用者名稱會列在「變更使用者名稱」區段中，並顯示為任何您建立的個人儲存庫的 URL 的第一個部分。
    4. 若要從外部 Git 用戶端透過 HTTPS 向 {{site.data.keyword.gitrepos}} 進行鑑別，請使用您的使用者名稱及個人存取記號。
    5. 如果您要重複使用 JazzHub Git 儲存庫的本端儲存庫，請將儲存庫指向 {{site.data.keyword.gitrepos}} 中的新儲存庫。從終端機 Shell 中，切換至在其中複製 JazzHub Git 儲存庫的目錄。輸入 `git remote set-url` 指令：`git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        若要檢查哪些遠端 URL 設為哪些遠端名稱，請使用 `git remote -v` 指令。預設遠端名稱是 `origin`。如果您有更進階的安裝，則指令的形式如下：`git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

3. 選用項目：若要探索您專案的開發成熟度、團隊的作法，以及程式碼庫的品質，請將 IBM Cloud {{site.data.keyword.DRA_short}} 新增至工具鏈。{{site.data.keyword.DRA_short}} 會將開發人員、團隊及部署分析人員套用至 DevOps 專案。如需相關資訊，請參閱[開始使用 {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html)。

  {{site.data.keyword.DRA_short}} 只能在美國南部地區使用。
  {: tip}


## 疑難排解
{: #upgrade_troubleshoot}

如果您發生專案升級相關問題，請將問題張貼至[支援討論區 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}。在討論區貼文中，併入 {{site.data.keyword.jazzhub_short}} 專案及 {{site.data.keyword.contdelivery_short}} 工具鏈的 URL，並將貼文標上 `devops-services` 標籤。


## 常見問題集
{: #upgrade_faq}

### 我的 JazzHub 專案與英國地區相關聯，但我的工具鏈在美國南部地區。如何執行此項程序？
{: #faq_region}

hub.jazz.net 的專案和工具鏈都在美國南部地區進行管理。如果您的專案已配置成將應用程式部署至不同地區（例如英國地區），則工具鏈也仍然會將應用程式部署至該地區。因此，資料管理所在位置其實沒有什麼改變。工具鏈未來將可在更多地區使用。

### 升級之後，Track &amp; Plan 中的工作項目及儀表板會發生什麼情況？
{: #faq_tp}

{{site.data.keyword.contdelivery_short}} 服務透過 {{site.data.keyword.gitrepos}} 提供問題追蹤功能，這是由 IBM 管理，並且是以 GitLab Community Edition 為基礎。{{site.data.keyword.contdelivery_short}} 也支援整合其他規劃及問題追蹤工具，例如 GitHub Issues 及 JIRA。

在自動升級處理程序期間，已將 Track &amp; Plan 工作項目移轉至 Git Issues。GitHub Issues 和 {{site.data.keyword.gitrepos}} 提供看板與問題追蹤，以便進行規劃。若要進一步瞭解 Issue Board（這是 Git Repos and Issue Tracking 中的看板特性），請參閱 [Issue Board ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}。

如果您需要與已淘汰 JazzHub Track &amp; Plan 的功能相同的客戶，則在選取的國家或地區中有一項新的 IBM Track and Plan on Cloud 服務可以依每月每位使用者購買。使用這項雲端服務，您會在單一承租戶雲端訂閱中獲得完整的功能，相等於 Rational Team Concert&trade; 貢獻者授權。

這項新的 IBM Track and Plan on Cloud 服務提供的功能遠比已淘汰的 JazzHub Track &amp; Plan 更豐富，並且支援處理程序自訂作業、專案階層、SAFe&reg; 以及許多其他敏捷式和混合式方法，也提供成長超越單一專案的可擴充性。它是根據最新版本的 Rational Team Concert 6.0.3，且在未來 60 天內將為 6.0.4 版，而 JazzHub Track &amp; Plan 則是根據 Rational Team Concert 5.x。您可以透過其他服務將資料移轉到 IBM Track and Plan on Cloud。您可以與 [Tom Hollowell ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](mailto:trhollow@us.ibm.com){:new_window}（Connected Products SaaS 業務主管）聯絡，以取得相關資訊。

如需 IBM Track and Plan on Cloud 的相關資訊，或是想要線上購買，請造訪 [IBM Marketplace ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}。

若要購買 Build Automation 及 Source Code Management，可以選擇 [Rational Team Concert on Cloud ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window}。

### 升級之後，我的程式碼儲存庫會發生什麼情況？
{: #faq_repo}

升級之後，新的 Git 服務會類似於您先前的服務。如果您已搭配使用 github.com 與 JazzHub 專案，則工具鏈會連接至相同的 GitHub 儲存庫。如果您的 JazzHub 專案使用 IBM Hosted Git，則會將該儲存庫的內容複製到 {{site.data.keyword.gitrepos}}（這是 {{site.data.keyword.contdelivery_short}} 的一部分且由 IBM 管理）中的新儲存庫。

如需升級處理程序中各種儲存庫處理方式的相關資訊，請參閱下表。

|專案儲存庫|專案類型	|工具鏈儲存庫|
|:----------|:------------------------------|:------------------|
|github.com 		|專用或公用|具有 {{site.data.keyword.Bluemix_notm}} Public 的相同 github.com 儲存庫。|
|hub.jazz.net/git		|專用或公用|{{site.data.keyword.gitrepos}} 中具有 {{site.data.keyword.Bluemix_notm}} Public 的新專用或公用儲存庫。|
|Jazz SCM		|專用或公用|{{site.data.keyword.gitrepos}} 中具有 {{site.data.keyword.Bluemix_notm}} Public 的新專用或公用儲存庫。|
{: caption="表 1. 對映至工具鏈儲存庫的專案儲存庫" caption-side="top"}


### 升級之後，我專案中的建置定義會發生什麼情況？
{: #faq_build}

如果您使用 Jazz 而非 Delivery Pipeline 來建置原始碼，則必須將建置定義手動移轉至工具鏈中的 Delivery Pipeline。

如果您使用 Jazz SCM 作為來源儲存庫，且使用 Delivery Pipeline 建置程式碼，則會將 Jazz SCM 中的原始檔自動移至 Git 儲存庫。您的 Delivery Pipeline 配置會維持相同，只除了它會使用來自 Git 儲存庫的原始檔，而不是來自 Jazz SCM 的原始檔。

### 我必須為已升級至工具鏈的專案建立組織，才能將信用卡新增至帳戶。我的信用卡會被收費嗎？
{: #faq_charges}

身為[隨收隨付制客戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}，如果您使用的任何運行環境、服務或元件超過其在 {{site.data.keyword.Bluemix_notm}} 型錄中所列的免費額度，則會向您收費。如需用量預估，請參閱[定價單 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}。如需 Continuous Delivery 的現行定價，請參閱 [{{site.data.keyword.Bluemix_notm}} 型錄 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}。

如果您是 IBM 員工，則可以按照內部 IBM 專案將帳單計入部門，來代替個人信用卡。如果您需要使用超過 IBM 員工免費額度的資源，請建立支援問題單。

### 我找不到或無法存取工具鏈。我該怎麼辦？
{: #faq_find}

工具鏈是在 {{site.data.keyword.Bluemix_notm}} 組織中進行管理。升級處理程序會將 JazzHub 專案的所有成員都新增至工具鏈。不過，除非 {{site.data.keyword.Bluemix_notm}} 組織的擁有者將那些使用者新增至組織，否則他們看不到工具鏈。

若要存取您的工具鏈，請移至 {{site.data.keyword.Bluemix_notm}}，並按一下功能表圖示，然後按一下**服務 &gt; DevOps**。即會開啟「工具鏈」頁面。請確定您在美國南部地區，而且您在包含工具鏈的組織中。如果您的工具鏈未列在「工具鏈」頁面上，請參閱[此常見問題 (FAQ) 項目](#faq_uk)。

### 我的專案與英國地區相關聯。升級之後，我看到錯誤訊息、我的同事無法存取工具鏈，而且我在 {{site.data.keyword.Bluemix_notm}} 的「工具鏈」頁面上看不到工具鏈。這是怎麼回事？
{: #faq_uk}

**完整問題：**

根據專案設定，我的 JazzHub 專案與 {{site.data.keyword.Bluemix_notm}} 英國地區相關聯。我已驗證我的專案設定，方法是移至其在 JazzHub 上的概觀頁面，並按一下**設定**圖示（看起來像齒輪），然後按一下**選項 &gt; 將此設為 {{site.data.keyword.Bluemix_notm}} 專案：地區**。在我將專案升級至美國中的工具鏈之後，發生下列問題：

   1. 當我選取美國組織時，看到一則訊息，指出組織在美國南部地區沒有空間，而且系統會提示我建立空間。我不要在美國執行任何作業。
   
   2. 我的一些同事無法存取工具鏈，雖然他們被列為原始 JazzHub 專案中的成員。如果他們嘗試從英國地區的應用程式概觀頁面中按一下**檢視工具鏈**來開啟工具鏈，則會看到「拒絕存取」訊息。
   
   3. 雖然我可以從英國地區的應用程式概觀頁面中按一下**檢視工具鏈**直接存取工具鏈，但是在 [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} 看不到我的「工具鏈」頁面上列出此工具鏈。我收到無法修改工具鏈的錯誤，或收到沒有工具鏈而需要建立一個的錯誤。 

**回答：**

如果您來自非美國 {{site.data.keyword.Bluemix_notm}} 組織，而且在升級之前未明確地將組織展開至美國南部地區，則可能會發生這些問題。您可以開啟「工具鏈」頁面來確認這種情況。您將會在頁面的開頭看到地區及組織。 

發生的情況是在升級時，非美國組織不在美國，因此升級會查閱您剛好可存取的另一個組織，以為您選取另一個組織。

如果您在美國切換至該 {{site.data.keyword.Bluemix_notm}} 組織，則可以找到工具鏈。如果您將同事新增至該組織，則他們會獲得存取權。此工具鏈可以繼續部署至您的非美國組織。唯一的問題是這兩個組織不同；您無法跨組織自動執行使用者管理。

如果您要工具鏈位在符合非美國組織的美國組織中，請遵循下列步驟：

   1. 登入 [https://console.bluemix.net ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net){: new_window}，然後選取您所來自的非美國地區及組織。
   
   2. 在 {{site.data.keyword.Bluemix_notm}} 標頭中，切換至美國南部地區。系統會提示您在該地區中建立空間。
   
   3. 在美國南部地區中建立空間，以將組織展開至該地區。 
   
   4. 刪除已透過升級處理程序建立的工具鏈。 
   
      不會自動刪除 Git 儲存庫。您可能要手動刪除它，或立即將它重新命名。如果您已對它進行變更，則可以更新未來的工具鏈，以在稍後使用。
      {: tip}

   5. 回到 JazzHub 專案。它應該針對另一個升級嘗試自行重設。如果未重設，請聯絡 hub@jazz.net，並提供專案的 URL。
   
   6. 重新啟動升級處理程序，並務必選取美國的適當組織，並符合您在非美國地區的組織名稱。
   
   7. 如果您已從前一次工具鏈升級嘗試保留或重新命名 Git 儲存庫（請參閱步驟 4），則可以重新配置工具鏈中的 Git 卡片，以改為指向此 Git 儲存庫 URL。變更會自動反映在管線中。若要確認，請檢查「建置」階段上的「輸入」標籤。
