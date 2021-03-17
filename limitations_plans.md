---

copyright:
  years: 2016, 2020
lastupdated: "2021-03-17"

keywords: users of a service instance, authorized users, pipeline usage, Git Repos and Issue Tracking limitations

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}


# Plan limitations and usage
{: #limitations_usage}
{: help} 
{: support}

The use of {{site.data.keyword.contdelivery_full}} is limited to the building, deploying, testing, and ongoing operations of applications on the {{site.data.keyword.cloud_notm}} platform or other compatible platform-as-a-service or infrastructure-as-a-service offerings.

## Scope of a service instance
{: #service_scope}

You must have a {{site.data.keyword.contdelivery_short}} [service instance](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} to create and use DevOps toolchains that include the {{site.data.keyword.deliverypipeline}}, {{site.data.keyword.gitrepos}}, {{site.data.keyword.DRA_short}}, and Eclipse Orion {{site.data.keyword.webide}} tool integrations. A service instance might belong to either a [resource group](/docs/services/account?topic=account-rgs) or to an {{site.data.keyword.Bluemix_notm}} organization (org). The {{site.data.keyword.contdelivery_short}} service instance in a specific region and resource group or org meters and governs your usage of all of the toolchains in the same region and resource group or org.

You can create *new* instances of the {{site.data.keyword.contdelivery_short}} service only in resource groups. If you are missing a {{site.data.keyword.contdelivery_short}} service for an org that contains toolchains, you can either create the toolchains again in a resource group or contact [IBM Support](https://cloud.ibm.com/unifiedsupport){:external} for help. The migration of toolchains from orgs to resource groups is not currently supported.

You can have only one Lite service per account. It is recommended that you use the Professional plan if you want to work with toolchains in multiple orgs or resource groups, or within multiple regions.
{: tip}

## Authorized users
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [service plans](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} are defined and priced based on the number of authorized users for a service instance. Individual contributors, including the following examples, are counted as authorized users:

 * Users who interact with issues, issues boards, source code, or other artifacts in a {{site.data.keyword.gitrepos}} repository (repo).
 * Users who manipulate, trigger (either directly in the user interface or indirectly by committing to a repo), or view the status of a delivery pipeline.
 * Users who interact with the Eclipse Orion {{site.data.keyword.webide}}.
 * Users who interact with {{site.data.keyword.DRA_short}}.
 
The Lite plan is subject to limits. For more information about the Lite plan and the Professional plan, see the [service catalog](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} instances, see [{{site.data.keyword.at_full_notm}} events](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events).
 
### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in resource groups?

Users are counted and managed by using the list of authorized users that belongs to each  {{site.data.keyword.contdelivery_short}} service instance. Users are automatically added to this list when they meet any of the following criteria:

 * View, edit, or run a delivery pipeline.
 * Use the Eclipse Orion {{site.data.keyword.webide}}.
 * Have Developer (or greater) access to a repo in {{site.data.keyword.gitrepos}} that allows them to commit and push changes to that repo. Users of Git repos with the Guest or Reporter roles with read-only access are not counted as authorized users. 

Users with the Guest or Reporter roles are not automatically added to the authorized users list. To prevent users from accessing toolchains and automatically being added to the authorized user list for a {{site.data.keyword.contdelivery_short}} service instance, complete the following actions:

 * Remove the user's access to the toolchain from IAM.
 * Remove Developer access from all {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group by removing their repo access or downgrading their role to Guest or Reporter.
 
The specific activities that are used to automatically count users, and the method for counting those users might change over time. However, the process for counting users will continue to comply with the terms of {{site.data.keyword.contdelivery_short}} plans. You can also manually add users to the list of authorized users, at any time.
{: important}

For more information about using IAM to manage access to toolchains in a resource group or the toolchain itself, see [Managing user access to toolchains with Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security). For more information about managing access to a {{site.data.keyword.gitrepos}} repo, see [Project's members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.

The method that you use to organize toolchains within resource groups directly impacts user access and billing. When a user uses toolchains in multiple regions or resource groups, they are counted and billed for each {{site.data.keyword.contdelivery_short}} service instance within each unique pairing of region and resource group.
{: tip}

You can manage the list of authorized users on the **Manage** tab within the {{site.data.keyword.contdelivery_short}} service instance.

1. Go to the [Resource list](https://cloud.ibm.com/resources){:external} for your {{site.data.keyword.cloud_notm}} account.
2. In the **Name** column, in the filter text box, type `Continuous Delivery` to view your existing services.
3. For each service, click the hyperlink in the **Name** column.
4. In the **Manage** tab, you can view, add, or remove users from the list of Authorized Users, as needed.

Users are automatically added or added again when they use the {{site.data.keyword.contdelivery_short}} service. 
{: tip}

### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in orgs?

Authorized users are counted by using the list of users in the {{site.data.keyword.cloud_notm}} Foundry org that contains the {{site.data.keyword.contdelivery_short}} service. For more information about orgs and spaces, see [Creating organizations and spaces](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

To view the list of users in your org in an {{site.data.keyword.cloud_notm}} Public environment, from the {{site.data.keyword.cloud_notm}} console, go to **Manage > Account**. Then, click **Cloud Foundry orgs**.

### How can you view billing and usage information?

You can view all of the instances of the {{site.data.keyword.contdelivery_short}} service in your account and the number of users and pipeline executions that are reported against each instance in an {{site.data.keyword.cloud_notm}} Public environment.

1. From the menu bar, click **Manage > Billing and usage**.
2. Click **Usage**.
3. In the **Services** section, click **View plans** for the {{site.data.keyword.contdelivery_short}} service.
4. Click **View details** for the plan that you want to view information about.
5. Click **View instance details** for the instance of {{site.data.keyword.contdelivery_short}} that you want to view usage information for.

The `AUTHORIZED_USERS_PER_MONTH` metric is calculated based on a monthly average of users that is counted daily. 
{: tip}

### What happens when you exceed the limits of your service plan?

The Lite service plan has other limitations, such as the number of Delivery Pipeline jobs that can run or the storage consumption. For more information about the plan description, see the [service catalog](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. If any of the plan limitations are exceeded in a billing period, the service suspends. For example, Delivery Pipeline jobs do not run for the remainder of the billing period.

Upgrading to the Professional plan will remove these limitations and reactivate the service.
{: tip}

### How can you change to a different service plan?
{: ui}

You can upgrade from the {{site.data.keyword.contdelivery_short}} Lite service plan to the Professional plan.

1. From the console, click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) > **Resource list** to view your list of resources.
1. Click the {{site.data.keyword.contdelivery_short}} service that you want to upgrade.
1. Click **Plan** in the {{site.data.keyword.contdelivery_short}} service instance dashboard. 
1. In the **Change pricing plan** section, select **Professional** to upgrade to the {{site.data.keyword.contdelivery_short}} Professional plan, and click **Save**.
1. After you change your plan, you must restage your app. Go to your resource list to find the app that the service is bound to. Click the Menu icon ![Menu icon](../icons/icon_hamburger.svg) **> Resource list**. In the app menu, select **Restart App**.

#### Changing a plan through the CLI
{: cli}

As an alternative to the console, you can change the {{site.data.keyword.contdelivery_short}} service's pricing plan by using the {{site.data.keyword.cloud_notm}} command-line interface (CLI).

1. Check whether the service is enabled with the resource controller.

   ```
   ibmcloud catalog service continuous-delivery
   ```
   {:codeblock}

   If the service is enabled with the resource controller (RC), it lists `RC Compatible true`. Make note of the ID of the plan that you want to change to.

   ```
   ID                 59b735ee-5938-4ebd-a6b2-541aef2d1f68
   Name               continuous-delivery
   Kind               service
   Provider           IBM
   Tags               dev_ops, eu_access, gc_migrate, ibm_created, lite, rc_compatible
   Active             true
   Description        Support DevOps best practices by using Git, issue tracking, CI/CD pipelines, and the Eclipse Orion Web IDE in the Cloud.
   Bindable           false
   Original Name      continuous-delivery
   RC Compatible      true
   RC Provisionable   true
   IAM Compatible     true
   Children           Name                      Kind         ID                                            
                      lite                      plan         a35fb0e9-4fc2-400e-8161-49078e5af632 
                      professional              plan         9ca4dc64-bc7b-4aba-9c1c-8bbf30ff127e
    ```

1. Change the plan for your service instance.

   - If the service is RC-enabled, change your plan by using the [`ibmcloud resource service-instance-update` command](/docs/cli/reference/ibmcloud?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_update).

     ```
     ibmcloud resource service-instance-update <service_instance_name> --service-plan-id <plan_id>
     ```
     {: codeblock}

   - If the service is not RC-enabled and is therefore based on Cloud Foundry, change your plan by using the [`ibmcloud cf update-service` command](/docs/cli?topic=cli-ibmcloud_commands_services#ibmcloud_service_update).

     ```
     ibmcloud cf update-service <service_instance_name> [-p <plan_name>]
     ```
     {:codeblock}

## Delivery Pipeline usage
{: #pipeline_usage}

The acceptable usage behaviors include, but are not limited to, these behaviors:

* The compilation and assembly of artifacts for supported programming languages.
* The automated deployment of application artifacts, configurations, and supporting resources or services.
* Testing, validation, and other development event-generated behavior that is triggered as the result of a development process.

The usage behaviors that are not permitted include, but are not limited to, these behaviors:

* The use of pipeline jobs or workers for general compute behaviors, such as Bitcoin mining, distributed denial-of-service attacks, and malicious or offensive behavior to other clients or users within the {{site.data.keyword.Bluemix_notm}} platform or general internet users.
* The use in the normal development process for sites or services that promote hate speech, or other activities that violate the [IBM Business Conduct Guidelines](https://www.ibm.com/investor/att/pdf/BCG_accessible_2020.pdf){:external}.
* The use of event-generated behavior for malicious intrusion or attacks against {{site.data.keyword.cloud_notm}} or other sites.

At the discretion of IBM, users who violate the acceptable usage behaviors of the {{site.data.keyword.contdelivery_short}} services or the IBM Business Conduct Guidelines can be disabled without notice. At the discretion of IBM, some services can be restored if users correct their usage behaviors after they are notified of the offensive action. Otherwise, accounts can be suspended or terminated.

## Git Repos and Issue Tracking limitations
{: #git_limitations}

{{site.data.keyword.gitrepos}} is built on GitLab Community Edition and hosted by IBM on {{site.data.keyword.Bluemix_notm}}, however, a few GitLab options are not available:

 * Because {{site.data.keyword.deliverypipeline}} provides continuous integration and continuous delivery for {{site.data.keyword.cloud_notm}}, the continuous integration features in GitLab are not supported.
 * GitLab admin functions are not available because they are managed by IBM.
 * {{site.data.keyword.gitrepos}} might not be fully accessible.

## Git Repos and Issue Tracking user information and content
{: #git_projects}

Three types of {{site.data.keyword.gitrepos}} projects are available:

  1. Public projects are visible to all site visitors. The content in a public project is visible to everyone who accesses {{site.data.keyword.contdelivery_short}}, even if they are not invited to the project.
  2. Private projects are visible to select users only. For more information about granting users access to a project, see [Project members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. Internal projects are visible to all logged-in users. Any user who has an {{site.data.keyword.cloud_notm}} account can view these projects.

You can modify the project type in the project's settings. For more information about the project settings, see [How to change project visibility](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

When you use {{site.data.keyword.gitrepos}}, the content that you contribute to a project is licensed under any terms that are specified in that project. When you create a project, include a file that describes the license that applies to the content. When you contribute to a project, your name and the email address that is associated with your commits might be visible to the public. The email address that is associated with your {{site.data.keyword.cloud_notm}} account is used when you create commits through the {{site.data.keyword.gitrepos}} web interface.
