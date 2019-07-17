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


# Utilizzo di immagini di base con versione
{: #pipeline_versioned_base_images}

Quando sviluppi applicazioni per {{site.data.keyword.Bluemix_notm}}, puoi utilizzare le immagini di base con versione per eseguire i lavori della pipeline per assicurarti di utilizzare gli strumenti, le librerie e i runtime correnti. Le immagini di base con versione ti consentono di accertarti che i bit che costituiscono l'applicazione e l'ambiente in cui distribuisci l'applicazione siano coerenti. Puoi controllare quando gli strumenti, le librerie o i runtime per la tua applicazione cambiano e aggiornarli quando ha senso durante il ciclo di sviluppo.

Puoi anche utilizzare le [immagini Docker personalizzate](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) per controllare quali strumenti e versioni di tali strumenti vengono utilizzati per creare e distribuire le applicazioni. Tuttavia, questo metodo richiede che tu abbia familiarità con Docker e di mantenere e aggiornare l'immagine che crei.
{: tip}

## Specifica della versione dell'immagine
{: #specify_base_image_version}

1. Nella pagina Pipeline, fai clic su ![Icona Overflow](images/overflow-icon-2.svg) per accedere all'elenco di opzioni.
2. Fai clic su **Configure Pipeline**.
3. Nella scheda **Image version**, seleziona la versione dell'immagine predefinita da utilizzare per tutti i lavori nella tua pipeline. 

Se scegli l'opzione `Latest`, i lavori della pipeline vengono eseguiti con la versione dell'immagine corrente. La versione dell'immagine corrente viene visualizzata tra parentesi dopo l'opzione `Latest`. Quando è disponibile una nuova versione dell'immagine, l'immagine che viene utilizzata cambia. Potresti dover modificare la tua pipeline per supportare eventuali strumenti più recenti inclusi nella nuova immagine.
{: tip}
 
 ### Contenuti della versione dell'immagine
 {: #image_version_contents}
 
 Sono disponibili le seguenti versioni di immagini:

* **Versione 1.0**: questa immagine precedente corrisponde all'ambiente in cui sono stati eseguiti i lavori della pipeline prima che fossero disponibili le immagini di base con versione. Questa immagine contiene tutte le versioni degli strumenti che erano disponibili quando l'immagine è stata creata, ma non viene più aggiornata. Per accedere alle nuove versioni degli strumenti, esegui l'aggiornamento alla versione dell'immagine corrente. Per ulteriori informazioni sui contenuti della versione dell'immagine 1.0, vedi [Risorse preinstallate](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

* **Versione 2.0**: per visualizzare i contenuti della versione 2.0, dall'immagine in esecuzione, immetti `default_versions.sh`. L'immagine include i seguenti strumenti:

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
 
 * **Versione 2.1**: per visualizzare il contenuto della versione 2.1, dall'immagine in esecuzione, immetti `default_versions.sh`. L'immagine include i seguenti strumenti:

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
 
 Dopo la versione 2.0, le immagini non includono più `grunt` o `python`. Puoi scegliere di installare `grunt` o `python`, se necessario.
 {: tip}

 ## Configurazione dell'immagine per uno specifico lavoro della pipeline
 {: #configure_image_for_job}
 
 In generale, non si consiglia di configurare l'immagine da utilizzare per i singoli lavori della pipeline. Questo metodo aumenta gli sforzi per eseguire l'upgrade a una nuova versione dell'immagine poiché devi aggiornare ogni lavoro della pipeline. Tuttavia, potrebbero verificarsi delle circostanze in cui devi configurare l'immagine per uno specifico lavoro della pipeline.
 {: important}
 
 1. Nella fase, fai clic sull'icona **Stage Configuration** e fai quindi clic su **Configure Stage**.
 2. Nella scheda **JOBS**, fai clic sul lavoro che vuoi modificare.
 3. L'opzione **Pipeline image version** mostra la versione dell'immagine corrente disponibile e la versione che stai utilizzando per il lavoro della pipeline selezionato. Per modificare la versione dell'immagine in modo da utilizzare la versione corrente per eseguire il lavoro della pipeline, seleziona **Latest**.

Per eseguire i lavori della pipeline con l'immagine che hai selezionato nella pagina di configurazione della pipeline, seleziona **Pipeline default**.
{: tip}
