---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-26"

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

# 延伸 Delivery Pipeline
{: #deliverypipeline_extending}

您可以配置工作使用支援的服務，來延伸 {{site.data.keyword.contdelivery_full}} 的 {{site.data.keyword.deliverypipeline}} 功能。例如，測試工作可以執行靜態程式碼掃描，建置工作則可以將字串進行全球化。
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

下列作業說明如何使用 Delivery Pipeline 來整合選取的工具。

## 使用管線執行靜態程式碼掃描

{: #deliverypipeline_scan}

要在部署程式碼之前找出其中的安全問題嗎？如果您將 {{site.data.keyword.staticanalyzerfull}} 當成管線的一部分來使用，則可以針對 Java™ 應用程式的靜態 `.war`、`.ear`、`.jar` 或 `.class` 建置二進位檔來執行自動化檢查。

使用 {{site.data.keyword.staticanalyzershort}} 服務的管線通常包括下列階段：

+ 用來建置原始檔的建置階段
+ 包含下列工作的處理階段：
  + 用來執行 Static Analyzer 服務的建置工作
  + 用來執行容器建置的建置工作
+ 用來部署容器的部署階段


### 建立靜態程式碼掃描

開始之前，請[檢閱服務的使用條款 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. 建立處理階段。

  a. 按一下**新增階段**。

  b. 將階段命名（例如，`Processing`）。

  c. 針對輸入類型，選取**建置構件**。

  d. 針對階段及工作，驗證值並在必要時予以更新。

2. 在處理階段中，新增建置工作來執行程式碼掃描。

  a. 在**工作**標籤上，按一下**新增工作**。

  b. 針對工作類型，選取**測試**。

  c. 針對測試器類型，選取 **IBM Security Static Analyzer**。

  d. 針對組織及空間，驗證值並在必要時予以更新。

  e. 視需要，選取或清除**為我設定服務及空間**勾選框。

    * 如果您要管線檢查 {{site.data.keyword.Bluemix_short}} 空間來尋找服務以及將服務連結至容器的應用程式，請選取此勾選框。如果服務或所連結的應用程式不存在，則管線會將服務的免費方案新增至您的空間。建立的已連結應用程式命名為 `pipeline_bridge_app`。然後，管線會使用來自 pipeline_bridge_app 的認證，以存取連結的服務。

    * 如果您已在 {{site.data.keyword.Bluemix_short}} 空間中配置服務及連結的應用程式，或者要[手動配置這些需求](/docs/containers/container_integrations.html#container_binding_pipeline){: new_window}，請清除此勾選框。

  f. 在**等待分析完成的分鐘數**欄位中，鍵入 0 - 59 分鐘的值。預設值為 5 分鐘。在工作結束時，{{site.data.keyword.staticanalyzershort}} 儀表板的 URL 是在主控台日誌中。

     如果 {{site.data.keyword.staticanalyzershort}} 掃描未在指定的時間之前完成，則工作會失敗。不過，掃描分析會繼續執行，而且您可以在 {{site.data.keyword.staticanalyzershort}} 儀表板上進行檢視。{{site.data.keyword.staticanalyzershort}} 掃描完成之後，如果您重新執行工作，則不會重新提交掃描要求，而且可以完成管線工作。您也可以配置在掃描結果成功時不封鎖管線。如需指示，請參閱下一步。

  g. 視您想要在此工作失敗或逾時採取何種作法而定，選取或清除**如果此工作失敗，停止執行此階段**勾選框。漏洞數太高時，工作會失敗。

    * 如果您選取此勾選框，而且工作失敗，則階段中的後續工作以及後續階段不會執行。

    * 如果您清除此勾選框，而且工作失敗，則階段會繼續執行，而不封鎖後續的工作及階段。例如，如果您知道報告包含許多要處理的問題，則可以配置階段繼續執行，因為掃描可能需要很長的時間。在此情況下，您可能不希望剩餘的工作及階段只因為掃描花費太長的時間而停止。

  h. 按一下**儲存**。

3. 工作完成時，請按一下**檢視日誌及歷程**來檢視結果。如果分析成功或逾時，則會在掃描結果中顯示 URL。如果掃描狀態為擱置中，請等待掃描完成，以查看完整結果。

4. 如果您需要在分析完成之前再次執行處理階段，您可以重新執行。不過，在下列情況下，不會重新提交新的分析，而會使用先前的結果：
  * 當您啟動新的分析時，處理階段仍在執行中
  * 已提交針對建置的掃描
  * 尚未執行新的原始檔建置

5. 若要開始新的分析，請完成下列其中一個步驟：
  * 執行輸入至處理階段的建置階段，然後重新執行處理階段。
  * 開啟掃描結果的 URL，然後按一下**垃圾**圖示。然後，重新執行處理階段。

主控台輸出範例：

**成功掃描**
![範例成功掃描](images/analyzer_success.png)

**擱置掃描**
![範例擱置掃描](images/analyzer_pending.png)

如需使用 {{site.data.keyword.staticanalyzershort}} 服務的相關資訊，請參閱 [{{site.data.keyword.staticanalyzershort}} 服務文件](/docs/services/ApplicationSecurityonCloud/index.html){: new_window}。

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
