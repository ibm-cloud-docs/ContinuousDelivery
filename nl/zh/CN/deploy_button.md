---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# 创建“部署到 {{site.data.keyword.Bluemix_notm}}”按钮 {: #deploy-button}

“部署到 {{site.data.keyword.Bluemix_notm}}”按钮是共享公共 Git 源代码应用程序的有效方法，这样其他人就能使用工具链来试用代码并将其部署到 IBM {{site.data.keyword.Bluemix_notm}}。此按钮不但需要的配置最少，而且可插入到支持标记的任何位置。任何用户单击此按钮后，都会在新的 Git 存储库中创建代码的克隆副本，这样原始应用程序始终不受影响。
{: shortdesc}

当用户单击您的按钮时，会发生以下操作：

1. 如果用户没有活动的 {{site.data.keyword.Bluemix_notm}} 帐户，那么必须创建帐户。用户可以创建试用帐户，也可以创建实际帐户。

2. 用户可以通过单击 {{site.data.keyword.deliverypipeline}} 图标来选择区域、组织、空间和应用程序名称。建议让应用程序名称与工具链名称相同，该名称是由原始 Git 存储库的名称和时间构成的。也可以编辑工具链名称。

3. 将创建一个工具链，该工具链包含您的 Git 存储库的新专用克隆、用于构建和部署代码更改的管道、用于在云上编辑代码的 Eclipse Orion {{site.data.keyword.webide}} 以及问题跟踪程序。

  **提示**：如果 `.bluemix` 目录包含 `toolchain.yml` 文件，那么该文件用于指定工具链的工具集成。有关 `toolchain.yml` 文件的更多信息，请参阅[创建定制工具链](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}。

4. 如果应用程序需要构建文件，那么会自动检测构建文件并构建应用程序。

5. 如果为构建和部署过程配置了管道，那么将使用 `pipeline.yml` 文件来部署应用程序。

6. 如果应用程序需要容器，那么会使用用于定义 IBM Containers 服务的 `pipeline.yml` 文件和用于定义图像的 Dockerfile 在 {{site.data.keyword.Bluemix_notm}} 容器中部署应用程序。

7. 应用程序会部署到用户选定的 {{site.data.keyword.Bluemix_notm}} 组织中。

## 按钮示例 {: #button-examples}

下面是公共 {{site.data.keyword.gitrepos}} 存储库的应用程序按钮示例：

[![部署到 Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

下面是公共 GitHub 存储库的应用程序按钮示例：

[![部署到 Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## 创建按钮 {: #create-button}

要创建“部署到 {{site.data.keyword.Bluemix_notm}}”按钮，请复制并修改下列某个片段模板。在 URL 中指定 Git 存储库和分支。

### 创建 HTML 格式的按钮

要创建 HTML 格式的按钮，请复制以下片段并插入公共 Git 存储库 URL 和分支。

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="部署到 Bluemix"></a>
```
{: codeblock}

如果未在片段的存储库 URL 中包含 `branch` 参数，那么“部署到 Bluemix”按钮缺省为存储库的主分支。

### 创建 Markdown 格式的按钮

要创建 Markdown 格式的按钮，请复制以下片段并插入公共 Git 存储库 URL 和分支。

```Markdown
[![部署到 Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

如果未在片段的存储库 URL 中包含 `branch` 参数，那么“部署到 Bluemix”按钮缺省为存储库的主分支。

### 使用按钮片段 {: #button-snippet}

创建“部署到 Bluemix”按钮片段后，可以将其插入博客、文章、Wiki、自述文件或您希望推广自己应用程序的其他任何位置。

定制“部署到 {{site.data.keyword.Bluemix_notm}}”按钮的片段时，请注意这两个模板使用的都是外部按钮图像的缺省路径，图像格式为 PNG 且为英语。

* 如果您希望按钮使用 SVG 图像而不是 PNG 图像，请将此片段中使用的按钮图像的路径更改为 `https://bluemix.net/deploy/button.svg`。

* 如果您希望按钮使用大图像，请将此片段中使用的按钮图像的路径更改为 `https://bluemix.net/deploy/button_x2.png`。此图像是缺省图像大小的两倍。

* 如果您希望本地存储图像，那么可以下载图像并将其存储在 Git 存储库中。调整路径以使用图像的相对位置。

* 如果要使用该按钮的翻译版本，那么可以远程引用相应版本或从 [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window} 下载相应版本。

## 存储库注意事项 {: #button-repo}

查看在“部署到 {{site.data.keyword.Bluemix_notm}}”按钮中使用的存储库的以下注意事项。


## 构建文件需求
{: build_file}

如果必须先构建应用程序，然后才能进行部署，那么必须在存储库中包含构建文件。如果在存储库的根目录中检测到构建脚本文件，那么将在部署前触发代码的自动构建。

支持的构建器包括：

* [Ant ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")：](http://ant.apache.org/manual/using.html){:new_window}`build.xml`，用于将输出构建到 `./output/` 文件夹
* [Gradle ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")：](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window}`/build.gradle`，用于将输出构建到 `.` 文件夹
* [Grunt ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")：](http://gruntjs.com/getting-started#the-gruntfile){:new_window}`/Gruntfile.js`，用于将输出构建到 `.` 文件夹
* [Maven ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")：](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window}`/pom.xml`，用于将输出构建到 `./target/` 文件夹

### 管道文件需求
{: pipeline_file}

要在 `.bluemix` 目录中为工具链配置管道，请包含 `pipeline.yml` 文件。对于该目录中的每个 `pipeline.yml` 文件，在实例化工具链时将分别创建一个管道。

如果在 `.bluemix` 目录中没有 `pipeline.yml` 文件，那么“部署到 {{site.data.keyword.Bluemix_notm}}”按钮将创建具有两个阶段的缺省管道：“构建”阶段和用于部署到 Cloud Foundry 的“部署”阶段。

要创建管道文件，请查阅[定制工具链管道指示信息](toolchains_custom.html#toolchains_custom_pipeline_yml)中的示例文件。与在 Web 界面中定义管道一样，可以使用文本通过创建阶段和作业，设置输入和环境变量以及添加脚本来定义管道。您还可以在[此演示项目](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix)中查看大量更复杂的管道文件。

### 容器 Dockerfile 需求
{: container_dockerfile}

要使用 IBM Containers 在容器中部署应用程序，必须在存储库的根目录中包含 Dockerfile ，并在 `.bluemix` 目录中包含 `pipeline.yml` 文件。

Dockerfile 类似于某种应用程序构建脚本。如果在存储库中检测到 Dockerfile，那么在容器中部署应用程序之前，会自动将该应用程序构建到映像中。如果必须先构建应用程序，然后才能将其构建到映像中，那么要包含应用程序的构建脚本和 Dockerfile。

要了解有关创建 Dockerfile 的更多信息，请参阅 [Docker 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.docker.com/reference/builder/){:new_window}。要遵循使用工具链模板来部署到 Kubernetes 的逐步指示信息，请参阅[教程：使用“开发 Kubernetes 应用程序”工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window} 或[教程：使用“使用 Helm 开发 Kubernetes 应用程序”工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window}。  
  要了解有关将 Cloud Foundry 应用程序移植到 Kubernetes 集群的信息，请参阅[教程：移植 Cloud Foundry 应用程序以部署到 Kubernetes ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/port-an-app-from-cf-to-kubernetes-in-a-toolchain?task=0){:new_window}。  

手动创建专用于容器的 `pipeline.yml`

要手动创建专用于容器的 `pipeline.yml`，请参阅 [GitHub 中的示例 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/Puquios/){:new_window}。

## 清单文件需求（对于部署到 Cloud Foundry 的应用程序）
{: #manifest_files}

`manifest.yml` 文件无需位于存储库中。但是，如果应用程序需要运行其他服务，那么必须提供声明这些服务的清单文件。

要了解有关清单文件的更多信息，请参阅[应用程序清单](/docs/cfapps/depapps.html#appmanifest)。
