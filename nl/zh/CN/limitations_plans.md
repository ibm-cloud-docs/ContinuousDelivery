---

copyright:
  years: 2016, 2017
lastupdated: "2017-7-24"
---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 计划限制和使用
{: #deliverypipeline_plans}
{: #free_deprecation}

{{site.data.keyword.contdelivery_full}} 的使用限制为在 {{site.data.keyword.Bluemix_notm}} 平台或其他兼容平台即服务或基础架构即服务产品上，对应用程序进行构建、部署、测试和不间断的操作。

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
