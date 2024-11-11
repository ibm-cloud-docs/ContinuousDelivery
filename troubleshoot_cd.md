---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-31"

keywords: troubleshoot, toolchains

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

General problems with using {{site.data.keyword.contdelivery_full}} might include user access issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

## Why are users added back to the authorized user list after I remove them? 
{: #troubleshoot-authorized_user}
{: troubleshoot}
{: support}

Users or their accesses were not removed from all locations.
 
A user that you removed from the authorized user list was added to the list again.
{: tsSymptoms}

You didn't remove the user or their access from all of the {{site.data.keyword.contdelivery_short}} instances, toolchains, or the {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group.
{: tsCauses}

To remove authorized users and prevent them from being added again, complete the following steps:
{: tsResolve}

* Remove the user's access in IAM to all toolchains in the resource group.
* Remove the user from the authorized user list in the {{site.data.keyword.contdelivery_short}} instance.
* Remove Developer access from all {{site.data.keyword.gitrepos}} repos that are attached to all of the toolchains in the resource group.

You can maintain an activity log related to authorized users. For more information, see [{{site.data.keyword.atracker_full_notm}} events](/docs/ContinuousDelivery?topic=ContinuousDelivery-at_events) and [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users).

## Why do I not have the option to enable consolidate billing for my {{site.data.keyword.contdelivery_short}} instance?
{: #troubleshoot-consolidate_billing-tab}
{: troubleshoot}
{: support}

The Consolidated billing tab isn't included in the **Manage** options for your {{site.data.keyword.contdelivery_short}} instance.
{: tsSymptoms}

The instance is not included in an enterprise account, and it is not using the Professional plan. You can enable consolidated billing only for instances with the Professional plan in an enterprise account.
{: tsCauses}

If the instance is in an enterprise account, upgrade the instance to the Professional plan. If the instance is not included in an enterprise account, complete the following steps:

1. Switch to the enterprise account of the enterprise in which you want to manage consolidated billing. 
1. Create or select an instance to configure consolidated billing. For more information, see [Consolidated billing](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#consolidated_billing).
{: tsResolve}

Even though you can't enable consolidated billing for instances that aren't included in an enterprise account, you can still take advantage of consolidate billing as long as the following conditions are true:

* The instance is included in a child account of the enterprise. 
* The instance is in the same region as the instance in which consolidated billing is enabled at the enterprise account level.

## Why do I get an error about Lite plan limits when I try to run a pipeline?
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
