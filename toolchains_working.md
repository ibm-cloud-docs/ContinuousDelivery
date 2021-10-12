---

copyright:
  years: 2015, 2021

lastupdated: "2021-05-31"

keywords: set of tool integrations, toolchains, templates, collective power of a toolchain, IBM Cloud, IAM, 

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
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}

# Creating toolchains
{: #toolchains_getting_started}
{: help} 
{: support}

A *toolchain* is a set of tool integrations that support development, deployment, and operations tasks. The collective power of a toolchain is greater than the sum of its individual tool integrations.
{: shortdesc}

Open toolchains are available in the Public and Dedicated environments on {{site.data.keyword.cloud}}. You can create a toolchain in two ways: use a template to create a toolchain or create a toolchain from an app.

Each toolchain is associated with a specific resource group or organization (org). If a toolchain is associated with a resource group, any user that has Identity and Access Management (IAM) Viewer permission for the toolchain resource or the resource group that contains it can access the toolchain. If the toolchain is associated with an org, any user that is a member of that org can be added to the access control list for any of its associated toolchains. For more information about access control for toolchains in Cloud Foundry orgs, see [Managing user access to toolchains in Cloud Foundry orgs](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-cf-security). For more information about access control for toolchains in resource groups, see [Managing user access to toolchains in resource groups](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security).

On {{site.data.keyword.cloud_notm}} Public, depending on the template or toolchain that you use, the toolchain might include a GitHub or Git repository (repo) that is populated with app starter code and a preconfigured delivery pipeline. When you push changes to the toolchain's repo, the delivery pipeline automatically builds and deploys the app to {{site.data.keyword.cloud_notm}}.

On {{site.data.keyword.cloud_notm}} Dedicated, depending on the template or toolchain that you use, the toolchain might include a GitHub repo that is populated with app starter code and a preconfigured delivery pipeline. When you push changes to the toolchain's GitHub repo, the delivery pipeline automatically builds and deploys the apps to {{site.data.keyword.cloud_notm}}.

To see which toolchains and tool integrations are available, see [Toolchain availability, templates, and tutorials](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about).

## Creating a toolchain from a template   
{: #creating_a_toolchain_from_a_template}

You can use a template as a starting point to [create a toolchain](https://cloud.ibm.com/devops/create){: external} that includes a specific set of tool integrations. Depending on the template that you use, you can create a toolchain that has a specific set of tool integrations or an empty toolchain that you can add tool integrations to. Learn more about how to use the templates from the [IBM Cloud Garage Method ](https://www.ibm.com/cloud/garage/category/tools){:external}.

1. If you use {{site.data.keyword.cloud_notm}} Public, log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. If you use {{site.data.keyword.cloud_notm}} Dedicated, log in to your Dedicated environment on {{site.data.keyword.cloud_notm}}
1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
1. On the **Toolchains** page, click **Create a Toolchain**.
1. On the **Create a Toolchain** page, click a toolchain template.
1. Review the diagram of the toolchain that you are about to create. The diagram shows each tool integration in its lifecycle phase in the toolchain.

 A few of the toolchain templates have multiple instances of a tool integration. For example, the Microservices toolchain template on {{site.data.keyword.cloud_notm}} Public contains three instances of GitHub and three instances of Delivery Pipeline, one for each of the three microservices.
 {: tip}

 The diagram in the following image is an example. When you create a toolchain, the diagram shows each tool integration that is part of the toolchain.
![Toolchain diagram](images/toolchain_diagram2.png)

1. Review the default information for the toolchain settings:

 * The toolchain's name identifies it in {{site.data.keyword.cloud_notm}}. If you want to use a different name, change the toolchain's name.
 * The region to create the toolchain in. If you want to use a different region, select it from the list of available regions.
 * The resource group or organization to create the toolchain in. Click the link to switch between selecting resource groups and orgs. If you want to use a different resource group or org, select it from the list of available resource groups or orgs.
 * The provider for your source repository, such as GitHub, GitLab, or Bitbucket. If you want to use a different source provider, select it from the list of available repos.
 
   Resource groups are available in the Dallas, Washington, Toronto, London, Frankfurt, Sydney, Osaka, and Tokyo regions. Cloud Foundry orgs are supported in the Dallas, London, and Frankfurt regions.
   {: important}

1. In the Tool Integrations section, select each tool integration that you want to configure for your toolchain. A few of the tool integrations do not require configuration. For more information about configuring the tool integrations, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).

 Many of the tool integrations that comprise a toolchain require a secret to authenticate with the {{site.data.keyword.contdelivery_short}} service.
 {: tip}
 
 A secret is credentials that can be provided in the form of a password, authentication token, API key, or certificate. For example, when you add the Delivery Pipeline tool integration to your toolchain, you must provide a secret in the form of an API key. 

 a. In the Tool Integrations section, click **{{site.data.keyword.deliverypipeline}}**.

 b. Click **New** to create an {{site.data.keyword.cloud}} API Key.

 c. Click **OK** to apply your new API key.
 
   Each user can have a maximum of 20 API keys. 
   {: tip}
   
 d.  Click **OK** to create the API key without saving a secure copy of the key. 
 
 e. To securely save the API key so that you can use it again in other toolchains and starter kit workflows:
 
  * Select the **Save this key in a secrets store for reuse** checkbox to integrate with the default IBM Key Protect secrets store.
  * If you don't have an existing instance of Key Protect, specify a name for the instance and the secret.
  * Click **OK** to apply your new API key.
   
 f. To validate that your Key Protect instance was successfully created, go to your [{{site.data.keyword.cloud}} Resource list](https://cloud.ibm.com/resources){: external} and expand the **Services** twistie. To view your API keys, from the menu bar, click **Manage** &gt; **Access (IAM)**, and select **{{site.data.keyword.cloud}} API keys**.

 g. The API key that you created and copied to Key Project is now available for use on the Create a Toolchain page. Any tool integration that requires a secret displays a key icon. Click the key icon to open a Secrets Picker dialog box to retrieve secrets from one or more Key Protect instances. 
 
1. Click **Create**. Several steps run automatically to set up your toolchain. The tool integrations that are set up are different depending on which toolchain template you selected and whether you are using {{site.data.keyword.cloud_notm}} Public or {{site.data.keyword.cloud_notm}} Dedicated. For example, when you create a Microservices toolchain on {{site.data.keyword.cloud_notm}} Public, these steps are run:

 * The toolchain is created.
 * If you configured Delivery Pipeline, the pipelines are created and triggered.
 * If you configured Sauce Labs, the toolchain is set up to add Sauce Labs test jobs to the pipelines.
 * If you configured PagerDuty, the toolchain is set up to send alert notifications to the PagerDuty service that you specified.
 * If you configured Slack, the toolchain is set up to send notifications about deployment status to the Slack channel that you specified.
 * If you configured a source code tool integration such as GitHub, the sample GitHub repo is cloned into your GitHub account.


## Creating a toolchain from an app
{: #creating_a_toolchain_from_an_app}

You can create a toolchain from your app. The toolchain can support continuous development, deployment, monitoring, and more, and it is associated with your app. Each app can be associated with a toolchain. When you push changes to the toolchain's GitHub repo, the pipeline automatically builds and deploys the app.

If you created your app by using your own code repository, click **Deploy my app** on your app's details page. Then, follow the steps that are described in [Creating apps from your own code repository](/docs/apps?topic=apps-tutorial-byoc#tutorial-byoc).
{: note}

1. If you created your app by using a starter kit, click **Deploy my app** on your app's details page. Next, select a deployment target. If you use {{site.data.keyword.cloud_notm}} Public, your app is configured for continuous delivery from a new GitHub repo that is populated with the app starter code. If you use {{site.data.keyword.cloud_notm}} Dedicated, your app is configured for continuous delivery from a new GitHub repo that is populated with the app starter code.
1. On the toolchain configuration page, review the diagram of the toolchain that you are about to create. The diagram shows each tool integration in its lifecycle phase in the toolchain.
1. Review the default information for the toolchain settings. The toolchain's name identifies it in {{site.data.keyword.cloud_notm}}. If you want to use a different name, change the toolchain's name.
1. In the Tool Integrations section, select each tool integration that you want to configure for your toolchain. A few of the tool integrations do not require configuration. For more information about configuring the tool integrations, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).
1. Click **Create**. Several steps run automatically to set up your toolchain. The tool integrations that are set up are different depending on whether you are using toolchains on {{site.data.keyword.cloud_notm}} Public or {{site.data.keyword.cloud_notm}} Dedicated. For example, when you create a toolchain from an app on {{site.data.keyword.cloud_notm}} Public, these steps are run:

 * The toolchain is created.
 * If you configured Delivery Pipeline, the pipelines are created and triggered.
 * If you configured GitHub, the sample GitHub repo is cloned into your GitHub account.


## Viewing a toolchain
{: #viewing_a_toolchain}

### Viewing a toolchain in the console
{: #viewing-toolchain-console}
{: ui}

After you configure the toolchain and its tool integrations, you can view a visual representation of the toolchain.

You can view a toolchain from an app by clicking the toolchain name from your app's details page.
{: tip}

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. 
1. On the Toolchains page, select a **Resource Group** or **Location**. All of the toolchains that are contained within the selected resource group or Cloud Foundry org are displayed. Click the toolchain that you want to view to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
2. To access a tool integration that is in your toolchain, click the tool.

 If you have more than one GitHub or Git repo, you might have multiple cards for the same tool integration because each repo is represented by its own card. If you have more than one pipeline, you might have multiple cards for the same tool integration because each pipeline is represented by its own card. For example, when you create a Microservices toolchain, each of the three microservices has its own GitHub or Git repo and its own pipeline.
 {: tip}
 
### Viewing a toolchain by using the CLI
{: #viewing-toolchain-cli}
{: cli}

The command-line interface (CLI) toolchain view depends on the currently targeted resource group. Use the following commands to identify or change your currently targeted resource group.

* To view the currently targeted resource group, run the following command:
  ```
  ibmcloud target
  ``` 
  {: codeblock}

* If no resource group is set, or if you would like to change the resource group, run the following command: 
  ```
  ibmcloud target -g [resource-group]
  ```
  {: codeblock}

* To view toolchains in the targeted resource group, run the following command:
  ```
  ibmcloud dev toolchains
  ```
  {: codeblock}

* To view the details for a specific toolchain, run the following command:
  ```
  ibmcloud dev toolchain-get [toolchain-name]
  ```
  {: codeblock}

* To view the toolchain details in a browser, run the following command:
  ```
  ibmcloud dev toolchain-open [toolchain-name]
  ```
  {: codeblock}  

## Take a tutorial: Using toolchains
{: #toolchain_tutorials}

Check out one of these tutorials on the [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}.

  * [Add a toolchain to an app](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){: external}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}.
