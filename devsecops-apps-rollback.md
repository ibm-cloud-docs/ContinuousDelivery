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

# Rolling back apps from production
{: #cd-devsecops-apps-rollback}

When you work with {{site.data.keyword.contdelivery_notm}}, you might need to roll back a deployed app to a previous version on prod because of an issue.
{: shortdesc}

1.  Choose a point in the Inventory to roll back to. All commits are reverted up to this point, and then promoted as a pull request.
2. The Rollback promotion pull request is merged and the continuous delivery pipeline starts.
3. The pipeline picks up the content of the prod branch from that tag, calculates the deployment delta between the current commit and the contents of the `latest-prod` tag, and attempts to deploy.
4. Successful deployment concludes by attaching the `latest-prod` tag to the commit that you work with.
