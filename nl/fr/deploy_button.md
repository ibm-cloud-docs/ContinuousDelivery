---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Création d'un bouton Déployer dans {{site.data.keyword.Bluemix_notm}} {: #deploy-button}

Le bouton Déployer dans {{site.data.keyword.Bluemix_notm}} est un moyen efficace de partager votre application Git publique avec d'autres personnes afin de permettre à ces dernières d'expérimenter le code et de le déployer dans IBM {{site.data.keyword.Bluemix_notm}} à l'aide d'une chaîne d'outils. Il nécessite une configuration minimale et vous pouvez l'insérer à n'importe quel emplacement prenant en charge le balisage. Lorsqu'une personne clique sur ce bouton, une copie clonée du code est créée dans un nouveau référentiel Git, et votre application d'origine n'est pas affectée.
{: shortdesc}

Lorsqu'un utilisateur clique sur votre bouton, les actions suivantes se produisent :

1. Si la personne ne dispose pas d'un compte {{site.data.keyword.Bluemix_notm}} actif, elle doit créer un compte. Il peut s'agir d'un compte d'essai ou d'un compte réel.

2. La personne peut sélectionner une région, une organisation, un espace et un nom d'application en cliquant sur l'icône {{site.data.keyword.deliverypipeline}}. Le nom d'application suggéré est identique au nom de la chaîne d'outils, construit à partir du nom de votre référentiel Git d'origine et de l'heure. Le nom de la chaîne d'outils peut également être édité.

3. Une chaîne d'outils est créée. Elle inclut un nouveau clone privé de votre référentiel Git, un pipeline pour la génération et le déploiement des modifications de code, l'interface Eclipse Orion {{site.data.keyword.webide}} pour l'édition du code sur le cloud, et un dispositif de suivi de problèmes.

  **Astuce** : si le répertoire `.bluemix` contient un fichier `toolchain.yml`, celui-ci est utilisé pour spécifier les intégrations d'outils pour la chaîne d'outils. Pour plus d'informations sur le fichier `toolchain.yml`, voir [Création de chaînes d'outils personnalisées](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}.

4. Si l'application requiert un fichier de génération, celui-ci est détecté automatiquement et l'application est générée.

5. Si un pipeline est configuré pour le processus de génération et de déploiement, un fichier `pipeline.yml` est utilisé pour déployer l'application.

6. Si l'application requiert un conteneur, un fichier `pipeline.yml` qui définit le service IBM Containers et un fichier Dockerfile qui définit une image sont utilisés pour déployer l'application dans un conteneur {{site.data.keyword.Bluemix_notm}}.

7. L'application est déployée sur l'organisation {{site.data.keyword.Bluemix_notm}} que la personne a sélectionnée.

## Exemples de bouton {: #button-examples}

Examinez l'exemple de bouton suivant pour un référentiel {{site.data.keyword.gitrepos}} public :

[![Déployer dans Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

Examinez l'exemple de bouton suivant pour un référentiel  GitHub public :

[![Déployer dans Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## Création d'un bouton {: #create-button}

Pour créer un bouton Déployer dans {{site.data.keyword.Bluemix_notm}}, copiez et modifiez les modèles de fragment ci-dessous. Spécifiez un référentiel Git et une branche dans l'URL.

### Création d'un bouton en HTML

Pour créer un bouton en HTML, copiez ce fragment et insérez une URL et une branche de référentiel Git public.

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="Deploy to Bluemix"></a>
```
{: codeblock}

Si vous n'incluez pas le paramètre `branch` dans l'URL de référentiel de votre fragment, la branche maître du référentiel est la cible par défaut du bouton Déployer dans Bluemix.

### Création d'un bouton en Markdown

Pour créer un bouton en Markdown, copiez ce fragment et insérez une URL et une branche de référentiel Git public.

```Markdown
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

Si vous n'incluez pas le paramètre `branch` dans l'URL de référentiel de votre fragment, la branche maître du référentiel est la cible par défaut du bouton Déployer dans Bluemix.

### Utilisation des fragments de bouton {: #button-snippet}

Après avoir créé un fragment du bouton Déployer dans Bluemix, vous pouvez l'insérer dans des blogues, des articles, des wikis, des fichiers Readme ou dans n'importe quel endroit où vous souhaitez promouvoir votre application.

Lorsque vous personnalisez le fragment pour votre bouton Déployer dans {{site.data.keyword.Bluemix_notm}}, tenez compte du fait que les deux modèles utilisent un chemin par défaut vers une image de bouton externe au format PNG et en anglais.

* Si vous préférez utiliser une image SVG au lieu d'une image PNG pour le bouton, modifiez le chemin d'accès à l'image du bouton qui est utilisé dans le fragment et remplacez-le par `https://bluemix.net/deploy/button.svg`.

* Si vous préférez utiliser une image pour le bouton, modifiez le chemin d'accès à l'image du bouton qui est utilisé dans le fragment et remplacez-le par `https://bluemix.net/deploy/button_x2.png`. La taille de cette image est deux fois supérieure à celle de l'image par défaut.

* Si vous préférez stocker l'image en local, vous pouvez la télécharger et la stocker dans votre référentiel Git. Ajustez le chemin d'accès pour qu'il reflète l'emplacement relatif de l'image.

* Si vous voulez utiliser une version traduite du bouton, vous pouvez la référencer à distance ou la télécharger depuis [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}.

## Remarques sur le référentiel {: #button-repo}

Passez en revue ces remarques pour le référentiel que vous utilisez dans votre bouton Déployer dans {{site.data.keyword.Bluemix_notm}}.


## Exigences relatives au fichier de génération
{: build_file}

Si l'application doit être générée avant de pouvoir être déployée, vous devez inclure un fichier de génération dans votre référentiel. Si un fichier script de génération est détecté dans le répertoire principal du référentiel, une génération automatique du code se déclenche avant le déploiement.

Les générateurs pris en charge sont les suivants :

* [Ant ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") : ](http://ant.apache.org/manual/using.html){:new_window} `build.xml`, qui génère une sortie dans le dossier `./output/`
* [Gradle ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") : ](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window} `/build.gradle`, qui génère une sortie dans le dossier `.` 
* [Grunt ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") : ](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`, qui génère une sortie dans le dossier `.` 
* [Maven ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") : ](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window} `/pom.xml`, qui génère une sortie dans le dossier `./target/`.

### Exigences relatives au pipeline
{: pipeline_file}

Afin de configurer le pipeline pour la chaîne d'outils dans un répertoire `.bluemix`, ajoutez un fichier `pipeline.yml`. Pour chaque fichier`pipeline.yml` de ce répertoire, un pipeline est créé lorsque la chaîne d'outils est instanciée.

Si vous n'avez pas de fichier `pipeline.yml` dans le répertoire `.bluemix`, le bouton Déployer dans {{site.data.keyword.Bluemix_notm}} créera un pipeline par défaut avec deux étapes : une étape de génération et une étape de déploiement déployant dans Cloud Foundry.

Pour créer un fichier de pipeline, examinez l'exemple de fichier dans la rubrique [Création de modèles de chaîne d'outils personnalisés](toolchains_custom.html#toolchains_custom_pipeline_yml). Tout comme vous définissez un pipeline dans l'interface Web, vous définissez un pipeline dans du texte en créant des étapes et des travaux, en définissant des entrées et des variables d'environnement et en ajoutant des scripts. Vous pouvez également visualiser un certain nombre de fichiers de pipeline plus complexes dans [ce projet de démonstration](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix).

### Exigences relative au fichier Dockerfile d'un conteneur
{: container_dockerfile}

Pour déployer une application dans un conteneur à l'aide d'IBM Containers, vous devez inclure un fichier Dockerfile dans le répertoire principal du référentiel et vous devez ajouter un fichier `pipeline.yml` dans un répertoire `.bluemix`.

Le fichier Dockerfile agit comme une sorte de script de génération pour l'application. Si un fichier Dockerfile est détecté dans le référentiel, l'application est générée automatiquement dans une image avant d'être déployée dans un conteneur. Si l'application proprement dite doit être générée avant que l'application ne soit générée dans une image, ajoutez un script de génération pour l'application et un fichier Dockerfile.

Pour en savoir plus sur la création de fichiers Dockerfile, voir la [documentation Docker ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.docker.com/reference/builder/){:new_window}.  Pour suivre les instructions étape par étape à l'aide d'un modèle de chaîne d'outils pour déployer vers Kubernetes, voir le [tutoriel Utilisation d'une chaîne d'outils "Développer une application Kubernetes"![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window} ou le [tutoriel Utilisation de la chaîne d'outils "Développer une application Kubernetes avec Helm"![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window}.  
Pour en savoir plus sur le portage de votre application Cloud Foundry sur un cluster Kubernetes, voir le [tutoriel Portage de votre application Cloud Foundry pour un déploiement sur Kubernetes ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/port-an-app-from-cf-to-kubernetes-in-a-toolchain?task=0){:new_window}.  

`` 

Pour créer manuellement un fichier `pipeline.yml` spécifiquement pour les conteneurs, voir les [exemples dans GitHub ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/Puquios/){:new_window}.

## Exigences relatives au fichier manifeste (pour les applications déployées dans Cloud Foundry)
{: #manifest_files}

La présence d'un fichier `manifest.yml` n'est pas requise dans votre référentiel. Toutefois, si votre application requiert l'exécution d'autres services, vous devez fournir un fichier manifeste qui déclare ces services.

Pour en savoir plus sur les fichiers manifeste, voir [Manifeste d'application](/docs/cfapps/depapps.html#appmanifest).
