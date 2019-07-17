---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

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


# {{site.data.keyword.deliverypipeline}} プライベート・ワーカーでの作業
{: #private-workers}

{{site.data.keyword.deliverypipeline}} は、パブリック・ワーカーとプライベート・ワーカーを使用してパイプライン・ジョブを実行します。デフォルトでは、IBM 管理対象のパブリック共有インフラストラクチャー上ではパブリック・ワーカーを使用してパイプライン・ジョブが実行されます。
{: shortdesc}

特定のシナリオでは、{{site.data.keyword.deliverypipeline}} が内部リソースまたはオンプレミス・リソースへのアクセス権を必要とする場合があります。このような状況の場合、{{site.data.keyword.deliverypipeline}} プライベート・ワーカーに接続して統合し、独自の Kubernetes インフラストラクチャー上で実行できます。

## 前提条件
{: #private_workers_prereqs}

プライベート・ワーカーをセットアップする場合、その前に以下のリソースが揃っていることを確認してください。

* Kubernetes クラスター。プライベート・ワーカーをインストールするには、クラスターがなければなりません。独自のクラスターを提供するか、{{site.data.keyword.containerlong_notm}} から[クラスターをセットアップ](https://cloud.ibm.com/kubernetes/clusters){:external}することができます。

* 少なくとも 1 つのステージを含むパイプラインを備えたツールチェーン。既存のツールチェーンを使用するか、[ツールチェーンを作成](https://cloud.ibm.com/devops/create){:external}することができます。

## {{site.data.keyword.deliverypipeline}} プライベート・ワーカーのセットアップ
{: #set_up_private_worker}

プライベート・ワーカーをセットアップするには、以下のステップを実行します。

1. ご使用のツールチェーン用に {{site.data.keyword.deliverypipeline}} Private Worker ツール統合を構成します。
2. プライベート・ワーカーで Kubernetes クラスターを構成します。
3. パイプライン内でプライベート・ワーカーを使用します。

### {{site.data.keyword.deliverypipeline}} Private Worker ツール統合の構成
{: #configure_private_worker_integration}

ご使用のツールチェーン用に {{site.data.keyword.deliverypipeline}} Private Worker ツール統合を構成するには、以下のステップを実行します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「{{site.data.keyword.deliverypipeline}} Private Worker」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「{{site.data.keyword.deliverypipeline}} Private Worker」**をクリックします。

1. ツール統合の名前を入力します。この名前は、パイプライン・ステージの**「ワーカー」**タブで、プライベート・ワーカーのプールを識別します。
1. サービス ID の API キーを入力して、1 つ以上のプライベート・ワーカーが作業を検索できる作業キューへのアクセスを認証します。サービス ID API キーがない場合は、**「作成」** をクリックして、このプライベート・ワーカー用の API キーを生成します。
1. **「統合の作成」**をクリックします。
1. ツールチェーンから**「{{site.data.keyword.deliverypipeline}} Private Worker」**をクリックして、このサービス ID に関連付けられた API キーを使用して登録されたすべてのワーカーのリストを表示します。

**{{site.data.keyword.deliverypipeline}} Private Worker** ツール統合について詳しくは、[{{site.data.keyword.deliverypipeline}} プライベート・ワーカーの構成](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker)を参照してください。

### Kubernetes クラスターの構成
{: #configure_kubernetes_cluster}

以下のように、プライベート・ワーカーで Kubernetes クラスターを構成します。

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. 構成対象の {{site.data.keyword.deliverypipeline}} Private Worker ツール統合のカードをクリックします。
1. **「開始」**をクリックしてから、Kubernetes クラスター上でプライベート・ワーカーをインストールして登録するステップに従います。

### パイプライン内での {{site.data.keyword.deliverypipeline}} プライベート・ワーカーの使用
{: #use_private_worker_pipeline}

パイプライン内でプライベート・ワーカーを使用するには、以下のステップを実行します。

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. プライベート・ワーカーを使用しようとしているパイプラインのカードをクリックします。
1. 「パイプライン」ページ上のステージで、**「ステージ構成」**アイコンをクリックし、**「ステージの構成」**をクリックします。
1. **「ワーカー」**タブをクリックします。
1. パイプライン内で使用しようとしているプライベート・ワーカーを選択します。 

 パイプライン・ステージにおけるジョブはデフォルトで、そのパイプラインが定義されているリージョン内の、IBM 管理対象の共有ワーカーのプールを使用して実行されます。
 {: tip}
 
1. **「保存」**をクリックします。
1. ステージを手動で実行するか、または関連する Kubernetes クラスター上の、指定されたプライベート・ワーカーを使用して、ステージでジョブを実行するトリガーを待機することができます。ジョブのログ・ファイル出力を表示して、使用されたワーカーを判別できます。  


## {{site.data.keyword.deliverypipeline}} Private Worker ツール統合の資格情報の変更
{: #modify_private_worker}

プライベート・ワーカーをセットアップした後に、ツール統合で使用される資格情報を更新できます。これらの資格情報が削除されたり、期限が切れたり、暗号漏えいしたりする場合には、変更することもできます。新しいサービス ID を作成するか、 API キーを更新すると、資格情報を更新できます。

### サービス ID の作成
{: #create_service_id}

サービス ID を作成するには、以下のステップを実行します。

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. 変更しようとしているプライベート・ワーカー・ツール統合のカードで、メニューをクリックして構成オプションにアクセスします。
1. **「作成」**をクリックします。
1. サービス ID の名前と説明を入力します。
1. **「統合の保存」**をクリックします。
1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. 新しいユーザー資格情報の指定対象の {{site.data.keyword.deliverypipeline}} Private Worker ツール統合のカードをクリックします。
1. **「開始」**をクリックし、ステップ 2 と 3 を実行して、クラスター上でプライベート・ワーカーを登録して検証します。

### API キーの更新
{: #update_api_key}

{{site.data.keyword.deliverypipeline}} Private Worker ツール統合で使用するために API キーを更新するには、以下のステップを実行します。

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. 変更しようとしている {{site.data.keyword.deliverypipeline}} Private Worker ツール統合のカードで、メニューをクリックして構成オプションにアクセスします。
1. 新しい API キーを指定します。 
1. **「統合の保存」**をクリックします。

## {{site.data.keyword.deliverypipeline}} プライベート・ワーカーの削除
{: #delete_private_worker}

プライベート・ワーカーを削除するには、以下のステップを実行します。

1. ワーカーのプールからプライベート・ワーカーを削除します。
1. Kubernetes クラスターからプライベート・ワーカーを削除します。

### ワーカーのプールからの {{site.data.keyword.deliverypipeline}} プライベート・ワーカーの削除

ワーカーのプールからプライベート・ワーカーを削除するには、以下のステップを実行します。

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. 構成対象の {{site.data.keyword.deliverypipeline}} Private Worker ツール統合のカードをクリックします。
1. **「概要」**をクリックします。
1. 削除しようとしているプライベート・ワーカーのメニューをクリックして、構成オプションにアクセスします。
1. **「削除」**をクリックしてから、**「確認」**をクリックします。

### Kubernetes クラスターからの {{site.data.keyword.deliverypipeline}} プライベート・ワーカーの削除

クラスターからプライベート・ワーカーを削除するには、以下のステップを実行します。

1. 構成対象の {{site.data.keyword.deliverypipeline}} Private Worker ツール統合のカードをクリックします。
1. **「開始」**をクリックし、クラスターからプライベート・ワーカーを削除するステップに従います。

## {{site.data.keyword.deliverypipeline}} Private Worker ツール統合の削除
{: #delete_private_workers_tool_integration}

ツールチェーンから {{site.data.keyword.deliverypipeline}} Private Worker ツール統合を削除する場合、削除を取り消すことはできません。
{: important}

{{site.data.keyword.deliverypipeline}} Private Worker ツール統合を削除するには、以下のステップを実行します。

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
1. 削除しようとしている {{site.data.keyword.deliverypipeline}} Private Worker ツール統合のカードで、メニューをクリックして構成オプションにアクセスします。
1. ツールチェーンからツール統合を削除するには、**「削除」**をクリックします。
1. **「削除」**をクリックして確認します。{{site.data.keyword.deliverypipeline}} Private Worker ツール統合がツールチェーンから削除され、デリバリー・パイプラインの「ステージ構成」ページの**「ワーカー」** タブ内で使用できなくなります。

{{site.data.keyword.deliverypipeline}} Private Worker ツール統合をツールチェーンから削除しても、プライベート・ワーカーがパイプライン・ステージ用に構成されている場合には、「ステージ構成」ページの**「ワーカー」**タブ内に引き続きリストされます。しかし、このプライベート・ワーカーは使用不可になり、「削除済み」というラベルが付けられます。代わりに、別のプライベート・ワーカーがある場合はそのワーカーを選択するか、またはパブリック・ワーカーを使用する必要があります。
{: tip}
