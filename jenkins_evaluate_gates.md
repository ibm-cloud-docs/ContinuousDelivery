---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-15"

keywords: devops insights, communicate, toolchain, pipeline, jenkins, test, tests, gate, gate failing, app

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Evaluating gates 
{: #evaluate-gates-jenkins}

You can evaluate gates by using Jenkins to integrate your project with {{site.data.keyword.DRA_full}}. {{site.data.keyword.DRA_short}} gates check whether your test results comply with a defined policy. If the policy is not met, the {{site.data.keyword.DRA_short}} gate fails by default. You can also configure gates to act in an advisory role to allow pipeline progression even after failure.
{: shortdesc}


## Before you begin
{: #prereqs-gates-jenkins}

* Before you evaluate a gate policy on an application build, you must publish test records. For more information, see [Publishing test results by using Jenkins](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-jenkins).
* Create a policy with rules. For more information, see [Defining policies and rules](/docs/ContinuousDelivery?topic=ContinuousDelivery-defining-policies-rules).


## Defining gates 
{: #gates-jenkins}

Add gates to your pipeline by using the **`evaluateGate`** command. Gates enforce {{site.data.keyword.DRA_short}} policies, which set test requirements for build promotion. 

This step requires one parameter. It can also accept two of the three optional parameters. The follow is a list of parameters and their definitions.

| Parameter         | Definition                                                                                                                   |
|-------------------|------------------------------------------------------------------------------------------------------------------------------|
| `policy`          | The name of the policy that the gate implements. The policy's name is defined in {{site.data.keyword.DRA_short}}.            |
| `forceDecision`   | Optional: Set this parameter to `true` to stop the pipeline if the gate fails. Set it to `false` to force the pipeline to continue after a gate fails. By default, the value is false. |
| `buildNumber`     | Optional: Set value to any string to represent a version number.                                                             |
| `applicationName` | Optional: Set the application name. When this value is set, the environment variable IBM_CLOUD_DEVOPS_APP_NAME is ignored. |
{: caption="Publishing build records parameters and definitions" caption-side="top"}

The following example command includes the parameters. In this command, the pipeline continues running regardless of the gate's decision.

```text
evaluateGate policy: 'Weather App Policy', forceDecision: 'true'
```
{: codeblock}


## Viewing gate evaluation
{: #view-gate-jenkins}

You can view the results of the gate evaluation on the Risk Analysis page in the {{site.data.keyword.DRA_short}} console. The Risk Analysis page relies on the presence of a gate after a staging deployment job in your pipeline. Make sure that you have a gate after you deploy to the staging environment, but before you deploy to a production environment. For more information about the Risk Analysis page, see [Your deployment environments](/docs/ContinuousDelivery?topic=ContinuousDelivery-deployment-environment).


## Next steps
{: #next-steps-gates}

After you evaluate your gates, [send the pipeline status to {{site.data.keyword.IBM_notm}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-communicating-toolchains-jenkins). 
