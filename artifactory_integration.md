---

copyright:
  years: 2015, 2023
lastupdated: "2023-04-10"

keywords: tool integrations, IBM Cloud Public, Artifactory

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring Artifactory
{: #artifactory}

Configure the Artifactory repository manager to store build artifacts in your Artifactory repository (repo).
{: shortdesc}

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **Artifactory**.

1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **Artifactory**.

1. Type the URL for the Artifactory repo that you want to open when you click the Artifactory card.
1. Select the repository type that you want to connect to.
1. If you are using an Artifactory npm registry, follow these steps:

   a. Type the email address that is associated with your registry.

   b. Type the authentication token that is associated with your registry.

   c. Type the URL for your Artifactory release repo, which is your private registry on the Artifactory server.

   d. Type the URL for the Mirror or Public registry that you use to combine multiple public and private npm registries. For example, this URL might be the URL of the virtual registry on your Artifactory server that can access both your private registry and a cache of the npm global registry.

1. If you are using an Artifactory Maven repo, follow these steps:

   a. Type the user ID that is associated with your repo.

   b. Type the password that is associated with your repo.

   c. Type the URL for your Artifactory release repo, which is your private release repo on the Artifactory server.

   d. Type the URL for your Artifactory snapshot repo, which is your private snapshot repo on the Artifactory server.

   e. Type the URL for the Mirror or Public repo that you use to combine multiple public and private Maven repos. For example, this URL might be the URL of the virtual repo on your Artifactory server that can access both your private repos and a cache of the Maven central repo.

1. Click **Create Integration**.
1. On the **Third-Party tools** card, click the Artifactory tool integration for the Artifactory repo that you want to work with. The Artifactory website opens, where you can view the contents of the repo.
1. Optional: If you are using a toolchain on {{site.data.keyword.cloud_notm}} Public and you want to build your app by using Artifactory with npm, configure your pipeline to add an npm build job. For instructions to configure the build job, see the [Configuring an Artifactory npm build job in your pipeline](#config_artifactory_npm) section.
1. Optional: If you are using a toolchain on {{site.data.keyword.cloud_notm}} Public and you want to build your app by using Artifactory with Maven, configure your pipeline to add a Maven build job. For instructions to configure the build job, see the [Configuring an Artifactory Maven build job in your pipeline](#config_artifactory_maven) section.

## Configuring an Artifactory npm build job in your pipeline
{: #config_artifactory_npm}

Before you configure an npm build job in your pipeline, you must have a working pipeline that can use your build SCM repo as input. You must also configure Artifactory for your toolchain. For instructions to configure Artifactory, see the [Artifactory](#artifactory) section.

Configure {{site.data.keyword.deliverypipeline}} to add an npm build job:

1. Create a stage and set the input to the appropriate SCM repo.
1. On the stage, add a build job.
1. Configure the build job:

   ![npm build job](images/artifactory_npm_job.png){: caption="Figure 1. npm build job" caption-side="bottom"}

   a. For the builder type, select **NPM Build**.

   b. If you configured multiple instances of the Artifactory tool integration, enter the name of the Artifactory tool integration that you want to configure the npm build job for.

   c. For the tool integration type, select **Artifactory**.

   d. For the build command, enter the commands to build your npm module or publish it to your registry. This example shows the commands to either build the module or publish it.

    ```text
    npm install
    # or
    npm publish --registry "${NPM_RELEASE_URL}"
    ```
 
    You can find the URL and user credentials that you used to connect to your registry in the configuration settings for the Artifactory tool integration.
    {: tip}

   e. If your build job publishes to the Artifactory registry, and the format of your node module version is `x.y.z-SNAPSHOT.w`, select the **Increment snapshot module version** checkbox. The build job automatically updates the module version before the job publishes to the Artifactory registry. The job selects the highest version of the module from the npm registry and the local `package.json` file, and increments the module version by using semver. The build job does not deliver the changes to the SCM repo.

1. Click **SAVE**. Whenever your pipeline runs, this build job uses the configuration information from the Artifactory tool integration to connect to your npm registry.

## Configuring an Artifactory Maven build job in your pipeline
{: #config_artifactory_maven}

Before you configure a Maven Build job in your pipeline, you need a working pipeline that can use your build SCM repo as input, and you must configure Artifactory for your toolchain. For instructions to configure Artifactory, see the [Artifactory](#artifactory) section.

Configure the {{site.data.keyword.deliverypipeline}} to add a Maven Build job:

1. Create a stage and set the input to the appropriate SCM repo.
1. On the stage, add a build job.
1. Configure the build job:

   ![Maven build job](images/artifactory_maven_job.png){: caption="Figure 2. Maven build job" caption-side="bottom"}

   a. For the builder type, select **Maven Build**.

   b. If you configured multiple instances of the Artifactory tool integration, enter the name of the Artifactory tool integration that you want to configure the Maven Build job for.

   c. For the tool integration type, select **Artifactory**.

   d. For the build command, enter the commands to build your Maven module or publish it to your snapshot registry. This example shows the commands to either build the module or publish it to a snapshot registry.

    ```text
    mvn -B clean package
    # or
    mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
    ```

   You can find the URL and user credentials that you used to connect to your registry in the configuration settings for the Artifactory tool integration.
   {: tip}

1. Click **SAVE**. Whenever your pipeline runs, this build job uses the configuration information from the Artifactory tool integration to connect to your Maven repo.

## Configuring Artifactory by using the API
{: #artifactory-config-parameters}

The Artifactory tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `artifactory` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| dashboard_url | optional, updatable | String | dashboard_url | The URL of the Artifactory server dashboard for this tool integration. In the graphical UI, the browser goes to this dashboard when you click the Artifactory tool integration card. |
| mirror_url | optional, updatable | String | mirror_url | The URL of your Artifactory virtual repo where you can view your private repos and a cache of the public repos. |
| name | required, updatable | String | name | The name of this tool integration. |
| release_url | optional, updatable | String | release_url | The URL of your Artifactory release repo. |
| repository_name | optional, updatable | String | repository_name | The name of your Artifactory repo where your Docker images are located. |
| repository_url | optional, updatable | String | repository_url | The URL of your Artifactory repo where your Docker images are located. |
| snapshot_url | optional, updatable | String | snapshot_url | The URL of your Artifactory snapshot repo. |
| token | optional, updatable | Password | token | The Access Token for your Artifactory repo. You can use a toolchain secret reference for this parameter. For more information about toolchain secret references, see [Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| type | required, updatable | String | type | The repo type for your Artifactory tool integration. |
| user_id | optional, updatable | String | user_id | The user ID or email address for your Artifactory repo. |
{: caption="Table 1. Artifactory tool integration parameters" caption-side="bottom"}

## Learn more about Artifactory
{: #learn_more_artifactory}

To learn more about Artifactory, see the [Artifactory article](https://www.ibm.com/garage/method/practices/deliver/tool_artifactory/){: external} on the IBM Cloud Garage Method.
