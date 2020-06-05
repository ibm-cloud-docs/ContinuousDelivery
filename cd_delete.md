---

copyright:
  years: 2020

lastupdated: "2020-06-03"

keywords: ibmcloud, resource, service instance, restore, CLI tool, IBM Cloud

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Deleting a {{site.data.keyword.contdelivery_short}} service instance
{: #delete_cd_service}
{: help} 
{: support}

You can delete a {{site.data.keyword.contdelivery_short}} service instance by using either the {{site.data.keyword.cloud_notm}} console or the {{site.data.keyword.cloud_notm}} CLI.
{: shortdesc}

To delete a {{site.data.keyword.contdelivery_short}} service instance, you must have either the Administrator or Editor user permissions.

Deleting an instance of the {{site.data.keyword.contdelivery_short}} service impacts your ability to use tool integrations within toolchains that are contained in the same region and resource group as the deleted service instance. For more information about this limitation, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).
{: important}

## Deleting a service instance from the console
{: #deleting_cd_console}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){:external}.
1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
1. In the **Services** section, locate the active {{site.data.keyword.contdelivery_short}} service instance.
1. From the {{site.data.keyword.contdelivery_short}} service instance's **Actions** ![Overflow icon](images/overflow-icon-2.svg) menu, click **Delete**.
1. Click **Delete** to confirm that you want to delete the {{site.data.keyword.contdelivery_short}} service.

## Deleting a service instance by using the CLI
{: #deleting_cd_cli}

* To view service instances, run the [`ibmcloud resource service-instances`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instances) command:
  ```
  ~$ ibmcloud resource service-instances
  ``` 
  {: codeblock}

* To delete the service instance, run the [`ibmcloud resource service-instance-delete`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command: 
  ```
  ~$ ibmcloud resource service-instance-delete <name or id of service instance>
  ```
  {: codeblock}

## Restoring a deleted service instance
{: #restoring_cd_instance}

After you delete an instance of the {{site.data.keyword.contdelivery_short}} service, you can restore the deleted service instance within the data retention period of seven days. After the seven-day period expires, the service instance is permanently deleted. 

To view which service instances are available for restoration, use the [`ibmcloud resource reclamations`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamations) command. To restore a deleted service, use the [`ibmcloud resource reclamation-restore`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation_restore) command. If you try to restore a deleted service and an active {{site.data.keyword.contdelivery_short}} service instance exists, the restoration is blocked. To view the details for a resource reclamation, use the [`ibmcloud resource reclamation`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation) command, with the `--output JSON` option.

You can have one active instance of {{site.data.keyword.contdelivery_short}} only in a region and resource group. After you delete an instance of the {{site.data.keyword.contdelivery_short}} service from a region and resource group, you can use one of the following options to create a service instance again:

* Restore the deleted service instance within the data retention period of seven days.
* Permanently remove the deleted service instance by using the [`ibmcloud resource reclamation-delete`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation_delete) command, and then [create a {{site.data.keyword.contdelivery_short}} service](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service) instance again.
