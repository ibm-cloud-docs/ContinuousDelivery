---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-11"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# {{site.data.keyword.contdelivery_short}} 疑難排解
{: #troubleshoot-cd}

一般 {{site.data.keyword.contdelivery_full}} 使用問題可能包括 GitHub 鑑別、管線建立、工具整合配置或 Cloud Foundry 問題。在許多情況下，您都可以遵循一些簡單的步驟來回復這些問題。
{:shortdesc}

## 我嘗試將 GitHub 工具整合新增至工具鏈，但為什麼未新增工具整合？
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

您必須向 GitHub 授權，以授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。

GitHub 工具整合未新增至工具鏈。
{: tsSymptoms}

如果 {{site.data.keyword.Bluemix_notm}} 未獲授權存取 GitHub 帳戶，則不會將工具整合新增至工具鏈。
{: tsCauses}

如果您要在建立工具鏈時配置 GitHub 工具整合，請遵循下列步驟以使用 GitHub 進行授權：
{: tsResolve}

  1. 在「可配置的整合」區段中，按一下 **GitHub**。
  1. 如果您要在 {{site.data.keyword.Bluemix_notm}} Public 上建立工具鏈，但未授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub，請按一下**授權**來移至 GitHub 網站。
  1. 如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。

如果您已有工具鏈，請更新 GitHub 工具整合的配置：

 1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
 1. 在 GitHub 卡片上，按一下功能表，然後按一下**配置**。
 1. 更新配置設定，以授權 {{site.data.keyword.Bluemix_notm}} 存取 GitHub。按一下**授權**，以移至 GitHub 網站。如果您沒有作用中的 GitHub 階段作業，則系統會提示您登入。按一下**授權應用程式**，以容許 {{site.data.keyword.Bluemix_notm}} 存取 GitHub 帳戶。
 1. 完成設定的更新後，請按一下**儲存整合**。
 

## 在不同地區的工具鏈中，為什麼無法在某個地區的工具鏈中使用 {{site.data.keyword.gitrepos}} 工具整合？
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

您不可以跨多個地區使用 {{site.data.keyword.gitrepos}} 實例。

嘗試將 {{site.data.keyword.gitrepos}} 工具整合新增至工具鏈時，收到下列錯誤訊息：
{: tsSymptoms}

`Repository URL is not valid. The repository must be on {local GitLab URL}.`

其中 `{local GitLab URL}` 是工具鏈所在地區中的 {{site.data.keyword.gitrepos}} 工具整合 URL。
   
因為 {{site.data.keyword.gitrepos}} 與 {{site.data.keyword.contdelivery_short}} 服務在其執行地區中緊密整合，所以您不可以跨多個地區使用 {{site.data.keyword.gitrepos}} 實例。
{: tsCauses}

建立通用 GitLab 整合，並使用此整合來指向不同地區中的 {{site.data.keyword.gitrepos}} 儲存庫，而不要建立 {{site.data.keyword.gitrepos}} 工具整合。
{: tsResolve}

1. 在 DevOps 儀表板的「工具鏈」頁面上，按一下要新增此整合的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下**新增工具**。
1. 在「工具整合」區段中，按一下 **GitLab**。
1. 按一下您要使用的 GitLab 伺服器。如果您要存取的儲存庫所在的 GitLab 伺服器未出現在此清單中，則請新增自訂伺服器：

 a. 按一下**新增自訂伺服器**。

 b. 鍵入伺服器的名稱。此伺服器名稱將會出現在可用的 GitLab 伺服器清單中。
 
 c. 鍵入自訂 GitLab 伺服器的「根 URL」。
 
 d. 輸入自訂 GitLab 伺服器的個人存取記號。如果您沒有個人存取記號，則請[建立個人存取記號](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)。
 
 e. 按一下**儲存自訂整合**。
 
1. 如果您有 GitLab 儲存庫並且想要使用它，請針對儲存庫類型按一下**現有**，然後鍵入 URL。
1. 如果您要使用新的 GitLab 儲存庫，請鍵入儲存庫的名稱，並鍵入您所複製或分出之儲存庫的 URL，然後選取儲存庫類型：

 a. 若要建立空的儲存庫，請按一下**新建**。

 b. 若要建立 GitLab 儲存庫的副本，請按一下**複製**。

 c. 若要分出 GitLab 儲存庫，以透過合併要求來提出變更，請按一下**分出**。

1. 如果您要在伺服器上建立公用儲存庫，請清除**將此儲存庫設為專用**勾選框。
1. 如果您要使用 GitLab Issues 進行問題追蹤，請選取**啟用 GitLab Issues** 勾選框。
1. 如果您要透過建立確定的標籤和註解以及確定所參照之問題的標籤和註解來追蹤程式碼變更部署，請選取**追蹤程式碼變更部署**勾選框。如需相關資訊，請參閱[使用工具鏈追蹤程式碼的部署位置 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 按一下**建立整合**。

如需配置 GitLab 工具整合的相關資訊，請參閱[配置 GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)。


## 為什麼無法從使用不同地區中專用儲存庫的範本來建立工具鏈？
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

您使用的工具鏈範本會參照專用 {{site.data.keyword.gitrepos}} 儲存庫。

{{site.data.keyword.gitrepos}} 是地區特有的。如果您嘗試從範本建立工具鏈，並將目標設為沒有專用儲存庫的地區，則 Git 整合設定會失敗。
{: tsSymptoms}
   
當您將 {{site.data.keyword.gitrepos}} 儲存庫新增至特定地區中的工具鏈時，IBM ID 會對映至可讓您在該地區中存取 GitLab 的 GitLab 使用者名稱。即使 GitLab 使用者名稱在所有地區中都相同，每個地區中的相關聯 GitLab 使用者都會不同，因為每個地區都有不同的 GitLab 安裝。不會將其他地區中的 GitLab 使用者存取權自動授與工具鏈，即使 GitLab 使用者名稱相同也是一樣。
{: tsCauses}

請將 {{site.data.keyword.gitrepos}} 儲存庫設為公用，因此從任何位置都可以進行存取，包括其他 {{site.data.keyword.Bluemix_notm}} 地區。
{: tsResolve}

如果儲存庫必須為專用，則儲存庫擁有者可以在來源儲存庫所在的 GitLab 伺服器上建立[個人存取記號](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)來授與其存取權。在建立工具鏈期間，您只需要存取專用儲存庫，就可以複製內容。可以建立具有到期日的個人存取記號，以限制其生命期限在一天之後到期。 

在您有個人存取記號之後，可以建立 URL 以從其他地區存取儲存庫。配置工具整合時，請在**來源儲存庫 URL** 欄位中，更新儲存庫 URL 以使用使用者名稱及存取記號。

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

其中 `user` 是 GitLab 使用者名稱、`XXXXXXX` 是存取記號、[`group` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window} 是儲存庫儲存所在的群組，而 `node-hello-world` 是儲存庫名稱。

如果您的 GitLab 儲存庫不在 GitLab 群組內，則 `group` 的值會與您的使用者名稱相同。
{: tip}


## 為什麼無法透過 https 複製 {{site.data.keyword.gitrepos}} 儲存庫？
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

您必須使用個人存取記號或 SSH 金鑰來執行 Git 作業。

您嘗試從指令行使用 https 推送或複製儲存庫，但無法鑑別，即使輸入正確的密碼也是一樣。
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} 所使用的單一登入機制不支援在指令行上使用使用者名稱及密碼的 Git 鑑別。
{: tsCauses}

若要執行複製或推送這類 Git 作業，您必須使用個人存取記號或 SSH 金鑰。如需建立個人存取記號或 SSH 金鑰的相關資訊，請參閱[入門指導教學](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)。
{: tsResolve}

## 嘗試使用 SSH 複製 {{site.data.keyword.gitrepos}} 儲存庫時，為什麼系統提示我進行鑑別？
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

專用 SSH 金鑰位置或許可權可能發生問題，或 Git 指令行可能未使用專用 SSH 金鑰以向 {{site.data.keyword.gitrepos}} 進行鑑別。

我已透過 {{site.data.keyword.gitrepos}} 使用者介面新增 SSH 公開金鑰。嘗試使用 SSH 來複製儲存庫時，系統提示我輸入密碼或安全代碼，或顯示錯誤訊息，指出鑑別失敗。
{: tsSymptoms}
   
下列任何 SSH 問題可能會提示您鑑別，或顯示錯誤訊息：
{: tsCauses}

* Git 指令行可能未使用專用 SSH 金鑰以向 {{site.data.keyword.gitrepos}} 進行鑑別。

* 專用 SSH 金鑰可能不在預設 ~/.ssh/id_rsa 位置中。

* 專用 SSH 金鑰可能沒有正確的許可權 (600)。


使用下列任何方法來解決此問題：
{: tsResolve}

* 如果您使用預設專用 SSH 金鑰位置，則請驗證 ~/.ssh/ 資料夾及 ~/.ssh/id_rsa 私密金鑰檔的許可權。如果許可權太廣泛，則 SSH 依預設不會使用私密金鑰。請確定 ~/.ssh/ 資料夾的許可權設為 700，而 ~/.ssh/id_rsa 資料夾的許可權設為 600。

* 如果您的私密金鑰不在預設位置中，則請使用下列指令以在環境變數中指定它：

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* 若要使用連線資訊來除錯此問題，請將 -v 或 -vvv 旗標新增至 `GIT_SSH_COMMAND` 環境變數：

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## 我已嘗試透過電子郵件將使用者新增至 GitLab 專案，但他們未收到邀請。如何將他們新增至專案？
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

使用者電子郵件可能會封鎖邀請。

我已使用列在 {{site.data.keyword.gitrepos}} 中的使用者電子郵件位址來邀請使用者加入 GitLab 專案，但他們未收到電子郵件。
{: tsSymptoms}
   
垃圾郵件過濾器可能會封鎖電子郵件進入使用者收件匣。
{: tsCauses}

您可以使用下列任何方法來解決此問題：
{: tsResolve}

* 檢查電子郵件垃圾郵件資料夾，判定是否已將電子郵件邀請標示為垃圾郵件。電子郵件會從 noreply@ 位址送出。更新垃圾郵件過濾器，以容許來自此位址的電子郵件。

* 調查不受使用者控制的公司垃圾郵件過濾器是否封鎖電子郵件。請要求使用者登入 {{site.data.keyword.gitrepos}} 使用者介面，並將其使用者 ID 傳送給您。您可以使用使用者的使用者 ID 將使用者新增至 GitLab 專案。


## 為什麼從我正在撰寫的範本建立工具鏈時未適當地建立管線？ 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

您的管線可能會因 pipeline.yaml 定義中的錯誤而遺漏工作及階段這類資源。

嘗試從我正在撰寫的範本建立工具鏈時，在「管線」頁面上收到下列錯誤訊息：
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

一般而言，pipeline.yaml 定義中的錯誤會導致此問題。
{: tsCauses}
   
您可以使用下列任何方法來除錯此錯誤：
{: tsResolve}

* 使用管線使用者介面來建立範例管線，以抄寫您正在嘗試使用範本所建置的管線。將 `/yaml` 附加至管線 URL，以產生可用來尋找顯著差異的類似 pipeline.yaml 檔案。例如，`https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`。

* 使用遠端控制工具鏈建立機制。在**建立工具鏈**頁面上，開啟除錯器，並評估 `window.Testflags = {nocreate: 1}` 表示式。當您在此模式按一下**建立工具鏈**時，不會建立工具鏈。相反地，傳遞給 API 的資訊會傳回給主控台，而您可以在其中進行檢閱。


## 我已配置工具鏈的工具整合，但為什麼並未配置它？
{: troubleshoot-tool-integration-error}
{: troubleshoot}

如果在設定處理程序期間發生錯誤，或工具鏈與工具之間的通訊未適當地完成，則配置會失敗。

在您新增及配置工具鏈的工具整合之後，會顯示錯誤訊息，指出設定失敗。
{: tsSymptoms}

新增工具整合時，工具鏈會與工具整合所代表的工具進行通訊，來佈建任何必要資源，以及建立它們與工具鏈的關聯。如果在設定處理程序期間發生錯誤，或工具鏈與工具之間的通訊未適當地完成，則工具整合會進入錯誤狀態。
{: tsCauses}

 ![設定失敗錯誤](images/tool_setup_failed.png)

您可以嘗試重新配置工具整合：
{: tsResolve}

1. 在其工具卡片上，將游標移至 `Setup failed` 訊息上方，然後按一下**重新配置**。

 ![「重新配置」按鈕](images/tool_reconfigure.png)

1. 確定您使用的是有效的配置參數。如果是無效的配置導致錯誤，則會顯示錯誤訊息；例如，`The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`。更新工具整合的設定，然後按一下**儲存整合**。
1. 如果是通訊問題導致錯誤，請按一下**儲存整合**以重試。


## 為什麼無法將 {{site.data.keyword.contdelivery_short}} 新增至 Cloud Foundry 組織？
{: troubleshoot-resource_groups}
{: troubleshoot}

您無法再於 Cloud Foundry 組織中建立 {{site.data.keyword.contdelivery_short}} 服務實例。 

下列訊息會顯示在 Cloud Foundry 組織中工具鏈的「工具鏈」頁面上：
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

當您按一下**新增服務**時，沒有選項可以在 Cloud Foundry 組織中建立 {{site.data.keyword.contdelivery_short}}。您只可以在資源群組中建立 {{site.data.keyword.contdelivery_short}}。

資源群組已將 Cloud Foundry 組織取代為服務實例的偏好容器。不過，您仍然可以在 Cloud Foundry 組織中建立工具鏈，以支援 Cloud Foundry 組織中的現有 {{site.data.keyword.contdelivery_short}} 實例。
{: tsCauses}

在資源群組中重新建立工具鏈，然後從 Cloud Foundry 組織中移除原始工具鏈。或者，除非提供將現有工具鏈從 Cloud Foundry 組織移轉至資源群組的方法，否則您可以忽略錯誤訊息。
{: tsResolve}


## 為什麼無法使用 `ibmcloud` CLI 來刪除工具鏈？
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

目前，您無法使用 ibmcloud 資源 CLI 來刪除工具鏈。 

我已嘗試從指令行使用 `ibmcloud resource service-instance-delete` 指令來刪除工具鏈，而且指令失敗並發生下列錯誤訊息：
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

工具鏈是 Cloud 平台上您目前無法使用 `ibmcloud resource` CLI 刪除的特殊類型的資源。
{: tsCauses}

若要刪除工具鏈，請執行下列動作：
{: tsResolve}

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下要刪除的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。
1. 按一下**檢視應用程式**旁的**其他動作**功能表。
1. 按一下**刪除**。刪除工具鏈會移除其所有工具整合，這樣可能會刪除那些整合所管理的資源。
1. 鍵入工具鏈名稱，然後按一下**刪除**，來確認刪除。  


## 在確定及推送至儲存庫之後，為什麼無法使用「即時編輯」？
{: #troubleshoot-liveedit}
{: troubleshoot}

當您在 Eclipse Orion {{site.data.keyword.webide}} 外部部署時，會清除「即時編輯」模式。

您可以從指令行或 {{site.data.keyword.webide}} 確定及推送變更，而且「即時編輯」無法使用。
{: tsSymptoms}
   
當您建立同時包含 {{site.data.keyword.contdelivery_short}} 管線及 {{site.data.keyword.webide}} 的工具鏈時，這兩個工具整合都可以部署應用程式。依預設，管線及 {{site.data.keyword.webide}} 會使用相同的 Cloud Foundry 應用程式及 URL 來部署至相同的 Cloud Foundry 組織及空間。當您在 {{site.data.keyword.webide}} 外部部署時，會清除「即時編輯」模式。
{: tsCauses}

若要使用「即時編輯」快速地開發應用程式的測試版本，請從 {{site.data.keyword.webide}} 部署至不同的 Cloud Foundry 應用程式、空間及 URL。當您的程式碼變更完成時，您可以確定及推送程式碼來觸發管線建置及部署應用程式的正式作業版本。
{: tsResolve}

1. 從執行列中，選取您要編輯的啟動配置。
2. 編輯針對「空間」及「主機」指定的值。
3. 按一下**儲存**及**結束**。
4. 按一下執行列中的**執行**按鈕。您可能需要部署多次，才能啟用「即時編輯」按鈕。

如需「即時編輯」的相關資訊，請參閱[即時編輯](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit)。


## {{site.data.keyword.webide}} 執行列中的「未同步」的意義為何？
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

工作區中的檔案系統未同步。

在「即時編輯」模式中，{{site.data.keyword.webide}} 會同步處理工作區中的檔案與執行中 Cloud Foundry 應用程式，而且檔案未同步。
{: tsSymptoms}
   
如果在 {{site.data.keyword.webide}} 外部修改應用程式，則工作區中的檔案系統可能會未同步。如果 {{site.data.keyword.webide}} 無法從應用程式擷取同步化狀態，則它也可能未同步。
{: tsCauses}

重新建立一般通訊及同步處理檔案時，可能會在一分鐘或兩分鐘之後清除狀態。否則，您可以在啟用「即時編輯」模式時啟動及停止應用程式。
{: tsResolve}
