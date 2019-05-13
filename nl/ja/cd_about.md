---

Copyright:
  years: 2015, 2019
lastupdated: "2019-03-27"

keywords: IBM Cloud Public, Use Developer Insights, US South

subcollection: ContinuousDelivery

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


# ツールチェーンの使用可能状況、テンプレート、チュートリアル  
{: #cd_about}  

ツールチェーンは、{{site.data.keyword.Bluemix_notm}} Public と Dedicated で使用できます。 ツールチェーンを作成するための開始点として、テンプレートを使用することができます。
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated で提供されているツールチェーンの比較
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} Public は、[http://cloud.ibm.com ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://cloud.ibm.com){:new_window} によってアクセスされるアプリケーションを構築、実行、および管理するための、オープン・スタンダードのクラウド・ベース・プラットフォームです。 {{site.data.keyword.Bluemix_notm}} Dedicated は、{{site.data.keyword.Bluemix_notm}} Public 環境とユーザーのネットワークの両方に安全に接続される専用 SoftLayer 環境で {{site.data.keyword.Bluemix_notm}} の機能を提供します。 ユーザーの会社の {{site.data.keyword.Bluemix_notm}} Dedicated 環境には、{{site.data.keyword.Bluemix_notm}} Public サイトと同じツール統合が含まれていない可能性があります。

ソース・コード管理と問題のトラッキングについては、{{site.data.keyword.Bluemix_notm}} Public では通常、{{site.data.keyword.gitrepos}} (IBM によってホストされ、[GitLab Community Edition ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://about.gitlab.com/){:new_window} 上に構築されている) または GitHub (github.com) を使用します。 {{site.data.keyword.Bluemix_notm}} Dedicated でも github.com の使用は可能ですが、通常は、ユーザーの会社によってインストールされたか、IBM によって管理されている {{site.data.keyword.ghe_short}} が使用されます。

{{site.data.keyword.contdelivery_short}} は、選択された地域内の {{site.data.keyword.Bluemix_notm}} Public と、{{site.data.keyword.Bluemix_notm}} Dedicated で使用できます。 ツールチェーンは、{{site.data.keyword.contdelivery_short}} を {{site.data.keyword.Bluemix_notm}} Public で使用しているか、それとも {{site.data.keyword.Bluemix_notm}} Dedicated で使用しているかによって異なります。

ツールチェーンは現在、すべての地域で使用できるわけではありませんが、お客様のアプリをすべての地域にデプロイするようにツールチェーンを構成することは可能です。 詳しくは、[複数の領域にわたるセキュアな Web アプリケーションのデプロイのチュートリアル](/docs/tutorials?topic=solution-tutorials-multi-region-webapp){: new_window}を参照してください。
{: tip}

|ツールチェーン |{{site.data.keyword.Bluemix_notm}} Public	|{{site.data.keyword.Bluemix_notm}} Dedicated |
|:----------|:------------------------------|:------------------|
|ツール統合 		|サポートされているツール統合のリストについては、[ツール統合の構成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}を参照してください。 		|使用可能なツール統合は、ご使用環境での {{site.data.keyword.contdelivery_short}} のセットアップ方法によって決まります。			|
|テンプレートからのツールチェーンの作成		|[{{site.data.keyword.Bluemix_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://cloud.ibm.com/devops){:new_window} にログインします。		|{{site.data.keyword.Bluemix_notm}} 上の Dedicated 環境にログインします。			|
|アプリからのツールチェーンの作成		|アプリ・スターター・コードが取り込まれた新規 GitHub リポジトリーからアプリの継続的デリバリーが構成されます。		|アプリ・スターター・コードが取り込まれた新規 GitHub または GitHub Enterprise リポジトリーからアプリの継続的デリバリーが構成されます。		|  
|Delivery Pipeline のデプロイメント領域		|すべての {{site.data.keyword.Bluemix_notm}} Public 領域が Cloud Foundry デプロイメント・ジョブで使用可能です。 		|{{site.data.keyword.Bluemix_notm}} Dedicated 領域が使用可能です。 特定の環境内での {{site.data.keyword.contdelivery_short}} のセットアップ方法に応じて、同じカスタマー・アカウント内のその他の Dedicated 領域または Local 領域も使用可能な可能性があります。		|
|Delivery Pipeline のデプロイメント・ジョブ		|すべての[ジョブ・タイプ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs)が使用可能です。		|Dedicated 環境にインストールされていない {{site.data.keyword.Bluemix_notm}} サービスに依存するジョブ・タイプは、使用可能でない可能性があります。	例えば、コンテナー・ビルドとコンテナー・デプロイのジョブ・タイプは、{{site.data.keyword.containerlong_notm}} がインストールされていない環境では使用できない可能性があります。	|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} Dedicated と {{site.data.keyword.Bluemix_notm}} Public のツールチェーンの違い" caption-side="top"}


## ツールチェーン・テンプレート
{: #templates}

[ツールチェーンを作成![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/devops/create){: new_window}するための開始点としてテンプレートを使用することができます。 ツールチェーン・テンプレートは、開発、デプロイメント、および運用の各タスクをサポートする特定のツール統合セットを含んでいます。

ユーザーの会社の {{site.data.keyword.Bluemix_notm}} Dedicated 環境は、{{site.data.keyword.Bluemix_notm}} Public サイトと同じツールチェーン・テンプレートを含んでいない可能性があります。 {{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated の両方で使用可能なツールチェーン・テンプレートは、{{site.data.keyword.Bluemix_notm}} Dedicated 上では異なるツール統合セットを含んでいる可能性があります。
{: note}

一部のツールチェーン・テンプレートには、{{site.data.keyword.contdelivery_short}} サービスの一部であるツール統合が組み込まれています。 そのサービスのインスタンスがまだリソース・グループまたは組織にない場合は、**「作成」**をクリックしてツールチェーンを作成すると、無料のライト・プランが選択されてサービスが自動的に追加されます。 詳細情報とご利用条件については、[{{site.data.keyword.Bluemix_notm}} カタログ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/catalog/services/continuous-delivery/){:new_window} を参照してください。

「Develop and test microservices on Cloud Foundry」ツールチェーンは、Cloudant ストアによってサポートされている Catalog API と Orders API を使用してアプリをデプロイします。 アプリのデプロイの一部として、無料の Cloudant サービス・インスタンスが作成されます。 詳細情報とご利用条件については、[{{site.data.keyword.Bluemix_notm}} カタログ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){:new_window} を参照してください。

事前定義された DevOps ツールチェーン・テンプレートは現実世界の各種シナリオを解決する推奨例であり、各テンプレートにサンプル・アプリが含まれています。  テンプレートからツールチェーンを作成するときに Git リポジトリーを指定することで、独自のアプリを使用できます。

<table valign="top" padding="2px">
  <caption>表 2. ツールチェーン・テンプレート</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">テンプレートおよび利用可能な地域</th>
    <th style="width:50%; text-align:left; vertical-align:top">説明および参照できるチュートリアル</th>
    <th style="text-align:left; vertical-align:top">含まれるツール</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">「Develop a Cloud Foundry app」ツールチェーン <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、米国東部、ドイツ、東京、および英国で利用可能

  </td><td>
  このツールチェーンを使用すると、Cloud Foundry アプリを開発およびデプロイできます。 デフォルトで、このツールチェーンではサンプル Node.js の「Hello world」アプリが使用されますが、代わりにユーザー独自の GitHub リポジトリーにリンクすることもできます。 このツールチェーンは、継続的デリバリー、ソース管理、問題のトラッキング、およびオンライン編集用に事前構成されています。	<br><br>

  利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">「Develop a Cloud Foundry app」ツールチェーンを使用したツールチェーンの入門<img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">「Develop a Kubernetes app」ツールチェーン <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、米国東部、ドイツ、東京、および英国で利用可能

  </td><td>
  このツールチェーンを使用して、アプリケーションを開発し、{{site.data.keyword.containerlong_notm}} によって管理されている Kubernetes クラスターに安全にデプロイすることができます。 デフォルトで、このツールチェーンではサンプル Node.js の「Hello World」アプリが使用されますが、代わりにユーザー独自の GitHub リポジトリーにリンクすることもできます。 このツールチェーンは、脆弱性アドバイザーを使用した継続的デリバリー、ソース管理、問題のトラッキング、およびオンライン編集用に事前構成されています。 <br><br>
  利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">「Develop a Kubernetes app」ツールチェーンを使用する <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.containerlong_notm}} (Kubernetes クラスター)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">「Develop a Kubernetes app with Helm」ツールチェーン
   <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、米国東部、ドイツ、東京、および英国で利用可能

  </td><td>
  このツールチェーンを使用して、Docker アプリケーションとその Helm Chart を一緒にソース管理で開発し、それを自動的にビルドして Kubernetes クラスターにデプロイすることができます。 このツールチェーンは、ビルドとデプロイの前にスモーク・テストを実行し、コンテナー・レジストリーと Kubernetes クラスターのために専用コンテナー・レジストリーおよび名前空間を使用してプライバシーを確保します。 また、このツールチェーンは、脆弱性アドバイザーを使用することで、セキュアなイメージだけがデプロイされるようにします。 <br><br>
  利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">「Develop a Kubernetes app with Helm」ツールチェーンを使用する <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.containerlong_notm}} (Kurbernetes クラスター) (Helm Chart を使用)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">「Develop and test a Cloud Foundry app」ツールチェーン
   <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、ドイツ、英国で利用可能

  </td><td>
  このクラウド・ネイティブ・ツールチェーンでは、DevOps Insights を使用してシンプルな Cloud Foundry アプリケーションのデプロイメントをゲート制御できます。 デフォルトで、このツールチェーンではサンプル Node.js 気象アプリが使用されます。あるいは、ユーザー独自の GitHub リポジトリーにリンクすることもできます。 このツールチェーンは、Mocha を使用して単体テストを実行し、Istanbul を使用してコード・カバレッジをチェックします。<br><br>
  利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">「Develop and test a Cloud Foundry app」ツールチェーンを使用する <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  "Develop and test microservices on Cloud Foundry" toolchain <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、ドイツ、英国で利用可能

  </td><td>
  このクラウド・ネイティブ・ツールチェーンでは、サンプルを使用して、3 つのマイクロサービス (Catalog API、Orders API、および両方の API を呼び出す UI) からなるオンライン・ストアを作成することができます。 このツールチェーンは、継続的デリバリー、ソース管理、機能テスト、問題のトラッキング、オンライン編集、およびアラート通知用に事前構成されています。 <br><br>
  利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">「Develop and test microservices on Cloud Foundry」ツールチェーンを使用する <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">
「Garage Method tutorial with Cloud Foundry」ツールチェーン <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、米国東部、ドイツ、東京、および英国で利用可能

</td><td>
このツールチェーンは、Garage Method での特徴である DevOps プラクティスを示します。 このツールチェーンは、継続的デリバリー、ソース管理、テストの自動化、および自動化されたモニタリングと運用について事前構成されています。 このツールチェーンには、Node.js Express 4 で作成されたサンプル・アプリが付属しており、このアプリはさらなる拡張が可能です。 <br><br>利用可能なコース: <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Garage Method Advocate バッジを獲得する <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a>
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>GitHub and Issues
</li><li>Google アナリティクス
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fdevops-insights%2FDevOpsInsights_Demo_Toolchain_Template" target="_blank">「DevOps Insights Quick Start Demo」ツールチェーン <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、ドイツ、英国で利用可能

</td><td>
このツールチェーンを使用すると、セットアップしなくても {{site.data.keyword.DRA_short}} の機能を探索することができます。始めに、{{site.data.keyword.Bluemix}} にログインします。このデモンストレーションには、参照ツールチェーンと 3 つの GitHub リポジトリーから取得したデータが含まれています。品質ダッシュボードの中で、全チームの全アプリケーションのデータを整理、テスト、構築、およびデプロイする方法を探索してください。トレンドを評価し、改善が必要な分野を理解すると、自分のリソースをどこに集中させるべきかが分かります。Team Dynamics 内のリリースごとに、チーム・メンバーがどのようにコラボレーションしているかを確認できます。<br><br>
利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights" target="_blank">{{site.data.keyword.DRA_full}} の探索 <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>
</td><td><ul><li>
GitHub and Issues
</li><li>{{site.data.keyword.DRA_full}}
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">Build your own ツールチェーン <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a> <br><br>

  米国南部、米国東部、ドイツ、東京、および英国で利用可能

</td><td>
このツールチェーンには、事前構成されたツールは含まれていません。 ツールチェーンを既に熟知している場合、独自のツールチェーンをセットアップできます。 <br><br>
利用可能なチュートリアル: <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">カスタム・ツールチェーンの作成 <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a>
</td><td> &nbsp;&nbsp; なし
</td></tr>

<tr><td>Continuous Delivery ツールチェーン <br><br>

 米国南部、米国東部、ドイツ、東京、および英国で利用可能

</td><td>
このツールチェーンは、アプリの継続的デリバリーを有効にしている場合に使用できます。 <br><br>
利用可能なチュートリアル:

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Add a toolchain to an app <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Create a custom toolchain <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>
GitHub and Issues
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>カスタム・ツールチェーン・テンプレート <br><br>

 米国南部、米国東部、ドイツ、東京、および英国で利用可能

</td><td>
<br><br>
他のユーザーが使用できるカスタム・ツールチェーン・テンプレートを作成できます。 <br><br>

参照資料:
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">カスタム・ツールチェーン・テンプレートの作成 <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a>
 <br><br>
利用可能なチュートリアル:
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">カスタム・ツールチェーンのテンプレートの作成 <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン"></a></td>
<td>なし
</td></tr>

</table>
