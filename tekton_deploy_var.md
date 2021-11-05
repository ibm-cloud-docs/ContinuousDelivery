---

copyright:
  years: 2020, 2021
lastupdated: "2021-04-21"

keywords: environment properties, environment resources, IBM Java, Tekton environments

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Tekton Pipelines environment and resources
{: #tekton_environment}

The following information and resources are available by default to a {{site.data.keyword.contdelivery_full}} Tekton PipelineRun.

## PipelineRun annotations
{: #tekton_run_annotations}

The following table lists and describes each of the annotations that are included in a Tekton PipelineRun.


| Run Annotation | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| `devops.cloud.ibm.com/build-number` | The build number for the pipeline. This number is the cumulative total of pipeline runs from all triggers. |
| `devops.cloud.ibm.com/listener` | The Tekton eventlistener that is mapped to the trigger that initiated this pipeline run. |
| `devops.cloud.ibm.com/pipeline-id` | The unique ID of the pipeline that is used for this run. |
| `devops.cloud.ibm.com/trigger-name` | The name of the trigger that initiated this pipeline run.  |
| `devops.cloud.ibm.com/trigger-type` | The type of the trigger that initiated this pipeline run. The type can be either `manual`, `timer`, `scm`, or `generic`. |
| `devops.cloud.ibm.com/triggered-by` | The user who initiated the trigger. This value is the IBMId of either the user who pressed the run button for `manual` triggers, the user who last saved the trigger for `timer` triggers, or the user who performed the Git action for `scm` triggers.  This value is empty for `generic` triggers. |
| `devops.cloud.ibm.com/pipeline-run-url` | The URL of the details page for this pipeline run. |
| `devops.cloud.ibm.com/tekton-pipeline` | The unique ID of this pipeline run. |
{: caption="Table 1. PipelineRun annotations" caption-side="top"}

### Accessing annotations
{: #tekton_access_annotations}

You can access annotations from the tasks within your pipeline definition yaml file. The following example shows how to access the `devops.cloud.ibm.com/build-number` annotation. To provide that annotation as an environment variable, replace it with one of the run annotations that is listed in Table 1. PipelineRun annotations.

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

The {{site.data.keyword.contdelivery_short}} Tekton PipelineRun resource creates a specific `ConfigMap` and `Secret` for environment properties. Secure properties are available in the `secure-properties` Kubernetes `Secret`, including any `Tool integration` properties for which the selected field contains a secure value. Non-secure properties are available in the `environment-properties` Kubernetes `ConfigMap`. The keys are the name of the field that is provided in the pipeline authoring UI.

When you access a `ConfigMap` or `Secret`, make sure that you locate the correct object name and references so that your pipeline can successfully complete.
{: important}

### Accessing individual values
{: #tekton_key_values}

You can access individual key-values within a `Task`. The following code snippet uses the sample **apikey** property name (with secure properties) and the **environment** property name (with text properties). These property names are set in the delivery pipeline Properties page.

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

## Learn more about Tekton delivery pipelines
{: #tekton_learn_more}

To learn more about Tekton and Continuous Delivery, see [Tekton: A Modern Approach to Continuous Delivery](https://www.ibm.com/cloud/blog/tekton-a-modern-approach-to-continuous-delivery){: external} or take this tutorial:

* [Develop a Kubernetes app by using Tekton delivery pipelines](https://www.ibm.com/cloud/architecture/tutorials/develop-kubernetes-app-using-tekton-delivery-pipelines){: external}
