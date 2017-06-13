---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# {{site.data.keyword.contdelivery_short}} 疑難排解
{: #ts_cd}

取得使用 {{site.data.keyword.contdelivery_full}} 之一般疑難排解問題的答案。
{:shortdesc}


## 無法授權使用 GitHub
{: #cannot_authorize_github}

您未獲授權使用 GitHub。
{:shortdesc}

如果您未獲授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶，則可能會發生下列任何問題：
{: tsSymptoms}

 * 當您嘗試將 GitHub 工具整合新增至工具鏈時，未新增工具整合。
 * 當您將變更推送至 GitHub 或 GitHub Enterprise 儲存庫時，未自動執行管線。

{{site.data.keyword.Bluemix_notm}} 未獲授權存取 GitHub。  
{: tsCauses}

如果您要在建立工具鏈時配置 GitHub 工具整合，請遵循下列步驟：
{: tsResolve}

  1. 在「可配置的整合」區段中，按一下 **GitHub**。
  1. 如果您在「{{site.data.keyword.Bluemix_notm}} 公用」上建立工具鏈，但並未授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub，請按一下**授權**來移至 GitHub 網站。
  1. 如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。如果您有作用中的 GitHub 階段作業，但最近未輸入過密碼，則系統可能會提示您輸入 GitHub 密碼進行確認。

如果您已有工具鏈，請更新 GitHub 工具整合的配置：

 1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
 1. 在 GitHub 卡片上，按一下功能表，然後按一下**配置**。
 1. 更新配置設定，以授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub。按一下**授權**，以移至 GitHub 網站。如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。如果您有作用中的 GitHub 階段作業，但最近未輸入過密碼，則系統可能會提示您輸入 GitHub 密碼進行確認。
 1. 完成設定的更新後，請按一下**儲存整合**。


## 無法建立工具鏈
{: #cannot_create_toolchain}

建立工具鏈時會顯示錯誤。
{:shortdesc}

當您建立工具鏈，您會看到下列錯誤訊息：
{: tsSymptoms}

`This organization contains 200 toolchains, which is the maximum limit. Before you can add another toolchain, remove one or more toolchains from the organization.`

組織 (org) 中的工具鏈不得超過 200 個。  
{: tsCauses}

從組織移除一個以上的工具鏈，然後重新建立工具鏈。
{: tsResolve}


## 已超出組織的記憶體限制
{: #org_outofmemory}

如果您已超出組織的記憶體限制，可能無法將應用程式部署到 {{site.data.keyword.Bluemix_notm}}。您可以減少應用程式所使用的記憶體，或增加帳戶的記憶體配額。試用帳戶的記憶體配額上限為 2 GB，只能藉由移到付費帳戶來增加。

將應用程式部署至 {{site.data.keyword.Bluemix_notm}} 時，您看到下列錯誤訊息：
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

當組織剩餘的記憶體量少於您想要部署之應用程式所需的記憶體量時，就會發生這個錯誤。試用帳戶的記憶體配額上限為 2 GB。
{: tsCauses}

您可以增加帳戶的記憶體配額，或減少應用程式所使用的記憶體。
{: tsResolve}

  * 若要增加帳戶的記憶體配額，請將試用帳戶轉換為付費帳戶。如需如何將試用帳戶轉換成付費帳戶的相關資訊，請參閱[付費帳戶](/docs/pricing/index.html#pay-accounts)。
  * 若要減少應用程式所使用的記憶體，請使用 {{site.data.keyword.Bluemix_notm}} 主控台或 cf 指令行介面。

    如果您使用 {{site.data.keyword.Bluemix_notm}} 主控台，請完成下列步驟：

    1. 在應用程式儀表板中，選取您的應用程式。即會開啟應用程式詳細資料頁面。
    2. 在「運行環境」窗格中，您可以針對您的應用程式減少記憶體上限及（或）應用程式實例的數目。

    如果您使用 cf 指令行介面，請完成下列步驟：

    1. 檢查有多少記憶體用於應用程式：

	  ```
	  cf apps
	  ```

	  cf apps 指令會列出您在現行空間中部署的所有應用程式。也會顯示每個一應用程式的狀態。

    2. 若要減少應用程式所使用的記憶體量，請減少應用程式實例的數目及（或）記憶體上限：

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. 重新啟動應用程式，讓變更生效。

如需管理應用程式的一般問題的相關資訊，請參閱[管理應用程式疑難排解](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps)。


## 未載入工具鏈
{: #toolchains_load}

當您按一下工具鏈以檢視其「概觀」頁面時，未載入工具鏈。
{:shortdesc}

在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。然後，按一下**概觀**。工具鏈的「概觀」頁面未開啟。
{: tsSymptoms}

請檢查 {{site.data.keyword.Bluemix_notm}} 狀態，以查看問題是否因中斷而起。
{: tsCauses}

請檢視「{{site.data.keyword.Bluemix_notm}} 狀態」頁面，以確定是否有已知問題影響 {{site.data.keyword.Bluemix_notm}} 平台及 {{site.data.keyword.Bluemix_notm}} 中的主要服務。
{: tsResolve}

您可以選擇下列其中一個選項來尋找「狀態」頁面：

  * 登入 {{site.data.keyword.Bluemix_notm}} 主控台。從功能表列中，按一下**支援**，然後選取**狀態**。請檢查針對 ![部分問題](../../support/images/some_issues.svg) 圖示列出的資源。此圖示可能指出運作中斷。
  * 直接在 [IBM {{site.data.keyword.Bluemix_notm}} - 系統狀態 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://ibm.biz/bluemixstatus){: new_window} 存取它。

如需「{{site.data.keyword.Bluemix_notm}} 狀態」頁面的相關資訊，請參閱 [Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status)。


## 未配置工具整合
{: #tool_integration_error}

配置工具鏈的工具整合之後，其工具卡片上顯示 `Setup failed` 錯誤。
{:shortdesc}

配置工具整合之後，您檢視其在工具鏈之「概觀」頁面上的工具卡片，並注意到設定失敗。
{: tsSymptoms}

 ![設定失敗錯誤](images/tool_setup_failed.png)

新增工具整合時，工具鏈會與工具整合所代表的工具進行通訊，來佈建任何必要資源，以及建立它們與工具鏈的關聯。如果在設定處理程序期間發生錯誤，或工具鏈與工具之間的通訊未適當地完成，則工具整合會進入錯誤狀態。
{: tsCauses}

重新配置工具整合：
{: tsResolve}

1. 在其工具卡片上，將游標移至 `Setup failed` 訊息上方，然後按一下**重新配置**。

 ![「重新配置」按鈕](images/tool_reconfigure.png)

1. 確定您使用的是有效的配置參數。如果是無效的配置導致錯誤，則會顯示錯誤訊息；例如，`The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`。更新工具整合的設定，然後按一下**儲存整合**。
1. 如果是通訊問題導致錯誤，請按一下**儲存整合**以重試。
