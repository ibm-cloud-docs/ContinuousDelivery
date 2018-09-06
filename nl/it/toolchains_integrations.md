---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}   

# Configurazione delle integrazioni dello strumento
{: #integrations}

Puoi configurare le integrazioni dello strumento che supportano le attività di operazioni, sviluppo e distribuzione mentre crei una toolchain aperta o puoi aggiungere e configurare le integrazioni dello strumento per personalizzare una toolchain esistente.  
{:shortdesc}

Le integrazioni dello strumento disponibili per aggiungere e configurare la tua toolchain sono diverse a seconda se stai utilizzando le toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato. Se stai utilizzando le toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico, le integrazioni dello strumento a tua disposizioni dipendono dalla regione della tua toolchain e dalla disponibilità di integrazioni dello strumento in tale regione. Se stai utilizzando le toolchain in {{site.data.keyword.Bluemix_notm}} Dedicato, le integrazioni dello strumento disponibili dipendono dal modo in cui {{site.data.keyword.contdelivery_full}} è stato configurato nel tuo ambiente specifico.

|Integrazione strumento |Disponibile in {{site.data.keyword.Bluemix_notm}} Pubblico	|Disponibile in {{site.data.keyword.Bluemix_notm}} Dedicato (dipendente dall'ambiente)|
|:----------|:------------------------------|:------------------|
|{{site.data.keyword.alertnotificationshort}}		|Stati Uniti Sud		|No		|
|Artifactory		|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|Monitoraggio della disponibilità		|Stati Uniti Sud		|No		|
|Bitbucket		|Stati Uniti Sud, Germania, Regno Unito		|No		|
|Gestione evento cloud		|Stati Uniti Sud		|No		|
|{{site.data.keyword.deliverypipeline}} 		|Stati Uniti Sud, Germania, Regno Unito	   	|Sì  		|
|{{site.data.keyword.DRA_short}} 		|Stati Uniti Sud		|No			|
|Eclipse Orion {{site.data.keyword.webide}}		|Stati Uniti Sud, Germania, Regno Unito		|Sì			|
|{{site.data.keyword.gitrepos}}	|Stati Uniti Sud, Germania, Regno Unito		|No		|
|GitHub		|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|{{site.data.keyword.ghe_short}} Dedicato e problemi			|No		|Sì		|
|GitLab		|Stati Uniti Sud, Germania, Regno Unito		|No		|
|Jenkins		|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|JIRA		|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|Nexus			|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|Altro strumento			|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|PagerDuty			|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|Rational Team Concert			|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|Sauce Labs		|Stati Uniti Sud, Germania, Regno Unito		|No		|
|Slack			|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
|SonarQube			|Stati Uniti Sud, Germania, Regno Unito		|Sì		|
{: caption="Tabella 1. Integrazioni dello strumento disponibili per le toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e Dedicato" caption-side="top"}

Se vuoi iniziare a sviluppare con il codice sorgente in {{site.data.keyword.Bluemix_notm}} Pubblico, configura l'integrazione dello strumento GitHub o l'integrazione dello strumento {{site.data.keyword.gitrepos}} prima di configurare la {{site.data.keyword.deliverypipeline}}. Se desideri avviare lo sviluppo con il codice in {{site.data.keyword.Bluemix_notm}} Dedicato, configura l'integrazione dello strumento {{site.data.keyword.ghe_short}} o l'integrazione dello strumento GitHub prima di configurare la {{site.data.keyword.deliverypipeline}}.
{: tip}


## Configurazione di Alert Notification
{: #alertnotification}

{{site.data.keyword.alertnotificationfull}} è una soluzione basata sul cloud ibrida che puoi utilizzare per centralizzare e semplificare la tua strategia di notifica. Funziona con altre applicazioni in loco e basate sul cloud. Gli avvisi vengono inoltrati a {{site.data.keyword.alertnotificationshort}} utilizzando un'API RESTful sicura.

Configura {{site.data.keyword.alertnotificationshort}} per ricevere le notifiche sui problemi durante il tuo processo DevOps.

### Prerequisiti

1. Se non disponi di un account {{site.data.keyword.alertnotificationshort}}, registrane uno:

 a. Apri la pagina [IBM {{site.data.keyword.alertnotificationshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/alert-notification){: new_window} in IBM Marketplace.

 b. Acquista una sottoscrizione o registrati per la prova gratuita di 90 giorni.

1. Dopo aver configurato il tuo account {{site.data.keyword.alertnotificationshort}}, apri [My IBM Dashboard ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://myibm.ibm.com/dashboard/){: new_window}.
1. Accanto a IBM {{site.data.keyword.alertnotificationshort}}, fai clic su **Launch**.
1. Fai clic su **Manage API Keys** e su **Create API Key**.
1. Nel campo **Create API Key**, immetti una descrizione.
1. Fai clic su **Generate**. Vengono visualizzate le nuove informazioni sulla chiave API, inclusi nome e password. Hai bisogno di tali informazioni per la configurazione dell'integrazione dello strumento, per cui mantieni aperta la finestra della nuova chiave API. Per motivi di sicurezza, non puoi richiamare successivamente la password della chiave API.

### Configurazione di Alert Notification

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **{{site.data.keyword.alertnotificationshort}}**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **{{site.data.keyword.alertnotificationshort}}**.

1. Immetti l'URL per l'API {{site.data.keyword.alertnotificationshort}} che desideri utilizzare. Puoi trovare l'URL nella pagina di gestione delle chiavi API del servizio {{site.data.keyword.alertnotificationshort}}; ad esempio, `https://ibmnotifybm.mybluemix.net/api/alerts/v1`.
1. Immetti il nome della chiave API per {{site.data.keyword.alertnotificationshort}}. Puoi trovare il nome della chiave API nella finestra della nuova chiave API.
1. Immetti la password che {{site.data.keyword.alertnotificationshort}} ha generato per la chiave API. Puoi trovare la password della chiave API nella finestra della nuova chiave API.
1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su **{{site.data.keyword.alertnotificationshort}}**.

### Ulteriori informazioni su Alert Notification

Per ulteriori informazioni su {{site.data.keyword.alertnotificationshort}}, leggi l'[articolo su IBM {{site.data.keyword.alertnotificationshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/manage/tool_alert_notification/){: new_window} su IBM Cloud Garage Method o segui queste esercitazioni:

  * [Aggiungi una integrazione dello strumento a una toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/add-a-tool-integration-to-a-toolchain){:new_window}

  * [Gestisci la tua applicazione {{site.data.keyword.Bluemix_notm}} utilizzando {{site.data.keyword.Bluemix_notm}} Availability Monitoring and Alert Notification ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:new_window}


## Configurazione di Artifactory
{: #artifactory}

Configura il gestore del repository Artifactory per archiviare le risorse di build nel tuo repository (repo) Artifactory:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Artifactory**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Artifactory**.

1. Immetti l'URL per il repository Artifactory che desideri aprire quando fai clic sulla scheda Artifactory.
1. Seleziona il tipo di repository a cui vuoi collegarti.
1. Se stai utilizzando un registro npm Artifactory, completa la seguente procedura:

 a. Immetti l'indirizzo email associato al tuo registro.

 b. Immetti il token di autenticazione associato al tuo registro.

 c. Immetti l'URL per il tuo repository della release Artifactory, che corrisponde al tuo registro privato nel server Artifactory.

 d. Immetti l'URL per il registro Mirror o Public che utilizzi per combinare più registri npm privati e pubblici. Ad esempio, questo URL potrebbe essere l'URL del registro virtuale nel tuo server Artifactory che può accedere al tuo registro privato e a una cache del registro globale npm.

1. Se stai utilizzando un repository Artifactory Maven, completa la seguente procedura:

 a. Immetti l'ID utente associato al tuo repository.

 b. Immetti la password associata al tuo repository.

 c. Immetti l'URL per il tuo repository della release Artifactory, che corrisponde al tuo repository della release privato sul server Artifactory.

 d. Immetti l'URL del tuo repository delle istantanee Artifactory, che corrisponde al tuo repository delle istantanee privato sul server Artifactory.

 e. Immetti l'URL per il repository Mirror o Public che utilizzi per combinare più repository Maven privati e pubblici. Ad esempio, questo URL potrebbe essere l'URL del repository virtuale nel tuo server Artifactory che può accedere ai tuoi repository privati e a una cache del repository centrale Maven.

1. Fai clic su **Create Integration**.
1. Fai clic sulla scheda del repository Artifactory che desideri utilizzare. Si apre il sito web Artifactory, dove puoi visualizzare i contenuti del repository.
1. Facoltativo: se stai utilizzando una toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e desideri creare la tua applicazione utilizzando Artifactory con npm, configura la tua pipeline per aggiungere un lavoro di build npm. Per istruzioni sulla configurazione del lavoro di build, consulta la sezione [Configurazione di un lavoro di build npm Artifactory nella tua pipeline](#config_artifactory_npm).
1. Facoltativo: se stai utilizzando una toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e desideri creare la tua applicazione utilizzando Artifactory con Maven, configura la tua pipeline per aggiungere un lavoro di build Maven. Per istruzioni sulla configurazione del lavoro di build, consulta la sezione [Configurazione di un lavoro di build Artifactory Maven nella tua pipeline](#config_artifactory_maven).

### Configurazione di un lavoro di build npm Artifactory nella tua pipeline
{: #config_artifactory_npm}

Prima di configurare un lavoro di build npm nella tua pipeline, devi disporre di una pipeline funzionante che utilizzi per creare il repository SCM come input e devi configurare Artifactory per la tua toolchain. Per istruzioni sulla configurazione di Artifactory, vedi la sezione [Artifactory](#artifactory).

Configura {{site.data.keyword.deliverypipeline}} per aggiungere un lavoro di build npm:

1. Crea una fase e configura l'input per il repository SCM appropriato.
1. Nella fase, aggiungi un lavoro di build.
1. Configura il lavoro di build:
  ![npm build job](images/artifactory_npm_job.png)

  a. Per il tipo di builder, seleziona **NPM Build**.

  b. Se hai configurato più istanze dell'integrazione dello strumento Artifactory, immetti il nome dell'integrazione dello strumento Artifactory per cui desideri configurare il lavoro di build npm.

  c. Per il tipo di integrazione dello strumento, seleziona **Artifactory**.

  d. Per il comando di build, immetti i comandi per creare il tuo modulo npm o pubblicalo nel tuo registro. Questo esempio mostra i comandi per creare il modulo o per pubblicarlo.
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  Puoi trovare l'URL e le credenziali utente che hai utilizzato per collegarti al tuo registro nelle impostazioni di configurazione per l'integrazione dello strumento Artifactory.
  {: tip}

  e. Se il tuo lavoro di build viene pubblicato nel registro Artifactory e il formato della versione del modulo del tuo nodo è `x.y.z-SNAPSHOT.w`, seleziona la casella di spunta **Increment snapshot module version**. Il lavoro di build aggiorna automaticamente la versione del modulo prima che il lavoro venga pubblicato nel registro Artifactory. Il lavoro seleziona l'ultima versione del modulo dal registro npm e il file `package.json` locale e incrementa la versione del modulo utilizzando semver. Il lavoro di build non fornisce le modifiche al repository SCM.

1. Fai clic su **SAVE**. Se la tua pipeline è in esecuzione, questo lavoro di build utilizza le informazioni sulla configurazione dall'integrazione dello strumento Artifactory per collegarsi al tuo registro npm.

### Configurazione di un lavoro di build Artifactory Maven nella tua pipeline
{: #config_artifactory_maven}

Prima di configurare un lavoro di build Maven nella tua pipeline, devi disporre di una pipeline funzionante che utilizzi per creare il repository SCM come input e devi configurare Artifactory per la tua toolchain. Per istruzioni sulla configurazione di Artifactory, vedi la sezione [Artifactory](#artifactory).

Configura la {{site.data.keyword.deliverypipeline}} per aggiungere un lavoro di build Maven:

1. Crea una fase e configura l'input per il repository SCM appropriato.
1. Nella fase, aggiungi un lavoro di build.
1. Configura il lavoro di build:
  ![Maven build job](images/artifactory_maven_job.png)

  a. Per il tipo di builder, seleziona **Maven Build**.

  b. Se hai configurato più istanze dell'integrazione dello strumento Artifactory, immetti il nome dell'integrazione dello strumento Artifactory per cui desideri configurare il lavoro di build Maven.

  c. Per il tipo di integrazione dello strumento, seleziona **Artifactory**.

  d. Per il comando di build, immetti i comandi per creare il tuo modulo Maven o pubblicalo nel tuo registro delle istantanee. Questo esempio mostra i comandi per creare il modulo o per pubblicarlo in un registro delle istantanee.
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  Puoi trovare l'URL e le credenziali utente che hai utilizzato per collegarti al tuo registro nelle impostazioni di configurazione per l'integrazione dello strumento Artifactory.
  {: tip}

1. Fai clic su **SAVE**. Se la tua pipeline è in esecuzione, questo lavoro di build utilizza le informazioni sulla configurazione dall'integrazione dello strumento Artifactory per collegarsi al tuo repository Maven.

### Ulteriori informazioni su Artifactory

Per ulteriori informazioni su Artifactory, leggi l'[articolo su Artifactory ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/deliver/tool_artifactory/){: new_window} su IBM Cloud Garage Method.


## Aggiunta del monitoraggio della disponibilità
{: #availabilitymonitoring}

{{site.data.keyword.prf_hublong}} isola i problemi, identifica i modelli e migliora le prestazioni prima che gli utenti ne siano influenzati. Puoi verificare la tua applicazioni da diverse posizioni in tutto il mondo, integrarla con le delivery pipeline e ottenere informazioni approfondite su come ottimizzare continuamente il tuo codice.

Questa integrazione dello strumento è preconfigurata e non richiede alcun parametro di configurazione. Non puoi riconfigurare questa integrazione dello strumento.
{: tip}

Per verificare, monitorare e migliorare l'integrità della tua applicazione, come la crei, aggiungi l'integrazione dello strumento {{site.data.keyword.prf_hubshort}}:

1. Nel dashboard DevOps, nella pagina Toolchains, fai clic sulla toolchain a cui desideri aggiungere {{site.data.keyword.prf_hubshort}}. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **{{site.data.keyword.prf_hubshort}}**.

1. Fai clic su **Create Integration**.
1. Fai clic su **{{site.data.keyword.prf_hubshort}}** per aprire il dashboard {{site.data.keyword.prf_hubshort}}, seleziona un'applicazione e configura il monitoraggio per l'applicazione.

### Ulteriori informazioni sul Monitoraggio della disponibilità

Per ulteriori informazioni su {{site.data.keyword.prf_hubshort}}, leggi l'[articolo su {{site.data.keyword.prf_hublong}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/manage/tool_bluemix_availability_monitoring/){: new_window} su IBM Cloud Garage Method o segui questa esercitazione:

  * [Gestisci la tua applicazione {{site.data.keyword.Bluemix_notm}} utilizzando {{site.data.keyword.Bluemix_notm}} Availability Monitoring and Alert Notification ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:new_window}


## Configurazione di Bitbucket
{: #bitbucket}

Consente di archiviare il proprio codice sorgente in un repository nuovo o esistente su bitbucket.org e di partecipare al social coding mediante wiki, traccia dei problemi e richieste di pull.

Configura Bitbucket per collaborare sul codice con il tuo team:

1. Dal dashboard DevOps, fai clic su **Toolchains**. Fai clic sulla toolchain a cui desideri aggiungere Bitbucket. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Bitbucket**.

   Se stai configurando questa integrazione dello strumento su {{site.data.keyword.Bluemix_notm}} Pubblico e non hai autorizzato {{site.data.keyword.Bluemix_notm}} ad accedere a Bitbucket, fai clic su **Autorizza** per andare al sito web Bitbucket. Se non hai una sessione di Bitbucket attiva, ti viene richiesto di eseguire l'accesso. Fai clic su **Grant access** per consentire alle toolchain {{site.data.keyword.Bluemix_notm}} di accedere alle seguenti parti del tuo account Bitbucket:
   
   * **Leggi le informazioni del tuo account**. Ottieni le informazioni sull'utente di base per popolare l'interfaccia utente.
   
   * **Leggi e modifica i problemi dei tuoi repository**. Consenti a {{site.data.keyword.contdelivery_short}} di aggiornare i problemi per indicare quando la pipeline distribuisce i commit collegati a tali problemi. 
   
   * **Leggi le impostazioni del progetto del tuo team e leggi i repository contenuti nei progetti del tuo team**. Consenti a {{site.data.keyword.contdelivery_short}} di integrarsi con i repository gestiti dai team.
   
   * **Leggi e modifica i tuoi repository e le rispettive richieste di pull**. Consenti a {{site.data.keyword.contdelivery_short}} di eseguire il push del codice nei repository, quando gli utenti richiedono il codice.
   
   * **Gestisci i tuoi repository**. Consenti a {{site.data.keyword.contdelivery_short}} di creare nuovi repository, quando richiesto dagli utenti.
   
   * **Leggi le informazioni di appartenenza al tuo team**. Consenti a {{site.data.keyword.contdelivery_short}} di mostrare un elenco dei tuoi team nel menu **Owner** visualizzato quando crei un nuovo repository.
   
   * **Leggi e modifica i webhook dei tuoi repository**. Consenti alla pipeline di attivare le build quando viene eseguito il push dei commit a un repository.
   {: tip}
   
   Se hai una sessione di Bitbucket attiva ma non hai immesso la tua password recentemente, ti potrebbe essere richiesto di immettere la tua password Bitbucket per la conferma.

1. Fai clic sul server Bitbucket che vuoi utilizzare.
1. Se hai un repository Bitbucket che vuoi utilizzare, immetti l'URL per il repository. Per il tipo di repository, fai clic su **Existing**.
1. Se desideri utilizzare un nuovo repository Bitbucket, immetti un nome per il repository, digita l'URL per il repository che stai clonando o dividendo e seleziona il tipo di repository:

 a. Per creare un repository vuoto, fai clic su **New**.

 b. Per creare una copia di un repository, fai clic su **Clone**.

 c. Per biforcare un repository in modo che sia possibile fornire le modifiche attraverso le richieste di importazione, fai clic su **Fork**.

1. Per creare un repository privato sul server, seleziona la casella di spunta **Make this repository private**.
1. Per utilizzare Bitbucket Issues per la traccia dei problemi, seleziona la casella di spunta **Enable Bitbucket Issues**.
1. Per tracciare la distribuzione delle modifiche del codice creando tag e commenti sui commit, ed etichette e commenti sui problemi a cui fanno riferimento i commit, seleziona la casella di spunta **Track deployment of code changes**. Per ulteriori informazioni, consulta [Track where your code is deployed with toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic sulla scheda per il repository Bitbucket che desideri utilizzare. Si apre il sito web Bitbucket, dove puoi visualizzare il contenuto del repository.
1. Se hai abilitato Problemi Bitbucket, fai clic su **Bitbucket Issues** per aprirlo. Puoi utilizzare questa istanza dei problemi Bitbucket per la toolchain completa, anche se la toolchain contiene più repository Bitbucket.    

Se non hai i privilegi Proprietario o Master per il repository a cui sei collegato, la tua integrazione è limitata perché non puoi utilizzare un webhook. I webhook sono richiesti per eseguire automaticamente una pipeline quando si esegue il push di un commit al repository. Senza un webhook, devi avviare le tue pipeline manualmente.
{: tip}

### Ulteriori informazioni su Bitbucket

Per ulteriori informazioni su Bitbucket, leggi l'[articolo su Bitbucket ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/code/tool_bitbucket/){: new_window} su IBM Cloud Garage Method.


## Aggiunta della gestione evento cloud
{: #cloudeventmanagement}

{{site.data.keyword.evtmgt_full}} fornisce una vista consolidata di problemi che si verificano con i tuoi servizi, applicazioni e infrastruttura. Puoi configurare la gestione dell'indicente in tempo reale per risolvere i problemi più efficacemente.

Questa integrazione dello strumento è preconfigurata e non richiede alcun parametro di configurazione. Non puoi riconfigurarla.
{: tip}

Per aiutare il tuo team DevOps a raggiungere gli obiettivi di archiviazione operativa affidabile, qualità del servizio e miglioramento continuo, aggiungi la gestione dell'evento cloud alla tua toolchain:

1. Dal dashboard DevOps, fai clic su **Toolchains**. Fai clic sulla toolchain a cui desideri aggiungere la gestione dell'evento cloud. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Gestione evento cloud**.

1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su una qualsiasi delle seguenti schede dello strumento:

 * **Cloud Event Management** per iniziare ad utilizzare la gestione dell'evento cloud.

 * **{{site.data.keyword.alertnotificationshort}}** per creare le politiche che determinano quali utenti ricevono le notifiche dell'incidente.

 * **Runbook Automation** per gestire il tuo catalogo di runbook nella gestione dell'evento cloud:

### Ulteriori informazioni su Gestione evento cloud

Per ulteriori informazioni su Gestione evento cloud, leggi l'[articolo su Cloud Event Management ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){: new_window} su IBM Cloud Garage Method.


## Configurazione di Delivery Pipeline
{: #deliverypipeline}

{{site.data.keyword.deliverypipeline}} automatizza la distribuzione continua dei tuoi progetti tramite una sequenza di fasi che richiamano i lavori di input ed esecuzione, come le creazioni, le verifiche e le distribuzioni.

Configura {{site.data.keyword.deliverypipeline}} per automatizzare la distribuzione, la verifica e la creazione continua delle tue applicazioni:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **{{site.data.keyword.deliverypipeline}}**. A seconda del template che utilizzi, possono essere disponibili diversi campi. Rivedi i valori di campo predefiniti e se necessario, modifica queste impostazioni.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **{{site.data.keyword.deliverypipeline}}**.

1. Specifica un nome per la tua nuova pipeline.
1. Se hai intenzione di utilizzare la tua pipeline per distribuire un'interfaccia utente, seleziona la casella di spunta **Mostra applicazioni nel menu VISUALIZZA APPLICAZIONI**. Tutte le applicazioni create dalla tua pipeline vengono visualizzate nell'elenco **Visualizza applicazione** nella pagina di panoramica della toolchain.
1. Fai clic su **Create Integration** per aggiungere la {{site.data.keyword.deliverypipeline}} alla tua toolchain.
1. Fai clic su **{{site.data.keyword.deliverypipeline}}** per visualizzare la pipeline e configurarla. Per informazioni sulla configurazione di una pipeline, consulta [Building and deploying pipelines](/docs/services/ContinuousDelivery/pipeline_build_deploy.html){: new_window}.

  Se vuoi che la pipeline venga eseguita automaticamente quando si esegue il push del commit al tuo repository GitHub, {{site.data.keyword.ghe_short}} o Git, segui questa procedura:

   a. Configura GitHub, {{site.data.keyword.ghe_short}} o {{site.data.keyword.gitrepos}} per la tua toolchain prima di definire le fasi per la tua pipeline. Le fasi della pipeline necessitano di URL Git per i tuoi repository. Ogni fase della pipeline può far riferimento solo a uno dei repository GitHub, {{site.data.keyword.ghe_short}} o Git associati alla tua toolchain. Per istruzioni sulla configurazione di GitHub, vedi la sezione [GitHub](#github). Per istruzioni sulla configurazione di {{site.data.keyword.ghe_short}} dedicato, consulta [Introduzione a {{site.data.keyword.ghe_long}}](/docs/services/ghededicated/index.html){: new_window}. Per istruzioni per configurare {{site.data.keyword.gitrepos}}, consulta la sezione [{{site.data.keyword.gitrepos}}](#gitbluemix).

   b. Utilizza un webhook. Senza un webhook, puoi eseguire le pipeline solo manualmente. Per utilizzare un webhook quando ti colleghi a un repository GitHub o {{site.data.keyword.ghe_short}}, hai bisogno di privilegi di amministratore. Per collegarti a un repository {{site.data.keyword.gitrepos}}, hai bisogno dei privilegi Master o Proprietario.

1. Facoltativo: se stai utilizzando una toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e desideri che Sauce Labs esegua delle verifiche sulla tua applicazione, configura la {{site.data.keyword.deliverypipeline}} per aggiungere un lavoro di verifica Sauce Labs. Per istruzioni sulla configurazione del lavoro di verifica, consulta la sezione [Configurazione di un lavoro di verifica Sauce Labs nella tua pipeline](#config_saucelabs).

### Configurazione di un lavoro di verifica Sauce Labs nella tua pipeline
{: #config_saucelabs}

Prima di configurare un lavoro di verifica Sauce Labs nella tua pipeline, devi disporre di una pipeline funzionante provvista di fasi per creare e distribuire la tua applicazione e devi configurare Sauce Labs per la tua toolchain. Per istruzioni sulla configurazione di Sauce Labs, consulta la sezione [Sauce Labs](#saucelabs).

Configura la {{site.data.keyword.deliverypipeline}} per aggiungere un lavoro di verifica Sauce Labs:

1. Se non disponi di una fase che distribuisce una versione di verifica della tua applicazione, creane una.
1. Nella fase, aggiungi un lavoro di verifica dopo il lavoro di distribuzione. Posizionando questi lavori nella stessa fase, essi possono accedere alla stessa serie di proprietà dell'ambiente.   
  ![Lavoro di verifica](images/toolchain_test_job.png)

1. Configura la fase. Nella scheda **ENVIRONMENT PROPERTIES**, crea la proprietà CF_APP_NAME.

  Il nome utente e la chiave di accesso di Sauce Labs sono disponibili nello script del lavoro di test in forma di variabili di ambiente SAUCE_USERNAME e SAUCE_ACCESS_KEY. Quando scrivi i tuoi test, devi utilizzare queste variabili di ambiente per eseguire l'autenticazione con Sauce Labs.
  {: tip}

1. Configura il lavoro di distribuzione. Nel campo **Deploy Script**, includi questo comando: `export CF_APP_NAME="$CF_APP"`. Questo comando esporta il nome dell'applicazione come una proprietà dell'ambiente.
1. Configura il lavoro di verifica. I valori nella seguente immagine sono degli esempi. I campi **Service Instance**, **Target**, **Organization** e **Space** vengono popolati con il nome utente, la regione, l'organizzazione e lo spazio Sauce Labs che stai utilizzando.  
![Configura lavoro](images/toolchain_configure_job.png)

  a. Per il tipo di tester, seleziona **Sauce Labs**.

  b. Per l'istanza del servizio, seleziona il nome utente Sauce Labs che hai utilizzato durante la configurazione di Sauce Labs per la tua toolchain.

   Per visualizzare il nome utente e la chiave di accesso utilizzati durante la configurazione di Sauce Labs per la tua toolchain, fai clic su **Configure**.
   {: tip}

  c. Nel campo **Test Execution Command**, immetti i comandi che installano le dipendenze necessarie per le tue verifiche e quindi esegui le verifiche. Ad esempio, per un'applicazione Node.js, devi immettere questi comandi:
     ```
     npm install
     node_modules/grunt-cli/bin/grunt test:sauce:parallel
     ```

    d. Se desideri visualizzare i report di verifica nei log del lavoro di verifica, seleziona la casella di spunta **Enable Test Report** e imposta il pattern del file dei risultati della verifica su `test/*.xml`.

1. Fai clic su **SAVE**. Se la tua pipeline è in esecuzione, puoi eseguire le tue verifiche Sauce Labs.

### Ulteriori informazioni su Delivery Pipeline

Per ulteriori informazioni su {{site.data.keyword.deliverypipeline}}, consulta [Gestione delle pipeline](/docs/services/ContinuousDelivery/pipeline_working.html){: new_window} e l'[articolo su Delivery Pipeline![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/deliver/tool_delivery_pipeline/){: new_window} in IBM Cloud Garage Method o segui queste esercitazioni:

  * [Crea una pipeline ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/create-a-pipeline){:new_window}

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}


## Aggiunta di DevOps Insights (Beta)
{: #dra}

{{site.data.keyword.DRA_full}} raccoglie e analizza i risultati dalle verifiche di unità, dalle verifiche funzionali e dagli strumenti di copertura del codice per determinare se il tuo codice soddisfa i criteri predefiniti nei gate specificati nel tuo processo di distribuzione. Se il tuo codice non soddisfa o supera i criteri, la distribuzione viene arrestata per prevenire che vengano rilasciati dei rischi. Puoi utilizzare {{site.data.keyword.DRA_short}} come una rete di sicurezza per il tuo ambiente di fornitura continua o come modo per implementare e migliorare gli standard di qualità.

 Questa integrazione dello strumento è disponibile solo su {{site.data.keyword.Bluemix_notm}} Pubblico.È preconfigurata e non richiede alcun parametro di configurazione. Non puoi riconfigurare questa integrazione dello strumento.
 {: tip}

Aggiungi {{site.data.keyword.DRA_short}} per mantenere e migliorare la qualità del tuo codice {{site.data.keyword.Bluemix_notm}} monitorando le tue distribuzioni per identificare i rischi prima che vangano rilasciati.

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **{{site.data.keyword.DRA_short}}**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **{{site.data.keyword.DRA_short}}**.

1. Fai clic su **Create Integration**.
1. Fai clic su **{{site.data.keyword.DRA_short}}** e quindi completa i primi passi: creazione dei criteri, connessione dei criteri alla pipeline ed esecuzione della pipeline.

### Ulteriori informazioni su DevOps Insights

Per ulteriori informazioni su {{site.data.keyword.DRA_short}}, leggi l'[articolo su {{site.data.keyword.DRA_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/learn/tool_devops_insights/){: new_window} su IBM Cloud Garage Method o segui queste esercitazioni:

  * [Use the "Develop and test a Cloud Foundry app" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:new_window}

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [Garantisci delle distribuzioni di qualità utilizzando la toolchain "Deployment Risk Analytics with GitHub and Jenkins" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}


## Aggiunta di Eclipse Orion Web IDE
{: #webide}

Eclipse Orion {{site.data.keyword.webide}} è un ambiente basato sul web integrato dove puoi creare, modificare, eseguire il debug e completare le attività di controllo dell'origine. Puoi spostare senza interruzioni dalla modifica per l'esecuzione, l'invio e la distribuzione.

 Questa integrazione dello strumento è preconfigurata. Non richiede alcun parametro di configurazione e non puoi riconfigurarla.
 {: tip}

Aggiungi l'integrazione dello strumento Eclipse Orion {{site.data.keyword.webide}} per completare le attività di controllo dell'origine:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Eclipse Orion {{site.data.keyword.webide}}**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Eclipse Orion {{site.data.keyword.webide}}**.

1. Fai clic su **Create Integration**.
1. Fai clic su **Eclipse Orion {{site.data.keyword.webide}}**. Il tuo spazio di lavoro viene prepopolato con i repository GitHub o {{site.data.keyword.ghe_short}}. I repository associati con la tua toolchain corrente sono evidenziati.

### Ulteriori informazioni su Eclipse Orion Web IDE

Per ulteriori informazioni su Eclipse Orion {{site.data.keyword.webide}}, vedi [Modifica del codice con Eclipse Orion {{site.data.keyword.webide}}](/docs/services/ContinuousDelivery/web_ide.html){: new_window} e l'articolo su [ Eclipse Orion {{site.data.keyword.webide}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/code/tool_eclipse_orion_web_ide/){: new_window} su IBM Cloud Garage Method o segui queste esercitazioni:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}


## Configurazione di Git Repos and Issue Tracking
{: #gitbluemix}

L'integrazione dello strumento {{site.data.keyword.gitrepos}} è basata su GitLab Community Edition, che è un servizio di host basato sul web per i repository Git. Puoi avere sia copie locali che remote dei tuoi repository. Per ulteriori informazioni, consulta [{{site.data.keyword.gitrepos}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help){:new_window}.

Se stai configurando {{site.data.keyword.gitrepos}} mentre stai creando la toolchain, attieniti alla seguente procedura:    

1. Nella sezione delle integrazioni configurabili, fai clic su **Git Repos and Issue Tracking**.
1. Rivedi le ubicazioni di destinazione predefinite per i repository Git. Questi repository vengono clonati dai repository di esempio. Se necessario, modifica i nomi dei repository di destinazione.

Se hai una toolchain e vuoi migrare un repository Git presente nella tua toolchain a {{site.data.keyword.gitrepos}}, completa la seguente procedura:

Queste istruzioni si applicano alle toolchain che già contengono il repository Git da migrare a {{site.data.keyword.gitrepos}}. Per informazioni sull'aggiunta di diversi tipi di repository Git alla tua toolchain, vedi le sezioni [Configurazione di GitHub](#github), [Configurazione di GitHub Enterprise e dei problemi su {{site.data.keyword.Bluemix_notm}} Dedicato](#configghe) e [Configurazione di GitLab](#gitlab).
{: tip}

1. Nel dashboard DevOps, nella pagina Toolchain, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.
1. Fai clic su **Add a tool**.
1. Nella sezione delle integrazioni dello strumento, fai clic su **Git Repos and Issue Tracking**.
1. Per creare una copia del repository Git, per il tipo di repository, fai clic su **Clone**. Immetti un nuovo nome per il repository e l'URL per il repository di origine.
1. Se desideri utilizzare i problemi per il tracciamento del problema, seleziona la casella di spunta **Enable Issues**.
1. Se desideri tracciare la distribuzione delle modifiche del codice creando tag e commenti nei commit e le etichette e i commenti sui problemi a cui fanno riferimento i commit, seleziona la casella di spunta **Track deployment of code changes**. Per ulteriori informazioni, consulta [Track where your code is deployed with toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Fai clic su **Create Integration**.

Dopo aver clonato il repository Git, puoi rimuoverlo dalla tua toolchain.
{: tip}

Se hai una toolchain e stai aggiungendo {{site.data.keyword.gitrepos}} a essa, attieniti alla seguente procedura:    

1. Nel dashboard DevOps, nella pagina Toolchain, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.
1. Fai clic su **Add a tool**.
1. Nella sezione delle integrazioni dello strumento, fai clic su **Git Repos and Issue Tracking**.
1. Seleziona un tipo di repository:     

  a. Per creare un repository vuoto, per il tipo di repository, fai clic su **New** e immetti il nome del repository.    
  b. Per biforcare un repository Git in modo che sia possibile fornire le modifiche attraverso le richieste di unione, per il tipo di repository, fai clic su **Fork**. Immetti l'URL per il repository di origine.    
  c. Per creare una copia di un repository Git, per il tipo di repository, fai clic su **Clone**. Immetti un nuovo nome per il repository e l'URL per il repository di origine.     
  d. Se hai un repository Git e desideri utilizzarlo, per il tipo di repository, fai clic su **Existing**. Immetti l'URL.    

1. Se desideri utilizzare i problemi per il tracciamento del problema, seleziona la casella di spunta **Enable Issues**.
1. Se desideri tracciare la distribuzione delle modifiche del codice creando tag e commenti nei commit e le etichette e i commenti sui problemi a cui fanno riferimento i commit, seleziona la casella di spunta **Track deployment of code changes**. Per ulteriori informazioni, consulta [Track where your code is deployed with toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Fai clic su **Create Integration**.
1. Fai clic sulla scheda del repository Git che desideri utilizzare. Viene aperta la pagina della panoramica del tuo progetto.    

Se non hai i privilegi Master o Proprietario per il repository a cui sei collegato, la tua integrazione è limitata perché non puoi utilizzare un webhook. I webhook sono richiesti per eseguire automaticamente una pipeline quando si esegue il push di un commit al repository. Senza un webhook, devi avviare le tue pipeline manualmente.
{: tip}

### Ulteriori informazioni su Git Repos and Issue Tracking

Per ulteriori informazioni su {{site.data.keyword.gitrepos}}, leggi l'[articolo {{site.data.keyword.gitrepos}}: Social coding hosted by IBM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/code/tool_git_repos_and_issue_tracking/){: new_window} su IBM Cloud Garage Method o segui questa esercitazione:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}


## Configurazione di GitHub
{: #github}

GitHub è un servizio host basato sul web per i repository Git. Puoi avere sia copie locali che remote dei tuoi repository, ciò rende più semplice la collaborazione.

{{site.data.keyword.ghe_short}} è un servizio host basato sul web, in loco per i repository Git.

Problemi GitHub è uno strumento di traccia che ti permette di lavorare sui tuoi piani in un solo posto. È integrato con il tuo repository di sviluppo in modo che puoi focalizzarti sulle attività importanti.

Puoi configurare GitHub come una integrazione dello strumento nella tua toolchain in modo da poter gestire il codice sorgente in un repository nuovo o esistente su GitHub.com o nell'istanza di {{site.data.keyword.ghe_short}} all'interno della tua azienda. Partecipa al social coding attraverso wiki, traccia dei problemi e richieste di pull.

Se stai configurando questa integrazione dello strumento mentre stai creando la toolchain, segui questi passi:

1. Se memorizzi il tuo codice sorgente in un repository GitHub, nella sezione Integrazioni configurabili, fai clic su **GitHub**. Se stai configurando questa integrazione dello strumento su {{site.data.keyword.Bluemix_notm}} Pubblico e non hai autorizzato {{site.data.keyword.Bluemix_notm}} ad accedere a GitHub, fai clic su **Autorizza** per andare al sito web GitHub. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub. Se disponi di una sessione GitHub attiva ma non hai immesso la tua password recentemente, ti potrebbe essere richiesto di immettere la tua password GitHub per la conferma.
1. Se utilizzi un repository sul tuo proprio server {{site.data.keyword.ghe_short}}, nella sezione Integrazioni configurabili, fai clic su **Add custom server**.

 La rete deve essere in grado di accedere al server Git di destinazione da un ambiente {{site.data.keyword.Bluemix_notm}} Dedicato. Se il tuo server GitHub non è disponibile su Internet pubblica o il nome host non viene risolto nel DNS (Domain Name Server) pubblico, [apri un ticket di supporto](/docs/services/ContinuousDelivery/cd_support.html#support-ticket){: new_window}. Puoi utilizzare il ticket di supporto per inoltrare una richiesta per aprire gli instradamenti di rete o aggiornare le impostazioni DNS.
 {: tip}

 Immetti un titolo per il tuo server GitHub personalizzato e specifica l'URL root del server. Immetti il token di accesso personale e fai clic su **Save custom integration**.

  Se non hai un token di accesso personale, puoi crearne uno:

     a. In una qualsiasi pagina di GitHub, fai clic sull'icona del tuo profilo e seleziona **Settings**.

     b. Nella barra laterale, fai clic su **Personal access tokens**.

     c. Fai clic su **Generate new token**.

     d. Aggiungi una descrizione per il token.

     e. Seleziona le caselle di spunta **repo** e **user** per definire l'accesso per il token personale.

     f. Fai clic su **Generate token**.

     g. Copia il token in un'ubicazione sicura e nell'applicazione di gestione delle password. Per motivi di sicurezza, dopo aver lasciato la pagina, non potrai più visualizzare il token.

1. Rivedi le ubicazioni del repository di destinazione predefinite per i repository GitHub. Questi repository vengono clonati dai repository di esempio. Se necessario, modifica i nomi dei repository di destinazione.
 ![Ubicazioni del repository di destinazione predefinite](images/toolchain_github_config.png)

Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, completa la seguente procedura:

1. Nel dashboard DevOps, nella pagina Toolchain, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.
1. Fai clic su **Add a tool**.
1. Nella sezione Integrazioni strumento, fai clic su **GitHub**.
1. Fai clic sul server GitHub server che vuoi utilizzare.
1. Se disponi di un repository GitHub o {{site.data.keyword.ghe_short}} e desideri utilizzarlo, per il tipo di repository, fai clic su **Existing** e immetti l'URL.
1. Se desideri utilizzare un nuovo repository GitHub o {{site.data.keyword.ghe_short}}, immetti un nome per il repository, digita l'URL per il repository che stai clonando o dividendo e seleziona il tipo di repository:

 a. Per creare un repository vuoto, fai clic su **New**.

 b. Per creare una copia di un repository GitHub o {{site.data.keyword.ghe_short}}, fai clic su **Clone**.

 c. Per biforcare un repository GitHub o {{site.data.keyword.ghe_short}} in modo che sia possibile fornire le modifiche attraverso le richieste di importazione , fai clic su **Fork**.

1. Se sei un utente di GitHub.com con un account aggiornato o se hai selezionato un server {{site.data.keyword.ghe_short}} e vuoi creare un nuovo repository privato sul server, seleziona la casella di spunta **Make this repository private**.
1. Se desideri utilizzare Problemi GitHub per la traccia del problema, seleziona la casella di spunta **Enable GitHub Issues**.
1. Se desideri tracciare la distribuzione delle modifiche del codice creando tag e commenti nei commit e le etichette e i commenti sui problemi a cui fanno riferimento i commit, seleziona la casella di spunta **Track deployment of code changes**. Per ulteriori informazioni, consulta [Track where your code is deployed with toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Fai clic su **Create Integration**.
1. Fai clic sulla scheda del repository GitHub o {{site.data.keyword.ghe_short}} che desideri utilizzare. A seconda del repository che hai selezionato, si aprirà il sito web di GitHub o il repository {{site.data.keyword.ghe_short}} della tua azienda, dove puoi visualizzare i contenuti del repository.

  Puoi utilizzare gli strumenti per la gestione del codice sorgente integrati in Eclipse Orion {{site.data.keyword.webide}} per modificare il repository GitHub e distribuire un'applicazione dal tuo spazio di lavoro.
  {: tip}

1. Se hai abilitato Problemi GitHub, fai clic su **GitHub Issues** per aprirlo. Puoi utilizzare questa istanza dei problemi GitHub per la toolchain completa, anche se la toolchain contiene più repository GitHub o {{site.data.keyword.ghe_short}}.    

Se non hai i privilegi da amministratore per il repository a cui sei collegato, la tua integrazione è limitata perché non puoi utilizzare un webhook. I webhook sono richiesti per eseguire automaticamente una pipeline quando si esegue il push di un commit al repository. Senza un webhook, devi avviare le tue pipeline manualmente.
{: tip}

### Ulteriori informazioni su GitHub

Per ulteriori informazioni su GitHub, consulta l'[articolo su GitHub ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/code/tool_github/){: new_window} e l'[articolo su GitHub Issues ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: new_window} in IBM Cloud Garage Method o segui queste esercitazioni:

 * [Use the "Develop and test a Cloud Foundry app" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:new_window}

  * [Garantisci delle distribuzioni di qualità utilizzando la toolchain "Deployment Risk Analytics with GitHub and Jenkins" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}

  * [Create a custom toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain){:new_window}


## Configurazione di GitHub Enterprise e dei problemi su {{site.data.keyword.Bluemix_notm}} Dedicato
{: #configghe}

 Queste istruzioni si applicano a {{site.data.keyword.Bluemix_notm}} Dedicato per {{site.data.keyword.ghe_short}}. Se stai utilizzando la tua propria versione gestita di {{site.data.keyword.ghe_short}}, alcuni passi potrebbero essere diversi a seconda delle tue procedure interne.
 {: tip}

{{site.data.keyword.ghe_long}} è un servizio host basato sul web, in loco per i repository Git. {{site.data.keyword.ghe_short}} Dedicato è solo per i clienti {{site.data.keyword.Bluemix_notm}} Dedicato. GitHub Issues è uno strumento di traccia che ti permette di lavorare sui tuoi piani in un solo posto. È integrato con il tuo repository di sviluppo in modo che puoi focalizzarti sulle attività importanti. Per ulteriori informazioni su {{site.data.keyword.ghe_short}} dedicato e sui problemi GitHub, consulta [Introduzione a {{site.data.keyword.ghe_long}}](/docs/services/ghededicated/index.html){: new_window} e l'[articolo su GitHub Issues ![Icona link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: new_window} in IBM Cloud Garage Method.

Puoi configurare {{site.data.keyword.ghe_short}} come una integrazione dello strumento nella tua toolchain in modo da poter gestire il codice sorgente nell'istanza [{{site.data.keyword.Bluemix_notm}} Dedicato](/docs/dedicated/index.html#dedicated){: new_window} all'interno della tua azienda.

1. Se stai configurando questa integrazione dello strumento mentre stai creando la toolchain, segui questi passi:

 a. Prima di accedere a {{site.data.keyword.ghe_short}} Dedicato per la prima volta, chiedi all'amministratore di regione della tua azienda di aggiungere il tuo ID utente alla tua istanza di {{site.data.keyword.Bluemix_notm}} Dedicato dal registro utenti della tua azienda utilizzando LDAP. Per informazioni sull'impostazione del tuo account {{site.data.keyword.ghe_short}}, vedi [Introduzione a {{site.data.keyword.ghe_long}}](/docs/services/ghededicated/index.html){: new_window}.

 b. Nella sezione Integrazioni configurabili, fai clic su **{{site.data.keyword.ghe_short}}**.    

 c. Controlla il nome predefinito per il nuovo repository {{site.data.keyword.ghe_short}}. Se necessario, modifica il nome del nuovo repository. La seguente immagine mostra un esempio di un repository clonato da un repository di esempio. Puoi utilizzare un repository esistente o nuovo. Per utilizzare un nuovo repository, puoi creare un repository vuoto, clonare un repository o biforcarne uno.
 ![Ubicazioni del repository predefinite](images/toolchain_ghe_config.png)

1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **{{site.data.keyword.ghe_short}}**.

1. Se disponi di un repository {{site.data.keyword.ghe_short}} e desideri utilizzarlo, digitane l'URL. Per il tipo di repository, fai clic su **Existing**.
1. Se desideri utilizzare un nuovo repository {{site.data.keyword.ghe_short}}, immetti un nome per il repository, l'URL per il repository che stai clonando o dividendo e seleziona il tipo di repository:

 a. Per creare un repository vuoto, fai clic su **New**.

 b. Per creare una copia di un repository, fai clic su **Clone**.

 c. Per biforcare un repository in modo che sia possibile fornire le modifiche attraverso le richieste di importazione, fai clic su **Fork**.

1. Per utilizzare GitHub Issues per la traccia del problema, seleziona la casella di spunta **Enable GitHub Issues**.
1. Fai clic su **Create Integration**.
1. Fai clic sulla scheda del repository {{site.data.keyword.ghe_short}} che desideri utilizzare. Viene aperto il repository {{site.data.keyword.ghe_short}} della tua azienda.

  Puoi utilizzare gli strumenti per la gestione del codice sorgente integrati in Eclipse Orion {{site.data.keyword.webide}} per modificare il repository {{site.data.keyword.ghe_short}} e distribuire un'applicazione dal tuo spazio di lavoro.
  {: tip}

1. Se hai abilitato Problemi GitHub, fai clic su **GitHub Issues**. Puoi utilizzare questa istanza dei problemi GitHub per la toolchain completa, anche se la toolchain contiene più repository GitHub.    

Se non hai i privilegi da amministratore per il repository a cui sei collegato, la tua integrazione è limitata perché non puoi utilizzare un webhook. I webhook sono richiesti per eseguire automaticamente una pipeline quando si esegue il push di un commit al repository. Senza un webhook, devi avviare le tue pipeline manualmente.
{: tip}


## Configurazione di GitLab
{: #gitlab}

GitLab è un servizio di hosting basato sul web per i repository Git. Puoi avere sia copie locali che remote dei tuoi repository, ciò rende più semplice la collaborazione.

Puoi configurare GitLab come una integrazione dello strumento nella tua toolchain in modo da poter gestire il codice sorgente in un repository nuovo o esistente su GitLab.com o nell'istanza di GitLab della tua azienda. Partecipa al social coding attraverso wiki, traccia dei problemi e richieste di unione.

Se stai configurando questa integrazione dello strumento mentre stai creando la toolchain, segui questi passi:

1. Se memorizzi il tuo codice sorgente in un repository GitLab, nella sezione Integrazioni configurabili, fai clic su **GitLab**. Se stai configurando questa integrazione dello strumento su {{site.data.keyword.Bluemix_notm}} Pubblico e non hai autorizzato {{site.data.keyword.Bluemix_notm}} ad accedere a GitLab, fai clic su **Autorizza** per andare al sito web GitLab. Se non disponi di una sessione GitLab attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitLab. Se disponi di una sessione GitLab attiva ma non hai immesso la tua password recentemente, ti potrebbe essere richiesto di immettere la tua password GitLab per la conferma.
1. Se utilizzi un repository sul tuo proprio server GitLab, nella sezione Integrazioni configurabili, fai clic su **Add custom server**.

 La rete deve essere in grado di accedere al server GitLab di destinazione da un ambiente {{site.data.keyword.Bluemix_notm}} Dedicato.
 {: tip}

 Immetti un titolo per il tuo server GitLab personalizzato e specifica l'URL root del server. Immetti il token di accesso personale e fai clic su **Save custom integration**.

  Se non hai un token di accesso personale, puoi crearne uno:

     a. In una qualsiasi pagina di GitLab, fai clic sull'icona del tuo profilo e seleziona **Settings**.

     b. Nella pagina Access Tokens, immetti il nome dell'applicazione per la quale vuoi creare un token di accesso personale.

     c. Facoltativo. Scegli una data di scadenza per il token di accesso.

     d. Seleziona la casella di spunta **api** per definire l'accesso per il token personale.

     e. Fai clic su **Create personal access token**.

     f. Copia il token in un'ubicazione sicura e nell'applicazione di gestione delle password. Per motivi di sicurezza, dopo aver lasciato la pagina, non potrai più visualizzare il token.

1. Rivedi le ubicazioni del repository di destinazione predefinite per i repository GitLab. Questi repository vengono clonati dai repository di esempio. Se necessario, modifica i nomi dei repository di destinazione.

Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, completa la seguente procedura:

1. Nel dashboard DevOps, nella pagina Toolchain, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.
1. Fai clic su **Add a tool**.
1. Nella sezione Integrazioni strumento, fai clic su **GitLab**.
1. Fai clic sul server GitLab server che vuoi utilizzare.
1. Se hai un repository GitLab e desideri utilizzarlo, per il tipo di repository, fai clic su **Existing** e immetti l'URL.
1. Se desideri utilizzare un nuovo repository GitLab, immetti un nome per il repository, digita l'URL per il repository che stai clonando o dividendo e seleziona il tipo di repository:

 a. Per creare un repository vuoto, fai clic su **New**.

 b. Per creare una copia di un repository GitLab, fai clic su **Clone**.

 c. Per biforcare un repository GitLab in modo che sia possibile fornire le modifiche attraverso le richieste di unione, fai clic su **Fork**.

1. Se vuoi creare un repository pubblico sul server, deseleziona la casella di spunta **Make this repository private**.
1. Se desideri utilizzare Problemi di GitLab per la traccia del problema, seleziona la casella di spunta **Enable GitLab Issues**.
1. Se desideri tracciare la distribuzione delle modifiche del codice creando tag e commenti nei commit e le etichette e i commenti sui problemi a cui fanno riferimento i commit, seleziona la casella di spunta **Track deployment of code changes**. Per ulteriori informazioni, consulta [Track where your code is deployed with toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Fai clic su **Create Integration**.
1. Fai clic sulla scheda del repository GitLab che desideri utilizzare. A seconda del repository che hai selezionato, si aprirà il sito web di GitLab o il repository GitLab della tua azienda, dove puoi visualizzare i contenuti del repository.

  Puoi utilizzare gli strumenti per la gestione del codice sorgente integrati in Eclipse Orion {{site.data.keyword.webide}} per modificare il repository GitLab e distribuire un'applicazione dal tuo spazio di lavoro.
  {: tip}

1. Se hai abilitato Problemi GitLab, fai clic su **GitLab Issues** per aprirlo. Puoi utilizzare questa istanza dei problemi GitLab per la toolchain completa, anche se la toolchain contiene più repository GitLab.    

Se non hai i privilegi Proprietario o Master per il repository a cui sei collegato, la tua integrazione è limitata perché non puoi utilizzare un webhook. I webhook sono richiesti per eseguire automaticamente una pipeline quando si esegue il push di un commit al repository. Senza un webhook, devi avviare le tue pipeline manualmente.
{: tip}

### Ulteriori informazioni su GitLab

Per ulteriori informazioni su GitLab, leggi l'[articolo su GitLab ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){: new_window} su IBM Cloud Garage Method.


## Configurazione di Jenkins
{: #jenkins}

Jenkins è uno strumento open source, basato sul server che crea e verifica il software continuamente, supportando le procedure di integrazione e fornitura continua.

Prima di creare un'integrazione dello strumento Jenkins, devi disporre di un server Jenkins.
{: tip}

Con l'integrazione dello strumento Jenkins, puoi inviare le tue notifiche del lavoro Jenkins ad altri strumenti nella tua toolchain, come Slack e PagerDuty. Per tenere traccia del codice nelle distribuzioni, puoi aggiungere i messaggi di distribuzione ai commit Git e ai problemi Git o JIRA correlati. Puoi anche visualizzare le tue distribuzioni nella pagina delle connessioni della toolchain. Puoi fornire i risultati a {{site.data.keyword.DRA_short}}, aggiungere i gate di qualità automatizzati e tracciare il tuo rischio di distribuzione.

Configura Jenkins per automatizzare la distribuzione, la verifica e la creazione continua delle tue applicazioni:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Jenkins**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Jenkins**.

1. Immetti il nome che desideri visualizzare per questa integrazione del servizio nella scheda Jenkins nella tua toolchain.
1. Immetti l'URL per il server Jenkins che desideri aprire quando fai clic sulla scheda Jenkins dalla tua toolchain.
1. Copia il webhook della toolchain generato.
1. Nel tuo server Jenkins, completa la seguente procedura:

 a. [Installa il plug-in IBM Cloud DevOps ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Installingtheplugin){: new_window}.

 b. [Configura Jenkins per la notifica delle toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Notifyingtoolchains){: new_window}.

 c. Torna alla pagina di configurazione dell'integrazione per l'integrazione dello strumento Jenkins.

1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su **Jenkins** per visualizzare il server Jenkins.  

### Ulteriori informazioni su Jenkins

Per ulteriori informazioni su Jenkins, leggi l'[articolo su Jenkins ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/deliver/tool_jenkins/){: new_window} su IBM Cloud Garage Method o segui questa esercitazione:

  * [Garantisci delle distribuzioni di qualità utilizzando la toolchain "Deployment Risk Analytics with GitHub and Jenkins" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}

## Configurazione di JIRA
{: #jira}

JIRA è uno strumento che traccia i problemi e i bug relativi al tuo software. L'integrazione dello strumento JIRA aggiorna i problemi del tuo progetto se Jenkins o {{site.data.keyword.deliverypipeline}} esegue una distribuzione. In modo che l'integrazione dello strumento JIRA tracci i tuoi problemi, devi utilizzare i commit smart JIRA nei tuoi messaggi di commit. Per ulteriori informazioni sui commit smart JIRA, consulta [Using Smart Commits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://confluence.atlassian.com/fisheye/using-smart-commits-298976812.html){: new_window}.

Configura JIRA per pianificare, tracciare e distribuire il codice di qualità:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **JIRA**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **JIRA**.

1. Se hai un progetto JIRA e desideri collegarti ad esso, per il tipo di JIRA, fai clic su **Existing**:

 a. Immetti la chiave del progetto JIRA. Puoi trovare la chiave del progetto nell'URL del progetto JIRA.

 b. Immetti l'URL dell'API di base per la tua istanza JIRA. Puoi trovare l'URL dell'API dall'intestazione della tua istanza JIRA. Fai clic sull'icona **Administration** e su **System**.

 c. Se ti stai collegando a un'istanza JIRA privata o se vuoi ricevere informazioni sulla tracciabilità da un'istanza JIRA pubblica, immetti il tuo nome utente e password JIRA.

 d. Per tracciare la distribuzione delle modifiche del codice per il progetto creando etichette e commenti per i problemi di riferimento, seleziona la casella di spunta **Track deployment of code changes**. Assicurati di utilizzare il commit smart JIRA per fare riferimento ai problemi JIRA nei tuoi commit GitHub. Se non selezioni questa opzione, l'integrazione dello strumento JIRA ignora tutti i commit.

1. Se vuoi creare un progetto JIRA, per il tipo di JIRA, fai clic su **New**:

 a. Immetti una chiave del progetto JIRA da utilizzare con il nuovo progetto. Questa chiave viene utilizzata come un identificativo univoco nell'URL del progetto.

 b. Immetti un nome per il progetto JIRA.

 c. Immetti l'URL dell'API di base per la tua istanza JIRA. Puoi trovare l'URL dell'API dall'intestazione della tua istanza JIRA. Fai clic sull'icona **Administration** e su **System**.

 d. Immetti il nome utente per il leader del progetto JIRA che desideri utilizzare per questo progetto. Per specificare qualcuno come il leader del progetto JIRA, tale persona deve avere l'autorizzazione da leader del progetto in JIRA.

 e. Immetti il nome utente amministratore per questa istanza di JIRA.

 f. Immetti la password dell'amministratore per questa istanza di JIRA.

 g. Per tracciare la distribuzione delle modifiche del codice per il progetto creando etichette e commenti per i problemi di riferimento, seleziona la casella di spunta **Track deployment of code changes**. Assicurati di utilizzare il commit smart JIRA per fare riferimento ai problemi JIRA nei tuoi commit GitHub. Se non selezioni questa opzione, l'integrazione dello strumento JIRA ignora tutti i commit.

1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su **JIRA** per visualizzare il dashboard del progetto JIRA a cui sei collegato.

### Ulteriori informazioni su JIRA

Per ulteriori informazioni su JIRA, leggi l'[articolo su JIRA ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/code/tool_jira/){: new_window} su IBM Cloud Garage Method o segui questa esercitazione:

  * [Gain insights by using the "Developer Insights and Team Dynamics with GitHub and JIRA" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain){:new_window}


## Configurazione di Nexus
{: #nexus}

Configura il gestore del repository Nexus per archiviare le risorse di build nel tuo repository (repo) Nexus:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Nexus**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Nexus**.

1. Immetti un nome per questa istanza dell'integrazione dello strumento Nexus.
1. Immetti l'URL per il repository Nexus che desideri aprire quando fai clic sulla scheda Nexus dalla tua toolchain.
1. Seleziona il tipo di repository a cui vuoi collegarti.
1. Se hai selezionato **npm registry**, completa la seguente procedura:

 a. Immetti l'indirizzo email associato al tuo registro.

 b. Immetti il token di autenticazione associato al tuo registro.

 c. Immetti l'URL per il tuo repository della release Nexus, che corrisponde al tuo registro privato nel server Nexus.

 d. Immetti l'URL per il registro Mirror o Public che utilizzi per combinare più registri npm privati e pubblici. Ad esempio, questo URL potrebbe essere l'URL del registro virtuale nel tuo server Nexus che può accedere al tuo registro privato e a una cache del registro globale npm.

1. Se hai selezionato **Maven repository**, completa la seguente procedura:

 a. Immetti l'ID utente associato al tuo repository.

 b. Immetti la password associata al tuo repository.

 c. Immetti l'URL per il tuo repository della release Nexus, che corrisponde al tuo registro privato nel server Nexus.

 d. Immetti l'URL del tuo repository delle istantanee Nexus, che corrisponde al tuo repository delle istantanee privato nel server Nexus.

 e. Immetti l'URL per il repository Mirror o Public che utilizzi per combinare più repository Maven privati e pubblici. Ad esempio, questo URL potrebbe essere l'URL del repository virtuale nel tuo server Nexus che può accedere ai tuoi repository privati e a una cache del repository centrale Maven.

1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic sulla scheda del repository Nexus che desideri utilizzare. Si apre il sito web Nexus, dove puoi visualizzare i contenuti del repository.
1. Facoltativo: se stai utilizzando una toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e desideri creare la tua applicazione utilizzando Nexus con npm, configura la tua pipeline per aggiungere un lavoro di build npm. Per istruzioni sulla configurazione del lavoro di build, consulta la sezione [Configurazione di un lavoro di build npm Nexus nella tua pipeline](#config_nexus_npm).
1. Facoltativo: se stai utilizzando una toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e desideri creare la tua applicazione utilizzando Nexus con Maven, configura la tua pipeline per aggiungere un lavoro di build Maven. Per istruzioni sulla configurazione del lavoro di build, consulta la sezione [Configurazione di un lavoro di build Nexus Maven nella tua pipeline](#config_nexus_maven).

### Configurazione di un lavoro di build npm Nexus nella tua pipeline
{: #config_nexus_npm}

Prima di configurare un lavoro di build npm nella tua pipeline, devi disporre di una pipeline funzionante che utilizzi per creare il repository SCM come input e devi configurare Nexus per la tua toolchain. Per istruzioni sulla configurazione di Nexus, vedi la sezione [Nexus](#nexus).

Configura {{site.data.keyword.deliverypipeline}} per aggiungere un lavoro di build npm:

1. Crea una fase e configura l'input per il repository SCM appropriato.
1. Nella fase, aggiungi un lavoro di build.
1. Configura il lavoro di build:
  ![npm build job](images/nexus_npm_job.png)

  a. Per il tipo di builder, seleziona **NPM Build**.

  b. Se hai configurato più istanze dell'integrazione dello strumento Nexus, immetti il nome dell'integrazione dello strumento Nexus per cui desideri configurare il lavoro di build npm.

  c. Per il tipo di integrazione dello strumento, seleziona **Nexus**.

  d. Per il comando di build, immetti i comandi per creare il tuo modulo npm o pubblicalo nel tuo registro. Questo esempio mostra i comandi per creare il modulo o per pubblicarlo.
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  **Suggerimento:** puoi trovare l'URL e le credenziali utente che hai utilizzato per collegarti al tuo registro nelle impostazioni di configurazione per l'integrazione dello strumento Nexus.

  e. Se il tuo lavoro di build viene pubblicato nel registro Nexus e il formato della versione del modulo del tuo nodo è `x.y.z-SNAPSHOT.w`, seleziona la casella di spunta **Increment snapshot module version**. Il lavoro di build aggiorna automaticamente la versione del modulo prima che venga pubblicato nel registro Nexus. Il lavoro di build seleziona l'ultima versione del modulo dal registro npm e il file `package.json` locale e incrementa la versione del modulo utilizzando semver. Il lavoro di build non fornisce le modifiche al repository SCM.

1. Fai clic su **SAVE**. Se la tua pipeline è in esecuzione, questo lavoro di build utilizza le informazioni sulla configurazione dall'integrazione dello strumento Nexus per collegarsi al tuo registro npm.

### Configurazione di un lavoro di build Maven Nexus nella tua pipeline
{: #config_nexus_maven}

Prima di configurare un lavoro di build Maven nella tua pipeline, devi disporre di una pipeline funzionante che utilizzi per creare il repository SCM come input e devi configurare Nexus per la tua toolchain. Per istruzioni sulla configurazione di Nexus, vedi la sezione [Nexus](#nexus).

Configura la {{site.data.keyword.deliverypipeline}} per aggiungere un lavoro di build Maven:

1. Crea una fase e configura l'input per il repository SCM appropriato.
1. Nella fase, aggiungi un lavoro di build.
1. Configura il lavoro di build:
  ![Maven build job](images/nexus_maven_job.png)

  a. Per il tipo di builder, seleziona **Maven Build**.

  b. Se hai configurato più istanze dell'integrazione dello strumento Nexus, immetti il nome dell'integrazione dello strumento Nexus per cui desideri configurare il lavoro di build Maven.

  c. Per il tipo di integrazione dello strumento, seleziona **Nexus**.

  d. Per il comando di build, immetti i comandi per creare il tuo modulo Maven o pubblicalo nel tuo registro delle istantanee. Questo esempio mostra i comandi per creare il modulo o per pubblicarlo.
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  Puoi trovare l'URL e le credenziali utente che hai utilizzato per collegarti al tuo registro nelle impostazioni di configurazione per l'integrazione dello strumento Nexus.
  {: tip}

1. Fai clic su **SAVE**. Se la tua pipeline è in esecuzione, questo lavoro di build utilizza le informazioni sulla configurazione dall'integrazione dello strumento Nexus per collegarsi al tuo repository Maven.

### Ulteriori informazioni su Nexus

Per ulteriori informazioni su Nexus, leggi l'[articolo su Nexus ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/deliver/tool_nexus/){: new_window} su IBM Cloud Garage Method.


## Configurazione di uno strumento personalizzato (altro strumento)
{: #othertool}

Se il tuo team utilizza uno strumento che non è incluso nell'elenco di integrazioni delle toolchain, puoi integrare uno strumento personalizzato.

Configura uno strumento personalizzato in modo che funzioni con gli altri strumenti della tua toolchain e sia disponibile per il tuo team:

1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Altro strumento**.

1. Immetti il nome dello strumento.
1. Seleziona la fase del ciclo di vita strettamente associata allo strumento. Questa selezione determina sotto quale categoria viene elencato lo strumento nella pagina di panoramica.
1. Aggiungi un URL icona. L'icona viene visualizzata nella scheda della tua integrazione dello strumento.
1. Aggiungi un URL documentazione.
1. Specifica un nome per l'istanza dello strumento. Ad esempio: My Team Tool.
1. Aggiungi un URL istanza dello strumento. Questo URL si apre se viene fatto clic sulla scheda dell'integrazione dello strumento.
1. Aggiungi una descrizione dello strumento.
1. (Avanzate) Aggiungi ulteriori proprietà come necessario. Ad esempio, elenca eventuali informazioni o attributi richiesti per integrare il tuo strumento con gli altri strumenti della toolchain.  
1. Fai clic su **Create Integration**.

### Ulteriori informazioni sullo strumento personalizzato

Per ulteriori informazioni sullo strumento personalizzato, vedi [Introducing custom tool integration for {{site.data.keyword.Bluemix_notm}} toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2016/10/custom-tool-integration-with-bluemix-toolchains/){: new_window} o segui questa esercitazione:

  * [Aggiungi una integrazione dello strumento personalizzato a una toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/add-a-custom-tool-integration-to-a-toolchain){:new_window}


## Configurazione di PagerDuty
{: #pagerduty}

PagerDuty integra i dati da più sistemi di monitoraggio in un singola vista. Quando si verifica un problema, PagerDuty si assicura che venga inviata una notifica al membro del team più adatto a risolverlo in quel momento. Se il membro del team non risponde al problema, possono essere configurate delle escalation per instradare il problema agli ingegneri secondari o ai gestori delle operazioni.

Configura PagerDuty per inviare notifiche quando si verifica un problema nella fase della pipeline in modo che puoi risolvere i problemi più velocemente e ridurre il tempo di inattività:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **PagerDuty**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **PagerDuty**.

1. Se desideri integrare PagerDuty a livello di account utilizzando una chiave API, fai clic su **Account**:

 a. Digita la chiave di accesso API per il tuo account PagerDuty. Se non disponi di un account PagerDuty, [registrane uno ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://signup.pagerduty.com/accounts/new){: new_window}. Per istruzioni su come trovare una chiave, consulta [Generating an API Key ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){: new_window}.

 b. Digita il nome del tuo servizio PagerDuty.

 c. Digita l'indirizzo email per il contatto PagerDuty primario.

 d. Digita il numero di telefono del contatto PagerDuty primario.

1. Se desideri integrare PagerDuty a livello di servizio utilizzando una chiave di integrazione, fai clic su **Service**:

 a. Immetti l'URL del servizio PagerDuty in cui vuoi pubblicare gli avvisi.

 b. Immetti la tua chiave di integrazione di PagerDuty. Puoi trovare la tua chiave o creare una chiave nella sezione Integrazioni della pagina del servizio PagerDuty.

1. Fai clic su **Create Integration**.
1. Fai clic su **PagerDuty** per andare alla pagina pagerduty.com. Puoi visualizzare gli eventi associati al servizio PagerDuty che hai specificato quando hai configurato questa integrazione dello strumento per la tua toolchain.

### Ulteriori informazioni su PagerDuty

Per ulteriori informazioni su PagerDuty, leggi l'[articolo su PagerDuty ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/manage/tool_pagerduty/){: new_window} su IBM Cloud Garage Method o segui questa esercitazione e il corso di Garage Method advocate:

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [Become a Garage Method advocate ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:new_window}


## Configurazione di Rational Team Concert
{: #rationalteamconcert}

IBM Rational Team Concert&trade; è uno strumento di collaborazione dei team che integra le attività di sviluppo, compresi la pianificazione dell'iterazione, la gestione delle modifiche, la traccia dei difetti, il controllo origine, l'automazione delle build e la creazione di report.

Configura Rational Team Concert per applicare un approccio DevOps e una fornitura continua nel tuo ambiente di sviluppo:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Rational Team Concert**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Rational Team Concert**.

1. Immetti l'URL per il server Rational Team Concert che vuoi aprire quando fai clic sulla scheda Rational Team Concert dalla tua toolchain.
1. Immetti l'ID utente che utilizzi per accedere al server Rational Team Concert.
1. Immetti la password che usi per accedere al server Rational Team Concert.
1. Se hai un'area del progetto Rational Team Concert che vuoi aggiungere alla tua toolchain, attieniti alla seguente procedura:

 a. Dall'elenco **Project Area type**, seleziona **Existing project area**.

 b. Immetti il nome dell'area progetto da aggiungere alla tua toolchain.

1. Se vuoi creare un'area progetto Rational Team Concert da aggiungere alla tua toolchain, attieniti alla seguente procedura:

 a. Dall'elenco **Project Area type**, seleziona **New project area**.

 b. Immetti un nome per la nuova area progetto da aggiungere alla tua toolchain.

 c. Immetti il nome del template del processo di Rational Team Concert da utilizzare per creare il progetto.

1. Per tenere traccia della distribuzione di modifiche del codice per il progetto creando tag e commenti sugli elementi di lavoro, seleziona la casella di spunta **Track deployment of code changes**.
1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su **Rational Team Concert** per aprire il dashboard Rational Team Concert che hai configurato.

### Ulteriori informazioni su Rational Team Concert

Per ulteriori informazioni su Rational Team Concert, leggi l'[articolo su IBM Rational Team Concert ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/think/tool_rtc/){: new_window} su IBM Cloud Garage Method.


## Configurazione di Sauce Labs
{: #saucelabs}

Sauce Labs esegue verifiche di unità funzionali. Quando una suite di verifica Sauce Labs è configurata come un lavoro di verifica nella {{site.data.keyword.deliverypipeline}}, la suite di test può eseguire verifiche sulla tua applicazione mobile o web come parte di un processo di distribuzione continua. Queste verifiche possono fornire un controllo prezioso del flusso per i tuoi progetti, che funzionano come gate per prevenire la distribuzione di codice errato.

 Questa integrazione dello strumento è disponibile solo su {{site.data.keyword.Bluemix_notm}} Pubblico.
 {: tip}

Configura Sauce Labs per eseguire verifiche funzionali automatizzate su più sistemi operativi e browser in modo che puoi emulare la modalità di utilizzo di un sito o di un'applicazione di un utente.

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Sauce Labs**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Sauce Labs**.

1. Digita il nome utente associato con il tuo account Sauce Labs. Puoi [trovare il tuo nome utente nel messaggio di benvenuto all'inizio della tua pagina account Sauce Labs ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://saucelabs.com/account){: new_window}.
1. Digita la chiave di accesso per il tuo account Sauce Labs. Puoi [trovare la chiave nella tua pagina account Sauce Labs ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://saucelabs.com/account){: new_window}.
1. Fai clic su **Create Integration**.
1. Fai clic su **Sauce Labs** per andare alla pagina saucelabs.com e visualizzare l'attività di verifica per la toolchain.

 Se hai aggiunto un lavoro di verifica Sauce Labs alla {{site.data.keyword.deliverypipeline}}, puoi selezionare l'istanza del servizio. Per istruzioni sulla configurazione di un lavoro di verifica nella tua pipeline, consulta la sezione [Configurazione di un lavoro di verifica Sauce Labs nella tua pipeline](#config_saucelabs).
 {: tip}

### Ulteriori informazioni su Sauce Labs

Per ulteriori informazioni su Sauce Labs, consulta l'[articolo su Sauce Labs ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/deliver/tool_sauce_labs/){: new_window} in IBM Cloud Garage Method o seguenti questa esercitazione:

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}



## Configurazione di Slack
{: #slack}

Le notifiche che vengono pubblicate nei canali Slack pubblici sono visibili a tutti i membri del team. Ricorda che sei responsabile del contenuto che pubblichi.
{: tip}

Slack è un sistema di notifica e messaggistica in tempo reale basato sul cloud. Slack fornisce chat persistente, che è un'alternativa più interattiva alla email per la collaborazione del team. Puoi comunicare con il tuo team su un canale dedicato o su una serie di canali direttamente correlati al tuo lavoro. Puoi inoltre condividere file e immagini tramite i canali o con messaggi diretti tra due o più persone. Le comunicazioni nei messaggi diretti e sui canali vengono conservate in modo che puoi ricercarle.

Configura Slack per ricevere notifiche sulla tua toolchain dalle integrazioni delle strumento, come ad esempio le attività di distribuzione e verifica:

1. Se stai configurando questa integrazione dello strumento mentre crei la toolchain, nella sezione Integrazioni configurabili, fai clic su **Slack**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **Slack**.

1. Immetti l'URL webhook Slack, che viene generato da Slack come un webhook in entrata. Hai bisogno di un URL webhook Slack per ricevere notifiche sulla tua toolchain dalle integrazioni delle strumento. Per istruzioni su come creare o trovare il tuo webhook, consulta [Incoming Webhooks ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://api.slack.com/incoming-webhooks){: new_window}.

 Se hai utilizzato una chiave API per il tuo canale Slack per ricevere notifiche relative alla tua toolchain dalle integrazioni dello strumento, devi aggiornare la tua configurazione per utilizzare invece un webhook.
 {: tip}

1. Digita il nome del canale Slack a cui desideri vengano inviate le notifiche. Il canale deve esistere ed essere attivo nel tuo team Slack.
1. Immetti il nome host dell'URL del tuo team Slack, che corrisponde alla parola o alla frase prima di `.slack.com` nel tuo URL del team. Ad esempio, se il tuo URL del team è `https://team.slack.com`, il nome host è `team`.
1. Fai clic su **Create Integration**.

 Se il team e il canale Slack che hai specificato non possono essere raggiunti, viene visualizzato l'errore `Setup Failed` nella scheda Slack. Passa con il mouse sul messaggio `Setup Failed` e fai clic su **Reconfigure**. Assicurati di stare utilizzando dei parametri di configurazione validi per l'URL del webhook Slack, il canale Slack e il nome host dell'URL per il tuo team Slack. Aggiorna le impostazioni come richiesto e fai clic su **Save Integration**.
 {: tip}

1. Fai clic su **Slack**. Puoi visualizzare tutte le attività per la tua toolchain nel canale Slack configurato.

### Ulteriori informazioni su Slack

Per ulteriori informazioni su Slack, consulta l'[articolo su Slack ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/culture/tool_slack/){: new_window} in IBM Cloud Garage Method oppure esegui questa esercitazione e il corso di Garage Method Advocate:

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [Become a Garage Method advocate ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:new_window}


## Configurazione di SonarQube
{: #sonarqube}

SonarQube fornisce una panoramica dello stato generale e della qualità del codice sorgente ed evidenzia i problemi riscontrati nel nuovo codice. I programmi di analisi del codice rilevano errori complessi, come ad esempio dereferenziazioni di puntatori null, errori di logica e perdita di risorse, per più di 20 linguaggi di codifica.

Configura SonarQube per analizzare e misurare continuamente la qualità del tuo codice sorgente:

1. Dal dashboard DevOps, fai clic su **Toolchains**. Fai clic sulla toolchain a cui desideri aggiungere SonarQube. In alternativa, nella pagina della panoramica della tua applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.  

 a. Fai clic su **Add a Tool**.

 b. Nella sezione Integrazioni strumento, fai clic su **SonarQube**.

1. Immetti un nome per questa istanza dell'integrazione dello strumento SonarQube.
1. Immetti l'URL per l'istanza SonarQube che desideri aprire quando fai clic sulla scheda SonarQube dalla tua toolchain.
1. Facoltativo: immetti il nome utente che utilizzi per connetterti al server SonarQube.

 Devi specificare un nome utente solo se utilizzi una password per connetterti al server SonarQube. Se per la connessione utilizzi un token di autenticazione, lascia vuoto questo campo.
 {: tip}

1. Immetti la password o il token di autenticazione che utilizzi per connetterti al server SonarQube.
1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su **SonarQube** per visualizzare il dashboard dell'istanza SonarQube a cui sei connesso.

### Ulteriori informazioni su SonarQube

Per ulteriori informazioni su SonarQube, leggi l'[articolo su SonarQube ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/content/learn/tool_sonarqube/){: new_window} su IBM Cloud Garage Method.
