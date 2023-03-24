---

copyright:
  years: 2015, 2023
lastupdated: "2023-03-24"

keywords: troubleshoot, toolchains, tool integrations

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for toolchains
{: #troubleshoot-toolchains}

General problems with using toolchains might include tool integration configuration, toolchain template, or Cloud Foundry issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}


## Why can't I create a toolchain from a template that uses a private repo in a different region?
{: #troubleshoot-cd-grit-integration-private}
{: troubleshoot}
{: support}

The toolchain template that you are using references a private {{site.data.keyword.gitrepos}} repo.

{{site.data.keyword.gitrepos}} is region-specific. When you try to create a toolchain from a template and target a region that the private repo isn't located in, the Git integration setup fails.
{: tsSymptoms}
   
When you add a {{site.data.keyword.gitrepos}} repo to a toolchain in a specific region, your IBM ID is mapped to a GitLab user name that gives you access to GitLab in that region. Even though your GitLab user name appears the same in all regions, the associated GitLab user is different in each region because each region has a separate installation of GitLab. Access to GitLab users in other regions isn't automatically granted to toolchains even when the GitLab user name appears to be the same.
{: tsCauses}

Make the {{site.data.keyword.gitrepos}} repo public so that it can be accessed from anywhere, including other {{site.data.keyword.cloud_notm}} regions.
{: tsResolve}

If the repo must be private, the repo owner can grant access to it by creating a [personal access token](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) on the GitLab server where the source repo is located. You need access only to the private repo to clone the content during the toolchain creation. The personal access token can be created with an expiry date to limit its lifetime to expire after one day. 

After you have a personal access token, you can create a URL to access the repo from other regions. While you are configuring the tool integration, in the **Source repository URL** field, update the repo URL to use your user name and access token.

`https://user:XXXXXXX@us-south.git.cloud.ibm.com/group/node-hello-world`

Where `user` is your GitLab user name, `XXXXXXX` is the access token, [group](https://us-south.git.cloud.ibm.com/help/user/group/index.md){: external} is the group where the repo is stored, and `node-hello-world` is the repo name.

If your GitLab repo isn't located within a GitLab group, the value of `group` is the same as your user name.
{: tip}


## I configured a tool integration for my toolchain, why wasn't it configured?
{: #troubleshoot-tool-integration-error}
{: troubleshoot}
{: support}

If an error occurs during the setup process or if the communication between the toolchain and the tool does not complete properly, the configuration fails.

After you add and configure a tool integration for your toolchain, an error message is displayed to indicate that the setup failed.
{: tsSymptoms}

When you add a tool integration, the toolchain communicates with the tool that is represented by the tool integration to provision any necessary resources and associate them with the toolchain. If an error occurs during the setup process or if the communication between the toolchain and the tool does not complete properly, the tool integration is put into an error state.
{: tsCauses}

You can try to configure the tool integration again:
{: tsResolve}

1. On its tool card, hover over the `Setup failed` message and click **Reconfigure**.

   ![Reconfigure button](images/tool_reconfigure.png){: caption="Figure 1. Reconfigure tool integration" caption-side="bottom"}

1. Make sure that you are using valid configuration parameters. If the error was caused by an invalid configuration, an error message is displayed; for example, `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`. Update the settings for the tool integration and click **Save integration**.
1. If the error was caused by a communication problem, click **Save integration** to try again.

## Why can't I create a toolchain to deploy my app to Cloud Foundry?
{: #troubleshoot-deploy_cf}
{: troubleshoot}
{: support}

Before you can create a toolchain that deploys to a Cloud Foundry org, you must have an existing org and space, with the Developer role assigned. 

You try to create a toolchain to deploy your app to Cloud Foundry. After you enter your API key, the **Organization** and **Space** fields are empty and you cannot create your toolchain.
{: tsSymptoms} 

A Cloud Foundry org and space can't be located in your account.
{: tsCauses}

[Add a Cloud Foundry org and space to your account](https://cloud.ibm.com/account/cloud-foundry){: external}, and assign the Developer role to users at the space level. For more information about Cloud Foundry orgs and spaces, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
{: tsResolve}

## Why can't I delete toolchains by using the `ibmcloud` CLI?
{: #troubleshoot-delete_toolchains_cli}
{: troubleshoot}
{: support}

Currently, you can't delete toolchains by using the ibmcloud resource CLI. 

I tried to delete a toolchain from the command line by using the `ibmcloud resource service-instance-delete` command, and the command fails with the following error message:
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

Toolchains are a special type of resource on the Cloud platform that you currently can't delete by using the `ibmcloud resource` CLI.
{: tsCauses}

To delete a toolchain:
{: tsResolve}

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the **Toolchains** page, click the toolchain to delete. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View toolchain**.
1. Click the **Actions** menu, then select **Delete**. Deleting a toolchain removes all of its tool integrations, which might delete resources that are managed by those integrations.
1. Confirm the deletion by typing the name of the toolchain and clicking **Delete**.

You can use the {{site.data.keyword.cloud_notm}} CLI {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands to delete toolchains. After you [install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-devtools-manually), you can delete a toolchain from the command line by using the [`ibmcloud dev toolchain-delete`](/docs/cli?topic=cli-idt-cli#toolchain-delete) command. 
{: tip}

## Why can't I view my toolchains in my DevOps dashboard?
{: #view-toolchain-ts}
{: troubleshoot}

When you go to the DevOps dashboard, your toolchains aren't displayed.
{: tsSymptoms}

Your toolchain doesn't show in the toolchain unless you have the proper location selected. {{site.data.keyword.DRA_short}} is only available in three locations: Dallas, Frankfurt, and London.
{: tsCauses}

On your toolchain page, change the location to Dallas, Frankfurt, or London to show all of your {{site.data.keyword.DRA_short}} integrated toolchains.
{: tsResolve}

## Why can't I create a toolchain when the root key is disabled?
{: #create-toolchain-root-key}
{: troubleshoot}

When you attempt to create a toolchain, the following notification is displayed: `The root key of the Key Management Service instance that was configured for the Continuous Delivery service in the selected resource group and region is disabled`.
{: tsSymptoms}

When you create a toolchain, you must protect it by using a root key for encryption that is enabled.
{: tsCauses}

Use one of the following methods to enable the root key for encryption: 
{: tsResolve}

* [Enable the root key for the {{site.data.keyword.keymanagementservicefull}} instance](/docs/key-protect?topic=key-protect-disable-keys#enable-root-key) that is associated with your {{site.data.keyword.contdelivery_short}} service, in the region where you want to create a toolchain. 

* [Enable the root key for the {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} instance](/docs/hs-crypto?topic=hs-crypto-disable-keys#enable-ui) that is associated with your {{site.data.keyword.contdelivery_short}} service, in the region where you want to create a toolchain.

## Why can't I view the service instances that I created on the Toolchains page when the root key is disabled?
{: #view-toolchain-root-key}
{: troubleshoot}

When you open your toolchain, the following notification is displayed: `The root key of the key management service instance that was used to encrypt this toolchain is disabled.`
{: tsSymptoms}

Because the information that is required to view the toolchain's service instances is decrypted when you open a toolchain, you must ensure that the root key for encryption is enabled.
{: tsCauses}

Use one of the following methods to enable the root key for encryption:
{: tsResolve}

* [Enable the root key for the {{site.data.keyword.keymanagementservicefull}} instance](/docs/key-protect?topic=key-protect-disable-keys#enable-root-key) that is associated with your {{site.data.keyword.contdelivery_short}} service, in the region where you want to view the toolchain.

* [Enable the root key for the {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} instance](/docs/hs-crypto?topic=hs-crypto-disable-keys#enable-ui) that is associated with your {{site.data.keyword.contdelivery_short}} service, in the region where you want to view the toolchain.

## When I use Terraform or the API to configure a tool integration, why does the configuration fail with the `Could not find value for secret reference...` error?
{: #troubleshoot-dangling-secret-ref}
{: troubleshoot}

The tool integration is configured with a reference to a secret, but the toolchain cannot find the referenced secret or secret store.

When you use Terraform or the API to create or update a tool integration, the configuration fails with the `Could not find value for secret reference...` error message.
{: tsSymptoms}

Many tool integrations include configuration properties that are classified as secrets. When you set these properties in a Terraform resource or API call, you can set them as [secrets references](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secrets_references). A secret reference is a specially formatted string that identifies the name and location of a secret in a secret store that is integrated into the toolchain. This error indicates that the toolchain cannot find the identified secret, or that the secret store is not integrated into the toolchain. The error can occur for secrets references by name if one or more of the segments in the secrets reference `{vault:...}` string are incorrect, or if a key of the specified group, name, or field does not exist in the secret store. The error can occur for secrets references by CRN if the secret CRN references a secret that was deleted.
{: tsCauses}

The error message includes the secret reference string that cannot be resolved.
{: tsResolve}

Complete the following tasks for secrets references by name:

* Check that the secret store is integrated as a tool into the toolchain, and that the tool integration is correctly configured to identify by the service instance name. If the tool integration is misconfigured, edit the tool integration to correct the error condition, and then save the configuration.
* Check that the first segment of the `{vault::...}` secret reference matches the name of the secret store tool integration. For example, the secret reference `{vault::my-secret-store.my-secret}` expects the toolchain to have a secret store tool integration that is named `my-secret-store`. This value is the name of tool integration, *not* the name of the secret store service instance.
* If the secret is stored in {{site.data.keyword.keymanagementserviceshort}}, check that the second segment of the `{vault::...}` secret reference matches the name of the key that you want to use in the {{site.data.keyword.keymanagementserviceshort}} service instance. For example, the secret reference `{vault::my-kms.my-key}` expects to find a key that is named `my-key` in the {{site.data.keyword.keymanagementserviceshort}} service instance. This service instance is integrated into the toolchain with a {{site.data.keyword.keymanagementserviceshort}} tool integration that is named `my-kms`.
* If the secret is stored in {{site.data.keyword.secrets-manager_short}}, check that the second, and third segments of the `{vault::...}` secret reference match the names of the secret group and secret that you want to use in the {{site.data.keyword.secrets-manager_short}} service instance. For example, the secret reference `{vault::my-sm.my-group.my-key}` expects to find a secret that is named `my-key` in a secret group that is named `my-group`. This secret and secret group are stored within the {{site.data.keyword.secrets-manager_short}} service instance that is integrated into the toolchain by using a {{site.data.keyword.secrets-manager_short}} tool integration that is named `my-sm`.
* If the secret is stored in HashiCorp Vault, check that the second and third segments of the `{vault::...}` secret reference match the names of the secret and the secret field in the HashiCorp Vault server. For example, the secret reference `{vault::my-hcv.my-secret.my-field}` expects to find a secret that is named `my-secret` in the HashiCorp Vault server, and a field named `my-field` within that secret. This server is integrated into the toolchain by using a HashiCorp Vault tool integration that is named `my-hcv`.

Complete the following tasks for secrets references by CRN:

* Check that the secret store is integrated as a tool into the toolchain, and that the tool integration is correctly configured to identify by the service instance CRN. If the tool integration is misconfigured, edit the tool integration to correct the error condition, and then save the configuration.
* Check that the CRN of the {{site.data.keyword.secrets-manager_short}} service instance that is configured in the tool integration matches the CRN of the failing secret. 

## When I use Terraform or the API to configure a tool integration, why does the configuration fail with the `A problem was encountered while attempting to resolve secret reference...` error?
{: #troubleshoot-missing-s2s-auth}
{: troubleshoot}

The tool integration is configured with a reference to a secret, but the toolchain is not authorized to retrieve the secret from the secret store where the secret resides.

When you use Terraform or the API to create or update a tool integration, the configuration fails with the `A problem was encountered while attempting to resolve secret reference...` error message.
{: tsSymptoms}

Many tool integrations include configuration properties that are classified as secrets. When you set these properties in a Terraform resource or API call, you can set them as [secrets references](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secrets_references). A secret reference is a specially formatted string that identifies the name and location of a secret in a secret store that is integrated into the toolchain. With {{site.data.keyword.cloud_notm}} secret store services such as {{site.data.keyword.keymanagementserviceshort}} and {{site.data.keyword.secrets-manager_short}}, the error indicates that the toolchain can contact the secret store service, but is not authorized to retrieve secrets from the service. Typically, this issue occurs because {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) does not have a service-to-service authorization policy that allows the toolchain to read secrets from the service.
{: tsCauses}

The error message includes the secret reference string that cannot be resolved.
{: tsResolve}

Complete the following tasks for secrets references by name:

* Examine the first segment of the `{vault::...}` secret reference. This segment is the name of the secret store tool integration in the toolchain. For example, the `{vault::my-kms.my-key}` secret reference identifies a secret store tool integration that is named `my-kms`.
* Examine the secret store tool integration configuration to make sure that the `name` parameter matches the name of the secret store tool integration. Also, make sure that the tool integration is correctly configured to identify by the service instance name, and that the correct {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.secrets-manager_short}} service instance is selected.
* By using IAM, add a service-to-service authorization policy from the toolchain to the {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.secrets-manager_short}} service instance. In the authorization policy, the toolchain is the *source* service, and the secret store is the *target* service. When you target {{site.data.keyword.keymanagementserviceshort}}, make sure that the policy grants the `Viewer` and `ReaderPlus` roles. When you target {{site.data.keyword.secrets-manager_short}}, make sure that the policy grants the `Viewer` and `SecretsReader` roles.

Complete the following tasks for secrets references by CRN:

* Examine the secret store tool integration configuration to make sure that it is correctly configured to identify by the service instance CRN. Also, make sure that the CRN for the {{site.data.keyword.secrets-manager_short}} service instance is correct.
* Use IAM to add a service-to-service authorization policy from the toolchain to the {{site.data.keyword.secrets-manager_short}} service instance. In the authorization policy, the toolchain is the *source* service, and the {{site.data.keyword.secrets-manager_short}} instance is the *target* service. Make sure that the policy grants the `Viewer` and `SecretsReader` roles.

For more information about service-to-service authorization policies, see [Using authorizations to grant access between services](/docs/account?topic=account-serviceauth). 

For an example of how to configure a service-to-service authorization policy from a toolchain to a secret store service instance with Terraform, see [Specifying secret references with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security&interface=terraform#cd_secrets_references_terraform).

## When I use Terraform or the API to configure a {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, or {{site.data.keyword.appconfig_short}} tool integration, why does the configuration fail?
{: #troubleshoot-missing-service}
{: troubleshoot}

The tool integration refers to a {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, or {{site.data.keyword.appconfig_short}} service instance that does not exist.

When you use Terraform or the API to create or update a {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, or {{site.data.keyword.appconfig_short}} tool integration, the configuration fails with the `There was a problem with the provided service parameters, please check that they are valid` error message.
{: tsSymptoms}

The tool integration is configured with the name or ID of a {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, or {{site.data.keyword.appconfig_short}} service instance that cannot be found or accessed. If you are using Terraform to manage both the service instance and the tool integration, Terraform might attempt to create, or update the tool integration before it creates the service instance.
{: tsCauses}

If you are using Terraform, check your Terraform configuration to make sure that the [`ibm_cd_toolchain_tool_keyprotect`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_keyprotect){: external}, [`ibm_cd_toolchain_tool_secretsmanager`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_secretsmanager){: external}, or [`ibm_cd_toolchain_tool_appconfig`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_appconfig){: external} tool integration resource depends on the {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, or {{site.data.keyword.appconfig_short}} [`ibm_resource_instance`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/resource_instance){: external} resource that the tool integration represents. You can specify this dependency within the tool integration resource by referring to attributes of the service instance resource, or by specifying a `depends_on` meta-argument that refers to the service instance resource. You can refer directly to the service instance resource, or indirectly through other intermediate resources. By declaring dependencies between resources correctly, you can coerce Terraform into creating, updating, and deleting resources in the correct sequence.
{: tsResolve}

For an example of how dependencies work between Terraform resources, see [Specifying secret references with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security&interface=terraform#cd_secrets_references_terraform).

If you are using the API, check the configuration parameters of the {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, or {{site.data.keyword.appconfig_short}} tool integration that you are trying to create or update. Verify that the name or ID of the service instance that you are trying to integrate is correctly specified within the configuration of the tool integration.
