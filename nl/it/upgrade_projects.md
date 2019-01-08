---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Aggiorna il tuo progetto {{site.data.keyword.jazzhub_short}} a una toolchain
{: #upgrade_projects}

{{site.data.keyword.jazzhub}} si sta trasformando in {{site.data.keyword.contdelivery_full}}. Come parte di tale modifica, verrà eseguito un upgrade dei progetti a toolchain.

Puoi aggiornare il tuo progetto o attendere che venga aggiornato automaticamente. Per un'esperienza ottimale, assicurati di soddisfare i [prerequisiti](#upgrade_prereqs) e aggiorna il tuo progetto il prima possibile in modo da poter controllare quale sia il nome della tua toolchain e in quale organizzazione viene creata.
{: shortdesc}

**Domande frequenti (FAQ)**

- [Il mio progetto JazzHub è associato alla regione Regno Unito, ma la toolchain si trova nella regione Stati Uniti Sud. Come funzionerà questa combinazione?](#faq_region)
- [Cosa succede ai miei elementi di lavoro e ai miei dashboard in Track &amp; Plan quando eseguo l'upgrade?](#faq_tp)
- [Cosa succede al mio repository di codice quando eseguo l'upgrade?](#faq_repo)
- [Cosa succede alle mie definizioni di build nel mio progetto quando eseguo l'upgrade a una toolchain?](#faq_build)
- [Devo creare un'organizzazione per il mio progetto di cui viene eseguito l'upgrade a una toolchain. Capisco che devo aggiungere una carta di credito al mio account prima di poter creare un'organizzazione. Come verrà eseguito l'addebito sulla mia carta di credito?](#faq_charges)
- [Non riesco a trovare o ad accedere alla mia toolchain. Cosa posso fare?](#faq_find)
- [Il mio progetto è associato alla regione Regno Unito. Dopo l'upgrade, visualizzo messaggi di errore, i miei colleghi non riescono ad accedere alla toolchain e non vedo la mia toolchain nella pagina Toolchains sulla piattaforma {{site.data.keyword.Bluemix_notm}}. Che succede?](#faq_uk)

## Toolchain
{: #compare_toolchains}

Le toolchain sono simili ai progetti, con alcune importanti differenze:

- I progetti possono avere solo un repository (repo) e una pipeline. Le toolchain possono avere quanti repository e pipeline necessiti.
- Le toolchain possono includere gli strumenti che non sono disponibili nei progetti, come Slack, Sauce Labs, PagerDuty e {{site.data.keyword.DRA_full}}.
- L'accesso alle toolchain è gestito tramite le organizzazioni {{site.data.keyword.Bluemix_notm}} standard. L'appartenenza viene mantenuta al livello dell'organizzazione, in modo diverso dai progetti, in cui l'appartenenza era mantenuta al livello del progetto.

Puoi trovare informazioni sulle toolchain su [YouTube ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://youtu.be/2SIPE1e7NJ4){: new_window} o in [Introduzione a {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Link esterno a YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Prerequisiti
{: #upgrade_prereqs}

- Per accedere alla tua toolchain del progetto aggiornata, hai bisogno di un ID {{site.data.keyword.Bluemix_notm}}. Prima di eseguire l'aggiornamento, devi verificare di disporre di un ID {{site.data.keyword.Bluemix_notm}} attivo. Se non ne hai uno, [registrati](https://console.ng.bluemix.net/registration/).
- Assicurati che il tuo proprietario del progetto {{site.data.keyword.jazzhub_short}} sia corretto. La toolchain che viene creata dal tuo progetto fa parte dell'organizzazione {{site.data.keyword.Bluemix_notm}} di tale proprietario.
- Assicurati che l'organizzazione e lo spazio in cui vuoi creare la tua toolchain siano in {{site.data.keyword.Bluemix_notm}} Pubblico nella regione Stati Uniti Sud. Per confermare di avere un'organizzazione e uno spazio validi negli Stati Uniti Sud, accedi a [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} e crea uno spazio se ti viene richiesto di crearne uno.
- Se intendi avviare l'aggiornamento, assicurati di essere membro di ogni organizzazione e spazio in cui distribuisce la pipeline. L'aggiornamento può essere avviato da qualsiasi amministratore del progetto. Tuttavia, se l'amministratore che avvia l'aggiornamento non è un membro di ogni organizzazione e spazio in cui distribuisce la pipeline, la pipeline non può essere creata. La persona che avvia l'aggiornamento diventa il proprietario del repository nella toolchain.
- Eclipse Orion {{site.data.keyword.webide}} nella toolchain è distinto dal {{site.data.keyword.webide}} che è associato al tuo progetto. Se utilizzi {{site.data.keyword.webide}} e hai delle modifiche non eseguite, eseguile prima dell'aggiornamento.


## Aggiornamento da un progetto a una toolchain
{: #project_to_toolchain}

I progetti in hub.jazz.net e le toolchain sono entrambi ospitati nella regione Stati Uniti Sud. Se il tuo progetto è stato configurato per distribuire le applicazioni in una regione differente, le distribuisce comunque a tale regione dopo che ne è stato eseguito l'upgrade a una toolchain.
{: tip}

Quando il tuo progetto è pronto per essere aggiornato, viene visualizzato un messaggio nella scheda del progetto e nella pagina della panoramica.

![Immagine della scheda con l'etichetta pronto per l'aggiornamento](images/card-project-to-upgrade.png)

![Ora del messaggio pronto per l'aggiornamento](images/banner-ready-to-upgrade.png)

Puoi trovare i progetti che sono pronti per l'aggiornamento dal menu nella pagina dei progetti personali:

![Immagine della voce del menu progetti per l'aggiornamento](images/menu-projects-to-upgrade.png)
{: tip}

Quando avvii l'aggiornamento, le fasi della pipeline nel tuo progetto vengono bloccate. Non puoi eseguirle o modificarle. Se ripristini l'aggiornamento eliminando la toolchain, la pipeline viene sbloccata.

Se il tuo progetto utilizza un repository Git ospitato su JazzHub, una volta avviato l'aggiornamento, il repository viene bloccato per garantire l'integrità dei dati che vengono spostati nella toolchain. Se ripristini l'aggiornamento eliminando la toolchain, il repository su JazzHub viene sbloccato.

Per informazioni dettagliate su come viene trattato ogni tipo di repository nel processo di upgrade, vedi la seguente tabella.

|Repository del progetto |Tipo di progetto	|Repository della toolchain |
|:----------|:------------------------------|:------------------|
|github.com 		|Privato o pubblico 		|Lo stesso repository github.com con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
|hub.jazz.net/git		|Privato o pubblico 		|Un nuovo repository in {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
{: caption="Tabella 1. Repository del progetto associati ai repository della toolchain" caption-side="top"}

## Avvio del processo di aggiornamento
{: #start_upgrade}

Prima di avviare il processo di aggiornamento, puoi guardarlo in esecuzione su [YouTube ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://youtu.be/LSr2e3uvyLs){: new_window}.
[![Link esterno a YouTube](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

Per aggiornare il tuo progetto in una toolchain, completa la seguente procedura:

1. Per avviare il processo di aggiornamento, nel messaggio informativo, fai clic su **upgrade now**. Viene aperta la pagina "Project upgrade toolchain".

   ![Esempio di una pagina di aggiornamento](images/project-upgrade-toolchain.png)

   Per una panoramica sul processo di aggiornamento, leggi la descrizione in questa pagina. La toolchain include una nuova pipeline che contiene le stesse fasi e lavori della pipeline del progetto. In aggiunta, la toolchain contiene un puntatore a Eclipse Orion {{site.data.keyword.webide}} che viene eseguito in {{site.data.keyword.contdelivery_short}}.

   In questo esempio, poiché il progetto utilizza un repository pubblico su github.com, la toolchain è collegata allo stesso repository GitHub. Se il tuo progetto utilizza un repository Git ospitato su JazzHub, il contenuto di tale repository viene clonato in un nuovo repository in {{site.data.keyword.gitrepos}}, che fa parte di {{site.data.keyword.contdelivery_short}}.

2. Per personalizzare la toolchain, puoi configurare alcune impostazioni:

   - Per modificare il nome della toolchain, modifica il campo **Name**.

      ![Campo nome](images/name-change.png)

   - Per modificare in quale organizzazione {{site.data.keyword.Bluemix_notm}} creare la toolchain, seleziona l'organizzazione dal tuo menu dell'account:

      ![{{site.data.keyword.Bluemix_notm}} Selezionatore dell'organizzazione](images/bluemix-organization-chooser.png)

   Poiché le toolchain sono gestite al livello dell'organizzazione, assicurati di selezionare un'organizzazione in cui i membri del progetto che devono accedere alla toolchain esistano o possano essere aggiunti.

3. Se nel tuo progetto hai utilizzato Track & Plan, puoi trasferire i tuoi dati Track & Plan a Problemi GitHub.

   ![Opzioni di Track and Plan](images/upgrade-tutorial-track-and-plan.png)

   - Indica se vuoi migrare i tuoi dati Track & Plan.
   - Per impostazione predefinita, tutti i tuoi dati Track & Plan vengono migrati. Se preferisci migrare solo gli elementi di lavoro che fanno parte di una determinata query, specifica tale query.
   - Seleziona qualsiasi attributo di elemento di lavoro che vuoi associare alle etichette in Problemi GitHub.

4. Fai clic su **Create**. La nuova toolchain è stata creata e ne viene visualizzata la pagina della panoramica.

   ![Panoramica della toolchain aggiornata](images/new-toolchain-page.png)

   - Per accedere al tuo repository GitHub o al programma di traccia dei problemi associato, fai clic su **GitHub** o **Issues**.
   - Per accedere alla tua pipeline, fai clic su **Delivery Pipeline**.
   - Per accedere a {{site.data.keyword.webide}}, che contiene i contenuti del tuo repository che sono stati selezionati nello spazio di lavoro, fai clic su **Eclipse Orion {{site.data.keyword.webide}}**.

   Se ritorni al tuo progetto durante l'aggiornamento, il messaggio del banner potrebbe indicare che l'aggiornamento è in corso, soprattutto se il processo di aggiornamento prevede l'importazione del codice sorgente a un nuovo repository o l'importazione degli elementi di lavoro Track &amp; Plan come problemi.

   ![Messaggio sul progetto che viene aggiornato a un toolchain](images/project-being-upgraded-banner.png)

## Rivisitazione del tuo progetto
{: #revisit_projects}

Sei ora pronto ad utilizzare la tua nuova toolchain. Il tuo progetto è ora etichettato come "Upgraded" e, nella pagina della panoramica, viene visualizzato un messaggio di conferma.

![Immagine della scheda del progetto con l'etichetta Upgraded](images/card-upgraded-project.png)

![Progetto aggiornato](images/banner-upgraded.png)

Puoi visualizzare quali progetti sono stati aggiornati selezionando **Upgraded Projects** dal menu nella pagina dei progetti personali:

![Immagine della voce di menu Upgraded Projects](images/menu-upgraded-projects.png)

Se hai bisogno di annullare l'aggiornamento, elimina la tua toolchain. Puoi eliminare la toolchain dal menu **More Actions** nella pagina della panoramica della toolchain:

![immagine dell'azione Delete nel menu More Actions](images/upgrade-tutorial-delete-toolchain.png)

Quando ritorni al tuo progetto, il messaggio di aggiornamento viene nuovamente visualizzato e puoi rieseguire l'aggiornamento quando sei pronto.

## Passi successivi
{: #upgrade_next_steps}

1. Conferma che l'aggiornamento è stato completato aggiornando il tuo browser e controllando che il messaggio nella pagina della panoramica del progetto indichi che il progetto è stato aggiornato a questa toolchain:

   ![Messaggio nel banner che indica che il progetto è stato aggiornato](images/banner-upgraded.png)

   Se il messaggio indica "upgrade now," l'aggiornamento non è riuscito. Fai clic sul link **upgrade now** per riprovare.
   {: tip}

   ![Messaggio nel banner che indica che il progetto è pronto per l'aggiornamento](images/banner-ready-to-upgrade.png)

2. Fornisci ai tuoi membri del team l'accesso alla toolchain.
    - Ogni membro del team deve avere un account {{site.data.keyword.Bluemix_notm}} valido. I membri del team che non hanno un account valido devono [registrarsi ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/registration){:new_window}.
    - Concedi l'accesso alla toolchain ai membri dell'organizzazione dalla pagina di gestione della toolchain. I membri del progetto esistente vengono aggiunti come membri della toolchain come parte del processo di aggiornamento. Per ulteriori informazioni sul controllo dell'accesso alle toolchain, consulta [Gestione dell'accesso ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Se un utente non è un membro dell'organizzazione a cui appartiene la toolchain, aggiungilo all'organizzazione utilizzando la pagina Gestisci organizzazioni.
    - Se la tua toolchain utilizza {{site.data.keyword.gitrepos}}, tutti i membri del progetto JazzHub che dispongono di un ID {{site.data.keyword.Bluemix_notm}} valido vengono aggiunti al repository {{site.data.keyword.gitrepos}} con gli stessi privilegi che avevano nel progetto JazzHub. Se il tuo progetto JazzHub include membri che non dispongono di un ID {{site.data.keyword.Bluemix_notm}} valido, devono registrarne uno ed essere aggiunti al repository.
      Per ulteriori informazioni sulla gestione delle organizzazioni, consulta [Gestione di organizzazioni e spazi ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Utilizza gli strumenti dalla tua toolchain invece degli strumenti dal tuo progetto {{site.data.keyword.jazzhub_short}}. Ad esempio, per modificare il codice da un browser, utilizza la Web IDE dalla tua toolchain.

4. Se stai utilizzando {{site.data.keyword.gitrepos}}, effettua l'autenticazione utilizzando il token di accesso personale o una chiave SSH. Per ulteriori informazioni sulle chiavi SSH, vedi [Creazione di un token di accesso personale o di una chiave SSH per l'autenticazione](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Per effettuare l'autenticazione da un client Git esterno tramite https, segui questa procedura:
    1. Vai alla pagina [Access Tokens ![icona link esterno ](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} delle tue impostazioni utente {{site.data.keyword.gitrepos}}.
    2. Crea un token di accesso personale che utilizzi come ambito **api**.
    3. Vai alla pagina [Account ![icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/profile/account){:new_window} e cerca il tuo nome utente per {{site.data.keyword.gitrepos}}. Il tuo nome utente è elencato nella sezione "Change username" e viene mostrato come prima parte dell'URL per ogni repository personale che crei.
    4. Per effettuare l'autenticazione con {{site.data.keyword.gitrepos}} da un client Git esterno tramite https, utilizza il tuo nome utente e il token di accesso personale.
    5. Se vuoi riutilizzare il repository locale del tuo repository Git JazzHub, punta il repository al nuovo repository in {{site.data.keyword.gitrepos}}. Da una shell in un terminale, passa alla directory in cui viene clonato il repository Git JazzHub Git. Immetti il comando `git remote set-url`: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        Per controllare su quali nomi remoti sono impostati determinati URL remoti, utilizza il comando `git remote -v`. Il nome remoto predefinito è `origin`. Se hai una configurazione più avanzata, il formato del comando è il seguente: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

5. Una volta che la tua toolchain è configurata e inizi a utilizzarla, valuta la possibilità di effettuare tutti o una parte dei seguenti passi per garantire che nessuno utilizzi il tuo progetto:
    - Aggiungi un suffisso al nome del tuo progetto per indicare che non deve essere utilizzato. Potresti aggiungere `_DO_NOT_USE` alla fine del nome progetto.
    - Aggiorna la descrizione del progetto per indicare che non è più utilizzato e aggiungi un puntatore alla toolchain.
    - Rimuovi i membri dal progetto.
    - Elimina il progetto quando non ti serve più.

6. Facoltativo: per esplorare la maturità di sviluppo del progetto, le procedure del tuo team e la qualità del tuo codice di base, aggiungi IBM Cloud {{site.data.keyword.DRA_short}} alla toolchain. {{site.data.keyword.DRA_short}} applica le analisi di sviluppatori, dei team e di distribuzione ai progetti DevOps. Per ulteriori informazioni, vedi [Introduzione a {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Risoluzione dei problemi
{: #upgrade_troubleshoot}

Se riscontri un problema durante il processo di aggiornamento, prova una o alcune delle seguenti procedura per la risoluzione dei problemi:

- Controlla i [prerequisiti](#upgrade_prereqs) per assicurarti di soddisfarli. In particolare, assicurati di essere membro di ogni organizzazione e spazio in cui distribuisce la pipeline.
- Se il problema si è verificato durante il tuo primo tentativo di aggiornamento e soddisfi tutti i requisiti, prova a ripetere l'aggiornamento.
- Se il tuo progetto utilizza Jazz SCM o IBM Hosted Git per il controllo origine, controlla la dimensione del repository. Se è maggiore di 500 MB, [contatta il team dei servizi DevOps ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.
- Se non riesci a trovare o ad accedere alla tua toolchain, vedi [questa voce FAQ](#faq_find).
- Se continui a riscontrare problemi, pubblica una domanda nel [forum di supporto ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. Nel post del forum, includi gli URL al tuo progetto {{site.data.keyword.jazzhub_short}} e alla tua toolchain {{site.data.keyword.contdelivery_short}} e contrassegna il post con la tag `devops-services`.


## Domande frequenti (FAQ)
{: #upgrade_faq}

### Il mio progetto JazzHub è associato alla regione Regno Unito, ma la toolchain si trova nella regione Stati Uniti Sud. Come funziona questa combinazione?
{: #faq_region}

I progetti in hub.jazz.net e le toolchain sono entrambi ospitati nella regione Stati Uniti Sud. Se il tuo progetto è configurato per distribuire le applicazioni in una regione differente, come ad esempio la regione Regno Unito, le distribuisce comunque a tale regione dopo il suo upgrade a una toolchain. Pertanto, niente sta veramente cambiando relativamente a dove vengono ospitati i dati. Le toolchain saranno disponibili in più regioni, in futuro.

### Cosa succede ai miei elementi di lavoro e ai miei dashboard in Track &amp; Plan quando eseguo l'upgrade?
{: #faq_tp}

Il servizio {{site.data.keyword.contdelivery_short}} fornisce delle funzionalità di traccia dei problemi tramite {{site.data.keyword.gitrepos}}, che è ospitato da IBM e basato su GitLab Community Edition. {{site.data.keyword.contdelivery_short}} supporta anche le integrazioni con altri strumenti di pianificazione e di traccia dei problemi, quali GitHub Issues e JIRA.

Durante il processo di upgrade, puoi scegliere di migrare i tuoi elementi di lavoro Track &amp; Plan a Git Issues. Sia GitHub Issues che {{site.data.keyword.gitrepos}} forniscono tabelle Kanban e traccia dei problemi per la pianificazione. Per ulteriori informazioni su Issue Boards, che sono la funzione Kanban in Git Repos and Issue Tracking, consulta [Issue board ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Per i clienti che richiedono la stessa funzione dell'ora dichiarato obsoleto JazzHub Track &amp; Plan, un nuovo servizio IBM Track and Plan on Cloud è disponibile per l'acquisto separatamente in paesi selezionati su una base per utente al mese. Con questo servizio cloud, otterrai una funzione completa, equivalente alle licenze di collaboratore Rational Team Concert&trade;, in una sottoscrizione cloud a tenant singolo.

Questo nuovo servizio IBM Track and Plan on Cloud fornisce una funzionalità molto più articolata dell'ora dichiarato obsoleto JazzHub Track &amp; Plan, supportando la personalizzazione dei processi, le gerarchie di progetti, SAFe&reg; e molti altri metodi agili e ibridi, oltre a una scalabilità per crescere oltre un singolo progetto. Si basa sulla versione più recente di Rational Team Concert 6.0.3 e sarà alla versione 6.0.4 entro i prossimi 60 giorni, mentre JazzHub Track &amp; Plan era basato su Rational Team Concert 5.x. È possibile una migrazione dei dati a IBM Track and Plan on Cloud mediante servizi supplementari. Per ulteriori informazioni, puoi contattare [Tom Hollowell ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader.

Per informazioni su IBM Track and Plan on Cloud, o per comprare online, vai all'[IBM Marketplace ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Inoltre, per acquistare il servizio di automazione delle build e la gestione del codice sorgente, [Rational Team Concert on Cloud ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} è un'opzione.

### Cosa succede al mio repository di codice quando eseguo l'upgrade?
{: #faq_repo}

Dopo che hai eseguito l'upgrade, il tuo nuovo servizio Git è paragonabile a quanto avevi prima. Se utilizzavi github.com con il tuo progetto JazzHub, la toolchain viene connessa allo stesso repository GitHub. Se il tuo progetto JazzHub utilizzava IBM Hosted Git, il contenuto di tale repository viene clonato in un nuovo repository in {{site.data.keyword.gitrepos}}, che fa parte di {{site.data.keyword.contdelivery_short}} ed è ospitato da IBM.

Per informazioni dettagliate su come viene trattato ogni tipo di repository nel processo di upgrade, vedi la seguente tabella.

|Repository del progetto |Tipo di progetto	|Repository della toolchain |
|:----------|:------------------------------|:------------------|
|github.com 		|Privato o pubblico 		|Lo stesso repository github.com con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
|hub.jazz.net/git		|Privato o pubblico 		|Un nuovo repository privato o pubblico in {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} Pubblico.	|
{: caption="Tabella 1. Repository del progetto associati ai repository della toolchain" caption-side="top"}


### Cosa succede alle mie definizioni di build nel mio progetto quando eseguo l'upgrade a una toolchain?
{: #faq_build}

Se stai creando il tuo codice sorgente utilizzando Jazz invece di Delivery Pipeline, devi migrare manualmente le tue definizioni di build a Delivery Pipeline nella tua toolchain.

Se stai utilizzando SCM come un repository di origine e utilizzando Delivery Pipeline per creare il tuo codice, l'origine in Jazz SCM viene automaticamente spostata in un repository Git. La tua configurazione Delivery Pipeline rimane la stessa, con la differenza che utilizza l'origine dal repository Git invece dell'origine da Jazz SCM.

### Devo creare un'organizzazione per il mio progetto di cui verrà eseguito l'upgrade a una toolchain. Capisco che devo aggiungere una carta di credito al mio account prima di poter creare un'organizzazione. Come verrà eseguito l'addebito sulla mia carta di credito?
{: #faq_charges}

In quanto [cliente con Pagamento a consumo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, l'eventuale utilizzo di runtime, servizi o componenti oltre le allocazioni gratuite per essi elencate nel catalogo {{site.data.keyword.Bluemix_notm}} ti verrà addebitato. Per una stima dell'utilizzo, consulta il [listino prezzi![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Per i prezzi correnti per Continuous Delivery, consulta il [catalogo {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Se sei un dipendente IBM, i progetti IBM interni possono essere fatturati ai reparti invece che a una carta di credito personale. Se devi usare risorse oltre le allocazioni gratuite per i dipendenti IBM, crea un ticket di supporto.

### Non riesco a trovare o ad accedere alla mia toolchain. Cosa posso fare?
{: #faq_find}

Le toolchain sono ospitate nelle organizzazioni {{site.data.keyword.Bluemix_notm}}. Il processo di upgrade aggiunge tutti i membri del progetto JazzHub alla toolchain. Tuttavia, a meno che il proprietario dell'organizzazione {{site.data.keyword.Bluemix_notm}} non aggiunga quegli utenti all'organizzazione, questi non potranno visualizzare la toolchain.

Per accedere alla tua toolchain, vai alla piattaforma {{site.data.keyword.Bluemix_notm}}, fai clic sull'icona di menu e fai clic su **Services &gt; DevOps**. Viene aperta la pagina Toolchains. Assicurati di essere nella regione Stati Uniti Sud e di trovarti nell'organizzazione che contiene la toolchain. Se la tua toolchain non è elencata nella pagina Toolchains, vedi [questa voce FAQ](#faq_uk).

In alternativa, anche se il sito di JazzHub è ancora disponibile, puoi accedere alla tua toolchain facendo clic sul link nel banner della pagina Overview del tuo progetto.

### Il mio progetto è associato alla regione Regno Unito. Dopo l'upgrade, visualizzo messaggi di errore, i miei colleghi non riescono ad accedere alla toolchain e non vedo la mia toolchain nella pagina Toolchains su {{site.data.keyword.Bluemix_notm}}. Che succede?
{: #faq_uk}

**Domanda completa:**

Il mio progetto JazzHub è associato alla regione {{site.data.keyword.Bluemix_notm}} del Regno Unito in base alle impostazioni del progetto. Ho verificato le impostazioni del progetto andando alla pagina di panoramica su JazzHub, facendo clic sull'icona **Settings**, che ha la forma di un ingranaggio, e facendo clic su **Options &gt; Make this an {{site.data.keyword.Bluemix_notm}} Project: Region**. Dopo aver eseguito l'upgrade del progetto alla toolchain negli Stati Uniti, si verificano questi problemi:

   1. Quando seleziono l'organizzazione degli Stati Uniti, visualizzo un messaggio che dice che l'organizzazione non ha uno spazio nella regione Stati Uniti Sud e mi viene richiesto di creare uno spazio. Non voglio eseguire nulla negli Stati Uniti.
   
   2. Alcuni dei miei colleghi non possono accedere alla toolchain, anche se sono stati elencati come membri nel progetto JazzHub originale. Se provano ad aprire la toolchain dalla pagina di panoramica dell'applicazione nella regione Regno Unito facendo clic su **View Toolchain**, visualizzano un messaggio di "accesso negato".
   
   3. Non vedo la toolchain elencata nella pagina Toolchains all'indirizzo [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, anche se posso accedere alla toolchain direttamente dalla pagina di panoramica dell'applicazione nella regione Regno Unito facendo clic su **View Toolchain**. Visualizzo un errore che indica che non possono modificare la toolchain o un errore che indica che non ho una toolchain e che devo crearne una. 

**Risposta:**

Questi problemi si verificano se provieni da una regione {{site.data.keyword.Bluemix_notm}} diversa dagli Stati Uniti e non espandi in modo esplicito la tua organizzazione nella regione Stati Uniti Sud prima di eseguire l'upgrade. Puoi confermare questo scenario in due modi:

   * Quando apri l'URL della toolchain, controlla l'intestazione {{site.data.keyword.Bluemix_notm}}. Molto probabilmente, vedrai il tuo nome dell'organizzazione e non viene indicato alcuno spazio.
   
   * Dalla pagina di panoramica della tua toolchain, fai clic su **Manage**. Nella pagina Access Control, fai clic sul link **Org managers**. L'organizzazione che contiene la toolchain viene elencata nella pagina principale.

Ciò che è accaduto è che al momento dell'upgrade, la tua organizzazione non statunitense non esisteva negli Stati Uniti, pertanto l'upgrade ha selezionato per te un'altra organizzazione cercando tra quelle a cui hai accesso.

Se passi a quella organizzazione {{site.data.keyword.Bluemix_notm}} negli Stati Uniti, puoi trovare la toolchain. Se aggiungi i tuoi colleghi a tale organizzazione, viene loro concesso l'accesso. Questa toolchain può continuare a distribuire nella tua organizzazione non statunitense. L'unico problema è che queste due organizzazioni sono distinte e non puoi eseguire la gestione degli utenti su entrambe automaticamente.

Se desideri che la tua toolchain sia in un'organizzazione statunitense che corrisponde alla tua organizzazione non statunitense, completa questa procedura:

   1. Accedi a [https://console.bluemix.net ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net){: new_window} e seleziona la regione non statunitense e l'organizzazione da cui provieni.
   
   2. Nell'intestazione {{site.data.keyword.Bluemix_notm}}, passa alla regione Stati Uniti Sud. Ti viene richiesto di creare uno spazio in tale regione.
   
   3. Crea uno spazio nella regione Stati Uniti Sud per espandere la tua organizzazione in tale regione. 
   
   4. Elimina la toolchain creata attraverso il processo di upgrade. 
   
      Il repository Git non viene eliminato automaticamente. Per ora potresti volerlo eliminare manualmente o rinominare. Se già hai modificato il repository, puoi aggiornare la futura toolchain per utilizzarla in seguito.
      {: tip}

   5. Torna al progetto JazzHub. Questo viene ripristinato per un altro tentativo di upgrade. Se non viene ripristinato, contatta hub@jazz.net e fornisci l'URL del progetto.
   
   6. Riavvia il processo di upgrade e assicurati di selezionare l'organizzazione appropriata negli Stati Uniti, che corrisponde al nome della tua organizzazione nella regione non statunitense.
   
   7. Se hai mantenuto o rinominato il repository Git dal tentativo di upgrade della toolchain precedente, (vedi il passo 4), puoi riconfigurare la scheda Git nella tua toolchain in modo da puntare invece all'URL di questo repository Git. La modifica viene automaticamente riflessa nella pipeline. Per confermare, controlla la scheda Input nella fase di build.
