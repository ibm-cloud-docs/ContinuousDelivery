---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Risoluzione dei problemi per {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

I problemi generali con l'utilizzo di {{site.data.keyword.contdelivery_full}} possono includere l'autenticazione GitHub, la creazione di pipeline, la configurazione dell'integrazione dello strumento o i problemi di Cloud Foundry. In molti casi, puoi risolvere questi problemi seguendo pochi semplici passi.
{:shortdesc}

## Ho provato ad aggiungere l'integrazione dello strumento GitHub alla mia toolchain, perché l'integrazione dello strumento non è stata aggiunta?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

Devi eseguire l'autorizzazione presso GitHub in modo che {{site.data.keyword.Bluemix_notm}} sia autorizzato ad accedere al tuo account GitHub.

L'integrazione dello strumento GitHub non è stata aggiunta alla tua toolchain.
{: tsSymptoms}

Se {{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere al tuo account GitHub, l'integrazione dello strumento non viene aggiunta alla tua toolchain.
{: tsCauses}

Se stai configurando l'integrazione dello strumento GitHub mentre stai creando la tua toolchain, attieniti alla seguente procedura per eseguire l'autorizzazione presso GitHub:
{: tsResolve}

  1. Nella sezione delle integrazioni configurabili, fai clic su **GitHub**.
  1. Se stai creando la toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e {{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere a GitHub, fai clic su **Authorize** per andare al sito web GitHub.
  1. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub.

Se già disponi di una toolchain, aggiorna la configurazione dell'integrazione dello strumento GitHub:

 1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
 1. Nella scheda GitHub, fai clic sul menu e su **Configure**.
 1. Aggiorna le impostazioni di configurazione per autorizzare {{site.data.keyword.Bluemix_notm}} ad accedere a GitHub. Fai clic su **Authorize** per andare al sito web GitHub. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub.
 1. Quando hai terminato di aggiornare le impostazioni, fai clic su **Save Integration**.
 

## Perché non posso utilizzare l'integrazione dello strumento {{site.data.keyword.gitrepos}} nella mia toolchain da una regione in una toolchain in una regione differente?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

Non puoi utilizzare un'istanza di {{site.data.keyword.gitrepos}} in più regioni.

Quando provo ad aggiungere l'integrazione dello strumento {{site.data.keyword.gitrepos}}, ricevo il seguente messaggio di errore:
{: tsSymptoms}

`Repository URL is not valid. The repository must be on {local GitLab URL}.`

Dove `{local GitLab URL}` è l'URL dell'integrazione dello strumento {{site.data.keyword.gitrepos}} nella regione dove si trova la toolchain.
   
Poiché {{site.data.keyword.gitrepos}} è strettamente integrato con il servizio {{site.data.keyword.contdelivery_short}} nella regione in cui sono in esecuzione, non puoi utilizzare un'istanza di {{site.data.keyword.gitrepos}} in più regioni.
{: tsCauses}

Invece di creare un'integrazione dello strumento {{site.data.keyword.gitrepos}}, crea un'integrazione GitLab generica e utilizza questa integrazione per puntare al repository {{site.data.keyword.gitrepos}} (repo) in una regione diversa.
{: tsResolve}

1. Nel dashboard DevOps, nella pagina Toolchains, fai clic sulla toolchain a cui desideri aggiungere questa integrazione. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.
1. Fai clic su **Add a tool**.
1. Nella sezione Integrazioni strumento, fai clic su **GitLab**.
1. Fai clic sul server GitLab server che vuoi utilizzare. Se il server GitLab in cui risiede il repository a cui desideri accedere non è visualizzato in questo elenco, aggiungi un server personalizzato:

 a. Fai clic su **Add custom server**.

 b. Immetti un nome per il server. Questo nome server sarà visualizzato nell'elenco dei server GitLab disponibili.
 
 c. Immetti l'URL root del server GitLab personalizzato.
 
 d. Immetti un token di accesso personale per il tuo server GitLab personalizzato. Se non hai un token di accesso personale, [creane uno](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat).
 
 e. Fai clic su **Save custom integration**.
 
1. Se hai un repository GitLab e desideri utilizzarlo, per il tipo di repository, fai clic su **Existing** e immetti l'URL.
1. Se desideri utilizzare un nuovo repository GitLab, immetti un nome per il repository, digita l'URL per il repository che stai clonando o dividendo e seleziona il tipo di repository:

 a. Per creare un repository vuoto, fai clic su **New**.

 b. Per creare una copia di un repository GitLab, fai clic su **Clone**.

 c. Per biforcare un repository GitLab in modo che sia possibile fornire le modifiche attraverso le richieste di unione, fai clic su **Fork**.

1. Se vuoi creare un repository pubblico sul server, deseleziona la casella di spunta **Make this repository private**.
1. Se desideri utilizzare Problemi di GitLab per la traccia del problema, seleziona la casella di spunta **Enable GitLab Issues**.
1. Se desideri tracciare la distribuzione delle modifiche del codice creando tag e commenti nei commit e le etichette e i commenti sui problemi a cui fanno riferimento i commit, seleziona la casella di spunta **Track deployment of code changes**. Per ulteriori informazioni, vedi [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Fai clic su **Create Integration**.

Per ulteriori informazioni sulla configurazione di un'integrazione dello strumento GitLab, vedi [Configurazione di GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab).


## Perché non posso creare una toolchain da un template che utilizza un repository privato in una regione diversa?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

Il template della toolchain che stai utilizzando fa riferimento a un repository {{site.data.keyword.gitrepos}} privato.

{{site.data.keyword.gitrepos}} è specifico per la regione. Quando provi a creare una toolchain da un template e indichi come destinazione una regione in cui non è presente il repository privato, l'impostazione dell'integrazione Git non riesce.
{: tsSymptoms}
   
Quando aggiungi un repository {{site.data.keyword.gitrepos}} a una toolchain in una specifica regione, il tuo ID IBM viene associato a un nome utente GitLab che ti dà accesso a GitLab in tale regione. Anche se il tuo nome utente GitLib si presenta uguale in tutte le regioni, l'utente GitLab associato è diverso in ciascuna regione perché ognuna ha un'installazione separata di GitLab. L'accesso agli utenti GitLab in altre regioni non viene concesso automaticamente alle toolchain anche quando il nome utente GitLab sembra essere lo stesso.
{: tsCauses}

Rendi pubblico il repository {{site.data.keyword.gitrepos}} in modo che sia possibile accedere ad esso da qualsiasi posizione, comprese altre regioni {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Se il repository deve essere privato, il suo proprietario può concedere l'accesso a esso creando un [token di accesso personale](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) sul server GitLab dove si trova il repository di origine. Hai bisogno dell'accesso solo al repository privato per clonare il contenuto durante la creazione della toolchain. Il token di accesso personale può essere creato con una data di scadenza per limitarne la durata a una scadenza dopo un giorno. 

Una volta che disponi di un token di accesso personale, puoi creare un URL per accedere al repository da altre regioni. Mentre stai configurando l'integrazione dello strumento, nel campo **Source repository URL** aggiorna l'URL del repository per utilizzare i tuoi nome utente e token di accesso.

`https://user:XXXXXXX@us-south.git.cloud.ibm.com/group/node-hello-world`

Dove `user` è il tuo nome utente GitLab, `XXXXXXX` è il token di accesso, [`group`](https://us-south.git.cloud.ibm.com/help/user/group/index.md){: external} è il gruppo dove è archiviato il repository e `node-hello-world` è il nome del repository.

Se il tuo repository GitLab non si trova all'interno di un gruppo GitLab, il valore di `group` è uguale al tuo nome utente.
{: tip}


## Perché non posso clonare il mio repository {{site.data.keyword.gitrepos}} su https?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Devi utilizzare un token di accesso personale o una chiave SSH per eseguire le operazioni Git.

Provi ad eseguire il push o la clonazione di un repository dalla riga di comando utilizzando https e non riesci ad eseguire l'autenticazione anche se hai immesso la password corretta.
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} utilizza un meccanismo SSO (single sign-on) che non supporta l'autenticazione Git che utilizza un nome utente e una password sulla riga di comando.
{: tsCauses}

Per eseguire operazioni Git come clonazione o push, devi utilizzare un token di accesso personale o una chiave SSH. Per ulteriori informazioni sulla creazione di un token di accesso personale o di una chiave SSH, vedi l'[Esercitazione introduttiva](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## Perché mi viene richiesto di eseguire l'autenticazione quando provo a clonare il mio repository {{site.data.keyword.gitrepos}} utilizzando SSH?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

Ci potrebbero essere dei problemi con l'ubicazione o con le autorizzazioni per la tua chiave SSH privata oppure è possibile che la riga di comando Git non stia utilizzando la tua chiave SSH privata per eseguire l'autenticazione presso {{site.data.keyword.gitrepos}}.

Ho aggiunto la mia chiave pubblica SSH mediante l'interfaccia utente {{site.data.keyword.gitrepos}}. Quando provo a clonare un repository utilizzando SSH, mi vengono richiesti una password o un codice di sicurezza oppure viene visualizzato un messaggio di errore che indica che l'autenticazione non è riuscita.
{: tsSymptoms}
   
Uno qualsiasi dei seguenti problemi SSH potrebbe richiederti di eseguire l'autenticazione o potrebbe visualizzare un messaggio di errore.
{: tsCauses}

* È possibile che la riga di comando Git non stia utilizzando la tua chiave SSH privata per eseguire l'autenticazione presso {{site.data.keyword.gitrepos}}.

* La tua chiave SSH privata potrebbe non essere nell'ubicazione ~/.ssh/id_rsa predefinita.

* La tua chiave SSH privata potrebbe non disporre delle autorizzazioni corrette (600).


Utilizza uno qualsiasi dei seguenti metodi per risolvere questo problema:
{: tsResolve}

* Se utilizzi l'ubicazione di chiave SSH privata predefinita, verifica le autorizzazioni per la cartella ~/.ssh/ e il file di chiave privata ~/.ssh/id_rsa. Se le autorizzazioni sono troppo ampie, per impostazione predefinita SSH non utilizza una chiave privata. Assicurati che le autorizzazioni per la cartella  ~/.ssh/ siano impostate su 700 e che le autorizzazioni per la cartella ~/.ssh/id_rsa siano impostate su 600.

* Se la tua chiave privata non si trova nell'ubicazione predefinita, utilizza il seguente comando per specificarla in una variabile di ambiente:

```
  GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git
```

* Per eseguire il debug di questo problema utilizzando le informazioni di connessione, aggiungi l'indicatore -v o -vvv alla variabile di ambiente `GIT_SSH_COMMAND`:

```
  GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git
```
```
  GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git
```


## Ho provato ad aggiungere un utente al mio progetto GitLab via email ma non ha ricevuto l'invito. Come lo aggiungo al mio progetto?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

L'invito potrebbe essere bloccato dall'email dell'utente.

Ho invitato un utente al mio progetto GitLab utilizzando il suo indirizzo email che è elencato in {{site.data.keyword.gitrepos}} ma non ha ricevuto l'email.
{: tsSymptoms}
   
È possibile che i filtri contro la posta indesiderata (spam) non consentano all'email di essere ricevuta nella casella di posta in arrivo. 
{: tsCauses}

Per risolvere il problema, puoi utilizzare uno dei seguenti metodi:
{: tsResolve}

* Controlla la tua cartella di posta indesiderata della email per determinare se l'invito via email è stato contrassegnato come posta indesiderata (spam). Le email sono inviate da un indirizzo noreply@. Aggiorna i tuoi filtri contro la posta indesiderata per consentire le email da questo indirizzo.

* Appura se i filtri contro la posta indesiderata aziendali fuori dal controllo dell'utente stanno bloccando l'email. Chiedi all'utente di accedere all'interfaccia utente {{site.data.keyword.gitrepos}} e di inviarti il suo ID utente. Puoi aggiungere l'utente al progetto GitLab utilizzando il suo ID utente.


## Perché la pipeline non viene creata correttamente quando creo una toolchain dal template che sto scrivendo? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

Alla tua pipeline potrebbero mancare risorse quali i lavori e le fasi a causa di un errore nella tua definizione pipeline.yaml.

Quando provo a creare una toolchain da un template che sto scrivendo, ricevo il seguente messaggio di errore nella pagina Pipeline.
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

Di norma, questo problema è causato da un errore nella tua definizione pipeline.yaml.
{: tsCauses}
   
Puoi utilizzare uno qualsiasi dei seguenti metodi per eseguire il debug di questo errore:
{: tsResolve}

* Utilizza l'interfaccia utente della pipeline per creare una pipeline di esempio che replica la pipeline che stai provando a creare con il tuo template. Accoda `/yaml` all'URL della pipeline per generare un file pipeline.yaml simile che puoi utilizzare per cercare le ovvie differenze. Ad esempio, `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`.

* Utilizza il meccanismo di creazione della toolchain headless. Nella pagina **Create a Toolchain**, apri il programma di debug e valuta l'espressione `window.Testflags = {nocreate: 1}`. Quando fai clic su **Create a Toolchain** in questa modalità, la toolchain non viene creata. Invece, le informazioni che vengono passate all'API vengono restituite alla console dove puoi esaminarle.


## Ho provato a eseguire la distribuzione a Kubernetes utilizzando il Delivery Pipeline, perché sto ottenendo un errore relativo a un oggetto non valido? 
{: troubleshoot-cd-pipeline-kubernetes}
{: troubleshoot}

L'immagine di base della pipeline 1.0 include kubectl v1.14.2. Potresti ricevere un errore se il cluster Kubernetes a cui ti stai connettendo sta eseguendo una versione più recente di Kubernetes. 

Quando provo ad eseguire la distribuzione a Kubernetes utilizzando la Delivery Pipeline, ricevo il seguente messaggio di errore:
{: tsSymptoms}

`error:SchemaeError(io.k8s.api.core.v1.SecretProjection): invalid object doesn't have additional properties`

Di norma, questo problema si verifica quando la versione del comando kubectl nella tua immagine di base della pipeline non è compatibile con la versione di Kubernetes in esecuzione nel cluster.
{: tsCauses}
   
Per risolvere il problema, puoi utilizzare uno dei seguenti metodi:
{: tsResolve}

* Utilizza una versione dell'immagine di base della pipeline più recente che, quando creata, includa la versione attualmente rilasciata dikubectl. Per informazioni su come specificare la versione dell'immagine più recente, vedi [Specifica della versione dell'immagine](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline_versioned_base_images#specify_base_image_version).

* Assicurati che il tuo lavoro della pipeline stia eseguendo la versione corretta di kubectl. Ad esempio, aggiungi le seguenti righe all'inizio del tuo lavoro della pipeline per eseguire kubectl v1.14.2:

```
  curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.14.2/bin/linux/amd64/kubectl
  chmod +x ./kubectl
  sudo mv ./kubectl /usr/local/bin/kubectl
```

Se stai eseguendo kubectl v1.14.2 da un'immagine di base della pipeline 1.0, l'opzione sudo non è disponibile. Sostituisci la riga sudo con il seguente comando per aggiungere kubectl al tuo percorso:
```
   mkdir ~/.bin && export PATH=~/.bin:$PATH && mv ./kubectl ~/.bin/kubectl
```

Per ulteriori informazioni sull'accesso all'esatta versione di kubectl di cui hai bisogno, vedi [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux){: external}.
{: tip}


## Ho configurato un'integrazione dello strumento per la mia toolchain, perché non è stata configurata?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

Se si verifica un errore durante il processo di impostazione o se le comunicazioni tra la toolchain e lo strumento non si completano correttamente, la configurazione non riesce.

Dopo che hai aggiunto e configurato un'integrazione dello strumento per la tua toolchain, viene visualizzato un messaggio di errore per indicare che l'impostazione non è riuscita.
{: tsSymptoms}

Quando aggiungi un'integrazione dello strumento, la toolchain comunica con lo strumento rappresentato dall'integrazione dello strumento per eseguire il provisioning di tutte le risorse e le associa alla toolchain. Se si verifica un errore nel processo di configurazione o se la comunicazione tra la toolchain e lo strumento non viene completata correttamente, l'integrazione dello strumento viene messa in uno stato di errore.
{: tsCauses}

 ![Errore configurazione non riuscita](images/tool_setup_failed.png)

Puoi provare a configurare nuovamente l'integrazione dello strumento:
{: tsResolve}

1. Nella relativa scheda, passa con il mouse sul messaggio `Setup failed` e fai clic su **Reconfigure**.

 ![Pulsante riconfigura](images/tool_reconfigure.png)

1. Assicurati di stare utilizzando dei parametri di configurazione validi. Se l'errore è stato causato da una configurazione non valida, viene visualizzato un messaggio di errore; ad esempio, `Impossibile configurare l'integrazione. Controlla le impostazione e riprova. Motivo: Invalid api_key:fakeKey`. Aggiorna le impostazioni per l'integrazione dello strumento e fai clic su **Save integration**.
1. Se l'errore è stato causato da un problema di comunicazione, fai clic su **Save integration** per ritentare.


## Perché non possono aggiungere {{site.data.keyword.contdelivery_short}} a un'organizzazione Cloud Foundry?
{: troubleshoot-resource_groups}
{: troubleshoot}

Non puoi più creare istanze del servizio {{site.data.keyword.contdelivery_short}} nelle organizzazioni Cloud Foundry. 

Il seguente messaggio viene visualizzato nella pagina Toolchains per la tua toolchain in un'organizzazione Cloud Foundry:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

Quando fai clic su **Add the service**, non è disponibile alcuna opzione per creare {{site.data.keyword.contdelivery_short}} in un'organizzazione Cloud Foundry. Puoi solo creare {{site.data.keyword.contdelivery_short}} in un gruppo di risorse.

I gruppi di risorse hanno sostituito le organizzazioni Cloud Foundry come contenitori preferiti per le istanze del servizio. Tuttavia, puoi ancora creare le toolchain nelle organizzazioni Cloud Foundry per supportare le istanze {{site.data.keyword.contdelivery_short}} pre-esistenti nelle organizzazioni Cloud Foundry.
{: tsCauses}

Crea nuovamente la tua toolchain nei gruppi di risorse e quindi rimuovi la toolchain originale dall'organizzazione Cloud Foundry. In alternativa, puoi ignorare il messaggio di errore finché non viene fornito un metodo per migrare le toolchain esistenti dalle organizzazioni Cloud Foundry ai gruppi di risorse.
{: tsResolve}


## Perché non posso eliminare le toolchain utilizzando la CLI `ibmcloud`?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

Attualmente, non riesco a eliminare le toolchain utilizzando la CLI delle risorse di ibmcloud. 

Ho provato a eliminare una toolchain dalla riga di comando utilizzando il comando `ibmcloud resource service-instance-delete` e il comando non riesce con il seguente messaggio di errore:
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

Le toolchain sono un tipo speciale di risorsa sulla piattaforma cloud che attualmente non puoi eliminare utilizzando la CLI `ibmcloud resource`.
{: tsCauses}

Per eliminare una toolchain:
{: tsResolve}

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain da eliminare. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**.
1. Fai clic sul menu **More Actions**, accanto a **View app**.
1. Fai clic su **Delete**. L'eliminazione di una toolchain rimuove tutte le sue integrazioni dello strumento e ciò potrebbe eliminare le risorse gestite da tali integrazioni.
1. Conferma l'eliminazione digitando il nome della toolchain e facendo clic su **Delete**.  


## Perché Live Edit non è disponibile dopo che eseguo il commit e il push a un repository?
{: #troubleshoot-liveedit}
{: troubleshoot}

Quando esegui distribuzioni al di fuori di Eclipse Orion {{site.data.keyword.webide}}, la modalità Live Edit viene annullata.

Esegui il commit e il push di una modifica dalla riga di comando o da {{site.data.keyword.webide}} e Live Edit non è disponibile.
{: tsSymptoms}
   
Quando crei una toolchain che contiene sia una pipeline {{site.data.keyword.contdelivery_short}} che {{site.data.keyword.webide}}, entrambe le integrazioni dello strumento possono distribuire la tua applicazione (app). Per impostazione predefinita, sia la pipeline che {{site.data.keyword.webide}} eseguono la distribuzione alla stessa organizzazione e allo stesso spazio Cloud Foundry utilizzando la stessa applicazione e lo stesso URL Cloud Foundry. Quando esegui una distribuzione all'esterno di {{site.data.keyword.webide}}, la modalità Live Edit viene annullata.
{: tsCauses}

Per sviluppare rapidamente una versione di test della tua applicazione utilizzando Live Edit, esegui la distribuzione a un'applicazione, uno spazio e un URL Cloud Foundry differenti da {{site.data.keyword.webide}}. Una volta completate le tue modifiche del codice, puoi eseguire il commit e il push del codice per attivare la pipeline per creare e distribuire la versione di produzione della tua applicazione.
{: tsResolve}

1. Dalla barra di esecuzione, seleziona la configurazione di avvio che desideri modificare.
2. Modifica i valori specificati per Space e Host.
3. Fai clic su **Save** ed **Exit**.
4. Fai clic sul pulsante **Run** nella barra di esecuzione. Potresti dover eseguire la distribuzione più volte per abilitare il pulsante Live Edit.

Per ulteriori informazioni su Live Edit, vedi [Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit).


## Che significa "not synchronized" nella barra di esecuzione di {{site.data.keyword.webide}}?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

Il file system nel tuo spazio di lavoro non è sincronizzato.

In modalità Live Edit, {{site.data.keyword.webide}} sincronizza i file dal tuo spazio di lavoro con l'applicazione Cloud Foundry in esecuzione e i file non sono sincronizzati.
{: tsSymptoms}
   
Il file system nel tuo spazio di lavoro potrebbe diventare non sincronizzato se l'applicazione viene modificata fuori da {{site.data.keyword.webide}}. Può anche diventare non sincronizzata se {{site.data.keyword.webide}} non è in grado di richiamare lo stato di sincronizzazione dall'applicazione.
{: tsCauses}

Lo stato potrebbe essere annullato dopo un minuto o due, quando le normali comunicazioni vengono ristabilite e i file vengono sincronizzati. Altrimenti, puoi avviare e arrestare l'applicazione con la modalità Live Edit abilitata.
{: tsResolve}
