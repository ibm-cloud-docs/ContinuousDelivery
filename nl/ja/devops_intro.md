---

Copyright:
 years: 2015, 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# {{site.data.keyword.Bluemix_notm}} DevOps
{: #devops_intro}

市場の要求する速さでソフトウェアとサービスを提供するには、チームが反復と実験を迅速に行う必要があります。 フィードバックとデータに基づいて、新しいバージョンを頻繁にデプロイする必要があります。 最も成功しているクラウド開発チームは、最新の DevOps のカルチャーとプラクティスを採用し、クラウド・ネイティブ・アーキテクチャーを主軸にして、クラス最高のツールによってツールチェーンを組み立てて、生産性を高めています。 これらが迅速に行えるなら、競争上の強みになります。

 
<a href="https://www.ibm.com/cloud/garage">IBM Cloud Garage Method <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> では、企業が大規模なイノベーションを行えるようにするための、アーキテクチャー、プラクティス、および DevOps ツールチェーンについて説明しています。カルチャーを変革し、ツールを効率的に素早く使用できるようにするために、{{site.data.keyword.Bluemix_notm}} Garage Method をお役立てください。

エンタープライズ・アプリケーションの開発者は、クラウド・ネイティブ・アプリケーションのビルドとデプロイをすぐに開始できます。 サービスの完全なセットを使用して、コグニティブ、IoT、ブロックチェーン、モバイル、およびデータ集中型のアプリケーションを構築できます。 IBM Cloud アプリケーション・サービスを使用すると、個々の開発者はプロジェクトを作成し、アプリケーション・スターター・キットを選択し、実稼働の準備ができたアプリケーションを {{site.data.keyword.Bluemix_notm}} にデプロイすることができます。 プラットフォームのコード生成テクノロジーにより、開発者の希望する言語およびフレームワークで、それぞれのニーズやユースケースに合わせて調整されたスターター・アプリケーションが作成されます。 Watson Conversation など、ユース・ケースのサポートに必要なサービスは、自動的にプロビジョンされます。 開発者は、ローカル・ワークステーションまたはクラウドでデバッグとテストを行い、DevOps ツールチェーンを使用して他のユーザーとコラボレーションし、配信プロセスを自動化することができます。

チーム・メンバーがプロジェクトに参加するときには、開発、デプロイメント、および実稼働の各操作にまたがる統合ツール・セットが必要となります。 IBM の Open Toolchain アーキテクチャーにより、チームは、IBM やオープン・ソースなどからそのクラスで最高の DevOps ツールを迅速にプロビジョンできます。 これらのツール間の統合は自動的に構成されます。 ツールチェーンはこのプラットフォームの最重要概念で、これによって、開発者は必要なものすべてを 1 箇所で素早く編成し、時間の経過とともにツールチェーンを発展させることができます。 IBM は、Garage Method のベスト・プラクティスをサポートするツールチェーン・テンプレートを提供しています。これをカスタマイズして、企業全体に実証済みのツールチェーン・パターンをプロモートすることができます。

{{site.data.keyword.contdelivery_full}} は、DevOps ツールチェーン用のツールのコア・セットを提供します。それらは、{{site.data.keyword.gitrepos}}、Delivery Pipeline、Eclipse Orion {{site.data.keyword.webide}} です。 {{site.data.keyword.gitrepos}} は、GitLab Community Edition をベースにしており、計画ボードと、マージ要求によるソース・コード・コラボレーションを提供します。 Delivery Pipeline は、開発から実稼働への過程で変更が加えられていくときに、複数の環境に渡ってビルド、テスト、およびデプロイメントの各ジョブを統合します。 アプリケーションは、Cloud Foundry 環境、{{site.data.keyword.Bluemix_notm}} 上の Kubernetes クラスター、またはパブリック・クラウドかプライベート・クラウドのいずれかに、短時間でデプロイできます。 Eclipse Orion {{site.data.keyword.webide}} を使用すると、開発者は任意のブラウザーからコードに素早くアクセスできます。

Open ツールチェーンは、{{site.data.keyword.contdelivery_short}} の周辺に、Slack、Atlassian JIRA、Sonatype Nexus、JFrog Artifactory、Sauce Labs、PagerDuty、IBM Cloud Availability Monitoring、IBM Cloud Alert Notification、IBM Vulnerability Advisor、IBM Globalization Pipeline などの 1 つ以上のツールを統合します。 GitHub、GitHub Enterprise、Jenkins などの他のツールを {{site.data.keyword.contdelivery_short}} の機能の代わりに使用することもできます。 開発者は、Visual Studio Code、Eclipse などの自分の好みの IDE やエディターを使用することもできます。

コード・リポジトリー、問題トラッキング・システム、ビルド・システム、およびデプロイメント・システムは、アプリをより効率的かつ効果的に配信するのに役立つ豊富なデータを提示します。 {{site.data.keyword.DRA_full}} はビッグデータ分析を使用して、経営陣、マネージャー、および開発者に貴重な分析情報を提供します。 {{site.data.keyword.DRA_short}} は、DevOps ツールチェーンのデータを集約および分析して、特定の変更をデプロイするリスク、およびコードベースとチームの生産性の両方を改善するための分野についてアドバイスします。 Delivery Pipeline は、変更のリスクに基づいて、環境へのデプロイメントを自動的にゲート制御できます。

リソース・グループは、米国南部、米国東部、英国、ドイツ、および東京領域で利用可能です。 Cloud Foundry の組織は、米国南部、英国およびドイツ地域でサポートされています。
{: note}

{{site.data.keyword.Bluemix_notm}} DevOps は、クラウド開発用の具体的なプラクティスとアーキテクチャーを提供します。これによって開発者は {{site.data.keyword.Bluemix_notm}} でサービスの豊富なカタログを使用する新規プロジェクトを迅速に開始できます。また、{{site.data.keyword.Bluemix_notm}} DevOps によって、高速で制御された自動配信のための、オープンで統合されたツールのセットが開発者に提供されます。
