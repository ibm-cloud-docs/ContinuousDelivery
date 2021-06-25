---

copyright:
  years: 2021
lastupdated: "2021-06-18"

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

# Setting pull request status
{: #cd-devsecops-set-pr-status}

After you [install the CoCoA CLI on Linux](docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-install-cocoa-cli) to set the status of a commit, you can use the `cocoa set-status` command to set the pull request status.
{: shortdesc}
<!-- This installation guide about the CoCoA CLI maybe will be removed since it's not open-sourced and needs TaaS ? -->

The current implementation is tested on GitHub. For a list of available values, see [GitHub statuses](https://docs.github.com/en/rest/reference/repos#statuses){: external}.
{: tip}

1. Specify the following environment variables:

 ```
GHE_TOKEN=    # Github token
GHE_ORG=      # Github organization/username
GHE_REPO=     # Github repository
GHE_COMMIT=   # Github commit hash
```

1. Running the following command to set the pull request status:

 ```
$ cocoa set-status \
 --state="pending" \
 --targetURL="https://cloud.ibm.com/devops/pipelines/tekton/some-toolchain/runs/some-pipelinerun/lint/lint?env_id=ibm:yp:us-south" \
 --context="tekton/lint" \
 --description="Tekton linter is running."
 ```
