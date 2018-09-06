---

copyright:
  years: 2015, 2018

lastupdated: "2018-8-2"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 创建工具链
{: #toolchains_getting_started}

*工具链*是支持开发、部署和操作任务的一组工具集成。工具链的整体能力大于其各个单独工具集成的总和。
{: shortdesc}

{{site.data.keyword.Bluemix}} 上的 Public 和 Dedicated 环境中可使用开放式工具链。您可以使用两种方法来创建工具链：使用模板创建工具链，或者通过应用程序创建工具链。

每个工具链都与特定资源组或组织相关联。如果工具链与资源组相关联，那么只要用户对工具链资源具有 Identity and Access Management (IAM) 查看者许可权，或者对包含该工具链的资源组具有该许可权，就可以访问该工具链。如果工具链与组织相关联，那么只要是该组织的成员，任何用户都可以被添加到与该组织相关联的工具链的访问控制表中。有关 Cloud Foundry 组织中工具链的访问控制的更多信息，请参阅[管理对 Cloud Foundry 组织中工具链的访问权](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}。有关资源组中工具链的访问控制的更多信息，请参阅[管理对资源组中工具链的访问权](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window}。

##通过模板创建工具链   
{: #creating_a_toolchain_from_a_template}

您可以使用模板作为起始点来[创建工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/devops/create){: new_window}，其包含一组特定工具集成。了解如何通过 [IBM Cloud Garage Method ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/category/tools){:new_window} 使用模板的更多信息。

1. 如果您使用 {{site.data.keyword.Bluemix_notm}} Public，请登录到 [{{site.data.keyword.Bluemix_notm}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://console.bluemix.net){:new_window}。
1. 如果您使用 {{site.data.keyword.Bluemix_notm}} Dedicated，请登录到 {{site.data.keyword.Bluemix_notm}} 上的 Dedicated 环境。
1. 从 {{site.data.keyword.Bluemix_notm}} 菜单栏上的菜单中，单击 **DevOps**。
1. 在 DevOps 仪表板的**工具链**页面上，单击**创建工具链**。
1. 在**创建工具链**页面上，单击工具链模板。
1. 复查您要创建的工具链的图。该图按生命周期阶段显示工具链中的每一个工具集成。

 有一些工具链模板具有工具集成的多个实例。例如，{{site.data.keyword.Bluemix_notm}} Public 上的微服务工具链模板包含三个 GitHub 实例和三个 Delivery Pipeline 实例，每个实例都对应于三个微服务中的一个。
 {: tip}

 以下图像中的图是示例。创建工具链时，该图显示属于工具链的每一个工具集成。![工具链图](images/toolchain_diagram2.png)

1. 复查工具链设置的缺省信息：

 * 工具链的名称在 {{site.data.keyword.Bluemix_notm}} 中起到标识符的作用。如果要使用其他名称，请更改工具链的名称。
 * 要在其中创建工具链的区域。如果要使用其他区域，请从可用区域列表中选择该区域。
 * 要在其中创建工具链的资源组或组织。单击链接以在选择资源组和组织之间进行切换。如果要使用其他资源组或组织，请从可用资源组或组织列表中选择该资源组或组织。
 
   资源组仅在美国南部区域可用。
   {: tip}

1. 在“工具集成”部分中，选择要为工具链配置的每一个工具集成。有些工具集成无需进行配置。有关配置工具集成的信息，请参阅[配置工具集成](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}。
1. 单击**创建**。此时将自动运行数个步骤，以设置工具链。设置的工具集成根据您所选的工具链模板以及您使用的是 {{site.data.keyword.Bluemix_notm}} Public 还是 {{site.data.keyword.Bluemix_notm}} Dedicated 而有所不同。例如，当您在 {{site.data.keyword.Bluemix_notm}} Public 上创建微服务工具链时，会运行以下步骤：

 * 将创建工具链。
 * 如果已配置 Delivery Pipeline，那么会创建并触发管道。
 * 如果已配置 Sauce Labs，那么会设置工具链以向管道添加 Sauce Labs 测试作业。
 * 如果已配置 PagerDuty，那么会设置工具链，以向指定的 PagerDuty 服务发送警报通知。
 * 如果已配置 Slack，那么会设置工具链，以向指定的 Slack 通道发送有关部署状态的通知。
 * 如果已配置源代码工具集成（如 GitHub），那么样本 GitHub 存储库会克隆到 GitHub 帐户。


##通过应用程序创建工具链
{: #creating_a_toolchain_from_an_app}

您可以从应用程序创建工具链。工具链可以支持持续开发、部署、监视等操作，且与应用程序相关联。每一个应用程序都可以与工具链相关联。当您将更改推送到工具链的 GitHub 或 {{site.data.keyword.ghe_short}} 存储库时，管道会自动构建和部署应用程序。  

1. 在应用程序“概述”页面的“持续交付”卡上，单击**启用**。如果您使用 {{site.data.keyword.Bluemix_notm}} Public，那么将会对您的应用程序进行配置，以便可通过填充应用程序入门模板代码的新 GitHub 存储库，进行持续交付。如果您使用 {{site.data.keyword.Bluemix_notm}} Dedicated，那么将会对您的应用程序进行配置，以便可通过填充应用程序入门模板代码的新 GitHub 或 {{site.data.keyword.ghe_short}} 存储库，进行持续交付。
1. 在工具链创建页面上，复查您要创建的工具链的图。该图按生命周期阶段显示工具链中的每一个工具集成。
1. 复查工具链设置的缺省信息。工具链的名称在 {{site.data.keyword.Bluemix_notm}} 中起到标识符的作用。如果要使用其他名称，请更改工具链的名称。
1. 在“工具集成”部分中，选择要为工具链配置的每一个工具集成。有些工具集成无需进行配置。有关配置工具集成的信息，请参阅[配置工具集成](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}。
1. 单击**创建**。此时将自动运行数个步骤，以设置工具链。设置的工具集成根据您是在 {{site.data.keyword.Bluemix_notm}} Public 上还是在 {{site.data.keyword.Bluemix_notm}} Dedicated 上使用工具链而有所不同。例如，当您在 {{site.data.keyword.Bluemix_notm}} Public 上通过应用程序创建工具链时，会运行以下步骤：

 * 将创建工具链。
 * 如果已配置 Delivery Pipeline，那么会创建并触发管道。
 * 如果已配置 GitHub，那么样本 GitHub 存储库会克隆到 GitHub 帐户。


##查看工具链
{: #viewing_a_toolchain}

配置工具链及其工具集成之后，您可以查看工具链的可视化表示。

1. 在 DevOps 仪表板的**工具链**页面上，选择**资源组**或 **CLOUD FOUNDRY 组织**。将显示选中的资源组或 Cloud Foundry 组织中包含的所有工具链。单击想要查看的工具链以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**。然后，单击**概述**。
2. 要访问工具链中的工具集成，请单击工具。

 如果您具有多个 GitHub、{{site.data.keyword.ghe_short}} 或 Git 存储库，那么同一工具集成可能具有多个卡，因为每一个存储库由其自己的卡表示。如果您具有多个管道，那么同一工具集成可能具有多个卡，因为每一个管道由其自己的卡表示。例如，当您创建微服务工具链时，三个微服务中的每一个都具有自己的 GitHub、{{site.data.keyword.ghe_short}} 或 Git 存储库和自己的管道。
 {: tip}

## 学习教程：使用工具链
{: #toolchain_tutorials}

查阅 [IBM&reg; Cloud Garage Method ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage){:new_window} 上的下列某个教程：

  * [使用“开发 Cloud Foundry 应用程序”工具链来创建和使用第一个工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。

  * [添加工具链至应用程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}。

  * [使用“在 Cloud Foundry 上开发和测试微服务”工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}。
