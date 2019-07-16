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


# Trabalhando com imagens base com versão
{: #pipeline_versioned_base_images}

Ao desenvolver aplicativos para o {{site.data.keyword.Bluemix_notm}}, é possível usar imagens base com versão para executar tarefas de pipeline para garantir que você esteja usando as ferramentas, bibliotecas e tempos de execução atuais. As imagens base com versão ajudam você a garantir que os bits que compõem o aplicativo e o ambiente no qual você implementa o aplicativo sejam consistentes. É possível controlar quando as ferramentas, as bibliotecas ou os tempos de execução de seu aplicativo mudam e atualizá-los, quando necessário, durante o ciclo de desenvolvimento.

Também é possível usar [imagens customizadas do Docker](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) para controlar as ferramentas e quais versões dessas ferramentas são usadas para criar e implementar aplicativos. No entanto, esse método exige que você esteja familiarizado com o Docker e mantenha e atualize a imagem criada.
{: tip}

## Especificando a versão da imagem
{: #specify_base_image_version}

1. Na página Pipeline, clique em ![Ícone de estouro](images/overflow-icon-2.svg) para acessar a lista de opções.
2. Clique em **Configurar Pipeline**.
3. Na guia **Versão da imagem**, selecione a versão padrão da imagem a ser usada para todas as tarefas em seu pipeline. 

Ao escolher a opção `Mais Recente`, as tarefas do pipeline são executadas com a versão atual da imagem. A versão atual da imagem é exibida entre colchetes após a opção `Mais Recente`. Quando uma nova versão de imagem estiver disponível, a imagem usada mudará. Pode ser necessário modificar seu pipeline para suportar quaisquer ferramentas mais recentes incluídas na nova imagem.
{: tip}
 
 ### Conteúdo da versão da imagem
 {: #image_version_contents}
 
 As seguintes versões de imagem estão disponíveis:

* **Versão 1.0**: essa imagem anterior corresponde ao ambiente no qual as tarefas de pipeline foram executadas antes que as imagens base com versão estivessem disponíveis. Essa imagem contém todas as versões das ferramentas que estavam disponíveis quando a imagem foi criada, mas não está mais sendo atualizada. Para acessar novas versões de ferramentas, atualize para a versão atual da imagem. Para obter mais informações sobre o conteúdo da versão da imagem 1.0, consulte [Recursos pré-instalados](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

* **Versão 2.0**: para visualizar os conteúdos da versão 2.0, na imagem em execução, digite `default_versions.sh`. Essa imagem inclui as seguintes ferramentas:

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
 
 * **Versão 2.1**: para visualizar o conteúdo da versão 2.1, na imagem em execução, digite `default_versions.sh`. Essa imagem inclui as seguintes ferramentas:

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
 
 Após a versão 2.0, as imagens não incluem mais `grunt` nem `python`. É possível optar por instalar `grunt` ou `python`, se necessário.
 {: tip}

 ## Configurando a imagem para uma tarefa de pipeline específica
 {: #configure_image_for_job}
 
 Em geral, não é recomendável configurar a imagem para o uso em tarefas de pipeline individuais. Esse método aumenta a necessidade de upgrade para uma nova versão da imagem, pois deve-se atualizar cada tarefa de pipeline. No entanto, pode haver circunstâncias nas quais seja necessário configurar a imagem para uma tarefa de pipeline específica.
 {: important}
 
 1. No estágio, clique no ícone **Configuração do estágio** e, em seguida, clique em **Configurar estágio**.
 2. Na guia **JOBS**, clique na tarefa que deseja modificar.
 3. A opção **Versão da imagem de pipeline** mostra a versão atual disponível da imagem, além da versão sendo usada para a tarefa de pipeline selecionada. Para mudar a versão da imagem e usar a versão atual para executar a tarefa de pipeline, selecione **Mais Recente**.

Para executar tarefas de pipeline com a imagem selecionada na página de configuração de pipeline, selecione **Padrão de pipeline**.
{: tip}
