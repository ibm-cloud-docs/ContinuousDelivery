---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-27"

keywords: IBM Cloud button, yml file, build file

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Creazione di un pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}} {: #deploy-button}

Il pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}} è un modo efficace per condividere la tua applicazione originata da Git pubblica in modo che altri utenti possano sperimentarne il codice ed eseguirne la distribuzione a {{site.data.keyword.Bluemix_notm}} utilizzando una toolchain. Il pulsante richiede una configurazione minima e puoi inserirlo dovunque siano supportate le markup. Un utente che fa clic sul pulsante crea una copia clonata del codice in un nuovo repository Git in modo che la tua applicazione originale rimanga inalterata.  
{: shortdesc}

Quando qualcuno fa clic sul tuo pulsante, si verificano le seguenti azioni:

1. Se la persona non ha un account {{site.data.keyword.Bluemix_notm}} attivo, deve creare un account. Può creare un account di prova o un account reale.

2. La persona può selezionare una regione, un gruppo di risorse (disponibile nelle regioni Stati Uniti Sud, Stati Uniti Est, Regno Unito, Germania e Tokyo) oppure l'organizzazione e lo spazio (disponibili nelle regioni Stati Uniti Sud, Regno Unito e Germania) e il nome applicazione facendo clic sull'icona {{site.data.keyword.deliverypipeline}}. Il nome suggerito per l'applicazione è uguale al nome della toolchain, che viene creato dal nome del tuo repository Git originale e dell'ora. Il nome della toolchain può anche essere modificato.

3. Viene creata una toolchain che include un nuovo clone privato del tuo repository Git, una pipeline per la creazione e distribuzione delle modifiche di codice, Eclipse Orion {{site.data.keyword.webide}} per la modifica del codice sul Cloud e un programma di traccia dei problemi.

  Se la directory `.bluemix` contiene un file `toolchain.yml`, questo file viene utilizzato per specificare le integrazioni dello strumento per la toolchain. Per ulteriori informazioni sul file `toolchain.yml`, vedi [Creazione di toolchain personalizzate](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_custom){: new_window}.
  {: tip}

4. Se l'applicazione richiede un file di build, esso viene rilevato automaticamente e l'applicazione viene creata.

5. Se una pipeline viene configurata per il processo di creazione e di distribuzione, viene utilizzato un file `pipeline.yml` per distribuire l'applicazione.

6. Se l'applicazione richiede un contenitore, viene utilizzato un file `pipeline.yml` che definisce {{site.data.keyword.containerlong_notm}} e un Dockerfile che definisce un'immagine per distribuire l'applicazione in {{site.data.keyword.containerlong_notm}}.

7. L'applicazione viene distribuita all'organizzazione {{site.data.keyword.Bluemix_notm}} selezionata dalla persona.

## Esempi del pulsante {: #button-examples}

Vedi un esempio di pulsante dell'applicazione per un repository {{site.data.keyword.gitrepos}} pubblico:

[![Distribuisci a IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

Vedi un esempio di pulsante dell'applicazione per un repository GitHub pubblico:

[![Distribuisci a IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## Creazione di un pulsante {: #create-button}

Per creare un pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}}, copia e modifica uno dei seguenti template di frammento. Specifica un repository e un ramo Git nell'URL.

### Creazione di un pulsante in HTML

Per creare un pulsante in HTML, copia questo frammento e inserisci un ramo e URL del repository Git pubblico.

```HTML
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://cloud.ibm.com/devops/setup/deploy/button.png" alt="Distribuisci a IBM Cloud"></a>
```
{: codeblock}

Se non includi il parametro `branch` nell'URL del repository del frammento, il pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}} utilizza come valore predefinito il ramo principale del repository.

### Creazione di un pulsante in Markdown

Per creare un pulsante in Markdown, copia questo frammento e inserisci un ramo e URL del repository Git pubblico.

```Markdown
[![Distribuisci a IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

Se non includi il parametro `branch` nell'URL del repository del frammento, il pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}} utilizza come valore predefinito il ramo principale del repository.

### Utilizzo dei frammenti del pulsante {: #button-snippet}

Dopo aver creato un frammento di pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}}, puoi inserirlo in blog, articoli, wiki, file readme o ovunque tu voglia promuovere la tua applicazione.

Quando personalizzi il frammento per il tuo pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}}, considera che entrambi i template utilizzano un percorso predefinito a un'immagine pulsante esterna in formato PNG e in inglese.

* Se per il pulsante preferisci utilizzare un'immagine SVG invece di PNG, modifica il percorso dell'immagine pulsante utilizzata nel frammento in `https://cloud.ibm.com/devops/setup/deploy/button.svg`.

* Se per il pulsante preferisci utilizzare un'immagine, modifica il percorso dell'immagine del pulsante utilizzata nel frammento in `https://cloud.ibm.com/devops/setup/deploy/button_x2.png`. Questa immagine è due volte la dimensione di quella predefinita.

* Se preferisci memorizzare l'immagine localmente, puoi scaricare l'immagine e memorizzarla nel repository Git. Regola il percorso per utilizzare l'ubicazione relativa dell'immagine.

* Se vuoi utilizzare una versione tradotta del pulsante, puoi fare riferimento a esso in remoto oppure scaricarlo da [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}.

## Considerazioni sul repository {: #button-repo}

Consulta queste considerazioni per il repository che utilizzi nel tuo pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}}.


### Requisiti dei file di build
{: build_file}

Se occorre creare l'applicazione prima che possa essere distribuita, devi includere un file di build nel tuo repository. Se viene rilevato un file script di build nella directory root del repository, viene attivato un build automatico del codice prima della distribuzione.

I builder supportati includono:

* [Ant ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`, che crea l'output nella cartella `./output/`
* [Gradle ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"):](https://docs.gradle.org/current/userguide/getting_started.html){:new_window} `/build.gradle`, che crea l'output nella cartella `.`
* [Grunt ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`, che crea l'output nella cartella `.`
* [Maven ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"):](http://maven.apache.org/guides/introduction/introduction-to-the-pom.html){:new_window} `/pom.xml`, che crea l'output nella cartella `./target/`

### Requisiti dei file pipeline
{: pipeline_file}

Per configurare la pipeline per la toolchain in una directory `.bluemix`, includi un file `pipeline.yml`. Per ogni file `pipeline.yml` in tale directory, viene creata una pipeline dopo aver istanziato la toolchain.

Se non hai il file `pipeline.yml` nella directory `.bluemix`, il pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}} creerà una pipeline predefinita con due fasi: una fase di build e una fase di distribuzione che esegue la distribuzione a Cloud Foundry.

Per creare un file pipeline, vedi il file di esempio nelle [istruzioni sulla pipeline di toolchain personalizzata](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_custom#toolchains_custom_pipeline_yml). Come quando definisci una pipeline nell'interfaccia web, definisci una pipeline in testo creando fasi e lavori, impostando input e variabili di ambiente e aggiungendo script. Puoi anche vedere alcuni file di pipeline più complessi in [questo progetto di dimostrazione](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix).

### Requisiti dei Dockerfile di contenitore
{: container_dockerfile}

Per distribuire un'applicazione in un contenitore utilizzando {{site.data.keyword.containerlong_notm}}, devi includere un Dockerfile nella directory root del repository e, in una directory `.bluemix`, devi includere un file `pipeline.yml`.

Il Dockerfile agisce come una sorta di script di build per l'applicazione. Se un Dockerfile viene rilevato nel repository, l'applicazione viene integrata automaticamente in un'immagine prima che venga distribuita in un contenitore. Se la stessa applicazione deve essere creata prima di essere integrata in un'immagine, includi uno script di build per l'applicazione e un Dockerfile.

Per ulteriori informazioni sulla creazione dei Dockerfile, consulta la [documentazione di Docker ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://docs.docker.com/reference/builder/){:new_window}. Per seguire delle istruzioni dettagliate con un modello toolchain per eseguire la distribuzione a Kubernetes, consulta l'[Esercitazione: Use the "Develop a Kubernetes app" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window} oppure l'[Esercitazione: Use the "Develop a Kubernetes app with Helm" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window}.

Per informazioni sulla portabilità della tua applicazione Cloud Foundry a un cluster Kubernetes, consulta l'[Esercitazione: Port a Cloud Foundry app to deploy to Kubernetes in a toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/port-a-cf-app-to-deploy-to-kubernetes-in-a-toolchain?task=0){:new_window}.  

Per creare manualmente un file `pipeline.yml` che sia specifico per i contenitori, vedi gli [esempi in GitHub ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/Puquios/){:new_window}.

### Requisiti dei file manifest (per le applicazioni distribuite a Cloud Foundry)
{: #manifest_files}

Un file `manifest.yml` non è richiesto all'interno del tuo repository. Tuttavia, se la tua applicazione richiede che siano eseguiti degli altri servizi, devi fornire un file manifest che dichiara tali servizi.

Per ulteriori informazioni sui file manifest, consulta [Manifest dell'applicazione](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
