---

copyright:
  years: 2021
lastupdated: "2021-06-29"

keywords: DevSecOps

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Pull request pipeline
{: #cd-devsecops-pr-pipeline}

Pull request pipeline runs set compliance status checks on a pull request for the specified application (app) repository (repo).
{:shortdesc}

Attempts to merge a pull request into the master branch might be blocked because of failed compliance status checks. Opening or updating a pull request against the master branch triggers the pull request pipeline to run. You can run your own setup for the pipelines and tests in [custom script](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-custom-scripts){: external}.

## Stages and tasks
{: #cd-devsecops-pipeline-order}

|Task or stage |Short description	|Customizable in `.pipeline-config.yaml` |
|:----------|:------------------------------|:------------------|
|`start` 		 |Set up the pipeline environment. 		|No		|
|`setup`		 |Set up your build and test environment.			|Yes|
|`unit-tests`|Run unit tests and app tests on app code.		|Yes |
|`compliance-checks` 	 |Run Code Risk Analyzer scans and other compliance checks on app repos.   	|No			|
{: caption="Table 1. Pipeline order" caption-side="top"}

## Scans and checks in compliance checks
{: #cd-devsecops-pipeline-compliancechecks}

| Scan or check |  Description | 
|---------|------------|
| Detect secrets | The [IBM Detect Secrets](https://github.com/IBM/detect-secrets) tool identifies where secrets are visible in app code. |
| Code Risk Analyzer vulnerability scan | Finds vulnerabilities for all of the app package dependencies, container base images, and operating system packages. Uses the Code Risk Analyzer tool. |
| Code Risk Analyzer CIS check |  Runs configuration checks on Kubernetes deployment manifests. Uses the Code Risk Analyzer tool. | 
| Code Risk Analyzer Bill of Material (BOM) check | The BOM for a specified repo that captures the pedigree of all of the dependencies. This BOM is collected at different granularities. For example, the BOM captures the list of base images that are used in the build, the list of packages from the base images, and the list of app packages that are installed over the base image. The BOM acts as a ground truth for the analytic results and can potentially be used to enforce policy gates. Uses the Code Risk Analyzer tool. |
| Repository compliance checking | Checks that branch protection settings are correct. |
{: caption="Table 2. Compliance scans and checks" caption-side="top"}
    
These scripts are run on all of the app repos that the pipeline is aware of. To add repos to these scans, use the [`pipelinectl`](/docs/ContinuousDelivery?topic=ContinuousDelivery-pipelinectl) interface that is provided in your setup stage.

For more information about using multiple GitHub Enterprise repos in pull request and continuous integration pipelines, see [Using GitHub Enterprise repos in pull request and continuous integration pipelines](#cd-devsecops-gherepos-pipelines). For more information about the expected output from user script stages, see [Custom scripts](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-custom-scripts).

## Task jobs
{: #cd-devsecops-pipeline-jobs}

| Task job |  Description | 
|---------|------------|
| `code-pr-start` | Clones app and DevSecOps repos, and sets the initial pending state for status checks on {{site.data.keyword.gitrepos}} repos. |
| `code-setup` | The placeholder for a user-defined setup custom script where the user can complete their pipeline setup. |
| `code-unit-tests` |  The placeholder for a user-defined test custom script where the user can run their own tests. | 
| `code-pr-finish` | Runs all of the required compliance checks, comments the results to the pull request, and sets their result on the {{site.data.keyword.gitrepos}} repos. |
{: caption="Table 3. Compliance scans and checks" caption-side="top"}

## Merge pull requests with issues
{: #cd-devsecops-merge-pr}

You can use Administrator rights to merge pull requests with failed status checks to the repo. However, these pull requests register a `failure` result in their evidence for the failing task. This result is included in the evidence summary and change request description, and impacts the final compliance score on the Security and Compliance Center.

## Environment properties
{: #cd-devsecops-environment-prop}

The following table lists and describes the pipeline parameters that are provided out of the box for pull request pipelines:

|Name |Type	|Description |Required or Optional |
|:----------|:------------------------------|:------------------|:----------|
|`git-token`		                |SECRET		|The {{site.data.keyword.gitrepos}} repo token.	|Optional			|
|`ibmcloud-api-key`	          |SECRET		|The {{site.data.keyword.cloud}} API key that interacts with the `ibmcloud` CLI tool.	|Required			|
|`pipeline-config-repo`		      |text		  |The URL of the repo that contains the pipeline configuration YAML and scripts.	|Optional			|
|`pipeline-config-branch`		    |text		  |The branch in the `pipeline-config-repo` that contains the  configuration YAML and scripts.	|Optional			|
|`pipeline-config`		          |text		  |The name of the configuration YAML file that customizes pipeline behavior.	|Optional			|
|`pipeline-dockerconfigjson`		|SECRET		|The base64-encoded Docker `config.json` file that pulls images from a private registry.	|Optional			|
|`pipeline-debug`		            |select		|The pipeline debug mode switch.	|Optional			|
|`slack-notifications`		      |text		  |The switch that turns the Slack integration on or off.	|Optional			|
{: caption="Table 4. Environment properties}

You can add parameters to the pipelines on the pipeline UI, and access them from the [custom scripts](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-custom-scripts).
{: tip}
