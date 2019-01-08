---

copyright:
  years:  2018
lastupdated: "2018-7-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Identity and Access Management を使用した Continuous Delivery へのユーザー・アクセス権限の管理

リソース・グループ内の {{site.data.keyword.contdelivery_full}} サービス・インスタンスに対する、アカウントのユーザーのアクセス権限は、{{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) によって制御されます。 

**注**: 

* {{site.data.keyword.contdelivery_short}} のサービス・インスタンスに対するユーザー・アクセス権限と、ツールチェーン・インスタンスに対するユーザー・アクセス権限は別々に管理されます。 リソース・グループ内のツールチェーンに対するユーザー・アクセス権限の管理について詳しくは、[Identity and Access Management を使用したツールチェーンへのユーザー・アクセス権限の管理](/docs/services/ContinuousDelivery/toolchains_iam_security.html){: new_window}を参照してください。

* Cloud Foundry 組織内のツールチェーンに対するユーザー・アクセス権限は、リソース・グループ内のツールチェーンに対するユーザー・アクセス権限と異なる方法で管理されます。 Cloud Foundry 組織内のツールチェーンに対するユーザー・アクセス権限の管理について詳しくは、[Cloud Foundry の組織内のツールチェーンへのアクセスの管理](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}を参照してください。

ご使用のアカウント内の {{site.data.keyword.contdelivery_short}} サービスにアクセスするすべてのユーザーには、IAM ユーザー役割が定義されたアクセス・ポリシーを割り当てる必要があります。 そのポリシーによって、選択したサービスまたはインスタンスのコンテキスト内でユーザーが実行できるアクションが決まります。 許可されるアクションは、サービス上で実行できる操作として、{{site.data.keyword.Bluemix_notm}} サービスによってカスタマイズされて定義されます。 その後、アクションは IAM ユーザー役割にマップされます。

ポリシーにより、アクセス権限をさまざまなレベルで付与することができます。 以下のようなオプションがあります。 

* アカウント内のすべてのサービス・インスタンスに対するアクセス権限
* アカウント内の個別のサービス・インスタンスに対するアクセス権限
* インスタンス内の特定のリソースに対するアクセス権限
* アカウント内のすべての IAM 対応サービスに対するアクセス権限

アクセス・ポリシーの有効範囲を定義した後に、役割を割り当てることができます。 {{site.data.keyword.contdelivery_short}} サービス内で各役割が実行できるアクションを示した、下記の表を参照してください。

下記の表は、プラットフォーム管理役割にマップされたアクションの詳細を示しています。 プラットフォーム管理役割により、ユーザーはプラットフォーム・レベルでサービス・リソースに対するタスクを実行できます。例えば、サービスに対するユーザー・アクセス権限の割り当て、サービス ID の作成または削除、インスタンスの作成、アプリケーションへのインスタンスのバインドなどを実行できます。

| プラットフォーム管理役割 | アクションの説明 | アクションの例|
|:-----------------|:-----------------|:-----------------|
| ビューアー、オペレーター | {{site.data.keyword.contdelivery_short}} サービスのインスタンスを表示します。 | <ul><li>{{site.data.keyword.contdelivery_short}} サービス・インスタンスをクリックして、ダッシュボードを開く。</li>|</ul>
| エディター、管理者 | {{site.data.keyword.contdelivery_short}} サービスのインスタンスの作成、表示、更新、プラン変更、削除を行います。 |<ul><li>リソース・グループに {{site.data.keyword.contdelivery_short}} のインスタンスをプロビジョンする。</li><li>リソース・グループから {{site.data.keyword.contdelivery_short}} のインスタンスを削除する。</li><li>{{site.data.keyword.contdelivery_short}} インスタンスのプランをライトからプロフェッショナルに変更する。</li></ul> |
| 管理者 | 許可ユーザー・リストを更新します。| <ul><li>許可ユーザー・リストにユーザーを追加する。</li><li>許可ユーザー・リストからユーザーを削除する。</li></ul> |
{: caption="表 1. IAM ユーザーの役割とアクション" caption-side="top"}

 {{site.data.keyword.contdelivery_short}} のために、以下のアクションが用意されています。

| アクション | サービスに対する操作 | 役割
|:-----------------|:-----------------|:--------------|
| 作成 | リソース・グループに {{site.data.keyword.contdelivery_short}} サービス・インスタンスをプロビジョンします。 | 管理者、エディター |
| 更新 | リソース・グループ内の {{site.data.keyword.contdelivery_short}} サービス・インスタンスを更新します。 例えば、サービス・インスタンスの名前を変更します。 | 管理者、エディター |
| update_plan | リソース・グループ内の {{site.data.keyword.contdelivery_short}} サービス・インスタンスのプランを変更します。 | 管理者、エディター |
| 削除 | リソース・グループから {{site.data.keyword.contdelivery_short}} サービス・インスタンスを削除します。 | 管理者、エディター |
| retrieve | リソース・グループ内の {{site.data.keyword.contdelivery_short}} サービス・インスタンスを表示します。 | 管理者、エディター、オペレーター、ビューアー |
| add-auth-users | {{site.data.keyword.contdelivery_short}} サービス・インスタンス内の「管理」タブで、許可ユーザー・リストにエントリーを追加します。 | 管理者、ライター、マネージャー |
| remove-auth-users | {{site.data.keyword.contdelivery_short}} サービス・インスタンス内の「管理」タブで、許可ユーザー・リストからエントリーを削除します。 | 管理者、ライター、マネージャー |
{: caption="表 2. サービスのアクションと操作" caption-side="top"}

次の表は、サービス・アクセス役割にマップされたアクションの詳細を示しています。 ユーザーは、サービス・アクセス役割を持つことで、{{site.data.keyword.contdelivery_short}} にアクセスしたり、{{site.data.keyword.contdelivery_short}} API を呼び出したりすることができます。

| サービス・アクセス役割 | アクションの説明 | アクションの例|
|:-----------------|:-----------------|:-----------------|
| ライター、管理者 | {{site.data.keyword.contdelivery_short}} サービス・インスタンス内の「管理」タブで、許可ユーザー・リストのユーザーを追加および削除します。 | <ul><li>許可ユーザーを追加する。</li><li>許可ユーザーを削除する。</li></ul>|
{: caption="表 3. IAM のサービス・アクセス役割とアクション" caption-side="top"}

UI でのユーザー役割の割り当てについては、[IAM アクセス権限の管理](/docs/iam/mngiam.html#iammanidaccser)を参照してください。

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
