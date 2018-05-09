---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Continuous Delivery 概説
{: #cd_getting_started}

アプリケーションのビルドとデプロイメントを自動化するオープン・ツールチェーンが組み込まれた {{site.data.keyword.contdelivery_full}} を使用することによって、DevOps アプローチを取り入れることができます。 開発、デプロイメント、運用の作業をサポートする単純なデプロイメント・ツールチェーンを作成することから始めることができます。
{: shortdesc}

{{site.data.keyword.Bluemix_notm}} カタログから {{site.data.keyword.contdelivery_short}} を選択してそのインスタンスを作成した後、テンプレートから継続的デリバリー・ツールチェーンを作成するか、または既存のツールチェーンを使用して作業することができます。
 ![Continuous Delivery ウェルカム・ページ](images/cd_landing_page2.png)

* テンプレートから継続的デリバリー・ツールチェーンを作成して構成するには、**[「ここから開始 します」](#starting_from_a_toolchain_template)**をクリックします。ツールチェーンは、パイプラインのプランニング、開発、デプロイと、アプリケーションの管理のためのツールを統合したものです。 ツールチェーンに対していつでもツールを追加したり削除したりできます。
* ツールチェーンが既にある場合は、「ツールチェーン・テンプレートから開始 (Start from a toolchain template)」セクションで、**「ツールチェーンを表示 (View your toolchains)」**をクリックします。 ツールチェーンの扱いについて詳しくは、[ツールチェーンの使用](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}を参照してください。

##{{site.data.keyword.contdelivery_short}} の概要
{: #cd_overview}

{{site.data.keyword.contdelivery_short}} は、DevOps プラクティスや業界最高レベルのツールを使用したアプリケーションのビルド、テスト、デリバリーを可能にします。
{:shortdesc}

{{site.data.keyword.contdelivery_short}} サービスは、以下の DevOps ワークフローをサポートします。

 * 統合された DevOps のオープン・[ツールチェーン](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window}を作成して、開発、デプロイメント、および運用の各タスクをサポートするツール統合を可能にできます。

  ツールチェーンとは、アプリケーションを共同で開発、ビルド、デプロイ、テスト、管理するために使用できる統合ツール・セットです。ツールチェーンを使用すると、操作を反復可能にして管理しやすくすることができます。 ツールチェーンには、オープン・ソース・ツール、{{site.data.keyword.Bluemix_notm}} サービス ([{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window} など)、およびサード・パーティー製のツール (GitHub、PagerDuty、Slack など) を含めることができます。 
  
  **注**: {{site.data.keyword.DRA_short}} は米国南部地域でのみ利用可能です。

 * 自動化された[パイプライン](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window}を使用すれば、継続的なデリバリーが可能になります。

  ビルド、単体テスト、デプロイメントなどを自動化します。 最小限の人的介入で、反復可能な方法でビルド、テスト、デプロイします。 いつでも実稼動環境で使用できるよう準備します。

 * [Web ベースの IDE](/docs/services/ContinuousDelivery/web_ide.html){: new_window} を使用して、どこからでもコードを編集してプッシュします。

  GitHub でソース管理のタスクの作成、編集、実行、デバッグ、完成を行えます。 コードの編集から実稼動環境へのデプロイに、シームレスに移ります。 
  
 * IBM がホストする GitLab Community Edition ベースの [Git repository (repos) and issue tracker](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window} を使用して、チームのコラボレーションやソース・コードの管理を行えます。

  コードを保護するきめ細かいアクセス制御を通して Git リポジトリーを管理します。 マージ要求を使用して、コードをレビューし、コラボレーションを向上させます。 Issue Tracker を介して問題を追跡し、アイデアを共有します。 Wiki システム上にプロジェクトを文書化します。


##ツールチェーン・テンプレートから開始 (Starting from a toolchain template)
{: #starting_from_a_toolchain_template}

[テンプレート ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン icon")](https://console.bluemix.net/devops/create){: new_window} から継続的デリバリー・ツールチェーンを作成して構成するには、以下のようにします。

1. **「ツールチェーンの作成 (Create a Toolchain)」**ページで、ツールチェーン・テンプレートをクリックします。
1. 作成しようとしているツールチェーンの図を確認します。 この図は、ツールチェーン内の各ツール統合とそのライフサイクル・フェーズを示しています。

 **ヒント**: 一部のツールチェーン・テンプレートには、同じツール統合の複数のインスタンスが含まれています。 例えば、{{site.data.keyword.Bluemix_notm}} Public の Microservices ツールチェーン・テンプレートには、GitHub の 3 つのインスタンスと Delivery Pipeline の 3 つのインスタンス (3 つのマイクロサービスのそれぞれに対して 1 つずつ) が含まれています。

 次のイメージの図はその例です。 ツールチェーンを作成すると、ツールチェーンを構成する各ツール統合がこの図に表示されます。![ツールチェーンの図](images/toolchain_diagram2.png)
1. ツールチェーン設定のデフォルト情報を確認します。

 * ツールチェーンの名前は、そのツールチェーンを {{site.data.keyword.Bluemix_notm}} 内で識別するためのものです。 別の名前を使用する場合は、ツールチェーンの名前を変更します。
 * ツールチェーンを作成する対象の地域。別の地域を利用する場合は、選択可能な地域のリストから選んでください。
 * ツールチェーンを作成する対象の組織。別の組織を利用する場合は、選択可能な組織のリストから選んでください。
 
1. 「ツール統合 (Tool Integrations)」セクションで、ツールチェーンに構成する各ツール統合を選択します。 いくつかのツール統合は、構成を必要としません。 ツール統合の構成については、[ツール統合の構成](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}を参照してください。
1. **「作成」**をクリックします。 以下のようにいくつかのステップが自動的に実行されて、ツールチェーンがセットアップされます。 セットアップされるツール統合は、どのツールチェーン・テンプレートを選択したのか、また、{{site.data.keyword.Bluemix_notm}} Public と {{site.data.keyword.Bluemix_notm}} Dedicated のどちらを使用しているのかによって異なります。 例えば、Microservices ツールチェーンを {{site.data.keyword.Bluemix_notm}} Public で作成する場合、以下のステップが実行されます。

 * ツールチェーンが作成されます。
 * Delivery Pipeline を構成した場合は、パイプラインが作成されて実行します。
 * Sauce Labs を構成した場合は、パイプラインに Sauce Labs テスト・ジョブを追加するようにツールチェーンがセットアップされます。
 * PagerDuty を構成した場合は、指定した PagerDuty サービスにアラート通知を送信するようにツールチェーンがセットアップされます。
 * Slack を構成した場合は、指定した Slack チャネルにデプロイメント状況に関する通知を送信するようにツールチェーンがセットアップされます。
 * GitHub などのソース・コード・ツール統合を構成した場合、サンプル GitHub リポジトリーが GitHub アカウントに複製されます。
