---

copyright:
  years: 2015, 2018

lastupdated: "2018-12-6"


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

# Creazione delle toolchain
{: #toolchains_getting_started}

Una *toolchain* è una serie di integrazioni dello strumento che supporta le attività operative, di sviluppo e di distribuzione. La potenza collettiva di una toolchain è superiore alla somma delle relative integrazioni dello strumento.
{: shortdesc}

Le toolchain aperte sono disponibili negli ambienti Pubblico e Dedicato in {{site.data.keyword.Bluemix}}. Puoi creare una toolchain in due modi: utilizzando un template o creandola da un'applicazione.

Ogni toolchain viene associata a un'organizzazione (org) o a un gruppo di risorse specifico. Se una toolchain viene associata a un gruppo di risorse, qualsiasi utente con autorizzazione da visualizzatore IAM (Identity and Access Management) per la risorsa toolchain o per il gruppo di risorse che lo contiene, può accedere alla toolchain. Se la toolchain viene associata a un'organizzazione, tutti gli utenti che sono membri di tale organizzazione possono essere aggiunti all'elenco di controllo dell'accesso per ognuna delle rispettive toolchain associate. Per ulteriori informazioni sul controllo dell'accesso per le toolchain nelle organizzazioni Cloud Foundry, consulta [Gestione dell'accesso utente alle toolchain nelle organizzazioni Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}. Per ulteriori informazioni sul controllo dell'accesso per le toolchain nei gruppi di risorse, consulta [Gestione dell'accesso alle toolchain nei gruppi di risorse](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window}.

##Creazione di una toolchain da un template   
{: #creating_a_toolchain_from_a_template}

Puoi utilizzare un template come punto di partenza nella [creazione di una toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/devops/create){: new_window} che includa una serie specifica di integrazioni dello strumento. Scopri come utilizzare i template da [IBM Cloud Garage Method ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/category/tools){:new_window}.

1. Se utilizzi {{site.data.keyword.Bluemix_notm}} Pubblico, accedi a [{{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://cloud.ibm.com){:new_window}.
1. Se utilizzi {{site.data.keyword.Bluemix_notm}} Dedicato, accedi al tuo ambiente dedicato in {{site.data.keyword.Bluemix_notm}}.
1. Dal menu sulla barra dei menu di {{site.data.keyword.Bluemix_notm}}, fai clic su **DevOps**.
1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su **Create a Toolchain**.
1. Nella pagina **Create a Toolchain**, fai clic su un template di toolchain.
1. Esamina il diagramma della toolchain che stai per creare. Il diagramma mostra ogni integrazione dello strumento nella fase del suo ciclo di vita nella toolchain.

 Alcuni template della toolchain dispongono di più istanze di un'integrazione dello strumento. Ad esempio, il template della toolchain Microservizi su {{site.data.keyword.Bluemix_notm}} Pubblico contiene tre istanze di GitHub e tre di Delivery Pipeline, una per ognuno dei tre microservizi.
 {: tip}

 Il diagramma nella seguente immagine è un esempio. Quando crei una toolchain, il diagramma mostra ogni integrazione dello strumento che fa parte della toolchain.
![Diagramma toolchain](images/toolchain_diagram2.png)

1. Rivedi le informazioni predefinite per la configurazione della toolchain:

 * Il nome della toolchain la identifica in {{site.data.keyword.Bluemix_notm}}. Se vuoi utilizzare un nome diverso, modifica il nome della toolchain.
 * La regione in cui creare la toolchain. Se vuoi utilizzare una regione differente, selezionala dall'elenco delle regioni disponibili.
 * L'organizzazione o il gruppo di risorse in cui creare la toolchain. Fai clic sul link per passare dalla selezione di gruppi di risorse alle organizzazioni. Se vuoi utilizzare una organizzazione o un gruppo di risorse differente, selezionalo dall'elenco di organizzazioni o gruppi di risorse disponibili.
 
   I gruppi di risorse sono disponibili nelle regioni Stati Uniti Sud, Stati Uniti Est, Regno Unito, Germania e Tokyo. Le organizzazioni Cloud Foundry sono supportate nelle regioni Stati Uniti Sud, Regno Unito e Germania.
   {: important}

1. Nella sezione Integrazioni dello strumento, seleziona ogni integrazione dello strumento che desideri configurare per la tua toolchain. Alcune delle integrazioni dello strumento non richiedono configurazione. Per informazioni sulla configurazione delle integrazioni dello strumento, consulta [Configurazione delle integrazioni dello strumento](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Fai clic su **Create**. Diversi passi vengono eseguiti automaticamente per configurare la tua toolchain. Le integrazioni dello strumento configurate a seconda della toolchain selezionata e se stai utilizzando {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato. Ad esempio, quando crei una toolchain Microservizi in {{site.data.keyword.Bluemix_notm}} Pubblico, deve essere eseguita questa procedura:

 * La toolchain viene creata.
 * Se hai configurato Delivery Pipeline, le pipeline vengono create e attivate.
 * Se hai configurato Sauce Labs, la toolchain viene configurata per aggiungere i lavori di verifica Sauce Labs alle pipeline.
 * Se hai configurato PagerDuty, la toolchain viene configurata per inviare notifiche di avviso al servizio PagerDuty che hai specificato.
 * Se hai configurato Slack, la toolchain viene configurata per inviare notifiche sullo stato della distribuzione al canale Slack che hai specificato.
 * Se hai configurato un'integrazione dello strumento del codice sorgente come GitHub, il repository GitHub di esempio viene clonato nel tuo account GitHub.


##Creazione di una toolchain da un applicazione
{: #creating_a_toolchain_from_an_app}

Puoi creare una toolchain dalla tua applicazione. La toolchain può supportare il monitoraggio, la distribuzione e lo sviluppo continuo ed anche altro, e viene associata alla tua applicazione. Ogni applicazione può essere associata con una toolchain. Quando esegui il push delle modifiche a un repository {{site.data.keyword.ghe_short}} o GitHub della toolchain, la pipeline automaticamente crea e distribuisce l'applicazione.

Se hai creato la tua applicazione utilizzando il tuo repository di codice, fai clic su **Connect to DevOps toolchain** nella pagina dei dettagli della tua applicazione. Attieniti quindi alla procedura descritta in [Creazione di applicazioni dal tuo repository di codice](/docs/apps/tutorials/tutorial_byoc.html).
{: note}

1. Se hai creato la tua applicazione utilizzando un kit starter, fai clic su **Deploy to cloud** nella pagina dei dettagli della tua applicazione. Se utilizzi {{site.data.keyword.Bluemix_notm}} Pubblico, la tua applicazione è configurata per la distribuzione continua da un nuovo repository GitHub che viene popolato con il codice starter dell'applicazione. Se utilizzi {{site.data.keyword.Bluemix_notm}} Dedicato, la tua applicazione è configurata per la distribuzione continua da un nuovo repository GitHub o {{site.data.keyword.ghe_short}} che viene popolato con il codice starter dell'applicazione.
1. Nella pagina di creazione della toolchain, rivedi il diagramma della toolchain che stai per creare. Il diagramma mostra ogni integrazione dello strumento nella fase del suo ciclo di vita nella toolchain.
1. Rivedi le informazioni predefinite per la configurazione della toolchain. Il nome della toolchain la identifica in {{site.data.keyword.Bluemix_notm}}. Se vuoi utilizzare un nome diverso, modifica il nome della toolchain.
1. Nella sezione Integrazioni dello strumento, seleziona ogni integrazione dello strumento che desideri configurare per la tua toolchain. Alcune delle integrazioni dello strumento non richiedono configurazione. Per informazioni sulla configurazione delle integrazioni dello strumento, consulta [Configurazione delle integrazioni dello strumento](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Fai clic su **Create**. Diversi passi vengono eseguiti automaticamente per configurare la tua toolchain. Le integrazioni dello strumento configurate sono diverse a seconda che tu stia utilizzando {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato. Ad esempio, quando crei una toolchain da un'applicazione su {{site.data.keyword.Bluemix_notm}} Pubblico, devono essere eseguiti questi passi:

 * La toolchain viene creata.
 * Se hai configurato Delivery Pipeline, le pipeline vengono create e attivate.
 * Se hai configurato GitHub, il repository GitHub di esempio viene clonato nel tuo account GitHub.


##Visualizzazione di una toolchain
{: #viewing_a_toolchain}

Dopo aver configurato la toolchain e le sue integrazioni dello strumento, puoi visualizzare una rappresentazione visiva della toolchain.

Puoi visualizzare una toolchain da un'applicazione facendo clic su **Visualizza toolchain** dalla pagina dei dettagli della tua applicazione.
{: tip}

1. Nel dashboard DevOps, nella pagina **Toolchains**, seleziona **RESOURCE GROUP** o **CLOUD FOUNDRY ORG**. Vengono visualizzate tutte le toolchain contenute all'interno dell'organizzazione Cloud Foundry o del gruppo di risorse selezionato. Fai clic sulla toolchain che desideri visualizzare per aprire la relativa pagina Panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**. Fai quindi clic su **Overview**.
2. Per accedere all'integrazione dello strumento nella tua toolchain, fai clic sullo strumento.

 Se disponi di più di un repository GitHub, {{site.data.keyword.ghe_short}} o Git, puoi avere più schede per la stessa integrazione dello strumento perché ogni repository è rappresentato dalla propria scheda. Se hai più di una pipeline, potresti avere più schede per la stessa integrazione dello strumento perché ogni pipeline è rappresentata dalla propria scheda. Ad esempio, quando crei una toolchain Microservizi, ognuno dei tre microservizi ha il proprio repository GitHub, {{site.data.keyword.ghe_short}} o Git e la propria pipeline.
 {: tip}

## Visualizza una esercitazione: utilizzo delle toolchain
{: #toolchain_tutorials}

Guarda una di queste esercitazioni su [IBM&reg; Cloud Garage Method ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Aggiungi una toolchain a un'applicazione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
