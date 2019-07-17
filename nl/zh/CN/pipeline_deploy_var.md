---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-28"

keywords: Environment properties, IBM Java, pipeline environments

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 环境属性和资源
{: #deliverypipeline_environment}

缺省情况下，可以在管道环境中使用下列属性和资源。

<!--##Contents
* [Environment properties](#env)
    * [General purpose properties](#gen)
    * [Runtime and tool properties](#runtime)
    * [Deployment properties](#deployment)
* [Pre-installed resources](#resources)
    * [Runtimes and tools](#tools)
    * [Node modules](#node)-->

## 环境属性
{: #deliverypipeline_envprop}

### 一般用途属性
下表列出并描述了缺省情况下在管道环境中可用的每个通用环境属性。

|环境属性|描述|
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
|ARCHIVE_DIR|用于归档或下载归档的目录。|
|BUILD_ID|当前作业执行的唯一标识。|
|BUILD_DISPLAY_NAME|BUILD_ID 值，前缀为“#”。|
|BUILD_NUMBER|显示在管道 UI 中的递增阶段标识。|
|GIT_BRANCH|被作业用作输入的 Git 分支。此属性仅在将 Git 存储库用作输入的作业中可用。|
|GIT_COMMIT|被作业用作输入的 Git 落实。此属性仅在将 Git 存储库用作输入的作业中可用。|
|GIT_PREVIOUS_COMMIT|作业上一次成功运行的 Git 落实值。此属性仅在将 Git 存储库用作输入的作业中可用。|
|GIT_URL|被作业用作输入的 Git 存储库 URL。此属性仅在将 Git 存储库用作输入的作业中可用。|
|IDS_JOB_ID|作业配置的唯一标识。|
|IDS_JOB_NAME|作业配置的名称。|
|IDS_OUTPUT_PROPS|以逗号分隔的阶段环境属性的名称。|
|IDS_PROJECT_NAME|项目的名称，例如，<code>所有者 - 项目名称</code>。|
|IDS_STAGE_NAME|当前阶段的名称。|
|IDS_URL|当前管道的 URL。|
|IDS_VERSION|要部署的构建的编号，或者 SCM 标识。此属性仅可用于部署作业。
|JOB_NAME|当前管道上下文中的唯一作业标识。|
|PIPELINE_ARTIFACT_URL|在当前构建作业完成后可用于下载该作业的工件的 URL。您必须使用有效的不记名令牌才能访问这些工件。|
|PIPELINE_INITIAL_STAGE_EXECUTION_ID|管道运行的唯一标识。|
|PIPELINE_KUBERNETES_CLUSTER_NAME|在当前作业中选择的 Kubernetes 集群的名称。|
|PIPELINE_LOG_URL|在当前作业完成后可用于下载该作业的日志文件的 URL。您必须使用有效的不记名令牌才能访问这些日志文件。|
|PIPELINE_STAGE_INPUT_JOB_ID|作为当前阶段输入的作业的标识。|
|PIPELINE_STAGE_INPUT_REV|当前阶段的输入的修订版。|
| PIPELINE_TRIGGERING_USER |管道作业的当前用户|
|TASK_ID|作业当前运行的唯一标识。|
|TMPDIR|存储临时文件的目录位置。|
|WORKSPACE|当前工作目录的路径。|
{: caption="表 1. 通用环境属性" caption-side="top"}

### 运行时和工具属性
下表列出并描述了缺省情况下在管道环境中可用的每个运行时和工具环境属性。

|环境属性|描述|
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
|ANT_HOME|Apache Ant 1.9.2 的路径。|
|ANT_JAVA8_HOME|需要 Java 8 的 Apache Ant 1.10 以上版本的路径。|
|GRADLE_HOME|Gradle 1.11 的路径。|
|JAVA_HOME|IBM&reg; Java&trade; 7 的路径。|
|JAVA7_HOME|IBM Java 7 的路径。|
|JAVA8_HOME|IBM Java 8 的路径。|
|MAVEN_HOME|Apache Maven 3.2.1 的路径。|
|NODE_HOME|Node.js 0.10.29 的路径。|
{: caption="表 2. 运行时和工具环境属性" caption-side="top"}

要在管道脚本中使用 Apache Ant 1.10+，请将 `ANT_HOME` 设置为 `$ANT_JAVA8_HOME`，将 `JAVA_HOME` 设置为 `$JAVA8_HOME`。
{: tip}

### 部署属性
下表列出并描述了缺省情况下在管道环境中可用的每个部署环境属性。

|环境属性|描述|
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
|CF_APP|对于部署，它是要部署的应用程序的名称。此属性是部署的必需属性，可以在脚本自身中、在部署作业配置界面中或在项目的 `manifest.yml` 文件中指定。|
|CF_ORG|对于部署，它是要部署到的组织的名称。|
|CF_ORGANIZATION_ID|对于部署，它是要部署到的组织的标识。|
|CF_SPACE|对于部署，它是要部署到的空间的名称。|
|CF_SPACE_ID|对于部署，它是要部署到的空间的标识。|
|CF_TARGET_URL|对于部署，它是 {{site.data.keyword.Bluemix_short}} 或 Cloud Foundry 的 URL。|
|IDS_VERSION|对于部署，它是要部署的应用程序的版本，或者是源标识。|
{: caption="表 3. 部署环境属性" caption-side="top"}

## 预安装的资源
{: #deliverypipeline_resources}

每个管道中都预安装了多个运行时、工具和 Node 模块。

### 运行时和工具
下表列出了每个管道中可用的每个预安装运行时和工具。

所有链接都位于主目录中。
{: tip}

|资源|链接名称|路径|
|----------|-----------|-----------|
|Apache Ant 1.9.2|ant|/opt/IBM/ant|
|Cloud Foundry CLI 6.14|cf|/opt/IBM/cf|
|Gradle 1.12|gradle|/opt/IBM/gradle|
|Gradle 2.9|gradle2|/opt/IBM/gradle2|
|IBM Cloud CLI (bx) 0.13.0|ibmcloud|/usr/local/ibmcloud/bin/ibmcloud|
|IBM Java（缺省）|java|/opt/IBM/java|
|IBM Java 7 x86_64-71|java7|/opt/IBM/java7|
|IBM Java 8 x86_64-80|java8|/opt/IBM/java8|
|Apache Maven 3.2.1|maven|/opt/IBM/maven|
|IBM Node|node|/opt/IBM/node|
|IBM Rational Team Concert&trade; SCM Tools|RTC-SCM-Tools|/opt/IBM/RTC-SCM-Tools|
{: caption="表 4. 运行时和工具的链接名称和路径" caption-side="top"}

管道环境提供 64 位版本的 IBM Node 0.10、0.10.48、0.12、0.12.17、4.2、4.4.5、4.6.0、6.2.2 和 6.7.0。要选择版本，请使用导出命令。

例如，要使用 Node 0.12.7，请输入此命令：`export PATH=/opt/IBM/node-v0.12/bin:$PATH`

要使用 Node 4.2.2，请输入此命令：`export PATH=/opt/IBM/node-v4.2/bin:$PATH`

### Node 模块

下列 Node 模块在管道环境中是全局安装的：

* grunt@0.4.5
* grunt-cli@0.1.13
* grunt-contrib-concat@0.4.0
* grunt-contrib-jshint@0.10.0
* grunt-contrib-nodeunit@0.4.1
* grunt-contrib-qunit@0.5.1
* grunt-contrib-uglify@0.5.0
* grunt-contrib-watch@0.6.1
* karma@0.12.23
* karma-cli@0.0.4
* karma-jasmine@0.1.5
* karma-phantomjs-launcher@0.1.4
* phantomjs@1.9.10
