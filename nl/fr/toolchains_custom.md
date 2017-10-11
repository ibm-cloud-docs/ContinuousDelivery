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


# Création de modèles de chaîne d'outils personnalisés
{: #toolchains_custom}

Améliorez votre flux de travaux DevOps en créant un modèle de chaîne d'outils personnalisé. Vous pouvez démarrer rapidement avec un modèle de chaîne d'outils existant, ou créer une chaîne d'outils qui inclut uniquement les intégrations dont vous avez besoin. Vous pouvez ajouter ou retirer des intégrations de votre chaîne d'outils à tout moment.
{:shortdesc}

Vous pouvez [créer et déployer une chaîne d'outils](/docs/toolchains/toolchains_setup.html){: new_window} de différentes manières. Après avoir créé une chaîne d'outils personnalisée, vous pouvez la partager en utilisant un bouton [Déployer dans {{site.data.keyword.Bluemix_notm}}](/docs/develop/deploy_button.html){: new_window}.


## Initiation
{: #toolchains_custom_gettingstarted}

Pour créer un modèle de chaîne d'outils personnalisé, commencez par cloner le modèle de chaîne d'outils Cloud Foundry simple. En clonant un modèle existant, vous bénéficiez d'un point de départ pour votre chaîne d'outils personnalisée. 

1. En utilisant le client Git de votre choix, entrez la commande suivante pour cloner le modèle [de chaîne d'outils simple](https://github.com/open-toolchain/simple-toolchain){: new_window} dans GitHub.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 Ce modèle déploie une application Hello World de base à partir d'un référentiel GitHub unique et inclut une chaîne d'outils simple qui est préconfigurée pour la distribution continue, le contrôle des sources, le suivi des problèmes et l'édition en ligne. 

2. Si vous utilisez un modèle de chaîne d'outils plus complexe, vous pouvez commencer par cloner la [chaîne d'outils native pour le cloud pour les microservices](https://github.com/open-toolchain/toolchain-demo){: new_window}.

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

Le modèle de microservices déploie un magasin en ligne composé de trois microservices, chacun d'eux étant contenus dans leur propre référentiel GitHub. Il s'agit également d'une chaîne d'outils plus complexe qui est préconfigurée pour :
* La distribution continue
* Le contrôle des sources
* Les déploiements Blue-Green
* Les tests fonctionnels 
* Le suivi des problèmes 
* L'édition en ligne 
* La messagerie

Quel que soit le modèle que vous choisissez, le processus de personnalisation de la chaîne d'outils que vous créez est généralement le même.

Une fois le modèle cloné, vous obtenez un référentiel GitHub de base qui contient un fichier Readme et un répertoire `.bluemix`. Le répertoire contient tous les fichiers de configuration nécessaires au fonctionnement de la chaîne d'outils. Le répertoire `.bluemix` doit au moins contenir les fichiers suivants :

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![Fichiers minimum requis pour définir une chaîne d'outils](images/min_files_for_a_toolchain.png)


Chacun de ces fichiers est décrit dans les sections ci-dessous. Chaque section contient des informations de configuration que vous pouvez consulter à mesure que votre chaîne d'outils évolue. 


## Présentation des fichiers de configuration
{: #toolchains_custom_config_files}


Les fichiers de configuration de modèle de chaîne d'outils sont principalement composés de fichiers YAML formatés. Chaque fichier contient des métadonnées décrivant différents aspects de la chaîne d'outils. Les métadonnées incluent notamment :
* Des informations sur les référentiels de chaîne d'outils, GitHub ou Git Repo and Issue Tracking
* Des informations détaillées sur la façon dont le code est généré et déployé
* Des propriétés de configuration relatives aux outils compris dans la chaîne d'outils 

Plus votre chaîne d'outils devient complexe, plus la complexité de vos fichiers de configuration est susceptible d'augmenter.  

Voici un guide de bonnes pratiques pour la gestion de vos fichiers YAML :

* Utilisez uniquement des espaces. Les tabulations ne sont pas autorisées.
* Toutes les propriétés et toutes les listes doivent présenter un retrait de ligne d'un ou de plusieurs espaces. 
* Toutes les clés et toutes les propriétés sont sensibles à la casse. 

Prêtez une attention particulière au formatage du fichier YAML afin de réduire les risques d'erreur. Pour rechercher les éventuelles erreurs, vous pouvez utiliser un valideur simple, tel que [cet analyseur syntaxique](http://wiki.ess3.net/yaml/){: new_window}.
{: tip}

## Configuration du fichier de chaîne d'outils
{: #toolchains_custom_toolchain_yml}

Le fichier `toolchain.yml` est au coeur de votre chaîne d'outils. Ce fichier décrit toutes les caractéristiques de votre chaîne d'outils, y compris les référentiels à rechercher, les services à inclure, ainsi que les détails de génération. Afin de rendre son contenu plus compréhensible, vous pouvez fractionner ce fichier en plusieurs sections. 

1\. **Section de présentation de la chaîne d'outils :**

 Cette section du fichier fournit les détails simples relatifs à votre chaîne d'outils que l'utilisateur peut visualiser sur la page de création de la chaîne d'outils. Ajoutez un nom et une description pour votre chaîne d'outils. Vous pouvez également inclure une image, par exemple, un logo ou une représentation visuelle de votre chaîne d'outils. 

 Outre la présentation de votre chaîne d'outils, cette section comprend également une clé nommée `required` qui définit les outils faisant partie de la chaîne d'outils. Le créateur de la chaîne d'outils configure ces outils lorsqu'il la créée à partir de votre modèle. Pour chaque outil configurable sur la page de création de la chaîne d'outils, ajoutez en tant que propriété de la clé `required` la clé parente de l'outil qui est définie dans le fichier `toolchain.yml`. 

 Ce fragment est un exemple qui illustre cette section :

 ```
 ---
template
  name: "Simple Toolchain"
  description: "This Hello World application uses Node.js and includes a toolchain that is preconfigured for continuous delivery, source control, issue tracking, and online editing.\n\nTo get started, click **Create**."
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

Dans cet exemple, l'URL Git et la branche Git s'appliquent à un nouveau modèle de chaîne d'outils. 

2\. **Définitions de référentiel GitHub :**

 Une chaîne d'outils peut fournir une distribution continue pour n'importe quel nombre de référentiels GitHub. Cette section du fichier `toolchain.yml` contient la définition de chaque référentiel. 

 Pour chaque référentiel GitHub et Git Repos and Issue Tracking ajouté à la chaîne d'outils, ajoutez une clé parente qui représente le nom de votre référentiel GitHub avec les propriétés suivantes : 

| Elément | Clé/Propriété | Valeur | Description |
|------|--------------|-------|-------------|
| repo-name | Clé |  | Nom de référentiel. Cette clé correspond au nom (sample-repo) |
| service_id | Propriété | <`githubpublic` , `githubprivate`> | Type de référentiel GitHub |
| parameters: | Clé |  |  |
| repo_name | Propriété |  | Modèle pour repo-name. L'exemple qui suit utilise le nom de la chaîne d'outils comme nom de référentiel |
| repo_url | Propriété |  | URL du référentiel GitHub |
| type | Propriété | <`new` , `fork` , `clone` , `link`> | Façon dont le référentiel est créé |
| has_issues | Propriété | <`true` , `false`> | Utilisation de GitHub Issues |
| enable_traceability | Propriété |  <`true` , `false`> | Indique s'il y a lieu de suivre le déploiement des modifications de code en créant des étiquettes, des libellés et des commentaires sur les validations, les demandes d'extraction et les problèmes référencés |

 **Remarque :** si vous définissez plusieurs référentiels et que vous les configurez comme `has_issues: true`, une instance unique du dispositif de suivi de problèmes GitHub est ajoutée à la chaîne d'outils. Le dispositif de suivi trace les problèmes de tous les référentiels pour lesquels cette propriété a pour valeur `true`.

 Ce fragment est un exemple qui illustre cette section :

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

3\. **Informations sur le pipeline :**

 Vous pouvez fournir en permanence un pipeline à votre projet. Cette section du fichier contient les détails de configuration utilisés pour générer et déployer le code dans chacun des référentiels GitHub et Git Repos and Issue Tracking. 

 Pour commencer, pour chaque référentiel défini dans votre chaîne d'outils, ajoutez une clé parente qui représente un nom de son pipeline. Envisagez de dériver cette clé à partir du nom de votre référentiel GitHub ou Git Repos and Issue Tracking. Ajoutez les propriétés suivantes :

| Elément | Clé/Propriété | Valeur | Description |
|------|--------------|-------|-------------|
| pipeline-name | Clé |  | Nom du pipeline (sample-build) |
| service_id | Propriété | <`pipeline`> | Nom du service à utiliser |
| parameters | Clé |  |  |
| name | Propriété | <`repo_name`> | Identique à la définition dans la section repos |
| ui-pipeline | Propriété | <`true` , `false`> |  |
| configuration | Clé |  |  |
| content | Propriété | <`$ref(pipeline.yml)`> | Fichier contenant votre définition de pipeline |
| env | Clé |  |  |
| SAMPLE_REPO | Clé | <`repo-name-key`> | Nom identique à celui de votre clé parente de référentiel |
| CF_APP_NAME |  Propriété | <`'{{form.pipeline.parameters.prod-app-name}}'`> | Nom utilisé par Cloud Foundry. Envisagez d'incorporer votre nom de clé parente de référentiel GitHub dans cette propriété |
| PROD_SPACE_NAME | Propriété | <`'{{form.pipeline.parameters.prod-space}}'`> | Nom de l'espace {{site.data.keyword.Bluemix_notm}} vers lequel effectuer le déploiement |
| PROD_ORG_NAME | Propriété | <`'{{form.pipeline.parameters.prod-organization}}'`> | Nom de l'organisation {{site.data.keyword.Bluemix_notm}} vers laquelle effectuer le déploiement |
| PROD_REGION_ID | Propriété | <`'{{form.pipeline.parameters.prod-region}}'`> | Nom de la région {{site.data.keyword.Bluemix_notm}} vers laquelle effectuer le déploiement |
| execute | Propriété | <`true` , `false`> | Démarrer le pipeline après sa création |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 Des informations sur la création d'un fichier `pipeline.yml` sont fournies [ultérieurement.](#toolchains_custom_pipeline_yml)

 Ce fragment est un exemple qui illustre cette section du fichier :

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

4\. Informations sur le déploiement :


 Dans le cadre de la distribution continue, vous pouvez configurer une chaîne d'outils afin de déployer une application sur n'importe quels région, organisation et espace {{site.data.keyword.Bluemix_notm}} auxquels un utilisateur peut accéder. Les détails spécifiques relatifs à l'emplacement du déploiement de votre application peuvent être sélectionnés sur la page de création de la chaîne d'outils.
 ![Paramètres de configuration du pipeline de distribution](images/deploy_configuration.png)

 Cette section du fichier toolchain.yml définit les étapes de pipeline configurables sur la page de création de la chaîne d'outils.

 Pour commencer, la clé parente 'deploy' est utilisée pour identifier les propriétés de configuration de déploiement. Les propriétés suivantes constituent le reste de la section :
| Elément | Clé/Propriété | Valeur | Description |
|------|--------------|-------|-------------|
| deploy | Clé |  | Nom de la section de déploiement |
| schema | Propriété | <`deploy.json`> | Fichier dans lequel est définie la présentation de l'interface utilisateur utilisée pour configurer les détails de déploiement |
| service-category | Propriété | <`pipeline`> | Service qui utilise les configurations de déploiement |
| parameters | Clé |  |  |
| prod-region | Propriété | <`"{{region}}"`> | Définit la région {{site.data.keyword.Bluemix_notm}} pour l'étape de production  |
| prod-organization | Propriété | <`"{{organization}}"`> | Définit l'organisation {{site.data.keyword.Bluemix_notm}} pour l'étape de production |
| prod-space | Propriété | <`prod`> | Définit l'espace {{site.data.keyword.Bluemix_notm}} pour l'étape de production |
| github-repo-name | Propriété | <`"{{repo-name-key.parameters.repo_name}}"`> | Variable utilisée pour transmettre le nom de référentiel GitHub à la page de création de la chaîne d'outils |
Pour plus d'informations sur la création d'un fichier deploy.json, voir [cette section] (#toolchains_custom_deploy_json).

 L'exemple suivant illustre la définition d'une seule étape de déploiement dans un environnement de production :

 ```
 ## Configuration d'une étape de déploiement
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

 La plupart du temps, l'exemple de code peut être utilisé tel quel et ne nécessite que très peu de modifications. Pour personnaliser cette section, définissez le nom 'github-repo-name' de telle manière qu'il soit cohérent avec le nom de votre référentiel. Les informations contenues dans le fichier [`deploy.json`](#toolchains_custom_deploy_json) devront également être mises à jour.

 Pour créer un pipeline plus complexe contenant des étapes dev, QA et Prod, vous pouvez utiliser les propriétés suivantes sous la clé 'parameters'.

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

 ## Configuration d'un pipeline
 {: #toolchains_custom_pipeline_yml}

 Le fichier pipeline.yml contient tous les détails de configuration des étapes de votre pipeline. Vous pouvez commencer avec un fichier pipeline.yml existant et le personnaliser en fonction de vos besoins.
 Si votre chaîne d'outils contient plus d'un pipeline, indiquez des noms uniques dans chaque fichier pipeline.yml.

 Exemple de fichier pipeline.yml :

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


 ## Configuration de l'interface de pipeline
 {: #toolchains_custom_deploy_json}

 Sur la page de création de la chaîne d'outils, lorsque vous sélectionnez Delivery Pipeline dans la section Intégrations configurables, celle-ci est détaillée et présente les éléments suivants :
 	* Le nom de l'application
 	* La région, l'organisation et l'espace dans lesquels vos étapes de pipeline effectuent le déploiement

Vous pouvez configurer ces éléments pour chaque outil.

 ![Paramètres de configuration du pipeline de distribution](images/deploy_configuration.png)

 La présentation de cette section dans l'interface utilisateur est définie par le schéma 'deploy.json'.

 Au sein du schéma, les propriétés suivantes doivent être mises à jour afin de correspondre aux détails de votre application :

 	* Title
 	* Description
 	* LongDescription
 	* All instances of `hello-world-name` and associated details should be modified to match that of your application.

 Le fragment suivant illustre un exemple de fichier deploy.json :

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


## Configuration des autres outils

 Après avoir configuré les composants de base de votre chaîne d'outils, vous pouvez inclure d'autres intégrations d'outils qui apportent d'autres fonctions à votre chaîne d'outils. Une entrée spécifique est requise dans le fichier toolchain.yml pour chaque outil supplémentaire. Certains outils nécessitent également que vous ajoutiez un fichier de configuration YAML distinct au répertoire .bluemix.
 ![Fichiers requis pour définir une chaîne d'outils](images/files_for_toolchain_with_additional_tools.png)

Pour connaître la liste des intégrations d'outils disponibles, voir l'article <a ref="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">Services disponibles dans un modèle de chaîne d'outils</a>. Les exemples suivants montrent comment formater les ajouts effectués sur un fichier YAML de chaîne d'outils :

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
