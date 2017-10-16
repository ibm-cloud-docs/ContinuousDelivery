---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# {{site.data.keyword.contdelivery_short}} のトラブルシューティング
{: #ts_cd}

{{site.data.keyword.contdelivery_full}} の使用に関するトラブルシューティングのための一般的な質問に対する回答を示します。
{:shortdesc}


## GitHub で許可できない
{: #cannot_authorize_github}

ユーザーが GitHub で許可されていません。
{:shortdesc}

GitHub アカウントにアクセスできるように {{site.data.keyword.Bluemix_notm}} を許可していない場合、以下の問題が発生する可能性があります。
{: tsSymptoms}

 * GitHub ツール統合をツールチェーンに追加しようとしたときに、ツール統合が追加されない。
 * 変更を GitHub リポジトリーまたは GitHub Enterprise リポジトリーにプッシュしたときに、パイプラインが自動的に実行されない。

{{site.data.keyword.Bluemix_notm}} が GitHub へのアクセスを許可されていません。  
{: tsCauses}

ツールチェーン作成時に GitHub ツール統合を構成している場合、以下の手順を実行します。
{: tsResolve}

  1. 「構成可能な統合 (Configurable Integrations)」セクションで**「GitHub」**をクリックします。
  1. {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを作成していて、GitHub にアクセスできるよう {{site.data.keyword.Bluemix_notm}} を認可していない場合、**「認可 (Authorize)」**をクリックして GitHub Web サイトに移動します。
  1. アクティブな GitHub セッションがない場合は、ログインするよう求められます。**「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。

既にツールチェーンが存在している場合は、GitHub ツール統合の構成を更新します。

 1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
 1. GitHub カードで、メニューをクリックし、**「構成」**をクリックします。
 1. {{site.data.keyword.Bluemix_notm}} が GitHub にアクセスすることを許可するよう構成設定を更新します。**「認可 (Authorize)」**をクリックして GitHub Web サイトに移動します。アクティブな GitHub セッションがない場合は、ログインするよう求められます。**「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。
 1. 設定の更新が完了したら、**「統合の保存」**をクリックします。


## ツールチェーンを作成できない
{: #cannot_create_toolchain}

ツールチェーンを作成すると、エラーが表示されます。
{:shortdesc}

ツールチェーンを作成すると、次のようなエラー・メッセージが表示されます。
{: tsSymptoms}

`この組織には、200 個のツールチェーンが含まれています。これは上限です。別のツールチェーンを追加する前に、この組織から 1 つ以上のツールチェーンを削除してください。`

1 つの組織に 200 個より多くのツールチェーンを含めることはできません。  
{: tsCauses}

組織のツールチェーンを 1 つ以上削除してから、もう一度ツールチェーンを作成してください。
{: tsResolve}


## 組織のメモリー上限を超過
{: #org_outofmemory}

組織のメモリー上限を超過すると、アプリを {{site.data.keyword.Bluemix_notm}} にデプロイできなくなる可能性があります。アプリが使用するメモリーを減らすか、アカウントのメモリー割り当て量を増やすことができます。トライアル・アカウントの最大メモリー割り当て量は 2 GB です。
この割り当ては、支払アカウントにアップグレードするときに増やすことができます。

アプリを {{site.data.keyword.Bluemix_notm}} にデプロイすると、次のエラー・メッセージが表示されます。
{: tsSymptoms}

`失敗 サーバー・エラー、状況コード: 400、エラー・コード: 100005、メッセージ: 組織のメモリー上限を超過しました。`

このエラーは、組織に残っているメモリー量が、デプロイするアプリに必要なメモリー量より少ない場合に発生します。トライアル・アカウントの最大メモリー割り当て量は 2 GB です。
{: tsCauses}

アカウントのメモリー割り当て量を増やすか、アプリが使用するメモリーを減らします。
{: tsResolve}

  * アカウントのメモリー割り当て量を増やすには、トライアル・アカウントを支払アカウントに移行してください。トライアル・アカウントを支払アカウントに移行する方法については、[支払アカウント](/docs/pricing/index.html#pay-accounts)を参照してください。
  * アプリが使用するメモリーを減らすには、{{site.data.keyword.Bluemix_notm}} コンソールまたは CF コマンド・ライン・インターフェースのいずれかを使用します。

    {{site.data.keyword.Bluemix_notm}} コンソールを使用する場合は、以下の手順を実行します。

    1. 「アプリ」ダッシュボードでアプリを選択します。アプリ詳細ページが開きます。
    2. 「ランタイム」ペインで、メモリー上限またはアプリ・インスタンス数のいずれか、あるいはその両方を減らすことができます。

    CF コマンド・ライン・インターフェースを使用する場合は、以下の手順を実行します。

    1. アプリで使用しているメモリー量を調べます。

	  ```
	  cf apps
	  ```

	  cf apps コマンドを実行すると、現行スペースにデプロイしたアプリがすべてリストされます。各アプリの状況も表示されます。

    2. アプリが使用するメモリー量を減らすには、アプリ・インスタンス数またはメモリー上限のいずれか、あるいはその両方を減らします。

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. アプリを再始動して、変更を有効にします。

アプリの管理に関する一般的な問題について詳しくは、[Troubleshooting for managing apps](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps) を参照してください。


## Eclipse Orion Web IDE の実行バーに Bluemix Live Sync アイコンが表示されない
{: #ts_llz_lkb_3r}

アプリを作成しても、Eclipse Orion Web IDE 実行バーに IBM Bluemix Live Sync アイコンが表示されません。ライブ編集アイコンを備えた完全な実行バーが表示されません。

![実行バー](images/webide_runbar_light.png)   

Web IDE で Node.js アプリを編集するときは、{{site.data.keyword.Bluemix_notm}} ライブ編集、即時再始動、デバッグの各アイコンは実行バーに表示されません。
{: tsSymptoms}

以下の場合にはアイコンは使用できません。
{: tsCauses}

* `manifest.yml` ファイルがプロジェクトの最上位に格納されていない。
* アプリはルートではなくサブディレクトリーに格納されているが、そのサブディレクトリーのパスが `manifest.yml` ファイルに指定されていない。
* アプリに `package.json` ファイルが含まれていない。

以下のいずれかのメソッドを使用します。{: tsResolve}

* `manifest.yml` ファイルがルートに格納されていない場合は、そこに格納します。
* アプリがサブディレクトリーに格納されている場合は、そのサブディレクトリーのパスを `manifest.yml` ファイルに指定します。

   ```
    path: path_to_application
    ```
* アプリと同じディレクトリーに `package.json` ファイルを作成します。


## ツールチェーンがロードされない
{: #toolchains_load}

ツールチェーンをクリックしてその「概要」ページを表示しようとしても、ツールチェーンがロードされません。
{:shortdesc}

DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。次に、**「概要」**をクリックします。ツールチェーンの「概要」ページが開きません。
{: tsSymptoms}

{{site.data.keyword.Bluemix_notm}} の状況を見て、問題の原因が障害によるものかどうか確認します。
{: tsCauses}

{{site.data.keyword.Bluemix_notm}} の「状況」ページを参照して、{{site.data.keyword.Bluemix_notm}} プラットフォームや、{{site.data.keyword.Bluemix_notm}} の主なサービスに影響を与えている既知の問題がないか確認します。
{: tsResolve}

「状況」ページは、以下のいずれかのオプションによって表示できます。

  * {{site.data.keyword.Bluemix_notm}} コンソールにログインします。メニュー・バーで、**「サポート」**をクリックして**「状況」**を選択します。リストされたリソースについて ![問題](../../support/images/some_issues.svg) アイコンがないか確認してください。このアイコンは、障害があることを示している可能性があります。
  * [IBM {{site.data.keyword.Bluemix_notm}} - システム状況 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://ibm.biz/bluemixstatus){: new_window} で直接アクセスします。

{{site.data.keyword.Bluemix_notm}} の「状況」ページについて詳しくは、[Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status) を参照してください。


## ツール統合が構成されない
{: #tool_integration_error}

ツールチェーン用にツール統合を構成した後、そのツール統合のツール・カードに `Setup failed` エラーが表示されます。
{:shortdesc}

ツール統合を構成した後、ツールチェーンの「概要」ページに、そのツール統合のツール・カードが表示され、セットアップが失敗したことが通知されます。
{: tsSymptoms}

 ![Setup failed エラー](images/tool_setup_failed.png)

ツール統合を追加すると、ツールチェーンはそのツール統合によって表されるツールと通信して、必要なリソースのプロビジョンを行い、それらをツールチェーンと関連付けます。このセットアップ処理中にエラーが発生した場合、または、ツールチェーンとツールとの間の通信が正常に完了しない場合、ツール統合はエラー状態になります。
{: tsCauses}

次のようにして、ツール統合を再構成します。
{: tsResolve}

1. ツール・カードで `Setup failed` メッセージの上に移動し、**「再構成 (Reconfigure)」**をクリックします。

 ![「再構成」ボタン](images/tool_reconfigure.png)

1. 有効な構成パラメーターを使用していることを確認します。無効な構成が原因でエラーが起こった場合、例えば `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey` のようなエラー・メッセージが表示されます。ツール統合の設定を更新し、**「統合の保存」**をクリックします。
1. 通信の問題が原因でエラーが起こった場合、**「統合の保存」**をクリックして再試行します。



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
