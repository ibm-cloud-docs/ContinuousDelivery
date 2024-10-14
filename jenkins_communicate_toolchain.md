---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-15"


keywords: devops insights, communicate, toolchain, pipeline, jenkins, gate, gate failing, app

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:tip: .tip}
{:codeblock: .codeblock}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Communicating with your toolchains
{: #communicating-toolchains-jenkins}

Communicate with your toolchain so you can automatically see when a pipeline stage passes or fails. You can communicate with your toolchain by sending your pipeline status to {{site.data.keyword.IBM_notm}}. 
{: shortdesc}


## Before you begin
{: #prereqs-communicating-jenkins}

Before you notify your toolchain, you must evaluate a gate policy on an application build. For more information, see [Evaluating gates by using Jenkins](/docs/ContinuousDelivery?topic=ContinuousDelivery-evaluate-gates-jenkins).


## Using `notifyOTC` 
{: #using-notifyOTC}

Send the pipeline status to your toolchain by using the **`notifyOTC`** command. This task requires two parameters, and it can also take an extra optional one. 

| Parameter    | Definition                                                                                                                      |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| `stageName`  | The current pipeline stage's name.                                                                                             |
| `status`     | The current pipeline stage's status. Using `SUCCESS`, `FAILURE`, or `ABORTED` automatically highlights the text in Slack. |
{: caption="Parameters and definitions for communicating with toolchains" caption-side="top"}

The following examples illustrate how to use the notifyOTC step in both declarative and scripted pipeline definitions:

```text
notifyOTC stageName: "Deploy", status: "SUCCESS"
```
{: codeblock}
