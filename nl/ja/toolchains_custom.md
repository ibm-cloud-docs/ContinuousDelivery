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


# カスタム・ツールチェーン・テンプレートの作成
{: #toolchains_custom}

カスタム・ツールチェーン・テンプレートを作成して DevOps ワークフローを改善します。既存のツールチェーン・テンプレートを使用してすぐに始めるか、必要な統合のみを組み込んだツールチェーンを作成できます。ツールチェーンの統合はいつでも追加したり削除したりできます。
{:shortdesc}

[ツールチェーンを作成およびデプロイ](/docs/toolchains/toolchains_setup.html){: new_window}するには、いくつかの方法を使用できます。カスタム・ツールチェーンを作成したら、[「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタン](/docs/develop/deploy_button.html){: new_window}を使用してこれを共有できます。


## 概説
{: #toolchains_custom_gettingstarted}

カスタム・ツールチェーン・テンプレートを作成するには、まず Simple Cloud Foundry ツールチェーン・テンプレートのクローン作成から開始します。既存のテンプレートのクローン作成は、カスタマイズしたツールチェーンの開始点となります。

1. 選択した Git クライアントを使用して、次のコマンドを入力し、GitHub の[シンプルなツールチェーン](https://github.com/open-toolchain/simple-toolchain){: new_window}のテンプレートのクローンを作成します。

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 このテンプレートは、基本的な Hello World アプリケーションを単一の GitHub リポジトリーからデプロイします。このテンプレートには、継続的デリバリー、ソース管理、問題のトラッキング、オンライン編集のための構成があらかじめ行われたシンプルなツールチェーンが含まれています。

2. さらに複雑なツールチェーン・テンプレートから開始する場合は、[マイクロサービス用のクラウド・ネイティブのツールチェーン](https://github.com/open-toolchain/toolchain-demo){: new_window}のクローンを作成することから始めることができます。

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

マイクロサービス・テンプレートは、3 つのマイクロサービス (それぞれ独自の GitHub リポジトリーに含まれる) で構成されるオンライン・ストアをデプロイします。また、これは、次の項目用に事前構成された、より複雑なツールチェーンでもあります。
* 継続的デリバリー
* ソース管理
* Blue-green デプロイメント
* 機能テスト 
* 問題のトラッキング 
* オンライン編集 
* メッセージング

いずれのテンプレートを選択するかに関係なく、作成するツールチェーンのカスタマイズ・プロセスは一般的に同じです。

テンプレートのクローンを作成すると、Readme ファイルと `.bluemix` ディレクトリーを含んだ基本的な GitHub リポジトリーが作成されます。このディレクトリーには、ツールチェーンの動作に必要なすべての構成ファイルが含まれます。`.bluemix` ディレクトリーには、少なくとも次のファイルが含まれている必要があります。

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![ツールチェーンの定義に必要な最小限のファイル](images/min_files_for_a_toolchain.png)


これらの各ファイルについては、以降のセクションで説明します。各セクションには、ツールチェーンの展開に合わせて確認できる構成情報が含まれます。 


## 構成ファイルについて
{: #toolchains_custom_config_files}


ツールチェーン・テンプレートの構成ファイルは、主に YAML 形式のファイルで構成されます。各ファイルには、ツールチェーンの様々な側面を記述するメタデータが含まれます。メタデータには次の情報が含まれます
* ツールチェーン、GitHub、または Git Repo and Issue Tracking リポジトリーに関する情報。
* コードのビルドとデプロイ方法に関する詳細。
* ツールチェーンに含まれるツールの構成プロパティー。 

ツールチェーンが複雑になると、構成ファイルも同様に複雑になることがあります。 

YAML ファイルで作業する際に注意すべきガイドラインは次のとおりです。

* スペースにはスペースだけを使用します。タブは許可されません。
* すべてのプロパティーとリストは、1 つ以上のスペースでインデントする必要があります。
* すべてのキーとプロパティーは大/小文字が区別されます。

YAML ファイルのフォーマットに細心の注意を払い、エラーが発生する可能性を低くします。
エラーを確認するには、[このパーサー](http://wiki.ess3.net/yaml/){: new_window}のようなシンプルなバリデーターを使用できます。
{: tip}

## ツールチェーン・ファイルの構成
{: #toolchains_custom_toolchain_yml}

`toolchain.yml` ファイルは、ツールチェーンの中核です。プルするリポジトリー、含めるサービス、ビルドの詳細などのツールチェーンの仕様が、すべてこのファイルに記述されます。内容を分かりやすくするために、いくつかのセクションに分割することができます。

1\. **ツールチェーンの情報の概要**

 ファイルのこのセクションでは、ツールチェーンの作成ページでユーザーに表示されるツールチェーンのシンプルな詳細情報が提供されます。ツールチェーンの名前とともに、ツールチェーンの目的についての説明を含めます。ロゴやツールチェーンを視覚的に表したイメージを含めることもできます。

 ツールチェーンの概要のコンテンツを提供することに加えて、このセクションには、ツールチェーンを構成するツールを定義する `required` という名前のキーも含まれます。ツールチェーンの作成者は、テンプレートからツールチェーンを作成する際に、これらのツールを構成します。ツールチェーンの作成ページで構成できるツールごとに、`toolchain.yml` ファイルで `required` キーのプロパティーとして定義されているツールの親キーを追加します。

 次のスニペットは、このセクションの例を示しています。

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

この例の Git URL と Git ブランチは、新規ツールチェーン・テンプレートのものです。

2\. **GitHub リポジトリーの定義**

 ツールチェーンは、任意の数の GitHub リポジトリーに対して継続的デリバリーを提供できます。`toolchain.yml` ファイルのこのセクションで、各リポジトリーが定義されます。

 ツールチェーンに追加される GitHub と Git Repo and Issue Tracking リポジトリーそれぞれについて、GitHub リポジトリーの名前を表す親キーを次のプロパティーとともに追加します。

| アイテム| キー/プロパティー| 値| 説明 |
|------|--------------|-------|-------------|
| repo-name| キー|  | リポジトリー名。このキーは名前 (sample-repo) に一致します|
| service_id| プロパティー| <`githubpublic`、`githubprivate`> | GitHub リポジトリーのタイプ|
| パラメーター:| キー|  |  |
| repo_name| プロパティー|  | repo-name のパターン。以下の例では、リポジトリー名としてツールチェーン名が使用されています |
| repo_url| プロパティー|  | GitHub リポジトリーの URL|
| タイプ| プロパティー| <`new`、`fork`、`clone`、`link`> | リポジトリーの作成方法 |
| has_issues| プロパティー| <`true`、`false`> | GitHub Issues の使用|
| enable_traceability | properties
|  <`true`、`false`> | コミット、プル要求、参照される問題に対するタグ、ラベル、コメントを作成することによって、コード変更のデプロイメントをトラッキングするかどかを判断します。|

 **注意:** 複数のリポジトリーを定義して `has_issues: true` として構成すると、GitHub Issue トラッカーの単一のインスタンスがツールチェーンに追加されます。トラッカーは、`true` に設定されているすべてのリポジトリーの問題をフォローします。

 次のスニペットは、このセクションの例を示しています。

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

3\. **パイプラインの情報:**

 パイプラインを使用してプロジェクトを継続的にデリバリーできます。ファイルのこのセクションでは、各 GitHub と Git Repo and Issue Tracking リポジトリーでコードをビルドしてデプロイするために使用される構成の詳細を定義します。

 まず、ツールチェーンで定義されたリポジトリーごとに、そのパイプラインの名前を表す親キーを追加します。このキーは、GitHub または Git Repo and Issue Tracking リポジトリーの名前に基づいたものにすることを検討していください。次のプロパティーを追加します。

| アイテム| キー/プロパティー| 値| 説明 |
|------|--------------|-------|-------------|
| pipeline-name| キー|  | パイプラインの名前 (sample-build) |
| service_id| プロパティー| <`pipeline`> | 使用するサービスの名前|
| パラメーター | キー|  |  |
| 名前
| プロパティー| <`repo_name`> | リポジトリーのセクションで定義される名前と同じです |
| ui-pipeline| プロパティー| <`true`、`false`> |  |
| 構成
| キー|  |  |
| コンテンツ| プロパティー| <`$ref(pipeline.yml)`> | パイプラインを定義するファイル|
| env| キー|  |  |
| SAMPLE_REPO | キー| <`repo-name-key`> | リポジトリーの親キーと同じ名前 |
| CF_APP_NAME|  プロパティー| <`'{{form.pipeline.parameters.prod-app-name}}'`> | Cloud Foundry で使用する名前。このプロパティーに GitHub リポジトリーの親キー名を組み込むことを検討してください。 |
| PROD_SPACE_NAME| プロパティー| <`'{{form.pipeline.parameters.prod-space}}'`> | デプロイ先の {{site.data.keyword.Bluemix_notm}} スペースの名前|
| PROD_ORG_NAME| プロパティー| <`'{{form.pipeline.parameters.prod-organization}}'`> | デプロイ先の {{site.data.keyword.Bluemix_notm}} の組織の名前|
| PROD_REGION_ID| プロパティー| <`'{{form.pipeline.parameters.prod-region}}'`> | デプロイ先の {{site.data.keyword.Bluemix_notm}} の地域の名前|
| execute| プロパティー| <`true`、`false`> | 作成後にパイプラインを開始します|

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 `pipeline.yml` ファイルの作成については、[後続のセクション](#toolchains_custom_pipeline_yml)を参照してください。

 次のスニペットは、ファイルのこのセクションの例を示しています。

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

4\. **デプロイメントの詳細:** - need to verify


 継続的デリバリー・プロセスの一部として、ユーザーがアクセスできる任意の {{site.data.keyword.Bluemix_notm}} の地域、組織、またはスペースにアプリケーションをデプロイするようにツールチェーンを構成できます。アプリケーションをデプロイする場所の具体的な詳細を、ツールチェーンの作成ページから選択できます。![Delivery Pipeline の構成設定](images/deploy_configuration.png)

 「toolchain.yml」ファイルのこのセクションでは、ツールチェーンの作成ページから構成できるパイプラインのステージを定義します。

 まず、親キー「deploy」を使用して、デプロイメントの構成プロパティーを特定します。このセクションを構成するその他のプロパティーは次のとおりです。| アイテム | キー/プロパティー | 値 | 説明 |
|------|--------------|-------|-------------|
| deploy | key |  | デプロイメント・セクションの名前 |
| schema | property | <`deploy.json`> | デプロイメントの詳細を構成するための UI のレイアウトを定義するファイル |
| service-category | property | <`pipeline`> | デプロイメントの構成を使用するサービス |
| parameters | key |  |  |
| prod-region | property | <`"{{region}}"`> | 本稼働ステージの {{site.data.keyword.Bluemix_notm}} の地域を定義します |
| prod-organization | property | <`"{{organization}}"`> | 本稼働ステージの {{site.data.keyword.Bluemix_notm}} の組織を定義します |
| prod-space | property | <`prod`> | 本稼働ステージの {{site.data.keyword.Bluemix_notm}} のスペースを定義します |
| github-repo-name | property | <`"{{repo-name-key.parameters.repo_name}}"`> | GitHub リポジトリー名をツールチェーンの作成ページに渡すための変数 |

「deploy.json」ファイルの作成について詳しくは、[このセクション](#toolchains_custom_deploy_json)を参照してください。

 次の例では、実稼働環境にデプロイする単一のステージを定義しています。

 ```
 ## デプロイメント・ステージの構成
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

 このサンプル・コードは、ほとんどの部分をそのまま使用することができますが、わずかな点だけを変更する必要があります。このセクションをカスタマイズするには、リポジトリーの名前に合うように「github-repo-name」を設定します。[「deploy.json」](#toolchains_custom_deploy_json)ファイル内の詳細も更新する必要があります。

 開発、QA、実動ステージを含むより複雑なパイプラインを作成する場合は、「parameters」キーの次のプロパティーを置き換えます。

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


 ## パイプラインの構成
 {: #toolchains_custom_pipeline_yml}

 「pipeline.yml」ファイルには、パイプラインのステージの構成の詳細がすべて含まれます。既存の pipeline.yml から開始して、ニーズに合わせてこれをカスタマイズできます。

 ツールチェーンに複数のパイプラインが含まれている場合、「pipeline.yml」ファイルごとに固有の名前を指定します。

 以下は「pipeline.yml」ファイルの例です。

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
      # ログの表示
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## パイプライン・インターフェースの構成
 {: #toolchains_custom_deploy_json}

 ツールチェーンの作成ページで、「構成可能な統合 (Configurable Integrations)」セクションから「Delivery Pipeline」を選択すると、セクションが展開されて次のアイテムが表示されます。

 	* The application's name
 	* The Region, Organization, and Space that your pipeline stages deploy to.

ツールごとにこれらのアイテムを構成できます。

 ![Delivery Pipeline の構成設定](images/deploy_configuration.png)

 UI のこのセクションのレイアウトは、「deploy.json」スキーマによって定義されます。

 スキーマ内で、アプリケーションの詳細と一致するように、次のプロパティーを更新する必要があります。* Title
 	* Description
 	* LongDescription
 	* All instances of `hello-world-name` and associated details should be modified to match that of your application.

 次のスニペットは、「deploy.json」ファイルの例です。

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


 ## 他のツール構成

 ツールチェーンの中核となるコンポーネントを構成したら、ツールチェーンに機能を追加する他のツールの統合を含めることができます。追加するすべてのツールについて、「toolchain.yml」ファイルに独自のエントリーが必要です。一部のツールの場合は、「.bluemix」ディレクトリーに個別の YAML 構成ファイルを追加することも必要になります。

 ![ツールチェーンの定義に必要なファイル](images/files_for_toolchain_with_additional_tools.png)

使用可能なツール統合のリストについては、<a ref="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">ツールチェーン・テンプレートで使用可能なサービス</a>を参照してください。次の例に、ツールチェーンの YAML ファイルに追加をフォーマットする方法を示します。

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
