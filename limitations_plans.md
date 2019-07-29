---

copyright:
  years: 2016, 2019
lastupdated: "2019-07-29"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# Plan limitations and usage
{: #limitations_usage}

The use of {{site.data.keyword.contdelivery_full}} is limited to the building, deploying, testing, and ongoing operations of applications on the {{site.data.keyword.Bluemix_notm}} platform or other compatible platform-as-a-service or infrastructure-as-a-service offerings.

## Scope of a service instance
{: #service_scope}

You must have a {{site.data.keyword.contdelivery_short}} [service instance](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} to create and use DevOps toolchains. A service instance might belong to either an {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) [resource group](/docs/services/resources?topic=resources-rgs) or to an {{site.data.keyword.Bluemix_notm}} organization (org).

You can create *new* instances of the {{site.data.keyword.contdelivery_short}} service only in resource groups. If you are missing a {{site.data.keyword.contdelivery_short}} service for an org that contains toolchains, you can either create the toolchains again in a resource group or contact [IBM Support](https://cloud.ibm.com/unifiedsupport){:external} for help. The migration of toolchains from orgs to resource groups is not currently supported.

You can have one Lite service only per account. It is recommended that you use the Professional plan if you want to work with toolchains in multiple orgs or resource groups, or within multiple regions.
{: tip}


## Authorized users
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [service plans](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} are defined and priced based on the number of authorized users for a service instance. Individual contributors, including the following examples, are counted as authorized users:

 * Users who interact with issues, issues boards, source code, or other artifacts in a {{site.data.keyword.gitrepos}} repository (repo).
 * Users who manipulate, trigger (either directly in the user interface or indirectly by committing to a repo), or view the status of a delivery pipeline.
 * Users who interact with the Eclipse Orion {{site.data.keyword.webide}}.
 
The Lite plan is subject to limits. For more information about the Lite plan and the Professional plan, see the [service catalog](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}
 
### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in resource groups?

The specific activities that are used to automatically count users, and the method for counting those users might change over time. However, the process for counting users will continue to comply with the terms of {{site.data.keyword.contdelivery_short}} plans. You can also manually add users to the list of authorized users, at any time.
{: important}

Authorized users are counted and managed for each service instance by using the list of authorized users for billing and Lite plan limits. {{site.data.keyword.contdelivery_short}} service users are automatically added to this list when they complete any of the following activities:
 
 * View, edit, or run a delivery pipeline.
 * Trigger a delivery pipeline to run by way of a Git push, merge, or commit to the branch that is configured as an input trigger.
 * Use the Eclipse Orion {{site.data.keyword.webide}}.

When a delivery pipeline is triggered by a change to an IBM Git repo, all users who have Developer or greater access to the repo are added to the list of authorized users.
{: tip}

You can prevent users from accessing toolchains and automatically being added to the authorized user list for a {{site.data.keyword.contdelivery_short}} service instance by using IAM to remove access to the toolchain. You can also remove Developer access to any Git repos that are integrated with the toolchain. For more information about using IAM to manage access to toolchains in a resource group or the toolchain itself, see [Managing user access to {{site.data.keyword.contdelivery_short}} with Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security). For more information about managing access to an IBM Git repo, see [Project's members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.

The method that you use to organize toolchains within resource groups directly impacts user access and billing. When a user uses toolchains in multiple resource groups, they are counted and billed for each service in those resource groups.
{: tip}

You can manage the list of authorized users on the **Manage** tab within the  {{site.data.keyword.contdelivery_short}} service instance.

1. Go to the [Resource List](https://cloud.ibm.com/resources){:external} for your {{site.data.keyword.Bluemix_notm}} account.
2. In the **Name** column, in the filter text box, type **Continuous Delivery** to show your existing services.
3. For each service, click the hyperlink in the **Name** column.
4. In the **Manage** tab, you can view, add, or remove users from the list of Authorized Users, as needed.

Users are automatically added or added again when they use the {{site.data.keyword.contdelivery_short}} service. 
{: tip}

### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in orgs?

Authorized users are counted by using the list of users in the {{site.data.keyword.Bluemix_notm}} org that contains the {{site.data.keyword.contdelivery_short}} service. For more information about orgs and spaces, see [Creating organizations and spaces](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

To view the list of users in your org in an {{site.data.keyword.Bluemix_notm}} Public environment, from the menu bar, click **Manage > Account**. Then, click **Cloud Foundry orgs**.

### How can you view billing and usage information?

You can view all of the instances of the {{site.data.keyword.contdelivery_short}} service in your account and the number of users and pipeline executions that are reported against each instance in an {{site.data.keyword.Bluemix_notm}} Public environment.

1. From the menu bar, click **Manage > Billing and usage**.
2. Click **Usage**.
3. In the **Services** section, click **View plans** for the {{site.data.keyword.contdelivery_short}} service.
4. Click **View details** for the plan that you want to view information about.
5. Click **View instance details** for the instance of {{site.data.keyword.contdelivery_short}} that you want to view usage information for.

The `AUTHORIZED_USERS_PER_MONTH` metric is calculated based on a monthly average of users that is counted daily. 
{: tip}

### What happens when you exceed the limits of your service plan?

The Lite service plan has other limitations, such as the number of Delivery Pipeline jobs that can run or the storage consumption. For more information about the plan description, see the [service catalog](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. If any of the plan limitations are exceeded in a billing period, the service suspends. For example, Delivery Pipeline jobs do not run for the remainder of the billing period.

## Delivery Pipeline usage
{: #pipeline_usage}

The acceptable usage behaviors include, but are not limited to, these behaviors:

* The compilation and assembly of artifacts for supported programming languages.
* The automated deployment of application artifacts, configurations, and supporting resources or services.
* Testing, validation, and other development event-generated behavior that is triggered as the result of a development process.

The usage behaviors that are not permitted include, but are not limited to, these behaviors:

* The use of pipeline jobs or workers for general compute behaviors, such as Bitcoin mining, distributed denial-of-service attacks, and malicious or offensive behavior to other clients or users within the {{site.data.keyword.Bluemix_notm}} platform or general internet users.
* The use in the normal development process for sites or services that promote hate speech, or other activities that violate the IBM Business Conduct Guidelines.
* The use of event-generated behavior for malicious intrusion or attacks against {{site.data.keyword.Bluemix_notm}} or other sites.

At the discretion of IBM, users who violate the acceptable usage behaviors of the {{site.data.keyword.contdelivery_short}} services or the [IBM Business Conduct Guidelines](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} can be disabled without notice. At the discretion of IBM, some services can be restored if users correct their usage behaviors after they are notified of the offensive action. Otherwise, accounts can be suspended or terminated.

## Git Repos and Issue Tracking limitations
{: #git_limitations}

{{site.data.keyword.gitrepos}} is built on GitLab Community Edition and hosted by IBM on {{site.data.keyword.Bluemix_notm}}, however, a few GitLab options are not available:

 * Because {{site.data.keyword.deliverypipeline}} provides continuous integration and continuous delivery for {{site.data.keyword.Bluemix_notm}}, the continuous integration features in GitLab are not supported.
 * GitLab admin functions are not available because they are managed by IBM.
 * {{site.data.keyword.gitrepos}} might not be fully accessible.

## Git Repos and Issue Tracking user information and content
{: #git_projects}

Three types of {{site.data.keyword.gitrepos}} projects are available:

  1. Public projects are visible to all site visitors. The content in a public project is visible to everyone who accesses {{site.data.keyword.contdelivery_short}}, even if they are not invited to the project.
  2. Private projects are visible to select users only. For more information about granting users access to a project, see [Project users](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. Internal projects are visible to all logged-in users. Any user who has an {{site.data.keyword.Bluemix_notm}} account can view these projects.

You can modify the project type in the project's settings. For more information about the project settings, see [How to change project visibility](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

When you use {{site.data.keyword.gitrepos}}, the content that you contribute to a project is licensed under any terms that are specified in that project. When you create a project, include a file that describes the license that applies to the content. When you contribute to a project, your name and the email address that is associated with your commits might be visible to the public. The email address that is associated with your {{site.data.keyword.Bluemix_notm}} account is used when you create commits through the {{site.data.keyword.gitrepos}} web interface.
