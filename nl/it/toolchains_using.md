---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:tip: .tip}
{:important: .important}

# Utilizzo delle toolchain
{: #toolchains-using}

Le toolchain aperte sono disponibili negli ambienti Pubblico e Dedicato in {{site.data.keyword.Bluemix}}. Puoi utilizzare una toolchain per essere produttivo nella tua attività di sviluppo, distribuzione e nelle operazioni giornaliere. Dopo che hai configurato una toolchain, puoi aggiungere, eliminare o configurare le integrazioni dello strumento e gestire l'accesso alla toolchain.
{: shortdesc}

Puoi gestire le toolchain nelle regioni pubbliche Stati Uniti Sud, Stati Uniti Est, Regno Unito, Germania e Tokyo utilizzando i gruppi di risorse. Puoi utilizzare le organizzazioni Cloud Foundry per gestire le toolchain nelle regioni pubbliche Stati Uniti Sud, Regno Unito e Germania. Il controllo dell'accesso e la gestione dell'utente autorizzato funzionano in modo diverso per le toolchain a seconda se sono contenuti in un gruppo di risorse o in un'organizzazione Cloud Foundry.
{: important}

## Configurazione di un'integrazione dello strumento
{: #configuring_a_tool_integration}

Se hai differito la configurazione di un'integrazione dello strumento quando hai creato una toolchain, viene visualizzato un pulsante **Configura** nella relativa scheda. Se hai configurato un'integrazione dello strumento quando hai creato una toolchain, puoi aggiornare le impostazioni di configurazione.

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Se hai bisogno di configurare un'integrazione dello strumento per la prima volta, nella sua scheda, fai clic su **Configure**.

  ![Pulsante Configure](images/toolchain_tile_configure.png)

 Quando hai terminato la configurazione dell'integrazione dello strumento, fai clic su **Save Integration**.

1. Se hai bisogno di aggiornare la configurazione dell'integrazione dello strumento, nella sua scheda, fai clic sul menu per accedere alle opzioni di configurazione.

  ![Menu Configuration](images/toolchain_tile_menu.png)

 Alcune delle integrazioni dello strumento sono preconfigurate e non richiedono alcun parametro di configurazione. Puoi aggiornare le impostazioni di configurazione solo per le integrazioni dello strumento che hai configurato.
 {: tip}

 Quando hai terminato di aggiornare le impostazioni, fai clic su **Save Integration**. Per ulteriori informazioni sulla configurazione di specifiche integrazioni dello strumento, consulta [Configurazione delle integrazioni dello strumento](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}.

## Aggiunta di un'integrazione dello strumento
{: #adding_a_tool_integration}

Puoi aggiungere e configurare le integrazioni dello strumento per la tua toolchain. Le integrazioni dello strumento disponibili sono diverse a seconda se utilizzi {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato.

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Per visualizzare un elenco di integrazioni dello strumento da aggiungere, fai clic su **Add a tool**.
1. Fai clic sull'integrazione dello strumento che desideri aggiungere.
1. Immetti tutte le informazioni necessarie per configurare l'integrazione dello strumento.
1. Fai clic su **Create Integration** per aggiungere l'integrazione dello strumento alla tua toolchain.

## Eliminazione di un'integrazione dello strumento
{: #deleting_a_tool_integration}

Se elimini un'integrazione dello strumento dalla tua toolchain, l'eliminazione non può essere annullata.

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Nella scheda per l'integrazione dello strumento che desideri eliminare, fai clic sul menu per accedere alle opzioni di configurazione.
1. Per eliminare l'integrazione dello strumento dalla tua toolchain, fai clic su **Delete**.
1. Conferma facendo clic su **Delete**.  

## Gestione dell'accesso alle toolchain nei gruppi di risorse
{: #managing_access_resource_groups}

Puoi utilizzare il servizio IAM (Identity and Access Management) per gestire l'accesso utente alle toolchain. Per ulteriori informazioni sulla gestione del controllo dell'accesso con IAM, consulta [Gestione dell'accesso utente alle toolchain con Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}. 

Solo gli utenti che fanno parte dell'elenco di utenti autorizzati per l'istanza selezionata di {{site.data.keyword.contdelivery_short}} possono utilizzare le funzioni Delivery Pipeline, Eclipse Orion {{site.data.keyword.webide}} e {{site.data.keyword.gitrepos}} delle toolchain {{site.data.keyword.contdelivery_short}}. Puoi gestire la titolarità dell'utente autorizzato dalla scheda Manage dell'istanza selezionata di {{site.data.keyword.contdelivery_short}}, all'interno del gruppo di risorse specificato.

Per accedere alle funzioni chiave di {{site.data.keyword.contdelivery_short}} in una toolchain, ad esempio Delivery Pipeline, un utente deve avere accesso alla toolchain in IAM e deve far parte anche dell'elenco di utenti autorizzati dell'istanza {{site.data.keyword.contdelivery_short}}.
{: important}

La titolarità dell'utente autorizzato si applica a tutte le toolchain contenute nello stesso gruppo di risorse dell'istanza di {{site.data.keyword.contdelivery_short}}.
{: tip}


## Gestione dell'accesso alle toolchain nelle organizzazioni Cloud Foundry
{: #managing_access_orgs}

Puoi consentire agli utenti di accedere alla toolchain aggiungendoli all'organizzazione a cui è associata la toolchain e all'elenco del controllo dell'accesso per la toolchain. Ogni toolchain è associata a un'organizzazione specifica e ogni utente che è membro di tale organizzazione può essere aggiunto per accedere alle toolchain associate. L'organizzazione con cui stai attualmente lavorando è visualizzata nella barra dei menu. Per accedere a un diversa serie di toolchain, passa a un'altra organizzazione.

Devi aggiungere gli utenti all'organizzazione della toolchain nella regione in cui è ospitata la toolchain. Se la toolchain è stata configurata per distribuire le applicazioni in una regione differente, le distribuirà comunque a tale regione.
{: important}

Se stai utilizzando {{site.data.keyword.Bluemix_notm}} Dedicato per {{site.data.keyword.ghe_short}}, quando aggiungi gli utenti alla tua organizzazione o ai tuoi spazi {{site.data.keyword.Bluemix_notm}}, gli utenti possono accedere a {{site.data.keyword.ghe_short}} utilizzando i loro ID e password {{site.data.keyword.Bluemix_notm}}. Quando gli utenti accedono, vengono creati degli account per loro. Quando aggiungi utenti ai tuoi spazi o organizzazioni {{site.data.keyword.Bluemix_notm}}, non vengono automaticamente aggiunti al repository {{site.data.keyword.ghe_short}}. Qualcuno che dispone dei privilegi di amministratore per il repository li deve aggiungere. Per ulteriori informazioni, vedi [Using Dedicated GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started){: new_window}. Se stai utilizzando la tua propria versione gestita di {{site.data.keyword.ghe_short}}, segui le procedure interne.

###Suggerimenti per la gestione dell'accesso a una toolchain

* Per gestire l'accesso alla toolchain, nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain da gestire e quindi fai clic su **Manage**. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Manage**.

* Per concedere l'accesso a tutti i membri dell'organizzazione della toolchain, fai clic su **Add org**. Tutti i membri di tale organizzazione possono visualizzare la toolchain.

* Puoi concedere i privilegi di amministratore a un'organizzazione o un utente. Gli amministratori possono modificare ed eliminare la toolchain. Per concedere i privilegi di amministratore, seleziona la casella di spunta **ADMIN** per l'organizzazione o l'utente.

* Se selezioni la casella di spunta **ADMIN** per un'organizzazione, tutti i membri di tale organizzazione diventano amministratori. Se aggiungi membri all'organizzazione dopo aver concesso i privilegi di amministratore all'organizzazione, a questi membri viene fornito lo stesso accesso degli altri membri nell'organizzazione.

* Per concedere l'accesso a un utente che è membro dell'organizzazione della toolchain, immetti l'ID dell'utente e fai clic su **Add user**. L'utente può visualizzare la toolchain.

* Per concedere l'accesso a un utente che non è membro dell'organizzazione della toolchain, completa la seguente procedura:

   a. Dalla barra dei menu, fai clic su **Gestisci > Accesso (IAM)**.

   b. Fai clic su **L'accesso inizia con l'utente**.
   
   c. Dalla riga per l'utente a cui vuoi assegnare l'accesso, seleziona il menu **Azioni** e fai quindi clic su **Assegna accesso**.
   
   d. Seleziona **Assegna l'accesso utilizzando Cloud Foundry**.

   e. Seleziona **Assegna organizzazione**.

   f. Assegna l'accesso utente:

     * Scegli un'organizzazione a cui aggiungere l'utente.

     * Assegna un ruolo organizzazione.

     * Scegli una regione.

     * Scegli uno spazio.

     * Assegna un ruolo per lo spazio selezionato nell'organizzazione.

     Per impostazione predefinita, i gestori dell'organizzazione hanno tutti i privilegi di amministratore per tutte le toolchain associate ad essa. Per concedere tutti i privilegi di amministratore all'utente, seleziona il ruolo **Gestore**. I ruoli Gestore della fatturazione e Revisore non influenzano l'accesso alla toolchain. Puoi modificare i ruoli successivamente nella pagina della directory del team. Per ulteriori informazioni, consulta [Ruoli Cloud Foundry](/docs/iam?topic=iam-cfaccess#cfaccess){: new_window}.
     {: tip}

   Dopo che l'utente è un membro dell'organizzazione, ritorna alla pagina di gestione della toolchain e aggiungi l'utente alla toolchain.  


## Eliminazione di una toolchain
{: #deleting_a_toolchain}

Puoi eliminare una toolchain e specificare quali delle integrazioni dello strumento associate desideri eliminare. Quando elimini una toolchain, l'eliminazione non può essere annullata.

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain da eliminare. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain**.
1. Fai clic sul menu **More Actions**, accanto a **View app**.
1. Fai clic su **Delete**. L'eliminazione di una toolchain rimuove tutte le sue integrazioni dello strumento e ciò potrebbe eliminare le risorse gestite da tali integrazioni.
1. Conferma l'eliminazione digitando il nome della toolchain e facendo clic su **Delete**.  

 Quando elimini un GitHub, {{site.data.keyword.ghe_short}} o l'integrazione dello strumento {{site.data.keyword.gitrepos}}, il repository associato non viene eliminato da GitHub, {{site.data.keyword.ghe_short}} o {{site.data.keyword.gitrepos}}. Devi rimuovere il repository manualmente.
 {: tip}

##Visualizza una esercitazione: utilizzo delle toolchain
{: #toolchain-tutorial}

Guarda queste esercitazioni in [IBM&reg; Cloud Garage Method ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Aggiungi una toolchain a un'applicazione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
