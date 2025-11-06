---

copyright:
  years: 2015, 2025
lastupdated: "2025-10-30"

keywords: troubleshoot, private workers

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Troubleshooting for Pipeline Private Workers
{: #troubleshoot-pipeline-private-workers}

General problems with using Pipeline Private Workers might include Kubernetes cluster and kubectl version issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

## Why is my {{site.data.keyword.deliverypipeline}} Private Worker inactive?
{: #troubleshoot-pw-inactive}
{: troubleshoot}
{: support}

Private workers within a pool of workers can be in one of the following states:

* Active with the current, supported version of private workers
* Inactive with an unsupported version of private workers
* Inactive and Unregistered

Your private worker is inactive. Inactive private workers cannot handle incoming run requests. Pipeline stages that use an inactive private worker cannot complete.
{: tsSymptoms}
   
An agent can become inactive

1. if there is an issue with your Kubernetes cluster and the worker cannot communicate with the regional control plan services
2. if the version of the private worker that you are running is no longer supported
3. if the agent on the cluster has become Unregistered
{: tsCauses}

If the agent is reporting Unregistered after previously working, you can attempt to fix the registration by running the following command

`kubectl patch worke${AGENT_NAME} --subresource=status --type=merge -p '{"status": {"registrationStatus": {"state": "Succeeded"}}}'`

If the preceding command fails or if your {{site.data.keyword.deliverypipeline}} private worker is registered but still is inactive you can install the private worker again. Register the {{site.data.keyword.deliverypipeline}} private worker on the Kubernetes cluster again.
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

```text
Error from server (InternalError): error when creating "https://private-worker-service.us-south.devops.cloud.ibm.com/install": Internal error occurred: admission webhook "trust.hooks.securityenforcement.admission.cloud.ibm.com" denied the request: 
Deny "ghcr.io/tekton-releases/github.com/tektoncd/pipeline/cmd/controller@sha256:80e040a58ce6c4d58ae893eb934777bce013ef8be079967dc3db783d76fa5aaa", no matching repositories in ClusterImagePolicy and no ImagePolicies in the "tekton-pipelines" namespace
Error from server (InternalError): error when creating "https://private-worker-service.us-south.devops.cloud.ibm.com/install": Internal error occurred: admission webhook "trust.hooks.securityenforcement.admission.cloud.ibm.com" denied the request: 
Deny "ghcr.io/tekton-releases/github.com/tektoncd/pipeline/cmd/webhook@sha256:da75fbdaeb800813d85b99f7f54b665e8d0edbb2c5a7ffc6a99d66aede0291a3", no matching repositories in ClusterImagePolicy and no ImagePolicies in the "tekton-pipelines" namespace

```
   
The private worker installer pulls images from `icr.io`. Some platforms, such as IBM Cloud Private, do not allow these container registries on the default image policy.
{: tsCauses}

Make sure that the policy for pulling images in your cluster supports pulling images from `icr.io`. For example, if you are installing the private worker framework on {{site.data.keyword.cloud_notm}} Private, add those policies by using the {{site.data.keyword.cloud_notm}} Private Web console. For more information about managing image security enforcement by using the IBM Cloud Private Web console, see [Enforcing container image security](https://www.ibm.com/docs/en/cloud-private/3.2.x?topic=images-enforcing-container-image-security){: external}. For more information about managing image security enforcement by using Porteris, see [Portieris Policies](https://github.com/IBM/portieris/blob/main/POLICIES.md){: external}.
{: tsResolve}

The following example shows how to use the IBM Cloud CLI to create the ClusterImagePolicy:

If you use Portieris as an admission controller, you might need to change the `apiVersion` in the example to `portieris.cloud.ibm.com/v1`.
{: tip}

```text
cat <<EOF | kubectl apply -f -
apiVersion: securityenforcement.admission.cloud.ibm.com/v1beta1
kind: ClusterImagePolicy
metadata:
  name: iks-private-registries
spec:
  repositories:
  - name: "*.icr.io/*"
    policy:
EOF
```

## Why is my {{site.data.keyword.deliverypipeline}} Private Worker not listed?
{: #troubleshoot-pw-listed}
{: troubleshoot}
{: support}

My private worker agent is listed on the cluster with a status of `inactive`, but it is not listed on the private worker integration Overview page.
{: tsSymptoms}
   
The API key that was used to install the worker agent might not be included in the `ServiceID` that is used by the private worker integration. 
{: tsCauses}

Remove the misconfigured worker agent from the cluster and install the worker agent again. Make sure that the API key that is included in the installation command also exists in the `ServiceId` that is used in the same installation command. Use the link for the `ServiceId` that is available on both the private worker integration page and the Identity and Access Management (IAM) page to generate a valid API key.
{: tsResolve}
