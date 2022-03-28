---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, publish, build, record, jenkins, test, tests, app, dashboard

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}

# Publishing a build record
{: #publish-build-jenkins}

You can publish a build record by using Jenkins to integrate your projects with {{site.data.keyword.DRA_full}}. Build records notify {{site.data.keyword.DRA_short}} when a build is complete. This record contains the application name, branch, build ID, reference to Git repo, and other fields. You must publish build records to view any test records, deployment records, or evaluate policies in {{site.data.keyword.DRA_short}}. 
{: shortdesc}

{{site.data.keyword.DRA_full}} tracks deployment risk based on published test data. When you integrate Jenkins with {{site.data.keyword.DRA_short}}, you are instrumenting {{site.data.keyword.DRA_short}} to gather information from your Jenkins project. Information that is gathered is presented in the {{site.data.keyword.DRA_short}} dashboard to provide visibility into your DevOps process. 


## Before you begin
{: #prereq-build-jekins}

You must have a toolchain. For more information, see [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started). 

Add the Jenkins tool to your app's toolchain. For more information, see [Configure Jenkins](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jenkins). 


## Publishing build records with Jenkins 
{: #build-jenkins}

These variables are required for the pipeline to integrate with {{site.data.keyword.DRA_short}}.

| Environment variable            | Definition                | 
|---------------------------------|---------------------------|
| `IBM_CLOUD_DEVOPS_API_KEY`      | A unique code that is passed in to an application programming interface (API) to identify the calling application or user. Store the API key as Jenkins credentials. (secret text type). |
| `IBM_CLOUD_DEVOPS_APP_NAME`     | The name of the application that your toolchain deploys. If applicationName parameter is passed to the step job, then this value is ignored for that step. |
| `IBM_CLOUD_DEVOPS_TOOLCHAIN_ID` | The ID of your toolchain. |
{: caption="Table 1. Jenkins environment variables and definitions" caption-side="top"}

For each command, you need to specify the toolchain ID to export the environment variable. These environment variables and credentials are used by the {{site.data.keyword.DRA_full}} plug-in to interact with {{site.data.keyword.DRA_short}}. Here is an example of setting them in the declarative pipeline format.

```text
environment {
        IBM_CLOUD_DEVOPS_API_KEY = credentials('BM_API_KEY')
        IBM_CLOUD_DEVOPS_APP_NAME = 'Weather-App'
        IBM_CLOUD_DEVOPS_TOOLCHAIN_ID = '1111111-aaaa-2222-bbbb-333333333'
    }
```
{: codeblock}

For more information about creating an API key, see [Managing user API keys](/docs/services/account?topic=account-userapikey).

For more information about your toolchain ID, see [Identifying your toolchain ID](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources). 

Publish build records with the publishBuildRecord step. This step requires four parameters. It can also accept one optional parameter. 

| Parameter         | Definition                                                                                                                   |
|-------------------|------------------------------------------------------------------------------------------------------------------------------|
| `gitBranch`       | The name of the Git Branch that the build uses.                                                                              |
| `gitCommit`       | The Git commit's ID that the build uses.                                                                                       |
| `gitRepo`         | The URL of the Git repository.                                                                                               |
| `result`          | The result of the build stage. The value is SUCCESS or FAIL.                                                                 |
| `buildNumber`     | Optional: The set value to any string that represents version number.                                                         |
| `applicationName` | Optional: Set the application name. If this value is set the environment variable, `IBM_CLOUD_DEVOPS_APP_NAME` is ignored.   |
{: caption="Table 2. Publishing build records parameters and definitions" caption-side="top"}

Here are the parameters in an example command:

```text
stages {
    Stage(`Build) {
        environmnet {
            // get git commit from Jenkins
            GIT_COMMIT = sh(returnStdout: true, script: 'git rev-parse HEAD').trim()
            GIT_BRANCH = 'master'
            GIT_REPO = 'https:github.com/xunronli-ibm/DemoDRA/'
        }
        steps {
            echo "building"
        }
        // post build section to use "publishBuildRecord" method to publish build record
        post {
            success {
                publishBuildRecord gitBranch: "${GIT_BRANCH}", gitCommit: "${GIT_COMMIT}", gitRepo: "${GIT_REPO}", result:"SUCCESS"
            }
            failure {
                publishBuildRecord gitBranch: "${GIT_BRANCH}", gitCommit: "${GIT_COMMIT}", gitRepo: "${GIT_REPO}", result:"FAIL"
            }
        }
    }
}
```
{: codeblock}

The Jenkins Pipeline doesn't show Git information as environment variables. You can get the Git commit ID by using the command sh(returnStdout: true, script: 'Git rev-parse HEAD').trim().


## {{site.data.keyword.DRA_short}} steps
{: #insights-steps-jenkins}

The Cloud DevOps plug-in adds four steps to Jenkins pipelines for you to use. Use these steps in your pipelines to interact with {{site.data.keyword.DRA_short}}. Add these steps to your pipeline definition wherever you need them to run. For example, you might upload test results after you run a test, and then evaluate those results at a gate after they are uploaded.

| Step                  | Use                          |
|-----------------------|------------------------------|
| `publishBuildRecord`  | Publishes build information  |
| `publishTestResult`   | Publishes test results       |
| `publishDeployRecord` | Publishes deployment records |
| `evaluateGate`        | Enforces policies            |
{: caption="Table 3. {{site.data.keyword.DRA_short}} steps and uses" caption-side="top"}

By default, the version number is set to be {pipeline name}:{build number}, you can also set the custom version number in each step


## Sample pipeline and code
{: #pipeline-code-jenkins}

Here are two complete pipeline examples that are defined as [declarative Jenkins file](https://github.com/jenkinsci/ibm-cloud-devops-plugin/blob/master/Declarative-Jenkinsfile){: external} and a [scripted Jenkins file](https://github.com/jenkinsci/ibm-cloud-devops-plugin/blob/master/Scripted-Jenkinsfile){: external}. 

The [Git repo](https://github.com/devops-insights/DemoDRA){: external} contains a sample nodejs application code, tests, and Jenkins file that you can experiment with. Fork the repo and modify the Jenkins file with your actual information. 

If you didn't install NodeJS in your Jenkins environment, you might have to install the node.js Jenkins plug-in. If you installed NodeJS, you can comment out the "tools" section in the Jenkins file.
{: tip}


## Viewing Build Frequency
{: #build-frequency-jenkins}

When this build job completes, the pipeline publishes a message to {{site.data.keyword.DRA_short}} that a build is complete. You can view the build record on the Build Frequency page. To view the Build Frequency page, use the following steps. 

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. 
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Build Frequency**.  

## Next steps
{: #next-build-jenkins}

Learn how to [publish a deployment record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-deploy-jenkins) by using Jenkins.
