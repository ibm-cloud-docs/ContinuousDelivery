---

copyright:
  years: 2016, 2018
lastupdated: "2018-11-29"
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


# Delivery Pipeline 概述
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} 包含 Delivery Pipeline，用于以可重复的方式进行构建、测试和部署，需要的人为干预最少。在管道中，阶段序列可检索输入并运行作业（例如，构建、测试和部署）。
{:shortdesc}

查看、修改或运行管道的许可权基于拥有管道的工具链的访问控制。有关工具链的访问控制的更多信息，请参阅[管理对资源组中工具链的访问权](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window}和[管理对 Cloud Foundry 组织中工具链的访问权](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}。
{: important}

您可以指定由管道提供的要在多个作业类型中运行的脚本，这样就可以直接控制作业运行内容。这些脚本在包含多个标准开发工具的 Docker 映像中运行，其中包括与 {{site.data.keyword.Bluemix_notm}} 运行时进行交互所需的工具。有关标准 Docker 映像中包含哪些内容的更多信息，请参阅[预安装的资源](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_resources){: new_window}。如果作业需要的开发工具在标准映像中没有提供，或者您需要这些工具的不同版本，那么可以使用定制映像。有关定制映像的更多信息，请参阅[使用定制 Docker 映像](/docs/services/ContinuousDelivery/pipeline_custom_docker_images.html#custom_docker_images){: new_window}。

当管道运行脚本时，会使用环境变量将描述作业运行位置上下文的属性传递到脚本。例如，作为阶段输入的存储库的 URL，要运行的阶段和作业的名称，作业类型所指定的参数，等等。要查看可用环境变量的列表，请参阅[预安装的资源](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_envprop){: new_window}。 

您可以在管道级别和阶段级别定义属性。管道属性是跨管道中所有阶段和作业共享的。阶段属性对特定阶段来说是唯一的，并且在该阶段中是跨所有作业共享的。有关属性的更多信息，请参阅[环境属性（环境变量）](/docs/services/ContinuousDelivery/pipeline_about.html#environment_properties)。

## 阶段
{: #deliverypipeline_stages}

在构建、部署和测试代码时，阶段可用于组织输入和作业。阶段从源控制存储库（SCM 存储库）接受输入，或者在其他阶段中构建作业。对于 SCM 存储库，输入是存储库中特定分支的内容；对于构建作业，输入是作业所产生的工件。当您创建第一个阶段时，会在**输入**选项卡中包含缺省设置。

当阶段运行时，该阶段的输入会传递到阶段中的每个作业。会为每一个作业提供一个干净的运行容器。结果是，阶段中的作业彼此之间无法传递工件。要在作业之间传递工件，请将作业分隔到两个阶段中，并使用第一阶段中作业的输出作为第二阶段的输入。
{: tip}

与定义管道属性的方法相似，您也可以定义阶段属性已用于特定阶段的所有作业中。例如，您可以定义 `TEST_URL` 属性，该属性传递 URL 以在阶段中部署和测试作业。部署作业将部署到该 URL，而测试作业将在该 URL 测试正在运行的应用程序。还会使用环境变量将阶段属性传递到作业脚本。如果在管道级别和阶段级别定义了相同的属性，那么会使用阶段属性的值。

缺省情况下，在阶段中每当更改传递到项目的 SCM 存储库时，都会自动运行构建和部署操作。阶段和作业按顺序运行；它们为您的工作实现流程控制。例如，您可能将测试阶段置于部署阶段之前。如果测试阶段中的测试失败，部署阶段不会运行。

您可能想要对特定阶段进行更严格的控制。如果在某个阶段输入时发生了更改，而您不想在每次发生更改时该阶段都运行，那么您可以禁用该功能。在**输入**选项卡的“阶段触发器”部分中，单击**仅当手动运行此阶段时才运行作业**。

![“输入”选项卡](images/input_tab_only_execute.png)


### 构建阶段
{: #build_stage}

构建阶段指定**构建器类型**以指示如何构建工件。  

在构建作业中可用的很多字段都是在多个构建器类型中很常见的。
{: tip}

可用的构建器类型包括：

* **简单** - 使用**简单**构建器类型的作业采用当前阶段的输入，而不进行修改，将其归档以备后续阶段使用。通常，只有当阶段的输入是来自 SCM 存储库时，**简单**构建器类型才有用。
* **Ant** - 使用此构建器以使用 Apache Ant 文件来管理构建作业。
  * **构建脚本** - 此构建器类型可以是任何有效的构建脚本。缺省情况下，此构建器类型设置为“ant”。
  * **工作目录** - 指定脚本在哪个目录中运行。
  * **构建归档目录** - 指定包含后续阶段要用于归档的作业输出的目录。
  * **启用测试报告** - 选中此复选框以指定构建作业运行生成 JUnit XML 格式结果文件的测试。基于结果文件的报告会显示在“作业结果”页面的“测试”选项卡上。如果任何测试失败，那么作业将标记为失败。

  * **启用代码覆盖报告** - 选中此复选框以显示可用于代码覆盖报告的更多字段。您可以指定覆盖运行器（如 Istanbul、JaCoCo、ore Cobertura），覆盖结果文件的位置以及覆盖结果目录（相对于工作目录）。
* **Container Registry**
* **Gradle（Artifactory、Nexus 或 SonarQube）**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven（Artifactory、Nexus 或 SonarQube）**
* **npm（Artifactory 或 Nexus）**
* **Shell 脚本**

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

构建和部署脚本的样本可以在 [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons) 中找到。

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

作业最长可以运行 60 分钟。当作业超过此限制时即会失败。如果作业会超过此限制，请将其分成多个作业。例如，如果作业执行三个任务，那么您可以将其分成三个作业：每个任务一个作业。
{: tip}

要了解如何将作业添加到阶段，请参阅[将作业添加到阶段](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}。

### 构建作业

构建作业可对您的项目进行编译，以为部署做好准备。它们会生成可发送到构建归档目录的工件，但是缺省情况下，工件会置于项目的根目录中。

从构建作业接受输入的作业必须参考与其采用相同结构创建的构建工件。例如，如果构建作业将构建工件归档至 `output` 目录，那么部署脚本会参考 `output` 目录而非项目根目录，以部署编译过的项目。可以通过在**构建归档目录**字段中输入目录名称来指定归档目录。使此字段保留为空白将归档根目录。

如果使用**简单**构建器类型，那么不会编译或构建代码；而是将其打包，并使其可用于未来的阶段。
{: tip}

使用 Cloud Foundry 部署时，Cloud Foundry 会包含正确的工件以允许应用程序运行。有关更多信息，请参阅[使用 cf 命令部署应用程序](/docs/cloud-foundry/deploy-apps.html#dep_apps)。Cloud Foundry 应用程序的管道包含运行 cf 命令的部署阶段。

Cloud Foundry 尝试[检测 buildpack 以使用 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://docs.cloudfoundry.org/buildpacks/detection.html)。可以在应用程序根文件夹的清单文件中指定要使用的 [buildpack](/docs/cfapps/byob.html#using-community-buildpacks)。buildpack 通常会检查用户提供的工件，以确定要下载的依赖项以及如何配置应用程序以与绑定服务进行通信。有关清单文件的更多信息，请参阅[应用程序清单](/docs/cloud-foundry/deploy-apps.html#appmanifest)。

### 部署作业

部署作业可将项目作为应用程序上传到 {{site.data.keyword.Bluemix_notm}}，且可通过 URL 进行访问。部署项目之后，可以在 {{site.data.keyword.Bluemix_notm}} 仪表板上查找已部署的应用程序。

部署作业可以部署新的应用程序或更新现有的应用程序。即使您最初使用其他方法（如 Cloud Foundry 命令行界面或 Web IDE 中的运行栏）部署了应用程序，您也可以使用部署作业更新该应用程序。要更新应用程序，请在部署作业中，使用该应用程序的名称。

可以部署到一个或多个区域和服务。例如，您可以设置 {{site.data.keyword.deliverypipeline}} 以使用一个或多个服务，在一个区域中进行测试，然后部署到多个区域中的生产环境。有关更多信息，请参阅[区域](/docs/overview/ibm-cloud.html#ov_intro-reg){: new_window}。

### 测试作业
如果您想要求满足某些条件，请在构建和部署作业之前或之后，包括测试作业。您可以定制测试作业，按您的需要定制为简单或复杂。例如，您可能会发出 cURL 命令并期望获得特定响应。您还可能使用第三方测试服务（如 Sauce Labs），运行一组单元测试或运行功能测试。

如果测试产生 JUnit XML 格式的结果文件，那么基于结果文件的报告将显示在每个测试结果页面的**测试**选项卡上。如果测试失败，那么作业也会失败。

## 环境属性（环境变量）
{: #environment_properties}

一组预定义的环境属性提供作业执行环境相关信息的访问权。有关预定义环境属性的完整列表，请参阅[环境属性和资源](/docs/services/ContinuousDelivery/pipeline_deploy_var.html)。

也可以定义自己的环境属性。例如，可以定义 `API_KEY` 属性以传递管道中所有脚本用来访问 {{site.data.keyword.Bluemix_notm}} 资源的 API 密钥。

可以添加以下类型的属性：

* **文本**：具有单行值的属性关键字。
* **文本区域**：具有多行值的属性关键字。
* **安全**：具有单行值的属性关键字，使用 AES-128 加密来保护安全。该值显示为星号。
* **属性**：项目存储库中的文件。此文件可以包含多个属性。每一个属性必须位于自己的行上。要分隔键值对，请使用等号 (=)。用引号括起所有字符串值。例如，`MY_STRING="SOME STRING VALUE"`。

您可以通过在作业脚本中运行 `env` 命令来检查管道作业的环境属性。
{:tip}

### 管道属性
要定义管道属性，请从“管道”页面上的溢出菜单中选择**配置管道**。

![管道溢出菜单](images/OverflowMenu.png)

在“管道”配置页面的**环境属性**选项卡中，设置管道级别环境属性。

![管道属性页面](images/PipelineProperties.png)

### 阶段属性
要定义阶段属性，请打开“阶段”配置页面，然后单击**环境属性**选项卡。

![阶段属性页面](images/StageProperties.png)

还可以通过导出属性在同一阶段的作业之间传递环境属性。例如，您可以包含以下命令以便在该阶段的另一个作业中使用 `$API_KEY` 属性：`export API_KEY=<insert API key here>`
{:tip}

### 计算属性
您可以计算跨各个阶段共享的环境属性值，方法是在运行该阶段时创建 `build.properties` 文件，然后让下一个阶段运行该文件。例如，构建作业可以在构建脚本中包括以下命令：

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

所有作业都通过运行 `build.properties` 文件（如果存在）来启动。

## 创建和使用工件
{: #artifacts}

构建作业自动访存运行用户脚本的当前文件夹中的内容。如果不需要整个 Git 存储库内容以供将来部署，那么最好配置显式输出目录，然后在该目录中复制或创建相关工件。作业脚本在构建结果（输出目录）中运行。

部署到 Cloud Foundry 的作业需要指定使用其权限运行作业的用户的 Platform API 密钥，以及用于部署工件的区域、组织和空间。如果需要更多服务来运行应用程序，那么必须在 `manifest.yml` 文件中指定这些服务。

部署到 {{site.data.keyword.containerlong_notm}} 的部署作业需要指定使用其权限运行作业的用户的 Platform API 密钥、Dockerfile 和可选的 Helm 图表。  

作业脚本在作业使用分配的 Platform API 密钥登录到目标环境后运行（以便您可以在脚本中运行 `cf push` 或 `kubectl` 命令）。

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

清单文件名为 `manifest.yml`，存储在项目的根目录中，用于控制如何将项目部署到 {{site.data.keyword.Bluemix_notm}}。有关创建项目清单文件的信息，请参阅[有关应用程序清单的 {{site.data.keyword.Bluemix_notm}} 文档](/docs/cloud-foundry/deploy-apps.html#appmanifest)。要与 {{site.data.keyword.Bluemix_notm}} 集成，项目的根目录中必须包含清单文件。但是，无需基于该文件中的信息进行部署。

在管道中，您可以使用 `cf push` 命令自变量，指定清单文件可以执行的所有事项。`cf push` 命令自变量在具有多个部署目标的项目中非常有用。如果多个部署作业全部尝试使用项目清单文件中指定的路径，那么会发生冲突。

为避免冲突，可以使用 `cf push` 后接主机名自变量 `-n` 和路径名来指定路径。通过修改各个阶段的部署脚本，可以避免部署到多个目标时发生的路径冲突。

若要使用 `cf push` 命令自变量，请打开部署作业的配置设置，并修改**部署脚本**字段。有关更多信息，请参阅 [Cloud Foundry Push 文档![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}。
