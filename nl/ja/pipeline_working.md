---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# パイプラインでの作業  
{: #pipeline-working}

ビルドと {{site.data.keyword.Bluemix}} へのデプロイメントを自動化するには、{{site.data.keyword.contdelivery_full}} パイプラインを使用します。
{: shortdesc}

パイプラインでは、いくつかのビルド・タイプから選択できます。 ビルド・スクリプトを指定すれば、
{{site.data.keyword.contdelivery_short}} が実行します。ビルド・システムをセットアップする必要はありません。 1 回クリックするだけで、1 つ以上の {{site.data.keyword.Bluemix_notm}} スペース、Cloud Foundry のパブリック・サーバー、{{site.data.keyword.containerlong}} の Docker コンテナーに自動的にアプリをデプロイできます。

ビルド・ジョブが、アプリのソース・コードを Git リポジトリーからコンパイルしてパッケージします。 ビルド・ジョブは、WAR ファイルや {{site.data.keyword.containerlong_notm}} の Docker コンテナーなど、デプロイ可能な成果物を作成します。 また、ビルド内で単体テストを自動的に実行することができます。 コミットがプッシュされるたびにビルドがトリガーされるように、ビルド・ジョブを設定することができます。

デプロイメント・ジョブは、出力をビルド・ジョブから取得して、{{site.data.keyword.containerlong_notm}} や Cloud Foundry サーバー ({{site.data.keyword.Bluemix_notm}} など) にデプロイします。

1 つ以上の地域やサービスにデプロイできます。 例えば、1 つ以上のサービスを使用して、1 つの地域でテストし、複数の地域で実動にデプロイするよう {{site.data.keyword.deliverypipeline}} をセットアップできます。 

##パイプラインの作成

以下のいずれかの方法を使用してパイプラインを作成できます。

   * [既存の Cloud Foundry アプリケーションからツールチェーンを作成します](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}。 作成されたツールチェーンにはパイプラインが含まれています。

   * 少なくとも 1 つのパイプラインを含む [テンプレートからツールチェーンを作成します](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window}。

   * [既存のツールチェーンに {{site.data.keyword.deliverypipeline}} ツール統合](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window} を追加します。
   
{{site.data.keyword.deliverypipeline}} から、構成を変更したり、ビルドのステータス、デプロイされたアプリ、最近のデプロイメントを確認したり、最新のログとデプロイメントの詳細を参照したり、パイプラインを削除したりすることができます。
