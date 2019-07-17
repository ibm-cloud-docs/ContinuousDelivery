---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# Utilizzo e limitazioni del piano
{: #limitations_usage}

L'utilizzo di {{site.data.keyword.contdelivery_full}} è limitato alla creazione, distribuzione, verifica e alle operazioni in corso delle applicazioni sulla piattaforma {{site.data.keyword.Bluemix_notm}} o su altre offerte platform-as-a-service o infrastructure-as-a-service compatibili.

## Ambito di un'istanza del servizio
{: #service_scope}

Devi avere una {{site.data.keyword.contdelivery_short}} [istanza del servizio](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} per creare e utilizzare le toolchain DevOps. Un'istanza del servizio potrebbe appartenere a un [gruppo di risorse](/docs/services/resources?topic=resources-rgs) {{site.data.keyword.Bluemix_notm}} IAM (Identity and Access Management) o a un'organizzazione (org) {{site.data.keyword.Bluemix_notm}}.

Puoi creare delle *nuove* istanze del servizio {{site.data.keyword.contdelivery_short}} solo nei gruppi di risorse. La migrazione di toolchain da organizzazioni a gruppi di risorse non è attualmente supportata. Se ti manca un servizio {{site.data.keyword.contdelivery_short}} per un'organizzazione che contiene delle toolchain, puoi creare nuovamente le toolchain in un gruppo di risorse oppure contattare il [supporto IBM](https://cloud.ibm.com/unifiedsupport){:external} per assistenza.

Puoi avere solo un singolo servizio Lite per ogni account. Ti consigliamo di usare il piano Professional se vuoi gestire le toolchain in più organizzazioni o gruppi di risorse oppure all'interno di più regioni.
{: tip}


## Utenti autorizzati
{: #authorized_users}

I [piani di servizio](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} {{site.data.keyword.contdelivery_short}} sono definiti e il loro prezzo è determinato in base al numero di utenti autorizzati per un'istanza del servizio. Chiunque contribuisca a uno sforzo deve essere considerato un utente autorizzato, compresi:

 * Gli utenti che interagiscono con i problemi, con i pannelli dei problemi, con il codice sorgente o altre risorse utente in un repository {{site.data.keyword.gitrepos}}.
 * Gli utenti che manipolano, attivano (direttamente nell'interfaccia utente o indirettamente eseguendo il commit a un repository) o visualizzano lo stato di una delivery pipeline.
 * Gli utenti che interagiscono con Eclipse Orion {{site.data.keyword.webide}}.
 
Il piano Lite è soggetto a limiti. Per ulteriori informazioni sul piano Lite e sul piano Professional, vedi il [catalogo dei servizi](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}
 
### Come vengono contati gli utenti per le istanze di {{site.data.keyword.contdelivery_short}} nei gruppi di risorse?

Gli utenti autorizzati vengono conteggiati e gestiti per ogni istanza del servizio esaminando l'elenco degli utenti autorizzati per i limiti del piano Lite e di fatturazione. Gli utenti del servizio {{site.data.keyword.contdelivery_short}} vengono aggiunti automaticamente a questo elenco. Puoi impedire agli utenti di accedere alle toolchain e di essere aggiunti automaticamente a un'istanza del servizio {{site.data.keyword.contdelivery_short}}. Per ulteriori informazioni sull'utilizzo di IAM per rimuovere l'accesso utente dal gruppo di risorse che contiene la toolchain (o dalla toolchain stessa), vedi [Gestione dell'accesso utente a {{site.data.keyword.contdelivery_short}} con Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security). 

Il metodo che utilizzi per organizzare le toolchain all'interno dei gruppi di risorse si ripercuote direttamente sull'accesso utente e sulla fatturazione. Quando gli utenti utilizzano le toolchain in più gruppi di risorse, vengono conteggiati e fatturati per ogni servizio in tali gruppi di risorse.
{: tip}

Puoi gestire l'elenco di utenti autorizzati nella scheda **Gestisci** all'interno dell'istanza del servizio {{site.data.keyword.contdelivery_short}}.

1. Vai all'[Elenco risorse](https://cloud.ibm.com/resources){:external} per il tuo account {{site.data.keyword.Bluemix_notm}}.
2. Nella colonna **Nome** , nella casella di testo del filtro, immetti **Continuous Delivery** per visualizzare i tuoi servizi esistenti.
3. Per ciascun servizio, fai clic sul collegamento ipertestuale nella colonna **Nome**.
4. Nella scheda **Gestisci**, puoi visualizzare, aggiungere o rimuovere utenti dall'elenco di Utenti autorizzati, come necessario.

Gli utenti vengono automaticamente aggiunti o aggiunti nuovamente quando utilizzano il servizio {{site.data.keyword.contdelivery_short}}.
{: tip}

### Come vengono conteggiati gli utenti per le istanze di {{site.data.keyword.contdelivery_short}} nelle organizzazioni?

Gli utenti autorizzati vengono conteggiati verificando tutti gli utenti nell'organizzazione {{site.data.keyword.Bluemix_notm}} che contiene il servizio {{site.data.keyword.contdelivery_short}}. Per ulteriori informazioni sulle organizzazioni e sugli spazi, vedi [Creazione di organizzazioni e spazi](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

Per visualizzare l'elenco di utenti nella tua organizzazione in un ambiente {{site.data.keyword.Bluemix_notm}} Pubblico, dalla barra dei menu fai clic su **Gestisci > Account**. Fai quindi clic su **Organizzazioni Cloud Foundry**.

### Come puoi visualizzare le informazioni di fatturazione e di utilizzo?

Puoi visualizzare tutte le istanze del servizio {{site.data.keyword.contdelivery_short}} nel tuo account e il numero di utenti ed esecuzioni pipeline segnalati rispetto a ciascuna istanza in un ambiente {{site.data.keyword.Bluemix_notm}} Pubblico.

1. Dalla barra dei menu, fai clic su **Gestisci > Fatturazione e utilizzo**.
2. Fai clic su **Utilizzo**.
3. Nella sezione **Servizi**, fai clic su **Visualizza piani** per il servizio {{site.data.keyword.contdelivery_short}}.
4. Fai clic su **Visualizza dettagli** per il piano di cui desideri visualizzare le informazioni.
5. Fai clic su **Visualizza i dettagli dell'istanza** per l'istanza di {{site.data.keyword.contdelivery_short}} per cui desideri visualizzare le informazioni sull'utilizzo.

La metrica `AUTHORIZED_USERS_PER_MONTH` viene calcolata in base a una media mensile di utenti che viene conteggiata ogni giorno.
{: tip}

### Cosa succede quando si superano i limiti del proprio piano di servizio?

Il piano di servizio Lite ha altre limitazioni, quali il numero di lavori Delivery Pipeline che può essere eseguito oppure il consumo di archiviazione. Per ulteriori informazioni sulla descrizione del piano, vedi il [catalogo dei servizi](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. Se qualcuna delle limitazioni del piano viene superata in un periodo di fatturazione, il servizio viene sospeso. Ad esempio, i lavori Delivery Pipeline non vengono eseguiti per il resto del periodo di fatturazione.

## Utilizzo di Delivery Pipeline
{: #pipeline_usage}

Le modalità di utilizzo accettabili includono, ma non limitate a, i seguenti comportamenti:

* La compilazione e l'assemblaggio delle risorse per i linguaggi di programmazione supportati.
* La distribuzione automatizzata delle configurazioni e delle risorse dell'applicazione e dei servizi e delle risorse di supporto.
* La verifica, la convalida e gli altri comportamenti generati degli eventi di sviluppo che vengono attivati come risultato di un processo di sviluppo.

Le modalità di utilizzo che non sono consentite includono, ma non sono limitate a, i seguenti comportamenti:

* L'utilizzo dei lavori e dei nodi di lavoro della pipeline per i comportamenti di calcolo generali, come l'estrazione di Bitcoin, gli attacchi DoS (denial-of-service) distribuiti e il comportamento dannoso o offensivo verso altri clienti o utenti all'interno della piattaforma {{site.data.keyword.Bluemix_notm}} o agli utenti di Internet in generale.
* L'utilizzo nel normale processo di sviluppo per i siti o i servizi che promuovono incitamento all'odio o altre attività che violano le linee guida di condotta del business IBM.
* L'utilizzo del comportamento generato dagli eventi per le intrusioni dannose o per gli attacchi malintenzionati a {{site.data.keyword.Bluemix_notm}} o ad altri siti.

A discrezione di IBM, gli utenti che violano i comportamenti di utilizzo accettabili dei servizi {{site.data.keyword.contdelivery_short}} o le [Linee guida di condotta di business di IBM](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} possono essere disabilitati senza preavviso. A discrezione di IBM, alcuni servizi possono essere ripristinati se gli utenti correggono i loro comportamenti di utilizzo dopo che sono stati informati dell'azione offensiva. Altrimenti, gli account possono essere sospesi o terminati.

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
  2. I progetti privati sono visibili solo a utenti selezionati. Per ulteriori informazioni sulla concessione agli utenti dell'accesso a un progetto, vedi il documento relativo agli [utenti del progetto](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. I progetti interni sono visibili a tutti gli utenti che hanno eseguito l'accesso. Qualsiasi utente che ha un account {{site.data.keyword.Bluemix_notm}} può visualizzare questi progetti.

Puoi modificare il tipo di progetto nelle impostazioni del progetto. Per ulteriori informazioni sulle impostazioni del progetto, vedi [How to change project visibility](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

Quando usi {{site.data.keyword.gitrepos}}, il contenuto da te apportato a un progetto viene concesso in licenza in base ai termini specificati in tale progetto. Quando crei un progetto, includi un file che descrive la licenza che si applica al contenuto. Quando contribuisci a un progetto, il tuo nome e l'indirizzo email associato ai tuoi commit potrebbero essere visibili al pubblico. L'indirizzo email associato al tuo account {{site.data.keyword.Bluemix_notm}} viene utilizzato quando crei dei commit tramite l'interfaccia web {{site.data.keyword.gitrepos}}.
