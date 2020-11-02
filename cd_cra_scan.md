---

copyright:
  years: 2020
lastupdated: "2020-11-02"

keywords: Code Risk Analyzer, code repositories, DevOps Insights, scan pull requests, Tekton pipelines

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

# Scanning pull requests
{: #cd-cra-scan-pr}

After you configure Code Risk Analyzer for your code repositories (repos), you can create and scan pull requests. The Code Risk Analyzer starts the following process when you create a pull request for your repo:

1. The Code Risk Analyzer pipeline that you previously configured runs automatically.
1. The pipeline discovers your code repo dependencies, such as application packages, container images, or operating system packages.
1. The pipeline identifies any vulnerabilities that are associated with these dependencies and posts a comment in your pull request. If too many vulnerabilities are found, the pull request comment might display only a subset of the vulnerabilities.
1. The pipeline scans Dockerfiles and Kubernetes yaml files for best practices, and then posts a comment in your pull request.
1. The pipeline adds a link to the Bill of Materials file in your pull request.
