---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Introduzione a Continuous Delivery
{: #cd_getting_started}

Adotta un approccio DevOps utilizzando {{site.data.keyword.contdelivery_full}}, che include le toolchain aperte che automatizzano la creazione e la distribuzione di applicazioni. Puoi iniziare creando una semplice toolchain di distribuzione che supporta le attività operative, di sviluppo e di distribuzione.
{: shortdesc}

Dopo che hai creato un'istanza di {{site.data.keyword.contdelivery_short}} selezionandolo dal catalogo {{site.data.keyword.Bluemix_notm}}, puoi creare una toolchain continuous delivery da un template oppure utilizzare le toolchain esistenti.
 ![Pagina di benvenuto di Continuous Delivery](images/cd_landing_page2.png)

* Per creare e configurare una toolchain continuous delivery da un template, fai clic su **[Start here](#starting_from_a_toolchain_template)**. La toolchain integra gli strumenti per la pianificazione, lo sviluppo, la distribuzione di pipeline e la gestione delle tue applicazioni. Puoi sempre aggiungere o rimuovere strumenti dalla toolchain.
* Se già hai delle toolchain, nella sezione "Start from a toolchain template" fai clic su **View your toolchains**. Per ulteriori informazioni sull'utilizzo delle toolchain, vedi [Gestione delle toolchain](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}.

##Panoramica di {{site.data.keyword.contdelivery_short}}
{: #cd_overview}

Con {{site.data.keyword.contdelivery_short}}, puoi creare, testare e fornire applicazioni utilizzando le procedure e gli strumenti leader nel settore DevOps.
{:shortdesc}

Il servizio {{site.data.keyword.contdelivery_short}} supporta i tuoi flussi di lavoro DevOps:

 * Puoi creare [toolchain](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window} DevOps integrate per abilitare le integrazioni dello strumento che supportano le tue attività di sviluppo, distribuzione e operative.

  Una toolchain è una serie di strumenti integrata che puoi utilizzare per sviluppare, creare, distribuire, verificare e gestire in modo collaborativo le applicazioni e per rendere le operazioni ripetibili e più facili da gestire. Le toolchain possono includere degli strumenti open source, servizi {{site.data.keyword.Bluemix_notm}}, quali[{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window}, e strumenti di terze parti, quali GitHub, PagerDuty e Slack. 
  
  **Nota**: {{site.data.keyword.DRA_short}} è disponibile solo nella regione Stati Uniti Sud.

 * Fornitura continua mediante [pipeline](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window} automatizzate.

  Automatizza creazioni, verifiche di unità, distribuzioni e altro ancora. Crea, verifica e distribuisci in modo ripetibile con il minimo intervento umano. Tieniti pronto per il rilascio in produzione in qualsiasi momento,

 * Modifica ed esegui il push del tuo codice da qualsiasi luogo utilizzando l'[IDE basato su Web](/docs/services/ContinuousDelivery/web_ide.html){: new_window}.

  Crea, modifica, esegui e completa le attività di controllo origine in GitHub ed eseguine il debug. Passa facilmente dalla modifica del tuo codice alla sua distribuzione in produzione. 
  
 * Collabora con il tuo team e gestisci il tuo codice sorgente con un [repository (repo) Git e il programma di traccia dei problemi](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window} ospitato da IBM e sviluppato su GitLab Community Edition.

  Gestisci i repository Git attraverso i controlli dell'accesso accurati che mantengono il codice sicuro. Rivedi il codice e migliora la collaborazione tramite le richieste di unione. Tieni traccia dei problemi e condividi le idee tramite il programma di traccia dei problemi. Documenta i progetti sul sistema wiki.


##Inizia da un template di toolchain
{: #starting_from_a_toolchain_template}

Per creare e configurare una toolchain di fornitura continua da un [template ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/devops/create){: new_window}:

1. Nella pagina **Create a Toolchain**, fai clic su un template di toolchain.
1. Esamina il diagramma della toolchain che stai per creare. Il diagramma mostra ogni integrazione dello strumento nella fase del suo ciclo di vita nella toolchain.

 **Suggerimento**: alcuni template della toolchain dispongono di più istanze di un'integrazione dello strumento. Ad esempio, il template della toolchain Microservizi su {{site.data.keyword.Bluemix_notm}} Pubblico contiene tre istanze di GitHub e tre di Delivery Pipeline, una per ognuno dei tre microservizi.

 Il diagramma nella seguente immagine è un esempio. Quando crei una toolchain, il diagramma mostra ogni integrazione dello strumento che fa parte della toolchain.
 ![Diagramma_toolchain](images/toolchain_diagram2.png)
1. Rivedi le informazioni predefinite per la configurazione della toolchain:

 * Il nome della toolchain la identifica in {{site.data.keyword.Bluemix_notm}}. Se vuoi utilizzare un nome diverso, modifica il nome della toolchain.
 * La regione in cui creare la toolchain. Se vuoi utilizzare una regione differente, selezionala dall'elenco delle regioni disponibili.
 * L'organizzazione in cui creare la toolchain. Se vuoi utilizzare una organizzazione differente, selezionala dall'elenco di organizzazioni disponibili.
 
1. Nella sezione Integrazioni dello strumento, seleziona ogni integrazione dello strumento che desideri configurare per la tua toolchain. Alcune delle integrazioni dello strumento non richiedono configurazione. Per informazioni sulla configurazione delle integrazioni dello strumento, consulta [Configurazione delle integrazioni dello strumento](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Fai clic su **Create**. Diversi passi vengono eseguiti automaticamente per configurare la tua toolchain. Le integrazioni dello strumento configurate a seconda della toolchain selezionata e se stai utilizzando {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato. Ad esempio, quando crei una toolchain Microservizi in {{site.data.keyword.Bluemix_notm}} Pubblico, deve essere eseguita questa procedura:

 * La toolchain viene creata.
 * Se hai configurato Delivery Pipeline, le pipeline vengono create ed eseguite.
 * Se hai configurato Sauce Labs, la toolchain viene configurata per aggiungere i lavori di verifica Sauce Labs alle pipeline.
 * Se hai configurato PagerDuty, la toolchain viene configurata per inviare notifiche di avviso al servizio PagerDuty che hai specificato.
 * Se hai configurato Slack, la toolchain viene configurata per inviare notifiche sullo stato della distribuzione al canale Slack che hai specificato.
 * Se hai configurato un'integrazione dello strumento del codice sorgente come GitHub, il repository GitHub di esempio viene clonato nel tuo account GitHub.
