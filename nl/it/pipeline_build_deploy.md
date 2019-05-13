---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-12"

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

# Creazione e distribuzione
{: #deliverypipeline_build_deploy}

{{site.data.keyword.contdelivery_full}} include Delivery Pipeline, che puoi utilizzare per implementare un processo di integrazione continua e distribuzione continua ripetibile.
{:shortdesc}

Completa le seguenti attività per configurare una pipeline.

## Aggiunta di una fase
{: #deliverypipeline_add_stage}

1. Nella pagina Pipeline, fai clic su **ADD STAGE**. Viene aperta la pagina di configurazione della fase.
2. Configura la fase.
  1. Nella scheda **INPUT**, seleziona un input per la fase.  Per le fasi di build, la scheda di input include un campo **Branch** per specificare il ramo nel repository da utilizzare per l'input.
  2. Nella scheda **JOBS**, aggiungi e configura almeno un lavoro. La prima fase normalmente dispone di almeno un lavoro di creazione.
3. Fai clic su **SAVE**.

## Aggiunta di un lavoro a una fase
{: #deliverypipeline_add_job}

1. Nella fase, fai clic sull'icona **Stage Configuration** e fai quindi clic su **Configure Stage**.
2. Fai clic sulla scheda **JOBS**.
3. Fai clic su **ADD JOB**. Seleziona il tipo di lavoro da aggiungere.
4. Configura il lavoro.
5. Fai clic su **SAVE**.

![Aggiunta di un lavoro a una fase](images/AddJob2.png)

## Esecuzione di una fase
{: #deliverypipeline_run_stage}

Puoi eseguire manualmente una fase facendo clic sull'icona **Run Stage** nella pagina Pipeline.

![Clic sull'icona di esecuzione della fase su una fase](images/RunStage.png)

Puoi anche richiedere distribuzioni e creazioni on-demand dalla pagina della cronologia di creazione in uno dei seguenti due modi:
* Trascina una creazione nella casella nella fase configurata.
* Nella sezione LAST EXECUTION RESULT, fai clic sull'icona **Send to** e seleziona quindi uno spazio in cui eseguire la distribuzione.
  ![Fase di esecuzione con questa icona di creazione](images/deploy_to.png)

Per annullare una fase in esecuzione, nella fase, fai clic su **View logs and history**. Nell'elenco dei lavori, fai clic sul numero di lavori in esecuzione e quindi fai clic su **CANCEL**. Puoi anche annullare i lavori individualmente facendo clic su un lavoro e quindi su **CANCEL** o facendo clic sull'icona **Stop** per un lavoro nella relativa fase.

## Distribuzione di un'applicazione
{: #deliverypipeline_deploy}

Un lavoro di distribuzione configurato correttamente distribuisce la tua applicazione alla tua destinazione quando il lavoro è in esecuzione. Per eseguire manualmente un lavoro di distribuzione, fai clic sull'icona **Run Stage** della fase in cui si trova il lavoro.

### Revisioni input
{: #deliverypipeline_input_revisions}

Quando esegui una fase manualmente o se viene eseguita perché la fase precedente è stata completata, la fase in esecuzione seleziona la propria revisione dell'input. Generalmente, la revisione dell'input è un numero di build. Per selezionare la revisione dell'input, la fase segue queste condizioni:

* Se viene selezionata una revisione specifica, la utilizza.
* Se non viene specificata una revisione specifica, ricerca nelle fasi precedenti finché non trova una fase che utilizza lo stesso input. Trova e utilizza l'ultima revisione di esecuzione corretta di tale input.
* Se non viene specificata una revisione specifica e nessun'altra fase utilizza l'origine specificata come input, utilizza l'ultima revisione dell'input.

Puoi distribuire una creazione precedente. Nella fase che contiene la generazione, fai clic su **View logs and history**. Nella pagina che viene aperta, fai clic per espandere il numero di esecuzione e quindi fai clic sul lavoro di creazione. Fai clic su **SEND TO** e seleziona una destinazione.
{: tip}

### Aggiunta di servizi alle applicazioni
{: #deliverypipeline_add_services}

Puoi aggiungere i servizi alle tue applicazioni e gestirli dal tuo dashboard {{site.data.keyword.Bluemix_notm}} o dalla CLI (command line interface) Cloud Foundry. Puoi anche immettere i comandi della CLI Foundry negli script per i lavori della pipeline. Ad esempio, puoi aggiungere un servizio a un'applicazione nello script di un lavoro di distribuzione. Per ulteriori informazioni sull'aggiunta dei servizi, consulta [Connessione dei servizi alle applicazioni esterne](/docs/resources?topic=resources-externalapp).

## Visualizzazione dei log
{: #deliverypipeline_view_logs}

Puoi visualizzare i log per i lavori e visualizzare le fasi poiché sono in esecuzione nella pagina della cronologia della fase.

1. Per visualizzare un log del lavoro, fai clic sul lavoro. In alternativa, in una fase, fai clic su **View logs and history**.

2. Per visualizzare il log di runtime di un'applicazione distribuita, fai clic su **View runtime log**.

In aggiunta ai log del lavoro, puoi visualizzare i risultati della verifica dell'unità, le risorse utente generate e le modifiche al codice per ogni lavoro di creazione.

Puoi anche eseguire, ridistribuire, annullare o configurare una fase dalla pagina Stage History. Fai clic su **RUN** per eseguire la fase, su **REDEPLOY** per eseguire nuovamente la distribuzione se si tratta di un lavoro di distribuzione oppure su **CONFIGURE** per configurare una fase. Puoi annullare una fase in esecuzione facendo clic sul numero di esecuzione e quindi su **ANNULLA**.

### Download dei log da uno script
{: #deliverypipeline_download_logs}

Puoi scaricare il file di log per un lavoro della pipeline da uno script e salvare il `PIPELINE_LOG_URL` che viene fornito mentre il lavoro della pipeline è in esecuzione. Il seguente esempio mostra la procedura per caricare il file di log del lavoro della pipeline su un sistema diverso.


1. Imposta una proprietà di ambiente `JOB_LOG` per la tua fase.

1. Nel tuo lavoro della pipeline, salva il `PIPELINE_LOG_URL`.

   ```shell
   export JOB_LOG="$PIPELINE_LOG_URL"
   ```
1. Utilizza il `PIPELINE_LOG_URL` in un lavoro successivo all'interno della stessa fase per scaricare il file di log per esportarlo su un sistema diverso. Utilizza un token Bearer IBM Cloud per accedere al file di log.

   ```shell
   ibmcloud login -a api.ng.bluemix.net \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   curl -H "Authorization: Bearer $BEARER"  \
     -H "Accept: text/plain" \
     -D /tmp/headers.txt \
     -o job_log.txt \
     "$JOB_LOG"
   ```
1. Controlla l'intestazione `X-More-Data`. Se l'intestazione è impostata su `true`, il file di log è in fase di generazione o elaborazione. Se l'intestazione è impostata su `false`, il file di log è pronto per l'uso.

   ```shell
   grep X-More-Data /tmp/headers.txt
   X-More-Data: false
   ```
1. Carica il file di log sul tuo sistema.

   ```shell
   scp job_log.txt user@example.org:/job1/logs
   ```


### Download di risorse da uno script
{: #deliverypipeline_download_artifacts}

Puoi scaricare le risorse per un lavoro di build della pipeline da uno script e salvare il `PIPELINE_ARTIFACT_URL` che viene fornito mentre il lavoro della pipeline è in esecuzione. Il seguente esempio mostra la procedura per caricare le risorse del lavoro della pipeline su un sistema diverso.


1. Imposta una proprietà di ambiente `JOB_ARTIFACT` per la tua fase.

1. Nel tuo lavoro della pipeline, salva il `PIPELINE_ARTIFACT_URL`.

   ```shell
   export JOB_ARTIFACT="$PIPELINE_ARTIFACT_URL"
   ```
   
1. Utilizza il `PIPELINE_ARTIFACT_URL` in un lavoro successivo all'interno della stessa fase per scaricare le risorse per esportarle su un sistema diverso. Utilizza un token Bearer IBM Cloud per accedere alle risorse.

   ```shell
   ibmcloud login -a api.ng.bluemix.net \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   DOWNLOAD_URL=$( curl -H "Authorization: Bearer $BEARER"  \
     "$JOB_ARTIFACT" )

   curl -O  "$DOWNLOAD_URL"
   ```
   
1. Carica le risorse sul tuo sistema.

   ```shell
   scp $(basename "$DOWNLOAD_URL") user@example.org:/job1/artifacts
   ```
