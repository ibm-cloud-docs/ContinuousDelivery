---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.jazzhub_short}} プロジェクトをツールチェーンにアップグレード
{: #upgrade_projects}

{{site.data.keyword.jazzhub}} は、{{site.data.keyword.contdelivery_full}} へと進化しました。 その変更の一部として、プロジェクトはツールチェーンにアップグレードされます。

ユーザーは、プロジェクトを自分でアップグレードするか、自動的にアップグレードされるのを待つことができます。 最良の結果を得るためには、[前提条件](#upgrade_prereqs)を満たしたうえで、できるだけ早くプロジェクトをアップグレードして、ツールチェーンの名前やツールチェーンが作成される組織を制御できるようにしてください。
{: shortdesc}

**よくある質問**

- [私の JazzHub プロジェクトは英国地域に関連付けられていますが、ツールチェーンは米国南部地域になります。 どのような仕組みですか。](#faq_region)
- [アップグレードする場合、Track &amp; Plan 内の作業項目とダッシュボードはどうなりますか。](#faq_tp)
- [アップグレードする場合、コード・リポジトリーはどうなりますか。](#faq_repo)
- [ツールチェーンにアップグレードする場合、プロジェクト内のビルド定義はどうなりますか。](#faq_build)
- [ツールチェーンにアップグレードするプロジェクト用の組織を作成する必要があります。 組織を作成するには、その前にアカウントにクレジット・カードを追加する必要があることは理解しています。 クレジット・カードに課金されるのでしょうか。](#faq_charges)
- [ツールチェーンが見つからず、アクセスもできません。 どうすればよいですか?](#faq_find)
- [私のプロジェクトは英国地域に関連付けられています。 アップグレード後、エラー・メッセージが表示され、同僚はツールチェーンにアクセスできず、{{site.data.keyword.Bluemix_notm}} プラットフォームの「ツールチェーン」ページに私のツールチェーンが表示されません。 何が原因でしょうか?](#faq_uk)

## ツールチェーン
{: #compare_toolchains}

ツールチェーンはプロジェクトと同様ですが、以下のようないくつかの重要な違いがあります。

- プロジェクトは、1 つのリポジトリーとパイプラインしか持てません。 ツールチェーンは、必要に応じていくつでもリポジトリーとパイプラインを持つことができます。
- ツールチェーンには、Slack、Sauce Labs、PagerDuty、および {{site.data.keyword.DRA_full}} などの、プロジェクトでは使用できないツールを組み込むことができます。
- ツールチェーンへのアクセスは、標準の {{site.data.keyword.Bluemix_notm}} 組織で管理されます。 メンバーシップは、プロジェクト・レベルで管理されていたプロジェクトと異なり、組織レベルで維持されます。

ツールチェーンについては、[YouTube ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://youtu.be/2SIPE1e7NJ4){: new_window} または [{{site.data.keyword.contdelivery_short}} 概説](/docs/services/ContinuousDelivery/index.html) [![YouTube への外部リンク](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window} で説明しています。

## 前提条件
{: #upgrade_prereqs}

- アップグレードされたプロジェクトのツールチェーンにアクセスするには、{{site.data.keyword.Bluemix_notm}} ID が必要です。 アップグレードする前に、アクティブな {{site.data.keyword.Bluemix_notm}} ID を持っていることを確認する必要があります。 持っていない場合は、[登録](https://console.ng.bluemix.net/registration/)してください。
- {{site.data.keyword.jazzhub_short}} プロジェクト所有者が正しいことを確認してください。 プロジェクトから作成されるツールチェーンは、その所有者の {{site.data.keyword.Bluemix_notm}} 組織の一部になります。
- ツールチェーンを作成する組織とスペースが米国南部地域の {{site.data.keyword.Bluemix_notm}} Public にあることを確認します。 米国南部に有効な組織とスペースがあることを確認するには、[https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} にログインし、スペースを作成するように求められたらそれを作成します。
- アップグレードを開始する計画がある場合は、パイプラインがデプロイされるすべての組織およびスペースのメンバーであることを確認してください。 プロジェクト管理者であれば誰でもアップグレードを開始できます。 ただし、アップグレードを開始する管理者がパイプラインのデプロイ先のすべての組織およびスペースのメンバーでなければ、パイプラインは作成されません。 アップグレードを開始する人が、ツールチェーンのリポジトリーの所有者になります。
- ツールチェーン内の Eclipse Orion {{site.data.keyword.webide}} は、プロジェクトに関連付けられた {{site.data.keyword.webide}} から分離しています。 {{site.data.keyword.webide}} を使用していて、コミットされていない変更がある場合は、アップグレードする前にそれらの変更をコミットしてください。


## プロジェクトからツールチェーンへのアップグレード
{: #project_to_toolchain}

hub.jazz.net のプロジェクトとツールチェーンはどちらも、米国南部地域でホストされます。 異なる地域にアプリをデプロイするようにプロジェクトが構成されている場合でも、プロジェクトがツールチェーンにアップグレードされた後に、アプリは前述の地域にデプロイされます。
{: tip}

プロジェクトのアップグレード準備ができると、プロジェクトのカードおよび「概要」ページにメッセージが表示されます。

![「アップグレードの準備完了 (Ready To Upgrade)」ラベルを含むカードのイメージ](images/card-project-to-upgrade.png)

![「アップグレード時間 (Time to Upgrade)」メッセージ](images/banner-ready-to-upgrade.png)

アップグレード準備ができたプロジェクトは、「マイ・プロジェクト」ページのメニューから見つけることができます。

![「アップグレードするプロジェクト (Projects To Upgrade)」メニュー項目のイメージ](images/menu-projects-to-upgrade.png)
{: tip}

アップグレードを開始すると、プロジェクト内のパイプライン・ステージはロックされます。 ロックされたパイプライン・ステージは、実行することも変更することもできません。 ツールチェーンを削除してアップグレードを元に戻すと、パイプラインはアンロックされます。

JazzHub でホストされている Git リポジトリーをプロジェクトが使用する場合は、アップグレード開始後に、ツールチェーンに移動するデータの整合性を確保するためにリポジトリーがロックされます。 ツールチェーンを削除してアップグレードを元に戻すと、JazzHub 上のリポジトリーはアンロックされます。

アップグレード・プロセス中に各タイプのリポジトリーがどのように処理されるかについて、次の表にまとめています。

|プロジェクト・リポジトリー |プロジェクト・タイプ	|ツールチェーン・リポジトリー |
|:----------|:------------------------------|:------------------|
|github.com 		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public と同じ github.com リポジトリー	|
|hub.jazz.net/git		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public の {{site.data.keyword.gitrepos}}内の新しいリポジトリー	|
{: caption="表 1. プロジェクト・リポジトリー対ツールチェーン・リポジトリーのマッピング" caption-side="top"}

## アップグレード・プロセスの開始
{: #start_upgrade}

アップグレード・プロセスを開始する前に、[YouTube![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://youtu.be/LSr2e3uvyLs){: new_window} で実際のアップグレード・プロセスを見ることをお勧めします。
[![YouTube への外部リンク](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

プロジェクトをツールチェーンにアップグレードするには、以下のステップを実行します。

1. アップグレード・プロセスを開始するには、バナー・メッセージで**「今すぐアップグレード (upgrade now)」**をクリックします。 「プロジェクト・アップグレード・ツールチェーン (Project upgrade toolchain)」ページが開きます。

   ![アップグレード・ページの例](images/project-upgrade-toolchain.png)

   アップグレード・プロセスの概要については、そのページ上の説明をお読みください。 ツールチェーンには、プロジェクトのパイプラインと同じステージとジョブを含む新しいパイプラインが組み込まれます。 さらに、ツールチェーンには、{{site.data.keyword.contdelivery_short}} で実行されている Eclipse Orion {{site.data.keyword.webide}} へのポインターも含まれます。

   この例では、プロジェクトは github.com のパブリック・リポジトリーを使用するため、ツールチェーンは同じ GitHub リポジトリーに接続されます。 JazzHub にホストされている Git リポジトリーをプロジェクトが使用する場合、そのリポジトリーの内容は、{{site.data.keyword.contdelivery_short}} の一部である {{site.data.keyword.gitrepos}}内の新しいリポジトリーに複製されます。

2. ツールチェーンをカスタマイズするには、次のいくつかの設定を構成できます。

   - ツールチェーンの名前を変更するには、**「名前」**フィールドを編集します。

      ![「名前」フィールド](images/name-change.png)

   - ツールチェーンを作成する {{site.data.keyword.Bluemix_notm}} 組織を変更するには、アカウント・メニューから組織を選択します。

      ![{{site.data.keyword.Bluemix_notm}} 組織の選択機能](images/bluemix-organization-chooser.png)

   ツールチェーンは組織レベルで管理されるため、ツールチェーンにアクセスする必要があるプロジェクト・メンバーが存在している、またはそれらのメンバーを追加できる組織を必ず選択するようにしてください。

3. プロジェクトで Track & Plan を使用した場合は、Track & Plan データを GitHub Issues に転送できます。

   ![Track and Plan のオプション](images/upgrade-tutorial-track-and-plan.png)

   - Track & Plan データをマイグレーションするかどうかを示します。
   - デフォルトでは、Track & Plan データのすべてがマイグレーションされます。 特定の照会の一部である作業項目のみをマイグレーションする場合は、その照会を指定します。
   - GitHub Issues のラベルにマップする作業項目の属性を選択します。

4. **「作成」**をクリックします。 新しいツールチェーンが作成され、「概要」ページが表示されます。

   ![アップグレードされたツールチェーンの概要](images/new-toolchain-page.png)

   - GitHub リポジトリー、または関連付けられた Issue Tracker にアクセスするには、**「GitHub」**または**「Issues」**をクリックします。
   - パイプラインにアクセスするには、**「Delivery Pipeline」**をクリックします。
   - ワークスペースにチェックアウトされた、リポジトリーのコンテンツを含む {{site.data.keyword.webide}} にアクセスするには、**Eclipse Orion {{site.data.keyword.webide}}** をクリックします。

   アップグレード中にプロジェクトに戻った場合、ソース・コードを新しいリポジトリーにインポートする処理や、Track &amp; Plan 作業項目を問題としてインポートする処理がアップグレード・プロセスに含まれる場合は特に、アップグレードが進行中であることがバナー・メッセージで示されることがあります。

   ![ツールチェーンにアップグレードされるプロジェクトに関するメッセージ](images/project-being-upgraded-banner.png)

## プロジェクトの再訪
{: #revisit_projects}

これで新しいツールチェーンを使用する準備ができました。 プロジェクトには「アップグレード済み」のラベルが付けられ、「概要」ページに確認メッセージが表示されます。

![「アップグレード済み (Upgraded)」ラベルを含むプロジェクト・カードのイメージ](images/card-upgraded-project.png)

![アップグレード済みプロジェクト](images/banner-upgraded.png)

「マイ・プロジェクト」ページのメニューから**「アップグレード済みプロジェクト (Upgraded Projects)」**を選択することにより、どのプロジェクトがアップグレードされているか確認できます。

![「アップグレード済みプロジェクト」メニュー項目のイメージ](images/menu-upgraded-projects.png)

アップグレードを元に戻す必要がある場合は、ツールチェーンを削除します。 ツールチェーンの「概要」ページの**「他のアクション」**メニューからツールチェーンを削除できます。

![「他のアクション」メニューの削除アクションのイメージ](images/upgrade-tutorial-delete-toolchain.png)

プロジェクトに戻るとアップグレード・メッセージが再び表示され、準備ができたら再びアップグレードできます。

## 次のステップ
{: #upgrade_next_steps}

1. ブラウザーを最新表示し、プロジェクトの「概要」ページでプロジェクトが「このツールチェーンにアップグレードされた」というメッセージがあるかどうか調べて、アップグレードが完了したことを確認します。

   ![プロジェクトがアップグレードされたことを示すバナーのメッセージ](images/banner-upgraded.png)

   「今すぐアップグレード」というメッセージが表示されたら、アップグレードは失敗しています。 **「今すぐアップグレード (upgrade now)」**リンクをクリックして再試行してください。
   {: tip}

   ![プロジェクトがアップグレード可能状態であることを示すバナーのメッセージ](images/banner-ready-to-upgrade.png)

2. チーム・メンバーにツールチェーンへのアクセス権限を付与します。
    - 各チーム・メンバーには、有効な {{site.data.keyword.Bluemix_notm}} アカウントが必要です。 アカウントを持っていないチーム・メンバーは、[登録![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/registration){:new_window}する必要があります。
    - ツールチェーンの「管理」ページから、ツールチェーンに対するアクセス権限を組織のメンバーに付与します。 既存のプロジェクト・メンバーは、アップグレード・プロセスの一部としてツールチェーンのメンバーに追加されます。 ツールチェーンのアクセス制御について詳しくは、[アクセスの管理 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window} を参照してください。
    - ユーザーがツールチェーンの属する組織のメンバーでない場合は、「組織の管理」ページから、そのユーザーを組織に追加します。
    - ツールチェーンで {{site.data.keyword.gitrepos}} が使用される場合、有効な {{site.data.keyword.Bluemix_notm}} ID を持つすべての JazzHub プロジェクト・メンバーは、JazzHub プロジェクトで持っていたものと同じ特権で {{site.data.keyword.gitrepos}} リポジトリーに追加されます。 JazzHub プロジェクトに有効な {{site.data.keyword.Bluemix_notm}} ID を持たないメンバーがいる場合、そのメンバーを登録し、リポジトリーに追加する必要があります。
      組織の管理について詳しくは、[組織とスペースの管理 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window} を参照してください。

3. {{site.data.keyword.jazzhub_short}} プロジェクトからのツールではなく、ツールチェーンからのツールを使用します。 例えば、ブラウザーからコードを編集するには、ツールチェーンから Web IDE を使用します。

4. {{site.data.keyword.gitrepos}}を使用する場合は、個人用アクセス・トークンまたは SSH 鍵を使用して認証します。 SSH 鍵について詳しくは、[認証のための個人用アクセス・トークンまたは SSH 鍵の作成](/docs/services/ContinuousDelivery/git_working.html#git_authentication)を参照してください。 外部 Git クライアントから https を使用して認証するには、以下のステップを実行します。
    1. {{site.data.keyword.gitrepos}}・ユーザー設定の[「Access Tokens」ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} にアクセスします。
    2. スコープとして **api** を使用する個人用アクセス・トークンを作成します。
    3. [「Account」ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/profile/account){:new_window} にアクセスして、{{site.data.keyword.gitrepos}}に使用しているユーザー名を見つけます。 ご使用のユーザー名は「Change username」セクションにリストされ、作成する個人用リポジトリーの URL の最初の部分として示されます。
    4. 外部 Git クライアントから https を使用して {{site.data.keyword.gitrepos}}に対する認証を行うには、ユーザー名と個人用アクセス・トークンを使用します。
    5. JazzHub Git リポジトリーのローカル・リポジトリーを再使用する場合は、そのリポジトリーを {{site.data.keyword.gitrepos}}内の新しいリポジトリーに複製します。 端末のシェルから、JazzHub Git リポジトリーが複製されているディレクトリーに移動します。 `git remote set-url` コマンド `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo> を入力します。`

        どのリモート URL がどのリモート名に設定されているかを確認するには、`git remote -v` コマンドを使用します。 デフォルトのリモート名は `origin` です。 より高度なセットアップの場合、コマンドの形式は `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo> のようになります。`
        {: tip}

5. ツールチェーンがセットアップされ、それを使い始めたなら、そのプロジェクトが誰にも使用されないようにするために、以下のステップのすべてまたはいくつかを実行することを検討してください。
    - 使用してはならないことを示す接尾部をプロジェクト名に追加する。 例えば、プロジェクトの末尾に `_DO_NOT_USE` を追加します。
    - 使用されなくなったことを示すためにプロジェクトの説明を更新し、ツールチェーンへのポインターを追加する。
    - プロジェクトからメンバーを削除する。
    - 必要がなくなったプロジェクトは削除する。

6. オプション: プロジェクトの開発成熟度、チームのプラクティス、コード・ベースの品質を探るには、ツールチェーンに IBM Cloud {{site.data.keyword.DRA_short}} を追加します。 {{site.data.keyword.DRA_short}} は、開発者、チーム、デプロイメントの分析を DevOps プロジェクトに適用します。 詳しくは、[{{site.data.keyword.DRA_short}} 概説](/docs/services/DevOpsInsights/index.html)を参照してください。


## トラブルシューティング
{: #upgrade_troubleshoot}

アップグレード・プロセス時に問題が発生したら、以下のトラブルシューティング手順のうちの 1 つ以上を試してください。

- [前提条件](#upgrade_prereqs)を満たしていることを確認します。 特に、パイプラインがデプロイされるすべての組織およびスペースのメンバーであることを確認してください。
- すべての前提条件を満たしているが、最初のアップグレード試行時に問題が発生した場合は、アップグレードをやり直します。
- ソース管理に対してプロジェクトで Jazz SCM または IBM がホストする Git を使用している場合は、リポジトリーのサイズを確認します。 500 MB を超える場合は、[DevOps サービス・チームにお問い合わせください![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}。
- ツールチェーンが見つからないか、アクセスできない場合は、[この FAQ 項目](#faq_find)を参照してください。
- 引き続き問題が発生する場合は、[サポート・フォーラム![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}に質問を投稿します。 フォーラムへの投稿には、{{site.data.keyword.jazzhub_short}} プロジェクトと {{site.data.keyword.contdelivery_short}} ツールチェーンの URL を記載し、`devops-services` タグを付けてください。


## よくある質問
{: #upgrade_faq}

### 私の JazzHub プロジェクトは英国地域に関連付けられていますが、ツールチェーンは米国南部地域になります。 どのような仕組みですか。
{: #faq_region}

hub.jazz.net のプロジェクトとツールチェーンはどちらも、米国南部地域でホストされます。 英国地域などの異なる地域にアプリをデプロイするようにプロジェクトが構成されている場合でも、プロジェクトがツールチェーンにアップグレードされた後に、アプリは前述の地域にデプロイされます。 そのため、データがホストされる場所に関しては、変更がありません。 ツールチェーンは、今後、複数の地域で利用できるようになる予定です。

### アップグレードする場合、Track &amp; Plan 内の作業項目とダッシュボードはどうなりますか。
{: #faq_tp}

{{site.data.keyword.contdelivery_short}} サービスには、IBM がホストする GitLab Community Edition ベースの {{site.data.keyword.gitrepos}} を使用する問題追跡機能があります。 {{site.data.keyword.contdelivery_short}} はまた、プランニングと問題追跡のための他のツール (GitHub Issues や JIRA など) との統合もサポートしています。

アップグレード・プロセス中に、Track &amp; Plan 作業項目を Git Issues に移行することを選択できます。 GitHub Issues と {{site.data.keyword.gitrepos}} のどちらにも、プランニング用のかんばんボードと問題追跡機能が備わっています。 Git Repos and Issue Tracking のかんばん機能である「問題ボード」について詳しくは、[問題ボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window} を参照してください。

非推奨の JazzHub Track &amp; Plan と同じ機能が必要なお客様は、新しい IBM Track and Plan on Cloud サービスを該当する国で別途購入できます。このサービスは、月単位でユーザーごとに購入します。 このクラウド・サービスを利用すると、単一のテナント・クラウド・サブスクリプションで、Rational Team Concert&trade; コントリビューター・ライセンスに相当するフル機能を利用できます。

この新しい IBM Track and Plan on Cloud サービスの機能は非推奨の JazzHub Track &amp; Plan よりも豊富で、プロセスのカスタマイズ、プロジェクトの階層、SAFe&reg; やその他の多くのアジャイルかつハイブリッドなメソッド、単一プロジェクトからのスケーラビリティーなどをサポートしています。 これは最新バージョンの Rational Team Concert 6.0.3 をベースとしていて、今後 60 日間以内にバージョン 6.0.4 になる予定です。一方、JazzHub Track &amp; Plan のベースは Rational Team Concert 5.x でした。 追加サービスを使用すると、IBM Track and Plan on Cloud へのデータ移行が可能です。 詳しくは、コネクティッド製品 SaaS のセールス・リーダーである [Tom Hollowell ![ 外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:trhollow@us.ibm.com){:new_window} にお問い合わせください。

IBM Track and Plan on Cloud の詳細を確認したりオンラインで購入したりする場合には、[IBM マーケットプレイス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window} にアクセスしてください。

ビルド自動化およびソース・コード管理を追加購入するには、[Rational Team Concert on Cloud ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} を選択できます。

### アップグレードする場合、コード・リポジトリーはどうなりますか。
{: #faq_repo}

アップグレードすると、それまでのサービスと同等の新しい Git サービスを使用できるようになります。 github.com を JazzHub プロジェクトで使用していた場合は、ツールチェーンが同じ GitHub リポジトリーに接続されます。 IBM がホストする Git を JazzHub プロジェクトで使用していた場合は、そのリポジトリーの内容が、{{site.data.keyword.contdelivery_short}} の一部として IBM がホストする {{site.data.keyword.gitrepos}} 内の新しいリポジトリーに複製されます。

アップグレード・プロセス中に各タイプのリポジトリーがどのように処理されるかについて、次の表にまとめています。

|プロジェクト・リポジトリー |プロジェクト・タイプ	|ツールチェーン・リポジトリー |
|:----------|:------------------------------|:------------------|
|github.com 		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public と同じ github.com リポジトリー	|
|hub.jazz.net/git		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public の {{site.data.keyword.gitrepos}} の新しいプライベート・リポジトリーまたはパブリック・リポジトリー	|
{: caption="表 1. プロジェクト・リポジトリー対ツールチェーン・リポジトリーのマッピング" caption-side="top"}


### ツールチェーンにアップグレードする場合、プロジェクト内のビルド定義はどうなりますか。
{: #faq_build}

Delivery Pipeline ではなく Jazz を使用してソース・コードを構築する場合、ツールチェーンの Delivery Pipeline にビルド定義を手動で移行する必要があります。

Jazz SCM をソース・リポジトリーとして使用し、Delivery Pipeline を使用してコードをビルドする場合は、Jazz SCM 内のソースが Git リポジトリーに自動的に移されます。 Jazz SCM のソースではなく Git リポジトリーのソースを消費している点を除けば、Delivery Pipeline の構成は同じままです。

### ツールチェーンにアップグレードするプロジェクト用の組織を作成する必要があります。 組織を作成するには、その前にアカウントにクレジット・カードを追加する必要があることは理解しています。 クレジット・カードに課金されるのでしょうか。
{: #faq_charges}

[従量課金 (PAYG) のお客様 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window} が、{{site.data.keyword.Bluemix_notm}} カタログにリストされている無料割り当て分を超えたランタイム、サービス、コンポーネントを使用すると課金されます。 使用量の見積もりについては、[料金シート ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window} を参照してください。 継続的デリバリーの現在の料金については、[{{site.data.keyword.Bluemix_notm}} カタログ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window} を参照してください。

IBM 社員の場合、内部 IBM プロジェクトは、個人のクレジット・カードではなく部門に対して課金されます。 IBM 社員に割り当てられている無料分を超えるリソースを使用する必要がある場合、サポート・チケットを作成してください。

### ツールチェーンが見つからず、アクセスもできません。 どうすればよいですか?
{: #faq_find}

ツールチェーンは {{site.data.keyword.Bluemix_notm}} 組織でホストされます。 アップグレード・プロセスによって、JazzHub プロジェクトのすべてのメンバーはツールチェーンに追加されます。 ただし、{{site.data.keyword.Bluemix_notm}} 組織の所有者がユーザーを組織に追加しない限り、ユーザーはツールチェーンを表示できません。

ツールチェーンにアクセスするには、{{site.data.keyword.Bluemix_notm}} プラットフォームに移動し、メニュー・アイコンをクリックして、**「サービス」&gt;「DevOps」**をクリックします。 「ツールチェーン」ページが開きます。 自分が米国南部地域にいることと、ツールチェーンを含む組織にいることを確認します。 ツールチェーンが「ツールチェーン」ページにリストされない場合は、[この FAQ 項目](#faq_uk)を参照してください。

または、JazzHub サイトがまた利用可能な場合は、プロジェクトの「概要」ページにあるバナーのリンクをクリックしてツールチェーンに移動できます。

### 私のプロジェクトは英国地域に関連付けられています。 アップグレード後、エラー・メッセージが表示され、同僚はツールチェーンにアクセスできず、{{site.data.keyword.Bluemix_notm}} の「ツールチェーン」ページに私のツールチェーンが表示されません。 何が原因でしょうか?
{: #faq_uk}

**質問全文:**

私の JazzHub プロジェクトはプロジェクト設定に従って {{site.data.keyword.Bluemix_notm}} 英国地域に関連付けられています。 JazzHub の概要ページに移動して、**「設定」**アイコン (歯車のような絵) をクリックし、**「オプション」&gt;「この {{site.data.keyword.Bluemix_notm}} プロジェクトの作成: 地域 (Make this a {{site.data.keyword.Bluemix_notm}} Project: Region)」**をクリックして、プロジェクト設定を確認しました。 プロジェクトを米国のツールチェーンにアップグレードした後、以下の問題が発生します。

   1. 米国組織を選択すると、組織には米国南部地域のスペースがないというメッセージが表示され、スペースを作成するよう求められます。 米国では何も実行するつもりはありません。
   
   2. 同僚の何人かが、オリジナルの JazzHub プロジェクトのメンバーとしてリストされていたのに、ツールチェーンにアクセスできません。 彼らが**「ツールチェーンの表示」**をクリックして英国地域のアプリの概要ページからツールチェーンを開こうとすると、「アクセス拒否」のメッセージが表示されます。
   
   3. **「ツールチェーンの表示」**をクリックして英国地域のアプリの概要ページからは直接ツールチェーンにアクセスできますが、[https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}で私の「ツールチェーン」ページにリストされているツールチェーンは表示されません。 ツールチェーンを変更できないというエラーが表示されるか、ツールチェーンがないので作成する必要があるというエラーが表示されます。 

**回答:**

これらの問題は、米国以外の {{site.data.keyword.Bluemix_notm}} 組織に所属していて、アップグレードの前に明示的に米国南部地域に組織を拡張していなかった場合に発生します。 これについては 2 つの方法で確認できます。

   * ツールチェーン URL を開いたときに、{{site.data.keyword.Bluemix_notm}} ヘッダーを確認します。 ほとんどの場合は、所属の組織名が表示され、スペースは示されていません。
   
   * ツールチェーンの概要ページから、**「管理」**をクリックします。 アクセス制御ページで、**「組織マネージャー (Org managers)」**リンクをクリックします。 ツールチェーンが含まれる組織がメインページにリストされます。

何が起こったかというと、アップグレード時に、所属の米国以外の組織が米国に存在しなかったので、たまたまアクセスしたことのある別の組織が検出されてそれがアップグレードで選択されたということです。

米国のその {{site.data.keyword.Bluemix_notm}} 組織に切り替えると、ツールチェーンを見つけることができます。 同僚をその組織に追加すれば、彼らにアクセス権限が付与されます。 このツールチェーンは、所属の米国以外の組織に引き続きデプロイできます。ただ問題になるのは、これらの 2 つの組織がまったく別物であり、ユーザー管理を自動的に両方に対して実行できない点です。

所属の米国以外の組織に一致する米国の組織にツールチェーンを置きたい場合は、以下の手順に従ってください。

   1. [https://console.bluemix.net ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net){: new_window} にログインし、所属している、米国以外の地域と組織を選択します。
   
   2. {{site.data.keyword.Bluemix_notm}} ヘッダーで、米国南部地域に切り替えます。 その地域でスペースを作成するよう求められます。
   
   3. 米国南部地域でスペースを作成して、所属の組織をその地域に拡張します。 
   
   4. アップグレード・プロセスで作成されたツールチェーンを削除します。 
   
      Git リポジトリーは、自動的には削除されません。 手動で削除するか、該当する名前に変更することができます。 リポジトリーを変更した場合は、今後のツールチェーンでそれを使用するように更新できます。{: tip}

   5. JazzHub プロジェクトに戻ります。 アップグレードのやり直しのため、リセットする必要があります。 リセットされない場合は、hub@jazz.net に連絡を取り、プロジェクトの URL を提供してください。
   
   6. アップグレード・プロセスを再始動し、米国の適切な組織が選択されていることを確認し、所属の米国地域以外の組織の名前を一致させます。
   
   7. 以前のツールチェーン・アップグレード時の Git リポジトリーを保持または名前変更している場合 (ステップ 4 参照)、ツールチェーンの Git カードを再構成して、この Git リポジトリー URL を指すように変更できます。 変更はパイプラインに自動的に反映されます。 確認のため、ビルド・ステージの「入力」タブを検査してください。
