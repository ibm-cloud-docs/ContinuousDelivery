---

copyright:
  years: 2023
lastupdated: "2023-05-12"

keywords: troubleshoot, toolchains, toolchain events

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for toolchain events
{: #troubleshoot-toolchains-events}

General problems with using toolchains might include tool integration configuration, toolchain template, or Cloud Foundry issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}


## Why am I not receiving any toolchain events?
{: #troubleshoot-receive-events}
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


## Why am I not receiving any Tekton pipeline events?
{: #troubleshoot-receive-tekton-events}
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
