---

Copyright:
  years: 2019
lastupdated: "2019-02-27"

keywords: pipeline versioned base image, image version, IBM Cloud team uses

subcollection: ContinuousDelivery

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
	v10.15.1
	
	# npm --version
	6.4.1
	
	# jq --version
	jq-1.6
	
	# kubectl version
	Client-Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	Die Verbindung zum Server localhost:8080 wurde nicht zugelassen. Sicherstellen, dass der korrekte Host bzw. Port angegeben wurde.
	
	# helm version --client
	Client: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}
	
	# ibmcloud -version
	ibmcloud version 0.13.1+0536e96-2018-12-20T10:00:05+00:00
	
	# ibmcloud plugin list
 Liste der installierten Plug-ins...
	
	Plugin-Name                            Version   Status
	cloud-functions/wsk/functions/fn       1.0.29
	container-registry                     0.1.365
	container-service/kubernetes-service   0.2.44       
	
	# java -version
	java version "1.8.0_191"
	Java(TM) SE Runtime Environment (build 8.0.5.27 - pxa6480sr5fp27-20190104_01(SR5 FP27))
	IBM J9 VM (Build 2.9, JRE 1.8.0 Linux amd64-64-Bit Compressed References 20181219_405297 (JIT aktiviert, AOT aktiviert)
	OpenJ9   - 3f2d574
	OMR      - 109ba5b
	IBM      - e2996d1)
	JCL      - 20190104_01 auf der Basis von Oracle jdk8u191-b26
	
	# ant -version
	Apache Ant(TM) Version 1.10.5 kompiliert am 10. Juli 2018
	
	# mvn -version
	Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
	Maven-Home: /opt/IBM/maven
	Java-Version: 1.8.0_191, Vendor: IBM Corporation, Laufzeit: /opt/IBM/java8/jre
	Standardländereinstellung: en_US, Plattformcodierung: UTF-8
	Betriebssystem: "linux", Version: "4.4.0-141-generic", arch: "amd64", family: "unix"
	
	# gradle -version
	
	Willkommen bei Gradle 5.2!
	
	Highlights in diesem Release:
	 - Gruppe von Abhängigkeiten definieren, die mit dem Java-Plattform-Plug-in interagieren
	 - Neue C++-Plug-ins mit integriertem Abhängigkeitsmanagement
	 - Neue C++-Projekttypen für die Initiierung von Gradle
	 - Einfügen des Service in Plug-ins und Projekterweiterungen
	
	Weitere Details finden Sie unter https://docs.gradle.org/5.2/release-notes.html.
	
	------------------------------------------------------------
	Gradle 5.2
	------------------------------------------------------------
	
	Buildzeit:     2019-02-04 11:16:48 UTC
	Überarbeitung: 840644a429c8b8b9ae399867eb1660e3109bc7a3
	
	Kotlin DSL:    1.1.3
	Kotlin:        1.3.20
	Groovy:        2.5.4
	Ant:           Apache Ant(TM) Version 1.9.13, kompiliert am 10. Juli 2018
	JVM:           1.8.0_191 (IBM Corporation 2.9)
	OS:            Linux 4.4.0-141-generic amd64
  ```
 {: codeblock}
 
 ## Image für einen bestimmten Pipelinejob konfigurieren
 {: #configure_image_for_job}
 
 Im Allgemeinen wird nicht empfohlen, das für einzelne Pipelinejobs zu verwendende Image zu konfigurieren. Dies erhöht den Aufwand eines Upgrades auf eine neue Imageversion, da hierfür jeder Pipelinejob aktualisiert werden muss. In bestimmten Situationen kann es jedoch erforderlich sein, das Image für einen bestimmten Pipelinejob zu konfigurieren.
 {: important}
 
 1. Klicken Sie in der Stage auf das Symbol **Phasenkonfiguration** und dann auf **Phase konfigurieren**.
 2. Klicken Sie auf der Registerkarte **Jobs** auf den zu ändernden Job.
 3. Mit der Option **Pipeline-Imageversion** werden die verfügbare aktuelle Imageversion und die für den ausgewählten Pipelinejob verwendete Version angezeigt. Wählen Sie **Neueste** aus, um die Imageversion so zu ändern, dass für die Ausführung des Pipelinejobs die aktuelle Version verwendet wird.

Wenn Sie Pipelinejobs mit dem Image ausführen möchten, das Sie auf der Pipelinekonfigurationsseite ausgewählt haben, wählen Sie **Standardeinstellung für Pipeline** aus.
{: tip}
