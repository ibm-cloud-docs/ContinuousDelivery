---

copyright:
  years: 2021
lastupdated: "2021-09-21"

keywords: deployment strategies, tekton, pipeline, toolchain, CD, CI, automate, automation, continuous delivery, continuous integration, DevOps, shift-left, shift left, secure DevOps, IBM Cloud

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Deployment Strategies:
{: #ds_definition}

A deployment strategy is a way to change or upgrade an application in a production environment in a controlled manner. There are more than one reasons why this topic assumes importance. Some of the most prominent are:

* Avoid a downtime of an application
* Conduct specific tests like a new functionality or for specific users or both, 
* Limit issues in production to a limited users in case there happens to be an issue.
* In case there are any issues found, gain control over rapid rollback to the previous version.

Let's look into the various types of deployment strategies:

## Basic
{: #ds_basic}

Deploy a new release, stopping and updating all running instances at once, thus causing downtime.

For rollback, the old version has to be redeployed.

This strategy is simple, fast and cheap. At the same time it is the riskiest and causes down time. Thus, not recommended for critical applications.

## Rolling Update
{: #ds_rolling_update}

Deploy a new release with no downtime by incrementally updating all its instances in a rapid manner.
Rollback requires redeploying the previous release, which may not be immediate.

## Blue-Green Deployment
{: #ds_bg_deploy}

In this deployment strategy, you can leverage two permanent production environments (blue and green) with only one receiving traffic at any time. Deploy the new release to the idle environment, then switch all traffic to it with no downtime.
For rapid rollback, simply switch all traffic back to the other environment that remained unchanged.

This deployment strategy is fast, easily understood and easy to rollback as we simply flp the traffic to old deployment.

## Canary Release
{: #ds_canary_release}

Deploy a new release in parallel with the original production environment, with no downtime, then incrementally route more traffic to it until it replaces the original one which can be torn down. We can control the amount of traffic and the time interval of the update to the new release.

For rapid rollback during progressive rollout, all traffic can be routed back to the original production environment.

In this approach the risk of introducing any issues to the production is reduced by slowly directing the traffic. This method is also the slowest to transition from old to a new release of the software being deployed. Canary deployments allow organizations to test two different versions of the software side by side in production.

