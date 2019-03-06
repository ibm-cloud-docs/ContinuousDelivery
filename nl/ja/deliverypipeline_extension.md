---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-5"

---

<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Delivery Pipeline の拡張
{: #deliverypipeline_extending}

サポートされるサービスを使用するようにジョブを構成することで、{{site.data.keyword.contdelivery_full}} の {{site.data.keyword.deliverypipeline}} の機能を拡張できます。 例えば、テスト・ジョブで静的コード・スキャンを実行し、ビルド・ジョブで文字列をグローバル化できます。
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

次のタスクは、選択されたツールを Delivery Pipeline と統合する方法を説明します。

## パイプラインを使用した静的コード・スキャンの実行

{: #deliverypipeline_scan}

コードをデプロイする前にコードのセキュリティー問題を検索したい場合、 {{site.data.keyword.staticanalyzerfull}} をパイプラインの一部として使用すると、Java™ アプリの静的 `.war`、`.ear`、`.jar`、または `.class` ビルド・バイナリー・ファイルに対して自動化チェックを実行できます。

{{site.data.keyword.staticanalyzershort}} サービスを使用するパイプラインは、通常以下のステージを含みます。

+ ソース・ファイルをビルドするためのビルド・ステージ
+ 以下のジョブを含む処理ステージ
  + Static Analyzer サービスを実行するためのビルド・ジョブ
  + コンテナー・ビルドを実行するビルド・ジョブ
+ コンテナーをデプロイするためのデプロイ・ステージ


### 静的コード・スキャンの作成

開始する前に、[サービスのご利用条件を確認します![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}。

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. 処理ステージを作成します。

  a. **「ステージの追加」**をクリックします。

  b. ステージに`「処理」`などの名前を付けます。

  c. 入力タイプに**「ビルド成果物」**を選択します。

  d. ステージとジョブの値を確認し、必要であれば値を更新します。

2. この処理ステージに、コード・スキャンを実行するためのビルド・ジョブを追加します。

  a. **「ジョブ」**タブで、**「ジョブの追加 (ADD JOB)」**をクリックします。

  b. ジョブ・タイプに**「テスト」**を選択します。

  c. テスター・タイプに**「IBM Security Static Analyzer」**を選択します。

  d. 組織とスペースの値を確認し、必要であれば値を更新します。

  e. 必要に応じて**「サービスとスペースの自動セットアップ」**チェック・ボックスを選択またはクリアします。

    * サービス用の {{site.data.keyword.Bluemix_short}} のスペースと、サービスをコンテナーにバインドするアプリを、パイプラインで確認する場合は、このチェック・ボックスを選択します。 サービスやバインドされたアプリが存在しない場合、パイプラインによって、このサービスの無料プランがご使用のスペースに追加されます。 作成されたバインド済みアプリには、`pipeline_bridge_app` という名前が付けられます。 その後、パイプラインは、pipeline_bridge_app からの資格情報を使用して、バインド済みサービスにアクセスします。

    * サービスとバインド済みアプリを {{site.data.keyword.Bluemix_short}} のスペースで構成してある場合、またはこれらの要件を手動で構成する場合は、このチェック・ボックスをクリアします。

  f. **「分析の完了を待機する時間」**フィールドで、0 から 59 分の値を入力します。 デフォルト値は 5 分です。 ジョブ終了時、{{site.data.keyword.staticanalyzershort}} ダッシュボードの URL がコンソール・ログに記録されます。

     {{site.data.keyword.staticanalyzershort}} のスキャンが指定した時間までに終了しない場合は、ジョブは失敗します。 しかし、スキャンの分析は実行を続行し、{{site.data.keyword.staticanalyzershort}} ダッシュボードで表示することができます。 {{site.data.keyword.staticanalyzershort}} スキャンの完了後に、ジョブを再実行した場合、スキャン要求は再実行依頼されず、パイプライン・ジョブは完了できます。 また、正常に終了したスキャン結果でパイプラインをブロックされないように構成することもできます。 手順については、次のステップを参照してください。

  g. このジョブが失敗またはタイムアウトになる場合の対応に応じて、**「このジョブが失敗したらこのステージの実行を停止する (Stop running this stage if this job fails)」**チェック・ボックスを選択またはクリアします。 脆弱性が高い場合、ジョブは失敗する可能性があります。

    * このチェック・ボックスを選択した状態でジョブが失敗した場合、このステージ内の後続のジョブと後続のステージは実行されません。

    * このチェック・ボックスをクリアした状態でジョブが失敗した場合、ステージは後続のジョブとステージをブロックせずに続行します。 例えば、処理すべき多くの問題がレポートに含まれていることが分かっている場合、スキャンには長時間かかる可能性があるため、続行するようにステージを構成するという選択肢もありえます。 こうしたシナリオでは、単にスキャンに時間がかかりすぎるという理由だけで残りのジョブとステージの実行を停止するのは避けたいと考えられます。

  h. **「保存」**をクリックします。

3. ジョブが終了したら、**「ログおよび履歴の表示」**をクリックして結果を表示します。 分析が成功またはタイムアウトになった場合、スキャン結果に URL が表示されます。 スキャン状況が処理中になっている場合は、スキャンが完了して全結果が表示されるまで待ちます。

4. 分析が終了する前に再度処理ステージの実行が必要な場合は、実行可能です。 しかし、次のような状況では、新しい分析は再実行依頼されず、前回の結果が使用されます。
  * 新しい分析を始めたときに処理ステージが実行中だった場合
  * ビルドのスキャンがすでに実行依頼されている場合
  * 新しいソース・ビルドがまだ実行されていない場合

5. 新しい分析を始動するには、次のいずれかの手順を実行します。
  * 処理ステージに入力するビルド・ステージを実行してから、処理ステージを再度実行します。
  * スキャン結果の URL を開き、**「ごみ箱」**アイコンをクリックします。 その後、処理ステージを再度実行します。

コンソール出力例:

**成功したスキャン**
![成功したスキャンの例](images/analyzer_success.png)

**保留中のスキャン**
![保留中のスキャンの例](images/analyzer_pending.png)

<!--

## Globalizing strings by using the pipeline
{: #deliverypipeline_globalize}

You can translate strings automatically into other languages when you use the IBM Globalization Pipeline service with your pipeline. IBM Globalization Pipeline uses machine translation to translate your source files as part of the pipeline's build and deployment process.

You can also update the machine-translated strings within the globalization project. A translator or native speaker of the language can then review the machine-translated strings to ensure that they are of a high quality.

To see an example of a typical pipeline that uses the Globalization Pipeline service, watch this video:

<iframe width="640" height="360" src="https://www.youtube.com/embed/UToj7FIomCg?feature=player_embedded" frameborder="0" allowfullscreen></iframe>

### Creating a globalization stage and job
Before you begin:

1. All English-translatable strings should be included in one or more `filename_en.properties` or `filename_en.json` files that all use the same name. For example: `messages_en.properties`.

2. If your messages are in `.json` files, remove the depth from the structure by removing any subkeys. To remove the subkeys, change instances of `{key: {subkey: value, subkey:value}}` to `{key:value, key:value}`.

To create the globalization stage and job:

1. Create a globalization stage.

  a. Click **ADD STAGE**.

  b. Name the stage; for example, `Globalization`.

  c. For the input type, select **SCM repository**.

2. In the globalization stage, add a job to translate the source files.

  a. On the **JOBS** tab, click **ADD JOB**.

  b. For the job type, select **Build**.

  c. For the builder type, select **IBM Globalization Pipeline**.

  d. For the organization and space, verify the values and update them if needed.

  e. In the **Source file name** field, type the name and extension of the `.properties` or `.json` input file. If you have files in different subdirectories, but they all have the same name, you need to type the file name once only. For example, if you have a `messages_en.properties` file in three directories, type `messages_en.properties` for the source file name, and all files with that name will be translated.

  f. Determine whether to select the **Set up service and space for me** check box.

    * If you want the pipeline to check your {{site.data.keyword.Bluemix_notm}} space for the service and an app that binds the service to the container, select this check box. If the service or bound app does not exist, the pipeline adds the free plan of the service to your space for you. The bound app that is created is named `pipeline_bridge_app`. Then, the pipeline uses the credentials from pipeline_bridge_app to access the bound services.

    * If you configured the service and bound app in your {{site.data.keyword.Bluemix_notm}} space already or if you want to [configure these requirements manually](/docs/containers/container_integrations.html#container_binding_pipeline), leave this check box cleared.

  g. For the Globalization bundle prefix, enter a prefix for the bundle name, which is structured in this format: `<globalization_bundle_prefix>.path.to.source.file`. The pipeline job creates this Globalization bundle for you in the Globalization Pipeline service.


    **Tip:** Use the DevOps Services project name in the prefix so that the project can be identified easily in the Globalization Pipeline service.


  h. Click **SAVE**.

3. Create another stage to package your app. For the input of the job in this stage, use the IBM Globalization Pipeline job from the previous stage. Do not use the source as the input. The Globalization Pipeline job augments the source files with the machine-translated strings.

4. To ensure that the machine-translated content is included in the packaged app, create another stage to package the app in. For the input to that stage, include the Globalization Pipeline job.

The machine translated files are placed in the same directory as the source `.properties` or `.json` file. To view the files, click **Job > Artifacts**.

After the stage is completed, you can review the translated files from the console output. You can also direct translators to the files so that they can review the machine-translation output and provide revisions to improve quality. The revisions are stored in a Cloudant™ database and take precedence over any future machine translations of the same strings.

For more information about using the Globalization Pipeline service from the {{site.data.keyword.Bluemix_notm}} Dashboard, [see the Globalization Pipeline service documentation](https://www.ng.bluemix.net/docs/services/GlobalizationPipeline/index.html).

-->
<!--

## Creating Slack notifications for builds in the pipeline
{: #deliverypipeline_slack}

You can send notifications about {{site.data.keyword.containerlong}}, {{site.data.keyword.staticanalyzershort}}, and {{site.data.keyword.globalizationfull}} build results from your Delivery Pipeline to your Slack channels.

Before you begin, create or copy a Slack WebHook URL:

1. Open the Slack Integration page for your team: `https://_project_name_.slack.com/services`
2. In the list of integrations, locate **Incoming WebHooks** and click **Add**.
3. Select a channel and click **Add Incoming WebHooks Integration**.
4. Add a **WebHook URL** or copy an existing one.

For more information, see [Incoming WebHooks in the Slack documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://api.slack.com/incoming-webhooks){: new_window}.

To create Slack notifications:

1. In the pipeline, open the configuration for a stage.
2. In the **ENVIRONMENT PROPERTIES** tab, click **ADD PROPERTY**.
3. Select **Text property**.
4. Enter the name and a value for the environment property. Repeat to create multiple environment properties.

  _Table 1. Environment properties for configuring Slack notifications_

  <table>
  <tr>
  <th>Name</th>
  <th>Value</th>
  <th>Description</th>
  <tr/>
  <tr>
    <td><code>SLACK_WEBHOOK_PATH</code></td>
    <td>A URL</td>
    <td>Required. The WebHook URL that is saved in the settings for your Slack Project.</td>
  </tr>
  <tr>
    <td><code>SLACK_COLOR</code></td>
    <td>You can enter one of the following values:
      <ul><li><code>good</code></li>
      <li><code>warning</code></li>
      <li><code>danger</code></li>
      <li>Any hexadecimal color, such as #439FEO</li></ul></td>
    <td>Optional. The color of the border that is displayed along the side of the message in Slack. The default colors are green for good messages, red for bad messages, and gray for informational messages.</td>
  </tr>
  <tr>
    <td><code>NOTIFY_FILTER</code></td>
    <td>To receive only a subset of the message types, enter one of the following values:
      <ul>
      <li><code>good</code>: Get unknown, good and info messages only. Bad messages are not sent.</li>
      <li><code>bad</code>: Get all messages.</li>
      <li><code>info</code>: Get info messages only. Good, bad, and unknown messages are not sent.</li>
      <li><code>unknown</code>: Get all messages.</li></ul>
      Example: If you set <code>NOTIFY_FILTER = bad</code>, error notifications are only displayed in the Slack Channel.</td>
    <td>Optional. Decide which type of messages to send notifications for. By default, good and bad messages are sent, but not informational messages.
      <ul><li><code>good</code>: Successful build results.</li>
      <li><code>bad</code>: Unsuccessful build results.</li>
      <li><code>info</code>: Informational messages about the build process.</li>
      <li><code>unknown</code>: Unknown messages are not assigned a type.</li></ul></td>
   </table>

5. Click **Save**.

6. Repeat these steps to send Slack notifications for other stages that include IBM Container Service, IBM Security Analyzer, and IBM Globalization jobs.

The build notification that is displayed in Slack includes a link to the project and sometimes to the project's dashboard. For a Slack user to open these links, the user must be registered with {{site.data.keyword.Bluemix_notm}} and be a member of the organization that the pipeline is configured in.

## Creating HipChat notifications for builds in the pipeline
{: #deliverypipeline_hipchat}

You can send notifications about IBM Container Service, IBM Security Static Analyzer, and IBM Globalization build results from your Delivery Pipeline to your HipChat rooms.

Before you begin, create or copy and existing HipChat token:

1. Go to your HipChat Account page for your team: `https://_project_name_.hipchat.com/account/api`
2. Create a new token, or use an existing one.

To create HipChat notifications:

1. In the pipeline, open the configuration for a stage.
2. In the **ENVIRONMENT PROPERTIES** tab, click **ADD PROPERTY**.
3. Select **Text Property**.
4. Enter the name and a value for the environment property. Repeat to create multiple environment properties.

  _Table 2. Environment Properties for configuring HipChat notifications_

  <table>
  <tr>
  <th>Name</th>
  <th>Value</th>
  <th>Description</th>
  </tr>
  <tr>
    <td><code>HIP_CHAT_TOKEN</code></td>
    <td>Alphanumeric String</td>
    <td>Required. See "Before you begin" for instructions on creating or copying an existing HipChat token.</td>
  </tr>
  <tr>
    <td><code>HIP_CHAT_ROOM_NAME</code></td>
    <td>Room name</td>
    <td>Required.</td>
  </tr>
  <tr>
    <td><code>HIP_CHAT_COLOR</code></td>
    <td>Enter one of the following values:
      <ul><li><code>yellow</code></li>
      <li><code>red</code></li>
      <li><code>green</code></li>
      <li><code>purple</code></li>
      <li><code>gray</code></li>
      <li><code>random</code></li></ul>
    </td>
    <td>Optional: Specify the background color and the border color of HipChat notifications. If you set <code>HIP_CHAT_COLOR</code>, you do not need to specify the color when you call the script.
     <p><code>-l notification_level</code></p> </td>
  </tr>
  <tr>
    <td><code>NOTIFICATION_COLOR</code></td>
    <td>Enter one of the following values:
      <ul><li><code>good</code></li>
      <li><code>danger</code></li>
      <li><code>info</code></li></ul>
    This variable applies to both HipChat and Clack notification colors. If you specify <code>NOTIFICATION_COLOR</code>, you do not need to specify <code>HIP_CHAT_COLOR</code> or <code>SLACK_COLOR</code>.</td>
    <td>Optional: Specify the background color and the border color of both HipChat and Slack notifications. If you set <code>NOTIFICATION_COLOR</code>, you do not need to specify the color when you call the script.
     <p><code>-l notification_level</code></p> </td>
  </tr>
  <tr>
    <td><code>NOTIFICATION_LEVEL</code></td>
    <td>Enter one of the following values:
      <ul><li><code>good</code></li>
      <li><code>info</code></li>
      <li><code>bad</code></li></ul></td>
    <td>Optional: Specify the notification level. See <code>NOTIFICATION_FILTER</code> for more detail on what triggers the notification.</td>
  </tr>
  <tr>
    <td><code>NOTIFICATION_FILTER</code></td>
    <td>Enter one of the following values:
      <ul><li><code>good</code></li>
      <li><code>info</code></li>
      <li><code>bad</code></li></ul>
    <td>Optional: Specify the notification filter level. Notifications are sent when the following parameters are met:
      <ul><li><code>NOTIFICATION_FILTER = good</code> and <code>NOTIFICATION_LEVEL = bad</code>, <code>good</code>, or <code>unknown</code></li>
      <li><code>NOTIFICATION_FILTER = info</code> and <code>NOTIFICATION_LEVEL = bad</code>, <code>good</code>, <code>info</code>, or <code>unknown</code></li>
      <li><code>NOTIFICATION_FILTER = bad</code> and <code>NOTIFICATION_LEVEL = bad</code> or <code>unknown</code></li>
      <li><code>NOTIFICATION_FILTER = unknown</code> and <code>NOTIFICATION_LEVEL = bad</code>, <code>good</code>, or <code>unknown</code></li></ul></td>
    </tr>
  </table>

5. Click **Save**.

6. Repeat these steps to send HipChat notifications for other stages that include IBM Container Service, IBM Security Static Analyzer, and IBM Globalization jobs.

-->
