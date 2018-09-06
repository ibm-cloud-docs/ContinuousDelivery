---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Collabora con il tuo team e gestisci il tuo codice sorgente con un repository (repo) Git e il programma di traccia dei problemi ospitato da IBM e creato con [GitLab Community Edition ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://about.gitlab.com/){:new_window}.
{: shortdesc}

L'integrazione dello strumento {{site.data.keyword.gitrepos}} supporta i team per gestire il codice e per la collaborazione in modi diversi:
   * Gestire i repository Git attraverso i controlli dell'accesso accurati che mantengono il codice sicuro
   * Rivedere il codice e migliorare la collaborazione tramite le richieste di unione
   * Tracciare i problemi e condividere le idee tramite il programma di traccia del problema
   * Documentare i progetti nel sistema wiki

Poiché questa integrazione dello strumento è creata in GitLab Community Edition e ospitata da IBM sulla piattaforma {{site.data.keyword.Bluemix_notm}}, alcune opzioni GitLab non sono disponibili. Ad esempio, Delivery Pipeline fornisce l'integrazione e la fornitura continue per {{site.data.keyword.Bluemix_notm}}; altrimenti, le funzioni di integrazione continua in GitLab non sono supportate. In aggiunta, le funzioni di gestione non sono disponibili perché sono gestite da IBM.
{: tip}

## Utilizzo di {{site.data.keyword.gitrepos}} in locale
{: #git_local}

Puoi accedere localmente ai repository Git memorizzati in {{site.data.keyword.gitrepos}}. Per istruzioni sulla configurazione di Git in locale, vedi [Start using Git on the command line ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}.

{{site.data.keyword.gitrepos}} supporta solo le connessioni HTTPS che utilizzano TLS1.2. Se usi Eclipse per stabilire una connessione, ti potrebbe essere richiesto di specificare questo protocollo per la tua versione di Java&trade; aggiungendo `-Dhttps.protocols=TLSv1.2` al tuo file eclipse.ini e riavviando quindi Eclipse.
{: tip}

## Autenticazione presso {{site.data.keyword.gitrepos}}
{: #git_authentication}

I tuoi login e password {{site.data.keyword.Bluemix_notm}} sono utilizzati solo per l'autenticazione con {{site.data.keyword.gitrepos}} in un browser web. Non puoi utilizzare le tue credenziali utente {{site.data.keyword.Bluemix_notm}} per eseguire l'autenticazione da client Git esterni. Per completare le operazioni Git remote, come ad esempio `clone` o `push`, dal tuo repository Git locale, devi utilizzare un token di accesso personale o una chiave SSH per l'autenticazione con {{site.data.keyword.gitrepos}}.

### Creazione di un token di accesso personale
{: #create_pat}

Per l'autenticazione con il tuo repository Git su HTTPS, devi creare un token di accesso personale.
{: tip}

1. Nel dashboard {{site.data.keyword.gitrepos}} User Settings, nella [pagina Access Tokens ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, immetti il nome dell'applicazione per cui vuoi creare un token di accesso. Ad esempio, `Git CLI`.
1. Facoltativo: scegli una data di scadenza per il token di accesso.
1. Seleziona la casella di spunta **api** per creare un token di accesso personale che utilizza api come ambito.
1. Fai clic su **Create Personal Access Token**. Annota il tuo token di accesso in un posto sicuro per utilizzi futuri.
1. Nella [pagina Account ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, nella sezione Change username, trova il tuo nome utente {{site.data.keyword.gitrepos}}. Il tuo nome utente viene visualizzato anche come primo segmento dell'URL per qualsiasi repository Git personale da te creato.
1. Utilizza il tuo nome utente {{site.data.keyword.gitrepos}} e il tuo token di accesso personale per eseguire l'autenticazione presso il tuo repository Git da un client Git esterno.

Per ulteriori informazioni, consulta [Personal access tokens ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}.

### Creazione di una chiave SSH  
{:create_ssh }

Per creare una chiave SSH, consulta [How to create your SSH Keys ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}. L'accesso ai tuoi repository con l'autenticazione SSH potrebbe richiedere ulteriore configurazione per i proxy e i firewall.

Per ulteriori informazioni, consulta [SSH ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/ssh/README){:new_window}.

## Limiti dimensione repository e file fisici
{: #git_limits}

I file sono tassativamente limitati a 100 MB. Il limite di dimensione del repository consigliato è 1 GB. Se il tuo repository supera 1 GB, potresti ricevere un'email con una richiesta di riduzione della dimensione del repository.

## Visualizza una esercitazione: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Guarda una di queste esercitazioni su [IBM&reg; Cloud Garage Method ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}. Impara come creare una toolchain aperta da un template e utilizzarla per la fornitura continua a un'applicazione "Hello World".

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}. Impara come creare una toolchain da un template con tre microservizi e utilizzare la toolchain per la fornitura continua di un negozio online.
