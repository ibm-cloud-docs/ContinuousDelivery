---

copyright:
  years: 2016, 2018
lastupdated: "2018-7-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 计划限制和使用
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}} 的使用限制为在 {{site.data.keyword.Bluemix_notm}} 平台或其他兼容平台即服务或基础架构即服务产品上，对应用程序进行构建、部署、测试和不间断的操作。

## 授权用户
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} 服务套餐基于服务实例的授权用户数来定义和定价。参与工作的任何人都必须计为一个授权用户，包括：

 * 与 {{site.data.keyword.gitrepos}} 存储库中的问题、问题板、源代码或其他工件进行交互的用户。
 * 操作、触发（在 UI 中直接触发或通过提交到存储库间接触发）交付管道或查看交付管道状态的用户。
 * 与 Eclipse Orion {{site.data.keyword.webide}} 交互的用户。
 
### 如何针对组织中 {{site.data.keyword.contdelivery_short}} 的实例对用户计数？

通过查看包含 {{site.data.keyword.contdelivery_short}} 服务的云组织中的所有用户来对授权用户计数。 

要查看 {{site.data.keyword.Bluemix_notm}} Public 环境的组织中的用户列表，请从菜单栏中，单击**管理 > 帐户 > Cloud Foundry 组织**。

要查看 {{site.data.keyword.Bluemix_notm}} Dedicated 环境的组织中的用户列表，请从菜单栏中，单击**帐户 > 管理组织**。

您还可以查看帐户中 {{site.data.keyword.contdelivery_short}} 服务的所有实例以及针对 {{site.data.keyword.Bluemix_notm}} Public 环境中的每个实例报告的用户数。

1. 从菜单栏中，单击**管理 > 计费和使用情况 > 使用情况**。
2. 单击**使用情况仪表板**。
3. 从“帐户”菜单中，单击 **Cloud Foundry 组织**。
4. 单击要查看其使用情况信息的组织。

要查看帐户中 {{site.data.keyword.contdelivery_short}} 服务的所有实例以及针对 {{site.data.keyword.Bluemix_notm}} Dedicated 环境中的每个实例报告的用户数：

1. 从菜单栏中，单击**帐户 > 管理组织**。
2. 单击**使用情况仪表板**。

### 如何针对资源组中 {{site.data.keyword.contdelivery_short}} 的实例对用户计数？

通过查看 {{site.data.keyword.contdelivery_short}} 服务实例中“管理”选项卡上的用户列表，对授权用户计数。 

要查看授权用户的列表，请打开服务实例仪表板，然后单击“管理”选项卡。

您还可以查看帐户中 {{site.data.keyword.contdelivery_short}} 服务的所有实例以及针对每个实例报告的用户数。

1. 从菜单栏中，单击**管理 > 计费和使用情况 > 使用情况**。
2. 单击**使用情况仪表板**。
3. 从“帐户”菜单中，单击**资源组**。
4. 单击要查看其使用情况信息的资源组。

### 超出服务套餐的限制时会发生什么情况？ 

某些服务套餐可能有其他限制，例如可以运行的 Delivery Pipeline 作业数或存储器消耗量。有关更多信息，请参阅目录中的套餐描述。如果在结算周期内超出任何套餐限制，那么该服务可能会暂挂。例如，Delivery Pipeline 作业可能不会在结算周期的剩余时间内运行。

## Delivery Pipeline 使用情况
{: #pipeline_usage}

可接受的使用行为包括但不限于以下行为：

* 对于受支持的编程语言，编译和组合工件
* 自动部署应用程序工件、配置和支持资源或服务
* 因开发流程而触发的测试、验证和其他开发事件生成行为

不允许的使用行为包括但不限于以下行为：

* 使用管道作业或工作程序进行一般计算行为，如比特币挖掘、分布式拒绝服务攻击和对 IBM Cloud 平台内的其他客户或用户或一般互联网用户的恶意或攻击行为
* 在正常开发流程中用于助长仇恨言论的站点或服务，或者违反 IBM 商业行为准则的其他活动。
* 使用事件生成行为，对 {{site.data.keyword.Bluemix_notm}} 或其他站点进行恶意侵入或攻击

如果用户违反了 {{site.data.keyword.contdelivery_short}} 服务或 [IBM 商业行为准则 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} 规定的可接受使用行为，那么 IBM 将酌情直接禁用而不另行通知。如果用户在收到攻击行为的通知后更正了其使用行为，IBM 将酌情复原一些服务。否则，可能会暂挂或终止帐户。

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
  2. 专用项目仅对选择的用户可见。有关授予用户项目访问权的详细信息，请参阅[项目用户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}。
  3. 内部项目对所有登录的用户可见。具有 {{site.data.keyword.Bluemix_notm}} 帐户的任何用户都可以查看这些项目。

您可以在项目的设置中修改项目类型。有关更多信息，请参阅[如何更改项目可视性 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}。

当您使用 {{site.data.keyword.gitrepos}} 时，您向项目提供的内容即获得该项目中指定的任何条款的许可。当您创建项目时，请包括描述适用于该内容的许可证的文件。当您提交至项目时，您与提交相关联的名称和电子邮件地址可能对公众可见。当您通过 {{site.data.keyword.gitrepos}} Web 界面创建提交时，会使用与 {{site.data.keyword.Bluemix_notm}} 帐户相关联的电子邮件地址。

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
