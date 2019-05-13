---

copyright:
  years:  2018, 2019
lastupdated: "2019-02-25"

keywords: Administrator Create, Administrator Update, Editor Update, Update

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


# Gestione dell'accesso utente per la fornitura continua con Identity and Access Management
{: #cd-iam-security}

L'accesso alle risorse del servizio {{site.data.keyword.contdelivery_full}} nei gruppi di risorse per gli utenti nel tuo account viene controllato da {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Note**: 

* L'accesso utente per le istanze del servizio {{site.data.keyword.contdelivery_short}} e le istanze della toolchain viene gestito separatamente. Per ulteriori informazioni sulla gestione dell'accesso utente alle toolchain nei gruppi di risorse, consulta [Gestione dell'accesso utente alle toolchain con Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}.

* L'accesso utente alle toolchain nelle organizzazioni Cloud Foundry viene gestito in modo diverso rispetto a quello nei gruppi di risorse. Per ulteriori informazioni sulla gestione dell'accesso utente alle toolchain nelle organizzazioni Cloud Foundry, consulta [Gestione dell'accesso utente alle toolchain nelle organizzazioni Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.

Ogni utente che accede al servizio {{site.data.keyword.contdelivery_short}} nel tuo account deve avere assegnata una politica di accesso con un ruolo utente IAM definito. Tale politica determina quali azioni possono essere effettuate dall'utente all'interno del contesto del servizio o dell'istanza che selezioni. Le azioni consentite sono personalizzate e definite dal servizio {{site.data.keyword.Bluemix_notm}} come operazioni che è consentito eseguire sul servizio. Le azioni vengono poi associate ai ruoli utente IAM.

Le politiche consentono di concedere l'accesso a diversi livelli. Alcune delle opzioni includono quanto segue: 

* Accesso a tutte le istanze del servizio nel tuo account
* Accesso a una singola istanza del servizio nel tuo account
* Accesso a una risorsa specifica all'interno di un'istanza
* Accesso a tutti i servizi abilitati IAM nel tuo account

Dopo aver definito l'ambito della politica di accesso, assegna un ruolo. Esamina le seguenti tabelle che descrivono quali azioni sono consentite da ciascun ruolo all'interno del servizio {{site.data.keyword.contdelivery_short}}.

La seguente tabella illustra le azioni che sono associate ai ruoli di gestione della piattaforma. I ruoli di gestione della piattaforma consentono agli utenti di eseguire le attività sulle risorse del servizio a livello di piattaforma, ad esempio assegnare l'accesso utente per il servizio, creare o eliminare l'ID servizio, creare le istanze e associare le istanze alle applicazioni.

| Ruolo di gestione della piattaforma | Descrizione delle azioni | Azioni di esempio|
|:-----------------|:-----------------|:-----------------|
| Visualizzatore, Operatore | Visualizza le istanze del servizio {{site.data.keyword.contdelivery_short}}. | <ul><li>Fa clic su un'istanza del servizio {{site.data.keyword.contdelivery_short}} per aprirne il dashboard.</li></ul>|
| Editor, Amministratore | Crea, visualizza, aggiorna, modifica il piano ed elimina le istanze del servizio {{site.data.keyword.contdelivery_short}}. |<ul><li>Esegui il provisioning di un'istanza di {{site.data.keyword.contdelivery_short}} in un gruppo di risorse.</li><li>Elimina un'istanza di {{site.data.keyword.contdelivery_short}} da un gruppo di risorse.</li><li>Modifica un piano dell'istanza di {{site.data.keyword.contdelivery_short}} da Lite a Professional.</li></ul> |
| Amministratore | Aggiorna l'elenco degli utenti autorizzati.| <ul><li>Aggiunge un utente all'elenco di utenti autorizzati.</li><li>Rimuove un utente dall'elenco di utenti autorizzati.</li></ul> |
{: caption="Tabella 1. Azioni e ruoli utente IAM" caption-side="top"}

 Per {{site.data.keyword.contdelivery_short}}, esistono le seguenti azioni:

| Azione | Operazione nel servizio | Ruolo
|:-----------------|:-----------------|:--------------|
| create | Esegue il provisioning di un'istanza del servizio {{site.data.keyword.contdelivery_short}} in un gruppo di risorse. | Amministratore, Editor |
| update | Aggiorna un'istanza del servizio {{site.data.keyword.contdelivery_short}} in un gruppo di risorse. Ad esempio, ridenomina l'istanza del servizio. | Amministratore, Editor |
| update_plan | Modifica il piano per l'istanza del servizio {{site.data.keyword.contdelivery_short}} in un gruppo di risorse. | Amministratore, Editor |
| delete | Elimina un'istanza del servizio {{site.data.keyword.contdelivery_short}} da un gruppo di risorse. | Amministratore, Editor |
| retrieve | Visualizza un'istanza del servizio {{site.data.keyword.contdelivery_short}} in un gruppo di risorse. | Amministratore, Editor, Operatore, Visualizzatore |
| add-auth-users | Aggiunge le voci all'elenco degli utenti autorizzati nella scheda di gestione all'interno dell'istanza del servizio {{site.data.keyword.contdelivery_short}}. | Amministratore, Scrittore, Gestore |
| remove-auth-users | Rimuove le voci dall'elenco degli utenti autorizzati nella scheda di gestione all'interno dell'istanza del servizio {{site.data.keyword.contdelivery_short}}. | Amministratore, Scrittore, Gestore |
{: caption="Tabella 2. Operazioni e azioni del servizio" caption-side="top"}

La seguente tabella illustra le azioni che sono associate ai ruoli di accesso al servizio. I ruoli di accesso al servizio consentono agli utenti di accedere a {{site.data.keyword.contdelivery_short}} così come di richiamare l'API {{site.data.keyword.contdelivery_short}}.

| Ruolo di accesso al servizio | Descrizione delle azioni | Azioni di esempio|
|:-----------------|:-----------------|:-----------------|
| Scrittore, Gestore | Aggiunge e rimuove gli utenti autorizzati nella scheda di gestione all'interno di un'istanza del servizio {{site.data.keyword.contdelivery_short}}. | <ul><li>Aggiunge l'utente autorizzato.</li><li>Rimuove l'utente autorizzato.</li></ul>|
{: caption="Tabella 3. Azioni e ruoli di accesso al servizio IAM" caption-side="top"}

Per informazioni sull'assegnazione dei ruoli utente nell'IU, consulta [Gestione accesso IAM](/docs/iam?topic=iam-iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
