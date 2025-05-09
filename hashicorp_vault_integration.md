---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-18"

keywords: tool integrations, IBM Cloud Public, HashiCorp Vault

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}   

# Configuring HashiCorp Vault
{: #hashicorpvault}

You can configure HashiCorp Vault as a tool integration in your toolchain so that you can access and refer to securely stored secrets in a HashiCorp Vault server.
{: shortdesc}

Before you configure the HashiCorp Vault tool integration for your toolchain, you need the authentication method and associated credentials with permission to access the HashiCorp Vault server that you want to connect to. For example, if the `authentication_method` is `github`, you must know your `token` credential. You also need to know the values for the `server url`, `integration url`, and `secrets path`. If the HashiCorp Vault server is bound to a specific port, include the port number in the server url. For example, `https://192.168.0.100:8200`.
{: important}

The HashiCorp Vault tool integration supports only secrets references by name. If you want to use secrets references by CRN, you must use a [{{site.data.keyword.secrets-manager_short}} tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager).
{: tip} 

Configure HashiCorp Vault to securely manage secrets such as API keys and secrets that are part of your toolchain or delivery pipeline:

1. If you are configuring this tool integration as you are creating the toolchain, and a HashiCorp Vault tool integration exists within the template that you are configuring, click the **HashiCorp Vault** tab. Alternatively, in the **More tools** section, click **HashiCorp Vault**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **HashiCorp Vault**.

1. Type the name that you want to display for this tool integration on the HashiCorp Vault card in your toolchain. The secret name supports characters within the `a-z`, `A-Z`, and `0-9`ranges, and the space character. Characters that are outside of these ranges are not allowed and prevent the secret from resolving. For example, `my.secret` is an invalid secret name, but `my-secret` is valid.
1. Type the URL for the HashiCorp Vault server that you want to open when you click the HashiCorp Vault card from your toolchain. Make sure that this URL is prefixed with the `http` or `https` protocol and ends with the HashiCorp Vault port number, such as `https://www.acme.com:8200`.
1. Type the URL for the HashiCorp Vault tool integration. This value can be any valid URL such as an organization-specific URL that is related to your organization's HashiCorp Vault server Web UI console or documentation.
1. Type the path to the secrets on the HashiCorp Vault server that is accessible when you use the configured authentication method and the associated authentication credentials. This value must include only the secrets path and cannot include a secrets name at the end of the secrets path. If your authentication credentials contain the relevant LIST permission within the specified secrets path, you can view the list of secrets within that path.
1. Click **Create Integration**.
1. On the Toolchain's Overview page, on the **Third-Party tools** card, click **HashiCorp Vault** to use the HashiCorp Vault Secrets Picker and Pusher components to select secrets for use within your toolchain or delivery pipeline.  

## Configuring HashiCorp Vault by using the API
{: #hashicorp-config-parameters}

The HashiCorp Vault tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `hashicorpvault` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| authentication_method | required, updatable | String | authentication_method | The authentication method for your HashiCorp Vault instance. |
| dashboard_url | required, updatable | String | dashboard_url | The URL of the HashiCorp Vault server dashboard for this tool integration. In the graphical UI, the browser goes to this dashboard when you click the HashiCorp Vault tool integration card. |
| default_secret | optional, updatable | String | default_secret | The default secret name that is used if your HashiCorp Vault instance does not return a list of secret names. |
| name | required, updatable | String | name | The name of this tool integration. Secret references include this name to identify the secrets store where the secrets reside. All of the secrets store tools that are integrated into a toolchain must have a unique name to allow secret resolution to function properly. |
| password | optional, updatable | Password | password | The authentication password for your HashiCorp Vault instance when you use the `userpass` authentication method. This parameter is ignored for other authentication methods. You can use a toolchain secret reference for this parameter. For more information about using secret references, see [Protecting your sensitive data in Continuous Delivery](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| path | required, updatable | String | path | The mount path where your secrets are stored in your HashiCorp Vault instance. |
| role_id | optional, updatable | Password | role_id | The authentication role ID for your HashiCorp Vault instance when you use the `approle` authentication method. This parameter is ignored for other authentication methods. Manage `role_id` as a secret and do not share this parameter in plain text. You can use a toolchain secret reference for this parameter. For more information about secret references, see [Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| secret_filter | optional, updatable | String | secret_filter | A regular expression to filter the list of secret names that are returned from your HashiCorp Vault instance. |
| secret_id | optional, updatable | Password | secret_id | The authentication secret ID for your HashiCorp Vault instance when you use the `approle` authentication method. This parameter is ignored for other authentication methods. You can use a toolchain secret reference for this parameter. For more information about secret references, see [Protecting your sensitive data in Continuous Delivery](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| server_url | required, updatable | String | server_url | The server URL for your HashiCorp Vault instance. |
| token | optional, updatable | Password | token | The authentication token for your HashiCorp Vault instance when you use the `github` and `token` authentication methods. This parameter is ignored for other authentication methods. You can use a toolchain secret reference for this parameter. For more information about secret references, see [Protecting your sensitive data in Continuous Delivery](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| username | optional, updatable | String | username | The authentication username for your HashiCorp Vault instance when you use the `userpass` authentication method. This parameter is ignored for other authentication methods. |
{: caption="HashiCorp Vault tool integration parameters" caption-side="bottom"}

## Learn more about HashiCorp Vault
{: #learn_hashicorp_vault}

To learn more about HashiCorp Vault, see [HashiCorp Vault](https://www.vaultproject.io/){: external}.
