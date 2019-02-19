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


# Working with versioned base images
{: #pipeline_versioned_base_images}

When you develop applications for {{site.data.keyword.Bluemix_notm}}, you can use versioned base images to run pipeline jobs to make sure that you are using the current tools, libraries, and runtimes. Versioned base images help you to make sure that the bits that make up the application, and the environment that you deploy the application to, are consistent. You can control when the tools, libraries, or runtimes for your application change and update them when it makes sense during the development cycle.

You can also use [custom Docker images](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) to control both the tools and which versions of those tools are used to build and deploy applications. However, this method requires that you are familiar with Docker and you must maintain and update the image that you create.
{: tip}

## Specifying the image version
{: #specify_base_image_version}

1. On the Pipeline page, click ![Overflow icon](images/overflow-icon-2.svg) to access the list of options.
2. Click **Configure Pipeline**.
3. In the **Image version** tab, select the default image version to use for all jobs in your pipeline. 

If you choose the `Latest` option, the pipeline jobs are run with the current image version. The current image version is displayed in brackets after the `Latest` option. When a new image version is available, the image that is used changes. You might need to modify your pipeline to support any newer tools that are included in the new image.
{: tip}
 
 ### Image version contents
 {: #image_version_contents}
 
 The following image versions are available:

* **Version 1.0**: This earlier image matches the environment that pipeline jobs were run in before versioned base images were available. This image contains all of the versions of the tools that were available when the image was created, but it is no longer being updated. To access new versions of tools, update to the current image version. For more information about the contents of the 1.0 image version, see [Preinstalled resources](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

* **Version 2.0**: To view the contents of version 2.0, from the running image, type `default_versions.sh`. This image includes the following tools:

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
 
 ## Configuring the image for a specific pipeline job
 {: #configure_image_for_job}
 
 In general, it is not recommended to configure the image to use for individual pipeline jobs. This method increases the effort to upgrade to a new image version since you must update each pipeline job. However, there might be circumstances in which you are required to configure the image for a specific pipeline job.
 {: important}
 
 1. On the stage, click the **Stage Configuration** icon, and then click **Configure Stage**.
 2. In the **JOBS** tab, click the job that you want to modify.
 3. The **Pipeline image version** option shows the current image version that is available, and the version that you are using for the selected pipeline job. To change the image version to use the current version to run the pipeline job, select **Latest**.

To run pipeline jobs with the image that you selected on the pipeline configuration page, select **Pipeline default**.
{: tip}
