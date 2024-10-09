---

copyright:
  years: 2018, 2024
lastupdated: "2024-07-25"

keywords: secure environment, data, Data, high availability, access

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Securing your data in {{site.data.keyword.contdelivery_short}}
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} hosts your databases in a highly available and secure environment:

* Data is encrypted at rest (GPFS, LUKS, and built-in disk) and in transit (HTTPS and SSH) by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service, or the services and infrastructure that it depends on.
* [Personal data can be encrypted only in the Professional plan](#cd_professional_plan) by using a root key within an instance of the {{site.data.keyword.keymanagementservicefull}} service or the {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} service.
* Client and system credentials are stored on encrypted disks. 
* Configuration data for tool integrations and {{site.data.keyword.deliverypipeline}} property values might include sensitive information. This data is encrypted by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service because it is stored in databases that are internal to the service. 
* The application and data are configured for high availability.
* Access to data is limited to only those users who require the data to support and maintain the service.

## Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}
{: #cd_secure_credentials}

The {{site.data.keyword.contdelivery_short}} service encrypts customer-owned sensitive data before it stores it in databases that are used internally by the service. Sensitive data includes third-party tool integration configuration data and {{site.data.keyword.deliverypipeline}} property values. Data is encrypted by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service or by using encryption keys from the root key that is specified within an instance of the {{site.data.keyword.keymanagementservicefull}} service or the {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} service.

DevOps processes often require various types of credentials (such as usernames and passwords, API keys, service keys, and SSH keys) to interact with other systems to build, test, and deploy applications. You are responsible for ensuring that these credentials aren't inadvertently shared outside of their intended audience. Access to these credentials by malicious actors might disrupt your IT operations, cause unexpected costs, or use your resources to start attacks. IBM is not responsible for protecting and maintaining the security of your credentials.

To keep your credentials secure, make sure that you follow this guidance:

* Do not store credentials in Git repos. Depending on the repo settings, files within a repo might be visible to other members of your organization, other {{site.data.keyword.cloud_notm}} users, or the public internet.
* Do not include user credentials in {{site.data.keyword.deliverypipeline}} definitions because they might be visible to other users. Specifically, do not place user credentials within {{site.data.keyword.deliverypipeline}} Classic job definition scripts, {{site.data.keyword.deliverypipeline}} Tekton yaml files, or scripts that are started by delivery pipelines.
* Do not publish user credentials in log files that are created when a pipeline runs because these files might be shared.
* Do not specify credentials in plain text in calls to {{site.data.keyword.contdelivery_short}} APIs, such as when you configure [tool integrations](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [Tekton pipeline environment properties](https://cloud.ibm.com/apidocs/tekton-pipeline#create-tekton-pipeline-properties){: external}, or [Tekton pipeline trigger properties](https://cloud.ibm.com/apidocs/tekton-pipeline#create-tekton-pipeline-trigger-properties){: external}. 
* Do not include credentials, personal identifying information, or other sensitive information in calls to the [POST /toolchains/{toolchain_id}/events](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external} API. The API sends events containing the data you specify to instances of {{site.data.keyword.en_short}} that are integrated into the toolchain. {{site.data.keyword.en_short}} will subsequently forward the events to configured destinations such as email, SMS, and Slack.
* Do not specify credentials in plain text in Terraform configuration files, such as when you define tool integration resources, Tekton pipeline environment property resources, or Tekton pipeline trigger property resources. Instead, manage credentials in a secrets storage service and specify them by reference in API calls and Terraform configurations. For more information about managing secrets by reference, see [Protecting your credentials by using secrets references](#cd_secrets_references).
   
{{site.data.keyword.cloud_notm}} provides several options that you can use for secure key storage and secrets.

* [Classic pipeline secure environment properties](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about)
* [Tekton pipeline secure environment properties](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines)
* [{{site.data.keyword.keymanagementservicefull}}](/docs/key-protect?topic=key-protect-getting-started-tutorial)
* [{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-get-started)
* [HashiCorp Vault](https://www.vaultproject.io/){: external}
   
For more information about secure DevOps best practices, see [DevOps Security](https://www.ibm.com/topics/devops?mhsrc=ibmsearch_a&mhq=Secure%20DevOps#toc-security-j2-0639C){: external}.

## Protecting your credentials by using secrets references
{: #cd_secrets_references}

Many of the properties that you can configure when you are working with {{site.data.keyword.contdelivery_short}} toolchains and delivery pipelines, such as passwords, API keys, certificates, or other tokens, are classified as secrets or credentials. To set the value of a secure property, you can either use plain text or a secrets reference. Using a secrets reference is the recommended method for setting the value of a secure property.

When you set a secure property with a *plain text* secret value, {{site.data.keyword.contdelivery_short}} actively encrypts and stores the value internally. Although the value is kept secure within the {{site.data.keyword.contdelivery_short}} service, the service cannot protect the value on the client side. When you set a secure property by using the console in your browser, by calling an API, or by configuring a Terraform resource, the plain text secret might be exposed on your local systems. Plain text secrets are also more difficult to rotate. When a secret, such as an API key, must be rotated, all secure properties that carry the secret value must also be located and updated.

When you set a secure property with a *secrets reference* value, the value is a specially formatted string that refers to the location or address of a secret that is managed within a secrets storage service such as [{{site.data.keyword.keymanagementservicefull}}](/docs/key-protect), [{{site.data.keyword.secrets-manager_full}}](/docs/secrets-manager), or HashiCorp Vault. Although {{site.data.keyword.contdelivery_short}} actively encrypts and stores the secrets reference value internally, the secret value is not exposed on the client side. When {{site.data.keyword.contdelivery_short}} must retrieve the secret to perform processing on your behalf, it internally retrieves the value from the referenced secrets store. Secrets references are also resilient to rotation. Typically, when a secret is rotated within a secrets store, the location or address of the secret remains the same. Only the secret value itself is changed.

Two types of secrets references are supported: by name or by [Cloud Resource Name (CRN)](/docs/account?topic=account-crn). Currently, only [{{site.data.keyword.secrets-manager_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager) tool integrations support referencing secrets by CRN. This format allows for greater flexibility because you can reference secrets from a {{site.data.keyword.secrets-manager_short}} instance in a different account if the correct [authorization](https://cloud.ibm.com/iam/authorizations){: external} is in place. 

Make sure that you consider the following prerequisites for specifying a secrets reference within the scope of a toolchain:

* The secrets store must be added to the toolchain as a tool integration. For more information about secrets store tool integrations, see [Configuring {{site.data.keyword.keymanagementserviceshort}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-keyprotect), [Configuring {{site.data.keyword.secrets-manager_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager), and [Configuring HashiCorp Vault](/docs/ContinuousDelivery?topic=ContinuousDelivery-hashicorpvault).
* An IAM service-to-service authorization policy must be configured to allow the source toolchain to retrieve secrets from the target secrets store. For more information about service-to-service authorizations, see [Using authorizations to grant access between services](/docs/account?topic=account-serviceauth).

When you work outside of the console, such as with the API or Terraform, use the following format for secrets references by name:

* `{vault::SECRET_STORE_INTEGRATION_NAME.SECRET_NAME}` when you reference secrets that are contained within {{site.data.keyword.keymanagementserviceshort}}.
* `{vault::SECRET_STORE_INTEGRATION_NAME.SECRET_GROUP_NAME.SECRET_NAME}` when you reference secrets that are contained within {{site.data.keyword.secrets-manager_short}}.
* `{vault::SECRET_STORE_INTEGRATION_NAME.SECRET_NAME.FIELD_NAME}` when you reference secrets that are contained within HashiCorp Vault.

where:

* `SECRET_STORE_INTEGRATION_NAME` is the name of the secrets store integration in the toolchain, *not* the name of the secrets store service instance.
* `SECRET_GROUP_NAME` is the name of the group that contains the secret within {{site.data.keyword.secrets-manager_short}}.
* `SECRET_NAME` is the name of the secret in the secrets store.
* `FIELD_NAME` is the name of the field within the HashiCorp Vault secret.

To use a CRN secrets reference, obtain the secret CRN directly from the {{site.data.keyword.secrets-manager_short}} UI or programmatically by using the CLI, API, or SDKs.

### Specifying secrets references by using the console
{: #cd_secrets_references_ui}
{: ui}

When you use the console, the fields for tool integration configuration properties and {{site.data.keyword.deliverypipeline}} properties that are classified as secure are annotated with a key icon. Click this icon to open a dialog from which you can select a secrets store and secret. Alternatively, for secrets references by CRN, paste the CRN value directly into the property.

### Specifying secrets references with the API
{: #cd_secrets_references_api}
{: api}

You can work with secure properties with secrets reference values in calls to the API, which requires an [IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
```bash
export CD_TOOLCHAIN_AUTH_TYPE=iam && \
export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
export CD_TOOLCHAIN_URL=https://api.us-south.devops.cloud.ibm.com/toolchain/v2
```
{: pre}

#### Using secrets references by name
{: #cd_secrets_references_name}

The following example demonstrates how to use a secrets reference by name secret. It shows how to create a Slack tool integration with an API token (Slack webhook) that is stored in an instance of {{site.data.keyword.keymanagementserviceshort}}. This example assumes that the toolchain already contains a {{site.data.keyword.keymanagementserviceshort}} tool integration and that an IAM service-to-service authorization policy from the source toolchain to the target {{site.data.keyword.keymanagementserviceshort}} service instance is in place.

```curl
curl -X POST \
https://api.us-south.devops.cloud.ibm.com/toolchain/v2/toolchains/01234567-89ab-cdef-0123-456789abcdef/tools \
-H "Authorization: Bearer $TOKEN" \
-H 'Accept: application/json' \
-H 'Content-Type: application/json' \
-d '{
    "tool_type_id": "slack",
    "parameters": {
    "api_token": "{vault::my-kms-tool-integration.my-slack-webhook}",
    "channel_name": "my_slack_channel_name",
    "team_url": "my_slack_team_name"
    }
}' 
```
{: pre}
{: curl}

```javascript
const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
...
(async () => {
    const toolchainService = CdToolchainV2.newInstance();
    const slackParameters = {
        api_token: "{vault::my-kms-tool-integration.my-slack-webhook}",
        channel_name: "my_slack_channel_name",
        team_url: "my_slack_team_name"
    };

    const toolPrototypeModel = {
        toolchainId: "01234567-89ab-cdef-0123-456789abcdef",
        toolTypeId: "slack",
        parameters: slackParameters
    };

    const slackTool = await toolchainService.createTool(toolPrototypeModel);
})();
```
{: codeblock}
{: node}

```go
import (
    "github.com/IBM/continuous-delivery-go-sdk/cdtoolchainv2"
)
...
toolchainClientOptions := &cdtoolchainv2.CdToolchainV2Options{}
toolchainClient, err := cdtoolchainv2.NewCdToolchainV2UsingExternalConfig(toolchainClientOptions)
slackParameters := map[string]interface{}{
    "api_token": "{vault::my-kms-tool-integration.my-slack-webhook}",
    "channel_name": "my_slack_channel_name",
    "team_url": "my_slack_team_name",
}
createToolOptions := toolchainClient.NewCreateToolOptions("01234567-89ab-cdef-0123-456789abcdef", "slack")
createToolOptions.SetParameters(slackParameters)
slackTool, response, err := toolchainClient.CreateTool(createToolOptions)
```
{: codeblock}
{: go}

```python
from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
...
toolchain_service = CdToolchainV2.new_instance()
slack_parameters = {
    "api_token": "{vault::my-kms-tool-integration.my-slack-webhook}",
    "channel_name": "my_slack_channel_name",
    "team_url": "my_slack_team_name"
}
slack_tool = toolchain_service.create_tool(
    toolchain_id = "01234567-89ab-cdef-0123-456789abcdef",
    tool_type_id = "slack",
    parameters = slack_parameters
)
```
{: codeblock}
{: python}

```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   HashMap<String, Object> slackParameters = new HashMap<>();
   slackParameters.put("api_token", "{vault::my-kms-tool-integration.my-slack-webhook}");
   slackParameters.put("channel_name", "my_slack_channel_name");
   slackParameters.put("team_url", "my_slack_team_name");
   CreateToolOptions createSlackToolOptions = new CreateToolOptions.Builder()
      .parameters(slackParameters)
      .toolchainId({toolchain_id})
      .toolTypeId("slack")
      .build();
   Response<ToolchainToolPost> response = toolchainService.createTool(createSlackToolOptions).execute();
   ToolchainToolPost slackTool = response.getResult();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the secret reference values that are used in the previous example.

| Value | Description |
|:---------|:------------|
| `my-kms-tool-integration` | The name of the {{site.data.keyword.keymanagementserviceshort}} tool integration in the toolchain. It is not the name of the {{site.data.keyword.keymanagementserviceshort}} service instance. |
| `my-slack-webhook` | The name of the standard key that is managed in the {{site.data.keyword.keymanagementserviceshort}} service instance. |
{: caption="Secret reference values" caption-side="top"}

#### Using secrets references by CRN
{: #cd_secrets_references_crn}

The following example demonstrates how to use a secrets reference by CRN secret. It shows how to create a Slack tool integration with an API token (Slack webhook) that is stored in an instance of {{site.data.keyword.secrets-manager_short}}. This example assumes that the toolchain already contains a {{site.data.keyword.secrets-manager_short}} tool integration and that an IAM service-to-service authorization policy from the source toolchain to the target {{site.data.keyword.secrets-manager_short}} service instance is in place.

```curl
curl -X POST \
https://api.us-south.devops.cloud.ibm.com/toolchain/v2/toolchains/01234567-89ab-cdef-0123-456789abcdef/tools \
-H "Authorization: Bearer $TOKEN" \
-H 'Accept: application/json' \
-H 'Content-Type: application/json' \
-d '{
    "tool_type_id": "slack",
    "parameters": {
    "api_token": "crn:v1:bluemix:public:secrets-manager:us-south:a/9bb43e401a7a87d15145da761da98571:604de62c-c04f-3f5e-b7e8-4acafe0ecde7:secret:5ec17023-b631-fbcb-ef9c-4f2eb01f1dda",
    "channel_name": "my_slack_channel_name",
    "team_url": "my_slack_team_name"
    }
}' 
```
{: pre}
{: curl}

```javascript
const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
...
(async () => {
    const toolchainService = CdToolchainV2.newInstance();
    const slackParameters = {
        api_token: "crn:v1:bluemix:public:secrets-manager:us-south:a/9bb43e401a7a87d15145da761da98571:604de62c-c04f-3f5e-b7e8-4acafe0ecde7:secret:5ec17023-b631-fbcb-ef9c-4f2eb01f1dda",
        channel_name: "my_slack_channel_name",
        team_url: "my_slack_team_name"
    };

    const toolPrototypeModel = {
        toolchainId: "01234567-89ab-cdef-0123-456789abcdef",
        toolTypeId: "slack",
        parameters: slackParameters
    };

    const slackTool = await toolchainService.createTool(toolPrototypeModel);
})();
```
{: codeblock}
{: node}

```go
import (
    "github.com/IBM/continuous-delivery-go-sdk/cdtoolchainv2"
)
...
toolchainClientOptions := &cdtoolchainv2.CdToolchainV2Options{}
toolchainClient, err := cdtoolchainv2.NewCdToolchainV2UsingExternalConfig(toolchainClientOptions)
slackParameters := map[string]interface{}{
    "api_token": "crn:v1:bluemix:public:secrets-manager:us-south:a/9bb43e401a7a87d15145da761da98571:604de62c-c04f-3f5e-b7e8-4acafe0ecde7:secret:5ec17023-b631-fbcb-ef9c-4f2eb01f1dda",
    "channel_name": "my_slack_channel_name",
    "team_url": "my_slack_team_name",
}
createToolOptions := toolchainClient.NewCreateToolOptions("01234567-89ab-cdef-0123-456789abcdef", "slack")
createToolOptions.SetParameters(slackParameters)
slackTool, response, err := toolchainClient.CreateTool(createToolOptions)
```
{: codeblock}
{: go}

```python
from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
...
toolchain_service = CdToolchainV2.new_instance()
slack_parameters = {
    "api_token": "crn:v1:bluemix:public:secrets-manager:us-south:a/9bb43e401a7a87d15145da761da98571:604de62c-c04f-3f5e-b7e8-4acafe0ecde7:secret:5ec17023-b631-fbcb-ef9c-4f2eb01f1dda",
    "channel_name": "my_slack_channel_name",
    "team_url": "my_slack_team_name"
}
slack_tool = toolchain_service.create_tool(
    toolchain_id = "01234567-89ab-cdef-0123-456789abcdef",
    tool_type_id = "slack",
    parameters = slack_parameters
)
```
{: codeblock}
{: python}

```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   HashMap<String, Object> slackParameters = new HashMap<>();
   slackParameters.put("api_token", "crn:v1:bluemix:public:secrets-manager:us-south:a/9bb43e401a7a87d15145da761da98571:604de62c-c04f-3f5e-b7e8-4acafe0ecde7:secret:5ec17023-b631-fbcb-ef9c-4f2eb01f1dda");
   slackParameters.put("channel_name", "my_slack_channel_name");
   slackParameters.put("team_url", "my_slack_team_name");
   CreateToolOptions createSlackToolOptions = new CreateToolOptions.Builder()
      .parameters(slackParameters)
      .toolchainId({toolchain_id})
      .toolTypeId("slack")
      .build();
   Response<ToolchainToolPost> response = toolchainService.createTool(createSlackToolOptions).execute();
   ToolchainToolPost slackTool = response.getResult();
   ```
   {: codeblock}
   {: java}

### Specifying secrets references with Terraform
{: #cd_secrets_references_terraform}
{: terraform}

You can work with secure properties with secrets reference values in Terraform.

#### Using secrets references by name
{: #cd_secretsreferences_name_terraform}

The following example shows a complete set of resources for a {{site.data.keyword.keymanagementserviceshort}} service instance, a standard key (Slack webhook), a toolchain, an IAM service-to-service authorization policy, a {{site.data.keyword.keymanagementserviceshort}} tool integration, and a Slack tool integration that references the webhook secret by name.

This example also includes an `ibm_kms_key` standard key resource with a `payload` that is set to the base64-encoded Slack webhook secret. It shows the relationship between the name of the key and the value of the secrets reference within the Slack tool integration resource. In practice, it is more secure to create the standard key ahead of time from a separate Terraform project or other process to which only limited, authorized personnel have access.
{: tip}

```terraform
variable "slack_webhook" {}
variable "slack_channel" {}
variable "slack_team" {}

data "ibm_resource_group" "rg" {
    name = "default"
}

resource "ibm_resource_instance" "kms" {
    name              = "my-kms-service-instance"
    service           = "kms"
    plan              = "tiered-pricing"
    location          = "us-south"
    resource_group_id = data.ibm_resource_group.rg.id
}

resource "ibm_kms_key" "key" {
    instance_id  = ibm_resource_instance.kms.guid
    key_name     = "my-slack-webhook"
    standard_key = true
    payload      = base64encode(var.slack_webhook)
}

resource "ibm_cd_toolchain" "toolchain" {
    name              = "tf-toolchain-secret-refs"
    resource_group_id = data.ibm_resource_group.rg.id
}

resource "ibm_iam_authorization_policy" "s2s" {
    source_service_name         = "toolchain"
    source_resource_instance_id = ibm_cd_toolchain.toolchain.id
    target_service_name         = "kms"
    target_resource_instance_id = ibm_resource_instance.kms.guid
    roles                       = ["Viewer", "ReaderPlus"]
}

resource "ibm_cd_toolchain_tool_keyprotect" "integration" {
    toolchain_id = ibm_cd_toolchain.toolchain.id
    parameters {
        name           = "my-kms-tool-integration"
        region         = var.region
        resource_group = data.ibm_resource_group.rg.name
        instance_name  = ibm_resource_instance.kms.name
    }
    depends_on = [
        ibm_iam_authorization_policy.s2s
    ]
}

resource "ibm_cd_toolchain_tool_slack" "integration" {
    toolchain_id = ibm_cd_toolchain.toolchain.id
    parameters {
        webhook      = "{vault::my-kms-tool-integration.my-slack-webhook}"
        channel_name = var.slack_channel
        team_name    = var.slack_team
    }
    depends_on = [
        ibm_cd_toolchain_tool_keyprotect.integration
        ibm_kms_key.key
    ]
}
```
{: codeblock}

The following table lists and describes each of the secrets reference values that are used in the previous example.

| Value | Description |
|:---------|:------------|
| `my-kms-tool-integration` | The name of the {{site.data.keyword.keymanagementserviceshort}} tool integration in the toolchain. It is not the name of the {{site.data.keyword.keymanagementserviceshort}} service instance. |
| `my-slack-webhook` | The name of the standard key that is managed in the {{site.data.keyword.keymanagementserviceshort}} service instance. |
{: caption="Secret reference values" caption-side="top"}

#### Using secrets references by CRN
{: #cd_secretsreferences_crn_terraform}

The following example assumes that an instance of {{site.data.keyword.secrets-manager_short}} exists. It shows resources for an arbitrary secret (Slack webhook), a toolchain, an IAM service-to-service authorization policy, a {{site.data.keyword.secrets-manager_short}} tool integration, and a Slack tool integration that references the webhook secret by CRN.

This example includes an `ibm_sm_arbitrary_secret` key resource with a `payload` that is set to the Slack webhook secret. It shows how to use the CRN from the key resource as the value of the secrets reference within the Slack tool integration resource. In practice, it is more secure to create the standard key ahead of time from a separate Terraform project or other process to which only limited, authorized personnel have access.
{: tip}

```terraform
variable "slack_webhook" {}
variable "slack_channel" {}
variable "slack_team" {}
variable "secrets_manager_name" {}

data "ibm_resource_group" "rg" {
    name = "default"
}

data ibm_resource_instance "sm" {
    name = var.secrets_manager_name
}

resource "ibm_sm_arbitrary_secret" "key" {
    instance_id     = data.ibm_resource_instance.sm.guid
    region          = data.ibm_resource_instance.sm.location
    secret_group_id = "default"
    name            = "my-slack-webhook"
    payload         = "var.slack_webhook"
}

resource "ibm_cd_toolchain" "toolchain" {
    name              = "tf-toolchain-secret-refs"
    resource_group_id = data.ibm_resource_group.rg.id
}

resource "ibm_iam_authorization_policy" "s2s" {
    source_service_name         = "toolchain"
    source_resource_instance_id = ibm_cd_toolchain.toolchain.id
    target_service_name         = "secrets-manager"
    target_resource_instance_id = data.ibm_resource_instance.sm.guid
    roles                       = ["Viewer", "SecretsReader"]
}

resource "ibm_cd_toolchain_tool_secretsmanager" "integration" {
    toolchain_id = ibm_cd_toolchain.toolchain.id
    parameters {
        name             = "my-sm-tool-integration"
        instance_id_type = "instance-crn"
        instance_crn     = data.ibm_resource_instance.sm.resource_crn
    }
    depends_on = [
        ibm_iam_authorization_policy.s2s
    ]
}

resource "ibm_cd_toolchain_tool_slack" "integration" {
    toolchain_id = ibm_cd_toolchain.toolchain.id
    parameters {
        webhook      = ibm_sm_arbitrary_secret.key.crn
        channel_name = var.slack_channel
        team_name    = var.slack_team
    }
    depends_on = [
        ibm_cd_toolchain_tool_secretsmanager.integration
    ]
}
```
{: codeblock}

## Protecting your data with customer-managed keys 
{: #cd_professional_plan}

By default, {{site.data.keyword.contdelivery_short}} encrypts your data by using keys that are internal to the {{site.data.keyword.contdelivery_short}} service. For greater security and control, you can configure {{site.data.keyword.contdelivery_short}} to encrypt your data by using keys that you manage. This option is available only under the Professional plan, and only at the time that you are provisioning an instance of the {{site.data.keyword.contdelivery_short}} service. If you select your own Key Management Service, such as {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}, the following values are encrypted by using your own key instead of the encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service.

| Component | Value | 
|:-----------------|:-----------------|
|Toolchain		|Properties and parameters     |
|Pipeline		| * Property keys and values \n * Job logs \n * Job artifacts  |
|Integrations		| * Slack (Slack webhook) \n * Pagerduty (API access key, Integration key) \n * Sauce Labs (Access key) \n * Artifactory (API key) \n * HashiCorp Vault (Token, Role ID, Secret ID, Password) \n *  Jenkins (Jenkins API token) \n * JIRA (JIRA API token) \n * Nexus (Authentication token) \n * Rational Team Concert (Password) \n * Security and Compliance Center ({{site.data.keyword.cloud_notm}} API key) \n * Sonarqube (SonarQube password or authentication token) |
|{{site.data.keyword.DRA_full}}		|Attachment in test records |
{: caption="Values that are encrypted by using your own key" caption-side="top"}

The following components encrypt personal data by using only the provider-managed encryption key.

| Component | Value | 
|:-----------------|:-----------------|
|{{site.data.keyword.gitrepos}}		| * Issues, pull requests, and source code \n * Personal information, such as name, email, profile picture, address, and other information from the profile page     |
{: caption="Values that are encrypted by using the provider-managed key" caption-side="top"}

For more information about creating a {{site.data.keyword.contdelivery_short}} service instance that encrypts data with a customer key, see [Creating a {{site.data.keyword.contdelivery_short}} service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service).

## Protecting your data when you use third-party tool integrations
{: #cd_secure_integrations}

When you configure a tool integration for a toolchain, you explicitly enable data sharing between the {{site.data.keyword.contdelivery_short}} service and the tool integration. The kind of data that is shared, and whether data is sent to the tool, received from the tool, or both, varies depending on the type of tool integration.

Before you configure a tool integration, make sure you understand what data is shared. If you work with regulated data or data that you consider sensitive, make sure that the third-party tool usage and any data that might be shared with it do not compromise the confidentiality, integrity, or availability of your resources, or otherwise violate regulatory controls.

To learn more about tool integrations, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).

## Protecting your data when you use {{site.data.keyword.gitrepos}}
{: #cd_secure_grit}

{{site.data.keyword.gitrepos}} is an IBM-hosted component of the {{site.data.keyword.contdelivery_short}} service. All of the data that you provide to {{site.data.keyword.gitrepos}}, including but not limited to source files, issues, pull requests, and project configuration properties, is managed securely within {{site.data.keyword.contdelivery_short}}. However, {{site.data.keyword.gitrepos}} supports various mechanisms for exporting, sending, or otherwise sharing data to users and third parties.

The ability of {{site.data.keyword.gitrepos}} to share information is typical of many social coding platforms. However, such sharing might conflict with regulatory controls that apply to your business. After you create a project in {{site.data.keyword.gitrepos}}, but before you entrust any files, issues, records, or other data with the project, review the project settings and change any settings that you deem necessary to protect your data. Settings to review include visibility levels, email notifications, integrations, web hooks, access tokens, deploy tokens, and deploy keys.

### Project visibility levels
{: #cd_secure_grit_visibility}

{{site.data.keyword.gitrepos}} projects can have one of the following visibility levels: private, internal, or public.

* Private projects are visible only to project members. This setting is the default visibility level for new projects, and is the most secure visibility level for your data.
* Internal projects are visible to all users that are logged in to {{site.data.keyword.cloud_notm}}.
* Public projects are visible to anyone.

To limit project access to only project members, complete the following steps:

1. From the project sidebar, click **Settings** > **General**.
2. On the General Settings page, click **Visibility** > **project features** > **permissions**.
3. Locate the Project visibility setting.
4. Select **Private**, if it is not already selected.
5. Click **Save changes**.

### Project membership
{: #cd_secure_grit_membership}

{{site.data.keyword.gitrepos}} is a cloud hosted social coding environment that is available to all {{site.data.keyword.contdelivery_short}} users. If you are a {{site.data.keyword.gitrepos}} project Maintainer or Owner, you can invite any user and group members to the project. {{site.data.keyword.cloud_notm}} places no restrictions on who you can invite to a project. Because you can invite anyone into a GitLab project, be careful to invite only those users or groups who are part of your company or organization, unless you explicitly intend otherwise.

For more information about managing GitLab project members, see [Members of a project](https://docs.gitlab.com/ee/user/project/members/){: external}.

### Project email settings
{: #cd_secure_grit_email}

By default, {{site.data.keyword.gitrepos}} notifies project members by way of email about project activities. These emails typically include customer-owned data that was provided to {{site.data.keyword.gitrepos}} by users. For example, if a user posts a comment to an issue, {{site.data.keyword.gitrepos}} sends an email to all subscribers that includes information such as a copy of the comment, the user who posted it, and when the comment was posted. To turn off all email notifications for your project, complete the following steps:

1. From the project sidebar, click **Settings** > **General**.
2. On the General Settings page, click **Visibility** > **project features** > **permissions**.
3. Select the **Disable email notifications** checkbox.
4. Click **Save changes**.

### Project integrations and webhooks
{: #cd_secure_grit_integrations}

{{site.data.keyword.gitrepos}} projects might also be configured with integrations or webhooks to other systems, or equipped with access tokens, deploy tokens, and deploy keys. To review or change the integrations, webhooks, tokens, and keys that might be configured with your project, from the project sidebar, complete the following steps:

1. From the project sidebar, click **Settings**.
2. Click **Integrations** to work with your project's integrations with other applications.
3. Click **Webhooks** to work with your project's webhooks to other systems.
4. Click **Access Tokens** to work with access tokens that might grant access to your project.
5. Expand **Deploy Tokens** to work with the deploy tokens that might grant access to your project.
6. Expand **Deploy Keys** to work with deploy keys that might grant access to your project.

To learn more about working with {{site.data.keyword.gitrepos}}, see [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working).

## Protecting your data when you use Delivery Pipelines
{: #cd_secure_pipeline}

{{site.data.keyword.contdelivery_short}} pipelines run the jobs and steps that you provide. The {{site.data.keyword.contdelivery_short}} service securely manages the log output and build artifacts that are produced by your pipeline runs. However, {{site.data.keyword.contdelivery_short}} does not limit or manage the function of your pipeline job or step scripts.

When you develop and configure your pipeline job and step scripts, make sure that your scripts do not run actions that might compromise the confidentiality, integrity, or availability of your resources, or otherwise violate regulatory controls.

To learn more about Delivery Pipelines, see and [Working with pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about) and [Working with Tekton pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines).


## Protecting your data when you use Terraform
{: #cd_secure_terraform}

When you use Terraform to manage {{site.data.keyword.contdelivery_short}} resources, some of the variables, arguments, and attributes that are processed by Terraform might carry secret values such as passwords or API tokens. These values might be specified by you in your Terraform configuration language files, they might be retrieved and stored in Terraform state by the Terraform tool, or both. The following list provides examples of secret values that you must protect when you use Terraform.

* The IAM API Key that the {{site.data.keyword.cloud_notm}} Terraform Provider requires to authenticate to the {{site.data.keyword.cloud_notm}}. This key is specified in the `ibmcloud_api_key` argument of your Terraform module's `provider "ibm"` block.
* The arguments or attributes that represent passwords, access tokens, API keys, or other kinds of secrets in some `ibm_cd_toolchain_tool` resources and data sources.
* Property values that are designated as secrets in some `ibm_cd_tekton_pipeline_property` or `ibm_cd_tekton_pipeline_trigger_property` resources or data sources.

Use {{site.data.keyword.bplong_notm}} and the following practices to limit the exposure of sensitive data:

* Use Terraform variables to inject values into Terraform blocks.
* Use {{site.data.keyword.bplong_notm}} to securely manage and share secrets.
* Use {{site.data.keyword.bplong_notm}} to securely manage and share the Terraform state.
* Use the {{site.data.keyword.contdelivery_short}} secrets references when you specify secrets within the `ibm_cd_toolchain_tool`, `ibm_cd_tekton_pipeline_property`, or `ibm_cd_tekton_pipeline_trigger_property` resources.

If you are using the Terraform command-line tool, use the following practices to limit the exposure of sensitive data:

* Use Terraform variables to inject values into Terraform blocks.
* Allow the Terraform command-line tool to prompt for values when you run commands such as `terraform plan` or `terraform apply`.
* Control access to your Terraform state since it might contain secrets. Local Terraform state is written in plain text.
* Use the {{site.data.keyword.contdelivery_short}} secrets references when you specify secrets within the `ibm_cd_toolchain_tool`, `ibm_cd_tekton_pipeline_property`, or `ibm_cd_tekton_pipeline_trigger_property` resources.

To limit the exposure of sensitive data, avoid the following practices:

* Writing secrets in plain text inside any Terraform blocks, such as resource blocks, data blocks, or provider blocks.
* Writing secrets in plain text within the `terraform.tfvars`, `terraform.tfvars.json`, `*.auto.tfvars`, or `*.auto.tfvars.json` files.
* Delivering the `terraform.tfvars`, `terraform.tfvars.json`, `*.auto.tfvars`, or `*.auto.tfvars.json` files that contain secrets to source code repos.
* Delivering your Terraform state into source code repos.

Use {{site.data.keyword.bplong_notm}} instead of the Terraform command-line tool to process your Terraform configurations. {{site.data.keyword.bplong_notm}} offers several advantages such as secure storage of sensitive configuration properties.
{: tip}

For more information about {{site.data.keyword.bplong_notm}}, see the [{{site.data.keyword.bplong_notm}} documentation](/docs/schematics).

For more information about sensitive data in Terraform state, see [Sensitive Data in State](https://developer.hashicorp.com/terraform/language/state/sensitive-data){: external}.

For more information about how to set input variables in Terraform, see [Assigning Values to Root Module Variables](https://developer.hashicorp.com/terraform/language/values/variables#assigning-values-to-root-module-variables){: external}.


## Deleting your data from {{site.data.keyword.contdelivery_short}}
{: #cd_delete-data}

When you delete a {{site.data.keyword.contdelivery_short}} service instance, the related toolchains, tool integrations, tools, and data (including personal data) are not deleted. For more information about how to manage and delete data that is stored with toolchains, tool integrations, and tools, see [Modifying, exploring, and deleting personal data](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_personal_data#managing_personal_data).
