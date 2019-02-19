---

copyright:
  years:  2018, 2019
lastupdated: "2019-2-1"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Managing user access to Continuous Delivery with Identity and Access Management
{: #cd-iam-security}

Access to {{site.data.keyword.contdelivery_full}} service instances in resource groups for users in your account is controlled by {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Notes**: 

* User access for {{site.data.keyword.contdelivery_short}} service instances and toolchain instances is managed separately. For more information about managing user access to toolchains in resource groups, see [Managing user access to toolchains with Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}.

* User access for toolchains in Cloud Foundry orgs is managed differently than user access to toolchains in resource groups. For more information about managing user access to toolchains in Cloud Foundry orgs, see [Managing access to toolchains in Cloud Foundry orgs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.

Every user that accesses the {{site.data.keyword.contdelivery_short}} service in your account must be assigned an access policy with an IAM user role defined. That policy determines what actions the user can perform within the context of the service or instance you select. The allowable actions are customized and defined by the {{site.data.keyword.Bluemix_notm}} service as operations that are allowed to be performed on the service. The actions are then mapped to IAM user roles.

Policies enable access to be granted at different levels. Some of the options include the following: 

* Access across all instances of the service in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance
* Access to all IAM-enabled services in your account

After you define the scope of the access policy, you assign a role. Review the following tables which outline what actions each role allows within the {{site.data.keyword.contdelivery_short}} service.

The following table details actions that are mapped to platform management roles. Platform management roles enable users to perform tasks on service resources at the platform level, for example assign user access for the service, create or delete service IDs, create instances, and bind instances to applications.

| Platform management role | Description of actions | Example actions|
|:-----------------|:-----------------|:-----------------|
| Viewer, Operator | View instances of the {{site.data.keyword.contdelivery_short}} service. | <ul><li>Click a {{site.data.keyword.contdelivery_short}} service instance to open its dashboard.</li></ul>|
| Editor, Administrator | Create, view, update, modify the plan for, and delete instances of the {{site.data.keyword.contdelivery_short}} service. |<ul><li>Provision an instance of {{site.data.keyword.contdelivery_short}} in a resource group.</li><li>Delete an instance of {{site.data.keyword.contdelivery_short}} from a resource group.</li><li>Change a {{site.data.keyword.contdelivery_short}} instance plan from Lite to Professional.</li></ul> |
| Administrator | Update the Authorized Users list.| <ul><li>Add a user to the Authorized Users list.</li><li>Remove a user from the Authorized Users list.</li></ul> |
{: caption="Table 1. IAM user roles and actions" caption-side="top"}

 For {{site.data.keyword.contdelivery_short}}, the following actions exist:

| Action | Operation on service | Role
|:-----------------|:-----------------|:--------------|
| create | Provision a {{site.data.keyword.contdelivery_short}} service instance in a resource group. | Administrator, Editor |
| update | Update a {{site.data.keyword.contdelivery_short}} service instance in a resource group. For example, rename the service instance. | Administrator, Editor |
| update_plan | Change the plan for the {{site.data.keyword.contdelivery_short}} service instance in a resource group. | Administrator, Editor |
| delete | Delete a {{site.data.keyword.contdelivery_short}} service instance from a resource group. | Administrator, Editor |
| retrieve | View a {{site.data.keyword.contdelivery_short}} service instance in a resource group. | Administrator, Editor, Operator, Viewer |
| add-auth-users | Add entries to the Authorized Users list on the Manage tab within the {{site.data.keyword.contdelivery_short}} service instance. | Administrator, Writer, Manager |
| remove-auth-users | Remove entries from the Authorized Users list on the Manage tab within the {{site.data.keyword.contdelivery_short}} service instance. | Administrator, Writer, Manager |
{: caption="Table 2. Service actions and operations" caption-side="top"}

The following table details actions that are mapped to service access roles. Service access roles enable users access to {{site.data.keyword.contdelivery_short}} as well as the ability to call the {{site.data.keyword.contdelivery_short}} API.

| Service access role | Description of actions | Example actions|
|:-----------------|:-----------------|:-----------------|
| Writer, Manager | Add and remove users from the Authorized Users list on the Manage tab within a {{site.data.keyword.contdelivery_short}} service instance. | <ul><li>Add authorized user.</li><li>Remove authorized user.</li></ul>|
{: caption="Table 3. IAM service access roles and actions" caption-side="top"}

For information about assigning user roles in the UI, see [Managing IAM access](/docs/iam?topic=iam-iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
