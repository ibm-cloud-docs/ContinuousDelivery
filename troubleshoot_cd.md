---

copyright:
  years: 2015, 2022
lastupdated: "2022-06-20"

keywords: troubleshoot, toolchains, Cloud Foundry

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:deprecated: .deprecated}
{:tip: .tip}
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Troubleshooting for {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

General problems with using {{site.data.keyword.contdelivery_full}} might include Cloud Foundry issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}


## Why can't I add {{site.data.keyword.contdelivery_short}} to a Cloud Foundry org?
{: #troubleshoot-resource_groups}
{: troubleshoot}
{: support}

Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances and toolchains are deprecated. You can no longer create Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances. As of 14 January 2022, you cannot create new toolchains within Cloud Foundry orgs. You can create new toolchains in resource groups. On 28 February 2022, all toolchains within Cloud Foundry orgs that did not contain a Professional plan instance of the {{site.data.keyword.contdelivery_short}} service were deleted. As of 15 August 2022, all toolchains within Cloud Foundry orgs that contain a Professional plan instance of the {{site.data.keyword.contdelivery_short}} service will be deleted. Before this date, you can use the [toolchain migration wizard](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains) to migrate existing toolchains from Cloud Foundry orgs to resource groups.
{: deprecated}

You can no longer create instances of the {{site.data.keyword.contdelivery_short}} service in Cloud Foundry orgs. You can no longer create new toolchains in Cloud Foundry orgs.

The following message is displayed on the Toolchains page for your toolchain in a Cloud Foundry org:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

When you click **Add the service** there is no option to create {{site.data.keyword.contdelivery_short}} in a Cloud Foundry org. You can only create {{site.data.keyword.contdelivery_short}} in a resource group.

Resource groups replaced Cloud Foundry orgs for the management of {{site.data.keyword.contdelivery_short}} service instances and toolchains.
{: tsCauses}

Migrate your toolchains from Cloud Foundry orgs to resource groups. For more information about migrating toolchains, see [Migrating toolchains to a resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains).
{: tsResolve}


## Why can't I delete {{site.data.keyword.contdelivery_short}} from a Cloud Foundry org?
{: #troubleshoot-delete_cd}
{: troubleshoot}
{: support}

You cannot delete an instance of the {{site.data.keyword.contdelivery_short}} service from your Cloud Foundry org if it contains any toolchains within the same account, region, and org as the service instance.

I tried to delete {{site.data.keyword.contdelivery_short}} from a Cloud Foundry org. The deletion fails with the following error message: 
{: tsSymptoms}

`Service instance Continuous Delivery-ab: Service broker error: The Continuous Delivery service cannot be deleted because the org contains 20 toolchains. Before you can delete the service, you must delete all of the toolchains from the org. (CF-ServiceBrokerBadResponse - 10001)` 

To delete a {{site.data.keyword.contdelivery_short}} service instance from a Cloud Foundry org, you cannot have any toolchains in the same account, region, and org as the service instance.
{: tsCauses}

Locate any toolchains that are in the same account, region, and org as the {{site.data.keyword.contdelivery_short}} service instance. For each toolchain, you can either migrate the toolchain to a resource group, or delete the toolchain. For more information about migrating toolchains, see [Migrating toolchains to a resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains).
{: tsResolve}

Org-based toolchains aren't visible from the command line or the resource list. To find and either migrate or delete these toolchains, go to the [Toolchains](https://cloud.ibm.com/devops){: external} page. When you search for toolchains that are blocking the deletion of the {{site.data.keyword.contdelivery_short}} service instance, look in the account, region, and org where the service instance is located.
{: tip}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. If you have more than one account, you can click your account name in the {{site.data.keyword.cloud_notm}} console menu bar to select another account that you can access. 
1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
1. Make note of the location and the org that the {{site.data.keyword.cloud_notm}} service is contained in.
1. On the [Toolchains](https://cloud.ibm.com/devops/toolchains){: external} page, select the location and Cloud Foundry org for the {{site.data.keyword.contdelivery_short}} service instance. All of the toolchains that are associated with this service instance are displayed.
1. Either [migrate](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains) or [delete](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#deleting_a_toolchain) each of the toolchains. These actions cannot be undone.
1. After you migrate or delete all of the toolchains, delete the {{site.data.keyword.contdelivery_short}} service instance from the [Resource list](https://cloud.ibm.com/resources){: external}.

You must repeat this procedure for each {{site.data.keyword.contdelivery_short}} service instance that is associated with toolchains.
{: important}


## I tried to deploy a sample starter application to Cloud Foundry. Why did the deployment fail?
{: #troubleshoot-sampleapp_deploy}
{: troubleshoot}
{: support}

You exceeded the memory limit for your Cloud Foundry org. 

I tried to deploy a sample starter application to Cloud Foundry. The deployment fails with the following error message:
{: tsSymptoms}

`You have exceeded your organization's memory limit: app requested more memory than available` 

You exceeded the memory limit for your Cloud Foundry org. This memory limit depends on your account settings. For example, users within Lite plan accounts are limited to 256 MB of memory. You might need to upgrade your account.
{: tsCauses}

Upgrade your account:
{: tsResolve}

1. Go to the [{{site.data.keyword.cloud_notm}} dashboard](https://cloud.ibm.com/resources){: external} and stop any apps that are not in use. Running apps only are counted to determine whether the memory limit is exceeded.
1. Reduce the minimum required memory that is specified in the app's `manifest.yml` file. Make sure that your app can still start with the reduced memory.
1. [Upgrade your account](https://cloud.ibm.com/account/settings){: external}. For more information about account types and upgrading your account, see [Account types](/docs/account?topic=account-accounts).


## I removed a user from the authorized user list. Why does this user keep getting added to the list again?
{: #troubleshoot-authorized_user}
{: troubleshoot}
{: support}

Users or their accesses were not removed from all locations.
 
A user that you removed from the authorized user list was added to the list again.
{: tsSymptoms}

You didn't remove the user or their access from all of the {{site.data.keyword.contdelivery_short}} service instances, toolchains, or the {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group.
{: tsCauses}

To remove authorized users from the {{site.data.keyword.contdelivery_short}} service and prevent them from being added again:
{: tsResolve}

* Remove the user's access in IAM to all toolchains in the resource group.
* Remove the user from the authorized user list in the {{site.data.keyword.contdelivery_short}} service instance.
* Remove Developer access from all {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group.

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} instances, see [{{site.data.keyword.at_full_notm}} events](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events). For more information about managing authorized users, see [Authorized users](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users).
