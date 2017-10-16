---

copyright:
  years: 2015, 2017
lastupdated: "2017-7-24"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 将 {{site.data.keyword.jazzhub_short}} 项目升级到工具链
{: #upgrade_projects}

{{site.data.keyword.jazzhub}} 逐步发展到 {{site.data.keyword.contdelivery_full}}。作为该变化的一部分，项目将升级到工具链。

您可以升级项目或等待其自动升级。为了获得最佳体验，请确保满足[先决条件](#upgrade_prereqs)并尽快升级项目，以便您可以控制工具链的名称以及在其中创建工具链的组织。
{: shortdesc}

**常见问题解答**

- [我的 JazzHub 项目与英国区域相关联，但我的工具链将在美国南部区域。这将如何运作？](#faq_region)
- [升级时，Track &amp; Plan 中的工作项和仪表板将发生什么？](#faq_tp)
- [升级时，代码存储库将发生什么？](#faq_repo)
- [升级到工具链时，项目中的构建定义将发生什么？](#faq_build)
- [我需要为将升级到工具链的我的项目创建组织。我了解我需要先向我的帐户添加信用卡，然后才能创建组织。要对我的信用卡进行收费吗？](#faq_charges)
- [我找不到或无法访问我的工具链。我该怎么做？](#faq_find)
- [我的项目与英国区域相关联。升级后，我看到错误消息，我的同事无法访问工具链，在 Bluemix 的“工具链”页面上看不到我的工具链。出了什么问题？](#faq_uk)

## 工具链
{: #compare_toolchains}

工具链与项目类似，但有以下几个重要的不同之处：

- 项目只能具有一个储存库和管道。工具链可以具有您所需的任意多个存储库和管道。
- 工具链可以包括项目中不可用的工具，如 Slack、Sauce Labs、PagerDuty 和 {{site.data.keyword.DRA_full}}。
- 工具链的访问权通过标准 {{site.data.keyword.Bluemix_notm}} 组织进行管理。成员资格在组织级别维护，这与项目不同，其成员资格在项目级别维护。

您可以在 [YouTube ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://youtu.be/2SIPE1e7NJ4){: new_window} 上或从 [{{site.data.keyword.contdelivery_short}} 入门](/docs/services/ContinuousDelivery/index.html)中了解工具链的相关信息。[![YouTube 的外部链接](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}


## 先决条件
{: #upgrade_prereqs}

- 要访问已升级的项目的工具链，您需要 {{site.data.keyword.Bluemix_notm}} 标识。在升级之前，必须验证您是否具有有效的 {{site.data.keyword.Bluemix_notm}} 标识。如果您没有，请进行[注册](https://console.ng.bluemix.net/registration/)。
- 确保您的 {{site.data.keyword.jazzhub_short}} 项目所有者正确。通过您的项目创建的工具链将成为该所有者的 {{site.data.keyword.Bluemix_notm}} 组织的一部分。
- 确保要在其中创建工具链的组织和空间位于美国南部区域的 {{site.data.keyword.Bluemix_notm}} Public 中。要确认您是否在美国南部具有有效的组织和空间，请登录到 [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}，并创建空间（如果系统提示您创建空间）。
- 如果您计划启动升级，请确保您是管道部署到的每个组织和空间的成员。任何项目管理员都可以启动升级。但是，如果启动升级的管理员不是管道部署到的每个组织和空间的成员，那么无法创建管道。启动升级的人员将成为工具链中存储库的所有者。
- 工具链中的 Eclipse Orion {{site.data.keyword.webide}} 独立于与项目相关联的 {{site.data.keyword.webide}}。如果您使用 {{site.data.keyword.webide}} 且您具有未提交的更改，请在升级之前先提交它们。


## 从项目升级到工具链
{: #project_to_toolchain}

**重要信息**：hub.jazz.net 上的项目以及工具链均在美国南部区域进行托管。如果您的项目配置为将应用程序部署到其他区域，那么该项目升级到工具链后，仍会将应用程序部署到美国南部区域。

当项目已就绪可以进行升级时，在项目的卡上和“概述”页面上会显示消息。

![具有“升级准备就绪”标签的卡的图像](images/card-project-to-upgrade.png)

![升级时间消息](images/banner-ready-to-upgrade.png)

**提示：**您可以在“我的项目”页面上，通过菜单查找准备升级的项目：

![“要升级的项目”菜单项的图像](images/menu-projects-to-upgrade.png)

启动升级后，将锁定项目中的管道阶段。您将无法运行或修改这些阶段。如果通过删除工具链来还原升级，那么会解锁管道。

如果项目使用的是在 JazzHub 上托管的 Git 存储库，那么在启动升级后，会锁定该存储库以确保移至工具链的数据的完整性。如果通过删除工具链来还原升级，那么会解锁 JazzHub 上的存储库。

有关如何在升级过程中处理每种类型的存储库的完整详细信息，请参阅下表。

|项目存储库|项目类型|工具链存储库|
|:----------|:------------------------------|:------------------|
|github.com|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上的相同 github.com 存储库。|
|hub.jazz.net/git|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上 {{site.data.keyword.gitrepos}} 中的新存储库。|
{: caption="表 1. 映射到工具链存储库的项目存储库" caption-side="top"}

## 启动升级过程
{: #start_upgrade}

在启动升级过程之前，您可以在 [YouTube ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://youtu.be/LSr2e3uvyLs){: new_window} 上观看其运行。[![YouTube 的外部链接](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}


要将项目升级到工具链，请遵循以下步骤：

1. 要启动升级过程，请在条幅消息上，单击**立即升级**。此时将打开“项目升级工具链”页面。

   ![升级页面的示例](images/project-upgrade-toolchain.png)

   如需升级过程的概述，请阅读该页面上的描述。工具链将包含新的管道，其包含与项目管道相同的阶段和作业。此外，工具链还包含指向 {{site.data.keyword.contdelivery_short}} 中运行的 Eclipse Orion {{site.data.keyword.webide}} 的指针。

   在此示例中，因为项目使用 github.com 上的公共存储库，所以工具链将连接到相同的 GitHub 存储库。如果项目使用的是在 JazzHub 上托管的 Git 存储库，那么会将该存储库的内容克隆到作为 {{site.data.keyword.contdelivery_short}} 一部分的 {{site.data.keyword.gitrepos}} 中的新存储库。

2. 要定制工具链，您可以配置一些设置：

   - 要更改工具链的名称，请编辑**名称**字段。

      ![名称字段](images/name-change.png)

   - 要更改要在其中创建工具链的 {{site.data.keyword.Bluemix_notm}} 组织，请从帐户菜单中选择组织：

      ![Bluemix 组织选择器](images/bluemix-organization-chooser.png)

   因为工具链在组织级别管理，所以请确保选择需要访问工具链的项目成员已经存在或者可以添加的组织。

3. 如果在项目中使用了 Track & Plan，那么可以将 Track & Plan 数据传输到 GitHub Issues。

   ![Track and Plan 选项](images/upgrade-tutorial-track-and-plan.png)

   - 指示是否要迁移 Track & Plan 数据。
   - 缺省情况下，将迁移所有 Track & Plan 数据。如果希望仅迁移属于特定查询的工作项，请指定该查询。
   - 选择要映射到 GitHub Issues 中标签的任何工作项属性。

4. 单击**创建**。此时将创建新的工具链，同时显示其“概述”页面。

   ![已升级工具链的概述](images/new-toolchain-page.png)

   - 要访问 GitHub 存储库或相关联的问题跟踪程序，请单击 **GitHub** 或 **Issues**。
   - 要访问管道，请单击 **Delivery Pipeline**。
   - 要访问 {{site.data.keyword.webide}}（其包含检出至工作空间的存储库内容），请单击 **Eclipse Orion {{site.data.keyword.webide}}**。

   如果在升级期间返回到您的项目，那么可能会有条幅消息声明正在进行升级，尤其是升级过程涉及将源代码导入到新存储库或将 Track &amp; Plan 工作项作为问题导入时。

   ![有关要升级到工具链的项目的消息](images/project-being-upgraded-banner.png)

## 重新访问项目
{: #revisit_projects}

您已准备好使用新的工具链。现在，您的项目标签为“已升级”，且在“概述”页面上，会显示确认消息。

![具有“已升级”标签的项目卡的图像](images/card-upgraded-project.png)

![已升级的项目](images/banner-upgraded.png)

您可以在“我的项目”页面上，从菜单选择**已升级的项目**来查看哪些项目已升级。

![“已升级项目”菜单项的图像](images/menu-upgraded-projects.png)

如果您需要还原升级，请删除工具链。可以从工具链的“概述”页面上的**更多操作**菜单中删除工具链：

![“更多操作”菜单中“删除”操作的图像](images/upgrade-tutorial-delete-toolchain.png)

返回到您的项目时，会再次显示升级消息，您可以在准备就绪后再次升级。

## 后续步骤
{: #upgrade_next_steps}

1. 通过刷新浏览器，并检查项目“概述”页面上是否有消息称项目“已升级到此工具链”，从而确认升级是否完成：

   ![条幅中指示项目已升级的消息](images/banner-upgraded.png)

   **注**：如果消息为“立即升级”，说明升级失败。请单击**立即升级**链接以重试。

   ![条幅中指示项目准备好升级的消息](images/banner-ready-to-upgrade.png)

2. 为团队成员提供工具链的访问权。
    - 每个团队成员都必须具有有效的 {{site.data.keyword.Bluemix_notm}} 帐户。没有帐户的团队成员必须进行[注册 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/registration){:new_window}。
    - 在工具链的“管理”页面中，授予组织成员对工具链的访问权。在升级过程中，会将现有项目成员添加为工具链的成员。有关工具链访问控制的更多信息，请参阅[管理访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}。
    - 如果用户不是工具链所属的组织的成员，请通过“管理组织”页面将其添加到该组织。
    - 如果工具链使用 {{site.data.keyword.gitrepos}}，那么具有有效 Bluemix 标识且具有与 JazzHub 项目中相同特权的所有 JazzHub 项目成员都将添加到 {{site.data.keyword.gitrepos}} 存储库。如果 JazzHub 项目包含的成员没有有效的 Bluemix 标识，那么这些成员应该注册 Bluemix 标识后，再添加到存储库。有关管理组织的更多信息，请参阅[管理组织和空间 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}。

3. 从工具链使用工具而非从 {{site.data.keyword.jazzhub_short}} 项目使用工具。例如，要从浏览器编辑代码，请从工具链使用 Web IDE。

4. 如果要使用 {{site.data.keyword.gitrepos}}，请通过个人访问令牌或 SSH 密钥进行认证。有关 SSH 密钥的更多信息，请参阅[创建个人访问令牌或 SSH 密钥以进行认证](/docs/services/ContinuousDelivery/git_working.html#git_authentication)。要从外部 Git 客户机通过 HTTPS 进行认证，请执行以下步骤：
    1. 转至 {{site.data.keyword.gitrepos}} 用户设置的[“访问令牌”页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window}。
    2. 创建将 **api** 用作作用域的个人访问令牌。
    3. 转至[“帐户”页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/account){:new_window} 并找到您用于 {{site.data.keyword.gitrepos}} 的用户名。您的用户名会列在“更改用户名”部分中，并且显示为所创建的任何个人存储库的 URL 的第一部分。
    4. 要从外部 Git 客户机通过 HTTPS 向 {{site.data.keyword.gitrepos}} 进行认证，请使用您的用户名和个人访问令牌。
    5. 如果要复用 JazzHub Git 存储库的本地存储库，请将该存储库指向 {{site.data.keyword.gitrepos}} 中的新存储库。从终端的 shell 中，切换到在其中克隆 JazzHub Git 存储库的目录。输入 `git remote set-url` 命令：`git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        **提示**：要检查哪些远程 URL 设置为哪些远程名称，请使用 `git remote -v` 命令。缺省远程名称为 `origin`。如果您有更高级的设置，那么该命令的格式如下：`git remote set-url<remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

5. 已设置工具链并开始使用时，请考虑执行以下所有或任何步骤以确保没有任何人使用您的项目：
    - 向您的项目名称添加后缀，以指示不得使用此项目。您可在项目名称末尾添加 `_DO_NOT_USE`。
    - 更新项目的描述，以提醒不再使用该项目，并添加指向工具链的指针。
    - 除去项目中的成员。
    - 不再需要项目时，将其删除。

6. 可选：要了解项目的开发成熟期、团队实践和代码库质量，请向工具链添加 IBM Cloud {{site.data.keyword.DRA_short}}。{{site.data.keyword.DRA_short}} 会将开发者、团队和部署分析应用于 DevOps 项目。有关更多信息，请参阅 [{{site.data.keyword.DRA_short}} 入门](/docs/services/DevOpsInsights/index.html)。


## 故障诊断
{: #upgrade_troubleshoot}

如果在升级过程中遇到问题，请尝试以下一个或多个故障诊断步骤：

- 检查[先决条件](#upgrade_prereqs)以确保满足这些条件。尤其是，请确保您是管道部署到的每个组织和空间的成员。
- 如果首次尝试升级期间发生此问题，并且您满足所有先决条件，请重试升级。
- 如果项目使用 Jazz SCM 或 IBM Hosted Git 进行源代码控制，请检查存储库的大小。如果大于 500 MB，请[联系 DevOps 服务团队 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}。
- 如果找不到工具链或无法访问工具链，请参阅[此常见问题解答条目](#faq_find)。
- 如果持续遇到问题，请在[支持论坛 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window} 上发布问题。在论坛帖子中，请包含 {{site.data.keyword.jazzhub_short}} 项目和 {{site.data.keyword.contdelivery_short}} 工具链的 URL，并使用 `devops-services` 标签来标记帖子。


## 常见问题解答
{: #upgrade_faq}

### 我的 JazzHub 项目与英国区域相关联，但我的工具链将在美国南部区域。这将如何运作？
{: #faq_region}

hub.jazz.net 上的项目以及工具链均在美国南部区域进行托管。如果您的项目配置为将应用程序部署到其他区域（如英国区域），那么该项目升级到工具链后，仍会将应用程序部署到该区域。因此，关于数据的托管位置，实际上并没有发生变化。未来，工具链将在更多区域可用。

### 升级时，Track &amp; Plan 中的工作项和仪表板将发生什么？
{: #faq_tp}

{{site.data.keyword.contdelivery_short}} 服务通过 {{site.data.keyword.gitrepos}} 提供问题跟踪功能，后者由 IBM 托管且以 GitLab Community Edition 为基础。{{site.data.keyword.contdelivery_short}} 还支持与其他规划和问题跟踪工具（如 GitHub Issues 和 JIRA）集成。

在升级过程中，您可以选择将 Track &amp; Plan 工作项迁移至 Git Issues。GitHub Issues 和 {{site.data.keyword.gitrepos}} 都提供看板和问题跟踪功能，以进行规划。要了解 Git Repos and Issue Tracking 中看板功能“问题板”的更多信息，请参阅[问题板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}。

对于需要与已弃用 JazzHub Track &amp; Plan 相同功能的客户来说，可以按月按用户在所选国家或地区个别购买新 IBM Track and Plan on Cloud 服务。使用此云服务，您将在单个租户云预订中，获得等同于 Rational Team Concert&trade; 内容添加者许可证的完整功能。

此新 IBM Track and Plan on Cloud 服务提供比已弃用 JazzHub Track &amp; Plan 更丰富的功能，支持流程定制、项目层次结构、SAFe&reg; 和许多其他灵活的混合方法，以及可成长超过单个项目的可扩展性。它以最新版本的 Rational Team Concert 6.0.3 为基础，将在未来 60 天内升级为 V6.0.4，而 JazzHub Track &amp; Plan 以 Rational Team Concert 5.x 为基础。通过其他服务，IBM Track and Plan on Cloud 可进行数据迁移。您可以联系相关产品 SaaS 销售主管 [Tom Hollowell ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:trhollow@us.ibm.com){:new_window}，以获取更多信息。

有关 IBM Track and Plan on Cloud 或在线购买的相关信息，请访问 [IBM Marketplace ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}。

要额外购买 Build Automation 和 Source Code Management，可以选择 [Rational Team Concert on Cloud ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window}。

### 升级时，代码存储库将发生什么？
{: #faq_repo}

在您升级之后，新 Git 服务将可与您之前所拥有的服务相媲美。如果您搭配使用 github.com 和 JazzHub 项目，那么您的工具链将连接至相同的 GitHub 存储库。如果您的 JazzHub 项目使用 IBM 托管的 Git，那么该存储库的内容将会克隆到 {{site.data.keyword.gitrepos}} 中的新存储库，其由 IBM 托管且为 {{site.data.keyword.contdelivery_short}} 的一部分。

有关如何在升级过程中处理每种类型的存储库的完整详细信息，请参阅下表。

|项目存储库|项目类型|工具链存储库|
|:----------|:------------------------------|:------------------|
|github.com|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上的相同 github.com 存储库。|
|hub.jazz.net/git|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上 {{site.data.keyword.gitrepos}} 中的新专用或公共存储库。|
{: caption="表 1. 映射到工具链存储库的项目存储库" caption-side="top"}


### 升级到工具链时，项目中的构建定义将发生什么？
{: #faq_build}

如果您使用 Jazz 而非 Delivery Pipeline 构建源代码，那么您必须手动将构建定义迁移到工具链的 Delivery Pipeline 中。

如果您使用 Jazz SCM 作为源存储库并使用 Delivery Pipeline 构建代码，那么 Jazz SCM 中的源代码将会自动移至 Git 存储库。Delivery Pipeline 配置仍保持不变，只是它将从 Git 存储库使用源代码而非从 Jazz SCM 使用源代码。

### 我需要为将升级到工具链的项目创建组织。我了解我需要先向我的帐户添加信用卡，然后才能创建组织。要对我的信用卡收费吗？
{: #faq_charges}

作为[现买现付客户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}，如果您使用任何运行时、服务或组件超过 Bluemix 目录中为其列出的免费限额，那么您需要付费。有关使用情况估算的信息，请参阅[价格表 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}。有关 Continuous Delivery 的当前定价，请参阅 [Bluemix 目录 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}。

如果您是 IBM 员工，内部 IBM 项目可以计入部门费用而非个人信用卡。如果您需要使用的资源超出 IBM 员工的免费限额，请创建支持凭单。

### 我找不到或无法访问我的工具链。我该怎么做？
{: #faq_find}

工具链在 Bluemix 组织中进行托管。升级过程会将 JazzHub 项目的所有成员添加到工具链。但是，除非 Bluemix 组织的所有者将这些用户添加到组织，否则这些用户将无法看到工具链。

要访问工具链，请转至 Bluemix，单击“菜单”图标，然后单击**服务 &gt; DevOps**。这将打开“工具链”页面。确保您位于美国南部区域，并且您所属的组织中包含该工具链。如果工具链未在“工具链”页面上列出，请参阅[此常见问题解答条目](#faq_uk)。

或者，在 JazzHub 站点仍可用期间，可以通过单击项目的“概述”页面上条幅中的链接转至工具链。

### 我的项目与英国区域相关联。升级后，我看到错误消息，我的同事无法访问工具链，在 Bluemix 的“工具链”页面上看不到我的工具链。出了什么问题？
{: #faq_uk}

**完整问题：**

我的 JazzHub 项目根据项目设置与 {{site.data.keyword.Bluemix_notm}} 英国区域相关联。我验证了项目设置，方法是转至 JazzHub 上的项目概述页面，单击**设置**图标（形似齿轮），然后单击**选项 &gt; 使此项成为 Bluemix 项目：区域**。但我将项目升级到位于美国的工具链后，发生了以下问题：

   1. 我选择美国组织时，看到一条消息称，该组织在美国南部地区没有空间，并且系统提示我创建空间。我不想在美国运行任何内容。
   
   2. 我的一些同事已经作为成员在原始 JazzHub 项目中列出，但仍无法访问工具链。如果他们尝试通过单击**查看工具链**从英国区域的“应用程序概述”页面来打开工具链，会看到“访问被拒绝”消息。
   
   3. 虽然我可以通过单击**查看工具链**直接从英国区域的“应用程序概述”页面访问工具链，但我在位于 [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} 的“我的工具链”页面上看不到该工具链列出。我要么收到错误信息说我无法修改工具链；要么收到错误信息说我没有工具链，需要创建工具链。 

**回答：**

如果您来自非美国的 {{site.data.keyword.Bluemix_notm}} 组织，并且未在升级之前将组织显式扩展到美国南部区域，那么可能会发生这些问题。您可以通过以下两种方式来进行确认：

   * 打开工具链 URL 时，检查 {{site.data.keyword.Bluemix_notm}} 标题。最有可能的情况是，您将看到您的组织名称，但不会指示任何空间。
   
   * 从工具链的“概述”页面中，单击**管理**。在“访问控制”页面上，单击**组织管理员**链接。包含工具链的组织将列在主页面上。

发生的情况是，在升级时，您的非美国组织在美国不存在，因此升级通过查找您刚好有权访问的另一个组织而为您选择了该组织。

如果切换到美国的该 {{site.data.keyword.Bluemix_notm}} 组织，就可以找到工具链。如果您将同事添加到该组织，即授予他们相应的访问权。此工具链可以继续部署到您的非美国组织。唯一的问题是这两个组织是不同的；您无法自动执行对这两个组织的用户管理。

如果希望工具链位于与非美国组织相匹配的美国组织中，请执行以下步骤：

   1. 登录到 [https://console.bluemix.net ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net){: new_window}，然后选择您所属的非美国区域和组织。
   
   2. 在 {{site.data.keyword.Bluemix_notm}} 标题中，切换到美国南部区域。系统将提示您在该区域中创建空间。
   
   3. 在美国南部区域创建空间，以将组织扩展到该区域。 
   
   4. 删除通过升级过程创建的工具链。 
   
      **注：**不会自动删除 Git 存储库。目前，您可能希望手动将其删除或将其重命名。如果已经对其进行了更改，那么可以日后切换未来的工具链以使用该存储库。

   5. 返回到 JazzHub 项目。此项目应该已自行重置以再次尝试升级。如果未重置，请联系 hub@jazz.net 并提供此项目的 URL。
   
   6. 重新启动升级过程，并确保在美国选择正确的组织，让该组织名称与非美国区域中的组织名称相匹配。
   
   7. 如果保留或重命名先前工具链升级尝试的 Git 存储库（请参阅步骤 4），那么可以改为将工具链中的 Git 卡重新配置为指向此 Git 存储库 URL。更改会自动反映在管道中。要进行确认，请检查“构建”阶段上的“输入”选项卡。

