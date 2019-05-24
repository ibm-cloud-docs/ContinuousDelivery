---

copyright:
  years: 2015, 2019
lastupdated: "2019-05-23"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Troubleshooting for {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

General problems with using {{site.data.keyword.contdelivery_full}} might include GitHub authentication, pipeline creation, tool integration configuration, or Cloud Foundry issues. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

## I tried to add the GitHub tool integration to my toolchain, why wasn't the tool integration added?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

You must authorize with GitHub so that {{site.data.keyword.Bluemix_notm}} is authorized to access your GitHub account.

The GitHub tool integration wasn't added to your toolchain.
{: tsSymptoms}

If {{site.data.keyword.Bluemix_notm}} is not authorized to access your GitHub account, the tool integration is not added to your toolchain.
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps to authorize with GitHub:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and {{site.data.keyword.Bluemix_notm}} is not authorized to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account.
 1. When you are finished updating the settings, click **Save Integration**.
 

## Why can't I use the {{site.data.keyword.gitrepos}} tool integration in my toolchain from one region in a toolchain within a different region?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

You cannot use an instance of {{site.data.keyword.gitrepos}} across multiple regions.

When I attempt to add the {{site.data.keyword.gitrepos}} tool integration to my toolchain, I receive the following error message:
{: tsSymptoms}

`Repository URL is not valid. The repository must be on {local GitLab URL}.`

Where `{local GitLab URL}` is the URL of the {{site.data.keyword.gitrepos}} tool integration, in the region where the toolchain resides.
   
Because {{site.data.keyword.gitrepos}} is tightly integrated with the {{site.data.keyword.contdelivery_short}} service in the region in which they are running, you cannot use an instance of {{site.data.keyword.gitrepos}} across multiple regions.
{: tsCauses}

Instead of creating a {{site.data.keyword.gitrepos}} tool integration, create a generic GitLab integration and use this integration to point to the {{site.data.keyword.gitrepos}} repository (repo) in a different region.
{: tsResolve}

1. On the DevOps dashboard, on the Toolchains page, click the toolchain that you want to add this integration to. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain** and click **Overview**.
1. Click **Add a Tool**.
1. In the Tool Integrations section, click **GitLab**.
1. Click the GitLab server that you want to use. If the GitLab server where the repo you want to access resides does not appear in this list, add a custom server:

 a. Click **Add custom server**.

 b. Type a name for the server. This server name will appear in the list of available GitLab servers.
 
 c. Type the Root URL of the custom GitLab server.
 
 d. Enter a personal access token for your custom GitLab server. If you don't have a personal access token, [create one](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat).
 
 e. Click **Save custom integration**.
 
1. If you have a GitLab repo and want to use it, for the repository type, click **Existing** and type the URL.
1. If you want to use a new GitLab repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

 a. To create an empty repo, click **New**.

 b. To create a copy of a GitLab repo, click **Clone**.

 c. To fork a GitLab repo so that you can contribute changes through merge requests, click **Fork**.

1. If you want to create a public repo on the server, clear the **Make this repository private** check box.
1. If you want to use GitLab's Issues for issue tracking, select the **Enable GitLab Issues** check box.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** check box. For more information, see [Track where your code is deployed with toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:new_window}.
1. Click **Create Integration**.

For more information about configuring a GitLab tool integration, see [Configuring GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab).


## Why can't I create a toolchain from a template that uses a private repo in a different region?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

The toolchain template that you are using references a private {{site.data.keyword.gitrepos}} repo.

{{site.data.keyword.gitrepos}} is region-specific. When you try to create a toolchain from a template and target a region that the private repo isn't located in, the Git integration setup fails.
{: tsSymptoms}
   
When you add a {{site.data.keyword.gitrepos}} repo to a toolchain in a specific region, your IBM ID is mapped to a GitLab user name that gives you access to GitLab in that region. Even though your GitLab user name appears the same in all regions, the associated GitLab user is different in each region because each region has a separate installation of GitLab. Access to GitLab users in other regions isn't automatically granted to toolchains even when the GitLab user name appears to be the same.
{: tsCauses}

Make the {{site.data.keyword.gitrepos}} repo public so that it can be accessed from anywhere, including other {{site.data.keyword.Bluemix_notm}} regions.
{: tsResolve}

If the repo must be private, the repo owner can grant access to it by creating a [personal access token](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) on the GitLab server where the source repo is located. You need access only to the private repo to clone the content during the toolchain creation. The personal access token can be created with an expiry date to limit its lifetime to expire after one day. 

After you have a personal access token, you can create a URL to access the repo from other regions. While you are configuring the tool integration, in the **Source repository URL** field, update the repo URL to use your user name and access token.

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

Where `user` is your GitLab user name, `XXXXXXX` is the access token, [`group` ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window} is the group where the repo is stored, and `node-hello-world` is the repo name.

If your GitLab repo isn't located within a GitLab group, the value of `group` is the same as your user name.
{: tip}


## Why can't I clone my {{site.data.keyword.gitrepos}} repo over https?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

You must use a personal access token or an SSH key to perform Git operations.

You try to push or clone a repo from the command line by using https and cannot authenticate even though you entered the correct password.
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} uses a single sign-on mechanism that does not support Git authentication that uses a user name and password on the command line.
{: tsCauses}

To perform Git operations such as clone or push, you must use a personal access token or an SSH key. For more information about creating a personal access token or SSH key, see the [Getting started tutorial](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## Why am I prompted to authenticate when I try to clone my {{site.data.keyword.gitrepos}} repo by using SSH?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

There might be issues with the location or the permissions for your private SSH key, or the Git command line might not be using your private SSH key to authenticate with {{site.data.keyword.gitrepos}}.

I added my SSH public key by way of the {{site.data.keyword.gitrepos}} user interface. When I try to clone a repo by using SSH, I am prompted for a password or security code, or an error message is displayed indicating that the authentication failed.
{: tsSymptoms}
   
Any of the following SSH issues might prompt you to authenticate, or display an error message:
{: tsCauses}

* The Git command line might not be using your private SSH key to authenticate with {{site.data.keyword.gitrepos}}.

* Your private SSH key might not be in the default ~/.ssh/id_rsa location.

* Your private SSH key might not have the correct permissions (600).


Use any of the following methods to resolve this issue:
{: tsResolve}

* If you use the default private SSH key location, verify the permissions for the ~/.ssh/ folder and the ~/.ssh/id_rsa private key file. If the permissions are too broad, by default SSH does not use a private key. Make sure that the permissions for the  ~/.ssh/ folder are set to 700 and the permissions for the ~/.ssh/id_rsa folder are set to 600.

* If your private key is not in the default location, use the following command to specify it in an environment variable:

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* To debug this issue by using connection information, add the -v or the -vvv flag to the `GIT_SSH_COMMAND` environment variable:

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## I tried adding a user to my GitLab project by way of email, but they didn't receive the invitation. How do I add them to my project?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

The invitation might be blocked by the user's email.

I invited a user to my GitLab project by using their email address that is listed in {{site.data.keyword.gitrepos}}, but they didn't receive the email.
{: tsSymptoms}
   
The email might be blocked from the user's inbox by spam filters. 
{: tsCauses}

You can use any of the following methods to resolve this problem:
{: tsResolve}

* Check your email spam folder to determine whether the email invitation was marked as spam. Emails are sent from a noreply@ address. Update your spam filters to allow emails from this address.

* Investigate whether corporate spam filters that are outside of the user's control are blocking the email. Ask the user to log in to the {{site.data.keyword.gitrepos}} user interface and send you their user ID. You can add the user to the GitLab project by using their user ID.


## Why isn't the pipeline created properly when I create a toolchain from the template that I'm writing? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

Your pipeline might be missing resources such as jobs and stages due to an error in your pipeline.yaml definition.

When I attempt to create a toolchain from a template that I'm writing, I receive the following error message on the Pipeline page:
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

Typcially, this issue is caused by an error in your pipeline.yaml definition.
{: tsCauses}
   
You can use any of the following methods to debug this error:
{: tsResolve}

* Use the pipeline user interface to create an example pipeline that replicates the pipeline that you are trying to build with your template. Append `/yaml` to the pipeline URL to generate a similar pipeline.yaml file that you can use to look for obvious differences. For example, `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`.

* Use the headless toolchain creation mechanism. On the **Create a Toolchain** page, open the debugger and evaluate the `window.Testflags = {nocreate: 1}` expression. When you click **Create a Toolchain** in this mode, the toolchain is not created. Instead, the information that is passed to the API is returned to the console where you can review it.


## I configured a tool integration for my toolchain, why wasn't it configured?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

If an error occurs during the setup process or if the communication between the toolchain and the tool does not complete properly, the configuration fails.

After you add and configure a tool integration for your toolchain, an error message is displayed to indicate that the setup failed.
{: tsSymptoms}

When you add a tool integration, the toolchain communicates with the tool that is represented by the tool integration to provision any necessary resources and associate them with the toolchain. If an error occurs during the setup process or if the communication between the toolchain and the tool does not complete properly, the tool integration is put into an error state.
{: tsCauses}

 ![Setup failed error](images/tool_setup_failed.png)

You can try to configure the tool integration again:
{: tsResolve}

1. On its tool card, hover over the `Setup failed` message and click **Reconfigure**.

 ![Reconfigure button](images/tool_reconfigure.png)

1. Make sure that you are using valid configuration parameters. If the error was caused by an invalid configuration, an error message is displayed; for example, `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`. Update the settings for the tool integration and click **Save integration**.
1. If the error was caused by a communication problem, click **Save integration** to try again.


## Why can't I add {{site.data.keyword.contdelivery_short}} to a Cloud Foundry org?
{: troubleshoot-resource_groups}
{: troubleshoot}

You can no longer create instances of the {{site.data.keyword.contdelivery_short}} service in Cloud Foundry orgs. 

The following message is displayed on the Toolchains page for your toolchain in a Cloud Foundry org:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

When you click **Add the service** there is no option to create {{site.data.keyword.contdelivery_short}} in a Cloud Foundry org. You can only create {{site.data.keyword.contdelivery_short}} in a resource group.

Resource groups have replaced Cloud Foundry orgs as the preferred containers for service instances. However, you can still create toolchains in Cloud Foundry orgs to support pre-existing {{site.data.keyword.contdelivery_short}} instances in Cloud Foundry orgs.
{: tsCauses}

Create your toolchain again in resource groups, and then remove the original toolchain from the Cloud Foundry org. Alternatively, you can ignore the error message until a method to migrate existing toolchains from Cloud Foundry orgs to resource groups is provided.
{: tsResolve}


## Why can't I delete toolchains by using the `ibmcloud` CLI?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

Currently, you can't delete toolchains by using the ibmcloud resource CLI. 

I tried to delete a toolchain from the command line by using the `ibmcloud resource service-instance-delete` command, and the command fails with the following error message:
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

Toolchains are a special type of resource on the Cloud platform that you currently can't delete by using the `ibmcloud resource` CLI.
{: tsCauses}

To delete a toolchain:
{: tsResolve}

1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to delete. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. Click the **More Actions** menu, which is next to **View app**.
1. Click **Delete**. Deleting a toolchain removes all of its tool integrations, which might delete resources that are managed by those integrations.
1. Confirm the deletion by typing the name of the toolchain and clicking **Delete**.  


## Why is Live Edit unavailable after I commit and push to a repo?
{: #troubleshoot-liveedit}
{: troubleshoot}

When you deploy outside of the Eclipse Orion {{site.data.keyword.webide}}, Live Edit mode is cleared.

You commit and push a change from the command line or the {{site.data.keyword.webide}} and Live Edit is unavailable.
{: tsSymptoms}
   
When you create a toolchain that contains both a {{site.data.keyword.contdelivery_short}} pipeline and the {{site.data.keyword.webide}}, both tool integrations can deploy your application (app). By default, both the pipeline and the {{site.data.keyword.webide}} deploy to the same Cloud Foundry org and space, by using the same Cloud Foundry app and URL. When you deploy outside of the {{site.data.keyword.webide}}, Live Edit mode is cleared.
{: tsCauses}

To rapidly develop a test version of your app by using Live Edit, deploy to a different Cloud Foundry app, space, and URL from the {{site.data.keyword.webide}}. When your code changes are complete, you can commit and push the code to trigger the pipeline to build and deploy the production version of your app.
{: tsResolve}

1. From the run bar, select the launch configuration that you want to edit.
2. Edit the values that are specified for Space and Host.
3. Click **Save** and **Exit**.
4. Click the **Run** button in the run bar. You might need to deploy multiple times to enable the Live Edit button.

For more information about Live Edit, see [Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit).


## What does "not synchronized" mean in the {{site.data.keyword.webide}} run bar?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

The file system in your workspace is out of sync.

In Live Edit mode, the {{site.data.keyword.webide}} synchronizes files from your workspace with the running Cloud Foundry app and the files are out of sync.
{: tsSymptoms}
   
The file system in your workspace might become out of sync if the app is modified outside of the {{site.data.keyword.webide}}. It can also become out of sync if the {{site.data.keyword.webide}} can't retrieve the synchronization state from the app.
{: tsCauses}

The state might clear after a minute or two when normal communications are reestablished and the files are synchronized. Otherwise, you can start and stop the app with Live Edit mode enabled.
{: tsResolve}
