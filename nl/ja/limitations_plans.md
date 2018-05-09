---

copyright:
  years: 2016, 2018
lastupdated: "2018-4-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# プランの制限と使用
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}} の使用は、{{site.data.keyword.Bluemix_notm}} プラットフォーム、あるいはその他の互換性のある Platform as a Service または Infrastructure as a Service のオファリングでのアプリケーションの構築、デプロイ、テスト、および進行中の運用に制限されています。

## 許可ユーザー
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} サービス・プランは、サービス・インスタンスの許可ユーザー数に基づいて定義され、価格設定されます。以下に示すユーザーを含め、作業に貢献するすべてのユーザーを許可ユーザーとしてカウントする必要があります。

 * {{site.data.keyword.gitrepos}} リポジトリー内の問題、問題ボード、ソース・コード、その他の成果物を扱うユーザー。
 * デリバリー・パイプラインの状況を操作、トリガー (UI で直接、またはリポジトリーにコミットすることによって間接的に)、または表示するユーザー。
 * Eclipse Orion {{site.data.keyword.webide}} を扱うユーザー。
 
### ユーザーのカウント方法

{{site.data.keyword.contdelivery_short}} サービスを含む Cloud 組織内のすべてのユーザーを表示して、許可ユーザーをカウントします。 

組織内のユーザーのリストを表示するには、メニュー・バーから**「管理」>「アカウント」>「Cloud Foundry の組織」**をクリックします。

また、お客様のアカウント内の {{site.data.keyword.contdelivery_short}} サービスにおけるすべてのインスタンスと、各インスタンスに対して報告されたユーザー数も表示できます。

1. メニュー・バーで、**「管理」>「アカウント」>「Cloud Foundry の組織」**をクリックします。
2. **「使用状況ダッシュボード」**をクリックします。

### サービス・プランの制限を超えた場合 

サービス・プランによっては、実行できる Delivery Pipeline ジョブの数やストレージ使用量など、他の制限が課される場合があります。詳しくは、カタログ内のプランの説明を参照してください。請求対象期間内にプランのいずれかの制限を超過すると、サービスが一時停止する場合があります。例えば、Delivery Pipeline ジョブが、請求対象期間の残りの期間に実行されなくなる場合があります。

## Delivery Pipeline の使用
{: #pipeline_usage}

容認される使用行動としては以下の行動があります。ただし、これらに限定されるわけではありません。

* サポート対象プログラミング言語用の成果物のコンパイルとアセンブリー
* アプリケーション成果物、構成、およびサポートするリソースまたはサービスの自動デプロイメント
* 開発プロセスの結果としてトリガーされる、テスト、妥当性検査、およびその他の開発イベント生成行動

許可されない使用行動としては以下の行動があります。ただし、これらに限定されるわけではありません。

* 一般的な計算行動でのパイプライン・ジョブまたは作業者の使用。例えば、ビットコインのマイニング、分散サービス妨害攻撃、および IBM Cloud プラットフォーム内の他のクライアントやユーザー、または一般的なインターネット・ユーザーに対する悪意のある動作や攻撃的動作
* ヘイト・スピーチや、IBM ビジネス・コンダクト・ガイドラインに違反するその他の活動をプロモートするサイトまたはサービスのための通常の開発プロセスでの使用。
* {{site.data.keyword.Bluemix_notm}} またはその他のサイトに対する悪意のある侵入または攻撃のためのイベント生成行動の使用

{{site.data.keyword.contdelivery_short}} サービスの容認される使用行動または [IBM ビジネス・コンダクト・ガイドライン![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window}に違反するユーザーは、IBM の判断で、予告なしに使用不可にする可能性があります。 ユーザーが違反アクションについて通知を受け取った後に使用行動を訂正した場合は、IBM の判断で一部のサービスを復元する可能性があります。 そうでない場合、アカウントは一時停止または停止となる可能性があります。

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
  2. プライベート・プロジェクトは、選択されたユーザーのみが閲覧できます。 ユーザーにプロジェクトへのアクセス権を付与する方法について詳しくは、[Project users ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window} を参照してください。
  3. 内部プロジェクトは、ログインしているすべてのユーザーが閲覧できます。 {{site.data.keyword.Bluemix_notm}} アカウントを持つすべてのユーザーが、これらのプロジェクトを閲覧できます。

プロジェクト・タイプは、プロジェクトの設定で変更できます。 詳しくは、[How to change project visibility ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window} を参照してください。

{{site.data.keyword.gitrepos}} を使用する場合、プロジェクトに投稿したコンテンツには、そのプロジェクトに指定されている使用条件に基づくライセンスが交付されます。 プロジェクトを作成するときに、コンテンツに適用するライセンスについて説明したファイルを含めてください。 プロジェクトに投稿すると、コミットに関連付けられた名前と E メール・アドレスが公開される可能性があります。 {{site.data.keyword.gitrepos}} Web インターフェースを使用してコミットを作成した場合は、{{site.data.keyword.Bluemix_notm}} アカウントに関連付けられた E メール・アドレスが使用されます。

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
