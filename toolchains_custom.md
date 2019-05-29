---

copyright:
  years: 2017, 2019
lastupdated: "2019-05-28"

keywords: toolchain template, Configuration properties, readme file

subcollection: ContinuousDelivery

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Creating custom toolchain templates
{: #toolchains_custom}

Improve your DevOps workflow by creating a custom toolchain template. You can get started quickly with an existing toolchain template, or create a toolchain template that includes only the tool integrations that you need. You can add or remove integrations from your toolchain at any time.
{:shortdesc}

You can [create a toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started){: new_window} in several ways. After you create a custom toolchain template, you can share it by [creating a deploy to {{site.data.keyword.Bluemix_notm}} button](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deploy-button){: new_window}. For more information about the toolchain template SDK, see [Open Toolchain SDK](https://github.com/open-toolchain/sdk/wiki/){:new_window}. For a step-by-step tutorial, see the [Garage Method site](https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain/){:new_window}.


## Getting started
{: #toolchains_custom_gettingstarted}

To create a custom toolchain template, begin by cloning the Simple Cloud Foundry toolchain template. Cloning an existing template gives you a starting point for your customized toolchain.

1. Using the Git client of your choice, enter the following command to clone the [Simple Toolchain](https://github.com/open-toolchain/simple-toolchain){: new_window} template in GitHub.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 This template deploys a basic Hello World application from a single GitHub repository and includes a simple toolchain that is preconfigured for continuous delivery, source control, issue tracking, and online editing.

2. If you want to start with a more complex toolchain template, clone the [Cloud-native Toolchain for Microservices template](https://github.com/open-toolchain/toolchain-demo){: new_window}.

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

The microservices template deploys an online store that is composed of three microservices, each contained in their own GitHub repository. It also is a more complex toolchain that is preconfigured for:
* Continuous delivery
* Source control
* Blue-green deployments
* Functional testing
* Issue tracking
* Online editing
* Messaging

Regardless of which template you choose, the process for customizing the toolchain that you create is generally the same.

After you clone the template, you have a basic GitHub repository that contains a readme file and a `.bluemix` directory. The directory contains all of the configuration files that the toolchain requires to function. At a minimum, the `.bluemix` directory must contain the following files:

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![Minimum files that are needed to define a toolchain](images/min_files_for_a_toolchain.png)


Each of these files is explained in the following sections. Each section contains configuration information that you can consult as your toolchain evolves.
YAML is a data serialization language that is a strict superset of JSON, with the addition of syntactically significant newlines and indentation. However, YAML doesn’t allow literal tab characters.

## Understanding the configuration files
{: #toolchains_custom_config_files}


The toolchain template configuration files are comprised primarily of YAML formatted files. Each file contains metadata that describes different aspects of the toolchain. The metadata includes:
* Information about the toolchain and repositories.
* Details about how code is built and deployed.
* Configuration properties for the tools that are in the toolchain.

As your toolchain becomes more complex, the configuration files might become more complex.

When you work with YAML files, follow these guidelines:

* Only spaces use spaces. Tabs are not allowed.
* All properties and lists must be indented with one or more spaces.
* All keys and properties are case-sensitive.

Pay careful attention to the YAML file's formatting to reduce your chance of encountering errors.
To check for errors, use a simple validator such as [this parser](http://wiki.ess3.net/yaml/){: new_window}.
{: important}

## Planning the services
Each service subsection contains the following information:

* name - A user-generated string that is used to identify this service in the context of the current file. You can use this name to mark a service as required.

* service_id - A unique string that identifies the service. This string comes directly from the [service catalog](https://github.com/open-toolchain/sdk/wiki/services.md){: new_window}.

* parameters - Zero or more configuration parameters for the service. These parameters vary between services. Users must consult the catalog to determine which parameters are required by a particular service.

### Including text from other files

All of the information for your toolchain can be stored in the `toolchain.yml` file. However, you might want to create separate files for each tool integration UI that uses `$text`. Using separate files can make maintaining your toolchains easier, and minimize the time that you spend editing configuration files. This example snippet from a `toolchain.yml` file shows how to use the contents of the `pipeline.yml` file as the value for `content`.

```
  configuration:
    content:
      $text: pipeline.yml
```

### Localizing your toolchain template

You can localize your toolchain by externalizing your UI strings in the `nls` directory so that the strings in the toolchain are displayed in the user's preferred language.
Your `toolchain.yml` file must include an `$i18n` reference.  
The following example shows an `$i18n` reference to a `messages.yml` file:

```
messages:
  $i18n: messages.yml
```

  The English strings are in `messages.yml` and other languages use the languages code, such as `messages_de.yml`. You can find the list of language codes in
  [Tags for Identifying Languages](https://tools.ietf.org/html/rfc5646){: new_window}.

   To reference the externalize string, use `$ref` to retrieve the string.  For example,

```
  template:
    name:
      $ref: "#/messages/template.name"
```

  If you don't use externalized strings, you can use:

```
  template:
    name: my_template
```

For more information about UI strings, see the [Messages section of the Open Toolchain SDK](https://github.com/open-toolchain/sdk/wiki/Template-File-Format#messages-section){: new_window}.

## Configuring the toolchain file
{: #toolchains_custom_toolchain_yml}

The `toolchain.yml` file is the heart of your toolchain. The specifics of your toolchain, including the repositories to pull in, the services to include, and the build details are all outlined in this file. To understand its contents, you can break down the file into several sections.

1\. **Introductory toolchain information:**

 This section of the file provides simple details about your toolchain that the user can see on the toolchain creation page. Include a name for your toolchain, along with a description that explains the toolchain's purpose. You can also include an image, such as a logo or a visual depiction of your toolchain.

 In addition to providing introductory content for your toolchain, this section also includes a key that is named `required` that defines the tools that are part of the toolchain. The toolchain's creator configures these tools when they create the toolchain from your template. For each tool that can be configured on the toolchain creation page, add the tool's parent key as it is defined in the `toolchain.yml` file as a property of the `required` key.

 This snippet shows an example of this section:

 ```
 ---
template
  name: "Simple Toolchain"
  description: "This Hello World application uses Node.js and includes a toolchain that is preconfigured for continuous delivery, source control, issue tracking, and online editing.\n\nTo get started, click **Create**."
  header: '![](toolchain.svg)'
  icon: icon.svg
  required:
   - sample-build
   - sample-repo
  info:
    git url: >-
      [https://github.com/my-toolchain/simple-toolchain](https://github.com/open-toolchain/simple-toolchain)
    git branch: >-
      [master](https://github.com/my-toolchain/simple-toolchain/tree/master)
  ```
 {: codeblock}

In that example, the Git URL and Git branch are for a new toolchain template.

2\. **Repository definitions:**

 A toolchain can provide continuous delivery for any number of Git repositories such as GitHub, GitHub Enterprise, Git Repos and Issue Tracking, and GitLab. The repository definitions section of the `toolchain.yml` file is where each repository is defined.

 For each repository that is added to the toolchain, add a parent key that represents the name of your repository with the following properties:

| Item | Key/Property | Value | Description |
|------|--------------|-------|-------------|
| repo-name | key |  | Repository name. This key matches the name (sample-repo) |
| service_id | property | <`githubpublic` , `githubprivate`, `hostedgit`, `gitlab`> | Type of repository |
| parameters: | key |  |  |
| repo_name | property |  | Pattern for repo-name. The example that follows uses the toolchain name as the repo name |
| repo_url | property |  | URL of the repository |
| type | property | <`new` , `fork` , `clone` , `link`> | How to create the new repository |
| has_issues | property | <`true` , `false`> | Use Issues |
| enable_traceability | properties |  <`true` , `false`> | Determines whether to track the deployment of code changes by creating tags, labels and comments on commits, pull requests and referenced issues.|
{: caption="Table 1. Repo keys and property values" caption-side="top"}

 If you define multiple repositories and configure them as `has_issues: true`, a single instance of GitHub Issue tracker is added to the toolchain. The tracker follows issues for all repositories that are set to `true`.
 {: tip}

 This snippet shows an example of this section:

 ```
 # Github repos
 services:
  sample-repo:
    service_id: githubpublic
    parameters:
      repo_name: '{{toolchain.name}}'
      repo_url: 'https://github.com/open-toolchain/node-hello-world'
      type: clone
      has_issues: true
      enable_traceability: true
 ```
 {: codeblock}

3\. **Pipeline information:**

 You can continuously deliver your project with a pipeline. This section of the file defines the configuration details that are used to build and deploy the code in each of your GitHub and Git Repos and Issue Tracking repositories.

 To start, for each repository that is defined in your toolchain, add a parent key that represents a name of its pipeline. Consider deriving this key from the name of your GitHub or Git Repos and Issue Tracking repository. Add the following properties:

| Item | Key/Property | Value | Description |
|------|--------------|-------|-------------|
| pipeline-name | key |  | Name for the pipeline (sample-build) |
| service_id | property | <`pipeline`> | Name of the service to use |
| parameters | key |  |  |
| name | property | <`repo_name`> | Same as the name defined in the repos section |
| ui-pipeline | property | <`true` , `false`> |True if the applications that this pipeline deploys are shown in the **View app** menu on the toolchains page  |
| configuration | key |  |  |
| content | property | <`$ref(pipeline.yml)`> | File that defines your pipeline definition |
| env | key |  |  |
| SAMPLE_REPO | key | <`repo-name-key`> | The same name as your repository parent key |
| CF_APP_NAME |  property | <`'{{form.pipeline.parameters.prod-app-name}}'`> | Name that is used by Cloud Foundry. Consider incorporating your repository parent key name into this property. |
| PROD_SPACE_NAME | property | <`'{{form.pipeline.parameters.prod-space}}'`> | Name of {{site.data.keyword.Bluemix_notm}} space to deploy to |
| PROD_ORG_NAME | property | <`'{{form.pipeline.parameters.prod-organization}}'`> | Name of {{site.data.keyword.Bluemix_notm}} organization to deploy to |
| PROD_REGION_ID | property | <`'{{form.pipeline.parameters.prod-region}}'`> | Name of {{site.data.keyword.Bluemix_notm}} region to deploy to |
| execute | property | <`true` , `false`> | Start pipeline after creation |
{: caption="Table 2. Pipeline keys and property values" caption-side="top"}

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 More information about creating a `pipeline.yml` file can be found in a [later section.](#toolchains_custom_pipeline_yml)

 The following snippet shows an example of this section of the file:

 ```
 # Pipelines
  sample-build:
    service_id: pipeline
    parameters:
      services:
        - sample-repo
      name: '{{services.sample-repo.parameters.repo_name}}'
      ui-pipeline: true
      configuration:
        content:
          $ref: pipeline.yml
        env:
          SAMPLE_REPO: sample-repo
          CF_APP_NAME: '{{form.pipeline.parameters.prod-app-name}}'
          PROD_SPACE_NAME: '{{form.pipeline.parameters.prod-space}}'
          PROD_ORG_NAME: '{{form.pipeline.parameters.prod-organization}}'
          PROD_REGION_ID: '{{form.pipeline.parameters.prod-region}}'
       execute: true
 ```
 {: codeblock}

4\. **Deployment details:**

 As part of the continuous delivery process, you can configure a toolchain to deploy an application to any {{site.data.keyword.Bluemix_notm}} region, organization, or space to which a user has access. You can specify the details about where to deploy your application on the [toolchain creation](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started){: new_window} page.

This section of the `toolchain.yml` file defines the pipeline stages that are available to configure from the toolchain creation page.

 The parent key `deploy` is used to identify the deployment configuration properties. The following properties comprise the rest of the section:

| Item | Key/Property | Value | Description |
|------|--------------|-------|-------------|
| deploy | key |  | Name of the deployment section |
| schema | property | <`deploy.json`> | File that defines the layout of the UI for configuring your deployment details |
| service-category | property | <`pipeline`> | Service that uses the deployment configurations |
| parameters | key |  |  |
| prod-region | property | <`"{{region}}"`> | Defines the {{site.data.keyword.Bluemix_notm}} region for the production stage |
| prod-organization | property | <`"{{organization}}"`> | Defines the {{site.data.keyword.Bluemix_notm}} organization for the production stage |
| prod-space | property | <`prod`> | Defines the {{site.data.keyword.Bluemix_notm}} space for the production stage |
| github-repo-name | property | <`"{{repo-name-key.parameters.repo_name}}"`> | Variable to pass the GitHub repository name to the toolchain creation page |
{: caption="Table 3. Deployment configuration property keys and values" caption-side="top"}

For more information about creating a `deploy.json` file, see [this section](#toolchains_custom_deploy_json).

 The following example defines a single stage that deploys to a production environment.

 ```
 ## Configuring a deployment stage
 deploy:
   schema: deploy.json
   service-category: pipeline
   parameters:
 	prod-region: "{{region}}"
 	prod-organization: "{{organization}}"
 	prod-space: prod
 	hello-world-name: "{{hello-world-repo.parameters.repo_name}}"
 ```
 {: codeblock}

 You can use the code example, with a few modifications. To customize this section, set `github-repo-name` to be consistent with your repository's name. You must also update details in the [`deploy.json`](#toolchains_custom_deploy_json) file.

 To create a more complex pipeline that includes dev, QA, and Prod stages, you can substitue the following properties under the `parameters` key.

 ```
   parameters:
 	dev-region: "{{region}}"
 	qa-region: "{{region}}"
 	prod-region: "{{region}}"
 	dev-organization: "{{organization}}"
 	qa-organization: "{{organization}}"
 	prod-organization: "{{organization}}"
 	dev-space: dev
 	qa-space: qa
 	prod-space: prod
 ```
 {: codeblock}

 ## Configuring a pipeline
 {: #toolchains_custom_pipeline_yml}

 The `pipeline.yml` file contains all of the configuration details for the stages of your pipeline. You can start with an existing pipeline.yml and customize it to meet your needs.

 If your toolchain contains more than one pipeline, provide unique names for each `pipeline.yml` file.

 The following example shows a `pipeline.yml` file:

 ```
 ---
stages:
- name: BUILD
  inputs:
  - type: git
    branch: master
    service: ${SAMPLE_REPO}
  triggers:
  - type: commit
  jobs:
  - name: Build
    type: builder
- name: DEPLOY
  inputs:
  - type: job
    stage: BUILD
    job: Build
  triggers:
  - type: stage
  properties:
  - name: CF_APP_NAME
    value: undefined
    type: text
  - name: APP_URL
    value: undefined
    type: text
  jobs:
  - name: Blue-Green Deploy
    type: deployer
    target:
      region_id: ${PROD_REGION_ID}
      organization: ${PROD_ORG_NAME}
      space: ${PROD_SPACE_NAME}
      application: ${CF_APP_NAME}
    script: |
      #!/bin/bash
      # Push app
      if ! cf app $CF_APP; then  
        cf push $CF_APP
      else
        OLD_CF_APP=${CF_APP}-OLD-$(date +"%s")
        rollback() {
          set +e  
          if cf app $OLD_CF_APP; then
            cf logs $CF_APP --recent
            cf delete $CF_APP -f
            cf rename $OLD_CF_APP $CF_APP
          fi
          exit 1
        }
        set -e
        trap rollback ERR
        cf rename $CF_APP $OLD_CF_APP
        cf push $CF_APP
        cf delete $OLD_CF_APP -f
      fi
      # Export app name and URL for use in later Pipeline jobs
      export CF_APP_NAME="$CF_APP"
      export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
      # View logs
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## Configuring the pipeline interface
 {: #toolchains_custom_deploy_json}

 On the [toolchain creation](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started){: new_window} page, when Delivery Pipeline is selected from the Configurable Integrations section, the section expands to display the following items:

 	* The application's name.
 	* The region, organization, and space that your pipeline stages deploy to.

You can configure those items for each tool.

 The layout of this section in the UI is defined by the `deploy.json` schema.

 Within the schema, update the following properties to match the details of your application:

 	* Title
 	* Description
 	* LongDescription
 	* All instances of `hello-world-name` and the associated details

 The following snippet is an example of a `deploy.json` file:

 ```
 {
    "$schema": "http://json-schema.org/draft-04/schema#",
    "messages": {
        "$i18n": "locales.yml"
    },
    "title": {
        "$ref": "#/messages/deploy.title"
    },
    "description": {
        "$ref": "#/messages/deploy.description"
    },
    "longDescription": {
        "$ref": "#/messages/deploy.longDescription"
    },
    "type": "object",
    "properties": {
        "prod-region": {
            "description": "The {{site.data.keyword.Bluemix_notm}} region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The {{site.data.keyword.Bluemix_notm}} org",
            "type": "string"
        },
        "prod-space": {
            "description": "The {{site.data.keyword.Bluemix_notm}} space",
            "type": "string"
        },
        "prod-app-name": {
            "description": {
                "$ref": "#/messages/deploy.appDescription"
            },
            "type": "string",
            "pattern": "\\S"
        }
    },
    "required": [
        "prod-region",
        "prod-organization",
        "prod-space",
        "prod-app-name"
    ],
    "form": [
        {
            "type": "validator",
            "url": "/devops/setup/bm-helper/helper.html"
        },
        {
            "type": "text",
            "readonly": false,
            "title": {
                "$ref": "#/messages/deploy.appName"
            },
            "key": "prod-app-name"
        },
        {
            "type": "table",
            "columnCount": 4,
            "widths": [
                "15%",
                "28%",
                "28%",
                "28%"
            ],
            "items": [
                {
                    "type": "label",
                    "title": ""
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/region"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/organization"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/space"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/prodStage"
                    }
                },
                {
                    "type": "select",
                    "key": "prod-region"
                },
                {
                    "type": "select",
                    "key": "prod-organization"
                },
                {
                    "type": "select",
                    "key": "prod-space",
                    "readonly": false
                }
            ]
        }
    ]
}
 ```
 {: codeblock}


## Other tool configurations

 After you configure the core components of your toolchain, you can include other tool integrations that add more functions to your toolchain. All additional tools require their own entry in the `toolchain.yml` file. Some tools also require that you add a separate YAML configuration file to the `.bluemix` directory.

 ![Files needed to define a toolchain](images/files_for_toolchain_with_additional_tools.png)

To see the list of available tool integrations, see <a href="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">Services available in a toolchain template</a>. The following examples show how to format additions to a toolchain YAML file.

### **Slack**

#### toolchain.yml
{: #slack_toolchain_yaml}

```
messaging:
  service_id: slack
  $ref: slack.yml
```
{: codeblock}

#### slack.yml
{: #slack_slack_yaml}

```
---YAML
parameters:
  api_token: ""
  channel_name: ""
```
{: codeblock}

### **Sauce Labs**

#### toolchain.yml
{: #sauce_toolchain_yaml}

```YAML
test:
  service_id: saucelabs
  $ref: saucelabs.yml
```
{: codeblock}

#### saucelabs.yml
{: #sauce_slack_yaml}

```YAML
---
parameters:
  username: ""
  key: ""
```
{: codeblock}

### **Eclipse Orion Web IDE**

####	toolchain.yml
{: #eclipse_toolchain_yaml}

```YAML
webide:
  service_id: orion
```
{: codeblock}
