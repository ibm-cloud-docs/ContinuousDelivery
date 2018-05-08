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

# 扩展 Delivery Pipeline
{: #deliverypipeline_extending}

通过配置作业使用受支持的服务，您可以扩展 {{site.data.keyword.contdelivery_full}} 的 {{site.data.keyword.deliverypipeline}} 功能。例如，测试作业可以运行静态代码扫描，而构建作业可以将字符串全球化。
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

以下任务描述如何将所选工具与 Delivery Pipeline 相集成。

## 使用管道运行静态代码扫描

{: #deliverypipeline_scan}

想要在部署代码之前发现代码中的安全问题？使用 {{site.data.keyword.staticanalyzerfull}} 作为管道的一部分时，可针对 Java™ 应用程序的静态 `.war`、`.ear`、`.jar` 或 `.class` 构建二进制文件运行自动检查。

使用 {{site.data.keyword.staticanalyzershort}} 服务的管道通常包括以下阶段：

+ 构建阶段，用于构建源文件
+ 处理阶段，包括以下作业：
  + 用于运行 Static Analyzer 服务的构建作业
  + 用于运行容器构建的构建作业
+ 部署阶段，用于部署容器


### 创建静态代码扫描

开始之前，请[查看服务的使用条款 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. 创建处理阶段。

  a. 单击**添加阶段**。

  b. 为该阶段命名，例如 `Processing`。

  c. 对于输入类型，选择**构建工件**。

  d. 对于阶段和作业，验证值并视需要更新值。

2. 在处理阶段中，添加构建作业以运行代码扫描。

  a. 在**作业**选项卡上，单击**添加作业**。

  b. 对于作业类型，选择**测试**。

  c. 对于测试程序类型，选择 **IBM Security Static Analyzer**。

  d. 对于组织和空间，验证值并视需要更新值。

  e. 根据需要，选中或清除**为我设置服务和空间**复选框。

    * 如果要让管道检查 {{site.data.keyword.Bluemix_short}} 空间中是否有该服务以及将该服务绑定到容器的应用程序，请选中此复选框。如果不存在该服务或绑定的应用程序，那么管道会将该服务的免费套餐添加到空间。所创建的绑定应用程序名为 `pipeline_bridge_app`。之后，管道会使用 pipeline_bridge_app 中的凭证来访问绑定的服务。

    * 如果您已在 {{site.data.keyword.Bluemix_short}} 空间中配置该服务和绑定的应用程序，或者如果您想要[手动配置这些需求](/docs/containers/container_integrations.html#container_binding_pipeline){: new_window}，请使该复选框保留清除状态。

  f. 在**等待分析完成的时间（分钟）**字段中，输入 0 到 59 分钟之间的值。缺省值为 5 分钟。作业结束时 {{site.data.keyword.staticanalyzershort}} 仪表板的 URL 会显示在控制台日志中。

     如果您指定的时间到期时 {{site.data.keyword.staticanalyzershort}} 扫描未完成，那么作业会失败。但是，扫描分析会继续运行，而您可以在 {{site.data.keyword.staticanalyzershort}} 仪表板上查看分析。在 {{site.data.keyword.staticanalyzershort}} 扫描完成后，如果重新运行该作业，就不会重新提交扫描请求，而管道作业可以完成。或者，也可以配置为扫描结果成功时不阻塞管道。有关指示信息，请参阅下一步。

  g. 根据在此作业失败或超时的情况下您希望执行什么操作，选中或清除**此作业失败时停止运行此阶段**复选框。当漏洞较大时，作业可能会失败。

    * 如果您选中该复选框而作业失败，那么该阶段中的后续作业和后续阶段不会运行。

    * 如果您清除该复选框而作业失败，那么该阶段会继续而不会阻止后续作业和阶段。例如，如果您知道该报告包含许多要处理的问题，那么您可能会设置该阶段继续运行，因为扫描可能会花很长时间。在此情况下，您可能不希望仅仅因为扫描需要花很长时间而停止剩余的作业和阶段。

  h. 单击**保存**。

3. 作业完成时，单击**查看日志和历史记录**，以查看结果。如果分析成功或超时，那么会在扫描结果中显示 URL。如果扫描状态为暂挂，请等待直到扫描完成，以查看完整结果。

4. 如果在分析完成之前需要重新运行处理阶段，那么您可以这样做。但是，在以下情况下，不会重新提交新分析而会使用之前的结果：
  * 当您启动新分析时，处理阶段仍在运行。
  * 已经提交构建的扫描
  * 新源构建尚未运行

5. 要启动新分析，请完成以下某个步骤：
  * 运行输入到处理阶段的构建阶段，然后重新运行处理阶段。
  * 打开扫描结果的 URL 并单击**废纸篓**图标。然后，重新运行处理阶段。

控制台输出示例：

**成功扫描**
![成功扫描示例](images/analyzer_success.png)

**暂挂扫描**
![暂挂扫描示例](images/analyzer_pending.png)

有关使用 {{site.data.keyword.staticanalyzershort}} 服务的更多信息，请参阅 [{{site.data.keyword.staticanalyzershort}}Static Analyzer 服务文档](/docs/services/ApplicationSecurityonCloud/index.html){: new_window}。

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
