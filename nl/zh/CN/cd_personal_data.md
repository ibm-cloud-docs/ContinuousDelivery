---

copyright:
  years: 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 在 Continuous Delivery 中管理个人数据
{: #cd_personal_data}

可以在 {{site.data.keyword.contdelivery_full}} 中修改、导出或删除个人数据。
{: shortdesc}

个人数据是与自然人相关或用于识别自然人的任何信息。例如，个人数据可以是姓名、电子邮件地址、头像、令牌或用于 {{site.data.keyword.contdelivery_short}} 的任意数量的标识。以下 {{site.data.keyword.contdelivery_short}} 组件包含个人数据：

 * Eclipse Orion {{site.data.keyword.webide}}
 * {{site.data.keyword.gitrepos}}
 * {{site.data.keyword.contdelivery_short}} 管道
 * 工具链和工具集成
 * [GitHub Enterprise on IBM Cloud ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/ghededicated/ghe_personal_data.html){: new_window}
 * [{{site.data.keyword.DRA_full}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/DevOpsInsights/insights_personal_data.html){: new_window}
 
IBM 不管理 {{site.data.keyword.contdelivery_short}} 服务中的数据。在退出在 {{site.data.keyword.Bluemix_notm}} Public 中托管的 {{site.data.keyword.contdelivery_short}} 服务之前，必须删除自己的数据。
{: tip}

{{site.data.keyword.contdelivery_short}} 提供相应的许可权来管理资源组或 Cloud Foundry 组织内的数据。您的公司可能具有限制这些许可权的策略。如果您没有相应的许可权，请与您的 {{site.data.keyword.Bluemix_notm}} 帐户的管理员联系。

要管理个人数据，您必须了解 IBM Cloud 帐户、这些帐户的使用方式及其关联的访问权。
 
## 帐户和访问权
{: #accounts_access_rights}

要在 IBM Cloud 中工作，您必须使用用户名和密码登录。登录后，IBM Cloud 将至少使一个 IBM Cloud 帐户与您的用户凭证相关联。创建资源（如 Cloud Foundry 组织、资源组、工具链和 {{site.data.keyword.contdelivery_short}} 对象）时，这些资源会与 IBM Cloud 帐户相关联。

IBM Cloud 登录结构提供了在不同帐户中工作的选项。通过使用 IBM Cloud 用户界面，您可以从一个帐户切换到另一个帐户。登录时，以下任一类型的帐户都可能与您的用户凭证相关联： 

 * 个人帐户
 * 公司帐户
 * 公司个人帐户

###个人帐户

通常，每个用户都有自己的帐户，即其个人帐户。您可以轻松识别自己的个人帐户，因为该帐户通常包含您的姓名，如 *John Smith 的帐户*。 

您对个人帐户中创建的所有对象都具有完全权限。您可以邀请其他用户加入您的帐户，为这些用户分配对您所创建的对象的权限，以及为其分配在您帐户中创建对象的权限。这意味着其他用户的个人数据可能位于您的帐户中，而您的个人数据也可能位于其他用户的帐户中。 

如果您有权在帐户中创建对象，那么您也有权对其进行修改和删除，而不管对象存储在哪个帐户中。两个用户协作时，他们通常会共享一个个人帐户。

###公司帐户

公司帐户由您的公司设置。通常，会将您自动添加到该帐户，而不是邀请您加入。公司帐户向用户提供了一个工作、通信和共享资源并收费的场所；但是，这仅仅是约定。公司帐户实际上与个人帐户没有任何区别。在公司帐户中创建的对象将与该帐户相关联，并且可以邀请用户加入该帐户。

为公司工作的人员组成的团队通常使用公司帐户进行协作。

###公司个人帐户

为公司工作时，您帐户中的工作可能由该公司合法拥有。为公司工作的许多用户会拥有公司个人帐户。如果您登录到帐户时所使用的凭证包含公司名称，并且还包含看起来像是个人帐户的名称，那么您个人帐户中的工作可能属于该公司。

公司个人帐户与其他任何帐户都毫无区别。您可以邀请用户加入公司个人帐户，而在公司个人帐户中创建的对象归该帐户所有。

如果您为拥有您工作的公司工作，那么通常包含您姓名的个人帐户被视为公司个人帐户。 

## 修改、导出和删除个人数据
{: #managing_personal_data}

无论使用哪种类型的 IBM Cloud 帐户，如果您有权处理帐户中的对象，那么可以修改、导出和删除这些对象。在进行更改之前，请与其他用户进行协调，以确保不会不必要地修改或删除数据。

在删除帐户中的数据之前，请确定帐户是个人帐户还是公司个人帐户。

###个人帐户

如果您拥有个人帐户，那么可以更改和删除数据。如果您与其他用户共享您的帐户，那么您拥有这些数据，但您可能希望就共享工作与其他用户联系。 

如果您无法登录到 IBM Cloud 帐户，请[联系 IBM 支持 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/cloud/support){:new_window}
 
###公司个人帐户

如果您拥有公司个人帐户，那么进行任何更改时，都必须与公司和团队的其他成员协调。您可删除自己的个人数据，而不管这些数据是存储在公司帐户还是公司个人帐户中。确保不会删除与其他用户共享的工作。

在开始管理 {{site.data.keyword.contdelivery_short}} 组件的个人数据之前，请确保您正在 IBM Cloud 帐户中工作。要查看您当前正在其中工作的 IBM Cloud 帐户，请在菜单栏上单击您的个人档案头像。 

如果您无法登录到 IBM Cloud 帐户，请联系您的公司，并与其合作来删除您的个人数据。

如果要从 {{site.data.keyword.contdelivery_short}} 中删除您的所有个人数据，那么删除这些数据的顺序非常重要。首先，删除所有 {{site.data.keyword.webide}} 工作空间。接下来，删除 {{site.data.keyword.gitrepos}} 数据，然后删除 {{site.data.keyword.gitrepos}} 帐户。最后，删除交付管道、工具集成和工具链。
{: tip}

## 导出和删除 Web IDE 数据
{: #managing_web_ide_data}

{{site.data.keyword.webide}} 在云中提供个人工作空间。可以使用 {{site.data.keyword.webide}} 来克隆 Git 存储库并编辑文件。您拥有自己的 {{site.data.keyword.webide}} 工作空间；此工作空间不与其他任何帐户共享。

在删除 {{site.data.keyword.webide}} 数据之前，您可能要导出工作。删除工作空间后，将从 {{site.data.keyword.contdelivery_short}} 中除去这些工作空间，并删除所有文件。
{: tip}

###导出 Web IDE 工作空间

要导出 {{site.data.keyword.webide}} 工作空间，请执行以下操作：

1. 选择**文件 > 导出 > Zip**。
1. 对要导出的每个工作空间重复此操作。

###删除 Web IDE 工作空间

要删除 {{site.data.keyword.webide}} 工作空间（包括您的所有个人数据），请执行以下操作：

1. 在任何工具链中，浏览至 {{site.data.keyword.webide}}。
1. 单击左侧导航侧边栏中的**设置**图标 <img class="inline" src="images/webide_settings_icon_light_small.png" alt="“设置”图标">。
1. 单击**用户个人档案**。
1. 单击**删除**以从 {{site.data.keyword.webide}} 中除去您的所有数据。

{{site.data.keyword.webide}} 使用单点登录机制。首次访问此工具集成时，会为您的 IBM Cloud 帐户创建一个对应的 {{site.data.keyword.webide}} 帐户，但会隐藏该帐户。删除所有工作空间后，不要访问 {{site.data.keyword.webide}}。如果再次访问 {{site.data.keyword.webide}}，系统将自动创建一个新帐户，您必须将其删除。
{: tip}

## 修改、导出和删除 Git Repos and Issue Tracking 数据
{: #managing_grit_data}

{{site.data.keyword.gitrepos}} 在云中提供托管的 Git 服务。单点登录机制用于使 IBM Cloud 帐户与 Git 帐户相关联。将在 Git 帐户中为您创建全名和短名称。其他用户可以使用您的短名称在 Git 问题内的注释中提及您。您可以定制 Git 帐户并添加个人数据，例如您本人的描述或图像。 

{{site.data.keyword.gitrepos}} 提供了功能强大而又复杂的社交编码环境，在该环境中，用户可向不同的项目添加内容，并且对象是共享的。在此环境中，可能很难找到并删除个人数据。

您的帐户个人档案和设置、个人项目、组和片段都与 Git 帐户相关联。如果删除 Git 帐户，那么将删除这些对象。要删除其他项目中的个人数据，请浏览至该项目，然后对其进行修改以除去个人数据，或者删除整个项目。在删除共享项目之前，请确保与团队的其他成员进行协调。

在删除 Git 帐户之前，请从其他项目中删除您的个人数据。删除 Git 帐户后，可能很难或者无法查找您向其添加了内容的所有项目。
{: tip}

###个人项目和共享项目

您可以邀请其他用户在项目中进行协作。在帐户内创建的 Git 项目称为个人项目。您还可以创建 Git 组，在其中项目可由多个 Git 所有者拥有。您可以为组创建新项目，也可以将个人项目的所有权转移到组。Git 组通常用于表示 IBM Cloud 公司帐户，以指示公司对项目的所有权。

###导出 Git Repos and Issue Tracking 项目

删除 {{site.data.keyword.gitrepos}} 项目之前，可以导出该项目以对其进行归档。 

1. 单击左侧导航侧边栏中的**设置**图标 <img class="inline" src="images/webide_settings_icon_light_small.png" alt="“设置”图标">。
1. 单击**常规**。
1. 单击**展开**以展开“导出项目”部分。
1. 单击**导出项目**。

对项目归档后，可以将其导入到其他 GitHub 实例。 

###删除 Git Repos and Issue Tracking 帐户

您可以删除自己的 {{site.data.keyword.gitrepos}} 帐户以及该帐户所拥有的所有内容。

1. 在 {{site.data.keyword.gitrepos}}“用户设置”仪表板的[“帐户”页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}的“删除帐户”部分中，单击**删除帐户**。
1. 这将删除所有 Git 项目，包括存储库和问题。此外，还会从您所属的任何 {{site.data.keyword.gitrepos}} 组中将您除去。

删除帐户后，某些内容会保留。这些内容会分配给系统范围的 Ghost 用户。有关删除 {{site.data.keyword.gitrepos}} 帐户的更多信息，请参阅[删除用户帐户 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/account/delete_account#associated-records){:new_window}。
{: tip}

{{site.data.keyword.gitrepos}} 使用单点登录机制，该机制会在您首次访问工具集成时，自动为您的 IBM Cloud 帐户创建相应的 Git 帐户。删除您的帐户后，不要访问 {{site.data.keyword.gitrepos}}。如果再次访问 {{site.data.keyword.gitrepos}}，系统将自动创建一个新帐户，您必须将其删除。
{: tip}

## 修改、导出和删除 Continuous Delivery 管道数据
{: #managing_pipeline_data}

{{site.data.keyword.contdelivery_short}} 管道运行脚本来构建和测试应用程序，以及将应用程序部署到 IBM Cloud。为此，管道提供了阶段、作业、环境变量和其他可能包含个人数据的对象。您可以单独删除这些对象，也可以删除整个管道。

在删除共享对象或管道之前，请确保与团队的其他成员进行协调。删除阶段可能会导致管道发生故障。

管道不能存在于工具链外部。如果删除工具链，与该工具链关联的所有管道也将一并删除。如果计划删除整个工具链，那么无需单独删除每个管道。请改为跳至“修改和删除工具链与工具集成”部分，然后执行相关步骤来删除工具链。
{: tip}

管道阶段可能包含个人数据，例如以环境属性形式提供的凭证以及显示管道的当前状态的管道定义。阶段还可能包含要修改或删除的作业中的脚本，以及要导出的最新管道运行的工件和日志。使用“配置阶段”或“删除阶段”操作来修改或删除阶段。使用“下载”操作可从阶段导出工件或日志。

  ![“阶段”菜单](images/pipeline_stages.png)

###修改管道阶段

要修改管道阶段，请执行以下操作：

1. 在“管道”页面上，单击**设置**图标。
1. 单击**配置阶段**。
1. 在**环境属性**选项卡上，编辑或删除属性。
1. 修改管道阶段内的作业脚本。选择作业并更改属于“构建配置”、“部署配置”或“测试配置”的值。
   
   ![修改作业脚本](images/job_script.png)
  
1. 从管道阶段中删除作业。在**作业**选项卡上，选择要删除的作业，然后单击**除去**。
 
###导出管道阶段

要导出管道阶段的定义，请将 `/yaml` 附加到管道 URL：

`http(s)://<DevOps Services domain>/pipeline/user/project/yaml`


要导出管道阶段的工件和日志：

1. 在“管道”页面上，单击**查看日志和历史记录**。
1. 单击要导出其工件和日志的构建号。
1. 单击**下载** > **工件**可导出所选构建的工件。
1. 单击**下载** > **日志**可导出所选构建的日志。  

###删除管道阶段

要删除管道阶段，请执行以下操作：

1. 在“管道”页面上，单击**设置**图标。
1. 单击**删除阶段**。

## 修改和删除工具链与工具集成
{: #managing_toolchains}

通过使用工具链，团队可以协作并共享不同的工具集成。 

建议您使用与团队或公司关联的数据（而不要使用与您关联的数据）来配置所有 {{site.data.keyword.contdelivery_short}} 集成。但是，在某些情况下，可能会无意中使用您的个人数据。在此类情况下，您必须识别您拥有的所有数据并将其删除。

创建工具集成后，{{site.data.keyword.contdelivery_short}} 无法记录所有数据的源。例如，其他团队成员可能使用您在电子邮件中提供的个人数据为您创建工具集成。您必须了解自己拥有的数据，并确保将其删除。

在删除共享工具集成或工具链之前，请与团队的其他成员进行协调。

###修改和删除工具集成

创建工具集成时，系统需要您提供用户凭证以及与该集成相关的其他帐户信息。如果您使用了自己的个人凭证和帐户信息，请将这些信息替换为其他值，或者删除该工具集成。

要修改工具集成，请执行以下操作：

1. 在工具的卡上，单击菜单以访问配置选项。

  ![“工具配置”菜单](images/toolchain_tile_menu.png)

1. 完成更新设置时，单击**保存集成**。

要删除工具集成，请执行以下操作：

1. 要从工具链中删除工具集成，请单击**删除**。
1. 单击**删除**以确认。

###删除工具链

如果删除工具链，那么该删除操作无法撤销。

1. 在 DevOps 仪表板的**工具链**页面上，单击要删除的工具链。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**。
1. 单击**更多操作**菜单，其位于**查看应用程序**的旁边。
1. 单击**删除**。删除工具链将除去其所有工具集成（包括管道），这可能会删除由这些集成管理的资源。
1. 通过输入工具链的名称并单击**删除**，以确认删除。 

在删除工具链时，不会删除关联的 {{site.data.keyword.gitrepos}} 存储库。有权访问这些存储库的用户如果执行过 `git clone` 或者创建过 {{site.data.keyword.webide}} 工作空间，就可能有数据的副本。要确保删除所有数据，必须请求这些用户删除其数据副本。
{: tip}

###删除所有工具链

无法同时删除资源组或组织内的所有工具链。您必须一次删除一个工具链。

工具链是按 IBM Cloud 区域和资源组或 Cloud Foundry 组织划分范围的。请确保选择每个区域以及该区域内的资源组或组织，以删除已创建的每个工具链。
{: tip}
