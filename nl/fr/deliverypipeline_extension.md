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

# Extension de Delivery Pipeline
{: #deliverypipeline_extending}

Vous pouvez étendre les capacités de la fonction {{site.data.keyword.deliverypipeline}} d'{{site.data.keyword.contdelivery_full}} en configurant vos travaux afin d'utiliser les services pris en charge. Par exemple, les travaux de test peuvent exécuter des analyses de code statique et les travaux de génération peuvent globaliser des chaînes.
{:shortdesc}

<!-- Include a sentence to briefly introduce the steps/subtopics. Example: -->

Les tâches suivantes expliquent comment intégrer des outils sélectionnés à un service Delivery Pipeline.

## Exécution d'analyses de code statique à l'aide du pipeline

{: #deliverypipeline_scan}

Vous souhaitez rechercher des problèmes de sécurité dans votre code avant de le déployer ? Lorsque vous utilisez {{site.data.keyword.staticanalyzerfull}} dans le cadre de votre pipeline, vous pouvez exécuter des vérifications automatisées sur les fichiers binaires de génération `.war`, `.ear`, `.jar` ou`.class` statique d'application Java.

Un pipeline qui utilise le service {{site.data.keyword.staticanalyzershort}} inclut généralement les étapes suivantes :

+ Une étape de génération permettant de créer les fichiers source
+ Une étape de traitement incluant les travaux suivants :
  + Un travail de génération permettant d'exécuter le service Static Analyzer
  + Un travail de génération exécutant une génération de conteneur
+ Une étape de déploiement permettant de déployer le conteneur


### Création d'une analyse de code statique

Avant de commencer, [consultez les
conditions d'utilisation du service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm-6814-01){: new_window}.

<!-- Use ordered list markup for the step section. Include code examples as needed. -->

1. Créez une étape de traitement.

  a. Cliquez sur **Ajouter une étape**.

  b. Donnez un nom à l'étape, par exemple, `Traitement en cours`.

  c. Pour le type d'entrée, sélectionnez **Artefacts de génération**.

  d. Pour l'étape et pour le travail, vérifiez les valeurs et mettez-les à jour si besoin.

2. Dans l'étape de traitement, ajoutez un travail de génération pour exécuter l'examen du code.

  a. Dans l'onglet **Travaux**, cliquez sur **Ajouter un travail**.

  b. Pour le type de travail, sélectionnez **Tester**.

  c. Pour le type de testeur, sélectionnez **IBM Security Static Analyzer**.

  d. Pour l'organisation et l'espace, vérifiez les valeurs et mettez-les à jour si besoin.

  e. Sélectionnez ou désélectionnez la case à cocher **Configurer un service et un espace pour moi** selon vos besoins.

    * Si vous souhaitez que le pipeline vérifie dans votre espace {{site.data.keyword.Bluemix_short}} l'existence du service et d'une application qui établit une liaison entre le service et le conteneur, sélectionnez la case à cocher. Si le service ou l'application liée n'existe pas, il est créé par le pipeline pour ajouter le forfait gratuit du service à votre espace. L'application liée est créée avec le nom `pipeline_bridge_app`. Ensuite, le pipeline utilise les données d'identification de pipeline_bridge_app pour accéder aux services liés.

    * Si vous avez déjà configuré le service et lié l'application dans votre espace {{site.data.keyword.Bluemix_short}}, ou si vous désirez
configurer manuellement ces exigences, ne cochez pas cette case.

  f. Dans la zone **Temps d'attente en minutes pour l'achèvement de l'analyse**, tapez une valeur comprise entre 0 et 59 minutes. La valeur par défaut est 5 minutes. Une URL vers le tableau de bord {{site.data.keyword.staticanalyzershort}} figure dans les journaux de console à la fin du travail.

     Si l'analyse {{site.data.keyword.staticanalyzershort}} n'est pas terminée avant l'heure que vous avez spécifiée, le travail échoue. Toutefois, l'analyse de l'examen continue de s'exécuter et vous pouvez l'afficher sur le tableau de bord {{site.data.keyword.staticanalyzershort}}. Une fois l'examen {{site.data.keyword.staticanalyzershort}} terminé, si vous relancez l'exécution du travail, la demande d'examen n'est pas soumise à nouveau et le travail de pipeline peut être effectué. Sinon, vous pouvez configurer le pipeline pour qu'il ne soit pas bloqué si l'analyse aboutit. Pour obtenir des instructions, voir l'étape suivante.

  g. Sélectionnez ou désélectionnez la case à cocher **Arrêter d'exécuter cette étape si ce travail échoue** selon ce qui doit se produire si ce travail échoue ou dépasse le délai d'attente prévu. Les travaux peuvent échouer lorsque les vulnérabilités sont élevées.

    * Si vous sélectionnez la case à cocher et que le travail échoue, les travaux ultérieurs dans l'étape et les étapes ultérieures ne s'exécutent pas.

    * Si vous désélectionnez la case à cocher et que le travail échoue, l'étape se poursuit sans bloquer les travaux et les étapes ultérieurs. Par exemple, si vous savez que le rapport inclut de nombreux problèmes à traiter, vous souhaiterez peut-être configurer la poursuite de l'étape car l'examen peut durer un certain temps. Dans ce cas, il n'est pas souhaitable que le reste de vos travaux et de vos étapes s'arrêtent uniquement parce que l'examen
dure trop longtemps.

  h. Cliquez sur **SAUVEGARDER**.

3. Lorsque le travail est terminé, affichez les résultats en cliquant sur **Afficher les journaux et l'historique
**. En cas de réussite ou de dépassement de délai de l'analyse, une URL apparaît dans les résultats de l'examen. Si l'examen est en attente, attendez qu'il se termine pour afficher tous les résultats.

4. Vous pouvez, si nécessaire, exécuter à nouveau l'étape de traitement avant la fin de l'analyse. Toutefois, dans les situations suivantes, une nouvelle analyse n'est pas soumise à nouveau et les résultats précédents sont utilisés :
  * L'étape de traitement était toujours en cours d'exécution lorsque vous avez démarré une nouvelle analyse.
  * Un examen était déjà soumis pour la génération.
  * Une nouvelle génération de source n'a pas encore été exécutée.

5. Pour démarrer une nouvelle analyse, exécutez l'une des étapes suivantes :
  * Exécutez l'étape de génération qui entre dans l'étape de traitement, puis relancez l'exécution de l'étape de traitement.
  * Ouvrez l'URL des résultats de l'examen, puis cliquez sur l'icône **Corbeille**. Ensuite, relancez l'étape de traitement.

Exemples de sortie dans la console :

**Examen réussi**
![Exemple d'examen réussi](images/analyzer_success.png)

**Examen en attente**
![Exemple d'examen en attente](images/analyzer_pending.png)

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
