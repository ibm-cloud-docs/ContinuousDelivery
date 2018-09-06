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

# Estensione di Delivery Pipeline
{: #deliverypipeline_extending}

Puoi estendere le funzionalità {{site.data.keyword.deliverypipeline}} di {{site.data.keyword.contdelivery_full}} configurando i tuoi lavori per l'utilizzo dei servizi supportati. Ad esempio, i lavori di verifica possono eseguire delle scansioni di codice statico e i lavori di creazione possono globalizzare le stringhe.
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

Le seguenti attività descrivono come integrare gli strumenti selezionati con un Delivery Pipeline.

## Esecuzione delle scansioni di codice statico utilizzando la pipeline

{: #deliverypipeline_scan}

Desideri ricercare i problemi di sicurezza nel tuo codice prima di distribuirlo? Quando utilizzi {{site.data.keyword.staticanalyzerfull}} come parte della tua pipeline, puoi eseguire dei controlli automatizzati nei file binari di creazione `.war`, `.ear`, `.jar` o `.class` statici della tua applicazione Java™.

Una pipeline che utilizza il servizio {{site.data.keyword.staticanalyzershort}} normalmente include tre fasi:

+ Una fase di build per generare i file di origine
+ Una fase di elaborazione che include tali lavori:
  + Un lavoro di creazione per eseguire il servizio Static Analyzer
  + Un lavoro di creazione per eseguire la creazione del contenitore
+ Una fase di distribuzione per distribuire il contenitore


### Creazione di una scansione di codice statico

Prima di iniziare, [riesamina i Termini di utilizzo per il servizio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. Crea una fase di elaborazione.

  a. Fai clic su **ADD STAGE**.

  b. Fornisce un nome per la fase, ad esempio, `Processing`.

  c. Per il tipo di input, seleziona **Build Artifacts**.

  d. Per la fase e il lavoro, verifica i valori e aggiornali se necessario.

2. Nella fase di elaborazione, aggiungi un lavoro di creazione per eseguire la scansione del codice.

  a. Nella scheda **JOBS**, fai clic su **ADD JOB**.

  b. Per il tipo di lavoro, seleziona **Test**.

  c. Per il tipo di tester, seleziona **IBM Security Static Analyzer**.

  d. Per l'organizzazione e lo spazio, verifica i valori e aggiornali se necessario.

  e. Seleziona o deseleziona la casella di spunta **Set up service and space for me** come necessario.

    * Se vuoi che la tua pipeline controlli il tuo spazio {{site.data.keyword.Bluemix_short}} per trovare il servizio e un'applicazione che associ il servizio al contenitore, seleziona la casella di spunta. Se il servizio o l'applicazione associata non esistono, la pipeline aggiunge il piano gratuito del servizio al tuo spazio. L'applicazione associata che viene creata è denominata `pipeline_bridge_app`. Quindi, la pipeline utilizza le credenziali da pipeline_bridge_app per accedere ai servizi associati.

    * Se hai già configurato il servizio e associato l'applicazione nel tuo spazio {{site.data.keyword.Bluemix_short}} o se vuoi [configurare questi requisiti manualmente](/docs/containers/container_integrations.html#container_binding_pipeline){: new_window}, lascia deselezionata la casella di spunta.

  f. Nel campo **Minuti di attesa per il completamento dell'analisi**, immetti un valore compreso tra 0 e 59 minuti. Il valore predefinito è 5 minuti. Un URL al dashboard {{site.data.keyword.staticanalyzershort}} è presente nei log della console alla fine del lavoro.

     Se la scansione di {{site.data.keyword.staticanalyzershort}} non viene completata entro il tempo specificato, il lavoro ha esito negativo. Tuttavia, l'analisi della scansione continua ad essere eseguita e puoi visualizzarla nel dashboard di {{site.data.keyword.staticanalyzershort}}. Dopo che la scansione di {{site.data.keyword.staticanalyzershort}} è stata completata, se riesegui il lavoro, la richiesta di scansione non viene reinviata e il lavoro della pipeline può essere completato. In alternativa, puoi configurare la pipeline in modo da non venir bloccata da un risultato della scansione positivo. Per le istruzioni, consulta la seguente fase.

  g. Seleziona o deseleziona la casella di spunta **Arrestare l'esecuzione di questa fase se il lavoro non riesce** a seconda di cosa desideri succeda se il lavoro non riesce o va in timeout. I lavori possono avere esito negativo quando le vulnerabilità sono elevate.

    * Se selezioni la casella di spunta e il lavoro ha esito negativo, i successivi lavori nella fase e le successive fasi non saranno eseguiti.

    * Se deselezioni la casella di spunta e il lavoro ha esito negativo, la fase continua senza bloccare i successivi lavori e fasi. Ad esempio, se sai che il report include molti problemi di elaborazione, puoi configurare la fase in modo che continui perché la scansione può durare a lungo. In questo scenario, potresti non voler arrestare il resto dei tuoi lavori e fasi solo perché la scansione impiega troppo tempo.

  h. Fai clic su **SAVE**.

3. Quando il lavoro termina, visualizza i risultati facendo clic su **View logs and history**. Se l'analisi ha esito positivo o va in timeout, viene visualizzato un URL nei risultati della scansione. Se lo stato della scansione è in attesa, attendi finché la scansione finisca per visualizzare i risultati completi.

4. Se hai bisogno di eseguire nuovamente la fase di elaborazione prima che termini l'analisi, puoi farlo. Tuttavia, nelle seguenti situazioni, non viene reinviata una nuova analisi e vengono utilizzati i precedenti risultati:
  * La fase di elaborazione è ancora in esecuzione quando hai avviato la nuova analisi
  * Una scansione è già stata inviata per la build
  * Non è ancora stata eseguita una nuova creazione dell'origine

5. Per avviare una nuova analisi, completa una delle seguenti fasi:
  * Esegui la fase di build che si inserisce nella fase di elaborazione e quindi esegui nuovamente la fase di elaborazione.
  * Apri l'URL per i risultati della scansione e fai clic sull'icona **Cestino**. Quindi, esegui nuovamente la fase di elaborazione.

Esempi di output della console:

**Scansione con esito positivo**
![Esempio di scansione con esito positivo](images/analyzer_success.png)

**Scansione in attesa**
![Esempio di scansione in attesa](images/analyzer_pending.png)

Per ulteriori informazioni sull'utilizzo del servizio {{site.data.keyword.staticanalyzershort}}, consulta la [documentazione del servizio {{site.data.keyword.staticanalyzershort}}](/docs/services/ApplicationSecurityonCloud/index.html){: new_window}.

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
