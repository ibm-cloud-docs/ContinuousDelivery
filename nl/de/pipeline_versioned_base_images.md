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


# Mit versionsbasierten Images arbeiten
{: #pipeline_versioned_base_images}

Bei der Entwicklung von Anwendungen für {{site.data.keyword.Bluemix_notm}} können Sie versionsbasierte Images für die Ausführung von Pipelinejobs verwenden, um sicherzustellen, dass die korrekten Tools, Bibliotheken und Laufzeiten verwendet werden. Mithilfe versionsbasierter Images können Sie sicherstellen, dass die Komponenten, aus denen die Anwendung besteht, und die Umgebung, in der Sie die Anwendung bereitstellen, konsistent sind. Sie können steuern, wann die Tools, Bibliotheken oder Laufzeiten für die Anwendung geändert werden, und diese zu einem sinnvollen Zeitpunkt während des Entwicklungszyklus aktualisieren.

Darüber hinaus können Sie [angepasste Docker-Images](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) verwenden, um sowohl die Tools als auch die Versionen dieser Tools, die für den Build und die Bereitstellung von Anwendungen verwendet werden, zu steuern. Zur Verwendung dieser Methode müssen Sie jedoch mit Docker vertraut sein und das erstellte Image verwalten und aktualisieren.
{: tip}

## Imageversion angeben
{: #specify_base_image_version}

1. Klicken Sie auf der Seite 'Pipeline' auf ![Überlaufsymbol](images/overflow-icon-2.svg), um auf die Liste der Optionen zuzugreifen.
2. Klicken Sie auf **Pipeline konfigurieren**.
3. Wählen Sie auf der Registerkarte **Imageversion** die Standardimageversion aus, die für alle Jobs in der Pipeline verwendet werden soll. 

Wenn Sie die Option `Neueste` auswählen, werden die Pipelinejobs mit der aktuellen Imageversion ausgeführt. Die aktuelle Imageversion wird in eckigen Klammern nach der Option `Neueste` angezeigt. Wenn eine neue Imageversion verfügbar ist, ändert sich das verwendete Image. Sie müssen möglicherweise die Pipeline so ändern, dass sie gegebenenfalls neuere Tools unterstützt, die im neuen Image enthalten sind.
{: tip}
 
 ### Inhalt der Imageversion
 {: #image_version_contents}
 
 Die folgenden Imageversionen sind verfügbar:

* **Version 1.0**: Dieses frühere Image entspricht der Umgebung, in der Pipelinejobs ausgeführt wurden, bevor versionsbasierte Images verfügbar waren. Dieses Image enthält alle Versionen der Tools, die bei der Erstellung des Images verfügbar waren, wird jedoch nicht mehr aktualisiert. Für den Zugriff auf neue Versionen der Tools müssen Sie eine Aktualisierung auf die aktuelle Imageversion durchführen. Weitere Informationen zum Inhalt der Imageversion 1.0 finden Sie in [Vorinstallierte Ressourcen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

* **Version 2.0**: Zum Anzeigen des Inhalts von Version 2.0 geben Sie im aktiven Image `default_versions.sh` ein. Dieses Image enthält die folgenden Tools:

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
	Client-Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	Die Verbindung zum Server localhost:8080 wurde nicht zugelassen. Sicherstellen, dass der korrekte Host bzw. Port angegeben wurde.

	# helm version --client
	Client: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.14.0+3303164-2019-02-06T06:09:00+00:00

	# ibmcloud plugin list
	Installierte Plug-ins auflisten...

	Plug-in-Name                           Version   Status
	cloud-functions/wsk/functions/fn       1.0.30
	container-registry                     0.1.380
	container-service/kubernetes-service   0.2.99    Aktualisierung verfügbar
	doi                                    0.1.0


	# java -version
	openjdk version "1.8.0_191"
	OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.16.04.1-b12)
	OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)

	# ant -version
	Apache Ant(TM) Version 1.10.5 kompiliert am 10. Juli 2018

	# mvn -version
	Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
	Maven-Home: /opt/IBM/maven
	Java-Version: 1.8.0_191, Vendor: Oracle Corporation, Laufzeit: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Standardländereinstellung: en_US, Plattformcodierung: UTF-8
	Betriebssystem: "linux", Version: "4.4.0-141-generic", arch: "amd64", family: "unix"

	# gradle -version

	Willkommen bei Gradle 5.2.1!
	
	Highlights in diesem Release:
	 - Gruppe von Abhängigkeiten definieren, die mit dem Java-Plattform-Plug-in interagieren
	 - Neue C++-Plug-ins mit integriertem Abhängigkeitsmanagement
	 - Neue C++-Projekttypen für die Initiierung von Gradle
	 - Einfügen des Service in Plug-ins und Projekterweiterungen

	Weitere Details finden Sie unter https://docs.gradle.org/5.2.1/release-notes.html


	------------------------------------------------------------
	Gradle 5.2.1
	------------------------------------------------------------

	Buildzeit:    2019-02-08 19:00:10 UTC
	Überarbeitung:f02764e074c32ee8851a4e1877dd1fea8ffb7183

	Kotlin DSL:   1.1.3
	Kotlin:       1.3.20
	Groovy:       2.5.4
	Ant:          Apache Ant(TM) Version 1.9.13 kompiliert am 10. Juli 2018
	JVM:          1.8.0_191 (Oracle Corporation 25.191-b12)
	OS:            Linux 4.4.0-141-generic amd64
  ```
 {: codeblock}
 
 * **Version 2.1**: Zum Anzeigen des Inhalts von Version 2.1 geben Sie im aktiven Image `default_versions.sh` ein. Dieses Image enthält die folgenden Tools:

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
	Client-Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.3", GitCommit:"5e53fd6bc17c0dec8434817e69b04a25d8ae0ff0", GitTreeState:"clean", BuildDate:"2019-06-06T01:44:30Z", GoVersion:"go1.12.5", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.14.1", GitCommit:"5270352a09c7e8b6e8c9593002a73535276507c0", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.16.2+d1a5f92-2019-06-06T18:32:54+00:00

	# ibmcloud plugin list
	Installierte Plug-ins auflisten...

	Plug-in-Name                           Version   Status
	cloud-functions/wsk/functions/fn       1.0.32
	container-registry                     0.1.391
	container-service/kubernetes-service   0.3.47
	doi                                    0.1.2


	# java -version
	openjdk version "1.8.0_212"
	OpenJDK Runtime Environment (build 1.8.0_212-8u212-b03-0ubuntu1.16.04.1-b03)
	OpenJDK 64-Bit Server VM (build 25.212-b03, mixed mode)

	# ant -version
	Apache Ant(TM) Version 1.10.6 kompiliert am 2. Mai 2019

	# mvn -version
	Apache Maven 3.6.1 (d66c9c0b3152b2e69ee9bac180bb8fcc8e6af555; 2019-04-04T19:00:29Z)
	Maven-Home: /opt/IBM/maven
	Java-Version: 1.8.0_212, Vendor: Oracle Corporation, Laufzeit: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Standardländereinstellung: en_US, Plattformcodierung: UTF-8
	Betriebssystem: "linux", Version: "4.4.0-141-generic", arch: "amd64", family: "unix"

	# gradle -version

	Willkommen bei Gradle 5.4.1!
	
	Highlights in diesem Release:
	 - Builds mit JDK12 ausführen
	 - Neue API für inkrementelle Tasks
	 - Aktualisierungen für native Projekte, einschließlich Swift 5-Unterstützung

	Weitere Details finden Sie unter https://docs.gradle.org/5.4.1/release-notes.html


	------------------------------------------------------------
	Gradle 5.4.1
	------------------------------------------------------------

	Buildzeit:    2019-04-26 08:14:42 UTC
	Überarbeitung:261d171646b36a6a28d5a19a69676cd098a4c19d

	Kotlin:       1.3.21
	Groovy:       2.5.4
	Ant:          Apache Ant(TM) Version 1.9.13 kompiliert am 10. Juli 2018
	JVM:          1.8.0_212 (Oracle Corporation 25.212-b03)
	OS:            Linux 4.4.0-141-generic amd64
  ```
 {: codeblock}
 
 Nach Version 2.0 enthalten Images nicht mehr `grunt` oder `python`. Falls erforderlich, können Sie `grunt` oder `python` installieren.{: tip}

 ## Image für einen bestimmten Pipelinejob konfigurieren
 {: #configure_image_for_job}
 
 Im Allgemeinen wird nicht empfohlen, das für einzelne Pipelinejobs zu verwendende Image zu konfigurieren. Dies erhöht den Aufwand eines Upgrades auf eine neue Imageversion, da hierfür jeder Pipelinejob aktualisiert werden muss. In bestimmten Situationen kann es jedoch erforderlich sein, das Image für einen bestimmten Pipelinejob zu konfigurieren.
 {: important}
 
 1. Klicken Sie in der Stage auf das Symbol **Phasenkonfiguration** und dann auf **Phase konfigurieren**.
 2. Klicken Sie auf der Registerkarte **Jobs** auf den zu ändernden Job.
 3. Mit der Option **Pipeline-Imageversion** werden die verfügbare aktuelle Imageversion und die für den ausgewählten Pipelinejob verwendete Version angezeigt. Wählen Sie **Neueste** aus, um die Imageversion so zu ändern, dass für die Ausführung des Pipelinejobs die aktuelle Version verwendet wird.

Wenn Sie Pipelinejobs mit dem Image ausführen möchten, das Sie auf der Pipelinekonfigurationsseite ausgewählt haben, wählen Sie **Standardeinstellung für Pipeline** aus.
{: tip}
