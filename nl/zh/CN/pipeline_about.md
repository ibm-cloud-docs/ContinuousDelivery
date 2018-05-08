---

copyright:
  years: 2016, 2018
lastupdated: "2018-3-22"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Delivery Pipeline 概述
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} 包含 Delivery Pipeline，用于以可重复的方式进行构建、测试和部署，需要的人为干预最少。在管道中，阶段序列可检索输入并运行作业（例如，构建、测试和部署）。
{:shortdesc}

以下各节描述管道背后的概念性详细信息。

## 阶段
{: #deliverypipeline_stages}

在构建、部署和测试代码时，阶段可用于组织输入和作业。阶段从源控制存储库（SCM 存储库）接受输入，或者在其他阶段中构建作业（构建工件）。当您创建第一个阶段时，会在**输入**选项卡上为您设置缺省设置。

阶段输入会传递到该阶段包含的作业中，并且会为每一个作业提供一个干净的运行容器。

**要点**：阶段中的作业彼此之间无法传递工件。由于您无法在阶段之间传递工件，因此，如果部署阶段将使用构建阶段工件，那么需要有一个独立于部署阶段的构建阶段。

您可以定义可在所有作业中使用的阶段环境属性。例如，您可以定义 `TEST_URL` 属性，该属性传递单个 URL 以在单个阶段中部署和测试作业。部署作业将部署到该 URL，而测试作业将在该 URL 测试正在运行的应用程序。

缺省情况下，在阶段中每当更改传递到项目的 SCM 存储库时，都会自动运行构建和部署操作。阶段和作业按顺序运行；它们为您的工作实现流程控制。例如，您可能将测试阶段置于部署阶段之前。如果测试阶段中的测试失败，部署阶段不会运行。

您可能想要对特定阶段进行更严格的控制。如果在某个阶段输入时发生了更改，而您不想在每次发生更改时该阶段都运行，那么您可以禁用该功能。在**输入**选项卡的“阶段触发器”部分中，单击**仅当手动运行此阶段时才运行作业**。

![“输入”选项卡](images/input_tab_only_execute.png)


### 构建阶段
{: #build_stage}

<!-- Need the Pipeline team to fill out what each builder does and possible add an example -->
构建阶段指定**构建器类型**以指示如何构建工件。可用的构建器类型包括：

1. **简单** - 如果使用**简单**构建器类型，那么不会编译或构建代码；而是将其打包，并使其可用于未来的阶段。
2. **Ant**
3. **Container Registry**
4. **Gradle**
5. **Gradle（Artifactory、Nexus 或 SonarQube）**
6. **Grunt**
7. **IBM Globalization Pipeline**
8. **Maven**
9. **Maven（Artifactory、Nexus 或 SonarQube）**
10. **npm**
11. **npm（Artifactory 或 Nexus）**
12. **Shell 脚本**

### 部署阶段
部署阶段指定来自构建阶段的输入。部署阶段中的作业指定**部署程序类型**。可用的部署程序类型包括：

1. **Cloud Foundry**
2. **Kubernetes**

## 作业
{: #deliverypipeline_jobs}

作业是阶段中的执行单元。一个阶段可以包含多个作业，阶段中的作业可以按顺序运行。缺省情况下，如果某个作业失败，那么阶段中的后续作业不会运行。

![在阶段中构建和测试作业](images/jobs.png)

作业在 Docker 容器中的独立工作目录中运行，而这些容器是为运行每一个管道所创建的。在作业运行之前，其工作目录中会填充在阶段级别定义的输入。例如，您的某个阶段中可能包含测试作业和部署作业。如果您在一个作业上安装依赖项，那么这些依赖项无法用于另一个作业。但是，如果您在阶段输入中提供依赖项，那么这些依赖项可用于这两个作业。

除了简单类型构建作业之外，当您配置作业时，可以包括内含构建、测试或部署命令的 UNIX shell 脚本。因为作业在特定容器中运行，所以一个作业的操作无法影响其他作业的运行环境，即使这些作业属于相同的阶段也是如此。

bod 和部署脚本的样本可以在 [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons) 中找到。

此外，管道作业仅可以 `sudo` 运行以下命令：
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


作业运行之后，即会废弃针对其创建的容器。可以持久存储作业运行的结果，但是不会持久存储其运行的环境。

**注**：作业最长可以运行 60 分钟。当作业超过此限制时即会失败。如果作业会超过此限制，请将其分成多个作业。例如，如果作业执行三个任务，那么您可以将其分成三个作业：每个任务一个作业。

要了解如何将作业添加到阶段，请参阅[将作业添加到阶段](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}。

### 构建作业

构建作业可对您的项目进行编译，以为部署做好准备。它们会生成可发送到构建归档目录的工件，但是缺省情况下，工件会置于项目的根目录中。

从构建作业接受输入的作业必须参考与其采用相同结构创建的构建工件。例如，如果构建作业将构建工件归档至 `output` 目录，那么部署脚本会参考 `output` 目录而非项目根目录，以部署编译过的项目。可以通过在**构建归档目录**字段中输入目录名称来指定归档目录。使此字段保留为空白将归档根目录。

**注**：如果使用**简单**构建器类型，那么不会编译或构建代码；而是将其打包，并使其可用于未来的阶段。

使用 Cloud Foundry 部署时，Cloud Foundry 会包含正确的工件以允许应用程序运行。有关更多信息，请参阅[使用 cf 命令部署应用程序](https://console.ng.bluemix.net/docs/manageapps/depapps.html#dep_apps)。Cloud Foundry 应用程序的管道包含运行 cf 命令的部署阶段。

Cloud Foundry 尝试[检测 buildpack 以使用 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://docs.cloudfoundry.org/buildpacks/detection.html)。可以在应用程序根文件夹的清单文件中指定要使用的 [buildpack](/docs/cfapps/byob.html#using-community-buildpacks)。buildpack 通常会检查用户提供的工件，以确定要下载的依赖项以及如何配置应用程序以与绑定服务进行通信。有关清单文件的更多信息，请参阅[应用程序清单](/docs/manageapps/depapps.html#appmanifest)。

### 部署作业

部署作业可将项目作为应用程序上传到 {{site.data.keyword.Bluemix_notm}}，且可通过 URL 进行访问。部署项目之后，可以在 {{site.data.keyword.Bluemix_notm}} 仪表板上查找已部署的应用程序。

部署作业可以部署新的应用程序或更新现有的应用程序。即使您最初使用其他方法（如 Cloud Foundry 命令行界面或 Web IDE 中的运行栏）部署了应用程序，您也可以使用部署作业更新该应用程序。要更新应用程序，请在部署作业中，使用该应用程序的名称。

可以部署到一个或多个区域和服务。例如，您可以设置 {{site.data.keyword.deliverypipeline}} 以使用一个或多个服务，在一个区域中进行测试，然后部署到多个区域中的生产环境。有关更多信息，请参阅[区域](/docs/overview/whatisbluemix.html#ov_intro_reg){: new_window}。

### 测试作业
如果您想要求满足某些条件，请在构建和部署作业之前或之后，包括测试作业。您可以定制测试作业，按您的需要定制为简单或复杂。例如，您可能会发出 cURL 命令并期望获得特定响应。您还可能使用第三方测试服务（如 Sauce Labs），运行一组单元测试或运行功能测试。

如果测试产生 JUnit XML 格式的结果文件，那么基于结果文件的报告将显示在每个测试结果页面的**测试**选项卡上。如果测试失败，那么作业也会失败。

## 环境属性（环境变量）
{: #environment_properties}

您可以在作业的 shell 命令中包括环境属性。这些属性提供作业执行环境相关信息的访问权。有关更多信息，请参阅 [{{site.data.keyword.deliverypipeline}} 服务的环境属性和资源](/docs/services/ContinuousDelivery/pipeline_deploy_var.html)。可以通过导出属性在同一阶段的作业之间传递环境属性。要在阶段之间传递环境属性，请在阶段中的存储库中创建 `build.properties` 文件，然后让下一个阶段执行 `build.properties`。例如，构建作业可以在构建脚本中包括以下命令：

    `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

    所有作业都通过执行 `build.properties` 文件（如果存在）来启动。

## 创建和使用工件
{: #artifacts}

构建作业自动访存执行用户脚本的当前文件夹中的内容。如果不需要整个 Git 存储库内容以供将来部署，那么最好配置显式输出目录，然后在该目录中复制或创建相关工件。作业脚本在构建结果（输出目录）中执行。

部署到 Cloud Foundry 的部署作业需要指定用于部署工件的组织和空间。如果需要其他服务来运行应用程序，那么需要在 `manifest.yml` 文件中指定这些服务。

将部署到 Kubernetes 集群的 IBM Cloud Container Service 的部署作业需要 Dockerfile 和（可选）Helm 图表。  

作业脚本在作业登录到目标环境后运行（以便您可以在脚本中执行 `cf push` 或 `kubectl` 命令）。

## 管道示例
{: #deliverypipeline_example}

简单管道可能包含三个阶段：

1. 构建阶段，对应用程序进行编译并运行构建过程。
2. 测试阶段，部署应用程序的实例，并对其运行测试。
3. 生产阶段，部署已测试应用程序的生产实例。

此管道在以下概念图中显示：

![管道中各阶段和作业的概念图](images/diagram.jpg)

*三个阶段管道的概念模型*

阶段从存储库和构建作业接受输入，阶段中的作业按顺序彼此独立地运行。在管道示例中，尽管测试和生产阶段都将构建阶段的输出作为其输入，各阶段还是按顺序运行。

## Cloud Foundry 清单文件
{: #deliverypipeline_manifest}

清单文件名为 `manifest.yml`，存储在项目的根目录中，用于控制如何将项目部署到 {{site.data.keyword.Bluemix_notm}}。有关创建项目清单文件的信息，请参阅[有关应用程序清单的 {{site.data.keyword.Bluemix_notm}} 文档](/docs/manageapps/depapps.html#appmanifest)。要与 {{site.data.keyword.Bluemix_notm}} 集成，项目的根目录中必须包含清单文件。但是，无需基于该文件中的信息进行部署。

在管道中，您可以使用 `cf push` 命令自变量，指定清单文件可以执行的所有事项。`cf push` 命令自变量在具有多个部署目标的项目中非常有用。如果多个部署作业全部尝试使用项目清单文件中指定的路径，那么会发生冲突。

为避免冲突，可以使用 `cf push` 后接主机名自变量 `-n` 和路径名来指定路径。通过修改各个阶段的部署脚本，可以避免部署到多个目标时发生的路径冲突。

若要使用 `cf push` 命令自变量，请打开部署作业的配置设置，并修改**部署脚本**字段。有关更多信息，请参阅 [Cloud Foundry Push 文档![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}。
