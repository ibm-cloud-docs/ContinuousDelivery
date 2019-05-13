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


# 使用已版本化的基礎映像檔
{: #pipeline_versioned_base_images}

當您開發 {{site.data.keyword.Bluemix_notm}} 的應用程式時，可以使用已版本化的基礎映像檔來執行管線工作，以確定您使用最新的工具、程式庫和運行環境。已版本化的基礎映像檔有助於您確定構成應用程式的各部分，以及您將應用程式部署到的環境，兩者是一致的。您可以控制應用程式的工具、程式庫或運行環境何時變更，並且在開發週期中有意義的時間更新它們。

您也可以使用[自訂 Docker 映像檔](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images)來控制工具和那些工具的哪些版本要用於建置及部署應用程式。不過，這種方法需要您熟悉
Docker，且您必須維護和更新您建立的映像檔。
{: tip}

## 指定映像檔版本
{: #specify_base_image_version}

1. 在「管線」頁面上，按一下 ![概觀圖示](images/overflow-icon-2.svg) 以存取選項清單。
2. 按一下**配置管線**。
3. 在**映像檔版本**標籤中，選取要用於您管線中所有工作的預設映像檔版本。 

如果您選擇 `Latest` 選項，管線工作會使用現行映像檔版本來執行。現行映像檔版本顯示於 `Latest` 選項之後的方括弧中。有新的映像檔版本可用時，使用的映像檔會變更。您可能需要修改管線，以支援新映像檔中包含的任何較新工具。
{: tip}
 
 ### 映像檔版本內容
 {: #image_version_contents}
 
 以下是可用的映像檔版本：

* **1.0 版**：這個較早的映像檔符合管線工作是在已版本化基礎映像檔可用之前執行的環境。這個映像檔包含當映像檔建立時可用的所有工具版本，但它已不再更新。若要存取新版本的工具，請更新為現行映像檔版本。如需 1.0 映像檔版本內容的相關資訊，請參閱[預先安裝的資源](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources)。

* **2.0 版**：若要檢視 2.0 版的內容，請從執行中的映像檔，鍵入 `default_versions.sh`。這個映像檔包含下列工具：

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
 
 ## 配置特定管線工作的映像檔
 {: #configure_image_for_job}
 
 一般而言，不建議為個別管線工作配置要使用的映像檔。這個方法會增加升級至新映像檔版本的工作量，因為您必須更新每個管線工作。不過，可能會有些情況下您必須為特定管線工作配置映像檔。
 {: important}
 
 1. 在階段上，按一下**階段配置**圖示，然後按一下**配置階段**。
 2. 在**工作**標籤，按一下您要修改的工作。
 3. **管線映像檔版本**選項會顯示可用的現行映像檔版本，以及您正用於所選管線工作的版本。若要將映像檔版本變更為使用現行版本來執行管線工作，請選取 **Latest**。

若要使用您在管線配置頁面上選取的映像檔來執行管線工作，請選取 **Pipeline default**。
{: tip}
