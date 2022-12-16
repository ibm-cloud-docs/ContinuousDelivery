---

copyright:
  years: 2022
lastupdated: "2022-12-15"

keywords: Delivery Pipeline Private Workers, externalized mode, private worker, kustomize, external secrets

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Using {{site.data.keyword.deliverypipeline}} Tekton Pipelines with externalized properties
{: #external-properties}

You can run pipelines that contain pipeline properties that are not stored with the {{site.data.keyword.deliverypipeline}}. By using these externalized properties, you can manage pipeline environment properties in a Git repository (repo) and use version control and tracking.
{: shortdesc}

After a pipeline is externalized, pipeline runs occur in the same way, depending on the triggers that are configured for the pipeline. The values of any properties that are externalized and specified by way of the pipeline UI are overridden by the values in the UI when the property names and property types match.

## Configuring a pipeline to use externalized properties
{: #external-properties-config}

The latest private worker agent versions support external properties natively. This support uses [Kustomize](https://kustomize.io/){: external} and [External Secrets](https://external-secrets.io/){: external}, and requires a pipeline that is configured to use external properties. 

As of Kubernetes version 1.14, Kustomize is included in Kubernetes to provide a declarative means of cluster configuration and Kubernetes object creation by using `yaml` files. To use externalized properties, your pipelines require a `kustomize.yaml` file.

By using the External Secrets operator, you can synchronize secrets from external APIs with Kubernetes secrets. Supported providers include [{{site.data.keyword.secrets-manager_full}}](/docs/secrets-manager?topic=secrets-manager-getting-started). By using the operator, you can represent secrets and providers within `yaml` files that are stored in a repo, such as Git. To use externalized secure properties, your pipeline definitions must provide `yaml` files that define both a `SecretStore` and an `ExternalSecret`. 

### Configuring a cluster
{: #cluster-config}

Pipelines with externalized environment properties are supported on [pipeline private worker installations](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers&interface=ui) at version 0.14.9 or later, or on IBM-provided managed workers.

If you are using your own private worker, you must run the following command on the cluster that hosts that worker.

```text
kubectl set env deployment/private-worker-agent -n tekton-pipelines ENABLE_CDPR="true"
```
{: codeblock}

For more information about the images that the private worker installation places on a cluster, see [Pipeline Private Worker images](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers&interface=ui#private-workers-images).

### Configuring a pipeline
{: #pipeline-config}

To configure a pipeline to use external properties, you must add a pipeline definition entry to the Definitions page. Make sure that this entry references a path to the location within your repo that contains the following files:

* `environment-properties.env`: The externalized representation of nonsecure pipeline properties in key value pairs.
* `kustomization.yaml`: The kustomization file that is used at the start of a pipeline run.
* `external-secret-store.yaml`: An External Secrets definition of an external secret store such as [HashiCorp Vault](https://external-secrets.io/v0.6.1/provider/hashicorp-vault/#hashicorp-vault){: external}.
* `external-secret.yaml`: An External Secrets definition of a secret stored in the secret store that is defined in the `external-secret-store.yaml` file.

For example, complete the following steps in the repo that contains the existing Tekton resource definitions:

1. Add a folder named `base`.
2. Add the path of this folder to your pipeline definitions.
3. In the `base` folder, add the `environment-properties.env`, `kustomization.yaml`, `external-secret-store.yaml`, and `external-secret.yaml` files.
4. Update these files to match the properties that you want to externalize.

#### Example externalized `environment-properties.env` file
{: #externalized-env-prop-file}

```text
## Pipeline Environment Properties: base/environment-properties.env
REGION=eu-de
BRANCH=main
CLUSTER_NAMESPACE=default
pipeline-debug=0
```
{: codeblock}

#### Example externalized `kustomization.yaml` file
{: #externalized-kustomization-file}

```text
## Pipeline Kustomize file: base/kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
commonLabels:
  devops.cloud.ibm.com/cd: kustomize
generatorOptions:
  disableNameSuffixHash: true
resources:
  - external-secret.yaml
  - external-secret-store.yaml
configMapGenerator:
  - name: environment-properties
    envs:
      - environment-properties.env
```
{: codeblock}

#### Example externalized `external-secret-store.yaml` file
{: #externalized-secret-store-file}

```text
## Pipeline Hashicorp vault secret store: base/external-secret-store.yaml
apiVersion: external-secrets.io/v1beta1
kind: SecretStore
metadata:
  name: hv-vault-backend
spec:
  provider:
    vault:
      server: "https://VAULT:PORT"
      path: ""
      version: "v1"
      auth:
        appRole:
          path: "approle"
          roleId: "12345678-1234-1234-1234-123456789012"
          # Reference to a key in a K8 Secret that contains the App Role SecretId
          secretRef:
            name: "secure-properties"
            key: "vault_secret_id"
```
{: codeblock}

#### Example externalized `external-secret.yaml` file
{: #externalized-external-secret-file}

```text
## Pipeline secure property stored externally: base/external-secret.yaml
apiVersion: external-secrets.io/v1beta1
kind: ExternalSecret
metadata:
  name: "my-external-secret"
spec:
  secretStoreRef:
    name: hv-vault-backend
    kind: SecretStore
  refreshInterval: "0s"
  target:
    name: mysecrets
    creationPolicy: "Owner"
    deletionPolicy: "Delete"
  data:
  - secretKey: API_KEY
    remoteRef:
      key: VAULT/PATH/my-ibmcloud-apikey
      property: value
```
{: codeblock}

### Configuring a root secret
{: #root-secret-config}

To use external secrets, you must configure at least one secret store. This secret store requires its own access secret, named *root secret*.

You must add this root secret as a secure property to the Environment properties page of the pipeline that is being externalized. The root secret name must match the `secretRef.key` value that is specified in the `SecretStore` definition, for example, `vault_secret_id`.
