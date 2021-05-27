---

copyright:
  years: 2020, 2021

lastupdated: "2021-05-26"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository, Git source control, authentication, GitHub 

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Creating toolchains with Git
{: #toolchains_git}
{: help} 
{: support}

You can use a template that contains either a {{site.data.keyword.gitrepos}} or GitHub tool integration as a starting point to create a toolchain that you can add Git repositories (repos) to. Alternatively, you can start with an empty toolchain and add either a {{site.data.keyword.gitrepos}} or GitHub tool integration to it. 
{: shortdesc}

To see which toolchain templates contain the {{site.data.keyword.gitrepos}} or GitHub tool integrations, see [Toolchain availability, templates, and tutorials](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about#templates).

## Creating a toolchain from a template with {{site.data.keyword.gitrepos}} or GitHub   
{: #creating_a_toolchain_git}

You can use a template as a starting point to [create a toolchain](https://cloud.ibm.com/devops/create){:external} that includes either a {{site.data.keyword.gitrepos}} or GitHub tool integration. Learn more about how to use the templates from the [IBM Cloud Garage Method](https://www.ibm.com/cloud/garage/category/tools){:external}.

1. If you use {{site.data.keyword.cloud_notm}} Public, log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){:external}.
1. If you use {{site.data.keyword.cloud_notm}} Dedicated, log in to your Dedicated environment on {{site.data.keyword.cloud_notm}}
1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**.
1. On the DevOps dashboard, on the **Toolchains** page, click **Create a Toolchain**.
1. On the **Create a Toolchain** page, click a toolchain template.
1. Review the diagram of the toolchain that you are about to create. The diagram shows each tool integration in its lifecycle phase in the toolchain.
1. Review the default information for the toolchain settings:

 * The toolchain's name identifies it in {{site.data.keyword.cloud_notm}}. If you want to use a different name, change the toolchain's name.
 * The region to create the toolchain in. If you want to use a different region, select it from the list of available regions.
 * The resource group or organization to create the toolchain in. Click the link to switch between selecting resource groups and orgs. If you want to use a different resource group or org, select it from the list of available resource groups or orgs.
 * The provider for your source repository, such as GitHub or GitLab. If you want to use a different source provider, select it from the list of available repos.
 
   Resource groups are available in the Dallas, Washington, Toronto, London, Frankfurt, Sydney, Osaka, and Tokyo regions. Cloud Foundry orgs are supported in the Dallas, London, and Frankfurt regions. Because Cloud Foundry orgs are deprecated, it is recommended that you use resource groups instead.
   {: important}

1. In the Tool Integrations section, select each tool integration that you want to configure for your toolchain. For more information about configuring the tool integrations, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations). 
1. Click **Create**. Several steps run automatically to set up your toolchain. The tool integrations that are set up are different depending on which toolchain template you selected and whether you are using {{site.data.keyword.cloud_notm}} Public or {{site.data.keyword.cloud_notm}} Dedicated. For example, when you create a Microservices toolchain on {{site.data.keyword.cloud_notm}} Public, these steps are run:

 * The toolchain is created.
 * If you configured Delivery Pipeline, the pipelines are created and triggered.
 * If you configured Sauce Labs, the toolchain is set up to add Sauce Labs test jobs to the pipelines.
 * If you configured PagerDuty, the toolchain is set up to send alert notifications to the PagerDuty service that you specified.
 * If you configured Slack, the toolchain is set up to send notifications about deployment status to the Slack channel that you specified.
 * If you configured a source code tool integration such as GitHub, the sample GitHub repo is cloned into your GitHub account.


## Creating an empty toolchain and adding the Git tool integration
{: #creating_empty_toolchain_git}

You can create an empty toolchain and then add a Git tool integration to the toolchain to start adding Git repos.

1. If you use {{site.data.keyword.cloud_notm}} Public, log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){:external}.
1. If you use {{site.data.keyword.cloud_notm}} Dedicated, log in to your Dedicated environment on {{site.data.keyword.cloud_notm}}
1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**.
1. On the DevOps dashboard, on the **Toolchains** page, click **Create a Toolchain**.
1. On the **Create a Toolchain** page, click the **Build your own toolchain** template.
1. Review the default information for the toolchain settings:

 * The toolchain's name identifies it in {{site.data.keyword.cloud_notm}}. If you want to use a different name, change the toolchain's name.
 * The region to create the toolchain in. If you want to use a different region, select it from the list of available regions.
 * The resource group or organization to create the toolchain in. Click the link to switch between selecting resource groups and orgs. If you want to use a different resource group or org, select it from the list of available resource groups or orgs.
 
   Resource groups are available in the Dallas, Washington, Toronto, London, Frankfurt, Sydney, Osaka, and Tokyo regions. Cloud Foundry orgs are supported in the Dallas, London, and Frankfurt regions.
   {: important}

1. Click **Create** to create your empty toolchain.
1. Click **Add Tool**, and then select **GitHub** or **{{site.data.keyword.gitrepos}}** to add either of these tool integrations to your toolchain.
1. For more information about configuring the GitHub tool integration, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-github).
1. For more information about configuring the {{site.data.keyword.gitrepos}} tool integration, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-grit).


For a tutorial about how to create a custom toolchain, see [Create a custom toolchain](https://www.ibm.com/cloud/architecture/tutorials/create-a-custom-toolchain){:external}.
{: tip}
