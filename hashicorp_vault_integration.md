---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-09"

keywords: tool integrations, IBM Cloud Public, Hashicorp Vault

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}   

# Configuring HashiCorp Vault
{: #hashicorpvault}

You can configure HashiCorp Vault as a tool integration in your toolchain so that you can access and refer to securely stored secrets in a HashiCorp Vault server.
{: shortdesc}

Before you configure the HashiCorp Vault tool integration for your toolchain, you need the authentication method and associated credentials with permission to access the HashiCorp Vault server that you want to connect to. For example, if the `authentication_method` is `github`, you must know your `token` credential. You also need to know the values for the `server url`, `integration url`, and `secrets path`. If the HashiCorp Vault server is bound to a specific port, include the port number in the server url. For example, `https://192.168.0.100:8200`.
{: important}

Configure HashiCorp Vault to securely manage secrets such as API keys and secrets that are part of your toolchain or delivery pipeline:

1. If you are configuring this tool integration as you are creating the toolchain, and a HashiCorp Vault tool integration exists within the template that you are configuring, click the **HashiCorp Vault** tab. Alternatively, in the **More tools** section, click **HashiCorp Vault**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **HashiCorp Vault**.

1. Type the name that you want to display for this tool integration on the HashiCorp Vault card in your toolchain. The secret name supports characters within the `a-z`, `A-Z`, and `0-9`ranges, and the space character. Characters that are outside of these ranges are not allowed and prevent the secret from resolving. For example, `my.secret` is an invalid secret name, but `my-secret` is valid.
1. Type the URL for the HashiCorp Vault server that you want to open when you click the HashiCorp Vault card from your toolchain. Make sure that this URL is prefixed with the `http` or `https` protocol and ends with the HashiCorp Vault port number, such as `https://www.acme.com:8200`.
1. Type the URL for the HashiCorp Vault tool integration. This value can be any valid URL such as an organization-specific URL that is related to your organization's HashiCorp Vault server Web UI console or documentation.
1. Type the path to the secrets on the HashiCorp Vault server that is accessible when you use the configured authentication method and the associated authentication credentials. This value must include only the secrets path and cannot include a secrets name at the end of the secrets path. If your authentication credentials contain the relevant LIST permission within the specified secrets path, you can view the list of secrets within that path.
1. Click **Create Integration**.
1. On the Toolchain's Overview page, on the **Third-Party tools** card, click **HashiCorp Vault** to use the HashiCorp Vault Secrets Picker and Pusher components to select secrets for use within your toolchain or delivery pipeline.  

## Configuring HashiCorp Vault by using the API
{: #config-parameters}

The HashiCorp Vault tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `hashicorpvault` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| name | required, updatable | String | name | The name of this tool integration, for example `my-hashicorp-vault`, that is displayed in your toolchain. |
| server_url | required, updatable | String | server_url | The server URL for your HashiCorp Vault instance. |
| authentication_method | required, updatable | String | authentication_method | The authentication method for your HashiCorp Vault instance. |
| token | optional, updatable | Password | token | The authentication token for your HashiCorp Vault instance. |
| role_id | optional, updatable | Password | role_id | The authentication role ID for your HashiCorp Vault instance. |
| secret_id | optional, updatable | Password | secret_id | The authentication secret ID for your HashiCorp Vault instance. |
| dashboard_url | required, updatable | String | dashboard_url | The URL that you want to go to when you click the HashiCorp Vault integration tile. |
| path | required, updatable | String | path | The mount path where your secrets are stored in your HashiCorp Vault instance. |
| secret_filter | optional, updatable | String | secret_filter | A regular expression that filters the list of secret names that are returned from your HashiCorp Vault instance. |
| default_secret | optional, updatable | String | default_secret | A default secret name that is used if a list of secret names is not returned from your HashiCorp Vault instance. |
| username | optional, updatable | String | username | The authentication username for your HashiCorp Vault instance. |
| password | optional, updatable | Password | password | The authentication password for your HashiCorp Vault instance. |
{: caption="Table 1. HashiCorp Vault tool integration parameters" caption-side="bottom"}

## Learn more about HashiCorp Vault
{: #learn_hashicorp_vault}

To learn more about HashiCorp Vault, see [HashiCorp Vault](https://www.vaultproject.io/){: external}.
