---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-27"

keywords: troubleshoot, toolchains, Cloud Foundry

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Troubleshooting for {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

General problems with using {{site.data.keyword.contdelivery_full}} might include Cloud Foundry issues. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}


## Why can't I add {{site.data.keyword.contdelivery_short}} to a Cloud Foundry org?
{: troubleshoot-resource_groups}
{: troubleshoot}
{: support}

You can no longer create instances of the {{site.data.keyword.contdelivery_short}} service in Cloud Foundry orgs. 

The following message is displayed on the Toolchains page for your toolchain in a Cloud Foundry org:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

When you click **Add the service** there is no option to create {{site.data.keyword.contdelivery_short}} in a Cloud Foundry org. You can only create {{site.data.keyword.contdelivery_short}} in a resource group.

Resource groups have replaced Cloud Foundry orgs as the preferred containers for service instances. However, you can still create toolchains in Cloud Foundry orgs to support pre-existing {{site.data.keyword.contdelivery_short}} instances in Cloud Foundry orgs.
{: tsCauses}

Create your toolchain again in resource groups, and then remove the original toolchain from the Cloud Foundry org. Alternatively, you can ignore the error message until a method to migrate existing toolchains from Cloud Foundry orgs to resource groups is provided.
{: tsResolve}


## Why can't I delete {{site.data.keyword.contdelivery_short}} from a Cloud Foundry org?
{: troubleshoot-delete_cd}
{: troubleshoot}
{: support}

You cannot delete an instance of the {{site.data.keyword.contdelivery_short}} service from your Cloud Foundry org if it contains any toolchains within the same account, region, and org as the service instance.

I tried to delete {{site.data.keyword.contdelivery_short}} from a Cloud Foundry org. The deletion fails with the following error message: 
{: tsSymptoms}

`Service instance Continuous Delivery-ab: Service broker error: The Continuous Delivery service cannot be deleted because the org contains 20 toolchains. Before you can delete the service, you must delete all of the toolchains from the org. (CF-ServiceBrokerBadResponse - 10001)` 

To delete a {{site.data.keyword.contdelivery_short}} service instance from a Cloud Foundry org, you cannot have any toolchains in the same account, region, and org as the service instance.
{: tsCauses}

Locate and delete any toolchains that are in the same account, region, and org as the {{site.data.keyword.contdelivery_short}} service instance.
{: tsResolve}

Org-based toolchains aren't visible from the command line or the resource list. To find and delete these toolchains, go to the [Toolchains](https://cloud.ibm.com/devops){: external} page. When you search for toolchains that are blocking the deletion of the {{site.data.keyword.contdelivery_short}} service instance, look in the account, region, and org where the service instance is located.
{: tip}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){:external}.
1. If you have more than one account, you can click your account name in the console menu bar to select another account that you can access. 
1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
1. Make note of the location and the org that the {{site.data.keyword.cloud_notm}} service is contained in.
1. On the [Toolchains](https://cloud.ibm.com/devops/toolchains){: external} page, select the location and Cloud Foundry org for the {{site.data.keyword.contdelivery_short}} service instance. All of the toolchains that are associated with this service instance are displayed.
1. [Delete each of the toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#deleting_a_toolchain). This action cannot be undone.
1. After you delete all of the toolchains, delete the {{site.data.keyword.contdelivery_short}} service instance from the [Resource list](https://cloud.ibm.com/resources){: external}.

You must repeat this procedure for each {{site.data.keyword.contdelivery_short}} service instance that is associated with toolchains.
{: important}


## I tried to deploy a sample starter application to Cloud Foundry. Why did the deployment fail?
{: troubleshoot-sampleapp_deploy}
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
