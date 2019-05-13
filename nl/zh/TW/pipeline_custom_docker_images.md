---

Copyright:
  years: 2018, 2019
lastupdated: "2019-02-27"

keywords: pipeline base image, custom Docker, IBM Cloud team uses

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


# 使用自訂 Docker 映像檔
{: #custom_docker_images}

管線基礎映像檔可能不支援建置的所有需求。例如，您可能需要更精細地控制 node、java 或其他工具的版本。此問題的處理方式是在管線工作中包括首要步驟，以安裝一系列的新套件，並且仔細地配置環境變數（例如 `PATH`）來設定環境。不過，更好的方式是使用執行「自訂 Docker 映像檔」的管線支援作為工作基礎。

不論您使用「建置」、「測試」或「部署」工作類型，都可以選取「自訂 Docker 映像檔」子類型來提供要使用的 Docker 映像檔名稱，以及指定要執行的 Script。例如，使用下列選項，以使用 Maven 3.5.3 及 IBM Java 來執行「建置」工作：

 ![使用自訂映像檔的 Maven 建置](images/custom-image-maven-build.png)


## 指定 Docker 映像檔名稱
{: #docker_image_name}

自訂 Docker 映像檔工作中的 Docker 映像檔名稱，其設計目的是要以映像檔名稱與 Docker CLI 搭配運作的相同方式來運作。Docker 映像檔名稱的格式為：`[repository][:][tag]`。例如，針對 `docker run maven:3.5.3-ibmjava`，Docker 映像檔名稱是 `maven:3.5.3-ibmjava`，其中 `maven` 是儲存庫，而 `3.5.3-ibmjava` 是標籤。您可以使用的 Docker 映像檔名稱沒有限制；任何有效的 Docker 映像檔都會運作。

如果 **Docker 映像檔名稱**欄位未完成，則會使用標準管線基礎映像檔。
{: tip}

依預設，會在 [Docker Hub ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://hub.docker.com/){: new_window} 上搜尋您的儲存庫。如果您使用另一個 Docker 登錄（例如 {{site.data.keyword.registrylong}}），則可以使用完整 DNS 名稱。您也可以在 Docker Hub 上使用映像檔的完整名稱。例如，`registry.hub.docker.com/library/maven:3.5.3-ibmjava`。

Docker 映像檔的 `tag` 是選用項目。依預設，如果您未指定標籤，則會設為 `latest`。預設值 `latest` 只是儲存庫擁有者必須管理的標籤名稱。這不表示依時間順序而言，此 Docker 映像檔是最新的映像檔。

您可以在 Docker Hub 中找到大型儲存庫社群。IBM 會管理 [https://hub.docker.com/u/ibmcom/ ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://hub.docker.com/u/ibmcom/){: new_window} 上 IBM Cloud 團隊所使用的數個公用儲存庫。`ibmcom/ibmjava` 及 `ibmcom/ibmnode` 儲存庫可用作建置基礎。 

## 使用專用映像檔登錄
{: #private_image_registry}

如果您是使用需要鑑別的專用登錄，則必須設定兩個額外的階段環境內容：`DOCKER_USERNAME` 及 `DOCKER_PASSWORD`。您可以使用安全內容來遮罩 `DOCKER_PASSWORD`。取回您的映像檔之前，自訂 Docker 映像檔工作會使用您的使用者名稱及密碼認證來完成 `docker login`。

針對大部分登錄，您可以使用已提供給您的使用者名稱及密碼。如果您使用 {{site.data.keyword.registrylong_notm}} 來儲存專用映像檔，則必須使用平台「API 金鑰」來進行鑑別。 

1. [要求平台 API 金鑰 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/iam/#/apikeys){: new_window}，並確定您已儲存金鑰。 
1. 針對 `DOCKER_USERNAME` 使用 `iamapikey` 並針對 `DOCKER_PASSWORD` 使用您所儲存的平台「API 金鑰」，來建立兩階段環境內容。

 ![{{site.data.keyword.registrylong_notm}} 認證](images/custom-image-private-repository.png)


## 指定 Script
{: #specify_script}

您可以使用自訂 Docker 映像檔工作中的 **Script** 區塊，以建立作業資料夾中所執行的 Script 檔案，這類似於一般管線工作的運作方式。 

會置換但不會呼叫 Docker 映像檔之 Dockerfile 中的 `ENTRYPOINT` 及 `CMD`。在某些情況下，可能表示您需要將起始設定步驟新增至 Script。
{: tip}

自訂 Docker 映像檔工作可讓您對 Script 的執行方式具有更大的彈性；具體而言，您可以控制指令直譯器。一般而言，如果 Script 第一行的開頭為 `#!` 及指令直譯器名稱，則會使用該項目以在工作中執行指令。如果您未指定指令直譯器，則會使用 Docker 映像檔的預設 Shell。一般而言，會使用 `#!/bin/bash` 或 `#!/bin/sh`；如果您指定適當的 Docker 映像檔，則 `awk`、`node` 及 `ruby` 的映像檔指令直譯器也會運作。
