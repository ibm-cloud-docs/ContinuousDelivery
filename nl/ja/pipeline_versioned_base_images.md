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
	v10.15.1
	
	# npm --version
	6.4.1
	
	# jq --version
	jq-1.6
	
	# kubectl version
	Client Version: version.Info{Major:"1", Minor:"12", GitVersion:"v1.12.2", GitCommit:"17c77c7898218073f14c8d573582e8d2313dc740", GitTreeState:"clean", BuildDate:"2018-10-24T06:54:59Z", GoVersion:"go1.10.4", Compiler:"gc", Platform:"linux/amd64"}
	サーバー localhost:8080 への接続は拒否され、「did you specify the right host or port? (正しいホストまたはポートを指定しましたか)」のメッセージが返されます
	
	# helm version --client
	Client: &version.Version{SemVer:"v2.12.3", GitCommit:"eecf22f77df5f65c823aacd2dbd30ae6c65f186e", GitTreeState:"clean"}
	
	# ibmcloud -version
	ibmcloud version 0.13.1+0536e96-2018-12-20T10:00:05+00:00
	
	# ibmcloud plugin list
	Listing installed plug-ins...
	
	プラグイン名                           バージョン   状況
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
