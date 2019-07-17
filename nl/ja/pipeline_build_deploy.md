---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-14"

keywords: ADD STAGE, Run Stage icon, JOBS tab

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# ビルドとデプロイ
{: #deliverypipeline_build_deploy}

{{site.data.keyword.contdelivery_full}} には、Delivery Pipeline が組み込まれています。これを使用して、反復可能な継続的統合および継続的デリバリー・プロセスを実装できます。
{:shortdesc}

パイプラインを構成するには、以下のタスクを実行します。

## ステージの追加
{: #deliverypipeline_add_stage}

1. 「パイプライン」ページで、**「ステージの追加」**をクリックします。 「ステージ構成」ページが開きます。
2. ステージを構成します。
  1. **「入力」**タブで、ステージの入力を選択します。  「ビルド」ステージの場合、入力タブには、入力に使用するリポジトリー内のブランチを指定する**「ブランチ」**フィールドが含まれます。
  2. **「ジョブ」**タブで、少なくとも 1 つのジョブを追加して構成します。 通常、最初のステージには、少なくとも 1 つのビルド・ジョブがあります。
3. **「保存」**をクリックします。

## ステージへのジョブの追加
{: #deliverypipeline_add_job}

1. ステージで、**「ステージ構成」**アイコンをクリックし、**「ステージの構成」**をクリックします。
2. **「ジョブ」**タブをクリックします。
3. **「ジョブの追加」**をクリックします。 追加するジョブのタイプを選択します。
4. ジョブを構成します。
5. **「保存」**をクリックします。

![ステージへのジョブの追加](images/AddJob2.png)

## ステージの実行
{: #deliverypipeline_run_stage}

「パイプライン」ページで**「ステージの実行」**アイコンをクリックして、手動でステージを実行できます。

![ステージでの「ステージの実行」アイコンのクリック](images/RunStage.png)

次の 2 つの方法のいずれかを使用して、ビルド履歴ページからオンデマンドのビルドとデプロイメントを要求することもできます。
* 構成されたステージの下にあるボックスにビルドをドラッグする。
* 「最終実行の結果」セクションで、**「送信先」**アイコンをクリックし、デプロイ先のスペースを選択する ![「このビルドを含むステージの実行」アイコン](images/deploy_to.png)。

実行中のステージをキャンセルするには、ステージで**「ログおよび履歴の表示」**をクリックします。 ジョブのリストで、実行中のジョブの番号をクリックし、**「キャンセル」**をクリックします。 ジョブをクリックして**「キャンセル」**をクリックするか、そのステージのジョブの**「停止」**アイコンをクリックして、ジョブを個別にキャンセルすることもできます。

## アプリのデプロイ
{: #deliverypipeline_deploy}

デプロイ・ジョブが適切に構成されていれば、いつでもそのジョブが実行されるときに、アプリがターゲットにデプロイされます。 デプロイ・ジョブを手動で実行するには、ジョブがあるステージの**「ステージの実行」**アイコンをクリックします。

### 入力の改訂
{: #deliverypipeline_input_revisions}

ステージを手動で実行するか、その前のステージが完了したために実行される場合、実行中のステージはその入力の改訂を選択します。 通常、入力の改訂はビルド番号です。 入力の改訂を選択するには、ステージは以下の条件に従う必要があります。

* 特定の改訂が選択されている場合は、それを使用する。
* 特定の改訂が指定されていない場合は、同じ入力を使用するステージが見つかるまで前のステージを検索し、 その入力の最後に成功した実行の改訂を見つけて使用する。
* 特定の改訂が指定されておらず、その他のステージが指定ソースを入力として使用しない場合、入力の最新の改訂を使用する。

前のビルドをデプロイすることができます。 ビルドが含まれるステージで、**「ログおよび履歴の表示」**をクリックします。 ページが開いたら、実行番号をクリックして展開し、ビルド・ジョブをクリックします。 **「送信先」**をクリックし、ターゲットを選択します。
{: tip}

### アプリへのサービスの追加
{: #deliverypipeline_add_services}

アプリにサービスを追加し、{{site.data.keyword.Bluemix_notm}} ダッシュボードまたは Cloud Foundry コマンド・ライン・インターフェース (CLI) からそれらのサービスを管理することができます。 パイプライン・ジョブでは、スクリプトで Cloud Foundry CLI コマンドを発行することもできます。 例えば、デプロイ・ジョブのスクリプトでアプリにサービスを追加することができます。 詳しくは、『[外部アプリへのサービスの接続](/docs/resources?topic=resources-externalapp)』を参照してください。

## ログの表示
{: #deliverypipeline_view_logs}

「ステージ履歴」ページでの実行中に、ジョブのログおよびステージを表示することができます。

1. ジョブのログを表示するには、ジョブをクリックします。 または、ステージで**「ログおよび履歴の表示」**をクリックします。

2. デプロイされているアプリケーションのランタイム・ログを表示するには、**「ランタイム・ログの表示」**をクリックします。

ジョブ・ログに加えて、ビルド・ジョブの単体テストの結果、生成された成果物、コードの変更も表示できます。

「ステージ履歴」ページからステージを実行、再デプロイ、取り消し、または構成することもできます。 ステージを実行するには**「実行」**を、デプロイメント・ジョブの場合に再デプロイを行うには**「再デプロイ」**を、ステージを構成するには**「構成」**をクリックします。 ステージの実行中に実行番号をクリックして**「キャンセル」**をクリックすることにより、そのステージをキャンセルできます。

### スクリプトからのログのダウンロード
{: #deliverypipeline_download_logs}

パイプライン・ジョブのログ・ファイルをスクリプトからダウンロードして、パイプライン・ジョブの実行中に提供される `PIPELINE_LOG_URL` を保存できます。 次の例は、パイプライン・ジョブのログ・ファイルを別のシステムにアップロードする手順を示しています。


1. ステージの `JOB_LOG` 環境プロパティーをセットアップします。

1. パイプライン・ジョブで、`PIPELINE_LOG_URL` を保存します。

   ```shell
   export JOB_LOG="$PIPELINE_LOG_URL"
   ```
1. 同じステージ内の後のジョブで `PIPELINE_LOG_URL` を使用してログ・ファイルをダウンロードし、それを別のシステムにエクスポートします。 IBM Cloud ベアラー・トークンを使用して、ログ・ファイルにアクセスします。

   ```shell
   ibmcloud login -a cloud.ibm.com \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   curl -H "Authorization: Bearer $BEARER"  \
     -H "Accept: text/plain" \
     -D /tmp/headers.txt \
     -o job_log.txt \
     "$JOB_LOG"
   ```
1. `X-More-Data` ヘッダーを確認します。 ヘッダーが `true` に設定されている場合、ログ・ファイルは生成中または処理中です。 ヘッダーが `false` に設定されている場合、ログ・ファイルはすぐに使用できます。

   ```shell
   grep X-More-Data /tmp/headers.txt
   X-More-Data: false
   ```
1. ログ・ファイルをシステムにアップロードします。

   ```shell
   scp job_log.txt user@example.org:/job1/logs
   ```


### スクリプトからの成果物のダウンロード
{: #deliverypipeline_download_artifacts}

パイプライン・ビルド・ジョブの成果物をスクリプトからダウンロードして、パイプライン・ジョブの実行中に提供される `PIPELINE_ARTIFACT_URL` を保存できます。 次の例は、パイプライン・ジョブの成果物を別のシステムにアップロードする手順を示しています。


1. ステージの `JOB_ARTIFACT` 環境プロパティーをセットアップします。

1. パイプライン・ジョブで、`PIPELINE_ARTIFACT_URL` を保存します。

   ```shell
   export JOB_ARTIFACT="$PIPELINE_ARTIFACT_URL"
   ```
   
1. 同じステージ内の後のジョブで `PIPELINE_ARTIFACT_URL` を使用して成果物をダウンロードし、それを別のシステムにエクスポートします。 IBM Cloud ベアラー・トークンを使用して、成果物にアクセスします。

   ```shell
   ibmcloud login -a cloud.ibm.com \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   DOWNLOAD_URL=$( curl -H "Authorization: Bearer $BEARER"  \
     "$JOB_ARTIFACT" )

   curl -O  "$DOWNLOAD_URL"
   ```
   
1. 成果物をシステムにアップロードします。

   ```shell
   scp $(basename "$DOWNLOAD_URL") user@example.org:/job1/artifacts
   ```
