---

copyright:
  years: 2021
lastupdated: "2021-06-25"

keywords: DevSecOps

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:deprecated: .deprecated}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Custom scripts
{: #cd-devsecops-custom-scripts}

Custom scripts are extension points in the pipeline where adopters, teams, and users can provide scripts to run custom tasks that are required by their continuous integration and continuous delivery strategies.
{: shortdesc}

Custom scripts control the pipeline stages. You can use a configuration file (`pipeline-config.yaml`) to configure the behavior of stages, script content, and the base image that runs the scripts. The scripts and configuration for pipeline stages are loaded from a Git repo that can either be the app repo (similar to `.travis.yml` or `Jenkinsfile`) or a custom repo.

## Stages
{: #cd-devsecops-scripts-stages}

Stages in pull request, continuous integration, and continuous delivery pipelines run custom scripts.

* **Pull request pipeline stages**: setup, test

* **Continuous integration pipeline stages**: setup, test, static-scan, containerize, sign-artifact, deploy, acceptance-test, scan artifact, release

* **Continuous delivery pipeline stages**: set up, deploy, acceptance-test

### Stage descriptions
{: #cd-devsecops-stage-desc}

 * `setup`: Run scripts to complete setup tasks such as setting up an environment for a pipeline run, installing dependencies, and checking environments.
 * `test`: Run unit tests, include all of your tests that run on your codebase, and pre-deploy time.
 * `static-scan`: Run a static code analyzer tool.
 * `containerize`: Create the artifacts that are required by your app, such as Docker images, RPMs, and Java Archive (JARS) files.
 * `scan-artifact`: Scan the artifacts, for example, by using Container Registry Vulnerability Advisor for Docker images.
 * `sign-artifact`: Sign the artifacts.
 * `release`: Add artifacts to the inventory by marking them available for deployment.
 * `deploy`: Deploy artifacts to an environment such as test and dev or staging and prod.
 * `acceptance-test`: Run tests on deployed artifacts. You can also include your post-deployment tests in this stage.

## Configuration in `pipeline-config.yaml`
{: #cd-devsecops-scripts-stages}

You can use a `.pipeline-config.yaml` configuration file to extend pipeline behavior.

### File location
{: #cd-devsecops-scripts-location}

For pull request and continuous integration pipelines, store the `.pipeline-config.yaml` configuration file in an app repo in the same manner as the `.travis.yml`, or `Jenkinsfile` files. For continuous delivery pipelines, store this file in a dedicated repo. 

For all pipelines, you can customize the location and source of the `.pipeline-config.yaml` file with the following these pipeline UI parameters:

* `pipeline-config` to set the path of the configuration file. The default value is `.pipeline-config.yaml`.
* `pipeline-config-repo` to set the repo to pull the configuration and scripts from. The default value is the continuous integration app repo.
* `pipeline-config-branch`to use as the branch for the configuration in the config repo. The default value is the continuous integration app repo branch, and the master branch in continuous delivery.

### Configuration parameters
{: #cd-devsecops-scripts-configparm}

The configuration in the `.pipeline-config.yaml` file supports the following parameters:

These settings are not pipeline parameters, they must be part of your `.pipeline-config.yaml` file.
{: important}

* `image`: You can use any Docker image that is accessible by the pipeline worker as a base image for the task.

* `script`: The script to run in the stage. Because this field is used as a script file make sure that the contents act like a script file in the base image that you provided. You can include other scripts next to this configuration file, and refer to them from this entry point. For example,:

```
test:
  script: |
    #!/bin/sh
    scripts/lint.sh
    scripts/unit-test.sh
```

* `dind`: Specify whether to enable `docker-in-docker` for the script context. The default setting is false.

* `abort_on_failure`: By default the pipeline halts when the script fails. Set this to false allows the pipeline to continue, and the failed job is referenced in the evidence later.

* `image_pull_policy`: Set the pod ImagePullPolicy setting for the base image (provided in image). Possible values are the same as for k8s: Always | IfNotPresent 
Default value is IfNotPresent

* `configmap`: Pull key-value pairs from a provided configmap that is accessible by `PipelineRun`. The following values are supported:

    * `config-name`: Direct configmap name syntax, the stage runner tries to access and mount the configmap named `config-name`.
    * `$prop-name`: The indirect configmap name syntax. The configmap name is looked up from the environment-properties configmap, which contains every environment value that is set on the pipeline UI. For example, if there's a prop: my-config entry in the environment properties, then my-config is going to be used for $prop

* `secret`: Pull key-value pairs from a provided configmap that is accessible by `PipelineRun`. The following values are supported:

    * `secret-name`: The direct Secret name syntax. The stage runner tries to access and mount the Secret named `secret-name`.

    * `$prop-name`: The indirect Secret name syntax. The Secret name is looked up from the environment-properties configmap, which contains every environment value that is set on the pipeline UI. For example, if there's a prop: my-secret entry in the environment properties, my-secret is used for $prop.

#### Example configuration
{: #cd-devsecops-scripts-sample}

```
version: '1' # fixed, this value is used to track schema changes

# `setup` runs right after the app repo is cloned
setup:

  # the pipeline will break in case setup fails (default is true)
  abort_on_failure: true

  # any docker image can be used which is accessible by the private worker
  image: ibmcom/pipeline-base-image:2.7

  # you can reference configmaps, each key in the configmap is going to be available as `/config/{key}`
  configmap: my-config

    # `$prop` is the indirect config map syntax, the concrete configmap is looked
    # up from the `environment-properties` configmap
    #
    # Eg. if there's a `prop: my-config` entry in the environment properties,
    # then `my-config` is going to be used for `$prop`
  configmap: $prop

  # the mechanism described above works for secrets as well!
  secret: $my-secrets

  # the script is executed inside the checked out app repo
  script: |
    #!/bin/sh
    ...

# `test` runs after `setup`, but before building the docker image
test:
  image: ibmcom/pipeline-base-image:2.7 
  script: |
    #!/bin/sh
    ...

# `static-scan` runs after `test`, but before building the docker image
static-scan:
  image: ibmcom/pipeline-base-image:2.12
  script: |
    #!/bin/sh
    ...


# `deploy` runs after building the docker image
deploy:
  image: ibmcom/pipeline-base-image:2.7 

  # the script has access to the built docker image, which is available at `/config/image`
  script: |
    #!/bin/sh

    cat /config/image

# `acceptance-test` runs after `deploy`
acceptance-test:
  image: ibmcom/pipeline-base-image:2.7 
  script: |
    #!/bin/sh
    ...
```
To view the `.pipeline-config.yaml` configuration file that is used by default for the example app in the reference pipeline template, see the [configuration for pull requests and continuous integration](https://us-south.git.cloud.ibm.com/open-toolchain/hello-compliance-app/-/blob/master/.pipeline-config.yaml"){: external} and the [configuration for continuous delivery](https://us-south.git.cloud.ibm.com/open-toolchain/hello-compliance-deployment/-/blob/master/.pipeline-config.yaml"){: external}.

## Secrets, parameters, and properties
{: #cd-devsecops-scripts-secrets}

Use [pipelinectl commands](/docs/ContinuousDelivery?topic=ContinuousDelivery-pipelinectl) to read or write data from the pipeline at run time. You can read and write secrets, variables, repo data, artifact data, and evidence result artifacts (such as test result files) by way of the pipelinectl interface.

You do not need to install the pipelinectl tool for your scripts or base images, the reference pipeline provides the binary files for the context of your script.
{: tip}

### Accessing pipeline environment secrets and properties
{: #cd-devsecops-scripts-accesssecrets}

Environment properties and secrets (defined on the pipeline UI) are accessible through `pipelinectl`:

```
# if you set my_config_value on the UI, it's accessible via `get_env`
my_config_value=$(get_env my_config_value)
```

You can set other variables by using `set_env`:

```
set_env my_config_value "some value"

# later on, even in another stage
my_config_value$(get_env my_config_value)
```

These values are not persisted, they're scoped for a single pipeline run.
{: tip}

#### Example
{: #cd-devsecops-scripts-sample}

For example, you can create an Artifactory auth credential for your own build, if you add the required parameters to the pipeline UI:

    my-artifactory-email
    my-artifactory-user
    my-artifactory-password
    my-artifactory-url

When these parameters are available in the pipeline, you can access them in the user scripts and create a Docker auth JSON file For example:

```

kubectl create secret docker-registry regcred \
  --o json \
  --dry-run=client \
  --docker-server="$(get_env my-artifactory-url)" \
  --docker-username="$(get_env my-artifactory-user)" \
  --docker-email="$(get_env my-artifactory-email)" \
  --docker-password="$(get_env my-artifactory-password)" \
   | jq -r '.data[".dockerconfigjson"]' | base64 -d

{"auths":{"us.icr.io":{"username":"user@ibm.com","password":"secret-password","email":"user@ibm.com","auth":"dXNlckBpYm0uY29tOnNlY3JldC1wYXNzd29yZA=="}}}
```

### Parameters for custom scripts
{: #cd-devsecops-scripts-parm}

Besides the pipeline environment variables and secrets, these parameter values are provided for user script stages.

You can access repos, artifacts, files, and env variables by using the `pipelinectl` command in the user scripts. Use the following methods: list_repos, load_repo, load_artifact, list_artifacts, get_env. 

#### `pipelinectl`
{: #cd-devsecops-scripts-pipelinectl}

`app-repo` default is the default app repo that is cloned internally by the pipeline and added to the pipeline by using the `save_repo pipelinectl` interface with the `app-repo` reference name. If you set up the pipeline from the toolchain template, the default repo is either provided by the repo pipeline UI parameter or selected by its toolchain binding name. Use the `load_repo` command to access properties from the saved `app-repo`.

#### Values in `/config/`
{: #cd-devsecops-scripts-configvalue}

To support user script compatibility with an earlier version, these values are copied to `/config/`. Because the availability of these files depends on the pipeline context, make sure that they are available before you use their value.


| Path | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| `/config/api-key` | The value of `ibmcloud-api-key` copied, for script compatibility with an earlier version.|
| `/workspace/git-token` | The Git token obtained in the beginning of the pipeline for script compatibility with an earlier version |
| `/config/environment` | Deployment target environment for [inventory](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-inventory) |
| `/config/deployment-delta-path` | Path to the JSON file that contains the deployment delta |
| `/config/inventory-path` | Path to the inventory repo content |
| `/config/git-branch` | Currently, checked out Git branch of the application repo |
| `/config/git-commit` | Latest Git commit of the checked out application repo |
| `/config/repository-url` | Application repo URL |
| `/config/inventory-url` | Inventory repo URL |
| `/config/image` | Built docker image artifact, containing the registry, namespace, name, and the digest of the image |
| `/config/artifact` | Same as /config/image |
| `/config/signature` | The image artifact signature |
{: caption="Table 1. `/config/` Values" caption-side="top"}

These values are phased out and replaced by the stage I/O interface by way of pipelinectl.
{: deprecated}

#### Environment variables
{: #cd-devsecops-scripts-envvar}

Default ENV variables for the context of custom script stages, provided by the pipeline:

| Path | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| BUILD_NUMBER | Tekton pipeline build number|
| PIPELINE_CONFIG_PATH | Path to the pipeline script library root |
| PIPELINE_CONFIG_REPO_PATH | The directory where the pipeline config-repo is cloned |
| PIPELINE_RUN_NAME | Tekton pipeline run name |
| PIPELINE_RUN_ID | Tekton pipeline run ID |
| PIPELINE_RUN_URL | Tekton pipeline run URL |
| PIPELINE_ID | Tekton pipeline ID |
| STAGE | User script stage |
| TOOLCHAIN_DATA_PATH | The toolchain data path /toolchain/toolchain.json |
| TRIGGER_TYPE | Pipeline trigger type |
| TRIGGER_NAME | Pipeline trigger name |
| TRIGGER_PAYLOAD | Payload received by way of the pipeline trigger event, if there was any. For more information about working with payloads, see [Accessing arguments from webhook payloads](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-webhook-payloads). |
| TRIGGERED_BY | Some information on who triggered the pipeline (don't assume an email address, it can be a time-triggered run) |
| WORKSPACE | Path to the shared workspace |
{: caption="Table 2. Environment variables" caption-side="top"}

You can access these environment variables in any script, for example, `. ${PIPELINE_ID}`.

### Accessing toolchain data from custom scripts
{: #cd-devsecops-scripts-toolchaindata}

Toolchain data can be read from the toolchain.json file that is provided by the pipeline at the path that is stored in the `TOOLCHAIN_DATA_PATH` environment variable or you can use toolchain integration and jsonpath, and access them in `/config` just like any variable, or get_env, which does the same effect. 

### Shared workspaces
{: #cd-devsecops-scripts-workspaces}

Because these custom scripts operate in the same workspace, you can pass data between them by writing it into a file and reading it in the other task. This workspace is mounted on a path that is provided in the `$WORKSPACE` variable.

## Stage output
{: #cd-devsecops-scripts-stageoutput}

Data expected to be available by other stages on the workspace, so make sure to create them using the [`pipelinectl` commands](/docs/ContinuousDelivery?topic=ContinuousDelivery-pipelinectl). To make the required outputs available to the other stages and scripts in the pipeline, use pipelinectl's save methods, like save_repo, save_artifact, save_result and set_env. 

|Source stage |Description	|`Pipelinectl` method |Required |
|:----------|:------------------------------|:------------------|:----------|
|`setup` 		|You can [add more repos to the pipeline compliance checks and static code scan](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-gherepos-pipelines).		|`save_repo`		|No		|
|`test`		|To [attach test results to the compliance evidence as evidence artifacts](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-add-pipeline-steps), use the save_result command in this stage.		|`save_result`			|No		|
|`static-scan`		|To [attach test results to the compliance evidence as evidence artifacts](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-add-pipeline-steps), use the save_result command in this stage. 		|`save_result`		|No		|
|`containerize`		|[Add artifact names and digests to the pipeline](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-config-github).		|`save_artifact`		|Yes		|
|`sign-artifact` 		|Add image signature from GPG signing output   	|`save_artifact`			|Yes		|
|`acceptance-test` 		|To [attach test results to the compliance evidence as evidence artifacts](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-add-pipeline-steps), use the save_result command in this stage. 		|`save_result`			|No		|
{: caption="Table 3. Stage output" caption-side="top"}

### Stage results API
{: #cd-devsecops-scripts-resultsapi}

The result states of these custom stages are saved with `pipelinectl`. The result state of a stage is either success, failure or skipped. These results can be used later to evaluate whether the custom stage ran successfully.

The following tasks and stages are available:

* **Pull request pipeline stages**: setup, test, detect-secrets, and branch-protection. The detect-secrets and branch-protection stages are not custom stages. They are provided by the pipelines by default.

* **Continuous integration pipeline stages**: setup, test, static-scan, containerize, sign-artifact, deploy, acceptance-test, scan artifact, release, detect-secrets, branch-protection, bom-check, cis-check, and vulnerability-scan. The detect-secrets, branch-protection, bom-check, cis-check, and vulnerability-scan stages are not custom stages. They are provided by the pipelines by default.

* **Continuous delivery pipeline stages**: set up, deploy, acceptance-test, create-change-request, change-request-check-approval, change-request-change-state-to-implement, and close-change-request. The create-change-request, change-request-check-approval, change-request-change-state-to-implement, and close-change-request stages are not custom stage. They are provided by the pipelines by default.

#### Example usage

```
# List saved stage results
$ get_data result
detect-secrets
branch-protection

# Get stage result
$ get_data result detect-secrets
success
```
For more information about the Stage Results API, see [Using the Stage Results API in custom scripts](docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-stage-results).
