---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 入門指導教學
{: #cd_getting_started}

使用 {{site.data.keyword.contdelivery_full}} 來採用 DevOps 方式，它包含自動進行應用程式建置及部署的開放式工具鏈。您可以從建立支援開發、部署及操作作業的簡單部署工具鏈開始。
{: shortdesc}

##必要條件
{: #cd_prereqs}

在您從範本建立持續交付工具鏈之前，必須先建立 {{site.data.keyword.contdelivery_short}} 實例，方法是從 {{site.data.keyword.Bluemix_notm}} 型錄選取它。工具鏈會整合用於規劃、開發、部署管線以及管理應用程式的工具。您隨時可以從工具鏈新增或移除工具。如果您已有工具鏈，則可以[檢視現有工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}。如需使用工具鏈的相關資訊，請參閱[使用工具鏈](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}。

如果您已有 {{site.data.keyword.contdelivery_short}} 實例，則可以[建立工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops/create){: new_window} 或[檢視現有工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}。
{: tip}

##步驟 1：選取工具鏈範本
{: #select_a_toolchain_template}

1. 在**建立工具鏈**頁面上，按一下[工具鏈範本 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/devops/create){: new_window}。
1. 檢閱即將建立之工具鏈的圖表。此圖會顯示每個工具整合在工具鏈中的生命週期階段。

 有一些工具鏈範本會有多個工具整合實例。例如，{{site.data.keyword.Bluemix_notm}} Public 上的「微服務」工具鏈範本包含三個 GitHub 實例及三個 Delivery Pipeline 實例，三個微服務各有一個。
 {: tip}

 下列影像中的圖表是範例。當您建立工具鏈時，圖表會顯示每一個屬於工具鏈一部分的工具整合。![「工具鏈」圖表](images/toolchain_diagram2.png)
 
##步驟 2：建立工具鏈 
{: #create_a_toolchain}
 
1. 檢閱工具鏈設定的預設資訊：

 * 在 {{site.data.keyword.Bluemix_notm}} 中，可透過工具鏈名稱來識別工具鏈。如果您要使用不同的名稱，請變更工具鏈的名稱。
 * 要在其中建立工具鏈的地區。如果您要使用不同的地區，請從可用地區清單中選取它。
 * 要在其中建立工具鏈的資源群組或組織。按一下鏈結，以切換選取資源群組與組織。如果您要使用不同的資源群組或組織，請從可用資源群組或組織清單中選取它。
 
   資源群組只能在美國南部地區使用。
   {: tip}
 
1. 在「工具整合」區段中，選取您要配置給工具鏈的每一個工具整合。有些工具整合不需要進行配置。如需配置工具整合的相關資訊，請參閱[配置工具整合](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}。
1. 按一下**建立**。會自動執行數個步驟來設定工具鏈。視您選取的工具鏈範本以及使用的是 {{site.data.keyword.Bluemix_notm}} Public 還是 {{site.data.keyword.Bluemix_notm}} Dedicated 而定，設定的工具整合會有所不同。例如，當您在 {{site.data.keyword.Bluemix_notm}} Public 上建立「微服務」工具鏈時，會執行下列步驟：

 * 建立工具鏈。
 * 如果您已配置 Delivery Pipeline，則會建立及執行管線。
 * 如果您已配置 Sauce Labs，則會設定工具鏈將 Sauce Labs 測試工作新增至管線。
 * 如果您已配置 PagerDuty，則會設定工具鏈將警示通知傳送至所指定的 PagerDuty 服務。
 * 如果您已配置 Slack，則會設定工具鏈將部署狀態通知傳送至所指定的 Slack 頻道。
 * 如果您已配置原始碼工具整合（例如 GitHub），則會將範例 GitHub 儲存庫複製到 GitHub 帳戶。

##後續步驟
{: #next_steps}

請參閱 [IBM&reg; Cloud Garage Method ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage){:new_window} 上的其中一個指導教學：

  * [使用「開發 Cloud Foundry 應用程式」工具鏈建立及使用您的第一個工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。

  * [將工具鏈新增至應用程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}。
