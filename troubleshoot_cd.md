---

copyright:
  years: 2015, 2023
lastupdated: "2023-06-05"

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

You can maintain an activity log related to authorized users. For more information about viewing, managing, and auditing service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} instances, see [{{site.data.keyword.at_full_notm}} events](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-at-events). For more information about managing authorized users, see [Authorized users](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users).

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
