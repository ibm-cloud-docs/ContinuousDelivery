---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-27"

keywords: toolchain template, Configuration properties, readme file

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


# 建立自訂工具鏈範本
{: #toolchains_custom}

建立自訂工具鏈範本，以改善 DevOps 工作流程。您可以快速開始使用現有工具鏈範本，或建立只包含所需工具整合的工具鏈範本。您隨時可以新增或移除工具鏈的整合。
{:shortdesc}

您可以透過數種方式[建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started){: new_window}。在您建立自訂工具鏈範本之後，即可[建立部署至 {{site.data.keyword.Bluemix_notm}} 按鈕](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deploy-button){: new_window}進行共用。如需工具鏈範本 SDK 的相關資訊，請參閱 [Open Toolchain SDK](https://github.com/open-toolchain/sdk/wiki/){:new_window}。如需逐步指導教學，請參閱 [Garage Method 網站](https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain/){:new_window}。


## 開始使用
{: #toolchains_custom_gettingstarted}

若要建立自訂工具鏈範本，請從複製「簡單 Cloud Foundry」工具鏈範本開始。複製現有範本可提供自訂工具鏈的起始點。

1. 使用您選擇的 Git 用戶端，輸入下列指令，來複製 GitHub 中的[簡單工具鏈](https://github.com/open-toolchain/simple-toolchain){: new_window}範本。

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 此範本會部署單一 GitHub 儲存庫中的基本 Hello World 應用程式，並包括已預先配置以進行持續交付、來源控制、問題追蹤及線上編輯的簡單工具鏈。

2. 如果您想要從較複雜的工具鏈範本開始，請複製[微服務的雲端原生工具鏈範本](https://github.com/open-toolchain/toolchain-demo){: new_window}。

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

微服務範本會部署包含三個微服務的線上商店，而這三個微服務各包含在其自己的 GitHub 儲存庫中。它也是針對下列項目預先配置的較複雜工具鏈：
* 持續交付
* 來源控制
* 藍綠部署
* 功能測試
* 問題追蹤
* 線上編輯
* 傳訊

不論您選擇哪一種範本，自訂所建立工具鏈的處理程序通常都相同。

在您複製範本之後，所具有的基本 GitHub 儲存庫會包含一個 Readme 檔及一個 `.bluemix` 目錄。此目錄會包含工具鏈運作所需的所有配置檔。`.bluemix` 目錄最少必須包含下列檔案：

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![定義工具鏈所需的最少檔案數](images/min_files_for_a_toolchain.png)


下列各節說明上述每一個檔案。每一個小節都會包含您可在工具鏈發展時諮詢的配置資訊。YAML 是一種資料序列化語言，其為 JSON 的嚴格超集，並新增了語法顯著換行及縮排。不過，YAML 不容許文字定位點字元。

## 瞭解配置檔
{: #toolchains_custom_config_files}


工具鏈範本配置檔主要包含 YAML 格式化檔案。每一個檔案都包含 meta 資料，可說明工具鏈的不同層面。meta 資料包括：
* 工具鏈及儲存庫的相關資訊。
* 如何建置及部署程式碼的相關詳細資料。
* 工具鏈中工具的配置內容。

在您的工具鏈變得更為複雜時，配置檔的複雜性會變得更為複雜。

當您處理 YAML 檔案時，請遵循下列準則：

* 只有空間才能使用空格。不容許定位點。
* 所有內容及清單都必須使用一個以上的空格進行縮排。
* 所有索引鍵及內容都區分大小寫。

請特別注意 YAML 檔案的格式，以減少發生錯誤的機會。若要檢查以尋找錯誤，請使用簡單驗證器（例如[這個剖析器](http://wiki.ess3.net/yaml/){: new_window}）。
{: important}

## 規劃服務
每一個服務子區段都包含下列資訊：

* name - 使用者產生的字串，用來識別現行檔案之環境定義中的這個服務。您可以使用此名稱來將服務標示為必要。

* service_id - 識別服務的唯一字串。此字串直接來自[服務型錄](https://github.com/open-toolchain/sdk/wiki/services.md){: new_window}。

* parameters - 服務的零個以上配置參數。這些參數會在服務之間改變。使用者必須參考型錄以判斷特定服務需要哪些參數。

### 包括其他檔案中的文字

工具鏈的所有資訊都可以儲存在 `toolchain.yml` 檔案中。不過，您可能想要為使用 `$text` 的每一個工具整合使用者介面建立不同的檔案。使用不同的檔案可以更輕鬆地維護工具鏈，並將編輯配置檔所需的時間縮到最短。`toolchain.yml` 檔案中的此範例 Snippet 顯示如何使用 `pipeline.yml` 檔案的內容作為 `content` 的值。

```
  configuration:
    content:
      $text: pipeline.yml
```

### 本地化工具鏈範本

您可以本地化工具鏈，方法是將 `nls` 目錄中的使用者介面字串外部化，以使用者的偏好語言顯示工具鏈中的字串。您的 `toolchain.yml` 檔案必須包含 `$i18n` 參照。  
下列範例顯示 `messages.yml` 檔案的 `$i18n` 參照：

```
messages:
  $i18n: messages.yml
```

  英文字串是在 `messages.yml` 中，而其他語言會使用語言碼（例如 `messages_de.yml`）。您可以在[用來識別語言的標籤](https://tools.ietf.org/html/rfc5646){: new_window}中，找到語言碼清單。

   若要參照外部化字串，請使用 `$ref` 來擷取字串。例如，

```
  template:
    name:
      $ref: "#/messages/template.name"
```

  如果您未使用外部化字串，您可以使用：

```
  template:
    name: my_template
```

如需使用者介面字串的相關資訊，請參閱 [Open Toolchain SDK 的 Messages Section](https://github.com/open-toolchain/sdk/wiki/Template-File-Format#messages-section){: new_window}。

## 配置工具鏈檔案
{: #toolchains_custom_toolchain_yml}

`toolchain.yml` 檔案是工具鏈的核心。此檔案會概述工具鏈的所有特性（包括要取回的儲存庫、要包含的服務，以及建置詳細資料）。若要瞭解其內容，您可以將檔案分解成數個區段。

1\. **介紹工具鏈資訊：**

 檔案的這個區段提供使用者可以在工具鏈建立頁面上看到的工具鏈的簡單詳細資料。請包括工具鏈的名稱，以及可說明工具鏈用途的說明。您也可以包含影像（例如工具鏈的標誌或視覺化描述）。

 除了提供工具鏈的介紹內容之外，這個區段也包括名為 `required` 的索引鍵，以定義屬於工具鏈一部分的工具。工具鏈的建立者從範本建立工具鏈時，會配置這些工具。對於可在工具鏈建立頁面上配置的每一個工具，將 `toolchain.yml` 檔案中所定義之工具的母項索引鍵新增為 `required` 索引鍵的內容。

 此 Snippet 顯示這個區段的範例：

 ```
 ---
template
  name: "Simple Toolchain"
  description: "This Hello World application uses Node.js and includes a toolchain that is preconfigured for continuous delivery, source control, issue tracking, and online editing.\n\nTo get started, click **Create**."
  header: '![](toolchain.svg)'
  icon: icon.svg
  required:
   - sample-build
   - sample-repo
  info:
    git url: >-
      [https://github.com/my-toolchain/simple-toolchain](https://github.com/open-toolchain/simple-toolchain)
    git branch: >-
      [master](https://github.com/my-toolchain/simple-toolchain/tree/master)
  ```
 {: codeblock}

在該範例中，Git URL 及 Git 分支適用於新的工具鏈範本。

2\. **儲存庫定義：**

 工具鏈可以持續交付任意數目的 Git 儲存庫（例如 GitHub、GitHub Enterprise、Git Repos and Issue Tracking 及 GitLab）。`toolchain.yml` 檔案的儲存庫定義區段就是定義每一個儲存庫的位置。

 對於新增至工具鏈的每一個儲存庫，使用下列內容來新增可代表儲存庫名稱的母項索引鍵：

|項目 |索引鍵/內容|值|說明|
|------|--------------|-------|-------------|
|repo-name |索引鍵 |  |儲存庫名稱。此索引鍵符合名稱 (sample-repo) |
|service_id |內容 |<`githubpublic`、`githubprivate`、`hostedgit`、`gitlab`> |儲存庫類型 |
|parameters: |索引鍵 |  |  |
|repo_name |內容 |  |repo-name 的型樣。下列範例使用工具鏈名稱作為儲存庫名稱 |
|repo_url |內容 |  |儲存庫的 URL |
|type |內容 |<`new`、`fork`、`clone`、`link`> |如何建立新的儲存庫 |
|has_issues |內容 |<`true`、`false`> |使用 Issues |
|enable_traceability |properties
|<`true`、`false`> |透過建立確定的標記、標籤及註解、取回要求及所參照問題，來判定是否追蹤程式碼變更的部署。|

 如果您定義多個儲存庫，並將它們配置為 `has_issues: true`，則會將單一 GitHub Issue 追蹤器實例新增至工具鏈。此追蹤器會追蹤所有設為 `true` 的儲存庫的問題。
 {: tip}

 此 Snippet 顯示這個區段的範例：

 ```
 # Github repos
 services:
  sample-repo:
    service_id: githubpublic
    parameters:
      repo_name: '{{toolchain.name}}'
      repo_url: 'https://github.com/open-toolchain/node-hello-world'
      type: clone
      has_issues: true
      enable_traceability: true
 ```
 {: codeblock}

3\. **管線資訊：**

 您可以使用管線來持續交付專案。檔案的這個區段定義配置詳細資料，以用來在每一個 GitHub 及 Git Repos and Issue Tracking 儲存庫中建置及部署程式碼。

 若要開始，請針對工具鏈中所定義的每一個儲存庫，新增代表其管線名稱的母項索引鍵。請考量從 GitHub 或 Git Repos and Issue Tracking 儲存庫名稱衍生此索引鍵。請新增下列內容：

|項目 |索引鍵/內容|值|說明|
|------|--------------|-------|-------------|
|pipeline-name |索引鍵 |  |管線的名稱 (sample-build) |
|service_id |內容 |<`pipeline`> |要使用的服務名稱 |
|parameters |索引鍵 |  |  |
|name |內容 |<`repo_name`> |與 repos 區段中所定義的名稱相同 |
|ui-pipeline |內容 |<`true`、`false`> |如果此管線所部署的應用程式顯示在工具鏈頁面的**檢視應用程式**功能表中，則為 True |
|configuration |索引鍵 |  |  |
|content |內容 |<`$ref(pipeline.yml)`> |可定義管線定義的檔案 |
|env |索引鍵 |  |  |
|SAMPLE_REPO |索引鍵 |<`repo-name-key`> |與儲存庫母項索引鍵相同的名稱 |
|CF_APP_NAME |內容 | <`'{{form.pipeline.parameters.prod-app-name}}'`> |Cloud Foundry 所使用的名稱。請考量將儲存庫母項索引鍵名稱併入此內容。|
|PROD_SPACE_NAME |內容 | <`'{{form.pipeline.parameters.prod-space}}'`> |要部署至其中的 {{site.data.keyword.Bluemix_notm}} 空間名稱 |
|PROD_ORG_NAME |內容 | <`'{{form.pipeline.parameters.prod-organization}}'`> |要部署至其中的 {{site.data.keyword.Bluemix_notm}} 組織名稱 |
|PROD_REGION_ID |內容 | <`'{{form.pipeline.parameters.prod-region}}'`> |要部署至其中的 {{site.data.keyword.Bluemix_notm}} 地區名稱 |
|execute |內容 |<`true`、`false`> |在建立之後開始管線 |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 在[稍後區段](#toolchains_custom_pipeline_yml)中，可以找到建立 `pipeline.yml` 檔案的相關資訊。

 下列 Snippet 顯示檔案的這個區段的範例：

 ```
 # Pipelines
  sample-build:
    service_id: pipeline
    parameters:
      services:
        - sample-repo
      name: '{{services.sample-repo.parameters.repo_name}}'
      ui-pipeline: true
      configuration:
        content:
          $ref: pipeline.yml
        env:
          SAMPLE_REPO: sample-repo
          CF_APP_NAME: '{{form.pipeline.parameters.prod-app-name}}'
          PROD_SPACE_NAME: '{{form.pipeline.parameters.prod-space}}'
          PROD_ORG_NAME: '{{form.pipeline.parameters.prod-organization}}'
          PROD_REGION_ID: '{{form.pipeline.parameters.prod-region}}'
       execute: true
 ```
 {: codeblock}

4\. **部署詳細資料：**

 在持續交付處理程序期間，您可以配置工具鏈，將應用程式部署至使用者可以存取的任何 {{site.data.keyword.Bluemix_notm}} 地區、組織或空間。您可以在[工具鏈建立](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started){: new_window}頁面上指定在何處部署應用程式的詳細資料。

`toolchain.yml` 檔案的這個區段定義可從工具鏈建立頁面配置的管線階段。

 母索引鍵 `deploy` 可用來識別部署配置內容。下列內容構成區段的其餘部分：

|項目 |索引鍵/內容|值|說明|
|------|--------------|-------|-------------|
|deploy|索引鍵 |  |部署區段的名稱 |
|schema|內容 |<`deploy.json`> |定義用於配置部署詳細資料的使用者介面佈置的檔案|
|service-category|內容 |<`pipeline`> |使用部署配置的服務|
|parameters |索引鍵 |  |  |
|prod-region|內容 | <`"{{region}}"`> |定義正式作業階段的 {{site.data.keyword.Bluemix_notm}} 地區|
|prod-organization|內容 | <`"{{organization}}"`> |定義正式作業階段的 {{site.data.keyword.Bluemix_notm}} 組織|
|prod-space|內容 |<`prod`> |定義正式作業階段的 {{site.data.keyword.Bluemix_notm}} 空間|
|github-repo-name|內容 | <`"{{repo-name-key.parameters.repo_name}}"`> |要將 GitHub 儲存庫名稱傳遞給工具鏈建立頁面的變數|

如需建立 `deploy.json` 檔案的相關資訊，請參閱[本節](#toolchains_custom_deploy_json)。

 下列範例定義可部署至正式作業環境的單一階段。

 

 ```
 ## Configuring a deployment stage
 deploy:
   schema: deploy.json
   service-category: pipeline
   parameters:
 	prod-region: "{{region}}"
 	prod-organization: "{{organization}}"
 	prod-space: prod
 	hello-world-name: "{{hello-world-repo.parameters.repo_name}}"
 ```
 {: codeblock}

 您可以使用程式碼範例並進行一些修改。若要自訂此區段，請將 `github-repo-name` 設為與儲存庫的名稱一致。您也必須在 [`deploy.json`](#toolchains_custom_deploy_json) 檔案中更新詳細資料。

 若要建立包括 dev、QA 及 Prod 階段的更複雜管線，可以替換 `parameters` 索引鍵下的下列內容。

 ```
   parameters:
 	dev-region: "{{region}}"
 	qa-region: "{{region}}"
 	prod-region: "{{region}}"
 	dev-organization: "{{organization}}"
 	qa-organization: "{{organization}}"
 	prod-organization: "{{organization}}"
 	dev-space: dev
 	qa-space: qa
 	prod-space: prod
 ```
 {: codeblock}

 ## 配置管線
 {: #toolchains_custom_pipeline_yml}

 `pipeline.yml` 檔案包含管線階段的所有配置詳細資料。您可以從現有 pipeline.yml 開始，並自訂它以符合需求。

 

 如果您的工具鏈包含多個管線，請為每一個 `pipeline.yml` 檔案提供唯一的名稱。

 以下是 `pipeline.yml` 檔案範例：

 ```
 ---
stages:
- name: BUILD
  inputs:
  - type: git
    branch: master
    service: ${SAMPLE_REPO}
  triggers:
  - type: commit
  jobs:
  - name: Build
    type: builder
- name: DEPLOY
  inputs:
  - type: job
    stage: BUILD
    job: Build
  triggers:
  - type: stage
  properties:
  - name: CF_APP_NAME
    value: undefined
    type: text
  - name: APP_URL
    value: undefined
    type: text
  jobs:
  - name: Blue-Green Deploy
    type: deployer
    target:
      region_id: ${PROD_REGION_ID}
      organization: ${PROD_ORG_NAME}
      space: ${PROD_SPACE_NAME}
      application: ${CF_APP_NAME}
    script: |
      #!/bin/bash
      # Push app
      if ! cf app $CF_APP; then
        cf push $CF_APP
      else
        OLD_CF_APP=${CF_APP}-OLD-$(date +"%s")
        rollback() {
          set +e
          if cf app $OLD_CF_APP; then
            cf logs $CF_APP --recent
            cf delete $CF_APP -f
            cf rename $OLD_CF_APP $CF_APP
          fi
          exit 1
        }
        set -e
        trap rollback ERR
        cf rename $CF_APP $OLD_CF_APP
        cf push $CF_APP
        cf delete $OLD_CF_APP -f
      fi
      # Export app name and URL for use in later Pipeline jobs
      export CF_APP_NAME="$CF_APP"
      export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
      # View logs
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## 配置管線介面
 {: #toolchains_custom_deploy_json}

 在[工具鏈建立](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started){: new_window}頁面上，從「可配置的整合」區段中選取 Delivery Pipeline 時，會展開此區段以顯示下列項目：

 	* 應用程式的名稱。
 	* 在其中部署管線階段的地區、組織及空間。

您可以針對每一個工具配置這些項目。

 

 使用者介面中此區段的佈置是透過 `deploy.json` 綱目所定義。

 在此綱目內，更新下列內容以符合應用程式的詳細資料：

 	* Title
 	* Description
 	* LongDescription
 	* `hello-world-name` 的所有實例及相關聯的詳細資料

 下列 Snippet 是 `deploy.json` 檔案的範例：

 ```
 {
    "$schema": "http://json-schema.org/draft-04/schema#",
    "messages": {
        "$i18n": "locales.yml"
    },
    "title": {
        "$ref": "#/messages/deploy.title"
    },
    "description": {
        "$ref": "#/messages/deploy.description"
    },
    "longDescription": {
        "$ref": "#/messages/deploy.longDescription"
    },
    "type": "object",
    "properties": {
        "prod-region": {
            "description": "The {{site.data.keyword.Bluemix_notm}} region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The {{site.data.keyword.Bluemix_notm}} org",
            "type": "string"
        },
        "prod-space": {
            "description": "The {{site.data.keyword.Bluemix_notm}} space",
            "type": "string"
        },
        "prod-app-name": {
            "description": {
                "$ref": "#/messages/deploy.appDescription"
            },
            "type": "string",
            "pattern": "\\S"
        }
    },
    "required": [
        "prod-region",
        "prod-organization",
        "prod-space",
        "prod-app-name"
    ],
    "form": [
        {
            "type": "validator",
          "url": "/devops/setup/bm-helper/helper.html"
       },
        {
            "type": "text",
            "readonly": false,
            "title": {
                "$ref": "#/messages/deploy.appName"
            },
            "key": "prod-app-name"
        },
        {
            "type": "table",
            "columnCount": 4,
            "widths": [
                "15%",
                "28%",
                "28%",
                "28%"
            ],
            "items": [
                {
                    "type": "label",
                    "title": ""
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/region"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/organization"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/space"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/prodStage"
                    }
                },
                {
                    "type": "select",
                    "key": "prod-region"
                },
                {
                    "type": "select",
                    "key": "prod-organization"
                },
                {
                    "type": "select",
                    "key": "prod-space",
                    "readonly": false
                }
            ]
        }
    ]
}
 ```
 {: codeblock}


## 其他工具配置

 在您配置工具鏈的核心元件之後，可以包括將更多功能新增至工具鏈的其他工具整合。在 `toolchain.yml` 檔案中，所有其他工具都需要有自己的項目。部分工具也需要您將不同的 YAML 配置檔新增至 `.bluemix` 目錄。

 ![定義工具鏈所需的檔案](images/files_for_toolchain_with_additional_tools.png)

若要查看可用的工具整合清單，請參閱<a href="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">工具鏈範本中可用的服務</a>。下列範例顯示如何格式化對工具鏈 YAML 檔案的新增。

 

### **Slack**

#### toolchain.yml
{: #slack_toolchain_yaml}

```
messaging:
	  service_id: slack
	  $ref: slack.yml
	```
{: codeblock}

#### slack.yml
{: #slack_slack_yaml}

```
---YAML
parameters:
  api_token: ""
  channel_name: ""
	```
{: codeblock}

### **Sauce Labs**

#### toolchain.yml
{: #sauce_toolchain_yaml}

```YAML
test:
	  service_id: saucelabs
	  $ref: saucelabs.yml
	```
{: codeblock}

#### saucelabs.yml
{: #sauce_slack_yaml}

```YAML
---
	parameters:
	  username: ""
	  key: ""
	```
{: codeblock}

### **Eclipse Orion Web IDE**

####	toolchain.yml
{: #eclipse_toolchain_yaml}

```YAML
webide:
	  service_id: orion
	```
{: codeblock}
