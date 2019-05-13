---

copyright:
  years:  2018, 2019
lastupdated: "2019-02-27"

keywords: Administrator Create, Editor Update, Update, user access

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# 使用 Identity and Access Management 管理用户对工具链的访问权
{: #toolchains-iam-security}

{{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) 针对帐户中的用户控制对资源组中工具链的访问权。 

**注**： 

* 用户对工具链实例和 {{site.data.keyword.contdelivery_short}} 服务实例的访问权是单独管理的。有关管理用户对资源组中 {{site.data.keyword.contdelivery_short}} 服务实例的访问权的更多信息，请参阅[使用 Identity and Access Management 管理用户对 {{site.data.keyword.contdelivery_short}} 的访问权](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security){: new_window}。

* 用户对 Cloud Foundry 组织中工具链的访问权的管理方式与用户对资源组中 {{site.data.keyword.contdelivery_short}} 服务实例的访问权的管理方式不同。有关管理用户对 Cloud Foundry 组织中工具链访问权的更多信息，请参阅[管理对 Cloud Foundry 组织中工具链的访问权](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}。

对于访问您帐户中的工具链的每个用户，必须向其分配定义了 IAM 用户角色的访问策略。该策略确定用户可在您所选服务或实例的上下文中执行的操作。
{{site.data.keyword.Bluemix_notm}} 服务作为允许在服务上执行的操作来定制和定义允许的操作。然后，这些操作将映射到 IAM 用户角色。

策略允许在不同级别授予访问权，包括： 

* 对帐户中所有服务实例的访问权
* 对帐户中单个服务实例的访问权
* 对实例中特定资源的访问权
* 对帐户中所有启用 IAM 的服务的访问权

在定义访问策略的范围后，您将分配一个角色。复查下表，其中概述每个角色在工具链中允许的操作。

下表详述映射到平台管理角色的操作。平台管理角色支持用户在平台级别对服务资源执行任务，例如，分配服务的用户访问权、创建或删除服务标识、创建实例以及将实例绑定到应用程序。

|平台管理角色|操作描述|示例操作|
|:-----------------|:-----------------|:-----------------|
|查看者、操作员|查看工具链和 Delivery Pipeline。运行 Delivery Pipeline。| <ul><li>单击工具链可打开其“概述”页面。</li><li>单击管道作业所在阶段的**运行阶段**图标。</li></ul> |
|编辑者、管理员|创建、查看、更新和删除工具链和 Delivery Pipeline。|<ul><li>在 DevOps 仪表板的**工具链**页面上，单击**创建工具链**。</li><li>在 DevOps 仪表板的**工具链**页面上，单击工具链，以打开其“概述”页面。</li><li>在 DevOps 仪表板的**工具链**页面上，单击要删除的工具链。单击**更多操作**菜单，其位于**查看应用程序**的旁边。单击**删除**。</li></ul> |
{: caption="表 1. IAM 用户角色和操作" caption-side="top"}

 对于工具链，存在以下操作：

|操作|关于服务的操作|角色
|:-----------------|:-----------------|:--------------|
| create |在资源组中创建工具链。|管理员、编辑者 |
| update |更新资源组中的工具链。例如，重命名工具链。更改绑定到资源组中的工具链的 Delivery Pipeline。|管理员、编辑者 |
| update_plan |不适用。|管理员、编辑者 |
| delete |从资源组删除工具链。|管理员、编辑者 |
| retrieve |查看资源组中工具链的详细信息。查看并运行绑定到资源组中的工具链的 Delivery Pipeline。|管理员、编辑者、操作员、查看者|
| list-bindings |查看绑定到资源组中的工具链的工具集成。|管理员、编辑者、查看者|
| create-bindings |向资源组中的工具链添加工具集成。|管理员、编辑者 |
| delete-bindings |从资源组中的工具链除去工具集成。|管理员、编辑者 |
{: caption="表 2. 服务操作" caption-side="top"}

有关在 UI 中分配用户角色的信息，请参阅[管理 IAM 访问权](/docs/iam?topic=iam-iammanidaccser)。

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
