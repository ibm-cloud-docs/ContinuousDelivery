---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# 建立「部署至 {{site.data.keyword.Bluemix_notm}}」按鈕 {: #deploy-button} 

「部署至 {{site.data.keyword.Bluemix_notm}}」按鈕可讓您有效率地共用您的公用 Git 來源應用程式，讓其他人能夠試用程式碼，並使用工具鏈將其部署至 IBM {{site.data.keyword.Bluemix_notm}}。此按鈕需要的配置最少，而且您可以將其插入到任何支援標記的地方。按一下此按鈕的任何人都會在新的 Git 儲存庫中建立程式碼的複製副本，因此原始應用程式不受影響。
{: shortdesc}

當有人按一下您的按鈕時，就會進行下列動作： 

1. 如果該人員沒有作用中 {{site.data.keyword.Bluemix_notm}} 帳戶，則必須建立帳戶。他們可以建立試用帳戶或實際帳戶。 

2. 該人員可以按一下 {{site.data.keyword.deliverypipeline}} 圖示來選取地區、組織、空間及應用程式名稱。建議的應用程式名稱會與工具鏈名稱相同，而工具鏈名稱是建構自原始 Git 儲存庫的名稱及時間。您也可以編輯工具鏈名稱。

3. 建立的工具鏈包括 Git 儲存庫的新專用複製、用於建置及部署程式碼變更的管線、用於在「雲端」上編輯程式碼的 Eclipse Orion {{site.data.keyword.webide}}，以及問題追蹤器。 

  **提示**：如果 `.bluemix` 目錄包含 `toolchain.yml` 檔案，則會使用此檔案來指定工具鏈的工具整合。如需 `toolchain.yml` 檔案的相關資訊，請參閱[建立自訂工具鏈](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}。
 
4. 如果應用程式需要建置檔，則會自動偵測建置檔，並建置應用程式。 

5. 如果針對建置及部署處理程序配置管線，則會使用 `pipeline.yml` 檔案來部署應用程式。

6. 如果應用程式需要容器，則會使用定義 IBM Containers 服務的 `pipeline.yml` 檔案以及定義映像檔的 Dockerfile，在 {{site.data.keyword.Bluemix_notm}} 容器中部署應用程式。 

7. 應用程式會部署至該人員所選取的 {{site.data.keyword.Bluemix_notm}} 組織。 

## 按鈕的範例 {: #button-examples} 

請參閱公用 {{site.data.keyword.gitrepos}} 儲存庫的應用程式按鈕範例：

[![部署至 Bluemix](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

請參閱公用 GitHub 儲存庫的應用程式按鈕範例： 

[![部署至 Bluemix](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://github.com/ibmjstart/bluemix-node-mysql-uploader){:new_window}

請參閱在 {{site.data.keyword.Bluemix_notm}} 容器中部署之應用程式的按鈕範例： 

[![部署至 Bluemix](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://github.com/Puquios/hello-containers){:new_window}

## 建立按鈕 {: #create-button}

若要建立「部署至 {{site.data.keyword.Bluemix_notm}}」按鈕，請複製並修改下列其中一個 Snippet 範本。請在 URL 中指定 Git 儲存庫及分支。

### 以 HTML 建立按鈕

若要以 HTML 建立按鈕，請複製此 Snippet，並插入公用 Git 儲存庫 URL 及分支。

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="部署至 Bluemix"></a>
```

如果您未在 Snippet 的儲存庫 URL 中包括 `branch` 參數，則「部署至 Bluemix」按鈕會預設為儲存庫的主要分支。

### 以 Markdown 建立按鈕

若要以 Markdown 建立按鈕，請複製此 Snippet，並插入公用 Git 儲存庫 URL 及分支。

```Markdown
[![部署至 Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```

如果您未在 Snippet 的儲存庫 URL 中包括 `branch` 參數，則「部署至 Bluemix」按鈕會預設為儲存庫的主要分支。

### 使用按鈕 Snippet {: #button-snippet}

在您建立「部署至 Bluemix」按鈕 Snippet 之後，可以將它插入至部落格、文章、Wiki、Readme 檔，或您要提示應用程式的任何其他位置。

當您自訂「部署至 {{site.data.keyword.Bluemix_notm}}」按鈕的 Snippet 時，請考量這兩個範本都使用 PNG 格式且為英文的外部按鈕影像的預設路徑。 

* 如果您偏好使用按鈕的 SVG 影像，而非 PNG，請將 Snippet 中所使用按鈕影像的路徑變更為 `https://bluemix.net/deploy/button.svg`。
	
* 如果您偏好使用按鈕的影像，請將 Snippet 中所使用按鈕影像的路徑變更為 `https://bluemix.net/deploy/button_x2.png`。此影像是預設影像大小的兩倍。
	
* 如果您偏好在本端儲存影像，則可以下載影像，並將它儲存在 Git 儲存庫中。請調整路徑來使用影像的相對位置。
	
* 如果您要使用按鈕的翻譯版本，則可以遠端參照它，或從 [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window} 進行下載。 
	
## 儲存庫考量{: #button-repo} 

請針對「部署至 {{site.data.keyword.Bluemix_notm}}」按鈕中所使用的儲存庫，檢閱這些考量。 

### 資訊清單檔需求

`manifest.yml` 檔案不需要在儲存庫中。不過，如果您的應用程式需要其他服務才能執行，則必須提供用來宣告那些服務的資訊清單檔。

您可以利用資訊清單檔指定： 

* 唯一應用程式名稱。

* 宣告的服務，這是資訊清單延伸規格，可建立或尋找預期要在部署應用程式之前設定的必要或選用服務（例如資料快取服務）。您可以使用 [CF 指令行介面 ![外部鏈結圖示](../../icons/launch-glyph.svg)](https://github.com/cloudfoundry/cli/releases) 來執行 `cf marketplace` 指令，或是瀏覽 [{{site.data.keyword.Bluemix_notm}} 型錄](https://console.bluemix.net/catalog?ssoLogout=true&cm_mmc=developerWorks-_-dWdevcenter-_-devops-services-_-lp#/store)，以尋找合格的 {{site.data.keyword.Bluemix_notm}} 服務、標籤和方案清單。

「宣告的服務」是標準 Cloud Foundry 資訊清單格式的 IBM 延伸規格。此延伸規格可能會隨著該特性的發展與改進，在未來的版本中修訂。

如果您不知道如何建立資訊清單檔，請[在這裡瞭解如何建立它們 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#minimal-manifest){:new_window}。

```YAML
---
    #Template manifest.yml

  declared-services:
    arbitrary_service_instance_name:  # [required] 
      label: actual_service_name # [required] The actual service name from market place 
      plan: Shared # [optional] If provided, used to fetch the declared service. Otherwise, defaults to 'Free' or 'free'.
  applications:
  - services
    - arbitrary_service_instance_name
    name: appname
    host: apphostname
```

```YAML
---
    #Example manifest.yml

  declared-services: 
      sample-java-cloudant-cloudantNoSQLDB: 
        label: cloudantNoSQLDB 
        plan: Shared 
  applications:
  - services
    - sample-java-cloudant-cloudantNoSQLDB
    name: My app
    host: myapp
```


### 建置檔需求

如果必須先建置應用程式，才能進行部署，您必須在儲存庫中包括建置檔。如果在儲存庫的根目錄中偵測到建置 Script 檔，則會在部署之前觸發自動建置程式碼。 

支援的建置器包括：

* [Ant ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")：](http://ant.apache.org/manual/using.html){:new_window}`build.xml`，可將輸出建置至 `./output/` 資料夾
* [Gradle ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")：](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window}`/build.gradle`，可將輸出建置至 `.` 資料夾
* [Grunt ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")：](http://gruntjs.com/getting-started#the-gruntfile){:new_window}`/Gruntfile.js`，可將輸出建置至 `.` 資料夾
* [Maven ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")：](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window}`/pom.xml`，可將輸出建置至 `./target/` 資料夾

### 管線檔需求

若要在 `.bluemix` 目錄中配置工具鏈的管線，請包括 `pipeline.yml` 檔案。針對該目錄中的每一個 `pipeline.yml` 檔案，會在實例化工具鏈時建立管線。 

若要建立管線檔，請參閱[自訂工具鏈管線指示](toolchains_custom.html#toolchains_custom_pipeline_yml)中的範例檔案。就像當您在 Web 介面中定義管線時，會建立階段及工作、設定輸入及環境變數，以及新增 Script，以文字定義管線。您也可以在[此示範專案](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix)中查看若干較複雜的管線檔。

### 容器 dockerfile 需求

若要使用 IBM Containers 在容器中部署應用程式，您必須在儲存庫的根目錄中包括 Dockerfile，並在 `.bluemix` 目錄中包括 `pipeline.yml` 檔案。 

Dockerfile 用來作為應用程式的一種建置 Script。如果在儲存庫中偵測到 Dockerfile，會先將應用程式自動建置至映像檔，再將它部署在容器中。如果必須先建置應用程式本身，再將應用程式建置至映像檔，請包括應用程式的建置 Script 以及 Dockerfile。

若要進一步瞭解如何建立 Dockerfile，請參閱 [Docker 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.docker.com/reference/builder/){:new_window}。

若要手動建立容器特有的 `pipeline.yml`，請參閱 [GitHub 中的範例 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/Puquios/){:new_window}。
