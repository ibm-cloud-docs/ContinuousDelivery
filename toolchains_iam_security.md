---

copyright:
  years:  2018, 2019
lastupdated: "2019-12-17"

keywords: toolchains, user access, resource groups, IAM, access policy, Administrator Create, Editor Update, Update

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Managing user access to toolchains in resource groups
{: #toolchains-iam-security}

User access for toolchains in Cloud Foundry orgs is managed differently than user access to toolchains in resource groups. For more information about managing user access to toolchains in Cloud Foundry orgs, see [Managing access to toolchains in Cloud Foundry orgs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-cf-security).

Toolchains that you create in your account might not be visible to other users by default. Access to toolchains in resource groups for users in your account is controlled by [{{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM)](/docs/services/iam?topic=iam-iamoverview). You can assign access to [new users](#toolchains-access-new-users) and [existing users](#toolchains-access-existing-users) in your account.

User access for {{site.data.keyword.contdelivery_short}} service instances is managed separately. For more information about managing user access to {{site.data.keyword.contdelivery_short}} service instances in resource groups, see [Managing user access to {{site.data.keyword.contdelivery_short}} with Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security).
{: tip}

Every user that accesses toolchains in your account must be assigned an IAM access policy. The policy determines which toolchains the user can access and what actions the user is allowed to take.

Policies enable access to be granted at different levels or scopes, including, but not limited to: 

* Access across all toolchains in your account
* Access across all toolchains in a resource group in your account
* Access to a specific toolchain in your account

After you define the scope of the access policy, you assign a role. The role defines which actions the user is allowed to take. 

| Role | Actions |
|:-----------------|:-----------------|
| Viewer, Operator | View  |
| Editor, Administrator | View and edit |
{: caption="Table 1. User roles" caption-side="top"}


The following table lists the IAM user roles and the available toolchain actions for each role.

| Platform Management Role | Description of Actions | Example Actions|
|:-----------------|:-----------------|:-----------------|
| Viewer, Operator | View toolchains and delivery pipelines. Run delivery pipelines. | <ul><li>Click a toolchain to open its Overview page.</li><li>Click the **Run Stage** icon of the stage that your pipeline job is in.</li></ul> |
| Editor, Administrator | Create, view, update, and delete toolchains and delivery pipelines. |<ul><li>On the DevOps dashboard, on the Toolchains page, click **Create a Toolchain**.</li><li>On the DevOps dashboard, on the Toolchains page, click the toolchain to delete. Click the **More Actions** menu, which is next to **View app**. Click **Delete**.</li><li>On the DevOps dashboard, on the Toolchains page, click the toolchain to open its Overview page. Click **Add a Tool**, and then select the tool integration that you want to add.</li><li>On the DevOps dashboard, on the Pipeline page, click the **Stage Configuration** icon, and then click **Configure Stage**.</li></ul> |
{: caption="Table 2. IAM user roles and actions" caption-side="top"}


The following table lists and describes the available actions for toolchains:

| Action | Operation on Service | Role
|:-----------------|:-----------------|:--------------|
| toolchain.instance.create | Create a toolchain in a resource group. | Administrator, Editor |
| toolchain.instance.update | Update a toolchain in a resource group. For example, rename the toolchain. Change delivery pipelines that are bound to toolchains in a resource group. | Administrator, Editor |
| toolchain.instance.update_plan | Not applicable. | Administrator, Editor |
| toolchain.instance.delete | Delete a toolchain from a resource group. | Administrator, Editor |
| toolchain.instance.retrieve | View the details for a toolchain in a resource group. View and run delivery pipelines that are bound to toolchains in a resource group. | Administrator, Editor, Operator, Viewer |
| toolchain.instance.list-bindings | View the tool integrations that are bound to a toolchain in a resource group. | Administrator, Editor, Viewer |
| toolchain.instance.create-bindings | Add a tool integration to a toolchain in a resource group. | Administrator, Editor |
| toolchain.instance.delete-bindings | Remove a tool integration from a toolchain in a resource group. | Administrator, Editor |
| toolchain.instance.read-properties | Reserved for future use. | Administrator, Editor, Viewer |
| toolchain.instance.update-properties | Reserved for future use. | Administrator, Editor |
{: caption="Table 3. Service actions and operations" caption-side="top"}

## Assigning access to new users
{: #toolchains-access-new-users}

You can assign a new user access to all of the toolchains in your resource group.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Click **Invite users**.
3. Specify the email address of the user that you want to invite.
4. In the **Assign users additional access** section, click **IAM services**.
5. Choose to assign access to the **Toolchain** service within **All resource groups**.
6. In the **Platform access** section, select **Viewer** (or higher) access to provide the user with access to view toolchain service instances from the platform, perform platform actions that are required to configure and operate toolchain service instances, and assign access policies to other users.
7. In the **Resource group access** section, select the **Editor** role to provide the user with access to create, view, edit, or delete the toolchain service from resource groups. Select the **Viewer** role to provide the user with access to view toolchains only or to run delivery pipelines.
8. Click **Add**.
9. Click **Invite**. 

Depending on their role, the new user can now work with all of the toolchains within the specified resource groups. They can add tool integrations, modify and run pipelines, and use the Eclipse Orion {{site.data.keyword.webide}}.


## Assigning access to existing users
{: #toolchains-access-existing-users}

You can assign an existing user access to a toolchain in your resource group.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select the name of the user that you want to assign access.
3. In the **Assign users additional access** section, click **IAM services**.
4. Choose to assign access to the **Toolchain** service within **All resource groups**.
5. In the **Platform access** section, select **Viewer** (or higher) access to provide the user with access to view toolchain service instances from the platform, perform platform actions that are required to configure and operate toolchain service instances, and assign access policies to other users.
6. In the **Resource group access** section, select the **Editor** role to provide the user with access to create, view, edit, or delete the toolchain service from resource groups. Select the **Viewer** role to provide the user with access to view toolchains only or to run delivery pipelines.
7. Click **Add**.
8. Click **Invite**. 

Depending on their role, the user can now work with all of the toolchains within the specified resource group. They can add tool integrations, modify and run pipelines, and use the Eclipse Orion {{site.data.keyword.webide}}.

Although the most common and flexible methods for granting user access are described here, IAM supports other methods, such as by resource or resource type, or by resource group. For more information about how to assign users access to resources, such as toolchains, see [Managing access to resources](/docs/iam?topic=iam-iammanidaccser).
{: tip}
