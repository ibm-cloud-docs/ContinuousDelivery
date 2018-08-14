---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Getting started with Continuous Delivery
{: #cd_getting_started}

Adopt a DevOps approach by using {{site.data.keyword.contdelivery_full}}, which includes open toolchains that automate the building and deployment of applications. You can get started by creating a simple deployment toolchain that supports development, deployment, and operations tasks. 
{: shortdesc}

If you aleady have an instance of {{site.data.keyword.contdelivery_short}}, you can [create a toolchain ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/create){: new_window} or [view existing toolchains](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}.
{: tip}

After you create an instance of {{site.data.keyword.contdelivery_short}} by selecting it from the {{site.data.keyword.Bluemix_notm}} catalog, you can [create a continuous delivery toolchain from a template](#starting_from_a_toolchain_template). The toolchain integrates tools for planning, developing, deploying pipelines, and managing your applications. You can always add or remove tools from your toolchains. If you already have toolchains, you can [view existing toolchains](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}. For more information about working with toolchains, see [Using toolchains](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}.


##{{site.data.keyword.contdelivery_short}} overview
{: #cd_overview}

With {{site.data.keyword.contdelivery_short}}, you can build, test, and deliver applications by using DevOps practices and industry-leading tools.
{:shortdesc}

The {{site.data.keyword.contdelivery_short}} service supports your DevOps workflows:

 * You can create integrated DevOps open [toolchains](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window} to enable tool integrations that support your development, deployment, and operations tasks.

  A toolchain is an integrated set of tools that you can use to collaboratively develop, build, deploy, test, and manage applications and make operations repeatable and easier to manage. Toolchains can include open source tools, {{site.data.keyword.Bluemix_notm}} services, such as [{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window}, and third-party tools, such as GitHub, PagerDuty, and Slack. 
  
  {{site.data.keyword.DRA_short}} is available only in the US South region.
  {: tip}

 * Deliver continuously by using automated [pipelines](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window}.

  Automate builds, unit tests, deployments, and more. Build, test, and deploy in a repeatable way with minimal human intervention. Be ready to release into production at any time.

 * Edit and push your code from anywhere by using the [web-based IDE](/docs/services/ContinuousDelivery/web_ide.html){: new_window}.

  Create, edit, run, and debug, and complete source-control tasks in GitHub. Seemlessly move from editing your code to deploying it to production. 
  
 * Collaborate with your team and manage your source code with a [Git repository (repos) and issue tracker](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window} that is hosted by IBM and built on GitLab Community Edition.

  Manage Git repos through fine-grained access controls that keep code secure. Review code and enhance collaboration through merge requests. Track issues and share ideas through the issue tracker. Document projects on the wiki system.


##Starting from a toolchain template
{: #starting_from_a_toolchain_template}

To create and configure a continuous delivery toolchain from a [template ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/create){: new_window}:

1. On the **Create a Toolchain** page, click a toolchain template.
1. Review the diagram of the toolchain that you are about to create. The diagram shows each tool integration in its lifecycle phase in the toolchain.

 A few of the toolchain templates have multiple instances of a tool integration. For example, the Microservices toolchain template on {{site.data.keyword.Bluemix_notm}} Public contains three instances of GitHub and three instances of Delivery Pipeline, one for each of the three microservices.
 {: tip}

 The diagram in the following image is an example. When you create a toolchain, the diagram shows each tool integration that is part of the toolchain.
 ![Toolchain_diagram](images/toolchain_diagram2.png)
1. Review the default information for the toolchain settings:

 * The toolchain's name identifies it in {{site.data.keyword.Bluemix_notm}}. If you want to use a different name, change the toolchain's name.
 * The region to create the toolchain in. If you want to use a different region, select it from the list of available regions.
 * The resource group or organization to create the toolchain in. Click the link to switch between selecting resource groups and orgs. If you want to use a different resource group or org, select it from the list of available resource groups or orgs.
 
   Resource groups are available only in the US South region.
   {: tip}
 
1. In the Tool Integrations section, select each tool integration that you want to configure for your toolchain. A few of the tool integrations do not require configuration. For information about configuring the tool integrations, see [Configuring tool integrations](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Click **Create**. Several steps run automatically to set up your toolchain. The tool integrations that are set up are different depending on which toolchain template you selected and whether you are using {{site.data.keyword.Bluemix_notm}} Public or {{site.data.keyword.Bluemix_notm}} Dedicated. For example, when you create a Microservices toolchain on {{site.data.keyword.Bluemix_notm}} Public, these steps are run:

 * The toolchain is created.
 * If you configured Delivery Pipeline, the pipelines are created and run.
 * If you configured Sauce Labs, the toolchain is set up to add Sauce Labs test jobs to the pipelines.
 * If you configured PagerDuty, the toolchain is set up to send alert notifications to the PagerDuty service that you specified.
 * If you configured Slack, the toolchain is set up to send notifications about deployment status to the Slack channel that you specified.
 * If you configured a source code tool integration such as GitHub, the sample GitHub repo is cloned into your GitHub account.
