---

copyright:
  years: 2015, 2018
lastupdated: "2017-12-6"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Creating a Deploy to {{site.data.keyword.Bluemix_notm}} button {: #deploy-button}

The Deploy to {{site.data.keyword.Bluemix_notm}} button is an efficient way to share your public Git-sourced app so that other people can experiment with the code and deploy it to IBM {{site.data.keyword.Bluemix_notm}} by using a toolchain. The button requires minimal configuration and you can insert it anywhere that supports markup. Anyone who clicks the button creates a cloned copy of the code in a new Git repository (repo) so that your original app remains unaffected.
{: shortdesc}

When someone clicks your button, these actions occur:

1. If the person does not have an active {{site.data.keyword.Bluemix_notm}} account, they must create an account. They can create a trial account or a real account.

2. The person can select a region, organization, space, and app name by clicking the {{site.data.keyword.deliverypipeline}} icon. The suggested app name is the same as the toolchain name, which is constructed from the name of your original Git repo and the time. The toolchain name can also be edited.

3. A toolchain is created that includes a new private clone of your Git repo, a pipeline for building and deploying code changes, the Eclipse Orion {{site.data.keyword.webide}} for editing code on the Cloud, and an issue tracker.

  **Tip**: If the `.bluemix` directory contains a `toolchain.yml` file, the file is used to specify the tool integrations for the toolchain. For more information about the `toolchain.yml` file, see [Creating custom toolchains](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}.

4. If the app requires a build file, the build file is detected automatically and the app is built.

5. If a pipeline is configured for the build and deployment process, a `pipeline.yml` file is used to deploy the app.

6. If the app requires a container, a `pipeline.yml` file that defines the IBM Containers service and a Dockerfile that defines an image are used to deploy the app in a {{site.data.keyword.Bluemix_notm}} container.

7. The app is deployed to the {{site.data.keyword.Bluemix_notm}} organization that the person selected.

## Examples of the button {: #button-examples}

See an app button example for a public {{site.data.keyword.gitrepos}} repo:

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

See an app button example for a public GitHub repo:

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## Creating a button {: #create-button}

To create a Deploy to {{site.data.keyword.Bluemix_notm}} button, copy and modify one of the following snippet templates. Specify a Git repository and branch in the URL.

### Creating a button in HTML

To create a button in HTML, copy this snippet and insert a public Git repository URL and branch.

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="Deploy to Bluemix"></a>
```
{: codeblock}

If you don't include the `branch` parameter in your snippet's repository URL, the Deploy to Bluemix button defaults to the repository's master branch.

### Creating a button in Markdown

To create a button in Markdown, copy this snippet and insert a public Git repository URL and branch.

```Markdown
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

If you don't include the `branch` parameter in your snippet's repository URL, the Deploy to Bluemix button defaults to the repository's master branch.

### Using the button snippets {: #button-snippet}

After you create a Deploy to Bluemix button snippet, you can insert it into blogs, articles, wikis, readme files, or anywhere else you want to promote your app.

When you customize the snippet for your Deploy to {{site.data.keyword.Bluemix_notm}} button, consider that both of the templates use a default path to an external button image in PNG format and in English.

* If you prefer to use an SVG image for the button instead of a PNG, change the path to the button image that is used in the snippet to `https://bluemix.net/deploy/button.svg`.

* If you prefer to use an image for the button, change the path of the button image that is used in the snippet to `https://bluemix.net/deploy/button_x2.png`. This image is twice the size of the default one.

* If you prefer to store the image locally, you can download the image and store it in your Git repo. Adjust the path to use the relative location of the image.

* If you want to use a translated version of the button, you can reference it remotely or download it from [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![External link icon](../../icons/launch-glyph.svg "External link icon")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}.

## Repository considerations {: #button-repo}

Review these considerations for the repo that you use in your Deploy to {{site.data.keyword.Bluemix_notm}} button.

### Manifest file requirements

A `manifest.yml` file is not required to be in your repo. However, if your app requires other services to run, you must provide a manifest file that declares those services.

With the manifest file, you can specify:

* A unique app name.

* Declared services, a manifest extension which creates or looks for the required or optional services that are expected to be set up before the app is deployed, such as a data cache service. You can find a list of the eligible {{site.data.keyword.Bluemix_notm}} services, labels, and plans by using the [CF Command Line Interface ![External link icon](../../icons/launch-glyph.svg)](https://github.com/cloudfoundry/cli/releases) to run the `cf marketplace` command or by browsing the [{{site.data.keyword.Bluemix_notm}} catalog](https://console.bluemix.net/catalog?ssoLogout=true&cm_mmc=developerWorks-_-dWdevcenter-_-devops-services-_-lp#/store).

Declared services is an IBM extension of the standard Cloud Foundry manifest format. This extension might be revised in a future release as the feature evolves and improves.

If you don't know how to create manifest files, [learn how to create them here ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#minimal-manifest){:new_window}.

```YAML
---
    #Template manifest.yml

  declared-services:
    arbitrary_service_instance_name:  # [required]
      label: actual_service_name # [required] The actual service name from market place
      plan: Shared # [optional] If provided, used to fetch the declared service. Otherwise, defaults to 'Free' or 'free'.
  applications:
  - services
    - arbitrary_service_instance_name
    name: appname
    host: apphostname
```
{: codeblock}

```YAML
---
    #Example manifest.yml

  declared-services:
      sample-java-cloudant-cloudantNoSQLDB:
        label: cloudantNoSQLDB
        plan: Shared
  applications:
  - services
    - sample-java-cloudant-cloudantNoSQLDB
    name: My app
    host: myapp
```
{: codeblock}


### Build file requirements

If the app must be built before it can be deployed, you must include a build file in your repo. If a build script file is detected in the root directory of the repo, an automated build of the code is triggered before deployment.

Supported builders include:

* [Ant ![External link icon](../../icons/launch-glyph.svg "External link icon"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`, which builds output to the `./output/` folder
* [Gradle ![External link icon](../../icons/launch-glyph.svg "External link icon"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window} `/build.gradle`, which builds output to the `.` folder
* [Grunt ![External link icon](../../icons/launch-glyph.svg "External link icon"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`, which builds output to the `.` folder
* [Maven ![External link icon](../../icons/launch-glyph.svg "External link icon"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window} `/pom.xml`, which builds output to the `./target/` folder

### Pipeline file requirements

To configure the pipeline for the toolchain in a `.bluemix` directory, include a `pipeline.yml` file. For each `pipeline.yml` file in that directory, a pipeline is created when the toolchain is instantiated.

To create a pipeline file, consult the example file in the [custom toolchain pipeline instructions](toolchains_custom.html#toolchains_custom_pipeline_yml). Just as when you define a pipeline in the web interface, you define a pipeline in text by creating stages and jobs, setting inputs and environment variables, and adding scripts. You can also see a number of more complex pipeline files in [this demonstration project](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix).

### Container dockerfile requirements

To deploy an app in a container by using IBM Containers, you must include a Dockerfile in the root directory of the repo and, in a `.bluemix` directory, include a `pipeline.yml` file.

The Dockerfile acts as a kind of build script for the app. If a Dockerfile is detected in the repo, the app is automatically built into an image before it is deployed in a container. If the app itself must be built before the app is built into an image, include a build script for the app and a Dockerfile.

To learn more about creating Dockerfiles, see the [Docker documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.docker.com/reference/builder/){:new_window}.

To create a `pipeline.yml` manually that is specifically for containers, see the [examples in GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/Puquios/){:new_window}.
