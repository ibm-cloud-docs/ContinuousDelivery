---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-08"

keywords: run jobs, sequences of stages, job types

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Panoramica di Delivery Pipeline
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} include Delivery Pipeline per creare , testare e distribuire in modo ripetibile con un minimo intervento umano. In una pipeline, le sequenze di fasi richiamano l'input ed eseguono i lavori, come le build, i test e le distribuzioni.
{:shortdesc}

Le tue autorizzazioni per visualizzare, modificare o eseguire una pipeline sono basate sul controllo dell'accesso per la toolchain che gestisce la pipeline. Per ulteriori informazioni sul controllo dell'accesso per le toolchain, fai riferimento a [Gestione dell'accesso alle toolchain nei gruppi di risorse](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups){: new_window} e [Gestione dell'accesso alle toolchain nelle organizzazioni Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.
{: important}

Puoi specificare gli script da eseguire in molti dei tipi di lavoro forniti dalla pipeline, dandoti un controllo diretto su quello che viene eseguito dal lavoro. Tali script vengono eseguiti in un'immagine Docker che contiene diversi strumenti di sviluppo standard, compresi gli strumenti necessari per interagire con i runtime {{site.data.keyword.Bluemix_notm}}. Per ulteriori informazioni su quello che l'immagine Docker standard contiene, vedi [Risorse preinstallate](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources){: new_window}. Se il tuo lavoro richiede degli strumenti di sviluppo che non sono disponibili nell'immagine standard, o se hai bisogno di versioni differenti di tali strumenti, puoi utilizzare un'immagine personalizzata. Per ulteriori informazioni sulle immagini personalizzate, vedi [Utilizzo di immagini docker personalizzate](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images#custom_docker_images){: new_window}.

Quando la pipeline esegue gli script, le proprietà che descrivono il contesto in cui il lavoro è in esecuzione vengono passate allo script utilizzando le variabili di ambiente. Ad esempio, l'URL del repository che è l'input alla fase, il nome della fase e il lavoro che si sta eseguendo, i parametri specificati dal tipo di lavoro e così via. Per visualizzare un elenco delle variabili di ambiente disponibili, vedi [Risorse preinstallate](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources). 

Puoi definire le proprietà sia a livello di pipeline che a livello di fase. Le proprietà di pipeline vengono condivise in tutte le fasi e tutti i lavori in una pipeline. Le proprietà di fase sono univoche per una specifica fase e condivise in tutti i lavori in tale fase. Per ulteriori informazioni sulle proprietà, vedi [Proprietà dell'ambiente (variabili di ambiente)](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#environment_properties).

## Fasi
{: #deliverypipeline_stages}

Le fasi organizzano l'input e i lavori e come il tuo codice viene generato, distribuito e verificato. Le fasi accettano l'input dai repository di controllo dell'origine (repository SCM) o dai lavori di build in altre fasi. Per i repository SCM, l'input è il contenuto di uno specifico ramo nel repository; per i lavori di build, l'input consiste nelle risorse utente prodotte dal lavoro. Quando crei la tua prima fase, la scheda **INPUT** contiene le impostazioni predefinite.

Quando una fase viene eseguita, il suo input viene passato a ciascuno dei lavori in essa contenuti. A ogni lavoro viene assegnato un contenitore pulito in cui essere eseguito. Di conseguenza, i lavori all'interno di una fase non possono passarsi le risorse utente tra di loro. Per passare le risorse utente tra i lavori, separa i lavori in due fasi e usa l'output dal lavoro nella prima fase come input alla seconda fase.
{: tip}

Analogamente a come puoi definire le proprietà della pipeline, puoi anche definire le proprietà di fase per l'utilizzo in tutti i lavori in una specifica fase. Ad esempio, puoi definire una proprietà `TEST_URL` che passa un URL ai lavori di distribuzione e test in una fase. Il lavoro di distribuzione esegue la distribuzione a tale URL e il lavoro di test esegue un test dell'applicazione in esecuzione a tale URL. Le proprietà di fase vengono passate anche agli script di lavoro utilizzando le variabili di ambiente. Se qualche proprietà è definita sia al livello di pipeline che al livello di fase, viene utilizzato il valore della proprietà di fase.

Per impostazione predefinita, in una fase le creazioni e le distribuzioni vengono eseguite automaticamente ogni volta che si distribuiscono delle modifiche al repository SCM di un progetto. Le fasi e i lavori vengono eseguiti serialmente; abilitano il controllo del flusso per il tuo lavoro. Ad esempio, puoi posizionare una fase di verifica prima di una fase di distribuzione. Se i test nella fase di test hanno esito negativo, la fase di distribuzione non viene eseguita.

Potresti desiderare di avere maggiore controllo su una fase specifica. Se non desideri che una fase venga eseguita ogni volta che viene effettuata una modifica nel relativo input, puoi disabilitare tale funzionalità. Nella scheda **INPUT**, nella sezione Stage Trigger, fai clic su **Run jobs only when this stage is run manually**.

![La scheda INPUT](images/input_tab_only_execute.png)


### Fase di build
{: #build_stage}

La fase di build specifica un **tipo Builder** per indicare come creare le risorse utente.  

Molti dei campi disponibili nei lavori di build sono comuni in più tipi di Builder.
{: tip}

Sono disponibili i seguenti tipi di Builder:

* **Simple** - i lavori che utilizzano il tipo di builder **Simple** prendono l'input della fase corrente e, senza modificarlo, ne eseguono l'archiviazione per un utilizzo da parte delle future fasi. Di norma, il tipo di builder **Simple** è utile solo quando l'input della fase proviene da un repository SCM.
* **Ant** - utilizza questo tipo di builder per utilizzare i file Ant Apache per gestire il lavoro di build.
  * **Build script** - questo tipo di builder può essere qualsiasi script di build valido. Per impostazione predefinita, questo tipo di builder è impostato su 'ant'.
  * **Working directory** - specifica la directory dove viene eseguito lo script.
  * **Build archive directory** - Specifica la directory che contiene l'output del lavoro da archiviare per un utilizzo da parte di una fase successiva.
  * **Enable test report** - Seleziona questa casella di spunta per specificare che il lavoro di build esegue dei test che producono file di risultato in formato XML JUnit. Un report basato sui file dei risultati viene visualizzato nella scheda Test della pagina Job Results. Se un qualsiasi test ha esito negativo, il lavoro viene contrassegnato come non riuscito.
  * **Enable code coverage report** - seleziona questa casella di spunta per visualizzare ulteriori campi che puoi utilizzare per il report di copertura del codice. Puoi specificare lo strumento di esecuzione della copertura (come Istanbul, JaCoCo o Cobertura), l'ubicazione del file di risultato della copertura e la directory del risultato della copertura, relativa alla directory di lavoro.
* **Container Registry**
* **Gradle (Artifactory, Nexus o SonarQube)**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven (Artifactory, Nexus o SonarQube)**
* **npm (Artifactory o Nexus)**
* **Script di shell**

### Fase di distribuzione
La fase di distribuzione specifica l'input da una fase di build.  I lavori nella fase di distribuzione specificano un **tipo Deployer**.  Sono disponibili i seguenti tipi Deployer:

1. **Cloud Foundry**
2. **Kubernetes**

## Lavori
{: #deliverypipeline_jobs}

Il lavoro è un'unità di esecuzione in una fase. Una fase può contenere più lavori e i lavori in una fase vengono eseguiti in sequenza. Per impostazione predefinita, se un lavoro ha esito negativo, il lavoro seguente nella fase non viene eseguito.

![Lavori di creazione e di test in una fase](images/jobs.png)

I lavori vengono eseguiti in directory di lavoro separate all'interno dei contenitori Docker che sono stati creati per ogni esecuzione della pipeline. Prima che un lavoro venga eseguito, la relativa directory di lavoro viene compilata con l'input definito al livello della fase. Ad esempio, puoi avere una fase che contiene un lavoro di verifica e un lavoro di distribuzione. Se installi le dipendenze su un lavoro, non sono disponibili per un altro lavoro. Tuttavia, se rendi le dipendenze disponibili nell'input della fase, sono disponibili per entrambi i lavori.

Con eccezione dei lavori di creazione di tipo semplice, quando configuri un lavoro, puoi includere gli script shell UNIX che includono i comandi di creazione, verifica o distribuzione. Poiché i lavori sono eseguiti in un contenitore ad hoc, le azioni di un contenitore non possono influenzare gli ambienti di esecuzione di altri lavori, anche se tali lavori sono parte della stessa fase.

Degli script di build e di distribuzione di esempio sono disponibili in [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

In aggiunta, i lavori della pipeline possono eseguire solo i seguenti comandi come `sudo`:
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


Dopo l'esecuzione di un lavoro, il contenitore creato per esso viene eliminato. I risultati di un'esecuzione di un lavoro possono essere conservati, ma l'ambiente nel quale è stato eseguito non può esserlo.

I lavori possono essere eseguiti fino a un massimo di 60 minuti. Quando i lavori superano tale limite, vengono considerati con esito negativo. Se un lavoro sta per superare il limite, suddividilo in più lavori. Ad esempio, se un lavoro esegue tre attività, puoi suddividerlo in tre lavori: uno per ogni attività.
{: tip}

Per maggiori informazioni su come aggiungere un lavoro a una fase, consulta [Aggiunta di un lavoro a una fase](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy#deliverypipeline_add_job){: new_window}.

### Lavori di creazione

I lavori di creazione compilano il tuo progetto durante la preparazione per la distribuzione. Essi generano delle risorse utente che possono essere inviate a una directory di archivio di creazione, sebbene per impostazione predefinita, le risorse utente vengono posizionate nella directory root del progetto.

I lavori che ricevono l'input dai lavori di creazione devono far riferimento alle risorse utente di creazione nella stessa struttura in cui sono state create. Ad esempio, se un lavoro di creazione archivia le risorse utente di creazione in una directory `output`, uno script di distribuzione deve fare riferimento alla directory `output` anziché alla directory root del progetto per distribuire il progetto compilato. Puoi specificare la directory di archivio immettendo il nome directory nel campo **Build Archive Directory**. Lasciando il campo vuoto, si archivierà la directory root.

Se utilizzi il tipo di builder **Simple**, il codice non viene compilato o creato; invece viene inserito in un pacchetto e reso disponibile per le fasi future.
{: tip}

Quando distribuisci utilizzando Cloud Foundry, Cloud Foundry include le risorse corrette per consentire l'esecuzione della tua applicazione. Per ulteriori informazioni, vedi [Distribuzione delle applicazioni mediante il comando cf](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#deploy_apps). La pipeline per un'applicazione Cloud Foundry contiene una fase di distribuzione che esegue un comando cf.

Cloud Foundry tenta di [rilevare il pacchetto di build da utilizzare ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://docs.cloudfoundry.org/buildpacks/detection.html). Puoi specificare il [pacchetto di build](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_buildpacks#using_buildpacks) da utilizzare nel file manifest all'interno della cartella root della tua applicazione. I pacchetti di build generalmente esaminano le risorse fornite dall'utente per determinare quali dipendenze scaricare e come configurare le applicazioni per comunicare con i servizi associati. Per ulteriori informazioni sui file manifest, vedi [Manifest dell'applicazione](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).

### Lavori di distribuzione

I lavori di distribuzione caricano il tuo progetto in {{site.data.keyword.Bluemix_notm}} come un'applicazione e sono accessibili da un URL. Dopo che il progetto è stato distribuito, puoi trovare l'applicazione distribuita nel tuo dashboard {{site.data.keyword.Bluemix_notm}}.

I lavori di distribuzione possono distribuire nuove applicazioni o aggiornare applicazioni esistenti. Anche se hai prima distribuito un'applicazione utilizzando un altro metodo, come l'interfaccia della riga di comando Cloud Foundry o la barra di esecuzione nell'IDE web, puoi aggiornare l'applicazione utilizzando un lavoro di distribuzione. Per aggiornare un'applicazione, nel lavoro di distribuzione, utilizza il nome dell'applicazione.

Puoi eseguire la distribuzione a uno o più regioni e servizi. Ad esempio, puoi impostare il tuo {{site.data.keyword.deliverypipeline}} per utilizzare uno o più servizi, eseguire verifiche in una regione e distribuire in produzione in più regioni.

### Lavori di verifica
Se desideri richiedere che vengano rispettate le condizioni, includi i lavori di verifica prima o dopo i tuoi lavori di distribuzione o di creazione. Puoi personalizzare i lavori di verifica in modo che siano semplici o complessi a secondo dei tuoi bisogni. Ad esempio, puoi immettere un comando cURL e attendere una risposta particolare. Puoi anche eseguire una suite di verifiche dell'unità o di verifiche funzionali dell'esecuzione con servizi di verifica di terze parti, come ad esempio Sauce Labs.

Se le tue verifiche producono dei file dei risultati nel formato XML JUnit, viene visualizzato un report che si basa sui file dei risultati nella scheda **Tests** per ogni pagina del risultato della verifica. Se una verifica ha esito negativo, anche il lavoro ha esito negativo.

## Proprietà dell'ambiente (variabili di ambiente)
{: #environment_properties}

Una serie di proprietà di ambiente predefinite fornisce l'accesso alle informazioni sull'ambiente di esecuzione del lavoro. Per un elenco completo delle proprietà dell'ambiente predefinite, vedi [Risorse e proprietà dell'ambiente](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment).

Puoi anche definire delle tue proprietà dell'ambiente. Ad esempio, puoi definire una proprietà `API_KEY` che passa una chiave API che viene utilizzata per accedere alle risorse {{site.data.keyword.Bluemix_notm}} da tutti gli script nella pipeline.

Puoi aggiungere i seguenti tipi di proprietà:

* **Text**: una chiave della proprietà con un valore a singola riga.
* **Text Area**: una chiave della proprietà con un valore a più righe.
* **Secure**: una chiave della proprietà con un valore a singola riga che è protetta con una crittografia AES-128. Il valore viene visualizzato come degli asterischi.
* **Proprietà**: un file nel repository del progetto. Questo file può contenere più proprietà. Ogni proprietà deve essere sulla propria riga. Per coppie di valore-chiave separate, utilizzare il segno uguale (=). Racchiudi tutti i valori stringa tra virgolette. Ad esempio, `MY_STRING="SOME STRING VALUE"`.

Puoi esaminare le proprietà dell'ambiente per un lavoro della pipeline eseguendo il comando `env` nello script del lavoro.
{:tip}

### Proprietà della pipeline
Per definire le proprietà della pipeline, dal menu overflow nella pagina Pipeline, seleziona **Configure Pipeline**.

![Menu overflow della pipeline](images/OverflowMenu.png)

Dalla scheda **ENVIRONMENT PROPERTIES** nella pagina Pipeline configuration. imposta le proprietà dell'ambiente a livello della pipeline.

![Pagina properties della pipeline](images/PipelineProperties.png)

### Proprietà della fase
Per definire le proprietà della fase, apri la pagina Stage configuration e fai clic sulla scheda **ENVIRONMENT PROPERTIES**.

![Pagina properties della fase](images/StageProperties.png)

Puoi anche passare le variabili di ambiente tra i lavori nella stessa fase esportando le proprietà. Ad esempio, puoi includere il seguente comando per utilizzare la proprietà `$API_KEY` in un altro lavoro all'interno della fase:`export API_KEY=<insert API key here>`
{:tip}

### Proprietà calcolate
Puoi calcolare i valori delle proprietà di ambiente che sono condivisi nelle fasi creando un file `build.properties` mentre la fase è in esecuzione e lasciare quindi che la fase successiva esegua il file. Ad esempio, il tuo lavoro di build può includere il seguente comando nello script di build:

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

Tutti i lavori iniziano eseguendo il file `build.properties`, se esiste.

## Creazione e utilizzo di risorse utente
{: #artifacts}

I lavori di build recuperano automaticamente il contenuto nella cartella corrente dove viene eseguito lo script utente.  Se non ti serve tutto il contenuto del repository git per la successiva distribuzione, è preferibile che configuri una directory di output esplicita e che quindi copi o crei lì le risorse utente pertinenti.  Gli script del lavoro vengono eseguiti nel risultato della build (directory di output).

I lavori che eseguono la distribuzione a Cloud Foundry devono specificare la chiave API della piattaforma di un utente per cui tali lavori di autorità sono eseguiti e la regione, l'organizzazione e lo spazio dove distribuire le risorse utente. Se sono necessari ulteriori servizi per eseguire la tua applicazione, devi specificarli nel file `manifest.yml`.

I lavori di distribuzione che eseguono la distribuzione a {{site.data.keyword.containerlong_notm}} hanno bisogno di specificare la chiave API della piattaforma di un utente per cui tali lavori di autorità sono eseguiti, un Dockerfile e, facoltativamente, un grafico Helm.  

Lo script del lavoro viene eseguito dopo che il lavoro ha eseguito l'accesso all'ambiente di destinazione utilizzando la chiave API della piattaforma assegnata ad esso (in modo che tu possa eseguire i comandi `cf push` o `kubectl` nello script).

## Una pipeline di esempio
{: #deliverypipeline_example}

Una pipeline di esempio può contenere tre fasi:

1. Una fase di build che compila ed esegue i processi di creazione su un'applicazione.
2. Una fase di verifica che distribuisce un'istanza dell'applicazione e successivamente esegue le verifiche su di essa.
3. Una fase di produzione che distribuisce un'istanza di produzione dell'applicazione verificata.

Questa pipeline viene mostrata nel seguente diagramma concettuale:

![Diagramma concettuale di fasi e lavori in una pipeline](images/diagram.jpg)

*Un modello concettuale di una pipeline a tre fasi*

Le fasi ricevono i loro input dai repository e dai lavori di creazione e i lavori all'interno di una fase eseguono in sequenza e indipendentemente ogni lavoro. Nella pipeline di esempio, le fasi sono eseguite in sequenza, anche se le fasi di verifica e produzione prendono entrambe l'output della fase di build come proprio input.

## File manifest di Cloud Foundry
{: #deliverypipeline_manifest}

I file manifest, denominati `manifest.yml` sono archiviati nella directory root del progetto e controllano come il tuo progetto viene distribuito a {{site.data.keyword.Bluemix_notm}}. Per informazioni sulla creazione dei file manifest per un progetto, consulta la [documentazione {{site.data.keyword.Bluemix_notm}} sui manifest dell'applicazione](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest). Per l'integrazione con {{site.data.keyword.Bluemix_notm}}, il tuo progetto deve disporre di un file manifest nella relativa directory root. Tuttavia, non è obbligatorio eseguire la distribuzione in base alle informazioni nel file.

Nella pipeline, puoi specificare tutto quanto può fare un file manifest utilizzando gli argomenti del comando `cf push`. Gli argomenti del comando `cf push` sono utili nei progetti con più destinazioni di distribuzione. Se più lavori di distribuzione tentano tutti di utilizzare la rotta specificata nel file manifest del progetto, si verifica un conflitto.

Per prevenire i conflitti, puoi specificare una rotta utilizzando `cf push` seguito all'argomento del nome host, `-n` e un nome della rotta. Modificando lo script di distribuzione per le singole fasi, puoi prevenire conflitti di rotta quando distribuisci a più destinazioni.

Per utilizzare gli argomenti del comando `cf push`, apri le impostazioni di configurazione per un lavoro di distribuzione e modifica il campo **Deploy Script**. Per ulteriori informazioni, consulta la documentazione [Cloud Foundry Push ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
