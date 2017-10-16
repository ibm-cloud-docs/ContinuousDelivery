---

copyright:
  years: 2017
lastupdated: "2017-7-7"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# 创建定制工具链模板
{: #toolchains_custom}

通过创建定制工具链模板可改进 DevOps 工作流程。您可以使用现有工具链模板快速入门，也可以创建仅包含所需集成的工具链。您可以随时添加或除去工具链的集成。
{:shortdesc}

您可以通过多种方式[创建和部署工具链](/docs/toolchains/toolchains_setup.html){: new_window}。创建定制工具链后，可以使用[“部署到 {{site.data.keyword.Bluemix_notm}}”按钮](/docs/develop/deploy_button.html){: new_window}来共享该工具链。


## 入门
{: #toolchains_custom_gettingstarted}

要创建定制工具链模板，请首先克隆“简单 Cloud Foundry”工具链模板。克隆现有模板可作为您定制工具链的起点。

1. 使用所选的 Git 客户机，在 GitHub 中输入以下命令来克隆 GitHub 中的[简单工具链](https://github.com/open-toolchain/simple-toolchain){: new_window}模板。

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 此模板从单个 GitHub 存储库部署基本 Hello World 应用程序，并包含已针对持续交付、源代码控制、问题跟踪和联机编辑预配置的简单工具链。

2. 如果您希望从更复杂的工具链模板开始，那么可以首先克隆[微服务的云本机工具链](https://github.com/open-toolchain/toolchain-demo){: new_window}。

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

微服务模板将部署由三个微服务组成的网上商店，每个微服务都包含在其自己的 GitHub 存储库中。此模板还是一个更复杂的工具链，针对以下内容进行了预配置：
* 持续交付
* 源代码控制
* 蓝绿部署
* 功能测试 
* 问题跟踪 
* 联机编辑 
* 消息传递

无论选择哪个模板，用于定制所创建工具链的过程通常都相同。

克隆模板后，就会有一个基本 GitHub 存储库，该存储库包含自述文件和 `.bluemix` 目录。该目录中包含支持工具链正常运行的所有配置文件。`.bluemix` 目录至少必须包含以下文件：

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![定义工具链至少需要的文件](images/min_files_for_a_toolchain.png)


以下各部分对其中每个文件进行了说明。每个部分都包含配置信息，您可以在定义工具链的过程中查询这些信息。 


## 了解配置文件
{: #toolchains_custom_config_files}


工具链模板配置文件主要由 YAML 格式的文件组成。每个文件都包含元数据，描述工具链的不同方面。元数据包括：
* 有关工具链、GitHub 或 Git Repo and Issue Tracking 存储库的信息。
* 有关如何构建和部署代码的详细信息。
* 工具链中工具的配置属性。 

随着工具链变得越来越复杂，配置文件也可能越来越复杂。 

使用 YAML 文件时，须牢记下面几条准则：

* 空白处只使用空格。不允许使用跳格。
* 所有属性和列表都必须缩进一个或多个空格。
* 所有键和属性都是区分大小写的。

请特别注意 YAML 文件的格式设置，以减少遇到错误的机会。
要检查错误，可能要使用简单的验证器，比如[此解析器](http://wiki.ess3.net/yaml/){: new_window}。
{: tip}

## 配置工具链文件
{: #toolchains_custom_toolchain_yml}

`toolchain.yml` 文件是工具链的核心。此文件中概述了完整的工具链细节，包括要拉入的存储库、要包含的服务和构建详细信息。为了理解此文件的内容，可以将其分解成若干部分。

1\. **工具链介绍性信息：**

 文件的此部分提供有关工具链的简单详细信息，这些信息将在工具链创建页面上向用户显示。可包含工具链的名称以及描述，描述中说明工具链的用途。此外，还可以包含图像，如工具链的徽标或可视化描述。

 除了提供工具链的介绍性内容外，此部分还包含名为 `required` 的键，用于定义属于工具链的工具。工具链的创建者在基于模板创建工具链时可配置这些工具。对于可以在工具链创建页面上配置的每一个工具，请将 `toolchain.yml` 文件中定义的工具父键添加为 `required` 键的属性。

 以下片段显示了此部分的示例：

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

在该示例中，Git URL 和 Git 分支适用于新工具链模板。

2\. **GitHub 存储库定义：**

 工具链可以持续交付任意数量的 GitHub 存储库。`toolchain.yml` 文件的此部分中定义了每个存储库。

 对于将添加到工具链的每个 GitHub 和 Git Repo and Issue Tracking 存储库，使用以下属性来添加表示 GitHub 存储库名称的父键：

| 项| 键/属性| 值| 描述|
|------|--------------|-------|-------------|
| repo-name| 键|  | 存储库名称。此键与名称 (sample-repo) 相匹配|
| service_id| 属性| <`githubpublic` 或 `githubprivate`>| GitHub 存储库的类型|
| parameters:| 键|  |  |
| repo_name| 属性|  | repo-name 的模式。以下示例将工具链名称用作存储库名称|
| repo_url| 属性|  | GitHub 存储库的 URL|
| type| 属性| <`new`、`fork`、`clone` 或 `link`>| 如何创建存储库|
| has_issues| 属性| <`true` 或 `false`>| 使用 GitHub Issues|
| enable_traceability| 属性|  <`true` 或 `false`>| 通过对提交、拉取请求和所参考的问题创建标记、标签和注释，确定是否跟踪代码更改的部署。|

 **注：**如果定义了多个存储库，并将其配置为 `has_issues: true`，那么 GitHub Issues 跟踪程序的单个实例将添加到工具链。跟踪程序会跟踪已将此项设置为 `true` 的所有存储库的问题。

 以下片段显示了此部分的示例：

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

3\. **管道信息：**

 您可以通过管道持续交付项目。文件的此部分定义用于在每个 GitHub 和 Git Repo and Issue Tracking 存储库中构建和部署代码的配置详细信息。

 首先，对于在工具链中定义的每个存储库，添加表示其管道名称的父键。请考虑从 GitHub 或 Git Repo and Issue Tracking 存储库的名称中派生此键。添加以下属性：

| 项| 键/属性| 值| 描述|
|------|--------------|-------|-------------|
| pipeline-name| 键|  | 管道的名称 (sample-build)|
| service_id| 属性| <`pipeline`>| 要使用的服务的名称|
| parameters| 键|  |  |
| name| 属性| <`repo_name`>| 与“存储库”部分中定义的名称相同|
| ui-pipeline| 属性| <`true` 或 `false`>|  |
| configuration| 键|  |  |
| content| 属性| <`$ref(pipeline.yml)`>| 用于定义管道定义的文件|
| env| 键|  |  |
| SAMPLE_REPO| 键| <`repo-name-key`>| 与存储库父键的名称相同|
| CF_APP_NAME|  属性| <`'{{form.pipeline.parameters.prod-app-name}}'`> | Cloud Foundry 使用的名称。请考虑将 GitHub 存储库父键名称合并到此属性中。|
| PROD_SPACE_NAME| 属性| <`'{{form.pipeline.parameters.prod-space}}'`> | 要部署到的 {{site.data.keyword.Bluemix_notm}} 空间的名称|
| PROD_ORG_NAME| 属性| <`'{{form.pipeline.parameters.prod-organization}}'`> | 要部署到的 {{site.data.keyword.Bluemix_notm}} 组织的名称|
| PROD_REGION_ID| 属性| <`'{{form.pipeline.parameters.prod-region}}'`> | 要部署到的 {{site.data.keyword.Bluemix_notm}} 区域的名称|
| execute| 属性| <`true` 或 `false`>| 创建后启动管道|

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 有关创建 `pipeline.yml` 文件的信息，请参阅[后面的部分](#toolchains_custom_pipeline_yml)。

 以下片段显示文件此部分的示例：

 ```YAML
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

4\. **部署详细信息**：- 需要验证


 在持续交付过程中，工具链可以设置为将应用程序部署到用户有权访问的任何 {{site.data.keyword.Bluemix_notm}} 区域、组织或空间。工具链部署位置的具体详细信息可以从工具链创建页面中进行选择。

 ![Delivery Pipeline 配置设置](images/deploy_configuration.png)

  `toolchain.yml` 文件的此部分定义可从工具链创建页面进行配置的管道阶段。

 首先，父键 `deploy` 用于确定部署配置属性。以下属性构成了此部分的剩余内容：

| 项 | 键/属性 | 值 | 描述 |
|------|--------------|-------|-------------|
| deploy | 键 |  | 部署部分的名称 |
| schema | 属性 | <`deploy.json`> | 定义用于配置部署详细信息的 UI 布局的文件 |
| service-category | 属性 | <`pipeline`> | 使用部署配置的服务 |
| parameters | 键 |  |  |
| prod-region | 属性 | <`"{{region}}"`> | 定义生产阶段的 {{site.data.keyword.Bluemix_notm}} 区域 |
| prod-organization | 属性 | <`"{{organization}}"`> | 定义生产阶段的 {{site.data.keyword.Bluemix_notm}} 组织 |
| prod-space | 属性 | <`prod`> | 定义生产阶段的 {{site.data.keyword.Bluemix_notm}} 空间 |
| github-repo-name | 属性 | <`"{{repo-name-key.parameters.repo_name}}"`> | 用于将 GitHub 存储库名称传递到工具链创建页面的变量 |

有关创建 `deploy.json` 文件的更多信息，请参阅[此部分](#toolchains_custom_deploy_json)。

 以下示例定义了部署到生产环境的单个阶段。

 ```
 ## 配置部署阶段
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

 大多数情况下，代码示例可以按原样使用，只需略作修改。要定制此部分，请将 `github-repo-name` 设置为与存储库名称一致。此外，还需要更新 [`deploy.json`](#toolchains_custom_deploy_json) 文件中的详细信息。

 要创建包含开发、QA 和生产阶段的更复杂管道，可以替换 `parameters` 键下的以下属性。

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

 ## 配置管道
 {: #toolchains_custom_pipeline_yml}

  `pipeline.yml` 文件包含管道各阶段的所有配置详细信息。您可以从现有 pipeline.yml 开始，对其进行定制以满足您的需求。

 如果工具链包含多个管道，请为每个 `pipeline.yml` 文件提供唯一名称。

 下面是 `pipeline.yml` 文件的示例：

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


 ## 配置管道接口
 {: #toolchains_custom_deploy_json}

 从工具链创建页面上的“可配置的集成”部分中选择 Delivery Pipeline 时，此部分会展开以显示以下项：

 	* 应用程序的名称
 	* 将部署管道阶段的区域、组织和空间。

您可以为每个工具配置这些项。

 ![Delivery Pipeline 配置设置](images/deploy_configuration.png)

 UI 中此部分的布局由 `deploy.json` 模式进行定义。

 在该模式内，应该更新以下属性以便与应用程序的详细信息相匹配：

 	* 标题
 	* 描述
 	* 详细描述
 	* 应修改 `hello-world-name` 的所有实例及关联详细信息以便与应用程序的相应信息相匹配。

 以下片段是 `deploy.json` 文件的示例：

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
            "description": "The bluemix region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The bluemix org",
            "type": "string"
        },
        "prod-space": {
            "description": "The bluemix space",
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

 配置工具链的核心组件后，可以包含其他工具集成，以向工具链添加更多功能。所有其他工具在 `toolchain.yml` 文件中都需要有自己的条目。某些工具还需要您将单独的 YAML 配置文件添加到 `.bluemix` 目录中。

 ![定义工具链所需的文件](images/files_for_toolchain_with_additional_tools.png)

要查看可用工具集成的列表，请参阅<a ref="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">工具链模板中可用的服务</a>。以下示例显示如何设置工具链 YAML 文件添加项的格式。

 * **Slack**

### toolchain.yml
	```
	messaging:
	  service_id: slack
	  $ref: slack.yml
	```
	{: codeblock}

### slack.yml
	```
	---
	parameters:
	  api_token: ""
	  channel_name: ""
	```
	{: codeblock}

 * **Sauce Labs**

### toolchain.yml
	```
	test:
	  service_id: saucelabs
	  $ref: saucelabs.yml
	```
	{: codeblock}

### saucelabs.yml
	```
	---
	parameters:
	  username: ""
	  key: ""
	```
	{: codeblock}

 * **Eclipse Orion Web IDE**

###	toolchain.yml
	```
	webide:
	  service_id: orion
	```
	{: codeblock}
