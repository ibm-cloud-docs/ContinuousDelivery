---

copyright:
  years: 2015, 2025
lastupdated: "2025-04-29"

keywords: tool integrations, cos bucket tool integration

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring Cloud {{site.data.keyword.cos_short}}
{: #cos_integration}

{{site.data.keyword.cos_full}} is used to securely store large volumes of data, ensuring compliance and optimizing cost.
You can integrate {{site.data.keyword.cos_full_notm}} Bucket to store evidence.
You can also use this tool integration for specific storage requirements of your toolchains.

## Prerequisites
{: #cos_prerequisites}

You must make sure that you complete the following steps before you integrate your toolchain with a Cloud {{site.data.keyword.cos_short}} Bucket.

1. You must have an instance of Cloud {{site.data.keyword.cos_short}}, a bucket instance to add the Cloud {{site.data.keyword.cos_short}} Bucket tool to your toolchain.

1. To authenticate your Cloud {{site.data.keyword.cos_short}} Bucket, you can use an API Key or an HMAC Key. You must choose the suitable [authentication method](/docs/cloud-object-storage?topic=cloud-object-storage-service-credentials), depending on your requirement.

1. You can choose to [create service credentials](/docs/cloud-object-storage?topic=cloud-object-storage-service-credentials) for the Cloud {{site.data.keyword.secrets-manager_short}} instance under the **Service credentials** tab.

1. You can create {{site.data.keyword.secrets-manager_short}} instance to store service credentials created earlier. [Integrate the Secret Manager tool](/docs/devsecops?topic=devsecops-cd-devsecops-toolchains-secrets) with your toolchain and point the {{site.data.keyword.secrets-manager_short}} instance and the secrets that are created before to this integration.

To store and access evidence or other artifacts securely for your toolchain, configure Cloud {{site.data.keyword.cos_short}} Bucket:

1. If you are configuring this tool integration as you are creating the toolchain, and a Cloud {{site.data.keyword.cos_short}} Bucket exists, within the template that you are configuring, click the Cloud {{site.data.keyword.cos_short}} Bucket tab. Alternatively, in the **More tools** section, click Cloud {{site.data.keyword.cos_short}} Bucket.

1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, clicks the ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

   a. Click **Add**.

   b. In the Tool Integrations section, click **Cloud {{site.data.keyword.cos_short}} Bucket**.

1. Type a **Name** to identify the Cloud {{site.data.keyword.cos_short}} Bucket integration.

1. Select the **Authentication type** according to your requirements. If you are using **API Key** for authentication, provide **Cloud Object Storage API Key** and the **Cloud Object Storage instance**. If you are using an **HMAC** for authentication, provide an **Access Key ID** and **Secret Access Key** for the HMAC. You can create service credentials for both of these authentication methods for your Cloud {{site.data.keyword.cos_short}} instance. You can refer to these values directly as literals. However it is recommended to use {{site.data.keyword.secrets-manager_short}} integration that has these secrets that are stored. You can then select these secrets from a secret store for authentication.

1. Type **Bucket name** and **Endpoint** that is defined for the corresponding Cloud {{site.data.keyword.cos_short}} instance.
1. Click **Create Integration**.


## Configuring Cloud {{site.data.keyword.cos_short}} Bucket by using the API
{: #cos-config-parameters}

The {{site.data.keyword.cos_full_notm}} Bucket tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `cloudobjectstorage` value.
{: important}

| Parameter | Usage | Type | Description |
| --- | --- | --- | --- |
| `name` | required, updatable | String | The name used to identify this tool integration. |
| `auth_type` | required, updatable | String | The authentication type. Pass `apikey` for IBM Cloud API Key or `hmac` for HMAC (Hash Message Authentication Code).|
| `cos_api_key` | required, updatable | String | For `auth_type` as `apikey`, pass `cos_api_key` to authenticate access to the Cloud {{site.data.keyword.cos_short}} instance or `instance_crn`.|
| `instance_crn` | required, updatable | String | A reference to the existing Cloud {{site.data.keyword.cos_short}} instance.|
| `bucket_name` | required, updatable | String | The name of your Cloud {{site.data.keyword.cos_short}} bucket.|
| `hmac_access_key_id` | required, updatable | Password | HMAC Access Key defined for an HMAC Key. HMAC is identified by a combination of Access Key ID and Secret Access Key. It is associated with the Cloud {{site.data.keyword.cos_short}} instance. |
| `hmac_secret_access_key` | required, updatable | Password | Secret Access Key defined for an HMAC Key. HMAC is identified by a combination of Access Key ID and Secret Access Key. It is associated with the Cloud {{site.data.keyword.cos_short}} instance.|
| `endpoint` | required, updatable | String | Endpoint defined for Cloud {{site.data.keyword.cos_short}} instance. Options are `public`, `direct`, `private`|
 {: caption="{{site.data.keyword.cos_full_notm}} Bucket tool integration parameters" caption-side="bottom"}
