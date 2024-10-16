---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-16"

keywords: troubleshoot, Delivery Pipeline, toolchains, tool integrations

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for {{site.data.keyword.deliverypipeline}}
{: #troubleshoot-delivery-pipeline}

General problems with using {{site.data.keyword.deliverypipeline}} might include pipeline creation or tool integration configuration issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

## I created a toolchain and the {{site.data.keyword.deliverypipeline}} service doesn't initialize. Why doesn't the pipeline initialization complete?
{: #troubleshoot-pipeline-initialization}
{: troubleshoot}

You might need to configure and save the GitHub tool integration again.

The GitHub tool integration within your toolchain might be misconfigured, which is preventing the pipeline initialization from completing. 
{: tsSymptoms}

An eventing problem occurred which caused the GitHub tool integration to fail.
{: tsCauses}

Configure and save the GitHub tool integration again:
{: tsResolve}

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**. On the **Toolchains** page, click the toolchain that you created to open the Overview page. Alternatively, on the App Details page in your app, click the toolchain name.
1. On the Toolchain's Overview page, on the **Repositories** card, locate the GitHub tool integration.
1. Click the menu to access the configuration options, update the settings, and click **Save Integration**.
1. On the **Delivery pipelines** card, click the {{site.data.keyword.deliverypipeline}} tool integration to view the pipeline setup.

## Why isn't the pipeline created properly when I create a toolchain from the template that I'm writing? 
{: #troubleshoot-cd-pipeline-creation}
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

## I tried to run a pipeline, why am I getting an error about access to the Git repository (repo)? 
{: #troubleshoot-cd-pipeline-git}
{: troubleshoot}

The pipeline uses an access token to clone the Git repo. If this access token isn't valid, the owner of the Git integration cannot access the Git repo. 

Supported Git integrations include the GitHub, GitLab, Bitbucket, or Git Repos and Issue Tracking tool integrations.
{: tip}

When I attempt to run a pipeline, I receive the following error message:
{: tsSymptoms}

`The access token for this git repository is no longer valid. Please reconfigure the git integration to ensure the integration owner has access to this repository.`

The access token that the pipeline uses to clone the Git repo is no longer valid. This issue might occur because the token was invalidated. The access token might also be invalid if the owner of the Git integration lost access to the repo because of permission changes.
{: tsCauses}
   
Configure and save the Git integration again:
{: tsResolve}

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**. On the **Toolchains** page, click the toolchain that contains the Git integration that you want to update to open its Overview page. Alternatively, on the App Details page in your app, click the toolchain name.
1. On the Toolchain's Overview page, on the **Repositories** card, locate the Git tool integration.
1. Click the menu to access the configuration options, select the authorized Git account for the Git integration owner, and click **Save Integration**.
1. Run your pipeline again.

## I tried to deploy to Kubernetes by using the {{site.data.keyword.deliverypipeline}}, why am I getting an error about an invalid object? 
{: #troubleshoot-cd-pipeline-kubernetes}
{: troubleshoot}

The 1.0 pipeline base image includes kubectl v1.14.2. You might receive an error if the Kubernetes cluster that you are connecting to is running a more recent version of Kubernetes. 

When I attempt to deploy to Kubernetes by using the Delivery Pipeline, I receive the following error message:
{: tsSymptoms}

`error:SchemaeError(io.k8s.api.core.v1.SecretProjection): invalid object doesn't have additional properties`

Typically, this issue is caused when the version of the kubectl command in your pipeline base image is incompatible with the version of Kubernetes that is running in the cluster.
{: tsCauses}

You can use any of the following methods to resolve this problem:
{: tsResolve}

* Use a more recent pipeline base image version, which when created includes the currently released version of kubectl. For information about how to specify the latest image version, see [Specifying the image version](/docs/ContinuousDelivery?topic=ContinuousDelivery-pipeline_versioned_base_images#specify_base_image_version).

* Make sure that your pipeline job is running the correct version of kubectl. For example, add the following lines to the beginning of your pipeline job to run kubectl v1.14.2:

```bash
  curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.14.2/bin/linux/amd64/kubectl
  chmod +x ./kubectl
  sudo mv ./kubectl /usr/local/bin/kubectl
```

If you are running kubectl v1.14.2 from a 1.0 pipeline base image, the sudo option is not available. Replace the sudo line with the following command to add kubectl to your path:

```bash
   mkdir ~/.bin && export PATH=~/.bin:$PATH && mv ./kubectl ~/.bin/kubectl 
```

For more information about accessing the exact version of kubectl that you require, see [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/#install-kubectl-on-linux){: external}.
{: tip}

## I tried to run a pipeline, why am I getting a 403 error from the {{site.data.keyword.registrylong_notm}}? 
{: #troubleshoot-cd-pipeline-cr}
{: troubleshoot}

The {{site.data.keyword.registrylong}} pipeline pushes and pulls images to and from the [{{site.data.keyword.registrylong_notm}}](/docs/Registry?topic=Registry-registry_overview). The {{site.data.keyword.registrylong_notm}} service plan determines the amount of storage and pull traffic that you can use for your private images.
{: tip}

When I attempt to run a pipeline, I receive the following error message:
{: tsSymptoms}

`Failed to pull image "us.icr.io/sdl-ns/achilles:a100-p203-6-20190717161046-78fbc8a3a0fbc8571d887e57499642e0326e7035": rpc error: code = Unknown desc = failed to pull and unpack image "us.icr.io/sdl-ns/achilles:a100-p203-6-20190717161046-78fbc8a3a0fbc8571d887e57499642e0326e7035": failed to copy: httpReaderSeeker: failed open: unexpected status code https://us.icr.io/v2/sdl-ns/achilles/blobs/sha256:365b19774a508fd998bc636981cb9869a406786ad811e51937fa6fb089c86005: 403 Forbidden`

You might have exceeded your [pull traffic quota limits](/docs/Registry?topic=Registry-registry_quota#registry_quota_get), which prevents the Docker image from being fetched.
{: tsCauses}

Review your [quota limits and usage](/docs/Registry?topic=Registry-registry_quota#registry_quota_get) for storing and pulling images. [Free up used storage and change service plans](/docs/Registry?topic=Registry-registry_quota#registry_quota_freeup) or quota limits to stay within given quota limits.
{: tsResolve}

## I tried to compile my app in a single pipeline job, why did it fail? 
{: #troubleshoot-compile-app}
{: troubleshoot}

You require 4 GB of memory (not file store) to build your app in a single pipeline job.

When I attempt to compile my app in a single pipeline job, the build job fails with an unexpected error.
{: tsSymptoms}

Your app requires more than 4 GB of memory to compile in a single pipeline job.
{: tsCauses}

To build your app in a single pipeline job:
{: tsResolve}

1. Create an [{{site.data.keyword.contdelivery_full}} Pipeline Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers).
1. Configure your build job to use the [private worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers#configure_private_worker_integration).
  
## Why can't the {{site.data.keyword.deliverypipeline}} communicate through a firewall?
{: #troubleshoot-firewall-configuration}
{: troubleshoot}
{: support}

Your firewall configuration prevents the {{site.data.keyword.deliverypipeline}} from communicating with environments that are behind a firewall.

When I attempt to use the {{site.data.keyword.deliverypipeline}}, it cannot communicate through my firewall.
{: tsSymptoms}

Your firewall must be configured to allow the {{site.data.keyword.deliverypipeline}} to communicate with environments that are behind a firewall.
{: tsCauses}

You can update your firewall configurations to allow the {{site.data.keyword.deliverypipeline}} to access resources that are behind the firewall. Use the [{{site.data.keyword.cis_short_notm}} allowlist](/docs/cis?topic=cis-cis-allowlisted-ip-addresses) and the [subnet ranges](/docs/ContinuousDelivery?topic=ContinuousDelivery-pipeline-subnet-ranges), for your specific region.
{: tsResolve}

## Why did I receive a notification that repo references are fixed in my pipeline triggers or definitions?
{: #troubleshoot-repo-references}
{: troubleshoot}

You changed, added, or removed repo integrations from your toolchain, which caused references to the integrations that are stored in the pipeline triggers or definitions to become invalid. 

When I change, add, or remove repo integrations from my toolchain, warning icons and validation errors are displayed in my pipeline configuration.
{: tsSymptoms}

In certain scenarios, when you change, add, or remove repo integrations from your toolchain, references to these integrations that are stored in the pipeline triggers or definitions might become invalid.
{: tsCauses}

If a matching repo integration is located in the toolchain, the pipeline attempts to automatically update these references to fix the invalid integration references. A notification is displayed in the UI with one of the following messages:
{: tsResolve}

* `Repository reference fixed in the following triggers: [list of triggers]`
* `Repository reference fixed in the following definitions: [list of definitions]`

If you see one of these notifications, but no warnings or errors are displayed in the configuration, no further action is required. If warnings or errors still appear, you might need to update or create the trigger or definition again. 

## Why does my pipeline time out when it tries to connect to {{site.data.keyword.cos_full_notm}} private endpoints?
{: #troubleshoot-private-endpoints}
{: troubleshoot}

When you run a pipeline, requests to the {{site.data.keyword.cos_full_notm}} that use a private endpoint time out with no response. This time out can cause the pipeline to fail.
{: tsSymptoms}

{{site.data.keyword.cos_full_notm}} private endpoints are not accessible from all {{site.data.keyword.cloud_notm}} cluster types. Private {{site.data.keyword.cos_full_notm}} endpoints are not accessible from private workers that run on clusters within an {{site.data.keyword.vpc_full}} (VPC).
{: tsCauses}

Replace any `s3.private.*` {{site.data.keyword.cos_full_notm}} endpoints with `s3.direct.*` endpoints. `s3.direct.*` endpoints are direct endpoints that communicate with {{site.data.keyword.cos_full_notm}} from any {{site.data.keyword.cloud_notm}} cluster type. 
{: tsResolve}

## Why does my pipeline fail with an error that is related to secure properties?
{: #troubleshoot-secure-properties}
{: troubleshoot}

PipelineRuns fails with an error when any of the secure properties in the pipeline don't resolve at the start of the pipeline run.
{: tsSymptoms}

Pipelines that cannot retrieve a secret value from a secrets store or from either Secrets Manager, Key Protect, or HashiCorp Vault, fail with an error message that indicates which properties cannot be resolved. Resolution failures can occur even if the properties are not used directly in the triggered run. For example, resolution failures might occur if the path to the secret in the store is no longer valid, the secret store is inaccessible, or for authorization issues.
{: tsCauses}

If your pipelines contain secure properties that do not currently resolve, update these properties to refer to valid, retrievable secrets that are located in Secrets Manager, Key Protect, or HashiCorp Vault.
{: tsResolve}

Make sure that your pipeline specifies only those secure properties that are required for the successful completion of a triggered `PipelineRun` as pipeline trigger properties, instead of as pipeline level environment properties. Use pipeline level environment properties only when required.
{: important}

## Why does my pipeline report an error fetching the pipeline definition?
{: #troubleshoot-pipeline-definition}
{: troubleshoot}

An error appears on the {{site.data.keyword.deliverypipeline}} page in relation to fetching the pipeline definition. Alternatively, the error appears when attempting to trigger a PipelineRun.
{: tsSymptoms}

There are a number of reasons why a failure can occur when fetching the definition for a pipeline. For example, if the definition is defined in a very large repository, the request to fetch the definition can time out due to a delay in cloning the large repository before building the definition. Another example is when a definition input is targeted at a branch or path that no longer exists in the repository.
{: tsCauses}

Try resolving the problem by using one of the following options:
{: tsResolve}

* Reload the page to initiate a new request to fetch the definition. If this fails repeatedly, continue with the following options.
* Validate that all referenced branches and paths in your definition inputs match with resources that exist in the repository.
* Reduce the size of the repository containing your Tekton definition. Remove unnecessary files from the repository and update your `.gitignore` to exclude uploading any unnecessary files.
* Only include the minimum necessary files of your pipeline definition -- do not target your entire repository. Move all Tekton definition related files to a subfolder of your repository, then edit the definition input in your {{site.data.keyword.deliverypipeline}} settings to target the path at the subfolder. This option reduces the time necessary to clone the definition files from your repository.
* For large Tekton definitions, consider splitting the definition into multiple folders or multiple repositories. Then update the definition inputs in your {{site.data.keyword.deliverypipeline}} to target the necessary folders or repos.

The computed pipeline definition size limit is 1 MB. If you encounter errors when you save or run your pipeline, you might need to reduce the size of your pipeline definition, or split it into multiple pipelines.
{: important}

## Why does my pipeline fail to connect to a {{site.data.keyword.openshiftlong_notm}} cluster?
{: #troubleshoot-roks-access}
{: troubleshoot}

Pipelines that attempt an `oc login` can't log in to the target cluster that's running {{site.data.keyword.openshiftlong_notm}} version 4.13 and later.
{: tsSymptoms}

The issue is caused by change that is introduced in version 4.13 of [{{site.data.keyword.openshiftlong_notm}}](/docs/openshift?topic=openshift-cs_versions_413).  
{: tsCauses}

To work around the issue, use the following process:
```text
ibmcloud login --apikey "${IBMCLOUD_API_KEY}" -r "${REGION}" -g "${RESOURCE_GROUP}"
ibmcloud oc cluster config --cluster "${CLUSTER_NAME}" --endpoint private --admin
kubectl config current-context
oc version
oc get pods -A  # To verify connection
```
{: tsResolve}

## Why does my pipeline fail when executing a Git clone command?
{: #troubleshoot-git-clone}
{: troubleshoot}

Tekton Pipelines that are using the `git-clone-repo` command task might fail with the following error displayed: 
```sh
Clone was not successful. Code 128 - Retrying shortly... 
fatal: destination path '.' already exists and is not an empty directory.
```
{: tsSymptoms}

The issue is caused by a performance change in the infrastructure of the public managed pipeline workers. 
{: tsCauses}

To resolve this issue:
- Locate the tekton definitions under Settings for your pipeline and find the entry for `git` under Path. Click the repository link to open. Navigate to  `git/task-clone-repo.yaml` and then within that file find the `clone-repo` step. See the [Tekton Catalog example](https://github.com/open-toolchain/tekton-catalog/blob/master/git/task-clone-repo.yaml#L261) for the latest code for reference. 
- Add `rm -rf "lost+found"` to the definition prior to the `git clone` call. This ensures the directory for cloning is empty.
- Run the pipeline again.
{: tsResolve}

## Why does my pipeline fail to start on managed workers when executed from a trial account?
{: #troubleshoot-trial-account}
{: troubleshoot}

Classic pipelines that are executed from a trial account won't start due to the following error:
```text
This type of account is not entitled to use managed workers. Private workers can be used instead or to gain access managed worker capability the account must be upgraded to a paid plan.
```
{: tsSymptoms}

This behavior is caused by a revision of the permissions for trial accounts.
{: tsCauses}

Try the following options to resolve this issue:
- Execute your pipelines using a private worker running on your own cluster.
- Upgrade your trial account to a [Pay-As-You-Go](/docs/account?topic=account-accounts) account with a Lite plan.

## Why does my pipeline fail to trigger for pull request events from forked repositories?
{: #troubleshoot-fork-event}
{: troubleshoot}

Pipelines by default do not respond to pull request events from forked repositories
{: tsSymptoms}

This behavior is by design to prevent inadvertent execution of pipelines.
{: tsCauses}

To enable pipelines to execute on events from forked repositories do the following:

Tekton Pipelines: On the git trigger panel, enable the `Include pull request events from forks` toggle
Classic Pipelines: On the Input tab of the stage configuration, enable the `Include pull request events from forks` toggle 
