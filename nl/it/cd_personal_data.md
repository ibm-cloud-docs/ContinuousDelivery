---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: IBM Cloud account, personal data, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Gestione dei dati personali in Continuous Delivery
{: #cd_personal_data}

Puoi modificare, esportare, o eliminare i dati personali da {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

I dati personali sono le informazioni correlate a una persona fisica o che la identificano. Ad esempio, i dati personali possono essere un nome, un indirizzo email, un avatar, un token o qualsiasi numero di identificativi utilizzati con {{site.data.keyword.contdelivery_short}}. I seguenti componenti {{site.data.keyword.contdelivery_short}} contengono dati personali:

 * Eclipse Orion {{site.data.keyword.webide}}
 * {{site.data.keyword.gitrepos}}
 * Pipeline {{site.data.keyword.contdelivery_short}}
 * Toolchain e integrazioni dello strumento
 * [GitHub Enterprise su IBM Cloud ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/ghededicated?topic=ghededicated-ghe_personal_data){: new_window}
 * [{{site.data.keyword.DRA_full}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/DevOpsInsights?topic=DevOpsInsights-deleting_data){: new_window}
 
IBM non gestisce i dati nel servizio {{site.data.keyword.contdelivery_short}}. Prima di uscire dal servizio {{site.data.keyword.contdelivery_short}} che si trova in {{site.data.keyword.Bluemix_notm}} Pubblico, devi eliminare i tuoi dati.
{: important}

{{site.data.keyword.contdelivery_short}} fornisce le autorizzazioni appropriate per gestire i dati all'interno di un'organizzazione Cloud Foundry o di un gruppo di risorse. La tua azienda potrebbe avere delle politiche che limitano queste autorizzazioni. Se non disponi delle le autorizzazioni appropriate, contatta l'amministratore del tuo account {{site.data.keyword.Bluemix_notm}}.

Per gestire i tuoi dati personali, devi comprendere gli account IBM Cloud, in che modo questi account vengono utilizzati e i loro diritti di accesso associati.
 
## Account e diritti di accesso
{: #accounts_access_rights}

Per lavorare in IBM Cloud, devi eseguire l'accesso con un nome utente e password. Quando esegui l'accesso, IBM Cloud associa almeno un account IBM Cloud alle tue credenziali utente. Quando crei risorse, quali le organizzazioni Cloud Foundry, gruppi di risorse, toolchain e gli oggetti {{site.data.keyword.contdelivery_short}}, esse vengono associate a un account IBM Cloud.

La struttura di accesso di IBM Cloud ti offre l'opzione di lavorare in account differenti. Utilizzando l'interfaccia utente di IBM Cloud, puoi passare da un account all'altro. Quando esegui l'accesso, uno qualsiasi dei seguenti tipi di account potrebbe essere associato alle tue credenziali utente: 

 * Account personale
 * Account aziendale
 * Account individuale aziendale

###Account personali

Di norma, ciascun utente ha un suo account che è il suo account personale. Puoi identificare facilmente il tuo account personale perché di solito contiene il tuo nome, ad esempio *Account di John Smith*. 

Hai pieni diritti su tutti gli oggetti creati nel tuo account personale. Puoi invitare altri utenti a unirsi al tuo account, assegnare loro diritti sugli oggetti da te creati e assegnare loro i diritti per creare oggetti nel tuo account. Questo significa che i dati personali di altri utenti potrebbero essere presenti nel tuo account e i tuoi dati personali potrebbero essere presenti negli account di altri utenti. 

Se hai l'autorizzazione a creare un oggetto in un account, hai anche il diritto a modificarlo ed eliminarlo, indipendentemente dall'account in cui l'oggetto è archiviato. Quando collaborano, due utenti spesso condividono un account personale.

###Account aziendali

Un account aziendale è configurato dalla tua azienda. Di norma, vieni aggiunto automaticamente all'account, piuttosto che essere invitato. Gli account aziendali forniscono agli utenti un posto per lavorare, comunicare e condividere risorse e addebito; tuttavia, questa è solo una convenzione. Un account aziendale in realtà non è diverso da un account personale. Gli oggetti creati in un account aziendale sono associati all'account e gli utenti possono essere invitati all'account.

I team di persone che lavorano per un'azienda spesso collaborano utilizzando un account aziendale.

###Account individuali aziendali

Quando lavori per una società, il lavoro nel tuo account potrebbe appartenere, da un punto di vista legale, alla società stessa. Molti utenti che lavorano per una società hanno un account individuale aziendale. Se esegui l'accesso al tuo account utilizzando delle credenziali che contengono il nome della tua società e anche quello che sembra essere un account personale, il lavoro nel tuo account personale potrebbe appartenere alla società in questione.

Un account individuale aziendale non è diverso da qualsiasi altro account. Puoi invitare gli utenti a un account individuale aziendale e gli oggetti creati in un account individuale aziendale appartengono all'account.

Se lavori per una società che è proprietaria del tuo lavoro, un account personale che di norma contiene il tuo nome è considerato un account individuale aziendale. 

## Modifica, esportazione ed eliminazione di dati personali
{: #managing_personal_data}

Indipendentemente dal tipo di account IBM Cloud account utilizzato, se disponi dei diritti agli oggetti nell'account, puoi modificarli, esportarli ed eliminarli. Prima di apportare modifiche, coordinati con gli altri utenti per assicurarti di non modificare o eliminare dei dati senza che sia necessario.

Prima di eliminare dati da un account, determina se si tratta di un account personale o di un account individuale aziendale.

###Account personale

Se sei il proprietario di un account personale, puoi apportare modifiche ed eliminare i tuoi dati. Se condividi il tuo account con un altro utente, tu sei il proprietario dei dati ma sarebbe opportuno che tu contattassi tale utente in merito al lavoro condiviso. 

Se non riesci ad accedere al tuo account IBM Cloud, [contatta il supporto IBM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/support){:new_window}
 
###Account individuale aziendale

Se sei il proprietario di un account individuale aziendale, devi coordinare eventuali modifiche sia con la tua società che con gli altri membri del tuo team. Elimina i tuoi dati personali indipendentemente dal fatto che siano archiviati in un account aziendale o in un account individuale aziendale. Assicurati di non eliminare del lavoro che hai condiviso con altri utenti.

Prima di iniziare a gestire i tuoi dati personali per i componenti {{site.data.keyword.contdelivery_short}}, assicurati che stai lavorando nel tuo account IBM Cloud. Per visualizzare l'account IBM Cloud in cui stai lavorando al momento, nella barra dei menu fai clic sull'avatar del profilo. 

Se non riesci ad eseguire l'accesso al tuo account IBM Cloud, contatta la tua società e collaborate per eliminare i tuoi dati personali.

Se vuoi eliminare tutti i dati personali da {{site.data.keyword.contdelivery_short}}, l'ordine in cui elimini tali dati è importante. Elimina prima tutti i tuoi spazi di lavoro {{site.data.keyword.webide}}. Elimina quindi i tuoi dati {{site.data.keyword.gitrepos}} ed elimina quindi il tuo account {{site.data.keyword.gitrepos}}. Infine, elimina le tue delivery pipeline, integrazioni degli strumenti e toolchain.
{: tip}

## Esportazione ed eliminazione di dati Web IDE
{: #managing_web_ide_data}

{{site.data.keyword.webide}} fornisce uno spazio di lavoro personale nel cloud. Puoi utilizzare {{site.data.keyword.webide}} per clonare repository Git e modificare file. Sei il proprietario del tuo spazio di lavoro {{site.data.keyword.webide}}; non è condiviso da altri account.

Prima di eliminare i tuoi dati {{site.data.keyword.webide}}, sarebbe opportuno esportare il tuo lavoro. Dopo che li hai eliminati, i tuoi spazi di lavoro vengono rimossi da {{site.data.keyword.contdelivery_short}} e vengono eliminati tutti i file.
{: important}

###Esportazione di uno spazio di lavoro Web IDE

Per esportare uno spazio di lavoro {{site.data.keyword.webide}}:

1. Seleziona **File > Esporta > Zip**.
1. Ripeti per ogni spazio di lavoro che vuoi esportare.

###Eliminazione dei tuoi spazi di lavoro Web IDE

Per eliminare i tuoi spazi di lavoro {{site.data.keyword.webide}}, compresi tutti i tuoi dati personali:

1. Da qualsiasi toolchain, passa a {{site.data.keyword.webide}}.
1. Fai clic sull'icona **Settings** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Icona delle impostazioni"> nella barra laterale di navigazione sulla sinistra.
1. Fai clic su **USER PROFILE**.
1. Fai clic su **Delete** per rimuovere tutti i tuoi dati da {{site.data.keyword.webide}}.

{{site.data.keyword.webide}} utilizza un meccanismo SSO (single sign-on). La prima volta che accedi a questa integrazione dello strumento, viene creato un account {{site.data.keyword.webide}} corrispondente ma nascosto per il tuo account IBM Cloud. Dopo che hai eliminato tutti i tuoi spazi di lavoro, non accedere a {{site.data.keyword.webide}}. Se accedi nuovamente a {{site.data.keyword.webide}}, viene creato automaticamente un nuovo account che devi eliminare.
{: important}

## Modifica, esportazione ed eliminazione di repository Git e dati di traccia dei problemi
{: #managing_grit_data}

{{site.data.keyword.gitrepos}} fornisce un servizio Git ospitato nel cloud. Per associare il tuo account IBM Cloud a un account Git viene utilizzato un meccanismo SSO (single sign-on). Nel tuo account Git vengono creati per tuo conto un nome completo e un nome breve. Gli altri utenti possono utilizzare il tuo nome breve per fare riferimento a te in un commento all'interno di un problema Git. Puoi personalizzare il tuo account Git e aggiungere dati personali, come una descrizione di te stesso o un'immagine. 

{{site.data.keyword.gitrepos}} fornisce un ambiente di social coding potente ma complesso in cui gli utenti contribuiscono a diversi progetti e gli oggetti sono condivisi. Questo ambiente può rendere difficile individuare ed eliminare i tuoi dati personali.

I profili, le impostazioni, i progetti personali, i gruppi e i frammenti del tuo account sono associati al tuo account Git. Se elimini il tuo account Git, questi oggetti vengono eliminati. Per eliminare i dati personali in un altro progetto, passa al progetto e quindi modificalo per rimuovere i tuoi dati personali oppure elimina del tutto il progetto. Assicurati di coordinarti con altri membri del tuo team prima di eliminare progetti condivisi.

Prima di eliminare il tuo account Git, elimina i tuoi dati personali dagli altri progetti. Dopo che hai eliminato il tuo account Git, potrebbe essere difficile, se non impossibile, trovare tutti i progetti a cui hai contribuito.
{: tip}

###Progetti personali e condivisi

Puoi invitare altri utenti a collaborare ai progetti. I progetti Git che crei all'interno del tuo account sono detti progetti personali. Puoi anche creare dei gruppi Git in cui i progetti possono appartenere a più proprietari Git. Puoi creare dei nuovi progetti per il gruppo o trasferire la proprietà di progetti personali al gruppo. Un gruppo Git viene spesso utilizzato per rappresentare un account aziendale IBM Cloud per indicare l'appartenenza dei progetti alla società.

###Esportazione di un progetto Git Repos and Issue Tracking

Prima di eliminare un progetto {{site.data.keyword.gitrepos}}, puoi esportare il progetto per archiviarlo. 

1. Fai clic sull'icona **Settings** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Icona delle impostazioni"> nella barra laterale di navigazione sulla sinistra.
1. Fai clic su **General**.
1. Fai clic su **Expand** per espandere la sezione Export project.
1. Fai clic su **Export project**.

Dopo che il progetto è stato archiviato, puoi importarlo in un'altra istanza GitLab. 

###Eliminazione del tuo account Git Repos and Issue Tracking

Puoi eliminare il tuo account {{site.data.keyword.gitrepos}} e tutto quanto appartiene a tale account.

1. Nel dashboard User Settings {{site.data.keyword.gitrepos}}, nella [pagina Account ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, nella sezione Delete account, fai clic su **Delete account**.
1. Vengono eliminati tutti i progetti Git, compresi i repository e i problemi. Vieni anche rimosso da qualsiasi gruppo {{site.data.keyword.gitrepos}} a cui appartieni.

Dopo che il tuo account è stato eliminato, del contenuto continuerà a esistere. Questo contenuto viene assegnato a un Ghost User a livello di sistema. Per ulteriori informazioni sull'eliminazione di un account {{site.data.keyword.gitrepos}}, consulta [Deleting a user account ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/account/delete_account#associated-records){:new_window}.
{: tip}

{{site.data.keyword.gitrepos}} utilizza un meccanismo SSO (single sign-on) che crea automaticamente un account Git corrispondente per il tuo account IBM Cloud la prima volta che accedi all'integrazione dello strumento. Dopo che hai eliminato il tuo account, non accedere a {{site.data.keyword.gitrepos}}. Se accedi nuovamente a {{site.data.keyword.gitrepos}}, viene creato automaticamente un nuovo account che devi eliminare.
{: important}

## Modifica, esportazione ed eliminazione dei dati delle pipeline Continuous Delivery
{: #managing_pipeline_data}

Le pipeline {{site.data.keyword.contdelivery_short}} eseguono script per creare, testare e distribuire la tua applicazione su IBM Cloud. A tale fine, le pipeline forniscono fasi, lavori, variabili di ambiente e altri oggetti che potrebbero contenere dati personali. Puoi eliminare questi oggetti singolarmente oppure puoi eliminare un'intera pipeline.

Assicurati di coordinarti con gli altri membri del tuo team prima di eliminare oggetti condivisi o pipeline. L'eliminazione di una fase potrebbe causare la mancata riuscita di una pipeline.

Una pipeline non può esistere al di fuori di una toolchain. Se elimini una toolchain, vengono eliminate anche tutte le pipeline ad essa associate. Se intendi eliminare un'intera toolchain, non hai bisogno di eliminare ciascuna pipeline singolarmente. Passa invece direttamente alla sezione "Modifica ed eliminazione delle toolchain e delle integrazioni dello strumento" e attieniti alla procedura per eliminare una toolchain.
{: important}

Le fasi della pipeline possono includere dati personali quali le credenziali sotto forma di proprietà dell'ambiente e una definizione della pipeline che mostra il suo stato corrente. Le fasi possono anche includere degli script all'interno di lavori che vuoi modificare o eliminare, così come risorse utente e log delle esecuzione della pipeline più recenti che vuoi esportare. Utilizza le azioni Configure Stage o Delete Stage per modificare o eliminare una fase. Utilizza l'azione di scaricamento per esportare le risorse utente o i log da una fase.

  ![Menu Stages](images/pipeline_stages.png)

###Modifica di una fase della pipeline

Per modificare una fase della pipeline:

1. Nella pagina Pipeline, fai clic sull'icona **Settings**.
1. Fai clic su **Configure Stage**.
1. Nella scheda **ENVIRONMENT PROPERTIES**, modifica o elimina proprietà.
1. Modifica uno script di lavoro in una fase della pipeline. Seleziona il lavoro e modifica i valori che fanno parte della creazione, della distribuzione o della configurazione del test.
   
   ![Modifica script del lavoro](images/job_script.png)
  
1. Elimina un lavoro dalla fase della pipeline. Nella scheda **JOBS**, seleziona il lavoro che vuoi eliminare e fai clic su **Remove**.
 
###Esportazione di una fase della pipeline

Per esportare la definizione per un'intera pipeline, accoda `/yaml` all'URL della pipeline:

`https://cloud.ibm.com/devops/pipelines/<pipeline id>/yaml?env_id=<region id>`

Dove `<pipeline id>` e `<region id>` sono i valori che vengono visualizzati nell'URL della pagina della pipeline.

Il file yaml risultante include le definizioni di tutte le fasi della pipeline.


Per esportare le risorse utente e i log per una fase della pipeline:

1. Nella pagina Pipeline, fai clic su **View logs and history**.
1. Fai clic sul numero di build di cui desideri esportare le risorse utente e i log.
1. Fai clic su **DOWNLOAD** > **Artifacts** per esportare le risorse utente per la build selezionata.
1. Fai clic su **DOWNLOAD** > **Logs** per esportare i log per la build selezionata.  

###Eliminazione di una fase della pipeline

Per eliminare una fase della pipeline:

1. Nella pagina Pipeline, fai clic sull'icona **Settings**.
1. Fai clic su **Delete Stage**.

## Modifica ed eliminazione di toolchain e integrazioni dello strumento
{: #managing_toolchains}

Utilizzando le toolchain, i team possono collaborare e condividere diverse integrazioni dello strumento. 

Ti consigliamo di configurare tutte le integrazioni {{site.data.keyword.contdelivery_short}} utilizzando i dati associati al tuo team o alla tua società piuttosto che i dati associati a te. Tuttavia, in alcuni casi, potrebbero essere invece utilizzati inavvertitamente i tuoi dati personali. In tali casi, devi identificare tutti i dati che ti appartengono ed eliminarli.

Quando viene creata un'integrazione dello strumento, {{site.data.keyword.contdelivery_short}} non può registrare l'origine di tutti i dati. Ad esempio, un altro membro del team potrebbe creare un'integrazione dello strumento per tuo conto utilizzando i dati personali da te forniti in una email. Devi capire quali dati sono di tua proprietà e assicurarti che vengano eliminati.

Coordinati con gli altri membri del tuo team prima di eliminare le toolchain e le integrazioni dello strumento condivise.

###Modifica ed eliminazione delle integrazioni dello strumento

Quando crei un'integrazione dello strumento, ti viene richiesto di fornire le credenziali utente e altre informazioni di account pertinenti all'integrazione. Se hai usato le tue credenziali personali e le tue informazioni di account, sostituisci tali informazioni con valori differenti oppure elimina l'integrazione dello strumento.

Per modificare un'integrazione dello strumento:

1. Nella scheda dello strumento, fai clic sul menu per accedere alle opzioni di configurazione.

  ![Menu Tool Configuration](images/toolchain_tile_menu.png)

1. Quando hai terminato di aggiornare le impostazioni, fai clic su **Save Integration**.

Per eliminare un'integrazione dello strumento:

1. Per eliminare un'integrazione dello strumento dalla tua toolchain, fai clic su **Delete**.
1. Conferma facendo clic su **Delete**.

###Eliminazione di toolchain

Quando elimini una toolchain, l'eliminazione non può essere annullata.

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain da eliminare. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**.
1. Fai clic sul menu **More Actions**, accanto a **View app**.
1. Fai clic su **Delete**. L'eliminazione di una toolchain rimuove tutte le sue integrazioni dello strumento, comprese le pipeline, e ciò potrebbe eliminare le risorse gestite da tali integrazioni.
1. Conferma l'eliminazione digitando il nome della toolchain e facendo clic su **Delete**. 

Quando elimini una toolchain, i repository {{site.data.keyword.gitrepos}} associati non vengono eliminati. Gli utenti che hanno accesso a tali repository potrebbero disporre di copie dei dati se hanno eseguito `clone git` o creato uno spazio di lavoro {{site.data.keyword.webide}}. Per assicurarti che tutti i dati vengano eliminati, devi richiedere che tali utenti eliminino le copie dei dati.
{: tip}

###Eliminazione di tutte le toolchain

Non puoi eliminare tutte le toolchain in un'organizzazione o in un gruppo di risorse contemporaneamente. Devi eliminare ciascuna toolchain, una alla volta.

Le toolchain sono organizzate per regione IBM Cloud e organizzazione Cloud Foundry o gruppo di risorse. Assicurati di selezionare ogni regione e organizzazione o gruppo di risorse all'interno della regione per eliminare ogni toolchain che hai creato.
{: tip}
