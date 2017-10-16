---

copyright:
  years: 2015, 2017
lastupdated: "2017-7-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# Configurazione di client locali per operare con il controllo origine Git
{: #git_local}


Puoi gestire e lavorare con il tuo codice sorgente in un repository GitHub, GitHub Enterprise o Repository Git e tracciamento del problema, in locale o in Eclipse Orion Web IDE. Per lavorare in locale, clona il tuo repository con un client Git, come l'interfaccia della riga di comando Git, e modifica il codice attraverso il tuo editor favorito. Se lavori in Eclipse, puoi installare il plug-in EGit per il controllo della versione.

## Clonazione del tuo progetto Git dalla riga di comando


## Attività preliminari
{: #git_before_clone}

1. Per accedere al server Git al di fuori del browser, potresti dover creare un token di accesso personale o una chiave SSH per effettuare l'autenticazione.   La seguente tabella mostra le operazioni che devi eseguire per configurare l'autenticazione.

| Tipo Git  | Configurazione HTTPS | Utilizzo di HTTPS |  Configurazione SSH |
|:-----------|:-------------|:------------|:-------------|
| Repository Git e tracciamento del problema (git.ng.bluemix.com) | [Token di accesso personale](/docs/ContinuousDelivery/git_working.html#create_pat) | Nome utente di Repository Git e tracciamento del problema (non il tuo ID IBM) e token di accesso personale | [Configura la chiave SSH](/docs/ContinuousDelivery/git_working.html#create_ssh) |
| GitHub pubblico (github.com) | Il token di accesso personale non è obbligatorio, ma puoi configurarne uno e utilizzarlo | Nome utente e password GitHub o nome utente e token di accesso personale GitHub oppure solo token di accesso personale come nome utente | [Configura una chiave SSH GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Token di accesso personale](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) | Nome utente di GitHub Enterprise (non il tuo ID IBM) e token di accesso personale | [Configura la chiave SSH GitHub Enterprise](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) |

**Nota**: se preferisci usare SSH, puoi riutilizzare una singola chiave in tutti i server Git. Crea o individua la tua chiave e configurala in ogni server, come descritto nei precedenti link. Se crei la tua chiave con una passphrase, ti verrà richiesto di immettere questa passphrase quando utilizzi la chiave. 

2. Se hai intenzione di utilizzare la riga di comando Git, procedi come segue:

    a. Controlla se Git è installato. In una riga di comandi, immetti `git version`. Se Git è installato, viene visualizzato il numero di versione e puoi iniziare. 

    b. Se Git non è installato, [vai al sito web Git ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://git-scm.com/downloads){: new_window}.

    c. Scarica e installa la versione adatta al tuo sistema operativo. Puoi accettare i valori di installazione predefiniti. 


### Clonazione del tuo progetto
{: #git_clone}

Crea una copia locale dei file di progetto clonando il repository Git in modo da poter accedere ai contenuti del tuo repository al di fuori di Web IDE utilizzando un qualsiasi strumento desktop.

1. Dalla pagina Panoramica della tua toolchain, fai clic sulla scheda del repository che vuoi clonare.

2. Recupera l'URL del repository:

   a. In GitHub, fai clic su **Clona o scarica**. Per utilizzare HTTPS, seleziona **Usa HTTPS**.  Per utilizzare, SSH, fai clic su **Usa SSH**. Fai clic sull'icona degli appunti per copiare l'URL.

   b. In Repository Git e tracciamento del problema, seleziona **HTTPS** o **SSH** e copia l'URL nel campo.

3. Apri una riga di comando.

4. Modifica la directory in cui desideri che sia inserita la copia locale del repository Git.

5. Immetti `git clone`, incolla l'URL e premi Invio.

6. Se ti viene richiesta l'autenticazione, immetti le informazioni appropriate, come definito nella tabella precedente


Una volta completato il download, avrai una versione dei file nel tuo repository. Per ulteriori informazioni sull'utilizzo di Git, [consulta la documentazione di Git ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](http://git-scm.com/doc){: new_window}.


## Accesso al tuo repository utilizzando Eclipse e il plug-in EGit
{: #git_egit}

Se utilizzi Eclipse e hai un progetto che utilizza Git per il controllo sorgente, puoi utilizzare il plug-in EGit per gestire il tuo repository da Eclipse. Per istruzioni per l'installazione e la configurazione di EGit, vedi [Esercitazione di EGit ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
Se utilizzi Repository Git e tracciamento del problema e riscontri dei problemi, vedi [Repository Git e tracciamento del problema](git_working.html#git_local).

## Sviluppo con IBM Eclipse Tools
{: #git_eclipse_tools}

IBM Eclipse Tools for Bluemix fornisce dei plug-in che puoi installare in un ambiente Eclipse per integrare il tuo IDE con Bluemix.

Con gli strumenti, puoi distribuire i seguenti tipi di file e server al server Bluemix direttamente dal tuo ID Eclipse IDE o da IBM WebSphere&reg; Application Server Developer Tools (WDT):

* File JavaScript
* File WAR (archivio web)
* File EAR (enterprise archive)
* Server in pacchetto di Liberty Profile

Puoi anche creare dei servizi e collegarli alla tua applicazione e definire le variabili di ambiente come parte della distribuzione. Per ulteriori informazioni su IBM Eclipse Tools, [vedi Distribuzione di applicazioni con IBM Eclipse Tools for Bluemix](../../manageapps/eclipsetools/eclipsetools.html).
