---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: Eclipse Orion {{site.data.keyword.webide}}, file types, Local Editor Settings icon

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:download: .download}

# Eclipse Orion Web IDE での開発
{: #web_ide}

Eclipse Orion {{site.data.keyword.webide}} は、ブラウザー・ベースの開発環境であり、この開発環境では、コンテンツ・アシスト、コード補完、エラー・チェックによる支援を使用して、JavaScript、HTML、CSS で Web の開発を行うことができます。 {{site.data.keyword.webide}} はほとんどすべての言語に対応しており、大部分のファイル・タイプの構文を強調表示できます。 ソース管理が組み込まれており、コードをローカルにデプロイしてアプリのテストとデバッグを行うことができます。
{:shortdesc}

何よりも良い点は、{{site.data.keyword.webide}} が Web ベースであるという点です。 インストールが必要なものは何もなく、保守や拡大縮小が必要なものも何もありません。 インターネット接続さえあれば、どこでも開発を行うことができます。

規制対象データを {{site.data.keyword.webide}} 内のファイルに保存しないでください。 規制対象データ用の手順は現在機能していません。
{: tip}

{{site.data.keyword.webide}} は、キーボードでアクセスすることができますが、スクリーン・リーダーでも良好に動作します。 {{site.data.keyword.webide}} を使用してコードを編集することができますが、必要に応じて、任意のコード・エディターまたはテキスト・エディターを使用してコードを編集することもできます。 {{site.data.keyword.webide}} で提供されている Git 機能を使用することもできます。あるいは、Git コマンド・ラインまたは github.com を使用して {{site.data.keyword.webide}} Git 機能にアクセスすることもできます。
{: note}

## IDE のセットアップ
{: #editorsetup}

{{site.data.keyword.webide}} はカスタマイズ可能であり、開発ニーズに合わせて、カラー・スキーム、テクニカル・ツール、および設定を選択することができます。 これらの設定を表示および変更するには、左側のナビゲーション・サイドバーから、**「設定」**アイコン <img class="inline" src="images/webide_settings_icon_light_small.png" alt="設定アイコン"> をクリックします。

編集中にしばしば設定を変更する必要がある場合は、**「ローカル・エディター設定」**アイコン <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="「ローカル・エディター設定」アイコン">から簡単に設定にアクセスできます。

![ローカル・エディター設定](images/webide_local_editor_settings_light.png)

デフォルトでは、エディター・スタイルとフォント・サイズの設定が常に表示されます。 他のエディター設定をメニューに含めるには、以下の手順を実行します。

1. **「ローカル・エディター設定」**アイコン<img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="「ローカル・エディター設定」アイコン">をクリックします。

2. **「エディター設定」**をクリックします。

3. **「ローカル・エディター設定」**メニューから設定を組み込んだり除外したりするには、各設定の星印をクリックします。

![「エディター設定」トグル](images/webide_editor_settings_toggle_light.png)


## コードの編集
{: #editcode}

{{site.data.keyword.webide}} には、2 つの主要セクションがあります。 1 つ目のセクションはファイル・ナビゲーターであり、プロジェクト・ファイルがツリー構造で表示されます。 ファイル・ナビゲーターから、ファイルとフォルダーの作成、名前変更、削除、管理を行うことができます。

ファイルをファイル・ナビゲーターにアップロードするには、対象のファイルをコンピューターからファイル・ナビゲーターにドラッグします。
{: tip}

2 つ目のセクションはエディター・ペインです。 このエディターは、コンテンツ・アシストや構文検査など、いくつかのコーディング機能を備えています。

![Web IDE](images/webide_light.png)

### 複数のファイルの処理
1. 2 つのファイルを同時に操作するには、**「分割エディター・モードを変更します」**アイコン<img class="inline" src="images/webide_split_editor_icon_light_small.png"  alt="「分割エディター」アイコン">をクリックします。
2. 開いたメニューから、1 つのビューを選択します。

 ビューを選択した後、既にエディターで開かれていたファイルがある場合、そのファイルは両方のエディター・ビューに表示されます。

 一方のエディター・ビューに表示されているファイルをオープンまたは変更するには、次のようにします。
 1. 変更するエディター・ビューにカーソルを移動します。
 2. ファイル・ナビゲーターで、いずれかのファイルをクリックします。

### キーボード・ショートカット
{{site.data.keyword.webide}} のコマンドの多くは、キーボード・ショートカットでもアクセス可能です。

エディターのキーボード・ショートカットのリストを表示するには、**「ツール (Tools)」** > **「キーの表示 (Show keys)」**をクリックします。 または、Alt+Shift+? を押すか、MacOS の場合は Ctrl+Shift+? を押してリストを表示することもできます。 キーの上に移動し、鉛筆をクリックして新しいキー・バインディングを入力することで、ショートカットをカスタマイズできます。

## ソース・コードの管理
{: #sourcecontrol}

{{site.data.keyword.webide}} は、ソース・コード管理ツールと統合されています。 Git リポジトリーに関する作業を行うには、**「Git リポジトリー」**アイコン<img class="inline" src="images/webide_git_icon_light_small.png"  alt="「Git リポジトリー」アイコン">をクリックします。  詳しくは、[Eclipse Orion Web IDE での Git の作業](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_web_ide#git_web_ide)を参照してください。

## ワークスペースからのアプリのデプロイ
{: #deploy}

1. アプリをデプロイするには、実行バーから、起動構成を選択または作成します。![実行バー](images/webide_runbar_light.png)   
1. 「デプロイ」アイコン<img class="inline" src="images/webide_deploy_button_light_small.png"  alt="「デプロイ」アイコン">をクリックします。 ワークスペースの現在の内容と、起動構成に定義された環境を使用して、アプリのインスタンスがデプロイされます。
2. アプリがデプロイされた後、実行バーを使用して、アプリの停止、再始動、デバッグ、ログの表示などを行うことができます。

<table role="presentation">
<tr><td><img src="./images/stop_button.png"  alt="停止アイコン"></td><td>アプリを停止します。</td></tr>
<tr><td> <img src="./images/open_app_url.png"  alt="アプリ URL を開くアイコン"></td><td> デプロイされたアプリを開きます。</td></tr>
<tr><td><img src="./images/view_logs.png"  alt="ログ表示アイコン"></td><td>デプロイされたアプリのログを表示します。</td></tr>
<tr><td><img src="./images/open_dashboard.png"  alt="ダッシュボードを開くアイコン"></td><td>アプリのダッシュボードを開きます。</td></tr>
</table>

Node.js アプリを開発している場合は、ライブ編集モードを有効にします <img  src="./images/enable_live_edit.png"  alt="ライブ編集を有効にするスライダー">。

<table role="presentation"><tr><td><img src="./images/live_edit_restart.png"  alt="ライブ編集再開アイコン"></td><td>ライブ編集モードを有効にして、再デプロイメントなしでアプリを素早く再始動します。</td></tr>
<tr><td> <img src="./images/debug_icon.png"  alt="デバッグ・アイコン"></td>
<td>ライブ編集モードを有効にして、デバッガーにアクセスします。
</td></tr>
</table>

## サポートされる言語
{: #supported_languages}

Eclipse Orion {{site.data.keyword.webide}} では、コンテンツ・アシスト、ツールチップ、プレビュー、妥当性検査を提供しており、JavaScript、HTML、CSS、Markdown の各ファイルの構文を構文強調します。 また、以下のファイル・タイプの構文も強調表示できます。

<table role="presentation">
<tr>
<td>
<ul><li>Arduino
</li><li>C</li>
<li>C#
</li><li>C++
</li><li>CoffeeScript
</li><li>CSHTML
</li><li>組み込み JavaScript (ejs)
</li><li>Erlang
</li><li>Go
</li><li>HTML 抽象化マークアップ言語 (Haml)
</li><li>Jade
</li><li>Java
</li><li>JSON
</li><li>Less  
</li><li>Lua  
</li><li>Objective-C
</li><li>PHP
</li><li>Python</li></ul>
</td>
<td>
<ul><li>Ruby
</li><li>Sass/SCSS
</li><li>SQL
</li><li>Swift
</li><li>TypeScript
</li><li>Visual Basic (vb)
</li><li>VMHTML
</li><li>XHTML
</li><li>XML
</li><li>XQuery
</li><li>YAML
</li><li>Launch ファイル 	
</li><li>Dockerfile
</li><li>gitignore
</li><li>git config
</li><li>cfignore
</li><li>properties
</li></ul>
</td>
</tr>
</table>

## チュートリアルを始める: Eclipse Orion Web IDE
{: #toolchain_web_ide_tutorials}

[IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external} の以下のチュートリアルのいずれかをご確認ください。

  * [「Develop a Cloud Foundry app」ツールチェーンを使用して、初めてツールチェーンを作成し、使用します](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}。

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンを使用します](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}。 
