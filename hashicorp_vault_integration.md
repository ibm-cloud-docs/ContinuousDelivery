---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Hashicorp Vault

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

# Configuring HashiCorp Vault
{: #hashicorpvault}

You can configure HashiCorp Vault as a tool integration in your toolchain so that you can access and refer to securely stored secrets in a HashiCorp Vault server.
{:shortdesc}

Before you configure the HashiCorp Vault tool integration for your toolchain, you need the authentication method and associated credentials with permission to access the HashiCorp Vault server that you want to connect to. For example, if the `authentication_method` is `github`, you must know your `token` credential. You also need to know the values for the `server url`, `integration url`, and `secrets path`. If the HashiCorp Vault server is bound to a specific port, include the port number in the server url. For example, `https://192.168.0.100:8200`.
{: important}

Configure HashiCorp Vault to securely manage secrets such as API keys and secrets that are part of your toolchain or delivery pipeline:

1. If you are configuring this tool integration as you are creating the toolchain, and a HashiCorp Vault tool integration exists within the template that you are configuring, click the **HashiCorp Vault** tab. Alternatively, in the **More tools** section, click **HashiCorp Vault**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **HashiCorp Vault**.

1. Type the name that you want to display for this tool integration on the HashiCorp Vault card in your toolchain.
1. Type the URL for the HashiCorp Vault server that you want to open when you click the HashiCorp Vault card from your toolchain.
1. Type the URL for the HashiCorp Vault tool integration.
1. Type the path to the Secrets on the HashiCorp Vault server that is accessible when you use the configured Authentication method and associated authentication credentials.  
1. Click **Create Integration**.
1. From your toolchain, click **HashiCorp Vault** to use the HashiCorp Vault Secrets Picker and Pusher components to select secrets for use within your toolchain or delivery pipeline.  

## Learn more about HashiCorp Vault

To learn more about HashiCorp Vault, see [HashiCorp Vault](https://www.vaultproject.io/){:external}.
