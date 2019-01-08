---

copyright:
  years: 2016, 2018
lastupdated: "2018-11-29"
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


# Présentation de Delivery Pipeline
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} inclut Delivery Pipeline qui vous permet de générer, tester et déployer d'une manière reproductible avec un minimum d'intervention humaine. Dans un pipeline, des séquences d'étapes permettent d'extraire des entrées et d'exécuter des travaux, par exemple, des générations, des tests et des déploiements.
{:shortdesc}

Vos autorisations pour afficher, modifier ou exécuter un pipeline dépendent du contrôle d'accès de la chaîne d'outils propriétaire du pipeline. Pour plus d'informations sur le contrôle d'accès des chaînes d'outils, voir [Gestion de l'accès aux chaînes d'outils dans les groupes de ressources](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window} et [Gestion de l'accès aux chaînes d'outils dans les organisations Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}.
{: important}

Vous pouvez spécifier l'exécution de scripts dans plusieurs types de travaux fournis par le pipeline pour obtenir un contrôle direct de ce qui est exécuté par le travail. Ces scripts s'exécutent dans une image Docker contenant une série d'outils de développement standard, y compris les outils requis pour interagir avec les environnements d'exécution {{site.data.keyword.Bluemix_notm}}. Pour en savoir plus sur ce que contient l'image Docker standard, voir [Ressources préinstallées](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_resources){: new_window}. Si votre travail requiert des outils de développement qui ne sont pas disponibles dans l'image standard ou si vous avez besoin de versions différentes de ces outils, vous pouvez utiliser une image personnalisée. Pour en savoir plus sur les images personnalisées, voir [Utilisation des images Docker personnalisées](/docs/services/ContinuousDelivery/pipeline_custom_docker_images.html#custom_docker_images){: new_window}.

Lorsque le pipeline exécute les scripts, les propriétés qui décrivent le contexte où le travail s'exécute sont transmises au script à l'aide des variables d'environnement. Par exemple, l'URL du référentiel qui est l'entrée de l'étape, le nom de l'étape et le travail qui est exécuté, les paramètres spécifiés par le type de travail, etc. Pour afficher une liste des variables d'environnement disponibles, voir [Ressources préinstallées](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_envprop){: new_window}. 

Vous pouvez définir les propriétés au niveau du pipeline et au niveau de l'étape. Les propriétés d'un pipeline sont partagées entre toutes les étapes et tous les travaux d'un pipeline. Les propriétés d'étape sont spécifiques à une étape particulière et sont partagées entre tous les travaux de cette étape. Pour en savoir plus sur les propriétés, voir [Propriétés d'environnement (variables d'environnement)](/docs/services/ContinuousDelivery/pipeline_about.html#environment_properties).

## Etapes
{: #deliverypipeline_stages}

Les étapes organisent des entrées et des travaux à mesure que votre code est généré, déployé et testé. Les étapes acceptent les entrées des référentiels de contrôle des sources (référentiels SCM) ou des travaux de génération appartenant à d'autres étapes. Pour les référentiels SCM, les entrées sont le contenu d'une branche particulière du référentiel ; pour les travaux de génération, les entrées sont les artefacts produits par le travail. Lorsque vous créez votre première étape, l'onglet **INPUT** contient les paramètres par défaut.

Lorsqu'une étape s'exécute, l'entrée de l'étape est transmise à chaque travail de l'étape. Chaque travail obtient un conteneur propre dans lequel il peut s'exécuter. Par conséquent, les travaux à l'intérieur d'une étape ne peuvent pas se transmettre des artefacts entre eux. Pour transmettre des artefacts d'un travail à un autre, séparez les travaux dans deux étapes et utilisez la sortie du travail de la première étape comme entrée de la seconde étape.
{: tip}

De la même façon que vous pouvez définir les propriétés du pipeline, vous pouvez définir des propriétés d'étapes pour les utiliser dans tous les travaux d'une étape particulière. Par exemple, vous pouvez définir une propriété `TEST_URL` qui transmet une URL aux travaux de déploiement et de test dans une étape. Le travail de déploiement déploie dans cette URL et le travail de test teste l'application active sur l'URL. Les propriétés des étapes sont également transmises aux scripts de travail à l'aide des variables d'environnement. Si la même propriété est définie au niveau du pipeline et au niveau de l'étape, la valeur de la propriété d'étape est utilisée.

Par défaut dans une étape, les générations et les déploiements sont exécutés automatiquement à chaque fois que des changements sont livrés au référentiel SCM d'un projet. Les étapes et les travaux s'exécutent en série ; ils activent le contrôle du débit pour votre travail. Par exemple, vous pouvez placer une étape de test avant une étape de déploiement. Si les tests de l'étape de test échouent, l'étape de déploiement ne s'exécute pas.

Vous souhaiterez peut-être avoir un contrôle plus strict d'une étape spécifique. Si vous ne souhaitez pas qu'une étape s'exécute à chaque fois qu'une modification se produit au niveau de son entrée, vous pouvez désactiver cette fonction. Sur l'onglet **Entrée**, dans la section Déclencheur d'étape, cliquez sur **Exécuter les travaux lorsque cette étape est exécutée manuellement**.

![Onglet Entrée](images/input_tab_only_execute.png)


### Etape de génération
{: #build_stage}

L'étape de génération spécifie un **type de générateur** pour indiquer comment générer les artefacts.  

Plusieurs des zones disponibles dans les travaux de génération sont communes aux différents types de générateurs.
{: tip}

Les types de générateurs suivants sont disponibles :

* **Simple** - Les travaux qui utilisent le type de générateur **simple** prennent l'entrée de l'étape en cours et l'archivent sans la modifier pour qu'elle puisse être utilisée par les étapes futures. Généralement, le type de générateur **simple** est uniquement utile lorsque l'entrée de l'étape provient d'un référentiel SCM.
* **Ant** - Utilisez ce type de générateur pour utiliser des fichiers Apache Ant pour gérer le travail de génération.
  * **Script de génération** - Ce type de générateur peut être n'importe quel script de génération valide. Par défaut, ce type de générateur est défini sur 'ant'.
  * **Répertoire de travail** - Spécifie le répertoire où le script s'exécute.
  * **Répertoire d'archivage de génération** - Spécifie le répertoire qui contient la sortie du travail à archiver pour être utilisé par une étape ultérieure.
  * **Activer le rapport de test** - Sélectionnez cette case pour spécifier que le travail de génération exécute des tests qui produisent des fichiers de résultat au format JUnit XML. Un rapport basé sur les fichiers de résultats est affiché sur l'onglet Tests de la page de résultat de travail. Si un test échoue, le travail est marqué comme ayant échoué. 
  * **Activer le rapport de couverture du code** - Sélectionnez cette case pour afficher plus de zones que vous pouvez utiliser pour le rapport de couverture du code. Vous pouvez spécifier le module d'exécution de couverture (comme Istanbul, JaCoCo ou Cobertura), l'emplacement du fichier de résultat de couverture et le répertoire de résultat de couverture, par rapport au répertoire de travail.
* **Container Registry**
* **Gradle (Artifactory, Nexus ou SonarQube)
**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven (Artifactory, Nexus ou SonarQube)
**
* **npm (Artifactory ou Nexus)
**
* **Script Shell**

### Etape de déploiement
L'étape de déploiement spécifie l'entrée d'une étape de génération.  Les travaux d'une étape de déploiement spécifient un **type de déployeur**.  Les types de déployeurs suivants sont disponibles :

1. **Cloud Foundry**
2. **Kubernetes**

## Travaux
{: #deliverypipeline_jobs}

Un travail est une unité d'exécution au sein d'une étape. Une étape peut contenir plusieurs travaux et les travaux d'une étape s'exécutent de manière séquentielle. Par défaut, si un travail échoue, les travaux suivants dans cette étape ne s'exécutent pas.

![Travaux de génération et de test dans une étape](images/jobs.png)

Les travaux s'exécutent dans des répertoires de travail distincts au sein des conteneurs Docker qui sont créés pour chaque exécution de pipeline. Avant l'exécution d'un travail, son répertoire de travail est renseigné avec des entrées définies au niveau de l'étape. Par exemple, vous pouvez avoir une étape qui contient un travail de test et un travail de déploiement. Si vous installez des dépendances sur un travail, elles ne sont pas disponibles pour l'autre travail. Toutefois, si vous rendez les dépendances disponibles dans l'entrée de l'étape, elles sont disponibles pour les deux travaux.

A l'exception des travaux de génération de type simple, lorsque vous configurez un travail, vous pouvez inclure des scripts shell UNIX qui incluent des commandes de génération, de test ou de déploiement. Les travaux étant exécutés dans des conteneurs ad hoc, les actions sur un travail ne peuvent pas affecter les environnements d'exécution d'autres travaux, même si ces travaux font partie de la même étape.

Des exemples de scripts de génération et de déploiement sont disponibles à l'adresse [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

En outre, les travaux de pipeline peuvent exécuter uniquement les commandes suivantes en tant que `sudo` :
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


Une fois qu'un travail est exécuté, le conteneur qui a été créé pour lui est supprimé. Les résultats de l'exécution d'un travail peuvent être conservés, mais l'environnement dans lequel ce travail a été exécuté n'est pas conservé.

L'exécution des travaux peut prendre jusqu'à 60 minutes. Lorsqu'un travail dépasse cette limite, il échoue. Si un travail dépasse la limite, scindez-le en plusieurs travaux. Par exemple, si un travail effectue trois tâches, vous pouvez le scinder en trois travaux, un pour chaque tâche.
{: tip}

Pour savoir comment ajouter un travail à une étape, voir [Ajout d'un travail à une étape](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}.

### Travaux de génération

Les travaux de génération compilent votre projet dans le cadre de la préparation au déploiement. Ils génèrent des artefacts qui peuvent être envoyés à un répertoire d'archivage de génération, bien que par défaut, les artefacts soient placés dans le répertoire racine du projet.

Les travaux qui utilisent des entrées provenant de travaux de génération doivent faire référence à des artefacts de génération figurant dans la même structure que celle dans laquelle ils ont été créés. Par exemple, si un travail de génération procède à l'archivage d'artefacts de génération dans un répertoire `output`, un script de déploiement doit faire référence au répertoire `output` et non au répertoire cible de projet pour déployer le projet compilé. Vous pouvez spécifier le répertoire d'archivage en indiquant son nom dans la zone **Répertoire d'archivage de génération**. Si
vous laissez la zone vide, l'archivage est effectué dans le répertoire racine.

Si vous utilisez le type de générateur **Simple**, votre code n'est pas compilé ni généré ; il est conditionné et rendu disponible pour des étapes ultérieures.
{: tip}

Lorsque vous effectuez un déploiement à l'aide de la technologie Cloud Foundry, celle-ci inclut les artefacts appropriés permettant à votre application de s'exécuter. Pour plus d'informations, voir [Déploiement d'applications avec la commande cf](/docs/cloud-foundry/deploy-apps.html#dep_apps). Le pipeline pour une application Cloud Foundry contient une étape de déploiement qui exécute une commande cf.

Cloud Foundry tente de [détecter le pack de construction à utiliser![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://docs.cloudfoundry.org/buildpacks/detection.html). Vous pouvez spécifier le [pack de construction](/docs/cfapps/byob.html#using-community-buildpacks) à utiliser dans le fichier manifeste dans le dossier principal de votre application. En général, les packs de construction examinent les artefacts fournis par l'utilisateur afin d'identifier les dépendances à télécharger et de déterminer comment configurer les applications pour qu'elles communiquent avec des services liés. Pour plus d'informations sur les fichiers manifeste, voir [Manifeste d'application](/docs/cloud-foundry/deploy-apps.html#appmanifest).

### Travaux de déploiement

Les travaux de déploiement téléchargent votre projet vers {{site.data.keyword.Bluemix_notm}} en tant qu'application et sont accessibles depuis une URL. Une fois qu'un projet est déployé, l'application déployée apparaît sur votre tableau de bord {{site.data.keyword.Bluemix_notm}}.

Les travaux de déploiement peuvent déployer de nouvelles applications ou mettre à jour des applications existantes. Même si vous déployez une application à l'aide d'une autre méthode, par exemple, l'interface de ligne de commande Cloud Foundry ou la barre d'exécution de l'interface IDE Web, vous pouvez mettre à jour l'application à l'aide d'un travail de déploiement. Pour mettre à jour une application, dans le travail de déploiement, utilisez le nom de cette application.

Vous pouvez effectuer le déploiement dans une ou plusieurs régions et dans un ou plusieurs services. Par exemple, vous pouvez configurer votre {{site.data.keyword.deliverypipeline}} en vue d'utiliser un ou plusieurs services, le tester dans une région, et le déployer en production dans plusieurs régions. Pour plus d'informations, voir
[Régions](/docs/overview/ibm-cloud.html#ov_intro-reg){: new_window}.

### Travaux de test
Si vous voulez exiger que des conditions soient respectées, ajoutez des travaux de test avant ou après vos travaux de génération et de déploiement. Vous pouvez personnaliser des travaux de test pour qu'ils soient simples ou complexes selon vos besoins. Par exemple, vous pouvez exécuter une commande cURL et attendre une réponse spécifique. Vous pouvez également exécuter une suite de tests unitaires ou des tests fonctionnels avec des services de test tiers, tels que Sauce Labs.

Si vos tests génèrent des fichiers de
résultats au format JUnit XML, un rapport qui s'appuie sur les fichiers de résultats apparaît dans l'onglet **Tests** de chaque page de résultat de test. Si un test échoue, le travail échoue également.

## Propriétés d'environnement (variables d'environnement)
{: #environment_properties}

Un ensemble de propriétés d'environnement prédéfinies donne accès à des informations sur l'environnement d'exécution du travail. Pour obtenir une liste complète des propriétés d'environnement prédéfinies, voir [Propriétés et ressources d'environnement](/docs/services/ContinuousDelivery/pipeline_deploy_var.html).

Vous pouvez également définir vos propres propriétés d'environnement. Par exemple, vous pouvez définir une propriété `API_KEY` qui transmet une clé d'API qui est utilisée pour accéder aux ressources {{site.data.keyword.Bluemix_notm}} par tous les scripts du pipeline.

Vous pouvez ajouter les types de propriétés suivants :

* **Texte** : Clé de propriété avec une valeur monoligne.
* **Zone de texte** : Clé de propriété avec une valeur multiligne.
* **Sécurisé** : Clé de propriété avec une valeur monoligne qui est sécurisée avec le chiffrement AES-128. La valeur s'affiche sous forme d'astérisques.
* **Propriétés** : Fichier dans le référentiel du projet. Ce fichier peut contenir plusieurs propriétés. Chaque propriété doit figurer sur sa propre ligne. Pour distinguer des paires clé-valeur, utilisez le signe égal (=). Placez toutes les valeurs de chaîne entre guillemets. Par exemple, `MY_STRING="SOME STRING VALUE"`.

Vous pouvez examiner les propriétés d'environnement pour un travail de pipeline en exécutant la commande `env` dans le script du travail.
{:tip}

### Propriétés du pipeline
Pour définir les propriétés du pipeline, dans le menu déroulant dynamique qui apparaît sur la page Pipeline, sélectionnez **Configurer le pipeline**.

![Menu déroulant dynamique de Pipeline](images/OverflowMenu.png)

Dans l'onglet **Propriétés d'environnement** de la page de configuration de Pipeline, définissez les propriétés d'environnement au niveau du pipeline.

![Page des propriétés de Pipeline](images/PipelineProperties.png)

### Propriétés des étapes
Pour définir les propriétés des étapes, ouvrez la page de configuration d'Etape et cliquez sur l'onglet **Propriétés d'environnement**.

![Page des propriétés d'Etape](images/StageProperties.png)

Vous pouvez également transférer des propriétés d'environnement entre les travaux d'une même étape en exportant les propriétés. Par exemple, vous pouvez inclure la commande suivante pour utiliser la propriété `$API_KEY` dans un autre travail au sein de l'étape : `export API_KEY=<insert API key here>`
{:tip}

### Propriétés calculées
Vous pouvez calculer les valeurs des propriétés d'environnement qui sont partagées entre les étapes en créant un fichier `build.properties` pendant que l'étape s'exécute puis faire en sorte que l'étape suivante exécute le fichier. Par exemple, votre travail de génération peut inclure la commande suivante dans le script de génération :

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

Tous les travaux commencent à exécuter le fichier `build.properties`, s'il existe.

## Création et utilisation d'artefacts
{: #artifacts}

Les travaux de génération extraient automatiquement le contenu du dossier en cours dans lequel le script utilisateur est exécuté. Si vous n'avez pas besoin de tout le contenu du référentiel git pour un déploiement ultérieur, il est préférable de configurer un répertoire de sortie explicite puis de copier ou créer les artefacts pertinents. Les scripts de travail sont exécutés dans le résultat de génération (répertoire de sortie).

Les travaux qui sont déployés sur Cloud Foundry doivent spécifier la clé d'API de plateforme d'un utilisateur sous l'autorité duquel les travaux sont exécutés, ainsi que la région, l'organisation et l'espace où les artefacts doivent être déployés. Si d'autres services sont requis pour exécuter votre application, vous devez les spécifier dans le fichier `manifest.yml`.

Les travaux de déploiement déployés sur {{site.data.keyword.containerlong_notm}} doivent spécifier la clé d'API de plateforme d'un utilisateur sous l'autorité duquel les travaux sont exécutés, un fichier Dockerfile et éventuellement une charte Helm.   

Le script de travail s'exécute après la connexion du travail à l'environnement cible à l'aide de la clé d'API de plateforme qui lui est attribuée (vous pouvez donc exécuter des commandes `cf push` ou `kubectl` dans le script). 

## Exemple de pipeline
{: #deliverypipeline_example}

Un pipeline simple peut contenir trois étapes :

1. Une étape de génération qui compile et exécute des processus de génération sur une application.
2. Une étape de test qui déploie une instance de l'application, puis exécute des tests sur cette instance.
3. Une étape de production qui déploie une instance de production de l'application testée.

Ce pipeline est affiché dans le diagramme conceptuel suivant :

![Diagramme conceptuel des étapes et des travaux dans un pipeline](images/diagram.jpg)

*Modèle conceptuel d'un pipeline composé de trois étapes*

Les étapes prennent leur entrée dans des référentiels et des travaux de génération et les travaux au sein d'une étape s'exécutent de façon séquentielle et indépendamment les uns des autres. Dans l'exemple de pipeline, les étapes s'exécutent de manière séquentielle, même si les étapes de test et de production utilisent la sortie de l'étape de génération comme entrée.

## Fichiers manifeste de Cloud Foundry
{: #deliverypipeline_manifest}

Les fichiers manifeste, qui sont appelés `manifest.yml` et sont stockés dans le répertoire racine d'un projet, contrôlent la façon dont votre projet est déployé dans {{site.data.keyword.Bluemix_notm}}. Pour obtenir des informations sur la création des fichiers manifeste pour un projet, consultez la documentation [{{site.data.keyword.Bluemix_notm}} sur les manifestes d'application](/docs/cloud-foundry/deploy-apps.html#appmanifest). Pour s'intégrer à {{site.data.keyword.Bluemix_notm}}, votre projet doit contenir un fichier manifeste dans son répertoire racine. Toutefois, vous n'êtes pas obligé d'effectuer le déploiement conformément aux informations du fichier.

Dans le pipeline, vous pouvez spécifier tout ce qu'un fichier manifeste peut faire à l'aide des arguments de commande `cf push`. Les arguments de commande `cf push` sont utiles dans les projets qui possèdent plusieurs projets de déploiement. Si plusieurs travaux de déploiement tentent d'utiliser la route spécifiée dans le fichier manifeste du projet, un conflit se produit.

Pour éviter les conflits, vous pouvez spécifier une route en utilisant la commande `cf push` suivie de l'argument de nom d'hôte, `-n` et d'un nom de route. En modifiant le script de déploiement pour des étapes individuelles, vous pouvez éviter des conflits de route lorsque vous procédez au déploiement sur plusieurs cibles.

Pour utiliser les arguments de commande `cf push`, ouvrez les paramètres de configuration pour un travail de déploiement et modifiez la zone **Script de déploiement**. Pour plus d'informations, consultez la [documentation Cloud Foundry Push ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
