---

copyright:
  years: 2016, 2018
lastupdated: "2018-3-22"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Présentation de Delivery Pipeline
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} inclut Delivery Pipeline qui vous permet de générer, tester et déployer d'une manière reproductible avec un minimum d'intervention humaine. Dans un pipeline, des séquences d'étapes permettent d'extraire des entrées et d'exécuter des travaux, par exemple, des générations, des tests et des déploiements.
{:shortdesc}

Les sections ci-après décrivent les détails des concepts relatifs aux pipelines.

## Etapes
{: #deliverypipeline_stages}

Les étapes organisent des entrées et des travaux à mesure que votre code est généré, déployé et testé. Les étapes acceptent des entrées depuis
les référentiels de contrôle des sources (référentiels SCM) ou les travaux de génération (artefacts de génération) d'autres étapes. Lorsque vous créez votre première étape, les paramètres par défaut sont définis pour vous sur l'onglet **Entrée**.

Une entrée d'étape est transmise aux travaux qu'elle contient et chaque travail se voit attribuer un conteneur vide dans lequel il s'exécute.

**Important** : les travaux d'une étape ne peuvent pas se transmettre des artefacts les uns aux autres. Etant donné que vous ne pouvez pas transmettre des artefacts entre les étapes, vous devez avoir une étape de génération séparée d'une étape de déploiement si votre étape de déploiement utilisera les artefacts de l'étape de génération.

Vous pouvez définir des propriétés d'environnement d'étape qui peuvent être utilisées dans tous les travaux. Par exemple, vous pouvez définir une propriété `TEST_URL` qui transmet une URL unique pour déployer et tester des travaux dans une étape unique. Le travail de déploiement sera déployé sur cette URL et le travail de test testera l'application active au niveau de l'URL.

Par défaut dans une étape, les générations et les déploiements sont exécutés automatiquement à chaque fois que des changements sont livrés au référentiel SCM d'un projet. Les étapes et les travaux s'exécutent en série ; ils activent le contrôle du débit pour votre travail. Par exemple, vous pouvez placer une étape de test avant une étape de déploiement. Si les tests de l'étape de test échouent, l'étape de déploiement ne s'exécutera pas.

Vous souhaiterez peut-être avoir un contrôle plus strict d'une étape spécifique. Si vous ne souhaitez pas qu'une étape s'exécute à chaque fois qu'une modification se produit au niveau de son entrée, vous pouvez désactiver cette fonction. Sur l'onglet **Entrée**, dans la section Déclencheur d'étape, cliquez sur **Exécuter les travaux lorsque cette étape est exécutée manuellement**.

![Onglet Entrée](images/input_tab_only_execute.png)


### Etape de génération
{: #build_stage}

<!-- Need the Pipeline team to fill out what each builder does and possible add an example -->
L'étape de génération spécifie un **type de générateur** pour indiquer comment générer les artefacts. Les types de générateurs suivants sont disponibles :

1. **Simple** - Si vous utilisez le type de générateur **Simple**, votre code n'est pas compilé ni généré. Il est conditionné et mis à disposition pour les étapes futures.
2. **Ant**
3. **Container Registry
**
4. **Gradle**
5. **Gradle (Artifactory, Nexus ou SonarQube)
**
6. **Grunt**
7. **IBM Globalization Pipeline**
8. **Maven**
9. **Maven (Artifactory, Nexus ou SonarQube)
**
10. **npm**
11. **npm (Artifactory ou Nexus)
**
12. **Shell Script**

### Etape de déploiement
L'étape de déploiement spécifie l'entrée d'une étape de génération.  Les travaux d'une étape de déploiement spécifient un **type de déployeur**.  Les types de déployeurs suivants sont disponibles :

1. **Cloud Foundry**
2. **Kubernetes**

## Travaux
{: #deliverypipeline_jobs}

Un travail est une unité d'exécution au sein d'une étape. Une étape peut contenir plusieurs travaux et les travaux d'une étape s'exécutent de manière séquentielle. Par défaut, si un travail échoue, les travaux suivants dans cette étape ne s'exécutent pas.

![Travaux de génération et de test dans une étape](images/jobs.png)

Les travaux s'exécutent dans des répertoires de travail discrets au sein de conteneurs Docker créés pour chaque exécution de pipeline. Avant l'exécution d'un travail, son répertoire de travail est renseigné avec des entrées définies au niveau de l'étape. Par exemple, vous pouvez avoir une étape qui contient un travail de test et un travail de déploiement. Si vous installez des dépendances sur un travail, elles ne sont pas disponibles pour l'autre travail. Toutefois, si vous rendez les dépendances disponibles dans l'entrée de l'étape, elles sont disponibles pour les deux travaux.

A l'exception des travaux de génération de type simple, lorsque vous configurez un travail, vous pouvez inclure des scripts shell UNIX qui incluent des commandes de génération, de test ou de déploiement. Les travaux étant exécutés dans des conteneurs ad hoc, les actions sur un travail ne peuvent pas affecter les environnements d'exécution d'autres travaux, même si ces travaux font partie de la même étape.

Des exemples de scripts de travail et de déploiement sont disponibles à l'adresse [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

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

**Remarque** : l'exécution des travaux peut prendre jusqu'à 60 minutes. Lorsqu'un travail dépasse cette limite, il échoue. Si un travail dépasse la limite, scindez-le en plusieurs travaux. Par exemple, si un travail effectue trois tâches, vous pouvez le scinder en trois travaux, un pour chaque tâche.

Pour savoir comment ajouter un travail à une étape, voir [Ajout d'un travail à une étape](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}.

### Travaux de génération

Les travaux de génération compilent votre projet dans le cadre de la préparation au déploiement. Ils génèrent des artefacts qui peuvent être envoyés à un répertoire d'archivage de génération, bien que par défaut, les artefacts soient placés dans le répertoire racine du projet.

Les travaux qui utilisent des entrées provenant de travaux de génération doivent faire référence à des artefacts de génération figurant dans la même structure que celle dans laquelle ils ont été créés. Par exemple, si un travail de génération procède à l'archivage d'artefacts de génération dans un répertoire `output`, un script de déploiement doit faire référence au répertoire `output` et non au répertoire cible de projet pour déployer le projet compilé. Vous pouvez spécifier le répertoire d'archivage en indiquant son nom dans la zone **Répertoire d'archivage de génération**. Si
vous laissez la zone vide, l'archivage est effectué dans le répertoire racine.

**Remarque :** si vous utilisez le type de générateur **Simple**, votre code n'est pas compilé ni généré ; il est conditionné et rendu disponible pour des étapes ultérieures.

Lorsque vous effectuez un déploiement à l'aide de la technologie Cloud Foundry, celle-ci inclut les artefacts appropriés permettant à votre application de s'exécuter. Pour plus d'informations, voir [Déploiement d'applications avec la commande cf](https://console.ng.bluemix.net/docs/manageapps/depapps.html#dep_apps). Le pipeline pour une application Cloud Foundry contient une étape de déploiement qui exécute une commande cf.

Cloud Foundry tente de [détecter le pack de construction à utiliser![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://docs.cloudfoundry.org/buildpacks/detection.html). Vous pouvez spécifier le [pack de construction](/docs/cfapps/byob.html#using-community-buildpacks) à utiliser dans le fichier manifeste dans le dossier principal de votre application. En général, les packs de construction examinent les artefacts fournis par l'utilisateur afin d'identifier les dépendances à télécharger et de déterminer comment configurer les applications pour qu'elles communiquent avec des services liés. Pour plus d'informations sur les fichiers manifeste, voir [Manifeste d'application](/docs/manageapps/depapps.html#appmanifest).

### Travaux de déploiement

Les travaux de déploiement téléchargent votre projet vers {{site.data.keyword.Bluemix_notm}} en tant qu'application et sont accessibles depuis une URL. Une fois qu'un projet est déployé, l'application déployée apparaît sur votre tableau de bord {{site.data.keyword.Bluemix_notm}}.

Les travaux de déploiement peuvent déployer de nouvelles applications ou mettre à jour des applications existantes. Même si vous déployez une application à l'aide d'une autre méthode, par exemple, l'interface de ligne de commande Cloud Foundry ou la barre d'exécution de l'interface IDE Web, vous pouvez mettre à jour l'application à l'aide d'un travail de déploiement. Pour mettre à jour une application, dans le travail de déploiement, utilisez le nom de cette application.

Vous pouvez effectuer le déploiement dans une ou plusieurs régions et dans un ou plusieurs services. Par exemple, vous pouvez configurer votre {{site.data.keyword.deliverypipeline}} en vue d'utiliser un ou plusieurs services, le tester dans une région, et le déployer en production dans plusieurs régions. Pour plus d'informations, voir
[Régions](/docs/overview/whatisbluemix.html#ov_intro_reg){: new_window}.

### Travaux de test
Si vous voulez exiger que des conditions soient respectées, ajoutez des travaux de test avant ou après vos travaux de génération et de déploiement. Vous pouvez personnaliser des travaux de test pour qu'ils soient simples ou complexes selon vos besoins. Par exemple, vous pouvez exécuter une commande cURL et attendre une réponse spécifique. Vous pouvez également exécuter une suite de tests unitaires ou des tests fonctionnels avec des services de test tiers, tels que Sauce Labs.

Si vos tests génèrent des fichiers de
résultats au format JUnit XML, un rapport qui s'appuie sur les fichiers de résultats apparaît dans l'onglet **Tests** de chaque page de résultat de test. Si un test échoue, le travail échoue également.

## Propriétés d'environnement (variables d'environnement)
{: #environment_properties}

Vous pouvez inclure des propriétés d'environnement dans les commandes shell d'un travail. Les propriétés permettent d'accéder aux informations relatives à l'environnement d'exécution du travail. Pour plus d'informations, voir [Propriétés et ressources d'environnement pour le service {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery/pipeline_deploy_var.html). Les propriétés d'environnement peuvent être transférées entre les travaux d'une même étape en exportant les propriétés.  Pour transmettre les propriétés entre les différentes étapes, créez un fichier `build.properties` dans le référentiel puis faites exécuter le fichier `build.properties` par l'étape suivante.  Par exemple, votre travail de génération peut inclure cette commande dans le script de génération : 

    `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

    All jobs start by executing the `build.properties` file, if it exists.

## Création et utilisation d'artefacts
{: #artifacts}

Les travaux de génération récupèrent automatiquement le contenu du dossier dans lequel le script utilisateur est exécuté. Si vous n'avez pas besoin de tout le contenu du référentiel git pour un déploiement ultérieur, il est préférable de configurer un répertoire de sortie explicite et d'y copier ou d'y créer les artefacts pertinents. Les scripts de travaux sont exécutés dans le résultat de génération (répertoire de sortie).

Les travaux de déploiement déployant dans Cloud Foundry doivent spécifier l'organisation et l'espace où les artefacts doivent être déployés. Si des services supplémentaires sont requis pour exécuter votre application, vous devez les spécifier dans le fichier `manifest.yml`.

Les travaux de déploiement déployant dans IBM Cloud Container Service dans un cluster Kubernetes ont besoin d'un fichier Docker et éventuellement d'une charte Helm.  

Le script de travail s'exécute après que le travail se soit connecté à l'environnement cible (de sorte que vous pouvez effectuer les commandes `cf push` ou `kubectl` dans le script).

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

Les fichiers manifeste, qui sont appelés `manifest.yml` et sont stockés dans le répertoire racine d'un projet, contrôlent la façon dont votre projet est déployé dans {{site.data.keyword.Bluemix_notm}}. Pour obtenir des informations sur la création des fichiers manifeste pour un projet, consultez la documentation [{{site.data.keyword.Bluemix_notm}} sur les manifestes d'application](/docs/manageapps/depapps.html#appmanifest). Pour s'intégrer à {{site.data.keyword.Bluemix_notm}}, votre projet doit contenir un fichier manifeste dans son répertoire racine. Toutefois, vous n'êtes pas obligé d'effectuer le déploiement conformément aux informations du fichier.

Dans le pipeline, vous pouvez spécifier tout ce qu'un fichier manifeste peut faire à l'aide des arguments de commande `cf push`. Les arguments de commande `cf push` sont utiles dans les projets qui possèdent plusieurs projets de déploiement. Si plusieurs travaux de déploiement tentent d'utiliser la route spécifiée dans le fichier manifeste du projet, un conflit se produit.

Pour éviter les conflits, vous pouvez spécifier une route en utilisant la commande `cf push` suivie de l'argument de nom d'hôte, `-n` et d'un nom de route. En modifiant le script de déploiement pour des étapes individuelles, vous pouvez éviter des conflits de route lorsque vous procédez au déploiement sur plusieurs cibles.

Pour utiliser les arguments de commande `cf push`, ouvrez les paramètres de configuration pour un travail de déploiement et modifiez la zone **Script de déploiement**. Pour plus d'informations, consultez la [documentation Cloud Foundry Push ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
