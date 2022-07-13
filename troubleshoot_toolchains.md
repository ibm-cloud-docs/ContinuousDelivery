---

copyright:
  years: 2015, 2022
lastupdated: "2022-07-13"

keywords: troubleshoot, toolchains, tool integrations

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

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

![Setup failed error](images/tool_setup_failed.png){: caption="Figure 1. Setup failed error" caption-side="bottom"}

You can try to configure the tool integration again:
{: tsResolve}

1. On its tool card, hover over the `Setup failed` message and click **Reconfigure**.

   ![Reconfigure button](images/tool_reconfigure.png){: caption="Figure 2. Reconfigure tool integration" caption-side="bottom"}

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
