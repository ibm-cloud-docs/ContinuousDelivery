---

copyright:
  years: 2016, 2025
lastupdated: "2025-06-27"

keywords: users of a service instance, authorized users, pipeline usage, Git Repos and Issue Tracking limitations, consolidated billing

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Plan limitations and usage
{: #limitations_usage}
{: help}
{: support}

The use of {{site.data.keyword.contdelivery_full}} is limited to the building, deploying, testing, and ongoing operations of applications on the {{site.data.keyword.cloud_notm}} platform or other compatible platform-as-a-service (PaaS) or infrastructure-as-a-service (IaaS) products.

## Scope of a service instance
{: #service_scope}

You must have a {{site.data.keyword.contdelivery_short}} [service instance](https://cloud.ibm.com/catalog/services/continuous-delivery){: external} to create and use DevOps toolchains that include the {{site.data.keyword.deliverypipeline}}, {{site.data.keyword.gitrepos}}, and {{site.data.keyword.DRA_short}} tool integrations. A service instance resides in a region and belongs to a [resource group](/docs/account?topic=account-rgs). The {{site.data.keyword.contdelivery_short}} service instance in a specific region and resource group governs and meters your usage of all of the toolchains in the same region and resource group.

## Pricing plans
{: #pricing_plans}



The following table outlines the pricing plans of {{site.data.keyword.contdelivery_short}}:

| Plan | Cost | Limits |
|:-----|:-----|:-------|
| **Lite** | Free | The Lite plan offers the full capabilities of {{site.data.keyword.contdelivery_short}} with limits on usage. |
| **Professional** | Paid | The Professional plan offers the full capabilities of {{site.data.keyword.contdelivery_short}} with no limits on usage. |
{: caption="Pricing plans" caption-side="bottom"}





You can have at most one Lite service instance per account. It is recommended that you use the Professional plan if you want to work with toolchains in multiple resource groups or within multiple regions.
{: tip}

For more information, see [pricing plans](https://cloud.ibm.com/catalog/services/continuous-delivery){: external}.

## Usage metrics
{: #usage_metrics}

{{site.data.keyword.contdelivery_short}} service instances track and report usage metrics within your {{site.data.keyword.cloud_notm}} account. Depending on the pricing plan of a service instance, the metrics might affect usage cost, usage limits, or both. The following table outlines the usage metrics of {{site.data.keyword.contdelivery_short}}:



| Usage | Metric | Summary |
|:------|:-------|:--------|
| Authorized users | `AUTHORIZED_USERS_PER_MONTH` | A count of the average number of authorized users of the service instance within a given month. |
| Pipeline runs | `JOB_EXECUTIONS_PER_MONTH` | A count of the total number of pipeline Tekton step or classic job runs within a given month. |
{: caption="Usage metrics for Lite and Professional plans" caption-side="bottom"}





## Consolidated billing
{: #consolidated_billing}

By default, {{site.data.keyword.contdelivery_short}} service instances report usage independently of each other. If you have organized your toolchains into multiple resource groups in a stand-alone account or across several accounts in an [enterprise](/docs/enterprise-management?topic=enterprise-management-what-is-enterprise), users of your toolchains might be reported as authorized users multiple times from corresponding multiple instances of the {{site.data.keyword.contdelivery_short}} service.

For example, a developer on a Git Repos and Issue Tracking project that is integrated into two toolchains in different resource groups will be counted and, under the Professional plan, billed for twice.

Consolidated billing is disabled by default. However, you can enable consolidated billing of a {{site.data.keyword.contdelivery_short}} service instance with the Professional plan in an enterprise account, which results in the  consolidation of authorized users from all service instances in your enterprise hierarchy, within a region, to one list. By doing so, you can ensure that authorized users' email are counted and billed for only once within your enterprise and region.

The consolidated billing feature is available with the {{site.data.keyword.contdelivery_short}} Professional plan only. Consolidation occurs only within the region containing the {{site.data.keyword.contdelivery_short}} service instance that has the consolidated billing feature enabled.
{: restriction}

### Enabling consolidated billing
{: #consolidated_billing_enable}

To enable consolidated billing, you must have an instance of {{site.data.keyword.contdelivery_short}} with the Professional plan in an enterprise account, and you must have access to the instance with the Editor or Administrator role.
{: requirement}

To enable consolidated billing, complete the following steps:

1. In the {{site.data.keyword.cloud_notm}} console, select the enterprise account for which you want to consolidate billing from the account drop-down menu in the console menu bar.
1. Click the **Navigation Menu** ![Navigation Menu icon](../icons/icon_hamburger.svg "Menu") > **Resource list**.
1. Enter `Continuous Delivery` to filter the list to your existing instances.
1. Click the name of the instance to which you want to consolidate billing.
1. Click **Manage** > **Consolidated billing**.
1. Click **On** in the Enable consolidated billing section.
1. Review the list of email addresses to ensure it is complete and correct in the Consolidated authorized users section.

Consolidated billing details are available only in {{site.data.keyword.contdelivery_short}} service instances with the Professional plan located in the enterprise account (the top most account in the enterprise hierarchy).
{: tip}

If you change the plan of a {{site.data.keyword.contdelivery_short}} instance that has consolidated billing enabled from Professional to another plan, consolidated billing is disabled automatically. To re-enable consolidated billing, you must first change the plan back to Professional.
{: note}

### Disabling consolidated billing
{: #consolidated_billing_disable}

1. Follow steps 1 through 7 in the previous section.
1. Click **Off** in the Enable consolidated billing section.

### How does consolidated billing work?
{: #consolidated_billing_understanding}

By default, a count of authorized users is reported for each {{site.data.keyword.contdelivery_short}} instance. When consolidated billing is enabled on an instance in the enterprise account, the number of authorized users is reported by that instance on behalf of all instances in the same region and enterprise hierarchy, including those in all child accounts and any other instances in other resource groups in the enterprise account.

A list of authorized users from all instances in the region and account hierarchy is compiled. In addition, duplicate email addressed are removed, and a count of the resulting consolidated list of authorized user email addresses is reported at the enterprise account level.

To review the consolidated list of authorized user email addresses:

1. From your resource list, enter `Continuous Delivery` to filter the list to your instances.
1. Click the name of the instance in which consolidated billing is enabled.
1. Click **Manage** > **Consolidated billing**.
1. Review the list of email addresses in the Consolidated authorized users section. The list read-only, because it is generated from the authorized users lists of all service instances in the enterprise hierarchy.

When consolidated billing is enabled for a service instance, the **Manage** > **Authorized users** tabs for all other  instances in the enterprise hierarchy include details to explain that consolidated billing applies to those instances.
{: tip}

### Limitations of consolidated billing
{: #consolidated_billing_limitations}

* An enterprise account hierarchy is required. You can't enable consolidated billing across resource groups in a stand-alone account.
* The Professional plan is required.
   * You can't enable consolidated billing for a {{site.data.keyword.contdelivery_short}} instance with any other plan.
   * Authorized users are consolidated only from {{site.data.keyword.contdelivery_short}} instances with the Professional plan. In other words, instances with Lite plans do not participate in consolidated billing.
* You can enable consolidated billing only for a service instance in the enterprise account. And, you can enable it for at most one instance in the enterprise account.
* Consolidated billing applies to authorized users only. It does not affect how pipeline runs are reported.
* Consolidated billing is confined to a single given region. Usage cannot be consolidated from one region to another.
* Even though you might enable consolidated billing for a specific instance, zero authorized users are reported for all other Professional plan instances of the service in the enterprise hierarchy, even though the authorized users of those instances are still listed.

When you delete an instance in an enterprise account in which consolidated billing is enabled, billing for that instance stops. Other instances of the service in the enterprise and region resume normal billing. Consolidated billing is not automatically reactivated when a deleted service instance is restored during reclamation. To re-enable consolidated billing for a restored instance, go to **Manage** > **Consolidated billing** from your restored {{site.data.keyword.contdelivery_short}} instance tab.
{: tip}

## Managing authorized users
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} pricing plans are defined and priced based on the number of authorized users for an instance. Authorized users are added automatically to an instance in response to usage of the instance.

You can review and manage the list of authorized users from the **Manage** > **Consolidated billing** tab for each instance.

If consolidated billing is enabled, you can also review the list of authorized users from the Consolidated billing tab for each instance in an enterprise account.

If your toolchain integrates {{site.data.keyword.gitrepos}} projects in the `open-toolchain` group that is provided by {{site.data.keyword.IBM_notm}}, for example `us-south.git.cloud.ibm.com/open-toolchain`, members of these projects are not counted as authorized users of your toolchains.
{: exception}

The Lite plan is subject to limitations. For more information, see the [service pricing details](https://cloud.ibm.com/catalog/services/continuous-delivery){: external}.
{: tip}

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your instances, see [{{site.data.keyword.atracker_full_notm}} events](/docs/ContinuousDelivery?topic=ContinuousDelivery-at_events).

### How are users accounted for when {{site.data.keyword.contdelivery_short}} instances are in resource groups?
{: #count_users_rg}

Users are counted and managed by using the list of authorized users that belongs to each {{site.data.keyword.contdelivery_short}} instance. Users are automatically added to this list when they meet any of the following criteria:

* View, edit, or run (either directly in the user interface or indirectly by committing to a repo) a delivery pipeline.
* Interact with {{site.data.keyword.DRA_short}}.
* Have Developer (or greater) access to a repo in {{site.data.keyword.gitrepos}} that allows them to commit and push changes to that repo. Users of Git Project Access Tokens with the Developer (or greater) role are counted as authorized users. These users appear in the list of authorized users as `bot` users.

Users with the Guest or Reporter roles are not automatically added to the authorized users list. To prevent users from accessing toolchains and automatically being added to the authorized user list for a {{site.data.keyword.contdelivery_short}} service instance, complete the following actions:

* Remove the user's identity and access management (IAM) access to the toolchain.
* Remove Developer and higher access from all {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group and region by removing their repo access or downgrading their role to Guest or Reporter.

The specific activities that are used to automatically count users, and the method for counting those users, might change over time. However, the process for counting users will continue to comply with the terms of {{site.data.keyword.contdelivery_short}} plans. You can also manually add users to the list of authorized users at any time.
{: important}

For more information about using IAM to manage access to toolchains in a resource group or the toolchain itself, see [Managing user access to toolchains with Identity and Access Management](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security). For more information about managing access to a {{site.data.keyword.gitrepos}} repo, see [Project's members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){: external}.

The method that you use to organize toolchains in resource groups directly impacts user access and billing. By default, when a user uses toolchains in multiple regions or resource groups, they are accounted and billed for each {{site.data.keyword.contdelivery_short}} instance within each unique pairing of region and resource group. If you're using the Professional plan in an enterprise account, you might be able to reduce the total count of authorized users billed within the enterprise by enabling consolidated billing as previously described.
{: tip}

Complete the following steps to manage the list of authorized users of {{site.data.keyword.contdelivery_short}} instances:  on the **Manage** tab from the {{site.data.keyword.contdelivery_short}} instance.

1. From your resource list, enter `Continuous Delivery` to filter the list to your instances.
1. Click the name of an instance to navigate to the instance details.
   * Click **Manage** > **Authorized users** to view, add, or remove users from the list of authorized users as needed.
   * If you enabled consolidated billing, click **Manage** > **Consolidated billing** to view the consolidated list of authorized users.

    Users are automatically added or re-added when they use the {{site.data.keyword.contdelivery_short}} instance.
    {: tip}

When a user logs in to their {{site.data.keyword.cloud_notm}} account with an associated email address and selects a trusted profile, it is considered an authorized user. When a trusted profile is applied to an identity without an email address, such as a service id, the trusted profile is not classified or counted as an authorized user.
{: note}

## Viewing billing and usage details
{: #view_billing_usage}

You can view billing and usage details for the {{site.data.keyword.contdelivery_short}} instances in your account, plus the number of users and pipeline executions that are reported against each instance in an {{site.data.keyword.cloud_notm}} public environment.

1. From the console menu bar, click **Manage** > **Billing and usage**, and then click **Usage**.
1. From the list of services, click **View plans** for the {{site.data.keyword.contdelivery_short}} instance.
1. Click **View details** to view specific plan details for the instance.
1. Click **View instance details** view usage information for the instance.

The AUTHORIZED_USERS_PER_MONTH metric is calculated based on a monthly average of users that is counted daily. If consolidated billing is enabled, the instance in the enabled account reports a consolidated `AUTHORIZED_USERS_PER_MONTH` metric. All other instances in the enterprise hierarchy report zero.
{: tip}

### What happens when you exceed the limits of your service plan?
{: #exceed_limits}

The Lite service plan includes certain limitations, such as limitations on the number of authorized users of the service and on the number of Classic Delivery Pipeline jobs or Tekton steps that can run per month. If any of the plan limitations are exceeded in a billing period, the service is suspended. For example, Classic Delivery Pipeline jobs and Tekton pipeline steps do not run for the remainder of the billing period. For more information about the plan, see the [{{site.data.keyword.contdelivery_short}} details in the catalog](https://cloud.ibm.com/catalog/services/continuous-delivery) {: external}.

You avoid the limitations of the Lite service plan and reactivate your instance by upgrading to the Professional plan as described in the following sections.

### Upgrading your service plan in the UI
{: #change_service_plan}
{: ui}

1. From your resource list, click the {{site.data.keyword.contdelivery_short}} instance with the Lite service plan to upgrade.
1. Click **Plan** on the instance dashboard.
1. In the Change pricing plan section, select **Professional** , and click **Save**.

After you upgrade the plan, you must restage your app:

1. Go to your resource list and locate the app that the service is bound to.
1. Open the **Actions** menu, and select **Restart App**.

### Upgrading your service plan in the CLI
{: #change_plan_cli}
{: cli}

1. Check whether the service is enabled with the resource controller.

   ```text
   ibmcloud catalog service continuous-delivery
   ```
   {: codeblock}

   If the service is enabled with the resource controller, it lists `RC Compatible true`. Make note of the ID of the plan that you want to upgrade to.

   ```text
   ID                 59b735ee-5938-4ebd-a6b2-541aef2d1f68
   Name               continuous-delivery
   Kind               service
   Provider           IBM
   Tags               dev_ops, eu_access, gc_migrate, ibm_created, lite, rc_compatible
   Active             true
   Description        Support DevOps best practices by using Git, issue tracking, and CI/CD pipelines in the Cloud.
   Bindable           false
   Original Name      continuous-delivery
   RC Compatible      true
   RC Provisionable   true
   IAM Compatible     true
   Children           Name                      Kind         ID
                      lite                      plan         a35fb0e9-4fc2-400e-8161-49078e5af632
                      professional              plan         9ca4dc64-bc7b-4aba-9c1c-8bbf30ff127e
   ```

1. Upgrade the plan for your instance by using the [`ibmcloud resource service-instance-update` command](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_update).

   ```text
   ibmcloud resource service-instance-update <service_instance_name>
   --service-plan-id <plan_id>
   ```
   {: codeblock}

## Delivery pipeline usage
{: #pipeline_usage}

Review the following limitations for delivery pipelines included in a Lite service plan:

* The 500-step and job run limit includes both pipeline steps for Tekton pipelines and pipeline job runs for Classic pipelines. If your pipeline has multiple steps within a single run, such as with the DevSecOps pipelines, you might reach this limit quickly.
* Delivery pipeline failures, excluding skipped step runs and Classic job runs, are counted as part of the 500 Tekton step run limit per month. This 500-step run limit also applies to Classic job runs for Classic pipelines.
* All of your toolchains, and the pipelines within those toolchains, in a single resource group contribute to the same limit of 500 Tekton step runs per month. The same limitation is used, because pipeline step runs and job runs are counted at the resource group level for a specific {{site.data.keyword.contdelivery_short}} instance.

A five-day grace period is offered only once for the first time that you reach the 500-step run limit.
{: important}

The retention period for pipelines varies based on the pipeline type and the plan that is selected for the {{site.data.keyword.contdelivery_short}} instance.

* Classic pipelines retain a maximum of 10 stage runs on either plan.
* Tekton pipelines under the Professional plan retain PipelineRuns and their logs for one year.
* Tekton pipelines under the Lite plan retain PipelineRuns and their logs for 30 days.

The acceptable usage behaviors include, but are not limited to, the following behaviors:

* The compilation and assembly of artifacts for supported programming languages.
* The automated deployment of application artifacts, configurations, and supporting resources or services.
* Testing, validation, and other development event-generated behavior that is triggered as the result of a development process.

The usage behaviors that are not permitted include, but are not limited to, the following behaviors:

* The use of pipeline jobs or workers for general compute behaviors, such as Bitcoin mining, distributed denial-of-service attacks, and malicious or offensive behavior to other clients or users within the {{site.data.keyword.cloud_notm}} platform or general internet users.
* The use in the normal development process for sites or services that promote hate speech, or other activities that violate the [{{site.data.keyword.IBM_notm}} Business Conduct Guidelines](https://www.ibm.com/investor/att/pdf/IBM_Business_Conduct_Guidelines.pdf){: external}.
* The use of event-generated behavior for malicious intrusion or attacks against {{site.data.keyword.cloud_notm}} or other sites.

Users who violate the acceptable usage behaviors of the {{site.data.keyword.contdelivery_short}} services or the {{site.data.keyword.IBM_notm}} Business Conduct Guidelines can be disabled at the discretion of {{site.data.keyword.IBM_notm}} and without notice. Some services can be restored if users correct their usage behaviors after they are notified of the offensive action. Otherwise, accounts can be suspended or terminated.
{: important}

## Git repos and issue tracking limitations
{: #git_limitations}

{{site.data.keyword.gitrepos}} is built on GitLab Community Edition and hosted on {{site.data.keyword.cloud_notm}}, however, a few GitLab options are not available:

* Because {{site.data.keyword.deliverypipeline}} provides continuous integration and continuous delivery for {{site.data.keyword.cloud_notm}}, the continuous integration features in GitLab are not supported.
* GitLab admin functions are not available because they are managed by {{site.data.keyword.IBM_notm}}.
* {{site.data.keyword.gitrepos}} might not be fully accessible.

## Git repos and issue tracking user information and content
{: #git_projects}

Three types of {{site.data.keyword.gitrepos}} projects are available:

* Public projects are visible to all site visitors. The content in a public project is visible to everyone who accesses {{site.data.keyword.contdelivery_short}} even if they are not invited to the project.
* Private projects are visible to select users only. For more information about granting users access to a project, see [Project members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){: external}.
* Internal projects are visible to all logged-in users. Any user who has an {{site.data.keyword.cloud_notm}} account can view these projects.

For more information about the project settings, see [Change project visibility](https://us-south.git.cloud.ibm.com/help/user/public_access.md#change-project-visibility){: external}.

When you use {{site.data.keyword.gitrepos}}, the content that you contribute to a project is licensed under any terms that are specified in that project. When you create a project, include a file that describes the license that applies to the content. When you contribute to a project, your name and the email address that is associated with your commits might be visible to the public. The email address that is associated with your {{site.data.keyword.cloud_notm}} account is used when you create commits through the {{site.data.keyword.gitrepos}} web interface.

## Linking an instance to a Git Project
{: #git_projects_cd_instance_linking_validating}

 Git projects must be linked to a {{site.data.keyword.contdelivery_short}} instance that uses a toolchain, because Git Repos and Issue Tracking are a component of the service. Adding your project to a toolchain makes it easier to use other tools, such as {{site.data.keyword.contdelivery_short}} Pipelines or DevOps Insights. As a result, it streamlines your development workflows and improves your code quality.

You can use the console or an API to link your instance and toolchain instance to a Git project.

### Linking {{site.data.keyword.contdelivery_short}} and toolchain instances in the UI
{: #git_projects_cd_instance_linking_validating-ui}
{: ui}

#### Linking a new project
{: #git_projects_cd_instance_linking_validating-ui-new}

You're required to use the UI to link {{site.data.keyword.contdelivery_short}} and toolchain instances when you create a new project.

#### Linking an existing project
{: #git_projects_cd_instance_linking_validating-ui-exist}

1. Go to **Projects** > **General** > **Settings**.
1. Select the project that you want to add instances to.
1. Go to **{{site.data.keyword.contdelivery_short}}** > **Expand** to update or add a {{site.data.keyword.contdelivery_short}} and toolchain instance.


### Link {{site.data.keyword.contdelivery_short}} and toolchain instances by using the API
{: #git_projects_cd_instance_linking_validating-api}
{: api}

You can link {{site.data.keyword.contdelivery_short}} and toolchain instances when you're using the API to create a new project.

* Use an optional header `IBM-CLOUD-API-KEY` to add {{site.data.keyword.contdelivery_short}} and toolchains as you create a project. Generate the key value for your API key from the [console login page](https://cloud.ibm.com/login?redirect=%2Fiam%2Fapikeys).

* Add request parameters `toolchain_ID` and `cd_instance` to link your Git project to a specific {{site.data.keyword.contdelivery_short}} and toolchain instance.

   *  The `toolchain_id` parameter supersedes the `cd_instance` parameter. If both are provided, the toolchain ID is used. However, if only the `cd_instance` parameter is given, a default toolchain is automatically created for the specified CD instance.

      To successfully use these request parameters, you must use the `IBM-CLOUD-API-KEY` header.
      {: note}


Complete the following steps to find the IDs of your {{site.data.keyword.contdelivery_short}} and toolchain instances:

   1. In the console, click the **Navigation Menu** ![Navigation Menu icon](../icons/icon_hamburger.svg "Menu") > **Resource list**.
   1. From your list of resources, click the required toolchain or {{site.data.keyword.contdelivery_short}} instance.
   1. Click **Details** to view and copy the GUID and CRN details.

      For `toolchain_ID` parameter, use the toolchain's GUID. For `cd_instance` parameter, use either GUID or CRN as its value.
      {: note}
