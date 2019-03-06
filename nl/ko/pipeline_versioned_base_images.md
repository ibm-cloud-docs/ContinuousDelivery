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


# 버전화된 기본 이미지에 대한 작업
{: #pipeline_versioned_base_images}

{{site.data.keyword.Bluemix_notm}}용 애플리케이션을 개발할 때는 확실하게 최신 도구, 라이브러리 및 런타임을 사용하기 위해 버전화된 기본 이미지를 사용하여 파이프라인 작업을 실행할 수 있습니다. 버전화된 기본 이미지는 애플리케이션을 구성하는 요소와 애플리케이션을 배치하는 환경이 일치하도록 하는 데 도움을 줍니다. 사용자는 애플리케이션을 위한 도구, 라이브러리 및 런타임이 변경되는 시점을 제어할 수 있으며 개발 주기 중 적절하다고 생각되는 시점에 이를 업데이트할 수 있습니다. 

또한 [사용자 정의 Docker 이미지](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images)를 사용하여 애플리케이션을 빌드하고 배치하는 데 사용되는 도구와 이러한 도구의 사용되는 버전을 모두 제어할 수 있습니다. 그러나 이 방법을 사용하려면 사용자가 Docker에 대해 잘 알고 있어야 하며, 자신이 작성하는 이미지를 직접 유지보수하고 업데이트해야 합니다.
{: tip}

## 이미지 버전 지정
{: #specify_base_image_version}

1. 파이프라인 페이지에서 ![오버플로우 아이콘](images/overflow-icon-2.svg)을 클릭하여 옵션 목록에 액세스하십시오. 
2. **파이프라인 구성**을 클릭하십시오. 
3. **이미지 버전** 탭에서, 파이프라인 내 모든 작업에 사용할 기본 이미지 버전을 선택하십시오.  

`Latest` 옵션을 선택하면 파이프라인 작업이 현재 이미지 버전을 사용하여 실행됩니다. 현재 이미지 버전은 `Latest` 옵션 뒤의 대괄호 안에 표시됩니다. 새 버전이 사용 가능해지면 사용되는 이미지가 변경됩니다. 새 이미지에 포함된 새 도구를 지원하기 위해 파이프라인을 수정해야 할 수 있습니다.
{: tip}
 
 ### 이미지 버전 컨텐츠
 {: #image_version_contents}
 
 다음 이미지 버전을 사용할 수 있습니다. 

* **버전 1.0**: 이 초기 이미지는 버전화된 기본 이미지가 사용 가능해지기 전에 파이프라인 작업이 실행되었던 환경과 일치합니다. 이 이미지는 이미지가 작성되었을 때 사용 가능했으나 더 이상 업데이트되지 않은 도구의 모든 버전을 포함합니다. 새 버전의 도구에 액세스하려면 현재 이미지 버전으로 업데이트하십시오. 1.0 이미지 버전의 컨텐츠에 대한 자세한 정보는 [사전 설치된 리소스](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources)를 참조하십시오. 

* **버전 2.0**: 버전 2.0의 컨텐츠를 보려면 실행 중인 이미지에서 `default_versions.sh`를 입력하십시오. 이 이미지는 다음 도구를 포함합니다. 

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
 
 ## 특정 파이프라인 작업을 위한 이미지 구성
 {: #configure_image_for_job}
 
 일반적으로 개별 파이프라인 작업에 사용하기 위해 이미지를 구성하는 것은 좋지 않습니다. 이 방법은 사용자가 각 파이프라인 작업을 업데이트해야 하므로 새 이미지 버전으로 업그레이드하는 데 필요한 노력을 증가시킵니다. 그러나 특정 파이프라인 작업을 위해 이미지를 구성해야 하는 경우가 있을 수 있습니다.
 {: important}
 
 1. 단계에서 **단계 구성** 아이콘을 클릭한 후 **단계 구성**를 클릭하십시오.
 2. **작업** 탭에서 수정할 작업을 클릭하십시오. 
 3. **파이프라인 이미지 버전** 옵션은 사용 가능한 현재 이미지 버전과 선택된 파이프라인 작업에 대해 사용 중인 버전을 보여줍니다. 해당 파이프라인 작업을 실행하는 데 현재 버전을 사용하도록 이미지 버전을 변경하려면 **최신**을 선택하십시오. 

파이프라인 구성 페이지에서 선택한 이미지로 파이프라인 작업을 실행하려면 **파이프라인 기본값**을 선택하십시오.
{: tip}
