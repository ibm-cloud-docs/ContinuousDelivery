---

Copyright:
  years: 2018, 2019
lastupdated: "2019-02-27"

keywords: pipeline base image, custom Docker, IBM Cloud team uses

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


# 使用定制 Docker 映像
{: #custom_docker_images}

管道基本映像可能并不支持所有构建需求。例如，您可能需要对 Node、Java 或其他工具的版本进行更细颗粒度的控制。可以通过在管道作业中包含第一步来解决此问题，第一步用于安装一系列新程序包，并仔细配置环境变量（例如，`PATH`）来设置环境。但是，更好的方法是使用管道支持，将“定制 Docker 映像”作为您作业的基础。

无论使用的是“构建”、“测试”还是“部署”作业类型，都可以选择“定制 Docker 映像”子类型来提供要使用的 Docker 映像名称，并指定要运行的脚本。例如，使用以下选项来运行使用 Maven 3.5.3 和 IBM Java 的“构建”作业：

 ![使用定制映像进行 Maven 构建](images/custom-image-maven-build.png)


## 指定 Docker 映像名称
{: #docker_image_name}

定制 Docker 映像作业中的 Docker 映像名称旨在以映像名称用于 Docker CLI 的相同方式进行使用。Docker 映像名称的格式为：`[repository][:][tag]`。例如，对于 `docker run maven:3.5.3-ibmjava`，Docker 映像名称为 `maven:3.5.3-ibmjava`，其中 `maven` 是存储库，`3.5.3-ibmjava` 是标记。对于可以使用的 Docker 映像名称没有任何限制；任何有效的 Docker 映像都可使用。

如果未填写 **Docker 映像名称**字段，那么将使用标准管道基本映像。
{: tip}

缺省情况下，会在 [Docker Hub ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://hub.docker.com/){: new_window} 上搜索您的存储库。如果使用的是其他 Docker 注册表（如 {{site.data.keyword.registrylong}}），那么可以使用完整的 DNS 名称。您还可以使用 Docker Hub 上映像的标准名称。例如，`registry.hub.docker.com/library/maven:3.5.3-ibmjava`。

Docker 映像的 `tag` 是可选的。如果未指定标记，那么缺省情况下会将其设置为 `latest`。缺省值 `latest` 只是存储库所有者必须管理的标记名称。它并不意味着此 Docker 映像是时间上最新的映像。

您可以在 Docker Hub 上找到大型存储库社区。IBM 在以下位置托管了若干公共存储库供 IBM Cloud 团队使用：[https://hub.docker.com/u/ibmcom/ ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://hub.docker.com/u/ibmcom/){: new_window}。`ibmcom/ibmjava` 和 `ibmcom/ibmnode` 存储库很适合作为构建基础。 

## 使用专用映像注册表
{: #private_image_registry}

如果要使用需要认证的专用注册表，那么必须设置两个额外的阶段环境属性：`DOCKER_USERNAME` 和 `DOCKER_PASSWORD`。可以使用安全属性来掩蔽 `DOCKER_PASSWORD`。在拉取映像之前，定制 Docker 映像作业会使用您的用户名和密码凭证来完成 `docker login`。

对于大多数注册表，可以使用为您提供的用户名和密码。如果是使用 {{site.data.keyword.registrylong_notm}} 来存储专用映像，那么必须使用平台 API 密钥进行认证。 

1. [请求平台 API 密钥 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/iam/#/apikeys){: new_window}，并确保保存该密钥。 
1. 通过将 `iamapikey` 用于 `DOCKER_USERNAME`，并将保存的平台 API 密钥用于 `DOCKER_PASSWORD`，创建两个阶段环境属性。

 ![{{site.data.keyword.registrylong_notm}} 凭证](images/custom-image-private-repository.png)


## 指定脚本
{: #specify_script}

可以使用定制 Docker 映像作业中的 **script** 块来创建在任务文件夹中运行的脚本文件，类似于常规管道作业的工作方式。 

这将覆盖 Docker 映像的 Dockerfile 中的 `ENTRYPOINT` 和 `CMD`，并且不会调用这两项。在某些情况下，这可能意味着需要向脚本添加初始化步骤。
{: tip}

通过定制 Docker 映像作业，可以更灵活地运行脚本；特别是，可以控制命令解释器。通常，如果脚本的第一行以 `#!` 和命令解释器名称开头，那么该条目会用于运行作业中的命令。如果未指定命令解释器，那么将使用 Docker 映像的缺省 shell。通常，会使用 `#!/bin/bash` 或 `#!/bin/sh`；如果指定相应的 Docker 映像，那么 `awk`、`node` 和 `ruby` 的映像命令解释器也会工作。
