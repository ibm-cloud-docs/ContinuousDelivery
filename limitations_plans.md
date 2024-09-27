---

copyright:
  years: 2016, 2024
lastupdated: "2024-09-24"

keywords: users of a service instance, authorized users, pipeline usage, Git Repos and Issue Tracking limitations, consolidated billing

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Plan limitations and usage
{: #limitations_usage}
{: help}
{: support}

The use of {{site.data.keyword.contdelivery_full}} is limited to the building, deploying, testing, and ongoing operations of applications on the {{site.data.keyword.cloud_notm}} platform or other compatible platform-as-a-service or infrastructure-as-a-service offerings.

## Scope of a service instance
{: #service_scope}

You must have a {{site.data.keyword.contdelivery_short}} [service instance](https://cloud.ibm.com/catalog/services/continuous-delivery){: external} to create and use DevOps toolchains that include the {{site.data.keyword.deliverypipeline}}, {{site.data.keyword.gitrepos}}, and {{site.data.keyword.DRA_short}} tool integrations. A service instance resides in a region and belongs to a [resource group](/docs/account?topic=account-rgs). The {{site.data.keyword.contdelivery_short}} service instance in a specific region and resource group governs and meters your usage of all of the toolchains in the same region and resource group.

## Pricing plans
{: #pricing_plans}



The following table outlines the pricing plans of the {{site.data.keyword.contdelivery_short}} service:

| Plan | Cost | Limits |
|:-----|:-----|:-------|
| **Lite** | Free | The Lite plan offers the full capabilities of {{site.data.keyword.contdelivery_short}} with limits on usage. |
| **Professional** | Paid | The Professional plan offers the full capabilities of {{site.data.keyword.contdelivery_short}} with no limits on usage. |
{: caption="Table 1. Pricing plans" caption-side="bottom"}





You can have at most one Lite service instance per account. It is recommended that you use the Professional plan if you want to work with toolchains in multiple resource groups, or within multiple regions.
{: tip}

For more information about the plans, see [pricing plans](https://cloud.ibm.com/catalog/services/continuous-delivery){: external}.

## Usage metrics
{: #usage_metrics}

{{site.data.keyword.contdelivery_short}} service instances track and report usage metrics within your {{site.data.keyword.cloud_notm}} account. Depending upon the pricing plan of a service instance, the metrics may affect usage cost, usage limits, or both. The following table outlines the usage metrics of the {{site.data.keyword.contdelivery_short}} service:

| Usage | Metric | Summary |
|:------|:-------|:--------|
| Authorized users | `AUTHORIZED_USERS_PER_MONTH` | A count of the average number of authorized users of the service instance within a given month. |
| Pipeline runs | `JOB_EXECUTIONS_PER_MONTH` | A count of the total number of pipeline Tekton step or classic job runs within a given month. |
{: caption="Table 2. Usage metrics" caption-side="bottom"}

## Consolidated billing
{: #consolidated_billing}

By default, {{site.data.keyword.contdelivery_short}} service instances report usage independently of each other. If you have organized your toolchains into multiple resource groups in a standalone {{site.data.keyword.cloud_notm}} account or across several {{site.data.keyword.cloud_notm}} accounts in an [enterprise](/docs/secure-enterprise?topic=secure-enterprise-what-is-enterprise), then users of your toolchains may be reported as authorized users multiple times from corresponding multiple instances of the {{site.data.keyword.contdelivery_short}} service.

For example, a developer on a Git Repos and Issue Tracking project that is integrated into two toolchains in different resource groups will be counted and, under the Professional plan, billed for twice.

You can enable the consolidated billing feature of a {{site.data.keyword.contdelivery_short}} service instance with the Professional plan in an enterprise account to cause the service to consolidate the authorized users from all {{site.data.keyword.contdelivery_short}} service instances in your enterprise hierarchy, within a region, into one list. By using this feature, you can ensure that an authorized user email will only be counted and billed for once within your enterprise and region.

The consolidated billing feature is available with the {{site.data.keyword.contdelivery_short}} Professional plan only. Consolidation occurs only within the region containing the {{site.data.keyword.contdelivery_short}} service instance which has the consolidated billing feature enabled.
{: restriction}

Consolidated billing is disabled by default.
{: tip}

### How do you enable consolidated billing?
{: #consolidated_billing_enable}

To enable consolidated billing, you must have an instance of {{site.data.keyword.contdelivery_short}} with the Professional plan in an enterprise account, and you must have access to the instance with the `Editor` or `Administrator` role.
{: requirement}

To enable consolidated billing:

1. Login to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com).
2. Select the enterprise account within which you want to consolidate billing.
3. Go to the [Resource list](https://cloud.ibm.com/resources){: external}.
4. In the **Product** column, in the filter text box, type `Continuous Delivery` to view your existing services.
5. Locate the {{site.data.keyword.contdelivery_short}} service instance to which you want to consolidate billing.
6. Click on the name of the instance.
7. Click **Manage > Consolidated billing**.
8. In the **Enable consolidated billing** section, click the toggle button **On**.
9. In the **Consolidated authorized users** section, review the list of **Email** addresses to ensure it is complete and correct.

The **Consolidated billing** tab is available only in {{site.data.keyword.contdelivery_short}} service instances with the Professional plan located within the enterprise account (the top most account in the enterprise hierarchy).
{: tip}

If you change the plan of a {{site.data.keyword.contdelivery_short}} service instance that has consolidated billing enabled from Professional to another plan, consolidated billing will be disabled automatically. To re-enable consolidated billing, you must first change the plan back to Professional.
{: note}

### How do you disable consolidated billing?
{: #consolidated_billing_disable}

1. Follow steps 1 to 7 in [How do you enable consolidated billing?](#consolidated_billing_enable).
2. In the **Enable consolidated billing** section, click the toggle button **Off**.

### How does consolidated billing work?
{: #consolidated_billing_understanding}

By default, each {{site.data.keyword.contdelivery_short}} service instance is responsible for reporting its own count of authorized users. When consolidated billing is enabled on a service instance in the enterprise account, that instance takes over responsibility for reporting the number of authorized users on behalf of all service instances in the same region and in the enterprise hierarchy, including those in all child accounts, and including any other instances in other resource groups in the enterprise account. The instance gathers up the lists of authorized users from all instances in the region and in the hierarchy, eliminates duplicate email addresses, and reports a count of the resulting consolidated list of authorized user email addresses to the enterprise account.

To review the consolidated list of authorized user email addresses:

1. Login to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com).
2. Select the enterprise account.
3. Go to the [Resource list](https://cloud.ibm.com/resources){: external}.
4. In the **Product** column, in the filter text box, type `Continuous Delivery` to view your existing services.
5. Locate the {{site.data.keyword.contdelivery_short}} service instance that has consolidated billing enabled.
6. Click on the name of the instance.
7. Click **Manage > Consolidated billing**.
8. Review the list of **Email** addresses in the **Consolidated authorized users** section.

The list of consolidated authorized users is read-only, because it is computed from the authorized users lists of all service instances in the enterprise hierarchy.
{: note}

When consolidated billing is enabled on a service instance, the **Manage > Authorized users** tabs on all other service instances in the enterprise hierarchy will inform you that the service instances are participating in consolidated billing.
{: tip}

### Limitations of consolidated billing
{: #consolidated_billing_limitations}

* Consolidated billing requires an enterprise account hierarchy. You cannot enable consolidated billing across resource groups in a standalone account.
* Consolidated billing requires the Professional plan. Consolidated billing cannot be enabled on a {{site.data.keyword.contdelivery_short}} service instance with any other plan. Authorized users are consolidated only from {{site.data.keyword.contdelivery_short}} service instances with the Professional plan. For example, Lite plan {{site.data.keyword.contdelivery_short}} service instances do not participate in consolidated billing.
* Consolidated billing can be enabled only on a service instance in the enterprise account.
* Consolidated billing can be enabled on at most one service instance in the enterprise account.
* Consolidated billing applies to authorized users only. Consolidated billing does not affect how pipeline runs are reported.
* Consolidated billing is confined to a single given region. Usage cannot be consolidated from one region to another.
* While consolidated billing is enabled on a {{site.data.keyword.contdelivery_short}} service instance, all other Professional plan instances of the service in the enterprise hierarchy report zero authorized users, even though they continue to list their authorized users.

If you delete a {{site.data.keyword.contdelivery_short}} service instance in an enterprise account that has consolidated billing enabled, consolidated billing will cease, and all other instances of the service in the enterprise and region will resume normal billing. If you restore the deleted service instance while it is pending reclamation, consolidated billing will not automatically be re-enabled. If desired, you can re-enable consolidated billing from the **Manage > Consolidated billing** tab of the restored {{site.data.keyword.contdelivery_short}} service instance.
{: tip}

## Authorized users
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [pricing plans](https://cloud.ibm.com/catalog/services/continuous-delivery){: external} are defined and priced based on the number of authorized users for a service instance. Authorized users are added automatically to a service instance in response to usage of the service instance. You can review and manage the list of authorized users on the **Manage > Authorized users** tab of a {{site.data.keyword.contdelivery_short}} service instance. If [consolidated billing](#consolidated_billing) is enabled, you can review the consolidated list of authorized users on the **Manage > Consolidated billing** tab of the {{site.data.keyword.contdelivery_short}} service instance in the enterprise account.

If your toolchain integrates {{site.data.keyword.gitrepos}} projects in the `open-toolchain` group that is provided by IBM, such as in `us-south.git.cloud.ibm.com/open-toolchain`, members of these projects are not counted as authorized users of your toolchains.
{: exception}

The Lite plan is subject to limits. For more information about {{site.data.keyword.contdelivery_short}} plans, see the [service catalog](https://cloud.ibm.com/catalog/services/continuous-delivery){: external}.
{: tip}

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} instances, see [{{site.data.keyword.at_full_notm}} events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events).

### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in resource groups?
{: #count_users_rg}

Users are counted and managed by using the list of authorized users that belongs to each {{site.data.keyword.contdelivery_short}} service instance. Users are automatically added to this list when they meet any of the following criteria:

* View, edit, or run (either directly in the user interface or indirectly by committing to a repo) a delivery pipeline.
* Interact with {{site.data.keyword.DRA_short}}.
* Have Developer (or greater) access to a repo in {{site.data.keyword.gitrepos}} that allows them to commit and push changes to that repo. Users of Git Project Access Tokens with the Developer (or greater) role are counted as authorized users. These users appear in the list of authorized users as `bot` users.

Users with only the Guest or Reporter roles are not automatically added to the authorized users list. To prevent users from accessing toolchains and automatically being added to the authorized user list for a {{site.data.keyword.contdelivery_short}} service instance, complete the following actions:

* Remove the user's access to the toolchain from IAM.
* Remove Developer and higher access from all {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group and region by removing their repo access or downgrading their role to Guest or Reporter.

The specific activities that are used to automatically count users, and the method for counting those users might change over time. However, the process for counting users will continue to comply with the terms of {{site.data.keyword.contdelivery_short}} plans. You can also manually add users to the list of authorized users, at any time.
{: important}

For more information about using IAM to manage access to toolchains in a resource group or the toolchain itself, see [Managing user access to toolchains with Identity and Access Management](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security). For more information about managing access to a {{site.data.keyword.gitrepos}} repo, see [Project's members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){: external}.

The method that you use to organize toolchains within resource groups directly impacts user access and billing. By default, when a user uses toolchains in multiple regions or resource groups, they are counted and billed for each {{site.data.keyword.contdelivery_short}} service instance within each unique pairing of region and resource group. If you have an enterprise account and are using the {{site.data.keyword.contdelivery_short}} Professional plan, you may be able to reduce the total count of authorized users billed within the enterprise by [enabling consolidated billing](#consolidated_billing_enable).
{: tip}

You can manage the list of authorized users on the **Manage** tab within the {{site.data.keyword.contdelivery_short}} service instance.

1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
2. In the **Product** column, in the filter text box, type `Continuous Delivery` to view your existing services.
3. For each service, click the hyperlink in the **Name** column.
4. In the **Manage > Authorized users** tab, you can view, add, or remove users from the list of authorized users, as needed.
5. If you have enabled consolidated billing, in the **Manage > Consolidated billing** tab you can view the consolidated list of authorized users.

Users are automatically added or added again when they use the {{site.data.keyword.contdelivery_short}} service.
{: tip}

## Viewing billing and usage information
{: #view_billing_usage}

You can view all of the instances of the {{site.data.keyword.contdelivery_short}} service in your account and the number of users and pipeline executions that are reported against each instance in an {{site.data.keyword.cloud_notm}} Public environment.

1. From the menu bar, click **Manage > Billing and usage**.
2. Click **Usage**.
3. In the **Services** section, click **View plans** for the {{site.data.keyword.contdelivery_short}} service.
4. Click **View details** for the plan that you want to view information about.
5. Click **View instance details** for the instance of {{site.data.keyword.contdelivery_short}} that you want to view usage information for.

The `AUTHORIZED_USERS_PER_MONTH` metric is calculated based on a monthly average of users that is counted daily.
{: tip}

If consolidated billing is enabled, the {{site.data.keyword.contdelivery_short}} service instance in the enterprise account that is enabled will report  the consolidated `AUTHORIZED_USERS_PER_MONTH` metrics. All other service instances in the enterprise hierarchy will report zero.
{: remember}

### What happens when you exceed the limits of your service plan?
{: #exceed_limits}

The Lite service plan has limitations such as on the number of authorized users of the service, and on the number of Classic Delivery Pipeline jobs or Tekton steps that can run per month. For more information about the plan, see the [service catalog](https://cloud.ibm.com/catalog/services/continuous-delivery){: external}. If any of the plan limitations are exceeded in a billing period, the service suspends. For example, Classic Delivery Pipeline jobs and Tekton pipeline steps do not run for the remainder of the billing period.

Upgrading to the Professional plan will remove these limitations and reactivate the service.
{: tip}

### How can you change to a different service plan?
{: #change_service_plan}
{: ui}

You can upgrade from the {{site.data.keyword.contdelivery_short}} Lite service plan to the Professional plan.

1. From the console, click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) > **Resource list** to view your list of resources.
2. Click the {{site.data.keyword.contdelivery_short}} service that you want to upgrade.
3. Click **Plan** in the {{site.data.keyword.contdelivery_short}} service instance dashboard.
4. In the **Change pricing plan** section, select **Professional** to upgrade to the {{site.data.keyword.contdelivery_short}} Professional plan, and click **Save**.
5. After you change your plan, you must restage your app. Go to your resource list to find the app that the service is bound to. Click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) **> Resource list**. In the app menu, select **Restart App**.

### Changing a plan through the CLI
{: #change_plan_cli}
{: cli}

As an alternative to the console, you can change the {{site.data.keyword.contdelivery_short}} service's pricing plan by using the {{site.data.keyword.cloud_notm}} command-line interface (CLI).

1. Check whether the service is enabled with the resource controller.

   ```text
   ibmcloud catalog service continuous-delivery
   ```
   {: codeblock}

   If the service is enabled with the resource controller (RC), it lists `RC Compatible true`. Make note of the ID of the plan that you want to change to.

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

2. Change the plan for your service instance by using the [`ibmcloud resource service-instance-update` command](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_update).

   ```text
   ibmcloud resource service-instance-update <service_instance_name>
   --service-plan-id <plan_id>
   ```
   {: codeblock}

## Delivery Pipeline usage
{: #pipeline_usage}

Delivery pipelines under a {{site.data.keyword.contdelivery_short}} service instance Lite plan have several limitations.

* The 500-step and job run limit includes both pipeline steps for Tekton pipelines and pipeline job runs for Classic pipelines. If your pipeline has many steps within a single run, such as with the DevSecOps pipelines, you might reach this limit quickly.
* Delivery pipeline failures, excluding skipped step runs and Classic job runs, are counted as part of the 500 Tekton step run limit per month. This 500-step run limit also applies to Classic job runs for Classic pipelines.
* All of your toolchains and all of your pipelines within those toolchains that are in the same resource group contribute to the same limit of 500 Tekton step runs per month. The same limit is used because pipeline step runs and job runs are counted at the resource group level for a specific {{site.data.keyword.contdelivery_short}} instance.

A five-day grace period is offered the first time that you reach the 500-step run limit. This grace period is offered only *once*.
{: important}

The retention period for pipelines varies based on the pipeline type and the plan that is selected for the {{site.data.keyword.contdelivery_short}} service instance.

* Classic pipelines retain a maximum of 10 stage runs on either plan.
* Tekton pipelines under the Professional plan retain PipelineRuns and their logs for one year.
* Tekton pipelines under the Lite plan retain PipelineRuns and their logs for 30 days.

The acceptable usage behaviors include, but are not limited to, these behaviors:

* The compilation and assembly of artifacts for supported programming languages.
* The automated deployment of application artifacts, configurations, and supporting resources or services.
* Testing, validation, and other development event-generated behavior that is triggered as the result of a development process.

The usage behaviors that are not permitted include, but are not limited to, these behaviors:

* The use of pipeline jobs or workers for general compute behaviors, such as Bitcoin mining, distributed denial-of-service attacks, and malicious or offensive behavior to other clients or users within the {{site.data.keyword.cloud_notm}} platform or general internet users.
* The use in the normal development process for sites or services that promote hate speech, or other activities that violate the [IBM Business Conduct Guidelines](https://www.ibm.com/investor/att/pdf/IBM_Business_Conduct_Guidelines.pdf){: external}.
* The use of event-generated behavior for malicious intrusion or attacks against {{site.data.keyword.cloud_notm}} or other sites.

At the discretion of IBM, users who violate the acceptable usage behaviors of the {{site.data.keyword.contdelivery_short}} services or the IBM Business Conduct Guidelines can be disabled without notice. At the discretion of IBM, some services can be restored if users correct their usage behaviors after they are notified of the offensive action. Otherwise, accounts can be suspended or terminated.

## Git Repos and Issue Tracking limitations
{: #git_limitations}

{{site.data.keyword.gitrepos}} is built on GitLab Community Edition and hosted by IBM on {{site.data.keyword.cloud_notm}}, however, a few GitLab options are not available:

* Because {{site.data.keyword.deliverypipeline}} provides continuous integration and continuous delivery for {{site.data.keyword.cloud_notm}}, the continuous integration features in GitLab are not supported.
* GitLab admin functions are not available because they are managed by IBM.
* {{site.data.keyword.gitrepos}} might not be fully accessible.

## Git Repos and Issue Tracking user information and content
{: #git_projects}

Three types of {{site.data.keyword.gitrepos}} projects are available:

* Public projects are visible to all site visitors. The content in a public project is visible to everyone who accesses {{site.data.keyword.contdelivery_short}}, even if they are not invited to the project.
* Private projects are visible to select users only. For more information about granting users access to a project, see [Project members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){: external}.
* Internal projects are visible to all logged-in users. Any user who has an {{site.data.keyword.cloud_notm}} account can view these projects.

For more information about the project settings, see [Change project visibility](https://us-south.git.cloud.ibm.com/help/user/public_access.md#change-project-visibility){: external}.

When you use {{site.data.keyword.gitrepos}}, the content that you contribute to a project is licensed under any terms that are specified in that project. When you create a project, include a file that describes the license that applies to the content. When you contribute to a project, your name and the email address that is associated with your commits might be visible to the public. The email address that is associated with your {{site.data.keyword.cloud_notm}} account is used when you create commits through the {{site.data.keyword.gitrepos}} web interface.

## Link a Continuous Delivery service instance to a Git Project
{: #git_projects_cd_instance_linking_validating}

 Git projects must be linked to a Continuous Delivery service instance that uses a toolchain because Git Repos and Issue Tracking are a component of the Continuous Delivery service.  Adding your project to a toolchain makes it easier to use other tools such as Continuous Delivery Pipelines or DevOps Insights. Thus, it streamlines your development workflows and improves your code quality.

To link your Continuous Delivery service instance and toolchain instance to a Git project, you can use the UI or API.

### Link Continuous Delivery and toolchain instances in the UI
{: #git_projects_cd_instance_linking_validating-ui}
{: ui}

#### Linking a new project
{: #git_projects_cd_instance_linking_validating-ui-new}

You must link Continuous Delivery and toolchain instances in the UI when you're creating a new project. It is mandatory to link an existing CD and a toolchain instances in the UI.

#### Linking an existing project
{: #git_projects_cd_instance_linking_validating-ui-new}

1. Go to **Projects** > **General** > **Settings**
1. Select the project that you want to add instances to.
1. Go to **Continuous Delivery** > **Expand** to update or add a Continuous Delivery and toolchain instance.


### Link Continuous Delivery and toolchain instances by using the API
{: #git_projects_cd_instance_linking_validating-api}
{: api}

You can link Continuous Delivery and toolchain instances when you're using the API to create a new project.

* Use an optional header `IBM-CLOUD-API-KEY` to add Continuous Delivery and toolchains while creating a project. Generate the key value for your API key from [here](https://cloud.ibm.com/login?redirect=%2Fiam%2Fapikeys).


* Add request parameters `toolchain_ID` and `cd_instance` to link your Git project to a specific Continuous Delivery and toolchain instance.

   *  The `toolchain_id` parameter supersedes the `cd_instance` parameter. If both are provided, the toolchain ID is used. However, if only the `cd_instance` parameter is given, a default toolchain is automatically created for the specified CD instance.

   *  To successfully use these request parameters, you must use the `IBM-CLOUD-API-KEY` header.
   {: note}


To find your Continuous Delivery and toolchain instance IDs:

   1. Go to [Resources](https://cloud.ibm.com/resources) in [IBM Console](https://cloud.ibm.com).
   1. From your Resources, click the required toolchain or Continuous Delivery instance.
   1. Click **Details** to view and copy the GUID and CRN details.
      For `toolchain_ID` parameter, use the toolchain's GUID. For `cd_instance` parameter, use either GUID or CRN as its value.
      {: note}
