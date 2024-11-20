---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-24"

keywords: devops insights, evaluating gates, other ci/cd tools, test, tests, gate, gate failing, app, risk

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Evaluating gates
{: #evaluate-gates-cicd}

You can evaluate gates by using other continuous integration and continuous delivery (CI/CD) tools with the {{site.data.keyword.Bluemix}} command line interface (CLI) to integrate with {{site.data.keyword.DRA_full}}. {{site.data.keyword.DRA_short}} gates check whether your test results comply with a defined policy. If the policy is not met, the {{site.data.keyword.DRA_short}} gate fails by default. You can also configure gates to act in an advisory role to allow CI/CD tool progression even after failure.
{: shortdesc}


## Before you begin
{: #prereqs-gates-cicd}

* Publish test records. For more information, see [Publishing test results by using other CI/CD tools](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-cicd).
* Create a policy with rules. For more information, see [Defining policies and rules](/docs/ContinuousDelivery?topic=ContinuousDelivery-gate-ensure-quality#defining-policies-rules).


## Defining gates for other CI/CD tools
{: #gates-cicd}

Place gates before build promotion in your CI/CD tool to check the quality of the build against your policies to ensure that it's safe to promote from one environment to another. Use the `gate-evaluate` command to perform the gate check. 

After you create the policy, you can use the following script for gate evaluation:

```text

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Log in to IBM Cloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set
ibmcloud login --apikey $API_KEY --no-region

# The following line assumes that MY_APP_NAME and MY_BUILD_NUMBER environment variables have already been set.  POLICY is the name of the policy being evaluated.
ibmcloud doi gate-evaluate --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --policy POLICY
```
{: codeblock}


## Viewing gate evaluation
{: #view-gate-cicd}

You can view the results of the gate evaluation on the Risk Analysis page in {{site.data.keyword.DRA_short}}. The Risk Analysis page relies on the presence of a gate after a staging deployment job. Make sure that you have a gate after you deploy to the staging environment, but before you deploy to a production environment. For more information about the Risk Analysis page, see [Your deployment environments](/docs/ContinuousDelivery?topic=ContinuousDelivery-deployment-environment).
