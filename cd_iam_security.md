---

copyright:
  years:  2018, 2019
lastupdated: "2019-08-20"

keywords: Administrator Create, Administrator Update, Editor Update, service access roles, IAM, access policies

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


# Managing user access to Continuous Delivery in resource groups
{: #cd-iam-security}

Access to {{site.data.keyword.contdelivery_full}} service instances in resource groups for users in your account is controlled by {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

User access for toolchains is managed separately. For more information about managing user access to toolchains in resource groups, see [Managing user access to toolchains in resource groups](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security).
{: tip}

Every user that accesses {{site.data.keyword.contdelivery_short}} services in your account must be assigned an IAM access policy. The policy determines which {{site.data.keyword.contdelivery_short}} instances the user can access and what actions the user is allowed to take.

Policies enable access to be granted at different levels or scopes, including, but not limited to:

* Access across all {{site.data.keyword.contdelivery_short}} instances in your account
* Access across all {{site.data.keyword.contdelivery_short}} instances in a resource group within your account
* Access to a specific {{site.data.keyword.contdelivery_short}} instance in your account

After you define the scope of the access policy, you assign a role. Review the following tables which outline what actions each role allows within the {{site.data.keyword.contdelivery_short}} service.

The following table details actions that are mapped to platform management roles. Platform management roles enable users to perform tasks on service resources at the platform level, for example assign user access for the service, create or delete service IDs, create instances, and bind instances to applications.

| Platform Management Role | Description of Actions | Example Actions|
|:-----------------|:-----------------|:-----------------|
| Viewer, Operator | View instances of the {{site.data.keyword.contdelivery_short}} service. | <ul><li>Click a {{site.data.keyword.contdelivery_short}} service instance to open its dashboard.</li></ul>|
| Editor, Administrator | Create, view, update, modify the plan for, and delete instances of the {{site.data.keyword.contdelivery_short}} service. |<ul><li>Provision an instance of {{site.data.keyword.contdelivery_short}} in a resource group.</li><li>Delete an instance of {{site.data.keyword.contdelivery_short}} from a resource group.</li><li>Change a {{site.data.keyword.contdelivery_short}} instance plan from Lite to Professional.</li></ul> |
| Administrator | Update the Authorized Users list.| <ul><li>Add a user to the Authorized Users list.</li><li>Remove a user from the Authorized Users list.</li></ul> |
{: caption="Table 1. IAM user roles and actions" caption-side="top"}

 The following table details actions that are mapped to service access roles. Service access roles enable users access to {{site.data.keyword.contdelivery_short}} as well as the ability to call the {{site.data.keyword.contdelivery_short}} API.

| Service Access Role | Description of Actions | Example Actions|
|:-----------------|:-----------------|:-----------------|
| Writer, Manager | Add and remove users from the Authorized Users list on the Manage tab within a {{site.data.keyword.contdelivery_short}} service instance. | <ul><li>Add authorized user.</li><li>Remove authorized user.</li></ul>|
{: caption="Table 2. IAM service access roles and actions" caption-side="top"}

For information about assigning user roles in the UI, see [Managing IAM access](/docs/iam?topic=iam-iammanidaccser).
 
For {{site.data.keyword.contdelivery_short}}, the following actions exist:

| Action | Operation on Service | Role
|:-----------------|:-----------------|:--------------|
| create | Provision a {{site.data.keyword.contdelivery_short}} service instance in a resource group. | Administrator, Editor |
| update | Update a {{site.data.keyword.contdelivery_short}} service instance in a resource group. For example, rename the service instance. | Administrator, Editor |
| update_plan | Change the plan for the {{site.data.keyword.contdelivery_short}} service instance in a resource group. | Administrator, Editor |
| delete | Delete a {{site.data.keyword.contdelivery_short}} service instance from a resource group. | Administrator, Editor |
| retrieve | View a {{site.data.keyword.contdelivery_short}} service instance in a resource group. | Administrator, Editor, Operator, Viewer |
| add-auth-users | Add entries to the Authorized Users list on the Manage tab within the {{site.data.keyword.contdelivery_short}} service instance. | Administrator, Writer, Manager |
| remove-auth-users | Remove entries from the Authorized Users list on the Manage tab within the {{site.data.keyword.contdelivery_short}} service instance. | Administrator, Writer, Manager |
{: caption="Table 3. Service actions and operations" caption-side="top"}
