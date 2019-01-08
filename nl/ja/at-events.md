---

copyright:
  years: 2018
lastupdated: "2018-10-10"

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

# {{site.data.keyword.cloudaccesstrailshort}} イベント
{: #at_events}

ユーザーおよびアプリケーションが {{site.data.keyword.Bluemix}} 内の {{site.data.keyword.contdelivery_short}} サービスとどのように対話するのかを {{site.data.keyword.cloudaccesstrailfull}} サービスを使用してトラッキングします。 
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} サービスは、{{site.data.keyword.Bluemix_notm}} 内のサービスの状態を変更するユーザー開始アクティビティーを記録します。 詳細については、[{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla) を参照してください。

<!-- You can create different sections to group events by area. -->

## イベント・リスト
{: #events}

以下の表では、イベントを生成するアクションをリストします。

| アクション | 説明 | 
|:-----------------|:-----------------|
| continuous-delivery.toolchain.create | ツールチェーンを作成します | 
| continuous-delivery.toolchain.delete | ツールチェーンを削除します |
| toolchain.tool-instance.deploy | ツール統合を作成します |
| toolchain.tool-instance.undeploy | ツール統合を削除します |
{: caption="表 1. イベントを生成するアクション" caption-side="top"}

## イベントの表示先
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}} イベントは、イベントが生成される {{site.data.keyword.Bluemix_notm}} 地域内にある {{site.data.keyword.cloudaccesstrailshort}} **アカウント・ドメイン**で使用可能です。
