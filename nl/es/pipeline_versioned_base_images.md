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

* **Versión 2.0**: Para ver el contenido de la versión 2.0, desde la imagen en ejecución, escriba `default_versions.sh`. Esta imagen incluye las herramientas siguientes:

```
	# node --version
	v10.15.1
	
	# npm --version
	6.4.1
	
	# jq --version
	jq-1.6
	
	# kubectl version
	Versión de cliente: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	La conexión al servidor localhost:8080 se ha rechazado; ¿ha especificado el host y puerto correctos?
	
	# helm version --client
	Cliente: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}
	
	# ibmcloud -version
	ibmcloud versión 0.13.1+0536e96-2018-12-20T10:00:05+00:00
	
	# ibmcloud plugin list
	Lista de los plug-ins instalados...
	
	Nombre del plug-in                     Versión   Estado
	cloud-functions/wsk/functions/fn       1.0.29
	container-registry                     0.1.365
	container-service/kubernetes-service   0.2.44       
	
	# java -version
	java versión "1.8.0_191"
	Java(TM) SE Runtime Environment (build 8.0.5.27 - pxa6480sr5fp27-20190104_01(SR5 FP27))
	IBM J9 VM (build 2.9, JRE 1.8.0 Linux amd64-64-Bit Compressed References 20181219_405297 (JIT enabled, AOT enabled)
	OpenJ9   - 3f2d574
	OMR      - 109ba5b
	IBM      - e2996d1)
	JCL - 20190104_01 basado en Oracle jdk8u191-b26
	
	# ant -version
	Apache Ant(TM) versión 1.10.5 compilado el 10 de julio de 2018
	
	# mvn -version
	Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_191, vendor: IBM Corporation, runtime: /opt/IBM/java8/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.4.0-141-generic", arch: "amd64", family: "unix"
	
	# gradle -version
	
	¡Bienvenidos a Gradle 5.2!
	
	Aquí están los aspectos destacados de este release:
	 - Definir conjuntos de dependencias que funcionan conjuntamente con el plug-in de Java Platform
	 - Nuevos plug-ins de C++ con gestión incorporada de dependencias
	 - Nuevos tipos de proyecto de C++ para gradle init
	 - Inyección de servicios en plug-in y extensiones de proyecto
	
	Para obtener más detalles consulte https://docs.gradle.org/5.2/release-notes.html
	
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
 
 ## Configuración de la imagen para un trabajo de conducto específico
 {: #configure_image_for_job}
 
 Por regla general no se recomienda configurar la imagen para utilizarla con trabajos de conducto individuales. Este método incrementa el esfuerzo necesario para actualizar a una nueva versión de imagen dado que debe actualizarse cada trabajo de conducto. Sin embargo, es posible que haya circunstancias bajo las cuales sea necesario configurar la imagen para un trabajo de conducto específico.
 {: important}
 
 1. En la etapa, pulse el icono **Configuración de etapa** y, a continuación, pulse **Configurar etapa**.
 2. En el separador **TRABAJOS**, pulse en el trabajo que desea modificar.
 3. La opción **Versión de imagen del conducto** muestra la versión de la imagen actual disponible, y la versión que se está utilizando para el trabajo de conducto seleccionado. Para cambiar la versión de imagen de modo que se utilice la versión actual para ejecutar el trabajo de conducto, seleccione **Más reciente**.

Para ejecutar trabajos de conducto con la imagen que ha seleccionado en la página de configuración del conducto, seleccione **Predeterminada del conducto**.
{: tip}
