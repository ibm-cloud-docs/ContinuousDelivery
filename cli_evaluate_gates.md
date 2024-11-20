---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, evaluating gates, cli, test, tests, gate, gate failing, app

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
{: #evaluate-gates-cli}

{{site.data.keyword.DRA_full}} gates check whether your test results comply with a defined policy. If the policy is not met, the gate fails by default. You can also configure gates to act in an advisory role to allow pipeline progression even after failure.
{: shortdesc}


## Before you begin
{: #prereqs-gates-cli}

* [Publish your test results](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-cli).
* [Create a policy with rules](/docs/ContinuousDelivery?topic=ContinuousDelivery-gate-ensure-quality#defining-policies-rules).


## Defining gates for {{site.data.keyword.contdelivery_short}}
{: #gates-cd-cli}

Place your gates before the build promotion in your pipeline to check the quality of the build against your policies. Policies ensure that it is safe to promote your application from one environment to the next.

After you create the policy, you can use the following script for gate evaluation:

```text
#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Login to IBMCloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
ibmcloud login --apikey $API_KEY --no-region

# The following line assumes that MY_APP_NAME and MY_BUILD_NUMBER environment variables have already been set.  POLICY is the name of the policy being evaluated.
ibmcloud doi gate-evaluate --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --policy "$POLICY_NAME"
```
{: codeblock}


## Viewing gate evaluation
{: #view-gate-cli}

You can view the results of the gate evaluation on the Risk Analysis page, which relies on the presence of a gate after a staging deployment job in your pipeline. Make sure that you have a gate after you deploy to the staging environment, but before you deploy to a production environment. 

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Resource list**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Risk Analysis** in the navigation.  

For more information about the Risk Analysis page, see [Your deployment environments](/docs/ContinuousDelivery?topic=ContinuousDelivery-deployment-environment).
