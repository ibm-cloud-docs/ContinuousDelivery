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


# 使用已版本化的基本映像
{: #pipeline_versioned_base_images}

为 {{site.data.keyword.Bluemix_notm}} 开发应用程序时，可以使用已版本化的基本映像来运行管道作业，以确保使用的是最新工具、库和运行时。已版本化的基本映像有助于确保构成应用程序的各部分与将应用程序部署到环境是一致的。您可以控制应用程序的工具、库或运行时何时变更，并在开发周期中合适的时候对其进行更新。

还可以使用[定制 Docker 映像](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images)来控制工具以及用于构建和部署应用程序的工具版本。但是，此方法要求您熟悉 Docker，并且必须对您所创建的映像进行维护和更新。
{: tip}

## 指定映像版本
{: #specify_base_image_version}

1. 在管道页面上，单击 ![溢出图标](images/overflow-icon-2.svg) 以访问选项列表。
2. 单击**配置管道**。
3. 在**映像版本**选项卡中，选择要用于管道中的所有作业的缺省映像版本。 

如果选择的是`最新`选项，那么将使用当前映像版本运行管道作业。当前映像版本会在`最新`选项后的方括号中显示。当有新的映像版本可用时，所使用的映像将发生更改。您可能需要修改管道以支持此新映像中包含的任何更新的工具。
{: tip}
 
 ### 映像版本内容
 {: #image_version_contents}
 
 可用的映像版本如下：

* **V1.0**：在已版本化的基本映像可用之前，这一更早版本的映像与运行管道作业的环境是相匹配的。此映像包含在创建该映像时可用的所有版本的工具，但不会再有任何更新。要访问新版本的工具，请更新到当前映像版本。有关 1.0 映像版本内容的更多信息，请参阅[预安装的资源](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources)。

* **V2.0**：要查看 V2.0 的内容，请在正在运行的映像中输入 `default_versions.sh`。此映像包含以下工具：

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
 
 * **V2.1**：要查看 V2.1 的内容，请在正在运行的映像中输入 `default_versions.sh`。此映像包含以下工具：

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
 
 在 V2.0 之后，映像不再包含 `grunt` 或 `python`。可以根据需要选择安装 `grunt` 或 `python`。
 {: tip}

 ## 为特定管道作业配置映像
 {: #configure_image_for_job}
 
 通常，建议不要将该映像配置为用于单独的管道作业。由于必须更新每个管道作业，所以此方法会增加升级到新映像版本的工作量。但是，在某些情况下可能会要求您为特定管道作业配置该映像。
 {: important}
 
 1. 在阶段上，单击**阶段配置**图标，然后单击**配置阶段**。
 2. 在**作业**选项卡中，单击要修改的作业。
 3. **管道映像版本**选项会显示当先可用的映像版本，以及用于所选管道作业的当前使用版本。要将该映像版本更改为使用当前版本来运行管道作业，请选择**最新**。

要使用在管道配置页面上选择的映像来运行管道作业，请选择**管道缺省值**。
{: tip}
