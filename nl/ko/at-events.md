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

# {{site.data.keyword.cloudaccesstrailshort}} 이벤트
{: #at_events}

{{site.data.keyword.cloudaccesstrailfull}} 서비스를 사용하여 사용자 및 애플리케이션이 {{site.data.keyword.Bluemix}}에서 {{site.data.keyword.contdelivery_short}} 서비스와 상호작용하는 방식을 추적하십시오. 
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 서비스는 {{site.data.keyword.Bluemix_notm}}에서 서비스 상태를 변경하는 사용자 시작 활동을 기록합니다. 자세한 정보는 [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)의 내용을 참조하십시오.

<!-- You can create different sections to group events by area. -->

## 이벤트 목록
{: #events}

다음 표에는 이벤트를 생성하는 조치가 나열되어 있습니다.

| 조치 |설명 | 
|:-----------------|:-----------------|
| continuous-delivery.toolchain.create | 도구 체인 작성 | 
| continuous-delivery.toolchain.delete | 도구 체인 삭제 |
| toolchain.tool-instance.deploy | 도구 통합 작성 |
| toolchain.tool-instance.undeploy | 도구 통합 삭제 |
{: caption="표 1. 이벤트를 생성하는 조치" caption-side="top"}

## 이벤트 표시 위치
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} 이벤트는 이벤트가 생성되는 {{site.data.keyword.Bluemix_notm}} 지역에서 사용 가능한 {{site.data.keyword.cloudaccesstrailshort}} **계정 도메인**에서 사용할 수 있습니다.
