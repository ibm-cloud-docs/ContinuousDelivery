---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# プランの制限と使用
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}} の使用は、{{site.data.keyword.Bluemix_notm}} プラットフォーム、あるいはその他の互換性のある Platform as a Service または Infrastructure as a Service のオファリングでのアプリケーションの構築、デプロイ、テスト、および進行中の運用に制限されています。

## サービス・インスタンスの有効範囲
{: #service_scope}

DevOps ツールチェーンを作成して使用するには、{{site.data.keyword.contdelivery_short}} [サービス・インスタンス](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}が必要です。サービス・インスタンスは、{{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) [リソース・グループ](/docs/services/resources?topic=resources-rgs)または {{site.data.keyword.Bluemix_notm}} 組織 (組織) のどちらかに属しています。

{{site.data.keyword.contdelivery_short}} サービスの*新しい*インスタンスは、リソース・グループ内に限り作成できます。組織からリソース・グループへのツールチェーンのマイグレーションは、現在サポートされていません。ツールチェーンが含まれている組織に属する {{site.data.keyword.contdelivery_short}} サービスがない場合は、リソース・グループ内でツールチェーンを再作成するか、[IBM サポート](https://cloud.ibm.com/unifiedsupport){:external}に支援を依頼することができます。

1 つのアカウントにつき 1 つのライト・サービスのみを使用できます。複数の組織かリソース・グループ、または複数の地域内でツールチェーンを扱おうとしている場合は、プロフェッショナル・プランを使用することをお勧めします。
{: tip}


## 許可ユーザー
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [サービス・プラン](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}は、サービス・インスタンスの許可ユーザー数に基づいて定義され、価格設定されます。以下に示すユーザーを含め、作業に貢献するすべてのユーザーを許可ユーザーとしてカウントする必要があります。

 * {{site.data.keyword.gitrepos}} リポジトリー内の問題、問題ボード、ソース・コード、その他の成果物を扱うユーザー。
 * デリバリー・パイプラインの状況を操作、トリガー (ユーザー・インターフェースで直接、またはリポジトリーにコミットすることによって間接的に)、または表示するユーザー。
 * Eclipse Orion {{site.data.keyword.webide}} を扱うユーザー。
 
ライト・プランには制限があります。ライト・プランとプロフェッショナル・プランについて詳しくは、[サービス・カタログ](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}を参照してください。
{: tip}
 
### リソース・グループ内の {{site.data.keyword.contdelivery_short}} のインスタンスに対するユーザーのカウント方法

請求とライト・プランの制限について許可ユーザーのリストを調べることによって、サービス・インスタンスごとに許可ユーザーをカウントし、管理します。{{site.data.keyword.contdelivery_short}} サービス・ユーザーは、このリストに自動的に追加されます。ユーザーがツールチェーンにアクセスして {{site.data.keyword.contdelivery_short}} サービス・インスタンスに自動的に追加されることを回避することができます。IAM を使用して、ツールチェーンが含まれるリソース・グループ (またはツールチェーン自体) からユーザー・アクセス権限を削除することについて詳しくは、[Identity and Access Management を使用した {{site.data.keyword.contdelivery_short}} へのユーザー・アクセス権限の管理](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security)を参照してください。 

リソース・グループ内でツールチェーンを編成するために使用する方式は、ユーザーのアクセスと請求に直接影響します。ユーザーがツールチェーンを複数のリソース・グループで使用すると、それらのリソース・グループ内のサービスごとにカウントされ、請求されます。
{: tip}

{{site.data.keyword.contdelivery_short}} サービス・インスタンス内の**「管理」**タブで、許可ユーザーのリストを管理できます。

1. {{site.data.keyword.Bluemix_notm}} アカウントの[リソース・リスト](https://cloud.ibm.com/resources){:external}に進みます。
2. **「名前」**列のフィルター・テキスト・ボックスで、「**継続的デリバリー**」と入力して、既存のサービスを表示します。
3. サービスごとに、**「名前」**列内のハイパーリンクをクリックします。
4. **「管理」**タブで、必要に応じて、許可ユーザーのリストからユーザーの表示、追加、または削除を行うことができます。

ユーザーは、{{site.data.keyword.contdelivery_short}} サービスの使用時に、自動的に追加されるか、再び追加されます。
{: tip}

### 組織内の {{site.data.keyword.contdelivery_short}} のインスタンスに対するユーザーのカウント方法

{{site.data.keyword.contdelivery_short}} サービスを含む {{site.data.keyword.Bluemix_notm}} 組織内のすべてのユーザーを表示して、許可ユーザーをカウントします。組織とスペースについて詳しくは、[組織およびスペースの作成](/docs/cloud-foundry?topic=cloud-foundry-create_orgs)を参照してください。

{{site.data.keyword.Bluemix_notm}} パブリック環境において組織内のユーザーのリストを表示するには、メニュー・バーから**「管理」>「アカウント」**をクリックします。 次に、**「Cloud Foundry の組織」**をクリックします。

### 請求と使用量の情報の表示方法

{{site.data.keyword.Bluemix_notm}} パブリック環境の、お客様のアカウント内の {{site.data.keyword.contdelivery_short}} サービスにおけるすべてのインスタンスと、各インスタンスに対して報告されたユーザー数やパイプラインの実行数を表示できます。

1. メニュー・バーで、**「管理」>「請求および使用量」**をクリックします。
2. **「使用量」**をクリックします。
3. **「サービス」**セクションで、{{site.data.keyword.contdelivery_short}} サービスの**「プランの表示」**をクリックします。
4. 情報を表示する対象となるプランの**「詳細を表示」**をクリックします。
5. 使用状況の情報を表示する対象となる {{site.data.keyword.contdelivery_short}} のインスタンスの**「インスタンスの詳細の表示」**をクリックします。

`AUTHORIZED_USERS_PER_MONTH` メトリックは、日次でカウントされるユーザー数の 1 カ月の平均に基づいて計算されます。
{: tip}

### サービス・プランの制限を超えた場合

ライト・サービス・プランでは、実行できる Delivery Pipeline ジョブの数やストレージ使用量など、他の制限が課されます。プランの説明について詳しくは、[サービス・カタログ](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}を参照してください。請求対象期間内にプランのいずれかの制限を超過すると、サービスが一時停止します。例えば、Delivery Pipeline ジョブが、請求対象期間の残りの期間に実行されなくなります。

## Delivery Pipeline の使用
{: #pipeline_usage}

容認される使用行動としては以下の行動があります。ただし、これらに限定されるわけではありません。

* サポート対象プログラミング言語用の成果物のコンパイルとアセンブリー。
* アプリケーション成果物、構成、およびサポートするリソースまたはサービスの自動デプロイメント。
* 開発プロセスの結果としてトリガーされる、テスト、妥当性検査、その他の開発イベント生成行動。

許可されない使用行動としては以下の行動があります。ただし、これらに限定されるわけではありません。

* 一般的な計算行動でのパイプライン・ジョブまたは作業者の使用。例えば、ビットコインのマイニング、分散サービス妨害攻撃、および {{site.data.keyword.Bluemix_notm}} プラットフォーム内の他のクライアントやユーザー、または一般的なインターネット・ユーザーに対する悪意のある動作や攻撃的動作。
* ヘイト・スピーチや、IBM ビジネス・コンダクト・ガイドラインに違反するその他の活動をプロモートするサイトまたはサービスのための通常の開発プロセスでの使用。
* {{site.data.keyword.Bluemix_notm}} またはその他のサイトに対する悪意のある侵入または攻撃のためのイベント生成行動の使用。

{{site.data.keyword.contdelivery_short}} サービスの容認される使用行動または [IBM ビジネス・コンダクト・ガイドライン](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external}に違反するユーザーは、IBM の判断で、予告なしに使用不可にする可能性があります。ユーザーが違反アクションについて通知を受け取った後に使用行動を訂正した場合は、IBM の判断で一部のサービスを復元する可能性があります。 そうでない場合、アカウントは一時停止または停止となる可能性があります。

## Git Repos and Issue Tracking の制限
{: #git_limitations}

{{site.data.keyword.gitrepos}} は、GitLab Community Edition をベースとして作成され、IBM が {{site.data.keyword.Bluemix_notm}} 上にホストするものですが、使用できない GitLab オプションがいくつかあります。

 * {{site.data.keyword.Bluemix_notm}} の継続的統合と継続的デリバリーは、{{site.data.keyword.deliverypipeline}} が提供するため、GitLab の継続的統合機能はサポートされません。
 * 管理は IBM が行うため、GitLab の管理機能は使用できません。
 * {{site.data.keyword.gitrepos}} をフルに利用できない場合があります。

## Git Repos and Issue Tracking のユーザー情報とコンテンツ
{: #git_projects}

{{site.data.keyword.gitrepos}} プロジェクトには次の 3 つのタイプがあります。

  1. パブリック・プロジェクトは、すべてのサイト訪問者が閲覧できます。 パブリック・プロジェクトのコンテンツは、プロジェクトに招待されていなくても {{site.data.keyword.contdelivery_short}} にアクセスしたすべてのユーザーが閲覧できます。
  2. プライベート・プロジェクトは、選択されたユーザーのみが閲覧できます。ユーザーにプロジェクトへのアクセス権を付与する方法について詳しくは、[Project's members](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external} を参照してください。
  3. 内部プロジェクトは、ログインしているすべてのユーザーが閲覧できます。 {{site.data.keyword.Bluemix_notm}} アカウントを持つすべてのユーザーが、これらのプロジェクトを閲覧できます。

プロジェクト・タイプは、プロジェクトの設定で変更できます。 プロジェクトの設定について詳しくは、[How to change project visibility](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external} を参照してください。

{{site.data.keyword.gitrepos}} を使用する場合、プロジェクトに投稿したコンテンツには、そのプロジェクトに指定されている使用条件に基づくライセンスが交付されます。 プロジェクトを作成するときに、コンテンツに適用するライセンスについて説明したファイルを含めてください。 プロジェクトに投稿すると、コミットに関連付けられた名前と E メール・アドレスが公開される可能性があります。 {{site.data.keyword.gitrepos}} Web インターフェースを使用してコミットを作成した場合は、{{site.data.keyword.Bluemix_notm}} アカウントに関連付けられた E メール・アドレスが使用されます。
