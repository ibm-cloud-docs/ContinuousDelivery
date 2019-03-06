---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:tip: .tip}
{:important: .important}

# 使用工具链
{: #toolchains-using}

{{site.data.keyword.Bluemix}} 上的 Public 和 Dedicated 环境中可使用开放式工具链。您可以使用工具链，以使日常开发、部署和操作工作更富成效。设置工具链之后，您可以添加、删除或配置工具集成，并管理对工具链的访问。
{: shortdesc}

您可以使用资源组在美国南部、美国东部、英国、德国和东京公共区域管理工具链。您可以使用 Cloud Foundry 组织在美国南部、英国和德国公共区域管理工具链。根据工具链是包含在资源组还是 Cloud Foundry 组织中，工具链的访问控制和授权用户管理以不同方式运行。
{: important}

## 配置工具集成
{: #configuring_a_tool_integration}

如果创建工具链时延迟了工具集成的配置，那么其卡上会显示**配置**按钮。如果创建工具链时配置了工具集成，那么可以更新配置设置。

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 如果您需要全新配置工具集成，请在其卡上，单击**配置**。

  ![“配置”按钮](images/toolchain_tile_configure.png)

 完成配置工具集成时，单击**保存集成**。

1. 如果您需要更新工具集成的配置，请在其卡上，单击菜单以访问配置选项。

  ![“配置”菜单](images/toolchain_tile_menu.png)

 有一些工具集成已经过预配置，不需要任何配置参数。您仅可以针对您所配置的工具集成更新配置设置。
 {: tip}

 完成更新设置时，单击**保存集成**。有关配置特定工具集成的更多信息，请参阅[配置工具集成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}。

## 添加工具集成
{: #adding_a_tool_integration}

您可以为工具链添加和配置工具集成。可用的工具集成根据您是使用 {{site.data.keyword.Bluemix_notm}} Public 还是 {{site.data.keyword.Bluemix_notm}} Dedicated 而有所不同。

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 要查看要添加的工具集成列表，请单击**添加工具**。
1. 单击要添加的工具集成。
1. 输入配置工具集成所需的任何信息。
1. 单击**创建集成**，以向工具链添加工具集成。

## 删除工具集成
{: #deleting_a_tool_integration}

如果从工具链删除工具集成，那么该删除操作无法撤销。

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 在要删除的工具集成的卡上，单击菜单以访问配置选项。
1. 要从工具链删除工具集成，请单击**删除**。
1. 单击**删除**以确认。  

## 管理对资源组中工具链的访问权
{: #managing_access_resource_groups}

您可以使用 Identity and Access Management (IAM) 服务来管理用户对工具链的访问权。有关使用 IAM 管理访问控制的更多信息，请参阅[使用 Identity and Access Management 管理用户对工具链的访问权](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}。 

仅当用户存在于所选的 {{site.data.keyword.contdelivery_short}} 实例的授权用户列表中时，才能使用 Delivery Pipeline、Eclipse Orion {{site.data.keyword.webide}} 和 {{site.data.keyword.contdelivery_short}} 工具链的 {{site.data.keyword.gitrepos}} 功能。在指定的资源组中，您可以从所选 {{site.data.keyword.contdelivery_short}} 实例的“管理”选项卡来管理授权用户权利。

要访问工具链中 {{site.data.keyword.contdelivery_short}} 的关键功能，例如，Delivery Pipeline，用户必须具有 IAM 中工具链的访问权，并且用户还必须属于 {{site.data.keyword.contdelivery_short}} 实例的“授权用户”列表。
{: important}

授权用户权利应用于与 {{site.data.keyword.contdelivery_short}} 的实例的相同资源组中包含的所有工具链。
{: tip}


## 管理对 Cloud Foundry 组织中工具链的访问权
{: #managing_access_orgs}

您可以通过将用户添加到与工具链相关联的组织，以及工具链的访问控制表，对用户授予工具链的访问权。每一个工具链都与特定组织相关联，且属于该组织成员的任何用户都可以添加到任何相关联工具链的访问控制表中。您当前正为之工作的组织会显示在菜单栏上。要访问不同的工具链集，请切换到不同的组织。

必须在托管工具链的区域中向工具链的组织添加用户。如果工具链配置为将应用程序部署到其他区域，那么它仍会将应用程序部署到美国南部区域。
{: important}

将用户添加到 {{site.data.keyword.Bluemix_notm}} 组织和空间时，如果您使用 {{site.data.keyword.Bluemix_notm}} Dedicated for {{site.data.keyword.ghe_short}}，那么用户可以使用他们的 {{site.data.keyword.Bluemix_notm}} 标识和密码登录到 {{site.data.keyword.ghe_short}}。用户登录之后，将为他们创建帐户。将用户添加到 {{site.data.keyword.Bluemix_notm}} 组织和空间时，他们不会自动添加到 {{site.data.keyword.ghe_short}} 存储库。必须由具有存储库管理权限的人员进行添加。有关更多信息，请参阅[使用 Dedicated GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started){: new_window}。如果您使用自己的 {{site.data.keyword.ghe_short}} 受管版本，请遵循内部过程。

###管理工具链访问权的提示

* 要管理工具链访问权，请在 DevOps 仪表板的**工具链**页面上，单击要管理的工具链，然后单击**管理**。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**管理**。

* 要将访问权授予工具链的组织的所有成员，请单击**添加组织**。该组织的所有成员都可以查看该工具链。

* 您可以将管理特权授予某个组织或用户。管理员可以修改和删除工具链。要授予管理特权，请针对该组织或用户，选择 **ADMIN** 复选框。

* 如果您针对某个组织选择 **ADMIN** 复选框，那么该组织的所有成员都会成为管理员。如果您在对组织授予管理特权后向组织添加成员，那么那些成员会被授予组织其余成员一样的访问权。

* 要对属于工具链组织成员的用户授权访问权，请输入用户标识并单击**添加用户**。该用户可以查看工具链。

* 要对非工具链组织成员的用户授权访问权，请遵循以下步骤：

   a. 从菜单栏中，单击**管理 > 访问权 (IAM)**。

   b. 单击**访问权从该用户开始**。
   
   c. 从要分配访问权的用户的行中，选择**操作**菜单，然后单击**分配访问权**。
   
   d. 单击**使用 Cloud Foundry 分配访问权**。

   e. 选择**分配组织**。

   f. 分配用户访问权：

     * 选择要将用户添加到的组织。

     * 分配组织角色。

     * 选择区域。

     * 选择空间。

     * 为组织中的所选空间分配角色。

     缺省情况下，组织管理者对与组织相关联的所有工具链具有完全的管理特权。要向用户授予完全的管理特权，请选择**管理者**角色。“记帐管理者”和“审计员”角色不会影响工具链访问权。您可以日后在“团队目录”页面上更改这些角色。有关更多信息，请参阅 [Cloud Foundry 角色](/docs/iam?topic=iam-cfaccess#cfaccess){: new_window}。
     {: tip}

   在用户成为组织的成员后，返回到工具链的“管理”页面，并将用户添加到工具链。  


## 删除工具链
{: #deleting_a_toolchain}

您可以删除工具链，并指定您要删除的相关联工具集成。如果删除工具链，那么该删除操作无法撤销。

1. 在 DevOps 仪表板的**工具链**页面上，单击要删除的工具链。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**。
1. 单击**更多操作**菜单，其位于**查看应用程序**的旁边。
1. 单击**删除**。删除工具链将除去其所有工具集成，这可能删除由那些集成管理的资源。
1. 通过输入工具链的名称并单击**删除**，以确认删除。  

 当您删除 GitHub、{{site.data.keyword.ghe_short}} 或 {{site.data.keyword.gitrepos}} 工具集成时，不会从 GitHub、{{site.data.keyword.ghe_short}} 或 {{site.data.keyword.gitrepos}} 删除相关联的存储库。您必须手动除去存储库。
 {: tip}

##学习教程：使用工具链
{: #toolchain-tutorial}

在 [IBM&reg; Cloud Garage Method ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage){:new_window} 上查阅以下教程：

  * [使用“开发 Cloud Foundry 应用程序”工具链来创建和使用第一个工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。

  * [添加工具链至应用程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}。

  * [使用“在 Cloud Foundry 上开发和测试微服务”工具链 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}。
