---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.jazzhub_short}} プロジェクトがアップグレードされた後のツールチェーンの概説
{: #toolchains_post_upgrade}

hub.jazz.net の {{site.data.keyword.jazzhub}} プロジェクトは {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}} サービスのツールチェーンにアップグレードされます。 

hub.jazz.net の {{site.data.keyword.jazzhub_short}} は廃止されます。 

DevOps プロジェクトについては、[{{site.data.keyword.contdelivery_short}} サービス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/devops){:new_window} を使用してください。 {{site.data.keyword.Bluemix_notm}} になじみがない場合は、[{{site.data.keyword.Bluemix_notm}} とは](/docs/overview/ibm-cloud.html#overview)をご確認ください。

{: shortdesc}

## プロジェクトから作成されたツールチェーンの検索
{: #find_toolchain}

[ツールチェーンのページ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/devops/toolchains){: new_window}に移動して、hub.jazz.net プロジェクトの名前と一致する名前のツールチェーンが表示されることを確認し、アップグレードが完了したことを確認します。 プロジェクトが自動的にアップグレードされた場合は、以下の点に注意してください。
   - プロジェクトがアップグレードされる前に、そのプロジェクトの名前が別のツールチェーンで既に使用されている場合、プロジェクトのために作成された新規ツールチェーンは、プロジェクトと完全に一致する名前ではないことがあります。 
   - プロジェクトのツールチェーンが表示されない場合、所属する他の組織に切り替えてツールチェーンを確認してください。
   
## ツールチェーンの概要
{: #compare_toolchains}

hub.jazz.net に 1 つ以上のプロジェクトがあった場合、アップグレードが失敗していなければ、{{site.data.keyword.contdelivery_short}} サービスのツールチェーンに自動的にアップグレードされています。 IBM Cloud のアカウントまたは組織が無効であるために、アップグレードが失敗することがあります。 失敗した場合は、これらのアカウントや組織の所有者に対して、失敗したことと、その解決のために所有者が行う必要がある具体的なアクションを通知する E メールが送信されます。 アップグレードしたプロジェクトのツールチェーンを見つけるために支援が必要な場合は、[サポート![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}にお問い合わせください。 

ツールチェーンはプロジェクトと同様ですが、以下のようないくつかの重要な違いがあります。

- プロジェクトは、1 つのリポジトリーとパイプラインしか持てません。 ツールチェーンは、必要に応じていくつでもリポジトリーとパイプラインを持つことができます。
- ツールチェーンには、Slack、Sauce Labs、PagerDuty、および {{site.data.keyword.DRA_full}} などの、プロジェクトでは使用できないツールを組み込むことができます。

 {{site.data.keyword.DRA_short}} は、米国南部、英国およびドイツ地域で利用可能です。
 {: tip}
 
- プロジェクトでは、メンバーシップはプロジェクト・レベルで管理されていました。 ツールチェーンへのアクセスは、{{site.data.keyword.Bluemix_notm}} 組織とツールチェーンによって管理されます。 ツールチェーンで作業するには、ツールチェーンを含む組織のメンバーである必要があります。 ツールチェーンの所有者は、誰がツールチェーンにアクセスでき、何をすることができるかを制御できます。 アクセス制御について詳しくは、[ツールチェーンの概説](#upgrade_next_steps)のステップ 2 を参照してください。
- hub.jazz.net のプロジェクトで使用していたリポジトリーのタイプに応じて、ツールチェーンに GitHub.com リポジトリーまたは {{site.data.keyword.gitrepos}} リポジトリーが含まれる場合があります。

ツールチェーンについて詳しくは、[YouTube ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://youtu.be/2SIPE1e7NJ4){: new_window} または [{{site.data.keyword.contdelivery_short}} 概説](/docs/services/ContinuousDelivery/index.html)で説明しています。

## ツールチェーンの概説
{: #upgrade_next_steps}

1. チーム・メンバーにツールチェーンへのアクセス権限を付与します。
    - 各チーム・メンバーには、有効な {{site.data.keyword.Bluemix_notm}} アカウントが必要です。 アカウントを持っていないチーム・メンバーは、[登録![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/registration){:new_window}する必要があります。
    - ツールチェーンの「管理」ページから、ツールチェーンに対するアクセス権限を組織のメンバーに付与します。 既存のプロジェクト・メンバーは、アップグレード・プロセスの一部としてツールチェーンのメンバーに追加されます。 ツールチェーンのアクセス制御について詳しくは、[アクセスの管理 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window} を参照してください。
    - ユーザーがツールチェーンの属する組織のメンバーでない場合は、「組織の管理」ページから、そのユーザーを組織に追加します。
    - ツールチェーンで {{site.data.keyword.gitrepos}} が使用される場合、有効な {{site.data.keyword.Bluemix_notm}} ID を持つすべての JazzHub プロジェクト・メンバーは、JazzHub プロジェクトで持っていたものと同じ特権で {{site.data.keyword.gitrepos}} リポジトリーに追加されます。 JazzHub プロジェクトに有効な {{site.data.keyword.Bluemix_notm}} ID を持たないメンバーがいる場合、そのメンバーを登録することができます。 彼らを登録した後、リポジトリーに追加できます。
      組織の管理について詳しくは、[組織とスペースの管理 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/account/orgs_spaces.html#orgsspacesusers){:new_window} を参照してください。

2. {{site.data.keyword.gitrepos}}を使用する場合は、個人用アクセス・トークンまたは SSH 鍵を使用して認証します。 SSH 鍵について詳しくは、[認証のための個人用アクセス・トークンまたは SSH 鍵の作成](/docs/services/ContinuousDelivery/git_working.html#git_authentication)を参照してください。 外部 Git クライアントから https を使用して認証するには、以下のステップを実行します。
    1. {{site.data.keyword.gitrepos}}・ユーザー設定の[「Access Tokens」ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} にアクセスします。
    2. スコープとして **api** を使用する個人用アクセス・トークンを作成します。
    3. [「Account」ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/profile/account){:new_window} にアクセスして、{{site.data.keyword.gitrepos}}に使用しているユーザー名を見つけます。 ご使用のユーザー名は「Change username」セクションにリストされ、作成する個人用リポジトリーの URL の最初の部分として示されます。
    4. 外部 Git クライアントから HTTPS を使用して {{site.data.keyword.gitrepos}}に対する認証を行うには、ユーザー名と個人用アクセス・トークンを使用します。
    5. JazzHub Git リポジトリーのローカル・リポジトリーを再使用する場合は、そのリポジトリーを {{site.data.keyword.gitrepos}}内の新しいリポジトリーに複製します。 端末のシェルから、JazzHub Git リポジトリーが複製されているディレクトリーに移動します。 `git remote set-url` コマンド `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo> を入力します。`

        どのリモート URL がどのリモート名に設定されているかを確認するには、`git remote -v` コマンドを使用します。 デフォルトのリモート名は `origin` です。 より高度なセットアップの場合、コマンドの形式は `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo> のようになります。`
        {: tip}

3. オプション: プロジェクトの開発成熟度、チームのプラクティス、コード・ベースの品質を探るには、ツールチェーンに IBM Cloud {{site.data.keyword.DRA_short}} を追加します。 {{site.data.keyword.DRA_short}} は、開発者、チーム、デプロイメントの分析を DevOps プロジェクトに適用します。 詳しくは、[{{site.data.keyword.DRA_short}} 概説](/docs/services/DevOpsInsights/index.html)を参照してください。

  {{site.data.keyword.DRA_short}} は、米国南部、英国およびドイツ地域で利用可能です。
  {: tip}


## トラブルシューティング
{: #upgrade_troubleshoot}

プロジェクトのアップグレードに関連する問題が発生した場合、[サポート・フォーラム![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}に質問を投稿してください。 フォーラムへの投稿には、{{site.data.keyword.jazzhub_short}} プロジェクトと {{site.data.keyword.contdelivery_short}} ツールチェーンの URL を記載し、`devops-services` タグを付けてください。


## よくある質問
{: #upgrade_faq}

### 私の JazzHub プロジェクトは英国地域に関連付けられていましたが、ツールチェーンは米国南部地域になります。 これはどういうことでしょうか?
{: #faq_region}

hub.jazz.net のプロジェクトとツールチェーンはどちらも、米国南部地域でホストされます。 英国地域などの異なる地域にアプリをデプロイするようにプロジェクトが構成されている場合でも、ツールチェーンはアプリを前述の地域にデプロイします。 そのため、データがホストされる場所については、変更がありません。 ツールチェーンは、今後、複数の地域で利用できるようになる予定です。

### アップグレード後、Track &amp; Plan 内の作業項目とダッシュボードはどうなりましたか。
{: #faq_tp}

{{site.data.keyword.contdelivery_short}} サービスには、IBM がホストする GitLab Community Edition ベースの {{site.data.keyword.gitrepos}} を使用する問題追跡機能があります。 {{site.data.keyword.contdelivery_short}} はまた、プランニングと問題追跡のための他のツール (GitHub Issues や JIRA など) との統合もサポートしています。

自動化アップグレード・プロセス中に、Track & Plan 作業項目が Git Issues に移行されています。 GitHub Issues と {{site.data.keyword.gitrepos}} のどちらにも、プランニング用のかんばんボードと問題追跡機能が備わっています。 Git Repos and Issue Tracking のかんばん機能である「問題ボード」について詳しくは、[問題ボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window} を参照してください。

非推奨の JazzHub Track &amp; Plan と同じ機能が必要な場合は、新しい IBM Track and Plan on Cloud サービスを該当する国で月単位でユーザーごとに購入できます。 このクラウド・サービスを利用すると、単一のテナント・クラウド・サブスクリプションで、Rational Team Concert&trade; コントリビューター・ライセンスに相当するフル機能を利用できます。

この新しい IBM Track and Plan on Cloud サービスの機能は非推奨の JazzHub Track &amp; Plan よりも豊富で、プロセスのカスタマイズ、プロジェクトの階層、SAFe&reg; やその他の多くのアジャイルかつハイブリッドなメソッド、単一プロジェクトからのスケーラビリティーなどをサポートしています。 これは最新バージョンの Rational Team Concert 6.0.3 をベースとしていて、今後 60 日間以内にバージョン 6.0.4 になる予定です。一方、JazzHub Track &amp; Plan のベースは Rational Team Concert 5.x でした。 追加サービスを使用すると、IBM Track and Plan on Cloud へのデータ移行が可能です。 詳しくは、コネクティッド製品 SaaS のセールス・リーダーである [Tom Hollowell ![ 外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](mailto:trhollow@us.ibm.com){:new_window} にお問い合わせください。

IBM Track and Plan on Cloud の詳細を確認したりオンラインで購入したりする場合には、[IBM マーケットプレイス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window} を参照してください。

ビルド自動化およびソース・コード管理を購入するには、[Rational Team Concert on Cloud ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} を選択できます。

### アップグレード後、コード・リポジトリーはどうなりましたか。
{: #faq_repo}

アップグレード後は、それまでのサービスと同等の新しい Git サービスを使用できます。 github.com を JazzHub プロジェクトで使用していた場合、ツールチェーンは同じ GitHub リポジトリーに接続されます。 IBM がホストする Git を JazzHub プロジェクトで使用していた場合、そのリポジトリーの内容は、{{site.data.keyword.contdelivery_short}} の一部として IBM がホストする {{site.data.keyword.gitrepos}} 内の新しいリポジトリーに複製されます。

アップグレード・プロセス中に各タイプのリポジトリーがどのように処理されるかについて、次の表にまとめています。

|プロジェクト・リポジトリー |プロジェクト・タイプ	|ツールチェーン・リポジトリー |
|:----------|:------------------------------|:------------------|
|github.com 		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public と同じ github.com リポジトリー	|
|hub.jazz.net/git		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public の {{site.data.keyword.gitrepos}} の新しいプライベート・リポジトリーまたはパブリック・リポジトリー	|
|Jazz SCM		|プライベートまたはパブリック 		|{{site.data.keyword.Bluemix_notm}} Public の {{site.data.keyword.gitrepos}} の新しいプライベート・リポジトリーまたはパブリック・リポジトリー	|
{: caption="表 1. プロジェクト・リポジトリー対ツールチェーン・リポジトリーのマッピング" caption-side="top"}


### アップグレード後、プロジェクト内のビルド定義はどうなりましたか。
{: #faq_build}

Delivery Pipeline ではなく Jazz を使用してソース・コードを構築した場合は、ツールチェーンの Delivery Pipeline にビルド定義を手動で移行する必要があります。

Jazz SCM をソース・リポジトリーとして使用し、Delivery Pipeline を使用してコードをビルドした場合は、Jazz SCM 内のソースが Git リポジトリーに自動的に移されています。Jazz SCM のソースではなく Git リポジトリーのソースを使用する点を除けば、Delivery Pipeline の構成は同じままです。

### ツールチェーンにアップグレードされたプロジェクト用の組織を作成する必要があったので、アカウントにクレジット・カードを追加しました。 クレジット・カードに課金されるのでしょうか。
{: #faq_charges}

[従量課金 (PAYG) のお客様 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window} が、{{site.data.keyword.Bluemix_notm}} カタログにリストされている無料割り当て分を超えたランタイム、サービス、コンポーネントを使用すると課金されます。 使用量の見積もりについては、[料金シート ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window} を参照してください。 継続的デリバリーの現在の料金については、[{{site.data.keyword.Bluemix_notm}} カタログ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/catalog/services/continuous-delivery){: new_window} を参照してください。

IBM 社員の場合、内部 IBM プロジェクトは、個人のクレジット・カードではなく部門に対して課金されます。 IBM 社員に割り当てられている無料分を超えるリソースを使用する必要がある場合、サポート・チケットを作成してください。

### ツールチェーンが見つからず、アクセスもできません。 どうすればよいですか?
{: #faq_find}

ツールチェーンは {{site.data.keyword.Bluemix_notm}} 組織でホストされます。 アップグレード・プロセスによって、JazzHub プロジェクトのすべてのメンバーはツールチェーンに追加されます。 ただし、{{site.data.keyword.Bluemix_notm}} 組織の所有者がユーザーを組織に追加しない限り、ユーザーはツールチェーンを表示できません。

ツールチェーンにアクセスするには、{{site.data.keyword.Bluemix_notm}} に移動し、メニュー・アイコンをクリックして、**「サービス」&gt;「DevOps」**をクリックします。 「ツールチェーン」ページが開きます。 自分が米国南部地域にいることと、ツールチェーンを含む組織にいることを確認します。 ツールチェーンが「ツールチェーン」ページにリストされない場合は、[この FAQ 項目](#faq_uk)を参照してください。

### 私のプロジェクトは英国地域に関連付けられています。 アップグレード後、エラー・メッセージが表示され、同僚はツールチェーンにアクセスできず、{{site.data.keyword.Bluemix_notm}} の「ツールチェーン」ページに私のツールチェーンが表示されません。 何が原因でしょうか?
{: #faq_uk}

**質問全文:**

私の JazzHub プロジェクトはプロジェクト設定に従って {{site.data.keyword.Bluemix_notm}} 英国地域に関連付けられています。 JazzHub の概要ページに移動して、**「設定」**アイコン (歯車のような絵) をクリックし、**「オプション」&gt;「この {{site.data.keyword.Bluemix_notm}} プロジェクトの作成: 地域 (Make this a {{site.data.keyword.Bluemix_notm}} Project: Region)」**をクリックして、プロジェクト設定を確認しました。 プロジェクトを米国のツールチェーンにアップグレードした後、以下の問題が発生します。

   1. 米国組織を選択すると、組織には米国南部地域のスペースがないというメッセージが表示され、スペースを作成するよう求められます。 米国では何も実行するつもりはありません。
   
   2. 同僚の何人かが、オリジナルの JazzHub プロジェクトのメンバーとしてリストされていたのに、ツールチェーンにアクセスできません。 彼らが**「ツールチェーンの表示」**をクリックして英国地域のアプリの概要ページからツールチェーンを開こうとすると、「アクセス拒否」のメッセージが表示されます。
   
   3. **「ツールチェーンの表示」**をクリックして英国地域のアプリの概要ページからは直接ツールチェーンにアクセスできますが、[https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south){: new_window} で私の「ツールチェーン」ページにリストされているツールチェーンは表示されません。 ツールチェーンを変更できないというエラーが表示されるか、ツールチェーンがないので作成する必要があるというエラーが表示されます。 

**回答:**

これらの問題は、米国以外の {{site.data.keyword.Bluemix_notm}} 組織に所属していて、アップグレードの前に明示的に米国南部地域に組織を拡張していなかった場合に発生します。 この問題については「ツールチェーン」ページを開いて確認できます。このページの先頭に地域と組織が表示されます。 

何が起こったかというと、アップグレード時に、所属の米国以外の組織が米国に存在しなかったので、アクセスしたことのある別の組織が検出されてそれがアップグレードで選択されたということです。

米国のその {{site.data.keyword.Bluemix_notm}} 組織に切り替えると、ツールチェーンを見つけることができます。 同僚をその組織に追加すれば、彼らにアクセス権限が付与されます。 このツールチェーンは、所属の米国以外の組織に引き続きデプロイできます。ただ問題になるのは、これらの 2 つの組織がまったく別物であり、ユーザー管理を自動的に両方に対して実行できない点です。

所属の米国以外の組織に一致する米国の組織にツールチェーンを置きたい場合は、以下の手順に従ってください。

   1. [https://cloud.ibm.com ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com){: new_window} にログインし、所属している、米国以外の地域と組織を選択します。
   
   2. {{site.data.keyword.Bluemix_notm}} ヘッダーで、米国南部地域に切り替えます。 その地域でスペースを作成するよう求められます。
   
   3. 米国南部地域でスペースを作成して、所属の組織をその地域に拡張します。 
   
   4. アップグレード・プロセスで作成されたツールチェーンを削除します。 
   
      Git リポジトリーは、自動的には削除されません。 手動で削除するか、該当する名前に変更することができます。 Git リポジトリーの名前をすでに変更した場合は、今後のツールチェーンでそれを使用するように更新できます。
 {: tip}

   5. JazzHub プロジェクトに戻ります。 別のアップグレードを試行できるように、プロジェクトはリセットされます。プロジェクトがリセットされない場合は、hub@jazz.net に連絡を取り、プロジェクトの URL を提供してください。
   
   6. アップグレード・プロセスを再始動し、米国の適切な組織が選択されていることを確認し、所属の米国地域以外の組織の名前を一致させます。
   
   7. 以前のツールチェーン・アップグレード時の Git リポジトリーを保持または名前変更している場合 (ステップ 4 参照)、ツールチェーンの Git カードを再構成して、この Git リポジトリー URL を指すように変更できます。 変更はパイプラインに自動的に反映されます。 確認のため、ビルド・ステージの「入力」タブを検査してください。
