---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-20"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}


# Plan limitations and usage
{: #limitations_usage}

The use of {{site.data.keyword.contdelivery_full}} is limited to the building, deploying, testing, and ongoing operations of applications on the {{site.data.keyword.Bluemix_notm}} platform or other compatible platform-as-a-service or infrastructure-as-a-service offerings.

## Authorized users
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} service plans are defined and priced based on the number of authorized users of a service instance. Anyone who contributes to an effort must be counted as an authorized user, including:

 * Users who interact with issues, issues boards, source code, or other artifacts in a {{site.data.keyword.gitrepos}} repository.
 * Users who manipulate, trigger (either directly in the UI or indirectly by committing to a repo), or view the status of a delivery pipeline.
 * Users who interact with the Eclipse Orion {{site.data.keyword.webide}}.

### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in orgs?

Authorized users are counted by looking at all of the users in the Cloud organization (org) that contains the {{site.data.keyword.contdelivery_short}} service.

To view the list of users in your org in an {{site.data.keyword.Bluemix_notm}} Public environment, from the menu bar, click **Manage > Account**. Then, click **Cloud Foundry orgs**.

To view the list of users in your org in an {{site.data.keyword.Bluemix_notm}} Dedicated environment, from the menu bar, click **Account > Manage Organizations**.

You can also view all of the instances of the {{site.data.keyword.contdelivery_short}} service in your account and the number of users that are reported against each instance in an {{site.data.keyword.Bluemix_notm}} Public environment.

1. From the menu bar, click **Manage > Billing and usage**.
2. Click **Usage**.
3. In the **Services** section, click **View plans** for the {{site.data.keyword.contdelivery_short}} service.
4. Click **View details** for the plan that you want to view information about.
5. Click **View instance details** for the instance of {{site.data.keyword.contdelivery_short}} that you want to view usage information for.

To view all of the instances of the {{site.data.keyword.contdelivery_short}} service in your account and the number of users that are reported against each instance in an {{site.data.keyword.Bluemix_notm}} Dedicated environment:

1. From the menu bar, click **Account > Manage Organizations**.
2. Click **Usage Dashboard**.

### How are users counted for instances of {{site.data.keyword.contdelivery_short}} in resource groups?

Authorized users are counted by looking at the list of users on the Manage tab within the  {{site.data.keyword.contdelivery_short}} service instance.

To view the list of authorized users, open the service instance dashboard and click the Manage tab.

You can also view all of the instances of the {{site.data.keyword.contdelivery_short}} service in your account and the number of users that are reported against each instance.

1. From the menu bar, click **Manage > Billing and usage**.
2. Click **Usage**.
3. In the **Services** section, click **View plans** for the {{site.data.keyword.contdelivery_short}} service.
4. Click **View details** for the plan that you want to view information about.
5. Click **View instance details** for the resource group that you want to view usage information for.

### What happens when you exceed the limits of your service plan?

Some service plans might have other limitations, such as the number of Delivery Pipeline jobs that can be run or the storage consumption. For more information, see the plan description in the catalog. If any of the plan limitations are exceeded in a billing period, the service might suspend. For example, Delivery Pipeline jobs might not run for the remainder of the billing period.

## Delivery Pipeline usage
{: #pipeline_usage}

The acceptable usage behaviors include, but are not limited to, these behaviors:

* The compilation and assembly of artifacts for supported programming languages
* The automated deployment of application artifacts, configurations, and supporting resources or services
* Testing, validation, and other development event-generated behavior that is triggered as the result of a development process

The usage behaviors that are not permitted include, but are not limited to, these behaviors:

* The use of pipeline jobs or workers for general compute behaviors, such as Bitcoin mining, distributed denial-of-service attacks, and malicious or offensive behavior to other clients or users within the IBM Cloud platform or general internet users
* The use in the normal development process for sites or services that promote hate speech, or other activities that violate the IBM Business Conduct Guidelines
* The use of event-generated behavior for malicious intrusion or attacks against {{site.data.keyword.Bluemix_notm}} or other sites

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
  2. Private projects are visible to only select users. For more information about granting users access to a project, see [Project users](https://us-south.git.cloud.ibm.com/help/workflow/add-user/add-user.md){:external}.
  3. Internal projects are visible to all logged-in users. Any user who has a {{site.data.keyword.Bluemix_notm}} account can view these projects.

You can modify the project type in the project's settings. For more information, see [How to change project visibility](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

When you use {{site.data.keyword.gitrepos}}, the content that you contribute to a project is licensed under any terms that are specified in that project. When you create a project, include a file that describes the license that applies to the content. When you contribute to a project, your name and the email address that is associated with your commits might be visible to the public. The email address that is associated with your {{site.data.keyword.Bluemix_notm}} account is used when you create commits through the {{site.data.keyword.gitrepos}} web interface.
