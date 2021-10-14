---

copyright:
  years: 2015, 2021
lastupdated: "2021-08-25"

keywords: troubleshoot, Delivery Pipeline, toolchains, tool integrations

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

# Troubleshooting for {{site.data.keyword.deliverypipeline}}
{: #troubleshoot-delivery-pipeline}

General problems with using {{site.data.keyword.deliverypipeline}} might include pipeline creation or tool integration configuration issues. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

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

  1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the **Toolchains** page, click the toolchain that you created to open the Overview page. Alternatively, on the App Details page in your app, click the toolchain name.
  1. On the card for the GitHub tool integration, click the menu to access the configuration options.
  1. Update the settings and click **Save Integration**.
  1. Click the card for the Delivery Pipeline tool integration to view the pipeline setup. 


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

   1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the **Toolchains** page, click the toolchain that contains the Git integration that you want to update to open its Overview page. Alternatively, on the App Details page in your app, click the toolchain name.
   1. On the card for the Git integration, click the menu to access the configuration options.
   1. Select the authorized Git account for the Git integration owner.
   1. Click **Save Integration**.
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
{:troubleshoot}
{: support}

Your firewall configuration prevents the {{site.data.keyword.deliverypipeline}} from communicating with environments that are behind a firewall.

When I attempt to use the {{site.data.keyword.deliverypipeline}}, it cannot communicate through my firewall.
{: tsSymptoms}

Your firewall must be configured to allow the {{site.data.keyword.deliverypipeline}} to communicate with environments that are behind a firewall.
{: tsCauses}

You can update your firewall configurations to allow the {{site.data.keyword.deliverypipeline}} to access resources that are behind the firewall. Use the following subnet ranges, for your specific region.
{: tsResolve}

```
jp-tok
128.168.108.0/26
128.168.68.192/27
128.168.69.104/29
128.168.69.176/29
128.168.69.96/29
128.168.75.240/29
128.168.94.24/29
128.168.97.136/29
161.202.125.136/29
161.202.133.88/29
161.202.235.192/27
161.202.236.208/29
161.202.94.176/29
165.192.107.64/26
165.192.68.72/29
165.192.70.184/29
165.192.70.208/29
165.192.70.32/27
165.192.74.72/29
165.192.82.240/29
165.192.92.208/29
169.56.10.128/26
169.56.44.32/29
169.56.46.80/29
169.56.46.88/29
====
jp-osa
163.68.72.136/29
163.68.72.208/29
163.68.72.224/29
163.68.73.16/29
163.68.73.192/27
163.68.73.24/29
163.68.73.80/28
163.69.65.16/28
163.69.65.240/29
163.69.65.248/29
163.69.65.40/29
163.69.66.160/29
163.69.67.224/27
163.73.66.240/29
163.73.67.232/29
163.73.67.240/28
163.73.67.8/29
163.73.68.0/27
163.73.68.32/29
====
au-syd
130.198.71.168/29
130.198.80.128/28
130.198.80.168/29
130.198.84.80/29
130.198.84.88/29
130.198.85.32/27
130.198.85.80/29
130.198.86.232/29
130.198.88.104/29
130.198.88.96/29
130.198.92.72/29
130.198.93.224/29
130.198.97.192/29
135.90.66.176/28
135.90.66.200/29
135.90.66.96/27
135.90.67.176/29
135.90.69.144/29
135.90.70.112/29
135.90.75.64/29
135.90.75.72/29
135.90.75.96/29
135.90.91.112/29
135.90.91.120/29
168.1.211.232/29
168.1.218.96/29
168.1.36.32/27
168.1.38.80/29
168.1.41.168/29
168.1.47.96/29
168.1.59.208/28
168.1.61.200/29
====
us-south
169.46.126.96/29
169.46.16.104/29
169.46.19.64/29
169.46.33.200/29
169.46.53.224/29
169.46.57.88/29
169.46.73.152/29
169.46.9.32/29
169.46.93.64/29
169.47.114.8/29
169.47.98.88/29
169.48.166.216/29
169.48.215.40/29
169.48.219.200/29
169.48.227.128/29
169.48.227.64/29
169.48.65.216/29
169.48.72.96/29
169.48.74.80/29
169.59.195.160/29
169.60.247.192/26
169.60.43.192/29
169.61.132.64/26
169.61.136.136/29
169.61.38.72/29
169.61.41.64/26
169.61.47.96/29
174.37.18.240/29
52.116.182.136/29
52.117.151.136/29
====
us-east
169.47.136.96/29
169.47.137.224/29
169.47.140.64/26
169.47.143.136/29
169.47.145.16/29
169.47.36.216/29
169.47.53.56/29
169.59.129.176/29
169.60.122.8/29
169.60.82.104/29
169.60.85.152/29
169.60.92.192/26
169.61.100.16/29
169.61.100.24/29
169.61.107.200/29
169.61.113.200/29
169.61.79.72/29
169.62.25.104/29
169.62.28.88/29
169.62.30.64/26
169.62.7.232/29
52.117.72.48/29
52.117.90.16/29
====
eu-gb
158.175.104.64/26
158.175.106.136/29
158.175.109.96/29
158.175.110.240/29
158.175.122.200/29
158.175.139.144/29
158.175.71.8/29
158.175.99.80/29
====
eu-de
149.81.102.232/29
149.81.114.128/29
149.81.114.64/29
149.81.122.0/26
149.81.70.64/29
149.81.73.136/29
149.81.73.160/27
149.81.74.112/29
149.81.81.120/29
158.177.198.40/29
158.177.204.24/29
158.177.215.136/29
158.177.69.96/29
159.122.111.24/29
159.122.94.200/29
159.122.96.192/27
159.122.98.240/29
161.156.123.96/29
161.156.129.96/29
161.156.150.248/29
161.156.157.120/29
161.156.157.192/26
161.156.77.128/27
161.156.77.192/29
161.156.78.32/29
161.156.91.232/29
161.156.94.56/29
169.50.34.48/29
169.50.53.0/26
====
ca-tor
158.85.66.168/29
158.85.67.192/27
158.85.80.184/29
163.74.68.176/29
163.74.68.224/28
163.74.68.240/29
163.74.68.248/29
163.74.69.104/29
163.74.69.64/27
163.75.66.144/28
163.75.66.176/29
163.75.66.184/29
163.75.67.240/29
163.75.67.248/29
163.75.68.0/27
163.75.68.128/29
169.53.175.144/29
169.53.183.48/28
169.53.186.144/29
169.55.139.120/29


```
{: screen}
