---

copyright:
  years: 2020, 2023
lastupdated: "2023-06-27"

keywords: environment properties, environment resources, IBM Java, Tekton environments

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Tekton Pipelines environment and resources
{: #tekton_environment}

The following information and resources are available by default to an {{site.data.keyword.contdelivery_full}} Tekton `PipelineRun`.

## `PipelineRun` annotations
{: #tekton_run_annotations}

Table 1 describes the annotations that are included in a Tekton `PipelineRun`.

| Run Annotation                          | Description                                                                                                                                                                                                                                                                                          |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `devops.cloud.ibm.com/build-number`     | The build number for the pipeline. This number is the cumulative total of pipeline runs from all triggers.                                                                                                                                                                                           |
| `devops.cloud.ibm.com/listener`         | The Tekton `eventlistener` that is mapped to the trigger that initiated this pipeline run.                                                                                                                                                                                                             |
| `devops.cloud.ibm.com/pipeline-id`      | The unique ID of the pipeline that is used for this run.                                                                                                                                                                                                                                             |
| `devops.cloud.ibm.com/trigger-name`     | The name of the trigger that initiated this pipeline run.                                                                                                                                                                                                                                            |
| `devops.cloud.ibm.com/trigger-type`     | The type of the trigger that initiated this pipeline run. The type can be either `manual`, `timer`, `scm`, or `generic`.                                                                                                                                                                             |
| `devops.cloud.ibm.com/triggered-by`     | The user who initiated the trigger. This value is the IBMId of either the user who pressed **run** for `manual` triggers, the user who last saved the trigger for `timer` triggers, or the user who performed the Git action for `scm` triggers. This value is empty for `generic` triggers. |
| `devops.cloud.ibm.com/pipeline-run-url` | The URL of the details page for this pipeline run.                                                                                                                                                                                                                                                   |
| `devops.cloud.ibm.com/tekton-pipeline`  | The unique ID of this pipeline run.                                                                                                                                                                                                                                                                  |
{: caption="Table 1. PipelineRun annotations" caption-side="top"}

### Accessing annotations
{: #tekton_access_annotations}

You can access annotations from the tasks within your pipeline definition YAML file. The following example shows how to access the `devops.cloud.ibm.com/build-number` annotation. To provide that annotation as an environment variable, replace it with one of the run annotations from Table 1. `PipelineRun` annotations.

```yaml
apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: simple-task
spec:
  steps:
    - name: simple-step
      image: ubuntu
      env:
        - name: BUILD_NUMBER
          valueFrom:
            fieldRef:
              fieldPath: metadata.annotations['devops.cloud.ibm.com/build-number']
      command: ["bash", "-c"]
      args:
        - echo $BUILD_NUMBER;
          echo "COMPLETED"       

```

## PipelineRun `ConfigMap` and `Secret`
{: #tekton_envprop}

The {{site.data.keyword.contdelivery_short}} Tekton `PipelineRun` resource creates a specific `ConfigMap` and `Secret` for environment properties. Secure properties are available in the `secure-properties` Kubernetes `Secret`, including any `Tool integration` properties for which the selected field contains a secure value. Nonsecure properties are available in the `environment-properties` Kubernetes `ConfigMap`. The keys are the name of the field that is provided in the pipeline authoring user interface.

When you access a `ConfigMap` or `Secret`, make sure that you locate the correct object name and references so that your pipeline can successfully complete.
{: important}

### Accessing individual values
{: #tekton_key_values}

You can access individual key-values within a `Task`. The following code snippet uses the sample `apikey` property name (with secure properties) and the `environment` property name (with text properties). These property names are set in the delivery pipeline **Properties** page.

```yaml
apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: cm-echo-props
spec:
  steps:
    - name: cm-show-props
      image: ubuntu
      env:
        - name: SECURE_VALUE
          valueFrom:
            secretKeyRef:
              name: secure-properties
              key: apikey
        - name: ENVIRONMENT
          valueFrom:
            configMapKeyRef:
              name: environment-properties
              key: environment  
      command: ["/bin/bash", "-c"]
      args:
        - echo -e "environment from ConfigMap is >>";
          echo $ENVIRONMENT;
          echo "";
          echo -e "apikey from Secrets is >>";
          echo $SECURE_VALUE
```

### Accessing all values
{: #tekton_access_values}

You can add all of the key-value pairs from the `ConfigMap` and `Secret` to your `Task` environment:

```yaml
apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: cm-secrets-props
spec:
  steps:
    - name: cm-show-full-env
      image: ubuntu
      envFrom:
        - configMapRef:
            name: environment-properties
        - secretRef:
            name: secure-properties     
      command: ["/bin/bash", "-c"]
      args:
        - echo -e "The environment for this Step is ";
          env
```         

## Managed worker virtual machine (VM) sizing
{: #tekton_tshirt_sizing}

When you run a pipeline by using the IBM Managed Worker pool, a VM with a specific default memory is allocated. Although most jobs can run successfully with the provided memory, certain pipelines require extra memory for intensive tasks.

Users can specify a label on their tasks to indicate whether a task requires more (or less) memory for a specific task. This ability to identify the specific amount of resources that are required benefits resource usage and eventual cost savings.

To indicate which VM profile to apply to a specific task within a Tekton pipeline, add the `runtimeClassName` label to the task with one of the following VM values. If no label is provided, the default VM profile is used.

* `kata-tiny`: 128Mi
* `kata-small`: 2Gi
* `kata-medium`: 4Gi (default)
* `kata-large`: 8Gi 

For example:

```text
apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: task1
  labels:
    runtimeClassName: kata-tiny
    and so on.
``` 

You can also specify the same configuration in the `PipelineRun` as part of the `TriggerTemplate`. By specifying the `runtimeClassName` in the `PipelineRun`, users can select the VM profile that they want to use without changing the task definitions.

For example:

```yaml
apiVersion: tekton.dev/v1
kind: PipelineRun
metadata:
  generateName: pipeline-run-
spec:
  pipelineRef:
    name: pipeline
  taskRunSpecs:
    - pipelineTaskName: task1
      podTemplate:
        runtimeClassName: kata-tiny
```

## SLSA level 1 provenance
{: #tekton_slsa_provenance}

Supply chain Levels for Software Artifacts (SLSA), also known as "salsa", is a security framework. SLSA is a checklist of standards and controls to prevent tampering, improve integrity, and secure packages and infrastructure in your projects, businesses, or enterprises. SLSA gets you from safe enough to being as resilient as possible, at any link in the chain.

To achieve SLSA level 1, the build process must be fully scripted and automated, and generate provenance. [Provenance](https://slsa.dev/provenance){: external} is metadata about how an artifact was built, including the build process, top-level source, and dependencies. Knowing the provenance allows software consumers to make risk-based security decisions. Provenance at SLSA level 1 does not protect against tampering, but it offers a basic level of code source identification and can aid in vulnerability management.

To generate a provenance document in a {{site.data.keyword.contdelivery_short}} Tekton pipeline run, you must provide statements by using the `slsa-provenance-statement` statements that are emitted in the pipeline step logs.

For example, in the steps that produce a build artifact, add the following statements:

```yaml
::slsa-provenance-statement::{"subject":[{"name": "icr.io/johndoe/hello-containers-slsa-demo:1-master-287919f9-20220915220023", "digest": {"sha256": "6038ec21bd927a6bb578f58eed3b43d389d27671f1c7bb44ac2c4d7260c3176d"}}]}
::slsa-provenance-statement::{"materials":[{"uri":"https://registry.npmjs.org/@ampproject/remapping/-/remapping-2.2.0.tgz","digest":{"sha512":"qRmjj8nj9qmLTQXXmaR1cck3UXSRMPrbsLJAasZpF+t3riI71BXed5ebIOYwQntykeZuhjsdweEc9BxH5Jc26w=="}}]}
::slsa-provenance-statement::{"materials":[{"uri":"https://registry.npmjs.org/@babel/code-frame/-/code-frame-7.18.6.tgz","digest":{"sha512":"TDCmlK5eOvH+eH7cdAFlNXeVJqWIQ7gW9tY1GJIpUtFb6CmjVyq2VM3u71bOyR8CRihcCgMUYoDNyLXao3+70Q=="}}]}
```

The `slsa-provenance-statement` workflow command is defined as `::slsa-provenance-statement::` followed by a JSON format that defines a `subject` and `materials`. `Subject` is mandatory and no SLSA document is created without a `subject`. `Materials` is optional and corresponds to external resources that are used to produce the artifacts. 
{: tip}

For more information about the SLSA level 1 provenance field definitions, see the [SLSA website](https://slsa.dev/provenance/v0.1#fields){: external}.

### Retrieving the provenance document after a run
{: #tekton_slsa_provenance_retrieve}

To obtain provenance documents, download the pipeline run from the **Actions menu** on the **Pipeline run details** page. The provenance documents are part of the returned `.zip` file.

## Learn more about Tekton delivery pipelines
{: #tekton_learn_more}

To learn more about Tekton and {{site.data.keyword.contdelivery_short}}, see [Tekton: A Modern Approach to Continuous Delivery](https://www.ibm.com/cloud/blog/tekton-a-modern-approach-to-continuous-delivery){: external} or take the following tutorial: [Develop a Kubernetes app by using Tekton delivery pipelines](https://www.ibm.com/cloud/architecture/tutorials/develop-kubernetes-app-using-tekton-delivery-pipelines){: external}.
