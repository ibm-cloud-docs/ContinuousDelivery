---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-11"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# 有关 {{site.data.keyword.contdelivery_short}} 的故障诊断
{: #troubleshoot-cd}

使用 {{site.data.keyword.contdelivery_full}} 时遇到的一般问题可能包括 GitHub 认证、管道创建、工具集成配置或 Cloud Foundry 问题。在许多情况下，只需执行几个简单的步骤即可解决这些问题。
{:shortdesc}

## 我尝试向工具链添加 GitHub 工具集成，为什么未添加成功？
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

您必须使用 GitHub 进行授权，以便 {{site.data.keyword.Bluemix_notm}} 有权访问您的 GitHub 帐户。

GitHub 工具集成未添加到工具链。
{: tsSymptoms}

如果 {{site.data.keyword.Bluemix_notm}} 无权访问您的 GitHub 帐户，那么工具集成不会添加到工具链中。
{: tsCauses}

如果创建工具链时要配置 GitHub 工具集成，请遵循以下步骤授权 GitHub 访问权：
{: tsResolve}

  1. 在“可配置的集成”部分中，单击 **GitHub**。
  1. 如果要在 {{site.data.keyword.Bluemix_notm}} Public 上创建工具链，但尚未授权 {{site.data.keyword.Bluemix_notm}} 访问 GitHub，请单击**授权**以转至 GitHub Web 站点。
  1. 如果您没有活动的 GitHub 会话，那么系统会提示您登录。单击**授权应用程序**，以允许 {{site.data.keyword.Bluemix_notm}} 访问 GitHub 帐户。

如果已经具有工具链，请更新 GitHub 工具集成的配置：

 1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
 1. 在 GitHub 卡上，单击菜单并单击**配置**。
 1. 更新配置设置以授权 {{site.data.keyword.Bluemix_notm}} 访问 GitHub。单击**授权**以转至 GitHub Web 站点。如果您没有活动的 GitHub 会话，那么系统会提示您登录。单击**授权应用程序**，以允许 {{site.data.keyword.Bluemix_notm}} 访问 GitHub 帐户。
 1. 完成更新设置时，单击**保存集成**。
 

## 为什么无法将一个区域的工具链中的 {{site.data.keyword.gitrepos}} 工具集成用于其他区域的工具链中？
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

您不能在多个区域中使用一个 {{site.data.keyword.gitrepos}} 实例。

我尝试向工具链添加 {{site.data.keyword.gitrepos}} 工具集成，但收到以下错误消息：
{: tsSymptoms}

`存储库 URL 无效。存储库必须位于 {local GitLab URL}。`

其中，`{local GitLab URL}` 是工具链所在区域中 {{site.data.keyword.gitrepos}} 工具集成的 URL。
   
由于 {{site.data.keyword.gitrepos}} 与 {{site.data.keyword.contdelivery_short}} 服务在它们运行所在的区域中紧密集成，因此无法在多个区域中使用一个 {{site.data.keyword.gitrepos}} 实例。
{: tsCauses}

不要创建 {{site.data.keyword.gitrepos}} 工具集成，请改为创建通用的 GitLab 集成，并使用此集成来指向不同区域中的 {{site.data.keyword.gitrepos}} 存储库。
{: tsResolve}

1. 在 DevOps 仪表板的“工具链”页面上，单击要将此集成添加到的工具链。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 单击**添加工具**。
1. 在“工具集成”部分中，单击 **GitLab**。
1. 单击要使用的 GitLab 服务器。如果要访问的存储库所在的 GitLab 服务器未显示在此列表中，请添加定制服务器：

 a. 单击**添加定制服务器**。

 b. 输入服务器的名称。此服务器名称将显示在可用 GitLab 服务器列表中。
 
 c. 输入定制 GitLab 服务器的根 URL。
 
 d. 输入定制 GitLab 服务器的个人访问令牌。如果您没有个人访问令牌，请[创建个人访问令牌](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)。
 
 e. 单击**保存定制集成**。
 
1. 如果您有 GitLab 存储库并且想要使用该存储库，那么对于存储库类型，请单击**现有**并输入 URL。
1. 如果要使用新的 GitLab 存储库，请输入存储库的名称，输入您要克隆或派生的存储库的 URL，然后选择存储库类型：

 a. 要创建空的存储库，请单击**新建**。

 b. 要创建 GitLab 存储库的副本，请单击**克隆**。

 c. 要派生 GitLab 存储库以便您可以通过拉出请求来提供更改，请单击**派生**。

1. 如果要在服务器上创建公共存储库，请清除**使此存储库成为专用**复选框。
1. 如果要使用 GitLab Issues 进行问题跟踪，请选中**启用 GitLab Issues** 复选框。
1. 如果您要通过在提交上创建标记和注释，在提交所参考的问题上创建标签和注释，跟踪代码更改的部署，请选择**跟踪代码更改的部署**复选框。有关更多信息，请参阅[使用工具链跟踪代码部署位置 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}。
1. 单击**创建集成**。

有关配置 GitLab 工具集成的更多信息，请参阅[配置 GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)。


## 为什么无法通过使用其他区域中专用存储库的模板来创建工具链？
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

您使用的工具链模板引用的是专用 {{site.data.keyword.gitrepos}} 存储库。

{{site.data.keyword.gitrepos}} 是特定于区域的。尝试通过模板创建工具链并将该专用存储库不在其中的区域设定为目标时，Git 集成设置会失败。
{: tsSymptoms}
   
将 {{site.data.keyword.gitrepos}} 存储库添加到特定区域中的工具链时，您的 IBM 标识会映射到 GitLab 用户名，这将授予您对该区域中 GitLab 的访问权。尽管您的 GitLab 用户名在所有区域中显示为相同，每个区域中关联的 GitLab 用户也是不同的，因为每个区域都有一个单独的 GitLab 安装。对于其他区域中的 GitLab 用户，即使他们的 GitLab 用户名显示为相同，也不会自动授予这些用户对工具链的访问权。
{: tsCauses}

使 {{site.data.keyword.gitrepos}} 存储库成为公共的，以便可以从任何位置对其进行访问，包括其他 {{site.data.keyword.Bluemix_notm}} 区域。
{: tsResolve}

如果存储库必须是专用的，那么存储库所有者可以通过在源存储库所在的 GitLab 服务器上创建[个人访问令牌](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)来授予对该存储库的访问权。在创建工具链期间，您只需要对专用存储库的访问权就可克隆内容。可以创建具有到期日期的个人访问令牌，以将令牌的生命周期限制为一天后到期。 

拥有个人访问令牌后，可以创建用于访问其他区域中存储库的 URL。在配置工具集成时，在**源存储库 URL** 字段中，更新存储库 URL 以使用您的用户名和访问令牌。

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

其中，`user` 是您的 GitLab 用户名，`XXXXXXX` 是访问令牌，[`group` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window} 是存储库存储所在的组，`node-hello-world` 是存储库名称。

如果 GitLab 存储库不在 GitLab 组中，说明 `group` 的值与您的用户名相同。
{: tip}


## 为什么无法通过 HTTPS 来克隆 {{site.data.keyword.gitrepos}} 存储库？
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

您必须使用个人访问令牌或 SSH 密钥才能执行 Git 操作。

您尝试在命令行中使用 HTTPS 来推送或克隆存储库，但尽管您输入了正确的密码，仍无法进行认证。
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} 使用单点登录机制，该机制不支持在命令行上使用用户名和密码的 Git 认证。
{: tsCauses}

要执行克隆或推送等 Git 操作，必须使用个人访问令牌或 SSH 密钥。有关创建个人访问令牌或 SSH 密钥的更多信息，请参阅[入门教程](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)。
{: tsResolve}

## 我尝试使用 SSH 克隆 {{site.data.keyword.gitrepos}} 存储库时，为什么会提示我进行认证？
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

您的专用 SSH 密钥的位置或许可权可能存在问题，或者 Git 命令行可能未使用您的专用 SSH 密钥向 {{site.data.keyword.gitrepos}} 进行认证。

我已通过 {{site.data.keyword.gitrepos}} 用户界面添加了 SSH 公用密钥。但在尝试使用 SSH 克隆存储库时，系统提示我输入密码或安全代码，或者显示一条错误消息，指示认证失败。
{: tsSymptoms}
   
以下任何 SSH 问题都可能提示您进行认证，或者显示错误消息：
{: tsCauses}

* Git 命令行可能未使用您的专用 SSH 密钥向 {{site.data.keyword.gitrepos}} 进行认证。

* 您的专用 SSH 密钥可能不在缺省 ~/.ssh/id_rsa 位置。

* 您的专用 SSH 密钥可能没有正确的许可权 (600)。


使用以下任一方法来解决此问题：
{: tsResolve}

* 如果使用的是缺省专用 SSH 密钥位置，请验证 ~/.ssh/ 文件夹和 ~/.ssh/id_rsa 专用密钥文件的许可权。如果许可权过宽，那么缺省情况下 SSH 不会使用专用密钥。请确保 ~/.ssh/ 文件夹的许可权设置为 700，并且 ~/.ssh/id_rsa 文件夹的许可权设置为 600。

* 如果专用密钥不在缺省位置，请使用以下命令在环境变量中指定专用密钥：

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* 要使用连接信息来调试此问题，请将 -v 或 -vvv 标志添加到 `GIT_SSH_COMMAND` 环境变量：

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## 我尝试通过电子邮件向 GitLab 项目添加用户，但用户收不到邀请。如何将用户添加到项目中？
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

用户的电子邮件可能阻止了邀请。

我使用 {{site.data.keyword.gitrepos}} 中列出的用户电子邮件地址来邀请用户加入 GitLab 项目，但他们未收到该电子邮件。
{: tsSymptoms}
   
电子邮件可能被垃圾邮件过滤器阻止进入用户的收件箱中。
{: tsCauses}

可以使用以下任一方法来解决此问题：
{: tsResolve}

* 检查电子邮件垃圾邮件文件夹，以确定电子邮件邀请是否已标记为垃圾邮件。电子邮件是从 noreply@ 地址发送的。请更新垃圾邮件过滤器以允许来自此地址的电子邮件。

* 调查超出用户控制范围的公司垃圾邮件过滤器是否阻止了该电子邮件。请要求用户登录到 {{site.data.keyword.gitrepos}} 用户界面，并向您发送其用户标识。您可以使用用户标识将相应用户添加到 GitLab 项目。


## 通过我编写的模板创建工具链时，为什么管道没有正确创建？ 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

由于 pipeline.yaml 定义中有错误，管道可能缺少作业和阶段等资源。

我尝试通过编写的模板创建工具链时，在“管道”页面上收到以下错误消息：
{: tsSymptoms}

`此管道已创建，但可能缺少作业、阶段或其他资源。您可以使用此管道，或者如果需要，可以将其删除并创建其他管道。`

通常，导致此问题的原因是 pipeline.yaml 定义中有错误。
{: tsCauses}
   
可以使用以下任一方法来调试此错误：
{: tsResolve}

* 使用管道用户界面来创建示例管道，该管道将复制您尝试使用模板构建的管道。将 `/yaml` 附加到管道 URL 以生成类似的 pipeline.yaml 文件，您可以使用该文件来查找明显的差异。例如，`https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`。

* 使用无头工具链创建机制。在**创建工具链**页面上，打开调试器并对 `window.Testflags = {nocreate: 1}` 表达式求值。在此方式下单击**创建工具链**时，不会创建工具链。系统会改为将传递给 API 的信息返回到控制台，供您在其中复查这些信息。


## 我为工具链配置了工具集成，为什么未配置成功？
{: troubleshoot-tool-integration-error}
{: troubleshoot}

如果在设置过程中发生错误，或者工具链与工具之间的通信没有正确完成，那么配置会失败。


为工具链添加并配置工具集成后，会显示一条错误消息，指示设置失败。
{: tsSymptoms}

当您添加工具集成时，工具链会与工具集成所代表的工具进行通信，以供应任何必要资源，并将它们与工具链相关联。如果在设置过程中发生错误，或者工具链与工具之间的通信没有正确完成，那么工具集成会置于错误状态。
{: tsCauses}

 ![设置失败错误](images/tool_setup_failed.png)

您可以再次尝试配置工具集成：
{: tsResolve}

1. 在其工具卡上，将鼠标悬停在`设置失败`消息上并单击**重新配置**。

 ![“重新配置”按钮](images/tool_reconfigure.png)

1. 请确保您使用有效的配置参数。如果错误由无效的配置引起，那么会显示错误消息；例如，`无法设置集成。请检查设置并重试。
原因：api_key:fakeKey 无效`。请更新工具集成的设置并单击**保存集成**。
1. 如果错误由通信问题引起，请单击**保存集成**，然后重试。


## 为什么无法将 {{site.data.keyword.contdelivery_short}} 添加到 Cloud Foundry 组织？
{: troubleshoot-resource_groups}
{: troubleshoot}

您无法再在 Cloud Foundry 组织中创建 {{site.data.keyword.contdelivery_short}} 服务的实例。 

Cloud Foundry 组织中工具链的“工具链”页面上显示以下消息：
{: tsSymptoms}

`需要 Continuous Delivery 服务：请将该服务添加到组织，以确保不间断地使用该服务的功能。` 

单击**添加服务**时，无法在 Cloud Foundry 组织中创建 {{site.data.keyword.contdelivery_short}}。您只能在资源组中创建 {{site.data.keyword.contdelivery_short}}。

资源组已将作为首选容器的 Cloud Foundry 组织替换为服务实例。但是，您仍然可以在 Cloud Foundry 组织中创建工具链，以支持 Cloud Foundry 组织中先前存在的 {{site.data.keyword.contdelivery_short}} 实例。
{: tsCauses}

重新在资源组中创建工具链，然后从 Cloud Foundry 组织中除去原始工具链。或者，可以忽略该错误消息，直到提供将现有工具链从 Cloud Foundry 组织迁移到资源组的方法。
{: tsResolve}


## 为什么无法使用 `ibmcloud` CLI 来删除工具链？
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

目前，无法使用 ibmcloud resource CLI 来删除工具链。 

我尝试在命令行中使用 `ibmcloud resource service-instance-delete` 命令来删除工具链，但该命令失败并返回以下错误消息：
{: tsSymptoms}

`错误代码：RC-ServiceBrokerErrorResponse
消息：描述：必须在工具链仪表板中执行工具链删除`

工具链是云平台上的一种特殊类型的资源，目前无法使用 `ibmcloud resource` CLI 来删除该资源。
{: tsCauses}

要删除工具链，请执行以下操作：
{: tsResolve}

1. 在 DevOps 仪表板的**工具链**页面上，单击要删除的工具链。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**。
1. 单击**更多操作**菜单，其位于**查看应用程序**的旁边。
1. 单击**删除**。删除工具链将除去其所有工具集成，这可能删除由那些集成管理的资源。
1. 通过输入工具链的名称并单击**删除**，以确认删除。  


## 为什么向存储库执行提交和推送操作后，实时编辑不可用？
{: #troubleshoot-liveedit}
{: troubleshoot}

在 Eclipse Orion {{site.data.keyword.webide}} 外部进行部署时，将清除“实时编辑”方式。

通过命令行或 {{site.data.keyword.webide}} 提交并推送更改后，“实时编辑”不可用。
{: tsSymptoms}
   
创建包含 {{site.data.keyword.contdelivery_short}} 管道和 {{site.data.keyword.webide}} 的工具链时，这两个工具集成都可以部署应用程序。缺省情况下，管道和 {{site.data.keyword.webide}} 都使用相同的 Cloud Foundry 应用程序和 URL 部署到同一 Cloud Foundry 组织和空间。在 {{site.data.keyword.webide}} 外部进行部署时，将清除“实时编辑”方式。
{: tsCauses}

要使用“实时编辑”快速开发应用程序的测试版本，请通过 {{site.data.keyword.webide}} 部署到其他 Cloud Foundry 应用程序、空间和 URL。完成代码更改后，可以提交并推送代码来触发管道，以构建和部署应用程序的生产版本。
{: tsResolve}

1. 从运行栏中，选择要编辑的启动配置。
2. 编辑为“空间”和“主机”指定的值。
3. 单击**保存**，再单击**退出**。
4. 单击运行栏中的**运行**按钮。您可能需要多次部署才能启用“实时编辑”按钮。

有关实时编辑的更多信息，请参阅[实时编辑](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit)。


## {{site.data.keyword.webide}} 运行栏中“未同步”是什么意思？
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

工作空间中的文件系统不同步。

在“实时编辑”方式下，{{site.data.keyword.webide}} 会将工作空间中的文件与正在运行的 Cloud Foundry 应用程序同步，但现在这些文件未同步。
{: tsSymptoms}
   
如果在 {{site.data.keyword.webide}} 外部修改了应用程序，那么工作空间中的文件系统可能会变得不同步。如果 {{site.data.keyword.webide}} 无法从应用程序检索同步状态，该文件系统也可能会变得不同步。
{: tsCauses}

一两分钟后，当重新建立正常通信并且对文件同步后，此状态可能会清除。如果未清除，您可以在启用“实时编辑”方式的情况下启动和停止应用程序。
{: tsResolve}
