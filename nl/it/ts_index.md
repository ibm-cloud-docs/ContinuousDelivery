---

copyright:
  years: 2015, 2018
lastupdated: "2018-7-19"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Domande frequenti (FAQ)
{: #ts_cd}

Ottieni le risposte alle domande frequenti sull'utilizzo di {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Ho provato ad aggiungere l'integrazione dello strumento GitHub alla mia toolchain, perché l'integrazione dello strumento non è stata aggiunta?
{: #cannot_authorize_github}

Se {{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere al tuo account GitHub, l'integrazione dello strumento non viene aggiunta alla tua toolchain.

Se stai configurando l'integrazione dello strumento GitHub mentre stai creando la tua toolchain, attieniti alla seguente procedura per eseguire l'autorizzazione presso GitHub:

  1. Nella sezione delle integrazioni configurabili, fai clic su **GitHub**.
  1. Se stai creando la toolchain in {{site.data.keyword.Bluemix_notm}} Pubblico e {{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere a GitHub, fai clic su **Autorizza** per andare al sito web GitHub.
  1. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub.

Se già disponi di una toolchain, aggiorna la configurazione dell'integrazione dello strumento GitHub:

 1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
 1. Nella scheda GitHub, fai clic sul menu e su **Configure**.
 1. Aggiorna le impostazioni di configurazione per autorizzare {{site.data.keyword.Bluemix_notm}} ad accedere a GitHub. Fai clic su **Authorize** per andare al sito web GitHub. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub.
 1. Quando hai terminato di aggiornare le impostazioni, fai clic su **Save Integration**.


## Ho provato a creare una toolchain, perché sto ottenendo un errore?
{: #cannot_create_toolchain}

Quando provi a creare una toolchain in un'organizzazione, se ottieni il seguente messaggio di errore, rimuovi una o più toolchain dalla tua organizzazione e quindi crea nuovamente la tua toolchain.

`Questa organizzazione contiene 200 toolchain, che è il limite massimo. Prima di poter aggiungere un'altra toolchain, rimuovere una o più toolchain dall'organizzazione.`


## Perché la pagina Toolchains mostra che il piano Lite del servizio {{site.data.keyword.contdelivery_short}} è stato superato?

{{site.data.keyword.contdelivery_short}} offre due piani: Lite e Professional. Se hai il piano {{site.data.keyword.contdelivery_short}} Lite, puoi utilizzare le toolchain gratuitamente, fino ai limiti del piano. Il messaggio di errore indica che è stato superato uno o più limiti del piano Lite. Ad esempio, potresti aver superato il piano se hai troppi utenti autorizzati associati all'istanza del servizio {{site.data.keyword.contdelivery_short}} o se hai eseguito il numero massimo di lavori {{site.data.keyword.deliverypipeline}}. Per ulteriori informazioni sui termini del piano, consulta [Utilizzo e limitazioni del piano](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## Ho creato una toolchain, perché la pagina Toolchains mostra che è necessario un servizio Continuous Delivery?

I termini del piano per l'istanza del servizio {{site.data.keyword.contdelivery_short}} che si trova nello stesso gruppo di risorse o organizzazione della toolchain gestisce l'utilizzo di alcune integrazioni dello strumento ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} e {{site.data.keyword.gitrepos}}) contenute nel servizio. Il messaggio di errore indica che il gruppo di risorse o l'organizzazione non contiene l'istanza richiesta del servizio {{site.data.keyword.contdelivery_short}}. Per ulteriori informazioni sui termini del piano, consulta [Utilizzo e limitazioni del piano](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## Ho creato una toolchain in un'organizzazione Cloud Foundry, perché la pagina Toolchains mostra che è necessario un servizio Continuous Delivery?

Quando crei una toolchain in un gruppo di risorse o un'organizzazione che non dispone di un'istanza del servizio {{site.data.keyword.contdelivery_short}}, la piattaforma della toolchain tenta di creare automaticamente un'istanza del servizio utilizzando il piano Lite. Il messaggio di errore indica che la piattaforma della toolchain non è riuscita a creare l'istanza del servizio.

Questo errore potrebbe verificarsi quando crei una toolchain nella regione Stati Uniti Sud e in un'organizzazione che non dispone ancora di un istanza di {{site.data.keyword.contdelivery_short}}. Nella regione Stati Uniti Sud, devi creare tutte le nuove istanze del servizio {{site.data.keyword.contdelivery_short}} nei gruppi di risorse. 

Puoi creare la toolchain in un gruppo di risorse o in un'organizzazione che dispone già di un'istanza di {{site.data.keyword.contdelivery_short}}.
  

## Ho provato a distribuire un'applicazione a {{site.data.keyword.Bluemix_notm}}, perché sto ottenendo un errore?
{: #org_outofmemory}

Quando provi a distribuire un'applicazione a {{site.data.keyword.Bluemix_notm}}, se ottieni il seguente messaggio di errore, la quantità di memoria residua nella tua organizzazione è inferiore a quella richiesta dall'applicazione che vuoi distribuire.

`Errore Server NON RIUSCITO, codice stato: 400, codice errore: 100005, messaggio: Hai superato il limite di memoria della tua organizzazione.`

Puoi aumentare la quota di memoria del tuo account o ridurre la memoria utilizzata dalle tue applicazioni. La quota massima di memoria per un account di prova è 2 GB. Per aumentare la quota di memoria dell'account, converti il tuo account di prova in un account a pagamento. Per informazioni
su come convertire il tuo account di prova in un account a pagamento, vedi [Account a pagamento](/docs/pricing/index.html#pay-accounts). Per ridurre la memoria utilizzata dalle tue applicazioni, utilizza la console {{site.data.keyword.Bluemix_notm}} o l'interfaccia riga di comando cf.

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


## Ho creato un'applicazione, perché la barra di esecuzione non mostra le icone {{site.data.keyword.Bluemix_notm}} Live Sync in Eclipse Orion Web IDE?
{: #ts_llz_lkb_3r}

![Barra di esecuzione](images/webide_runbar_light.png)   

Quando modifichi un'applicazione Node.js in Web IDE, le icone di live edit, riavvio rapido e debug di {{site.data.keyword.Bluemix_notm}} non sono disponibili nella barra di esecuzione nelle seguenti circostanze:


* Il file `manifest.yml` non è memorizzato al livello principale del tuo progetto.
* La tua applicazione è memorizzata in una sottodirectory anziché nella root, ma il percorso della sottodirectory non è specificato nel file `manifest.yml`.
* L'applicazione non contiene un file `package.json`.


Se il file `manifest.yml` non è memorizzato nella root, memorizzalo lì. Se la tua applicazione è memorizzata in una sottodirectory, specifica il percorso di tale sottodirectory nel file `manifest.yml`. Se l'applicazione non contiene un file `package.json`, crearne uno che si trovi nella stessa directory della tua applicazione.


## Ho fatto clic su una toolchain per visualizzare la relativa pagina di panoramica, perché la toolchain non viene caricata?
{: #toolchains_load}

Controlla la pagina relativa allo stato di {{site.data.keyword.Bluemix_notm}} per determinare la presenza di problemi noti che interessano la piattaforma {{site.data.keyword.Bluemix_notm}} e i servizi principali in {{site.data.keyword.Bluemix_notm}}.

Puoi individuare la pagina Stato scegliendo una delle seguenti opzioni:

  * Accedi alla console {{site.data.keyword.Bluemix_notm}}. Dalla barra dei menu, fai clic su **Supporto** e seleziona **Stato**. Controlla le risorse elencate per l'icona di ![alcuni problemi](../../get-support/images/some_issues.svg). Questa icona potrebbe indicare un'interruzione.
  * Accedi ad essa direttamente nella pagina di [stato dei sistemi {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/status){: new_window}.

Per ulteriori informazioni sulla pagina relativa allo stato di {{site.data.keyword.Bluemix_notm}}, consulta [Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/get-support/ViewStatus.html#viewing-bluemix-status).


## Ho configurato un'integrazione dello strumento per la mia toolchain, perché non è stata configurata?
{: #tool_integration_error}

Quando aggiungi un'integrazione dello strumento, la toolchain comunica con lo strumento rappresentato dall'integrazione dello strumento per eseguire il provisioning di tutte le risorse e le associa alla toolchain. Se si verifica un errore nel processo di configurazione o se la comunicazione tra la toolchain e lo strumento non viene completata correttamente, l'integrazione dello strumento viene messa in uno stato di errore.

 ![Errore configurazione non riuscita](images/tool_setup_failed.png)

Puoi provare a configurare nuovamente l'integrazione dello strumento:

1. Nella relativa scheda, passa con il mouse sul messaggio `Setup failed` e fai clic su **Reconfigure**.

 ![Pulsante riconfigura](images/tool_reconfigure.png)

1. Assicurati di stare utilizzando dei parametri di configurazione validi. Se l'errore è stato causato da una configurazione non valida, viene visualizzato un messaggio di errore; ad esempio, `Impossibile configurare l'integrazione. Controlla le impostazione e riprova. Motivo: Invalid api_key:fakeKey`. Aggiorna le impostazioni per l'integrazione dello strumento e fai clic su **Save integration**.
1. Se l'errore è stato causato da un problema di comunicazione, fai clic su **Save integration** per ritentare.
