---

copyright:
  years: 2020, 2022

lastupdated: "2022-06-20"

keywords: ibmcloud, resource, service instance, restore, CLI tool, IBM Cloud

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
{:deprecated: .deprecated}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}

# Deleting a {{site.data.keyword.contdelivery_short}} service instance
{: #delete_cd_service}
{: help} 
{: support}

You can delete resource group-based and Cloud Foundry organization (org)-based {{site.data.keyword.contdelivery_short}} service instances.
{: shortdesc}

To delete a {{site.data.keyword.contdelivery_short}} service instance, you must have either the Administrator or Editor user permissions.

Deleting an instance of the {{site.data.keyword.contdelivery_short}} service impacts your ability to use tool integrations within toolchains that are contained in the same region and resource group as the deleted service instance. For more information about this limitation, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).
{: important}

## Deleting a resource group-based service instance
{: #deleting_cd_rg}

You can delete a resource group-based {{site.data.keyword.contdelivery_short}} service instance by using either the {{site.data.keyword.cloud_notm}} console or the {{site.data.keyword.cloud_notm}} CLI.

### Deleting a service instance from the console
{: #deleting_rg_console}
{: ui}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
1. In the **Services** section, locate the active {{site.data.keyword.contdelivery_short}} service instance.
1. From the {{site.data.keyword.contdelivery_short}} service instance's **Actions** ![Overflow icon](images/overflow-icon-2.svg) menu, click **Delete**.
1. Click **Delete** to confirm that you want to delete the {{site.data.keyword.contdelivery_short}} service.

### Deleting a service instance by using the CLI
{: #deleting_rg_cli}
{: cli}

* To view service instances, run the [`ibmcloud resource service-instances`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instances) command:

```text
~$ ibmcloud resource service-instances
``` 
{: codeblock}

* To delete the service instance, run the [`ibmcloud resource service-instance-delete`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command:
 
```text
~$ ibmcloud resource service-instance-delete <name or id of service instance>
```
{: codeblock}

### Restoring a deleted service instance
{: #restoring_cd_instance}

After you delete an instance of the {{site.data.keyword.contdelivery_short}} service, you can restore the deleted service instance within the data retention period of seven days. After the seven-day period expires, the service instance is permanently deleted. 

To view which service instances are available for restoration, use the [`ibmcloud resource reclamations`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamations) command. To restore a deleted service, use the [`ibmcloud resource reclamation-restore`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation_restore) command. If you try to restore a deleted service and an active {{site.data.keyword.contdelivery_short}} service instance exists, the restoration is blocked. To view the details for a resource reclamation, use the [`ibmcloud resource reclamation`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation) command, with the `--output JSON` option.

You can have one active instance of {{site.data.keyword.contdelivery_short}} only in a region and resource group. After you delete an instance of the {{site.data.keyword.contdelivery_short}} service from a region and resource group, you can use one of the following options to create a service instance again:

* Restore the deleted service instance within the data retention period of seven days.
* Permanently remove the deleted service instance by using the [`ibmcloud resource reclamation-delete`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation_delete) command, and then [create a {{site.data.keyword.contdelivery_short}} service](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service) instance again.


## Deleting a Cloud Foundry org-based service instance
{: #deleting_cd_cf}

Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances and toolchains are deprecated. You can no longer create Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances. As of 14 January 2022, you cannot create new toolchains within Cloud Foundry orgs. You can create new toolchains in resource groups. On 28 February 2022, all toolchains within Cloud Foundry orgs that did not contain a Professional plan instance of the {{site.data.keyword.contdelivery_short}} service were deleted. As of 15 August 2022, all toolchains within Cloud Foundry orgs that contain a Professional plan instance of the {{site.data.keyword.contdelivery_short}} service will be deleted. Before this date, you can use the [toolchain migration wizard](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains) to migrate existing toolchains from Cloud Foundry orgs to resource groups.
{: deprecated}

To prevent accidental deletion of existing Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances, you cannot delete any instances that contain toolchains within the org that they reside in. After you delete a Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instance, you cannot restore or re-create it. Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances do not have a reclamation period.
{: important}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. Delete all of the toolchains in the Cloud Foundry org that contains the {{site.data.keyword.contdelivery_short}} service instance:

   a. Go to the [Toolchains](https://cloud.ibm.com/devops/toolchains){: external} page for your {{site.data.keyword.cloud_notm}} account.
  
   b. Select the Cloud Foundry org and the location that you want to delete the service instance from.
  
   c. Complete the following steps for each toolchain in the Cloud Foundry org:
  
     *  From the toolchain's **Actions** ![Overflow icon](images/overflow-icon-2.svg) menu, click **Delete**.
    
     *  Type the name of the toolchain that you want to delete.
    
     *  Click **Delete** to confirm that you want to delete the toolchain.
     
1. Delete the {{site.data.keyword.contdelivery_short}} service instance:

   a. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
   
   b. In the **Cloud Foundry services** section, locate the active {{site.data.keyword.contdelivery_short}} service instance.
   
   c. From the {{site.data.keyword.contdelivery_short}} service instance's **Actions** ![Overflow icon](images/overflow-icon-2.svg) menu, click **Delete**.
   
   d. Type the name of the service instance that you want to delete.
   
   e. Click **Delete** to confirm that you want to delete the {{site.data.keyword.contdelivery_short}} service.
