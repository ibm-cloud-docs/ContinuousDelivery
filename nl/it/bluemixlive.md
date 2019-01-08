---



copyright:
  years: 2015，2018
lastupdated: "2018-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}


Se stai creando un'applicazione Node.js, puoi utilizzare {{site.data.keyword.Bluemix}} Live Sync per aggiornare rapidamente l'istanza dell'applicazione su {{site.data.keyword.Bluemix_notm}} e sviluppare senza ridistribuire manualmente.   
{: shortdesc}

Quando apporti una modifica, puoi vedere tale modifica nell'applicazione {{site.data.keyword.Bluemix_notm}} in esecuzione immediatamente. {{site.data.keyword.Bluemix_notm}} Live Sync funziona
<!--from both the command line and -->
in Eclipse Orion Web IDE (Web IDE). Puoi eseguire il debug delle applicazioni scritte in Node.js utilizzando {{site.data.keyword.Bluemix_notm}} Live Sync.  

{{site.data.keyword.Bluemix_notm}} Live Sync si articola in due funzioni.
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**Live Edit**

Puoi modificare un'applicazione Node.js in esecuzione in {{site.data.keyword.Bluemix_notm}} e verificarla subito nel tuo browser. Qualsiasi modifica da te apportata nel Web IDE viene propagata immediatamente al file system dell'applicazione.  

**Debug**  

Mentre un'applicazione Node.js è in modalità Live Edit, puoi accedere a essa mediante shell ed eseguirne il debug. Puoi modificare il codice in modo dinamico, inserire dei punti di interruzione, analizzare in dettaglio il codice, riavviare il runtime e altro ancora, utilizzando il programma di debug Node Inspector.  


##Live Edit
{: #live-edit}

Se stai creando un'applicazione Node.js che viene eseguita su {{site.data.keyword.Bluemix_notm}}, la funzione Live Edit di {{site.data.keyword.Bluemix_notm}} Live Sync può aggiornare rapidamente l'istanza dell'applicazione. Live Edit è disponibile solo nel Web IDE. Puoi utilizzare Live Edit per effettuare attività di sviluppo come faresti sul desktop senza eseguire nuovamente la distribuzione.

Live Edit è supportato solo per le applicazioni Node.js.

In Eclipse Orion Web IDE (Web IDE), nella barra di esecuzione, fai clic su **Live Edit**.

![Immagine della bara di esecuzione con live edit](images/bluemix-live-sync-light.png)

Utilizza Live Edit per visualizzare rapidamente in anteprima le modifiche alle applicazioni Node.js in esecuzione su {{site.data.keyword.Bluemix_notm}}. Quando aggiorni il tuo codice con Live Edit attivato, puoi aggiornare la finestra del browser della tua applicazione web per vedere tali modifiche riflesse entro pochi secondi da quando le hai apportate.

Per un'esercitazione sull'utilizzo della funzione Live Edit di {{site.data.keyword.Bluemix_notm}} Live Sync, consulta [Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop, debug, and deploy your app ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window}.

Quando modifichi i file nel tuo Web IDE, questi vengono ridistribuiti automaticamente alla tua istanza dell'applicazione su {{site.data.keyword.Bluemix_notm}}. Se hai bisogno di riavviare l'applicazione Node, fai clic sul pulsante **Restart** nella barra di esecuzione.

Per un'esperienza più coerente quanto utilizzi la funzione Live Edit di {{site.data.keyword.Bluemix_notm}} Live Sync, sono richiesti e aggiunti 256 MB di memoria supplementare.
{: tip}

## {{site.data.keyword.Bluemix_notm}} Live Debug
{: #live-debug}

Il debug di {{site.data.keyword.Bluemix_notm}} Live Sync utilizza
[Node Inspector ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/node-inspector/node-inspector){:new_window}
per fornire le funzioni di debug. Perché il programma di debug sia disponibile, devi utilizzare la versione 4 di Node in quanto le versioni successive di Node.js non includono Node Inspector.

Puoi accedere a Debug di {{site.data.keyword.Bluemix_notm}} Live quando {{site.data.keyword.Bluemix_notm}} Live Edit è abilitato per la tua applicazione Node.js.  

Con la funzione di debug, puoi modificare il codice in modo dinamico, inserire dei punti di interruzione, analizzare in dettaglio il codice, riavviare il runtime e altro ancora, e tutto questo mentre la tua applicazione viene servita da {{site.data.keyword.Bluemix_notm}}. Puoi sviluppare in modo incrementale la tua applicazione in modo agile mentre scegli dall'ampio elenco di servizi {{site.data.keyword.Bluemix_notm}}.

Debug di {{site.data.keyword.Bluemix_notm}} Live include le seguenti funzioni:

* Controllo del runtime dell'applicazione
* Esecuzione del debug utilizzando [Node Inspector ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/node-inspector/node-inspector){:new_window}
* Accesso shell

### Controllo del runtime dell'applicazione {: #app-runtime}

Con il controllo del runtime dell'applicazione, puoi utilizzare Debug per analizzare lo stato dell'applicazione in fase di avvio. Questa funzionalità è utile quando cerchi di risolvere i problemi di un'applicazione di cui si verifica un malfunzionamento all'avvio.

Mentre sviluppi la tua applicazione, puoi scegliere tra le seguenti azioni:

* Eseguire un rapido riavvio dell'applicazione
* Sospendere l'applicazione prima di eventuali esecuzioni di codice

Dopo aver eseguito l'accesso, viene visualizzata la pagina di Debug di {{site.data.keyword.Bluemix_notm}} Live.

### Debug {: #debug}

**Limitazione:** sono richiesti Google Chrome e Node 4.

Debug include le seguenti funzionalità:  
* Impostare dei punti di interruzione nel codice applicativo per mettere in pausa l'esecuzione a una specifica riga.
  I punti di interruzione non sono supportati nel programma principale, ma sono supportati nei punti di ingresso.
  {: tip}
* Modificare le condizioni del punto di interruzione per mettere in pausa l'esecuzione solo quando sono soddisfatti degli specifici criteri.
* Esaminare lo stato di campi e variabili locali.
* Visualizzare l'output di debug dalle chiamate `console.log()` immediatamente. Questa azione è più rapida del monitoraggio dei log cf.
* Utilizzare l'editor di codice sorgente integrato per apportare delle modifiche immediate, seppur temporanee, al codice applicativo in esecuzione.

### Shell {: #shell}

Questo strumento ti dà l'accesso shell al contenitore in cui è in esecuzione la tua applicazione. Usando questo terminale, puoi eseguire in remoto dei comandi shell di diagnostica per amministrare la tua applicazione. Tutte le versioni di Node.js supportano la funzione Shell.

Esegui il monitoraggio della memoria e dell'utilizzo della CPU all'interno dell'istanza che utilizza i comandi Linux standard, come **top**, **ps** e **kill**.

### Configurazione di un'applicazione per abilitare Debug di {{site.data.keyword.Bluemix_notm}} Live {: #configure_app_debug}

1. Il programma di debug di {{site.data.keyword.Bluemix_notm}} Live utilizza Node Inspector. Devi utilizzare Node versione 4 e devi inoltre consentire al pacchetto di build di rilevare il comando di avvio dell'applicazione. Il comando di avvio deve essere rilevato automaticamente dal pacchetto di build e non impostato nel file manifest.yml.

   Un file `package.json` che supporta Debug di {{site.data.keyword.Bluemix_notm}} Live è:

  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. Aumenta la memoria.  

    a. Nel file `manifest.yml` dell'applicazione, aggiungi 128 MB o più al valore specificato per l'attributo memoria.

Una volta installato Debug di {{site.data.keyword.Bluemix_notm}} Live, puoi utilizzare gli strumenti di debug.

Distribuisci l'applicazione e vai quindi a `https://_app-host.mybluemix.net_/bluemix-debug/manage` per accedere all'interfaccia utente di debug di {{site.data.keyword.Bluemix_notm}}. Quando ti viene richiesto di autenticarti, immetti nome utente e password del tuo ID IBM o un passcode monouso.    

L'inizializzazione del programma di debug potrebbe richiedere qualche minuto.
{: tip}

### Ripristino delle configurazioni dell'applicazione e disabilitazione di Debug di {{site.data.keyword.Bluemix_notm}} Live {: #restore_live_debug}

1. Ripristina la versione Node.js, il comando di avvio e il valore di memoria originale dell'applicazione.

2. Distribuisci l'applicazione.

### Per ulteriori informazioni

* Consulta [Strumenti Eclipse per {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.cloud.ibm.com/docs/manageapps/eclipsetools/eclipsetools.html){:new_window}
