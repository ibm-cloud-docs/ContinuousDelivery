---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-29"

keywords: Activity Tracker events, tool-instance, List of events

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

<!-- Name your file `at-events.md` and include it in the Reference nav group in your toc file. -->

# {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #at_events}

使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来跟踪用户和应用程序如何与 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.contdelivery_short}} 服务交互。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务记录 {{site.data.keyword.Bluemix_notm}} 中更改服务状态的用户启动的活动。有关更多信息，请参阅[{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)。


<!-- You can create different sections to group events by area. -->

## 事件列表
{: #events}

下表列出了生成事件的操作：

|操作|描述| 
|:-----------------|:-----------------|
| continuous-delivery.toolchain.create |创建工具链| 
| continuous-delivery.toolchain.delete |删除工具链|
| toolchain.tool-instance.deploy |创建工具集成|
| toolchain.tool-instance.undeploy |删除工具集成|
{: caption="表 1. 生成事件的操作" caption-side="top"}

## 查看事件的位置
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} 事件在生成事件的 {{site.data.keyword.Bluemix_notm}} 区域的 {{site.data.keyword.cloudaccesstrailshort}} **帐户域**中可用。
