---

Copyright:
  years: 2019
lastupdated: "2019-06-20"

keywords: pipeline versioned base image, image version, IBM Cloud team uses

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Utilisation des images de base versionnées
{: #pipeline_versioned_base_images}

Lorsque vous développez des applications pour {{site.data.keyword.Bluemix_notm}}, vous pouvez utiliser des images de base versionnées afin d'exécuter des travaux de pipeline et être certain d'utiliser les outils, bibliothèques et modules d'exécution en cours. Les images de base versionnées vous permettent de vous assurer que les bits qui constituent l'application et l'environnement sur lequel vous déployez l'application sont cohérents. Vous pouvez contrôler à quel moment les outils, les bibliothèques ou les modules d'exécution pour votre application sont modifiés et les mettre à jour au moment qui vous paraît opportun durant le cycle de développement.

Vous pouvez également utiliser des [images Docker personnalisées](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) pour contrôler à la fois les outils et les versions de ces outils qui sont utilisés pour créer et déployer des applications. Toutefois, cette méthode nécessite de maîtriser Docker et de gérer et mettre à jour l'image créée.
{: tip}

## Spécification de la version d'image
{: #specify_base_image_version}

1. Sur la page Pipeline, cliquez sur ![icône de flux de travaux](images/overflow-icon-2.svg) pour accéder à la liste d'options.
2. Cliquez sur **Configurer le pipeline**.
3. Sur l'onglet **Version d'image**, sélectionnez la version d'image par défaut à utiliser pour tous les travaux de votre pipeline. 

Si vous choisissez l'option `Dernière`, les travaux de pipeline sont exécutés avec la version d'image en cours. La version d'image en cours apparaît entre crochets après l'option `Dernière`. Lorsqu'une nouvelle version d'image est disponible, l'image qui est utilisée est modifiée. Il se peut que vous deviez modifier votre pipeline pour qu'il prenne en charge d'éventuels outils plus récents qui sont inclus dans la nouvelle image.
{: tip}
 
 ### Contenu de la version d'image
 {: #image_version_contents}
 
 Les versions d'image suivantes sont disponibles :

* **Version 1.0** : cette image antérieure correspond à l'environnement dans lequel les travaux de pipeline étaient exécutés avant la mise à disposition des images de base versionnées. Cette image contient toutes les versions des outils qui étaient disponibles lorsque l'image a été créée, mais elle n'est plus mise à jour. Pour accéder aux nouvelles versions d'outils, effectuez une mise à jour vers la version d'image en cours. Pour plus d'informations sur le contenu de la version d'image 1.0, voir [Ressources préinstallées](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

* **Version 2.0** : pour afficher le contenu de la version 2.0, à partir de l'image en cours, tapez `default_versions.sh`. Cette image inclut les outils suivants :

```
	# node --version
	v10.15.3

	# npm --version
	6.4.1

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.2.1

	# kubectl version
	Client Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	The connection to the server localhost:8080 was refused - did you specify the right host or port?

	# helm version --client
	Client: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.14.0+3303164-2019-02-06T06:09:00+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.30       
	container-registry                     0.1.380      
	container-service/kubernetes-service   0.2.99    Update Available   
	doi                                    0.1.0        


	# java -version
	openjdk version "1.8.0_191"
	OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.16.04.1-b12)
	OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)

	# ant -version
	Apache Ant(TM) version 1.10.5 compiled on July 10 2018

	# mvn -version
	Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.4.0-141-generic", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 5.2.1!

	Here are the highlights of this release:
	 - Define sets of dependencies that work together with Java Platform plugin
	 - New C++ plugins with dependency management built-in
	 - New C++ project types for gradle init
	 - Service injection into plugins and project extensions

	For more details see https://docs.gradle.org/5.2.1/release-notes.html


	------------------------------------------------------------
	Gradle 5.2.1
	------------------------------------------------------------

	Build time:   2019-02-08 19:00:10 UTC
	Revision:     f02764e074c32ee8851a4e1877dd1fea8ffb7183

	Kotlin DSL:   1.1.3
	Kotlin:       1.3.20
	Groovy:       2.5.4
	Ant:          Apache Ant(TM) version 1.9.13 compiled on July 10 2018
	JVM:          1.8.0_191 (Oracle Corporation 25.191-b12)
	OS:           Linux 4.4.0-141-generic amd64
  ```
 {: codeblock}
 
 * **Version 2.1** : pour afficher le contenu de la version 2.1, dans l'image en cours, entrez `default_versions.sh`. Cette image inclut les outils suivants :

```
	# node --version
	v10.16.0

	# npm --version
	6.9.0

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.0

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.3", GitCommit:"5e53fd6bc17c0dec8434817e69b04a25d8ae0ff0", GitTreeState:"clean", BuildDate:"2019-06-06T01:44:30Z", GoVersion:"go1.12.5", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.14.1", GitCommit:"5270352a09c7e8b6e8c9593002a73535276507c0", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.16.2+d1a5f92-2019-06-06T18:32:54+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.32       
	container-registry                     0.1.391      
	container-service/kubernetes-service   0.3.47  
	doi                                    0.1.2        


	# java -version
	openjdk version "1.8.0_212"
	OpenJDK Runtime Environment (build 1.8.0_212-8u212-b03-0ubuntu1.16.04.1-b03)
	OpenJDK 64-Bit Server VM (build 25.212-b03, mixed mode)

	# ant -version
	Apache Ant(TM) version 1.10.6 compiled on May 2 2019

	# mvn -version
	Apache Maven 3.6.1 (d66c9c0b3152b2e69ee9bac180bb8fcc8e6af555; 2019-04-04T19:00:29Z)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_212, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.4.0-141-generic", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 5.4.1!

	Here are the highlights of this release:
	 - Run builds with JDK12
	 - New API for Incremental Tasks
	 - Updates to native projects, including Swift 5 support

	For more details see https://docs.gradle.org/5.4.1/release-notes.html


	------------------------------------------------------------
	Gradle 5.4.1
	------------------------------------------------------------

	Build time:   2019-04-26 08:14:42 UTC
	Revision:     261d171646b36a6a28d5a19a69676cd098a4c19d

	Kotlin:       1.3.21
	Groovy:       2.5.4
	Ant:          Apache Ant(TM) version 1.9.13 compiled on July 10 2018
	JVM:          1.8.0_212 (Oracle Corporation 25.212-b03)
	OS:           Linux 4.4.0-141-generic amd64
  ```
 {: codeblock}
 
 Après la version 2.0, les images n'incluent plus `grunt` ou `python`. Vous pouvez choisir d'installer `grunt` ou `python`, si nécessaire.
 {: tip}

 ## Configuration de l'image pour un travail de pipeline spécifique
 {: #configure_image_for_job}
 
 En général, il n'est pas recommandé de configurer l'image à utiliser pour des travaux de pipeline individuels. Cette méthode augmente l'effort de mise à niveau vers une nouvelle version d'image dans la mesure où vous devez mettre à jour chaque travail de pipeline. Toutefois, dans certaines circonstances, vous devez configurer l'image pour un travail de pipeline spécifique.
 {: important}
 
 1. Sur l'étape, cliquez sur l'icône **Configuration de l'étape**, puis sur **Configurer l'étape**.
 2. Dans l'onglet **TRAVAUX**, cliquez sur le travail que vous souhaitez modifier.
 3. L'option **Version d'image Pipeline** affiche la version d'image en cours qui est disponible et la version que vous utilisez pour le travail de pipeline sélectionné. Pour modifier la version d'image et utiliser la version en cours pour exécuter le travail de pipeline, sélectionnez **Dernière**.

Pour exécuter des travaux de pipeline avec l'image que vous avez sélectionnée sur la page de configuration de pipeline, sélectionnez **Valeur par défaut de pipeline**.
{: tip}
