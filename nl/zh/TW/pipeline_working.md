---

copyright:
  years: 2015, 2018
lastupdated: "2018-7-19"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# 使用管線 {: #pipeline-working}

若要自動建置及部署至 {{site.data.keyword.Bluemix}}，請使用 {{site.data.keyword.contdelivery_full}} 管線。
{: shortdesc}

使用管線，有數種建置類型可供您選擇。您提供建置 Script，{{site.data.keyword.contdelivery_short}} 便會執行它，不需要設定建置系統。接著只要按一下，您便可將應用程式自動部署至一個或多個 {{site.data.keyword.Bluemix_notm}} 空間、公用 Cloud Foundry 伺服器，或 {{site.data.keyword.containerlong}} 上的 Docker 容器。

建置工作會從 Git 儲存庫編譯及包裝您的應用程式原始碼。建置工作會產生可部署的構件，例如 WAR 檔或 {{site.data.keyword.containerlong_notm}} 的 Docker 容器。此外，您可以在建置內自動執行單元測試。您可以設定建置工作，以在每次推送確定時觸發建置。

部署工作會取得建置工作的輸出，並將它部署至 {{site.data.keyword.containerlong_notm}} 或 Cloud Foundry 伺服器，例如 {{site.data.keyword.Bluemix_notm}}。

您可以部署至一或多個地區及服務。例如，您可以設定 {{site.data.keyword.deliverypipeline}} 使用一個以上的服務、在一個地區中測試，以及部署至多個地區進行正式作業。如需相關資訊，請參閱[地區](/docs/overview/whatisbluemix.html#ov_intro_reg){: new_window}。

##建立管線

您可以使用下列任何方法來建立管線：

   * [從現有 Cloud Foundry 應用程式建立工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html#creating_a_toolchain_from_an_app){: new_window}。產生的工具鏈包含管線。

   * [從範本建立工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html#creating_a_toolchain_from_a_template){: new_window}，而範本包含至少一個管線。

   * [新增 {{site.data.keyword.deliverypipeline}} 工具整合](/docs/services/ContinuousDelivery/toolchains_integrations.html#deliverypipeline){: new_window}至現有工具鏈。
   
從 {{site.data.keyword.deliverypipeline}} 中變更配置；檢查建置的狀態、已部署的應用程式及最近的部署；查看最新日誌及部署詳細資料，或者刪除管線。
