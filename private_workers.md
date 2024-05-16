---

copyright:
  years: 2019, 2024
lastupdated: "2024-05-16"

keywords: private workers integration, delivery pipeline, Kubernetes cluster, API key, Service ID, pool of workers

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Working with {{site.data.keyword.deliverypipeline}} Private Workers
{: #private-workers}

The {{site.data.keyword.deliverypipeline}} uses public and private workers to run pipeline jobs. By default, pipeline jobs are run by using public workers on IBM-managed public shared infrastructure. 
{: shortdesc}

In certain scenarios, your {{site.data.keyword.deliverypipeline}} might require access to internal or on-premises resources. In these situations, you can connect to and integrate a {{site.data.keyword.deliverypipeline}} Private Worker to run on your own Kubernetes infrastructure.

## Prerequisites
{: #private_workers_prereqs}

Before you set up a private worker, make sure that you have the following resources in place:

* A Kubernetes cluster. You must have a cluster to install a private worker. You can provide your own cluster or you can [set up a cluster](https://cloud.ibm.com/kubernetes/clusters){: external} from the {{site.data.keyword.containerlong_notm}}.

* Optional. A toolchain with a pipeline that contains at least one stage. You can create a toolchain by using the [{{site.data.keyword.deliverypipeline}} Private Worker tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers#configure_private_worker_integration). You can also create a toolchain by using the **Develop a Kubernetes app** toolchain template:

   1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
   1. Go to [https://cloud.ibm.com/devops/create](https://cloud.ibm.com/devops/create){: external} and select the **Develop a Kubernetes app** toolchain template.
   1. Complete the fields for the {{site.data.keyword.deliverypipeline}}.
   1. Click **Create** to create your Kubernetes app toolchain.

## Setting up a {{site.data.keyword.deliverypipeline}} Private Worker
{: #set_up_private_worker}

Toolchains provide an integrated set of tools to build, deploy, and manage your apps. Tool integrations are the building blocks of a toolchain. A pipeline that is contained within a toolchain that has one or more private worker integrations has extra options available. For Classic pipelines, these options are available on the **Workers** tab of the Stage Configuration page. For Tekton pipelines, these options are available within the settings that are specified on the **Worker** page.

For Tekton pipelines, you can also specify one worker per trigger, which overrides the worker that is configured at the pipeline level on the **Worker** page.
{: tip}

Complete the following steps to set up a private worker:

1. Configure the {{site.data.keyword.deliverypipeline}} Private Worker tool integration for your toolchain.
1. Configure your Kubernetes cluster with a private worker.
1. Use the private worker in your pipeline.

### Configuring the {{site.data.keyword.deliverypipeline}} Private Worker tool integration by using the console
{: #configure_private_worker_integration}
{: ui}

Complete the following steps to configure the {{site.data.keyword.deliverypipeline}} Private Worker tool integration for your toolchain:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Type a name for the tool integration. This name identifies a pool of private workers in the **Workers** tab of the pipeline stage.
1. Type your service ID API key to authenticate access to the work queue where one or more private workers can look for work. If you don't have a service ID API key, click **Create** to generate one for this private worker.
1. Click **Create Integration**.
1. From your toolchain's Overview page, on the **Delivery pipelines** card, click **{{site.data.keyword.deliverypipeline}} Private Worker**. A list of all of the workers that are registered by using an API key that is associated with this service ID is displayed.

The list of workers is empty until you use {{site.data.keyword.deliverypipeline}} private workers for the first time. 
{: tip}

For more information about the {{site.data.keyword.deliverypipeline}} Private Worker tool integration, see [Configuring {{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-privateworker).

### Configuring the {{site.data.keyword.deliverypipeline}} Private Worker tool integration with the API
{: #configure_private_worker_integration_api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/resource-controller#authentication){: external}.
1. [Determine the region and ID of the toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=api#viewing-toolchain-api) to which you want to add the {{site.data.keyword.deliverypipeline}} tool integration.
1. Add the {{site.data.keyword.deliverypipeline}} Private Worker tool integration to the toolchain.

   ```curl
   curl -X POST \
     https://api.{region}.devops.cloud.ibm.com/toolchain/v2/toolchains/{toolchain_id}/tools \
     -H 'Authorization: Bearer {token}' \
     -H 'Accept: application/json` \
     -H 'Content-Type: application/json' \
       -d '{
       "tool_type_id": "private_worker",
       "parameters": {
         "name":"{tool_integration_name}", "workerQueueCredentials":"{sid_apikey}"
         }
     }'
   ```
   {: pre}

The following table lists and describes each of the variables that are used in the previous step.   
    
| Variable | Description |
|:---------|:------------|
| `{region}` | The region in which the toolchain resides, for example, `us-south`. |
| `{tool_integration_name}` | A name for your tool integration, for example, `dev-worker`.|
| `{toolchain_id}` | The ID of the toolchain to which to add the tool integration. |
| `{token}` | A valid IAM bearer token. |
| `{sid_apikey}` | A service ID API key that is used by the private worker to authenticate with the work queue. |
{: caption="Table 1. Variables for adding the {{site.data.keyword.deliverypipeline}} Private Worker tool integration with the API" caption-side="top"}

### Configuring the {{site.data.keyword.deliverypipeline}} Private Worker tool integration with Terraform
{: #configure_private_worker_integration_terraform}
{: terraform}

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
1. Create a Terraform configuration file that is named `main.tf`. In this file, add the configuration to create a pipeline by using the HashiCorp Configuration Language. For more information about using this configuration language, see the [Terraform documentation](https://developer.hashicorp.com/terraform/language){: external}.

   A private worker must belong to a toolchain. You can also create toolchains by [using Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=terraform).
   {: important}
   
   The following example creates a toolchain and a private worker by using the specified Terraform resources.
  
   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_cd_toolchain" "my_toolchain" {
     name              = "terraform_toolchain"
     resource_group_id = data.ibm_resource_group.group.id
   }

   resource "ibm_cd_toolchain_tool_privateworker" "my_private_worker" {
     parameters {
        name = "terraform-private-worker"
        worker_queue_credentials = "{my_sid_apikey}"
     }
     toolchain_id = ibm_cd_toolchain.my_toolchain.id
   }
   ```
   {: codeblock}

   For more information about `ibm_cd_toolchain_tool_privateworker`, see the argument reference details in the [Terraform Registry Documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_privateworker){: external}.
  
1. Initialize the Terraform CLI, if required.

   ```terraform
   terraform init
   ```
   {: pre}
   
1. Create a Terraform execution plan. This plan summarizes all of the actions that must run to create a toolchain with a private worker.

   ```terraform
   terraform plan
   ```
   {: pre}

1. Apply the Terraform execution plan. Terraform takes all of the required actions to create the toolchain and the private worker.

   ```terraform
   terraform apply
   ```
   {: pre}

### Configuring your Kubernetes cluster
{: #configure_kubernetes_cluster}

Configure your Kubernetes cluster with a private worker:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the **{{site.data.keyword.deliverypipeline}} Private Worker** tool integration that you want to configure.
1. Click **Getting Started** and then follow the steps to install and register a private worker on your Kubernetes cluster.

### Using the {{site.data.keyword.deliverypipeline}} Private Worker in your pipeline
{: #use_private_worker_pipeline}

Complete the following steps to use the private worker in your pipeline:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the pipeline that you want to use the private worker with.
1. If you are using a Classic pipeline, on the Pipeline page, on the stage, click the **Stage Configuration** icon. Then, click **Configure Stage** and click the **Workers** tab.
1. If you are using a Tekton pipeline, from the trigger for which you want to specify a worker, select the Workers page. 
1. Select the private worker that you want to use in your pipeline. 

   By default, pipeline jobs and pipeline runs are run by using a pool of IBM-managed shared workers in the region where the pipeline is defined.
   {: tip}
 
1. Click **Save**.
1. You can manually run your Classic pipeline stage or Tekton pipeline, or you can wait for a trigger to start the pipeline run. The pipeline run is completed by using the specified private worker on the associated Kubernetes cluster. You can view the log file output for the jobs or the Run Details page in Tekton pipelines to determine which worker was used.  

### Verifying the {{site.data.keyword.deliverypipeline}} Private Worker output
{: #pw_verify_output}

If you are assigned the Toolchain Editor role, you can view the pipeline execution logs in the Stage History page of the pipeline.

If you are assigned the Toolchain Administrator role, or you have worker cluster access, you can also verify the Kubernetes resources in the installation, by way of the kubectl CLI. 

|Action |Command	|
|:----------|:------------------------------|
| View the list of namespaces in the cluster		|`$ kubectl get ns` (while the pipeline is running). At least one namespace, prefixed with `pw-` is returned during the pipeline job execution. For example, `pw-f0fb3cdb-5173-4785-ae92-bb05268e041e`. 		|
|View the pod that is running the pipeline job		|`$ kubectl get pods -n pw-f0fb3cdb-5173-4785-ae92-bb05268e041e`   |
|Start a bash session within a pod that is named `pw-f0fb3cdb-5173-4785-ae92-bb05268e041e`		|`kubectl -n pw-f0fb3cdb-5173-4785-ae92-bb05268e041e exec -it job-pod-e56e78 bash`		|
{: caption="Table 2. Private Worker output" caption-side="top"}


## Modifying the {{site.data.keyword.deliverypipeline}} Private Worker tool integration credentials
{: #modify_private_worker}

After you set up your private worker, you can update the credentials that are used for the tool integration. You might want to change these credentials if they are deleted, expired, or compromised. You can update the credentials by creating a new service ID or by updating the API key.

### Creating a service ID
{: #create_service_id}

A service ID identifies a service or an application in the same way that a user ID identifies a user. You can use a service ID to enable an application outside of {{site.data.keyword.cloud}} to access your {{site.data.keyword.cloud}} service. For more information about service IDs, see [Creating and working with service IDs](/docs/account?topic=account-serviceids).

Complete the following steps to create a service ID:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the private workers tool integration that you want to modify, click the menu, and then click **Configure** to access the configuration options.
1. Click **Create**.
1. Enter a name and description for the service ID.
1. Click **Save Integration**.
1. On the DevOps dashboard, on the **Toolchains** page, click a toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to specify new user credentials for.
1. Click **Getting Started**, and complete steps 2 and 3 to register and verify the private worker on your cluster.

### Updating the API key
{: #update_api_key}

An API key is a unique code that is passed to an API to identify the application or user that is calling it. To prevent malicious use of an API, you can use API keys to track and control how that API is used. For more information about API keys, see [Understanding API keys](/docs/account?topic=account-manapikey).

Complete the following steps to update the API key for use with the {{site.data.keyword.deliverypipeline}} Private Worker tool integration:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, go to the {{site.data.keyword.deliverypipeline}} Private Worker that you want to modify, click the menu, and then click **Configure** to access the configuration options.
1. Specify your new API key. It is recommended that you do not use the API key directly. Instead, use a Secrets Manager to store the API key and add a reference to that stored key in your private worker configuration.
1. Click **Save Integration**.

You can revoke access to a private worker by deleting the corresponding API key. Due to caching policies and invalidation, it might take up to 60 minutes for a deleted API key to prevent jobs from running. For more information about deleting an API key, see [Deleting an API key for a service ID](/docs/account?topic=account-serviceidapikeys&interface=ui#delete_service_key).
{: tip}

## Deleting a {{site.data.keyword.deliverypipeline}} Private Worker
{: #delete_private_worker}

Complete the following steps to delete a private worker:

1. Delete the private worker from the pool of workers.
1. Delete the private worker from your Kubernetes cluster.

### Deleting a {{site.data.keyword.deliverypipeline}} Private Worker from the pool of workers
{: #delete_from_pool}

Complete the following steps to delete the private worker from the pool of workers:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to configure.
1. Click **Overview**.
1. Click the menu for the private worker that you want to delete to access the configuration options.
1. Click **Remove** and then click **Confirm**.  

If you delete all of the private workers from a pool of workers, subsequent Classic pipelines stage runs fail and the `No workers currently registered` message is displayed in the Stage History. For Tekton pipelines, subsequent stage run requests are placed in a queue and do not start to run until a worker is available in the selected worker pool.
{: important}

Although deleting a private worker tool integration from a toolchain prevents that toolchain from using the pool of workers, other toolchains might still use the worker pool. You can delete a pool of workers from all toolchains by deleting the service ID that is associated with the {{site.data.keyword.deliverypipeline}} Private Worker tool integration.
{: tip}

### Deleting a {{site.data.keyword.deliverypipeline}} Private Worker from your Kubernetes cluster
{: #delete_from_cluster}

Complete the following steps in the console to delete the private worker from your cluster:

1. Click the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to configure.
1. Click **Getting Started** and follow the steps to delete the private worker from your cluster.


Run the following command to delete the private worker from your cluster by using the CLI:

```text
kubectl delete --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/install/worker?serviceId={SERVICE_ID}&apikey={APIKEY}&name={WORKER_NAME}"
```

## Deleting the {{site.data.keyword.deliverypipeline}} Private Worker tool integration by using the console
{: #delete_private_workers_integration}
{: ui}

If you delete the {{site.data.keyword.deliverypipeline}} Private Worker tool integration from your toolchain, the deletion cannot be undone.
{: important}

Complete the following steps to delete a {{site.data.keyword.deliverypipeline}} Private Worker tool integration:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the {{site.data.keyword.deliverypipeline}} Private Worker tool integration that you want to delete, and then click the menu to access the configuration options.
1. To delete the tool integration from your toolchain, click **Delete**.
1. Confirm by clicking **Delete**. The {{site.data.keyword.deliverypipeline}} Private Worker tool integration is removed from the toolchain and is no longer available in the **Workers** tab in the delivery pipeline Stage Configuration page.

If you delete the {{site.data.keyword.deliverypipeline}} Private Worker tool integration from a toolchain and the private worker is configured for a pipeline stage, it is still listed in the **Workers** tab of the Stage Configuration page. However, the private worker is disabled and labeled REMOVED. You must select a different private worker (if one exists) or use a public worker instead.
{: tip}

## Deleting the {{site.data.keyword.deliverypipeline}} Private Worker tool integration with the API
{: #delete_private_workers_integration_api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/resource-controller#authentication){: external}.
1. [Determine the region and ID of the toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=api#viewing-toolchain-api) to which you want to add the {{site.data.keyword.deliverypipeline}} tool integration.
1. Remove the {{site.data.keyword.deliverypipeline}} Private Worker tool integration from the toolchain.

   ```curl
   curl -X DELETE \
     https://api.{region}.devops.cloud.ibm.com/toolchain/v2/toolchains/{toolchain_id}/tools/{worker_id} \
     -H 'Authorization: Bearer {token}'
   ```
   {: pre}

The following table lists and describes each of the variables that are used in the previous step.   
    
| Variable | Description |
|:---------|:------------|
| `{region}` | The region in which the toolchain resides, for example, `us-south`. |
| `{worker_id}` | The ID of the private worker tool to delete.|
| `{toolchain_id}` | The ID of the toolchain to which to add the tool integration. |
| `{token}` | A valid IAM bearer token. |
{: caption="Table 3. Variables for deleting the {{site.data.keyword.deliverypipeline}} Private Worker tool integration with the API" caption-side="top"}

## Deleting the {{site.data.keyword.deliverypipeline}} Private Worker tool integration with Terraform
{: #delete_private_workers_integration_terraform}
{: terraform}

1. Locate the Terraform file (for example, `main.tf`) that contains the `resource` block for the existing pipeline.

   The `resource` in the following example describes an existing pipeline.

   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_cd_toolchain" "my_toolchain" {
     name              = "terraform_toolchain"
     resource_group_id = data.ibm_resource_group.group.id
   }

   resource "ibm_cd_toolchain_tool_privateworker" "my_private_worker" {
     parameters {
        name = "terraform-private-worker"
        worker_queue_credentials = "{my_sid_apikey}"
     }
     toolchain_id = ibm_cd_toolchain.my_toolchain.id
   }
   ```
   {: codeblock}

1. Remove the `ibm_cd_toolchain_privateworker` `resource` block from your terraform file.
1. Initialize the Terraform CLI, if required.

   ```terraform
   terraform init
   ```
   {: pre}
   
1. Create a Terraform execution plan. This plan summarizes all of the actions that must run to create a toolchain with a private worker.

   ```terraform
   terraform plan
   ```
   {: pre}

1. Apply the Terraform execution plan. Terraform takes all of the required actions to remove the private worker from your toolchain.

   ```terraform
   terraform apply
   ```
   {: pre}

Because the private worker agent might be used in other toolchains, it remains on your clusters until you delete it.
{: tip}

## Viewing the {{site.data.keyword.deliverypipeline}} Private Worker status
{: #status_private_workers}
 
You can view the private worker status on a cluster to verify that the private worker is registered, and that it uses a valid API key. Private worker registration and API key assignment is set up during the initial private worker registration. These settings allow the private worker to communicate with the {{site.data.keyword.contdelivery_full}} framework and be considered Active.

Complete the following steps to view the private worker status on the cluster where it is installed:

1. Log in as an authorized user to the cluster that hosts the worker.
1. Run the following command to list all of the agents that are registered on the cluster:
 
   ```text
   kubectl get workeragents
   ```

   The following information is listed for each agent:
   
   * **Name**: The name that is registered for this worker.
   * **ServiceID**: The `serviceId` of this worker.
   * **Agent**: Indicates whether the worker agent is operating correctly on the cluster by specifying `OK`, or displaying an error message.
   * **Registered**: The registration state of the worker, such as `Succeeded` or `Unregistered`.
   * **Version**: The version of this worker for the current version that is used by the framework, such as `OK`, `Outdated`, or `Unsupported`.
   * **Auth**: The validity of the API key that is used by the worker, such as `OK` or `Error`.
   * **Constrained**: Indicates whether any cluster issues exist that affect the worker by specifying `OK`, or displaying an error message.
   * **Paused**: Indicates whether the agent is actively searching for new tasks by specifying `true` or `false`.

To verify the overall status of a registered private worker pool, check the Overview page of the {{site.data.keyword.deliverypipeline}} private worker from the toolchain where it is used.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. On the **Delivery pipelines** card, click the private workers tool integration for which you want to view a list of all of the registered workers. This worker pool contains one or more private workers that are installed on different clusters, but share a `ServiceId`. When work is assigned to a private worker pool, any of the private workers that are listed in the pool are eligible to run the workload.

   The following information is provided for each worker that is registered in this pool:

   * **Name**: The name of the registered worker.
   * **Status**: The current status of the worker.
   * **Version**: The current version of the worker. If the current version is out of date, a notification is displayed.
   * **Tekton Version**: The Tekton release version.
   * **Cluster**: The name of the cluster that the worker is registered on, if available.
   * **Last Active**: The last time that the agent reported in.

   Private workers can have one of the following statuses:
 
   * **active**: The private worker is operating normally.
   * **inactive**: The private worker is offline. Check your cluster. You might need to register the private worker again.
   * **unsupported**: The private worker version in use is no longer supported. The private worker cannot run and you must update to the latest version.

## Updating a {{site.data.keyword.deliverypipeline}} Private Worker
{: #update_private_workers}

Complete the following steps to update a private worker to use the latest version:
 
 1. Log in as an authorized user to the cluster that hosts the worker.
 2. Run the following command:
 
   ```text
   kubectl apply --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/update"
   ```

## {{site.data.keyword.deliverypipeline}} Private Worker images 
{: #private-workers-images}

The private worker installation script pulls required images from the global {{site.data.keyword.registrylong}}. It pulls the most recent images of pipeline private workers and respective Tekton framework images that include fixes for any vulnerability found. 

The image URL for the pipeline private worker is `icr.io/continuous-delivery/pipeline/pipeline-private-worker:<agent version>`.

| Pipeline private worker image version | {{site.data.keyword.registrylong}} version | Known vulnerabilities
|:-----------------|:-----------------|:-----------------|
| 0.17.7 | `icr.io/continuous-delivery/pipeline/pipeline-private-worker:0.17.7` | - |
{: caption="Table 4. Private Worker images" caption-side="top"}

The private worker installation also pulls the following supporting open source images to the cluster:

```text
icr.io/continuous-delivery/pipeline/tekton/controller
icr.io/continuous-delivery/pipeline/tekton/entrypoint
icr.io/continuous-delivery/pipeline/tekton/nop
icr.io/continuous-delivery/pipeline/tekton/sidecarlogresults
icr.io/continuous-delivery/pipeline/tekton/events
icr.io/continuous-delivery/pipeline/tekton/workingdirinit
icr.io/continuous-delivery/pipeline/tekton/powershell
icr.io/continuous-delivery/pipeline/tekton/resolvers
icr.io/continuous-delivery/pipeline/tekton/webhook
```

The private worker agent also uses these internal images:

```text
icr.io/continuous-delivery/pipeline/pipeline-private-worker-util
icr.io/continuous-delivery/pipeline/tekton/kubectl-jq
icr.io/continuous-delivery/pipeline/tekton/ubi
icr.io/continuous-delivery/pipeline/tekton/base
```

### Support for previous {{site.data.keyword.deliverypipeline}} Private Worker images 
{: #previous-update_private_workers}

To take advantage of the current features and fixes, and to maintain full compliance, it is recommended that you keep your private worker images up to date.

For each subsequent release of a private worker image, the version number is updated.

* Agent changes result in a minor version increment, for example version 14.10 changes to version 14.11.
* A new Tekton framework change results in a major version increment, for example version 14.11 changes to version 15.0.

{{site.data.keyword.contdelivery_full}} supports the `n-1` major version of the current private worker image. For example, if the current image is version 14.x, previous version 13.x images are also allowed to run. After the major version of the pipeline worker image is incremented to 15.x, version 14.x images are allowed, but any version 13.x or earlier images are considered outdated.

