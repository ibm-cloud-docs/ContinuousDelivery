---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

IBM によってホストされ、[GitLab Community Edition ](https://about.gitlab.com/){: external} 上に構築されている Git リポジトリーと Issue Tracker を使用して、チームでの共同作業やソース・コードの管理を行います。
{: shortdesc}

プロジェクトで共同作業する個人的関係やビジネス上の関係がある人だけを招待してください。 プロジェクトで共同作業をする以外の目的で Git レポへの招待を使用するユーザーによるサービスへのアクセスは、中断されたり取り消されたりする場合があります。
{: important}

GitLab の代替機能として、GitHub と Git コマンド・ラインを利用できます。
{: note}

規制対象データを Git レポ内のファイルや問題に保存しないでください。 規制対象データ用の手順は現在機能していません。
{: tip}

{{site.data.keyword.gitrepos}} ツール統合は、以下に示すさまざまな方法でチームのコード管理とコラボレーションをサポートします。
   * コードの安全性を保つ、きめ細かいアクセス制御を通じて Git リポジトリーを管理する
   * マージ要求を介してコードを検討し、コラボレーションを強化する
   * Issue Tracker を介して問題を追跡し、アイデアを共有する
   * Wiki システム上にプロジェクトを文書化する

このツール統合は GitLab Community Edition 上に構築され、IBM によって {{site.data.keyword.Bluemix_notm}} プラットフォーム上でホストされているため、一部の GitLab オプションは使用できません。 例えば、Delivery Pipeline は、{{site.data.keyword.Bluemix_notm}} の継続的統合と継続的デリバリーを提供しているため、GitLab の継続的統合フィーチャーはサポートされません。 さらに、管理機能は、IBM によって管理されているため使用できません。
{: tip}


## {{site.data.keyword.gitrepos}} をローカルに使用する
{: #git_locally}

{{site.data.keyword.gitrepos}} に保管されている Git リポジトリーに、ローカルからアクセスできます。 ローカルで Git をセットアップする手順については、[Start using Git on the command line](https://us-south.git.cloud.ibm.com/help/gitlab-basics/start-using-git){: external} を参照してください。

{{site.data.keyword.gitrepos}} は、TLS1.2 を使用する HTTPS 接続のみをサポートします。 Eclipse を使用して接続する場合は、通常、使用する Java&trade; バージョンでこのプロトコルを指定する必要があります。そのためには、eclipse.ini ファイルに `-Dhttps.protocols=TLSv1.2` を追加してから Eclipse を再始動します。
{: tip}

## {{site.data.keyword.gitrepos}} での認証
{: #git_authentication}

{{site.data.keyword.Bluemix_notm}} ログインとパスワードは、Web ブラウザーでの {{site.data.keyword.gitrepos}} の認証のみに使用されます。 外部 Git クライアントからの認証に {{site.data.keyword.Bluemix_notm}} のユーザー資格情報を使用することはできません。 ローカル Git リポジトリーから `clone` または `push` などのリモート Git 操作を完了するには、個人用アクセス・トークンまたは SSH 鍵を使用して {{site.data.keyword.gitrepos}} の認証を行う必要があります。

### 個人用アクセス・トークンの作成
{: #create_pat}

HTTPS 経由で Git リポジトリーの認証を受けるために、個人用アクセス・トークンを作成する必要があります。
{: tip}

1. {{site.data.keyword.gitrepos}} ユーザー設定ダッシュボードの[「アクセス・トークン」ページ](https://us-south.git.cloud.ibm.com/profile/personal_access_tokens){: external}で、アクセス・トークンを作成するアプリケーションの名前を入力します。例えば、`「Git CLI」`と入力します。
1. オプション: アクセス・トークンの有効期限日を選択します。
1. **api** チェック・ボックスを選択して、スコープとして api を使用する個人用アクセス・トークンを作成します。
1. **「個人用アクセス・トークンの作成 (Create Personal Access Token)」**をクリックします。 後で使用するために、アクセス・トークンを安全な場所にメモしておきます。
1. [アカウント・ページ](https://us-south.git.cloud.ibm.com/profile/account){: external}の「ユーザー名の変更」セクションで自分の {{site.data.keyword.gitrepos}} ユーザー名を見つけます。ユーザー名は、作成した個人用 Git リポジトリーの URL の最初のセグメントとしても表示されています。
1. {{site.data.keyword.gitrepos}} ユーザー名と個人用アクセス・トークンを使用して、外部 Git クライアントから Git リポジトリーの認証を受けます。

詳しくは、[Personal access tokens](https://us-south.git.cloud.ibm.com/help/api/README.html#personal-access-tokens){: external} を参照してください。

### SSH 鍵の作成  
{:create_ssh }

SSH 鍵を作成するには、[How to create your SSH Keys](https://us-south.git.cloud.ibm.com/help/gitlab-basics/create-your-ssh-keys){: external} を参照してください。SSH 認証を使用してリポジトリーにアクセスするには、プロキシーおよびファイアウォールの追加構成が必要な場合があります。

詳しくは、[SSH](https://us-south.git.cloud.ibm.com/help/ssh/README){: external} を参照してください。

## 物理ファイルおよびリポジトリーのサイズ制限
{: #git_limits}

ファイルは、厳密に 100 MB に制限されています。 推奨されているリポジトリー・サイズ制限は 1 GB です。 リポジトリーが 1 GB を超えると、リポジトリー・サイズの削減を要求する E メールを受け取る可能性があります。

## チュートリアルを始める: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

[IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external} の以下のチュートリアルのいずれかをご確認ください。

  * [「Develop a Cloud Foundry app」ツールチェーンを使用して、初めてツールチェーンを作成し、使用します](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}。テンプレートからオープン・ツールチェーンを作成し、そのツールチェーンを使用して「Hello World」アプリの継続的デリバリーを行う方法を学習します。

  * [「Develop and test microservices on Cloud Foundry」ツールチェーンを使用します](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}。3 つのマイクロサービスを使用するテンプレートからツールチェーンを作成し、そのツールチェーンを使用してオンライン・ストアの継続的デリバリーを行う方法を説明します。
