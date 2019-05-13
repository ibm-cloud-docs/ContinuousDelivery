---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-08"

keywords: run jobs, sequences of stages, job types

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


# Delivery Pipeline 概觀
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} 包括 Delivery Pipeline，以最少人為介入的可重複方式進行建置、測試及部署。在管線中，階段的序列會擷取輸入並執行工作（例如建置、測試及部署）。
{:shortdesc}

檢視、修改或執行管線的許可權是根據擁有管線的工具鏈的存取控制。如需工具鏈之存取控制的相關資訊，請參閱[管理對資源群組中工具鏈的存取](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups){: new_window}及[管理對 Cloud Foundry 組織中工具鏈的存取](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}。
{: important}

您可以指定 Script 在管線提供的許多工作類型中執行，這樣能讓您直接控制工作執行的內容。這些 Script 會在 Docker 映像檔中執行，該映像檔包含許多標準開發工具，包括與 {{site.data.keyword.Bluemix_notm}} 運行環境互動所需的工具。如需標準 Docker 映像檔包含內容的相關資訊，請參閱[預先安裝的資源](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources){: new_window}。如果您的工作需要標準映像檔中未提供的開發工具，或是您需要那些工具的不同版本，可以使用自訂映像檔。如需自訂映像檔的相關資訊，請參閱[使用自訂 Docker 映像檔](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images#custom_docker_images){: new_window}。

當管線執行 Script 時，說明工作執行所在環境定義的內容，會藉由環境變數而被傳遞給 Script。例如，階段輸入儲存庫的 URL、正在執行的階段及工作名稱、工作類型指定的參數等等。若要檢視可用環境變數的清單，請參閱[預先安裝的資源](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources)。 

您可以在管線層次以及階段層次定義內容。管線內容會在管線中的所有階段與工作之間共用。階段內容專屬於特定的階段，並且在該階段中的所有工作之間共用。如需內容的相關資訊，請參閱[環境內容（環境變數）](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#environment_properties)。

## 階段
{: #deliverypipeline_stages}

建置、部署及測試程式碼時，階段會組織輸入及工作。階段可接受來自來源控制儲存庫（SCM 儲存庫）的輸入，或來自其他階段中之建置工作的輸入。針對 SCM 儲存庫，輸入是儲存庫中特定分支的內容；針對建置工作，輸入是工作產生的構件。當您建立第一個階段時，**輸入**標籤會包含設定預設值。

階段執行時，階段的輸入會傳遞給階段中的每個工作。每個工作都會得到一個全新的容器以便在其中執行。因此，階段內的工作無法將構件傳遞給彼此。若要在工作之間傳遞構件，請將工作分成兩個階段，然後使用來自第一個階段之工作的輸出，作為第二個階段的輸入。
{: tip}

類似於您定義管線內容的方法，您也可以定義階段內容，以便用於特定階段中的所有工作。例如，您可能會定義 `TEST_URL` 內容，以將 URL 傳遞給階段中的部署及測試工作。部署工作會部署至該 URL，測試工作則會測試該 URL 上的執行中應用程式。階段內容也會藉由使用環境變數傳遞給工作 Script。如果在管線層次及階段層次都定義了相同的內容，會使用階段內容的值。

在階段中，每次將變更遞送給專案的 SCM 儲存庫時，依預設會自動執行建置及部署。階段及工作會依序執行；它們讓您能進行工作的流程控制。例如，您可以在部署階段之前放置測試階段。如果測試階段中的測試失敗，則不會執行部署階段。

您可能想要更嚴格地控制特定階段。如果您不想要每次在輸入發生變更時都執行階段，則可以停用此功能。在**輸入**標籤的「階段觸發程式」區段中，按一下**只在手動執行此階段時才執行工作**。

![「輸入」標籤](images/input_tab_only_execute.png)


### 建置階段
{: #build_stage}

建置階段指定**建置器類型**，以指出如何建置構件。  

建置工作中可用的許多欄位，在多個建置器類型之間是共同的。
{: tip}

下列是可用的「建置器」類型：

* **Simple** - 使用 **Simple** 建置器類型的工作會取得現行階段的輸入，然後在不修改它的情況下保存以供未來階段使用。通常 **Simple** 建置器類型只適用於階段的輸入來自 SCM 儲存庫之時。
* **Ant** - 使用這個建置器類型，可以用 Apache Ant 檔案來管理建置工作。
  * **Build script** - 這個建置器類型可以是任何有效的建置 Script。依預設，這個建置器類型會設為 'ant'。
  * **Working directory** - 指定 Script 執行所在的目錄。
  * **Build archive directory** - 指定包含要保存以供後續階段使用之工作輸出的目錄。
  * **Enable test report** - 選取這個勾選框，可以指定建置工作會執行測試，以 JUnit XML 格式產生結果檔案。「工作結果」頁面的「測試」標籤上會顯示以結果檔案為基礎的報告。如果任何測試失敗，工作會標示為失敗。
  * **Enable code coverage report** - 選取這個勾選框，可以顯示您能用於程式碼涵蓋面報告的更多欄位。您可以指定涵蓋面執行器（例如 Istanbul、JaCoCo、ore Cobertura）、涵蓋面結果檔案的位置，以及涵蓋面結果目錄（相對於工作目錄）。
* **Container Registry**
* **Gradle（Artifactory、Nexus 或 SonarQube）**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven（Artifactory、Nexus 或 SonarQube）**
* **npm（Artifactory 或 Nexus）**
* **Shell Script**

### 部署階段
部署階段指定「建置」階段的輸入。部署階段中的工作指定**部署人員類型**。下列是可用的「部署人員」類型：

1. **Cloud Foundry**
2. **Kubernetes**

## 工作
{: #deliverypipeline_jobs}

工作是階段內的執行單位。一個階段可以包含多個工作，並且會循序執行階段中的工作。根據預設值，如果工作失敗，則不會執行階段中的後續工作。

![階段內的建置及測試工作](images/jobs.png)

工作是在為每一個管線執行所建立之 Docker 容器內的不同工作目錄中執行。執行工作之前，會將在階段層次所定義的輸入移入其工作目錄中。例如，您可以具有包含測試工作及部署工作的階段。如果您將相依關係安裝在某個工作上，則另一個工作無法使用這些相依關係。不過，如果您在階段的輸入中提供相依關係，則這兩個工作都可以使用這些相依關係。

簡單類型的建置工作除外，當您配置工作時，可以納入含有建置、測試或部署指令的 UNIX Shell Script。因為工作是在特定容器中執行，所以某個工作的動作無法影響其他工作的執行環境，即使那些工作是相同階段的一部分也是一樣。

在 [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons) 中可以找到範例建置及部署 Script。

此外，管線工作只能以 `sudo` 身分執行下列指令：
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


執行工作之後，會捨棄為它所建立的容器。工作執行的結果可以持續保存，但其執行環境則否。

工作最多可以執行 60 分鐘。工作超出此限制時，即會失敗。如果工作超出此限制，請將它分成多個工作。例如，如果工作執行三個作業，則可能會將它分成三個工作：一個作業一個工作。
{: tip}

若要瞭解如何將工作新增至階段，請參閱[將工作新增至階段](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy#deliverypipeline_add_job){: new_window}。

### 建置工作

建置工作會在準備部署時編譯您的專案。它們會產生可傳送至建置保存目錄的構件，不過根據預設值，會將構件放在專案的根目錄中。

從建置工作取得輸入的工作，必須參照在它們建立所在之相同結構中的建置構件。例如，如果建置工作會將建置構件保存至 `output` 目錄，則部署所編譯的專案時，部署 Script 會參照 `output` 目錄，而不是專案根目錄。您可以在**建置保存目錄**欄位中輸入目錄名稱，以指定要保存的目錄。將欄位空白，會保存根目錄。

如果您使用**簡單**建置器類型，則不會編譯或建置程式碼；會將它包裝並設為供未來階段使用。
{: tip}

當您使用 Cloud Foundry 進行部署時，Cloud Foundry 會包括正確的構件來容許應用程式執行。如需相關資訊，請參閱[使用 cf 指令來部署應用程式](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#deploy_apps)。Cloud Foundry 應用程式的管線包含執行 cf 指令的「部署」階段。

Cloud Foundry 會嘗試[偵測要使用的建置套件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.cloudfoundry.org/buildpacks/detection.html)。您可以在應用程式根資料夾的資訊清單檔中指定要使用的[建置套件](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_buildpacks#using_buildpacks)。建置套件一般會檢查使用者提供的構件，來判定下載的相依關係以及如何配置應用程式以與連結服務進行通訊。如需資訊清單檔的相關資訊，請參閱[應用程式資訊清單](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest)。

### 部署工作

部署工作會將您的專案當成應用程式上傳至 {{site.data.keyword.Bluemix_notm}}，而且可以從 URL 進行存取。部署專案之後，您可以在 {{site.data.keyword.Bluemix_notm}} 儀表板上找到所部署的應用程式。

部署工作可以部署新的應用程式，或更新現有的應用程式。即使您先使用另一種方法（例如 Cloud Foundry 指令行介面，或 Web IDE 中的執行列）來部署應用程式，還是可以使用部署工作來更新應用程式。若要更新應用程式，請在部署工作中使用該應用程式的名稱。

您可以部署至一或多個地區及服務。例如，您可以設定 {{site.data.keyword.deliverypipeline}} 使用一個以上的服務、在一個地區中測試，以及部署至多個地區進行正式作業。

### 測試工作
如果您想要要求符合條件，請在建置及部署工作之前或之後包含測試工作。您可以視需要將測試工作自訂成簡單或複雜。例如，您可以發出 cURL 指令，並預期會有特定回應。也可以使用協力廠商測試服務（例如 Sauce Labs）來執行一組單元測試或執行功能測試。

如果您的測試產生 JUnit XML 格式的結果檔案，則會在每個測試結果頁面的**測試**標籤上顯示根據這些結果檔案的報告。如果測試失敗，則工作也會失敗。

## 環境內容（環境變數）
{: #environment_properties}

一組預先定義的環境內容讓您能存取工作執行環境的相關資訊。如需預先定義環境內容的完整清單，請參閱[環境內容及資源](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment)。

您也可以定義自己的環境內容。例如，您可能定義 `API_KEY` 內容，以傳遞管線中所有 Script 用來存取 {{site.data.keyword.Bluemix_notm}} 資源的 API 金鑰。

您可以新增下列類型的內容：

* **文字**：具有單行值的內容索引鍵。
* **文字區**：具有多行值的內容索引鍵。
* **安全**：具有單行值的內容索引鍵，並且以 AES-128 加密來保護。值會顯示為星號。
* **內容**：專案儲存庫中的檔案。此檔案可以包含多個內容。每一個內容都必須單獨一行。若要區隔索引鍵值組，請使用等號 (=)。請使用引號括住所有字串值。例如，`MY_STRING="SOME STRING VALUE"`。

您可以在工作 Script 中執行 `env` 指令，來檢查管線工作的環境內容。
{:tip}

### 管線內容
若要定義管線內容，請從「管線」頁面的溢位功能表，選取**配置管線**。

![管線溢位功能表](images/OverflowMenu.png)

從「管線配置」頁面上的**環境內容**標籤，設定管線層次的環境內容。

![管線內容頁面](images/PipelineProperties.png)

### 階段內容
若要定義階段內容，請開啟「階段配置」頁面，然後按一下**環境內容**標籤。

![階段內容頁面](images/StageProperties.png)

您也可以匯出內容，以便在相同階段的工作之間傳遞環境內容。例如，您可以包含下列指令，以在階段內的另一個工作中使用 `$API_KEY` 內容：`export API_KEY=<insert API key here>`
{:tip}

### 計算的內容
您可以計算階段之間共用的環境內容值，方法是在階段執行時建立 `build.properties` 檔，然後讓下一個階段執行檔案。例如，您的建置工作可能會在建置 Script 中包含下列指令：

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

執行 `build.properties` 檔案（如果存在的話），即會啟動所有工作。

## 建立及使用構件
{: #artifacts}

建置工作會自動提取使用者 Script 執行所在之現行資料夾中的內容。如果您後續的部署不需要整個 Git 儲存庫內容，則最好配置明確輸出目錄，然後在該處複製或建立相關構件。工作 Script 是在建置結果（輸出目錄）中執行。

部署至 Cloud Foundry 的工作需要指定用來執行權限工作之使用者的「平台 API 金鑰」，以及要部署構件的地區、組織及空間。如果需要其他服務才能執行您的應用程式，則必須在 `manifest.yml` 檔案中指定它們。

部署至 {{site.data.keyword.containerlong_notm}} 的部署工作，需要指定用來執行權限工作之使用者的「平台 API 金鑰」、Dockerfile 以及選擇性地使用 Helm 圖表。  

工作使用指派給它的「平台 API 金鑰」登入目標環境之後，會執行工作 Script（以便您可以在 Script 中執行 `cf push` 或 `kubectl` 指令）。

## 範例管線
{: #deliverypipeline_example}

簡單的管線可能包含三個階段：

1. 「建置」階段：在應用程式上編譯及執行建置程序。
2. 「測試」階段：部署應用程式實例，然後對其執行測試。
3. 「正式作業」階段：部署所測試應用程式的正式作業實例。

此管線顯示在下列概念性圖表中：

![管線中階段及工作的概念性圖表](images/diagram.jpg)

*三階段管線的概念性模型*

階段都採用其從儲存庫及建置工作的輸入，而且會循序並各自獨立地執行階段內的工作。在範例管線中，會循序執行階段，即使「測試」及「正式作業」階段都採用「建置」階段的輸出作為其輸入。

## Cloud Foundry 資訊清單檔
{: #deliverypipeline_manifest}

資訊清單檔（名為 `manifest.yml` 並儲存在專案的根目錄中）控制如何將專案部署至 {{site.data.keyword.Bluemix_notm}}。如需建立專案資訊清單檔的相關資訊，請參閱[關於應用程式資訊清單的 {{site.data.keyword.Bluemix_notm}} 文件](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest)。若要與 {{site.data.keyword.Bluemix_notm}} 整合，您專案的根目錄中必須要有資訊清單檔。不過，您不需要根據檔案中的資訊來進行部署。

在管線中，您可以使用 `cf push` 指令引數來指定資訊清單檔可執行的所有項目。`cf push` 指令引數有助於具有多個部署目標的專案。如果多個部署工作都嘗試使用專案資訊清單檔中所指定的路徑，則會發生衝突。

為了避免衝突，指定路徑時可以使用 `cf push`，再加上主機名稱引數 `-n` 及路徑名稱。藉由修改個別階段的部署 Script，即可避免在部署至多個目標時發生路徑衝突。

若要使用 `cf push` 指令引數，請開啟部署工作的配置設定，並修改**部署 Script** 欄位。如需相關資訊，請參閱 [Cloud Foundry Push 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}。
