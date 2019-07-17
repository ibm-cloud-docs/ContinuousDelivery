---



copyright:
  years: 2015，2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

Node.js アプリケーションを作成する場合、{{site.data.keyword.Bluemix}} Live Sync を使用すると、{{site.data.keyword.Bluemix_notm}} 上のアプリケーション・インスタンスを素早く更新して開発することができ、手動で再デプロイする必要がありません。   
{: shortdesc}

変更を行うと、実行中の {{site.data.keyword.Bluemix_notm}} アプリケーションでその変更を即時に確認できます。 {{site.data.keyword.Bluemix_notm}} Live Sync は、
<!--from both the command line and --> Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}) で動作します。 

##Live Edit
{: #live-edit}

{{site.data.keyword.Bluemix_notm}} 上で実行される Node.js アプリケーションを編集し、ご使用のブラウザーですぐにテストすることができます。 {{site.data.keyword.webide}} 内で加えた変更はすべて、直ちに当該アプリケーションのファイル・システムに伝搬されます。

{{site.data.keyword.Bluemix_notm}} 上で実行する Node.js アプリケーションを作成する場合、{{site.data.keyword.Bluemix_notm}} Live Sync の Live Edit フィーチャーを使用することにより、アプリケーション・インスタンスを素早く更新できます。 Live Edit は {{site.data.keyword.webide}} 内でのみ使用できます。Live Edit を使用して、再デプロイせずにデスクトップ版と同様の開発を行うことができます。

Live Edit がサポートされるのは Node.js アプリケーションのみです。
{: important}

{{site.data.keyword.webide}} の実行バーで、**「Live Edit」**をクリックします。

![実行バーに表示された Live Edit のイメージ](images/cloud-live-sync-light.png)

Live Edit を使用すれば、{{site.data.keyword.Bluemix_notm}} で実行される Node.js アプリケーションに対する変更を迅速にプレビューできます。 Live Edit をオンにしてコードを更新すると、変更を加えてからほんの数秒で、Web アプリケーションのブラウザー・ウィンドウを最新表示して、変更が反映されたことを確認できます。

{{site.data.keyword.Bluemix_notm}} Live Sync の Live Edit フィーチャーの使用に関するチュートリアルについては、[Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop and deploy your app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external} を参照してください。

{{site.data.keyword.webide}} 内でファイルを変更すると、それらのファイルは {{site.data.keyword.Bluemix_notm}} 上のアプリケーション・インスタンスに自動的に再デプロイされます。Node アプリケーションの再始動が必要な場合は、実行バーにある**「再始動」**ボタンをクリックします。

{{site.data.keyword.Bluemix_notm}} Live Sync の Live Edit フィーチャーの使用時に、より一貫性のある動作をさせるためには、256 MB の追加メモリーが必要であり、メモリーが追加されます。
{: tip}
