---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-21"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 常見問題
{: #ts_cd}

取得使用 {{site.data.keyword.contdelivery_full}} 之常見問題的答案。
{:shortdesc}


## 我嘗試將 GitHub 工具整合新增至工具鏈，但為什麼未新增工具整合？
{: #cannot_authorize_github}

如果 {{site.data.keyword.Bluemix_notm}} 未獲授權存取 GitHub 帳戶，則不會將工具整合新增至工具鏈。

如果您要在建立工具鏈時配置 GitHub 工具整合，請遵循下列步驟以使用 GitHub 進行授權：

  1. 在「可配置的整合」區段中，按一下 **GitHub**。
  1. 如果您要在「{{site.data.keyword.Bluemix_notm}} 公用」上建立工具鏈，但未授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub，請按一下**授權**來移至 GitHub 網站。
  1. 如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。

如果您已有工具鏈，請更新 GitHub 工具整合的配置：

 1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
 1. 在 GitHub 卡片上，按一下功能表，然後按一下**配置**。
 1. 更新配置設定，以授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub。按一下**授權**，以移至 GitHub 網站。如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。
 1. 完成設定的更新後，請按一下**儲存整合**。


## 我嘗試建立工具鏈，但為什麼會收到錯誤？
{: #cannot_create_toolchain}

嘗試建立工具鏈時，如果您收到下列錯誤訊息，請從組織中移除一個以上的工具鏈，然後重新建立工具鏈。

`This organization contains 200 toolchains, which is the maximum limit. Before you can add another toolchain, remove one or more toolchains from the organization.`


## 我嘗試將應用程式部署至 {{site.data.keyword.Bluemix_notm}}，但為什麼會收到錯誤？
{: #org_outofmemory}

嘗試將應用程式部署至 {{site.data.keyword.Bluemix_notm}} 時，如果您收到下列錯誤訊息，則表示組織中的剩餘記憶體數量少於您要部署之應用程式所需的記憶體數量。

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

您可以增加帳戶的記憶體配額，或減少應用程式所使用的記憶體。試用帳戶的記憶體配額上限為 2 GB。
若要增加帳戶的記憶體配額，請將試用帳戶轉換為付費帳戶。如需如何將試用帳戶轉換成付費帳戶的相關資訊，請參閱[付費帳戶](/docs/pricing/index.html#pay-accounts)。若要減少應用程式所使用的記憶體，請使用 {{site.data.keyword.Bluemix_notm}} 主控台或 cf 指令行介面。

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


## 我已建立應用程式，但為什麼執行列未在 Eclipse Orion Web IDE 中顯示 {{site.data.keyword.Bluemix_notm}} Live Sync 圖示？
{: #ts_llz_lkb_3r}

![執行列](images/webide_runbar_light.png)   

在這些情況下，當您在 Web IDE 中編輯 Node.js 應用程式時，執行列中不會有 {{site.data.keyword.Bluemix_notm}} 即時編輯、快速重新啟動及除錯圖示：


* `manifest.yml` 檔案未儲存在專案的最上層。
* 您的應用程式儲存在子目錄中，而非根目錄中，但 `manifest.yml` 檔案中未指定該子目錄的路徑。
* 應用程式未包含 `package.json` 檔案。


如果 `manifest.yml` 檔案未儲存在根目錄中，請將它儲存在該處。如果應用程式儲存在子目錄中，請在 `manifest.yml` 檔案中指定該子目錄的路徑。如果應用程式未包含 `package.json` 檔案，請在與應用程式相同的目錄中建立一個。


## 我已按一下工具鏈以檢視其「概觀」頁面，但為什麼未載入工具鏈？
{: #toolchains_load}

請檢查「{{site.data.keyword.Bluemix_notm}} 狀態」頁面，以確定是否有已知問題影響 {{site.data.keyword.Bluemix_notm}} 平台及 {{site.data.keyword.Bluemix_notm}} 中的主要服務。

您可以選擇下列其中一個選項來尋找「狀態」頁面：

  * 登入 {{site.data.keyword.Bluemix_notm}} 主控台。從功能表列中，按一下**支援**，然後選取**狀態**。請檢查針對 ![部分問題](../../get-support/images/some_issues.svg) 圖示列出的資源。此圖示可能指出運作中斷。
  * 直接在 [{{site.data.keyword.Bluemix_notm}} - 系統狀態 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/status){: new_window} 存取它。

如需「{{site.data.keyword.Bluemix_notm}} 狀態」頁面的相關資訊，請參閱 [Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/get-support/ViewStatus.html#viewing-bluemix-status)。


## 我已配置工具鏈的工具整合，但為什麼並未配置它？
{: #tool_integration_error}

新增工具整合時，工具鏈會與工具整合所代表的工具進行通訊，來佈建任何必要資源，以及建立它們與工具鏈的關聯。如果在設定處理程序期間發生錯誤，或工具鏈與工具之間的通訊未適當地完成，則工具整合會進入錯誤狀態。


 ![設定失敗錯誤](images/tool_setup_failed.png)

您可以嘗試重新配置工具整合：

1. 在其工具卡片上，將游標移至 `Setup failed` 訊息上方，然後按一下**重新配置**。

 ![「重新配置」按鈕](images/tool_reconfigure.png)

1. 確定您使用的是有效的配置參數。如果是無效的配置導致錯誤，則會顯示錯誤訊息；例如，`The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`。更新工具整合的設定，然後按一下**儲存整合**。
1. 如果是通訊問題導致錯誤，請按一下**儲存整合**以重試。
