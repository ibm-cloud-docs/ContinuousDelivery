---

copyright:
  years: 2015, 2018
lastupdated: "2018-7-19"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 常见问题解答
{: #ts_cd}

获取有关使用 {{site.data.keyword.contdelivery_full}} 的常见问题的解答。
{:shortdesc}


## 我尝试向工具链添加 GitHub 工具集成，为什么未添加成功？
{: #cannot_authorize_github}

如果 {{site.data.keyword.Bluemix_notm}} 无权访问您的 GitHub 帐户，那么工具集成不会添加到工具链中。

如果创建工具链时要配置 GitHub 工具集成，请遵循以下步骤授权 GitHub 访问权：

  1. 在“可配置的集成”部分中，单击 **GitHub**。
  1. 如果要在 {{site.data.keyword.Bluemix_notm}} Public 上创建工具链，但尚未授权 {{site.data.keyword.Bluemix_notm}} 访问 GitHub，请单击**授权**以转至 GitHub Web 站点。
  1. 如果您没有活动的 GitHub 会话，那么系统会提示您登录。单击**授权应用程序**，以允许 {{site.data.keyword.Bluemix_notm}} 访问 GitHub 帐户。

如果已经具有工具链，请更新 GitHub 工具集成的配置：

 1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
 1. 在 GitHub 卡上，单击菜单并单击**配置**。
 1. 更新配置设置以授权 {{site.data.keyword.Bluemix_notm}} 访问 GitHub。单击**授权**以转至 GitHub Web 站点。如果您没有活动的 GitHub 会话，那么系统会提示您登录。单击**授权应用程序**，以允许 {{site.data.keyword.Bluemix_notm}} 访问 GitHub 帐户。
 1. 完成更新设置时，单击**保存集成**。


## 我尝试了创建工具链，为什么会遇到错误？
{: #cannot_create_toolchain}

尝试在组织中创建工具链时，如果收到以下错误消息，请从您的组织中除去一个或多个工具链，然后重新创建工具链。

`此组织包含 200 个工具链，其为最大限制。请从组织中除去一个或多个工具链，您才可以添加其他工具链。`


## 为何“工具链”页面显示已超过 {{site.data.keyword.contdelivery_short}} 服务轻量套餐？

{{site.data.keyword.contdelivery_short}} 提供两个套餐：轻量和专业。如果您有 {{site.data.keyword.contdelivery_short}} 轻量套餐，那么可以免费使用工具链，直至达到套餐限制的数量。错误消息指示您已超过轻量套餐的一个或多个限制。例如，如果有太多授权用户与 {{site.data.keyword.contdelivery_short}} 服务实例相关联或者如果运行了最大数量的 {{site.data.keyword.deliverypipeline}} 作业，那么可能超出套餐。有关套餐条款的更多信息，请参阅[套餐限制和使用情况](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}。


## 我已创建工具链，为什么“工具链”页面显示需要 Continuous Delivery 服务？

位于工具链的相同资源组或组织中的 {{site.data.keyword.contdelivery_short}} 服务实例的套餐条款管理服务中包含的某些工具集成的使用（{{site.data.keyword.deliverypipeline}}、Eclipse Orion {{site.data.keyword.webide}} 和 {{site.data.keyword.gitrepos}}）。错误消息指示资源组或组织不包含必需的 {{site.data.keyword.contdelivery_short}} 服务实例。有关套餐条款的更多信息，请参阅[套餐限制和使用情况](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}。


## 我已在 Cloud Foundry 组织中创建工具链，为什么“工具链”页面显示需要 Continuous Delivery 服务？

在没有 {{site.data.keyword.contdelivery_short}} 服务实例的资源组或组织中创建工具链时，工具链平台尝试使用轻量套餐自动创建服务实例。错误消息指示工具链平台无法创建服务实例。

在美国南部区域和尚无 {{site.data.keyword.contdelivery_short}} 实例的 Cloud Foundry 组织中创建工具链时，可能发生此错误。在美国南部区域中，必须创建资源组中 {{site.data.keyword.contdelivery_short}} 服务的所有新实例。 

您可以在资源组中创建工具链或者在已具有 {{site.data.keyword.contdelivery_short}} 实例的组织中创建工具链。
  

## 我尝试了将应用程序部署到 {{site.data.keyword.Bluemix_notm}}，为什么会遇到错误？
{: #org_outofmemory}

尝试将应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，如果收到以下错误消息，那么组织中剩余的内存量低于您要部署的应用程序所需的内存量。

`失败 服务器错误，状态码：400，错误代码：100005，消息：您已超过组织的内存限制。`

您可以增加帐户的内存配额，或者减少应用程序使用的内存。
试用帐户的最大内存配额为 2 GB。
要增加帐户的内存配额，请将试用帐户转换为付费帐户。有关将试用帐户转换为付费帐户的信息，请参阅 [付费帐户](/docs/pricing/index.html#pay-accounts)。要减少应用程序使用的内存，请使用 {{site.data.keyword.Bluemix_notm}} 控制台或 cf 命令行界面。
    

如果使用 {{site.data.keyword.Bluemix_notm}} 控制台，请完成以下步骤：

1. 在应用程序仪表板中，选择应用程序。这将打开应用程序详细信息页面。
1. 在运行时窗格中，可以减少应用程序的最大内存限制和/或应用程序实例数。
	

如果使用 cf 命令行界面，请完成以下步骤：

1. 检查应用程序使用的内存量。cf apps 命令会列出当前空间中部署的所有应用程序。还会显示每个应用程序的状态。

	  ```
	  cf apps
	  ```

1. 要减少应用程序使用的内存量，请减少应用程序实例数和/或最大内存限制：

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```
    
1. 重新启动应用程序以使更改生效。


## 我创建了一个应用程序，为什么在 Eclipse Orion Web IDE 中运行栏不显示 {{site.data.keyword.Bluemix_notm}} Live Sync 图标？
{: #ts_llz_lkb_3r}

![运行栏](images/webide_runbar_light.png)   

在 Web IDE 中编辑 Node.js 应用程序时，{{site.data.keyword.Bluemix_notm}} 的“实时编辑”、“快速重新启动”和“调试”图标在以下情况下不会显示在运行栏中：



* `manifest.yml` 文件未存储在项目的顶层。
* 应用程序存储在子目录中而不是根目录中，但在 `manifest.yml` 文件中未指定该子目录的路径。
* 应用程序中不包含 `package.json` 文件。


如果 `manifest.yml` 文件未存储在根目录中，请将其存储在那里。如果应用程序存储在子目录中，请在 `manifest.yml` 文件中指定该子目录的路径。如果应用程序不包含 `package.json` 文件，请在应用程序所在的目录中创建一个文件。


## 我单击了工具链以查看其“概述”页面，为什么未装入工具链？
{: #toolchains_load}

检查 {{site.data.keyword.Bluemix_notm}}“状态”页面，以确定 {{site.data.keyword.Bluemix_notm}} 中是否存在已知问题影响 {{site.data.keyword.Bluemix_notm}} 平台和主要服务。


可以通过选择以下两个选项之一来找到“状态”页面：

  * 登录到 {{site.data.keyword.Bluemix_notm}} 控制台。从菜单栏中单击**支持**，然后选择**状态**。检查列出的资源中是否存在 ![某些问题](../../get-support/images/some_issues.svg) 图标。此图标可能指示有中断情况。
  * 通过“[{{site.data.keyword.Bluemix_notm}} - 系统状态”![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/status){: new_window} 直接访问。


有关 {{site.data.keyword.Bluemix_notm}}“状态”页面的更多信息，请参阅[查看 {{site.data.keyword.Bluemix_notm}} 状态](https://console.bluemix.net/docs/get-support/ViewStatus.html#viewing-bluemix-status)。


## 我为工具链配置了工具集成，为什么未配置成功？
{: #tool_integration_error}

当您添加工具集成时，工具链会与工具集成所代表的工具进行通信，以供应任何必要资源，并将它们与工具链相关联。如果在设置过程中发生错误，或者工具链与工具之间的通信没有正确完成，那么工具集成会置于错误状态。


 ![设置失败错误](images/tool_setup_failed.png)

您可以再次尝试配置工具集成：

1. 在其工具卡上，将鼠标悬停在`设置失败`消息上并单击**重新配置**。

 ![“重新配置”按钮](images/tool_reconfigure.png)

1. 请确保您使用有效的配置参数。如果错误由无效的配置引起，那么会显示错误消息；例如，`无法设置集成。请检查设置并重试。
原因：api_key:fakeKey 无效`。请更新工具集成的设置并单击**保存集成**。
1. 如果错误由通信问题引起，请单击**保存集成**，然后重试。
