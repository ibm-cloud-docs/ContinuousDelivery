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


# バージョン付きベース・イメージの処理
{: #pipeline_versioned_base_images}

{{site.data.keyword.Bluemix_notm}} のアプリケーションを開発する際に、バージョン付きベース・イメージを使用してパイプライン・ジョブを実行することで、現行のツール、ライブラリー、およびランタイムが間違いなく使用されるようにすることができます。 バージョン付きベース・イメージを使用することで、アプリケーションを構成するビットとアプリケーションをデプロイする環境とを整合させることができます。 妥当であるなら、開発サイクル中に、アプリケーション用のツール、ライブラリー、またはランタイムを変更およびアップデートするタイミングをコントロールすることが可能です。

また、[カスタム Docker イメージ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images)を使用して、アプリケーションのビルドとデプロイに使用するツールの種類とバージョンの両方を制御することもできます。 ただし、そうするには Docker に精通していることが求められるだけでなく、作成するイメージの保守と更新を行うことも必要となります。
{: tip}

## イメージ・バージョンの指定
{: #specify_base_image_version}

1. 「パイプライン」ページで、![「オーバーフロー」アイコン](images/overflow-icon-2.svg)をクリックします。
2. **「パイプラインの構成」**をクリックします。
3. **「Image version (イメージ・バージョン)」**タブで、パイプライン内のすべてのジョブに使用するデフォルトのイメージ・バージョンを選択します。 

`「Latest (最新)」`オプションを選択すると、パイプライン・ジョブは現行イメージ・バージョンを使用して実行されます。 `「Latest (最新)」`オプションの後に、現行イメージ・バージョンが大括弧に囲まれて表示されます。 新しいイメージ・バージョンを使用可能になると、使用されるイメージが変更されます。 新しいイメージに新しいツールが含まれているときは、そのツールをサポートするようにパイプラインを変更することが必要になる場合もあります。
{: tip}
 
 ### イメージ・バージョンの内容
 {: #image_version_contents}
 
 次のイメージ・バージョンを使用できます。

* **バージョン 1.0**: この初期イメージは、バージョン付きベース・イメージが利用可能になる前にパイプライン・ジョブを実行していた環境と合致します。 このイメージには、イメージを作成した時点で使用可能であったツールのすべてのバージョンが含まれていますが、今後その内容が更新されることはありません。 新しいバージョンのツールを使用できるようにするには、現行イメージ・バージョンを更新する必要があります。 1.0 イメージ・バージョンの内容については詳しくは、『[あらかじめインストールされているリソース](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources)』を参照してください。

* **バージョン 2.0**: バージョン 2.0 の内容を表示するには、
実行中のイメージから `default_versions.sh` とタイプします。 このイメージには以下のツールが含まれています。

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
 
 * **バージョン 2.1**: バージョン 2.1 の内容を表示するには、実行中のイメージから `default_versions.sh` と入力します。このイメージには以下のツールが含まれています。

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
 
 バージョン 2.0 の後、イメージに `grunt` や `python` は含まれなくなりました。必要に応じて、`grunt` または `python` のインストールを選択できます。
 {: tip}

 ## 特定のパイプライン・ジョブ用のイメージの構成
 {: #configure_image_for_job}
 
 一般に、個別のパイプライン・ジョブ用に使用するイメージを構成することは推奨されていません。 新しいイメージ・バージョンにアップグレードするときに、各パイプライン・ジョブを更新しなければならなくなり、工数が増えてしまうためです。 とはいえ、特定のパイプライン・ジョブ用にイメージを構成することが必要な事情もあるかもしれません。
 {: important}
 
 1. ステージで、**「ステージ構成」**アイコンをクリックし、**「ステージの構成」**をクリックします。
 2. **「ジョブ」**タブで、変更するジョブをクリックします。
 3. **「Pipeline image version (パイプライン・イメージのバージョン)」**オプションに、
使用可能な現行イメージ・バージョンと、選択したパイプライン・ジョブに現在使用しているバージョンが表示されます。 イメージ・バージョンを変更し、現行バージョンを使用してパイプライン・ジョブを実行するには、**「Latest (最新)」**を選択します。

パイプライン構成ページで選択したイメージを使用してパイプライン・ジョブを実行するには、**「Pipeline default (パイプラインのデフォルト)」**を選択します。
{: tip}
