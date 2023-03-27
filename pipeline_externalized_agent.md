---

copyright:
  years: 2022, 2023
lastupdated: "2023-03-27"

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

As of Kubernetes version 1.14, Kustomize is included in Kubernetes to provide a declarative means of cluster configuration and Kubernetes object creation by using `yaml` files. To use externalized properties, your pipelines require a `kustomization.yaml` file.

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

To set up a pipeline to use external properties, you must specify two sets of attributes: *base properties* and *trigger properties*. 

*Base properties* represent the collection of properties and secrets that are global across trigger runs. You can find these values on the Environment Properties page within the pipeline UI. 

*Trigger properties* are the properties and secrets that are specified on an individual trigger. Property precedence means that trigger properties override base properties of the same name. While each pipeline has only one set of base properties, you can have many different sets of trigger properties.

Properties with the same name in the pipeline UI override any externalized properties.
{: important}

It is recommended that you separate your base properties and secrets by storing your base properties in a single folder within a Git repository (repo), and storing each trigger secret in its own separate folder.

### Base properties
{: #pipeline-base-properties}

A base properties folder must contain the following files:

* `.cdexternalpropbase`: An empty file that marks the current directory as containing externalized base properties.
* `environment-properties.env`: The externalized representation of nonsecure pipeline properties in key value pairs.
* `kustomization.yaml`: A YAML file that generates a configmap from the environment properties, and identifies the secret stores and external secrets that are defined in the directory.
* `external-secret-store.yaml`: An external secrets definition of an external secret store, such as [HashiCorp Vault](https://external-secrets.io/v0.6.1/provider/hashicorp-vault/#hashicorp-vault){: external}. You can have multiple stores that are used by different secrets.
* `external-secret.yaml`: An external secrets definition of a secret that is stored in the secret store that is defined in the `external-secret-store.yaml` file. You can have multiple external secrets.

#### Example
{: #base-properties-example}

Complete the following steps in the repo that you use to contain the externalized properties:

1. In the repo that contains the existing Tekton resource definitions, add a folder that is named `base`.
2. Add the path of this folder to your pipeline definitions.
3. In the `base` folder, add the `.cdexternalpropbase`, `environment-properties.env`, `kustomization.yaml`, `external-secret-store.yaml`, and `external-secret.yaml` files.
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

### Trigger properties
{: #pipeline-trigger-properties}

Make sure that each externalized trigger within a pipeline has its own trigger properties folder that contains the properties and external secrets to use for that trigger.

Each trigger properties folder must contain the following files:

* `.cdexternalproptrigger`: A file that marks the current directory as containing trigger properties. This file must have a JSON object with the name of the trigger, as shown in the following example.

   ```text
   {
       "triggerName" : "Deploy - External"
   }
   ```

* `trigger-properties.env`: The externalized representation of nonsecure pipeline properties within key value pairs.
* `kustomization.yaml`: A YAML file that generates a configmap from the trigger properties, and identifies the secret stores and external secrets that are defined in the directory.
* `external-secret.yaml`: An external secrets definition of a secret that is defined in the base folder.

#### Example
{: #externalized-properties-example}

Complete the following steps in the repo that you use to contain the externalized properties:

1. In the repo that contains the externalized properties, add a folder with a unique name such as `trigger[#]`.
2. Add the path of this folder to your pipeline definitions.
3. In the `base` folder, add the `.cdexternalproptrigger`, `trigger-properties.env`, `kustomization.yaml`, and `external-secret.yaml` files.
4. Update these files to match the properties that you want to externalize.

### Configuring a root secret
{: #root-secret-config}

To use external secrets, you must configure at least one secret store. This secret store requires its own access secret, named *root secret*.

You must add this root secret as a secure property to the Environment properties page of the pipeline that is being externalized. The root secret name must match the `secretRef.key` value that is specified in the `SecretStore` definition, for example, `vault_secret_id`.
