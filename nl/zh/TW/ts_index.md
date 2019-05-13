---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 常見問題
{: #ts_cd}

取得使用 {{site.data.keyword.contdelivery_full}} 之常見問題的答案。
{:shortdesc}

## 「工具鏈」頁面為什麼顯示必須要有 {{site.data.keyword.contdelivery_short}} 服務精簡方案？
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} 提供兩種方案：「精簡」及「專業」。如果您有「{{site.data.keyword.contdelivery_short}} 精簡」方案，則可以免費使用工具鏈，最多為方案的限制。錯誤訊息指出您已超出「精簡」方案的一個以上限制。例如，如果您有太多授權使用者與 {{site.data.keyword.contdelivery_short}} 服務實例相關聯，或已執行 {{site.data.keyword.deliverypipeline}} 工作數目上限，則可能會超過方案。如需方案條款的相關資訊，請參閱[方案限制及用量](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage){: new_window}。


## 在 30 天未作用之後，會刪除精簡方案服務中我的 {{site.data.keyword.contdelivery_short}} 服務狀態。未作用的意義為何？
{: #plan_inactivity}
{: faq}

相同的資源群組或 Cloud Foundry 組織內的一個以上工具鏈作用時，就會將 {{site.data.keyword.contdelivery_short}} 服務實例視為作用中。如果使用者透過使用者介面與其互動、觸發交付管線工作、存取 {{site.data.keyword.gitrepos}} 所管理的儲存庫，或 Eclipse Orion {{site.data.keyword.webide}} 工作區使用中，則會將工具鏈視為作用中。若要視為非作用中，所有與 {{site.data.keyword.contdelivery_short}} 服務相關聯的工具鏈都必須沒有所有這些條件持續 30 天。


## 我已建立工具鏈，「工具鏈」頁面為什麼顯示需要 Continuous Delivery 服務？
{: #service_required_resource_group}
{: faq}

位在與工具鏈相同之資源群組或組織中的 {{site.data.keyword.contdelivery_short}} 服務實例方案條款，可管理如何使用服務中所含的一些工具整合（{{site.data.keyword.deliverypipeline}}、Eclipse Orion {{site.data.keyword.webide}} 及 {{site.data.keyword.gitrepos}}）。錯誤訊息指出資源群組或組織未包含必要的 {{site.data.keyword.contdelivery_short}} 服務實例。如需方案條款的相關資訊，請參閱[方案限制及用量](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage){: new_window}。


## 我已更新 Cloud Foundry 組織中工具鏈的資訊，為什麼看不到工具鏈中的變更？
{: #updates_in_cloud_foundry}
{: faq}

當您直接從 Cloud Foundry 更新工具鏈資訊時，可能需要數分鐘的時間，{{site.data.keyword.contdelivery_short}} 服務才會重新整理及顯示變更。例如，如果您新增或移除 Cloud Foundry 組織中的使用者，則可能需要數分鐘的時間，{{site.data.keyword.contdelivery_short}} 才會探索是否有新使用者，以及容許該使用者存取工具鏈。


## 我已在 Cloud Foundry 組織中建立工具鏈，「工具鏈」頁面為什麼顯示需要 Continuous Delivery 服務？
{: #service_required_cloud_foundry}
{: faq}

當您在資源群組或組織中建立沒有 {{site.data.keyword.contdelivery_short}} 服務實例的工具鏈時，工具鏈平台會使用「精簡」方案來嘗試自動建立服務實例。錯誤訊息指出工具鏈平台無法建立服務實例。

當您在美國南部地區以及還沒有 {{site.data.keyword.contdelivery_short}} 實例的 Cloud Foundry 組織中建立工具鏈時，可能發生此錯誤。在美國南部地區中，您必須在資源群組中建立所有新的 {{site.data.keyword.contdelivery_short}} 服務實例。 

您可以在資源群組中建立工具鏈，或在組織中建立已有 {{site.data.keyword.contdelivery_short}} 實例的工具鏈。
  

## 如何將工具鏈從 Cloud Foundry 組織移至資源群組？
{: #toolchain_move_to_resource_group}
{: faq}

尚未提供將工具鏈從 Cloud Foundry 組織自動移轉至資源群組的特性。相反地，您可以在資源群組中手動重新建立工具鏈，然後從 Cloud Foundry 組織中移除原始工具鏈。


## 我嘗試將應用程式部署至 {{site.data.keyword.Bluemix_notm}}，但為什麼會收到錯誤？
{: #org_outofmemory}
{: faq}

嘗試將應用程式部署至 {{site.data.keyword.Bluemix_notm}} 時，如果您收到下列錯誤訊息，則表示組織中的剩餘記憶體數量少於您要部署之應用程式所需的記憶體數量。

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

您可以增加帳戶的記憶體配額，或減少應用程式所使用的記憶體。試用帳戶的記憶體配額上限為 2 GB。若要增加帳戶的記憶體配額，請將試用帳戶轉換為付費帳戶。如需如何將試用帳戶轉換成付費帳戶的相關資訊，請參閱[如何升級或變更帳戶？](/docs/account?topic=account-accountfaqs#changeacct)。若要減少應用程式所使用的記憶體，請使用 {{site.data.keyword.Bluemix_notm}} 主控台或 cf 指令行介面。

如果您使用 {{site.data.keyword.Bluemix_notm}} 主控台，請完成下列步驟：

1. 在應用程式儀表板中，選取您的應用程式。即會開啟應用程式詳細資料頁面。
1. 在「運行環境」窗格中，您可以針對您的應用程式減少記憶體上限及（或）應用程式實例的數目。

如果您使用 cf 指令行介面，請完成下列步驟：

1. 檢查有多少記憶體用於應用程式。cf apps 指令會列出您在現行空間中部署的所有應用程式。也會顯示每個一應用程式的狀態。

	  ```
	  cf apps
	  ```

1. 若要減少應用程式所使用的記憶體量，請減少應用程式實例的數目及（或）記憶體上限：

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```
    
1. 重新啟動應用程式，讓變更生效。


## 我已建立應用程式，但為什麼執行列未在 {{site.data.keyword.webide}} 中顯示 {{site.data.keyword.Bluemix_notm}} Live Sync 圖示？
{: #ts_llz_lkb_3r}
{: faq}

![執行列](images/webide_runbar_light.png)   

在這些情況下，當您在 {{site.data.keyword.webide}} 中編輯 Node.js 應用程式時，執行列中不會有 {{site.data.keyword.Bluemix_notm}} 即時編輯、快速重新啟動及除錯圖示：


* `manifest.yml` 檔案未儲存在專案的最上層。
* 您的應用程式儲存在子目錄中，而非根目錄中，但 `manifest.yml` 檔案中未指定該子目錄的路徑。
* 應用程式未包含 `package.json` 檔案。


如果 `manifest.yml` 檔案未儲存在根目錄中，請將它儲存在該處。如果應用程式儲存在子目錄中，請在 `manifest.yml` 檔案中指定該子目錄的路徑。如果應用程式未包含 `package.json` 檔案，請在與應用程式相同的目錄中建立一個。


## 我已按一下 {{site.data.keyword.webide}} 執行按鈕，日誌檔的位置為何？ 
{: #web_ide_log_files}
{: faq}  

當您按一下「執行」按鈕時，如果從桌面鍵入 `cf push`，則會將工作區內容推送至 Cloud Foundry，且方法與其部署方式相同。您可以從 Cloud Foundry 儀表板找到日誌檔。

如需部署工作區內容的相關資訊，請參閱[從工作區部署應用程式](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy)。


## 如何防止 {{site.data.keyword.webide}} 自動選取 Git 視圖中的所有變更？ 
{: #web_ide_git_view}
{: faq} 

{{site.data.keyword.webide}} 假設每次移至 Git 頁面時，依預設您要將送出的變更推送至程式碼儲存庫。如果您要從 GIT 喜好設定頁面手動選取要確定、同步、重設及取代的資源，則請清除**一律選取變更的檔案**勾選框。


## 為什麼 {{site.data.keyword.webide}} 不支援我所使用的語言？ 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}} 提供大量工具以及 JavaScript、HTML 和 CSS 支援。它也提供大部分熱門語言的語法強調顯示。您無法擴充 {{site.data.keyword.webide}} 以支援特定語言。若要檢視 {{site.data.keyword.webide}} 所支援的完整語言清單，請參閱[支援的語言](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages)。


## 如何找到 {{site.data.keyword.Bluemix_notm}} 及 {{site.data.keyword.contdelivery_short}} 服務的狀態？
{: #toolchains_load}
{: faq}

請檢查「{{site.data.keyword.Bluemix_notm}} 狀態」頁面，以確定是否有已知問題影響 {{site.data.keyword.Bluemix_notm}} 平台及 {{site.data.keyword.Bluemix_notm}} 中的主要服務。

您可以選擇下列其中一個選項來尋找「狀態」頁面：

  * 登入 {{site.data.keyword.Bluemix_notm}} 主控台。從功能表列中，按一下**支援**，然後選取**狀態**。請檢查針對 ![部分問題](../../get-support/images/some_issues.svg) 圖示列出的資源。此圖示可能指出運作中斷。
  * 直接在 [{{site.data.keyword.Bluemix_notm}} - 系統狀態 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/status){: new_window} 存取它。

如需「{{site.data.keyword.Bluemix_notm}} 狀態」頁面的相關資訊，請參閱 [Viewing {{site.data.keyword.Bluemix_notm}} status](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status){: new_window}。


## 如何在管線工作之間傳遞構件？
{: #artifacts_pipeline_jobs}
{: faq}

因為階段中的所有管線工作都會收到相同的階段輸入，所以您無法傳遞相同階段中工作之間的構件。不過，建置工作會產生其他階段中工作可使用的構件。若要在兩個工作之間傳遞構件，請將每個工作移至不同的階段。如需管線工作的相關資訊，請參閱[工作](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs)。


## 是否有管線工作可執行的時間上限？
{: #pipeline_jobs_time_limit}
{: faq}

每個管線工作最多可以執行 60 分鐘。如果工作超出此時間限制，則工作會失敗。檢查管線工作所執行的工作是否可以分為較小的步驟。您可以將管線工作分為數個執行少於 60 分鐘的較短管線工作。


## 管線安全內容的安全程度為何？
{: #pipeline_secure_properties}
{: faq}

管線安全內容是使用 AES-128 所加密，並在傳遞至管線 Script 之前立即予以解密。在內容使用者介面及管線日誌檔中使用星號，也可以遮罩處理這些內容。將資料寫入至管線工作的日誌檔之前，會掃描管線安全內容中所有值的完全相符項目。如果找到相符項目，則會使用星號予以遮罩處理。當您在僅遮罩處理完全相符項目之後使用安全內容及日誌檔時，請小心。 
