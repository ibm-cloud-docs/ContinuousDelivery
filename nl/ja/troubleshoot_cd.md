---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# {{site.data.keyword.contdelivery_short}} のトラブルシューティング
{: #troubleshoot-cd}

{{site.data.keyword.contdelivery_full}} を使用中に生じる可能性がある一般的な問題として、GitHub の認証、パイプラインの作成、ツール統合の構成、Cloud Foundry に関する問題などが挙げられます。 多くの場合、いくつかの簡単なステップを実行することで、これらの問題から復旧することが可能です。
{:shortdesc}

## GitHub ツール統合をツールチェーンに追加しようとしたのですが、ツール統合が追加されませんでした。
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

GitHub アカウントへのアクセスが {{site.data.keyword.Bluemix_notm}} に許可されるように、GitHub で許可を付与する必要があります。

GitHub ツール統合がツールチェーンに追加されませんでした。
{: tsSymptoms}

{{site.data.keyword.Bluemix_notm}} に GitHub アカウントへのアクセスを許可していない場合、ツール統合はツールチェーンに追加されません。
{: tsCauses}

ツールチェーン作成時に GitHub ツール統合を構成している場合、以下の手順に従って GitHub で許可を付与します。
{: tsResolve}

  1. 「構成可能な統合 (Configurable Integrations)」セクションで**「GitHub」**をクリックします。
  1. {{site.data.keyword.Bluemix_notm}} Public でツールチェーンを作成していて、GitHub にアクセスできるよう {{site.data.keyword.Bluemix_notm}} を認可していない場合、**「認可 (Authorize)」**をクリックして GitHub Web サイトに移動します。
  1. アクティブな GitHub セッションがない場合は、ログインするよう求められます。 **「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。

既にツールチェーンが存在している場合は、GitHub ツール統合の構成を更新します。

 1. DevOps ダッシュボードの**「ツールチェーン」**ページで、ツールチェーンをクリックしてその「概要」ページを開きます。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、その後で**「概要」**をクリックします。
 1. GitHub カードで、メニューをクリックし、**「構成」**をクリックします。
 1. {{site.data.keyword.Bluemix_notm}} が GitHub にアクセスすることを許可するよう構成設定を更新します。 **「認可 (Authorize)」**をクリックして GitHub Web サイトに移動します。 アクティブな GitHub セッションがない場合は、ログインするよう求められます。 **「アプリケーションを許可 (Authorize Application)」** をクリックして、{{site.data.keyword.Bluemix_notm}} が GitHub アカウントにアクセスできるようにします。
 1. 設定の更新が完了したら、**「統合の保存」**をクリックします。
 

## ある地域のツールチェーンに含まれる {{site.data.keyword.gitrepos}} ツール統合を、別の地域内のツールチェーンで使用できないのはなぜですか?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

{{site.data.keyword.gitrepos}} のインスタンスは、複数の地域をまたいで使用することはできません。

{{site.data.keyword.gitrepos}} ツール統合をツールチェーンに追加しようとすると、次のエラー・メッセージを受け取ります。
{: tsSymptoms}

`リポジトリー URL が無効です。 リポジトリーは {local GitLab URL} にある必要があります。`

ここで、`{local GitLab URL}` は、ツールチェーンが置かれている地域における、{{site.data.keyword.gitrepos}} ツール統合の URL です。
   
{{site.data.keyword.gitrepos}} と {{site.data.keyword.contdelivery_short}} サービスは、共に稼働している地域内で緊密に統合されているため、複数の地域をまたいで {{site.data.keyword.gitrepos}} のインスタンスを使用することはできません。
{: tsCauses}

{{site.data.keyword.gitrepos}} ツール統合を作成する代わりに、汎用 GitLab 統合を作成し、この統合を使用して別の地域にある {{site.data.keyword.gitrepos}} リポジトリーを参照するようにしてください。
{: tsResolve}

1. DevOps ダッシュボードの「ツールチェーン」ページで、この統合の追加先となるツールチェーンをクリックします。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックし、**「概要」**をクリックします。
1. **「ツールの追加」**をクリックします。
1. 「ツール統合」セクションで**「GitLab」**をクリックします。
1. 使用する GitLab サーバーをクリックします。 アクセスしようとしているリポジトリーがある GitLab サーバーが、このリストに表示されていない場合は、カスタム・サーバーを追加します。

 a. **「カスタム・サーバーの追加」**をクリックします。

 b. サーバーの名前を入力します。 このサーバー名は、使用可能な GitLab サーバーのリストに表示されます。
 
 c. カスタム GitLab サーバーのルート URL を入力します。
 
 d. カスタム GitLab サーバーの個人用アクセス・トークンを入力します。 個人用アクセス・トークンがない場合は、[それを作成します](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)。
 
 e. **「カスタム統合の保存」**をクリックします。
 
1. 既存の GitLab リポジトリーを使用する場合は、リポジトリーのタイプとして**「既存」**をクリックし、URL を入力します。
1. 新しい GitLab リポジトリーを使用する場合は、そのリポジトリーに付ける名前を入力し、複製またはフォークするリポジトリーの URL を入力し、リポジトリー・タイプを次のように選択します。

 a. 空のリポジトリーを作成する場合は、**「新規」**をクリックします。

 b. GitLab リポジトリーのコピーを作成する場合は、**「クローンを作成する (Clone)」**をクリックします。

 c. GitLab リポジトリーをフォークし、マージ要求で変更内容を提供できるようにする場合は、**「フォーク (Fork)」**をクリックします。

1. サーバー上にパブリック・リポジトリーを作成する場合は、**「このリポジトリーをプライベートにする (Make this repository private)」**チェック・ボックスをクリアします。
1. 問題のトラッキングに GitLab Issues を使用する場合は、**「GitLab Issues を使用可能にする (Enable GitLab Issues)」**チェック・ボックスにチェック・マークを付けます。
1. コミットに対するタグおよびコメントと、コミットで参照される問題に対するラベルおよびコメントを作成することによって、コード変更のデプロイメントをトラッキングしたい場合は、**「コード変更のデプロイメントを追跡する (Track deployment of code changes)」**チェック・ボックスにチェック・マークを付けます。 詳しくは、[Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external} を参照してください。
1. **「統合の作成」**をクリックします。

GitLab ツール統合の構成について詳しくは、[GitLab の構成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)を参照してください。


## 別の地域でプライベート・リポジトリーを使用するテンプレートからツールチェーンを作成できないのはなぜですか?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

使用するツールチェーン・テンプレートは、プライベート {{site.data.keyword.gitrepos}} リポジトリーを参照します。

{{site.data.keyword.gitrepos}} は地域固有のものです。 テンプレートからツールチェーンを作成しようとしているときに、プライベート・リポジトリーの配置先ではない地域をターゲットとして指定した場合、Git 統合セットアップが失敗します。
{: tsSymptoms}
   
特定の地域でツールチェーンに {{site.data.keyword.gitrepos}} リポジトリーを追加すると、IBM ID が、その地域内の GitLab へのアクセスを可能にする GitLab ユーザー名にマップされます。 GitLab ユーザー名がどの地域でも同じに見えるとしても、地域ごとに別個の GitLab がインストールされるため、地域ごとに別個の GitLab ユーザーが関連付けられます。 GitLab ユーザー名が同じに見える場合でも、他の地域の GitLab ユーザーへのアクセス権限が、ツールチェーンに自動的に付与されることはありません。
{: tsCauses}

{{site.data.keyword.gitrepos}} リポジトリーをパブリックに設定することで、他の {{site.data.keyword.Bluemix_notm}} 地域を含め、どの場所からもこのリポジトリーにアクセスできるようにします。
{: tsResolve}

リポジトリーをプライベートに設定しておく必要がある場合は、そこにアクセスするための権限をリポジトリー所有者が付与することができます。これは、ソース・リポジトリーが配置されている GitLab サーバーで[個人用アクセス・トークン](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)を作成することによって行います。 プライベート・リポジトリーへのアクセスが必要になるのは、ツールチェーンの作成中にコンテンツを複製するときに限られます。 有効期限日付を指定して個人用アクセス・トークンを作成することによって、1 日後に期限切れになるように存続期間を制限することができます。 

個人用アクセス・トークンを用意したら、他の地域からリポジトリーにアクセスするための URL を作成できます。 ツール統合の構成中に、**「ソース・リポジトリーの URL」**フィールドで、当該ユーザー名とアクセス・トークンを使用するようにリポジトリー URL を更新します。

`https://user:XXXXXXX@us-south.git.cloud.ibm.com/group/node-hello-world`

ここで、`user` は GitLab ユーザー名、`XXXXXXX` はアクセス・トークン、[`group`](https://us-south.git.cloud.ibm.com/help/user/group/index.md){: external} はリポジトリーが保管されているグループ、`node-hello-world` はリポジトリー名です。

GitLab リポジトリーが GitLab グループ内に配置されていない場合、`group` の値はユーザー名と同じになります。
{: tip}


## https を使用して {{site.data.keyword.gitrepos}} リポジトリーを複製することができないのはなぜですか?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Git 操作を実行するときには個人用アクセス・トークンまたは SSH 鍵を使用する必要があります。

コマンド・ラインから https を使用してリポジトリーをプッシュまたは複製しようとしましたが、正しいパスワードを入力したのに認証できません。
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} が使用するシングル・サインオン・メカニズムは、コマンド・ラインでユーザー名とパスワードを使用する Git 認証をサポートしていません。
{: tsCauses}

複製またはプッシュなどの Git 操作を実行するには、個人用アクセス・トークンまたは SSH 鍵を使用する必要があります。 個人用アクセス・トークンまたは SSH 鍵の作成について詳しくは、[入門チュートリアル](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)を参照してください。
{: tsResolve}

## SSH を使用して {{site.data.keyword.gitrepos}} リポジトリーを複製しようとすると認証を求めるプロンプトが出されるのはなぜですか?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

SSH 秘密鍵の場所または許可に問題がある可能性があります。あるいは、Git コマンド・ラインで、{{site.data.keyword.gitrepos}} での認証のために SSH 秘密鍵を使用していない可能性があります。

{{site.data.keyword.gitrepos}} ユーザー・インターフェースを使用して、SSH 公開鍵を追加しました。 SSH を使用してリポジトリーを複製しようとすると、パスワードまたはセキュリティー・コードの入力を求めるプロンプトが出されるか、あるいは認証の失敗を示すエラー・メッセージが表示されます。
{: tsSymptoms}
   
SSH に関して以下のいずれかの問題があると、認証を求めるプロンプトが出されるか、エラー・メッセージが表示される可能性があります。
{: tsCauses}

* Git コマンド・ラインで、{{site.data.keyword.gitrepos}} での認証のために SSH 秘密鍵を使用していない可能性がある。

* SSH 秘密鍵がデフォルトの場所 ~/.ssh/id_rsa に存在しない可能性がある。

* SSH 秘密鍵に正しい許可 (600) が付与されていない可能性がある。


この問題を解決するには、以下のいずれかの方法を使用します。
{: tsResolve}

* SSH 秘密鍵のデフォルトの場所を使用する場合は、~/.ssh/ フォルダーと ~/.ssh/id_rsa 秘密鍵ファイルに対する許可を確認します。 許可の範囲が広すぎる場合、デフォルトでは、SSH で秘密鍵が使用されません。 ~/.ssh/ フォルダーの許可が 700 に設定されていて、~/.ssh/id_rsa フォルダーの許可が 600 に設定されていることを確認してください。

* 秘密鍵がデフォルトの場所にない場合は、次のコマンドを使用して環境変数で指定してください。

```
  GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git
```

* 接続情報を使用してこの問題をデバッグするには、-v フラグまたは -vvv フラグを `GIT_SSH_COMMAND` 環境変数に追加します。

```
  GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git
```
```
  GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git
```


## E メールを使用してユーザーを GitLab プロジェクトに追加しようとしましたが、そのユーザーは招待を受信しませんでした。 ユーザーをプロジェクトに追加するにはどうすればよいですか?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

ユーザーの E メールで招待がブロックされている可能性があります。

{{site.data.keyword.gitrepos}} にリストされている E メール・アドレスを使用してユーザーを GitLab プロジェクトに招待しましたが、そのユーザーは E メールを受信しませんでした。
{: tsSymptoms}
   
メールが、スパム・フィルターによってユーザーの受信ボックスからブロックされている可能性があります。 
{: tsCauses}

この問題を解決するには、以下のいずれかの方法を使用することができます。
{: tsResolve}

* E メール・スパム・フォルダーを調べて、招待 E メールがスパムとしてマーク付けされていないか確認します。 E メールは noreply@ アドレスから送信されます。 このアドレスからの E メールを許可するように、スパム・フィルターを更新してください。

* ユーザーが制御できない企業のスパム・フィルターによって、E メールがブロックされていないかどうか調べます。 ユーザーに、{{site.data.keyword.gitrepos}} ユーザー・インターフェースにログインしてユーザー ID を送信するよう依頼してください。 そのユーザー ID を使用して、GitLab プロジェクトにユーザーを追加できます。


## 自分が作成しているテンプレートからツールチェーンを作成するときに、パイプラインが適切に作成されないのはなぜですか? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

pipeline.yaml 定義内のエラーが原因で、ジョブやステージなどのリソースがパイプラインから欠落している可能性があります。

自分が作成しているテンプレートからツールチェーンを作成しようとすると、「パイプライン」ページで次のエラー・メッセージが表示されます。
{: tsSymptoms}

`このパイプラインは作成されましたが、ジョブ、ステージ、またはその他のリソースが欠落している可能性があります。 このパイプラインを使用できますが、削除して別のパイプラインを作成することもできます。`

この問題は通常、pipeline.yaml 定義内のエラーが原因で発生します。
{: tsCauses}
   
このエラーをデバッグするには、以下のいずれかの方法を使用することができます。
{: tsResolve}

* パイプライン・ユーザー・インターフェースを使用することで、自分のテンプレートで作成しようとしているパイプラインを複製する、サンプル・パイプラインを作成します。 パイプライン URL に `/yaml` を追加して、類似の pipeline.yaml ファイルを生成してください。これを使用すると違いがはっきりするので、見つけやすくなります。 例えば、次のようにします: `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`。

* ヘッドレス・ツールチェーン作成メカニズムを使用します。 **「ツールチェーンの作成」**ページでデバッガーを開き、`window.Testflags = {nocreate: 1}` 式を評価します。 このモードで**「ツールチェーンの作成」**をクリックすると、ツールチェーンは作成されません。 その代わりに、API に渡された情報がコンソールに返されるので、それを確認することができます。


## Delivery Pipeline を使用して Kubernetes にデプロイしようとしましたが、無効なオブジェクトに関するエラーが発生するのはなぜですか? 
{: troubleshoot-cd-pipeline-kubernetes}
{: troubleshoot}

1.0 パイプライン基本イメージには kubectl v1.14.2 が含まれています。接続先の Kubernetes クラスターがより新しいバージョンの Kubernetes を実行している場合、エラーを受け取ることがあります。 

Delivery Pipeline を使用して Kubernetes にデプロイしようとすると、以下のエラー・メッセージを受け取ります。
{: tsSymptoms}

`error:SchemaeError(io.k8s.api.core.v1.SecretProjection): invalid object doesn't have additional properties`

通常、この問題は、パイプライン基本イメージに含まれる kubectl コマンドのバージョンが、クラスターで実行中の Kubernetes のバージョンと互換性がない場合に発生します。
{: tsCauses}
   
この問題を解決するには、以下のいずれかの方法を使用することができます。
{: tsResolve}

* より新しいバージョンのパイプライン基本イメージを使用してください。これにより、作成時に、現在リリースされているバージョンの kubectl が組み込まれます。最新のバージョンのイメージを指定する方法について詳しくは、[イメージ・バージョンの指定](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline_versioned_base_images#specify_base_image_version)を参照してください。

* パイプライン・ジョブが正しいバージョンの kubectl を実行していることを確認してください。例えば、kubectl v1.14.2 を実行するには、パイプライン・ジョブの先頭に以下の行を追加します。

```
  curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.14.2/bin/linux/amd64/kubectl
  chmod +x ./kubectl
  sudo mv ./kubectl /usr/local/bin/kubectl
```

1.0 パイプライン基本イメージから kubectl v1.14.2 を実行している場合、sudo オプションは使用できません。sudo 行を以下のコマンドに置き換えて、パスに kubectl を追加します。
```
   mkdir ~/.bin && export PATH=~/.bin:$PATH && mv ./kubectl ~/.bin/kubectl 
```

必要となる kubectl の正確なバージョンにアクセスする方法について詳しくは、[Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux){: external} を参照してください。
{: tip}


## ツールチェーン用にツール統合を構成しようとしましたが、構成されませんでした。
{: troubleshoot-tool-integration-error}
{: troubleshoot}

このセットアップ処理中にエラーが発生した場合、または、ツールチェーンとツールとの間の通信が正常に完了しない場合、構成が失敗します。

ツールチェーン用にツール統合を追加して構成した後、セットアップが失敗したことを示すエラー・メッセージが表示されます。
{: tsSymptoms}

ツール統合を追加すると、ツールチェーンはそのツール統合によって表されるツールと通信して、必要なリソースのプロビジョンを行い、それらをツールチェーンと関連付けます。 このセットアップ処理中にエラーが発生した場合、または、ツールチェーンとツールとの間の通信が正常に完了しない場合、ツール統合はエラー状態になります。
{: tsCauses}

 ![Setup failed エラー](images/tool_setup_failed.png)

次のようにして、ツール統合の構成を再試行できます。
{: tsResolve}

1. ツール・カードで `Setup failed` メッセージの上に移動し、**「再構成 (Reconfigure)」**をクリックします。

 ![「再構成」ボタン](images/tool_reconfigure.png)

1. 有効な構成パラメーターを使用していることを確認します。 無効な構成が原因でエラーが起こった場合、例えば `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey` のようなエラー・メッセージが表示されます。 ツール統合の設定を更新し、**「統合の保存」**をクリックします。
1. 通信の問題が原因でエラーが起こった場合、**「統合の保存」**をクリックして再試行します。


## {{site.data.keyword.contdelivery_short}} を Cloud Foundry 組織に追加できないのはなぜですか?
{: troubleshoot-resource_groups}
{: troubleshoot}

Cloud Foundry 組織で {{site.data.keyword.contdelivery_short}} サービスのインスタンスを作成することはできなくなりました。 

Cloud Foundry 組織内のツールチェーンについて、「ツールチェーン」ページに次のメッセージが表示されます。
{: tsSymptoms}

`Continuous Delivery サービスが必要です: サービス機能の使用を妨げられないようにするには、組織にサービスを追加してください。` 

**「サービスの追加 (Add the service)」**をクリックしたときに、Cloud Foundry 組織で {{site.data.keyword.contdelivery_short}} を作成するオプションが表示されません。{{site.data.keyword.contdelivery_short}} は、リソース・グループでのみ作成できます。

サービス・インスタンスの推奨コンテナーとして、リソース・グループが Cloud Foundry に取って代わりました。 ただし、Cloud Foundry 組織内の既存の {{site.data.keyword.contdelivery_short}} インスタンスをサポートするために、引き続き Cloud Foundry 組織でツールチェーンを作成することはできます。
{: tsCauses}

リソース・グループでツールチェーンを再作成してから、Cloud Foundry 組織から元のツールチェーンを削除します。あるいは、既存のツールチェーンを Cloud Foundry 組織からリソース・グループにマイグレーションする手段が提供されるようになるまで、エラー・メッセージを無視することができます。
{: tsResolve}


## `ibmcloud` CLI を使用してツールチェーンを削除することができないのはなぜですか?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

現時点で、ibmcloud resource CLI を使用してツールチェーンを削除することはできません。 

`ibmcloud resource service-instance-delete` コマンドを使用してコマンド・ラインからツールチェーンを削除しようとすると、コマンドが失敗し、次のエラー・メッセージが表示されます。
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

ツールチェーンは、Cloud プラットフォームにおける特別なリソース・タイプであり、現時点では `ibmcloud resource` CLI を使用して削除することはできません。
{: tsCauses}

ツールチェーンを削除するには、以下のようにします。
{: tsResolve}

1. DevOps ダッシュボードの**「ツールチェーン」**ページで、削除するツールチェーンをクリックします。 あるいは、アプリの「概要」ページの「継続的デリバリー」カードで、**「ツールチェーンの表示」**をクリックします。
1. **「アプリの表示」**の横にある**「その他のアクション」**メニューをクリックします。
1. **「削除」**をクリックします。 ツールチェーンを削除すると、そのツールチェーンのツール統合がすべて削除されます。結果として、その統合で管理されていたリソースが削除される可能性があります。
1. ツールチェーンの名前を入力し、**「削除」**をクリックして、削除を確認します。  


## リポジトリーへのコミットとプッシュの後、Live Edit を使用できなくなるのはなぜですか?
{: #troubleshoot-liveedit}
{: troubleshoot}

Eclipse Orion {{site.data.keyword.webide}} の外部でデプロイすると、Live Edit モードはクリアされます。

コマンド・ラインまたは {{site.data.keyword.webide}} から変更のコミットとプッシュを行うと、Live Edit は使用できなくなります。
{: tsSymptoms}
   
{{site.data.keyword.contdelivery_short}} パイプラインと {{site.data.keyword.webide}} の両方を含んだツールチェーンを作成すると、それらのツール統合の両方でアプリケーション (アプリ) をデプロイできるようになります。 デフォルトでは、そのパイプラインと {{site.data.keyword.webide}} の両方が、同じ Cloud Foundry のアプリおよび URL を使用して、同じ Cloud Foundry の組織およびスペースにデプロイします。 {{site.data.keyword.webide}} の外部でデプロイすると、Live Edit モードはクリアされます。
{: tsCauses}

Live Edit を使用してアプリのテスト・バージョンを迅速に開発するには、Cloud Foundry の別のアプリ、スペース、および URL に {{site.data.keyword.webide}} からデプロイします。 コードの変更が完了したら、コードをコミットとしてプッシュすることで、パイプラインによるアプリの実動バージョンのビルドとデプロイがトリガーされるようにします。
{: tsResolve}

1. 実行バーで、編集する対象となる起動構成を選択します。
2. スペースとホストに指定されている値を編集します。
3. **「保存」**および**「終了」**をクリックします。
4. 実行バーで**「実行」**ボタンをクリックします。 Live Edit ボタンを使用可能にするには、複数回デプロイする必要がある場合があります。

Live Edit について詳しくは、[Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit) を参照してください。


## {{site.data.keyword.webide}} の実行バーの「同期していない」とはどのような意味ですか?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

ワークスペース内のファイル・システムが同期していません。

Live Edit モードでは、{{site.data.keyword.webide}} はワークスペース内のファイルを、実行中の Cloud Foundry アプリと同期しますが、それらのファイルの同期が取れていません。
{: tsSymptoms}
   
{{site.data.keyword.webide}} の外部でアプリが変更された場合、ワークスペース内のファイル・システムが非同期の状態になる可能性があります。 また、{{site.data.keyword.webide}} がアプリから同期状態を取得できない場合も、非同期の状態になる可能性があります。
{: tsCauses}

正常な通信が再確立されると、1、2 分後に状態がクリアされ、ファイルが同期される可能性があります。 そうならない場合は、Live Edit モードを有効にしてアプリを開始し、停止することができます。
{: tsResolve}
