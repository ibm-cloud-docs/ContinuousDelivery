---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# 计划限制和使用
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}} 的使用限制为在 {{site.data.keyword.Bluemix_notm}} 平台或其他兼容平台即服务或基础架构即服务产品上，对应用程序进行构建、部署、测试和不间断的操作。

## 服务实例的作用域
{: #service_scope}

您必须具有 {{site.data.keyword.contdelivery_short}} [服务实例](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}才能创建和使用 DevOps 工具链。服务实例可能属于 {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) [资源组](/docs/services/resources?topic=resources-rgs)或 {{site.data.keyword.Bluemix_notm}} 组织。

只能在资源组中创建 {{site.data.keyword.contdelivery_short}} 服务的*新*实例。当前不支持将工具链从组织迁移到资源组。如果缺少包含工具链的组织的 {{site.data.keyword.contdelivery_short}} 服务，那么可以在资源组中再次创建工具链，或者联系 [IBM 支持人员](https://cloud.ibm.com/unifiedsupport){:external}以获取帮助。

每个帐户只能有一个轻量服务。如果要在多个组织或资源组中或在多个区域中使用工具链，建议您使用专业套餐。
{: tip}


## 授权用户
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [服务套餐](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}基于服务实例的授权用户数来定义和定价。参与工作的任何人都必须计为一个授权用户，包括：

 * 与 {{site.data.keyword.gitrepos}} 存储库中的问题、问题板、源代码或其他工件进行交互的用户。
 * 操作、触发（在用户界面中直接触发或通过提交到存储库间接触发）交付管道或查看交付管道状态的用户。
 * 与 Eclipse Orion {{site.data.keyword.webide}} 交互的用户。
 
轻量套餐存在限制。有关轻量套餐和专业套餐的更多信息，请参阅[服务目录](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}。
{: tip}
 
### 如何针对资源组中 {{site.data.keyword.contdelivery_short}} 的实例对用户计数？

通过查看授权用户列表来了解计费和轻量套餐限制，对每个服务实例的授权用户进行计数和管理。{{site.data.keyword.contdelivery_short}} 服务用户会自动添加到此列表。可以阻止用户访问工具链，并阻止用户自动添加到 {{site.data.keyword.contdelivery_short}} 服务实例。有关使用 IAM 从包含工具链的资源组（或从工具链本身）中除去用户访问权的更多信息，请参阅[使用 Identity and Access Management 管理用户对 {{site.data.keyword.contdelivery_short}} 的访问权](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security)。 

用于在资源组中组织工具链的方法直接影响用户访问权和计费。用户在多个资源组中使用工具链时，会对这些资源组中的每个服务的工具链计数并相应计费。
{: tip}

可以在 {{site.data.keyword.contdelivery_short}} 服务实例的**管理**选项卡上管理授权用户的列表。

1. 转至 {{site.data.keyword.Bluemix_notm}} 帐户的[资源列表](https://cloud.ibm.com/resources){:external}。
2. 在**名称**列的过滤器文本框中，输入 **Continuous Delivery** 以显示现有服务。
3. 对于每个服务，单击**名称**列中的超链接。
4. 在**管理**选项卡中，可以根据需要查看、添加或除去授权用户列表中的用户。

用户使用 {{site.data.keyword.contdelivery_short}} 服务时，会自动添加或重新添加这些用户。
{: tip}

### 如何针对组织中 {{site.data.keyword.contdelivery_short}} 的实例对用户计数？

通过查看包含 {{site.data.keyword.contdelivery_short}} 服务的 {{site.data.keyword.Bluemix_notm}} 组织中的所有用户来对授权用户计数。有关组织和空间的更多信息，请参阅[创建组织和空间](/docs/cloud-foundry?topic=cloud-foundry-create_orgs)。

要查看 {{site.data.keyword.Bluemix_notm}} Public 环境的组织中的用户列表，请从菜单栏中，单击**管理 > 帐户**。然后，单击 **Cloud Foundry 组织**。

### 如何查看计费和使用情况信息？

您可以查看帐户中 {{site.data.keyword.contdelivery_short}} 服务的所有实例以及针对 {{site.data.keyword.Bluemix_notm}} Public 环境中的每个实例报告的用户数和管道执行数。

1. 从菜单栏中，单击**管理 > 计费和使用情况**。
2. 单击**使用情况**。
3. 在**服务**部分中，对于 {{site.data.keyword.contdelivery_short}} 服务，单击**查看套餐**。
4. 对于要查看其信息的套餐，单击**查看详细信息**。
5. 对于要查看其使用情况信息的 {{site.data.keyword.contdelivery_short}} 实例，单击**查看实例详细信息**。

`AUTHORIZED_USERS_PER_MONTH` 度量值是根据每天计数的用户数的每月平均值计算出的。
{: tip}

### 超出服务套餐的限制时会发生什么情况？

轻量服务套餐有其他限制，例如可以运行的 Delivery Pipeline 作业数或存储器消耗量。有关套餐描述的更多信息，请参阅[服务目录](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}。
如果在结算周期内超出任何套餐限制，那么该服务会暂挂。例如，Delivery Pipeline 作业不会在结算周期的剩余时间内运行。

## Delivery Pipeline 使用情况
{: #pipeline_usage}

可接受的使用行为包括但不限于以下行为：

* 对于受支持的编程语言，编译和组合工件。
* 自动部署应用程序工件、配置和支持资源或服务。
* 因开发流程而触发的测试、验证和其他由开发事件生成的行为。

不允许的使用行为包括但不限于以下行为：

* 使用管道作业或工作程序执行一般计算行为，如比特币挖掘、分布式拒绝服务攻击和对 {{site.data.keyword.Bluemix_notm}} 平台内的其他客户或用户或者一般因特网用户的恶意或攻击行为。
* 在正常开发流程中用于助长仇恨言论的站点或服务，或者违反 IBM 商业行为准则的其他活动。
* 使用事件生成的行为，对 {{site.data.keyword.Bluemix_notm}} 或其他站点进行恶意侵入或攻击。

如果用户违反了 {{site.data.keyword.contdelivery_short}} 服务或 [IBM 商业行为准则](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external}规定的可接受使用行为，那么 IBM 将酌情直接禁用这些用户而不另行通知。如果用户在收到攻击行为的通知后更正了其使用行为，IBM 将酌情复原一些服务。否则，可能会暂挂或终止帐户。

## Git Repos and Issue Tracking 限制
{: #git_limitations}

虽然 {{site.data.keyword.gitrepos}} 以 GitLab Community Edition 为基础构建且由 IBM 在 {{site.data.keyword.Bluemix_notm}} 上托管，但是仍有一些 GitLab 选项不可用：

 * 因为 {{site.data.keyword.deliverypipeline}} 为 {{site.data.keyword.Bluemix_notm}} 提供持续集成和持续交付，所以在 GitLab 中不支持持续集成功能。
 * GitLab 管理功能不可用，因为它们由 IBM 管理。
 * 可能无法完全访问 {{site.data.keyword.gitrepos}}。

## Git Repos and Issue Tracking 用户信息和内容
{: #git_projects}

可以使用三种 {{site.data.keyword.gitrepos}} 项目类型：

  1. 公共项目对所有站点访问者可见。公共项目中的内容对可访问 {{site.data.keyword.contdelivery_short}} 的所有人可见，即使他们未受邀加入该项目也是如此。
  2. 专用项目仅对精选的用户显示。有关向用户授予项目访问权的更多信息，请参阅[项目用户](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}。
  3. 内部项目对所有登录的用户可见。具有 {{site.data.keyword.Bluemix_notm}} 帐户的任何用户都可以查看这些项目。

您可以在项目的设置中修改项目类型。有关项目设置的更多信息，请参阅[如何更改项目可视性](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}。

当您使用 {{site.data.keyword.gitrepos}} 时，您向项目提供的内容即获得该项目中指定的任何条款的许可。当您创建项目时，请包括描述适用于该内容的许可证的文件。当您提交至项目时，您与提交相关联的名称和电子邮件地址可能对公众可见。当您通过 {{site.data.keyword.gitrepos}} Web 界面创建提交时，会使用与 {{site.data.keyword.Bluemix_notm}} 帐户相关联的电子邮件地址。
