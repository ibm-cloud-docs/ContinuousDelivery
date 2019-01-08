---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-6"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# FAQ
{: #ts_cd}

{{site.data.keyword.contdelivery_full}} の使用に関する、よくある質問に対する回答を示します。
{:shortdesc}


## GitHub ツール統合をツールチェーンに追加しようとしたのですが、ツール統合が追加されませんでした。
{: #cannot_authorize_github}
{: faq}

{{site.data.keyword.Bluemix_notm}} に GitHub アカウントへのアクセスを許可していない場合、ツール統合はツールチェーンに追加されません。

ツールチェーン作成時に GitHub ツール統合を構成している場合、以下の手順を実行して、GitHub を指定して許可します。

  1. 「構成可能な統合 (Configurable Integrations)」セクションで**「GitHub」**をクリックします。
  1. {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを作成していて、GitHub にアクセスできるよう {{site.data.keyword.Bluemix_notm}} を認可していない場合、**「認可 (Authorize)」**をクリックして GitHub Web サイトに移動します。
  1. アクティブな GitHub セッションがない場合は、ログインするよう求められます。 **「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。

既にツールチェーンが存在している場合は、GitHub ツール統合の構成を更新します。

 1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
 1. GitHub カードで、メニューをクリックし、**「構成」**をクリックします。
 1. {{site.data.keyword.Bluemix_notm}} が GitHub にアクセスすることを許可するよう構成設定を更新します。 **「認可 (Authorize)」**をクリックして GitHub Web サイトに移動します。 アクティブな GitHub セッションがない場合は、ログインするよう求められます。 **「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。
 1. 設定の更新が完了したら、**「統合の保存」**をクリックします。


## ツールチェーンを作成しようとしたときに、エラーが発生しました。
{: #cannot_create_toolchain}
{: faq}

組織でツールチェーンを作成しようとしたときに、以下のエラー・メッセージが表示された場合は、組織のツールチェーンを 1 つ以上削除してから、もう一度ツールチェーンを作成してください。

`この組織には、200 個のツールチェーンが含まれています。これは上限です。 別のツールチェーンを追加する前に、この組織から 1 つ以上のツールチェーンを削除してください。`


## ツールチェーン・ページで、{{site.data.keyword.contdelivery_short}} サービスの Lite プランを超えたと表示されるのはなぜですか?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} には、Lite と Professional の 2 つのプランがあります。 {{site.data.keyword.contdelivery_short}} Lite プランの場合、プランの制限まで無料でツールチェーンを使用できます。 このエラー・メッセージは、ユーザーが Lite プランの制限を 1 つ以上超えたことを示します。 例えば、{{site.data.keyword.contdelivery_short}} サービス・インスタンスに関連付けられている許可ユーザーが多すぎる場合、または {{site.data.keyword.deliverypipeline}} ジョブの最大数を実行した場合には、プランを超えてしまう可能性があります。 プランの条件について詳しくは、 [プランの制限と使用法](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}を参照してください。


## ツールチェーンを作成しましたが、ツールチェーン・ページには継続的デリバリー・サービスが必要であると表示されるのはなぜですか?
{: #service_required_resource_group}
{: faq}

ツールチェーンと同じリソース・グループまたは組織にある {{site.data.keyword.contdelivery_short}} サービス・インスタンスのプランのご利用条件は、サービスに含まれているツール統合の一部 ({{site.data.keyword.deliverypipeline}}、Eclipse Orion {{site.data.keyword.webide}}、および {{site.data.keyword.gitrepos}}) の使用を管理します。 エラー・メッセージは、リソース・グループまたは組織に {{site.data.keyword.contdelivery_short}} サービスの必要なインスタンスが含まれていないことを示しています。 プランの条件について詳しくは、 [プランの制限と使用法](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}を参照してください。


## Cloud Foundry 組織内にツールチェーンを作成しました。ツールチェーン・ページに継続的デリバリー・サービスが必要であると表示されるのはなぜですか?
{: #service_required_cloud_foundry}
{: faq}

{{site.data.keyword.contdelivery_short}} サービスのインスタンスが含まれていないリソース・グループまたは組織内にツールチェーンを作成すると、ツールチェーン・プラットフォームは、Lite プランを使用してサービスのインスタンスを自動的に作成しようとします。 エラー・メッセージは、ツールチェーン・プラットフォームがサービス・インスタンスを作成できなかったことを示しています。

このエラーは、米国南部地域や、{{site.data.keyword.contdelivery_short}} のインスタンスがまだ存在しない Cloud Foundry 組織でツールチェーンを作成すると発生することがあります。 米国南部地域では、リソース・グループ内に {{site.data.keyword.contdelivery_short}} サービスの新規インスタンスをすべて作成する必要があります。 

リソース・グループにツールチェーンを作成するか、すでに {{site.data.keyword.contdelivery_short}} のインスタンスが存在する組織にツールチェーンを作成することができます。
  

## {{site.data.keyword.Bluemix_notm}} にアプリをデプロイしようとしたときに、エラーが発生しました。
{: #org_outofmemory}
{: faq}

{{site.data.keyword.Bluemix_notm}} にアプリをデプロイしようとしたときに、以下のエラー・メッセージが表示された場合は、組織に残っているメモリー量が、デプロイしようとしているアプリに必要なメモリー量より少なくなっています。

`失敗 サーバー・エラー、状況コード: 400、エラー・コード: 100005、メッセージ: 組織のメモリー上限を超過しました。`

アカウントのメモリー割り当て量を増やすか、アプリが使用するメモリーを減らします。 トライアル・アカウントの最大メモリー割り当て量は 2 GB です。 アカウントのメモリー割り当て量を増やすには、トライアル・アカウントを支払アカウントに移行してください。 トライアル・アカウントを支払アカウントに移行する方法については、[支払アカウント](/docs/pricing/index.html#pay-accounts)を参照してください。 アプリが使用するメモリーを減らすには、{{site.data.keyword.Bluemix_notm}} コンソールまたは CF コマンド・ライン・インターフェースのいずれかを使用します。

{{site.data.keyword.Bluemix_notm}} コンソールを使用する場合は、以下の手順を実行します。

1. 「アプリ」ダッシュボードでアプリを選択します。 アプリ詳細ページが開きます。
1. 「ランタイム」ペインで、メモリー上限またはアプリ・インスタンス数のいずれか、あるいはその両方を減らすことができます。

CF コマンド・ライン・インターフェースを使用する場合は、以下の手順を実行します。

1. アプリで使用しているメモリー量を調べます。 cf apps コマンドを実行すると、現行スペースにデプロイしたアプリがすべてリストされます。 各アプリの状況も表示されます。

	  ```
	  cf apps
	  ```

1. アプリが使用するメモリー量を減らすには、アプリ・インスタンス数またはメモリー上限のいずれか、あるいはその両方を減らします。

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```
    
1. アプリを再始動して、変更を有効にします。


## アプリを作成しましたが、Eclipse Orion Web IDE の実行バーに {{site.data.keyword.Bluemix_notm}} Live Sync アイコンが表示されません。
{: #ts_llz_lkb_3r}
{: faq}

![実行バー](images/webide_runbar_light.png)   

以下の状況では、Web IDE で Node.js アプリを編集するときに、{{site.data.keyword.Bluemix_notm}} ライブ編集、即時再始動、デバッグの各アイコンが実行バーに表示されません。


* `manifest.yml` ファイルがプロジェクトの最上位に格納されていない。
* アプリはルートではなくサブディレクトリーに格納されているが、そのサブディレクトリーのパスが `manifest.yml` ファイルに指定されていない。
* アプリに `package.json` ファイルが含まれていない。


`manifest.yml` ファイルがルートに格納されていない場合は、そこに格納します。 アプリがサブディレクトリーに格納されている場合は、そのサブディレクトリーのパスを `manifest.yml` ファイルに指定します。 アプリに `package.json` ファイルが含まれていない場合は、アプリと同じディレクトリー内に作成します。


## ツールチェーンをクリックしてその「概要」ページを表示しようとしても、ツールチェーンがロードされません。
{: #toolchains_load}
{: faq}

{{site.data.keyword.Bluemix_notm}} の「状況」ページを確認して、{{site.data.keyword.Bluemix_notm}} プラットフォームや、{{site.data.keyword.Bluemix_notm}} の主なサービスに影響を与えている既知の問題がないか判別します。

「状況」ページは、以下のいずれかのオプションによって表示できます。

  * {{site.data.keyword.Bluemix_notm}} コンソールにログインします。 メニュー・バーで、**「サポート」**をクリックして**「状況」**を選択します。 リストされたリソースについて ![問題](../../get-support/images/some_issues.svg) アイコンがないか確認してください。 このアイコンは、障害があることを示している可能性があります。
  * [{{site.data.keyword.Bluemix_notm}} - システム状況 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/status){: new_window} で直接アクセスします。

{{site.data.keyword.Bluemix_notm}} の「状況」ページについて詳しくは、[Viewing {{site.data.keyword.Bluemix_notm}} status](https://cloud.ibm.com/docs/get-support/ViewStatus.html#viewing-bluemix-status) を参照してください。


## ツールチェーン用にツール統合を構成しようとしましたが、構成されませんでした。
{: #tool_integration_error}
{: faq}

ツール統合を追加すると、ツールチェーンはそのツール統合によって表されるツールと通信して、必要なリソースのプロビジョンを行い、それらをツールチェーンと関連付けます。 このセットアップ処理中にエラーが発生した場合、または、ツールチェーンとツールとの間の通信が正常に完了しない場合、ツール統合はエラー状態になります。

 ![Setup failed エラー](images/tool_setup_failed.png)

次のようにして、ツール統合の構成を再試行できます。

1. ツール・カードで `Setup failed` メッセージの上に移動し、**「再構成 (Reconfigure)」**をクリックします。

 ![「再構成」ボタン](images/tool_reconfigure.png)

1. 有効な構成パラメーターを使用していることを確認します。 無効な構成が原因でエラーが起こった場合、例えば `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey` のようなエラー・メッセージが表示されます。 ツール統合の設定を更新し、**「統合の保存」**をクリックします。
1. 通信の問題が原因でエラーが起こった場合、**「統合の保存」**をクリックして再試行します。
