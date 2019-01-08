---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンの作成 {: #deploy-button}

作成した公開アプリを Git で共有する場合、「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンを用意しておくと、他のユーザーがそのコードを試し、ツールチェーンを使用して {{site.data.keyword.Bluemix_notm}} にデプロイできるので、効率的に共有できます。 このボタンは最小限の構成で済み、マークアップをサポートする場所ならどこにでも挿入できます。 他のユーザーがこのボタンをクリックすると、元のアプリには影響を与えることなく、新しい Git リポジトリーにそのコードのクローン・コピーが作成されます。  
{: shortdesc}

他のユーザーがこのボタンをクリックすると、以下のアクションが発生します。

1. そのユーザーがアクティブな {{site.data.keyword.Bluemix_notm}} アカウントを持っていなければ、アカウントを作成する必要があります。 トライアイル・アカウントまたは実アカウントを作成できます。

2. そのユーザーは、{{site.data.keyword.deliverypipeline}} アイコンをクリックすることによって、地域、リソース・グループ (米国南部、米国東部、英国、ドイツ地域で利用可能) または組織やスペース (米国南部、英国、ドイツ地域で利用可能)、およびアプリ名を選択できます。 推奨アプリ名はツールチェーンと同じ名前であり、元の Git リポジトリー名と現在時刻で構成されます。 ツールチェーン名は編集することもできます。

3. ツールチェーンが作成されます。そこには、Git リポジトリーの新しいプライベート・クローン、コード変更をビルドしてデプロイするためのパイプライン、クラウド上でコードを編集するための Eclipse Orion {{site.data.keyword.webide}}、Issue Tracker が含まれます。

  `.bluemix` ディレクトリーに `toolchain.yml` ファイルが含まれていれば、ツールチェーンのツール統合を指定するためにそのファイルが使用されます。 `toolchain.yml` ファイルについて詳しくは、[カスタム・ツールチェーンの作成](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}を参照してください。
  {: tip}

4. アプリがビルド・ファイルを必要とする場合、ビルド・ファイルが自動的に検出されて、アプリがビルドされます。

5. ビルドとデプロイメントのプロセスのためにパイプラインが構成されている場合、`pipeline.yml` ファイルを使用してアプリがデプロイされます。

6. アプリがコンテナーを必要とする場合、{{site.data.keyword.containerlong_notm}} を定義する `pipeline.yml` ファイルとイメージを定義する Dockerfile の両方を使用して、{{site.data.keyword.containerlong_notm}} にアプリがデプロイされます。

7. そのユーザーが選択した {{site.data.keyword.Bluemix_notm}} 組織にアプリがデプロイされます。

## このボタンの例 {: #button-examples}

パブリック {{site.data.keyword.gitrepos}} リポジトリーのアプリ・ボタンの例を以下に示します。

[![IBM Cloud にデプロイ](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

パブリック GitHub リポジトリーのアプリ・ボタンの例を以下に示します。

[![IBM Cloud にデプロイ](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## ボタンの作成 {: #create-button}

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンを作成するには、以下のいずれかのスニペット・テンプレートをコピーして変更します。 URL に Git リポジトリーとブランチを指定します。

### HTML でのボタンの作成

HTML でボタンを作成するには、このスニペットをコピーして、パブリック Git リポジトリー URL とブランチを挿入します。

```HTML
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://cloud.ibm.com/devops/setup/deploy/button.png" alt="IBM Cloud にデプロイ"></a>
```
{: codeblock}

スニペットのリポジトリー URL に `branch` パラメーターを含めない場合、「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンのデフォルトはリポジトリーのマスター・ブランチになります。

### Markdown でのボタンの作成

Markdown でボタンを作成するには、このスニペットをコピーして、パブリック Git リポジトリー URL とブランチを挿入します。

```Markdown
[![IBM Cloud にデプロイ](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

スニペットのリポジトリー URL に `branch` パラメーターを含めない場合、「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンのデフォルトはリポジトリーのマスター・ブランチになります。

### ボタン・スニペットの使用 {: #button-snippet}

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタン・スニペットを作成した後、それをブログ、記事、Wiki、README ファイルなど、アプリを宣伝したい場所に挿入できます。

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンのスニペットをカスタマイズする際、PNG 形式で英語の外部ボタン・イメージのデフォルト・パスを両方のテンプレートで使用することを考慮してください。

* PNG ではなく SVG イメージをボタンに使用する場合は、スニペットで使用されるボタン・イメージのパスを `https://cloud.ibm.com/devops/setup/deploy/button.svg` に変更します。

* ボタンにイメージを使用する場合は、スニペットで使用されるボタン・イメージのパスを `https://cloud.ibm.com/devops/setup/deploy/button_x2.png` に変更します。 このイメージのサイズは、デフォルト・イメージの 2 倍です。

* イメージをローカルに保管する場合は、イメージをダウンロードし、Git リポジトリーに保管できます。 イメージの相対ロケーションを使用するようにパスを調整してください。

* 翻訳版のボタンを使用する場合は、そのボタンをリモートで参照するか、[ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window} からダウンロードすることができます。

## リポジトリーに関する考慮事項 {: #button-repo}

「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンで使用するリポジトリーについて、以下の考慮事項を検討してください。


### ビルド・ファイルの要件
{: build_file}

アプリのデプロイ前にビルドが必要な場合は、リポジトリーにビルド・ファイルを含める必要があります。 リポジトリーのルート・ディレクトリーでビルド・スクリプト・ファイルが検出されると、デプロイメントの前にコードの自動ビルドが起動します。

サポートされるビルダーとしては、以下のものがあります。

* [Ant ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`。ビルド出力は `./output/` フォルダーに置かれます
* [Gradle ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](https://docs.gradle.org/current/userguide/getting_started.html){:new_window} `/build.gradle`。ビルド出力は `.` フォルダーに置かれます
* [Grunt ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`。ビルド出力は `.` フォルダーに置かれます
* [Maven ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン"):](http://maven.apache.org/guides/introduction/introduction-to-the-pom.html){:new_window} `/pom.xml`。ビルド出力は `./target/` フォルダーに置かれます

### パイプライン・ファイルの要件
{: pipeline_file}

ツールチェーン用のパイプラインを構成するには、`.bluemix` ディレクトリーに `pipeline.yml` ファイルを配置します。 ツールチェーンがインスタンス化されると、そのディレクトリー内の `pipeline.yml` ファイルごとにパイプラインが作成されます。

`.bluemix` ディレクトリーに `pipeline.yml` ファイルがない場合は、「{{site.data.keyword.Bluemix_notm}} にデプロイ」ボタンを使用すると、「ビルド」ステージと「デプロイ」ステージ (Cloud Foundry へのデプロイが行われる) という 2 つのステージを含むデフォルトのパイプラインが作成されます。

パイプライン・ファイルを作成する際は、[カスタム・ツールチェーン・パイプラインに関する説明](toolchains_custom.html#toolchains_custom_pipeline_yml)に記載されているサンプル・ファイルを参照してください。 Web インターフェースでパイプラインを定義する場合と同様に、ステージとジョブを作成し、入力と環境変数を設定し、スクリプトを追加することによって、テキストでパイプラインを定義します。 さらに[このデモンストレーション・プロジェクト](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix)に、より複雑なパイプライン・ファイルがいくつか用意されています。

### コンテナー Dockerfile の要件
{: container_dockerfile}

{{site.data.keyword.containerlong_notm}} を使用してアプリをコンテナーにデプロイするには、リポジトリーのルート・ディレクトリーに Dockerfile を含め、`.bluemix` ディレクトリーに `pipeline.yml` ファイルを含める必要があります。

Dockerfile は、アプリのビルド・スクリプトのようなものとして機能します。 リポジトリーで Dockerfile が検出されると、アプリは、コンテナーにデプロイされる前に自動的にイメージにビルドされます。 アプリがイメージにビルドされる前にアプリ自体をビルドする必要がある場合は、Dockerfile に加えてアプリのビルド・スクリプトを含めてください。

Dockerfile の作成について詳しくは、[Docker 資料 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.docker.com/reference/builder/){:new_window} を参照してください。 Kubernetes にデプロイするためにツールチェーン・テンプレートを使用するステップバイステップの手順については、[チュートリアル: 「Develop a Kubernetes app」ツールチェーンを使用する ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window}または[チュートリアル: 「Develop a Kubernetes app with Helm」ツールチェーンを使用する ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window} を参照してください。

Kubernetes クラスターへの Cloud Foundry アプリの移植について詳しくは、[Tutorial: Port a Cloud Foundry app to deploy to Kubernetes in a toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage/tutorials/port-a-cf-app-to-deploy-to-kubernetes-in-a-toolchain?task=0){:new_window} を参照してください。  

コンテナー専用の `pipeline.yml` を手動で作成するには、[GitHub の例 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/Puquios/){:new_window} を参照してください。

### マニフェスト・ファイルの要件 (Cloud Foundry にデプロイされたアプリの場合)
{: #manifest_files}

`manifest.yml` ファイルをリポジトリー内に用意しておく必要はありません。 ただし、アプリが他のサービスの実行を必要とする場合は、それらのサービスを宣言しているマニフェスト・ファイルを用意する必要があります。

マニフェスト・ファイルについて詳しくは、[アプリケーション・マニフェスト](/docs/cloud-foundry/deploy-apps.html#appmanifest)を参照してください。
