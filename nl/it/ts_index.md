---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Domande frequenti (FAQ)
{: #ts_cd}

Ottieni le risposte alle domande frequenti sull'utilizzo di {{site.data.keyword.contdelivery_full}}.
{:shortdesc}

## Perché la pagina Toolchains mostra che il piano Lite del servizio {{site.data.keyword.contdelivery_short}} è stato superato?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} offre due piani: Lite e Professional. Se hai il piano {{site.data.keyword.contdelivery_short}} Lite, puoi utilizzare le toolchain gratuitamente, fino ai limiti del piano. Il messaggio di errore indica che è stato superato uno o più limiti del piano Lite. Ad esempio, potresti aver superato il piano se hai troppi utenti autorizzati associati all'istanza del servizio {{site.data.keyword.contdelivery_short}} o se hai eseguito il numero massimo di lavori {{site.data.keyword.deliverypipeline}}. Per ulteriori informazioni sui termini del piano, consulta [Utilizzo e limitazioni del piano](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage){: new_window}.


## Il mio servizio {{site.data.keyword.contdelivery_short}} indica che i servizi del piano Lite vengono eliminati dopo 30 giorni di inattività. Cosa si intende per inattività?
{: #plan_inactivity}
{: faq}

Un'istanza del servizio {{site.data.keyword.contdelivery_short}} viene considerata attiva quando una o più delle toolchain all'interno dello stesso gruppo di risorse o della stessa organizzazione (org) Cloud Foundry sono attivi. Una toolchain è considerata attiva se gli utenti interagiscono con essa mediante l'interfaccia utente, se vengono attivati i lavori della delivery pipeline, se si accede ai repository gestiti da {{site.data.keyword.gitrepos}} o se gli spazi di lavoro Eclipse Orion {{site.data.keyword.webide}} sono in uso. Per essere considerata inattiva, tutte queste condizioni devono essere assenti per tutte le toolchain associate al servizio {{site.data.keyword.contdelivery_short}} per 30 giorni.


## Ho creato una toolchain, perché la pagina Toolchains mostra che è necessario un servizio Continuous Delivery?
{: #service_required_resource_group}
{: faq}

I termini del piano per l'istanza del servizio {{site.data.keyword.contdelivery_short}} che si trova nello stesso gruppo di risorse o organizzazione della toolchain gestisce l'utilizzo di alcune integrazioni dello strumento ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} e {{site.data.keyword.gitrepos}}) contenute nel servizio. Il messaggio di errore indica che il gruppo di risorse o l'organizzazione non contiene l'istanza richiesta del servizio {{site.data.keyword.contdelivery_short}}. Per ulteriori informazioni sui termini del piano, consulta [Utilizzo e limitazioni del piano](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage){: new_window}.


## Ho caricato le informazioni per una toolchain da un'organizzazione Cloud Foundry; perché non vedo alcuna modifica nella toolchain?
{: #updates_in_cloud_foundry}
{: faq}

Quando aggiorni le informazioni sulla toolchain direttamente da Cloud Foundry, potrebbe volerci qualche minuto perché il servizio {{site.data.keyword.contdelivery_short}} aggiorni e visualizzi le tue modifiche. Ad esempio, se aggiungi o rimuovi un utente da un'organizzazione Cloud Foundry, potrebbe volerci qualche minuto perché {{site.data.keyword.contdelivery_short}} rilevi che è presente un nuovo utente e consenta a tale utente di accedere alla toolchain.


## Ho creato una toolchain in un'organizzazione Cloud Foundry, perché la pagina Toolchains mostra che è necessario un servizio Continuous Delivery?
{: #service_required_cloud_foundry}
{: faq}

Quando crei una toolchain in un gruppo di risorse o un'organizzazione che non dispone di un'istanza del servizio {{site.data.keyword.contdelivery_short}}, la piattaforma della toolchain tenta di creare automaticamente un'istanza del servizio utilizzando il piano Lite. Il messaggio di errore indica che la piattaforma della toolchain non è riuscita a creare l'istanza del servizio.

Questo errore potrebbe verificarsi quando crei una toolchain nella regione Stati Uniti Sud e in un'organizzazione che non dispone ancora di un istanza di {{site.data.keyword.contdelivery_short}}. Nella regione Stati Uniti Sud, devi creare tutte le nuove istanze del servizio {{site.data.keyword.contdelivery_short}} nei gruppi di risorse. 

Puoi creare la toolchain in un gruppo di risorse o in un'organizzazione che dispone già di un'istanza di {{site.data.keyword.contdelivery_short}}.
  

## Come sposto la mia toolchain da un'organizzazione Cloud Foundry a un gruppo di risorse?
{: #toolchain_move_to_resource_group}
{: faq}

Una funzione che migra automaticamente le toolchain da un'organizzazione Cloud Foundry a un gruppo di risorse non è ancora disponibile. Puoi invece creare di nuovo in modo manuale la toolchain in un gruppo di risorse e rimuovere quindi la toolchain originale dall'organizzazione Cloud Foundry.


## Ho provato a distribuire un'applicazione a {{site.data.keyword.Bluemix_notm}}, perché sto ottenendo un errore?
{: #org_outofmemory}
{: faq}

Quando provi a distribuire un'applicazione a {{site.data.keyword.Bluemix_notm}}, se ottieni il seguente messaggio di errore, la quantità di memoria residua nella tua organizzazione è inferiore a quella richiesta dall'applicazione che vuoi distribuire.

`Errore Server NON RIUSCITO, codice stato: 400, codice errore: 100005, messaggio: Hai superato il limite di memoria della tua organizzazione.`

Puoi aumentare la quota di memoria del tuo account o ridurre la memoria utilizzata dalle tue applicazioni. La quota massima di memoria per un account di prova è 2 GB. Per aumentare la quota di memoria dell'account, converti il tuo account di prova in un account a pagamento. Per informazioni su come convertire il tuo account di prova in un account a pagamento, vedi [Come posso eseguire l'upgrade o modificare il mio tipo di account?](/docs/account?topic=account-accountfaqs#changeacct). Per ridurre la memoria utilizzata dalle tue applicazioni, utilizza la console {{site.data.keyword.Bluemix_notm}} o l'interfaccia riga di comando cf.

Se utilizzi la console {{site.data.keyword.Bluemix_notm}}, completa la seguente procedura:

1. Nel dashboard delle applicazioni, seleziona la tua applicazione. Viene visualizzata la pagina dei dettagli dell'applicazione.
1. Nel riquadro runtime, puoi ridurre il limite massimo di memoria o il numero di istanze dell'applicazione, o entrambi, per tua applicazione.

Se utilizzi l'interfaccia riga di comando cf, completa la seguente procedura:

1. Verifica la quantità di memoria utilizzata per le tue applicazioni. Il comando cf apps elenca tutte le applicazioni che hai distribuito nel tuo spazio corrente. Viene visualizzato anche lo stato di ciascuna applicazione.

	  ```
	  cf apps
	  ```

1. Per ridurre la quantità di memoria utilizzata dalla tua applicazione, riduci il numero di istanze dell'applicazione e/o il limite massimo di memoria.

	  ```
	  cf push appname -p percorso_applicazione -i numero_istanza -m limite_memoria
      ```
    
1. Riavvia la tua applicazione per rendere effettive le modifiche.


## Ho creato un'applicazione; perché la barra di esecuzione non mostra le icone {{site.data.keyword.Bluemix_notm}} Live Sync in {{site.data.keyword.webide}}?
{: #ts_llz_lkb_3r}
{: faq}

![Barra di esecuzione](images/webide_runbar_light.png)   

Quando modifichi un'applicazione Node.js in {{site.data.keyword.webide}}, le icone di live edit, riavvio rapido e debug di {{site.data.keyword.Bluemix_notm}} non sono disponibili nella barra di esecuzione nelle seguenti circostanze:


* Il file `manifest.yml` non è memorizzato al livello principale del tuo progetto.
* La tua applicazione è memorizzata in una sottodirectory anziché nella root, ma il percorso della sottodirectory non è specificato nel file `manifest.yml`.
* L'applicazione non contiene un file `package.json`.


Se il file `manifest.yml` non è memorizzato nella root, memorizzalo lì. Se la tua applicazione è memorizzata in una sottodirectory, specifica il percorso di tale sottodirectory nel file `manifest.yml`. Se l'applicazione non contiene un file `package.json`, crearne uno che si trovi nella stessa directory della tua applicazione.


## Ho fatto clic sul pulsante Run di {{site.data.keyword.webide}}; dove sono i file di log? 
{: #web_ide_log_files}
{: faq}  

Quando fai clic sul pulsante Run, viene eseguito il push del contenuto del tuo spazio di lavoro a Cloud Foundry nello stesso modo in cui ne viene eseguita la distribuzione se immetti `cf push` dal tuo desktop. Puoi trovare i file di log dal dashboard Cloud Foundry.

Per ulteriori informazioni sulla distribuzione del contenuto del tuo spazio di lavoro, vedi [Distribuzione di un'applicazione dal tuo spazio di lavoro](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy).


## Come evito che {{site.data.keyword.webide}} selezioni automaticamente tutte le modifiche nella vista Git? 
{: #web_ide_git_view}
{: faq} 

{{site.data.keyword.webide}} presume, per impostazione predefinita, che desideri eseguire il push delle modifiche in corso al tuo repository del codice ogni volta che vai alla pagina Git. Se desideri selezionare manualmente quali sono le risorse di cui eseguire il commit, la sincronizzazione, la reimpostazione o la sostituzione, dalla pagina delle preferenze di Git, deseleziona la casella di spunta **Always select changed files**.


## Perché {{site.data.keyword.webide}} non supporta il linguaggio da me utilizzato? 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}} fornisce un'ampia gamma di strumenti e supporto per JavaScript, HTML e CSS. Fornisce anche l'evidenziazione della sintassi per i linguaggi più diffusi. Non puoi estendere {{site.data.keyword.webide}} per supportare uno specifico linguaggio. Per visualizzare un elenco completo dei linguaggi supportati da {{site.data.keyword.webide}}, vedi [Linguaggi supportati](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages).


## Come trovo lo stato di {{site.data.keyword.Bluemix_notm}} e del servizio {{site.data.keyword.contdelivery_short}}?
{: #toolchains_load}
{: faq}

Controlla la pagina relativa allo stato di {{site.data.keyword.Bluemix_notm}} per determinare la presenza di problemi noti che interessano la piattaforma {{site.data.keyword.Bluemix_notm}} e i servizi principali in {{site.data.keyword.Bluemix_notm}}.

Puoi individuare la pagina Stato scegliendo una delle seguenti opzioni:

  * Accedi alla console {{site.data.keyword.Bluemix_notm}}. Dalla barra dei menu, fai clic su **Supporto** e seleziona **Stato**. Controlla le risorse elencate per l'icona di ![alcuni problemi](../../get-support/images/some_issues.svg). Questa icona potrebbe indicare un'interruzione.
  * Accedi ad essa direttamente nella pagina di [stato dei sistemi {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/status){: new_window}.

Per ulteriori informazioni sulla pagina relativa allo stato di {{site.data.keyword.Bluemix_notm}}, consulta [Visualizzazione dello stato di {{site.data.keyword.Bluemix_notm}}](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status){: new_window}.


## Come eseguo il passaggio di risorse tra i lavori della pipeline?
{: #artifacts_pipeline_jobs}
{: faq}

Poiché tutti i lavori della pipeline in una fase ricevono lo stesso input di fase, non puoi eseguire il passaggio di risorse tra i lavori che si trovano nella stessa fase. Tuttavia, i lavori di build generano delle risorse che possono essere utilizzate dai lavori in altre fasi. Per eseguire il passaggio di risorse tra due lavori, sposta ciascun lavoro in una fase differente. Per ulteriori informazioni sui lavori della pipeline, vedi [Lavori](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs).


## C'è un limite di tempo massimo di possibile esecuzione dei miei lavori della pipeline?
{: #pipeline_jobs_time_limit}
{: faq}

Ogni lavoro della pipeline può essere eseguito per un massimo di 60 minuti. Se supera questo limite di tempo, il lavoro non riesce. Esamina se l'attività eseguita dal lavoro della pipeline può essere divisa in passi più piccoli.Puoi dividere il lavoro della pipeline in diversi lavori della pipeline più brevi che vengono eseguiti per meno di 60 minuti.


## Quanto sono sicure le proprietà sicure della pipeline?
{: #pipeline_secure_properties}
{: faq}

Le proprietà sicure della pipeline sono crittografate utilizzando AES-128 e decrittografate immediatamente prima di essere passate al tuo script della pipeline. Queste proprietà sono anche mascherate utilizzando gli asterischi nell'interfaccia utente delle proprietà e nei tuoi file di log della pipeline. Prima che i dati vengano scritti nel file di log per il tuo lavoro della pipeline, ne viene eseguita la scansione per rilevare eventuali corrispondenze esatte a tutti i valori nelle proprietà sicure della pipeline. Se viene trovata una corrispondenza, viene mascherata utilizzando gli asterischi. Fai attenzione quando lavori con le proprietà sicure e i file di log poiché vengono mascherate solo le corrispondenze esatte. 
