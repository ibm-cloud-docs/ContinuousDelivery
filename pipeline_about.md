---

copyright:
  years: 2016, 2019
lastupdated: "2019-07-16"

keywords: run jobs, sequences of stages, job types

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Delivery Pipeline overview
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} includes Delivery Pipeline to build, test, and deploy in a repeatable way with minimal human intervention. In a pipeline, sequences of stages retrieve input and run jobs, such as builds, tests, and deployments.
{:shortdesc}

Your permissions to view, modify, or run a pipeline are based on the access control for the toolchain that owns the pipeline. For more information about access control for toolchains, see [Managing access to toolchains in resource groups](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups) and [Managing access to toolchains in Cloud Foundry orgs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs).
{: important}

You can specify the scripts to run in many of the job types that are provided by the pipeline, giving you direct control over what is run by the job. These scripts run in a Docker image that contains a number of standard development tools, including tools that are required for interacting with the {{site.data.keyword.Bluemix_notm}} runtimes. For more information about what the standard Docker image contains, see [Preinstalled resources](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources). If your job requires development tools that are not available in the standard image, or you need different versions of those tools, you can use a custom image. For more information about custom images, see [Working with custom Docker images](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images#custom_docker_images).

When the pipeline runs scripts, properties that describe the context where the job is running are passed to the script by using environment variables. For example, the URL of the repo that is the input to the stage, the name of the stage and the job that is being run, the parameters specified by the job type, and so on. To view a list of the available environment variables, see [Preinstalled resources](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources).

You can define properties at both the pipeline level and the stage level. Pipeline properties are shared across all stages and jobs in a pipeline. Stage properties are unique to a particular stage, and shared across all jobs in that stage. For more information about properties, see [Environment properties (Environment variables)](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#environment_properties).

## Stages
{: #deliverypipeline_stages}

Stages organize input and jobs as your code is built, deployed, and tested. Stages accept input from either source control repositories (SCM repositories) or build jobs in other stages. For SCM repositories, the input is the contents of a particular branch in the repository; for build jobs, the input is the artifacts that are produced by the job. When you create your first stage, the **INPUT** tab contains default settings.

When a stage runs, the stage's input is passed to each of the jobs in the stage. Each job is given a clean container to run in. As a result, jobs within a stage cannot pass artifacts to each other. To pass artifacts between jobs, separate the jobs into two stages, and use the output from the job in the first stage as input to the second stage.
{: tip}

Similar to how you can define pipeline properties, you can also define stage properties for use in all of the jobs in a particular stage. For example, you might define a `TEST_URL` property that passes a URL to the deploy and test jobs in a stage. The deploy job deploys to that URL and the test job tests the running app at the URL. Stage properties are also passed to job scripts by using environment variables. If the same property is defined at both the pipeline level and the stage level, the value of the stage property is used.

By default in a stage, builds and deployments are run automatically every time that changes are delivered to a project's SCM repository. Stages and jobs run serially; they enable flow control for your work. For example, you might place a test stage before a deployment stage. If the tests in the test stage fail, the deployment stage does not run.

You might want tighter control of a specific stage. If you do not want a stage to run every time that a change occurs at its input, you can disable the capability. On the **INPUT** tab, in the Stage Trigger section, click **Run jobs only when this stage is run manually**.

![The INPUT tab](images/input_tab_only_execute.png)

More stage trigger options are available for stages that use the Git repository input type. For example, you can choose to run jobs automatically for Git events on the chosen branch. When you choose this trigger type, you must select one or more of the following event types:

*	**When a commit is pushed** triggers when a push is made to the selected repo branch.
*	**When a pull/merge request is opened or updated** triggers when a pull request or merge request is opened or edited.
*	**When a pull/merge request is closed** triggers when a pull request or merge request is closed, even without an associated commit.

![The INPUT tab triggers](images/input_tab_only_triggers.png)

If you select the **When a pull/merge request is opened or updated** check box, the status of the pipeline is returned to the Git repo. When a pull request or merge request triggers your pipeline, an inline status check is displayed on the page. A status check is displayed for each of the stages that are run in your pipeline, and links to the logs and history for each stage are provided. As the status check runs, it updates from pending to either successful or failed. If your pipeline contains multiple stages, each stage reports its status in the check list.

This status feedback is also supported by the IBM hosted GitLab Community Edition tool for merge requests.
{: tip}

You can also restrict merging based on the results of the status checks by using Git branch protection rules. After a branch protection rule is created, all merging is blocked until all of the required status checks are successful. 

### Build stage
{: #build_stage}

The build stage specifies a **Builder type** to indicate how to build the artifacts.  

Many of the fields that are available in Build jobs are common across multiple Builder types.
{: tip}

The following Builder types are available:

* **Simple** - Jobs that use the **Simple** builder type take the current stage's input and without modifying it, archive it for use by future stages. Typically, the **Simple** builder type is only useful when the stage's input is from an SCM repository.
* **Ant** - Use this builder type to use Apache Ant files to manage the build job.
  * **Build script** - This builder type can be any valid build script. By default, this builder type is set to 'ant'.
  * **Working directory** - Specifies the directory where the script is run.
  * **Build archive directory** - Specifies the directory that contains the job's output to be archived for use by a subsequent stage.
  * **Enable test report** - Select this check box to specify that the build job runs tests that produce result files in JUnit XML format. A report based on the result files is displayed on the Tests tab of the Job Results page. If any tests failed, the job is marked as failed.
  * **Enable code coverage report** - Select this check box to show more fields that you can use for the code coverage report. You can specify the Coverage runner (such as Istanbul, JaCoCo, ore Cobertura), the location of the Coverage result file, and the Coverage result directory, relative to the Working directory.
* **Container Registry**
* **Gradle (Artifactory, Nexus, or SonarQube)**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven (Artifactory, Nexus, or SonarQube)**
* **npm (Artifactory or Nexus)**
* **Shell Script**

### Deploy stage
The deploy stage specifies input from a Build stage.  The jobs in the deploy stage specify a **Deployer type**.  The following Deployer types are available:

1. **Cloud Foundry**
2. **Kubernetes**

## Jobs
{: #deliverypipeline_jobs}

A job is an execution unit within a stage. A stage can contain multiple jobs, and the jobs in a stage run sequentially. By default, if a job fails, subsequent jobs in the stage do not run.

![Build and test jobs within a stage](images/jobs.png)

Jobs run in discrete working directories within Docker containers that are created for each pipeline run. Before a job is run, its working directory is populated with input that is defined at the stage level. For example, you might have a stage that contains a test job and a deploy job. If you install dependencies on one job, they are not available to the other job. However, if you make the dependencies available in the stage's input, they are available to both jobs.

Except for Simple-type build jobs, when you configure a job, you can include UNIX shell scripts that include build, test, or deployment commands. Because jobs are run in ad hoc containers, the actions of one job cannot affect the run environments of other jobs, even if those jobs are part of the same stage.

Sample build and deploy scripts can be found in [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons){: external}.

Additionally, pipeline jobs can run only the following commands as `sudo`:
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


After a job runs, the container that was created for it is discarded. The results of a job run can persist, but the environment in which it ran does not.

Jobs can run for up to 60 minutes. When jobs exceed that limit, they fail. If a job is exceeding the limit, break it into multiple jobs. For example, if a job performs three tasks, you might break it into three jobs: one for each task.
{: tip}

To learn how to add a job to a stage, see [Adding a job to a stage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy#deliverypipeline_add_job).

### Build jobs

Build jobs compile your project in preparation for deployment. They generate artifacts that can be sent to a build archive directory, although by default, the artifacts are placed in the project's root directory.

Jobs that take input from build jobs must reference build artifacts in the same structure that they were created in. For example, if a build job archives build artifacts to an `output` directory, a deploy script would refer to the `output` directory rather than the project root directory to deploy the compiled project. You can specify the directory to archive by entering the directory name in the **Build Archive Directory** field. Leaving the field blank archives the root directory.

If you use the **Simple** builder type, your code is not compiled or built; it is packaged and made available for future stages.
{: tip}

When you deploy by using Cloud Foundry, Cloud Foundry includes the correct artifacts to allow your app to run. For more information, see [Deploying applications by using the cf command](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#deploy_apps). The pipeline for a Cloud Foundry app contains a Deploy stage that runs a cf command.

Cloud Foundry tries to [detect the buildpack to use](http://docs.cloudfoundry.org/buildpacks/detection.html){: external}. You can specify the [buildpack](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_buildpacks#using_buildpacks) to use in the manifest file in the root folder of your app. Buildpacks typically examine user-provided artifacts to determine what dependencies to download and how to configure applications to communicate with bound services. For more information about manifest files, see [Application manifest](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).

### Deploy jobs

Deploy jobs upload your project to {{site.data.keyword.Bluemix_notm}} as an app and are accessible from a URL. After a project is deployed, you can find the deployed app on your {{site.data.keyword.Bluemix_notm}} dashboard.

Deploy jobs can deploy new apps or update existing apps. Even if you first deployed an app by using another method, such as the Cloud Foundry command line interface or the run bar in the Web IDE, you can update the app by using a deploy job. To update an app, in the deploy job, use that app's name.

You can deploy to one or many regions and services. For example, you can set up your {{site.data.keyword.deliverypipeline}} to use one or more services, test in one region, and deploy to production in multiple regions.

### Test jobs
If you want to require that conditions are met, include test jobs before or after your build and deploy jobs. You can customize test jobs to be as simple or complex as you need. For example, you might issue a cURL command and expect a particular response. You might also run a suite of unit tests or run functional tests with third-party test services, such as Sauce Labs.

If your tests produce result files in JUnit XML format, a report that is based on the result files is shown on the **Tests** tab of every test result page. If a test fails, the job also fails.

## Environment properties (Environment variables)
{: #environment_properties}

A set of predefined environment properties provides access to information about the job's execution environment. For a complete list of the predefined environment properties, see [Environment properties and resources](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment).

You can also define your own environment properties. For example, you might define an `API_KEY` property that passes an API key that is used to access {{site.data.keyword.Bluemix_notm}} resources by all scripts in the pipeline.

You can add the following types of properties:

* **Text**: A property key with a single-line value.
* **Text Area**: A property key with a multi-line value.
* **Secure**: A property key with a single-line value that is secured with AES-128 encryption. The value is displayed as asterisks.
* **Properties**: A file in the project's repository. This file can contain multiple properties. Each property must be on its own line. To separate key-value pairs, use the equals sign (=). Enclose all string values in quotation marks. For example, `MY_STRING="SOME STRING VALUE"`.

You can examine the environment properties for a pipeline job by running the `env` command in the job's script.
{:tip}

### Pipeline properties
To define pipeline properties, from the overflow menu on the Pipeline page, select **Configure Pipeline**.

![Pipeline overflow menu](images/OverflowMenu.png)

From the **ENVIRONMENT PROPERTIES** tab on the Pipeline configuration page, set the pipeline-level environment properties.

![Pipeline properties page](images/PipelineProperties.png)

### Stage properties
To define stage properties, open the Stage configuration page and click the **ENVIRONMENT PROPERTIES** tab.

![Stage properties page](images/StageProperties.png)

You can define a stage property by using an initial value (or a blank value), and then overriding that value in a job by exporting an environment variable. By overriding the initial value, subsequent jobs in the stage can see the new value. For example, you can include the following command to set the `$API_KEY` property and make it available to another job within the stage: `export API_KEY=<insert API key here>`
{:tip}

### Computed properties
You can compute the environment property values that are shared across stages by creating a `build.properties` file while the stage is running, and then have the next stage run the file. For example, your build job might include the following command in the build script:

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

All jobs start by running the `build.properties` file, if it exists.

## Creating and using artifacts
{: #artifacts}

Build jobs automatically fetch the content in the current folder where the user script is run.  If you do not need the entire git repo content for later deployment, it is preferable that you configure an explicit output directory and then copy or create the relevant artifacts there.  Job scripts are run in the build result (output directory).

Jobs that deploy to Cloud Foundry need to specify the Platform API key of a user under whose authority jobs run, and the region, org, and space of where to deploy the artifacts. If more services are required to run your app, you must specify them in the `manifest.yml` file.

Deploy jobs that deploy to the {{site.data.keyword.containerlong_notm}} need to specify the Platform API key of a user under whose authority jobs run, a Dockerfile, and optionally a Helm chart.  

The job script runs after the job has logged in to the target environment by using the Platform API key that is assigned to it (so that you can run `cf push`  or `kubectl` commands in the script).

## An example pipeline
{: #deliverypipeline_example}

A simple pipeline might contain three stages:

1. A Build stage that compiles and runs build processes on an app.
2. A Test stage that deploys an instance of the app and then runs tests on it.
3. A Prod stage that deploys a production instance of the tested app.

This pipeline is shown in the following conceptual diagram:

![A conceptual diagram of stages and jobs in a pipeline](images/diagram.jpg)

*A conceptual model of a three-stage pipeline*

Stages take their input from repositories and build jobs, and jobs within a stage run sequentially and independently of each other. In the example pipeline, the stages run sequentially, even though the Test and Prod stages both take the Build stage's output as their input.

## Cloud Foundry Manifest files
{: #deliverypipeline_manifest}

Manifest files, which are named `manifest.yml` and stored in a project's root directory, control how your project is deployed to {{site.data.keyword.Bluemix_notm}}. For information about creating manifest files for a project, see the [{{site.data.keyword.Bluemix_notm}} documentation about application manifests](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest). To integrate with {{site.data.keyword.Bluemix_notm}}, your project must have a manifest file in its root directory. However, you are not required to deploy based on the information in the file.

In the pipeline, you can specify everything that a manifest file can do by using `cf push` command arguments. The `cf push` command arguments are helpful in projects that have multiple deployment targets. If multiple deploy jobs all try to use the route that is specified in the project manifest file, a conflict occurs.

To avoid conflicts, you can specify a route by using `cf push` followed by the host name argument, `-n`, and a route name. By modifying the deployment script for individual stages, you can avoid route conflicts when you deploy to multiple targets.

To use the `cf push` command arguments, open the configuration settings for a deploy job and modify the **Deploy Script** field. For more information, see the [Cloud Foundry Push documentation](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: external}.
