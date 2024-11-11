---

copyright:
  years: 2023, 2024
lastupdated: "2024-10-25"

keywords: private workers integration, delivery pipeline, tekton chains

subcollection: ContinuousDelivery

---

# Using Tekton chains to manage supply chain security
{: #slsa-whatis}

Supply chain Levels for Software Artifacts (SLSA) is a security framework. SLSA is a checklist of standards and controls to prevent tampering, improve integrity, and secure packages and infrastructure in your projects, businesses, or enterprises. SLSA gets you from safe enough to being as resilient as possible, at any link in the chain.

To achieve SLSA level 3, Tekton pipelines are using the Tekton Chains. Tekton Chains is a Kubernetes Custom Resource Definition (CRD) controller that you can use to manage your supply chain security in Tekton.
For more information, see the [Tekton Chains documentation](https://github.com/tektoncd/chains).

## Setting up Tekton Chains on a private worker
{: #setup-chains-privateworker}

Use the command line to install the Tekton framework, the private worker agent framework, and the Tekton Chain framework. Add `&chains=true` to the command line to install the private worker framework. For example, on an {{site.data.keyword.containerlong_notm}} cluster, you can use the following command:

```text
kubectl apply --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/install?type=iks&olm=false&chains=true"
```

See the following example output:
```text
namespace/tekton-pipelines created
clusterrole.rbac.authorization.k8s.io/tekton-pipelines-controller-cluster-access created
clusterrole.rbac.authorization.k8s.io/tekton-pipelines-controller-tenant-access created
clusterrole.rbac.authorization.k8s.io/tekton-pipelines-webhook-cluster-access created
role.rbac.authorization.k8s.io/tekton-pipelines-controller created
role.rbac.authorization.k8s.io/tekton-pipelines-webhook created
role.rbac.authorization.k8s.io/tekton-pipelines-leader-election created
role.rbac.authorization.k8s.io/tekton-pipelines-info created
serviceaccount/tekton-pipelines-controller created
serviceaccount/tekton-pipelines-webhook created
clusterrolebinding.rbac.authorization.k8s.io/tekton-pipelines-controller-cluster-access created
clusterrolebinding.rbac.authorization.k8s.io/tekton-pipelines-controller-tenant-access created
clusterrolebinding.rbac.authorization.k8s.io/tekton-pipelines-webhook-cluster-access created
rolebinding.rbac.authorization.k8s.io/tekton-pipelines-controller created
rolebinding.rbac.authorization.k8s.io/tekton-pipelines-webhook created
rolebinding.rbac.authorization.k8s.io/tekton-pipelines-controller-leaderelection created
rolebinding.rbac.authorization.k8s.io/tekton-pipelines-webhook-leaderelection created
rolebinding.rbac.authorization.k8s.io/tekton-pipelines-info created
customresourcedefinition.apiextensions.k8s.io/clustertasks.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/customruns.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/pipelines.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/pipelineruns.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/resolutionrequests.resolution.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/tasks.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/taskruns.tekton.dev created
customresourcedefinition.apiextensions.k8s.io/verificationpolicies.tekton.dev created
secret/webhook-certs created
validatingwebhookconfiguration.admissionregistration.k8s.io/validation.webhook.pipeline.tekton.dev created
mutatingwebhookconfiguration.admissionregistration.k8s.io/webhook.pipeline.tekton.dev created
validatingwebhookconfiguration.admissionregistration.k8s.io/config.webhook.pipeline.tekton.dev created
clusterrole.rbac.authorization.k8s.io/tekton-aggregate-edit created
clusterrole.rbac.authorization.k8s.io/tekton-aggregate-view created
configmap/config-defaults created
configmap/feature-flags created
configmap/pipelines-info created
configmap/config-leader-election created
configmap/config-logging created
configmap/config-observability created
configmap/config-registry-cert created
configmap/config-spire created
deployment.apps/tekton-pipelines-controller created
service/tekton-pipelines-controller created
namespace/tekton-pipelines-resolvers created
clusterrole.rbac.authorization.k8s.io/tekton-pipelines-resolvers-resolution-request-updates created
role.rbac.authorization.k8s.io/tekton-pipelines-resolvers-namespace-rbac created
serviceaccount/tekton-pipelines-resolvers created
clusterrolebinding.rbac.authorization.k8s.io/tekton-pipelines-resolvers created
rolebinding.rbac.authorization.k8s.io/tekton-pipelines-resolvers-namespace-rbac created
configmap/bundleresolver-config created
configmap/cluster-resolver-config created
configmap/resolvers-feature-flags created
configmap/config-leader-election created
configmap/config-logging created
configmap/config-observability created
configmap/git-resolver-config created
configmap/hubresolver-config created
deployment.apps/tekton-pipelines-remote-resolvers created
horizontalpodautoscaler.autoscaling/tekton-pipelines-webhook created
deployment.apps/tekton-pipelines-webhook created
service/tekton-pipelines-webhook created
customresourcedefinition.apiextensions.k8s.io/batchpolls.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/cryptodetectors.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/pwtaskruns.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/localpipelines.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/workeragents.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/pwaconfigs.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/taskpayloads.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/cdpipelineruns.devops.cloud.ibm.com created
customresourcedefinition.apiextensions.k8s.io/steplogs.devops.cloud.ibm.com created
configmap/private-worker-agent-config-defaults created
deployment.apps/private-worker-agent created
role.rbac.authorization.k8s.io/private-worker-agent created
rolebinding.rbac.authorization.k8s.io/private-worker-agent created
serviceaccount/private-worker-agent created
clusterrolebinding.rbac.authorization.k8s.io/pwa-manager-rolebinding created
clusterrole.rbac.authorization.k8s.io/manager-role created
clusterrolebinding.rbac.authorization.k8s.io/external-secret-update-role created
serviceaccount/external-secret-update-role created
job.batch/extsecret-install-1697655985441 created
namespace/tekton-chains created
secret/signing-secrets created
configmap/chains-config created
deployment.apps/tekton-chains-controller created
clusterrolebinding.rbac.authorization.k8s.io/tekton-chains-controller-cluster-access created
clusterrole.rbac.authorization.k8s.io/tekton-chains-controller-cluster-access created
clusterrole.rbac.authorization.k8s.io/tekton-chains-controller-tenant-access created
clusterrolebinding.rbac.authorization.k8s.io/tekton-chains-controller-tenant-access created
serviceaccount/tekton-chains-controller created
role.rbac.authorization.k8s.io/tekton-chains-leader-election created
rolebinding.rbac.authorization.k8s.io/tekton-chains-controller-leaderelection created
role.rbac.authorization.k8s.io/tekton-chains-info created
rolebinding.rbac.authorization.k8s.io/tekton-chains-info created
configmap/chains-info created
configmap/config-logging created
configmap/tekton-chains-config-observability created
service/tekton-chains-metrics created
```
{: codeblock}

Next, you need to set the private and public key pair that's used for signing by Tekton Chains. For more information, see the [Tekton Chains documentation](https://github.com/tektoncd/chains).

## Triggering Tekton Chains
{: #trigger-chains}

To trigger Tekton Chains for your pipeline, add the task results to your Tekton task definitions. You need two task results:

* one that has a name that matches `*_IMAGE_DIGEST`
* one that has a name that matches `*_IMAGE_URL`

For example:
```text
...
   results:
    - name: APP_IMAGE_DIGEST
      description: The digest of the built image
    - name: APP_IMAGE_URL
      description: The url of the built image
...
```
Your task needs to set these two results within its script. You can also use any mechanism used by Tekton Chains.

## Pushing attestations to the image registry
{: #push-attestations}

By default, Tekton Chains is configured to save the attestation and signature to the oci registry. If you want to change the default behavior, edit the config map `chains-config` that's located in the `tekton-chains` namespace. For more information, see the [Tekton Chains documentation](https://github.com/tektoncd/chains).

## Verifying signatures
{: #verify-signatures}

To verify the signatures, you can use `cosign` as explained in the [Chains Signal Provenance Tutorial](https://github.com/tektoncd/chains/blob/main/docs/tutorials/signed-provenance-tutorial.md).

When running on managed workers, you can retrieve the public key that's used for validation by using the private-worker endpoint `https://private-worker-service.{REGION}.devops.cloud.ibm.com/chains/public_key`. You can save the contents returned by this endpoint to a file and use that file as your public key in the `cosign` command line.

## Downloading signature and attestation
{: #downloading-signature-and-attestation}

To get the attestation or signature itself, you need to use the `cosign` tool with the command `download signature` or `download attestation`.
