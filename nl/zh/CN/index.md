---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Continuous Delivery 入门
{: #cd_getting_started}

使用 {{site.data.keyword.contdelivery_full}} 以采用 DevOps 方法，这包括用于自动构建和部署应用程序的开放式工具链。首先，可以创建简单部署工具链来支持开发、部署和操作任务。
{: shortdesc}

通过从 {{site.data.keyword.Bluemix_notm}}“目录”中选择 {{site.data.keyword.contdelivery_short}} 来创建其实例后，可以通过模板创建持续交付工具链或使用现有工具链。![Continuous Delivery 欢迎页面](images/cd_landing_page2.png)

* 要通过模板创建并配置持续交付工具链，请单击**[从这里开始](#starting_from_a_toolchain_template)**。工具链将集成用于规划、开发、部署管道和管理应用程序的工具。您可以随时在工具链中添加或除去工具。
* 如果已经具有工具链，请在“从工具链模板开始”部分中，单击**查看工具链**。有关使用工具链的更多信息，请参阅[使用工具链](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}。

##{{site.data.keyword.contdelivery_short}} 概述
{: #cd_overview}

通过 {{site.data.keyword.contdelivery_short}}，您可以使用 DevOps 实践和业界领先的工具来构建、测试和交付应用程序。
{:shortdesc}

{{site.data.keyword.contdelivery_short}} 服务支持 DevOps 工作流程：

 * 可以创建集成 DevOps 开放式[工具链](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window}，以启用支持开发、部署和操作任务的工具集成。

  工具链是一组集成工具，可用于以协作方式开发、构建、部署、测试和管理应用程序并使得操作可重复使用且更易于管理。工具链可以包含开放式源代码工具、{{site.data.keyword.Bluemix_notm}} 服务（如 [{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window}）和第三方工具（如 GitHub、PagerDuty 和 Slack）。 
  
  **注**：{{site.data.keyword.DRA_short}} 仅在美国南部区域可用。

 * 使用自动化[管道](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window}持续交付。

  自动执行构建、单元测试、部署等操作。以可重复的方式进行构建、测试和部署，需要的人为干预最少。可随时发布到生产环境。

 * 使用[基于 Web 的 IDE](/docs/services/ContinuousDelivery/web_ide.html){: new_window} 从任意位置编辑并推送代码。

  在 GitHub 中创建、编辑、运行、调试和完成源代码控制任务。从编辑代码到将代码部署到生产环境，实现无缝衔接。 
  
 * 与您的团队协作，并使用由 IBM 托管且在 GitLab Community Edition 上构建的 [Git 存储库和问题跟踪程序](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window}来管理源代码。

  通过可让代码保持安全的精细访问控制来管理 Git 存储库。通过合并请求复查代码并加强协作。通过问题跟踪程序来跟踪问题并分享构想。在 Wiki 系统上记录项目。


##从工具链模板开始
{: #starting_from_a_toolchain_template}

要从[模板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/devops/create){: new_window} 创建并配置持续交付工具链，请执行以下操作：

1. 在**创建工具链**页面上，单击工具链模板。
1. 复查您要创建的工具链的图。该图按生命周期阶段显示工具链中的每一个工具集成。

 **提示**：有一些工具链模板具有工具集成的多个实例。例如，{{site.data.keyword.Bluemix_notm}} Public 上的微服务工具链模板包含三个 GitHub 实例和三个 Delivery Pipeline 实例，每个实例都对应于三个微服务中的一个。

 以下图像中的图是示例。创建工具链时，该图显示属于工具链的每一个工具集成。![工具链图](images/toolchain_diagram2.png)
1. 复查工具链设置的缺省信息：

 * 工具链的名称在 {{site.data.keyword.Bluemix_notm}} 中起到标识符的作用。如果要使用其他名称，请更改工具链的名称。
 * 要在其中创建工具链的区域。如果要使用其他区域，请从可用区域列表中选择该区域。
 * 要在其中创建工具链的组织。如果要使用其他组织，请从可用组织列表中选择该组织。
 
1. 在“工具集成”部分中，选择要为工具链配置的每一个工具集成。有些工具集成无需进行配置。有关配置工具集成的信息，请参阅[配置工具集成](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}。
1. 单击**创建**。此时将自动运行数个步骤，以设置工具链。设置的工具集成根据您所选的工具链模板以及您使用的是 {{site.data.keyword.Bluemix_notm}} Public 还是 {{site.data.keyword.Bluemix_notm}} Dedicated 而有所不同。例如，当您在 {{site.data.keyword.Bluemix_notm}} Public 上创建微服务工具链时，会运行以下步骤：

 * 将创建工具链。
 * 如果已配置 Delivery Pipeline，那么会创建并运行管道。
 * 如果已配置 Sauce Labs，那么会设置工具链以向管道添加 Sauce Labs 测试作业。
 * 如果已配置 PagerDuty，那么会设置工具链，以向指定的 PagerDuty 服务发送警报通知。
 * 如果已配置 Slack，那么会设置工具链，以向指定的 Slack 通道发送有关部署状态的通知。
 * 如果已配置源代码工具集成（如 GitHub），那么样本 GitHub 存储库会克隆到 GitHub 帐户。
