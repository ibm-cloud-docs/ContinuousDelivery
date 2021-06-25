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
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Pull request pipeline
{: #cd-devsecops-pr-pipeline}

Pull request pipeline runs set compliance status checks on a pull request for the specified application repository (repo).
{:shortdesc}

Attempts to merge a pull request into the master branch might be blocked because of failed compliance status checks. Opening or updating a pull request against the master branch triggers the pull request pipeline to run. You can run your own setup for the pipelines and tests in [custom script](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-custom-scripts){: external}.

## Pipeline order
{: #cd-devsecops-pipeline-order}

|Task |Steps	|Description |
|:----------|:------------------------------|:------------------|
|code-pr-start 		|`start`, `prepare-next-stage` 		|The pipeline initialization.			|
|code-setup		|`prepare`, `run-stage`, `prepare-next-stage`		|The user-defined script setup stage.			|
|code-unit-tests		|`prepare`, `run-stage`, `prepare-next-stage` 		|The user-defined script unit tests stage.		|
|code-pr-finish		|`prepare`, `detect-secrets`, `cra-discovery`, `cra-remediation`, `cra-remediation-comment`, `cra-cis-check`, `cra-cis-check-comment`		|Run compliance checks.		|
{: caption="Table 1. Pipeline order" caption-side="top"}

### Task jobs
{: #cd-devsecops-pipeline-jobs}

* `code-pr-start`: Clones app and DevSecOps repos, and sets the initial pending state for status checks on Git Repo and Issue Tracking Repositories.
* `code-setup`: The placeholder for a user-defined setup custom script where the user can complete their pipeline setup.
* `code-unit-tests`: The placeholder for a user-defined test custom script where the user can run their own tests.
* `code-pr-finish`: Runs all of the required compliance checks, comments the results to the pull request and sets their result on the Git Repo and Issue Tracking Repositories.

## Merge pull requests with issues
{: #cd-devsecops-merge-pr}

You can use Administrator rights to merge pull requests with failed status checks to the repo. However, these pull requests register a `failure` result in their evidence for the failing task. This result is included in the evidence summary, change request description, and impacts the final compliance score on the Security and Compliance Center.

## Environment properties
{: #cd-devsecops-environment-prop}

The following table lists and describes the pull request parameters that are provided out of the box for pipelines:

|Name |Type	|Description |Required or Optional |
|:----------|:------------------------------|:------------------|:----------|
|artifactory-dockerconfigjson 		|SECRET 		|The base64-encoded Docker `config.json` file that pulls the shift-left pipeline compliance images.			|Optional			|
|baseimage-auth-user		|text		|The credentials for the base image of the application Dockerfile, required by the Code Risk Analyzer scan.			|Optional			|
|baseimage-auth-email		|text 		|The credentials for the base image of the application Dockerfile, required by the Code Risk Analyzer scan.		|Optional			|
|baseimage-auth-host		|text		|The credentials for the base image of the application Dockerfile, required by the Code Risk Analyzer scan.	|Optional			|
|baseimage-auth-password		|SECRET		|The credentials for the base image of the application Dockerfile, required by the Code Risk Analyzer scan. |Optional			|
|git-token		|SECRET		|The Git Repo and Issue Tracking Repository token.	|Optional			|
|ibmcloud-api-key		|SECRET		|The {{site.data.keyword.cloud}} API key that interacts with the `ibmcloud` CLI tool.	|Required			|
|pipeline-config		|text		|The configuration file that customizes pipeline behavior.	|Optional			|
|pipeline-config-branch		|text		|The branch of the pipeline configuration.	|Optional			|
|pipeline-config-repo		|text		|The repo URL of the pipeline configuration location.	|Optional			|
|pipeline-dockerconfigjson		|SECRET		|The base64-encoded Docker `config.json` file that pulls images from a private registry.	|Optional			|
|pipeline-debug		|select		|The pipeline debug mode switch.	|Optional			|
|slack-notifications		|text		|The switch that turns the Slack integration on or off.	|Optional			|
{: caption="Table 2. Environment properties}

You can add parameters to the pipelines on the pipeline UI, and access them from the [custom scripts](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-custom-scripts).
{: tip}
