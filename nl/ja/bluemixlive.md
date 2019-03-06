---



copyright:
  years: 2015，2019
lastupdated: "2019-2-1"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}


Node.js アプリケーションを作成する場合、{{site.data.keyword.Bluemix}} Live Sync を使用すると、{{site.data.keyword.Bluemix_notm}} 上のアプリケーション・インスタンスを素早く更新して開発することができ、手動で再デプロイする必要がありません。   
{: shortdesc}

変更を行うと、実行中の {{site.data.keyword.Bluemix_notm}} アプリケーションでその変更を即時に確認できます。 {{site.data.keyword.Bluemix_notm}} Live Sync は、
<!--from both the command line and --> Eclipse Orion Web IDE (Web IDE) で動作します。 {{site.data.keyword.Bluemix_notm}} Live Sync を使用すると、Node.js で作成されたアプリケーションをデバッグすることができます。  

{{site.data.keyword.Bluemix_notm}} Live Sync は、2 つのフィーチャーで構成されています。
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**Live Edit**

{{site.data.keyword.Bluemix_notm}} 上で実行される Node.js アプリケーションを編集し、ご使用のブラウザーですぐにテストすることができます。 Web IDE 内で加えた変更はすべて、直ちに当該アプリケーションのファイル・システムに伝搬されます。  

**Debug**  

Node.js アプリケーションが Live Edit モードになっているとき、シェルでそのアプリケーションにアクセスしてデバッグすることができます。 Node Inspector というデバッガーを使用して、コードの動的な編集、ブレークポイントの挿入、コードのステップスルー、ランタイムの再始動などを行うことができます。  


##Live Edit
{: #live-edit}

{{site.data.keyword.Bluemix_notm}} 上で実行する Node.js アプリケーションを作成する場合、{{site.data.keyword.Bluemix_notm}} Live Sync の Live Edit フィーチャーを使用することにより、アプリケーション・インスタンスを素早く更新できます。 Live Edit は Web IDE 内でのみ使用できます。 Live Edit を使用して、再デプロイせずにデスクトップ版と同様の開発を行うことができます。

Live Edit がサポートされるのは Node.js アプリケーションのみです。

Eclipse Orion Web IDE (Web IDE) の実行バーで、**「Live Edit」**をクリックします。

![実行バーに表示された Live Edit のイメージ](images/bluemix-live-sync-light.png)

Live Edit を使用すれば、{{site.data.keyword.Bluemix_notm}} で実行される Node.js アプリケーションに対する変更を迅速にプレビューできます。 Live Edit をオンにしてコードを更新すると、変更を加えてからほんの数秒で、Web アプリケーションのブラウザー・ウィンドウを最新表示して、変更が反映されたことを確認できます。

{{site.data.keyword.Bluemix_notm}} Live Sync の Live Edit フィーチャーの使用に関するチュートリアルについては、[{{site.data.keyword.Bluemix_notm}} Live Sync を使用したアプリの開発、デバッグ、デプロイ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window} を参照してください。

Web IDE 内でファイルを変更すると、それらのファイルは {{site.data.keyword.Bluemix_notm}} 上のアプリケーション・インスタンスに自動的に再デプロイされます。 Node アプリケーションの再始動が必要な場合は、実行バーにある**「再始動」**ボタンをクリックします。

{{site.data.keyword.Bluemix_notm}} Live Sync の Live Edit フィーチャーの使用時に、より一貫性のある動作をさせるためには、256 MB の追加メモリーが必要であり、メモリーが追加されます。
{: tip}

## {{site.data.keyword.Bluemix_notm}} Live Debug
{: #live-debug}

{{site.data.keyword.Bluemix_notm}} Live Sync Debug では、[Node Inspector ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/node-inspector/node-inspector){:new_window} を使用してデバッグ・フィーチャーが提供されます。 デバッガーを使用可能にするには、バージョン 4 の Node を使用する必要があります。これより後のバージョンの Node.js には Node Inspector が組み込まれていないからです。

対象となる Node.js アプリにおいて {{site.data.keyword.Bluemix_notm}} Live Edit が使用可能になっていれば、{{site.data.keyword.Bluemix_notm}} Live Debug にアクセスできます。  

Debug を使用すると、アプリが {{site.data.keyword.Bluemix_notm}} で実行されている間に、コードの動的な編集、ブレークポイントの挿入、コードのステップスルー、ランタイムの再始動などを行うことができます。 {{site.data.keyword.Bluemix_notm}} の多数のサービスのリストから選択しながら、アプリを段階的に素早く開発できます。

{{site.data.keyword.Bluemix_notm}} Live Debug には、以下のフィーチャーが含まれています。

* アプリケーション・ランタイム制御
* [Node Inspector ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/node-inspector/node-inspector){:new_window} を使用したデバッグ
* シェル・アクセス

### アプリケーション・ランタイム制御 {: #app-runtime}

アプリケーション・ランタイム制御により、Debug を使用してアプリの開始時の状態を検査することができます。 この機能は、始動時に障害が起こるアプリをトラブルシューティングする際に役立ちます。

アプリの開発中、次のアクションから選択できます。

* アプリの再始動を迅速に実行する
* アプリのコードが実行される前にアプリを一時停止する

ログインすると、{{site.data.keyword.Bluemix_notm}} Live Debug ページが開きます。

### Debug {: #debug}

**制限:** Google Chrome または Node 4 が必要です。

Debug には、以下の機能が含まれています。  
* アプリ・コードにブレークポイントを設定して、特定の行で実行を一時停止する。
  ブレークポイントはメインプログラムではサポートされませんが、エントリー・ポイントではサポートされます。
  {: tip}
* ブレークポイントの条件を編集して、特定の基準が満たされた場合にのみ実行を一時停止する。
* ローカル変数やフィールドの状態を検査する。
* `console.log()` 呼び出しからのデバッグ出力を即座に表示する。 cf ログをモニターするより、このアクションの方が迅速です。
* 組み込みソース・コード・エディターを使用して、実行中のアプリ・コードに即時 (ただし一時的な) 変更を行う。

### Shell {: #shell}

このツールは、アプリが実行されているコンテナーへのシェル・アクセスを提供します。 この端末を使用することにより、診断シェル・コマンドをリモート側で実行してアプリを管理することができます。 すべてのバージョンの Node.js で Shell フィーチャーがサポートされます。

標準的な Linux コマンド (**top**、**ps**、**kill** など) を使用するインスタンス内におけるメモリーと CPU の使用量をモニターします。

### {{site.data.keyword.Bluemix_notm}} Live Debug を使用可能にするためのアプリの構成 {: #configure_app_debug}

1. {{site.data.keyword.Bluemix_notm}} Live Debugger は Node Inspector を使用します。 Node バージョン 4 を使用する必要があります。ビルドパックがアプリの start コマンドを検出できるようにする必要もあります。 start コマンドは、manifest.yml ファイル内に設定されるのではなく、ビルドパックによって自動検出される必要があります。

   {{site.data.keyword.Bluemix_notm}} Live Debug をサポートする `package.json` ファイルを以下に示します。

  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. メモリーを増やします。  

    a. アプリの `manifest.yml` ファイルで、メモリー属性に指定されている値に 128 MB 以上を追加します。

{{site.data.keyword.Bluemix_notm}} Live Debug がインストールされたら、デバッグ・ツールを使用することができます。

アプリをプッシュしてから `https://_app-host.mybluemix.net_/bluemix-debug/manage` をブラウズして、{{site.data.keyword.Bluemix_notm}} Debug のユーザー・インターフェースにアクセスします。 認証するよう求められたら、IBM ID のユーザー名とパスワードか、ワンタイム・パスコードを入力します。    

Debugger の初期化には 1 分程度かかることがあります。
{: tip}

### アプリの構成の復元と {{site.data.keyword.Bluemix_notm}} Live Debug の無効化 {: #restore_live_debug}

1. アプリの元の Node.js バージョン、start コマンド、メモリー値を復元します。

2. アプリをプッシュします。
