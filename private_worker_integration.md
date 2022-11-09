---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-09"

keywords: tool integrations, IBM Cloud Public, Delivery Pipeline Private Worker

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring {{site.data.keyword.deliverypipeline}} Private Worker
{: #privateworker}

{{site.data.keyword.deliverypipeline}} Private Worker connects with one or more private workers that run {{site.data.keyword.deliverypipeline}} workloads in isolation.
{: shortdesc}

Configure the {{site.data.keyword.deliverypipeline}} Private Worker tool integration to make private workers available to pipelines in a toolchain:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **{{site.data.keyword.deliverypipeline}} Private Worker**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Type a name for the tool integration. This name identifies a pool of private workers in the **Workers** tab of the pipeline stage.
1. Type your Service ID API key to authenticate access to the work queue where one or more private workers can look for work. If you don't have a Service ID API key, click **Create** to generate one for this private worker.
1. Click **Create Integration**.
1. From your toolchain, on the **Delivery pipelines** card, click the **{{site.data.keyword.deliverypipeline}} Private Worker** to view a list of all of the workers that are registered by using an API key that is associated with this Service ID.

## Configuring {{site.data.keyword.deliverypipeline}} Private Worker by using the API
{: #config-parameters}

The {{site.data.keyword.deliverypipeline}} Private Worker tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `private_worker` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| name | required, updatable | String | name | The name for this tool integration, for example, `my-private-worker` that is displayed on your toolchain. |
| workerQueueCredentials | required, updatable | Password | worker_queue_credentials | A secret from the secrets store, or a service ID API key that you create, that is used by the private worker to authenticate access to the work queue. |
| workerQueueIdentifier | optional, updatable | String | worker_queue_identifier | The service ID that is used to access the work queue. |
{: caption="Table 1. {{site.data.keyword.deliverypipeline}} Private Worker tool integration parameters" caption-side="bottom"}
