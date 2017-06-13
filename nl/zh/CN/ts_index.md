---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# {{site.data.keyword.contdelivery_short}} 故障诊断
{: #ts_cd}

获取使用 {{site.data.keyword.contdelivery_full}} 的常见故障诊断问题的答案。
{:shortdesc}


## 无法获取 GitHub 的授权
{: #cannot_authorize_github}

您无法从 GitHub 获取授权。
{:shortdesc}

如果您未授权 {{site.data.keyword.Bluemix_notm}} 访问您的 GitHub 帐户，那么可能会发生以下任何问题：
{: tsSymptoms}

 * 当您尝试向工具链添加 GitHub 工具集成时，不会添加该工具集成。
 * 当您将更改推送至 GitHub 或 GitHub Enterprise 存储库时，管道不会自动运行。

{{site.data.keyword.Bluemix_notm}} 未获授权访问 GitHub。  
{: tsCauses}

如果您在创建工具链时配置 GitHub 工具集成，请遵循以下步骤：
{: tsResolve}

  1. 在“可配置的集成”部分中，单击 **GitHub**。
  1. 如果您要在 {{site.data.keyword.Bluemix_notm}} Public 上创建工具链，但尚未授权 {{site.data.keyword.Bluemix_notm}} 访问 GitHub，请单击**授权**以转至 GitHub Web 站点。
  1. 如果您没有活动的 GitHub 会话，那么系统会提示您登录。单击**授权应用程序**，以允许 {{site.data.keyword.Bluemix_notm}} 访问 GitHub 帐户。如果您有活动的 GitHub 会话但最近未输入过密码，那么系统可能会提示您输入 GitHub 密码以进行确认。

如果已经具有工具链，请更新 GitHub 工具集成的配置：

 1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
 1. 在 GitHub 卡上，单击菜单并单击**配置**。
 1. 更新配置设置以授权 {{site.data.keyword.Bluemix_notm}} 访问 GitHub。单击**授权**以转至 GitHub Web 站点。如果您没有活动的 GitHub 会话，那么系统会提示您登录。单击**授权应用程序**，以允许 {{site.data.keyword.Bluemix_notm}} 访问 GitHub 帐户。如果您有活动的 GitHub 会话但最近未输入过密码，那么系统可能会提示您输入 GitHub 密码以进行确认。
 1. 完成更新设置时，单击**保存集成**。


## 无法创建工具链
{: #cannot_create_toolchain}

当您创建工具链时会显示错误。
{:shortdesc}

当您创建工具链时，您将看到以下错误消息：
{: tsSymptoms}

`此组织包含 200 个工具链，其为最大限制。请从组织中除去一个或多个工具链，您才可以添加其他工具链。`

组织中不能超过 200 个工具链。  
{: tsCauses}

从组织中除去一个或多个工具链，然后重新创建工具链。
{: tsResolve}


## 超过组织的内存限制
{: #org_outofmemory}

如果您已经超出了组织的内存限制，那么您可能无法将应用程序部署至 {{site.data.keyword.Bluemix_notm}}。您可以减少应用程序使用的内存，或者增加您帐户的内存配额。试用帐户的最大内存配额为 2 GB，仅可以通过转换为付费帐户来提高配额。

将应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，您会看到以下错误消息：
{: tsSymptoms}

`失败 服务器错误，状态码：400，错误代码：100005，消息：您已超过组织的内存限制。`

当组织的剩余内存量低于您要部署的应用程序所需的内存量时，会发生此错误。试用帐户的最大内存配额为 2 GB。
{: tsCauses}

您可以增加帐户的内存配额，或者减少应用程序使用的内存。
{: tsResolve}

  * 要增加帐户的内存配额，请将试用帐户转换为付费帐户。有关将试用帐户转换为付费帐户的信息，请参阅 [付费帐户](/docs/pricing/index.html#pay-accounts)。
  * 要减少应用程序使用的内存，请使用 {{site.data.keyword.Bluemix_notm}} 控制台或 cf 命令行界面。
    

    如果使用 {{site.data.keyword.Bluemix_notm}} 控制台，请完成以下步骤：

    1. 在应用程序仪表板中，选择应用程序。这将打开应用程序详细信息页面。
    2. 在运行时窗格中，可以减少应用程序的最大内存限制和/或应用程序实例数。
	

    如果使用 cf 命令行界面，请完成以下步骤：

    1. 检查应用程序使用了多少内存：

	  ```
	  cf apps
	  ```

	  cf apps 命令会列出当前空间中部署的所有应用程序。还会显示每个应用程序的状态。

    2. 要减少应用程序使用的内存量，请减少应用程序实例数和/或最大内存限制：

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. 重新启动应用程序以使更改生效。

有关管理应用程序的一般问题的更多信息，请参阅[应用程序管理故障诊断](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps)。


## 工具链未装入
{: #toolchains_load}

当您单击工具链以查看其“概述”页面时，工具链不会装入。
{:shortdesc}

在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序概述页面的“持续交付”卡上，单击**查看工具链**。然后，单击**概述**。工具链的“概述”页面不会打开。
{: tsSymptoms}

检查 {{site.data.keyword.Bluemix_notm}} 状态以查看问题是否因中断而引起。
{: tsCauses}

查看 {{site.data.keyword.Bluemix_notm}}“状态”页面，以确定 {{site.data.keyword.Bluemix_notm}} 中是否存在已知问题影响 {{site.data.keyword.Bluemix_notm}} 平台和主要服务。
{: tsResolve}

可以通过选择以下两个选项之一来找到“状态”页面：

  * 登录到 {{site.data.keyword.Bluemix_notm}} 控制台。从菜单栏中单击**支持**，然后选择**状态**。检查列出的资源中是否存在 ![某些问题](../../support/images/some_issues.svg) 图标。此图标可能指示有中断情况。
  * 通过 [IBM {{site.data.keyword.Bluemix_notm}} - 系统状态 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://ibm.biz/bluemixstatus){: new_window} 直接对其进行访问。

有关 {{site.data.keyword.Bluemix_notm}}“状态”页面的更多信息，请参阅[查看 {{site.data.keyword.Bluemix_notm}} 状态](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status)。


## 未配置工具集成
{: #tool_integration_error}

为工具链配置工具集成后，在其工具卡上会显示`设置失败`错误。
{:shortdesc}

在您配置工具集成后，您在工具链的“概述”页面上查看其工具卡，并注意到设置失败。
{: tsSymptoms}

 ![设置失败错误](images/tool_setup_failed.png)

当您添加工具集成时，工具链会与工具集成所代表的工具进行通信，以供应任何必要资源，并将它们与工具链相关联。如果在设置过程中发生错误，或者工具链与工具之间的通信没有正确完成，那么工具集成会置于错误状态。
{: tsCauses}

再次配置工具集成：
{: tsResolve}

1. 在其工具卡上，将鼠标悬停在`设置失败`消息上并单击**重新配置**。

 ![“重新配置”按钮](images/tool_reconfigure.png)

1. 请确保您使用有效的配置参数。如果错误由无效的配置引起，那么会显示错误消息；例如，`无法设置集成。请检查设置并重试。
原因：api_key:fakeKey 无效`。请更新工具集成的设置并单击**保存集成**。
1. 如果错误由通信问题引起，请单击**保存集成**，然后重试。
