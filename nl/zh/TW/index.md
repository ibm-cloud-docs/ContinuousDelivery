---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 開始使用 Continuous Delivery
{: #cd_getting_started}

使用 {{site.data.keyword.contdelivery_full}} 來採用 DevOps 方式，它包含自動進行應用程式建置及部署的開放式工具鏈。您可以從建立支援開發、部署及操作作業的簡單部署工具鏈開始。
{: shortdesc}

從 {{site.data.keyword.Bluemix_notm}} 型錄中選取 {{site.data.keyword.contdelivery_short}} 以建立其實例之後，您可以從範本建立持續交付工具鏈，或使用現有工具鏈。
 ![Continuous Delivery 歡迎使用頁面](images/cd_landing_page2.png)

* 若要從範本來建立及配置持續交付工具鏈，請按一下**[從這裡開始](#starting_from_a_toolchain_template)**。工具鏈會整合用於規劃、開發、部署管線以及管理應用程式的工具。您隨時可以從工具鏈新增或移除工具。
* 如果您已有工具鏈，請在「從工具鏈範本開始」區段中按一下**檢視工具鏈**。如需使用工具鏈的相關資訊，請參閱[使用工具鏈](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}。

##{{site.data.keyword.contdelivery_short}} 概觀
{: #cd_overview}

使用 {{site.data.keyword.contdelivery_short}} 時，您可以使用 DevOps 作法及業界領先工具來建置、測試及提供應用程式。
{:shortdesc}

{{site.data.keyword.contdelivery_short}} 服務支援 DevOps 工作流程：

 * 您可以建立整合式 DevOps 開放式[工具鏈](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window}，來啟用支援開發、部署及操作作業的工具整合。

  工具鏈是一組整合式工具，可用來協同開發、建置、部署、測試及管理應用程式，並且可以使作業能重複執行，也較容易管理。工具鏈可以包含開放程式碼工具、{{site.data.keyword.Bluemix_notm}} 服務（例如 [{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window}）和協力廠商工具（例如 GitHub、PagerDuty 及 Slack）。 
  
  **附註**：{{site.data.keyword.DRA_short}} 只能在美國南部地區使用。

 * 使用自動化[管線](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window}進行持續交付。

  自動進行建置、單元測試、部署及其他作業。以最少人為介入的可重複方式進行建置、測試及部署。隨時準備好投入正式作業。

 * 使用 [Web 型 IDE](/docs/services/ContinuousDelivery/web_ide.html){: new_window}，從任何位置編輯及推送程式碼。

  在 GitHub 中，建立、編輯、執行、除錯及完成來源控制作業。平順地從編輯程式碼，移至將程式碼部署至正式作業。 
  
 * 使用 IBM 所管理並以 GitLab Community Edition 為建置基礎的 [Git 儲存庫及問題追蹤器](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window}，來與團隊分工合作並且管理原始碼。

  透過讓程式碼更為安全的精密存取控制，來管理 Git 儲存庫。透過合併要求，來檢閱程式碼並加強協同作業。透過問題追蹤器，來追蹤問題與共用構想。在 Wiki 系統上記載專案。


##從工具鏈範本開始
{: #starting_from_a_toolchain_template}

若要從[範本 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops/create){: new_window} 來建立及配置持續交付工具鏈，請執行下列動作：

1. 在**建立工具鏈**頁面上，按一下工具鏈範本。
1. 檢閱即將建立之工具鏈的圖表。此圖會顯示每個工具整合在工具鏈中的生命週期階段。

 **提示**：有一些工具鏈範本會有多個工具整合實例。例如，「{{site.data.keyword.Bluemix_notm}} 公用」上的「微服務」工具鏈範本包含三個 GitHub 實例及三個 Delivery Pipeline 實例，三個微服務各有一個。

 下列影像中的圖表是範例。當您建立工具鏈時，圖表會顯示每一個屬於工具鏈一部分的工具整合。![「工具鏈」圖表](images/toolchain_diagram2.png)
1. 檢閱工具鏈設定的預設資訊：

 * 在 {{site.data.keyword.Bluemix_notm}} 中，可透過工具鏈名稱來識別工具鏈。如果您要使用不同的名稱，請變更工具鏈的名稱。
 * 要在其中建立工具鏈的地區。如果您要使用不同的地區，請從可用地區清單中選取它。
 * 要在其中建立工具鏈的組織。如果您要使用不同的組織，請從可用組織清單中選取它。
 
1. 在「工具整合」區段中，選取您要配置給工具鏈的每一個工具整合。有些工具整合不需要進行配置。如需配置工具整合的相關資訊，請參閱[配置工具整合](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}。
1. 按一下**建立**。會自動執行數個步驟來設定工具鏈。視您選取的工具鏈範本以及使用的是「{{site.data.keyword.Bluemix_notm}} 公用」還是「{{site.data.keyword.Bluemix_notm}} 專用」而定，設定的工具整合會有所不同。例如，當您在「{{site.data.keyword.Bluemix_notm}} 公用」上建立「微服務」工具鏈時，會執行下列步驟：

 * 建立工具鏈。
 * 如果您已配置 Delivery Pipeline，則會建立及執行管線。
 * 如果您已配置 Sauce Labs，則會設定工具鏈將 Sauce Labs 測試工作新增至管線。
 * 如果您已配置 PagerDuty，則會設定工具鏈將警示通知傳送至所指定的 PagerDuty 服務。
 * 如果您已配置 Slack，則會設定工具鏈將部署狀態通知傳送至所指定的 Slack 頻道。
 * 如果您已配置原始碼工具整合（例如 GitHub），則會將範例 GitHub 儲存庫複製到 GitHub 帳戶。
