---

copyright:
  years:  2018, 2023
lastupdated: "2023-12-05"

keywords: toolchains, user access, resource groups, IAM, access policy, Administrator Create, Editor Update, Update

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Managing access for toolchains in resource groups
{: #toolchains-iam-security}

Toolchains that you create in your account might not be visible to other users by default. Access to toolchains in resource groups for users in your account is controlled by [{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM)](/docs/services/account?topic=account-iamoverview). You can assign access to [new users](#toolchains-access-new-users) and [existing users](#toolchains-access-existing-users) in your account.

User access for {{site.data.keyword.contdelivery_short}} service instances is managed separately. For more information about managing user access to {{site.data.keyword.contdelivery_short}} service instances in resource groups, see [Managing user access to {{site.data.keyword.contdelivery_short}} with Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security).
{: tip}

Every user that accesses toolchains in your account must be assigned an IAM access policy. The policy determines which toolchains the user can access and what actions the user is allowed to take.

Policies enable access to be granted at different levels or scopes, including, but not limited to: 

* Access across all toolchains in your account
* Access across all toolchains in a resource group in your account
* Access to a specific toolchain in your account

After you define the scope of the access policy, you assign a role. The role defines which actions the user is allowed to take. The following table lists the IAM platform access roles and the available toolchain actions for each role.

| Platform Role | Description of Actions | Example Actions|
|:-----------------|:-----------------|:-----------------|
| Viewer | View toolchains and delivery pipelines. | * Click a toolchain to open its Overview page.  |
| Operator | View toolchains and delivery pipelines. Run delivery pipelines. Send client bespoke toolchain events. | * Click a toolchain to open its Overview page.  \n  \n * Click the **Run Stage** icon of the stage that your pipeline job is in.  \n  \n * Invoke the [POST /toolchains/{toolchain_id}/events](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external} API. |
| Editor, Administrator | Create, view, update, and delete toolchains and delivery pipelines. Run delivery pipelines. Send client bespoke toolchain events. | * From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the Toolchains page, click **Create a Toolchain**.  \n  \n * From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the Toolchains page, click the toolchain to delete. Click the **Actions** menu, then select **Delete**.  \n  \n * From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Click **Add tool**, and then select the tool integration that you want to add.  \n  \n * From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the Pipeline page, click the **Stage Configuration** icon, and then click **Configure Stage**. \n  \n * Click the **Run Stage** icon of the stage that your pipeline job is in.  \n  \n * Invoke the [POST /toolchains/{toolchain_id}/events](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external} API.  |
{: caption="Table 1. IAM platform roles" caption-side="bottom"}

The following table lists the IAM service access roles and the available actions for each role.

| Service Role | Description of Actions | Example Actions|
|:-----------------|:-----------------|:-----------------|
| EventSender | Send client bespoke toolchain events. | Invoke the [POST /toolchains/{toolchain_id}/events](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external} API. |
| PipelineRunner | Run delivery pipelines. | Click the **Run Stage** icon of the stage that your pipeline job is in. |
{: caption="Table 2. IAM service access roles" caption-side="bottom"}

EventSender access grants only the ability to send client bespoke toolchain events. To take other actions against a toolchain, other roles such as Viewer, Operator, Editor, or Administrator are required.
{: tip}

PipelineRunner access grants only the ability to run a delivery pipeline. To view a pipeline from the UI, an extra role such as the Viewer role is required.
{: tip}

The following table lists and describes the available actions for toolchains:

| Action | Operation on Service | Role
|:-----------------|:-----------------|:--------------|
| resource-controller.instance.create | Create a toolchain in a resource group. | Administrator, Editor |
| resource-controller.instance.update | Update a toolchain or a tool integration that is bound to a toolchain in a resource group. For example, rename the toolchain. Change delivery pipelines that are bound to toolchains in a resource group. | Administrator, Editor |
| resource-controller.instance.update_plan | Not applicable. | Administrator, Editor |
| resource-controller.instance.delete | Delete a toolchain from a resource group. | Administrator, Editor |
| resource-controller.instance.retrieve | View the details for a toolchain or for a tool integration that is bound to a toolchain in a resource group. | Administrator, Editor, Operator, Viewer |
| toolchain.event.send | Send a client bespoke toolchain event. | Administrator, Editor, EventSender, Operator |
| toolchain.instance.create-bindings | Add a tool integration to a toolchain in a resource group. | Administrator, Editor |
| toolchain.instance.delete-bindings | Remove a tool integration from a toolchain in a resource group. | Administrator, Editor |
| toolchain.instance.read-properties | Reserved for future use. | Administrator, Editor, Viewer |
| toolchain.instance.update-properties | Reserved for future use. | Administrator, Editor |
| toolchain.pipeline-run.create | Run a delivery pipeline. | Administrator, Editor, Operator, PipelineRunner |
{: caption="Table 3. Service actions and operations" caption-side="bottom"}

## Assigning access to new users
{: #toolchains-access-new-users}

You can assign a new user access to all of the toolchains in your resource group.

1. From the {{site.data.keyword.cloud_notm}} console, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Click **Invite users**.
3. Specify the email address of the user that you want to invite.
4. In the **How do you want to assign access?** section, click **Access Policy**.
5. Choose to assign access to the **Toolchain** service.
6. Scope the access to **Specific resources.** Select the **Resource group** attribute type and enter a resource group.
7. In the **Resource group access** section, select **Viewer** (or higher) access to provide the user with access to view toolchain service instances from the platform, perform platform actions that are required to configure and operate toolchain service instances, and assign access policies to other users.
8. In the **Roles and actions** section, select the **Editor** role to provide the user with access to create, view, edit, or delete the toolchain service from resource groups. Select the **Viewer** role to provide the user with access to view toolchains only. Select both the **Viewer** and **PipelineRunner** roles to provide the user with access to view toolchains or to run delivery pipelines.
9. Click **Add**.
10. Click **Invite**.

Depending on their role, the new user can now work with all of the toolchains within the specified resource groups. They can add tool integrations and modify and run pipelines.


## Assigning access to existing users
{: #toolchains-access-existing-users}

You can assign an existing user access to a toolchain in your resource group.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. From the row for the user that you want to assign access, select the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu.
3. Click **Assign access**.
4. In the **How do you want to assign access?** section, click **Access Policy**.
5. Choose to assign access to the **Toolchain** service.
6. Scope the access to **Specific resources.** Select the **Resource group** attribute type and enter a resource group.
7. In the **Resource group access** section, select **Viewer** (or higher) access to provide the user with access to view toolchain service instances from the platform, perform platform actions that are required to configure and operate toolchain service instances, and assign access policies to other users.
8. In the **Roles and actions** section, select the **Editor** role to provide the user with access to create, view, edit, or delete the toolchain service from resource groups. Select the **Viewer** role to provide the user with access to view toolchains only. Select both the **Viewer** and **PipelineRunner** roles to provide the user with access to view toolchains or to run delivery pipelines.
9. Click **Add**.
10. Click **Assign**.

Depending on their role, the user can now work with all of the toolchains within the specified resource group. They can add tool integrations and modify and run pipelines.

Although the most common and flexible methods for granting user access are described here, IAM supports other methods, such as by resource or resource type, or by resource group. For more information about how to assign users access to resources, such as toolchains, see [Managing access to resources](/docs/account?topic=account-assign-access-resources).
{: tip}

