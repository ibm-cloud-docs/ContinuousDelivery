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

# Ampliación de Delivery Pipeline
{: #deliverypipeline_extending}

Puede ampliar la capacidad de {{site.data.keyword.deliverypipeline}} de {{site.data.keyword.contdelivery_full}} configurando los trabajos para utilizar servicios soportados. Por ejemplo, los trabajos de prueba pueden ejecutar exploraciones de código estáticas y los trabajos de compilación pueden globalizar series.
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

Las tareas siguientes describen cómo integrar herramientas seleccionadas con un Delivery Pipeline.

## Ejecución de exploraciones de código estático utilizando el conducto

{: #deliverypipeline_scan}

¿Desea encontrar problemas de seguridad en el código antes de desplegarlo? Cuando utilice {{site.data.keyword.staticanalyzerfull}} como parte del conducto, puede ejecutar comprobaciones automatizadas en los archivos binarios de compilación `.war`, `.ear`, `.jar`, o `.class` estáticos de la app Java™.

Un conducto que utiliza el servicio de {{site.data.keyword.staticanalyzershort}} normalmente incluye estas etapas:

+ Una etapa de compilación para crear los archivos de origen
+ Una etapa de procesamiento que incluye estos trabajos:
  + Un trabajo de compilación para ejecutar el servicio de Static Analyzer
  + Un trabajo de compilación para ejecutar una compilación del contenedor
+ Una etapa de despliegue para desplegar el contenedor


### Creación de una exploración de código estático

Antes de empezar, [revise las Condiciones de uso para el servicio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. Cree una etapa de proceso.

  a. Pulse **AÑADIR ETAPA**.

  b. Ponga un nombre a la etapa, por ejemplo, `Procesando`.

  c. Para el tipo de entrada, seleccione **Artefactos de compilación**.

  d. Para la etapa y el trabajo, verifique los valores y actualícelos si es necesario.

2. En la etapa de proceso, añada un trabajo de compilación para ejecutar la exploración del código.

  a. En el separador **TRABAJOS**, pulse **AÑADIR TRABAJO**.

  b. Para el tipo de trabajo, seleccione la **Prueba**.

  c. Para el tipo de prueba, seleccione **IBM Security Static Analyzer**.

  d. Para la organización y el espacio, verifique los valores y actualícelos si es necesario.

  e. Seleccione o quite la marca del recuadro de selección **Configurar servicio y espacio automáticamente** según sea necesario.

    * Si desea que el conducto compruebe el espacio de {{site.data.keyword.Bluemix_short}} para el servicio y una app que enlaza el servicio al contenedor, marque el recuadro de selección. Si el servicio o la app enlazada no existen, el conducto añadirá el plan gratuito del servicio a su espacio. La app enlazada que se crea se denomina `pipeline_bridge_app`. A continuación, el conducto utilizará las credenciales de pipeline_bridge_app para acceder a los servicios enlazados.

    * Si ya ha configurado el servicio y ha enlazado la app en el espacio de {{site.data.keyword.Bluemix_short}}, o si desea configurar estos requisitos manualmente, deje el recuadro de selección sin marcar.

  f. En el campo **Minutos que se debe esperar para que el análisis se complete**, escriba un valor de 0 a 59 minutos. El valor predeterminado es 5 minutos. Un URL al panel de control de {{site.data.keyword.staticanalyzershort}} se encuentra en los registros de consola al final del trabajo.

     Si la exploración de {{site.data.keyword.staticanalyzershort}} no se ha completado antes del tiempo especificado, el trabajo fallará. Sin embargo, el análisis de la exploración continuará ejecutándose y puede verlo en el panel de control de {{site.data.keyword.staticanalyzershort}}. Una vez que se ha completado la exploración de {{site.data.keyword.staticanalyzershort}}, si vuelve a ejecutar el trabajo, la solicitud de exploración no se vuelve a enviar y el trabajo del conducto se puede completar. Como alternativa, puede configurar el conducto para no bloquearse en un resultado de exploraciones correctamente. Para obtener instrucciones, consulte el paso siguiente.

  g. Marque o quite la marca del recuadro de selección **Dejar de ejecutar esta etapa si el trabajo falla** en función de lo que desee que suceda si este trabajo falla o se excede el tiempo de espera. Los trabajos pueden fallar cuando las vulnerabilidades son altas.

    * Si marca el recuadro de selección y el trabajo falla, no se ejecutarán los trabajos posteriores de la etapa ni las etapas posteriores.

    * Si desmarca el recuadro de selección y el trabajo falla, la etapa continúa sin bloquear trabajos ni etapas posteriores. Por ejemplo, si sabe que el informe incluye muchos problemas para procesar, puede configurar la etapa para continuar porque la exploración puede tardar mucho tiempo. En este caso de ejemplo, es posible que no desee
que se detenga el resto de los trabajos y etapas sólo porque la exploración está tardando
demasiado tiempo.

  h. Pulse **GUARDAR**.

3. Cuando el trabajo finaliza, vea los resultados pulsando **Ver registros e historial**. Si el análisis se lleva a cabo correctamente o se excede el tiempo de espera, se mostrará un URL en los resultados de la exploración. Si el estado de la exploración es pendiente, espere hasta que se haya completado la exploración para ver los resultados completos.

4. Si tiene que ejecutar la etapa de proceso de nuevo antes de que finalice el análisis, puede hacerlo. Sin embargo, en las siguientes situaciones, no se volverá a enviar un nuevo análisis y se utilizarán los resultados anteriores:
  * La etapa de proceso todavía se estaba ejecutando cuando se ha iniciado un análisis nuevo
  * Ya se ha enviado una exploración para la compilación
  * Aún no se ha ejecutado una nueva compilación de origen

5. Para iniciar un análisis nuevo, complete uno de estos pasos:
  * Ejecute la etapa de compilación que entra en la etapa de proceso y, a continuación, ejecute la etapa de proceso de nuevo.
  * Abra el URL para los resultados de la exploración y pulse el icono **Papelera**. A continuación, ejecute la etapa de proceso de nuevo.

Ejemplos de salida de la consola:

**Exploración satisfactoria**
![Exploración satisfactoria de ejemplo](images/analyzer_success.png)

**Exploración pendiente**
![Exploración pendiente de ejemplo](images/analyzer_pending.png)

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
