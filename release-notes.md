---

copyright:
  years: 2019, 2022
lastupdated: "2022-09-16"

keywords: IBM Cloud Continuous Delivery, release notes, CD

subcollection: ContinuousDelivery

content-type: release-note

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:screen: .screen}
{:pre: .pre}
{:codeblock: .codeblock}
{:tip: .tip}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}
{:release-note: data-hd-content-type='release-note'}

# Release notes for {{site.data.keyword.contdelivery_short}}
{: #cd-relnotes}

Use these release notes to learn about the latest updates to {{site.data.keyword.contdelivery_full}} that are grouped by date. Release notes are available for a minimum of three years.
{: shortdesc}

## 16 September 2022
{: #ContinuousDelivery-sept1622}
{: release-note}

{{site.data.keyword.contdelivery_short}} service instances and toolchains that reside in Cloud Foundry orgs are no longer supported.
:   Services instances and toolchains that reside in resource groups remain fully supported.

## 08 September 2022
{: #ContinuousDelivery-sept0822}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.1.6](https://about.gitlab.com/releases/2022/08/30/critical-security-release-gitlab-15-3-2-released/){: external}.

## 22 July 2022
{: #ContinuousDelivery-july2222}
{: release-note}

The Beta Terraform resources and data sources, Go SDKs, and HTTP APIs are now available for working with Toolchains and Tekton Pipelines.
:   Terraform resources and data sources: [IBM-Cloud provider](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest){: external}.
:   Go SDKs: Open-source repository (repo) [continuous-delivery-go-sdk](https://github.com/IBM/continuous-delivery-go-sdk){: external}.
:   HTTP APIs: [{{site.data.keyword.contdelivery_short}} Toolchain](https://cloud.ibm.com/apidocs/toolchain){: external} and [{{site.data.keyword.contdelivery_short}} Tekton Pipeline](https://cloud.ibm.com/apidocs/tekton-pipeline){: external}.

    Ask questions and provide feedback in the [#ask-your-question](https://ibm-devops-services.slack.com/archives/C5AHRCLHH){: external} Slack channel.

## 20 July 2022
{: #ContinuousDelivery-july2022}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.0.4](https://about.gitlab.com/releases/2022/06/30/critical-security-release-gitlab-15-1-1-released/){: external}.

## 12 July 2022
{: #ContinuousDelivery-july1222}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.10.5](https://about.gitlab.com/releases/2022/06/30/critical-security-release-gitlab-15-1-1-released/){: external}.

## 08 July 2022
{: #ContinuousDelivery-july0822}
{: release-note}

The Eclipse Orion {{site.data.keyword.webide}} feature in the {{site.data.keyword.contdelivery_full}} service is deprecated.
:   The {{site.data.keyword.contdelivery_short}} service does not provide a direct replacement.

:   As of 8 August 2022, new toolchains will not include the {{site.data.keyword.webide}} as a default tool. You cannot create and add instances of the {{site.data.keyword.webide}} tool integration to existing toolchains. Existing instances of the {{site.data.keyword.webide}} continue to operate normally.

:   As of 7 October 2022, the {{site.data.keyword.webide}} tool integration will be removed from existing toolchains and the associated data will be deleted. It is recommended that you export your data from your {{site.data.keyword.webide}} workspace before this date, or commit and push all of your outstanding changes into a Git repository.

## 30 June 2022
{: #ContinuousDelivery-june3022}
{: release-note}

Private workers can now be run in stand-alone mode.
:   [Using {{site.data.keyword.deliverypipeline}} Private Workers in stand-alone mode](/docs/ContinuousDelivery?topic=ContinuousDelivery-standalone-mode-private-workers).

Private workers can now be managed on a Satellite cluster, providing easier management of workers on {{site.data.keyword.redhat_openshift_full}} clusters by using the Operator Lifecycle Manager (OLM) framework.
:   [Installing {{site.data.keyword.deliverypipeline}} Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers#pw_install_prereqs).

## 23 June 2022
{: #ContinuousDelivery-june2322}
{: release-note}

New toolchain template demonstrates how to use a pull-based deployment mechanism to continuously deploy Kubernetes resources to multiple clusters on [IBM Cloud Satellite](/docs/satellite) by using a Tekton pipeline.
:   [Satellite Template](https://cloud.ibm.com/devops/setup/deploy?repository=https://us-south.git.cloud.ibm.com/open-toolchain/satellite-cd-toolchain&env_id=ibm:yp:us-south){: external}.

## 13 June 2022
{: #ContinuousDelivery-june1322}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.10.4](https://about.gitlab.com/releases/2022/06/01/critical-security-release-gitlab-15-0-1-released/){: external}.

## 07 June 2022
{: #ContinuousDelivery-june2322}
{: release-note}

Private information in {{site.data.keyword.contdelivery_short}} and toolchains can now be protected by the Customer Root Key as part of Bring Your Own Key.
:   [Bring Your Own Key](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_professional_plan) is available only in a professional plan.

## 23 May 2022
{: #ContinuousDelivery-may2322}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.9.4](https://about.gitlab.com/releases/2022/05/02/security-release-gitlab-14-10-1-released/){: external}.

## 18 May 2022
{: #ContinuousDelivery-may1822}
{: release-note}

New toolchain template demonstrates how to deploy a sample NodeJS application with [Code Engine](/docs/codeengine) by using a Tekton pipeline.
:   [Code Engine Template](https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcode-engine-toolchain&env_id=ibm:yp:us-south){: external}.

## 5 May 2022
{: #ContinuousDelivery-may0522}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.8.5](https://about.gitlab.com/releases/2022/03/31/critical-security-release-gitlab-14-9-2-released/){: external}.

## 1 March 2022
{: #ContinuousDelivery-mar0122}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.7.4](https://about.gitlab.com/releases/2022/02/25/critical-security-release-gitlab-14-8-2-released/){: external}.

## 17 February 2022
{: #ContinuousDelivery-feb1722}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.6.4](https://about.gitlab.com/releases/2022/02/03/security-release-gitlab-14-7-1-released/){: external}.

## 24 January 2022
{: #ContinuousDelivery-jan2422}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.5.3](https://about.gitlab.com/releases/2022/01/11/security-release-gitlab-14-6-2-released/){: external}.

## 7 January 2022
{: #ContinuousDelivery-jan0722}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.4.4](https://about.gitlab.com/releases/2021/12/06/security-release-gitlab-14-5-2-released/){: external}.

## 30 November 2021
{: #ContinuousDelivery-nov3021}
{: release-note}

{{site.data.keyword.contdelivery_full}} is now available in the Sao Paulo region.
:   Each location has three different data centers and provides a full cloud service stack to enable high availability, redundancy, and geographical dispersion.

## 29 November 2021
{: #ContinuousDelivery-nov2921}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.4.2](https://about.gitlab.com/releases/2021/12/10/security-release-gitlab-runner-14-5-2-released/){: external}.

## 4 November 2021
{: #ContinuousDelivery-nov0421}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 14.3.4](https://about.gitlab.com/releases/2021/10/28/security-release-gitlab-14-4-1-released/){: external}.

## 31 October 2021
{: #ContinuousDelivery-oct3121}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.27.3](https://github.com/tektoncd/pipeline/releases/tag/v0.27.3){: external}.

## 21 October 2021
{: #ContinuousDelivery-oct2121}
{: release-note}

New in the DevSecOps reference implementation:
:   SonarQube scanning
:   Additional validations for image signing
:   Improvements to the getting-started experience

    Read the [announcement](https://www.ibm.com/cloud/blog/announcements/whats-new-with-devsecops-in-ibm-cloud){: external}.

## 7 October 2021
{: #ContinuousDelivery-oct0721}
{: release-note}

New toolchain templates demonstrate release strategies
:   Rolling: Deploy a new release with no downtime by incrementally updating all the instances in a sequential manner.
:   Blue-Green: Deploy a new release to an environment identical to — and isolated from — current production for quicker rollbacks and ease of testing.
:   Canary: Deploy a new release incrementally to the production environment, gradually replacing the older version of the application with the newer one, gating increments with a test to reducing risks.

    Read the [announcement](https://www.ibm.com/cloud/blog/explore-deployment-strategies-with-ibm-cloud-continuous-delivery){: external}.

## 30 September 2021
{: #ContinuousDelivery-sep3021}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.27.2](https://github.com/tektoncd/pipeline/releases/tag/v0.27.2){: external}.

## 9 July 2021
{: #ContinuousDelivery-jul0921}
{: release-note}

{{site.data.keyword.contdelivery_full}} is now available in the Toronto Region.
:   Each location has three different data centers and provides a full cloud service stack to enable high availability, redundancy, and geographical dispersion.

## 29 June 2021
{: #ContinuousDelivery-jun2921}
{: release-note}

DevSecOps Reference Implementation
:   A complete SDLC following NIST Configuration Management controls that you can configure in a few clicks by using toolchain templates. The workflow will build, scan, test, and deploy your cloud-native applications while ensuring security and compliance goals are met and evidence is retained for any future audits. The workflow can be customized to leverage other enterprise tools or implement custom policies.

    Read the [announcement](https://www.ibm.com/cloud/blog/announcements/devsecops-reference-implementation-for-audit-ready-compliance-across-development-teams){: external}.

## 24 May 2021
{: #ContinuousDelivery-may2421}
{: release-note}

Code Risk Analyzer now scans Terraform
:   Misconfiguration of infrastructure and cloud service dependencies can put enterprise applications and data at risk. Now, Code Risk Analyzer looks for these issues by scanning Terraform Infrastructure as Code (IaC) files.

    Read the [announcement](https://www.ibm.com/cloud/blog/announcements/code-risk-analyzer-adds-terraform-scanning){: external}.

## 30 April 2021
{: #ContinuousDelivery-apr3021}
{: release-note}

{{site.data.keyword.contdelivery_full}} is now available in the Osaka region.
:   Each location has three different data centers and provides a full cloud service stack to enable high availability, redundancy, and geographical dispersion.

## 31 March 2021
{: #ContinuousDelivery-mar3121}
{: release-note}

{{site.data.keyword.contdelivery_full}} is now available in the Sydney region.
:   Each location has three different data centers and provides a full cloud service stack to enable high availability, redundancy, and geographical dispersion.

## 28 February 2021
{: #ContinuousDelivery-feb2821}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.20.1](https://github.com/tektoncd/pipeline/releases/tag/v0.20.1){: external}.

## 30 November 2020
{: #ContinuousDelivery-nov3020}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.18.1](https://github.com/tektoncd/pipeline/releases/tag/v0.18.1){: external}.

## 2 November 2020
{: #ContinuousDelivery-nov0220}
{: release-note}

New Code Risk Analyzer scans source code repositories for:
:   Known vulnerabilities in open source dependencies
:   Known vulnerabilities in operating system dependencies
:   Conformance to the CIS Docker benchmark
:   Configuration risks in Kubernetes YAML

    Read the [announcement](https://www.ibm.com/cloud/blog/announcements/find-source-code-vulnerabilities-with-code-risk-analyzer){: external}.

## 30 September 2020
{: #ContinuousDelivery-sep3020}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.16.3](https://github.com/tektoncd/pipeline/releases/tag/v0.16.3){: external}.

## 31 July 2020
{: #ContinuousDelivery-jul3120}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.14.1](https://github.com/tektoncd/pipeline/releases/tag/v0.14.1){: external}.

## 30 April 2020
{: #ContinuousDelivery-apr3020}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.11.2](https://github.com/tektoncd/pipeline/releases/tag/v0.11.2){: external}.

## 28 February 2020
{: #ContinuousDelivery-feb2820}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.10.1](https://github.com/tektoncd/pipeline/releases/tag/v0.10.1){: external}.

## 31 October 2019
{: #ContinuousDelivery-oct3119}
{: release-note}

{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.7.0](https://github.com/tektoncd/pipeline/releases/tag/v0.7.0){: external}.

## 30 October 2019
{: #ContinuousDelivery-oct3019}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 12.2.7](https://about.gitlab.com/blog/2019/10/02/security-release-gitlab-12-dot-3-dot-3-released/){: external}.

## 10 October 2019
{: #ContinuousDelivery-oct1019}
{: release-note}

{{site.data.keyword.deliverypipeline}} now has Tekton option.
:   Tekton Pipelines is an open source project that you can use to configure and run continuous integration/continuous delivery (CI/CD) pipelines within a Kubernetes cluster. Pipelines are defined as Tekton resources in YAML, typically stored in a Git repository.
:   Read the [announcement](https://www.ibm.com/cloud/blog/announcements/build-and-deliver-using-tekton-enabled-pipelines){: external}.

## 2 October 2019
{: #ContinuousDelivery-oct0219}
{: release-note}

New DevOps tab in your IBM Cloud Kubernetes Service cluster details.
:   Find all toolchains whose delivery pipelines deployed to that cluster
:   Easily create a new DevOps toolchain
:   Read the [announcement](https://www.ibm.com/cloud/blog/announcements/connecting-ibm-cloud-kubernetes-service-and-ibm-continuous-delivery){: external}.

## 1 October 2019
{: #ContinuousDelivery-oct0119}
{: release-note}

DevOps Insights
:   DevOps Insights features are now part of Continuous Delivery.

## 20 September 2019
{: #ContinuousDelivery-sep2019}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 12.1.9](https://about.gitlab.com/2019/09/10/critical-security-release-gitlab-12-dot-2-dot-5-released/){: external}.

## 16 September 2019
{: #ContinuousDelivery-sep1619}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 12.0.8](https://about.gitlab.com/2019/08/29/security-release-gitlab-12-dot-2-dot-3-released/){: external}.

## 9 September 2019
{: #ContinuousDelivery-sep0919}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 11.11.8](https://about.gitlab.com/2019/08/12/critical-security-release-gitlab-12-dot-1-dot-6-released/){: external}.

## 5 September 2019
{: #ContinuousDelivery-sept0519}
{: release-note}

Develop and test microservices with Kubernetes and Helm template doesn't support API keys that aren't bound to a specific account.
:   When a {{site.data.keyword.deliverypipeline}} stage attempts to run the `ibmcloud login` command, it fails because no account is specified. To work around this limitation, in the {{site.data.keyword.deliverypipeline}} within the Develop and test microservices with Kubernetes and Helm template, create a pipeline property that is called `ACCOUNTID` and add the account that you want to use with the pipeline. In each pipeline stage, add `-c $ACCOUNTID` to each instance of the `ibmcloud login` command.

## 4 September 2019
{: #ContinuousDelivery-sep0419}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 11.10.8](https://about.gitlab.com/2019/07/03/security-release-gitlab-12-dot-0-dot-3-released/){: external}.

## 3 September 2019
{: #ContinuousDelivery-sept0319}
{: release-note}

{{site.data.keyword.deliverypipeline}} events are not translated.
:   Events that are triggered by the {{site.data.keyword.deliverypipeline}} send Slack messages. Since Slack APIs do not support multi-language message payload, these Slack messages cannot be translated.

## 28 August 2019
{: #ContinuousDelivery-aug2819}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 11.9.12](https://about.gitlab.com/2019/06/03/security-release-gitlab-11-dot-11-dot-1-released/){: external}.

## 24 June 2019
{: #ContinuousDelivery-jun2419}
{: release-note}

Stricter enforcement of service plans
:   A toolchain must be linked to a CD service in order for the Delivery Pipeline run.
:   Users of the CD service are automatically added to the list of "Authorized Users."
:   If you are using the Lite plan with more than five authorized users, the pipelines no longer run, pushes to Git Repos are unavailable, and DevOps Insights is unavailable.
:   If you are using the Lite plan, after 500 Delivery Pipeline jobs are run during a month, pipelines do not run, pushes to Git Repos are unavailable, and DevOps Insights is unavailable for the remainder of that billing period.

    Read the [announcement](https://www.ibm.com/cloud/blog/announcements/usage-and-billing-in-ibm-cloud-continuous-delivery){: external}.
