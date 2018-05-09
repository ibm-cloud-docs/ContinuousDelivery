---

copyright:
  years: 2015, 2018
lastupdated: "2018-2-26"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# {{site.data.keyword.gitrepos}}
{: #git_working}

IBM によってホストされ、[GitLab Community Edition ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://about.gitlab.com/){:new_window}上に構築されている Git リポジトリーおよび Issue Tracker を使用して、チームでの共同作業およびソース・コードの管理を行います。
{: shortdesc}

{{site.data.keyword.gitrepos}} ツール統合は、以下に示すさまざまな方法でチームのコード管理とコラボレーションをサポートします。
   * コードの安全性を保つ、きめ細かいアクセス制御を通じて Git リポジトリーを管理する
   * マージ要求を介してコードを検討し、コラボレーションを強化する
   * Issue Tracker を介して問題を追跡し、アイデアを共有する
   * Wiki システム上にプロジェクトを文書化する

**注:** このツール統合は GitLab Community Edition 上に構築され、IBM によって {{site.data.keyword.Bluemix_notm}} プラットフォーム上でホストされているため、一部の GitLab オプションは使用できません。 例えば、Delivery Pipeline は、{{site.data.keyword.Bluemix_notm}} の継続的統合と継続的デリバリーを提供しているため、GitLab の継続的統合フィーチャーはサポートされません。 さらに、管理機能は、IBM によって管理されているため使用できません。

## {{site.data.keyword.gitrepos}} をローカルに使用する
{: #git_local}

{{site.data.keyword.gitrepos}} に保管されている Git リポジトリーに、ローカルからアクセスできます。 ローカルで Git をセットアップする手順については、[Start using Git on the command line (コマンド・ラインでの Git の使用の開始) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window} を参照してください。

**ヒント**: {{site.data.keyword.gitrepos}} は、TLS1.2 を使用する HTTPS 接続のみをサポートします。 Eclipse を使用して接続する場合は、通常、使用する Java&trade; バージョンでこのプロトコルを指定する必要があります。そのためには、eclipse.ini ファイルに `-Dhttps.protocols=TLSv1.2` を追加してから Eclipse を再始動します。

## {{site.data.keyword.gitrepos}} での認証
{: #git_authentication}

{{site.data.keyword.Bluemix_notm}} ログインとパスワードは、Web ブラウザーでの {{site.data.keyword.gitrepos}} の認証のみに使用されます。 外部 Git クライアントからの認証に {{site.data.keyword.Bluemix_notm}} のユーザー資格情報を使用することはできません。 ローカル Git リポジトリーから `clone` または `push` などのリモート Git 操作を完了するには、個人用アクセス・トークンまたは SSH 鍵を使用して {{site.data.keyword.gitrepos}} の認証を行う必要があります。

### 個人用アクセス・トークンの作成
{: #create_pat}

**重要:** HTTPS 経由で Git リポジトリーの認証を受けるために、個人用アクセス・トークンを作成する必要があります。

1. {{site.data.keyword.gitrepos}} ユーザー設定ダッシュボードの[「アクセス・トークン」ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} で、アクセス・トークンを作成するアプリケーションの名前を入力します。 例えば、`「Git CLI」`と入力します。
1. オプション: アクセス・トークンの有効期限日を選択します。
1. **api** チェック・ボックスを選択して、スコープとして api を使用する個人用アクセス・トークンを作成します。
1. **「個人用アクセス・トークンの作成 (Create Personal Access Token)」**をクリックします。 後で使用するために、アクセス・トークンを安全な場所にメモしておきます。
1. [「Account」ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} の「Change username」セクションで自分の {{site.data.keyword.gitrepos}} ユーザー名を見つけます。 ユーザー名は、作成した個人用 Git リポジトリーの URL の最初のセグメントとしても表示されています。
1. {{site.data.keyword.gitrepos}} ユーザー名と個人用アクセス・トークンを使用して、外部 Git クライアントから Git リポジトリーの認証を受けます。

詳しくは、[Personal access tokens ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window} を参照してください。

### SSH 鍵の作成  
{:create_ssh }

SSH 鍵を作成するには、[How to create your SSH Keys ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window} を参照してください。 SSH 認証を使用してリポジトリーにアクセスするには、プロキシーおよびファイアウォールの追加構成が必要な場合があります。

詳しくは、[SSH ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://git.ng.bluemix.net/help/ssh/README){:new_window} を参照してください。

## 物理ファイルおよびリポジトリーのサイズ制限
{: #git_limits}

ファイルは、厳密に 100 MB に制限されています。 推奨されているリポジトリー・サイズ制限は 1 GB です。 リポジトリーが 1 GB を超えると、リポジトリー・サイズの削減を要求する E メールを受け取る可能性があります。

## チュートリアルを始める: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

[IBM&reg; Cloud Garage Method ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage){:new_window} の以下のチュートリアルのいずれかをチェックアウトします。

  * [ 「Develop a Cloud Foundry app」ツールチェーンを使用した初めてのツールチェーンの作成と使用 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン ")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。テンプレートからオープン・ツールチェーンを作成し、そのツールチェーンを使用して「Hello World」アプリの継続的デリバリーを行う方法を学習します。

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}。 3 つのマイクロサービスを使用するテンプレートからツールチェーンを作成し、そのツールチェーンを使用してオンライン・ストアの継続的デリバリーを行う方法を説明します。
