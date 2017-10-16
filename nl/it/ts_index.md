---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Risoluzione dei problemi {{site.data.keyword.contdelivery_short}}
{: #ts_cd}

Ottieni le risposte alle domande di risoluzione dei problemi comuni sull'utilizzo di {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Impossibile eseguire l'autorizzazione con GitHub
{: #cannot_authorize_github}

Non sei autorizzato con GitHub.
{:shortdesc}

Se {{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere al tuo account GitHub, può verificarsi uno di questi problemi:
{: tsSymptoms}

 * Quando tenti di aggiungere un'integrazione dello strumento GitHub alla tua toolchain, l'integrazione dello strumento non viene aggiunta.
 * La pipeline non viene eseguita automaticamente quando trasmetti le modifiche al tuo repository GitHub o GitHub Enterprise.

{{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere a GitHub.  
{: tsCauses}

Se stai configurando l'integrazione dello strumento GitHub mentre stai creando la tua toolchain, segui questi passi:
{: tsResolve}

  1. Nella sezione delle integrazioni configurabili, fai clic su **GitHub**.
  1. Se stai creando la toolchain in {{site.data.keyword.Bluemix_notm}} pubblico e {{site.data.keyword.Bluemix_notm}} non è autorizzato ad accedere a GitHub, fai clic su **Autorizza** per andare al sito web GitHub.
  1. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub.

Se già disponi di una toolchain, aggiorna la configurazione dell'integrazione dello strumento GitHub:

 1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic sulla toolchain per aprirne la pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
 1. Nella scheda GitHub, fai clic sul menu e su **Configure**.
 1. Aggiorna le impostazioni di configurazione per autorizzare {{site.data.keyword.Bluemix_notm}} ad accedere a GitHub. Fai clic su **Authorize** per andare al sito web GitHub. Se non disponi di una sessione GitHub attiva, ti viene richiesto di accedere. Fai clic su **Authorize Application** per consentire a {{site.data.keyword.Bluemix_notm}} di accedere al tuo account GitHub.
 1. Quando hai terminato di aggiornare le impostazioni, fai clic su **Save Integration**.


## Impossibile creare una toolchain
{: #cannot_create_toolchain}

Quando crei una toolchain, viene visualizzato un errore.
{:shortdesc}

Quando crei una toolchain, vedi il seguente messaggio di errore:
{: tsSymptoms}

`Questa organizzazione contiene 200 toolchain, che è il limite massimo. Prima di poter aggiungere un'altra toolchain, rimuovere una o più toolchain dall'organizzazione.`

Non puoi avere più di 200 toolchain in un'organizzazione (org)  
{: tsCauses}

Rimuovi una o più toolchain dalla tua organizzazione e crea quindi nuovamente la tua toolchain.
{: tsResolve}


## Il limite di memoria dell'organizzazione è stato superato
{: #org_outofmemory}

Potresti non riuscire a distribuire un'applicazione a {{site.data.keyword.Bluemix_notm}} se hai superato il limite di memoria della tua organizzazione. Puoi
ridurre la memoria utilizzata dalle tue applicazioni o aumentare la quota di memoria
del tuo account. La quota massima di memoria per un account di prova è 2 GB. È possibile aumentare la quota quando esegui l'upgrade a un account a pagamento.

Quando distribuisci un'applicazione a {{site.data.keyword.Bluemix_notm}}, vedi il seguente messaggio di errore:
{: tsSymptoms}

`Errore Server NON RIUSCITO, codice stato: 400, codice errore: 100005, messaggio: Hai superato il limite di memoria della tua organizzazione.`

Questo errore si verifica quando la quantità di memoria rimanente per la tua organizzazione è inferiore alla quantità di memoria richiesta dall'applicazione che desideri distribuire. La quota massima di memoria per un account di prova è 2 GB.
{: tsCauses}

Puoi aumentare la quota di memoria del tuo account o ridurre la memoria utilizzata dalle tue applicazioni.
{: tsResolve}

  * Per aumentare la quota di memoria dell'account, converti il tuo account di prova in un account a pagamento. Per informazioni
su come convertire il tuo account di prova in un account a pagamento, vedi [Account a pagamento](/docs/pricing/index.html#pay-accounts).
  * Per ridurre la memoria utilizzata dalle tue applicazioni, utilizza la console {{site.data.keyword.Bluemix_notm}} o l'interfaccia della riga di comando cf.

    Se utilizzi la console {{site.data.keyword.Bluemix_notm}}, completa la seguente procedura:

    1. Nel dashboard delle applicazioni, seleziona la tua applicazione. Viene visualizzata la pagina dei dettagli dell'applicazione.
    2. Nel riquadro runtime, puoi ridurre il limite massimo di memoria o il numero di istanze dell'applicazione, o entrambi, per tua applicazione.

    Se utilizzi l'interfaccia riga di comando cf, completa la seguente procedura:

    1. Verifica la quantità di memoria utilizzata per le tue applicazioni:

	  ```
	  cf apps
	  ```

	  Il comando cf apps elenca tutte le applicazioni che hai distribuito nel tuo spazio corrente. Viene visualizzato anche lo stato di ciascuna applicazione.

    2. Per ridurre la quantità di memoria utilizzata dalla tua applicazione, riduci il numero di istanze dell'applicazione e/o il limite massimo di memoria.

	  ```
	  cf push appname -p percorso_applicazione -i numero_istanza -m limite_memoria
      ```

    3. Riavvia la tua applicazione per rendere effettive le modifiche.

Per ulteriori informazioni sui problemi generali con la gestione delle tue applicazioni, consulta [Risoluzione dei problemi relativi alla gestione delle applicazioni](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps).


## La barra di esecuzione non mostra le icone di Bluemix Live Sync in Eclipse Orion Web IDE
{: #ts_llz_lkb_3r}

Hai creato un'applicazione, ma le icone di IBM Bluemix Live Sync non vengono visualizzate nella barra di esecuzione di Eclipse Orion Web IDE.  Non visualizzi l'intera barra di esecuzione con le icone di Live Edit:

![Barra di esecuzione](images/webide_runbar_light.png)   

Quando modifichi un'applicazione Node.js in Web IDE, le icone live edit, quick restart e debug di {{site.data.keyword.Bluemix_notm}} non vengono visualizzate nella barra di esecuzione.
{: tsSymptoms}

Le icone non sono disponibili nelle seguenti circostanze:
{: tsCauses}

* Il file `manifest.yml` non è memorizzato al livello principale del tuo progetto.
* La tua applicazione è memorizzata in una sottodirectory anziché nella root, ma il percorso della sottodirectory non è specificato nel file `manifest.yml`.
* L'applicazione non contiene un file `package.json`.

Utilizza uno dei seguenti metodi:
{: tsResolve}

* Se il file `manifest.yml` non è memorizzato nella root, memorizzalo lì.
* Se la tua applicazione è memorizzata in una sottodirectory, specifica il percorso di tale sottodirectory nel file `manifest.yml`.
   ```
    path: path_to_application
    ```
* Crea un file `package.json` che si trovi nella stessa directory della tua applicazione.


## La toolchain non viene caricata
{: #toolchains_load}

Quando fai clic su una toolchain per visualizzare la relativa pagina di panoramica, la toolchain non viene caricata.
{:shortdesc}

Nel dashboard DevOps, nella pagina **Toolchains**, fai clic sulla toolchain per aprire la relativa pagina di panoramica. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View toolchain**. Fai quindi clic su **Overview**. La pagina di panoramica per la toolchain non si apre.
{: tsSymptoms}

Controlla lo stato di {{site.data.keyword.Bluemix_notm}} per appurare se il problema è causato da un'interruzione.
{: tsCauses}

Visualizza la pagina Stato di {{site.data.keyword.Bluemix_notm}} per determinare la presenza di problemi noti che interessano la piattaforma {{site.data.keyword.Bluemix_notm}} e i servizi principali in {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Puoi individuare la pagina Stato scegliendo una delle seguenti opzioni:

  * Accedi alla console {{site.data.keyword.Bluemix_notm}}. Dalla barra dei menu, fai clic su **Supporto** e seleziona **Stato**. Controlla le risorse elencate per l'icona di ![alcuni problemi](../../support/images/some_issues.svg). Questa icona potrebbe indicare un'interruzione.
  * Accedi ad essa direttamente su [IBM {{site.data.keyword.Bluemix_notm}} - Stato del sistema ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://ibm.biz/bluemixstatus){: new_window}.

Per ulteriori informazioni sulla pagina Stato di {{site.data.keyword.Bluemix_notm}}, consulta [Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status).


## L'integrazione dello strumento non è configurata
{: #tool_integration_error}

Dopo aver configurato un'integrazione dello strumento per la tua toolchain, viene visualizzato l'errore `Setup failed` nella scheda dello strumento.
{:shortdesc}

Dopo aver configurato un'integrazione dello strumento, ne visualizzi la scheda dello strumento nella pagina della panoramica della toolchain e noti che la configurazione ha avuto esito negativo.
{: tsSymptoms}

 ![Errore configurazione non riuscita](images/tool_setup_failed.png)

Quando aggiungi un'integrazione dello strumento, la toolchain comunica con lo strumento rappresentato dall'integrazione dello strumento per eseguire il provisioning di tutte le risorse e le associa alla toolchain. Se si verifica un errore nel processo di configurazione o se la comunicazione tra la toolchain e lo strumento non viene completata correttamente, l'integrazione dello strumento viene messa in uno stato di errore.
{: tsCauses}

Configura nuovamente l'integrazione dello strumento:
{: tsResolve}

1. Nella relativa scheda, passa con il mouse sul messaggio `Setup failed` e fai clic su **Reconfigure**.

 ![Pulsante riconfigura](images/tool_reconfigure.png)

1. Assicurati di stare utilizzando dei parametri di configurazione validi. Se l'errore è stato causato da una configurazione non valida, viene visualizzato un messaggio di errore; ad esempio, `Impossibile configurare l'integrazione. Controlla le impostazione e riprova. Motivo: Invalid api_key:fakeKey`. Aggiorna le impostazioni per l'integrazione dello strumento e fai clic su **Save integration**.
1. Se l'errore è stato causato da un problema di comunicazione, fai clic su **Save integration** per ritentare.



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
