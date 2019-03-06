---

Copyright:
  years: 2019
lastupdated: "2019-2-14"

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
	v10.15.1
	
	# npm --version
	6.4.1
	
	# jq --version
	jq-1.6
	
	# kubectl version
	Client Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	The connection to the server localhost:8080 was refused - did you specify the right host or port?
	
	# helm version --client
	Client: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}
	
	# ibmcloud -version
	ibmcloud version 0.13.1+0536e96-2018-12-20T10:00:05+00:00
	
	# ibmcloud plugin list
	Listing installed plug-ins...
	
	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.29       
	container-registry                     0.1.365      
	container-service/kubernetes-service   0.2.44       
	
	# java -version
	java version "1.8.0_191"
	Java(TM) SE Runtime Environment (build 8.0.5.27 - pxa6480sr5fp27-20190104_01(SR5 FP27))
	IBM J9 VM (build 2.9, JRE 1.8.0 Linux amd64-64-Bit Compressed References 20181219_405297 (JIT enabled, AOT enabled)
	OpenJ9   - 3f2d574
	OMR      - 109ba5b
	IBM      - e2996d1)
	JCL - 20190104_01 based on Oracle jdk8u191-b26
	
	# ant -version
	Apache Ant(TM) version 1.10.5 compiled on July 10 2018
	
	# mvn -version
	Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_191, vendor: IBM Corporation, runtime: /opt/IBM/java8/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.4.0-141-generic", arch: "amd64", family: "unix"
	
	# gradle -version
	
	Welcome to Gradle 5.2!
	
	Here are the highlights of this release:
	 - Define sets of dependencies that work together with Java Platform plugin
	 - New C++ plugins with dependency management built-in
	 - New C++ project types for gradle init
	 - Service injection into plugins and project extensions
	
	For more details see https://docs.gradle.org/5.2/release-notes.html
	
	------------------------------------------------------------
	Gradle 5.2
	------------------------------------------------------------
	
	Build time:   2019-02-04 11:16:48 UTC
	Revision:     840644a429c8b8b9ae399867eb1660e3109bc7a3
	
	Kotlin DSL:   1.1.3
	Kotlin:       1.3.20
	Groovy:       2.5.4
	Ant:          Apache Ant(TM) version 1.9.13 compiled on July 10 2018
	JVM:          1.8.0_191 (IBM Corporation 2.9)
	OS:           Linux 4.4.0-141-generic amd64
  ```
 {: codeblock}
 
 ## Configuration de l'image pour un travail de pipeline spécifique
 {: #configure_image_for_job}
 
 En général, il n'est pas recommandé de configurer l'image à utiliser pour des travaux de pipeline individuels. Cette méthode augmente l'effort de mise à niveau vers une nouvelle version d'image dans la mesure où vous devez mettre à jour chaque travail de pipeline. Toutefois, dans certaines circonstances, vous devez configurer l'image pour un travail de pipeline spécifique.
 {: important}
 
 1. Sur l'étape, cliquez sur l'icône **Configuration de l'étape**, puis sur **Configurer l'étape**.
 2. Dans l'onglet **TRAVAUX**, cliquez sur le travail que vous souhaitez modifier. 
 3. L'option **Version d'image Pipeline** affiche la version d'image en cours qui est disponible et la version que vous utilisez pour le travail de pipeline sélectionné. Pour modifier la version d'image et utiliser la version en cours pour exécuter le travail de pipeline, sélectionnez **Dernière**.

Pour exécuter des travaux de pipeline avec l'image que vous avez sélectionnée sur la page de configuration de pipeline, sélectionnez **Valeur par défaut de pipeline**.
{: tip}
