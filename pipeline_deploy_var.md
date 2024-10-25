---

copyright:
  years: 2016, 2024
lastupdated: "2024-10-25"

keywords: environment properties, environment resources, IBM Java, pipeline environments

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Continuous Delivery environment properties and resources
{: #deliverypipeline_environment}

The following properties and resources are available by default in {{site.data.keyword.contdelivery_full}} {{site.data.keyword.deliverypipeline}} environments.

## Environment properties
{: #deliverypipeline_envprop}

### General-purpose properties
{: #general_purpose_properties}

The following table lists and describes each of the general-purpose environment properties that are available by default in pipeline environments.

| Environment Property | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| ARCHIVE_DIR | The directory to archive or to download archives into. |
| BUILD_ID | The unique ID for the current job execution.  |
| BUILD_DISPLAY_NAME | The BUILD_ID value, prefixed with "#". |
| BUILD_NUMBER | The incremental stage ID that is shown in the pipeline UI.  |
| GIT_BRANCH | The Git branch that the job uses as input. This property is only available in jobs that use a Git repository as input. |
| GIT_COMMIT | The Git commit that the job uses as input. This property is only available in jobs that use a Git repository as input. |
| GIT_PREVIOUS_COMMIT | The Git commit value of the job's last successful run. This property is only available in jobs that use a Git repository as input. |
| GIT_URL | The Git repository URL that the job uses as input. This property is only available in jobs that use a Git repository as input. |
| IDS_JOB_ID | The unique ID of the job's configuration. |
| IDS_JOB_NAME | The name of the job's configuration. |
| IDS_OUTPUT_PROPS | Comma-separated names of your stage environment properties. |
| IDS_PROJECT_NAME | The name of the project, for example, `Owner - Project Name`. |
| IDS_STAGE_NAME | The name of the current stage. |
| IDS_URL | The URL for the current pipeline. |
| IDS_VERSION | The number for the build that is being deployed or the SCM identifier. This property is available only in deploy jobs.
| JOB_NAME | The unique job ID in the context of the current pipeline. |
| PIPELINE_ARTIFACT_URL | The URL that you can use to download the artifacts of the current Build job after the job completes. You must use a valid Bearer token to access the artifacts. |
| PIPELINE_INITIAL_STAGE_EXECUTION_ID | The unique ID for the run of the pipeline. |
| PIPELINE_IMAGE_URL | The URL of the container image that is built by a Container Registry build job. This property is present only in a job whose stage input is a Container Registry build job. This input Container Registry build job must explicitly export `PIPELINE_IMAGE_URL`, for example: `export PIPELINE_IMAGE_URL=$REGISTRY_URL/$REGISTRY_NAMESPACE/$IMAGE_NAME:$BUILD_NUMBER`. |
| PIPELINE_KUBERNETES_CLUSTER_NAME | The name of the Kubernetes cluster that is selected in the current job. |
| PIPELINE_LOG_URL | The URL that you can use to download the log file of the current job after the job completes. You must use a valid Bearer token to access the log files. |
| PIPELINE_STAGE_INPUT_JOB_ID | The ID of the job that is input for the current stage. |
| PIPELINE_STAGE_INPUT_REV | The revision of the input for the current stage. |
| PIPELINE_TRIGGERING_USER | The current user for the pipeline job|
| TASK_ID | The unique ID of the job's current run. |
| TMPDIR | A directory location where temporary files are stored. |
| WORKSPACE | The path for the current working directory. |
{: caption="General-purpose environment properties" caption-side="top"}

### Runtime and tool properties
{: #runtime_properties}

The following table lists and describes each of the runtime and tool environment properties that are available by default in pipeline environments.

| Environment Property | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| ANT_HOME | The path to Apache Ant 1.9.2. |
| ANT_JAVA8_HOME | The path to a 1.10+ version of Apache Ant that requires Java 8. |
| GRADLE_HOME | The path to Gradle 1.11. |
| JAVA_HOME | The path to IBM&reg; Java&trade; 7. |
| JAVA7_HOME | The path to IBM Java 7. |
| JAVA8_HOME | The path to IBM Java 8. |
| MAVEN_HOME | The path to Apache Maven 3.2.1. |
| NODE_HOME | The path to Node.js 0.10.29. |
{: caption="Runtime and tool environment properties" caption-side="top"}

### Deployment properties
{: #deployment_properties}

The following table lists and describes each of the deployment environment properties that are available by default in pipeline environments.

| Environment Property | Description |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| CF_APP | For deployments, the name of the app to deploy. This property is required for deployment and can be specified in the script itself, the deploy job configuration interface, or the project's `manifest.yml` file. |
| CF_ORG | For deployments, the name of the organization (org) to deploy to. |
| CF_ORGANIZATION_ID | For deployments, the ID of the org to deploy to. |
| CF_SPACE | For deployments, the name of the space to deploy to. |
| CF_SPACE_ID | For deployments, the ID of the space to deploy to.  |
| CF_TARGET_URL | For deployments, the URL of {{site.data.keyword.cloud_notm}}. |
| IDS_VERSION | For deployments, the version of the app that is being deployed or the source identifier. |
{: caption="Deployment environment properties" caption-side="top"}
