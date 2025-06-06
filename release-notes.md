---

copyright:
  years: 2019, 2025

lastupdated: "2025-06-06"

keywords: IBM Cloud Continuous Delivery, release notes, CD

subcollection: ContinuousDelivery

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for {{site.data.keyword.contdelivery_short}}
{: #cd-relnotes}

Use these release notes to learn about the latest updates to {{site.data.keyword.contdelivery_full}} that are grouped by date. Release notes are available for a minimum of three years.
{: shortdesc}

## 29 April 2025
{: #ContinuousDelivery-apr2925}
{: release-note}

Private worker installation no longer supports the Operator Lifecycle Manager (OLM) framework.

## 25 September 2024
{: #ContinuousDelivery-sep2524}
{: release-note}

The {{site.data.keyword.contdelivery_short}} toolchain API method for generating bespoke toolchain events to {{site.data.keyword.en_short}}, [POST /toolchains/:toolchain_id/events](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event), is now generally available.
:  The `text_plain` property of the request payload is changed from a string to a JSON object of the form `{“content”: “string”}`. The API is otherwise unchanged from the Beta.
:  For more information, see [Enabling event notifications for toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd) and the [CD Toolchain API Docs](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external}.

## 19 August 2024
{: #ContinuousDelivery-august2424}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 17.1.4](https://about.gitlab.com/releases/2024/08/07/patch-release-gitlab-17-2-2-released/){: external}.

## 06 September 2024
{: #ContinuousDelivery-sep0624}
{: release-note}

Enabling Direct Integration with an Existing Git Repository
:   Link a Continuous Delivery service and toolchain instance to a Git project for seamless integration, automating code deployment, and real-time collaboration. It is **mandatory** to link Continuous Delivery service and toolchain instance for creating a new project in the UI.

:   For more information, see [Link a Continuous Delivery service instance to a Git Project](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage&interface=ui#git_projects).




## 09 July 2024
{: #ContinuousDelivery-09july2424}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 17.0.3](https://about.gitlab.com/releases/2024/06/26/patch-release-gitlab-17-1-1-released/){: external}.

## 01 July 2024
{: #ContinuousDelivery-01july2424}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.11.5](https://about.gitlab.com/releases/2024/06/26/patch-release-gitlab-17-1-1-released/){: external}.

## 24 June 2024
{: #ContinuousDelivery-june2424}
{: release-note}

The {{site.data.keyword.contdelivery_short}} service Professional plan now supports consolidated billing of authorized users within enterprise account hierarchies. This feature ensures that authorized user emails are counted and billed only once across all {{site.data.keyword.contdelivery_short}} service instances in your enterprise and in a region, rather than being counted and billed separately for each instance.
:   For more information, see [Consolidated billing](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#consolidated_billing).


{{site.data.keyword.deliverypipeline}}
:   Upgraded to [Tekton Pipelines v0.59.2](https://github.com/tektoncd/pipeline/releases/tag/v0.59.2){: external}.

## 15 February 2024
{: #ContinuousDelivery-feb1524}
{: release-note}

{{site.data.keyword.deliverypipeline}}
The toolchain service can now be selected as a service reference when creating network zones under [Context-based restrictions](/docs/account?topic=account-context-restrictions-whatis).

## 2 January 2024
{: #ContinuousDelivery-jan0224}
{: release-note}

The {{site.data.keyword.contdelivery_short}} toolchain API provides a new, beta method that you can use to generate bespoke (custom) toolchain events which the toolchain will forward to integrated instances of {{site.data.keyword.en_short}}.
:   For more information, see [Enabling event notifications for toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd) and the [CD Toolchain API Docs](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external}.

## 7 December 2023
{: #ContinuousDelivery-dec0723}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.5.3](https://about.gitlab.com/releases/2023/11/30/security-release-gitlab-16-6-1-released/){: external}.

## 24 November 2023
{: #ContinuousDelivery-nov2423}
{: release-note}

{{site.data.keyword.contdelivery_full}} is now available in the Madrid region.
:   Each location has three different data centers and provides a full cloud service stack to enable high availability, redundancy, and geographical dispersion.

## 16 November 2023
{: #ContinuousDelivery-nov1623}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.4.2](https://about.gitlab.com/releases/2023/10/31/security-release-gitlab-16-5-1-16-4-2-16-3-6-released/){: external}.

## 3 November 2023
{: #ContinuousDelivery-nov0323}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.3.5](https://about.gitlab.com/releases/2023/09/28/security-release-gitlab-16-4-1-released/){: external}.

## 19 October 2023
{: #ContinuousDelivery-otc1923}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.2.8](https://about.gitlab.com/releases/2023/09/28/security-release-gitlab-16-4-1-released/){: external}.

## 4 October 2023
{: #ContinuousDelivery-otc0423}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.1.5](https://about.gitlab.com/releases/2023/08/31/security-release-gitlab-16-3-1-released/){: external}.

## 27 September 2023
{: #ContinuousDelivery-sep2723}
{: release-note}

{{site.data.keyword.contdelivery_short}} toolchains APIs, SDKs, and Terraform now support looking up toolchains by name.
:   For more information, see the [CD Toolchain API Docs](https://cloud.ibm.com/apidocs/toolchain#list-toolchains-request){: external} and the [Terraform IBM Cloud provider docs](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/data-sources/cd_toolchains){: external}.

## 11 September 2023
{: #ContinuousDelivery-sep1123}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 16.0.8](https://about.gitlab.com/releases/2023/08/01/security-release-gitlab-16-2-2-released/){: external}.

:   In GitLab 16.0, any personal, project, or [group access token that does not have an expiration date](https://docs.gitlab.com/ee/update/deprecations.html#non-expiring-access-tokens){: external} will automatically have an expiration date set at one year.

## 12 July 2023
{: #ContinuousDelivery-july1223}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.11.11](https://about.gitlab.com/releases/2023/07/05/security-release-gitlab-16-1-2-released/){: external}.

## 13 June 2023
{: #ContinuousDelivery-june1323}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.10.8](https://about.gitlab.com/releases/2023/06/05/security-release-gitlab-16-0-2-released/){: external}.

## 19 May 2023
{: #ContinuousDelivery-may1923}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.9.8](https://about.gitlab.com/releases/2023/05/10/security-release-gitlab-15-11-3-released/){: external}.

## 20 April 2023
{: #ContinuousDelivery-apr2023}
{: release-note}

{{site.data.keyword.contdelivery_short}} toolchains are now integrated with the {{site.data.keyword.en_full}} service.
:   [Enabling {{site.data.keyword.en_short}} for toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd)

## 10 April 2023
{: #ContinuousDelivery-apr1023}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.8.5](https://about.gitlab.com/releases/2023/03/30/security-release-gitlab-15-10-1-released/){: external}.

## 21 February 2023
{: #ContinuousDelivery-feb2123}
{: release-note}

Java, Node, and Python SDKs for toolchains and Tekton pipelines are now generally available.
:   Java SDK: [github.com/IBM/continuous-delivery-java-sdk](https://github.com/IBM/continuous-delivery-java-sdk){: external}

:   Node SDK: [github.com/IBM/continuous-delivery-node-sdk](https://github.com/IBM/continuous-delivery-node-sdk){: external}

:   Python SDK: [github.com/IBM/continuous-delivery-python-sdk](https://github.com/IBM/continuous-delivery-python-sdk){: external}

## 13 February 2023
{: #ContinuousDelivery-feb1323}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.7.6](https://about.gitlab.com/releases/2023/01/31/security-release-gitlab-15-8-1-released/){: external}.

## 19 January 2023
{: #ContinuousDelivery-jan1923}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.6.6](https://about.gitlab.com/releases/2023/01/17/critical-security-release-gitlab-15-7-5-released/){: external}.

## 9 January 2023
{: #ContinuousDelivery-jan0923}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.6.3](https://about.gitlab.com/releases/2022/12/16/gitlab-15-6-3-released/){: external}.

## 14 December 2022
{: #ContinuousDelivery-dec1422}
{: release-note}

The {{site.data.keyword.contdelivery_short}} service is now designated as {{site.data.keyword.cloud_notm}} for Financial Services Validated.
:   This designation does not apply to all of the tools that you can integrate into toolchains. For more information about which tool integrations and tools are designated as {{site.data.keyword.cloud_notm}} for Financial Services Validated when they are used with {{site.data.keyword.contdelivery_short}} toolchains, see [Understanding tool integrations with {{site.data.keyword.cloud_notm}} for Financial Services](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).

:   For more information about {{site.data.keyword.cloud_notm}} for Financial Services, see [{{site.data.keyword.cloud_notm}} Framework for Financial Services](/docs/framework-financial-services).

## 7 December 2022
{: #ContinuousDelivery-dec0722}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.5.5](https://about.gitlab.com/releases/2022/11/30/security-release-gitlab-15-6-1-released/){: external}.

## 1 December 2022
{: #ContinuousDelivery-dec0122}
{: release-note}

The Terraform resources and data sources, Go SDKs, and HTTP APIs for toolchains and Tekton pipelines are now generally available.
:   Updates include a few breaking changes.

:   The Terraform resources and data sources, Go SDKs, and HTTP APIs are now a generally available, fully supported feature.

:   Read the [release notes](https://github.com/IBM/continuous-delivery-go-sdk/blob/main/RELEASE_NOTES.md){: external}.

## 18 November 2022
{: #ContinuousDelivery-nov1822}
{: release-note}

The Beta Terraform resources and data sources, Go SDKs, and HTTP APIs are updated, including several breaking changes.

:   Read the [release notes](https://github.com/IBM/continuous-delivery-go-sdk/blob/main/RELEASE_NOTES.md){: external}.

## 16 November 2022
{: #ContinuousDelivery-nov1622}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.4.4](https://about.gitlab.com/releases/2022/11/02/security-release-gitlab-15-5-2-released/){: external}.

## 2 November 2022
{: #ContinuousDelivery-nov0222}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.3.4](https://about.gitlab.com/releases/2022/09/29/security-release-gitlab-15-4-1-released/){: external}.

## 6 October 2022
{: #ContinuousDelivery-oct0622}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 15.2.5](https://about.gitlab.com/releases/2022/09/29/security-release-gitlab-15-4-1-released/){: external}.

## 5 October 2022
{: #ContinuousDelivery-oct0522}
{: release-note}

The Beta Terraform resources and data sources, Go SDKs, and HTTP APIs are updated, including several breaking changes.

:   Read the [release notes](https://github.com/IBM/continuous-delivery-go-sdk/blob/main/RELEASE_NOTES.md#012-2022-09-09-beta){: external} .

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
:   [Using {{site.data.keyword.deliverypipeline}} Private Workers in stand-alone mode](/docs/ContinuousDelivery?topic=ContinuousDelivery-external-properties).

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
{: #ContinuousDelivery-june0722}
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

    Read the [announcement](https://www.ibm.com/blog/announcement/whats-new-with-devsecops-in-ibm-cloud/){: external}.

## 7 October 2021
{: #ContinuousDelivery-oct0721}
{: release-note}

New toolchain templates demonstrate release strategies
:   Rolling: Deploy a new release with no downtime by incrementally updating all the instances in a sequential manner.
:   Blue-Green: Deploy a new release to an environment identical to — and isolated from — current production for quicker rollbacks and ease of testing.
:   Canary: Deploy a new release incrementally to the production environment, gradually replacing the older version of the application with the newer one, gating increments with a test to reducing risks.

    Read the [announcement](https://www.ibm.com/blog/explore-deployment-strategies-with-ibm-cloud-continuous-delivery/){: external}.

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

    Read the [announcement](https://www.ibm.com/blog/announcement/devsecops-reference-implementation-for-audit-ready-compliance-across-development-teams/){: external}.

## 24 May 2021
{: #ContinuousDelivery-may2421}
{: release-note}

Code Risk Analyzer now scans Terraform
:   Misconfiguration of infrastructure and cloud service dependencies can put enterprise applications and data at risk. Now, Code Risk Analyzer looks for these issues by scanning Terraform Infrastructure as Code (IaC) files.

    Read the [announcement](https://www.ibm.com/blog/announcement/code-risk-analyzer-adds-terraform-scanning/){: external}.

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
:   Upgraded to [GitLab 12.2.7](https://about.gitlab.com/releases/2019/10/02/security-release-gitlab-12-dot-3-dot-3-released/){: external}.

## 10 October 2019
{: #ContinuousDelivery-oct1019}
{: release-note}

{{site.data.keyword.deliverypipeline}} now has Tekton option.
:   Tekton Pipelines is an open source project that you can use to configure and run continuous integration/continuous delivery (CI/CD) pipelines within a Kubernetes cluster. Pipelines are defined as Tekton resources in YAML, typically stored in a Git repository.
:   Read the [announcement](https://www.ibm.com/blog/announcement/build-and-deliver-using-tekton-enabled-pipelines/){: external}.

## 2 October 2019
{: #ContinuousDelivery-oct0219}
{: release-note}

New DevOps tab in your IBM Cloud Kubernetes Service cluster details.
:   Find all toolchains whose delivery pipelines deployed to that cluster
:   Easily create a new DevOps toolchain
:   Read the [announcement](https://www.ibm.com/blog/announcement/connecting-ibm-cloud-kubernetes-service-and-ibm-continuous-delivery/){: external}.

## 1 October 2019
{: #ContinuousDelivery-oct0119}
{: release-note}

DevOps Insights
:   DevOps Insights features are now part of Continuous Delivery.

## 20 September 2019
{: #ContinuousDelivery-sep2019}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 12.1.9](https://about.gitlab.com/releases/2019/09/10/critical-security-release-gitlab-12-dot-2-dot-5-released/){: external}.

## 16 September 2019
{: #ContinuousDelivery-sep1619}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 12.0.8](https://about.gitlab.com/releases/2019/08/29/security-release-gitlab-12-dot-2-dot-3-released/){: external}.

## 9 September 2019
{: #ContinuousDelivery-sep0919}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 11.11.8](https://about.gitlab.com/releases/2019/08/12/critical-security-release-gitlab-12-dot-1-dot-6-released/){: external}.

## 5 September 2019
{: #ContinuousDelivery-sept0519}
{: release-note}

Develop and test microservices with Kubernetes and Helm template doesn't support API keys that aren't bound to a specific account.
:   When a {{site.data.keyword.deliverypipeline}} stage attempts to run the `ibmcloud login` command, it fails because no account is specified. To work around this limitation, in the {{site.data.keyword.deliverypipeline}} within the Develop and test microservices with Kubernetes and Helm template, create a pipeline property that is called `ACCOUNTID` and add the account that you want to use with the pipeline. In each pipeline stage, add `-c $ACCOUNTID` to each instance of the `ibmcloud login` command.

## 4 September 2019
{: #ContinuousDelivery-sep0419}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 11.10.8](https://about.gitlab.com/releases/2019/07/03/security-release-gitlab-12-dot-0-dot-3-released/){: external}.

## 3 September 2019
{: #ContinuousDelivery-sept0319}
{: release-note}

{{site.data.keyword.deliverypipeline}} events are not translated.
:   Events that are triggered by the {{site.data.keyword.deliverypipeline}} send Slack messages. Since Slack APIs do not support multi-language message payload, these Slack messages cannot be translated.

## 28 August 2019
{: #ContinuousDelivery-aug2819}
{: release-note}

{{site.data.keyword.gitrepos}}
:   Upgraded to [GitLab 11.9.12](https://about.gitlab.com/releases/2019/06/03/security-release-gitlab-11-dot-11-dot-1-released/){: external}.

## 24 June 2019
{: #ContinuousDelivery-jun2419}
{: release-note}

Stricter enforcement of service plans
:   A toolchain must be linked to a CD service in order for the Delivery Pipeline run.
:   Users of the CD service are automatically added to the list of "Authorized Users."
:   If you are using the Lite plan with more than five authorized users, the pipelines no longer run, pushes to Git Repos are unavailable, and DevOps Insights is unavailable.
:   If you are using the Lite plan, after 500 Delivery Pipeline jobs are run during a month, pipelines do not run, pushes to Git Repos are unavailable, and DevOps Insights is unavailable for the remainder of that billing period.

    Read the [announcement](https://www.ibm.com/blog/announcement/usage-and-billing-in-ibm-cloud-continuous-delivery/){: external}.
