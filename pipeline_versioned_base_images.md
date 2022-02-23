---

copyright:
  years: 2019, 2022
lastupdated: "2022-02-23"

keywords: pipeline versioned base image, image version, pipeline job

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}

# Working with versioned base images
{: #pipeline_versioned_base_images}

When you develop applications for {{site.data.keyword.cloud_notm}}, you can use versioned base images to run pipeline jobs to make sure that you are using the current tools, libraries, and runtimes. Versioned base images help you to make sure that the bits that make up the application, and the environment that you deploy the application to, are consistent. You can control when the tools, libraries, or runtimes for your application change and update them when it makes sense during the development cycle.
{: shortdesc}

The existing CLI plug-in repository infrastructure for downloading and updating the CLI binary files and plug-ins is deprecated. As of 1 October, 2021, you must upgrade pipelines that use the provided pipeline base image for version 2.14 or earlier (Ubuntu) or version 3.2 or earlier (UBI) to use one of the current versioned base images. The current image for Ubuntu is version 2.15. The current image for UBI is version 3.3.
{: deprecated}

If you do not upgrade the base image that is used by your pipelines, you might receive the following error:

```text
Unable to fetch plug-ins from repository 'IBM Cloud':
invalid character '<' looking for beginning of value
```

On 16 March 2020, the {{site.data.keyword.containerlong}} released a new version 1.0 of the {{site.data.keyword.cloud_notm}} CLI plug-in. Because this version is not 100% compatible with earlier versions, you must upgrade your scripts after you start to use this version. For more information about this new version of the {{site.data.keyword.cloud_notm}} CLI plug-in, see [Big changes are coming to the {{site.data.keyword.containerlong_notm}} CLI plugin to change your experience for the better](https://www.ibm.com/cloud/blog/announcements/boost-your-productivity-with-a-new-cli-experience-for-the-ibm-cloud-kubernetes-service){: external}. To maintain compatibility with the current {{site.data.keyword.containerlong_notm}} runtimes after the new version 1.0 is available, {{site.data.keyword.contdelivery_short}} will update the current base image for the {{site.data.keyword.deliverypipeline}} to include this version. For production workloads, set any of your pipelines that are using the current base image to instead use version 2.6 until you can update your scripts to work with the new version.
{: important}

You can also use [custom Docker images](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images) to control both the tools and which versions of those tools are used to build and deploy applications. However, this method requires that you are familiar with Docker and you must maintain and update the image that you create.

On 20 November 2020, Dockerhub introduced rate-limiting on anonymous image pulls. This change might impact users that are running jobs by using Dockerhub-hosted custom images.
{: tip}

Pipeline base images are hosted in a global IBM Cloud Container Registry namespace. To list these images, run the `ibmcloud cr images --restrict continuous-delivery` command when you target the global IBM Cloud Container Registry.

## Specifying the image version
{: #specify_base_image_version}

1. On the Pipeline page, click **Actions...** to access the list of options.
2. Click **Configure Pipeline**.
3. In the **Image version** tab, select either the **Experimental: RedHat UBI** or the **Ubuntu** image type. Then, based on the selected image type, select the default image version to use for all jobs in your pipeline. You can also customize this setting for each job in each stage of your pipeline.

![Image version](images/ubi-ubuntu-vbi.png){: caption="Figure 1. Image version" caption-side="bottom"}

If you choose the `Latest` option, the pipeline jobs are run with the current image version. The current image version is displayed in brackets after the `Latest` option. When a new image version is available, the image that is used changes. You might need to modify your pipeline to support any newer tools that are included in the new image.
{: tip}

Ubuntu based versioned based images are tagged as 2.x versions. Red Hat UBI based versioned base images are tagged as 3.x versions.

To add tools in a Red Hat UBI-based image, you must use the `yum` command. `apt-get` or `apt` commands are exclusively reserved for Ubuntu images. Because of these command restrictions, you cannot update existing pipelines to use version 3.x images without modifying the scripts. {: important}
 
## Image version contents
{: #image_version_contents}
 
After version 2.0, images no longer include grunt or python. If these tools are required for your build, you can install them manually. To install grunt, run `npm install -g grunt-cli`. Make sure that you don't change the Node.js version after you install grunt. To install python on a 2.x vbi, run `apt-get -qq update && apt-get -qq install -y python`. If you are using a 3.x vbi, you can use `yum update -yq && yum install -yq python3-pip`.
{: important}

Images are available on the IBM Cloud Container Registry. To list these hosted images, run the `ibmcloud cr images --restrict continuous-delivery` command when you target the global IBM Cloud Container Registry.

| Base image version | IBM Cloud Container Registry version |
|:-----------------|:-----------------|
| 3.6 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.6`|
| 3.5 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.5`|
| 3.4 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.4`|
| 3.3 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.3`|
| 3.2 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.2`|
| 3.1 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.1`|
| 3.0 | `icr.io/continuous-delivery/pipeline/pipeline-base-ubi:3.0`|
| 2.18 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.18`|
| 2.17 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.17`|
| 2.16 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.16`|
| 2.15 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.15`|
| 2.14 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.14`|
| 2.13 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.13`|
| 2.12 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.12`|
| 2.11 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.11`|
| 2.10 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.10`|
| 2.9 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.9`|
| 2.8 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.8`|
| 2.7 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.7`| 
| 2.6 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.6`| 
| 2.5 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.5`|
| 2.4 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.4.1`|
| 2.3 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.3`|
| 2.2 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.2`|
| 2.1 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.1`|
| 2.0 | `icr.io/continuous-delivery/pipeline/pipeline-base-image:2.0`|
{: caption="Table 1. Mapping between versioned based images and IBM Cloud Registry versions" caption-side="top"}

The following available image versions are listed in descending order, starting with the current version.
 
The version of `yq` that is preinstalled in the images corresponds to the yq tool created by [Mike Farah](https://github.com/mikefarah/yq){: external}.
{: tip}

### Version 3.6
{: #version_3_6}

To view the contents of version 3.6, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image includes the following tools:

```text
# node --version
	v16.14.0

	# npm --version
	8.3.1

	# jq --version
	jq-1.6

	# yq --version
	yq (https://github.com/mikefarah/yq/) version 4.20.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.14", GitCommit:"57a3aa3f13699cf3db9c52d228c18db94fa81876", GitTreeState:"clean", BuildDate:"2021-12-15T14:52:33Z", GoVersion:"go1.15.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.3 8d2625494a6a3d413e3d875a2ff7dd9b1ed1b1a9

	# helm version --client
	version.BuildInfo{Version:"v3.8.0", GitCommit:"d14138609b01886f544b2025f5000351c9eb092e", GitTreeState:"clean", GoVersion:"go1.17.5"}

	# ibmcloud -version
	ibmcloud version 2.4.0+4ca2c74-2022-01-20T18:32:41+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	cloud-internet-services                 1.14.1             true   
	code-engine[ce]                         1.26.0             true   
	container-registry                      0.1.560            true   
	container-service[kubernetes-service]   1.0.372            false   
	cra                                     0.1.11             false   
	doi                                     0.3.3              false   
	schematics                              1.7.2              false   
	cloud-functions[wsk/functions/fn]       1.0.58             false   


	# ibmcloud dev --version
	ibmcloud dev version 2.10.1

	# java -version
	openjdk version "11.0.11" 2021-04-20
	OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
	Eclipse OpenJ9 VM AdoptOpenJDK-11.0.11+9 (build openj9-0.26.0, JRE 11 Linux amd64-64-Bit Compressed References 20210421_975 (JIT enabled, AOT enabled)
	OpenJ9   - b4cc246d9
	OMR      - 162e6f729
	JCL      - 7796c80419 based on jdk-11.0.11+9)

	# ant -version
	Apache Ant(TM) version 1.10.12 compiled on October 13 2021

	# mvn -version
	Apache Maven 3.8.4 (9b656c72d54e5bacbed989b64718c159fe39b537)
	Maven home: /opt/IBM/maven
	Java version: 11.0.11, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.15.18-200.fc35.x86_64", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.4!

	Here are the highlights of this release:
	 - Aggregated test and JaCoCo reports
	 - Marking additional test source directories as tests in IntelliJ
	 - Support for Adoptium JDKs in Java toolchains

	For more details see https://docs.gradle.org/7.4/release-notes.html


	------------------------------------------------------------
	Gradle 7.4
	------------------------------------------------------------

	Build time:   2022-02-08 09:58:38 UTC
	Revision:     f0d9291c04b90b59445041eaa75b2ee744162586

	Kotlin:       1.5.31
	Groovy:       3.0.9
	Ant:          Apache Ant(TM) version 1.10.11 compiled on July 10 2021
	JVM:          11.0.11 (Eclipse OpenJ9 openj9-0.26.0)
	OS:           Linux 5.15.18-200.fc35.x86_64 amd64


	# oc version
	Client Version: 4.9.21

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1k zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1k  FIPS 25 Mar 2021

	# make
	GNU Make 4.2.1

	# docker
	Client:
	 Version:           20.10.12
	 API version:       1.41
	 Go version:        go1.16.12
	 Git commit:        e91ed57
	 Built:             Mon Dec 13 11:40:57 2021
	 OS/Arch:           linux/amd64
	 Context:           default

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 3.5
{: #version_3_5}

To view the contents of version 3.5, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image includes the following tools:

```text
	# node --version
	v16.13.2

	# npm --version
	8.1.2

	# jq --version
	jq-1.6

	# yq --version
	yq (https://github.com/mikefarah/yq/) version 4.16.2

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.14", GitCommit:"57a3aa3f13699cf3db9c52d228c18db94fa81876", GitTreeState:"clean", BuildDate:"2021-12-15T14:52:33Z", GoVersion:"go1.15.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.3 8d2625494a6a3d413e3d875a2ff7dd9b1ed1b1a9

	# helm version --client
	version.BuildInfo{Version:"v3.7.2", GitCommit:"663a896f4a815053445eec4153677ddc24a0a361", GitTreeState:"clean", GoVersion:"go1.16.10"}

	# ibmcloud -version
	ibmcloud version 2.3.0+26fbf88-2021-12-09T17:14:46+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	cloud-internet-services                 1.14.0             true   
	code-engine[ce]                         1.24.0             true   
	container-registry                      0.1.556            true   
	container-service[kubernetes-service]   1.0.353            false   
	cra                                     0.1.11             false   
	doi                                     0.3.3              false   
	schematics                              1.7.0              false   
	cloud-functions[wsk/functions/fn]       1.0.58             false   


	# ibmcloud dev --version
	ibmcloud dev version 2.10.0

	# java -version
	openjdk version "11.0.11" 2021-04-20
	OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
	Eclipse OpenJ9 VM AdoptOpenJDK-11.0.11+9 (build openj9-0.26.0, JRE 11 Linux amd64-64-Bit Compressed References 20210421_975 (JIT enabled, AOT enabled)
	OpenJ9   - b4cc246d9
	OMR      - 162e6f729
	JCL      - 7796c80419 based on jdk-11.0.11+9)

	# ant -version
	Apache Ant(TM) version 1.10.12 compiled on October 13 2021

	# mvn -version
	Apache Maven 3.8.4 (9b656c72d54e5bacbed989b64718c159fe39b537)
	Maven home: /opt/IBM/maven
	Java version: 11.0.11, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.76-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.3.3!

	Here are the highlights of this release:
	 - Easily declare new test suites in Java projects
	 - Support for Java 17
	 - Support for Scala 3

	For more details see https://docs.gradle.org/7.3.3/release-notes.html


	------------------------------------------------------------
	Gradle 7.3.3
	------------------------------------------------------------

	Build time:   2021-12-22 12:37:54 UTC
	Revision:     6f556c80f945dc54b50e0be633da6c62dbe8dc71

	Kotlin:       1.5.31
	Groovy:       3.0.9
	Ant:          Apache Ant(TM) version 1.10.11 compiled on July 10 2021
	JVM:          11.0.11 (Eclipse OpenJ9 openj9-0.26.0)
	OS:           Linux 5.10.76-linuxkit amd64


	# oc version
	Client Version: 4.9.13

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1k zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1k  FIPS 25 Mar 2021

	# make
	GNU Make 4.2.1

	# docker
	Client:
	 Version:           20.10.11
	 API version:       1.41
	 Go version:        go1.16.10
	 Git commit:        dea9396
	 Built:             Thu Nov 18 00:34:03 2021
	 OS/Arch:           linux/amd64
	 Context:           default

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 3.4
{: #version_3_4}

To view the contents of version 3.4, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image includes the following tools:

```text
	# node --version
	v16.13.0

	# npm --version
	8.1.0

	# jq --version
	jq-1.6

	# yq --version
	yq (https://github.com/mikefarah/yq/) version 4.14.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.2 a14b4e097ae1dc7514c5febd6d75f742a166ea75

	# helm version --client
	version.BuildInfo{Version:"v3.7.1", GitCommit:"1d11fcb5d3f3bf00dbe6fe31b8412839a96b3dc4", GitTreeState:"clean", GoVersion:"go1.16.9"}

	# ibmcloud -version
	ibmcloud version 2.2.0+99934b5-2021-11-10T16:34:14+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status             Private endpoints supported   
	code-engine[ce]                         1.23.1                       true   
	container-registry                      0.1.553                      true   
	container-service[kubernetes-service]   1.0.344                      false   
	cra                                     0.1.9                        false   
	doi                                     0.3.3                        false   
	schematics                              1.6.1                        false   
	cloud-functions[wsk/functions/fn]       1.0.56                       false   
	cloud-internet-services                 1.13.6                       true   


	# ibmcloud dev --version
	ibmcloud dev version 2.9.1

	# java -version
	openjdk version "11.0.11" 2021-04-20
	OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
	Eclipse OpenJ9 VM AdoptOpenJDK-11.0.11+9 (build openj9-0.26.0, JRE 11 Linux amd64-64-Bit Compressed References 20210421_975 (JIT enabled, AOT enabled)
	OpenJ9   - b4cc246d9
	OMR      - 162e6f729
	JCL      - 7796c80419 based on jdk-11.0.11+9)

	# ant -version
	Apache Ant(TM) version 1.10.12 compiled on October 13 2021

	# mvn -version
	Apache Maven 3.8.3 (ff8e977a158738155dc465c6a97ffaf31982d739)
	Maven home: /opt/IBM/maven
	Java version: 11.0.11, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.47-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.2!

	Here are the highlights of this release:
	 - Toolchain support for Scala
	 - More cache hits when Java source files have platform-specific line endings
	 - More resilient remote HTTP build cache behavior

	For more details see https://docs.gradle.org/7.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.2
	------------------------------------------------------------

	Build time:   2021-08-17 09:59:03 UTC
	Revision:     a773786b58bb28710e3dc96c4d1a7063628952ad

	Kotlin:       1.5.21
	Groovy:       3.0.8
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.11 (Eclipse OpenJ9 openj9-0.26.0)
	OS:           Linux 5.10.47-linuxkit amd64


	# oc version
	Client Version: 4.9.7

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1k zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1k  FIPS 25 Mar 2021

	# make
	GNU Make 4.2.1

	# docker
	Client:
	 Version:           20.10.9
	 API version:       1.41
	 Go version:        go1.16.8
	 Git commit:        c2ea9bc
	 Built:             Mon Oct  4 16:03:22 2021
	 OS/Arch:           linux/amd64
	 Context:           default

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 3.3
{: #version_3_3}

To view the contents of version 3.3, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image includes the following tools:

```text
	# node --version
	v14.17.6

	# npm --version
	6.14.15

	# jq --version
	jq-1.6

	# yq --version
	yq (https://github.com/mikefarah/yq/) version 4.13.2

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.0 c8bb937807d405d92be91f06ce2629e6202ac7a9

	# helm version --client
	version.BuildInfo{Version:"v3.7.0", GitCommit:"eeac83883cb4014fe60267ec6373570374ce770b", GitTreeState:"clean", GoVersion:"go1.16.8"}

	# ibmcloud -version
	ibmcloud version 2.1.0+a4d550e-2021-09-22T13:31:04+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	cloud-functions[wsk/functions/fn]       1.0.56             false   
	cloud-internet-services                 1.13.4             true   
	container-registry                      0.1.547            true   
	container-service[kubernetes-service]   1.0.312            false   
	cra                                     0.0.9              false   
	doi                                     0.3.3              false   
	schematics                              1.6.0              false   


	# ibmcloud dev --version
	ibmcloud dev version 2.9.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.11 compiled on July 10 2021

	# mvn -version
	Apache Maven 3.8.2 (ea98e05a04480131370aa0c110b8c54cf726c06f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.47-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.2!

	Here are the highlights of this release:
	 - Toolchain support for Scala
	 - More cache hits when Java source files have platform-specific line endings
	 - More resilient remote HTTP build cache behavior

	For more details see https://docs.gradle.org/7.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.2
	------------------------------------------------------------

	Build time:   2021-08-17 09:59:03 UTC
	Revision:     a773786b58bb28710e3dc96c4d1a7063628952ad

	Kotlin:       1.5.21
	Groovy:       3.0.8
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 5.10.47-linuxkit amd64


	# oc version
	Client Version: 4.8.11

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1g zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1g FIPS  21 Apr 2020

	# make
	GNU Make 4.2.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 3.2
{: #version_3_2}

To view the contents of version 3.2, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

This image includes the following tools:

```text
	# node --version
	v14.17.6

	# npm --version
	6.14.15

	# jq --version
	jq-1.6

	# yq --version
	yq (https://github.com/mikefarah/yq/) version 4.12.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.0 c8bb937807d405d92be91f06ce2629e6202ac7a9

	# helm version --client
	version.BuildInfo{Version:"v3.6.3", GitCommit:"d506314abfb5d21419df8c7e7e68012379db2354", GitTreeState:"clean", GoVersion:"go1.16.5"}

	# ibmcloud -version
	ibmcloud version 2.0.3+c7a1126-2021-08-27T19:17:51+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	cloud-internet-services                 1.13.4             true   
	container-registry                      0.1.543            true   
	container-service[kubernetes-service]   1.0.312            false   
	doi                                     0.3.2              false   
	schematics                              1.5.12             false   
	cloud-functions[wsk/functions/fn]       1.0.56             false   


	# ibmcloud dev --version
	ibmcloud dev version 2.8.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.11 compiled on July 10 2021

	# mvn -version
	Apache Maven 3.8.2 (ea98e05a04480131370aa0c110b8c54cf726c06f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.47-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.2!

	Here are the highlights of this release:
	 - Toolchain support for Scala
	 - More cache hits when Java source files have platform-specific line endings
	 - More resilient remote HTTP build cache behavior

	For more details see https://docs.gradle.org/7.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.2
	------------------------------------------------------------

	Build time:   2021-08-17 09:59:03 UTC
	Revision:     a773786b58bb28710e3dc96c4d1a7063628952ad

	Kotlin:       1.5.21
	Groovy:       3.0.8
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 5.10.47-linuxkit amd64


	# oc version
	Client Version: 4.8.5

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1g zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1g FIPS  21 Apr 2020

	# make
	GNU Make 4.2.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 3.1
{: #version_3_1}

To view the contents of version 3.1, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

This image includes the following tools:

```text
	# node --version
	v14.17.0

	# npm --version
	6.14.13

	# jq --version
	jq-1.6

	# yq --version
	yq version 4.9.3

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.8.2 9065b18ba4633c75862befca8188de4338d9f94a

	# helm version --client
	version.BuildInfo{Version:"v3.6.0", GitCommit:"7f2df6467771a75f5646b7f12afb408590ed1755", GitTreeState:"clean", GoVersion:"go1.16.3"}

	# ibmcloud -version
	ibmcloud version 1.6.0+59b6322-2021-05-26T20:13:53+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   Private endpoints supported   
	cloud-functions/wsk/functions/fn       1.0.56             false   
	cloud-internet-services                1.13.3             true   
	container-registry                     0.1.525            true   
	container-service/kubernetes-service   1.0.275            false   
	doi                                    0.3.2              false   
	schematics                             1.5.7              false   


	# ibmcloud dev --version
	ibmcloud dev version 2.7.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.9 compiled on September 27 2020

	# mvn -version
	Apache Maven 3.8.1 (05c21c65bdfed0f71a2f2ada8b84da59348c4c5d)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.42", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.0.2!

	Here are the highlights of this release:
	 - File system watching enabled by default
	 - Support for running with and building Java 16 projects
	 - Native support for Apple Silicon processors
	 - Dependency catalog feature preview

	For more details see https://docs.gradle.org/7.0.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.0.2
	------------------------------------------------------------

	Build time:   2021-05-14 12:02:31 UTC
	Revision:     1ef1b260d39daacbf9357f9d8594a8a743e2152e

	Kotlin:       1.4.31
	Groovy:       3.0.7
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 5.10.42 amd64


	# oc version
	Unable to connect to the server: dial tcp 172.21.0.1:443: i/o timeout
	Client Version: 4.7.13

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1g zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1g FIPS  21 Apr 2020

	# make
	GNU Make 4.2.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 3.0
{: #version_3_0}

To view the contents of version 3.0, from the running image, type `default_versions.sh`. The `3.x` branch provides images with the current tool versions. The current Java&trade; version is Java&trade; 11. Node.js no longer uses `nvm` to manage different node.js versions. It provides the current LTS version of Node.js at the time that it was built.

This image includes the following tools:

```text
	# node --version
	v14.16.1

	# npm --version
	6.14.12

	# jq --version
	jq-1.6

	# yq --version
	yq version 4.6.2

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.8.2 9065b18ba4633c75862befca8188de4338d9f94a

	# helm version --client
	version.BuildInfo{Version:"v3.5.3", GitCommit:"041ce5a2c17a58be0fcd5f5e16fb3e7e95fea622", GitTreeState:"dirty", GoVersion:"go1.15.8"}

	# ibmcloud -version
	ibmcloud version 1.4.0+4705d79-2021-02-24T21:18:06+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   Private endpoints supported   
	cloud-functions/wsk/functions/fn       1.0.53             false   
	cloud-internet-services                1.13.1             false   
	container-registry                     0.1.514            false   
	container-service/kubernetes-service   1.0.233            false   
	doi                                    0.3.1              false   
	schematics                             1.5.1              false   


	# ibmcloud dev --version
	ibmcloud dev version 2.6.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.9 compiled on September 27 2020

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.19.121-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.8.3!

	Here are the highlights of this release:
	- Faster Kotlin DSL script compilation
	- Vendor selection for Java toolchains
	- Convenient execution of tasks in composite builds
	- Consistent dependency resolution

	For more details see https://docs.gradle.org/6.8.3/release-notes.html


	------------------------------------------------------------
	Gradle 6.8.3
	------------------------------------------------------------

	Build time:   2021-02-22 16:13:28 UTC
	Revision:     9e26b4a9ebb910eaa1b8da8ff8575e514bc61c78

	Kotlin:       1.4.20
	Groovy:       2.5.12
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 4.19.121-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Info-ZIP.  Maintained by C. Spieler.  Send

	# git --version
	git version 2.27.0

	# curl
	curl 7.61.1 (x86_64-redhat-linux-gnu) libcurl/7.61.1 OpenSSL/1.1.1g zlib/1.2.11 brotli/1.0.6 libidn2/2.2.0 libpsl/0.20.2 (+libidn2/2.2.0) libssh/0.9.4/openssl/zlib nghttp2/1.33.0

	# wget
	GNU Wget 1.19.5 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1g FIPS  21 Apr 2020

	# make
	GNU Make 4.2.1

	# docker
	Client: Docker Engine - Community
	Version:           19.03.9
	API version:       1.40
	Go version:        go1.13.10
	Git commit:        9d988398e7
	Built:             Fri May 15 00:22:47 2020
	OS/Arch:           linux/amd64
	Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU ed 1.14.2
```
{: codeblock}

### Version 2.18
{: #version_2_18}

To view the contents of version 2.18, from the running image, type `default_versions.sh`.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image updated its version of node.js to the current LTS version 16.14.0. If you need to use another node.js version, you can use `nvm install v<node version>` at the beginning of your script.
{: tip}

This image includes the following tools:

```text
	# node --version
	v16.14.0

	# npm --version
	8.3.1

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# yq4 --version
	yq (https://github.com/mikefarah/yq/) version 4.20.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.14", GitCommit:"57a3aa3f13699cf3db9c52d228c18db94fa81876", GitTreeState:"clean", BuildDate:"2021-12-15T14:52:33Z", GoVersion:"go1.15.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.3 8d2625494a6a3d413e3d875a2ff7dd9b1ed1b1a9

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.8.0", GitCommit:"d14138609b01886f544b2025f5000351c9eb092e", GitTreeState:"clean", GoVersion:"go1.17.5"}

	# ibmcloud -version
	ibmcloud version 2.4.0+4ca2c74-2022-01-20T18:32:41+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	doi                                     0.3.3              false   
	schematics                              1.7.2              false   
	cloud-functions[wsk/functions/fn]       1.0.58             false   
	cloud-internet-services                 1.14.1             true   
	code-engine[ce]                         1.26.0             true   
	container-registry                      0.1.560            true   
	container-service[kubernetes-service]   1.0.372            false   
	cra                                     0.1.11             false   


	# ibmcloud dev --version
	ibmcloud dev version 2.10.1

	# java -version
	openjdk version "11.0.11" 2021-04-20
	OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
	Eclipse OpenJ9 VM AdoptOpenJDK-11.0.11+9 (build openj9-0.26.0, JRE 11 Linux amd64-64-Bit Compressed References 20210421_975 (JIT enabled, AOT enabled)
	OpenJ9   - b4cc246d9
	OMR      - 162e6f729
	JCL      - 7796c80419 based on jdk-11.0.11+9)

	# ant -version
	Apache Ant(TM) version 1.10.12 compiled on October 13 2021

	# mvn -version
	Apache Maven 3.8.4 (9b656c72d54e5bacbed989b64718c159fe39b537)
	Maven home: /opt/IBM/maven
	Java version: 11.0.11, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.15.18-200.fc35.x86_64", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.4!

	Here are the highlights of this release:
	 - Aggregated test and JaCoCo reports
	 - Marking additional test source directories as tests in IntelliJ
	 - Support for Adoptium JDKs in Java toolchains

	For more details see https://docs.gradle.org/7.4/release-notes.html


	------------------------------------------------------------
	Gradle 7.4
	------------------------------------------------------------

	Build time:   2022-02-08 09:58:38 UTC
	Revision:     f0d9291c04b90b59445041eaa75b2ee744162586

	Kotlin:       1.5.31
	Groovy:       3.0.9
	Ant:          Apache Ant(TM) version 1.10.11 compiled on July 10 2021
	JVM:          11.0.11 (Eclipse OpenJ9 openj9-0.26.0)
	OS:           Linux 5.15.18-200.fc35.x86_64 amd64


	# oc version
	Client Version: 4.9.21

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.35.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client:
	 Version:           20.10.12
	 API version:       1.41
	 Go version:        go1.16.12
	 Git commit:        e91ed57
	 Built:             Mon Dec 13 11:40:57 2021
	 OS/Arch:           linux/amd64
	 Context:           default

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU Ed 1.10
```
{: codeblock}

### Version 2.17
{: #version_2_17}

To view the contents of version 2.17, from the running image, type `default_versions.sh`.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image updated its version of node.js to the current LTS version 16.13.0. If you need to keep the previous node.js version 14.17.6, you can either continue to use the previous image or you can add `nvm install v14.17.6` to the beginning of your script.
{: tip}

This image includes the following tools:

```text
	# node --version
	v16.13.0

	# npm --version
	8.1.0

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# yq4 --version
	yq (https://github.com/mikefarah/yq/) version 4.16.2

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.14", GitCommit:"57a3aa3f13699cf3db9c52d228c18db94fa81876", GitTreeState:"clean", BuildDate:"2021-12-15T14:52:33Z", GoVersion:"go1.15.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.3 8d2625494a6a3d413e3d875a2ff7dd9b1ed1b1a9

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.7.2", GitCommit:"663a896f4a815053445eec4153677ddc24a0a361", GitTreeState:"clean", GoVersion:"go1.16.10"}

	# ibmcloud -version
	ibmcloud version 2.3.0+26fbf88-2021-12-09T17:14:46+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	container-registry                      0.1.556            true   
	container-service[kubernetes-service]   1.0.353            false   
	cra                                     0.1.11             false   
	doi                                     0.3.3              false   
	schematics                              1.7.0              false   
	cloud-functions[wsk/functions/fn]       1.0.58             false   
	cloud-internet-services                 1.14.0             true   
	code-engine[ce]                         1.24.0             true   


	# ibmcloud dev --version
	ibmcloud dev version 2.10.0

	# java -version
	openjdk version "11.0.11" 2021-04-20
	OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
	Eclipse OpenJ9 VM AdoptOpenJDK-11.0.11+9 (build openj9-0.26.0, JRE 11 Linux amd64-64-Bit Compressed References 20210421_975 (JIT enabled, AOT enabled)
	OpenJ9   - b4cc246d9
	OMR      - 162e6f729
	JCL      - 7796c80419 based on jdk-11.0.11+9)

	# ant -version
	Apache Ant(TM) version 1.10.12 compiled on October 13 2021

	# mvn -version
	Apache Maven 3.8.4 (9b656c72d54e5bacbed989b64718c159fe39b537)
	Maven home: /opt/IBM/maven
	Java version: 11.0.11, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.76-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.3.3!

	Here are the highlights of this release:
	 - Easily declare new test suites in Java projects
	 - Support for Java 17
	 - Support for Scala 3

	For more details see https://docs.gradle.org/7.3.3/release-notes.html


	------------------------------------------------------------
	Gradle 7.3.3
	------------------------------------------------------------

	Build time:   2021-12-22 12:37:54 UTC
	Revision:     6f556c80f945dc54b50e0be633da6c62dbe8dc71

	Kotlin:       1.5.31
	Groovy:       3.0.9
	Ant:          Apache Ant(TM) version 1.10.11 compiled on July 10 2021
	JVM:          11.0.11 (Eclipse OpenJ9 openj9-0.26.0)
	OS:           Linux 5.10.76-linuxkit amd64


	# oc version
	Client Version: 4.9.13

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.34.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client:
	 Version:           20.10.11
	 API version:       1.41
	 Go version:        go1.16.10
	 Git commit:        dea9396
	 Built:             Thu Nov 18 00:34:03 2021
	 OS/Arch:           linux/amd64
	 Context:           default

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU Ed 1.10
```
{: codeblock}

### Version 2.16
{: #version_2_16}

To view the contents of version 2.16, from the running image, type `default_versions.sh`.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image updated its version of node.js to the current LTS version 16.13.0. If you need to keep the previous node.js version 14.17.6, you can either continue to use the previous image or you can add `nvm install v14.17.6` to the beginning of your script.
{: tip}

This image includes the following tools:

```text
	# node --version
	v16.13.0

	# npm --version
	8.1.0

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# yq4 --version
	yq (https://github.com/mikefarah/yq/) version 4.14.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.2 a14b4e097ae1dc7514c5febd6d75f742a166ea75

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.7.1", GitCommit:"1d11fcb5d3f3bf00dbe6fe31b8412839a96b3dc4", GitTreeState:"clean", GoVersion:"go1.16.9"}

	# ibmcloud -version
	ibmcloud version 2.2.0+99934b5-2021-11-10T16:34:14+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status             Private endpoints supported   
	cloud-internet-services                 1.13.6                       true   
	code-engine[ce]                         1.23.1                       true   
	container-registry                      0.1.553                      true   
	container-service[kubernetes-service]   1.0.344                      false   
	cra                                     0.1.9                        false   
	doi                                     0.3.3                        false   
	schematics                              1.6.1                        false   
	cloud-functions[wsk/functions/fn]       1.0.56                       false   


	# ibmcloud dev --version
	ibmcloud dev version 2.9.1

	# java -version
	openjdk version "11.0.11" 2021-04-20
	OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
	Eclipse OpenJ9 VM AdoptOpenJDK-11.0.11+9 (build openj9-0.26.0, JRE 11 Linux amd64-64-Bit Compressed References 20210421_975 (JIT enabled, AOT enabled)
	OpenJ9   - b4cc246d9
	OMR      - 162e6f729
	JCL      - 7796c80419 based on jdk-11.0.11+9)

	# ant -version
	Apache Ant(TM) version 1.10.12 compiled on October 13 2021

	# mvn -version
	Apache Maven 3.8.3 (ff8e977a158738155dc465c6a97ffaf31982d739)
	Maven home: /opt/IBM/maven
	Java version: 11.0.11, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.47-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.2!

	Here are the highlights of this release:
	 - Toolchain support for Scala
	 - More cache hits when Java source files have platform-specific line endings
	 - More resilient remote HTTP build cache behavior

	For more details see https://docs.gradle.org/7.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.2
	------------------------------------------------------------

	Build time:   2021-08-17 09:59:03 UTC
	Revision:     a773786b58bb28710e3dc96c4d1a7063628952ad

	Kotlin:       1.5.21
	Groovy:       3.0.8
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.11 (Eclipse OpenJ9 openj9-0.26.0)
	OS:           Linux 5.10.47-linuxkit amd64


	# oc version
	Client Version: 4.9.7

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.34.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client:
	 Version:           20.10.9
	 API version:       1.41
	 Go version:        go1.16.8
	 Git commit:        c2ea9bc
	 Built:             Mon Oct  4 16:03:22 2021
	 OS/Arch:           linux/amd64
	 Context:           default

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU Ed 1.10
```
{: codeblock}

### Version 2.15
{: #version_2_15}

To view the contents of version 2.15, from the running image, type `default_versions.sh`.

The {{site.data.keyword.cloud_notm}} command-line interface (CLI) provides code risk analysis commands. You can use the {{site.data.keyword.cloud_notm}} CLI to analyze your code for vulnerabilities and compliance with certain rules. Code Risk Analyzer is available in all {{site.data.keyword.cloud_notm}} regions where toolchains are supported. For more information about Code Risk Analyzer, see [Code Risk Analyzer plug-in](/docs/code-risk-analyzer-cli-plugin).
{: tip}

This image includes the following tools:

```text
# node --version
v14.17.6

# npm --version
6.14.15

# jq --version
jq-1.6

# yq --version
yq version 2.4.1

# yq3 --version
yq version 3.4.1

# yq4 --version
yq (https://github.com/mikefarah/yq/) version 4.13.2

# kubectl version --client
Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

# buildctl --version
buildctl github.com/moby/buildkit v0.9.0 c8bb937807d405d92be91f06ce2629e6202ac7a9

# helm version --client
Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

# helm3 version --client
version.BuildInfo{Version:"v3.7.0", GitCommit:"eeac83883cb4014fe60267ec6373570374ce770b", GitTreeState:"clean", GoVersion:"go1.16.8"}

# ibmcloud -version
ibmcloud version 2.1.0+a4d550e-2021-09-22T13:31:04+00:00

# ibmcloud plugin list
Listing installed plug-ins...

Plugin Name                             Version   Status   Private endpoints supported   
cloud-internet-services                 1.13.4             true   
container-registry                      0.1.547            true   
container-service[kubernetes-service]   1.0.312            false   
cra                                     0.0.9              false   
doi                                     0.3.3              false   
schematics                              1.6.0              false   
cloud-functions[wsk/functions/fn]       1.0.56             false   


# ibmcloud dev --version
ibmcloud dev version 2.9.0

# java -version
openjdk version "11.0.10" 2021-01-19
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
OpenJ9   - 345e1b09e
OMR      - 741e94ea8
JCL      - 0a86953833 based on jdk-11.0.10+9)

# ant -version
Apache Ant(TM) version 1.10.11 compiled on July 10 2021

# mvn -version
Apache Maven 3.8.2 (ea98e05a04480131370aa0c110b8c54cf726c06f)
Maven home: /opt/IBM/maven
Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.10.47-linuxkit", arch: "amd64", family: "unix"

# gradle -version

Welcome to Gradle 7.2!

Here are the highlights of this release:
 - Toolchain support for Scala
 - More cache hits when Java source files have platform-specific line endings
 - More resilient remote HTTP build cache behavior

For more details see https://docs.gradle.org/7.2/release-notes.html


------------------------------------------------------------
Gradle 7.2
------------------------------------------------------------

Build time:   2021-08-17 09:59:03 UTC
Revision:     a773786b58bb28710e3dc96c4d1a7063628952ad

Kotlin:       1.5.21
Groovy:       3.0.8
Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
OS:           Linux 5.10.47-linuxkit amd64


# oc version
Client Version: 4.8.11

# zip
Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
This is Zip 3.0 (July 5th 2008), by Info-ZIP.

# unzip
UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

# git --version
git version 2.17.1

# curl
curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

# wget
GNU Wget 1.19.4 built on linux-gnu.

# openssl version
OpenSSL 1.1.1  11 Sep 2018

# make
GNU Make 4.1

# docker
Client: Docker Engine - Community
 Version:           19.03.9
 API version:       1.40
 Go version:        go1.13.10
 Git commit:        9d988398e7
 Built:             Fri May 15 00:22:47 2020
 OS/Arch:           linux/amd64
 Experimental:      false

# dc --version
dc (GNU bc 1.07.1) 1.4.1

# ed --version
GNU Ed 1.10
```
{: codeblock}

### Version 2.14
{: #version_2_14}

To view the contents of version 2.14, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v14.17.6

	# npm --version
	6.14.15

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# yq4 --version
	yq (https://github.com/mikefarah/yq/) version 4.12.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.9.0 c8bb937807d405d92be91f06ce2629e6202ac7a9

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.6.3", GitCommit:"d506314abfb5d21419df8c7e7e68012379db2354", GitTreeState:"clean", GoVersion:"go1.16.5"}

	# ibmcloud -version
	ibmcloud version 2.0.3+c7a1126-2021-08-27T19:17:51+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                             Version   Status   Private endpoints supported   
	container-service[kubernetes-service]   1.0.312            false   
	doi                                     0.3.2              false   
	schematics                              1.5.12             false   
	cloud-functions[wsk/functions/fn]       1.0.56             false   
	cloud-internet-services                 1.13.4             true   
	container-registry                      0.1.543            true   


	# ibmcloud dev --version
	ibmcloud dev version 2.8.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.11 compiled on July 10 2021

	# mvn -version
	Apache Maven 3.8.2 (ea98e05a04480131370aa0c110b8c54cf726c06f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.47-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.2!

	Here are the highlights of this release:
	 - Toolchain support for Scala
	 - More cache hits when Java source files have platform-specific line endings
	 - More resilient remote HTTP build cache behavior

	For more details see https://docs.gradle.org/7.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.2
	------------------------------------------------------------

	Build time:   2021-08-17 09:59:03 UTC
	Revision:     a773786b58bb28710e3dc96c4d1a7063628952ad

	Kotlin:       1.5.21
	Groovy:       3.0.8
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 5.10.47-linuxkit amd64


	# oc version
	Client Version: 4.8.5

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.17.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU Ed 1.10
```
 {: codeblock}

### Version 2.13
{: #version_2_13}

To view the contents of version 2.13, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v14.17.0

	# npm --version
	6.14.13

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# yq4 --version
	yq version 4.9.3

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.8.2 9065b18ba4633c75862befca8188de4338d9f94a

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.6.0", GitCommit:"7f2df6467771a75f5646b7f12afb408590ed1755", GitTreeState:"clean", GoVersion:"go1.16.3"}

	# ibmcloud -version
	ibmcloud version 1.6.0+59b6322-2021-05-26T20:13:53+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   Private endpoints supported   
	cloud-internet-services                1.13.3             true   
	container-registry                     0.1.525            true   
	container-service/kubernetes-service   1.0.275            false   
	doi                                    0.3.2              false   
	schematics                             1.5.7              false   
	cloud-functions/wsk/functions/fn       1.0.56             false   


	# ibmcloud dev --version
	ibmcloud dev version 2.7.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.9 compiled on September 27 2020

	# mvn -version
	Apache Maven 3.8.1 (05c21c65bdfed0f71a2f2ada8b84da59348c4c5d)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "5.10.42", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 7.0.2!

	Here are the highlights of this release:
	 - File system watching enabled by default
	 - Support for running with and building Java 16 projects
	 - Native support for Apple Silicon processors
	 - Dependency catalog feature preview

	For more details see https://docs.gradle.org/7.0.2/release-notes.html


	------------------------------------------------------------
	Gradle 7.0.2
	------------------------------------------------------------

	Build time:   2021-05-14 12:02:31 UTC
	Revision:     1ef1b260d39daacbf9357f9d8594a8a743e2152e

	Kotlin:       1.4.31
	Groovy:       3.0.7
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 5.10.42 amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO
	error: server took too long to respond with version information.

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.17.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU Ed 1.10
```
{: codeblock}

### Version 2.12
{: #version_2_12}

To view the contents of version 2.12, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v14.16.1

	# npm --version
	6.14.12

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# yq4 --version
	yq version 4.6.2

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"20", GitVersion:"v1.20.5", GitCommit:"6b1d87acf3c8253c123756b9e61dac642678305f", GitTreeState:"clean", BuildDate:"2021-03-18T01:10:43Z", GoVersion:"go1.15.8", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.8.2 9065b18ba4633c75862befca8188de4338d9f94a

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.5.3", GitCommit:"041ce5a2c17a58be0fcd5f5e16fb3e7e95fea622", GitTreeState:"dirty", GoVersion:"go1.15.8"}

	# ibmcloud -version
	ibmcloud version 1.4.0+4705d79-2021-02-24T21:18:06+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   Private endpoints supported   
	cloud-internet-services                1.13.1             false   
	container-registry                     0.1.514            false   
	container-service/kubernetes-service   1.0.233            false   
	doi                                    0.3.1              false   
	schematics                             1.5.1              false   
	cloud-functions/wsk/functions/fn       1.0.53             false   


	# ibmcloud dev --version
	ibmcloud dev version 2.6.0

	# java -version
	openjdk version "11.0.10" 2021-01-19
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.24.0, JRE 11 Linux amd64-64-Bit Compressed References 20210120_910 (JIT enabled, AOT enabled)
	OpenJ9   - 345e1b09e
	OMR      - 741e94ea8
	JCL      - 0a86953833 based on jdk-11.0.10+9)

	# ant -version
	Apache Ant(TM) version 1.10.9 compiled on September 27 2020

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.10, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: en_US, platform encoding: UTF-8
	OS name: "linux", version: "4.19.121-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.8.3!

	Here are the highlights of this release:
	- Faster Kotlin DSL script compilation
	- Vendor selection for Java toolchains
	- Convenient execution of tasks in composite builds
	- Consistent dependency resolution

	For more details see https://docs.gradle.org/6.8.3/release-notes.html


	------------------------------------------------------------
	Gradle 6.8.3
	------------------------------------------------------------

	Build time:   2021-02-22 16:13:28 UTC
	Revision:     9e26b4a9ebb910eaa1b8da8ff8575e514bc61c78

	Kotlin:       1.4.20
	Groovy:       2.5.12
	Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
	JVM:          11.0.10 (Eclipse OpenJ9 openj9-0.24.0)
	OS:           Linux 4.19.121-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.17.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client: Docker Engine - Community
	Version:           19.03.9
	API version:       1.40
	Go version:        go1.13.10
	Git commit:        9d988398e7
	Built:             Fri May 15 00:22:47 2020
	OS/Arch:           linux/amd64
	Experimental:      false

	# dc --version
	dc (GNU bc 1.07.1) 1.4.1

	# ed --version
	GNU Ed 1.10
```
{: codeblock}

### Version 2.11
{: #version_2_11}

To view the contents of version 2.11, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v12.20.1

	# npm --version
	6.14.11

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"17+", GitVersion:"v1.17.16-rc.0", GitCommit:"737e2c461a2999fa242d39e77b9252d0eee7167e", GitTreeState:"clean", BuildDate:"2020-12-09T11:14:02Z", GoVersion:"go1.13.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.8.0 73fe4736135645a342abc7b587bba0994cccf0f9

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.4.2", GitCommit:"23dd3af5e19a02d4f4baa5b2f242645a1a3af629", GitTreeState:"clean", GoVersion:"go1.14.13"}

	# ibmcloud -version
	ibmcloud version 1.3.0+4308925-2020-12-16T07:53:49+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   Private endpoints supported   
	container-service/kubernetes-service   1.0.208            false   
	doi                                    0.2.9              false   
	schematics                             1.4.25             false   
	cloud-functions/wsk/functions/fn       1.0.49             false   
	cloud-internet-services                1.11.0             false   
	container-registry                     0.1.497            false   


	# ibmcloud dev --version
	ibmcloud dev version 2.5.1

	# java -version
	openjdk version "11.0.9" 2020-10-20
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.9+11)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.23.0, JRE 11 Linux amd64-64-Bit Compressed References 20201022_810 (JIT enabled, AOT enabled)
	OpenJ9   - 0394ef754
	OMR      - 582366ae5
	JCL      - 3b09cfd7e9 based on jdk-11.0.9+11)

	# ant -version
	Apache Ant(TM) version 1.10.9 compiled on September 27 2020

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.9, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: c.u_US, platform encoding: UTF-8
	OS name: "linux", version: "4.19.121-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.7.1!

	Here are the highlights of this release:
	 - File system watching is ready for production use
	 - Declare the version of Java your build requires
	 - Java 15 support

	For more details see https://docs.gradle.org/6.7.1/release-notes.html


	------------------------------------------------------------
	Gradle 6.7.1
	------------------------------------------------------------

	Build time:   2020-11-16 17:09:24 UTC
	Revision:     2972ff02f3210d2ceed2f1ea880f026acfbab5c0

	Kotlin:       1.3.72
	Groovy:       2.5.12
	Ant:          Apache Ant(TM) version 1.10.8 compiled on May 10 2020
	JVM:          11.0.9 (Eclipse OpenJ9 openj9-0.23.0)
	OS:           Linux 4.19.121-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.17.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false
```
{: codeblock}
 
### Version 2.10
{: #version_2_10}
 
Starting with version 2.10, the versioned base image includes a Docker client.
{: tip}

To view the contents of version 2.10, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v12.20.0

	# npm --version
	6.14.9

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# yq3 --version
	yq version 3.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"17+", GitVersion:"v1.17.16-rc.0", GitCommit:"737e2c461a2999fa242d39e77b9252d0eee7167e", GitTreeState:"clean", BuildDate:"2020-12-09T11:14:02Z", GoVersion:"go1.13.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.8.0 73fe4736135645a342abc7b587bba0994cccf0f9

	# helm version --client
	Client: &version.Version{SemVer:"v2.17.0", GitCommit:"a690bad98af45b015bd3da1a41f6218b1a451dbe", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.4.2", GitCommit:"23dd3af5e19a02d4f4baa5b2f242645a1a3af629", GitTreeState:"clean", GoVersion:"go1.14.13"}

	# ibmcloud -version
	ibmcloud version 1.2.3+3577aee6-2020-09-25T14:34:09+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.49       
	cloud-internet-services                1.11.0       
	container-registry                     0.1.497      
	container-service/kubernetes-service   1.0.206      
	doi                                    0.2.9        
	schematics                             1.4.25       


	# ibmcloud dev --version
	ibmcloud dev version 2.5.0

	# java -version
	openjdk version "11.0.9" 2020-10-20
	OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.9+11)
	Eclipse OpenJ9 VM AdoptOpenJDK (build openj9-0.23.0, JRE 11 Linux amd64-64-Bit Compressed References 20201022_810 (JIT enabled, AOT enabled)
	OpenJ9   - 0394ef754
	OMR      - 582366ae5
	JCL      - 3b09cfd7e9 based on jdk-11.0.9+11)

	# ant -version
	Apache Ant(TM) version 1.10.9 compiled on September 27 2020

	# mvn -version
	Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
	Maven home: /opt/IBM/maven
	Java version: 11.0.9, vendor: AdoptOpenJDK, runtime: /usr/local/openjdk-11
	Default locale: c.u_US, platform encoding: UTF-8
	OS name: "linux", version: "4.19.121-linuxkit", arch: "amd64", family: "unix"

	# gradle -version

	Welcome to Gradle 6.7.1!

	Here are the highlights of this release:
	 - File system watching is ready for production use
	 - Declare the version of Java your build requires
	 - Java 15 support

	For more details see https://docs.gradle.org/6.7.1/release-notes.html


	------------------------------------------------------------
	Gradle 6.7.1
	------------------------------------------------------------

	Build time:   2020-11-16 17:09:24 UTC
	Revision:     2972ff02f3210d2ceed2f1ea880f026acfbab5c0

	Kotlin:       1.3.72
	Groovy:       2.5.12
	Ant:          Apache Ant(TM) version 1.10.8 compiled on May 10 2020
	JVM:          11.0.9 (Eclipse OpenJ9 openj9-0.23.0)
	OS:           Linux 4.19.121-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

	# zip
	Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
	This is Zip 3.0 (July 5th 2008), by Info-ZIP.

	# unzip
	UnZip 6.00 of 20 April 2009, by Debian. Original by Info-ZIP.

	# git --version
	git version 2.17.1

	# curl
	curl 7.58.0 (x86_64-pc-linux-gnu) libcurl/7.58.0 OpenSSL/1.1.1 zlib/1.2.11 libidn2/2.0.4 libpsl/0.19.1 (+libidn2/2.0.4) nghttp2/1.30.0 librtmp/2.3

	# wget
	GNU Wget 1.19.4 built on linux-gnu.

	# openssl version
	OpenSSL 1.1.1  11 Sep 2018

	# make
	GNU Make 4.1

	# docker
	Client: Docker Engine - Community
	 Version:           19.03.9
	 API version:       1.40
	 Go version:        go1.13.10
	 Git commit:        9d988398e7
	 Built:             Fri May 15 00:22:47 2020
	 OS/Arch:           linux/amd64
	 Experimental:      false
```
{: codeblock}
 
### Version 2.9
{: #version_2_9}

To view the contents of version 2.9, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v12.18.3

	# npm --version
	6.14.8

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"17", GitVersion:"v1.17.11", GitCommit:"ea5f00d93211b7c80247bf607cfa422ad6fb5347", GitTreeState:"clean", BuildDate:"2020-08-13T15:20:25Z", GoVersion:"go1.13.15", Compiler:"gc", Platform:"linux/amd64"}

	# buildctl --version
	buildctl github.com/moby/buildkit v0.7.2 22e230744171b4442101731951bbbecf97796ea5

	# helm version --client
	Client: &version.Version{SemVer:"v2.16.10", GitCommit:"bceca24a91639f045f22ab0f41e47589a932cf5e", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.3.1", GitCommit:"249e5215cde0c3fa72e27eb7a30e8d55c9696144", GitTreeState:"clean", GoVersion:"go1.14.7"}

	# ibmcloud -version
	ibmcloud version 1.2.1+29ade2b-2020-09-04T12:46:49+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	schematics                             1.4.18       
	cloud-functions/wsk/functions/fn       1.0.46       
	cloud-internet-services                1.10.0       
	container-registry                     0.1.494      
	container-service/kubernetes-service   1.0.157      
	doi                                    0.2.6        


	# ibmcloud dev --version
	ibmcloud dev version 2.5.0

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

	Welcome to Gradle 6.6.1!

	Here are the highlights of this release:
	 - Experimental build configuration caching
	 - Built-in conventions for handling credentials
	 - Java compilation supports --release flag

	For more details see https://docs.gradle.org/6.6.1/release-notes.html


	------------------------------------------------------------
	Gradle 6.6.1
	------------------------------------------------------------

	Build time:   2020-08-25 16:29:12 UTC
	Revision:     f2d1fb54a951d8b11d25748e4711bec8d128d7e3

	Kotlin:       1.3.72
	Groovy:       2.5.12
	Ant:          Apache Ant(TM) version 1.10.8 compiled on May 10 2020
	JVM:          11.0.7 (Eclipse OpenJ9 openj9-0.20.0)
	OS:           Linux 4.19.76-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

```
{: codeblock}
 
### Version 2.8
{: #version_2_8}

To view the contents of version 2.8, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
	# node --version
	v12.18.2

	# npm --version
	6.14.7

	# jq --version
	jq-1.6

	# yq --version
	yq version 2.4.1

	# kubectl version --client
	Client Version: version.Info{Major:"1", Minor:"17", GitVersion:"v1.17.5", GitCommit:"e0fccafd69541e3750d460ba0f9743b90336f24f", GitTreeState:"clean", BuildDate:"2020-04-16T11:44:03Z", GoVersion:"go1.13.9", Compiler:"gc", Platform:"linux/amd64"}

	# helm version --client
	Client: &version.Version{SemVer:"v2.16.9", GitCommit:"8ad7037828e5a0fca1009dabe290130da6368e39", GitTreeState:"clean"}

	# helm3 version --client
	version.BuildInfo{Version:"v3.2.4", GitCommit:"0ad800ef43d3b826f31a5ad8dfbb4fe05d143688", GitTreeState:"clean", GoVersion:"go1.13.12"}

	# ibmcloud -version
	ibmcloud version 1.1.0+cc908fe-2020-04-29T04:06:12+00:00

	# ibmcloud plugin list
	Listing installed plug-ins...

	Plugin Name                            Version   Status   
	cloud-functions/wsk/functions/fn       1.0.44       
	cloud-internet-services                1.9.9        
	container-registry                     0.1.482      
	container-service/kubernetes-service   1.0.118      
	doi                                    0.2.5        
	schematics                             1.4.17       


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

	Welcome to Gradle 6.5.1!

	Here are the highlights of this release:
	 - Experimental file-system watching
	 - Improved version ordering
	 - New samples

	For more details see https://docs.gradle.org/6.5.1/release-notes.html


	------------------------------------------------------------
	Gradle 6.5.1
	------------------------------------------------------------

	Build time:   2020-06-30 06:32:47 UTC
	Revision:     66bc713f7169626a7f0134bf452abde51550ea0a

	Kotlin:       1.3.72
	Groovy:       2.5.11
	Ant:          Apache Ant(TM) version 1.10.7 compiled on September 1 2019
	JVM:          11.0.7 (Eclipse OpenJ9 openj9-0.20.0)
	OS:           Linux 4.19.76-linuxkit amd64


	# oc version
	oc v3.11.0+0cbc58b
	kubernetes v1.11.0+d4cacc0
	features: Basic-Auth GSSAPI Kerberos SPNEGO

```
{: codeblock}
 
### Version 2.7
{: #version_2_7}

Starting with version 2.7, the default JVM is Java&trade; 11. Java&trade; 8 was removed. If you still need Java&trade; 1.8, you can either use version 2.6 or your own custom image. Although two versions of Helm are available, the default version is 2.16.6. You can access Helm version 3.2.1 by using the `helm3` command.

To view the contents of version 2.7, from the running image, type `default_versions.sh`. This image includes the following tools:

```text
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

```text
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

```text
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

```text
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

```text
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

```text
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

```text
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

```text
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

## Configuring the image for a specific pipeline job
{: #configure_image_for_job}
 
 In general, it is not recommended to configure the image to use for individual pipeline jobs. This method increases the effort to upgrade to a new image version since you must update each pipeline job. However, there might be circumstances in which you are required to configure the image for a specific pipeline job.
 {: important}
 
1. On the stage, click the **Stage Configuration** icon, and then click **Configure Stage**.
2. In the **JOBS** tab, click the job that you want to modify.
3. The **Pipeline image version** option shows the current image version that is available, and the version that you are using for the selected pipeline job. To change the image version to use the current version to run the pipeline job, select **Latest**.

To run pipeline jobs with the image that you selected on the pipeline configuration page, select **Pipeline default**.
{: tip} 
