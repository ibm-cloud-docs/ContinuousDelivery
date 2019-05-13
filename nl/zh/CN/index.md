---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-01"

keywords: IBM Cloud Continuous Delivery, tool integration, toolchain template

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


# 入门教程
{: #getting-started}

使用 {{site.data.keyword.contdelivery_full}} 以采用 DevOps 方法，这包括用于自动构建和部署应用程序的开放式工具链。首先，可以创建简单部署工具链来支持开发、部署和操作任务。
{: shortdesc}


如果已有 {{site.data.keyword.contdelivery_short}} 的实例，那么可以[创建工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/devops/create){: new_window} 或[查看现有工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/devops/toolchains){: new_window}。
{: tip}


##先决条件
{: #cd_prereqs}

必须先在 {{site.data.keyword.Bluemix_notm}}“目录”中选择 {{site.data.keyword.contdelivery_short}} 的实例以创建该实例，然后才能从模板创建持续交付工具链。工具链将集成用于规划、开发、部署管道和管理应用程序的工具。您可以随时在工具链中添加或除去工具。如果已有工具链，那么可[查看现有工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing_a_toolchain){: new_window}。有关使用工具链的更多信息，请参阅[使用工具链](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using){: new_window}。


##步骤 1：选择工具链模板
{: #select_a_toolchain_template}

1. 在**创建工具链**页面上，单击[工具链模板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/devops/create){: new_window}。
1. 复查您要创建的工具链的图。该图按生命周期阶段显示工具链中的每一个工具集成。

 有一些工具链模板具有工具集成的多个实例。例如，{{site.data.keyword.Bluemix_notm}} Public 上的微服务工具链模板包含三个 GitHub 实例和三个 Delivery Pipeline 实例，每个实例都对应于三个微服务中的一个。
 {: tip}

 以下图像中的图是示例。创建工具链时，该图显示属于工具链的每一个工具集成。![工具链图](images/toolchain_diagram2.png)
 
##步骤 2：创建工具链 
{: #create_a_toolchain}
 
1. 复查工具链设置的缺省信息：

 * 工具链的名称在 {{site.data.keyword.Bluemix_notm}} 中起到标识符的作用。如果要使用其他名称，请更改工具链的名称。
 * 要在其中创建工具链的区域。如果要使用其他区域，请从可用区域列表中选择该区域。
 * 要在其中创建工具链的资源组或组织。单击链接以在选择资源组和组织之间进行切换。如果要使用其他资源组或组织，请从可用资源组或组织列表中选择该资源组或组织。
 
   资源组在美国南部、美国东部、德国、东京和英国区域可用。在美国南部、英国和德国区域支持 Cloud Foundry 组织。
   {: important}
 
1. 在“工具集成”部分中，选择要为工具链配置的每一个工具集成。有些工具集成无需进行配置。有关配置工具集成的信息，请参阅[配置工具集成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}。
1. 单击**创建**。此时将自动运行数个步骤，以设置工具链。设置的工具集成根据您所选的工具链模板以及您使用的是 {{site.data.keyword.Bluemix_notm}} Public 还是 {{site.data.keyword.Bluemix_notm}} Dedicated 而有所不同。例如，当您在 {{site.data.keyword.Bluemix_notm}} Public 上创建微服务工具链时，会运行以下步骤：

 * 将创建工具链。
 * 如果已配置 Delivery Pipeline，那么会创建并运行管道。
 * 如果已配置 Sauce Labs，那么会设置工具链以向管道添加 Sauce Labs 测试作业。
 * 如果已配置 PagerDuty，那么会设置工具链，以向指定的 PagerDuty 服务发送警报通知。
 * 如果已配置 Slack，那么会设置工具链，以向指定的 Slack 通道发送有关部署状态的通知。
 * 如果已配置源代码工具集成（如 GitHub），那么样本 GitHub 存储库会克隆到 GitHub 帐户。

##后续步骤
{: #next_steps}

查阅 [IBM&reg; Cloud Garage Method ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage){:new_window} 上的下列某个教程：

  * [使用“开发 Cloud Foundry 应用程序”工具链来创建和使用第一个工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。

  * [添加工具链至应用程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}。
 
