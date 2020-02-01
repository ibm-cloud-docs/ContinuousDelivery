---

copyright:
  years: 2015, 2020
lastupdated: "2020-01-30"

keywords: troubleshoot, GitHub integration, Git Repos and Issue Tracking integration, GitLab project, Delivery Pipeline, toolchains, tool integrations, Live Edit, Web IDE

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

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
  1. If you are creating the toolchain on {{site.data.keyword.cloud_notm}} Public and {{site.data.keyword.cloud_notm}} is not authorized to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.cloud_notm}} to access your GitHub account.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.cloud_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account.
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

1. If you want to create a public repo on the server, clear the **Make this repository private** checkbox.
1. If you want to use GitLab's Issues for issue tracking, select the **Enable GitLab Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.

For more information about configuring a GitLab tool integration, see [Configuring GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab).


## I created a toolchain and the {{site.data.keyword.deliverypipeline}} service doesn't initialize. Why doesn't the pipeline initialization complete?
{: troubleshoot-pipeline-initialization}
{: troubleshoot}

You might need to configure and save the GitHub tool integration again.

The GitHub tool integration within your toolchain might be misconfigured, which is preventing the pipeline initialization from completing. 
{: tsSymptoms}

An eventing problem occurred which caused the GitHub tool integration to fail.
{: tsCauses}

Configure and save the GitHub tool integration again:
{: tsResolve}

  1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain that you created to open the Overview page. Alternatively, on the App Details page in your app, click the toolchain name.
  1. On the card for the GitHub tool integration, click the menu to access the configuration options.
  1. Update the settings and click **Save Integration**.
  1. Click the card for the Delivery Pipeline tool integration to view the pipeline setup. 


## Why can't I create a toolchain from a template that uses a private repo in a different region?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}
{: support}

The toolchain template that you are using references a private {{site.data.keyword.gitrepos}} repo.

{{site.data.keyword.gitrepos}} is region-specific. When you try to create a toolchain from a template and target a region that the private repo isn't located in, the Git integration setup fails.
{: tsSymptoms}
   
When you add a {{site.data.keyword.gitrepos}} repo to a toolchain in a specific region, your IBM ID is mapped to a GitLab user name that gives you access to GitLab in that region. Even though your GitLab user name appears the same in all regions, the associated GitLab user is different in each region because each region has a separate installation of GitLab. Access to GitLab users in other regions isn't automatically granted to toolchains even when the GitLab user name appears to be the same.
{: tsCauses}

Make the {{site.data.keyword.gitrepos}} repo public so that it can be accessed from anywhere, including other {{site.data.keyword.Bluemix_notm}} regions.
{: tsResolve}

If the repo must be private, the repo owner can grant access to it by creating a [personal access token](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) on the GitLab server where the source repo is located. You need access only to the private repo to clone the content during the toolchain creation. The personal access token can be created with an expiry date to limit its lifetime to expire after one day. 

After you have a personal access token, you can create a URL to access the repo from other regions. While you are configuring the tool integration, in the **Source repository URL** field, update the repo URL to use your user name and access token.

`https://user:XXXXXXX@us-south.git.cloud.ibm.com/group/node-hello-world`

Where `user` is your GitLab user name, `XXXXXXX` is the access token, [group](https://us-south.git.cloud.ibm.com/help/user/group/index.md){: external} is the group where the repo is stored, and `node-hello-world` is the repo name.

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

```
  GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git
```

* To debug this issue by using connection information, add the -v or the -vvv flag to the `GIT_SSH_COMMAND` environment variable:

```
  GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git
```
```
  GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git
```


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
{: support}

Your pipeline might be missing resources such as jobs and stages due to an error in your pipeline.yaml definition.

When I attempt to create a toolchain from a template that I'm writing, I receive the following error message on the Pipeline page:
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

Typically, this issue is caused by an error in your pipeline.yaml definition.
{: tsCauses}
   
You can use any of the following methods to debug this error:
{: tsResolve}

* Use the pipeline user interface to create an example pipeline that replicates the pipeline that you are trying to build with your template. Append `/yaml` to the pipeline URL to generate a similar pipeline.yaml file that you can use to look for obvious differences. For example, `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`.

* Use the headless toolchain creation mechanism. On the **Create a Toolchain** page, open the debugger and evaluate the `window.Testflags = {nocreate: 1}` expression. When you click **Create a Toolchain** in this mode, the toolchain is not created. Instead, the information that is passed to the API is returned to the console where you can review it.


## I tried to deploy to Kubernetes by using the Delivery Pipeline, why am I getting an error about an invalid object? 
{: troubleshoot-cd-pipeline-kubernetes}
{: troubleshoot}

The 1.0 pipeline base image includes kubectl v1.14.2. You might receive an error if the Kubernetes cluster that you are connecting to is running a more recent version of Kubernetes. 

When I attempt to deploy to Kubernetes by using the Delivery Pipeline, I receive the following error message:
{: tsSymptoms}

`error:SchemaeError(io.k8s.api.core.v1.SecretProjection): invalid object doesn't have additional properties`

Typically, this issue is caused when the version of the kubectl command in your pipeline base image is incompatible with the version of Kubernetes that is running in the cluster.
{: tsCauses}
   
You can use any of the following methods to resolve this problem:
{: tsResolve}

* Use a more recent pipeline base image version, which when created includes the currently released version of kubectl. For information about how to specify the latest image version, see [Specifying the image version](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline_versioned_base_images#specify_base_image_version).

* Make sure that your pipeline job is running the correct version of kubectl. For example, add the following lines to the beginning of your pipeline job to run kubectl v1.14.2:

```
  curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.14.2/bin/linux/amd64/kubectl
  chmod +x ./kubectl
  sudo mv ./kubectl /usr/local/bin/kubectl
```

If you are running kubectl v1.14.2 from a 1.0 pipeline base image, the sudo option is not available. Replace the sudo line with the following command to add kubectl to your path:
```
   mkdir ~/.bin && export PATH=~/.bin:$PATH && mv ./kubectl ~/.bin/kubectl 
```

For more information about accessing the exact version of kubectl that you require, see [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux){: external}.
{: tip}


## Why is my {{site.data.keyword.deliverypipeline}} Private Worker inactive?
{: #troubleshoot-pw-inactive}
{: troubleshoot}
{: support}

Private workers within a pool of workers can be in one of the following states:

* Active with the current, supported version of private workers
* Inactive with an unsupported version of private workers
* Inactive

Your private worker is inactive. Inactive private workers cannot handle incoming run requests. Pipeline stages that use an inactive private worker cannot complete.
{: tsSymptoms}
   
There is an issue with your Kubernetes cluster and the worker cannot be contacted. Or, the version of the private worker that you are running is no longer supported.
{: tsCauses}

To activate your {{site.data.keyword.deliverypipeline}} private worker, [install](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers#install_pw) the private worker again. Then, [register](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers#register_pw) the {{site.data.keyword.deliverypipeline}} private worker on the Kubernetes cluster again.
{: tsResolve}


## I tried to install support for {{site.data.keyword.deliverypipeline}} Private Workers in Kubernetes. Why did the installation fail?
{: #troubleshoot-pw-install}
{: troubleshoot}
{: support}

If there is an issue with the version of kubectl that you are running on the client machine, the {{site.data.keyword.deliverypipeline}} Private Worker installation fails. 

After you try to install support for private workers in Kubernetes, an error message is displayed to indicate that there is a schema mismatch and the installation fails.
{: tsSymptoms}

`SchemaError(io.k8s.apimachinery.pkg.apis.meta.v1.APIGroup): invalid object doesn't have additional properties`
   
There is a mismatch between the versions of kubectl that you are running on the Kubernetes server and the Kubernetes client.
{: tsCauses}

Install the latest version of kubectl on the client machine.
{: tsResolve}


## Why can't I pull images for tekton-releases or pipeline-private-worker from some container registries?
{: #troubleshoot-pw-images}
{: troubleshoot}
{: support}

Cluster security prevents you from pulling down images. 

When you try to install the private worker framework, an error message is displayed.
{: tsSymptoms}

```
Error from server (InternalError): error when creating "https://private-worker-service.us-south.devops.cloud.ibm.com/install": Internal error occurred: admission webhook "trust.hooks.securityenforcement.admission.cloud.ibm.com" denied the request: 
Deny "gcr.io/tekton-releases/github.com/tektoncd/pipeline/cmd/controller@sha256:80e040a58ce6c4d58ae893eb934777bce013ef8be079967dc3db783d76fa5aaa", no matching repositories in ClusterImagePolicy and no ImagePolicies in the "tekton-pipelines" namespace
Error from server (InternalError): error when creating "https://private-worker-service.us-south.devops.cloud.ibm.com/install": Internal error occurred: admission webhook "trust.hooks.securityenforcement.admission.cloud.ibm.com" denied the request: 
Deny "gcr.io/tekton-releases/github.com/tektoncd/pipeline/cmd/webhook@sha256:da75fbdaeb800813d85b99f7f54b665e8d0edbb2c5a7ffc6a99d66aede0291a3", no matching repositories in ClusterImagePolicy and no ImagePolicies in the "tekton-pipelines" namespace

```
   
The private worker installer pulls images from `gcr.io` and [Docker hub](https://hub.docker.com/r/ibmcom/pipeline-private-worker){: external}. Some platforms, such as IBM Cloud Private, do not allow these container registries on the default image policy.
{: tsCauses}

Make sure that the policy for pulling images in your cluster supports pulling images from `gcr.io` and `docker.io`. For example, if you are installing the private worker framework on {{site.data.keyword.cloud_notm}} Private, add those policies by using the {{site.data.keyword.cloud_notm}} Private Web console. For more information about managing image security enforcement by using the IBM Cloud Private Web console, see [Enforcing container image security](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/manage_images/image_security.html){: external}.
{: tsResolve}


## I configured a tool integration for my toolchain, why wasn't it configured?
{: troubleshoot-tool-integration-error}
{: troubleshoot}
{: support}

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
{: support}

You can no longer create instances of the {{site.data.keyword.contdelivery_short}} service in Cloud Foundry orgs. 

The following message is displayed on the Toolchains page for your toolchain in a Cloud Foundry org:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

When you click **Add the service** there is no option to create {{site.data.keyword.contdelivery_short}} in a Cloud Foundry org. You can only create {{site.data.keyword.contdelivery_short}} in a resource group.

Resource groups have replaced Cloud Foundry orgs as the preferred containers for service instances. However, you can still create toolchains in Cloud Foundry orgs to support pre-existing {{site.data.keyword.contdelivery_short}} instances in Cloud Foundry orgs.
{: tsCauses}

Create your toolchain again in resource groups, and then remove the original toolchain from the Cloud Foundry org. Alternatively, you can ignore the error message until a method to migrate existing toolchains from Cloud Foundry orgs to resource groups is provided.
{: tsResolve}


## Why can't I create a toolchain to deploy my app to Cloud Foundry?
{: troubleshoot-deploy_cf}
{: troubleshoot}
{: support}

Before you can create a toolchain in a Cloud Foundry org, you must have an existing org and space, with the Developer role assigned. 

You try to create a toolchain to deploy your app to Cloud Foundry. After you enter your API key, the **Organization** and **Space** fields are empty and you cannot create your toolchain.
{: tsSymptoms} 

A Cloud Foundry org and space can't be located in your account.
{: tsCauses}

[Add a Cloud Foundry org and space to your account](https://cloud.ibm.com/account/cloud-foundry){: external}, and assign the Developer role to users at the space level. For more information about Cloud Foundry orgs and spaces, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
{: tsResolve}


## I tried to deploy a sample starter application to Cloud Foundry. Why did the deployment fail?
{: troubleshoot-sampleapp_deploy}
{: troubleshoot}
{: support}

You exceeded the memory limit for your Cloud Foundry org. 

I tried to deploy a sample starter application to Cloud Foundry. The deployment fails with the following error message:
{: tsSymptoms}

`You have exceeded your organization's memory limit: app requested more memory than available` 

You exceeded the memory limit for your Cloud Foundry org. This memory limit depends on your account settings. For example, users within Lite plan accounts are limited to 256 MB of memory. You might need to upgrade your account.
{: tsCauses}

Upgrade your account:
{: tsResolve}

1. Go to the [{{site.data.keyword.cloud_notm}} dashboard](https://cloud.ibm.com/resources){: external} and stop any apps that are not in use. Running apps only are counted to determine whether the memory limit is exceeded.
1. Reduce the minimum required memory that is specified in the app's `manifest.yml` file. Make sure that your app can still start with the reduced memory.
1. [Upgrade your account](https://cloud.ibm.com/account/settings){: external}. For more information about account types and upgrading your account, see [Account types](/docs/account?topic=account-accounts).


## Why can't I delete toolchains by using the `ibmcloud` CLI?
{: troubleshoot-delete_toolchains_cli}
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

1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to delete. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**.
1. Click the **More Actions** menu, which is next to **View app**.
1. Click **Delete**. Deleting a toolchain removes all of its tool integrations, which might delete resources that are managed by those integrations.
1. Confirm the deletion by typing the name of the toolchain and clicking **Delete**.

You can use the ibmcloud dev CLI to delete toolchains. After you [install the {{site.data.keyword.dev_cli_notm}} CLI plug-in](/docs/cli?topic=cloud-cli-install-devtools-manually), you can delete a toolchain from the command line by using the [`ibmcloud dev toolchain-delete`](/docs/cli?topic=cloud-cli-idt-cli#toolchain-delete) command. 
{: tip}


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


## Why can't I view my toolchains in my DevOps dashboard?
{: #view-toolchain-ts}
{: troubleshoot}

When you go to the DevOps dashboard, your toolchains aren't displayed.
{: tsSymptoms}

Your toolchain doesn't show in the toolchain unless you have the proper location selected. {{site.data.keyword.DRA_short}} is only available in three locations: Dallas, Frankfurt, and London.
{: tsCauses}

On your toolchain page, change the location to Dallas, Frankfurt, or London to show all of your {{site.data.keyword.DRA_short}} integrated toolchains.
{: tsResolve}


## How do I find toolchains that support {{site.data.keyword.DRA_short}}?
{: #find-toolchain-ts}
{: faq}

You can't find any toolchain templates that support {{site.data.keyword.DRA_short}}.
{: tsSymptoms}

Toolchains with {{site.data.keyword.DRA_short}} appear in the catalog when the correct locations are selected. {{site.data.keyword.DRA_short}} is available only in three locations: Dallas, Frankfurt, and London.
{: tsCauses}

Update your current location by completing the following steps:

1. Click the **menu** icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. From the **LOCATION** menu, select Dallas, Frankfurt, or London depending on your location.
3. Click **Create a Toolchain** to return to the toolchain templates page.
{: tsResolve}

