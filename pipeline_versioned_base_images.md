---

Copyright:
  years: 2019, 2020
lastupdated: "2020-05-21"

keywords: pipeline versioned base image, image version, pipeline job

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

# Working with versioned base images
{: #pipeline_versioned_base_images}

When you develop applications for {{site.data.keyword.Bluemix_notm}}, you can use versioned base images to run pipeline jobs to make sure that you are using the current tools, libraries, and runtimes. Versioned base images help you to make sure that the bits that make up the application, and the environment that you deploy the application to, are consistent. You can control when the tools, libraries, or runtimes for your application change and update them when it makes sense during the development cycle.

As of 16 March 2020, the {{site.data.keyword.containerlong}} is releasing a new version 1.0 of the {{site.data.keyword.cloud_notm}} CLI plug-in. Because this version is not 100% compatible with earlier versions, you must upgrade your scripts after you start to use this version. For more information about this new version of the {{site.data.keyword.cloud_notm}} CLI plug-in, see [Big changes are coming to the {{site.data.keyword.containerlong_notm}} CLI plugin to change your experience for the better](https://www.ibm.com/cloud/blog/announcements/boost-your-productivity-with-a-new-cli-experience-for-the-ibm-cloud-kubernetes-service){: external}. To maintain compatibility with the current {{site.data.keyword.containerlong_notm}} runtimes after the new version 1.0 is available, {{site.data.keyword.contdelivery_short}} will update the current base image for the {{site.data.keyword.deliverypipeline}} to include this version. For production workloads, set any of your pipelines that are using the current base image to instead use version 2.6 until you can update your scripts to work with the new version.
{: important}

You can also use [custom Docker images](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) to control both the tools and which versions of those tools are used to build and deploy applications. However, this method requires that you are familiar with Docker and you must maintain and update the image that you create.
{: tip}

## Specifying the image version
{: #specify_base_image_version}

1. On the Pipeline page, click ![Overflow icon](images/overflow-icon-2.svg) to access the list of options.
2. Click **Configure Pipeline**.
3. In the **Image version** tab, select the default image version to use for all jobs in your pipeline. 

If you choose the `Latest` option, the pipeline jobs are run with the current image version. The current image version is displayed in brackets after the `Latest` option. When a new image version is available, the image that is used changes. You might need to modify your pipeline to support any newer tools that are included in the new image.
{: tip}
 
 ## Image version contents
 {: #image_version_contents}
 
 After version 2.0, images no longer include grunt or python. If these tools are required for your build, you can install them manually. To install grunt, run `npm install -g grunt-cli`. Make sure that you don't change the Node.js version after you install grunt. To install python, run `apt-get -qq update && apt-get -qq install -y python`.
 {: important}

Starting with version 2.2, images are available on [DockerHub](https://hub.docker.com/){: external}.

| Base image version | DockerHub image version |
|:-----------------|:-----------------|
| 2.7 | `ibmcom/pipeline-base-image:2.7`| 
| 2.6 | `ibmcom/pipeline-base-image:2.6`| 
| 2.5 | `ibmcom/pipeline-base-image:2.5`|
| 2.4 | `ibmcom/pipeline-base-image:2.4.1`|
| 2.3 | `ibmcom/pipeline-base-image:2.3`|
| 2.2 | `ibmcom/pipeline-base-image:2.2`|
| 2.1 | Not available |
| 2.0 | Not available |
| 1.0 | Not available |
{: caption="Table 1. Mapping between versioned based images and DockerHub images" caption-side="top"}

To access the DockerHub versioned base images, go to [ibmcom/pipeline-base-image](https://hub.docker.com/r/ibmcom/pipeline-base-image){: external}.

The following available image versions are listed in descending order, starting with the current version.
 
 The version of `yq` that is preinstalled in the images corresponds to the yq tool created by [Mike Farah](https://github.com/mikefarah/yq){: external}.
 {: tip}
 
 ### Version 2.7
 {: #version_2_7}

Starting with version 2.7, the default JVM is Java&trade; 11. Java&trade; 8 was removed. If you still need Java&trade; 1.8, you can either use version 2.6 or your own custom image. Although two versions of Helm are available, the default version is 2.16.6. You can access Helm version 3.2.1 by using the `helm3` command.

To view the contents of version 2.7, from the running image, type `default_versions.sh`. This image includes the following tools:

```
	# node --version
	v12.16.3

	# npm --version
	6.14.4

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"17", GitVersion:"v1.17.5", GitCommit:"e0fccafd69541e3750d460ba0f9743b90336f24f", GitTreeState:"clean", BuildDate:"2020-04-16T11:44:03Z", GoVersion:"go1.13.9", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.16.6", GitCommit:"dd2e5695da88625b190e6b22e9542550ab503a47", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.2.1", GitCommit:"fe51cd1e31e6a202cba7dead9552a6d418ded79a", GitTreeState:"clean", GoVersion:"go1.13.10"}

	# ibmcloud -version
	ibmcloud version 1.1.0+cc908fe-2020-04-29T04:06:12+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	schematics                             1.4.10       
	cloud-functions/wsk/functions/fn       1.0.39       
	cloud-internet-services                1.9.7        
	container-registry                     0.1.471      
	container-service/kubernetes-service   1.0.57       
	doi                                    0.2.1        


	# ibmcloud dev --version
	ibmcloud dev version 2.4.8

	# java -version
	openjdk version "11.0.7" 2020-04-14
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.7+10)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.20.0, JRE 11 Linux amd64-64-Bit Compressed References 20200416_574 (JIT enabled, AOT enabled)
	OpenJ9   - 05fa2d361
	OMR      - d4365f371
	JCL      - 838028fc9d based on jdk-11.0.7+10)

	# ant -version
	Apache Ant(TM) version 1.10.8 compiled on May 10 2020

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.7, vendor: Eclipse OpenJ9, runtime: /usr/local/openjdk-11
	Default locale: c.u_US, platform encoding: UTF-8
	OS name: "linux", version: "4.19.76-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.4!

	Here are the highlights of this release:
	 - Support for building, testing and running Java Modules
	 - Precompiled script plugins for Groovy DSL
	 - Single dependency lock file per project

	For more details see https://docs.gradle.org/6.4/release-notes.html


	------------------------------------------------------------
	Gradle 6.4
	------------------------------------------------------------

	Build time:   2020-05-05 19:18:55 UTC
	Revision:     42f7c3d0c3066b7b38bd0726760d4881e86fd19f

	Kotlin:       1.3.71
	Groovy:       2.5.10
	Ant:          Apache Ant(TM) version 1.10.7 compiled on September 1 2019
	JVM:          11.0.7 (Eclipse OpenJ9 openj9-0.20.0)
	OS:           Linux 4.19.76-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

  ```
 {: codeblock}
 
 ### Version 2.6
 {: #version_2_6}
 
To view the contents of version 2.6, from the running image, type `default_versions.sh`. This image includes the following tools:

```
	# node --version
	v12.13.0

	# npm --version
	6.12.0

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"16", GitVersion:"v1.16.2", GitCommit:"c97fe5036ef3df2967d086711e6c0c405941e14b", GitTreeState:"clean", BuildDate:"2019-10-15T19:18:23Z", GoVersion:"go1.12.10", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.16.0", GitCommit:"e13bc94621d4ef666270cfbe734aaabf342a49bb", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.20.0+5d69177-2019-10-31T07:15:05+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	container-registry                     0.1.437      
	container-service/kubernetes-service   0.4.61       
	doi                                    0.1.5        
	schematics                             1.4.2        
	cloud-functions/wsk/functions/fn       1.0.36       


	# java -version
	openjdk version "1.8.0_222"
	OpenJDK Runtime Environment (build 1.8.0_222-8u222-b10-1ubuntu1~16.04.1-b10)
	OpenJDK 64-Bit Server VM (build 25.222-b10, mixed mode)

	# ant -version
	Apache Ant(TM) version 1.10.7 compiled on September 1 2019

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_222, vendor: Private Build, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.9.184-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.0.1!

	Here are the highlights of this release:
	 - Substantial improvements in dependency management, including
	   - Publishing Gradle Module Metadata in addition to pom.xml
	   - Advanced control of transitive versions
	   - Support for optional features and dependencies
	   - Rules to tweak published metadata
	 - Support for Java 13
	 - Faster incremental Java and Groovy compilation
	 - New Zinc compiler for Scala
	 - VS2019 support
	 - Support for Gradle Enterprise plugin 3.0

	For more details see https://docs.gradle.org/6.0.1/release-notes.html


	------------------------------------------------------------
	Gradle 6.0.1
	------------------------------------------------------------

	Build time:   2019-11-18 20:25:01 UTC
	Revision:     fad121066a68c4701acd362daf4287a7c309a0f5

	Kotlin:       1.3.50
	Groovy:       2.5.8
	Ant:          Apache Ant(TM) version 1.10.7 compiled on September 1 2019
	JVM:          1.8.0_222 (Private Build 25.222-b10)
	OS:           Linux 4.9.184-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO
  ```
 {: codeblock}
 
 ### Version 2.5
 {: #version_2_5}
 
To view the contents of version 2.5, from the running image, type `default_versions.sh`. This image includes the following tools:

```
	# node --version
	v12.13.0

	# npm --version
	6.12.0

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"16", GitVersion:"v1.16.2", GitCommit:"c97fe5036ef3df2967d086711e6c0c405941e14b", GitTreeState:"clean", BuildDate:"2019-10-15T19:18:23Z", GoVersion:"go1.12.10", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.16.0", GitCommit:"e13bc94621d4ef666270cfbe734aaabf342a49bb", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.20.0+5d69177-2019-10-31T07:15:05+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.36       
	container-registry                     0.1.437      
	container-service/kubernetes-service   0.4.61       
	doi                                    0.1.5        


	# java -version
	openjdk version "1.8.0_222"
	OpenJDK Runtime Environment (build 1.8.0_222-8u222-b10-1ubuntu1~16.04.1-b10)
	OpenJDK 64-Bit Server VM (build 25.222-b10, mixed mode)

	# ant -version
	Apache Ant(TM) version 1.10.7 compiled on September 1 2019

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_222, vendor: Private Build, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.9.184-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.0.1!

	Here are the highlights of this release:
	 - Substantial improvements in dependency management, including
	   - Publishing Gradle Module Metadata in addition to pom.xml
	   - Advanced control of transitive versions
	   - Support for optional features and dependencies
	   - Rules to tweak published metadata
	 - Support for Java 13
	 - Faster incremental Java and Groovy compilation
	 - New Zinc compiler for Scala
	 - VS2019 support
	 - Support for Gradle Enterprise plugin 3.0

	For more details see https://docs.gradle.org/6.0.1/release-notes.html


	------------------------------------------------------------
	Gradle 6.0.1
	------------------------------------------------------------

	Build time:   2019-11-18 20:25:01 UTC
	Revision:     fad121066a68c4701acd362daf4287a7c309a0f5

	Kotlin:       1.3.50
	Groovy:       2.5.8
	Ant:          Apache Ant(TM) version 1.10.7 compiled on September 1 2019
	JVM:          1.8.0_222 (Private Build 25.222-b10)
	OS:           Linux 4.9.184-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO
  ```
 {: codeblock}
 
  ### Version 2.4
 {: #version_2_4}
   
To view the contents of version 2.4, from the running image, type `default_versions.sh`. This image includes the following tools:

```
	# node --version
	v10.16.3

	# npm --version
	6.9.0

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.0

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"15", GitVersion:"v1.15.3", GitCommit:"2d3c76f9091b6bec110a5e63777c332469e0cba2", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:54Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.14.3", GitCommit:"0e7f3b6637f7af8fcfddb3d2941fcc7cbebb0085", GitTreeState:"clean"}

	# ibmcloud -version
	ibmcloud version 0.18.1+09d36ed-2019-08-19T08:23:11+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	doi                                    0.1.5        
	cloud-functions/wsk/functions/fn       1.0.32       
	container-registry                     0.1.404	
	container-service/kubernetes-service   0.4.3        


	# java -version
	openjdk version "1.8.0_222"
	OpenJDK Runtime Environment (build 1.8.0_222-8u222-b10-1ubuntu1~16.04.1-b10)
	OpenJDK 64-Bit Server VM (build 25.222-b10, mixed mode)

	# ant -version
	Apache Ant(TM) version 1.10.6 compiled on May 2 2019

	# mvn -version
	Apache Maven 3.6.1 (d66c9c0b3152b2e69ee9bac180bb8fcc8e6af555; 2019-04-04T19:00:29Z)
	Maven home: /opt/IBM/maven
	Java version: 1.8.0_222, vendor: Private Build, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.9.184-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 5.6!

	Here are the highlights of this release:
	 - Incremental Groovy compilation
	 - Groovy compile avoidance
	 - Test fixtures for Java projects
	 - Manage plugin versions via settings script

	For more details see https://docs.gradle.org/5.6/release-notes.html


	------------------------------------------------------------
	Gradle 5.6
	------------------------------------------------------------

	Build time:   2019-08-14 21:05:25 UTC
	Revision:     f0b9d60906c7b8c42cd6c61a39ae7b74767bb012

	Kotlin:       1.3.41
	Groovy:       2.5.4
	Ant:          Apache Ant(TM) version 1.9.14 compiled on March 12 2019
	JVM:          1.8.0_222 (Private Build 25.222-b10)
	OS:           Linux 4.9.184-linuxkit amd64
	
	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

  ```
 {: codeblock}
 
  ### Version 2.3
 {: #version_2_3}
 
 To view the contents of version 2.3, from the running image, type `default_versions.sh`. This image includes the following tools:

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
	ibmcloud version 0.16.3+68cb57c-2019-06-20T08:59:16+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.32       
	container-registry                     0.1.395  
	container-service/kubernetes-service   0.3.58  
	doi                                    0.1.3   


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
	OS name: "linux", version: "4.9.184-linuxkit", arch: "amd64", family: "unix"

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
	OS:           Linux 4.9.184-linuxkit amd64

  ```
 {: codeblock}

 ### Version 2.2
 {: #version_2_2}

To view the contents of version 2.2, from the running image, type `default_versions.sh`. This image includes the following tools:

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
	ibmcloud version 0.16.3+68cb57c-2019-06-20T08:59:16+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.32       
	container-registry                     0.1.395  
	container-service/kubernetes-service   0.3.58 
	doi                                    0.1.3  


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
	OS name: "linux", version: "4.9.184-linuxkit", arch: "amd64", family: "unix"

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
	OS:           Linux 4.9.184-linuxkit amd64

  ```
 {: codeblock} 
 
 ### Version 2.1
 {: #version_2_1}

To view the contents of version 2.1, from the running image, type `default_versions.sh`. This image includes the following tools:

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

  ### Version 2.0
 {: #version_2_0}
 
 To view the contents of version 2.0, from the running image, type `default_versions.sh`. This image includes the following tools:

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

 ### Version 1.0
 {: #version_1_0}

This earlier image matches the environment that pipeline jobs were run in before versioned base images were available. This image contains all of the versions of the tools that were available when the image was created, but it is no longer being updated. To access new versions of tools, update to the current image version. For more information about the contents of the 1.0 image version, see [Preinstalled resources](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).
 
 ## Configuring the image for a specific pipeline job
 {: #configure_image_for_job}
 
 In general, it is not recommended to configure the image to use for individual pipeline jobs. This method increases the effort to upgrade to a new image version since you must update each pipeline job. However, there might be circumstances in which you are required to configure the image for a specific pipeline job.
 {: important}
 
 1. On the stage, click the **Stage Configuration** icon, and then click **Configure Stage**.
 2. In the **JOBS** tab, click the job that you want to modify.
 3. The **Pipeline image version** option shows the current image version that is available, and the version that you are using for the selected pipeline job. To change the image version to use the current version to run the pipeline job, select **Latest**.

To run pipeline jobs with the image that you selected on the pipeline configuration page, select **Pipeline default**.
{: tip}
