---

copyright:
  years: 2021
lastupdated: "2021-06-21"

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

# Promoting changes from the master branch
{: #cd-devsecops-promote-master}

Continuous integrtation pipelines update a subset of the inventory entries on the master branch and deploy them Staging.
{: shortdesc}

 1. Promotion creates a promotion pull request from staging to production.
 2. The pull request is  approved and merged.
 3. The continuous delivery pipelines starts and tags the current commit with the Pipeline Run ID.
 4. The pipeline uses that tag to pick up the content from the prod branch and calculates the deployment delta between the current commit and the content of the `latest-prod` tag.
 5. The pipeline attempt to deploy the content. During the deployment, the change request ID is attached to the commit that the pipeline works with as a tag.
 6. A successful deployment concludes by attaching the `latest-prod` tag to the commit you are working with.
