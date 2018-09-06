---

copyright:
  years: 2018
lastupdated: "2018-6-22"

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

使用 {{site.data.keyword.cloudaccesstrailfull}} 服務，以追蹤使用者及應用程式如何與 {{site.data.keyword.Bluemix}} 中的 {{site.data.keyword.contdelivery_short}} 服務互動。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者起始並且會變更 {{site.data.keyword.Bluemix_notm}} 中服務狀態的活動。如需相關資訊，請參閱 [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla)。

<!-- You can create different sections to group events by area. -->

## 事件清單
{: #events}

下表列出可產生事件的動作：

| 動作 |說明| 
|:-----------------|:-----------------|
| 工具鏈建立 | 建立工具鏈 | 
| 工具鏈刪除 | 刪除工具鏈 |
| 工具建立 | 建立工具整合 |
| 工具刪除 | 刪除工具整合 |
{: caption="表 1. 可產生事件的動作" caption-side="top"}

## 事件的檢視位置
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} 事件位於 {{site.data.keyword.cloudaccesstrailshort}} **帳戶網域**中，而帳戶網域位於產生事件的 {{site.data.keyword.Bluemix_notm}} 地區中。
