---

copyright:
  years: 2016, 2018
lastupdated: "2018-4-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Utilizzo e limitazioni del piano
{: #limitations_usage}

L'utilizzo di {{site.data.keyword.contdelivery_full}} è limitato alla creazione, distribuzione, verifica e alle operazioni in corso delle applicazioni sulla piattaforma {{site.data.keyword.Bluemix_notm}} o su altre offerte platform-as-a-service o infrastructure-as-a-service compatibili.

## Utenti autorizzati
{: #authorized_users}

I piani di servizio {{site.data.keyword.contdelivery_short}} definiti e il loro prezzo è determinato in base al numero di utenti autorizzati di un'istanza del servizio. Chiunque contribuisca a uno sforzo deve essere considerato un utente autorizzato, compresi:

 * Gli utenti che interagiscono con i problemi, con i pannelli dei problemi, con il codice sorgente o altre risorse utente in un repository {{site.data.keyword.gitrepos}}.
 * Gli utenti che manipolano, attivano (direttamente nell'IU o indirettamente eseguendo il commit a un repository) o visualizzano lo stato di una delivery pipeline.
 * Gli utenti che interagiscono con Eclipse Orion {{site.data.keyword.webide}}.
 
### Come vengono contati gli utenti?

Gli utenti autorizzati vengono contati verificando tutti gli utenti nell'organizzazione (org) Cloud che contiene il servizio {{site.data.keyword.contdelivery_short}}. 

Per visualizzare l'elenco di utenti nella tua organizzazione, dalla barra dei menu fai clic su **Manage > Account > Cloud Foundry Orgs**.

Puoi anche visualizzare tutte le istanze del servizio {{site.data.keyword.contdelivery_short}} nel tuo account e il numero di utenti segnalati rispetto a ciascuna istanza.

1. Dalla barra dei menu, fai clic su **Manage > Account > Cloud Foundry Orgs**.
2. Fai clic su **Usage Dashboard**.

### Cosa succede quando si superano i limiti del proprio piano di servizio? 

Alcuni piani di servizio possono avere altre limitazioni, come ad esempio il numero di lavori Delivery Pipeline che possono essere eseguiti o il consumo di archiviazione. Per ulteriori informazioni, consulta la descrizione del piano nel catalogo. Se qualcuna delle limitazioni del piano viene superata in un periodo di fatturazione, il servizio potrebbe essere sospeso. Ad esempio, i lavori Delivery Pipeline potrebbero non essere eseguiti per il resto del periodo di fatturazione.

## Utilizzo di Delivery Pipeline
{: #pipeline_usage}

Le modalità di utilizzo accettabili includono, ma non limitate a, i seguenti comportamenti:

* La compilazione e l'assemblaggio delle risorse per i linguaggi di programmazione supportati
* La distribuzione automatizzata delle configurazioni e delle risorse dell'applicazione e dei servizi e delle risorse supportati.
* La verifica, la convalida e gli altri comportamenti generati dell'evento di sviluppo che vengono attivati come risultato di un processo di sviluppo

Le modalità di utilizzo che non sono consentite includono, ma non sono limitate a, i seguenti comportamenti:

* L'utilizzo dei lavori e dei nodi di lavoro della pipeline per i comportamenti di calcolo generale, come l'estrazione di Bitcoin, gli attacchi DoS (denial-of-service) distribuiti e il comportamento dannoso o offensivo ad altri clienti o utenti all'interno della piattaforma IBM Cloud o agli utenti generali di Internet
* L'utilizzo nel normale processo di sviluppo per i siti o i servizi che promuovono incitamento all'odio o altre attività che violano le linee guida di condotta del business IBM.
* L'utilizzo del comportamento generato dall'evento per le intrusioni dannose o per gli attacchi a {{site.data.keyword.Bluemix_notm}} o ad altri siti

A discrezione di IBM, gli utenti che violano i comportamenti di utilizzo accettabili dei servizi {{site.data.keyword.contdelivery_short}} o le [Linee guida di condotta di business di IBM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} possono essere disabilitati senza preavviso. A discrezione di IBM, alcuni servizi possono essere ripristinati se gli utenti correggono i loro comportamenti di utilizzo dopo che sono stati informati dell'azione offensiva. Altrimenti, gli account possono essere sospesi o terminati.

## Limitazioni di Git Repos and Issue Tracking
{: #git_limitations}

{{site.data.keyword.gitrepos}} è sviluppato su GitLab Community Edition e ospitato da IBM su {{site.data.keyword.Bluemix_notm}}; tuttavia, alcune opzioni GitLab non sono disponibili:

 * Poiché {{site.data.keyword.deliverypipeline}} fornisce l'integrazione e la fornitura continue per {{site.data.keyword.Bluemix_notm}}, le funzioni di integrazione continua in GitLab non sono supportate.
 * Le funzioni di gestione GitLab non sono disponibili perché sono gestite da IBM.
 * {{site.data.keyword.gitrepos}} potrebbe non essere completamente accessibile.

## Informazioni sugli utenti e contenuto di Git Repos and Issue Tracking
{: #git_projects}

Sono disponibili tre tipi di progetti {{site.data.keyword.gitrepos}}:

  1. I progetti pubblici sono visibili a tutti i visitatori del sito. Il contenuto in un progetto pubblico è visibile a tutti gli utenti che accedono a {{site.data.keyword.contdelivery_short}}, anche se non sono invitati al progetto.
  2. I progetti privati sono visibili solo a utenti selezionati. Per informazioni dettagliate sulla concessione agli utenti dell'accesso a un progetto, consulta [Project users ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}.
  3. I progetti interni sono visibili a tutti gli utenti che hanno eseguito l'accesso. Qualsiasi utente che ha un account {{site.data.keyword.Bluemix_notm}} può visualizzare questi progetti.

Puoi modificare il tipo di progetto nelle impostazioni del progetto. Per ulteriori informazioni, consulta [How to change project visibility ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

Quando usi {{site.data.keyword.gitrepos}}, il contenuto da te apportato a un progetto viene concesso in licenza in base ai termini specificati in tale progetto. Quando crei un progetto, includi un file che descrive la licenza che si applica al contenuto. Quando contribuisci a un progetto, il tuo nome e l'indirizzo email associato ai tuoi commit potrebbero essere visibili al pubblico. L'indirizzo email associato al tuo account {{site.data.keyword.Bluemix_notm}} viene utilizzato quando crei dei commit tramite l'interfaccia web {{site.data.keyword.gitrepos}}.

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
