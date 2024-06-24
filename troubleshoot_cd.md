---

copyright:
  years: 2015, 2024
lastupdated: "2024-06-19"

keywords: troubleshoot, toolchains

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

General problems with using {{site.data.keyword.contdelivery_full}} might include user access issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

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

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} instances, see [{{site.data.keyword.at_full_notm}} events](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events). For more information about managing authorized users, see [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users).

## I want to enable consolidated billing. Why is there no Consolidated billing tab on the Manage pane of my {{site.data.keyword.contdelivery_short}} service instance?
{: #troubleshoot-consolidate_billing-tab}
{: troubleshoot}
{: support}

The **Manage** pane of the {{site.data.keyword.contdelivery_short}} service instance does not have a **Consolidated billing** tab.
{: tsSymptoms}

The service instance does not reside in an enterprise account, and it is not using the Professional plan. Only service instances with the Professional plan that are in an enterprise account (the top most account in an enterprise hierarchy) can be used to configure consolidated billing.
{: tsCauses}

If the service instance is in an enterprise account, upgrade the instance's plan to Professional. If the service instance is not located in an enterprise account, switch to the enterprise account of the enterprise in which you want to manage consolidated billing, then create or select a {{site.data.keyword.contdelivery_short}} service instance to configure consolidated billing. For more information about consolidated billing, see [Consolidated billing](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#consolidated_billing).
{: tsResolve}

If the service instance is not in an enterprise account, it cannot be used to configure consolidated billing; however, the service instance can still participate in consolidated billing provided that the instance resides in a child account within an enterprise, and the instance is in the same region as the service instance in the enterprise account that has billing consolidation enabled.
{: tip}

## I tried to run a pipeline, why am I getting an error about Lite plan limits?
{: #troubleshoot-tekton-step-restriction}
{: troubleshoot}
{: support}

The pipeline that you started failed with an error message.
 
You exceeded the 500-step and job run limit that includes both pipeline steps for Tekton pipelines and pipeline job runs for Classic pipelines. If your pipeline has many steps within a single run, such as with the DevSecOps pipelines, you might reach this limit quickly.
{: tsSymptoms}

Delivery pipeline failures, excluding skipped step runs and Classic job runs, are counted as part of the 500-step run limit per month. All of your toolchains and all of your pipelines within those toolchains that are in the same resource group contribute to the same limit of 500 Tekton step runs per month. The same limit is used because pipeline step runs and job runs are counted at the resource group level for a specific {{site.data.keyword.contdelivery_short}} instance.
{: tsCauses}

A five-day grace period is offered the first time that you reach the 500-step run limit. If you regularly exceed the 500-step run limit within a billing period, it is recommended that you update the {{site.data.keyword.contdelivery_short}} instance for that resource group and region to use a Professional plan.
{: tsResolve}
