---

copyright:
  years: 2021
lastupdated: "2021-06-21"

keywords: DevSecOps, secrets in toolchains, managing secrets in toolchains

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
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

# Managing secrets in your toolchains
{: #cd-devsecops-toolchains-secrets}

Many of the tool integrations in your CI and CD toolchains require secrets to be provided, for example passwords, API keys, certificates, or other tokens. For instance, an {{site.data.keyword.cloud}} API key is used to carry out the most basic of pipeline tasks, such as to log in to {{site.data.keyword.cloud_notm}}. Similarly, the artifactory tool integration requires an API token to access images that are loaded and run by pipeline tasks.
{: shortdesc}

For security reasons, these secrets should not belong to or be affiliated with a person's identity or account. This is because people often have greater access permissions than Toolchain automation requires, and it would violate the security principle of ["least privilege"](https://en.wikipedia.org/wiki/Principle_of_least_privilege){: external}. Also, people often change roles or even companies and their credentials should be removed which might break Toolchain automation. By using an identity that is affiliated specifically for automation purposes provides a separation of duties between automation and people who use the automation.

Instead, the secrets that are used for non-{{site.data.keyword.cloud_notm}} resources (such as Artifactory or GitHub Enterprise) should be affiliated with a w3 Functional-Id with only the appropriate access that is needed by the Toolchains. Likewise, secrets for {{site.data.keyword.cloud_notm}} resources should be affiliated with an [IAM service ID API key](/docs/account?topic=account-serviceidapikeys) that is affiliated with an [IAM service ID](/docs/account?topic=account-serviceids). The IAM service ID access permissions should be scoped to the least privilege required by the Toolchains.

Managing credentials like these must be done securely and in compliance with best practices in the field of secrets management. In particular, this means vaulting the required secrets by using an approved in-boundary vault provider, such as [Hashicorp](https://pages.github.ibm.com/SOSTeam/SOS-Docs/vault/aboutvault.html){: external} and then linking your toolchain secrets to those resources.

The Secrets Management capabilities that are provided in the Toolchain setup and Pipeline user interfaces enable easy selection of vaulted secrets by using Secrets Integrations for HashiCorp Vault and {{site.data.keyword.keymanagementservicelong}}. By using the Secrets Picker dialog, a toolchain or pipeline editor can easily select named secrets from a bound secrets integration that will then be resolved by reference within the toolchain and pipeline. After a secret is chosen, a canonical secret reference is injected into the corresponding toolchain or pipeline secure property where the format is `{vault::integration-name.secret-name}`. This long form canonical reference is used by the front-end user interface components and importantly, the resolved value of the actual secret is never exposed to a user or permitted service.

In addition to manually selecting chosen secrets on a one-by-one basis from any bound secrets integrations in a toolchain, the option of using Secret Hints is also available. This enables a toolchain template to be predefined with suggested secrets names, otherwise known as Hints, that are a short form secret reference. The format of a secret hint is `{vault::secret-name}` where no secret integration name is included. This provides flexibility to the toolchain author in that all required secret names can be prepopulated into a `toolchain.yml` and then these are automatically resolved against whatever secrets integrations are configured for the toolchain.

The secrets used in both CI and CD are outlined as follows:

A `Hint` is a suggested default name that is automatically resolved against the first matching secret with the same name across any of the available secrets integrations that are bound to the toolchain.
{: note}

## One Pipeline Secrets
{: #one-pipeline-secrets}

| Secret | Hint |  Information | 
|---------|------|------------|
| {{site.data.keyword.cloud_notm}} API key | `ibmcloud-api-key` | **Required: CI & CD** Used to authenticate with IBM public cloud and perform a wide range of operations |
| {{site.data.keyword.IBM_notm}} CSIO Certificate | `ciso-signing-cert` | **Required: CI only** This is the certificate that is used to sign images built by the CI pipeline |
| {{site.data.keyword.IBM_notm}} Private Worker Service API Key | `private-worker-service-api-key` | **Required: CI only** A Service ID API Key Used to run delivery pipeline workloads on a Tekton Private Worker Service |
| GitHub Access Token | `git-token` | **Optional: CI & CD** Used to authenticate with GitHub and provide access to the repositories |
| Artifactory API Token | `artifactory-token` | **Required: CI & CD** Used to access images used by pipeline tasks |
| Slack Web Hook | `slack-webhook` | **Optional: CI & CD** This webhook is required if you choose to use the Slack tool integration to post toolchain status notifications |
| ServiceNow API Token | `servicenow-token` | **Required: CD only** Used to access Service Now for change management operations |
| HashiCorp Vault Role ID | `role-id` | **Required: CI & CD** Used to authenticate with the Hashicorp SOS vault server | 
| HashiCorp Vault Secret ID | `secret-id` | **Required: CI & CD** Used to authenticate with the Hashicorp SOS vault server |
| {{site.data.keyword.cos_full_notm}} Writer API Key |  `cos-api-key` | **Required: CI & CD** Used to authenticate with IBM Cloud Object Storage service - This key must have writer permission | 
{: caption="Table 1. OnePipeline Secrets" caption-side="top"}

Most {{site.data.keyword.IBM}} service teams use Hashicorp vault servers stood up by SOS. When teams are on-boarded with this service, they are granted credentials to authenticate with the Hashicorp server (typically a `role-id` and `secret-id` when using `approle` authentication). Both the `role-id` and `secret-id` are secrets in themselves and need to be completed on the Hashicorp tool integration tab when creating the toolchain instance. It is recommended that these secrets are stored using an [{{site.data.keyword.keymanagementservicelong_notm}} tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-keyprotect) so that they can be securely retrieved and applied in the toolchain workflow. Apart from that, all other toolchain secrets should be stored and retrieved using Hashicorp.

If the pipeline environment property `git-token` is not set, `ibmcloud-api-key` is used to retrieve the GitHub Access Token by default. However, if `ibmcloud-api-key` does not have access to `git`, `git-token` must be set.
{: note}

### Configuring the Secrets Stores
{: #configure-secret-stores}

When creating a new instance of the CI or CD toolchain you will see a Hashicorp tool integration like the following example:

![HashiCorp Vault Tool Integration form with required fields and example values](images/hc-tool-int.png "HashiCorp Vault Tool Integration form with required fields and example values"){: caption="Figure 1. HashiCorp Vault Tool Integration" caption-side="bottom"}

<!-- Next 3 links need new targets or to be removed -->

To use Hashicorp, you must provide the following information:

* **Name**: A name for this tool integration. This name is displayed in the toolchain.
* **Server URL**: The server URL for your HashiCorp Vault Instance. For example, `https://vserv-us.sos.ibm.com:8200`, `https://vserv-eu.sos.ibm.com:8200`, `https://vserv-test.sos.ibm.com:8200`, `https://vserv.sos.ibm.com:8200`.
* **Integration URL**: The URL that you want to navigate to when you click the HashiCorp Vault Integration tile.
* **Secrets Path**: The mount path where your secrets are stored in your HashiCorp Vault Instance.
* **Authentication Method**: The Authentication method for your HashiCorp Vault Instance. Use `AppRole`.
* **Role ID**: Your team's [AppRole Role ID](https://pages.github.ibm.com/vault-as-a-service/vault/usage/approle-role-ids.html).
* **Secret ID**: Your team's [Secret ID](https://pages.github.ibm.com/vault-as-a-service/vault/usage/manage-secret-ids.html).

If you do not have a HashiCorp Vault instance set up, you can follow this [documentation](https://pages.github.ibm.com/vault-as-a-service/vault/onboarding/project.html) to request a `Role ID`.

The templates also come with a Key Protect tool integration:

![IBM Key Protect Tool Integration form with required fields and example values](images/kp-int.png "IBM Key Protect Tool Integration form with required fields and example values"){: caption="Figure 2. IBM Key Protect Tool Integration" caption-side="bottom"}

If you stored the `role id` and `secret id` in {{site.data.keyword.keymanagementserviceshort}} in advance, then you can select the {{site.data.keyword.keymanagementserviceshort}} instance that contains those secrets in the tool card as shown in Figure 2. Once that is done, then you can click the key icons on the `role id` and `secret id` fields in the Hashicorp tool card, and use the picker to apply the secrets to those fields.

Similarly, any other secrets that are used in the toolchain will have a key icon attached to the text field. You can use the same picker control to apply the Hashicorp secrets to all the remaining instances.
