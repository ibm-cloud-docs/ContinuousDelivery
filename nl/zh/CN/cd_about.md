---

Copyright:
  years: 2015, 2019
lastupdated: "2019-06-18"

keywords: IBM Cloud Public, Use Developer Insights, US South

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


# 工具链可用性、模板和教程  
{: #cd_about}  

工具链在 {{site.data.keyword.Bluemix_notm}} Public 和 Dedicated 上提供。您可以使用模板作为起始点来创建工具链。
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} Public 与 {{site.data.keyword.Bluemix_notm}} Dedicated 比较的工具链可用性
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} Public 是一种基于云的开放式标准平台，您可以在其中构建、运行和管理通过 [http://cloud.ibm.com](http://cloud.ibm.com){: external} 访问的应用程序。{{site.data.keyword.Bluemix_notm}} Dedicated 在安全连接到 {{site.data.keyword.Bluemix_notm}} Public 环境和您网络的专用基础架构环境中提供 {{site.data.keyword.Bluemix_notm}} 的功能。您公司的 {{site.data.keyword.Bluemix_notm}} Dedicated 环境可能未包含与 {{site.data.keyword.Bluemix_notm}} Public 站点相同的工具集成。

对于源代码管理和问题跟踪，{{site.data.keyword.Bluemix_notm}} Public 通常使用 {{site.data.keyword.gitrepos}}（由 IBM 托管并基于 [GitLab Community Edition](https://about.gitlab.com/){: external} 构建）或 GitHub (github.com)。{{site.data.keyword.Bluemix_notm}} Dedicated 也可以使用 github.com，但是它通常使用由您公司安装或由 IBM 管理的 {{site.data.keyword.ghe_short}}。

{{site.data.keyword.contdelivery_short}} 在所选区域中的 {{site.data.keyword.Bluemix_notm}} Public 上可用，也在 {{site.data.keyword.Bluemix_notm}} Dedicated 上可用。根据是在 {{site.data.keyword.Bluemix_notm}} Public 上还是在 {{site.data.keyword.Bluemix_notm}} Dedicated 上使用 {{site.data.keyword.contdelivery_short}}，工具链有所不同。

尽管目前工具链并非在所有区域都可用，但您可以配置工具链以在所有区域中部署应用程序。要了解更多信息，请阅读[跨多个区域部署安全 Web 应用程序教程](/docs/tutorials?topic=solution-tutorials-multi-region-webapp)。
{: tip}

|工具链|{{site.data.keyword.Bluemix_notm}} Public|{{site.data.keyword.Bluemix_notm}} Dedicated|
|:----------|:------------------------------|:------------------|
|工具集成|有关受支持工具集成的列表，请参阅[配置工具集成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations)。|可用的工具集成取决于 {{site.data.keyword.contdelivery_short}} 在您环境中的设置方式。|
|通过模板创建工具链|登录到 [{{site.data.keyword.Bluemix_notm}}](http://cloud.ibm.com/devops){: external}。|登录到 {{site.data.keyword.Bluemix_notm}} 上的 Dedicated 环境。|
|通过应用程序创建工具链|此时，将会对应用程序进行配置，以便可通过填充应用程序入门模板代码的新 GitHub 存储库，进行持续交付。|此时，将会对应用程序进行配置，以便可通过填充应用程序入门模板代码的新 GitHub 或 GitHub Enterprise 存储库，进行持续交付。|  
|Delivery Pipeline 部署区域|所有 {{site.data.keyword.Bluemix_notm}} Public 区域都可用于 Cloud Foundry 部署作业。|{{site.data.keyword.Bluemix_notm}} Dedicated 区域可用。根据 {{site.data.keyword.contdelivery_short}} 在特定环境中的设置方式，相同客户帐户中的其他 Dedicated 或 Local 区域也可能可用。|
|Delivery Pipeline 部署作业|所有[作业类型](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs)都可用。|取决于未安装在 Dedicated 环境中的 {{site.data.keyword.Bluemix_notm}} 服务的作业类型可能不可用。例如，容器构建和部署作业类型在没有 {{site.data.keyword.containerlong_notm}} 的环境中可能不可用。|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} Dedicated 和 {{site.data.keyword.Bluemix_notm}} Public 上工具链的区别" caption-side="top"}


## 工具链模板
{: #templates}

您可以使用模板作为起始点来[创建工具链](https://cloud.ibm.com/devops/create){: external}。工具链模板包括支持开发、部署和操作任务的一组特定工具集成。

贵公司的 {{site.data.keyword.Bluemix_notm}} Dedicated 环境可能未包含与 {{site.data.keyword.Bluemix_notm}} Public 站点相同的工具链模板。在 {{site.data.keyword.Bluemix_notm}} Public 和 {{site.data.keyword.Bluemix_notm}} Dedicated 上都可用的工具链模板可能在 {{site.data.keyword.Bluemix_notm}} Dedicated 上包含一组不同的工具集成。
{: note}

一些工具链模板包含属于 {{site.data.keyword.contdelivery_short}} 服务的工具集成。如果您的资源组或组织中还没有该服务的实例，那么当您单击**创建**以创建工具链时，该服务会自动随所选的免费轻量套餐一起添加。有关更多信息和条款，请参阅 [{{site.data.keyword.Bluemix_notm}} 目录](https://cloud.ibm.com/catalog/services/continuous-delivery/){: external}。

“在 Cloud Foundry 上开发和测试微服务”工具链会通过目录部署应用程序，并订购由 Cloudant 库支持的 API。在部署应用程序的过程中，会创建免费的 Cloudant 服务实例。有关更多信息和条款，请参阅 [{{site.data.keyword.Bluemix_notm}} 目录](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){: external}。

预定义的 DevOps 工具链模板是解决现实世界场景的建议示例，每个模板都包含一个样本应用程序。通过模板创建工具链时，可以通过指定 Git 存储库来使用自己的应用程序。

<table valign="top" padding="2px">
  <caption>表 2. 工具链模板</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">模板和可用区域</th>
    <th style="width:50%; text-align:left; vertical-align:top">描述和可用教程</th>
    <th style="text-align:left; vertical-align:top">包含的工具</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">“开发 Cloud Foundry 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、美国东部、德国、东京和英国可用

  </td><td>
有了此工具链，您可以开发和部署 Cloud Foundry 应用程序。缺省情况下，此工具链使用样本 Node.js“Hello world”应用程序，但是您可以改为链接到自己的 GitHub 存储库。该工具链已针对持续交付、源代码控制、问题跟踪和联机编辑进行了预配置。<br><br>

  尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">使用“开发 Cloud Foundry 应用程序”工具链来引入工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 和 Issues</li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">“开发 Kubernetes 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、美国东部、德国、东京和英国可用

  </td><td>
有了此工具链，您可以开发应用程序并将其安全地部署到 {{site.data.keyword.containerlong_notm}} 管理的 Kubernetes 集群中。缺省情况下，此工具链使用样本 Node.js“Hello World”应用程序，但是您可以改为链接到自己的 GitHub 存储库。此工具链已针对具有漏洞顾问程序的持续交付、源代码控制、问题跟踪和联机编辑进行了预配置。<br><br>
  尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">使用“开发 Kubernetes 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 和 Issues</li><li>{{site.data.keyword.containerlong_notm}}（Kubernetes 集群）</li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">“使用 Helm 开发 Kubernetes 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、美国东部、德国、东京和英国可用

  </td><td>
  有了此工具链，您可以在源代码控制中同时开发 Docker 应用程序及其 Helm chart，然后对其自动构建并部署到 Kubernetes 集群。此工具链在构建或部署之前会执行冒烟测试，并使用专用容器注册表以及该容器注册表和 Kubernetes 集群的名称空间来确保隐私。此工具链还会使用漏洞顾问程序来确保仅部署安全映像。<br><br>
尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">使用“使用 Helm 开发 Kubernetes 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>Git Repos and Issue Tracking</li><li>具有 Helm chart 的 {{site.data.keyword.containerlong_notm}}（Kubernetes 集群）
  </li></ul>
  </td></tr>
  
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-helm-toolchain" target="_blank">“在装有 Helm 的 Kubernetes 上开发和测试微服务”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、德国和英国可用

  </td><td>
  通过此云本机工具链，可以使用持续集成和持续部署管道的组合，以将单独开发的微服务协调到在环境中升级的发布中。此工具链使用包含以下三个微服务的样本网上商店应用程序：目录 API、订单 API 和调用这两个 API 的用户界面。此工具链已针对持续交付、源代码控制、功能测试、问题跟踪、联机编辑和警报通知进行了预配置。<br><br>
  尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-with-kubernetes-and-helm-toolchain" target="_blank">使用“使用 Kubernetes 和 Helm 开发和测试微服务”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>Git Repos and Issue Tracking</li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty</li><li>Sauce Labs</li><li>具有 Helm chart 的 {{site.data.keyword.containerlong_notm}}（Kubernetes 集群）
  </li></ul>
  </td></tr>
  
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcanary-testing-istio-toolchain" target="_blank">“使用 Istio 开发 Kubernetes 应用程序并对其进行 canary 测试”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、美国东部、德国、东京和英国可用

  </td><td>
  有了此工具链，您可以安全地开发应用程序，执行 A/B 测试，并将其部署到 {{site.data.keyword.containerlong_notm}} 管理的 Kubernetes 集群中。缺省情况下，此工具链使用样本 Node.js Hello World 应用程序，但是您可以改为链接到自己的 GitHub 存储库。此工具链已针对持续交付预配置为使用 A/B 测试、漏洞顾问程序、源代码控制、问题跟踪和联机编辑。<br><br>
  尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/use-canary-testing-in-kubernetes-using-istio-toolchain" target="_blank">使用“使用 Istio 在 Kubernetes 中运行第一个 canary 测试”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a> <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>Git Repos and Issue Tracking</li><li>{{site.data.keyword.containerlong_notm}}（Kubernetes 集群）
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">“开发和测试 Cloud Foundry 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、德国和英国可用

  </td><td>
  有了此云本机工具链，您可以使用 DevOps Insights 对简单 Cloud Foundry 应用程序的部署设置检测点。缺省情况下，此工具链使用样本 Node.js Weather 应用程序，或者您可以链接到自己的 GitHub 存储库。此工具链使用 Mocha 来运行单元测试，并使用 Istanbul 来检查代码覆盖范围。<br><br>
尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">使用“开发和测试 Cloud Foundry 应用程序”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>Git Repos and Issue Tracking</li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">“在 Cloud Foundry 上开发和测试微服务”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、德国和英国可用

  </td><td>
有了此云本机工具链，您可以使用样本来创建包含三个微服务的网上商店：目录 API、订单 API 和调用这两个 API 的 UI。此工具链已针对持续交付、源代码控制、功能测试、问题跟踪、联机编辑和警报通知进行了预配置。<br><br>
  尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">使用“在 Cloud Foundry 上开发和测试微服务”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 和 Issues</li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty</li><li>Sauce Labs</li><li>Slack</li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" target="_blank">“使用 Cloud Foundry 的 Garage Method 教程”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a> <br><br>

  在美国南部、美国东部、德国、东京和英国可用

</td><td>
此工具链示范 Garage Method 中配备的 DevOps 实践。该工具链已针对持续交付、源代码控制、测试自动化和自动化监视和操作进行了预配置。它随附以 Node.js Express 4 编写的样本应用程序，您可以进行进一步扩展。<br><br>尝试以下课程：<a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Become an IBM Cloud Innovate method advocate <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a>
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>GitHub 和 Issues</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty</li><li>Sauce Labs</li><li>Slack</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fdevops-insights%2FDevOpsInsights_Demo_Toolchain_Template" target="_blank">“DevOps Insights 快速入门演示”工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>

  在美国南部、德国和英国可用

</td><td>
有了此工具链，您无需进行任何设置就可以探索 {{site.data.keyword.DRA_short}}。首先，请登录到 {{site.data.keyword.Bluemix}}。此演示包含来自参考工具链和三个 GitHub 存储库的数据。了解如何在质量仪表板中组织、测试、构建和部署来自所有团队的所有应用程序的数据。评估趋势并了解需要改进的方面，以便确定应该将资源重点用于哪里。查看团队成员如何在 Team Dynamics 中按发布进行协作。<br><br>
尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights" target="_blank">Explore {{site.data.keyword.DRA_full}} <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
</td><td><ul><li>
GitHub 和 Issues</li><li>{{site.data.keyword.DRA_full}}
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">构建您自己的工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a> <br><br>

  在美国南部、美国东部、德国、东京和英国可用

</td><td>
此工具链没有预配置的工具。如果您已经熟悉工具链，那么您可以设置自己的工具链。<br><br>
尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">创建定制工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a>
</td><td> &nbsp;&nbsp; 无
</td></tr>

<tr><td>Continuous Delivery 工具链<br><br>

 在美国南部、美国东部、德国、东京和英国可用

</td><td>
启用应用程序的持续交付时，将使用此工具链。<br><br>
尝试以下教程：

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">向应用程序添加工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">创建定制工具链 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}</li><li>
GitHub 和 Issues</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>定制工具链模板<br><br>

 在美国南部、美国东部、德国、东京和英国可用

</td><td>
<br><br>
可以创建可供其他人使用的定制工具链模板。<br><br>

请参阅以下文档：
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">创建定制工具链模板 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a><br><br>
尝试以下教程：<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">为定制工具链创建模板 <img src="../../icons/launch-glyph.svg" alt="外部链接图标"></a></td>
<td>无
</td></tr>

</table>
