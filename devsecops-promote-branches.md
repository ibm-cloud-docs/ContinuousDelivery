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

# Promoting to target branches
{: #cd-devsecops-promote-branches}

To set up the inventory, you can either partition the repo to target  branches or keep checking and create target branches as  you go.
{: shortdesc}

1. The continuous integration pipelines populate the master branch with inventory entries.
2. Promote content from master to staging. If the staging branch exists, it shares a history with the master branch and creates a promotion pull request to staging. If the staging branch does not exist, you can create it by branching initial commit from master, and then creating a promotion pull request to staging.
3. Approve and merge the pull request. The continuous delivery pipelines starts, tags the current commit with the Pipeline Run ID, and picks up the content of the staging branch from that tag.
4. Because this is the first promotion to the new target, the deployment delta contains all of the items and attempts to deploy them.
5. During the deployment, the change request is attached as a tag to the commit that the pipeline works with. A successful deployment completes by attaching the `latest-staging` tag to the commit that you are working  with.
