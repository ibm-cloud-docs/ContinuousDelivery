---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 常见问题解答
{: #ts_cd}

获取有关使用 {{site.data.keyword.contdelivery_full}} 的常见问题的解答。
{:shortdesc}

## 为何“工具链”页面显示已超过 {{site.data.keyword.contdelivery_short}} 服务轻量套餐？
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} 提供两个套餐：轻量和专业。如果您有 {{site.data.keyword.contdelivery_short}} 轻量套餐，那么可以免费使用工具链，直至达到套餐限制的数量。错误消息指示您已超过轻量套餐的一个或多个限制。例如，如果有太多授权用户与 {{site.data.keyword.contdelivery_short}} 服务实例相关联或者如果运行了最大数量的 {{site.data.keyword.deliverypipeline}} 作业，那么可能超出套餐。有关套餐条款的更多信息，请参阅[套餐限制和使用情况](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)。


## {{site.data.keyword.contdelivery_short}} 服务声明，轻量套餐在 30 天不活动后会被删除。不活动是什么意思？
{: #plan_inactivity}
{: faq}

同一资源组或 Cloud Foundry 组织中有一个或多个工具链处于活动状态时，就会将 {{site.data.keyword.contdelivery_short}} 服务实例视为处于活动状态。如果用户通过用户界面与工具链交互，触发了交付管道作业，访问由 {{site.data.keyword.gitrepos}} 管理的存储库，或者正在使用 Eclipse Orion {{site.data.keyword.webide}} 工作空间，那么会将工具链视为处于活动状态。与 {{site.data.keyword.contdelivery_short}} 服务关联的所有工具链中必须不存在所有这些条件并且此情况持续 30 天，这时才会视为处于不活动状态。


## 我已创建工具链，为什么“工具链”页面显示需要 Continuous Delivery 服务？
{: #service_required_resource_group}
{: faq}

位于工具链的相同资源组或组织中的 {{site.data.keyword.contdelivery_short}} 服务实例的套餐条款管理服务中包含的某些工具集成的使用（{{site.data.keyword.deliverypipeline}}、Eclipse Orion {{site.data.keyword.webide}} 和 {{site.data.keyword.gitrepos}}）。错误消息指示资源组或组织不包含必需的 {{site.data.keyword.contdelivery_short}} 服务实例。有关套餐条款的更多信息，请参阅[套餐限制和使用情况](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)。


## 我更新了 Cloud Foundry 组织中工具链的信息，为什么在工具链中看不到这些更改？
{: #updates_in_cloud_foundry}
{: faq}

直接在 Cloud Foundry 中更新工具链信息时，{{site.data.keyword.contdelivery_short}} 服务可能需要几分钟时间才会刷新并显示您的更改。例如，如果在 Cloud Foundry 组织中添加或除去了用户，那么 {{site.data.keyword.contdelivery_short}} 可能需要几分钟时间才会发现有新用户，并允许该用户访问工具链。


## 我已在 Cloud Foundry 组织中创建工具链，为什么“工具链”页面显示需要 Continuous Delivery 服务？
{: #service_required_cloud_foundry}
{: faq}

在没有 {{site.data.keyword.contdelivery_short}} 服务实例的资源组或组织中创建工具链时，工具链平台尝试使用轻量套餐自动创建服务实例。错误消息指示工具链平台无法创建服务实例。

在美国南部区域和尚无 {{site.data.keyword.contdelivery_short}} 实例的 Cloud Foundry 组织中创建工具链时，可能发生此错误。在美国南部区域中，必须创建资源组中 {{site.data.keyword.contdelivery_short}} 服务的所有新实例。 

您可以在资源组中创建工具链或者在已具有 {{site.data.keyword.contdelivery_short}} 实例的组织中创建工具链。
  

## 如何将工具链从 Cloud Foundry 组织移至资源组？
{: #toolchain_move_to_resource_group}
{: faq}

尚未提供将工具链从 Cloud Foundry 组织自动迁移到资源组的功能。您可以改为在资源组中再次手动创建工具链，然后从 Cloud Foundry 组织中除去原始工具链。


## 我尝试了将应用程序部署到 {{site.data.keyword.Bluemix_notm}}，为什么会遇到错误？
{: #org_outofmemory}
{: faq}

尝试将应用程序部署到 {{site.data.keyword.Bluemix_notm}} 时，如果收到以下错误消息，那么组织中剩余的内存量低于您要部署的应用程序所需的内存量。

`失败 服务器错误，状态码：400，错误代码：100005，消息：您已超过组织的内存限制。`

您可以增加帐户的内存配额，或者减少应用程序使用的内存。
试用帐户的最大内存配额为 2 GB。
要增加帐户的内存配额，请将试用帐户转换为付费帐户。有关将试用帐户转换为付费帐户的信息，请参阅[如何升级或更改我的帐户？](/docs/account?topic=account-accountfaqs#changeacct)。要减少应用程序使用的内存，请使用 {{site.data.keyword.Bluemix_notm}} 控制台或 cf 命令行界面。
    

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


## 我创建了一个应用程序，为什么在 {{site.data.keyword.webide}} 中运行栏不显示 {{site.data.keyword.Bluemix_notm}} Live Sync 图标？
{: #ts_llz_lkb_3r}
{: faq}

![运行栏](images/webide_runbar_light.png)   

在 {{site.data.keyword.webide}} 中编辑 Node.js 应用程序时，{{site.data.keyword.Bluemix_notm}} 的“实时编辑”、“快速重新启动”和“调试”图标在以下情况下不会显示在运行栏中：


* `manifest.yml` 文件未存储在项目的顶层。
* 应用程序存储在子目录中而不是根目录中，但在 `manifest.yml` 文件中未指定该子目录的路径。
* 应用程序中不包含 `package.json` 文件。


如果 `manifest.yml` 文件未存储在根目录中，请将其存储在那里。如果应用程序存储在子目录中，请在 `manifest.yml` 文件中指定该子目录的路径。如果应用程序不包含 `package.json` 文件，请在应用程序所在的目录中创建一个文件。


## 我单击了 {{site.data.keyword.webide}} 的“运行”按钮，日志文件在哪里？ 
{: #web_ide_log_files}
{: faq}  

单击“运行”按钮时，工作空间的内容会推送到 Cloud Foundry，就像在桌面中输入 `cf push` 来部署这些内容的方式一样。您可以在 Cloud Foundry 仪表板中找到日志文件。

有关部署工作空间内容的更多信息，请参阅[从您的工作空间部署应用程序](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy)。


## 如何阻止 {{site.data.keyword.webide}} 自动选择 Git 视图中的所有更改？ 
{: #web_ide_git_view}
{: faq} 

缺省情况下，{{site.data.keyword.webide}} 假定您每次转至 Git 页面时，都要将传出更改推送到代码存储库。如果要在 GIT 首选项页面中手动选择要提交、同步、重置和替换的资源，请清除**始终选择更改的文件**复选框。


## 为什么 {{site.data.keyword.webide}} 不支持我使用的语言？ 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}} 为 JavaScript、HTML 和 CSS 提供了大量工具和支持。此外，还为大多数常用语言提供了语法突出显示功能。您无法扩展 {{site.data.keyword.webide}} 来支持特定语言。要查看 {{site.data.keyword.webide}} 支持的语言的完整列表，请参阅[受支持的语言](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages)。


## 如何查找 {{site.data.keyword.Bluemix_notm}} 和 {{site.data.keyword.contdelivery_short}} 服务的状态？
{: #toolchains_load}
{: faq}

检查 {{site.data.keyword.Bluemix_notm}}“状态”页面，以确定 {{site.data.keyword.Bluemix_notm}} 中是否存在已知问题影响 {{site.data.keyword.Bluemix_notm}} 平台和主要服务。


可以通过选择以下两个选项之一来找到“状态”页面：

  * 登录到 {{site.data.keyword.Bluemix_notm}} 控制台。从菜单栏中单击**支持**，然后选择**状态**。检查列出的资源中是否存在 ![某些问题](../../get-support/images/some_issues.svg) 图标。此图标可能指示有中断情况。
  * 通过“[{{site.data.keyword.Bluemix_notm}} - 系统状态](https://cloud.ibm.com/status){: external}”直接访问。

有关 {{site.data.keyword.Bluemix_notm}}“状态”页面的更多信息，请参阅[查看 {{site.data.keyword.Bluemix_notm}} 状态](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status)。


## 如何在管道作业之间传递工件？
{: #artifacts_pipeline_jobs}
{: faq}

由于一个阶段中的所有管道作业都会收到相同的阶段输入，因此无法在同一阶段的作业之间传递工件。但是，构建作业会生成其他阶段中的作业可以使用的工件。要在两个作业之间传递工件，请将这两个作业分别移入不同的阶段。有关管道作业的更多信息，请参阅[作业](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs)。


## 对于管道作业可以运行的最长时间有限制吗？
{: #pipeline_jobs_time_limit}
{: faq}

每个管道作业最长可运行 60 分钟。如果作业超过此时间限制，该作业会失败。检查管道作业执行的工作是否可以划分成更小的步骤。您可以将管道作业划分成若干个运行时间更短的管道作业，使其运行时间短于 60 分钟。


## 管道安全属性有多安全？
{: #pipeline_secure_properties}
{: faq}

管道安全属性使用 AES-128 进行加密，并在传递给管道脚本之前的那一刻才会解密。在属性用户界面和管道日志文件中，这些属性还会使用星号进行掩蔽。在将数据写入管道作业的日志文件之前，会扫描这些数据以查找与管道安全属性中的所有值完全匹配的内容。如果找到匹配项，将使用星号对其进行掩蔽。使用安全属性和日志文件时要小心，因为只有完全匹配项才会掩蔽。 
