---

copyright:
  years: 2019
lastupdated: "2019-08-12"

keywords: IBM Cloud Continuous Delivery, private workers integration

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


# Working with {{site.data.keyword.deliverypipeline}} Private Workers
{: #private-workers}

The {{site.data.keyword.deliverypipeline}} uses public and private workers to run pipeline jobs. By default, pipeline jobs are run by using public workers on IBM-managed public shared infrastructure. 
{: shortdesc}

In certain scenarios, your {{site.data.keyword.deliverypipeline}} might require access to internal or on-premises resources. In these situations, you can connect to and integrate a {{site.data.keyword.deliverypipeline}} Private Worker to run on your own Kubernetes infrastructure.

## Prerequisites
{: #private_workers_prereqs}

Before you set up a private worker, make sure that you have the following resources in place:

* A Kubernetes cluster. You must have a cluster to install a private worker. You can provide your own cluster or you can [set up a cluster](https://cloud.ibm.com/kubernetes/clusters){:external} from the {{site.data.keyword.containerlong_notm}}.

* Optional. A toolchain with a pipeline that contains at least one stage. You can also create a toolchain by using the [{{site.data.keyword.deliverypipeline}} Private Worker tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers#configure_private_worker_integration).

## Setting up a {{site.data.keyword.deliverypipeline}} Private Worker
{: #set_up_private_worker}

Complete the following steps to set up a private worker:

1. Configure the {{site.data.keyword.deliverypipeline}} Private Worker tool integration for your toolchain.
2. Configure your Kubernetes cluster with a private worker.
3. Use the private worker in your pipeline.

### Configuring the {{site.data.keyword.deliverypipeline}} Private Worker tool integration
{: #configure_private_worker_integration}

Complete the following steps to configure the {{site.data.keyword.deliverypipeline}} Private Worker tool integration for your toolchain:

1. To add the tool integration to your toolchain, on the DevOps dashboard, on the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View Toolchain**.

 a. Click **Add a Tool**.

 b. In the Tool Integrations section, click **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Type a name for the tool integration. This name identifies a pool of private workers in the **Workers** tab of the pipeline stage.
1. Type your Service ID API key to authenticate access to the work queue where one or more private workers can look for work. If you don't have a Service ID API key, click **Create** to generate one for this private worker.
1. Click **Create Integration**.
1. From your toolchain, click **{{site.data.keyword.deliverypipeline}} Private Worker** to view a list of all of the workers that are registered by using an API key that is associated with this Service ID.

The list of workers is empty until you use {{site.data.keyword.deliverypipeline}} private workers for the first time. 
{: tip}

For more information about the **{{site.data.keyword.deliverypipeline}} Private Worker** tool integration, see [Configuring {{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker).

### Configuring your Kubernetes cluster
{: #configure_kubernetes_cluster}

Configure your Kubernetes cluster with a private worker:

1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. Click the card for the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to configure.
1. Click  **Getting Started** and then follow the steps to install and register a private worker on your Kubernetes cluster.

### Using the {{site.data.keyword.deliverypipeline}} Private Worker in your pipeline
{: #use_private_worker_pipeline}

Complete the following steps to use the private worker in your pipeline:

1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. Click the card for the pipeline that you want to use the private worker with.
1. On the Pipeline page, on the stage, click the **Stage Configuration** icon and then click **Configure Stage**.
1. Click the **Workers** tab.
1. Select the private worker that you want to use in your pipeline. 

 By default, jobs in a pipeline stage are run by using a pool of IBM-managed shared workers in the region where the pipeline is defined.
 {: tip}
 
1. Click **Save**.
1. You can manually run your stage or wait for a trigger to run the jobs on the stage by using the specified private worker on the associated Kubernetes cluster. You can view the log file output for the jobs to determine which worker was used.  


## Modifying the {{site.data.keyword.deliverypipeline}} Private Worker tool integration credentials
{: #modify_private_worker}

After you set up your private worker, you can update the credentials that are used for the tool integration. You might want to change these credentials if they are deleted, expired, or compromised. You can update the credentials by creating a new Service ID or by updating the API key.

### Creating a Service ID
{: #create_service_id}

Complete the following steps to create a ServiceID:

1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. On the card for the private workers tool integration that you want to modify, click the menu, and then click **Configure** to access the configuration options.
1. Click **Create**.
1. Enter a name and description for the Service ID.
1. Click **Save Integration**.
1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. Click the card for the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to specify new user credentials for.
1. Click **Getting Started**, and complete steps 2 and 3 to register and verify the private worker on your cluster.

### Updating the API key
{: #update_api_key}

Complete the following steps to update the API key for use with the {{site.data.keyword.deliverypipeline}} Private Worker tool integration:

1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. On the card for the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to modify, click the menu, and then click **Configure** to access the configuration options.
1. Specify your new API key. 
1. Click **Save Integration**.

## Deleting a {{site.data.keyword.deliverypipeline}} Private Worker
{: #delete_private_worker}

Complete the following steps to delete a private worker:

1. Delete the private worker from the pool of workers.
1. Delete the private worker from your Kubernetes cluster.

### Deleting a {{site.data.keyword.deliverypipeline}} Private Worker from the pool of workers

Complete the following steps to delete the private worker from the pool of workers:

1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. Click the card for the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to configure.
1. Click **Overview**.
1. Click the menu for the private worker that you want to delete to access the configuration options.
1. Click **Remove** and then click **Confirm**.  

If you delete all of the private workers from a pool of workers, subsequent stage runs fail and the `No workers currently registered` message is displayed in the Stage History.
{: tip}


### Deleting a {{site.data.keyword.deliverypipeline}} Private Worker from your Kubernetes cluster

Complete the following steps to delete the private worker from your cluster:

1. Click the card for the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to configure.
1. Click **Getting Started** and follow the steps to delete the private worker from your cluster.

## Deleting the {{site.data.keyword.deliverypipeline}} Private Worker tool integration
{: #delete_private_workers_tool_integration}

If you delete the {{site.data.keyword.deliverypipeline}} Private Worker tool integration from your toolchain, the deletion cannot be undone.
{: important}

Complete the following steps to delete a {{site.data.keyword.deliverypipeline}} Private Worker tool integration:

1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. On the card for the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to delete, click the menu to access the configuration options.
1. To delete the tool integration from your toolchain, click **Delete**.
1. Confirm by clicking **Delete**. The {{site.data.keyword.deliverypipeline}} Private Worker tool integration is removed from the toolchain and is no longer available in the **Workers** tab in the delivery pipeline Stage Configuration page.

If you delete the {{site.data.keyword.deliverypipeline}} Private Worker tool integration from a toolchain and the private worker is configured for a pipeline stage, it is still listed in the **Workers** tab of the Stage Configuration page. However, the private worker is disabled and labeled REMOVED. You must select a different private worker (if one exists) or use a public worker instead.
{: tip}
