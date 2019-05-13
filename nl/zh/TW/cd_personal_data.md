---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: IBM Cloud account, personal data, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 在 Continuous Delivery 中管理個人資料
{: #cd_personal_data}

您可以從 {{site.data.keyword.contdelivery_full}} 中修改、匯出或刪除個人資料。
{: shortdesc}

個人資料是與自然人有關或可識別自然人的任何資訊。例如，個人資料可以是名稱、電子郵件位址、虛擬人像、記號或與 {{site.data.keyword.contdelivery_short}} 搭配使用的任意數目的 ID。下列 {{site.data.keyword.contdelivery_short}} 元件包含個人資料：

 * Eclipse Orion {{site.data.keyword.webide}}
 * {{site.data.keyword.gitrepos}}
 * {{site.data.keyword.contdelivery_short}} 管線
 * 工具鏈及工具整合
 * [IBM Cloud 上的 GitHub Enterprise ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/ghededicated?topic=ghededicated-ghe_personal_data){: new_window}
 * [{{site.data.keyword.DRA_full}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/DevOpsInsights?topic=DevOpsInsights-deleting_data){: new_window}
 
IBM 不會管理 {{site.data.keyword.contdelivery_short}} 服務中的資料。在您離開 {{site.data.keyword.Bluemix_notm}} Public 中所管理的 {{site.data.keyword.contdelivery_short}} 服務之前，必須刪除您自己的資料。
{: important}

{{site.data.keyword.contdelivery_short}} 提供管理資源群組或 Cloud Foundry 組織內資料的適當許可權。您公司的原則可能會限制這些許可權。如果您沒有適當的許可權，請聯絡 {{site.data.keyword.Bluemix_notm}} 帳戶的管理者。

若要管理個人資料，您必須瞭解 IBM Cloud 帳戶、這些帳戶的使用方式，以及其相關聯的存取權。
 
## 帳戶及存取權
{: #accounts_access_rights}

若要在 IBM Cloud 中工作，您必須以使用者名稱及密碼登入。當您登入時，IBM Cloud 會至少關聯一個 IBM Cloud 帳戶與您的使用者認證。當您建立資源（例如 Cloud Foundry 組織、資源群組、工具鏈及 {{site.data.keyword.contdelivery_short}} 物件）時，它們會與 IBM Cloud 帳戶相關聯。

IBM Cloud 登入結構提供在不同的帳戶中工作的選項。使用 IBM Cloud 使用者介面，您可以將某個帳戶切換為另一個帳戶。當您登入時，下列任何類型的帳戶都可能會與您的使用者認證相關聯： 

 * 個人帳戶
 * 公司帳戶
 * 公司個別帳戶

###個人帳戶

一般而言，每一位使用者都會有自己的帳戶，即其個人帳戶。您可以輕鬆地識別個人帳戶，因為它通常會包含您的名稱（例如，*John Smith's Account*）。 

您對個人帳戶中建立的所有物件具有完整權限。您可以邀請其他使用者加入您的帳戶、將所建立物件的權限指派給他們，以及將在您帳戶中建立物件的權限指派給他們。這表示其他使用者的個人資料可能在您的帳戶中，而您的個人資料可能在其他使用者的帳戶中。 

如果您具有在帳戶中建立物件的許可權，則也具有修改及刪除它的權限（不論在其中儲存物件的帳戶為何）。兩位使用者分工合作時，通常會共用個人帳戶。

###公司帳戶

公司帳戶是由您的公司所設定。一般而言，會自動將您新增至該帳戶，而非透過邀請。公司帳戶提供一個位置讓使用者工作、進行通訊以及共用資源和費用；不過，這只是慣例。公司帳戶與個人帳戶實際上並沒有差別。在公司帳戶中建立的物件與該帳戶相關聯，而且可以邀請使用者加入該帳戶。

為公司工作的人員團隊通常是使用公司帳戶進行分工合作。

###公司個別帳戶

當您為公司工作時，公司可能會合法地擁有您帳戶中的工作。許多為公司工作的使用者都會有公司個別帳戶。如果您使用包含公司名稱且也具有看來是個人帳戶的認證來登入帳戶，則您個人帳戶內的工作可能屬於公司。

公司個別帳戶與任何其他帳戶沒有差別。您可以邀請使用者加入公司個別帳戶，而且帳戶會擁有公司個別帳戶中所建立的物件。

如果您為擁有您的工作的公司工作，則會將通常包含您的名稱的個人帳戶視為公司個別帳戶。 

## 修改、匯出及刪除個人資料
{: #managing_personal_data}

不論使用哪種類型的 IBM Cloud 帳戶，如果您具有帳戶中物件的權限，則可以修改、匯出及刪除它們。進行變更之前，請與其他使用者合作，確定您不需要修改或刪除資料。

在您刪除帳戶中的資料之前，請判定它是個人帳戶還是公司個別帳戶。

###個人帳戶

如果您擁有個人帳戶，則可以進行變更以及刪除您的資料。如果您與另一位使用者共用您的帳戶，則您會擁有資料，但可能會想要聯絡他們告知有關所共用的工作。 

如果您無法登入 IBM Cloud 帳戶，請[與 IBM 支援中心聯絡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/support){:new_window}
 
###公司個別帳戶

如果您擁有公司個別帳戶，則必須與您公司及其他團隊成員共同處理任何變更。請刪除個人資料，不論它是儲存在公司帳戶還是公司個別帳戶中。請確定您未刪除與其他使用者共用的工作。

在您開始管理 {{site.data.keyword.contdelivery_short}} 元件的個人資料之前，請確定您是在 IBM Cloud 帳戶中工作。若要檢視您目前在其中工作的 IBM Cloud 帳戶，請在功能表列上按一下您的設定檔虛擬人像。 

如果您無法登入 IBM Cloud 帳戶，請與您的公司聯絡，並與他們合作來刪除您的個人資料。

如果您要從 {{site.data.keyword.contdelivery_short}} 中刪除您的所有個人資料，則刪除該資料的順序十分重要。首先，請刪除所有 {{site.data.keyword.webide}} 工作區。接下來，刪除 {{site.data.keyword.gitrepos}} 資料，然後刪除 {{site.data.keyword.gitrepos}} 帳戶。最後，刪除交付管線、工具整合及工具鏈。
{: tip}

## 匯出及刪除 Web IDE 資料
{: #managing_web_ide_data}

{{site.data.keyword.webide}} 提供雲端中的個人工作區。您可以使用 {{site.data.keyword.webide}} 來複製 Git 儲存庫以及編輯檔案。您會擁有您的 {{site.data.keyword.webide}} 工作區；任何其他帳戶都不會共用它。

在您刪除 {{site.data.keyword.webide}} 資料之前，可能會想要匯出工作。在您刪除工作區之後，就會從 {{site.data.keyword.contdelivery_short}} 中移除它們，並刪除所有檔案。
{: important}

###匯出 Web IDE 工作區

若要匯出 {{site.data.keyword.webide}} 工作區，請執行下列動作：

1. 選取**檔案 > 匯出 > Zip**。
1. 針對您要匯出的每一個工作區重複執行。

###刪除 Web IDE 工作區

若要刪除 {{site.data.keyword.webide}} 工作區（包括您的所有個人資料），請執行下列動作：

1. 從任何工具鏈中，導覽至 {{site.data.keyword.webide}}。
1. 在左側的導覽資訊看板中，按一下**設定**圖示 <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="設定圖示">。
1. 按一下**使用者設定檔**。
1. 按一下**刪除**，以移除 {{site.data.keyword.webide}} 中的所有資料。

{{site.data.keyword.webide}} 使用單一登入機制。第一次存取此工具整合時，會為 IBM Cloud 帳戶建立對應但隱藏的 {{site.data.keyword.webide}} 帳戶。刪除您的所有工作區之後，請不要存取 {{site.data.keyword.webide}}。如果您再次存取 {{site.data.keyword.webide}}，則會自動建立您必須刪除的新帳戶。
{: important}

## 修改、匯出及刪除 Git Repos and Issue Tracking 資料
{: #managing_grit_data}

{{site.data.keyword.gitrepos}} 提供雲端中的受管理 Git 服務。單一登入機制是用來關聯 IBM Cloud 帳戶與 Git 帳戶。在 Git 帳戶中，會為您建立完整名稱及簡稱。在 Git 問題的註解中，其他使用者可以使用您的簡稱來參照您。您可以自訂 Git 帳戶，以及新增個人資料（例如您自己的說明或影像）。 

{{site.data.keyword.gitrepos}} 提供一個功能強大但複雜的社交編碼環境，使用者可以在其中參與不同的專案，並共用物件。此環境可能很難找到及刪除您的個人資料。

您的帳戶設定檔與設定、個人專案、群組和 Snippet 都會與 Git 帳戶相關聯。如果您刪除 Git 帳戶，將會刪除這些物件。若要刪除另一個專案中的個人資料，請導覽至專案，然後修改它來移除個人資料，或刪除整個專案。請確定您先與其他團隊成員合作，再刪除共用專案。

在您刪除 Git 帳戶之前，請刪除其他專案中的個人資料。在您刪除 Git 帳戶之後，可能很難或無法找到您參與的所有專案。
{: tip}

###個人及共用專案

您可以邀請其他使用者，以便對專案進行分工合作。您在帳戶內建立的 Git 專案稱為「個人專案」。您也可以建立可由多個 Git 擁有者擁有其專案的 Git 群組。您可以建立群組的新專案，或將個人專案的所有權轉移給群組。Git 群組通常用來代表 IBM Cloud 公司帳戶，以指出公司所擁有的專案。

###匯出 Git Repos and Issue Tracking 專案

在您刪除 {{site.data.keyword.gitrepos}} 專案之前，可以匯出專案以進行保存。 

1. 在左側的導覽資訊看板中，按一下**設定**圖示 <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="設定圖示">。
1. 按一下**一般**。
1. 按一下**展開**，以展開「匯出專案」區段。
1. 按一下**匯出專案**。

保存專案之後，就可以將它匯入至另一個 GitLab 實例。 

###刪除 Git Repos and Issue Tracking 帳戶

您可以刪除 {{site.data.keyword.gitrepos}} 帳戶以及該帳戶所擁有的所有項目。

1. 在「{{site.data.keyword.gitrepos}} 使用者設定」儀表板之[帳戶頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} 的「刪除帳戶」區段中，按一下**刪除帳戶**。
1. 即會刪除所有 Git 專案（包括儲存庫及問題）。也會從您所屬的任何 {{site.data.keyword.gitrepos}} 群組中將您移除。

在刪除您的帳戶之後，會保留部分內容。此內容會指派給系統層面的「Ghost 使用者」。如需刪除 {{site.data.keyword.gitrepos}} 帳戶的相關資訊，請參閱[刪除使用者帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/profile/account/delete_account#associated-records){:new_window}。
{: tip}

{{site.data.keyword.gitrepos}} 使用單一登入機制，以在您第一次存取工具整合時自動建立 IBM Cloud 帳戶的對應 Git 帳戶。在您刪除帳戶之後，請不要存取 {{site.data.keyword.gitrepos}}。如果您再次存取 {{site.data.keyword.gitrepos}}，則會自動建立您必須刪除的新帳戶。
{: important}

## 修改、匯出及刪除 Continuous Delivery 管線資料
{: #managing_pipeline_data}

{{site.data.keyword.contdelivery_short}} 管線會執行 Script，以對 IBM Cloud 建置、測試及部署應用程式。為了這麼做，管線提供階段、工作、環境變數，以及可能包含個人資料的其他物件。您可以個別刪除這些物件，也可以刪除整個管線。

請確定您先與其他團隊成員合作，再刪除共用物件或管線。刪除階段可能會導致管線失敗。

管線不能存在於工具鏈外部。如果您刪除工具鏈，則會一併刪除與工具鏈相關聯的所有管線。如果您要刪除整個工具鏈，則不需要個別刪除每一個管線。相反地，請跳到「修改及刪除工具鏈和工具整合」小節，並遵循刪除工具鏈的步驟。
{: important}

管線階段可能包括個人資料（例如環境內容形式的認證），以及顯示管線現行狀態的管線定義。階段也可能會包括工作內您要修改或刪除的 Script，以及您要匯出之最新管線執行的構件及日誌。使用「配置階段」或「刪除階段」動作，即可修改或刪除階段。使用「下載」動作，以從階段中匯出構件或日誌。

  ![「階段」功能表](images/pipeline_stages.png)

###修改管線階段

若要修改管線階段，請執行下列動作：

1. 在「管線」頁面上，按一下**設定**圖示。
1. 按一下**配置階段**。
1. 在**環境內容**標籤上，編輯或刪除內容。
1. 修改管線階段內的工作 Script。選取工作，並變更屬於「建置」、「部署」或「測試配置」的值。
   
   ![修改工作 Script](images/job_script.png)
  
1. 從管線階段中刪除工作。在**工作**標籤上，選取您要刪除的工作，然後按一下**移除**。
 
###匯出管線階段

若要匯出整個管線的定義，請將 `/yaml` 附加至管線 URL 後面：

`https://cloud.ibm.com/devops/pipelines/<pipeline id>/yaml?env_id=<region id>`

其中 `<pipeline id>` 及 `<region id>` 是管線頁面 URL 中所顯示的值。

產生的 yaml 檔案包含所有管線階段的定義。


若要匯出管線階段的構件及日誌，請執行下列動作：

1. 在「管線」頁面上，按一下**檢視日誌及歷程**。
1. 按一下您要匯出構件及日誌的建置號碼。
1. 按一下**下載** > **構件**，以匯出所選取建置的構件。
1. 按一下**下載** > **日誌**，以匯出所選取建置的日誌。  

###刪除管線階段

若要刪除管線階段，請執行下列動作：

1. 在「管線」頁面上，按一下**設定**圖示。
1. 按一下**刪除階段**。

## 修改及刪除工具鏈和工具整合
{: #managing_toolchains}

透過使用工具鏈，團隊可以分工合作以及共用不同的工具整合。 

建議您使用與團隊或公司相關聯的資料，而不是與您相關聯的資料，來配置所有 {{site.data.keyword.contdelivery_short}} 整合。不過，在部分實例中，可能會不小心地改為使用您的個人資料。在這類實例中，您必須識別並刪除所有您擁有的資料。

建立工具整合時，{{site.data.keyword.contdelivery_short}} 無法記錄所有資料的原點。例如，另一個團隊成員可能會使用您在電子郵件中提供的個人資料，為您建立工具整合。您必須瞭解您擁有的資料，並確定已將之刪除。

請先與其他團隊成員合作，再刪除共用的工具整合或工具鏈。

###修改及刪除工具整合

當您建立工具整合時，需要提供使用者認證以及與整合相關的其他帳戶資訊。如果您已使用自己的個人認證及帳戶資訊，請將此資訊取代為不同的值，或刪除工具整合。

若要修改工具整合，請執行下列動作：

1. 在工具的卡片上，按一下功能表以存取配置選項。

  ![「工具配置」功能表](images/toolchain_tile_menu.png)

1. 完成設定的更新後，請按一下**儲存整合**。

若要刪除工具整合，請執行下列動作：

1. 若要從工具鏈中刪除工具整合，請按一下**刪除**。
1. 按一下**刪除**來進行確認。

###刪除工具鏈

當您刪除工具鏈時，無法復原刪除。

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下要刪除的工具鏈。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**。
1. 按一下**檢視應用程式**旁的**其他動作**功能表。
1. 按一下**刪除**。刪除工具鏈會移除其所有工具整合（包括管線），這樣可能會刪除那些整合所管理的資源。
1. 鍵入工具鏈名稱，然後按一下**刪除**，來確認刪除。 

當您刪除工具鏈時，不會刪除相關聯的 {{site.data.keyword.gitrepos}} 儲存庫。如果可存取這些儲存庫的使用者已執行 `git clone` 或建立 {{site.data.keyword.webide}} 工作區，則可能會有資料的副本。若要確定已刪除所有資料，您必須要求這些使用者刪除其資料副本。
{: tip}

###刪除所有工具鏈

您無法同時刪除資源群組或組織內的所有工具鏈。您必須逐一刪除每一個工具鏈。

工具鏈是以 IBM Cloud 地區及資源群組或 Cloud Foundry 組織限定範圍。請確定您選取每個地區及該地區內的資源群組或組織，以刪除您建立的每個工具鏈。
{: tip}
