---

Copyright:
  years: 2015, 2017
lastupdated: "2017-5-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# ツールチェーンの提供とテンプレート  
{: #cd_about}  

ツールチェーンは、{{site.data.keyword.Bluemix_notm}} Public と Dedicated で使用できます。ツールチェーンを作成するための開始点として、テンプレートを使用することができます。
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated で提供されているツールチェーンの比較
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} Public は、[http://bluemix.net ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bluemix.net){:new_window} によってアクセスされるアプリケーションを構築、実行、および管理するための、オープン・スタンダードのクラウド・ベース・プラットフォームです。{{site.data.keyword.Bluemix_notm}} Dedicated は、{{site.data.keyword.Bluemix_notm}} Public 環境とユーザーのネットワークの両方に安全に接続される専用 SoftLayer 環境で {{site.data.keyword.Bluemix_notm}} の機能を提供します。ユーザーの会社の {{site.data.keyword.Bluemix_notm}} Dedicated 環境には、{{site.data.keyword.Bluemix_notm}} Public サイトと同じツール統合が含まれていない可能性があります。

ソース・コード管理と問題のトラッキングについて、{{site.data.keyword.Bluemix_notm}} Public では一般に github.com が使用されます。{{site.data.keyword.Bluemix_notm}} Dedicated でも github.com の使用は可能ですが、通常は、ユーザーの会社によってインストールされたか、IBM によって管理されている {{site.data.keyword.ghe_short}} が使用されます。

{{site.data.keyword.contdelivery_short}} は、{{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated で使用可能です。ツールチェーンは、{{site.data.keyword.contdelivery_short}} を {{site.data.keyword.Bluemix_notm}} Public で使用しているか、それとも {{site.data.keyword.Bluemix_notm}} Dedicated で使用しているかによって異なります。

**ヒント**: ツールチェーンは米国南部地域でのみホストされます。異なる地域にアプリをデプロイするようにツールチェーンが構成されている場合でも、アプリは前述の地域にデプロイされます。

|ツールチェーン|{{site.data.keyword.Bluemix_notm}} Public	|{{site.data.keyword.Bluemix_notm}} Dedicated|
|:----------|:------------------------------|:------------------|
|ツール統合|サポートされているツール統合のリストについては、[ツール統合の構成](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}を参照してください。|使用可能なツール統合は、ご使用環境での {{site.data.keyword.contdelivery_short}} のセットアップ方法によって決まります。|
|テンプレートからのツールチェーンの作成|[{{site.data.keyword.Bluemix_notm}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://console.bluemix.net/devops){:new_window} にログインします。		|{{site.data.keyword.Bluemix_notm}} 上の Dedicated 環境にログインします。|
|アプリからのツールチェーンの作成|アプリ・スターター・コードが取り込まれた新規 GitHub リポジトリーからアプリの継続的デリバリーが構成されます。|アプリ・スターター・コードが取り込まれた新規 GitHub または GitHub Enterprise リポジトリーからアプリの継続的デリバリーが構成されます。|  
|Delivery Pipeline のデプロイメント領域|すべての {{site.data.keyword.Bluemix_notm}} Public 領域が Cloud Foundry デプロイメント・ジョブで使用可能です。|{{site.data.keyword.Bluemix_notm}} Dedicated 領域が使用可能です。特定の環境内での {{site.data.keyword.contdelivery_short}} のセットアップ方法に応じて、同じカスタマー・アカウント内のその他の Dedicated 領域または Local 領域も使用可能な可能性があります。|
|Delivery Pipeline のデプロイメント・ジョブ|すべての[ジョブ・タイプ](/docs/services/ContinuousDelivery/pipeline_about.html#deliverypipeline_jobs)が使用可能です。|Dedicated 環境にインストールされていない {{site.data.keyword.Bluemix_notm}} サービスに依存するジョブ・タイプは、使用可能でない可能性があります。例えば、コンテナー・ビルドとコンテナー・デプロイのジョブ・タイプは、{{site.data.keyword.Bluemix_notm}} Container サービスがインストールされていない環境では使用できない可能性があります。|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} Dedicated と {{site.data.keyword.Bluemix_notm}} Public のツールチェーンの違い" caption-side="top"}


## ツールチェーン・テンプレート
{: #templates}

[ツールチェーンを作成![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/create){: new_window}するための開始点としてテンプレートを使用することができます。ツールチェーン・テンプレートは、開発、デプロイメント、および運用の各タスクをサポートする特定のツール統合セットを含んでいます。

**ヒント**: ユーザーの会社の {{site.data.keyword.Bluemix_notm}} Dedicated 環境は、{{site.data.keyword.Bluemix_notm}} Public サイトと同じツールチェーン・テンプレートを含んでいない可能性があります。{{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated の両方で使用可能なツールチェーン・テンプレートは、{{site.data.keyword.Bluemix_notm}} Dedicated 上では異なるツール統合セットを含んでいる可能性があります。

一部のツールチェーン・テンプレートには、{{site.data.keyword.contdelivery_short}} サービスの一部であるツール統合が組み込まれています。そのサービスのインスタンスがまだ組織にない場合は、**「作成」**をクリックしてツールチェーンを作成した時に、無料で自動的にサービスが追加されます。詳細情報とご利用条件については、[Bluemix カタログ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/continuous-delivery/){:new_window}を参照してください。

Microservices ツールチェーン・テンプレートは、Cloudant ストアによって支持されているカタログ API とオーダー API を使用してアプリをデプロイします。アプリのデプロイの一部として、無料の Cloudant サービス・インスタンスが作成されます。詳細情報とご利用条件については、[Bluemix カタログ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/cloudant-nosql-db/){:new_window}を参照してください。

|テンプレート|説明|チュートリアルを始める|
|:----------|:------------------------------|:------------------|
|[Garage Method cloud-native tutorial toolchain![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial){:new_window} 		|このツールチェーンは、Garage Method での特徴である DevOps プラクティスを示します。このツールチェーンは、継続的デリバリー、ソース管理、テストの自動化、および自動化されたモニタリングと運用について事前構成されています。このツールチェーンには、Node.js Express 4 で作成されたサンプル・アプリが付属しており、このアプリはさらなる拡張が可能です。![ツールチェーン内のツール](images/cloud-native-tc-tools.png)
    |[Create and use your first toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_flow){:new_window} 		|
|[Microservices toolchain with {{site.data.keyword.DRA_short}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Ftoolchain-demo){:new_window}    |このクラウド・ネイティブ・ツールチェーンでは、サンプルを使用して、3 つのマイクロサービス (Catalog API、Orders API、および両方の API を呼び出す UI) からなるオンライン・ストアを作成することができます。このツールチェーンは、継続的デリバリー、ソース管理、機能テスト、問題のトラッキング、オンライン編集、およびアラート通知用に事前構成されています。|[Create and use a microservices toolchain with {{site.data.keyword.DRA_short}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_microservices){:new_window} 		|
|[Microservices toolchain with {{site.data.keyword.DRA_short}} (v2) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted){:new_window}  	 |このクラウド・ネイティブ・ツールチェーンでは、サンプルを使用して、3 つのマイクロサービス (Catalog API、Orders API、および両方の API を呼び出す UI) からなるオンライン・ストアを作成することができます。このツールチェーンは、継続的デリバリー、ソース管理、機能テスト、問題のトラッキング、オンライン編集、およびアラート通知用に事前構成されています。|[Create and use a microservices toolchain with {{site.data.keyword.DRA_short}} (v2) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_microservices_cd?task=1){:new_window} 		|
|[Secure container toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-container-toolchain){:new_window} 		|このツールチェーンを使用すると、セキュアな Docker コンテナー・アプリを開発およびデプロイできます。デフォルトで、このツールチェーンではサンプル Node.js の「Hello World」アプリが使用されますが、代わりにユーザー独自の GitHub リポジトリーにリンクすることもできます。このツールチェーンは、脆弱性アドバイザーを使用した継続的デリバリー、ソース管理、問題のトラッキング、およびオンライン編集用に事前構成されています。|[Create and use a secure container toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_secure_container){:new_window} 		|
|[Simple Cloud Foundry toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain){:new_window}		|このツールチェーンを使用すると、Cloud Foundry アプリを開発およびデプロイできます。デフォルトで、このツールチェーンではサンプル Node.js の「Hello world」アプリが使用されますが、代わりにユーザー独自の GitHub リポジトリーにリンクすることもできます。このツールチェーンは、継続的デリバリー、ソース管理、問題のトラッキング、およびオンライン編集用に事前構成されています。|[Create and use your first toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_flow){:new_window} 		|
|[Simple Cloud Foundry toolchain	(v2) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain-hosted){:new_window}	|このツールチェーンを使用すると、Cloud Foundry アプリを開発およびデプロイできます。デフォルトで、このツールチェーンではサンプル Node.js の「Hello World」アプリが、IBM がホストする Git リポジトリーに複製されます。複製されたアプリは後から変更できます。このツールチェーンは、継続的デリバリー、ソース管理、問題のトラッキング、およびオンライン編集用に事前構成されています。|[Create a toolchain that uses {{site.data.keyword.gitrepos}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_cfv2){:new_window} 		|
|[Simple Cloud Foundry toolchain with {{site.data.keyword.DRA_short}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo){:new_window}		|このクラウド・ネイティブ・ツールチェーンでは、{{site.data.keyword.DRA_short}} を使用してシンプルな Cloud Foundry アプリのデプロイメントをゲート制御できます。デフォルトで、このツールチェーンではサンプル Node.js 気象アプリが使用されます。あるいは、ユーザー独自の GitHub リポジトリーにリンクすることもできます。|[Create a toolchain that uses {{site.data.keyword.DRA_short}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_devops_insights){:new_window} 		|
|[Simple Container toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-container-toolchain){:new_window}		|このツールチェーンを使用すると、Docker コンテナー・アプリを開発およびデプロイできます。デフォルトで、このツールチェーンではサンプル Node.js の「Hello World」アプリが使用されますが、代わりにユーザー独自の GitHub リポジトリーにリンクすることもできます。このツールチェーンは、継続的デリバリー、ソース管理、問題のトラッキング、およびオンライン編集用に事前構成されています。|[Create and use a simple container toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_container){:new_window} 		|
|[Delivery Insights with IBM UrbanCode Deploy ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdeliveryinsights-toolchain){:new_window}		|このツールチェーンを使用すると、IBM UrbanCode Deploy からデプロイメント・メトリックを表示できます。{{site.data.keyword.DRA_short}} の「設定」ページから DevOps Connect をダウンロードして構成することにより IBM UrbanCode Deploy と通信するには、このツールチェーンを使用可能にします。|[View metrics from IBM UrbanCode Deploy servers in {{site.data.keyword.DRA_short}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_delivery_insights){:new_window} 		|
|[Deployment Risk Analytics with GitHub and Jenkins ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevopsinsights-toolchain){:new_window}		|このツールチェーンを使用すると、継続的統合および継続的デリバリーのための Jenkins プロセスについての洞察を得ることができます。Jenkins サーバーを構成して、Jenkins によってジョブが実行されている時に {{site.data.keyword.DRA_short}} にデータを送信することができます。また、品質ゲートを実装して、ポリシーに基づいてデプロイメントをブロックすることもできます。結果は、{{site.data.keyword.DRA_short}} の「デプロイメント・リスク」ダッシュボードで見ることができます。Jenkins で使用されているソース・リポジトリーを示すように GitHub リポジトリーを構成すると、変更トレーサビリティーが使用可能になります。|[Deployment Risk Analytics with GitHub and Jenkins ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_dra){:new_window}		|
|[Developer Insights and Team Dynamics with GitHub and JIRA ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevteaminsights-toolchain){:new_window}		|このツールチェーンを使用すると、プロジェクトの開発リスクを探り、ソーシャル・コーディング分析を使用して開発者間の対話パターンを理解することができます。GitHub のソース・コードを、GitHub の問題、JIRA の問題、またはそれら両方と併せて分析できます。Developer Insights を使用して、非常にエラーが発生しやすいファイルを識別し、プロジェクトがどのように DevOps プラクティスに従っているか確認します。Team Dynamics のソーシャル・コーディング分析は、チームが非生産的なプラクティスを修正できるように、チーム・メンバー間の対話レベルを識別します。|[Gain developer and team insights on a JIRA and GitHub project ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_dev_insights_team_dynamics){:new_window} 		|
|[Build your own toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain){:new_window}		|このツールチェーンには、事前構成されたツールは含まれていません。ツールチェーンを既に熟知している場合、独自のツールチェーンをセットアップできます。|[Create a custom toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_custom){:new_window}
{: caption="表 2. ツールチェーン・テンプレート" caption-side="top"}
