---

copyright:
  years: 2021
lastupdated: "2021-06-25"

keywords: DevSecOps, architecture, compliance, secure, CI, CD

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

# DevSecOps architecture
{: #cd-devsecops-arch}

The {{site.data.keyword.contdelivery_notm}} DevSecOps reference architecture can help to streamline compliance and audit-readiness. Through the standardization of CI/CD processes, application development teams can be sure that they are following security best practices. It provides a set of predefined CI and CD toolchain templates that use a collection of tool integrations and customizable reference Tekton pipelines for build, scan, test, change management, and deploy.
{: shortdesc}


The Tekton pipelines provide a framework of custom scripts that can be used to ensure the compliant, automated orchestration of code and configuration changes. Additionally, the pipelines can help to maintain a GitOps release inventory, while it collects and stores evidence that can be used to generate auditable change requests.

The pipelines can be used to deploy to public cloud, or hybrid target environments by leveraging Tekton private pipeline workers. The Tekton pipelines run in predefined container images along with some user scripts. Anything that can be scripted, can be run within boundaries of the Tekton pipelines.

## Shift-Left CI/CD design
{: #cd-devsecops-design}


Check out the following diagram to learn more about the implementation workflow.

![Reference implementation workflow](images/cm-arch.png "Reference implementation workflow"){: caption="Figure 1. Reference implementation workflow" caption-side="bottom"}

### Main features
{: #cd-devsecops-features}

* Pull or merge request validation uses a specific pull request (PR) pipeline, echoing status back into the pull request. This allows developers to catch problems early in the development cycle.
* Integration is achieved by using a continuous integration (CI) pipeline that implements many controls out of the box and collects normalized evidence for these in an evidence repository. It also writes metadata on the artifacts to be deployed into an artifacts inventory repo, which enables GitOps practices.
* Delivery is performed by using a continuous delivery (CD) pipeline to process content from the artifacts inventory and collect evidence to generate a change request for each deployment. It can also record compliance facts in the {{site.data.keyword.compliance_short}} and these can be assessed against a compliance profile. 

### Notes
{: #cd-devsecops-notes}

* As part of a CD staging deployment, typically CI pipelines emit to the inventory master branch by using pull requests to promote the changes to a staging branch. Then, when ready, the changes can be promoted again from staging to production with a subsequent branch promotion. 
* You can have multiple CI pipelines that output to a shared inventory and evidence repo, to drive a coordinated release deployment. Note: only one change request is created when multiple artifacts in that inventory are promoted.
* You can have multiple CD pipelines that pull from a shared inventory and evidence repo, which enables multiple environments to be targeted from the same CI input.

## Reusable assets
{: #cd-devsecops-reusable-assets}

The DevSecOps reference implementation is composed of the following building blocks:

* CLI: A command-line interface to help manage evidence collection, change requests, and inventory updates. 
* Script library: A library of useful scripts that drive compliance checks. 
* Tekton task library: Reusable Tekton tasks that can be aggregated into custom pipelines. These tasks are in particular used by the reference pipelines.
* Toolchain template for Continuous Integration with Tekton: Template for quickly provisioning a complete CI solution by using Tekton pipelines and integrating with multiple various tools, such as Git repos, secrets storage, image registry, code scans, object storage, and so on.
* Toolchain template for Continuous Delivery with Tekton: Template for quickly provisioning a complete CD solution by using Tekton pipelines and integrating with multiple various tools and integrating with the [{{site.data.keyword.compliance_full}}](https://www.ibm.com/cloud/security-and-compliance-center){: external}. For example, the tools might include Git repos, secrets storage, image registry, change management system, and so on.

## Learning resources
{: #cd-devsecops-learning-resources}

There a number of useful enablement resources available to help you evaluate and adopt the CI/CD templates. You might choose to start with the [Deploy a secure app with DevSecOps best practices](/docs/ContinuousDelivery?topic=ContinuousDelivery-tutorial-cd-devsecops) tutorial, which takes you through various common CI/CD paths.

Other useful learning aids are available here:

* [Getting started with {{site.data.keyword.contdelivery_full}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started)
* [Installing {{site.data.keyword.deliverypipeline}} private workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers)
* [Working with Tekton pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines)
* [Getting started with the {{site.data.keyword.cloud}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started)
* [Continuous Deployment to Kubernetes](/docs/solution-tutorials?topic=solution-tutorials-continuous-deployment-to-kubernetes)
* [Getting started with {{site.data.keyword.containerlong}}](/docs/containers?topic=containers-getting-started)
* [Toolchain availability, templates, and tutorials](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about)

