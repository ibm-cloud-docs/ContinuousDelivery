---

copyright:
  years: 2015, 2020
lastupdated: "2020-01-31"

keywords: GitHub tool integration, error message, Lite plan, toolchains, Cloud Foundry orgs, resource groups, IBM Cloud, Web IDE, Live Sync, pipeline jobs

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# FAQs
{: #ts_cd}

Get answers to frequently asked questions about using {{site.data.keyword.contdelivery_full}}.
{:shortdesc} 


## Why does the Toolchains page show that the {{site.data.keyword.contdelivery_short}} service Lite plan is exceeded?
{: #plan_exceeded}
{: faq}
{: support}

{{site.data.keyword.contdelivery_short}} offers two plans: Lite and Professional. If you have the {{site.data.keyword.contdelivery_short}} Lite plan, you can use toolchains for free, up to the limits of the plan. The error message indicates that you exceeded one or more limits of the Lite plan. For example, you might exceed the plan if you have too many authorized users who are associated with the {{site.data.keyword.contdelivery_short}} service instance, or if you ran the maximum number of {{site.data.keyword.deliverypipeline}} jobs. For more information about the terms of your plan, see [Plan limitations and usage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## My {{site.data.keyword.contdelivery_short}} service states that Lite plan services are deleted after 30 days of inactivity. What does inactivity mean?
{: #plan_inactivity}
{: faq}
{: support}

An instance of the {{site.data.keyword.contdelivery_short}} service is considered active when one or more of the toolchains within the same resource group or Cloud Foundry organization (org) are active. A toolchain is considered active if users interact with it by way of the user interface, delivery pipeline jobs are triggered, repositories that are managed by {{site.data.keyword.gitrepos}} are accessed, or Eclipse Orion {{site.data.keyword.webide}} workspaces are in use. To be considered inactive, all of these conditions must be absent for all of the toolchains that are associated with the {{site.data.keyword.contdelivery_short}} service, for 30 days.


## I created a toolchain, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_required_resource_group}
{: faq}
{: support}

The terms of the plan for the {{site.data.keyword.contdelivery_short}} service instance that is in the same resource group or org as the toolchain manages the use of some of the tool integrations ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}}, and {{site.data.keyword.gitrepos}}) that are contained in the service. The error message indicates that the resource group or org doesn't contain the required instance of the {{site.data.keyword.contdelivery_short}} service. For more information about the terms of your plan, see [Plan limitations and usage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## I updated information for a toolchain from a Cloud Foundry org, why don't I see my changes in the toolchain?
{: #updates_in_cloud_foundry}
{: faq}
{: support}

When you update the toolchain information directly from Cloud Foundry, it might take a few minutes for the {{site.data.keyword.contdelivery_short}} service to refresh and show your changes. For example, if you add or remove a user from a Cloud Foundry org, it might take a few minutes for {{site.data.keyword.contdelivery_short}} to discover that there is a new user and to allow that user to access the toolchain.


## I created a toolchain in a Cloud Foundry org, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_required_cloud_foundry}
{: faq}

When you create a toolchain in a resource group or org that does not have an instance of the {{site.data.keyword.contdelivery_short}} service, the toolchain platform attempts to automatically create an instance of the service by using the Lite plan. The error message indicates that the toolchain platform couldn't create the service instance.

This error might occur when you create a toolchain in the US South region and in a Cloud Foundry org that doesn't already have an instance of {{site.data.keyword.contdelivery_short}}. In the US South region, you must create all new instances of the {{site.data.keyword.contdelivery_short}} service in resource groups. 

You can either create the toolchain in a resource group or create the toolchain in an org that already has an instance of {{site.data.keyword.contdelivery_short}}.
  

## How do I move my toolchain from a Cloud Foundry org to a resource group?
{: #toolchain_move_to_resource_group}
{: faq}
{: support}

A feature to automatically migrate toolchains from a Cloud Foundry org to a resource group is not available yet. Instead, you can manually create the toolchain again in a resource group, and then remove the original toolchain from the Cloud Foundry org.


## I tried to deploy an app to {{site.data.keyword.cloud_notm}}, why am I getting an error?
{: #org_outofmemory}
{: faq}

When trying to deploy an app to {{site.data.keyword.Bluemix_notm}}, if you get the following error message, the amount of memory that is remaining in your organization is less than the amount of memory that is required by the app that you want to deploy.

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

You can either increase the memory quota of your account or reduce the memory that your apps use. The maximum memory quota for a trial account is 2 GB. To increase the memory quota of your account, convert your trial account to a pay account. For information about how to convert your trial account to a pay account, see [How do I upgrade or change my account?](/docs/account?topic=account-accountfaqs#changeacct). To reduce the memory that your apps use, use either the {{site.data.keyword.Bluemix_notm}} console or the cf command line interface.

If you use the {{site.data.keyword.Bluemix_notm}} console, complete the following steps:

1. In the Apps Dashboard, select your app. The app details page opens.
1. In the runtime pane, you can reduce the maximum memory limit or the numbers of app instances, or both, for your app.

If you use the cf command line interface, complete the following steps:

1. Check how much memory is being used for your apps. The cf apps command lists all the apps that you deployed in your current space. The status of each app is also displayed.

	  ```
	  cf apps
	  ```

1. To reduce the amount of memory that is used by your app, reduce the number of app instances or the maximum memory limit, or both:

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```
    
1. Restart your app for the changes to take effect.


## How do I bring my own code and deploy it by using {{site.data.keyword.contdelivery_short}}
{: #bmoc_deploy}
{: faq}

You can choose any of the following options to deploy your own code to {{site.data.keyword.contdelivery_short}}:

  * Go to the [Create App](https://cloud.ibm.com/developer/appservice/create-app?navMode=dashboard){: external}, create your app, and then [enable {{site.data.keyword.contdelivery_short}}](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) for the app. 
  * Create a toolchain by using one of the available templates (dependent on the deployment target and tool integrations). On the **Create a Toolchain** page, select the appropriate provider for your source repository, and then specify the link to your source code repo. After you create your toolchain, you might need to adjust the pipeline scripts for your deployment goals.
  * Create an empty toolchain, and then add tool integrations to deploy your app. For more information about using this method to deploy your code to {{site.data.keyword.contdelivery_short}}, see [Set up a DevOps delivery pipeline for your app](/docs/apps?topic=containers-tutorial-byoc-kube).


## I created an app, why doesn't the run bar show {{site.data.keyword.cloud_notm}} Live Sync icons in the {{site.data.keyword.webide}}?
{: #ts_llz_lkb_3r}
{: faq}

![Run bar](images/webide_runbar_light.png)   

When you edit a Node.js app in the {{site.data.keyword.webide}}, the {{site.data.keyword.cloud_notm}} live edit, quick restart, and debug icons aren't available in the run bar in these circumstances:


* The `manifest.yml` file isn't stored at the top level of your project.
* Your app is stored in a subdirectory rather than root, but the path to the subdirectory isn't specified in the `manifest.yml` file.
* The app does not contain a `package.json` file.


If the `manifest.yml` file isn't stored at the root, store it there. If your app is stored in a subdirectory, specify the path to the subdirectory in the `manifest.yml` file. If the app doesn't contain a `package.json` file, create one that is in the same directory as your app.


## I clicked the {{site.data.keyword.webide}} run button, where are the log files? 
{: #web_ide_log_files}
{: faq}  

When you click the Run button, the contents of your workspace are pushed to Cloud Foundry in the same way that they are deployed if you type `cf push` from your desktop. You can find the log files from the Cloud Foundry dashboard.

For more information about deploying the contents of your workspace, see [Deploying an app from your workspace](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy).


## How do I prevent the {{site.data.keyword.webide}} from automatically selecting all of the changes in the Git view? 
{: #web_ide_git_view}
{: faq} 

The {{site.data.keyword.webide}} assumes by default that you want to push outgoing changes to your code repository each time that you go to the Git page. If you want to manually select which resources to commit, sync, reset, and replace, from the GIT preference page, clear the **Always select changed files** checkbox.


## Why doesn't the {{site.data.keyword.webide}} support the language that I use? 
{: #web_ide_language_support}
{: faq}  

The {{site.data.keyword.webide}} provides extensive tools and support for JavaScript, HTML, and CSS. It also provides syntax highlighting for most popular languages. You can't extend the {{site.data.keyword.webide}} to support a particular language. To view a complete list of the languages that the {{site.data.keyword.webide}} supports, see [Supported languages](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages).


## How do I find the status of {{site.data.keyword.cloud_notm}} and the {{site.data.keyword.contdelivery_short}} service?
{: #toolchains_load}
{: faq}
{: support}

Check the {{site.data.keyword.cloud_notm}} Status page to determine whether known issues are affecting the {{site.data.keyword.cloud_notm}} platform and the major services in {{site.data.keyword.cloud_notm}}.

You can find the Status page by choosing either of the following options:

  * Log in to the {{site.data.keyword.cloud_notm}} console. From the menu bar, click **Support** and select **Status**. Check the listed resources for the ![some issues](../../get-support/images/some_issues.svg) icon. This icon might indicate an outage.
  * Access it directly at [{{site.data.keyword.cloud_notm}} - System Status](https://cloud.ibm.com/status){: external}.

For more information about the {{site.data.keyword.cloud_notm}} Status page, see [Viewing {{site.data.keyword.Bluemix_notm}} status](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status).


## How do I pass artifacts between pipeline jobs?
{: #artifacts_pipeline_jobs}
{: faq}
{: support}

When a stage runs, the stage's input is passed to each of the jobs in the stage. Each job is given a clean container to run in. As a result, jobs within a stage cannot pass artifacts to each other. To pass artifacts between jobs, separate the jobs into two stages, and use the output from the job in the first stage as input to the second stage.

For more information about pipeline jobs, see [Jobs](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs).


## Is there a maximum time limit that my pipeline jobs can run?
{: #pipeline_jobs_time_limit}
{: faq}
{: support}

Each pipeline job can run for a maximum of 60 minutes. However, you can increase the time limit to 24 hours by using [{{site.data.keyword.deliverypipeline}} Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers).


## How secure are the pipeline secure properties?
{: #pipeline_secure_properties}
{: faq}

Pipeline secure properties are encrypted by using AES-128, and decrypted immediately before they are passed to your pipeline script. These properties are also masked by using asterisks in the properties user interface and in your pipeline log files. Before data is written to the log file for your pipeline job, it is scanned for exact matches to all of the values in the pipeline secure properties. If a match is found, it is masked by using asterisks. Be careful when you are working with secure properties and log files since only exact matches are masked. 


## Can {{site.data.keyword.DRA_short}} be installed and run in an on-premises environment?
{: #run-on-prem}
{: faq}

{{site.data.keyword.DRA_short}} isn't available for an on-premises environment. It's only available in {{site.data.keyword.IBM_notm}} Public Cloud.


## My Jenkins or Travis CI is running in an on-premises environment or in another public cloud. Can I still publish build records, test records, deployment records to DevOps Insights, and use quality gates?
{: #CI-on-prem}
{: faq}

Yes, it doesn't matter from where your pipeline tool is running.


## I am deploying my applications to on-premises environments or other public clouds. Can I publish build records, test records, deployment records to {{site.data.keyword.DRA_short}}, and use quality gates for these applications? 
{: #app-on-prem}
{: faq}

Yes, it doesn't matter where your applications are deployed.


## Why can't I see my app on the Quality Dashboard page?
{: #app-quality-dashboard}
{: faq}

For an application to show up in the Quality Dashboard page, it must have a build record for the selected branch, and at least one test record for that build. For more information about build and test records, see [Integrating your {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-setting-values-cli).

You can find published build records on the Build Frequency page. For more information, see [Viewing the build frequency](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cli#build-frequency-cli).


## How do I delete {{site.data.keyword.DRA_short}}?
{: #delete-insights-faq}
{: faq}

Deleting your tool integration deletes all data that is associated with that toolchain. For more information about how to delete your {{site.data.keyword.DRA_short}} instance, see [Deleting a DevOps Insights tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-deleting_data).  


## Can I delete build, test, and deploy data from {{site.data.keyword.DRA_short}}?
{: #delete-specific-data}
{: faq}

You can delete data sets from for toolchain, environment, application, and for a branch. For more information about how to delete a specific data set, see [Deleting {{site.data.keyword.DRA_short}} data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-deleting_data).


## How do I find my toolchain ID?
{: #find-toolchain-ID}
{: faq}

You can find your toolchain ID in the URL of your selected toolchain tool. For more information, see [Identifying your toolchain ID](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources). 


## Do I need a {{site.data.keyword.contdelivery_short}} service instance to use {{site.data.keyword.DRA_short}}?
{: #cd-for-di}

Yes. To use {{site.data.keyword.DRA_short}}, you must create a {{site.data.keyword.contdelivery_short}} [service instance](https://cloud.ibm.com/catalog/services/continuous-delivery) if you don't already have one. For more information, see [Scope of a service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#service_scope). 


## How am I billed for {{site.data.keyword.DRA_short}}?
{: #billed-devops-insights}

You are not billed for {{site.data.keyword.DRA_short}} as an individual service. {{site.data.keyword.DRA_short}} counts toward your {{site.data.keyword.contdelivery_short}} limitations and usage. A user of {{site.data.keyword.DRA_short}} is added to your {{site.data.keyword.contdelivery_short}} authorized users. For more information, see [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users). 
