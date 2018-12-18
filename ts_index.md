---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-6"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
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


## I tried to add the GitHub tool integration to my toolchain, why wasn't the tool integration added?
{: #cannot_authorize_github}
{: faq}

If {{site.data.keyword.Bluemix_notm}} is not authorized to access your GitHub account, the tool integration is not added to your toolchain.

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps to authorize with GitHub:

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and {{site.data.keyword.Bluemix_notm}} is not authorized to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account.
 1. When you are finished updating the settings, click **Save Integration**.


## I tried to create a toolchain, why am I getting an error?
{: #cannot_create_toolchain}
{: faq}

When trying to create a toolchain in an org, if you get the following error message, remove one or more toolchains from your org and then create your toolchain again.

`This organization contains 200 toolchains, which is the maximum limit. Before you can add another toolchain, remove one or more toolchains from the organization.`


## Why does the Toolchains page show that the {{site.data.keyword.contdelivery_short}} service Lite plan is exceeded?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} offers two plans: Lite and Professional. If you have the {{site.data.keyword.contdelivery_short}} Lite plan, you can use toolchains for free, up to the limits of the plan. The error message indicates that you exceeded one or more limits of the Lite plan. For example, you might exceed the plan if you have too many authorized users who are associated with the {{site.data.keyword.contdelivery_short}} service instance, or if you ran the maximum number of {{site.data.keyword.deliverypipeline}} jobs. For more information about the terms of your plan, see [Plan limitations and usage](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## I created a toolchain, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_required_resource_group}
{: faq}

The terms of the plan for the {{site.data.keyword.contdelivery_short}} service instance that is in the same resource group or org as the toolchain manages the use of some of the tool integrations ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}}, and {{site.data.keyword.gitrepos}}) that are contained in the service. The error message indicates that the resource group or org doesn't contain the required instance of the {{site.data.keyword.contdelivery_short}} service. For more information about the terms of your plan, see [Plan limitations and usage](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## I created a toolchain in a Cloud Foundry org, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_required_cloud_foundry}
{: faq}

When you create a toolchain in a resource group or org that does not have an instance of the {{site.data.keyword.contdelivery_short}} service, the toolchain platform attempts to automatically create an instance of the service by using the Lite plan. The error message indicates that the toolchain platform couldn't create the service instance.

This error might occur when you create a toolchain in the US South region and in a Cloud Foundry org that doesn't already have an instance of {{site.data.keyword.contdelivery_short}}. In the US South region, you must create all new instances of the {{site.data.keyword.contdelivery_short}} service in resource groups. 

You can either create the toolchain in a resource group or create the toolchain in an org that already has an instance of {{site.data.keyword.contdelivery_short}}.
  

## I tried to deploy an app to {{site.data.keyword.Bluemix_notm}}, why am I getting an error?
{: #org_outofmemory}
{: faq}

When trying to deploy an app to {{site.data.keyword.Bluemix_notm}}, if you get the following error message, the amount of memory that is remaining in your organization is less than the amount of memory that is required by the app that you want to deploy.

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

You can either increase the memory quota of your account or reduce the memory that your apps use. The maximum memory quota for a trial account is 2 GB. To increase the memory quota of your account, convert your trial account to a pay account. For information about how to convert your trial account to a pay account, see [Pay accounts](/docs/pricing/index.html#pay-accounts). To reduce the memory that your apps use, use either the {{site.data.keyword.Bluemix_notm}} console or the cf command line interface.

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


## I created an app, why doesn't the run bar show {{site.data.keyword.Bluemix_notm}} Live Sync icons in the Eclipse Orion Web IDE?
{: #ts_llz_lkb_3r}
{: faq}

![Run bar](images/webide_runbar_light.png)   

When you edit a Node.js app in the Web IDE, the {{site.data.keyword.Bluemix_notm}} live edit, quick restart, and debug icons aren't available in the run bar in these circumstances:


* The `manifest.yml` file isn't stored at the top level of your project.
* Your app is stored in a subdirectory rather than root, but the path to the subdirectory isn't specified in the `manifest.yml` file.
* The app does not contain a `package.json` file.


If the `manifest.yml` file isn't stored at the root, store it there. If your app is stored in a subdirectory, specify the path to the subdirectory in the `manifest.yml` file. If the app doesn't contain a `package.json` file, create one that is in the same directory as your app.


## I clicked a toolchain to view its Overview page, why doesn't the toolchain load?
{: #toolchains_load}
{: faq}

Check the {{site.data.keyword.Bluemix_notm}} Status page to determine whether known issues are affecting the {{site.data.keyword.Bluemix_notm}} platform and the major services in {{site.data.keyword.Bluemix_notm}}.

You can find the Status page by choosing either of the following options:

  * Log in to the {{site.data.keyword.Bluemix_notm}} console. From the menu bar, click **Support** and select **Status**. Check the listed resources for the ![some issues](../../get-support/images/some_issues.svg) icon. This icon might indicate an outage.
  * Access it directly at [{{site.data.keyword.Bluemix_notm}} - System Status ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/status){: new_window}.

For more information about the {{site.data.keyword.Bluemix_notm}} Status page, see [Viewing {{site.data.keyword.Bluemix_notm}} status](https://cloud.ibm.com/docs/get-support/ViewStatus.html#viewing-bluemix-status).


## I configured a tool integration for my toolchain, why wasn't it configured?
{: #tool_integration_error}
{: faq}

When you add a tool integration, the toolchain communicates with the tool that is represented by the tool integration to provision any necessary resources and associate them with the toolchain. If an error occurs during the setup process or if the communication between the toolchain and the tool does not complete properly, the tool integration is put into an error state.

 ![Setup failed error](images/tool_setup_failed.png)

You can try to configure the tool integration again:

1. On its tool card, hover over the `Setup failed` message and click **Reconfigure**.

 ![Reconfigure button](images/tool_reconfigure.png)

1. Make sure that you are using valid configuration parameters. If the error was caused by an invalid configuration, an error message is displayed; for example, `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`. Update the settings for the tool integration and click **Save integration**.
1. If the error was caused by a communication problem, click **Save integration** to try again.
