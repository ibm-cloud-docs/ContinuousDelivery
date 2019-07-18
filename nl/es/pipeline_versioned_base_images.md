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


# Cómo trabajar con imágenes de base con versión
{: #pipeline_versioned_base_images}

Cuando se desarrollan aplicaciones para {{site.data.keyword.Bluemix_notm}}, pueden utilizarse imágenes de base con versión para ejecutar trabajos de conducto para asegurar que se están utilizando las herramientas, bibliotecas y entornos de tiempo de ejecución actuales. Las imágenes base con versión ayudan a asegurarse de que los bits que componen la aplicación, y el entorno en que ésta se despliega, son coherentes. Puede controlarse cuándo cambian las herramientas, bibliotecas y entornos de tiempo de ejecución de la aplicación y actualizarlas cuando tiene sentido durante el ciclo de desarrollo.

También pueden utilizarse [imágenes personalizadas de Docker](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) para controlar las herramientas y qué versiones de dichas herramientas se utilizan para crear y desplegar aplicaciones. Sin embargo, este método requiere estar familiarizado con Docker, y la imagen creada debe mantenerse y actualizarse.
{: tip}

## Cómo especificar la versión de imagen
{: #specify_base_image_version}

1. En la página Conducto, pulse ![Icono de desbordamiento](images/overflow-icon-2.svg) para acceder a la lista de opciones.
2. Pulse **Configurar conducto**.
3. En el separador **Versión de imagen**, seleccione la versión de imagen predeterminada para utilizar para todos los trabajos del conducto. 

Si elige la opción `Más reciente`, los trabajos del conducto se ejecutan con la versión de imagen actual. La versión de imagen actual se muestra entre corchetes después de la opción `Más reciente`. Cuando una nueva versión de imagen está disponible, la imagen utilizada cambia. Es posible que necesite modificar el conducto para dar soporte a las nuevas herramientas que puedan incluirse en la nueva imagen.
{: tip}
 
 ### Contenido de la versión de imagen
 {: #image_version_contents}
 
 Están disponibles las siguientes versiones de imagen:

* **Versión 1.0**: Esta imagen anterior coincide con el entorno en el que se ejecutaban los trabajos de conducto antes de que estuvieran disponibles las imágenes con versión. Esta imagen contiene todas las versiones de las herramientas que estaban disponibles cuando se creó la imagen, pero ya no se actualiza. Para acceder a versiones nuevas de las herramientas, actualice a la versión de imagen actual. Para obtener más información sobre el contenido de la versión de imagen 1.0, consulte [Recursos preinstalados](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

* **Versión 2.0**: para ver el contenido de la versión 2.0, desde la imagen en ejecución, escriba `default_versions.sh`. Esta imagen incluye las herramientas siguientes:

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
	Versión de cliente: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	La conexión al servidor localhost:8080 se ha rechazado; ¿ha especificado el host y puerto correctos?

	# helm version --client
	Cliente: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}

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
	Apache Ant(TM) versión 1.10.5 compilado el 10 de julio de 2018

	# mvn -version
	Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.4.0-141-generic", arch: "amd64", family: "unix"

	# gradle -version

	Bienvenido a Gradle 5.2.1

	Aquí están los aspectos destacados de este release:
	 - Definir conjuntos de dependencias que funcionan conjuntamente con el plug-in de Java Platform
	 - Nuevos plug-ins de C++ con gestión incorporada de dependencias
	 - Nuevos tipos de proyecto de C++ para gradle init
	 - Inyección de servicios en plug-in y extensiones de proyecto

	Para obtener más detalles, consulte https://docs.gradle.org/5.2.1/release-notes.html


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
 
 * **Versión 2.1**: para ver el contenido de la versión 2.1, desde la imagen en ejecución, escriba `default_versions.sh`. Esta imagen incluye las herramientas siguientes:

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

	Bienvenido a Gradle 5.4.1

	Aquí están los aspectos destacados de este release:
	 - Ejecutar compilaciones con JDK12
	 - Nueva API para tareas incrementales
	 - Actualizaciones en proyectos nativos, incluyendo soporte para Swift 5

	Para obtener más detalles, consulte https://docs.gradle.org/5.4.1/release-notes.html


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
 
 Tras la versión 2.0, las imágenes ya no incluyen `grunt` ni `python`. Puede optar por instalar
`grunt` o `python`, si es necesario.
 {: tip}

 ## Configuración de la imagen para un trabajo de conducto específico
 {: #configure_image_for_job}
 
 Por regla general no se recomienda configurar la imagen para utilizarla con trabajos de conducto individuales. Este método incrementa el esfuerzo necesario para actualizar a una nueva versión de imagen dado que debe actualizarse cada trabajo de conducto. Sin embargo, es posible que haya circunstancias bajo las cuales sea necesario configurar la imagen para un trabajo de conducto específico.
 {: important}
 
 1. En la etapa, pulse el icono **Configuración de etapa** y, a continuación, pulse **Configurar etapa**.
 2. En el separador **TRABAJOS**, pulse en el trabajo que desea modificar.
 3. La opción **Versión de imagen del conducto** muestra la versión de la imagen actual disponible, y la versión que se está utilizando para el trabajo de conducto seleccionado. Para cambiar la versión de imagen de modo que se utilice la versión actual para ejecutar el trabajo de conducto, seleccione **Más reciente**.

Para ejecutar trabajos de conducto con la imagen que ha seleccionado en la página de configuración del conducto, seleccione **Predeterminada del conducto**.
{: tip}
