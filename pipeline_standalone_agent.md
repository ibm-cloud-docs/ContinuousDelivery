---

copyright:
  years: 2022
lastupdated: "2022-11-21"

keywords: Delivery Pipeline Private Workers, stand-alone mode, private worker

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Using {{site.data.keyword.deliverypipeline}} Private Workers in stand-alone mode
{: #standalone-mode-private-workers}

You can use a private worker in stand-alone mode and run a pipeline that is stand-alone from {{site.data.keyword.cloud_notm}}. 
{: shortdesc}

By running a pipeline in stand-alone mode, you can "break glass" and restore functionality during a Customer Impacting Event (CIE). In stand-alone mode, you can also run a pipeline that requires resources that are available only in a restricted environment. You can also develop locally while you are running a pipeline in stand-alone mode.

## Running a pipeline in {{site.data.keyword.contdelivery_full}} versus stand-alone mode
{: #standalone_mode_cd}

Pipeline payloads that run in a {{site.data.keyword.contdelivery_short}} pipeline are processed in the {{site.data.keyword.cloud_notm}}. Pipelines that run in stand-alone mode are processed in-cluster by the agent and can run without any connection to the {{site.data.keyword.contdelivery_short}} pipeline infrastructure. To run in-cluster, pipelines that run in stand-alone mode must have access to all of the properties and secrets that they require. You can convert an existing {{site.data.keyword.contdelivery_short}} pipeline to run in stand-alone mode.

## Converting an existing pipeline to stand-alone mode
{: #standalone_mode_convert}

To run a pipeline in stand-alone mode, you must externalize all of the environment values and secrets so that the stand-alone agent can resolve and transform them. The pipeline UI provides an externalize properties option to help externalize these values and secrets. 

From the **Other settings** page within the pipeline UI, click **Download zip file**. The downloaded .zip file contains the following content: 

```text
├── README.md
├── base
│   ├── standalone.yaml
│   ├── environment-properties.env
│   ├── kustomization.yaml
│   └── secure-properties.env
└── triggers
    ├── trigger1
    │   ├── standalone-patch.yaml
    │   ├── environment-properties.env
    │   ├── kustomization.yaml
    │   └── secure-properties.env
    ├── trigger2
    │   ├── standalone-patch.yaml
    │   ├── environment-properties.env
    │   ├── kustomization.yaml
    │   └── secure-properties.env
    ...
    ├── trigger n
    │   ├── standalone-patch.yaml
    │   ├── environment-properties.env
    │   ├── kustomization.yaml
    │   └── secure-properties.env
```
{: codeblock}

This file contains a series of Kustomize folders that include a base folder that contains the pipeline's main config vars and secrets (exported from the env var tab) and one or more individual trigger overlay folders that contain specific trigger properties and secrets. A `standalone.yaml` file is added to the base folder that contains the repo definitions that are required to run this pipeline.

The exported properties are separated into two Kustomize files: `environment-properties.env` (for configMap values) and `secure-properties.env` (for secrets). The `environment-properties.env` file is a flat list of key:value pairs. The `secure-properties.env` file contains the key of the secret and a special reference format that is resolved at pipeline run time. This file also contains the key for by value secrets, by using `*********` for the value to prevent secret exposure.

### Using Kustomize
{: #standalone_mode_kustomize}

The agent in stand-alone mode now supports [Kustomize](https://kustomize.io/). A pipeline might contain multiple definitions, some of which include Kustomize and others that don't. By using the agent in stand-alone mode, you can process each repo independently and then merge the results to create the final pipeline. The order that the repos are defined in is respected.

### Specifying a trigger
{: #standalone_mode_pipeline_trigger}

You can continue to use the pipeline UI to connect external triggers to your pipelines by using webhooks and timers. The manual trigger mechanism is the only trigger mechanism that is supported for the stand-alone use case. This mechanism is triggered when you apply a Custom Resource Definition (CRD) to your local cluster.

You can specify both the pre-existing trigger and the event payload to use. For example, you can choose to use the GitHub trigger and create a fake payload.

## Creating a `CDPipelineRun` CRD
{: #standalone_mode_pipeline_run}

Pipelines in the agent in stand-alone mode are run by creating a `CDPipelineRun` CRD. This CRD provides enough details for the agent to resolve all of the repos and properties that are required to run the pipeline.

The following code snippet shows an example of a `CDPipelineRun` CRD with secret stores defined:

```text
apiVersion: devops.cloud.ibm.com/v1alpha1
kind: CDPipelineRun
metadata:
  name: cdpipelinerun-sample
spec:
  eventPayload: "{}"
  eventListener: test-listener
  secretStores:
  - name: "rootStore"
    vaultType: "hv"
    vaultHost: "https://myhashicorpvault.server.com:8200"
    authType: "approle"
    localSecretRef:
      name: "auth-creds-approle"
      namespace: "my-k8s-secrets-ns"
  - name: "runtimeStore"
    vaultType: "hv"
    vaultHost: "https://myhashicorpvault2.server.com:8200"
    authType: "approle"
    remoteSecretRef:
      secretStoreName: "rootStore"
      path: "mysecrets/standalone-agent/runtimeStoreAppRoleCreds"
  pipelineDefinitions:
  - repoURL: https://github.com/someuser/subpipeline
    repoBranch: kustom2
    repoPath: ".tekton/tests"
```
{: codeblock}

### `CDPipelineRun` CRD fields
{: #cdpipelinerun_crd_fields}

The `CDPipelineRun` CRD contains both mandatory and optional fields.

#### Mandatory fields
{: #mandatory_crd_fields}

The following fields are mandatory in the `CDPipelineRun` CRD:

* **CRD definition**: The definition of the `CDPipelineRun` CRD.

   ```text
   apiVersion: devops.cloud.ibm.com/v1alpha1
   kind: CDPipelineRun
   ```
   {: codeblock}

* **Metadata**: The name of the CRD. You must use a unique name for each namespace.

   ```text
   metadata:
     name: cdpipelinerun-sample
   ```
   {: codeblock}

* **Mandatory Spec Field - Event Listener**: The name of the event listener to run. This value is the name of the event listener in the pipeline definition, not the name of the trigger that is defined in the UI.

   ```text
   eventListener: test-listener
   ```
   {: codeblock}

* **Mandatory Spec Field - pipelineDefinitions**: The pipeline definitions that define where to look for pipeline Tekton definitions, such as the URL, branch, and path. This value is equivalent to adding a pipeline definition in the UI. The repos are cloned and the files are merged in the order that they are defined in. For more information about cloning private repos, see the Secret Stores optional field.

   ```text
    pipelineDefinitions:
     - repoURL: https://github.com/someuser/subpipeline
       repoBranch: kustom2
       repoPath: ".tekton/tests"
   ```
   {: codeblock}

#### Optional fields
{: #optional_crd_fields}

The following fields are optional in the `CDPipelineRun` CRD:

* **Secret Stores**: Secrets in the agent that run in stand-alone mode are resolved at run time. This resolution is handled by defining one or more secret stores. A secret store defines a vault type, a vault host URL, the vault auth type, and the key that is needed to connect. The following example defines a secret store that is named `rootStore`.

   ```text
   secretStores:
     - name: "rootStore"
       vaultType: "hv"
       vaultHost: "https://myhashicorpvault.server.com:8200"
       authType: "approle"
       localSecretRef:
         name: "auth-creds-approle"
         namespace: "myns"
   ```
   {: codeblock}

   Possible values for the `vaultType` field include:
   
   * `hv` - HashiCorp Vault
   * `kp` - IBM Key Protect
   * `sm` - IBM Secrets Manager
 
   Possible values for the `authType` field include:
   
   * `approle`
   * `token`


* **Secret Stores - localSecretRef**: After the parameters for a secret store are established, you must provide an initial key to authenticate with the secret store. To use an agent in stand-alone mode, you must first create this key as a regular Kubernetes secret.

   Possible values for the `authType` field include:
   
   * `approle`
   * `token`
   
* **approle**: The `approle` authType requires you to create two fields within the secret, named `ROLEID` and `SECRETID`. The following example creates a generic secret that is named `auth-creds-approl` in the specified namespace with two literals. You can use this secret by referencing it in a `localSecretRef` section.

   ```text
   kubectl create secret generic auth-creds-approle -n <NAMESPACE> --from-literal=ROLEID='1234-c567-8910-11dc-0ed938d38d2e' --from-literal=SECRETID='23432-5134312-53'
   ```
   {: codeblock}

* **token**: The token `authType` requires you to create a field within the secret named `TOKEN`. The following example creates a generic secret that is named `auth-creds-token` in the specified namespace with two literals. You can use this secret by referencing it in a `localSecretRef` section.

   ```text
   kubectl create secret generic auth-creds-token -n <NAMESPACE> --from-literal=TOKEN='1234-c567-8910-11dc-0ed938d38d2e'
   ```
   {: codeblock}

* **Secret Stores - remoteSecretRef**: After you unlock an initial secret store by way of a `localSecretRef`, you can reference the unlocked store to unlock a *different* secret store by defining a `remoteSecretRef` that refers to the unlocked store. The following example shows a `runtimeStore` secret store that uses the previously defined `rootStore` to look up a value for auth.

   ```text
     secretStores:
     - name: "rootStore"
       vaultType: "hv"
       vaultHost: "https://myhashicorpvault.server.com:8200"
       authType: "approle"
       localSecretRef:
         name: "auth-creds-approle"
         namespace: "myns"
     - name: "runtimeStore"
       vaultType: "hv"
       vaultHost: "https://myhashicorpvault2.server.com:8200"
       authType: "approle"
       remoteSecretRef:
         secretStoreName: "rootStore"
         path: "mysecrets/standalone-agent/runtimeStoreAppRoleCreds"
     ```
     {: codeblock}

## Installing the private worker agent
{: #standalone_mode_agent_framework}

Stand-alone mode is supported in the current [installation](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers&interface=ui). No additional steps are required.


## Running the exported .zip file
{: #standalone_mode_zip}

Complete the following steps to run an exported .zip folder:

1. Install the private worker agent framework on a cluster.
2. Export the .zip package.
3. Create a namespace:

   ```text
   `kubectl create ns <NAMESPACE>`
   ```
   {: codeblock}
   
4. Create any required local secrets.
5. Apply the contents of the trigger that you want to run to the new folder:

   ```text
   `kubectl apply -k <TRIGGER_OVERLAY_FOLDER> -n <NAMESPACE>`
   ```
   {: codeblock}
   
6. Use the Tekton Dashboard to view the exported .zip folder run.

### Installing the Tekton Dashboard
{: #standalone_mode_install_dashboar}

1. For instructions about how to install the Tekton dashboard, see [Installing Tekton Dashboard on Kubernetes](https://tekton.dev/docs/dashboard/install/#installing-tekton-dashboard-on-kubernetes){: external}.
2. For instructions about how to access the dashboard after it is installed, see [Accessing the Dashboard](https://tekton.dev/docs/dashboard/install/#accessing-the-dashboard){: external}.
