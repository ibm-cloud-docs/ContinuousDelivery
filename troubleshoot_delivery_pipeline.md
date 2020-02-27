---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-27"

keywords: troubleshoot, Delivery Pipeline, toolchains, tool integrations, private workers

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
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Troubleshooting for {{site.data.keyword.deliverypipeline}}
{: #troubleshoot-delivery-pipeline}

General problems with using {{site.data.keyword.deliverypipeline}} might include pipeline creation, tool integration configuration, or private worker issues. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

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


## I tried to deploy to Kubernetes by using the {{site.data.keyword.deliverypipeline}}, why am I getting an error about an invalid object? 
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
