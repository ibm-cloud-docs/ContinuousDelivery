---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-8"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Configurazione di client locali per operare con il controllo origine Git
{: #git_local}


Puoi gestire e lavorare con il tuo codice sorgente in un repository GitHub, GitHub Enterprise o Git Repos and Issue Tracking, in locale o in Eclipse Orion Web IDE. Per lavorare in locale, clona il tuo repository con un client Git, come l'interfaccia della riga di comando Git, e modifica il codice attraverso il tuo editor favorito. Se lavori in Eclipse, puoi installare il plug-in EGit per il controllo della versione.

## Clonazione del tuo progetto Git dalla riga di comando


## Attività preliminari
{: #git_before_clone}

1. Per accedere al server Git al di fuori del browser, potresti dover creare un token di accesso personale o una chiave SSH per effettuare l'autenticazione. La seguente tabella mostra le operazioni che devi eseguire per configurare l'autenticazione.

| Tipo Git  | Configurazione HTTPS | Utilizzo di HTTPS |  Configurazione SSH |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com) | [Token di accesso personale](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) | Nome utente di Git Repos and Issue Tracking (non il tuo ID IBM) e token di accesso personale | [Configura la chiave SSH](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) |
| GitHub pubblico (github.com) | Il token di accesso personale non è obbligatorio, ma puoi configurarne uno e utilizzarlo | Nome utente e password GitHub o nome utente e token di accesso personale GitHub oppure solo token di accesso personale come nome utente | [Configura una chiave SSH GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Token di accesso personale](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started#ghe_auth) | Nome utente di GitHub Enterprise (non il tuo ID IBM) e token di accesso personale | [Configura la chiave SSH GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started#ghe_auth) |

Se preferisci usare SSH, puoi riutilizzare una singola chiave in tutti i server Git. Crea o individua la tua chiave e configurala in ogni server, come descritto nei precedenti link. Se crei la tua chiave con una passphrase, ti viene richiesto di immettere questa passphrase quando utilizzi la chiave.
{: tip}

2. Se utilizzerai la riga di comando Git, completa la seguente procedura:

    a. Controlla se Git è installato. In una riga di comandi, immetti `git version`. Se Git è installato, viene visualizzato il numero di versione e puoi iniziare.

    b. Se Git non è installato, [vai al sito web Git ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://git-scm.com/downloads){: new_window}.

    c. Scarica e installa la versione adatta al tuo sistema operativo. Puoi accettare i valori di installazione predefiniti.


### Clonazione del tuo progetto
{: #git_clone}

Crea una copia locale dei file di progetto clonando il repository Git in modo da poter accedere ai contenuti del tuo repository al di fuori di Web IDE utilizzando un qualsiasi strumento desktop.

1. Dalla pagina Overview della tua toolchain, fai clic sulla scheda del repository che vuoi clonare.

2. Recupera l'URL del repository:

   a. In GitHub, fai clic su **Clone or download**. Per utilizzare HTTPS, seleziona **Use HTTPS**.  Per utilizzare, SSH, fai clic su **Use SSH**. Fai clic sull'icona degli appunti per copiare l'URL.

   b. In Git Repos and Issue Tracking, seleziona **HTTPS** o **SSH** e copia l'URL nel campo.

3. Apri una riga di comando.

4. Modifica la directory in cui desideri che sia inserita la copia locale del repository Git.

5. Immetti `git clone`, incolla l'URL e premi Invio.

6. Se ti viene richiesta l'autenticazione, immetti le informazioni appropriate, come definito nella tabella precedente


Una volta completato il download, avrai una versione dei file nel tuo repository. Per ulteriori informazioni sull'utilizzo di Git, [consulta la documentazione di Git ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](http://git-scm.com/doc){: new_window}.


## Accesso al tuo repository utilizzando Eclipse e il plug-in EGit
{: #git_egit}

Se utilizzi Eclipse e hai un progetto che utilizza Git per il controllo sorgente, puoi utilizzare il plug-in EGit per gestire il tuo repository da Eclipse. Per istruzioni per l'installazione e la configurazione di EGit, vedi [Esercitazione di EGit ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
Se utilizzi Git Repos and Issue Tracking e riscontri dei problemi, vedi [Git Repos and Issue Tracking](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_local).
