---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-15"

keywords: devops insights, gates, idra, test, tests, gate, gate failing, app

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Evaluating gates (deprecated)
{: #evaluating-gates-idra}

You can evaluate gates by using idra (deprecated) to integrate your {{site.data.keyword.deliverypipeline}} with {{site.data.keyword.DRA_full}}. {{site.data.keyword.DRA_short}} gates check whether your test results comply with a defined policy. If the policy is not met, the {{site.data.keyword.DRA_short}} gate fails by default. You can also configure gates to act in an advisory role to allow pipeline progression even after failure.
{: shortdesc}


## Before you begin
{: #prereqs-gates-idra}

* Publish your test results. For more information, see [Publishing test results by using idra (deprecated)](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-idra).
* Create a policy with rules. For more information, see [Defining policies and rules](/docs/ContinuousDelivery?topic=ContinuousDelivery-gate-ensure-quality#defining-policies-rules).


## Defining gates (deprecated)
{: #gates-cd-idra}

Place gates before build promotion to ensure that it's safe to promote from one environment to another.

After you create the policy, you can use the following script for gate evaluation:

```text
# Add user api key to stage environment variable as a secured property
export LOGICAL_APP_NAME="SampleApp"
export BUILD_PREFIX="master"

# Evaluate DevOps Insights gate
# node 4.x or above is needed
export PATH=/opt/IBM/node-v4.2/bin:$PATH
npm install -g grunt-idra3

idra --evaluategate --policy="$POLICY_NAME"
```
{: codeblock}


## Viewing gate evaluation
{: #view-gate-idra}

You can view the results of the gate evaluation on the Risk Analysis page in {{site.data.keyword.DRA_short}}. The Risk Analysis page relies on the presence of a gate after a staging deployment job in your pipeline. Make sure that you have a gate after you deploy to the staging environment, but before you deploy to a production environment. For more information about the Risk Analysis page, see [Your deployment environments](/docs/ContinuousDelivery?topic=ContinuousDelivery-deployment-environment).
