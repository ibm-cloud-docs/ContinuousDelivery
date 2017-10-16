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


# Angepasste Toolchain-Vorlagen erstellen
{: #toolchains_custom}

Verbessern Sie Ihren DevOps-Workflow durch das Erstellen einer angepassten Toolchain-Vorlage. Sie können Zeit sparen, indem Sie mit einer vorhandenen Toolchain-Vorlage beginnen, oder Sie können eine Toolchain erstellen, die nur die benötigten Toolintegrationen enthält. Sie können Toolchain-Integrationen jederzeit hinzufügen oder entfernen.
{:shortdesc}

Sie haben verschiedene Möglichkeiten, [eine Toolchain zu erstellen und bereitzustellen](/docs/toolchains/toolchains_setup.html){: new_window}. Wenn Sie eine angepasste Toolchain erstellt haben, können Sie sie über die [Schaltfläche zum Bereitstellen in {{site.data.keyword.Bluemix_notm}} ](/docs/develop/deploy_button.html){: new_window} für die gemeinsame Nutzung zur Verfügung stellen.


## Einführung
{: #toolchains_custom_gettingstarted}

Um eine angepasste Toolchain-Vorlage zu erstellen, klonen Sie zunächst die einfache Cloud Foundry-Toolchain-Vorlage. Das Klonen einer vorhandenen Vorlage bietet Ihnen einen Ausgangspunkt für Ihre angepasste Toolchain.

1. Verwenden Sie einen Git-Client Ihrer Wahl und geben Sie den folgenden Befehl ein, um die Vorlage für die [einfache Toolchain](https://github.com/open-toolchain/simple-toolchain){: new_window} in GitHub zu klonen.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 Diese Vorlage stellt eine einfache Hello World-Anwendung aus einem einzelnen GitHub-Repository bereit und enthält eine einfache Toolchain, die für Continuous Delivery, Quellcodeverwaltung, Problemverfolgung und Onlinebearbeitung vorkonfiguriert ist.

2. Wenn Sie lieber mit einer komplexeren Toolchain-Vorlage beginnen möchten, können Sie die [cloudnative Toolchain für Microservices](https://github.com/open-toolchain/toolchain-demo){: new_window} klonen. 

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

Die Microservice-Vorlage stellt ein Onlinegeschäft bereit, das aus drei Microservices besteht, die alle in einem eigenen GitHub-Repository enthalten sind. 
Es handelt sich dabei auch um eine komplexere Toolchain, die vorkonfiguriert ist für: 
* Continuous Delivery
* Quellcodeverwaltung
* Blue-Green-Bereitstellungen
* Funktionstests 
* Problemverfolgung 
* Onlinebearbeitung 
* Messaging

Unabhängig von der ausgewählten Vorlage ist der Prozess zum Anpassen der von Ihnen erstellten Toolchain im Allgemeinen derselbe.

Wenn Sie die Vorlage geklont haben, verfügen Sie über ein einfaches GitHub-Repository mit einer Readme-Datei und einem Verzeichnis `.bluemix`. Das Verzeichnis enthält alle Konfigurationsdateien, die für das Funktionieren der Toolchain erforderlich sind. 
Das Verzeichnis `.bluemix` muss mindestens folgende Dateien enthalten: 

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![Dateien, die mindestens zum Definieren einer Toolchain erforderlich sind](images/min_files_for_a_toolchain.png)


Alle diese Dateien werden in den folgenden Abschnitten erläutert. Jeder Abschnitt enthält die Konfigurationsinformationen, die Sie bei der Weiterentwicklung Ihrer Toolchain als Referenz verwenden können. 


## Erklärung der Konfigurationsdateien
{: #toolchains_custom_config_files}


Die Toolchain-Vorlagenkonfigurationsdateien bestehen primär aus YAML-formatierten Dateien. Jede Datei enthält Metadaten, die verschiedene Aspekte der Toolchain beschreiben. Die Metadaten umfassen Folgendes:
* Informationen über Toolchain-, GitHub- oder Git Repo and Issue Tracking-Repositorys
* Details dazu, wie der Code erstellt und bereitgestellt wird
* Konfigurationseigenschaften für die Tools, die in der Toolchain enthalten sind 

Wenn Ihre Toolchain komplexer wird, nehmen möglicherweise auch Ihre Konfigurationsdateien an Komplexität zu.  

Richtlinien für das Arbeiten mit YAML-Dateien:

* Verwenden Sie nur Leerzeichen. Tabulatoren sind nicht zulässig.
* Alle Eigenschaften und Listen müssen mit ein oder mehr Leerzeichen eingerückt sein.
* Bei allen Schlüsseln und Eigenschaften muss die Groß-/Kleinschreibung beachtet werden.

Achten Sie genau auf die Formatierung der YAML-Datei, um das Fehlerrisiko zu verringern.
Für die Fehlerprüfung können Sie zum Beispiel ein einfaches Prüfprogramm wie [diesen Parser](http://wiki.ess3.net/yaml/){: new_window} verwenden.
{: tip}

## Toolchain-Datei konfigurieren
{: #toolchains_custom_toolchain_yml}

Die Datei `toolchain.yml` ist der zentrale Bestandteil Ihrer Toolchain. Die Besonderheiten Ihrer Toolchain, wie z. B. die einzubeziehenden Repositorys und Services sowie Builddetails, sind alle in dieser Datei definiert. Der Inhalt der Datei ist in mehrere Sinnabschnitte gegliedert. 

1\. **Einführende Toolchain-Informationen:**

 Dieser Dateiabschnitt enthält einfache Details zu Ihrer Toolchain, die für den Benutzer auf der Seite zum Erstellen von Toolchains angezeigt werden. Geben Sie einen Namen für Ihre Toolchain sowie eine Beschreibung ein, die den Zweck der Toolchain erläutert. Sie können auch ein Bild (wie z. B. ein Logo oder eine grafische Darstellung der Toolchain) einfügen.

 Zusätzlich zu den einführenden Informationen zu Ihrer Toolchain enthält dieser Abschnitt einen Schlüssel `required`, der die Tools definiert, die Teil der Toolchain sind. Der Ersteller der Toolchain konfiguriert diese Tools, wenn er die Toolchain anhand Ihrer Vorlage erstellen. Fügen Sie für jedes Tool, das auf der Seite zum Erstellen von Toolchains konfiguriert werden kann, den übergeordneten Schlüssel des Tools hinzu, der in der Datei `toolchain.yml` als Eigenschaft des Schlüssels `required` definiert ist.

 Dieses Snippet zeigt ein Beispiel für diesen Abschnitt:

 ```
 ---
template
  name: "Einfache Toolchain"
  description: "Diese Hello World-Anwendung verwendet Node.js und enthält eine Toolchain, die für Continuous Delivery, Quellcodeverwaltung, Problemverfolgung und Onlinebearbeitung vorkonfiguriert ist.\n\nKlicken Sie auf **Erstellen**."
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

In diesem Beispiel werden die Git-URL und Git-Verzweigung für eine neue Toolchain-Vorlage verwendet.

2\. **GitHub-Repository-Definitionen:**

 Eine Toolchain ermöglicht Continuous Delivery für eine beliebige Zahl von GitHub-Repositorys. In diesem Abschnitt der Datei `toolchain.yml` werden die einzelnen Repositorys definiert.

 Fügen Sie für jedes GitHub- und Git Repo and Issue Tracking-Repository, das der Toolchain hinzugefügt wird, einen übergeordneten Schlüssel hinzu, der den Namen Ihres GitHub-Repositorys angibt, und zwar mit folgenden Eigenschaften:

| Element | Schlüssel/Eigenschaft | Wert | Beschreibung |
|------|--------------|-------|-------------|
| repo-name | Schlüssel |  | Repository-Name. Dieser Schlüssel stimmt mit dem Namen überein (sample-repo). |
| service_id | Eigenschaft | <`githubpublic` , `githubprivate`> | Typ des GitHub-Repositorys |
| parameters: | Schlüssel |  |  |
| repo_name | Eigenschaft |  | Muster für repo-name. Im folgenden Beispiel wird der Toolchain-Name als Repository-Name verwendet. |
| repo_url | Eigenschaft |  | URL des GitHub-Repositorys. |
| type | Eigenschaft | <`new` , `fork` , `clone` , `link`> | Art der Erstellung des Repositorys |
| has_issues | Eigenschaft | <`true` , `false`> | Verwendung von GitHub Issues |
| enable_traceability | Eigenschaften |  <`true` , `false`> | Bestimmt, ob die Bereitstellung von Codeänderungen bei Commits durch Erstellen von Tags und Kommentaren und bei Problemen, die über die Commits referenziert werden, mit Bezeichnungen und Kommentaren verfolgt werden sollen.|

 **Hinweis:** Wenn Sie mehrere Repositorys definieren und sie mit `has_issues: true` konfigurieren, wird eine einzelne Instanz des GitHub Issue-Trackers zur Toolchain hinzugefügt. Der Tracker verfolgt Probleme für alle Repositorys, die auf `true` gesetzt wurden.

 Dieses Snippet zeigt ein Beispiel für diesen Abschnitt:

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

3\. **Pipeline-Informationen:**

 Sie können Ihr Projekt mit einer Pipeline fortlaufend bereitstellen (Continuous Delivery). In diesem Dateiabschnitt werden die Konfigurationsdetails definiert, die für die Erstellung und Bereitstellung des Codes in den einzelnen GitHub- und Git Repo and Issue Tracking-Repositorys verwendet werden.

 Fügen Sie zunächst für jedes in Ihrer Toolchain definierte Repository einen übergeordneten Schlüssel hinzu, der einen Namen der zugehörigen Pipeline angibt. Es empfiehlt sich möglicherweise, diesen Schlüssel vom Namen des GitHub- oder Git Repo and Issue Tracking-Repositorys abzuleiten. Fügen Sie die folgenden Eigenschaften hinzu: 

| Element | Schlüssel/Eigenschaft | Wert | Beschreibung |
|------|--------------|-------|-------------|
| pipeline-name | Schlüssel |  | Name für die Pipeline (sample-build) |
| service_id | Eigenschaft | <`pipeline`> | Name des zu verwendenden Service |
| parameters | Schlüssel |  |  |
| name | Eigenschaft | <`repo_name`> | Entspricht dem im Abschnitt 'repos' definierten Namen |
| ui-pipeline | Eigenschaft | <`true` , `false`> |  |
| configuration | Schlüssel |  |  |
| content | Eigenschaft | <`$ref(pipeline.yml)`> | Datei, die Ihre Pipelinedefinition definiert |
| env | Schlüssel |  |  |
| SAMPLE_REPO | Schlüssel | <`repo-name-key`> | Derselbe Name wie beim übergeordneten Repository-Schlüssel |
| CF_APP_NAME |  Eigenschaft | <`'{{form.pipeline.parameters.prod-app-name}}'`> | Name, der von Cloud Foundry verwendet wird. Sie können den Namen des übergeordneten Schlüssels des GitHub-Repositorys in diese Eigenschaft aufnehmen. |
| PROD_SPACE_NAME | Eigenschaft | <`'{{form.pipeline.parameters.prod-space}}'`> | Name des {{site.data.keyword.Bluemix_notm}}-Bereichs für die Bereitstellung |
| PROD_ORG_NAME | Eigenschaft | <`'{{form.pipeline.parameters.prod-organization}}'`> | Name der {{site.data.keyword.Bluemix_notm}}-Organisation für die Bereitstellung |
| PROD_REGION_ID | Eigenschaft | <`'{{form.pipeline.parameters.prod-region}}'`> | Name der {{site.data.keyword.Bluemix_notm}}-Region für die Bereitstellung |
| execute | Eigenschaft | <`true` , `false`> | Starten der Pipeline nach der Erstellung |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 Informationen zum Erstellen einer Datei `pipeline.yml` sind in einem [späteren Abschnitt](#toolchains_custom_pipeline_yml) enthalten.

 Dieses Snippet zeigt ein Beispiel für diesen Dateiabschnitt:

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

4\. **Bereitstellungsdetails:** - Prüfung erforderlich


 Im Rahmen des Continuous Delivery-Prozesses können Sie eine Toolchain konfigurieren, um eine Anwendung für jede Region, jede Organisation und jeden Bereich unter {{site.data.keyword.Bluemix_notm}} bereitzustellen, auf die ein Benutzer zugreifen kann. Die spezifischen Details dazu, wo Ihre Anwendung bereitgestellt werden soll, können auf der Seite zum Erstellen der Toolchain ausgewählt werden.

 ![Delivery Pipeline-Konfigurationseinstellungen](images/deploy_configuration.png)

 Dieser Abschnitt der Datei `toolchain.yml` definiert die Pipeline-Stages, die auf der Seite zum Erstellen von Toolchains für die Konfiguration zur Verfügung stehen.

 Am Anfang wird der übergeordnete Schlüssel `deploy` verwendet, um die Eigenschaften für die Bereitstellungskonfiguration anzugeben. Die folgenden Eigenschaften bilden den Rest des Abschnitts:

| Element | Schlüssel/Eigenschaft | Wert | Beschreibung |
|------|--------------|-------|-------------|
| deploy | Schlüssel |  | Name des Bereitstellungsabschnitts |
| schema | Eigenschaft | <`deploy.json`> | Datei, die das Layout der UI zur Konfiguration Ihrer Bereitstellungsdetails definiert |
| service-category | Eigenschaft | <`pipeline`> | Service, der die Bereitstellungskonfigurationen verwendet |
| parameters | Schlüssel |  |  |
| prod-region | Eigenschaft | <`"{{region}}"`> | Definiert die {{site.data.keyword.Bluemix_notm}}-Region für die Produktionsstage |
| prod-organization | Eigenschaft | <`"{{organization}}"`> | Definiert die {{site.data.keyword.Bluemix_notm}}-Organisation für die Produktionsstage |
| prod-space | Eigenschaft | <`prod`> | Definiert den {{site.data.keyword.Bluemix_notm}}-Bereich für die Produktionsstage |
| github-repo-name | Eigenschaft | <`"{{repo-name-key.parameters.repo_name}}"`> | Variable zum Übergeben des GitHub-Repository-Namens an die Seite zur Toolchain-Erstellung |

Weitere Informationen zum Erstellen einer Datei `deploy.json` finden Sie in [diesem Abschnitt] (#toolchains_custom_deploy_json).

 Das folgende Beispiel definiert eine einzelne Stage, die die Bereitstellung in eine Produktionsumgebung vornimmt.

 ```
 ## Bereitstellungsstage konfigurieren
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

 Das Codebeispiel kann mit geringem Änderungsaufwand verwendet werden. Um diesen Abschnitt anzupassen, geben Sie für `github-repo-name` den Namen Ihres Repositorys an. Auch in der Datei [`deploy.json`](#toolchains_custom_deploy_json) sind einzelne Änderungen erforderlich.

 Um eine komplexere Pipeline mit dev-, qa- und prod-Stages zu erstellen, können die folgenden Eigenschaften unter dem Schlüssel `parameters` ersetzt werden.

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

 ## Pipeline konfigurieren
 {: #toolchains_custom_pipeline_yml}

 Die Datei `pipeline.yml` enthält alle Konfigurationsdetails für die Stages Ihrer Pipeline. Sie können mit einer vorhandenen Datei pipeline.yml beginnen und sie an Ihre Anforderungen anpassen.

 Wenn Ihre Toolchain mehrere Pipelines enthält, geben Sie einen eindeutigen Namen für jede Datei `pipeline.yml` an.

 Das folgende Beispiel zeigt eine Datei `pipeline.yml`:

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


 ## Pipelineschnittstelle konfigurieren
 {: #toolchains_custom_deploy_json}

 Wenn auf der Seite zum Erstellen der Toolchain die Delivery Pipeline im Abschnitt konfigurierbarer Integrationen ausgewählt wird, wird der Abschnitt erweitert, um folgende Elemente anzuzeigen:

 	* Der Anwendungsname
 	* Die Region, die Organisation und der Bereich, in denen die Pipeline-Stages die Bereitstellung vornehmen.

Sie können diese Elemente für jedes Tool konfigurieren.

 ![Delivery Pipeline-Konfigurationseinstellungen](images/deploy_configuration.png)

 Das Layout dieses Abschnitts in der Benutzerschnittstelle wird durch das Schema `deploy.json` definiert.

 Im Schema müssen die folgenden Eigenschaften aktualisiert werden, damit sie den Details Ihrer Anwendung entsprechen:

 	* Titel (title)
 	* Beschreibung (description)
 	* Lange Beschreibung (longDescription)
 	* Alle Instanzen von `hello-world-name` und die zugehörigen Details müssen geändert werden, damit sie denen Ihrer Anwendung entsprechen.

 Das folgende Snippet zeigt ein Beispiel für die Datei `deploy.json`:

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
            "description": "Bluemix-Region",
            "type": "string"
        },
        "prod-organization": {
            "description": "Bluemix-Organisation",
            "type": "string"
        },
        "prod-space": {
            "description": "Bluemix-Bereich",
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


## Andere Toolkonfigurationen

 Wenn Sie die Kernkomponenten der Toolchain konfiguriert haben, können Sie weitere Toolintegrationen einbeziehen, die zusätzliche Funktionen zu Ihrer Toolchain hinzufügen. Alle zusätzlichen Tools benötigen einen eigenen Eintrag in der Datei `toolchain.yml`. Bestimmte Tools setzen außerdem voraus, dass Sie eine separate YAML-Datei zum Verzeichnis `.bluemix` hinzufügen.

 ![Dateien, die zum Definieren einer Toolchain erforderlich sind](images/files_for_toolchain_with_additional_tools.png)

Eine Liste der verfügbaren Toolintegrationen finden Sie unter <a ref="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">Services, die in einer Toolchain-Vorlage verfügbar sind</a>. Die folgenden Beispiele zeigen, welches Format die Hinzufügungen zu einer Toolchain-YAML-Datei haben müssen.

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

 * **Eclipse Orion-Web-IDE**

###	toolchain.yml
	```
	webide:
	  service_id: orion
	```
	{: codeblock}
