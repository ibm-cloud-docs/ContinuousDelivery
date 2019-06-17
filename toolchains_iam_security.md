---

copyright:
  years:  2018, 2019
lastupdated: "2019-06-14"

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


# Managing user access to toolchains with Identity and Access Management
{: #toolchains-iam-security}

Access to toolchains in resource groups for users in your account is controlled by {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Notes**: 

* User access for toolchain instances and {{site.data.keyword.contdelivery_short}} service instances is managed separately. For more information about managing user access to {{site.data.keyword.contdelivery_short}} service instances in resource groups, see [Managing user access to {{site.data.keyword.contdelivery_short}} with Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security).

* User access for toolchains in Cloud Foundry orgs is managed differently than user access to {{site.data.keyword.contdelivery_short}} service instances in resource groups. For more information about managing user access to toolchains in Cloud Foundry orgs, see [Managing access to toolchains in Cloud Foundry orgs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs).

Every user that accesses toolchains in your account must be assigned an access policy with an IAM user role defined. That policy determines what actions the user can perform within the context of the service or instance you select. The allowable actions are customized and defined by the {{site.data.keyword.Bluemix_notm}} service as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles.

Policies enable access to be granted at different levels, including: 

* Access across all instances of the service in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance
* Access to all IAM-enabled services in your account

After you define the scope of the access policy, you assign a role. Review the following tables which outline what actions each role allows within toolchains.

The following table details actions that are mapped to platform management roles. Platform management roles enable users to perform tasks on service resources at the platform level, for example assign user access for the service, create or delete service IDs, create instances, and bind instances to applications.

| Platform Management Role | Description of Actions | Example Actions|
|:-----------------|:-----------------|:-----------------|
| Viewer, Operator | View toolchains and delivery pipelines. Run delivery pipelines. | <ul><li>Click a toolchain to open its Overview page.</li><li>Click the **Run Stage** icon of the stage that your pipeline job is in.</li></ul> |
| Editor, Administrator | Create, view, update, and delete toolchains and delivery pipelines. |<ul><li>On the DevOps dashboard, on the **Toolchains** page, click **Create a Toolchain**.</li><li>On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page.</li><li>On the DevOps dashboard, on the **Toolchains** page, click the toolchain to delete. Click the **More Actions** menu, which is next to **View app**. Click **Delete**.</li></ul> |
{: caption="Table 1. IAM user roles and actions" caption-side="top"}

 For toolchains, the following actions exist:

| Action | Operation on Service | Role
|:-----------------|:-----------------|:--------------|
| create | Create a toolchain in a resource group. | Administrator, Editor |
| update | Update a toolchain in a resource group. For example, rename the toolchain. Change delivery pipelines that are bound to toolchains in a resource group. | Administrator, Editor |
| update_plan | Not applicable. | Administrator, Editor |
| delete | Delete a toolchain from a resource group. | Administrator, Editor |
| retrieve | View the details for a toolchain in a resource group. View and run delivery pipelines that are bound to toolchains in a resource group. | Administrator, Editor, Operator, Viewer |
| list-bindings | View the tool integrations that are bound to a toolchain in a resource group. | Administrator, Editor, Viewer |
| create-bindings | Add a tool integration to a toolchain in a resource group. | Administrator, Editor |
| delete-bindings | Remove a tool integration from a toolchain in a resource group. | Administrator, Editor |
{: caption="Table 2. Service actions and operations" caption-side="top"}

For information about assigning user roles in the UI, see [Managing IAM access](/docs/iam?topic=iam-iammanidaccser).
