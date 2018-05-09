---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# IBM Confidential プロジェクトからツールチェーンへのアップグレード 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}} は、{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}} へと進化しました。 その変更の一部として、プロジェクトはツールチェーンにアップグレードされます。

プロジェクトをアップグレードする準備ができると、「概要」ページにメッセージが表示されます。 表示されたら、プロジェクトを {{site.data.keyword.Bluemix_notm}} Public のツールチェーンにアップグレードできます。 ツールチェーンには、ソース・コードのための Whitewater {{site.data.keyword.ghe_short}} リポジトリーが含まれます。 Whitewater {{site.data.keyword.ghe_short}} は、IBM 内でソーシャル・コーディングを促進して利用できるように、IBM チームに提供されます。 
{: shortdesc}

**{{site.data.keyword.contdelivery_short}} ツールチェーンは、Whitewater {{site.data.keyword.ghe_short}} で使用する場合は、IBM Confidential 資料として認定されます。** Whitewater {{site.data.keyword.ghe_short}} リポジトリーからの入力を受け取る Delivery Pipeline は、ステージング (YS1) 環境とパブリック (YP) 環境にデプロイできます。

アップグレード中、自分の代わりに Whitewater {{site.data.keyword.ghe_short}} にアクセスすることを {{site.data.keyword.contdelivery_short}} に許可するためのプロンプトが出されます。

## アップグレード後にメンバーを Whitewater {{site.data.keyword.ghe_short}} に追加する

JazzHub でホストされているリポジトリーをプロジェクトで使用している場合は、アップグレード中に新規リポジトリーが Whitewater {{site.data.keyword.ghe_short}} に作成されます。 アップグレードが終わったら、アップグレードを開始したユーザーが、その Whitewater {{site.data.keyword.ghe_short}} リポジトリーにチーム・メンバーを追加する必要があります。また、それらのチーム・メンバーに適切な特権を付与して新規リポジトリーにアクセスできるようにする必要があります。

## トラブルシューティング

パイプライン・デプロイメント・ステージのターゲットを変更しようとすると、偶発的に問題が発生することがあります。 このような問題が発生すると、**「組織」**フィールドと**「スペース」**フィールドにエラーが表示されます。

このような問題が発生するのは、通常、アップグレード中に作成されたパイプラインが以前と同じターゲットに正しくデプロイされるように、パイプラインからターゲットを変更した場合のみです。

ターゲットを変更しようとしてこの問題が発生した場合は、**「組織」**と**「スペース」**の各フィールドの値が設定されるまで、ターゲットを数回切り替えてください。

関連した問題によって、YS1 ターゲットへのデプロイメントが失敗することがあります。このような状況はまれにしか発生しませんが、発生した場合はパイプラインを再実行してください。

IBM DevOps Services チームは、これらの問題を解決するために積極的に取り組んでいます。
