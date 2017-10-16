---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# 「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンの作成 {: #deploy-button} 

作成した公開アプリを Git で共有する場合、「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンを用意しておくと、他のユーザーがそのコードを試し、ツールチェーンを使用して IBM {{site.data.keyword.Bluemix_notm}} にデプロイできるので、効率的に共有できます。このボタンは最小限の構成で済み、マークアップをサポートする場所ならどこにでも挿入できます。他のユーザーがこのボタンをクリックすると、元のアプリには影響を与えることなく、新しい Git リポジトリーにそのコードのクローン・コピーが作成されます。
{: shortdesc}

他のユーザーがこのボタンをクリックすると、以下のアクションが発生します。 

1. そのユーザーがアクティブな {{site.data.keyword.Bluemix_notm}} アカウントを持っていなければ、アカウントを作成する必要があります。トライアイル・アカウントまたは実アカウントを作成できます。 

2. そのユーザーは、{{site.data.keyword.deliverypipeline}} アイコンをクリックすることによって、地域、組織、スペース、アプリ名を選択できます。推奨アプリ名はツールチェーンと同じ名前であり、元の Git リポジトリー名と現在時刻で構成されます。ツールチェーン名は編集することもできます。

3. ツールチェーンが作成されます。そこには、Git リポジトリーの新しいプライベート・クローン、コード変更をビルドしてデプロイするためのパイプライン、クラウド上でコードを編集するための Eclipse Orion {{site.data.keyword.webide}}、Issue Tracker が含まれます。 

  **ヒント**: `.bluemix` ディレクトリーに `toolchain.yml` ファイルが含まれていれば、ツールチェーンのツール統合を指定するためにそのファイルが使用されます。`toolchain.yml` ファイルについて詳しくは、[カスタム・ツールチェーンの作成](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}を参照してください。
 
4. アプリがビルド・ファイルを必要とする場合、ビルド・ファイルが自動的に検出されて、アプリがビルドされます。 

5. ビルドとデプロイメントのプロセスのためにパイプラインが構成されている場合、`pipeline.yml` ファイルを使用してアプリがデプロイされます。

6. アプリがコンテナーを必要とする場合、IBM Containers サービスを定義する `pipeline.yml` ファイルとイメージを定義する Dockerfile の両方を使用して、{{site.data.keyword.Bluemix_notm}} コンテナーにアプリがデプロイされます。 

7. そのユーザーが選択した {{site.data.keyword.Bluemix_notm}} 組織にアプリがデプロイされます。 

## このボタンの例 {: #button-examples} 

パブリック {{site.data.keyword.gitrepos}} リポジトリーのアプリ・ボタンの例を以下に示します。

[![Bluemix にデプロイ](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

パブリック GitHub リポジトリーのアプリ・ボタンの例を以下に示します。 

[![Bluemix にデプロイ](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://github.com/ibmjstart/bluemix-node-mysql-uploader){:new_window}

{{site.data.keyword.Bluemix_notm}} コンテナーにデプロイされたアプリのボタンの例を以下に示します。 

[![Bluemix にデプロイ](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://github.com/Puquios/hello-containers){:new_window}

## ボタンの作成 {: #create-button}

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンを作成するには、以下のいずれかのスニペット・テンプレートをコピーして変更します。URL に Git リポジトリーとブランチを指定します。

### HTML でのボタンの作成

HTML でボタンを作成するには、このスニペットをコピーして、パブリック Git リポジトリー URL とブランチを挿入します。

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="Bluemix にデプロイ"></a>
```

スニペットのリポジトリー URL に `branch` パラメーターを含めない場合、「Bluemix にデプロイ」ボタンのデフォルトはリポジトリーのマスター・ブランチになります。

### Markdown でのボタンの作成

Markdown でボタンを作成するには、このスニペットをコピーして、パブリック Git リポジトリー URL とブランチを挿入します。

```Markdown
[![Bluemix にデプロイ](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```

スニペットのリポジトリー URL に `branch` パラメーターを含めない場合、「Bluemix にデプロイ」ボタンのデフォルトはリポジトリーのマスター・ブランチになります。

### ボタン・スニペットの使用{: #button-snippet}

「Bluemix にデプロイ」ボタン・スニペットを作成した後、それをブログ、記事、Wiki、README ファイルなど、アプリを宣伝したい場所に挿入できます。

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンのスニペットをカスタマイズする際、PNG 形式で英語の外部ボタン・イメージのデフォルト・パスを両方のテンプレートで使用することを考慮してください。 

* PNG ではなく SVG イメージをボタンに使用する場合は、スニペットで使用されるボタン・イメージのパスを `https://bluemix.net/deploy/button.svg` に変更します。
	
* ボタンにイメージを使用する場合は、スニペットで使用されるボタン・イメージのパスを `https://bluemix.net/deploy/button_x2.png` に変更します。このイメージのサイズは、デフォルト・イメージの 2 倍です。
	
* イメージをローカルに保管する場合は、イメージをダウンロードし、Git リポジトリーに保管できます。イメージの相対ロケーションを使用するようにパスを調整してください。
	
* 翻訳版のボタンを使用する場合は、そのボタンをリモートで参照するか、[ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window} からダウンロードすることができます。 
	
## リポジトリーに関する考慮事項{: #button-repo} 

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンで使用するリポジトリーについて、以下の考慮事項を検討してください。 

### マニフェスト・ファイルの要件

`manifest.yml` ファイルをリポジトリー内に用意しておく必要はありません。ただし、アプリが他のサービスの実行を必要とする場合は、それらのサービスを宣言しているマニフェスト・ファイルを用意する必要があります。

マニフェスト・ファイルによって、以下を指定できます。 

* 固有のアプリ名。

* 宣言されたサービス。これは、アプリのデプロイ前にセットアップすることが求められる必須サービスまたはオプション・サービス (データ・キャッシュ・サービスなど) を作成または検索するマニフェスト拡張機能です。[CF コマンド・ライン・インターフェース ![外部リンク・アイコン](../../icons/launch-glyph.svg)](https://github.com/cloudfoundry/cli/releases) を使用して `cf marketplace` コマンドを実行するか、[{{site.data.keyword.Bluemix_notm}} カタログ](https://console.bluemix.net/catalog?ssoLogout=true&cm_mmc=developerWorks-_-dWdevcenter-_-devops-services-_-lp#/store)を参照することによって、対象となる {{site.data.keyword.Bluemix_notm}} サービス、ラベル、プランのリストを見つけることができます。

宣言されたサービスは、標準 Cloud Foundry マニフェスト・フォーマットの IBM 拡張です。この拡張機能は、フィーチャーの発展と改善に伴い、今後のリリースで改訂される可能性があります。

マニフェスト・ファイルの作成方法が分からない場合は、[ここで作成方法を確認してください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#minimal-manifest){:new_window}。

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


### ビルド・ファイルの要件

アプリのデプロイ前にビルドが必要な場合は、リポジトリーにビルド・ファイルを含める必要があります。リポジトリーのルート・ディレクトリーでビルド・スクリプト・ファイルが検出されると、デプロイメントの前にコードの自動ビルドが起動します。 

サポートされるビルダーとしては、以下のものがあります。

* [Ant ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`。ビルド出力は `./output/` フォルダーに置かれます
* [Gradle ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window} `/build.gradle`。ビルド出力は `.` フォルダーに置かれます
* [Grunt ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`。ビルド出力は `.` フォルダーに置かれます
* [Maven ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window} `/pom.xml`。ビルド出力は `./target/` フォルダーに置かれます

### パイプライン・ファイルの要件

ツールチェーン用のパイプラインを構成するには、`.bluemix` ディレクトリーに `pipeline.yml` ファイルを配置します。ツールチェーンがインスタンス化されると、そのディレクトリー内の `pipeline.yml` ファイルごとにパイプラインが作成されます。 

パイプライン・ファイルを作成する際は、[カスタム・ツールチェーン・パイプラインに関する説明](toolchains_custom.html#toolchains_custom_pipeline_yml)に記載されているサンプル・ファイルを参照してください。Web インターフェースでパイプラインを定義する場合と同様に、ステージとジョブを作成し、入力と環境変数を設定し、スクリプトを追加することによって、テキストでパイプラインを定義します。さらに[このデモンストレーション・プロジェクト](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix)に、より複雑なパイプライン・ファイルがいくつか用意されています。

### コンテナー Dockerfile の要件

IBM Containers を使用してアプリをコンテナーにデプロイするには、リポジトリーのルート・ディレクトリーに Dockerfile を含め、`.bluemix` ディレクトリーに `pipeline.yml` ファイルを含める必要があります。 

Dockerfile は、アプリのビルド・スクリプトのようなものとして機能します。リポジトリーで Dockerfile が検出されると、アプリは、コンテナーにデプロイされる前に自動的にイメージにビルドされます。アプリがイメージにビルドされる前にアプリ自体をビルドする必要がある場合は、Dockerfile に加えてアプリのビルド・スクリプトを含めてください。

Dockerfile の作成について詳しくは、[Docker 資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.docker.com/reference/builder/){:new_window} を参照してください。

コンテナー固有の `pipeline.yml` を手動で作成するには、[GitHub の例 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/Puquios/){:new_window} を参照してください。
