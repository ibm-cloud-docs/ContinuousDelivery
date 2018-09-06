---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 入門チュートリアル
{: #cd_getting_started}

アプリケーションのビルドとデプロイメントを自動化するオープン・ツールチェーンが組み込まれた {{site.data.keyword.contdelivery_full}} を使用することによって、DevOps アプローチを取り入れることができます。 開発、デプロイメント、運用の作業をサポートする単純なデプロイメント・ツールチェーンを作成することから始めることができます。 
{: shortdesc}

##前提条件
{: #cd_prereqs}

テンプレートから継続的デリバリー・ツールチェーンを作成するには、その前に、{{site.data.keyword.contdelivery_short}} のインスタンスを {{site.data.keyword.Bluemix_notm}} カタログから選択して作成する必要があります。ツールチェーンは、パイプラインのプランニング、開発、デプロイと、アプリケーションの管理のためのツールを統合したものです。 ツールチェーンに対していつでもツールを追加したり削除したりできます。 ツールチェーンが既にある場合は、[既存のツールチェーンを表示](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}することができます。ツールチェーンの扱いについて詳しくは、[ツールチェーンの使用](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}を参照してください。

{{site.data.keyword.contdelivery_short}} のインスタンスが既にある場合は、[ツールチェーンを作成 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/create){: new_window} するか、または [既存のツールチェーンを表示](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}することができます。
{: tip}

##ステップ 1: ツールチェーン・テンプレートを選択します
{: #select_a_toolchain_template}

1. **「ツールチェーンの作成」**ページで、[ツールチェーン・テンプレート ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/create){: new_window} をクリックします。
1. 作成しようとしているツールチェーンの図を確認します。 この図は、ツールチェーン内の各ツール統合とそのライフサイクル・フェーズを示しています。

 一部のツールチェーン・テンプレートには、同じツール統合の複数のインスタンスが含まれています。 例えば、{{site.data.keyword.Bluemix_notm}} Public の Microservices ツールチェーン・テンプレートには、GitHub の 3 つのインスタンスと Delivery Pipeline の 3 つのインスタンス (3 つのマイクロサービスのそれぞれに対して 1 つずつ) が含まれています。
 {: tip}

 次のイメージの図はその例です。 ツールチェーンを作成すると、ツールチェーンを構成する各ツール統合がこの図に表示されます。![ツールチェーンの図](images/toolchain_diagram2.png)
 
##ステップ 2: ツールチェーンを作成します 
{: #create_a_toolchain}
 
1. ツールチェーン設定のデフォルト情報を確認します。

 * ツールチェーンの名前は、そのツールチェーンを {{site.data.keyword.Bluemix_notm}} 内で識別するためのものです。 別の名前を使用する場合は、ツールチェーンの名前を変更します。
 * ツールチェーンを作成する対象の地域。 別の地域を利用する場合は、選択可能な地域のリストから選んでください。
 * ツールチェーンを作成する対象のリソース・グループまたは組織。 リンクをクリックして、リソース・グループと組織の選択を切り替えます。別のリソース・グループまたは組織を利用する場合は、選択可能なリソース・グループまたは組織のリストから選んでください。
 
   リソース・グループは米国南部地域でのみ利用可能です。
   {: tip}
 
1. 「ツール統合 (Tool Integrations)」セクションで、ツールチェーンに構成する各ツール統合を選択します。 いくつかのツール統合は、構成を必要としません。 ツール統合の構成については、[ツール統合の構成](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}を参照してください。
1. **「作成」**をクリックします。 以下のようにいくつかのステップが自動的に実行されて、ツールチェーンがセットアップされます。 セットアップされるツール統合は、どのツールチェーン・テンプレートを選択したのか、また、{{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated のどちらを使用しているのかによって異なります。 例えば、Microservices ツールチェーンを {{site.data.keyword.Bluemix_notm}} Public で作成する場合、以下のステップが実行されます。

 * ツールチェーンが作成されます。
 * Delivery Pipeline を構成した場合は、パイプラインが作成されて実行します。
 * Sauce Labs を構成した場合は、パイプラインに Sauce Labs テスト・ジョブを追加するようにツールチェーンがセットアップされます。
 * PagerDuty を構成した場合は、指定した PagerDuty サービスにアラート通知を送信するようにツールチェーンがセットアップされます。
 * Slack を構成した場合は、指定した Slack チャネルにデプロイメント状況に関する通知を送信するようにツールチェーンがセットアップされます。
 * GitHub などのソース・コード・ツール統合を構成した場合、サンプル GitHub リポジトリーが GitHub アカウントに複製されます。

##次のステップ
{: #next_steps}

[IBM&reg; Cloud Garage Method ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage){:new_window} の以下のチュートリアルのいずれかをチェックアウトします。

  * [ 「Develop a Cloud Foundry app」ツールチェーンを使用した初めてのツールチェーンの作成と使用 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン ")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。

  * [Add a toolchain to an app ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}。
