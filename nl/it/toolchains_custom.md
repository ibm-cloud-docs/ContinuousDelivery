---

copyright:
  years: 2017
lastupdated: "2017-7-7"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Creazione di template di toolchain personalizzate
{: #toolchains_custom}

Migliora il tuo flusso di lavoro DevOps creando un template di toolchain personalizzata. Puoi iniziare rapidamente con un template di toolchain esistente oppure creare una toolchain che includa solo le integrazioni che ti servono. Puoi aggiungere o rimuovere le integrazioni della tua toolchain in qualsiasi momento.
{:shortdesc}

Puoi [creare e distribuire una toolchain](/docs/toolchains/toolchains_setup.html){: new_window} in molti modi. Dopo aver creato una toolchain personalizzata, puoi condividerla utilizzando un [pulsante Distribuisci a {{site.data.keyword.Bluemix_notm}}](/docs/develop/deploy_button.html){: new_window}.


## Introduzione
{: #toolchains_custom_gettingstarted}

Per creare un template di toolchain personalizzata, inizia a clonare il template di Toolchain Cloud Foundry semplice. La clonazione di un template esistente ti dà il punto di partenza per la tua toolchain personalizzata.

1. Utilizzando il tuo client Git preferito, immetti il seguente comando per clonare il template [Simple Toolchain](https://github.com/open-toolchain/simple-toolchain){: new_window} in GitHub.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 Questo template distribuisce un'applicazione Hello World di base da un unico repository GitHub e include una toolchain semplice che è preconfigurata per la fornitura continua, il controllo dell'origine, la traccia dei problemi e la modifica in linea.

2. Se preferisci iniziare con un template di toolchain più complessa, puoi iniziare a clonare il template [Cloud-native Toolchain for Microservices](https://github.com/open-toolchain/toolchain-demo){: new_window}.

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

Il template dei microservizi distribuisce un archivio online composto da tre microservizi, ciascuno contenuto nel proprio repository GitHub. Si tratta inoltre di una toolchain più complessa che è preconfigurata per:
* Fornitura continua
* Controllo origine
* Distribuzioni blue-green
* Test funzionale 
* Tracciamento dei problemi 
* Modifica in linea 
* Messaggistica

Indipendentemente dal template che scegli, il processo per personalizzare la toolchain creata è generalmente uguale.

Dopo aver clonato il template, avrai un repository GitHub di base che contiene un file readme e una directory `.bluemix`. La directory contiene tutti i file di configurazioni richiesti dalla toolchain per funzionare. Come minimo, la directory `.bluemix` deve contenere i seguenti file:

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![Fili minimi necessari per definire una toolchain](images/min_files_for_a_toolchain.png)


Ciascuno di questi file viene spiegato nelle seguenti sezioni. Ogni sezione contiene informazioni di configurazione che puoi consultare man mano che la tua toolchain si evolve. 


## Comprensione dei file di configurazione
{: #toolchains_custom_config_files}


I file di configurazione del template di toolchain sono composti principalmente da file in formato YAML. Ogni file contiene dei metadati che descrivono i diversi aspetti della toolchain. I metadati includono
* Informazioni sui repository di toolchain, GitHub o Repository Git e tracciamento del problema.
* Dettagli sulla modalità di creazione e distribuzione del codice.
* Proprietà di configurazione per gli strumenti che sono inclusi nella toolchain. 

Man mano che la tua toolchain diventa più complessa, aumenta anche la complessità dei file di configurazione. 

Alcune linee guida da tenere a mente quando lavori con i file YAML:

* Utilizza solo spazi. Le schede non sono consentite.
* Tutte le proprietà e tutti gli elenchi devono essere rientrati con uno o più spazi.
* Tutte le chiavi e proprietà sono sensibili al maiuscolo/minuscolo.

Presta molta attenzione alla formattazione del file YAML per ridurre la possibilità di riscontrare errori.
Per controllare gli errori, puoi utilizzare un semplice programma di convalida come [questo parser](http://wiki.ess3.net/yaml/){: new_window}.
{: tip}

## Configurazione del file di toolchain
{: #toolchains_custom_toolchain_yml}

Il file `toolchain.yml` è il cuore della tua toolchain. Le specifiche della toolchain, che includono i repository da richiamare, i servizi da includere e i dettagli di build, sono tutte descritte in questo file. Per dare un senso al suo contenuto, può essere suddiviso in diverse sezioni.

1\. **Informazioni introduttive sulla toolchain:**

 Questa sezione del file fornisce semplici dettagli sulla tua toolchain che l'utente può visualizzare sulla pagina di creazione della toolchain. Includi un nome per la toolchain, oltre a una descrizione che ne spiega la funzione. Puoi anche includere un'immagine, come un logo o una rappresentazione visiva della toolchain.

 Oltre a fornire contenuti introduttivi per la tua toolchain, questa sezione include anche una chiave denominata `required` che definisce gli strumenti che fanno parte della toolchain. Il creatore della toolchain configura questi strumenti quando crea la toolchain dal tuo template. Per ogni strumento che è possibile configurare nella pagina di creazione della toolchain, aggiungi la chiave principale dello strumento definita nel file `toolchain.yml` come proprietà della chiave `required`.

 Il seguente frammento mostra un esempio di questa sezione:

 ```
 ---
template
  name: "Toolchain semplice"
  description: "Questa applicazione Hello World utilizza Node.js e include una toolchain che è preconfigurata per la fornitura continua, il controllo dell'origine, la traccia dei problemi e la modifica in linea.\n\nPer iniziare, fai clic su **Crea**."
  header: '![](toolchain.svg)'
  icon: icon.svg
  required:
   - sample-build
   - sample-repo
  info:
    git url: >-
      [https://github.com/my-toolchain/simple-toolchain](https://github.com/open-toolchain/simple-toolchain)
    git branch: >-
      [master](https://github.com/my-toolchain/simple-toolchain/tree/master)
  ```
 {: codeblock}

In questo esempio, l'URL Git e il ramo Git sono relativi a un nuovo template di toolchain.

2\. **Definizioni del repository GitHub:**

 Una toolchain può offrire la fornitura continua per un numero qualsiasi di repository GitHub. Questa sezione del file `toolchain.yml` è dove viene definito ciascun repository.

 Per ogni repository GitHub e Repository Git e tracciamento del problema che viene aggiunto alla toolchain, aggiungi una chiave principale che rappresenti il nome del tuo repository GitHub con le seguenti proprietà:

| Elemento | Chiave/Proprietà | Valore | Descrizione|
|------|--------------|-------|-------------|
| repo-name | chiave |  | Nome del repository. Questa chiave corrisponde al nome (sample-repo) |
| service_id | proprietà | <`githubpublic` , `githubprivate`> | Tipo di repository GitHub |
| parameters: | chiave |  |  |
| repo_name | proprietà |  | Modello per repo-name. L'esempio che segue utilizza il nome toolchain come nome di repository |
| repo_url | proprietà |  | URL del repository GitHub |
| type | proprietà | <`new` , `fork` , `clone` , `link`> | Come viene creato il repository |
| has_issues | proprietà | <`true` , `false`> | Utilizza GitHub Issues |
| enable_traceability | proprietà |  <`true` , `false`> | Determina se tracciare la distribuzione delle modifiche del codice creando tag, etichette e commenti sui commit, richieste di importazione e problemi segnalati.|

 **Nota:** se definisci più repository e li configuri come `has_issues: true`, alla toolchain verrà aggiunta una singola istanza del programma di traccia dei problemi GitHub. Il programma di traccia segue i problemi relativi a tutti i repository impostati su `true`.

 Il seguente frammento mostra un esempio di questa sezione:

 ```
 # Github repos
 services:
  sample-repo:
    service_id: githubpublic
    parameters:
      repo_name: '{{toolchain.name}}'
      repo_url: 'https://github.com/open-toolchain/node-hello-world'
      type: clone
      has_issues: true
      enable_traceability: true
 ```
 {: codeblock}

3\. **Informazioni sulla pipeline:**

 Puoi fornire il tuo progetto in modo continuo utilizzando una pipeline. Questa sezione del file definisce i dettagli di configurazione utilizzati per creare e distribuire il codice in ciascuno dei tuoi repository GitHub e Repository Git e tracciamento del problema.

 Per iniziare, per ogni repository definito nella tua toolchain, aggiungi una chiave principale che rappresenti un nome della sua pipeline. Potresti derivare questa chiave dal nome del tuo repository GitHub o Repository Git e tracciamento del problema. Aggiungi le seguenti proprietà:

| Elemento | Chiave/Proprietà | Valore | Descrizione|
|------|--------------|-------|-------------|
| pipeline-name | chiave |  | Nome per la pipeline (sample-build) |
| service_id | proprietà | <`pipeline`> | Nome del servizio da utilizzare |
| parameters | chiave |  |  |
| name | proprietà | <`repo_name`> | Stesso nome definito nella sezione repos |
| ui-pipeline | proprietà | <`true` , `false`> |  |
| configuration | chiave |  |  |
| content | proprietà | <`$ref(pipeline.yml)`> | File che definisce la definizione della tua pipeline |
| env | chiave |  |  |
| SAMPLE_REPO | chiave | <`repo-name-key`> | Stesso nome della chiave principale del tuo repository |
| CF_APP_NAME |  proprietà | <`'{{form.pipeline.parameters.prod-app-name}}'`> | Nome utilizzato da Cloud Foundry. Potresti incorporare il nome della chiave principale del tuo repository GitHub in questa proprietà. |
| PROD_SPACE_NAME | proprietà | <`'{{form.pipeline.parameters.prod-space}}'`> | Nome dello spazio {{site.data.keyword.Bluemix_notm}} in cui distribuire |
| PROD_ORG_NAME | proprietà | <`'{{form.pipeline.parameters.prod-organization}}'`> | Nome dell'organizzazione {{site.data.keyword.Bluemix_notm}} in cui distribuire |
| PROD_REGION_ID | proprietà | <`'{{form.pipeline.parameters.prod-region}}'`> | Nome della regione {{site.data.keyword.Bluemix_notm}} in cui distribuire |
| execute | proprietà | <`true` , `false`> | Avvia la pipeline dopo la creazione |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 Informazioni sulla creazione di un file `pipeline.yml` sono disponibili in una [sezione successiva.](#toolchains_custom_pipeline_yml)

 Il seguente frammento mostra un esempio di questa sezione del file:

 ```YAML
 # Pipelines
  sample-build:
    service_id: pipeline
    parameters:
      services:
        - sample-repo
      name: '{{services.sample-repo.parameters.repo_name}}'
      ui-pipeline: true
      configuration:
        content:
          $ref: pipeline.yml
        env:
          SAMPLE_REPO: sample-repo
          CF_APP_NAME: '{{form.pipeline.parameters.prod-app-name}}'
          PROD_SPACE_NAME: '{{form.pipeline.parameters.prod-space}}'
          PROD_ORG_NAME: '{{form.pipeline.parameters.prod-organization}}'
          PROD_REGION_ID: '{{form.pipeline.parameters.prod-region}}'
       execute: true 
```
 {: codeblock}

4\. **Dettagli di distribuzione:** - da verificare


 Come parte del processo di fornitura continua, puoi configurare una toolchain per distribuire un'applicazione a qualsiasi regione, organizzazione o spazio {{site.data.keyword.Bluemix_notm}} a cui un utente ha accesso. I dettagli specifici di dove distribuire la tua applicazione possono essere selezionati dalla pagina di creazione della toolchain. 

 ![Impostazioni di configurazione di Delivery Pipeline](images/deploy_configuration.png)

 Questa sezione del file 'toolchain.yml' definisce le fasi della pipeline disponibili e configurabili dalla pagina di creazione della toolchain.

 Per iniziare, la chiave principale 'deploy' è utilizzata per identificare le proprietà di configurazione della distribuzione. Le seguenti proprietà compongono il resto della sezione:

| Elemento | Chiave/Proprietà | Valore | Descrizione |
|------|--------------|-------|-------------|
| deploy | chiave |  | Nome della sezione di distribuzione
| schema | proprietà | <`deploy.json`> | File che definisce il layout dell'IU per configurare i tuoi dettagli di distribuzione |
| service-category | proprietà | <`pipeline`> | Servizio che utilizza le configurazioni di distribuzione |
| parameters | chiave |  |  |
| prod-region | proprietà | <`"{{region}}"`> | Definisce la regione {{site.data.keyword.Bluemix_notm}} per la fase di produzione |
| prod-organization | proprietà | <`"{{organization}}"`> | Definisce l'organizzazione {{site.data.keyword.Bluemix_notm}} per la fase di produzione |
| prod-space | proprietà | <`prod`> | Definisce lo spazio {{site.data.keyword.Bluemix_notm}} per la fase di produzione |
| github-repo-name | proprietà | <`"{{repo-name-key.parameters.repo_name}}"`> | Variabile per passare il nome del repository GitHub alla pagina di creazione della toolchain |

Per ulteriori informazioni sulla creazione di un file 'deploy.json' file, vedi [questa sezione] (#toolchains_custom_deploy_json).

 Il seguente esempio definisce una singola fase che esegue la distribuzione in un ambiente di produzione.

 ```
 ## Configurazione di una fase di distribuzione
 deploy:
   schema: deploy.json
   service-category: pipeline
   parameters:
 	prod-region: "{{region}}"
 	prod-organization: "{{organization}}"
 	prod-space: prod
 	hello-world-name: "{{hello-world-repo.parameters.repo_name}}"
 ```
 {: codeblock}

 L'esempio di codice può essere usato per lo più così com'è e richiede solo una piccola modifica. Per personalizzare questa sezione, imposta `github-repo-name` in modo che sia coerente con il nome del tuo repository. Dovranno essere aggiornati anche i dettagli nel file [`deploy.json`](#toolchains_custom_deploy_json).

 Per creare una pipeline più complessa che includa le fasi di sviluppo, QA e produzione, è possibile sostituire le seguenti proprietà sotto la chiave 'parameters'.

 ```
   parameters:
 	dev-region: "{{region}}"
 	qa-region: "{{region}}"
 	prod-region: "{{region}}"
 	dev-organization: "{{organization}}"
 	qa-organization: "{{organization}}"
 	prod-organization: "{{organization}}"
 	dev-space: dev
 	qa-space: qa
 	prod-space: prod
 ```
 {: codeblock}

 ## Configurazione di una pipeline
 {: #toolchains_custom_pipeline_yml}

 Il file `pipeline.yml` contiene tutti i dettagli di configurazione relativi alle fasi della tua pipeline. Puoi iniziare con un file pipeline.yml e personalizzarlo in base alle tue necessità.

 Se la tua toolchain contiene più di una pipeline, fornisci nomi univoci per ciascun file 'pipeline.yml'.

 Di seguito è riportato un esempio di file 'pipeline.yml':

 ```
 ---
stages:
- name: BUILD
  inputs:
  - type: git
    branch: master
    service: ${SAMPLE_REPO}
  triggers:
  - type: commit
  jobs:
  - name: Build
    type: builder
- name: DEPLOY
  inputs:
  - type: job
    stage: BUILD
    job: Build
  triggers:
  - type: stage
  properties:
  - name: CF_APP_NAME
    value: undefined
    type: text
  - name: APP_URL
    value: undefined
    type: text
  jobs:
  - name: Blue-Green Deploy
    type: deployer
    target:
      region_id: ${PROD_REGION_ID}
      organization: ${PROD_ORG_NAME}
      space: ${PROD_SPACE_NAME}
      application: ${CF_APP_NAME}
    script: |
      #!/bin/bash
      # Push app
      if ! cf app $CF_APP; then  
        cf push $CF_APP
      else
        OLD_CF_APP=${CF_APP}-OLD-$(date +"%s")
        rollback() {
          set +e  
          if cf app $OLD_CF_APP; then
            cf logs $CF_APP --recent
            cf delete $CF_APP -f
            cf rename $OLD_CF_APP $CF_APP
          fi
          exit 1
        }
        set -e
        trap rollback ERR
        cf rename $CF_APP $OLD_CF_APP
        cf push $CF_APP
        cf delete $OLD_CF_APP -f
      fi
      # Export app name and URL for use in later Pipeline jobs
      export CF_APP_NAME="$CF_APP"
      export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
      # View logs
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## Configurazione dell'interfaccia della pipeline
 {: #toolchains_custom_deploy_json}

 Nella pagina di creazione della toolchain, quando si seleziona Delivery Pipeline nella sezione Integrazioni configurabili, la sezione si espande per visualizzare i seguenti elementi:

 	* Il nome dell'applicazione
 	* La regione, l'organizzazione e lo spazio a cui distribuiscono le fasi della pipeline.

Puoi configurare questi elementi per ogni strumento.

 ![Impostazioni di configurazione di Delivery Pipeline](images/deploy_configuration.png)

 Il layout di questa sezione nell'IU è definito dallo schema 'deploy.json'.

 All'interno dello schema, è necessario aggiornare le seguenti proprietà affinché corrispondano ai dettagli della tua applicazione:

 	* Titolo
 	* Descrizione
 	* Descrizione completa
 	* Tutte le istanze di `hello-world-name` e i dettagli associati devono essere modificati in modo che corrispondano a quelli della tua applicazione.

 Il seguente frammento è un esempio di file 'deploy.json':

 ```
 {
    "$schema": "http://json-schema.org/draft-04/schema#",
    "messages": {
        "$i18n": "locales.yml"
    },
    "title": {
        "$ref": "#/messages/deploy.title"
    },
    "description": {
        "$ref": "#/messages/deploy.description"
    },
    "longDescription": {
        "$ref": "#/messages/deploy.longDescription"
    },
    "type": "object",
    "properties": {
        "prod-region": {
            "description": "The bluemix region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The bluemix org",
            "type": "string"
        },
       "prod-space": {
            "description": "The bluemix space",
            "type": "string"
        },
        "prod-app-name": {
            "description": {
                "$ref": "#/messages/deploy.appDescription"
            },
            "type": "string",
            "pattern": "\\S"
        }
    },
    "required": [
        "prod-region",
        "prod-organization",
        "prod-space",
        "prod-app-name"
    ],
    "form": [
        {
            "type": "validator",
          "url": "/devops/setup/bm-helper/helper.html"
        },
        {
            "type": "text",
            "readonly": false,
            "title": {
                "$ref": "#/messages/deploy.appName"
            },
            "key": "prod-app-name"
        },
        {
            "type": "table",
            "columnCount": 4,
            "widths": [
                "15%",
                "28%",
                "28%",
                "28%"
            ],
            "items": [
                {
                    "type": "label",
                  "title": ""
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/region"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/organization"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/space"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/prodStage"
                    }
                },
                {
                    "type": "select",
                  "key": "prod-region"
                },
                {
                    "type": "select",
                  "key": "prod-organization"
                },
                {
                    "type": "select",
                  "key": "prod-space",
                  "readonly": false
                }
            ]
        }
    ]
}
 ```
 {: codeblock}


## Configurazioni di altri strumenti

 Dopo aver configurato i componenti principali della tua toolchain, puoi includere altre integrazioni dello strumento che aggiungono ulteriori funzioni alla tua toolchain. Tutti gli strumenti aggiuntivi richiedono la propria voce nel file 'toolchain.yml'. Alcuni strumenti richiedono anche di aggiungere un file di configurazione YALM separato nella directory '.bluemix'.

 ![File necessari per definire una toolchain](images/files_for_toolchain_with_additional_tools.png)

Per vedere l'elenco di integrazioni dello strumento disponibili, consulta <a ref="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">Servizi disponibili in un template di toolchain</a>. I seguenti esempi mostrano come formattare le aggiunte a un file YAML della toolchain.

 * **Slack**

### toolchain.yml
	```
	messaging:
	  service_id: slack
	  $ref: slack.yml
	```
	{: codeblock}

### slack.yml
	```
	---
	parameters:
	  api_token: ""
	  channel_name: ""
	```
	{: codeblock}

 * **Sauce Labs**

### toolchain.yml
	```
	test:
	  service_id: saucelabs
	  $ref: saucelabs.yml
	```
	{: codeblock}

### saucelabs.yml
	```
	---
	parameters:
	  username: ""
	  key: ""
	```
	{: codeblock}

 * **Eclipse Orion Web IDE**

###	toolchain.yml
	```
	webide:
	  service_id: orion
	```
	{: codeblock}
