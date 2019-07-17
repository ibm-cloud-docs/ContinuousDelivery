---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
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

## ツールチェーン・ページで、{{site.data.keyword.contdelivery_short}} サービスの Lite プランを超えたと表示されるのはなぜですか?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} には、Lite と Professional の 2 つのプランがあります。 {{site.data.keyword.contdelivery_short}} Lite プランの場合、プランの制限まで無料でツールチェーンを使用できます。 このエラー・メッセージは、ユーザーが Lite プランの制限を 1 つ以上超えたことを示します。 例えば、{{site.data.keyword.contdelivery_short}} サービス・インスタンスに関連付けられている許可ユーザーが多すぎる場合、または {{site.data.keyword.deliverypipeline}} ジョブの最大数を実行した場合には、プランを超えてしまう可能性があります。 プランの条件について詳しくは、 [プランの制限と使用法](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)を参照してください。


## {{site.data.keyword.contdelivery_short}} サービスで、ライト・プラン・サービスは、非アクティブの状態が 30 日経過すると削除されると説明されています。 非アクティブとは何ですか?
{: #plan_inactivity}
{: faq}

{{site.data.keyword.contdelivery_short}} サービスのインスタンスは、同じリソース・グループまたは Cloud Foundry 組織 (org) 内の 1 つ以上のツールチェーンがアクティブである場合にアクティブと見なされます。 ツールチェーンがアクティブであると見なされるのは、ユーザーがユーザー・インターフェースを介してそれと対話作業を行ったり、デリバリー・パイプライン・ジョブがトリガーされたり、{{site.data.keyword.gitrepos}} によって管理されているリポジトリーへのアクセスが行われたり、Eclipse Orion {{site.data.keyword.webide}} ワークスペースが使用されている場合です。 非アクティブであると見なされるためには、{{site.data.keyword.contdelivery_short}} サービスに関連付けられているすべてのツールチェーンについて、これらのすべての条件が 30 日間発生しないことが必要です。


## ツールチェーンを作成しましたが、ツールチェーン・ページには継続的デリバリー・サービスが必要であると表示されるのはなぜですか?
{: #service_required_resource_group}
{: faq}

ツールチェーンと同じリソース・グループまたは組織にある {{site.data.keyword.contdelivery_short}} サービス・インスタンスのプランのご利用条件は、サービスに含まれているツール統合の一部 ({{site.data.keyword.deliverypipeline}}、Eclipse Orion {{site.data.keyword.webide}}、および {{site.data.keyword.gitrepos}}) の使用を管理します。 エラー・メッセージは、リソース・グループまたは組織に {{site.data.keyword.contdelivery_short}} サービスの必要なインスタンスが含まれていないことを示しています。 プランの条件について詳しくは、 [プランの制限と使用法](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)を参照してください。


## Cloud Foundry 組織のツールチェーンの情報を更新したのですが、ツールチェーンの変更が表示されないのはなぜですか?
{: #updates_in_cloud_foundry}
{: faq}

Cloud Foundry からツールチェーン情報を直接更新すると、{{site.data.keyword.contdelivery_short}} サービスが更新されて変更内容が表示されるまでに数分かかることがあります。 例えば、Cloud Foundry 組織でユーザーを追加または削除した場合、{{site.data.keyword.contdelivery_short}} が新しいユーザーがいることを検出し、そのユーザーがツールチェーンにアクセスできるようになるまでに数分かかることがあります。


## Cloud Foundry 組織内にツールチェーンを作成しました。ツールチェーン・ページに継続的デリバリー・サービスが必要であると表示されるのはなぜですか?
{: #service_required_cloud_foundry}
{: faq}

{{site.data.keyword.contdelivery_short}} サービスのインスタンスが含まれていないリソース・グループまたは組織内にツールチェーンを作成すると、ツールチェーン・プラットフォームは、Lite プランを使用してサービスのインスタンスを自動的に作成しようとします。 エラー・メッセージは、ツールチェーン・プラットフォームがサービス・インスタンスを作成できなかったことを示しています。

このエラーは、米国南部地域や、{{site.data.keyword.contdelivery_short}} のインスタンスがまだ存在しない Cloud Foundry 組織でツールチェーンを作成すると発生することがあります。 米国南部地域では、リソース・グループ内に {{site.data.keyword.contdelivery_short}} サービスの新規インスタンスをすべて作成する必要があります。 

リソース・グループにツールチェーンを作成するか、すでに {{site.data.keyword.contdelivery_short}} のインスタンスが存在する組織にツールチェーンを作成することができます。
  

## ツールチェーンを Cloud Foundry 組織からリソース・グループに移動するにはどうしたらよいですか?
{: #toolchain_move_to_resource_group}
{: faq}

ツールチェーンを Cloud Foundry 組織からリソース・グループに自動的にマイグレーションするフィーチャーはまだ利用できません。 代わりに、リソース・グループ内にツールチェーンを手動で再度作成してから、Cloud Foundry 組織から元のツールチェーンを削除することができます。


## {{site.data.keyword.Bluemix_notm}} にアプリをデプロイしようとしたときに、エラーが発生しました。
{: #org_outofmemory}
{: faq}

{{site.data.keyword.Bluemix_notm}} にアプリをデプロイしようとしたときに、以下のエラー・メッセージが表示された場合は、組織に残っているメモリー量が、デプロイしようとしているアプリに必要なメモリー量より少なくなっています。

`失敗 サーバー・エラー、状況コード: 400、エラー・コード: 100005、メッセージ: 組織のメモリー上限を超過しました。`

アカウントのメモリー割り当て量を増やすか、アプリが使用するメモリーを減らします。 トライアル・アカウントの最大メモリー割り当て量は 2 GB です。 アカウントのメモリー割り当て量を増やすには、トライアル・アカウントを支払アカウントに移行してください。 トライアル・アカウントを支払アカウントに切り替える方法については、『[アカウントをアップグレードまたは変更するには、どのようにすればよいですか?](/docs/account?topic=account-accountfaqs#changeacct)』を参照してください。 アプリが使用するメモリーを減らすには、{{site.data.keyword.Bluemix_notm}} コンソールまたは CF コマンド・ライン・インターフェースのいずれかを使用します。

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


## アプリを作成しましたが、{{site.data.keyword.webide}} の実行バーに {{site.data.keyword.Bluemix_notm}} Live Sync アイコンが表示されないのはなぜですか?
{: #ts_llz_lkb_3r}
{: faq}

![実行バー](images/webide_runbar_light.png)   

以下の状況では、{{site.data.keyword.webide}} で Node.js アプリを編集するときに、{{site.data.keyword.Bluemix_notm}} のライブ編集、即時再始動、デバッグの各アイコンが実行バーに表示されません。


* `manifest.yml` ファイルがプロジェクトの最上位に格納されていない。
* アプリはルートではなくサブディレクトリーに格納されているが、そのサブディレクトリーのパスが `manifest.yml` ファイルに指定されていない。
* アプリに `package.json` ファイルが含まれていない。


`manifest.yml` ファイルがルートに格納されていない場合は、そこに格納します。 アプリがサブディレクトリーに格納されている場合は、そのサブディレクトリーのパスを `manifest.yml` ファイルに指定します。 アプリに `package.json` ファイルが含まれていない場合は、アプリと同じディレクトリー内に作成します。


## {{site.data.keyword.webide}} 実行ボタンをクリックしましたが、ログ・ファイルはどこにありますか? 
{: #web_ide_log_files}
{: faq}  

実行ボタンをクリックすると、デスクトップで `cf push` と入力した場合にデプロイされる場合と同じ方法で、ワークスペースのコンテンツが Cloud Foundry にプッシュされます。 Cloud Foundry ダッシュボードからログ・ファイルを見つけることができます。

ワークスペースのコンテンツをデプロイする方法について詳しくは、[ワークスペースからのアプリのデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy)を参照してください。


## {{site.data.keyword.webide}} で Git ビューのすべての変更が自動的に選択されるのを防ぐにはどうしたらよいですか? 
{: #web_ide_git_view}
{: faq} 

{{site.data.keyword.webide}} はデフォルトで、ユーザーが Git ページに移動するたびに出力変更を自分のコード・リポジトリーにプッシュするという想定で機能します。 GIT 設定ページからコミット、同期、リセット、および置換するリソースを手動で選択する場合は、**「変更済みファイルを常に選択」**チェック・ボックスをクリアします。


## 自分が使用している言語が {{site.data.keyword.webide}} でサポートされていないのはなぜですか? 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}} では、JavaScript、HTML、CSS 向けの広範なツールとサポートが提供されています。 さらに、一般的によく使用される言語の構文強調表示もサポートしています。 特定の言語をサポートするように {{site.data.keyword.webide}} を拡張することはできません。 {{site.data.keyword.webide}} がサポートする言語の完全なリストを表示するには、[サポートされている言語](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages)を参照してください。


## {{site.data.keyword.Bluemix_notm}} と {{site.data.keyword.contdelivery_short}} サービスの状況を確認するにはどうしたらよいですか?
{: #toolchains_load}
{: faq}

{{site.data.keyword.Bluemix_notm}} の「状況」ページを確認して、{{site.data.keyword.Bluemix_notm}} プラットフォームや、{{site.data.keyword.Bluemix_notm}} の主なサービスに影響を与えている既知の問題がないか判別します。

「状況」ページは、以下のいずれかのオプションによって表示できます。

  * {{site.data.keyword.Bluemix_notm}} コンソールにログインします。 メニュー・バーで、**「サポート」**をクリックして**「状況」**を選択します。 リストされたリソースについて ![問題](../../get-support/images/some_issues.svg) アイコンがないか確認してください。 このアイコンは、障害があることを示している可能性があります。
  * [{{site.data.keyword.Bluemix_notm}} - システム状況](https://cloud.ibm.com/status){: external}で直接アクセスします。

{{site.data.keyword.Bluemix_notm}} の「状況」ページについて詳しくは、[Viewing {{site.data.keyword.Bluemix_notm}} status](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status) を参照してください。


## パイプライン・ジョブ間で成果物を渡すにはどうしたらよいですか?
{: #artifacts_pipeline_jobs}
{: faq}

同じステージに属するすべてのパイプライン・ジョブは同じステージ入力を受け取るため、同じステージに属するジョブ間で成果物を渡すことはできません。 ただし、ビルド・ジョブは他のステージのジョブが使用できる成果物を生成します。 2 つのジョブ間で成果物を渡すには、各ジョブを別々のステージに移動します。 パイプライン・ジョブについて詳しくは、[ジョブ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs)を参照してください。


## パイプライン・ジョブを実行できる最大時間制限はありますか?
{: #pipeline_jobs_time_limit}
{: faq}

各パイプライン・ジョブは最大 60 分間実行できます。 ジョブがこの制限時間を超えると、ジョブは失敗します。 パイプライン・ジョブが実行する作業を小さなステップに分割できるかどうかを確認してください。 パイプライン・ジョブは、60 分未満で実行される複数の短いパイプライン・ジョブに分割できます。


## パイプライン・セキュア・プロパティーはどれほど安全ですか?
{: #pipeline_secure_properties}
{: faq}

パイプライン・セキュア・プロパティーは、AES-128 を使用して暗号化され、パイプライン・スクリプトに渡される直前に復号されます。 これらのプロパティーは、プロパティーのユーザー・インターフェースおよびパイプライン・ログ・ファイルの中で、アスタリスクを使用してマスクされます。 パイプライン・ジョブのログ・ファイルにデータが書き込まれる前に、パイプライン・セキュア・プロパティーのすべての値と完全に一致するものがあるかどうかスキャンされます。 一致が見つかった場合、アスタリスクを使用してマスクされます。 完全に一致するものだけがマスクされるため、セキュア・プロパティーとログ・ファイルを扱う際には注意してください。 
