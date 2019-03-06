---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-7"

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


# Esercitazione introduttiva
{: #cd_getting_started}

Adotta un approccio DevOps utilizzando {{site.data.keyword.contdelivery_full}}, che include le toolchain aperte che automatizzano la creazione e la distribuzione di applicazioni. Puoi iniziare creando una semplice toolchain di distribuzione che supporta le attività operative, di sviluppo e di distribuzione. 
{: shortdesc}

##Prerequisiti
{: #cd_prereqs}

Prima di poter creare una toolchain di fornitura continua da un template, devi creare un'istanza di {{site.data.keyword.contdelivery_short}} selezionandola dal catalogo {{site.data.keyword.Bluemix_notm}}. La toolchain integra gli strumenti per la pianificazione, lo sviluppo, la distribuzione di pipeline e la gestione delle tue applicazioni. Puoi sempre aggiungere o rimuovere strumenti dalla toolchain. Se già disponi di una toolchain, puoi [visualizzare le toolchain esistenti](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing_a_toolchain){: new_window}. Per ulteriori informazioni sull'utilizzo delle toolchain, vedi [Gestione delle toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using){: new_window}.

Se già disponi di un'istanza di {{site.data.keyword.contdelivery_short}}, puoi [creare una toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/devops/create){: new_window} o [visualizzare le toolchain esistenti ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/devops/toolchains){: new_window}.
{: tip}

##Passo 1: seleziona un template di toolchain
{: #select_a_toolchain_template}

1. Nella pagina **Create a Toolchain**, fai clic su un [template di toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/devops/create){: new_window}.
1. Esamina il diagramma della toolchain che stai per creare. Il diagramma mostra ogni integrazione dello strumento nella fase del suo ciclo di vita nella toolchain.

 Alcuni template della toolchain dispongono di più istanze di un'integrazione dello strumento. Ad esempio, il template della toolchain Microservizi su {{site.data.keyword.Bluemix_notm}} Pubblico contiene tre istanze di GitHub e tre di Delivery Pipeline, una per ognuno dei tre microservizi.
 {: tip}

 Il diagramma nella seguente immagine è un esempio. Quando crei una toolchain, il diagramma mostra ogni integrazione dello strumento che fa parte della toolchain.
 ![Diagramma_toolchain](images/toolchain_diagram2.png)
 
##Passo 2: crea una toolchain 
{: #create_a_toolchain}
 
1. Rivedi le informazioni predefinite per la configurazione della toolchain:

 * Il nome della toolchain la identifica in {{site.data.keyword.Bluemix_notm}}. Se vuoi utilizzare un nome diverso, modifica il nome della toolchain.
 * La regione in cui creare la toolchain. Se vuoi utilizzare una regione differente, selezionala dall'elenco delle regioni disponibili.
 * L'organizzazione o il gruppo di risorse in cui creare la toolchain. Fai clic sul link per passare dalla selezione di gruppi di risorse alle organizzazioni. Se vuoi utilizzare una organizzazione o un gruppo di risorse differente, selezionalo dall'elenco di organizzazioni o gruppi di risorse disponibili.
 
   I gruppi di risorse sono disponibili nelle regioni Stati Uniti Sud, Stati Uniti Est, Regno Unito, Germania e Tokyo. Le organizzazioni Cloud Foundry sono supportate nelle regioni Stati Uniti Sud, Regno Unito e Germania.
   {: important}
 
1. Nella sezione Integrazioni dello strumento, seleziona ogni integrazione dello strumento che desideri configurare per la tua toolchain. Alcune delle integrazioni dello strumento non richiedono configurazione. Per informazioni sulla configurazione delle integrazioni dello strumento, consulta [Configurazione delle integrazioni dello strumento](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}.
1. Fai clic su **Create**. Diversi passi vengono eseguiti automaticamente per configurare la tua toolchain. Le integrazioni dello strumento configurate a seconda della toolchain selezionata e se stai utilizzando {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato. Ad esempio, quando crei una toolchain Microservizi in {{site.data.keyword.Bluemix_notm}} Pubblico, deve essere eseguita questa procedura:

 * La toolchain viene creata.
 * Se hai configurato Delivery Pipeline, le pipeline vengono create ed eseguite.
 * Se hai configurato Sauce Labs, la toolchain viene configurata per aggiungere i lavori di verifica Sauce Labs alle pipeline.
 * Se hai configurato PagerDuty, la toolchain viene configurata per inviare notifiche di avviso al servizio PagerDuty che hai specificato.
 * Se hai configurato Slack, la toolchain viene configurata per inviare notifiche sullo stato della distribuzione al canale Slack che hai specificato.
 * Se hai configurato un'integrazione dello strumento del codice sorgente come GitHub, il repository GitHub di esempio viene clonato nel tuo account GitHub.

##Passi successivi
{: #next_steps}

Guarda una di queste esercitazioni su [IBM&reg; Cloud Garage Method ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Aggiungi una toolchain a un'applicazione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.
