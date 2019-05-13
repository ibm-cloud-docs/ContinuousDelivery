---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-12"

keywords: Environment properties, IBM Java, pipeline environments

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Risorse e proprietà dell'ambiente
{: #deliverypipeline_environment}

Le seguenti proprietà e risorse sono disponibili per impostazione predefinita negli ambienti della pipeline.

<!--##Contents
* [Environment properties](#env)
    * [General purpose properties](#gen)
    * [Runtime and tool properties](#runtime)
    * [Deployment properties](#deployment)
* [Pre-installed resources](#resources)
    * [Runtimes and tools](#tools)
    * [Node modules](#node)-->

## Proprietà dell'ambiente
{: #deliverypipeline_envprop}

### Proprietà per scopi generici

| Proprietà ambiente | Descrizione |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| ARCHIVE_DIR | La directory per archiviare o in cui scaricare gli archivi. |
| BUILD_ID | L'ID univoco per l'esecuzione del lavoro corrente.  |
| BUILD_DISPLAY_NAME | Il valore BUILD_ID, con prefisso "#". |
| BUILD_NUMBER | L'ID della fase incrementale visualizzato nella IU della pipeline.  |
| GIT_BRANCH | Il ramo Git che il lavoro utilizza come input. Questa proprietà è disponibile nei lavori che utilizzano un repository Git come input. |
| GIT_COMMIT | Il commit Git che il lavoro utilizza come input. Questa proprietà è disponibile nei lavori che utilizzano un repository Git come input. |
| GIT_PREVIOUS_COMMIT | Il valore di commit Git dell'ultima esecuzione del lavoro con esito positivo. Questa proprietà è disponibile nei lavori che utilizzano un repository Git come input. |
| GIT_URL | L'URL del repository Git che il lavoro utilizza come input. Questa proprietà è disponibile nei lavori che utilizzano un repository Git come input. |
| IDS_JOB_ID | L'ID univoco della configurazione del lavoro. |
| IDS_JOB_NAME | Il nome della configurazione del lavoro. |
| IDS_OUTPUT_PROPS | I nomi separati da virgole delle tue proprietà dell'ambiente della fase. |
| IDS_PROJECT_NAME | Il nome del progetto, ad esempio <code>Owner - Project Name</code>. |
| IDS_STAGE_NAME | Il nome della fase corrente. |
| IDS_URL | L'URL della pipeline corrente. |
| IDS_VERSION | Il numero per la build che sta venendo distribuita o dell'identificativo SCM. Questa proprietà è disponibile solo nei lavori di distribuzione.
| JOB_NAME | L'ID del lavoro univoco nel contesto della pipeline corrente. |
| PIPELINE_ARTIFACT_URL | L'URL che puoi utilizzare per scaricare le risorse del lavoro di build corrente dopo il completamento del lavoro. Devi utilizzare un token Bearer valido per accedere alle risorse. |
| PIPELINE_INITIAL_STAGE_EXECUTION_ID | L'ID univoco per l'esecuzione della pipeline. |
| PIPELINE_KUBERNETES_CLUSTER_NAME | Il nome del cluster Kubernetes selezionato nel lavoro corrente. |
| PIPELINE_LOG_URL | L'URL che puoi utilizzare per scaricare il file di log del lavoro corrente dopo il completamento del lavoro. Devi utilizzare un token Bearer valido per accedere ai file di log. |
| PIPELINE_STAGE_INPUT_JOB_ID | L'ID del lavoro che è l'input della fase corrente. |
| PIPELINE_STAGE_INPUT_REV | La revisione dell'input della fase corrente. |
| PIPELINE_TRIGGERING_USER | L'utente corrente per il lavoro di pipeline|
| TASK_ID | L'ID univoco per l'esecuzione corrente del lavoro. |
| TMPDIR | Un'ubicazione della directory in cui i file temporanei vengono archiviati. |
| WORKSPACE | Il percorso della directory di lavoro corrente. |

### Proprietà di runtime e dello strumento

| Proprietà ambiente | Descrizione |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| ANT_HOME | Il percorso a Apache Ant 1.9.2. |
| ANT_JAVA8_HOME | Il percorso a una versione 1.10+ di Apache Ant che richiede Java 8. |
| GRADLE_HOME | Il percorso a Gradle 1.11. |
| JAVA_HOME | Il percorso a IBM&reg; Java&trade; 7. |
| JAVA7_HOME | Il percorso a IBM Java 7. |
| JAVA8_HOME | Il percorso a IBM Java 8. |
| MAVEN_HOME | Il percorso a Apache Maven 3.2.1. |
| NODE_HOME | Il percorso a Node.js 0.10.29. |

Per utilizzare Apache Ant 1.10+ negli script della tua pipeline, imposta `ANT_HOME` su `$ANT_JAVA8_HOME` e `JAVA_HOME` su `$JAVA8_HOME`.
{: tip}

### Proprietà di distribuzione

| Proprietà ambiente | Descrizione |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| CF_APP | Per le distribuzioni, il nome dell'applicazione da distribuire. Questa proprietà è obbligatoria per la distribuzione e può essere specificata nello script stesso, nell'interfaccia di configurazione del lavoro di distribuzione o nel file `manifest.yml` del progetto. |
| CF_ORG | Per le distribuzioni, il nome dell'organizzazione (org) a cui distribuire. |
| CF_ORGANIZATION_ID | Per le distribuzioni, l'ID dell'organizzazione a cui distribuire. |
| CF_SPACE | Per le distribuzioni, il nome dello spazio a cui distribuire. |
| CF_SPACE_ID | Per le distribuzioni, l'ID dello spazio a cui distribuire.  |
| CF_TARGET_URL | Per le distribuzioni, l'URL di {{site.data.keyword.Bluemix_short}} o Cloud Foundry. |
| IDS_VERSION | Per le distribuzioni, la versione dell'applicazione che sta venendo distribuita o dell'identificativo della risorsa. |

## Risorse preinstallate
{: #deliverypipeline_resources}

Molti runtime, strumenti e moduli Node sono preinstallati in ogni pipeline.

### Runtime e strumenti

Tutti i link sono alla directory home.
{: tip}

| Risorsa | Nome link | Percorso |
|----------|-----------|-----------|
|Apache Ant 1.9.2|ant |/opt/IBM/ant |
|CLI Cloud Foundry 6.14 |cf | /opt/IBM/cf |
|Gradle 1.12|gradle |/opt/IBM/gradle |
|Gradle 2.9 |gradle2 |/opt/IBM/gradle2 |
|CLI IBM Cloud (bx) 0.13.0 |ibmcloud |/usr/local/ibmcloud/bin/ibmcloud |
|IBM Java (predefinito)|java |/opt/IBM/java |
|IBM Java 7 x86_64-71 |java7 |/opt/IBM/java7 |
|IBM Java 8 x86_64-80|java8 |/opt/IBM/java8 |
|Apache Maven 3.2.1 |maven |/opt/IBM/maven |
|IBM Node |node |/opt/IBM/node |
|Strumenti IBM Rational Team Concert&trade; SCM |RTC-SCM-Tools |/opt/IBM/RTC-SCM-Tools |

L'ambiente pipeline offre versioni a 64 bit di IBM Node 0.10, 0.10.48, 0.12, 0.12.17, 4.2, 4.4.5, 4.6.0, 6.2.2 e 6.7.0. Per scegliere una versione, utilizza il comando export.

Ad esempio, per utilizzare Node 0.12.7, digita questo comando: `export PATH=/opt/IBM/node-v0.12/bin:$PATH`

Per utilizzare Node 4.2.2, digita questo comando: `export PATH=/opt/IBM/node-v4.2/bin:$PATH`

### Moduli Node

I seguenti moduli Node sono globalmente installati nell'ambiente della pipeline:

* grunt@0.4.5
* grunt-cli@0.1.13
* grunt-contrib-concat@0.4.0
* grunt-contrib-jshint@0.10.0
* grunt-contrib-nodeunit@0.4.1
* grunt-contrib-qunit@0.5.1
* grunt-contrib-uglify@0.5.0
* grunt-contrib-watch@0.6.1
* karma@0.12.23
* karma-cli@0.0.4
* karma-jasmine@0.1.5
* karma-phantomjs-launcher@0.1.4
* phantomjs@1.9.10
