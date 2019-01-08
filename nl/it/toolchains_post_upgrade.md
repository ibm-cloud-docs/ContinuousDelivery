---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Introduzione alle toolchain dopo l'aggiornamento al tuo progetto {{site.data.keyword.jazzhub_short}}
{: #toolchains_post_upgrade}

Dei progetti {{site.data.keyword.jazzhub}} in hub.jazz.net viene eseguito l'upgrade alle toolchain nel servizio {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}}. 

{{site.data.keyword.jazzhub_short}} in hub.jazz.net è stato ritirato. 

Per i tuoi progetti DevOps, utilizza il servizio [{{site.data.keyword.contdelivery_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/devops){:new_window}. Se sei un nuovo utente di {{site.data.keyword.Bluemix_notm}}, assicurati di controllare la [Panoramica su {{site.data.keyword.Bluemix_notm}}](/docs/overview/ibm-cloud.html#overview).

{: shortdesc}

## Trova la toolchain che è stata creata dal tuo progetto
{: #find_toolchain}

Conferma che l'aggiornamento è completo andando alla [pagina Toolchains ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/devops/toolchains){: new_window} e verificando che vengano visualizzate le toolchain con nomi che corrispondono ai nomi dei tuoi progetti hub.jazz.net. Se i tuoi progetti sono stati aggiornati automaticamente, tiene a mente questi avvertimenti:
   - Se un'altra toolchain ha già utilizzato il nome del tuo progetto prima che il progetto venisse aggiornato, la nuova toolchain creata per il tuo progetto potrebbe non avere il nome esatto del progetto. 
   - Se non vedi le toolchain per i tuoi progetti, passa a qualsiasi altra organizzazione a cui appartieni e controlla lì le toolchain.
   
## Panoramica delle toolchain
{: #compare_toolchains}

Se avevi uno o più progetti in hub.jazz.net, ne è stato automaticamente eseguito l'upgrade alle toolchain nel servizio {{site.data.keyword.contdelivery_short}}, tranne nel caso in cui l'upgrade non sia riuscito. Gli upgrade possono non riuscire a causa di organizzazioni o account IBM Cloud non validi. I proprietari di tali account e organizzazioni sono stati avvisati per email degli errori e sono state segnalate loro le azioni specifiche che devono eseguire per risolverli. Se hai bisogno di assistenza nell'individuare la toolchain del tuo progetto aggiornato, contatta il [supporto ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. 

Le toolchain sono simili ai progetti, con alcune importanti differenze:

- I progetti possono avere solo un repository (repo) e una pipeline. Le toolchain possono avere quanti repository e pipeline necessiti.
- Le toolchain possono includere gli strumenti che non sono disponibili nei progetti, come Slack, Sauce Labs, PagerDuty e {{site.data.keyword.DRA_full}}.

 {{site.data.keyword.DRA_short}} è disponibile nelle regioni Stati Uniti Sud, Regno Unito e Germania.
  {: tip}
 
- Nei progetti, l'appartenenza era mantenuta al livello del progetto. L'accesso alle toolchain è gestito dall'organizzazione {{site.data.keyword.Bluemix_notm}} e dalla toolchain. Per lavorare con una toolchain, devi essere un membro dell'organizzazione che contiene la toolchain. Il proprietario della toolchain ha un ulteriore controllo su chi può accedere alla toolchain e cosa può fare. Per ulteriori informazioni sul controllo dell'accesso, vedi il Passo 2 in [Introduzione alla tua toolchain](#upgrade_next_steps).
- A seconda del tipo di repository utilizzato nel tuo progetto su hub.jazz.net, la toolchain potrebbe contenere un repository GitHub.com o un repository {{site.data.keyword.gitrepos}}.

Puoi trovare ulteriori informazioni sulle toolchain su [YouTube ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://youtu.be/2SIPE1e7NJ4){: new_window} o in [Introduzione a {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html)

## Introduzione alla tua toolchain
{: #upgrade_next_steps}

1. Fornisci ai tuoi membri del team l'accesso alla toolchain.
    - Ogni membro del team deve avere un account {{site.data.keyword.Bluemix_notm}} valido. I membri del team che non hanno un account valido devono [registrarsi ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/registration){:new_window}.
    - Concedi l'accesso alla toolchain ai membri dell'organizzazione dalla pagina di gestione della toolchain. I membri del progetto esistente vengono aggiunti come membri della toolchain come parte del processo di aggiornamento. Per ulteriori informazioni sul controllo dell'accesso alle toolchain, consulta [Gestione dell'accesso ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Se un utente non è un membro dell'organizzazione a cui appartiene la toolchain, aggiungilo all'organizzazione utilizzando la pagina Gestisci organizzazioni.
    - Se la tua toolchain utilizza {{site.data.keyword.gitrepos}}, tutti i membri del progetto JazzHub che dispongono di un ID {{site.data.keyword.Bluemix_notm}} valido vengono aggiunti al repository {{site.data.keyword.gitrepos}} con gli stessi privilegi che avevano nel progetto JazzHub. Se il tuo progetto JazzHub include membri che non dispongono di un ID {{site.data.keyword.Bluemix_notm}} valido, possono registrarne uno. Dopo la registrazione, puoi aggiungerli al repository.
      Per ulteriori informazioni sulla gestione delle organizzazioni, consulta [Gestione di organizzazioni e spazi ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/account/orgs_spaces.html#orgsspacesusers){:new_window}.

2. Se stai utilizzando {{site.data.keyword.gitrepos}}, effettua l'autenticazione utilizzando il token di accesso personale o una chiave SSH. Per ulteriori informazioni sulle chiavi SSH, vedi [Creazione di un token di accesso personale o di una chiave SSH per l'autenticazione](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Per effettuare l'autenticazione da un client Git esterno tramite https, segui questa procedura:
    1. Vai alla pagina [Access Tokens ![icona link esterno ](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} delle tue impostazioni utente {{site.data.keyword.gitrepos}}.
    2. Crea un token di accesso personale che utilizzi come ambito **api**.
    3. Vai alla pagina [Account ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/account){:new_window} e cerca il tuo nome utente per {{site.data.keyword.gitrepos}}. Il tuo nome utente è elencato nella sezione "Change username" e viene mostrato come prima parte dell'URL per ogni repository personale che crei.
    4. Per effettuare l'autenticazione con {{site.data.keyword.gitrepos}} da un client Git esterno tramite HTTPS, utilizza il tuo nome utente e il token di accesso personale.
    5. Se vuoi riutilizzare il repository locale del tuo repository Git JazzHub, punta il repository al nuovo repository in {{site.data.keyword.gitrepos}}. Da una shell del terminale, passa alla directory in cui viene clonato il repository Git JazzHub. Immetti il comando `git remote set-url`: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        Per controllare su quali nomi remoti sono impostati determinati URL remoti, utilizza il comando `git remote -v`. Il nome remoto predefinito è `origin`. Se hai una configurazione più avanzata, il formato del comando è il seguente: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

3. Facoltativo: per esplorare la maturità di sviluppo del progetto, le procedure del tuo team e la qualità del tuo codice di base, aggiungi IBM Cloud {{site.data.keyword.DRA_short}} alla toolchain. {{site.data.keyword.DRA_short}} applica le analisi di sviluppatori, dei team e di distribuzione ai progetti DevOps. Per ulteriori informazioni, vedi [Introduzione a {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).

  {{site.data.keyword.DRA_short}} è disponibile nelle regioni Stati Uniti Sud, Regno Unito e Germania.
  {: tip}


## Risoluzione dei problemi
{: #upgrade_troubleshoot}

Se riscontri dei problemi correlati all'aggiornamento del tuo progetto, pubblica una domanda nel [forum di supporto ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. Nel post del forum, includi gli URL al tuo progetto {{site.data.keyword.jazzhub_short}} e alla tua toolchain {{site.data.keyword.contdelivery_short}} e contrassegna il post con la tag `devops-services`.


## Domande frequenti (FAQ)
{: #upgrade_faq}

### Il mio progetto JazzHub era associato alla regione Regno Unito, ma la toolchain si trova nella regione Stati Uniti Sud. Come funziona questa combinazione?
{: #faq_region}

I progetti in hub.jazz.net e le toolchain sono entrambi ospitati nella regione Stati Uniti Sud. Se il tuo progetto era stato configurato per distribuire applicazioni a una regione differente, come ad esempio la regione Regno Unito, la toolchain esegue comunque la distribuzione delle applicazioni anche a tale regione. Pertanto non cambierà nulla sulla posizione in cui vengono ospitati i dati. Le toolchain saranno disponibili in più regioni, in futuro.

### Cosa è successo ai miei elementi di lavoro e ai miei dashboard in Track &amp; Plan dopo l'upgrade?
{: #faq_tp}

Il servizio {{site.data.keyword.contdelivery_short}} fornisce delle funzionalità di traccia dei problemi tramite {{site.data.keyword.gitrepos}}, che è ospitato da IBM e basato su GitLab Community Edition. {{site.data.keyword.contdelivery_short}} supporta anche le integrazioni con altri strumenti di pianificazione e di traccia dei problemi, quali GitHub Issues e JIRA.

Durante il processo di upgrade automatizzato, i tuoi elementi di lavoro Track & Plan sono stati migrati a Git Issues. Sia GitHub Issues che {{site.data.keyword.gitrepos}} forniscono tabelle Kanban e traccia dei problemi per la pianificazione. Per ulteriori informazioni su Issue Boards, che sono una funzione Kanban in Git Repos and Issue Tracking, consulta [Issue board ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Se hai bisogno della stessa funzione dell'ora dichiarato obsoleto JazzHub Track &amp; Plan, un nuovo servizio IBM Track and Plan on Cloud è disponibile per l'acquisto in paesi selezionati su una base di un utente al mese. Con questo servizio cloud, otterrai una funzione completa, equivalente alle licenze di collaboratore Rational Team Concert&trade;, in una sottoscrizione cloud a tenant singolo.

Questo nuovo servizio IBM Track and Plan on Cloud fornisce una funzionalità molto più articolata dell'ora dichiarato obsoleto JazzHub Track &amp; Plan, supportando la personalizzazione dei processi, le gerarchie di progetti, SAFe&reg; e molti altri metodi agili e ibridi, oltre a una scalabilità per crescere oltre un singolo progetto. Si basa sulla versione più recente di Rational Team Concert 6.0.3 e sarà alla versione 6.0.4 entro i prossimi 60 giorni, mentre JazzHub Track &amp; Plan era basato su Rational Team Concert 5.x. È possibile una migrazione dei dati a IBM Track and Plan on Cloud mediante servizi supplementari. Per ulteriori informazioni, puoi contattare [Tom Hollowell ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader.

Per informazioni su IBM Track and Plan on Cloud, o per comprare online, vedi [IBM Marketplace ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Per acquistare il servizio di automazione delle build e la gestione del codice sorgente, [Rational Team Concert on Cloud ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} è un'opzione.

### Cosa è successo al mio repository di codice dopo l'upgrade?
{: #faq_repo}

Dopo che hai eseguito l'upgrade, il tuo nuovo servizio Git è paragonabile a quanto avevi prima. Se utilizzavi github.com con il tuo progetto JazzHub, la toolchain viene connessa allo stesso repository GitHub. Se il tuo progetto JazzHub utilizzava IBM Hosted Git, il contenuto di tale repository viene clonato in un nuovo repository in {{site.data.keyword.gitrepos}}, che fa parte di {{site.data.keyword.contdelivery_short}} ed è ospitato da IBM.

Per ulteriori informazioni su come viene trattato ogni tipo di repository nel processo di upgrade, vedi la seguente tabella.

|Repository del progetto |Tipo di progetto	|Repository della toolchain |
|:----------|:------------------------------|:------------------|
|github.com 		|Privato o pubblico 		|Lo stesso repository github.com con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
|hub.jazz.net/git		|Privato o pubblico 		|Un nuovo repository privato o pubblico in {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
|Jazz SCM		|Privato o pubblico 		|Un nuovo repository privato o pubblico in {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
{: caption="Tabella 1. Repository del progetto associati ai repository della toolchain" caption-side="top"}


### Cosa è successo alle mie definizioni di build nel mio progetto dopo l'upgrade?
{: #faq_build}

Se hai creato il tuo codice sorgente utilizzando Jazz invece di Delivery Pipeline, devi migrare manualmente le tue definizioni di build a Delivery Pipeline nella tua toolchain.

Se hai utilizzato SCM come un repository di origine e hai utilizzato Delivery Pipeline per creare il tuo codice, l'origine in Jazz SCM viene automaticamente spostata in un repository Git. La tua configurazione Delivery Pipeline rimane la stessa, con la differenza che utilizza l'origine dal repository Git invece dell'origine da Jazz SCM.

### Ho dovuto creare un'organizzazione per il mio progetto di cui è stato eseguito l'upgrade a una toolchain, quindi ho aggiunto una carta di credito al mio account. Come verrà eseguito l'addebito sulla mia carta di credito?
{: #faq_charges}

In quanto [cliente con Pagamento a consumo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, l'eventuale utilizzo di runtime, servizi o componenti oltre le allocazioni gratuite per essi elencate nel catalogo {{site.data.keyword.Bluemix_notm}} ti verrà addebitato. Per una stima dell'utilizzo, consulta il [listino prezzi![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Per i prezzi correnti per Continuous Delivery, consulta il [catalogo {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/catalog/services/continuous-delivery){: new_window}.

Se sei un dipendente IBM, i progetti IBM interni possono essere fatturati ai reparti invece che a una carta di credito personale. Se devi usare risorse oltre le allocazioni gratuite per i dipendenti IBM, crea un ticket di supporto.

### Non riesco a trovare o ad accedere alla mia toolchain. Cosa posso fare?
{: #faq_find}

Le toolchain sono ospitate nelle organizzazioni {{site.data.keyword.Bluemix_notm}}. Il processo di upgrade aggiunge tutti i membri del progetto JazzHub alla toolchain. Tuttavia, a meno che il proprietario dell'organizzazione {{site.data.keyword.Bluemix_notm}} non aggiunga quegli utenti all'organizzazione, questi non potranno visualizzare la toolchain.

Per accedere alla tua toolchain, vai al sito di {{site.data.keyword.Bluemix_notm}}, fai clic sull'icona di menu e fai clic su **Services &gt; DevOps**. Viene aperta la pagina Toolchains. Assicurati di essere nella regione Stati Uniti Sud e di trovarti nell'organizzazione che contiene la toolchain. Se la tua toolchain non è elencata nella pagina Toolchains, vedi [questa voce FAQ](#faq_uk).

### Il mio progetto è associato alla regione Regno Unito. Dopo l'upgrade, visualizzo messaggi di errore, i miei colleghi non riescono ad accedere alla toolchain e non vedo la mia toolchain nella pagina Toolchains su {{site.data.keyword.Bluemix_notm}}. Che succede?
{: #faq_uk}

**Domanda completa:**

Il mio progetto JazzHub è associato alla regione {{site.data.keyword.Bluemix_notm}} del Regno Unito in base alle impostazioni del progetto. Ho verificato le impostazioni del progetto andando alla pagina di panoramica su JazzHub, facendo clic sull'icona **Settings**, che ha la forma di un ingranaggio, e facendo clic su **Options &gt; Make this an {{site.data.keyword.Bluemix_notm}} Project: Region**. Dopo aver eseguito l'upgrade del progetto alla toolchain negli Stati Uniti, si verificano questi problemi:

   1. Quando seleziono l'organizzazione degli Stati Uniti, visualizzo un messaggio che dice che l'organizzazione non ha uno spazio nella regione Stati Uniti Sud e mi viene richiesto di creare uno spazio. Non voglio eseguire nulla negli Stati Uniti.
   
   2. Alcuni dei miei colleghi non possono accedere alla toolchain, anche se sono stati elencati come membri nel progetto JazzHub originale. Se provano ad aprire la toolchain dalla pagina di panoramica dell'applicazione nella regione Regno Unito facendo clic su **View Toolchain**, visualizzano un messaggio di "accesso negato".
   
   3. Non vedo la toolchain elencata nella pagina Toolchains all'indirizzo [https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, anche se posso accedere alla toolchain direttamente dalla pagina di panoramica dell'applicazione nella regione Regno Unito facendo clic su **View Toolchain**. Visualizzo un errore che indica che non possono modificare la toolchain o un errore che indica che non ho una toolchain e che devo crearne una. 

**Risposta:**

Questi problemi si verificano se provieni da una regione {{site.data.keyword.Bluemix_notm}} diversa dagli Stati Uniti e non espandi in modo esplicito la tua organizzazione nella regione Stati Uniti Sud prima di eseguire l'upgrade. Puoi confermare questo problema aprendo la pagina Toolchains. Puoi vedere la regione e l'organizzazione all'inizio della pagina. 

Ciò che è accaduto è che, al momento dell'upgrade, la tua organizzazione non statunitense non esisteva negli Stati Uniti, pertanto l'upgrade ha selezionato per te un'altra organizzazione cercandone una a cui hai accesso.

Se passi a quella organizzazione {{site.data.keyword.Bluemix_notm}} negli Stati Uniti, puoi trovare la toolchain. Se aggiungi i tuoi colleghi a tale organizzazione, viene loro concesso l'accesso. Questa toolchain può continuare a distribuire nella tua organizzazione non statunitense. L'unico problema è che queste due organizzazioni sono distinte e non puoi eseguire la gestione degli utenti su entrambe automaticamente.

Se desideri che la tua toolchain sia nell'organizzazione statunitense che corrisponde alla tua organizzazione non statunitense, completa questa procedura:

   1. Accedi a [https://cloud.ibm.com ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com){: new_window} e seleziona la regione non statunitense e l'organizzazione da cui provieni.
   
   2. Nell'intestazione {{site.data.keyword.Bluemix_notm}}, passa alla regione Stati Uniti Sud. Ti viene richiesto di creare uno spazio in tale regione.
   
   3. Crea uno spazio nella regione Stati Uniti Sud per espandere la tua organizzazione in tale regione. 
   
   4. Elimina la toolchain creata attraverso il processo di upgrade. 
   
      Il repository Git non viene eliminato automaticamente. Per ora potresti volerlo eliminare manualmente o rinominare. Se già hai rinominato il repository Git, puoi aggiornare la futura toolchain per farne uso in un secondo momento.
      {: tip}

   5. Torna al progetto JazzHub. Il progetto viene automaticamente reimpostato per un altro tentativo di upgrade. Se il progetto non viene ripristinato, contatta hub@jazz.net e fornisci l'URL del progetto.
   
   6. Riavvia il processo di upgrade e assicurati di selezionare l'organizzazione appropriata negli Stati Uniti, che corrisponde al nome della tua organizzazione nella regione non statunitense.
   
   7. Se hai mantenuto o rinominato il repository Git dal tentativo di upgrade della toolchain precedente, (vedi il passo 4), puoi riconfigurare la scheda Git nella tua toolchain in modo da puntare invece all'URL di questo repository Git. La modifica viene automaticamente riflessa nella pipeline. Per confermare, controlla la scheda Input nella fase di build.
