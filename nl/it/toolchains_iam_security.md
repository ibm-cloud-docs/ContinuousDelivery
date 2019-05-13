---

copyright:
  years:  2018, 2019
lastupdated: "2019-02-27"

keywords: Administrator Create, Editor Update, Update, user access

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gestione dell'accesso utente alle toolchain con Identity and Access Management
{: #toolchains-iam-security}

L'accesso alle toolchain nei gruppi di risorse per gli utenti nel tuo account viene controllato da {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Note**: 

* L'accesso utente per le istanze del servizio {{site.data.keyword.contdelivery_short}} e le istanze della toolchain viene gestito separatamente. Per ulteriori informazioni sulla gestione dell'accesso utente alle istanze del servizio {{site.data.keyword.contdelivery_short}} nei gruppi di risorse, consulta [Gestione dell'accesso utente a {{site.data.keyword.contdelivery_short}} con Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security){: new_window}.

* L'accesso utente alle toolchain nelle organizzazioni Cloud Foundry viene gestito in modo diverso rispetto a quello delle istanze del servizio {{site.data.keyword.contdelivery_short}} nei gruppi di risorse. Per ulteriori informazioni sulla gestione dell'accesso utente alle toolchain nelle organizzazioni Cloud Foundry, consulta [Gestione dell'accesso utente alle toolchain nelle organizzazioni Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.

Ogni utente che accede alle toolchain nel tuo account deve avere assegnata una politica di accesso con un ruolo utente IAM definito. Tale politica determina quali azioni possono essere effettuate dall'utente all'interno del contesto del servizio o dell'istanza che selezioni. Le azioni consentite sono personalizzate e definite dal servizio {{site.data.keyword.Bluemix_notm}} come operazioni che è consentito eseguire sul servizio. Le azioni vengono poi associate ai ruoli utente IAM.

Le politiche consentono di concedere l'accesso a diversi livelli, tra cui: 

* Accesso a tutte le istanze del servizio nel tuo account
* Accesso a una singola istanza del servizio nel tuo account
* Accesso a una risorsa specifica all'interno di un'istanza
* Accesso a tutti i servizi abilitati IAM nel tuo account

Dopo aver definito l'ambito della politica di accesso, assegna un ruolo. Esamina le seguenti tabelle che descrivono quali azioni sono consentite da ciascun ruolo all'interno delle toolchain.

La seguente tabella illustra le azioni che sono associate ai ruoli di gestione della piattaforma. I ruoli di gestione della piattaforma consentono agli utenti di eseguire le attività sulle risorse del servizio a livello di piattaforma, ad esempio assegnare l'accesso utente per il servizio, creare o eliminare l'ID servizio, creare le istanze e associare le istanze alle applicazioni.

| Ruolo di gestione della piattaforma | Descrizione delle azioni | Azioni di esempio|
|:-----------------|:-----------------|:-----------------|
| Visualizzatore, Operatore | Visualizza le toolchain e le delivery pipeline. Esegue le delivery pipeline. | <ul><li>Fai clic su una toolchain per aprire la relativa pagina Overview.</li><li>Fai clic sull'icona **Run Stage** della fase in cui si trova il tuo lavoro della pipeline.</li></ul> |
| Editor, Amministratore | Crea, visualizza, aggiorna ed elimina le toolchain e le delivery pipeline. |<ul><li>Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su **Create a Toolchain**.</li><li>Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain per aprirne la pagina di panoramica.</li><li>Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain da eliminare. Fai clic sul menu **More Actions**, accanto a **View app**. Fai clic su **Delete**.</li></ul> |
{: caption="Tabella 1. Azioni e ruoli utente IAM" caption-side="top"}

 Per le toolchain, esistono le seguenti azioni:

| Azione | Operazione nel servizio | Ruolo
|:-----------------|:-----------------|:--------------|
| create | Crea una toolchain in un gruppo di risorse. | Amministratore, Editor |
| update | Aggiorna una toolchain in un gruppo di risorse. Ad esempio, ridenomina la toolchain. Modifica le delivery pipeline collegate alle toolchain in un gruppo di risorse. | Amministratore, Editor |
| update_plan | Non applicabile. | Amministratore, Editor |
| delete | Elimina una toolchain da un gruppo di risorse. | Amministratore, Editor |
| retrieve | Visualizza i dettagli per una toolchain in un gruppo di risorse. Visualizza ed esegue le delivery pipeline collegate alle toolchain in un gruppo di risorse. | Amministratore, Editor, Operatore, Visualizzatore |
| list-bindings | Visualizza le integrazioni dello strumento collegate a una toolchain in un gruppo di risorse. | Amministratore, Editor, Visualizzatore |
| create-bindings | Aggiunge un'integrazione dello strumento a una toolchain in un gruppo di risorse. | Amministratore, Editor |
| delete-bindings | Rimuove un'integrazione dello strumento da una toolchain in un gruppo di risorse. | Amministratore, Editor |
{: caption="Tabella 2. Operazioni e azioni del servizio" caption-side="top"}

Per informazioni sull'assegnazione dei ruoli utente nell'IU, consulta [Gestione accesso IAM](/docs/iam?topic=iam-iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
