---

copyright:
  years: 2015, 2024
lastupdated: "2024-06-19"

keywords: error message, Lite plan, toolchains, IBM Cloud

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for {{site.data.keyword.contdelivery_short}}
{: #ts_cd}

Get answers to frequently asked questions about using {{site.data.keyword.contdelivery_full}}.
{: shortdesc} 


## My {{site.data.keyword.contdelivery_short}} service states that Lite plan services are deleted after 30 days of inactivity. What does inactivity mean?
{: #plan_inactivity}
{: faq}
{: support}

An instance of the {{site.data.keyword.contdelivery_short}} service is considered active when one or more of the toolchains within the same resource group is active. A toolchain is considered active if users interact with it by way of the user interface, delivery pipeline jobs are triggered, or repositories that are managed by {{site.data.keyword.gitrepos}} are accessed. To be considered inactive, all of these conditions must be absent for all of the toolchains that are associated with the {{site.data.keyword.contdelivery_short}} service, for 30 days.


## I tried to deploy an app to {{site.data.keyword.cloud_notm}}, why am I getting an error?
{: #org_outofmemory}
{: faq}

When trying to deploy an app to {{site.data.keyword.cloud_notm}}, if you get the following error message, the amount of memory that is remaining in your organization is less than the amount of memory that is required by the app that you want to deploy.

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

You can either increase the memory quota of your account or reduce the memory that your apps use. The maximum memory quota for a trial account is 2 GB. To increase the memory quota of your account, convert your trial account to a pay account. For information about how to convert your trial account to a pay account, see [How do I upgrade or change my account?](/docs/account?topic=account-accountfaqs#changeacct). To reduce the memory that your apps use, use either the {{site.data.keyword.cloud_notm}} console or the cf command line interface.

If you use the {{site.data.keyword.cloud_notm}} console, complete the following steps:

1. In the Apps Dashboard, select your app. The app details page opens.
1. In the runtime pane, you can reduce the maximum memory limit or the numbers of app instances, or both, for your app.

If you use the cf command line interface, complete the following steps:

1. Check how much memory is being used for your apps. The cf apps command lists all the apps that you deployed in your current space. The status of each app is also displayed.

   ```text
   cf apps
   ```

1. To reduce the amount of memory that is used by your app, reduce the number of app instances or the maximum memory limit, or both:

   ```text
   cf push appname -p app_path -i instance_number -m memory_limit
   ```
    
1. Restart your app for the changes to take effect.


## Can I use sample scripts to build and deploy my application?
{: #sample_scripts}
{: faq}

The [open-toolchain/commons](https://github.com/open-toolchain/commons){: external} GitHub repo contains a collection of common scripts that you can use in toolchains and pipelines. For example, you can use one of the shell scripts that is contained in this repo within your own toolchains in various ways.


## How do I bring my own code and deploy it by using {{site.data.keyword.contdelivery_short}}
{: #bmoc_deploy}
{: faq}

You can choose any of the following options to deploy your own code to {{site.data.keyword.contdelivery_short}}:
 
* Create a toolchain by using one of the available templates (dependent on the deployment target and tool integrations). On the **Create a Toolchain** page, select the appropriate provider for your source repository, and then specify the link to your source code repo. After you create your toolchain, you might need to adjust the pipeline scripts for your deployment goals.
* Create an empty toolchain, and then add tool integrations to deploy your app. For more information about using this method to deploy your code to {{site.data.keyword.contdelivery_short}}, see [Deploy an app on Kubernetes](/docs/ContinuousDelivery?topic=ContinuousDelivery-tutorial-cd-kubernetes).


## How do I find the status of {{site.data.keyword.cloud_notm}} and the {{site.data.keyword.contdelivery_short}} service?
{: #toolchains_load}
{: faq}
{: support}

Check the {{site.data.keyword.cloud_notm}} Status page to determine whether known issues are affecting the {{site.data.keyword.cloud_notm}} platform and the major services in {{site.data.keyword.cloud_notm}}.

You can find the Status page by choosing either of the following options:


* In the {{site.data.keyword.cloud_notm}} console, go to **Support**. From the Today's notifications widget, click **View all**, and then click **Status** to view the status of resources in all {{site.data.keyword.cloud_notm}} locations. You can view a list of events, in chronological order, for maintenance and incidents. You can search across all notifications, or filter by type, geographic locations, and individual resources. You can also view planned maintenance windows for which prior notice is provided and unplanned incidents or outages, which are posted as soon as the IBM Cloud team becomes aware of them. Incident notifications are regularly updated until they're resolved.
* Access it directly at [{{site.data.keyword.cloud_notm}} - System Status](https://cloud.ibm.com/status){: external}.


For more information about the {{site.data.keyword.cloud_notm}} Status page, see [Viewing {{site.data.keyword.cloud_notm}} status](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status).


## How do I remove authorized users from the {{site.data.keyword.contdelivery_short}} service?
{: #remove_authorized_users}
{: faq}
{: support}

You can remove authorized users from the {{site.data.keyword.contdelivery_short}} service and prevent them from being added again.

* Remove the user's access in IAM to all toolchains in the resource group.
* Remove the user from the authorized user list in the {{site.data.keyword.contdelivery_short}} service instance.
* Remove Developer access from all {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group.

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} instances, see [{{site.data.keyword.at_full_notm}} events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events). For more information about managing authorized users, see [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users).


## Why is the `AUTHORIZED_USERS_PER_MONTH` quantity reported in {{site.data.keyword.cloud_notm}} Billing and usage different from the actual number of authorized users listed for my {{site.data.keyword.contdelivery_short}} service instance?
{: #auth_user_counting}
{: faq}
{: support}

The `AUTHORIZED_USERS_PER_MONTH` quantity is computed as an average of the number of authorized users per day. If authorized users are added or removed, the average will increase or decrease. For example, if a service instance has one authorized user for the first half of June, then a second authorized user is added on June 16, the `AUTHORIZED_USERS_PER_MONTH` quantity for the entire month of June will be `1.5`.


## Why is the `AUTHORIZED_USERS_PER_MONTH` quantity reported in {{site.data.keyword.cloud_notm}} Billing and usage equal to zero for my {{site.data.keyword.contdelivery_short}} service instance?
{: #auth_user_zero}
{: faq}
{: support}

The service instance resides in an account in an enterprise, and is participating in consolidated billing. When consolidated billing is enabled on a {{site.data.keyword.contdelivery_short}} service instance in an enterprise account, only that instance will report a non-zero quantity of authorized users. All other {{site.data.keyword.contdelivery_short}} service instances in the enterprise hierarchy and in the same region will report zero authorized users, even though they continue to list their authorized users. For more information about consolidated billing, see [Consolidated billing](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#consolidated_billing).


## Can I avoid being billed for the same authorized users in multiple instances of the {{site.data.keyword.contdelivery_short}} service?
{: #avoid_multiple_billing}
{: faq}
{: support}

If your {{site.data.keyword.contdelivery_short}} service instances are organized into an enterprise, you can enable consolidated billing on a {{site.data.keyword.contdelivery_short}} service instance in the enterprise account so that authorized users are only reported for billing once for all service instances within the enterprise and in the same region. For more information about consolidated billing, see [Consolidated billing](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#consolidated_billing).


## Can I manage {{site.data.keyword.contdelivery_short}} service instances by using Terraform?
{: #manage_cd_terraform}
{: faq}
{: support}

You can use Terraform to provision, update, and de-provision instances of the {{site.data.keyword.contdelivery_short}} service. For more information about using Terraform with {{site.data.keyword.contdelivery_short}}, see [Creating a {{site.data.keyword.contdelivery_short}} service instance with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service&interface=terraform#create_cd_service_terraform), [Deleting a {{site.data.keyword.contdelivery_short}} service instance with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-delete_cd_service&interface=terraform#deleting_rg_terraform), and the [`ibm_resource_instance` resource documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/resource_instance){: external}.

You cannot use Terraform to manage the list of authorized users for a {{site.data.keyword.contdelivery_short}} service instance. You can manage the list of authorized users only by using the console. For information about authorized user management, see [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage&interface=ui#authorized_users).


## Can I manage {{site.data.keyword.contdelivery_short}} service instances by using an API?
{: #manage_cd_api}
{: faq}
{: support}

You can use HTTP APIs or selected programming language SDKs to provision, update, and de-provision instances of the {{site.data.keyword.contdelivery_short}} service. For more information about using {{site.data.keyword.contdelivery_short}} with the API, see [Creating a {{site.data.keyword.contdelivery_short}} service instance with the API](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service&interface=api#create_cd_service_api) and [Deleting a {{site.data.keyword.contdelivery_short}} service instance with the API](/docs/ContinuousDelivery?topic=ContinuousDelivery-delete_cd_service&interface=api#deleting_rg_api).

You cannot use APIs to manage the list of authorized users of a {{site.data.keyword.contdelivery_short}} service instance. You can manage the list of authorized users only by using the console. For information about authorized user management, see [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage&interface=ui#authorized_users).


## Can I use the console, APIs, or CLI to modify resources that are managed by Terraform?
{: #cd_resource_drift}
{: faq}
{: support}

When you use Terraform to manage resources such as {{site.data.keyword.contdelivery_short}} service instances, toolchains, and Tekton pipelines, avoid changing the resources by using the console, APIs, or CLI, or by any other method outside of Terraform's control.

If you circumvent Terraform by directly changing resources, you might cause [resource drift](https://developer.hashicorp.com/terraform/tutorials/state/resource-drift){: external}, a situation in which the states of your actual resources on {{site.data.keyword.cloud_notm}} deviate from the definition of the resources in Terraform. The next time that you apply the Terraform configuration, Terraform attempts to update your resources to bring them back in alignment with the Terraform configuration. This action might lead to unintended consequences, such as reverting changes or deleting and then re-creating resources.

For more information about resource drift, see [Manage Resource Drift](https://developer.hashicorp.com/terraform/tutorials/state/resource-drift){: external}. 
