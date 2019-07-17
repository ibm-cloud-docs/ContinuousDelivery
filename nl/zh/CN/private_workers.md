---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# 使用 {{site.data.keyword.deliverypipeline}} Private Worker
{: #private-workers}

{{site.data.keyword.deliverypipeline}} 使用公共和专用工作程序来运行管道作业。缺省情况下，管道作业是使用公共工作程序在 IBM 管理的公共共享基础架构上运行的。
{: shortdesc}

在某些情况下，{{site.data.keyword.deliverypipeline}} 可能需要访问内部或内部部署资源。在这些情况下，可以连接到 {{site.data.keyword.deliverypipeline}} Private Worker 并与之集成以在您自己的 Kubernetes 基础架构上运行。

## 先决条件
{: #private_workers_prereqs}

设置专用工作程序之前，请确保以下资源已就位：

* Kubernetes 集群。您必须具有集群才能安装专用工作程序。您可以提供自己的集群，也可以通过 {{site.data.keyword.containerlong_notm}} [设置集群](https://cloud.ibm.com/kubernetes/clusters){:external}。

* 具有管道的工具链，管道中至少包含一个阶段。可以使用现有工具链，也可以[创建工具链](https://cloud.ibm.com/devops/create){:external}。

## 设置 {{site.data.keyword.deliverypipeline}} Private Worker
{: #set_up_private_worker}

要设置专用工作程序，请完成以下步骤：

1. 为工具链配置 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成。
2. 配置 Kubernetes 集群以使用专用工作程序。
3. 在管道中使用专用工作程序。

### 配置 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成
{: #configure_private_worker_integration}

要为工具链配置 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成，请完成以下步骤：

1. 如果您在创建工具链时配置此工具集成，请在“可配置的集成”部分中，单击 **{{site.data.keyword.deliverypipeline}} Private Worker**。
1. 如果您有工具链，并且要将此工具集成添加到该工具链，请在 DevOps 仪表板的“工具链”页面上单击该工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。

 a. 单击**添加工具**。

 b. 在“工具集成”部分中，单击 **{{site.data.keyword.deliverypipeline}} Private Worker**。

1. 输入工具集成的名称。此名称用于在管道阶段的**工作程序**选项卡中标识专用工作程序池。
1. 输入服务标识 API 密钥，以认证对工作队列的访问权，在此队列中，一个或多个专用工作程序可以查找工作。如果您没有服务标识 API 密钥，请单击**创建**为此专用工作程序生成服务标识 API 密钥。
1. 单击**创建集成**。
1. 在工具链中，单击 **{{site.data.keyword.deliverypipeline}} Private Worker** 以查看使用与此服务标识关联的 API 密钥注册的所有工作程序的列表。

有关配置 **{{site.data.keyword.deliverypipeline}} Private Worker** 工具集成的更多信息，请参阅[配置 {{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker)。

### 配置 Kubernetes 集群
{: #configure_kubernetes_cluster}

配置 Kubernetes 集群以使用专用工作程序：

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 单击要配置的 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的卡。
1. 单击**开始使用**，然后执行相关步骤在 Kubernetes 集群上安装和注册专用工作程序。

### 在管道中使用 {{site.data.keyword.deliverypipeline}} Private Worker
{: #use_private_worker_pipeline}

要在管道中使用专用工作程序，请完成以下步骤：

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 单击要将专用工作程序用于的管道的卡。
1. 在“管道”页面的阶段上，单击**阶段配置**图标，然后单击**配置阶段**。
1. 单击**工作程序**选项卡。
1. 选择要在管道中使用的专用工作程序。 

 缺省情况下，管道阶段中的作业在定义管道的区域中使用 IBM 管理的共享工作程序池运行。
 {: tip}
 
1. 单击**保存**。
1. 可以手动运行阶段，也可以等待触发器触发，以使用关联 Kubernetes 集群上的指定专用工作程序来运行阶段上的作业。您可以查看作业的日志文件输出，以确定使用的工作程序。  


## 修改 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成凭证
{: #modify_private_worker}

设置专用工作程序后，可以更新用于工具集成的凭证。如果这些凭证已被删除、已到期或已泄露，那么您可能希望更改这些凭证。可以通过创建新的服务标识或更新 API 密钥来更新凭证。

### 创建服务标识
{: #create_service_id}

要创建服务标识，请完成以下步骤：

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 在要修改的 Private Worker 工具集成的卡上，单击菜单以访问配置选项。
1. 单击**创建**。
1. 输入服务标识的名称和描述。
1. 单击**保存集成**。
1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 单击要为其指定新用户凭证的 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的卡。
1. 单击**开始使用**，并完成步骤 2 和 3 以在集群上注册和验证专用工作程序。

### 更新 API 密钥
{: #update_api_key}

要更新用于 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的 API 密钥，请完成以下步骤：

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 在要修改的 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的卡上，单击菜单以访问配置选项。
1. 指定新的 API 密钥。 
1. 单击**保存集成**。

## 删除 {{site.data.keyword.deliverypipeline}} Private Worker
{: #delete_private_worker}

要删除专用工作程序，请完成以下步骤：

1. 从工作程序池中删除专用工作程序。
1. 从 Kubernetes 集群中删除专用工作程序。

### 从工作程序池中删除 {{site.data.keyword.deliverypipeline}} Private Worker

要从工作程序池中删除专用工作程序，请完成以下步骤：

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 单击要配置的 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的卡。
1. 单击**概述**。
1. 单击要删除的专用工作程序的菜单，以访问配置选项。
1. 单击**除去**，然后单击**确认**。

### 从 Kubernetes 集群中删除 {{site.data.keyword.deliverypipeline}} Private Worker

要从集群中删除专用工作程序，请完成以下步骤：

1. 单击要配置的 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的卡。
1. 单击**开始使用**，然后执行相关步骤从集群中删除专用工作程序。

## 删除 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成
{: #delete_private_workers_tool_integration}

如果从工具链中删除 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成，那么该删除操作无法撤销。
{: important}

要删除 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成，请完成以下步骤：

1. 在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。或者，在应用程序“概述”页面的“持续交付”卡上，单击**查看工具链**，然后单击**概述**。
1. 在要删除的 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成的卡上，单击菜单以访问配置选项。
1. 要从工具链删除工具集成，请单击**删除**。
1. 单击**删除**以确认。这将从工具链中除去 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成，并且工具集成在 Delivery Pipeline 的“阶段配置”页面的**工作程序**选项卡中不再可用。

如果从工具链中删除了 {{site.data.keyword.deliverypipeline}} Private Worker 工具集成，但专用工作程序已配置用于管道阶段，那么该工作程序仍会在“阶段配置”页面的**工作程序**选项卡中列出。但是，该专用工作程序已禁用并标注为“已除去”。您必须选择其他专用工作程序（如果存在）或改为使用公共工作程序。
{: tip}
