---

copyright:
  years: 2020, 2025
lastupdated: "2025-11-18"

keywords: environment properties, environment resources, IBM Java, Tekton environments

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Tekton pipelines environment properties and resources
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
{: caption="PipelineRun annotations" caption-side="top"}

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
      image: icr.io/continuous-delivery/pipeline/pipeline-base-image:2.69
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
{: codeblock}

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
      image: icr.io/continuous-delivery/pipeline/pipeline-base-image:2.69
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
{: codeblock}

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
      image: icr.io/continuous-delivery/pipeline/pipeline-base-image:2.69
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
{: codeblock}

## Managed worker virtual machine sizing
{: #tekton_tshirt_sizing}

When you run a pipeline by using the IBM Managed Worker pool, a VM with a specific default memory is allocated. Although most jobs can run successfully with the provided memory, certain pipelines require extra memory for intensive tasks.

Users can specify a label on their tasks to indicate whether a task requires more (or less) memory for a specific task. This ability to identify the specific amount of resources that are required benefits resource usage and eventual cost savings.

To indicate which VM profile to apply to a specific task within a Tekton pipeline, add the `runtimeClassName` label to the task with one of the following VM values. If no label is provided, the default VM profile is used.


* `small`: 2Gi
* `medium`: 4Gi (default)
* `large`: 8Gi 

For example:

```text
apiVersion: tekton.dev/v1beta1
kind: Task
metadata:
  name: task1
  labels:
    runtimeClassName: medium
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
      taskPodTemplate:
        runtimeClassName: medium
```
{: codeblock}








## Log format
{: #tekton_log_format}

This section describes the features and functionality of the log viewer provided on the PipelineRun details page, and the supported log format to take advantage of these features.

### Basic functionality
{: #tekton_log_basic}

The log viewer supports ANSI colour codes and text styles, and will automatically detect URLs in log content and render them as clickable links opening in a new window.

### Toolbar
{: #tekton_log_toolbar}

The toolbar displayed in the log viewer includes a number of additional features, including:

- maximize: increase the area available to the log viewer by hiding the task list and run header. This allows the user to eliminate distractions from other parts of the app and focus on the log content.
- user preferences: these are persisted locally in the browser and applied to all logs in the app. See the following sections for more details.

### Timestamps
{: #tekton_log_timestamps}

IBM-managed workers, and private workers with agent version 0.20.5 or later, produce log lines prefixed with timestamps by default. The user may show or hide these timestamps in the log viewer by toggling the option in the settings menu in the toolbar at the top of the log viewer.

The displayed timestamps are localised based on the user's browser settings, with the raw timestamp value received from the worker provided as a tooltip on hover.

### Log levels
{: #tekton_log_levels}

The log viewer parses log lines to detect the associated log level and decorate them accordingly to help with log consumability. The format supported is described below.

```
<timestamp> ::<level>::<message>
```

- `timestamp` is provided by the worker
- `level` is one of `error`, `warning`, `notice`, `info`, `debug`, `trace`
   - `debug` and `trace` logs are hidden by default
   - any log line without an explicit `level` is considered as `info`, but will not display the log level badge to avoid redundancy in the UI where users are not using the supported log format
- `message` is any other content on the line, and may contain ANSI codes for formatting, etc.

For example, the following snippet would output a log line at the `warning` level:

```sh
echo '::warning::Something that may require attention but is non-blocking…'
```
{: codeblock}

The displayed log levels can be changed via the settings menu in the toolbar at the top of the log viewer.

###  Log groups
{: #tekton_log_groups}

In addition to log levels, the log viewer also supports collapsible groups within the logs. The supported format is described below.

```
<timestamp> ::group::<message>
…
<timestamp> ::endgroup::
```

A `group` command marks the beginning of the group. The content of `message` is displayed as the title / summary of the group along with an indicator of the group's current state (i.e. expanded or collapsed). Clicking the summary will toggle the state of the group.

Groups are rendered in the collapsed state by default unless the step is still in progress when the logs are viewed. The user can expand or collapse groups as desired and their state will be maintained until the user navigates to a different view.

Log groups cannot be mixed with log levels on the same line, the `group`, `endgroup`, and log level commands are mutually exclusive. However, logs contained within a group can use log levels as normal.

Nesting groups is not supported. A `group` command will implicitly terminate any prior unterminated group.

For example, the following snippet would output a log group with the summary 'Additional config' containing a number of messages at the `info` level:

```sh
echo '::group::Additional config'
echo 'This extends the base config'
echo '::info:: More info about the config…'
echo '::endgroup::'
```
{: codeblock}

## Learn more about Tekton delivery pipelines
{: #tekton_learn_more}

To learn more about Tekton and {{site.data.keyword.contdelivery_short}}, see [Tekton: A Modern Approach to Continuous Delivery](https://www.ibm.com/blog/tekton-a-modern-approach-to-continuous-delivery/){: external}.
