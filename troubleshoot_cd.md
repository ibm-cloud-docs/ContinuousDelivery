---

copyright:
  years: 2015, 2022
lastupdated: "2022-09-02"

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

General problems with using {{site.data.keyword.contdelivery_full}} might include user access issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}


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
