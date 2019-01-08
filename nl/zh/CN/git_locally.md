---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 设置本地客户机以使用 Git 源代码控制
{: #git_local}


您可以在本地或在 Eclipse Orion Web IDE 中，管理和使用 GitHub、GitHub Enterprise 或 Git Repos and Issue Tracking 存储库中的源代码。要在本地工作，请使用 Git 客户机（例如，Git 命令行界面）克隆存储库，然后使用您喜欢的编辑器来编辑代码。如果是在 Eclipse 中工作，那么可以安装用于版本控制的 EGit 插件。

## 从命令行克隆 Git 项目


## 开始之前
{: #git_before_clone}

1. 要在浏览器外部访问 Git 服务器，可能需要创建个人访问令牌或 SSH 密钥来进行认证。下表显示了设置认证需要执行的操作。

|Git 类型|HTTPS 设置|HTTPS 使用|SSH 设置|
|:-----------|:-------------|:------------|:-------------|
|Git Repos and Issue Tracking (git.ng.bluemix.com)|[个人访问令牌](/docs/services/ContinuousDelivery/git_working.html#git_authentication)|Git Repos and Issue Tracking 用户名（不是您的 IBM 标识）和个人访问令牌|[配置 SSH 密钥](/docs/services/ContinuousDelivery/git_working.html#git_authentication)|
|公共 GitHub (github.com)|个人访问令牌不是必需的，但您可以设置并使用个人访问令牌|GitHub 用户名和密码，或 GitHub 用户名和个人访问令牌，或仅将个人访问令牌作为用户名|[配置 GitHub SSH 密钥](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)|
|GitHub Enterprise|[个人访问令牌](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth)|GitHub Enterprise 用户名（不是您的 IBM 标识）和个人访问令牌|[配置 GitHub Enterprise SSH 密钥](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth)|

如果更愿意使用 SSH，那么可以在所有 Git 服务器中复用单个密钥。如先前链接中所述，创建或找到密钥并在每个服务器中对其进行配置。如果使用口令创建密钥，那么在使用该密钥时，系统将提示您输入口令。
{: tip}

2. 如果要使用 Git 命令行，请完成以下步骤：

    a. 检查是否安装了 Git。在命令行上，输入 `git version`。如果安装了 Git，那么将显示版本号，然后您可以开始使用。

    b. 如果未安装 Git，请[转至 Git Web 站点 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://git-scm.com/downloads){: new_window}。

    c. 下载并安装适用于您的操作系统的版本。可以接受缺省安装值。


### 克隆项目
{: #git_clone}

通过克隆 Git 存储库来创建项目文件的本地副本，以便您可以使用任何桌面工具在 Web IDE 外部访问存储库内容。

1. 从工具链的“概述”页面中，单击要克隆的存储库的卡。

2. 收集存储库 URL：

   a. 在 GitHub 中，单击**克隆或下载**。要使用 HTTPS，请选择**使用 HTTPS**。要使用 SSH，请单击**使用 SSH**。单击“剪贴板”图标以复制 URL。

   b. 在 Git Repos and Issue Tracking 中，选择 **HTTPS** 或 **SSH**，然后复制字段中的 URL。

3. 打开命令行。

4. 将目录切换到希望 Git 存储库的本地副本所在的目录。

5. 输入 `git clone`，粘贴 URL，然后按 Enter 键。

6. 如果系统提示您进行认证，请输入上表中定义的相应信息。


下载完成后，在存储库中即有本地版本的文件。有关使用 Git 的更多信息，请参阅 [Git 文档 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://git-scm.com/doc){: new_window}.


## 使用 Eclipse 和 EGit 插件访问存储库
{: #git_egit}

如果使用的是 Eclipse，并且具有使用 Git 进行源代码控制的项目，那么可以使用 EGit 插件通过 Eclipse 来管理存储库。有关安装和配置 EGit 的指示信息，请参阅 [EGit 教程 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
如果使用的是 Git Repos and Issue Tracking，请参阅 [Git Repos and Issue Tracking](git_working.html#git_local)。

## 使用 IBM Eclipse Tools 进行开发
{: #git_eclipse_tools}

IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} 提供了可安装到 Eclipse 环境中的插件，用于将 IDE 与 {{site.data.keyword.Bluemix_notm}} 集成。

使用这些工具，可以直接从 Eclipse IDE 或 IBM WebSphere&reg; Application Server Developer Tools (WDT) 将以下类型的文件和服务器部署到 {{site.data.keyword.Bluemix_notm}}：

* JavaScript 文件
* WAR（Web 归档）文件
* EAR（企业归档）文件
* Liberty Profile 打包服务器

还可以创建服务，将其链接到应用程序，以及在部署过程中定义环境变量。有关 IBM Eclipse Tools 的更多信息，请参阅[使用 IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} 部署应用程序](/docs/manageapps/eclipsetools/eclipsetools.html)。
