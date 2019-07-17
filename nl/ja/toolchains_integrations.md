---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-27"

keywords: tool integrations, IBM Cloud Public, Alert Notification, Configuring Artifactory

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

# ツール統合の構成
{: #integrations}

開発、デプロイメント、および運用の作業をサポートするツール統合をオープン・ツールチェーンの作成時に構成するか、ツール統合を追加および構成して既存のツールチェーンをカスタマイズすることができます。  
{:shortdesc}

ツールチェーンで追加および構成できるツール統合は、{{site.data.keyword.Bluemix_notm}} Public または {{site.data.keyword.Bluemix_notm}} Dedicated のどちらを使用しているかによって異なります。 {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを使用している場合、利用できるツール統合は、ツールチェーンの地域と、その地域でツール統合を利用できるかどうかに応じて異なります。 {{site.data.keyword.Bluemix_notm}} Dedicated でツールチェーンを使用している場合、利用できるツール統合は、特定の環境で {{site.data.keyword.contdelivery_full}} がどのように設定されたかに応じて異なります。

|ツール統合 |{{site.data.keyword.Bluemix_notm}} Public で利用可能	|{{site.data.keyword.Bluemix_notm}} Dedicated で利用可能 (環境依存)|
|:----------|:------------------------------|:------------------|
|{{site.data.keyword.alertnotificationshort}}		|米国南部		|いいえ		|
|Artifactory		|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|Availability Monitoring		|米国南部		|いいえ		|
|Bitbucket		|米国南部、米国東部、ドイツ、東京、英国		|いいえ		|
|Cloud Event Management		|米国南部		|いいえ		|
|{{site.data.keyword.deliverypipeline}} 		|米国南部、米国東部、ドイツ、東京、英国	   	|はい  		|
|{{site.data.keyword.deliverypipeline}} Private Worker			|米国南部、米国東部、ドイツ、東京、英国		|いいえ		|
|{{site.data.keyword.DRA_short}} 		|米国南部、ドイツ、英国		|いいえ			|
|Eclipse Orion {{site.data.keyword.webide}}		|米国南部、米国東部、ドイツ、東京、英国		|はい			|
|{{site.data.keyword.gitrepos}}	|米国南部、米国東部、ドイツ、東京、英国		|いいえ		|
|GitHub		|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|Dedicated {{site.data.keyword.ghe_short}} and Issues			|いいえ		|はい		|
|GitLab		|米国南部、米国東部、ドイツ、東京、英国		|いいえ		|
|Jenkins		|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|JIRA		|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|Nexus			|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|他のツール			|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|PagerDuty			|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|Rational Team Concert			|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|Sauce Labs		|米国南部、米国東部、ドイツ、東京、英国		|いいえ		|
|Slack			|米国南部、米国東部、ドイツ、東京、英国		|はい		|
|SonarQube			|米国南部、米国東部、ドイツ、東京、英国		|はい		|
{: caption="表 1. {{site.data.keyword.Bluemix_notm}} Public と Dedicated のツールチェーンで使用可能なツール統合" caption-side="top"}

{{site.data.keyword.Bluemix_notm}} Public でソース・コードを開発することから始める場合は、{{site.data.keyword.deliverypipeline}} を構成する前に GitHub ツール統合または {{site.data.keyword.gitrepos}} ツール統合を構成してください。 {{site.data.keyword.Bluemix_notm}} Dedicated でコードでの開発を開始する場合は、{{site.data.keyword.deliverypipeline}} を構成する前に {{site.data.keyword.ghe_short}} ツール統合を構成します。
{: tip}


## Alert Notification の構成
{: #alertnotification}

{{site.data.keyword.alertnotificationfull}} は、通知戦略を中央化および簡素化するために使用できる、ハイブリッド・クラウド・ベースのソリューションです。 他のクラウド・ベースのアプリケーションおよびオンプレミス・アプリケーションと連携して機能します。 アラートはセキュアな RESTful API を使用して {{site.data.keyword.alertnotificationshort}} に転送されます。

DevOps 処理中の問題に関する通知を受け取るように {{site.data.keyword.alertnotificationshort}} を構成します。

### 前提条件

1. {{site.data.keyword.alertnotificationshort}} アカウントをお持ちでない場合、登録して取得します。

 a. IBM Marketplace で [IBM {{site.data.keyword.alertnotificationshort}}](https://www.ibm.com/us-en/marketplace/alert-notification){:external} ページを開きます。

 b. サブスクリプションを購入するか、90 日間の無料評価版に申し込みます。

1. {{site.data.keyword.alertnotificationshort}} アカウントのセットアップが終わったら、[My IBM Dashboard](https://myibm.ibm.com/dashboard/){:external} を開きます。
1. IBM {{site.data.keyword.alertnotificationshort}} の横の**「起動」**をクリックします。
1. **「API キーの管理 (Manage API Keys)」**をクリックし、**「API キーの作成 (Create API Key)」**をクリックします。
1. **「API キーの作成 (Create API Key)」**フィールドに説明を入力します。
1. **「生成 (Generate)」**をクリックします。 名前およびパスワードなどの新規 API キー情報が表示されます。 この情報はツール統合の構成に必要であるため、「新規 API キー (New API Key)」ウィンドウを開いたままにしておいてください。 セキュリティーのため、後で API キーのパスワードを取り出すことはできません。

### Alert Notification の構成

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「{{site.data.keyword.alertnotificationshort}}」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「{{site.data.keyword.alertnotificationshort}}」**をクリックします。

1. 使用したい {{site.data.keyword.alertnotificationshort}} API の URL を入力します。 URL は {{site.data.keyword.alertnotificationshort}} サービスの「API キーの管理 (Manage API Keys)」ページで見つけることができます (例: `https://ibmnotifybm.mybluemix.net/api/alerts/v1`)。
1. {{site.data.keyword.alertnotificationshort}} の API アクセス・キーを入力します。 API キー名は「新規 API キー (New API Key)」ウィンドウで確認できます。
1. API キーに対して {{site.data.keyword.alertnotificationshort}} が生成したパスワードを入力します。 API キーのパスワードは「新規 API キー (New API Key)」ウィンドウで確認できます。
1. **「統合の作成」**をクリックします。
1. ツールチェーンから、**「{{site.data.keyword.alertnotificationshort}}」**をクリックします。

### Alert Notification に関する詳細

{{site.data.keyword.alertnotificationshort}} について詳しくは、IBM Cloud Garage Method の[記事「IBM {{site.data.keyword.alertnotificationshort}}」](https://www.ibm.com/cloud/garage/content/manage/tool_alert_notification/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [ツールチェーンへのツール統合の追加](https://www.ibm.com/cloud/garage/tutorials/add-a-tool-integration-to-a-toolchain){:external}

  * [{{site.data.keyword.Bluemix_notm}} Availability Monitoring と Alert Notification を使用した {{site.data.keyword.Bluemix_notm}} アプリケーションの管理](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:external}


## Artifactory の構成
{: #artifactory}

ビルド成果物を Artifactory リポジトリーに保管するように Artifactory リポジトリー・マネージャーを構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Artifactory」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「Artifactory」**をクリックします。

1. Artifactory カードをクリックしたときに開くようにしたい Artifactory リポジトリーの URL を入力します。
1. 接続先にするリポジトリーのタイプを選択します。
1. Artifactory npm レジストリーを使用する場合は、以下のステップを実行します。

 a. レジストリーと関連付けられた E メール・アドレスを入力します。

 b. レジストリーと関連付けられた認証トークンを入力します。

 c. Artifactory サーバー上のプライベート・レジストリーである Artifactory リリース・リポジトリーの URL を入力します。

 d. 複数のパブリックおよびプライベート npm レジストリーを結合するために使用する Mirror または Public レジストリーの URL を入力します。 例えば、この URL は、プライベート・レジストリーと、npm グローバル・レジストリーのキャッシュの両方にアクセスできる、Artifactory サーバー上の仮想レジストリーの URL であることができます。

1. Artifactory Maven リポジトリーを使用する場合は、以下のステップを実行します。

 a. リポジトリーと関連付けられたユーザー ID を入力します。

 b. リポジトリーと関連付けられたパスワードを入力します。

 c. Artifactory サーバー上のプライベート・リリース・リポジトリーである Artifactory リリース・リポジトリーの URL を入力します。

 d. Artifactory サーバー上のプライベート・スナップショット・リポジトリーである Artifactory スナップショット・リポジトリーの URL を入力します。

 e. 複数のパブリックおよびプライベート Maven リポジトリーを結合するために使用する Mirror または Public リポジトリーの URL を入力します。 例えば、この URL は、プライベート・リポジトリーと、Maven 中央リポジトリーのキャッシュの両方にアクセスできる、Artifactory サーバー上の仮想リポジトリーの URL であることができます。

1. **「統合の作成」**をクリックします。
1. 作業対象の Artifactory リポジトリーのカードをクリックします。 Artifactory の Web サイトが開きます。そこでリポジトリーの内容を表示できます。
1. オプション: {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを使用していて、Artifactory を npm と共に使用してアプリをビルドしたい場合、パイプラインを構成して npm ビルド・ジョブを追加します。 ビルド・ジョブの構成手順については、『[パイプラインに Artifactory npm ビルド・ジョブを構成する](#config_artifactory_npm)』セクションを参照してください。
1. オプション: {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを使用していて、Artifactory を Maven と共に使用してアプリをビルドしたい場合、パイプラインを構成して Maven ビルド・ジョブを追加します。 ビルド・ジョブの構成手順については、『[パイプラインに Artifactory Maven ビルド・ジョブを構成する](#config_artifactory_maven)』セクションを参照してください。

### パイプラインに Artifactory npm ビルド・ジョブを構成する
{: #config_artifactory_npm}

パイプラインに npm ビルド・ジョブを構成する前に、ビルド SCM リポジトリーを入力として使用できる作業パイプラインが存在している必要があります。 また、ツールチェーンに Artifactory を構成しておく必要もあります。 Artifactory の構成手順については、[Artifactory](#artifactory) のセクションを参照してください。

{{site.data.keyword.deliverypipeline}} を構成して npm ビルド・ジョブを追加します。

1. ステージを作成し、入力を適切な SCM リポジトリーに設定します。
1. このステージでビルド・ジョブを追加します。
1. ビルド・ジョブを構成します。
  ![npm ビルド・ジョブ](images/artifactory_npm_job.png)

  a. ビルダー・タイプに**「NPM ビルド (NPM Build)」**を選択します。

  b. Artifactory ツール統合の複数インスタンスを構成した場合、npm ビルド・ジョブを構成する対象にしたい Artifactory ツール統合の名前を入力します。

  c. ツール統合タイプに**「Artifactory」**を選択します。

  d. ビルド・コマンドには、npm モジュールのビルドまたはレジストリーへのモジュールのパブリッシュを行うコマンドを入力します。 次の例は、モジュールのビルドまたはパブリッシュのいずれかを行うコマンドを示します。
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  レジストリーへの接続に使用した URL およびユーザー資格情報は、Artifactory ツール統合の構成設定で見つけることができます。
  {: tip}

  e. ビルド・ジョブが Artifactory レジストリーへのパブリッシュを行い、かつ、ノード・モジュール・バージョンのフォーマットが `x.y.z-SNAPSHOT.w` である場合、**「スナップショット・モジュール・バージョンのインクリメント (Increment snapshot module version)」**チェック・ボックスにチェック・マークを付けます。 ビルド・ジョブは、モジュール・バージョンを自動的に更新した後で、Artifactory レジストリーにパブリッシュします。 ジョブは、npm レジストリーおよびローカル `package.json` ファイルから最高バージョンのモジュールを選択し、semver を使用してモジュール・バージョンを増やします。 ビルド・ジョブは、変更を SCM リポジトリーに配信しません。

1. **「保存」**をクリックします。 パイプラインが実行されると、このビルド・ジョブは Artifactory ツール統合からの構成情報を使用して npm レジストリーに接続します。

### パイプラインに Artifactory Maven ビルド・ジョブを構成する
{: #config_artifactory_maven}

パイプラインに Maven ビルド・ジョブを構成する前に、ビルド SCM リポジトリーを入力として使用できる作業パイプラインが存在している必要があり、また、ツールチェーンに Artifactory を構成しておく必要もあります。 Artifactory の構成手順については、[Artifactory](#artifactory) のセクションを参照してください。

{{site.data.keyword.deliverypipeline}} を構成して Maven ビルド・ジョブを追加します。

1. ステージを作成し、入力を適切な SCM リポジトリーに設定します。
1. このステージでビルド・ジョブを追加します。
1. ビルド・ジョブを構成します。
  ![Maven ビルド・ジョブ](images/artifactory_maven_job.png)

  a. ビルダー・タイプに**「Maven ビルド (Maven Build)」**を選択します。

  b. Artifactory ツール統合の複数インスタンスを構成した場合、Maven ビルド・ジョブを構成する対象にしたい Artifactory ツール統合の名前を入力します。

  c. ツール統合タイプに**「Artifactory」**を選択します。

  d. ビルド・コマンドには、Maven モジュールのビルドまたはスナップショット・レジストリーへのモジュールのパブリッシュを行うコマンドを入力します。 次の例は、モジュールのビルドまたはスナップショット・レジストリーへのモジュールのパブリッシュのいずれかを行うコマンドを示します。
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  レジストリーへの接続に使用した URL およびユーザー資格情報は、Artifactory ツール統合の構成設定で見つけることができます。
  {: tip}

1. **「保存」**をクリックします。 パイプラインが実行されると、このビルド・ジョブは Artifactory ツール統合からの構成情報を使用して Maven リポジトリーに接続します。

### Artifactory に関する詳細

Artifactory について詳しくは、IBM Cloud Garage Method の[記事「Artifactory」](https://www.ibm.com/cloud/garage/content/deliver/tool_artifactory/){:external}を参照してください。


## Availability Monitoring の追加
{: #availabilitymonitoring}

{{site.data.keyword.prf_hublong}} は、ユーザーに影響が及ぶ前に、問題を切り分け、パターンを識別し、パフォーマンスを改善します。 世界中の場所でアプリをテストし、Delivery Pipeline に統合し、コードを継続的に最適化する方法についての洞察を深めることができます。

このツール統合は事前構成されているため、構成パラメーターは必要ありません。 このツール統合を再構成することはできません。
{: tip}

アプリをビルドするときに、アプリの正常性をテスト、モニター、および改善するために、{{site.data.keyword.prf_hubshort}} ツール統合を追加します。

1. DevOps ダッシュボードの「ツールチェーン」ページで、{{site.data.keyword.prf_hubshort}} を追加するツールチェーンをクリックします。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「{{site.data.keyword.prf_hubshort}}」**をクリックします。

1. **「統合の作成」**をクリックします。
1. **「{{site.data.keyword.prf_hubshort}}」**をクリックして {{site.data.keyword.prf_hubshort}} ダッシュボードを開き、アプリを選択し、そのアプリのモニタリングを構成します。

### Availability Monitoring に関する詳細

{{site.data.keyword.prf_hubshort}} について詳しくは、IBM Cloud Garage Method の[記事「{{site.data.keyword.prf_hublong}}」](https://www.ibm.com/cloud/garage/practices/manage/tool_bluemix_availability_monitoring/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [{{site.data.keyword.Bluemix_notm}} Availability Monitoring と Alert Notification を使用した {{site.data.keyword.Bluemix_notm}} アプリケーションの管理](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:external}


## Bitbucket の構成
{: #bitbucket}

bitbucket.org の新規か既存のリポジトリーにソース・コードを保管し、Wiki、問題のトラッキング、プル要求を介してソーシャル・コーディングに参加します。

チームとコードの共同作業を行うために Bitbucket を構成するには、以下のようにします。

1. DevOps ダッシュボードから、**「ツールチェーン」**をクリックします。 Bitbucket を追加するツールチェーンをクリックします。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「Bitbucket」**をクリックします。

   {{site.data.keyword.Bluemix_notm}} Public でこのツール統合を構成しており、Bitbucket へのアクセスを {{site.data.keyword.Bluemix_notm}} に許可していない場合は、**「許可」**をクリックして Bitbucket Web サイトに移動します。 アクティブな Bitbucket セッションがない場合は、ログインするよう求められます。 **「アクセス権限の付与 (Grant access)」**をクリックして、{{site.data.keyword.Bluemix_notm}} ツールチェーンが Bitbucket アカウントの以下の部分にアクセスできるようにします。
   
   * **アカウント情報をお読みください**。 基本的なユーザー情報を取得して、ユーザー・インターフェースを設定します。
   
   * **リポジトリーの問題を読み取り、変更します**。 {{site.data.keyword.contdelivery_short}} で問題を更新し、これらの問題にアタッチされているコミットをパイプラインがデプロイするときにそのことが示されるようにします。 
   
   * **チームのプロジェクト設定を読み、チームのプロジェクト内に含まれるリポジトリーを読み取ります**。 {{site.data.keyword.contdelivery_short}} で、チームが所有するリポジトリーと統合できるようにします。
   
   * **リポジトリーとそのプル要求を読み取り、変更します**。 ユーザーがコードを要求したときに、{{site.data.keyword.contdelivery_short}} でサンプル・コードをリポジトリーにプッシュできるようにします。
   
   * **リポジトリーを管理します**。 ユーザーから要求された場合に、{{site.data.keyword.contdelivery_short}} で新規リポジトリーを作成できるようにします。
   
   * **チーム・メンバーシップ情報をお読みください**。 {{site.data.keyword.contdelivery_short}} で、新規リポジトリーの作成時に表示される**「所有者」**メニューにチームのリストを表示できるようにします。
   
   * **リポジトリーの Web フックを読み取り、変更します**。 コミットがリポジトリーにプッシュされたときに、パイプラインがビルドをトリガーできるようにします。
   {: tip}
   
   アクティブな Bitbucket セッションはあるものの、最近パスワードを入力していない場合は、確認のために Bitbucket パスワードの入力を求められることがあります。

1. 使用する Bitbucket サーバーをクリックします。
1. 既存の Bitbucket リポジトリーを使用する場合は、そのリポジトリーの URL を入力します。 リポジトリー・タイプには、**「既存」**をクリックします。
1. 新しい Bitbucket リポジトリーを使用する場合は、そのリポジトリーに付ける名前を入力し、複製またはフォークするリポジトリーの URL を入力し、リポジトリー・タイプを次のように選択します。

 a. 空のリポジトリーを作成する場合は、**「新規」**をクリックします。

 b. リポジトリーのコピーを作成する場合は、**「クローンを作成する (Clone)」**をクリックします。

 c. リポジトリーをフォークし、プル・リクエストで変更内容を提供できるようにする場合は、**「フォーク (Fork)」**をクリックします。

1. サーバー上にプライベート・リポジトリーを作成するには、**「このリポジトリーをプライベートにする (Make this repository private)」**チェック・ボックスを選択します。
1. 問題のトラッキングに Bitbucket Issues を使用する場合は、**「Bitbucket Issues を使用可能にする (Enable Bitbucket Issues)」**チェック・ボックスにチェック・マークを付けます。
1. コミットに対するタグおよびコメントと、コミットで参照される問題に対するラベルおよびコメントを作成することによって、コード変更のデプロイメントをトラッキングするには、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 詳しくは、[Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external} を参照してください。
1. **「統合の作成」**をクリックします。
1. 作業対象の Bitbucket リポジトリーのカードをツールチェーンからクリックします。 Bitbucket の Web サイトが開きます。そこでリポジトリーの内容を表示できます。
1. Bitbucket Issues を使用可能にした場合、**「Bitbucket Issues」**をクリックして開きます。 ツールチェーンに複数の Bitbucket リポジトリーが含まれれている場合でも、Bitbucket Issues のこのインスタンスをツールチェーン全体に使用できます。

リンクしようとしているリポジトリーに対する所有者またはマスター特権がない場合は、Web フックを使用できないので統合は制限されます。 リポジトリーにコミットがプッシュされたときにパイプラインが自動的に実行されるようにするには、Web フックが必要です。 Web フックがない場合、パイプラインを手動で開始する必要があります。
{: tip}

### Bitbucket に関する詳細

Bitbucket について詳しくは、IBM Cloud Garage Method の[記事「Bitbucket」](https://www.ibm.com/cloud/garage/content/code/tool_bitbucket/){:external}を参照してください。


## Cloud Event Management の追加
{: #cloudeventmanagement}

{{site.data.keyword.evtmgt_full}} は、ユーザーのサービス、アプリケーション、およびインフラストラクチャーで発生する問題の統合ビューを提供します。 問題をより効率的に解決できるよう、リアルタイムのインシデント管理をセットアップできます。

このツール統合は事前構成されているため、構成パラメーターは必要ありません。 これを再構成することはできません。
{: tip}

信頼できる運用正常性、サービス品質、および継続的改善という目標を DevOps チームが達成するのを助けるために、Cloud Event Management をツールチェーンに追加します。

1. DevOps ダッシュボードから、**「ツールチェーン」**をクリックします。 Cloud Event Management を追加するツールチェーンをクリックします。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「Cloud Event Management」**をクリックします。

1. **「統合の作成」**をクリックします。
1. ツールチェーンから、以下のツール・カードのうち任意のものをクリックします。

 * Cloud Event Management を開始するには、**「Cloud Event Management」**をクリックします。

 * 問題の通知をユーザーがいつ受け取るのかを決定するポリシーを作成するには、**「{{site.data.keyword.alertnotificationshort}}」**をクリックします。

 * Cloud Event Management で運用手順書のカタログを管理するには、**「Runbook Automation」**をクリックします。

### Cloud Event Management に関する詳細

Cloud Event Management について詳しくは、IBM Cloud Garage Method の[記事「Cloud Event Management」](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){:external}を参照してください。


## Delivery Pipeline の構成
{: #deliverypipeline}

{{site.data.keyword.deliverypipeline}} は、入力を取得してジョブ (ビルド、テスト、デプロイメントなど) を実行するステージのシーケンスを通して、プロジェクトの継続的デプロイメントを自動化します。

アプリの継続的なビルド、テスト、デプロイメントを自動化するように {{site.data.keyword.deliverypipeline}}を構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「{{site.data.keyword.deliverypipeline}}」**をクリックします。 使用するテンプレートに応じて、使用できるフィールドは異なります。 デフォルトのフィールド値を確認し、必要に応じてそれらの設定を変更します。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「{{site.data.keyword.deliverypipeline}}」**をクリックします。

1. 新しいパイプラインの名前を指定します。
1. パイプラインを使用してユーザー・インターフェースをデプロイするよう計画している場合は、**「アプリケーションの表示メニューでアプリケーションを表示する (Show apps in the VIEW APP  menu)」**チェック・ボックスを選択します。 パイプラインが作成するすべてのアプリケーションが、ツールチェーンの「概要」ページの**「アプリケーションの表示 (View App)」**リストに表示されます。
1. **「統合の作成」**をクリックして、{{site.data.keyword.deliverypipeline}} をツールチェーンに追加します。
1. **「{{site.data.keyword.deliverypipeline}}」**をクリックして、パイプラインを表示し、構成します。 パイプラインの構成の基本を確認するには、『[パイプラインのビルドとデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)』を参照してください。

  GitHub リポジトリー、{{site.data.keyword.ghe_short}} リポジトリー、または Git リポジトリーにコミットがプッシュされるとパイプラインが自動的に実行されるようにしたい場合は、以下のステップを実行します。

   a. パイプラインのステージを定義する前に、ツールチェーン用に GitHub、{{site.data.keyword.ghe_short}}、または {{site.data.keyword.gitrepos}} を構成します。 パイプラインのステージには、リポジトリーの Git URL が必要です。 各パイプライン・ステージは、ツールチェーンと関連付けられた、GitHub リポジトリー、{{site.data.keyword.ghe_short}} リポジトリー、または Git リポジトリーのうち 1 つのみを参照できます。 GitHub の構成手順については、[GitHub](#github) のセクションを参照してください。 Dedicated {{site.data.keyword.ghe_short}} の構成方法については、[{{site.data.keyword.ghe_long}} 概説](/docs/services/ghededicated?topic=ghededicated-getting-started)を参照してください。{{site.data.keyword.gitrepos}} の構成手順については、[{{site.data.keyword.gitrepos}}](#grit) のセクションを参照してください。

   b. Web フックを使用します。 Web フックを使用しない場合、パイプラインは手動でのみ実行できます。 GitHub リポジトリーまたは {{site.data.keyword.ghe_short}} リポジトリーにリンクする場合に Web フックを使用するには、管理特権が必要です。 {{site.data.keyword.gitrepos}} リポジトリーにリンクするには、Master または Owner 特権が必要です。

1. オプション: {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを使用していて、Sauce Labs でアプリのテストを実行したい場合、{{site.data.keyword.deliverypipeline}} を構成して Sauce Labs テスト・ジョブを追加します。 テスト・ジョブの構成手順については、『[パイプラインに SauceLabs テスト・ジョブを構成する](#config_saucelabs)』セクションを参照してください。

### パイプラインに Sauce Labs テスト・ジョブを構成する
{: #config_saucelabs}

パイプラインに Sauce Labs テスト・ジョブを構成する前に、アプリをビルドしてデプロイするためのステージを含む、正常に機能するパイプラインが存在していなければなりません。 また、ツールチェーンに Sauce Labs を構成しておく必要もあります。 Sauce Labs の構成手順については、[Sauce Labs](#saucelabs) のセクションを参照してください。

{{site.data.keyword.deliverypipeline}} を構成して Sauce Labs テスト・ジョブを追加します。

1. アプリのテスト・バージョンをデプロイするステージがない場合は作成します。
1. そのステージで、デプロイ・ジョブの後にテスト・ジョブを追加します。 これらのジョブは、同じステージに置くことにより、同じ環境プロパティーのセットにアクセスできるようになります。   
  ![テスト・ジョブ](images/toolchain_test_job.png)

1. ステージを構成します。 **「環境プロパティー (ENVIRONMENT PROPERTIES)」**タブで、CF_APP_NAME プロパティーを作成します。

  Sauce Labs ユーザー名とアクセス・キーは、テスト・ジョブ・スクリプトでは SAUCE_USERNAME と SAUCE_ACCESS_KEY の各環境変数として使用可能です。 テストを記述する際は、これらの環境変数を使用して Sauce Labs の認証を受ける必要があります。
  {: tip}

1. デプロイ・ジョブを構成します。 「デプロイ・スクリプト」**フィールドに、コマンド `export CF_APP_NAME="$CF_APP"` を含めます。** このコマンドは、アプリ名を環境プロパティーとしてエクスポートします。
1. テスト・ジョブを構成します。 

  **「サービス・インスタンス」**、**「ターゲット」**、**「組織」**、**「スペース」**の各フィールドには、使用中の Sauce Labs のユーザー名、地域、組織、スペースが取り込まれます。
  {: tip}

  a. テスター・タイプには、**Sauce Labs** を選択します。

  b. サービス・インスタンスでは、ツールチェーンに Sauce Labs を構成したときに使用した Sauce Labs のユーザー名を選択します。

   ツールチェーン用に Sauce Labs を構成したときに使用したユーザー名およびアクセス・キーを表示するには、**「構成」**をクリックします。
   {: tip}

  c. **「テスト実行コマンド (Test Execution Command)」**フィールドに、テストに必要な依存関係をインストールしてテストを実行するコマンドを入力します。 例えば、Node.js アプリの場合、次のようなコマンドを入力します。
     ```
     npm install
     node_modules/grunt-cli/bin/grunt test:sauce:parallel
     ```

    d. テスト・ジョブ・ログでテストのレポートを確認する場合は、**「テスト・レポートを有効にする (Enable Test Report)」**チェック・ボックスにチェックマークを付け、「テスト結果のファイル・パターン (Test Result File Pattern)」を `test/*.xml` に設定します。

1. **「保存」**をクリックします。 パイプラインが実行されるときには必ず Sauce Labs のテストが実行されます。

### Delivery Pipeline に関する詳細

{{site.data.keyword.deliverypipeline}} について詳しくは、[パイプラインでの作業](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline-working)および IBM Cloud Garage Method の[記事「Delivery Pipeline article」](https://www.ibm.com/cloud/garage/content/deliver/tool_delivery_pipeline/){:external}を参照するか、これらのチュートリアルを始めてください。

  * [パイプラインの作成](https://www.ibm.com/cloud/garage/tutorials/create-a-pipeline){:external}

  * [「Develop a Cloud Foundry app」ツールチェーンを使用した初めてのツールチェーンの作成と使用](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}


## {{site.data.keyword.deliverypipeline}} Private Worker の構成
{: #privateworker}

{{site.data.keyword.deliverypipeline}} Private Worker は、{{site.data.keyword.deliverypipeline}} ワークロードを独立して実行する 1 つ以上のプライベート・ワーカーと接続します。

{{site.data.keyword.deliverypipeline}} Private Worker ツール統合を構成して、ツールチェーン内のパイプラインでプライベート・ワーカーを使用できるようにします。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「{{site.data.keyword.deliverypipeline}} Private Worker」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「{{site.data.keyword.deliverypipeline}} Private Worker」**をクリックします。

1. ツール統合の名前を入力します。この名前は、パイプライン・ステージの**「ワーカー」**タブで、プライベート・ワーカーのプールを識別します。
1. サービス ID の API キーを入力して、1 つ以上のプライベート・ワーカーが作業を検索できる作業キューへのアクセスを認証します。サービス ID API キーがない場合は、**「作成」** をクリックして、このプライベート・ワーカー用の API キーを生成します。
1. **「統合の作成」**をクリックします。
1. ツールチェーンから**「{{site.data.keyword.deliverypipeline}} Private Worker」**をクリックして、このサービス ID に関連付けられた API キーを使用して登録されたすべてのワーカーのリストを表示します。


## DevOps Insights の追加
{: #dra}

{{site.data.keyword.DRA_full}} は、単体テスト、機能テスト、およびコード・カバレッジ・ツールからの結果を収集して分析し、コードがデプロイメント・プロセスの指定されたゲートで事前定義の基準を満たすかどうかを判断します。 コードが基準を満たしていない、または基準を超えていない場合、リスク回避のために、デプロイメントが停止されます。 {{site.data.keyword.DRA_short}} を、継続的デリバリー環境のセーフティー・ネットとして、または品質標準の実装および改善のための手段として使用することができます。

 このツール統合は {{site.data.keyword.Bluemix_notm}} Public でのみ使用可能です。 これは事前構成されているため、構成パラメーターは必要ありません。 このツール統合を再構成することはできません。
 {: tip}

{{site.data.keyword.DRA_short}} を追加し、デプロイメントをモニタリングしてリリース前にリスクを洗い出すことで、{{site.data.keyword.Bluemix_notm}} のコードの品質を維持し、向上させることができます。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「{{site.data.keyword.DRA_short}}」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「{{site.data.keyword.DRA_short}}」**をクリックします。

1. **「統合の作成」**をクリックします。
1. **「{{site.data.keyword.DRA_short}}」**をクリックし、開始手順 (基準の作成、パイプラインへの基準の接続、パイプラインの実行) を完了します。

### DevOps Insights に関する詳細

{{site.data.keyword.DRA_short}} について詳しくは、IBM Cloud Garage Method の[記事「{{site.data.keyword.DRA_short}}」](https://www.ibm.com/cloud/garage/content/learn/tool_devops_insights/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [「Cloud Foundry アプリの開発とテスト」ツールチェーンの使用](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:external}

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンの使用](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}

  * [Explore {{site.data.keyword.DRA_full}}](https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights){:external}


## Eclipse Orion Web IDE の追加
{: #webide}

Eclipse Orion {{site.data.keyword.webide}} は、ソース管理タスクを作成、編集、実行、デバッグ、完了できる Web ベースの統合環境です。 編集から実行、送信、そしてデプロイまで、シームレスに行うことができます。

 このツール統合は事前構成済みです。 構成パラメーターは不要で、再構成することはできません。
 {: tip}

ソース管理タスクを完了するには、次の手順で Eclipse Orion {{site.data.keyword.webide}} ツール統合を追加します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Eclipse Orion {{site.data.keyword.webide}}」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「Eclipse Orion {{site.data.keyword.webide}}」**をクリックします。

1. **「統合の作成」**をクリックします。
1. **「Eclipse Orion {{site.data.keyword.webide}}」**をクリックします。 ワークスペースに GitHub または {{site.data.keyword.ghe_short}} のリポジトリーが事前に取り込まれています。 現行のツールチェーンと関連付けられているリポジトリーは強調表示されます。

### Eclipse Orion Web IDE に関する詳細

Eclipse Orion {{site.data.keyword.webide}} の詳細については、『[Eclipse Orion {{site.data.keyword.webide}} でのコード編集](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide)』を参照してください。 IBM Cloud Garage Method の[記事「Eclipse Orion {{site.data.keyword.webide}}」](https://www.ibm.com/cloud/garage/content/code/tool_eclipse_orion_web_ide/){:external}もお読みになれます。以下のチュートリアルを参照して、Eclipse Orion {{site.data.keyword.webide}} を使用してください。

  * [「Develop a Cloud Foundry app」ツールチェーンを使用した初めてのツールチェーンの作成と使用](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンの使用](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}


## Git Repos and Issue Tracking の構成
{: #grit}

{{site.data.keyword.gitrepos}} ツール統合は、GitLab Community Edition (Git リポジトリー用の Web ベースのホスティング・サービス) をベースにしています。 リポジトリーのローカルとリモートの両方のコピーを持つことができます。 詳しくは、[{{site.data.keyword.gitrepos}}](https://us-south.git.cloud.ibm.com/help){:external}を参照してください。

ツールチェーンの作成時に {{site.data.keyword.gitrepos}} を構成する場合は、以下の手順に従います。    

1. 「構成可能な統合」セクションで**「Git Repos and Issue Tracking」**をクリックします。
1. Git リポジトリーのデフォルト・ターゲット・ロケーションを確認します。 これらのリポジトリーは、サンプル・リポジトリーのクローンです。 必要に応じて、ターゲット・リポジトリーの名前を変更します。

ツールチェーンがあり、そのツールチェーン内の Git リポジトリーを {{site.data.keyword.gitrepos}} に移行する場合は、以下のステップを実行します。

ここで説明する手順は、{{site.data.keyword.gitrepos}} に移行する Git リポジトリーが既に含まれているツールチェーンに適用されます。 ツールチェーンにさまざまなタイプの Git リポジトリーを追加する方法については、[GitHub の構成](#github)、[{{site.data.keyword.Bluemix_notm}} Dedicated での GitHub Enterprise および GitHub Issues の構成](#configghe)、[GitLab の構成](#gitlab)の各セクションを参照してください。
{: tip}

1. DevOps ダッシュボードの「ツールチェーン」ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。
1. **「ツールの追加」**をクリックします。
1. 「ツール統合」セクションで**「Git Repos and Issue Tracking」**をクリックします。
1. Git リポジトリーのコピーを作成する場合は、リポジトリーのタイプとして**「クローンを作成する (Clone)」**をクリックします。 新規リポジトリー名と、ソース・リポジトリーの URL を入力します。
1. 問題のトラッキングに Issues を使用する場合は、**「Issues を使用可能にする (Enable Issues)」**チェック・ボックスにチェック・マークを付けます。
1. コミットに対するタグおよびコメントと、コミットで参照される問題に対するラベルおよびコメントを作成することによって、コード変更のデプロイメントをトラッキングしたい場合は、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 詳しくは、[Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external} を参照してください。
1. **「統合の作成」**をクリックします。

Git リポジトリーのクローンを作成したら、ツールチェーンから削除できます。
{: tip}

既存のツールチェーンに {{site.data.keyword.gitrepos}} を追加する場合は、以下の手順に従います。    

1. DevOps ダッシュボードの「ツールチェーン」ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。
1. **「ツールの追加」**をクリックします。
1. 「ツール統合」セクションで**「Git Repos and Issue Tracking」**をクリックします。
1. リポジトリー・タイプを選択します。     

  a. 空のリポジトリーを作成する場合は、リポジトリーのタイプとして**「新規 (New)」**をクリックし、リポジトリー名を入力します。    
  b. マージ要求を通して変更内容を提供できるように Git リポジトリーをフォークする場合は、リポジトリーのタイプとして**「フォーク (Fork)」**をクリックします。 ソース・リポジトリーの URL を入力します。    
  c. Git リポジトリーのコピーを作成する場合は、リポジトリーのタイプとして**「クローンを作成する (Clone)」**をクリックします。 新規リポジトリー名と、ソース・リポジトリーの URL を入力します。     
  d. 既存の Git リポジトリーを使用する場合は、リポジトリーのタイプとして**「既存」**をクリックします。 URL を入力します。    

1. 問題のトラッキングに Issues を使用する場合は、**「Issues を使用可能にする (Enable Issues)」**チェック・ボックスにチェック・マークを付けます。
1. コミットに対するタグおよびコメントと、コミットで参照される問題に対するラベルおよびコメントを作成することによって、コード変更のデプロイメントをトラッキングしたい場合は、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 詳しくは、[Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external} を参照してください。
1. **「統合の作成」**をクリックします。
1. 作業対象の Git リポジトリーのカードをクリックします。 プロジェクト概要のページが開きます。    

リンクしようとしているリポジトリーに対する Master または Owner 特権をお持ちでない場合、Web フックを使用できないので統合は制限されます。 リポジトリーにコミットがプッシュされたときにパイプラインが自動的に実行されるようにするには、Web フックが必要です。 Web フックがない場合、パイプラインを手動で開始する必要があります。
{: tip}

### Git Repos and Issue Tracking に関する詳細

{{site.data.keyword.gitrepos}} について詳しくは、IBM Cloud Garage Method の[記事「{{site.data.keyword.gitrepos}}: Social coding hosted by IBM」](https://www.ibm.com/cloud/garage/content/code/tool_git_repos_and_issue_tracking/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [「Develop a Cloud Foundry app」ツールチェーンを使用した初めてのツールチェーンの作成と使用](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}


## GitHub の構成
{: #github}

GitHub は、Git リポジトリーの Web ベースのホスティング・サービスです。 リポジトリーのローカルとリモートの両方のコピーを持つことができるので、共同作業が容易になります。

{{site.data.keyword.ghe_short}} は、オンプレミス型の Web ベースの Git リポジトリー・ホスティング・サービスです。

GitHub Issues は、作業と計画のすべてを 1 つの場所に保持するトラッキング・ツールです。 これは、ユーザーが重要タスクに注力できるようにユーザーの開発リポジトリーと統合されます。

GitHub.com または会社の {{site.data.keyword.ghe_short}} インスタンスの新規または既存のリポジトリーでソース・コードを管理できるように、ツールチェーン内の 1 つのツール統合として GitHub を構成できます。 Wiki、問題のトラッキング、プル要求を介してソーシャル・コーディングに参加します。

ツールチェーンの作成時にこのツール統合を構成する場合は、次の手順を実行します。

1. GitHub リポジトリーにソース・コードを格納している場合は、「構成可能な統合」セクションで**「GitHub」**をクリックします。 {{site.data.keyword.Bluemix_notm}} Public でこのツール統合を構成しており、GitHub へのアクセスを {{site.data.keyword.Bluemix_notm}} に許可していない場合は、**「許可」**をクリックして GitHub Web サイトに移動します。 アクティブな GitHub セッションがない場合は、ログインするよう求められます。 **「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。 アクティブな GitHub セッションはあるものの、最近パスワードを入力していない場合は、確認のために GitHub パスワードの入力を求められることがあります。
1. 独自の {{site.data.keyword.ghe_short}} サーバー上でリポジトリーを使用している場合は、「構成可能な統合」セクションで**「カスタム・サーバーの追加」**をクリックします。

 ネットワークを介して {{site.data.keyword.Bluemix_notm}} Dedicated 環境からターゲット Git サーバーにアクセスできる必要があります。 パブリック・インターネット上で GitHub サーバーを使用できない場合や、パブリック・ドメイン・ネーム・サーバー (DNS) 上でホスト名が解決しない場合は、[サポート・チケットを開きます](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_support#support-ticket)。 サポート・チケットを使用して、ネットワーク経路を開く要求や、DNS 設定を更新する要求を送信できます。
 {: important}

 カスタム GitHub サーバーのタイトルを入力し、サーバーのルート URL を指定します。 個人用アクセス・トークンを入力してから、**「カスタム統合の保存 (Save custom integration)」**をクリックします。

  個人用アクセス・トークンがない場合は作成できます。

     a. 任意の GitHub ページで、プロファイル・アイコンをクリックしてから**「設定」**をクリックします。

     b. サイドバーで、**「個人用アクセス・トークン (Personal access tokens)」**をクリックします。

     c. **「新規トークンの生成 (Generate new token)」**をクリックします。

     d. トークンの説明を追加します。

     e. **「リポジトリー (repo)」**と**「ユーザー」**の各チェック・ボックスを選択し、個人用トークンのアクセス権限を定義します。

     f. **「トークンの生成 (Generate token)」**をクリックします。

     g. アクセス・トークンを安全な場所またはパスワード管理アプリにコピーします。 セキュリティー上の理由から、ページを閉じた後はトークンを確認できなくなります。

1. GitHub リポジトリーのデフォルトのターゲット・リポジトリーの場所を確認します。 これらのリポジトリーは、サンプル・リポジトリーのクローンです。 必要に応じて、ターゲット・リポジトリーの名前を変更します。![デフォルトのターゲット・リポジトリーの場所](images/toolchain_github_config.png)

既存のツールチェーンにツール統合を追加する場合は、以下の手順に従います。

1. DevOps ダッシュボードの「ツールチェーン」ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。
1. **「ツールの追加」**をクリックします。
1. 「ツール統合」セクションで、**「GitHub」**をクリックします。
1. 使用する GitHub サーバーをクリックします。
1. 既存の GitHub または {{site.data.keyword.ghe_short}} リポジトリーを使用する場合は、リポジトリーのタイプとして**「既存」**をクリックし、URL を入力します。
1. 新しい GitHub または {{site.data.keyword.ghe_short}} リポジトリーを使用する場合は、そのリポジトリーに付ける名前を入力し、複製またはフォークするリポジトリーの URL を入力し、リポジトリー・タイプを次のように選択します。

 a. 空のリポジトリーを作成する場合は、**「新規」**をクリックします。

 b. GitHub または {{site.data.keyword.ghe_short}} リポジトリーのコピーを作成する場合は、**「クローンを作成する (Clone)」**をクリックします。

 c. GitHub または {{site.data.keyword.ghe_short}} リポジトリーをフォークし、プル・リクエストで変更内容を提供できるようにする場合は、**「フォーク (Fork)」**をクリックします。

1. アップグレードしたアカウントを持つ GitHub.com ユーザーの場合、または {{site.data.keyword.ghe_short}} サーバーを選択してこのサーバー上に新規のプライベート・リポジトリーを作成する場合は、**「このリポジトリーをプライベートにする (Make this repository private)」**チェック・ボックスを選択します。
1. 問題のトラッキングに GitHub Issues を使用する場合は、**「GitHub Issues を使用可能にする (Enable GitHub Issues)」**チェック・ボックスにチェック・マークを付けます。
1. コミットに対するタグおよびコメントと、コミットで参照される問題に対するラベルおよびコメントを作成することによって、コード変更のデプロイメントをトラッキングしたい場合は、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 詳しくは、[Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external} を参照してください。
1. **「統合の作成」**をクリックします。
1. 作業対象の GitHub または {{site.data.keyword.ghe_short}} リポジトリーのカードをクリックします。 選択したリポジトリーに応じて、GitHub Web サイトか会社の {{site.data.keyword.ghe_short}} リポジトリーが開きます。ここで、リポジトリーのコンテンツを表示できます。

  Eclipse Orion {{site.data.keyword.webide}} の統合ソース・コード管理ツールを使用して、GitHub リポジトリーを編集し、ワークスペースからアプリをデプロイすることができます。
  {: tip}

1. GitHub Issues を使用可能にした場合、**「GitHub Issues」**をクリックして開きます。 ツールチェーンに複数の GitHub または {{site.data.keyword.ghe_short}} リポジトリーが含まれれている場合でも、GitHub Issues のこのインスタンスをツールチェーン全体に使用できます。

リンクしようとしているリポジトリーに対する管理特権をお持ちでない場合、Web フックを使用できないので統合は制限されます。 リポジトリーにコミットがプッシュされたときにパイプラインが自動的に実行されるようにするには、Web フックが必要です。 Web フックがない場合、パイプラインを手動で開始する必要があります。
{: tip}

### GitHub に関する詳細

GitHub について詳しくは、IBM Cloud Garage Method の[記事「GitHub」](https://www.ibm.com/cloud/garage/content/code/tool_github/){:external}と[記事「GitHub Issues」](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){:external}を参照するか、以下のチュートリアルを始めてください。

 * [「Develop and test a Cloud Foundry app」ツールチェーンを使用する](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:external}
 * [「GitHub と Jenkins による開発リスク分析」ツールチェーンを使用した導入の品質確保](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:external}

 * [カスタム・ツールチェーンの作成](https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain){:external}


## {{site.data.keyword.Bluemix_notm}} Dedicated での GitHub Enterprise および GitHub Issues の構成
{: #configghe}

 ここで説明する手順は、{{site.data.keyword.Bluemix_notm}} Dedicated for {{site.data.keyword.ghe_short}} に適用されます。 独自の管理版の {{site.data.keyword.ghe_short}} を使用している場合、内部手順によっては一部のステップが異なることがあります。
 {: important}

{{site.data.keyword.ghe_long}} は、オンプレミス型の Web ベースの Git リポジトリー・ホスティング・サービスです。 Dedicated {{site.data.keyword.ghe_short}} は {{site.data.keyword.Bluemix_notm}} Dedicated ユーザー専用です。 GitHub Issues は、作業と計画を 1 つの場所に保持するトラッキング・ツールです。 これは、ユーザーが重要タスクに注力できるようにユーザーの開発リポジトリーと統合されます。 Dedicated {{site.data.keyword.ghe_short}} と GitHub Issues について詳しくは、[{{site.data.keyword.ghe_long}} 概説](/docs/services/ghededicated?topic=ghededicated-getting-started)と IBM Cloud Garage Method の[記事「GitHub Issues」](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){:external}を参照してください。

{{site.data.keyword.ghe_short}}  をツールチェーン内の 1 つのツール統合として構成して、会社の [{{site.data.keyword.Bluemix_notm}} Dedicated](/docs/dedicated?topic=dedicated-dedicated#dedicated) インスタンス内でソース・コードを管理できるようにすることができます。

1. ツールチェーンの作成時にこのツール統合を構成する場合は、次の手順を実行します。

 a. Dedicated {{site.data.keyword.ghe_short}} に初めてログインするときは、まずその前に LDAP を使用して会社のユーザー・レジストリーから自分のユーザー ID を {{site.data.keyword.Bluemix_notm}} Dedicated インスタンスに追加するよう、会社の地域管理者に依頼してください。 {{site.data.keyword.ghe_short}} アカウントのセットアップについては、[{{site.data.keyword.ghe_long}} の概説](/docs/services/ghededicated?topic=ghededicated-getting-started)を参照してください。

 b. 「構成可能な統合」セクションで**「{{site.data.keyword.ghe_short}}」**をクリックします。    

 c. 新しい {{site.data.keyword.ghe_short}} リポジトリーのデフォルト名を確認します。 必要に応じて、新しいリポジトリーの名前を変更してください。 次のイメージは、サンプル・リポジトリーのクローンとして作成されたリポジトリーの例を示しています。 既存のリポジトリーを使用することも、新しいリポジトリーを使用することもできます。 新しいリポジトリーを使用する場合は、空のリポジトリーを作成するか、リポジトリーのクローンを作成するか、リポジトリーをフォークすることができます。
 ![デフォルトのリポジトリーの場所](images/toolchain_ghe_config.png)

1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「{{site.data.keyword.ghe_short}}」**をクリックします。

1. 既存の {{site.data.keyword.ghe_short}} リポジトリーを使用する場合は、そのリポジトリーの URL を入力します。 リポジトリー・タイプには、**「既存」**をクリックします。
1. 新しい {{site.data.keyword.ghe_short}} リポジトリーを使用する場合は、そのリポジトリーに付ける名前を入力し、複製またはフォークするリポジトリーの URL を入力し、リポジトリー・タイプを次のように選択します。

 a. 空のリポジトリーを作成する場合は、**「新規」**をクリックします。

 b. リポジトリーのコピーを作成する場合は、**「クローンを作成する (Clone)」**をクリックします。

 c. リポジトリーをフォークし、プル・リクエストで変更内容を提供できるようにする場合は、**「フォーク (Fork)」**をクリックします。

1. 問題のトラッキングに GitHub Issues を使用する場合は、**「GitHub Issues を使用可能にする (Enable GitHub Issues)」**チェック・ボックスにチェック・マークを付けます。
1. **「統合の作成」**をクリックします。
1. 作業対象の {{site.data.keyword.ghe_short}} リポジトリーのカードをクリックします。 会社の {{site.data.keyword.ghe_short}} リポジトリーが開きます。

  Eclipse Orion {{site.data.keyword.webide}} の統合ソース・コード管理ツールを使用して、{{site.data.keyword.ghe_short}} リポジトリーを編集し、ワークスペースからアプリをデプロイすることができます。
  {: tip}

1. GitHub Issues を使用可能にした場合、**「GitHub Issues」**をクリックします。 ツールチェーンに複数の GitHub リポジトリーが含まれれている場合でも、GitHub Issues のこのインスタンスをツールチェーン全体に使用できます。    

リンクしようとしているリポジトリーに対する管理特権をお持ちでない場合、Web フックを使用できないので統合は制限されます。 リポジトリーにコミットがプッシュされたときにパイプラインが自動的に実行されるようにするには、Web フックが必要です。 Web フックがない場合、パイプラインを手動で開始する必要があります。
{: tip}


## GitLab の構成
{: #gitlab}

GitLab は、Git リポジトリーの Web ベースのホスティング・サービスです。 リポジトリーのローカルとリモートの両方のコピーを持つことができるので、共同作業が容易になります。

GitLab.com または会社の GitLab インスタンスの新規または既存のリポジトリーでソース・コードを管理できるように、ツールチェーン内の 1 つのツール統合として GitLab を構成できます。 Wiki、問題のトラッキング、マージ要求を介してソーシャル・コーディングに参加します。

ツールチェーンの作成時にこのツール統合を構成する場合は、次の手順を実行します。

1. GitLab リポジトリーにソース・コードを格納している場合は、「構成可能な統合」セクションで**「GitLab」**をクリックします。 {{site.data.keyword.Bluemix_notm}} Public でこのツール統合を構成しており、GitLab へのアクセスを {{site.data.keyword.Bluemix_notm}} に許可していない場合は、**「許可」**をクリックして GitLab Web サイトに移動します。 アクティブな GitLab セッションがない場合は、ログインするよう求められます。 **「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitLab アカウントにアクセスできるようにします。 アクティブな GitLab セッションはあるものの、最近パスワードを入力していない場合は、確認のために GitLab パスワードの入力を求められることがあります。
1. 独自の GitLab サーバー上でリポジトリーを使用している場合は、「構成可能な統合」セクションで**「カスタム・サーバーの追加」**をクリックします。

 ネットワークを介して {{site.data.keyword.Bluemix_notm}} Dedicated 環境からターゲット GitLab サーバーにアクセスできる必要があります。
 {: tip}

 カスタム GitLab サーバーのタイトルを入力し、サーバーのルート URL を指定します。 個人用アクセス・トークンを入力してから、**「カスタム統合の保存 (Save custom integration)」**をクリックします。

  個人用アクセス・トークンがない場合は作成できます。

     a. 任意の GitLab ページで、プロファイル・アイコンをクリックしてから**「設定」**をクリックします。

     b. 「アクセス・トークン (Access Tokens)」ページで、個人用アクセス・トークンの作成対象のアプリケーションの名前を入力します。

     c. オプション。 アクセス・トークンの有効期限日を選択します。

     d. **「api」**チェック・ボックスを選択し、個人用トークンのアクセス権限を定義します。

     e. **「個人用アクセス・トークンの作成 (Create personal access token)」**をクリックします。

     f. アクセス・トークンを安全な場所またはパスワード管理アプリにコピーします。 セキュリティー上の理由から、ページを閉じた後はトークンを確認できなくなります。

1. GitLab リポジトリーのデフォルトのターゲット・リポジトリーの場所を確認します。 これらのリポジトリーは、サンプル・リポジトリーのクローンです。 必要に応じて、ターゲット・リポジトリーの名前を変更します。

既存のツールチェーンにツール統合を追加する場合は、以下の手順に従います。

1. DevOps ダッシュボードの「ツールチェーン」ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。
1. **「ツールの追加」**をクリックします。
1. 「ツール統合」セクションで**「GitLab」**をクリックします。
1. 使用する GitLab サーバーをクリックします。
1. 既存の GitLab リポジトリーを使用する場合は、リポジトリーのタイプとして**「既存」**をクリックし、URL を入力します。
1. 新しい GitLab リポジトリーを使用する場合は、そのリポジトリーに付ける名前を入力し、複製またはフォークするリポジトリーの URL を入力し、リポジトリー・タイプを次のように選択します。

 a. 空のリポジトリーを作成する場合は、**「新規」**をクリックします。

 b. GitLab リポジトリーのコピーを作成する場合は、**「クローンを作成する (Clone)」**をクリックします。

 c. GitLab リポジトリーをフォークし、マージ要求で変更内容を提供できるようにする場合は、**「フォーク (Fork)」**をクリックします。

1. サーバー上にパブリック・リポジトリーを作成する場合は、**「このリポジトリーをプライベートにする (Make this repository private)」**チェック・ボックスをクリアします。
1. 問題のトラッキングに GitLab Issues を使用する場合は、**「GitLab Issues を使用可能にする (Enable GitLab Issues)」**チェック・ボックスにチェック・マークを付けます。
1. コミットに対するタグおよびコメントと、コミットで参照される問題に対するラベルおよびコメントを作成することによって、コード変更のデプロイメントをトラッキングしたい場合は、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 詳しくは、[Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external} を参照してください。
1. **「統合の作成」**をクリックします。
1. 作業対象の GitLab リポジトリーのカードをクリックします。 選択したリポジトリーに応じて、GitLab Web サイトか会社の GitLab リポジトリーが開きます。ここで、リポジトリーのコンテンツを表示できます。

  Eclipse Orion {{site.data.keyword.webide}} の統合ソース・コード管理ツールを使用して、GitLab リポジトリーを編集し、ワークスペースからアプリをデプロイすることができます。
  {: tip}

1. GitLab Issues を使用可能にした場合、**「GitLab Issues」**をクリックして開きます。 ツールチェーンに複数の GitLab リポジトリーが含まれれている場合でも、GitLab Issues のこのインスタンスをツールチェーン全体に使用できます。

リンクしようとしているリポジトリーに対する所有者またはマスター特権がない場合は、Web フックを使用できないので統合は制限されます。 リポジトリーにコミットがプッシュされたときにパイプラインが自動的に実行されるようにするには、Web フックが必要です。 Web フックがない場合、パイプラインを手動で開始する必要があります。
{: tip}

### GitLab に関する詳細

GitLab について詳しくは、IBM Cloud Garage Method の[記事「GitLab」](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){:external}を参照してください。


## Jenkins の構成
{: #jenkins}

Jenkins は、ソフトウェアを継続的にビルドおよびテストする、サーバー・ベースのオープン・ソースのツールであり、継続的統合および継続的デリバリーの履行をサポートします。

Jenkins ツール統合を作成する前に、Jenkins サーバーを用意する必要があります。
{: important}

Jenkins ツール統合を使用すれば、Jenkins ジョブ通知をツールチェーン内の他のツール (Slack や PagerDuty など) に送信できます。 デプロイメントでコードをトレースするために、デプロイメント・メッセージを Git コミットや関連 Git/JIRA 問題に追加できます。 また、デプロイメントを「ツールチェーン接続」ページに表示することもできます。 テスト結果を {{site.data.keyword.DRA_short}} に送信し、自動化された品質ゲートを追加し、デプロイメント・リスクをトラッキングすることができます。

アプリの継続的なビルド、テスト、デプロイメントを自動化するために Jenkins を構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Jenkins」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「Jenkins」**をクリックします。

1. ツールチェーン内の Jenkins カードでこのツール統合に対して表示したい名前を入力します。
1. ツールチェーンから Jenkins カードをクリックしたときに開くようにしたい Jenkins サーバーの URL を入力します。
1. 生成されたツールチェーン Web フックをコピーします。
1. Jenkins サーバーで、以下のステップを実行します。

 a. [IBM Cloud DevOps プラグインをインストールします](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Installingtheplugin){:external}。

 b. [ツールチェーンに通知するように Jenkins を構成します](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Notifyingtoolchains){:external}。

 c. Jenkins ツール統合の「統合の構成 (Configure the Integration)」ページに戻ります。

1. **「統合の作成」**をクリックします。
1. ツールチェーンから、**「Jenkins」**をクリックして Jenkins サーバーを表示します。  

### Jenkins に関する詳細

Jenkins について詳しくは、IBM Cloud Garage Method の[記事「Jenkins」](https://www.ibm.com/cloud/garage/content/deliver/tool_jenkins/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [「GitHub と Jenkins による開発リスク分析」ツールチェーンを使用した導入の品質確保](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:external}

## JIRA の構成
{: #jira}

JIRA は、ユーザーのソフトウェアに関連する問題およびバグを追跡するツールです。 Jenkins または {{site.data.keyword.deliverypipeline}} によってデプロイメントが実行されるたびに、JIRA ツール統合はプロジェクトの問題を更新します。 JIRA ツール統合で問題をトラッキングするには、コミット・メッセージ内で JIRA Smart Commits を使用する必要があります。 JIRA Smart Commits について詳しくは、[Using Smart Commits](https://confluence.atlassian.com/fisheye/using-smart-commits-298976812.html){:external} を参照してください。

品質コードの計画、追跡、および配信のために、JIRA を構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「JIRA」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「JIRA」**をクリックします。

1. JIRA プロジェクトがあり、それに接続したい場合、JIRA タイプとして**「既存」**をクリックします。

 a. JIRA プロジェクトの JIRA プロジェクト・キーを入力します。 プロジェクト・キーは JIRA プロジェクトの URL に含まれています。

 b. JIRA インスタンスのベース API URL を入力します。 API URL は、JIRA インスタンスのヘッダーで見つけることができます。 **「管理」**アイコンをクリックし、**「システム」**をクリックします。

 c. プライベート JIRA インスタンスに接続しているか、パブリック JIRA インスタンスからトレーサビリティー情報を受け取る場合は、JIRA のユーザー名とパスワードを入力します。

 d. 参照される問題に対するラベルおよびコメントを作成することによってプロジェクトに関するコード変更のデプロイメントをトラッキングするには、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 JIRA Smart Commit を使用して、GitHub コミットの JIRA 問題を参照するようにしてください。 このオプションが選択されていない場合、JIRA ツール統合はすべてのコミットを無視します。

1. JIRA プロジェクトを作成する場合、JIRA タイプとして**「新規 (New)」**を選択します。

 a. 新規プロジェクトに使用する JIRA プロジェクト・キーを入力します。 このキーは、プロジェクト URL 内で固有 ID として使用されます。

 b. JIRA プロジェクトの名前を入力します。

 c. JIRA インスタンスのベース API URL を入力します。 API URL は、JIRA インスタンスのヘッダーで見つけることができます。 **「管理」**アイコンをクリックし、**「システム」**をクリックします。

 d. このプロジェクトに使用したい JIRA プロジェクト・リーダーのユーザー名を入力します。 JIRA プロジェクト・リーダーとして指定される個人は、JIRA でプロジェクト・リーダー許可を持っている必要があります。

 e. JIRA のこのインスタンスの管理者のユーザー名を入力します。

 f. JIRA のこのインスタンスの管理者のパスワードを入力します。

 g. 参照される問題に対するラベルおよびコメントを作成することによってプロジェクトに関するコード変更のデプロイメントをトラッキングするには、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 JIRA Smart Commit を使用して、GitHub コミットの JIRA 問題を参照するようにしてください。 このオプションが選択されていない場合、JIRA ツール統合はすべてのコミットを無視します。

1. **「統合の作成」**をクリックします。
1. ツールチェーンから**「JIRA」**をクリックして、接続する JIRA プロジェクトのダッシュボードを表示します。

### JIRA に関する詳細

JIRA について詳しくは、IBM Cloud Garage Method の[記事「JIRA」](https://www.ibm.com/cloud/garage/content/code/tool_jira/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [「Developer Insights and Team Dynamics with GitHub and JIRA」ツールチェーンを使用して分析情報を得る](https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain){:external}


## Nexus の構成
{: #nexus}

ビルド成果物を Nexus リポジトリーに保管するように Nexus リポジトリー・マネージャーを構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Nexus」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「Nexus」**をクリックします。

1. Nexus ツール統合のこのインスタンスの名前を入力します。
1. ツールチェーンから Nexus カードをクリックしたときに開くようにしたい Nexus リポジトリーの URL を入力します。
1. 接続先にするリポジトリーのタイプを選択します。
1. **「npm レジストリー」**を選択した場合は、以下のステップを実行します。

 a. レジストリーと関連付けられた E メール・アドレスを入力します。

 b. レジストリーと関連付けられた認証トークンを入力します。

 c. Nexus サーバー上のプライベート・レジストリーである Nexus リリース・リポジトリーの URL を入力します。

 d. 複数のパブリックおよびプライベート npm レジストリーを結合するために使用する Mirror または Public レジストリーの URL を入力します。 例えば、この URL は、プライベート・レジストリーと、npm グローバル・レジストリーのキャッシュの両方にアクセスできる、Nexus サーバー上の仮想レジストリーの URL であることができます。

1. **「Maven リポジトリー」**を選択した場合は、以下のステップを実行します。

 a. リポジトリーと関連付けられたユーザー ID を入力します。

 b. リポジトリーと関連付けられたパスワードを入力します。

 c. Nexus サーバー上のプライベート・リリース・リポジトリーである Nexus リリース・リポジトリーの URL を入力します。

 d. Nexus サーバー上のプライベート・スナップショット・リポジトリーである Nexus スナップショット・リポジトリーの URL を入力します。

 e. 複数のパブリックおよびプライベート Maven リポジトリーを結合するために使用する Mirror または Public リポジトリーの URL を入力します。 例えば、この URL は、プライベート・リポジトリーと、Maven 中央リポジトリーのキャッシュの両方にアクセスできる、Nexus サーバー上の仮想リポジトリーの URL であることができます。

1. **「統合の作成」**をクリックします。
1. 作業対象の Nexus リポジトリーのカードをツールチェーンからクリックします。 Nexus の Web サイトが開きます。そこでリポジトリーの内容を表示できます。
1. オプション: {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを使用していて、Nexus を npm と共に使用してアプリをビルドしたい場合、パイプラインを構成して npm ビルド・ジョブを追加します。 ビルド・ジョブの構成手順については、『[パイプラインに Nexus npm ビルド・ジョブを構成する](#config_nexus_npm)』セクションを参照してください。
1. オプション: {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを使用していて、Nexus を Maven と共に使用してアプリをビルドしたい場合、パイプラインを構成して Maven ビルド・ジョブを追加します。 ビルド・ジョブの構成手順については、『[パイプラインに Nexus Maven ビルド・ジョブを構成する](#config_nexus_maven)』セクションを参照してください。

### パイプラインに Nexus npm ビルド・ジョブを構成する
{: #config_nexus_npm}

パイプラインに npm ビルド・ジョブを構成する前に、ビルド SCM リポジトリーを入力として使用できる作業パイプラインが存在している必要があり、また、ツールチェーンに Nexus を構成しておく必要もあります。 Nexus の構成手順については、[Nexus](#nexus) のセクションを参照してください。

{{site.data.keyword.deliverypipeline}} を構成して npm ビルド・ジョブを追加します。

1. ステージを作成し、入力を適切な SCM リポジトリーに設定します。
1. このステージでビルド・ジョブを追加します。
1. ビルド・ジョブを構成します。
  ![npm ビルド・ジョブ](images/nexus_npm_job.png)

  a. ビルダー・タイプに**「NPM ビルド (NPM Build)」**を選択します。

  b. Nexus ツール統合の複数インスタンスを構成した場合、npm ビルド・ジョブを構成する対象にしたい Nexus ツール統合の名前を入力します。

  c. ツール統合タイプに**「Nexus」**を選択します。

  d. ビルド・コマンドには、npm モジュールのビルドまたはレジストリーへのモジュールのパブリッシュを行うコマンドを入力します。 次の例は、モジュールのビルドまたはパブリッシュのいずれかを行うコマンドを示します。
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  **ヒント:** レジストリーへの接続に使用した URL およびユーザー資格情報は、Nexus ツール統合の構成設定で見つけることができます。

  e. ビルド・ジョブが Nexus レジストリーへのパブリッシュを行い、かつ、ノード・モジュール・バージョンのフォーマットが `x.y.z-SNAPSHOT.w` である場合、**「スナップショット・モジュール・バージョンのインクリメント (Increment snapshot module version)」**チェック・ボックスにチェック・マークを付けます。 ビルド・ジョブは、モジュール・バージョンを自動的に更新した後で、Nexus レジストリーにパブリッシュします。 ビルド・ジョブは、npm レジストリーおよびローカル `package.json` ファイルから最高バージョンのモジュールを選択し、semver を使用してモジュール・バージョンを増やします。 ビルド・ジョブは、変更を SCM リポジトリーに配信しません。

1. **「保存」**をクリックします。 パイプラインが実行されると、このビルド・ジョブは Nexus ツール統合からの構成情報を使用して npm レジストリーに接続します。

### パイプラインに Nexus Maven ビルド・ジョブを構成する
{: #config_nexus_maven}

パイプラインに Maven ビルド・ジョブを構成する前に、ビルド SCM リポジトリーを入力として使用できる作業パイプラインが存在している必要があり、また、ツールチェーンに Nexus を構成しておく必要もあります。 Nexus の構成手順については、[Nexus](#nexus) のセクションを参照してください。

{{site.data.keyword.deliverypipeline}} を構成して Maven ビルド・ジョブを追加します。

1. ステージを作成し、入力を適切な SCM リポジトリーに設定します。
1. このステージでビルド・ジョブを追加します。
1. ビルド・ジョブを構成します。
  ![Maven ビルド・ジョブ](images/nexus_maven_job.png)

  a. ビルダー・タイプに**「Maven ビルド (Maven Build)」**を選択します。

  b. Nexus ツール統合の複数インスタンスを構成した場合、Maven ビルド・ジョブを構成する対象にしたい Nexus ツール統合の名前を入力します。

  c. ツール統合タイプに**「Nexus」**を選択します。

  d. ビルド・コマンドには、Maven モジュールのビルドまたはスナップショット・レジストリーへのモジュールのパブリッシュを行うコマンドを入力します。 次の例は、モジュールのビルドまたはパブリッシュのいずれかを行うコマンドを示します。
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  レジストリーへの接続に使用した URL およびユーザー資格情報は、Nexus ツール統合の構成設定で見つけることができます。
  {: tip}

1. **「保存」**をクリックします。 パイプラインが実行されると、このビルド・ジョブは Nexus ツール統合からの構成情報を使用して Maven リポジトリーに接続します。

### Nexus に関する詳細

Nexus について詳しくは、IBM Cloud Garage Method の[記事「Nexus」](https://www.ibm.com/cloud/garage/content/deliver/tool_nexus/){:external}を参照してください。


## カスタム・ツール (その他のツール) の構成
{: #othertool}

チームがツールチェーン統合リストに含まれていないツールを使用する場合、カスタム・ツールを統合できます。

カスタム・ツールを構成して、ツールチェーン内の他のツールとともに機能し、チームで使用できるようにします。

1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「その他のツール (Other Tool)」**をクリックします。

1. ツール名を入力します。
1. ツールに最も密接に関連したライフサイクル・フェーズを選択します。 この選択によって、「概要」ページでツールがリストされるカテゴリーが決まります。
1. アイコン URL を追加します。 このアイコンがツール統合のカードに表示されます。
1. 資料 URL を追加します。
1. ツール・インスタンス名を指定します。 例えば、My Team Tool と指定します。
1. ツール・インスタンスの URL を追加します。 ツール統合のカードがクリックされると、この URL が開きます。
1. ツールの説明を追加します。
1. (上級) 必要に応じて、さらにプロパティーを追加します。 例えば、ご使用のツールをツールチェーンの他のツールと統合するために必要な情報または属性をリストします。  
1. **「統合の作成」**をクリックします。

### カスタム・ツールに関する詳細

カスタム・ツールについて詳しくは、[Introducing custom tool integration for {{site.data.keyword.Bluemix_notm}} toolchains](https://www.ibm.com/cloud/blog/introducing-custom-tool-integration-for-bluemix-toolchains/){:external} を参照するか、以下のチュートリアルを始めてください。

  * [ツールチェーンへのカスタム・ツール統合の追加](https://www.ibm.com/cloud/garage/tutorials/add-a-custom-tool-integration-to-a-toolchain){:external}


## PagerDuty の構成
{: #pagerduty}

PagerDuty は、複数のモニタリング・システムのデータを単一のビューに統合します。 問題が発生すると、PagerDuty によって、その時点で問題の修正に最適なチーム・メンバーに確実に通知が送信されます。 そのチーム・メンバーが問題に応答しない場合、次の担当者または運用管理者に問題を転送するようにエスカレーションを構成できます。

パイプライン・ステージで障害が発生したときに通知を送信するように PagerDuty を構成して、問題を迅速に修正してダウン時間を削減できるようにします。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「PagerDuty」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「PagerDuty」**をクリックします。

1. API キーを使用してアカウント・レベルで PagerDuty を統合する場合は、**「アカウント」**をクリックします。

 a. PagerDuty アカウントの API アクセス・キーを入力します。 PagerDuty アカウントをお持ちでない場合、[登録して取得](https://www.pagerduty.com/sign-up/){:external}してください。キーを確認する方法については、[Generating an API Key](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){:external} を参照してください。

 b. PagerDuty サービスの名前を入力します。

 c. PagerDuty の 1 次連絡先の E メール・アドレスを入力します。

 d. PagerDuty の 1 次連絡先の電話番号を入力します。

1. 統合キーを使用してサービス・レベルで PagerDuty を統合する場合は、**「サービス」**をクリックします。

 a. アラートの通知先となる PagerDuty サービスの URL を入力します。

 b. PagerDuty の統合キーを入力します。 PagerDuty サービス・ページの「統合」セクションで、このキーを見つけるか作成できます。

1. **「統合の作成」**をクリックします。
1. **「PagerDuty」**をクリックして pagerduty.com にアクセスします。 ツールチェーンに対してこのツール統合を構成したときに指定した PagerDuty サービスに関連付けられているイベントを表示できます。

### PagerDuty に関する詳細

PagerDuty について詳しくは、IBM Cloud Garage Method の[記事「PagerDuty」](https://www.ibm.com/cloud/garage/content/manage/tool_pagerduty/){:external}を参照するか、以下のチュートリアルと Garage Method 支持者のコースを始めてください。

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンの使用](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}

  * [Become a Garage Method advocate](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:external}


## Rational Team Concert の構成
{: #rationalteamconcert}

IBM Rational Team Concert&trade; は、反復計画、変更管理、障害追跡、ソース管理、ビルド自動化、レポート作成などの開発タスクを統合したチーム・コラボレーション・ツールです。

開発環境で DevOps 手法と継続的デリバリーを実践するために Rational Team Concert を構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Rational Team Concert」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「Rational Team Concert」**をクリックします。

1. ツールチェーンから Rational Team Concert カードをクリックしたときに開くようにする、Rational Team Concert サーバーの URL を入力します。
1. Rational Team Concert サーバーにアクセスするために使用するユーザー ID を入力します。
1. Rational Team Concert サーバーにアクセスするために使用するパスワードを入力します。
1. ツールチェーンに追加したい Rational Team Concert プロジェクト・エリアがある場合は、以下の手順に従います。

 a. **「プロジェクト・エリア・タイプ (Project Area type)」**リストで、**「既存のプロジェクト・エリア (Existing project area)」**を選択します。

 b. ツールチェーンに追加するプロジェクト・エリアの名前を入力します。

1. ツールチェーンに追加する Rational Team Concert プロジェクト・エリアを作成する場合は、以下の手順に従います。

 a. **「プロジェクト・エリア・タイプ (Project Area type)」**リストで、**「新規プロジェクト・エリア (New project area)」**を選択します。

 b. ツールチェーンに追加する新規プロジェクト・エリアの名前を入力します。

 c. プロジェクトの作成に使用する Rational Team Concert プロセス・テンプレートの名前を入力します。

1. 作業項目に対してタグとコメントを作成してプロジェクトのコード変更のデプロイメントを追跡するには、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。
1. **「統合の作成」**をクリックします。
1. ツールチェーンから**「Rational Team Concert」**をクリックして、構成した Rational Team Concert ダッシュボードを開きます。

### Rational Team Concert に関する詳細

Rational Team Concert について詳しくは、IBM Cloud Garage Method の[記事「IBM Rational Team Concert」](https://www.ibm.com/cloud/garage/content/think/tool_rtc/){:external}を参照してください。


## Sauce Labs の構成
{: #saucelabs}

Sauce Labs は、機能単体テストを実行します。 {{site.data.keyword.deliverypipeline}} 内のテスト・ジョブとして Sauce Labs テスト・スイートが構成されている場合、そのテスト・スイートは、継続的デリバリー・プロセスの一環として、Web アプリまたはモバイル・アプリに対するテストを実行できます。 これらのテストは、誤ったコードがデプロイされるのを防ぐためのゲートとして機能することで、プロジェクトに対して非常に有益なフロー制御を提供します。

 このツール統合は {{site.data.keyword.Bluemix_notm}} Public でのみ使用可能です。
 {: tip}

複数のオペレーティング・システムおよびブラウザーで自動化された機能テストを実行するように Sauce Labs を構成することによって、ユーザーがどのように Web サイトやアプリケーションを使用するのかをエミュレートできます。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Sauce Labs」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「Sauce Labs」**をクリックします。

1. Sauce Labs アカウントと関連付けられたユーザー名を入力します。 [ Sauce Labs アカウント・ページにあるウェルカム・メッセージでユーザー名を確認できます](https://app.saucelabs.com/user-settings){:external}。
1. Sauce Labs アカウントのアクセス・キーを入力します。 [Sauce Labs アカウント・ページでキーを確認できます](https://app.saucelabs.com/user-settings){:external}。
1. **「統合の作成」**をクリックします。
1. **「Sauce Labs」**をクリックして saucelabs.com に移動し、ツールチェーンのテスト・アクティビティーを表示します。

 Sauce Labs テスト・ジョブを {{site.data.keyword.deliverypipeline}} に追加した場合、サービス・インスタンスを選択できます。 パイプラインにテスト・ジョブを構成する手順については、『[パイプラインに Sauce Labs テスト・ジョブを構成する](#config_saucelabs)』セクションを参照してください。
 {: tip}

### Sauce Labs に関する詳細

Sauce Labs について詳しくは、IBM Cloud Garage Method の[記事「Sauce Labs」](https://www.ibm.com/cloud/garage/content/deliver/tool_sauce_labs/){:external}を参照するか、以下のチュートリアルを始めてください。

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンの使用](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}


## Slack の構成
{: #slack}

パブリック Slack チャネルに送信される通知は、チームの全員が見ることができます。 投稿したコンテンツの責任は投稿者が負います。
{: important}

Slack は、クラウド・ベースのリアルタイムでのメッセージングおよび通知のシステムです。 Slack が提供する永続的なチャットは、E メールの代わりに使用できる対話性に優れたチームのコラボレーション手段になります。 専用チャネルまたは作業に直接関連する一連のチャネルで、チームと連絡を取ることができます。 さらに、2 人以上のメンバー間で、チャネルやダイレクト・メッセージを使用して、ファイルとイメージを共有することもできます。 ダイレクト・メッセージとチャネルでの通信は、検索できるように保存されます。

テストやデプロイのアクティビティーなどのツールチェーンに関する通知をツール統合から受信するように Slack を構成します。

1. ツールチェーン作成時にこのツール統合を構成する場合は、「構成可能な統合」セクションで**「Slack」**をクリックします。
1. 既存のツールチェーンにこのツール統合を追加する場合は、DevOps ダッシュボードの「ツールチェーン」ページでそのツールチェーンをクリックして「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで、**「Slack」**をクリックします。

1. 着信 Web フックとして Slack によって生成された Slack Web フック URL を入力します。 Slack チャネルがツール統合からツールチェーンに関する通知を受け取るためには Slack Web フック URL が必要です。 Web フックを作成または確認する方法については、[Incoming Webhooks](https://api.slack.com/incoming-webhooks){:external} を参照してください。

 Slack チャネルがツール統合からツールチェーンについての通知を受け取れるようにするために API キーを使用する場合は、代わりに Web フックを使用するように構成を更新する必要があります。
 {: tip}

1. 通知を送信する Slack チャネルの名前を入力します。 このチャネルは存在していなければならず、Slack チームでアクティブである必要があります。
1. Slack チームの URL ホスト名を入力します。これは、チーム URL 内の `.slack.com` の前にある語または句です。 例えば、チーム URL が `https://team.slack.com` の場合、ホスト名は `team` です。
1. **「統合の作成」**をクリックします。

 指定した Slack チャネルおよびチームに到達できない場合、Slack カードに `Setup Failed` エラーが表示されます。 `Setup Failed` メッセージの上に移動し、**「再構成 (Reconfigure)」**をクリックしてください。 Slack Web フック URL、Slack チャネル、および Slack チームの URL ホスト名に、有効な構成パラメーターを使用していることを確認してください。 必要に応じて設定を更新し、**「統合の保存」**をクリックします。
 {: tip}

1. **「Slack」**をクリックします。 構成した Slack チャネルでツールチェーンのアクティビティーをすべて表示できます。

### Slack に関する詳細

Slack について詳しくは、IBM Cloud Garage Method の[記事「Slack」](https://www.ibm.com/cloud/garage/content/culture/tool_slack/){:external}を参照するか、以下のチュートリアルと Garage Method 支持者のコースを始めてください。

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンの使用](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}

  * [Become a Garage Method advocate](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:external}


## SonarQube の構成
{: #sonarqube}

SonarQube は、ソース・コードの全体的な正常性と品質の概要を提供し、新しいコード内で見つかった問題を強調表示します。 コード・アナライザーは、20 を超えるコーディング言語において、NULL ポインター間接参照などの注意を要するバグ、論理エラー、リソース・リークを検出します。

以下のようにして、ソース・コードの品質を継続的に分析および測定するように SonarQube を構成します。

1. DevOps ダッシュボードから、**「ツールチェーン」**をクリックします。 SonarQube を追加するツールチェーンをクリックします。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。 次に、**「概要」**をクリックします。  

 a. **「ツールの追加」**をクリックします。

 b. 「ツール統合」セクションで**「SonarQube」**をクリックします。

1. SonarQube ツール統合のこのインスタンスの名前を入力します。
1. ツールチェーンから SonarQube カードをクリックしたときに開くようにしたい SonarQube インスタンスの URL を入力します。
1. オプション: SonarQube サーバーへの接続に使用するユーザー名を入力します。

 ユーザー名の指定が必要なのは、SonarQube サーバーへの接続にパスワードを使用する場合のみです。 接続に認証トークンを使用する場合は、このフィールドを空のままにしてください。
 {: tip}

1. SonarQube サーバーへの接続に使用するパスワードまたは認証トークンを入力します。
1. **「統合の作成」**をクリックします。
1. ツールチェーンから**「SonarQube」**をクリックして、接続する SonarQube インスタンスのダッシュボードを表示します。

### SonarQube に関する詳細

SonarQube について詳しくは、IBM Cloud Garage Method の[記事「SonarQube」](https://www.ibm.com/cloud/garage/content/learn/tool_sonarqube/){:external}を参照してください。 
