---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 在 {{site.data.keyword.jazzhub_short}} 项目升级后开始使用工具链
{: #toolchains_post_upgrade}

hub.jazz.net 上的 {{site.data.keyword.jazzhub}} 项目已升级到 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}} 服务中的工具链。 

hub.jazz.net 上的 {{site.data.keyword.jazzhub_short}} 已撤销。 

对于 DevOps 项目，请使用 [{{site.data.keyword.contdelivery_short}} 服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/devops){:new_window}。如果您是 {{site.data.keyword.Bluemix_notm}} 的新用户，请务必查看 [{{site.data.keyword.Bluemix_notm}} 概述](/docs/overview/whatisbluemix.html#bluemixoverview)。

{: shortdesc}

## 查找基于项目创建的工具链
{: #find_toolchain}

通过转至[工具链页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/devops/toolchains){: new_window}，并验证显示的工具链名称是否与 hub.jazz.net 项目的名称相匹配，从而确认升级是否完成。如果项目已自动升级，请谨记以下注意事项：
   - 如果在升级项目之前另一个工具链已使用该项目的名称，那么为该项目创建的新工具链的名称可能与项目名称不完全相同。 
   - 如果未看到项目的工具链，请切换到您所属的其他任何组织并检查其中的工具链。
   - 如果依旧找不到某个项目的工具链，那么有可能升级仍在进行中。如果需要立即访问该工具链，请联系[支持人员 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}。

## 工具链概述
{: #compare_toolchains}

如果您在 hub.jazz.net 上有一个或多个项目，那么这些项目已自动升级到 {{site.data.keyword.contdelivery_short}} 服务中的工具链，除非升级失败。IBM Cloud 帐户或组织无效时，可导致升级失败。已通过电子邮件向这些帐户和组织所有者发送通知，告知升级失败以及解决这些问题时他们需要采取的特定操作。如果未看到项目的工具链，并且需要立即访问该工具链，请联系[支持人员 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}。 

工具链与项目类似，但有以下几个重要的不同之处：

- 项目只能具有一个储存库和管道。工具链可以具有您所需的任意多个存储库和管道。
- 工具链可以包括项目中不可用的工具，如 Slack、Sauce Labs、PagerDuty 和 {{site.data.keyword.DRA_full}}。

 **注**：{{site.data.keyword.DRA_short}} 仅在美国南部区域可用。
 
- 在项目中，成员资格在项目级别进行维护。对工具链的访问通过 {{site.data.keyword.Bluemix_notm}} 组织和工具链进行管理。要使用工具链，您必须是包含该工具链的组织的成员。工具链所有者有权进一步控制谁可以访问工具链以及他们可以执行的操作。有关详细信息，请参阅[工具链入门](#upgrade_next_steps)中的步骤 2。
- 根据在 hub.jazz.net 上您项目中使用的存储库的类型，工具链可能包含 GitHub.com 存储库或 {{site.data.keyword.gitrepos}} 存储库。

您可以在 [YouTube ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://youtu.be/2SIPE1e7NJ4){: new_window} 上或从 [{{site.data.keyword.contdelivery_short}} 入门](/docs/services/ContinuousDelivery/index.html)中了解工具链的更多信息。


## 工具链入门
{: #upgrade_next_steps}

1. 为团队成员提供工具链的访问权。
    - 每个团队成员都必须具有有效的 {{site.data.keyword.Bluemix_notm}} 帐户。没有帐户的团队成员必须进行[注册 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/registration){:new_window}。
    - 在工具链的“管理”页面中，授予组织成员对工具链的访问权。在升级过程中，会将现有项目成员添加为工具链的成员。有关工具链访问控制的更多信息，请参阅[管理访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}。
    - 如果用户不是工具链所属的组织的成员，请通过“管理组织”页面将其添加到该组织。
    - 如果工具链使用 {{site.data.keyword.gitrepos}}，那么具有有效 {{site.data.keyword.Bluemix_notm}} 标识的所有 JazzHub 项目成员将使用他们在 JazzHub 项目中拥有的相同特权添加到 {{site.data.keyword.gitrepos}} 存储库。如果 JazzHub 项目包含没有有效 {{site.data.keyword.Bluemix_notm}} 标识的成员，那么这些成员可以注册一个标识。这些成员注册后，就可以将其添加到存储库。有关管理组织的更多信息，请参阅[管理组织和空间 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}。

2. 如果要使用 {{site.data.keyword.gitrepos}}，请通过个人访问令牌或 SSH 密钥进行认证。有关 SSH 密钥的更多信息，请参阅[创建个人访问令牌或 SSH 密钥以进行认证](/docs/services/ContinuousDelivery/git_working.html#git_authentication)。要从外部 Git 客户机通过 HTTPS 进行认证，请执行以下步骤：
    1. 转至 {{site.data.keyword.gitrepos}} 用户设置的[“访问令牌”页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window}。
    2. 创建将 **api** 用作作用域的个人访问令牌。
    3. 转至[“帐户”页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/account){:new_window} 并找到您用于 {{site.data.keyword.gitrepos}} 的用户名。您的用户名会列在“更改用户名”部分中，并且显示为所创建的任何个人存储库的 URL 的第一部分。
    4. 要从外部 Git 客户机通过 HTTPS 向 {{site.data.keyword.gitrepos}} 进行认证，请使用您的用户名和个人访问令牌。
    5. 如果要复用 JazzHub Git 存储库的本地存储库，请将该存储库指向 {{site.data.keyword.gitrepos}} 中的新存储库。从终端 shell 中，切换到在其中克隆 JazzHub Git 存储库的目录。输入 `git remote set-url` 命令：`git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        **提示**：要检查哪些远程 URL 设置为哪些远程名称，请使用 `git remote -v` 命令。缺省远程名称为 `origin`。如果您有更高级的设置，那么该命令的格式如下：`git remote set-url<remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

3. 可选：要了解项目的开发成熟期、团队实践和代码库质量，请向工具链添加 IBM Cloud {{site.data.keyword.DRA_short}}。{{site.data.keyword.DRA_short}} 会将开发者、团队和部署分析应用于 DevOps 项目。有关更多信息，请参阅 [{{site.data.keyword.DRA_short}} 入门](/docs/services/DevOpsInsights/index.html)。

  **注**：{{site.data.keyword.DRA_short}} 仅在美国南部区域可用。


## 故障诊断
{: #upgrade_troubleshoot}

如果遇到与项目升级相关的问题，请在[支持论坛 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window} 上发布问题。在论坛帖子中，请包含 {{site.data.keyword.jazzhub_short}} 项目和 {{site.data.keyword.contdelivery_short}} 工具链的 URL，并使用 `devops-services` 标签来标记帖子。


## 常见问题解答
{: #upgrade_faq}

### 我的 JazzHub 项目与英国区域相关联，但我的工具链位于美国南部区域。这如何运作？
{: #faq_region}

hub.jazz.net 上的项目以及工具链均在美国南部区域进行托管。如果项目配置为将应用程序部署到其他区域（例如英国区域），那么工具链仍然会将应用程序部署到该区域。因此，关于数据的托管位置，实际上并没有发生变化。未来，工具链将在更多区域可用。

### 升级后，Track &amp; Plan 中的工作项和仪表板有什么变化？
{: #faq_tp}

{{site.data.keyword.contdelivery_short}} 服务通过 {{site.data.keyword.gitrepos}} 提供问题跟踪功能，后者由 IBM 托管且以 GitLab Community Edition 为基础。{{site.data.keyword.contdelivery_short}} 还支持与其他规划和问题跟踪工具（如 GitHub Issues 和 JIRA）集成。

在自动升级过程中，Track & Plan 工作项已迁移至 Git Issues。GitHub Issues 和 {{site.data.keyword.gitrepos}} 都提供看板和问题跟踪功能，以进行规划。要了解 Git Repos and Issue Tracking 中看板功能“问题板”的更多信息，请参阅[问题板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}。

如果您需要使用已弃用的 JazzHub Track &amp; Plan 中的功能，在特定国家或地区可以按月按用户购买新的 IBM Track and Plan on Cloud 服务。使用此云服务，您将在单个租户云预订中获得等同于 Rational Team Concert&trade; 参与者许可证的完整功能。

此新 IBM Track and Plan on Cloud 服务提供比已弃用 JazzHub Track &amp; Plan 更丰富的功能，支持流程定制、项目层次结构、SAFe&reg; 和许多其他灵活的混合方法，以及可成长超过单个项目的可扩展性。它以最新版本的 Rational Team Concert 6.0.3 为基础，将在未来 60 天内升级为 V6.0.4，而 JazzHub Track &amp; Plan 以 Rational Team Concert 5.x 为基础。通过其他服务，IBM Track and Plan on Cloud 可进行数据迁移。您可以联系相关产品 SaaS 销售主管 [Tom Hollowell ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](mailto:trhollow@us.ibm.com){:new_window}，以获取更多信息。

有关 IBM Track and Plan on Cloud 或在线购买的相关信息，请访问 [IBM Marketplace ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}。

要购买 Build Automation 和 Source Code Management，可以选择 [Rational Team Concert on Cloud ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window}。

### 升级后代码存储库有什么变化？
{: #faq_repo}

升级之后，新 Git 服务可与您之前所拥有的服务相媲美。如果您搭配使用 github.com 和 JazzHub 项目，那么您的工具链将连接到相同的 GitHub 存储库。如果您的 JazzHub 项目使用 IBM 托管的 Git，那么该存储库的内容会克隆到 {{site.data.keyword.gitrepos}} 中的新存储库，它由 IBM 托管并且是 {{site.data.keyword.contdelivery_short}} 的一部分。

有关如何在升级过程中处理每种类型的存储库的更多信息，请参阅下表。

|项目存储库|项目类型|工具链存储库|
|:----------|:------------------------------|:------------------|
|github.com|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上的相同 github.com 存储库。|
|hub.jazz.net/git|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上 {{site.data.keyword.gitrepos}} 中的新专用或公共存储库。|
|Jazz SCM|专用或公共|{{site.data.keyword.Bluemix_notm}} Public 上 {{site.data.keyword.gitrepos}} 中的新专用或公共存储库。|
{: caption="表 1. 映射到工具链存储库的项目存储库" caption-side="top"}


### 升级后，项目中的构建定义有什么变化？
{: #faq_build}

如果您使用了 Jazz 而非 Delivery Pipeline 来构建源代码，那么您必须手动将构建定义迁移到工具链中的 Delivery Pipeline。

如果您使用了 Jazz SCM 作为源存储库并使用 Delivery Pipeline 来构建代码，那么 Jazz SCM 中的源代码已自动移至 Git 存储库。Delivery Pipeline 配置保持不变，只是它使用 Git 存储库而非 Jazz SCM 中的源代码。

### 我必须为已升级到工具链的项目创建组织，所以我向帐户添加了信用卡。要对我的信用卡收费吗？
{: #faq_charges}

作为[现买现付客户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}，如果您使用任何运行时、服务或组件超过 {{site.data.keyword.Bluemix_notm}} 目录中为其列出的免费限额，那么您需要付费。有关使用情况估算的信息，请参阅[价格表 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}。有关 Continuous Delivery 的当前定价，请参阅 [{{site.data.keyword.Bluemix_notm}}“目录”![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}。


如果您是 IBM 员工，内部 IBM 项目可以计入部门费用而非个人信用卡。如果您需要使用的资源超出 IBM 员工的免费限额，请创建支持凭单。

### 我找不到或无法访问我的工具链。我该怎么做？
{: #faq_find}

工具链在 {{site.data.keyword.Bluemix_notm}} 组织中托管。升级过程会将 JazzHub 项目的所有成员添加到工具链。但是，除非 {{site.data.keyword.Bluemix_notm}} 组织的所有者将这些用户添加到组织，否则这些用户将无法看到工具链。

要访问工具链，请转至 {{site.data.keyword.Bluemix_notm}}，单击“菜单”图标，然后单击**服务 &gt; DevOps**。这将打开“工具链”页面。 确保您位于美国南部区域，并且您所属的组织中包含该工具链。如果工具链未在“工具链”页面上列出，请参阅[此常见问题解答条目](#faq_uk)。

### 我的项目与英国区域相关联。升级后，我看到错误消息，我的同事无法访问工具链，并且我在 {{site.data.keyword.Bluemix_notm}} 的“工具链”页面上看不到我的工具链。出了什么问题？
{: #faq_uk}

**完整问题：**

我的 JazzHub 项目根据项目设置与 {{site.data.keyword.Bluemix_notm}} 英国区域相关联。我验证了我的项目设置，方法是转至其在 JazzHub 上的项目概述页面，单击**设置**图标（形似齿轮），然后单击**选项 &gt; 使此项成为 {{site.data.keyword.Bluemix_notm}} 项目：区域**。但我将项目升级到位于美国的工具链后，发生了以下问题：

   1. 我选择美国组织时，看到一条消息称，该组织在美国南部地区没有空间，并且系统提示我创建空间。我不想在美国运行任何内容。
   
   2. 我的一些同事已经作为成员在原始 JazzHub 项目中列出，但仍无法访问工具链。如果他们尝试通过单击**查看工具链**从英国区域的“应用程序概述”页面来打开工具链，会看到“访问被拒绝”消息。
   
   3. 虽然我可以通过单击**查看工具链**直接从英国区域的“应用程序概述”页面访问工具链，但我在位于 [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} 的“我的工具链”页面上看不到该工具链列出。我要么收到错误信息说我无法修改工具链；要么收到错误信息说我没有工具链，需要创建工具链。 

**回答：**

如果您来自非美国的 {{site.data.keyword.Bluemix_notm}} 组织，并且未在升级之前将组织显式扩展到美国南部区域，那么可能会发生这些问题。您可以通过打开“工具链”页面来进行确认。您将在页面开头看到该地区和组织。 

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
   
   7. 如果保留或重命名先前工具链升级尝试的 Git 存储库（请参阅步骤 4），那么可以改为将工具链中的 Git 卡重新配置为指向此 Git 存储库 URL。更改会自动反映在管道中。要进行确认，请检查构建阶段上的“输入”选项卡。
