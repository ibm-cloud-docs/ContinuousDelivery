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

# Delivery Pipeline erweitern
{: #deliverypipeline_extending}

Sie können die {{site.data.keyword.deliverypipeline}}-Funktionalität von {{site.data.keyword.contdelivery_full}} erweitern, indem Sie Ihre Jobs für die Verwendung unterstützter Services konfigurieren. Testjobs können zum Beispiel statische Codescans ausführen und Buildjobs können Zeichenfolgen globalisieren.
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

Die folgenden Tasks beschreiben, wie ausgewählte Tools in eine Delivery Pipeline integriert werden.

## Die Ausführung von statischen Codescans durch die Verwendung der Pipeline

{: #deliverypipeline_scan}

Sie möchten Sicherheitsprobleme in Ihrem Code finden, bevor Sie diesen bereitstellen? Wenn Sie {{site.data.keyword.staticanalyzerfull}} als Teil Ihrer Pipeline verwenden, können Sie automatisierte Abgleiche mit den statischen Binärdateien für den Build Ihrer Java™ App mit den Endungen `.war`, `.ear`, `.jar` oder `.class` durchführen.

Eine Pipeline, die den Service {{site.data.keyword.staticanalyzershort}} verwendet, umfasst die folgenden Stages:

+ Eine Stage für den Build der Quellendateien
+ Eine Stage für die Verarbeitung mit den folgenden Jobs:
  + Ein Buildjob für die Ausführung des Service Static Analyzer
  + Ein Buildjob für die Ausführung eines Container-Builds
+ Eine Stage für die Bereitstellung des Containers


### Einen statischen Codescan erstellen

Bevor Sie mit den nachfolgenden Schritten beginnen, lesen Sie zunächst die [Nutzungsbedingungen für den Service ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}.

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. Erstellen Sie eine Stage für die Verarbeitung.

  a. Klicken Sie auf **Stage hinzufügen**.

  b. Benennen Sie die Stage. Zum Beispiel: `Verarbeitung`.

  c. Wählen Sie für den Eingabetyp **Buildartefakte** aus.

  d. Überprüfen Sie die Werte für die Stage und den Job und aktualisieren Sie diese bei Bedarf.

2. Fügen Sie in der Stage für die Verarbeitung einen Buildjob hinzu, um den Codescan auszuführen.

  a. Klicken Sie auf der Registerkarte **Jobs** auf **Job hinzufügen**.

  b. Wählen Sie als Jobtyp **Test** aus.

  c. Wählen Sie als Testtyp **IBM Security Static Analyzer** aus.

  d. Überprüfen Sie die Werte für die Organisation und den Bereich und aktualisieren Sie diese bei Bedarf.

  e. Markieren Sie das Kontrollkästchen **Service und Bereich für mich einrichten** oder heben Sie die Markierung bei Bedarf auf.

    * Wenn Sie möchten, dass die Pipeline Ihren {{site.data.keyword.Bluemix_short}}-Bereich auf den Service und eine App überprüft, die den Service an den Container bindet, wählen Sie das Kontrollkästchen aus. Wenn der Service oder die gebundene App nicht vorhanden sind, fügt die Pipeline den freien Plan des Service zu Ihrem Bereich hinzu. Die gebundene App, die erstellt wird, hat den Namen `pipeline_bridge_app`. Anschließend verwendet die Pipeline die Berechtigungsnachweise von der Datei 'pipeline_bridge_app', um auf die gebundenen Services zuzugreifen.

    * Wenn Sie den Service und die gebundene App in Ihrem {{site.data.keyword.Bluemix_short}}-Bereich konfiguriert haben oder wenn Sie [diese Anforderungen manuell konfigurieren](/docs/containers/container_integrations.html#container_binding_pipeline){: new_window} möchten, heben Sie die Markierung für das Kontrollkästchen auf.

  f. Geben Sie im Feld **Anzahl der Minuten für die Durchführung der Analyse** einen Wert zwischen 0 und 59 Minuten ein. Der Standardwert beträgt 5 Minuten. Eine URL zu dem Dashboard von {{site.data.keyword.staticanalyzershort}} befindet sich in den Konsolenprotokollen am Ende des Jobs.

     Wenn der {{site.data.keyword.staticanalyzershort}}-Scan nicht vor dem von Ihnen angegebenen Zeitpunkt vollständig ist, schlägt der Job fehl. Die Scananalyse wird jedoch weiter ausgeführt und Sie können sie im Dashboard von {{site.data.keyword.staticanalyzershort}} anzeigen. Nachdem der {{site.data.keyword.staticanalyzershort}}-Scan abgeschlossen ist, wird die Scananforderung nicht wiederholt, wenn Sie den Job erneut ausführen, und der Pipeline-Job kann abgeschlossen werden. Sie können die Pipeline stattdessen auch so konfigurieren, dass sie bei einem erfolgreichen Scan nicht blockiert wird. Erläuterungen hierzu folgen beim nächsten Schritt.

  g. Wählen Sie das Kontrollkästchen **Ausführen dieser Stage beenden, wenn dieser Job fehlschlägt** abhängig davon aus bzw. ab, was passieren soll, wenn dieser Job fehlschlägt oder das Zeitlimit überschreitet. Jobs können fehlschlagen, wenn die Anfälligkeit hoch ist.

    * Wenn Sie dieses Kontrollkästchen auswählen und der Job fehlschlägt, werden nachfolgende Jobs in dieser Stage und in folgenden Stages nicht ausgeführt.

    * Wenn Sie das Kontrollkästchen abwählen und der Job fehlschlägt, wird die Stage fortgesetzt ohne nachfolgende Jobs oder Stages zu blockieren. Wenn Sie zum Beispiel wissen, dass der Bericht viele Sicherheitsprobleme enthält, die bearbeitet werden müssen, empfiehlt es sich, die Stage für eine Fortsetzung zu konfigurieren, da der Scan sehr zeitaufwändig sein kann. Bei diesem Szenario ist es möglicherweise ungünstig, wenn die übrigen Jobs und Stages nur beendet werden, weil der Scan zu viel Zeit beansprucht.

  h. Klicken Sie auf **Speichern**.

3. Wenn der Job fertig gestellt ist, überprüfen Sie die Ergebnisse, indem Sie auf **Protokolle und Verlauf anzeigen** klicken. Wenn die Analyse erfolgreich war oder das Zeitlimit überschreitet, wird in den Scanergebnissen eine URL angezeigt. Wenn der Scanstatus anstehend ist, warten Sie, bis der Scan abgeschlossen ist, um die vollständigen Ergebnisse anzuzeigen.

4. Wenn Sie die Stage für die Verarbeitung erneut ausführen müssen, bevor die Analyse abgeschlossen ist, können Sie das tun. In den folgenden Situationen wird eine neue Analyse jedoch nicht erneut übergeben und die vorherigen Ergebnisse werden verwendet:
  * Die Stage für die Verarbeitung wird noch immer ausgeführt, wenn Sie eine neue Analyse gestartet haben.
  * Ein Scan wurde bereits für den Build übergeben.
  * Ein neuer Quellenbuild wurde noch nicht ausgeführt.

5. Führen Sie einen der folgenden Schritte aus, um eine neue Analyse zu starten:
  * Führen Sie die Stage für den Build aus, die Eingaben für die verarbeitende Stage liefert, und führen Sie dann die Stage für die Verarbeitung erneut aus.
  * Öffnen Sie die URL für die Scanergebnisse und klicken Sie auf das Symbol **Papierkorb**. Führen Sie anschließend die Stage für die Verarbeitung erneut aus.

Beispiele für die Konsolenausgabe:

**Erfolgreicher Scan**
![Beispiel für erfolgreichen Scan](images/analyzer_success.png)

**Anstehender Scan**
![Beispiel für anstehenden Scan](images/analyzer_pending.png)

Weitere Informationen zur Verwendung des Service {{site.data.keyword.staticanalyzershort}} enthält die [Dokumentation zum Service {{site.data.keyword.staticanalyzershort}}](/docs/services/ApplicationSecurityonCloud/index.html){: new_window}.

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
