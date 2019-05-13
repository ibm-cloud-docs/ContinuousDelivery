---

copyright:
  years:  2018, 2019
lastupdated: "2019-02-25"

keywords: Administrator Create, Administrator Update, Editor Update, Update

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


# 使用 Identity and Access Management 管理用户对 Continuous Delivery 的访问权
{: #cd-iam-security}

{{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) 针对帐户中的用户控制对资源组中 {{site.data.keyword.contdelivery_full}} 服务实例的访问权。 

**注**： 

* 单独管理用户对 {{site.data.keyword.contdelivery_short}} 服务实例和工具链实例的访问权。有关管理用户对资源组中工具链的访问权的更多信息，请参阅[使用 Identity and Access Management 管理用户对工具链的访问权](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}。

* 用户对 Cloud Foundry 组织中工具链的访问权的管理方式与用户对资源组中工具链的访问权的管理方式不同。有关管理用户对 Cloud Foundry 组织中工具链访问权的更多信息，请参阅[管理对 Cloud Foundry 组织中工具链的访问权](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}。

对于访问您帐户中的 {{site.data.keyword.contdelivery_short}} 服务的每个用户，必须向其分配定义了 IAM 用户角色的访问策略。该策略确定用户可在您所选服务或实例的上下文中执行的操作。
{{site.data.keyword.Bluemix_notm}} 服务作为允许在服务上执行的操作来定制和定义允许的操作。然后，这些操作将映射到 IAM 用户角色。

策略允许在不同级别授予访问权。部分选项包括： 

* 对帐户中所有服务实例的访问权
* 对帐户中单个服务实例的访问权
* 对实例中特定资源的访问权
* 对帐户中所有启用 IAM 的服务的访问权

在定义访问策略的范围后，您将分配一个角色。复查下表，其中概述每个角色在 {{site.data.keyword.contdelivery_short}} 服务中允许的操作。

下表详述映射到平台管理角色的操作。平台管理角色支持用户在平台级别对服务资源执行任务，例如，分配服务的用户访问权、创建或删除服务标识、创建实例以及将实例绑定到应用程序。

|平台管理角色|操作描述|示例操作|
|:-----------------|:-----------------|:-----------------|
|查看者、操作员|查看 {{site.data.keyword.contdelivery_short}} 服务的实例。| <ul><li>单击 {{site.data.keyword.contdelivery_short}} 服务实例以打开其仪表板。</li></ul>|
|编辑者、管理员|创建、查看、更新、修改 {{site.data.keyword.contdelivery_short}} 服务实例的套餐，以及删除该实例。|<ul><li>在资源组中供应 {{site.data.keyword.contdelivery_short}} 的实例。</li><li>从资源组删除 {{site.data.keyword.contdelivery_short}} 的实例。</li><li>将 {{site.data.keyword.contdelivery_short}} 实例套餐从轻量更改为专业。</li></ul> |
|管理员|更新“授权用户”列表。| <ul><li>向“授权用户”列表添加用户。</li><li>从“授权用户”列表除去用户。</li></ul> |
{: caption="表 1. IAM 用户角色和操作" caption-side="top"}

 对于 {{site.data.keyword.contdelivery_short}}，存在以下操作：

|操作|关于服务的操作|角色
|:-----------------|:-----------------|:--------------|
| create |在资源组中供应 {{site.data.keyword.contdelivery_short}} 服务实例。|管理员、编辑者 |
| update |更新资源组中的 {{site.data.keyword.contdelivery_short}} 服务实例。例如，重命名服务实例。|管理员、编辑者 |
| update_plan |更改资源组中 {{site.data.keyword.contdelivery_short}} 服务实例的套餐。|管理员、编辑者 |
| delete |从资源组删除 {{site.data.keyword.contdelivery_short}} 服务实例。|管理员、编辑者 |
| retrieve |查看资源组中的 {{site.data.keyword.contdelivery_short}} 服务实例。|管理员、编辑者、操作员、查看者|
| add-auth-users |在 {{site.data.keyword.contdelivery_short}} 服务实例中的“管理”选项卡上向“授权用户”列表添加条目。|管理者、写入者、管理者|
| remove-auth-users |在 {{site.data.keyword.contdelivery_short}} 服务实例中的“管理”选项卡上除去“授权用户”列表中的条目。|管理者、写入者、管理者|
{: caption="表 2. 服务操作" caption-side="top"}

下表详细描述了映射到服务访问角色的操作。服务访问角色支持用户访问 {{site.data.keyword.contdelivery_short}} 以及调用 {{site.data.keyword.contdelivery_short}} API。

|服务访问角色 |操作描述|示例操作|
|:-----------------|:-----------------|:-----------------|
|写入者、管理者|在 {{site.data.keyword.contdelivery_short}} 服务实例中的“管理”选项卡上向“授权用户”列表添加用户和除去其中的用户。| <ul><li>添加授权用户。</li><li>除去授权用户。</li></ul>|
{: caption="表T 3. IAM 服务访问角色和操作" caption-side="top"}

有关在 UI 中分配用户角色的信息，请参阅[管理 IAM 访问权](/docs/iam?topic=iam-iammanidaccser)。

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
