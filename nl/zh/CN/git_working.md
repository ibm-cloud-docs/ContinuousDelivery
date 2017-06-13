---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-6"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# Git Repos and Issue Tracking
{: #git_working}

与您的团队协作，并使用由 IBM 托管且在 [GitLab Community Edition ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://about.gitlab.com/){:new_window} 上构建的 Git 存储库和问题跟踪程序来管理源代码。
{: shortdesc}

{{site.data.keyword.gitrepos}} 工具集成支持团队以多种方式管理代码并协作：
   * 通过可让代码保持安全的细颗粒度访问控制来管理 Git 存储库
   * 通过合并请求复查代码并加强协作
   * 通过问题跟踪程序来跟踪问题并分享构想
   * 在 Wiki 系统上记录项目

**注：**因为此工具集成以 GitLab Community Edition 为基础构建且由 IBM 在 Bluemix 上托管，因此有一些 GitLab 选项不可用。例如，Delivery Pipeline 为 Bluemix 提供持续集成和持续交付，因此在 GitLab 中不支持持续集成功能。此外，管理功能也不可用，因为它们由 IBM 管理。

## 文件和存储库大小限制
{: #git_limits}

文件严格限制为 100 MB。建议的存储库大小限制为 1 GB。如果您的存储库超过 1 GB，那么您可能会收到电子邮件，其中包括减少存储库大小的请求。

## 在本地使用 Git Repos and Issue Tracking
{: #git_local}

可以在本地访问存储在 {{site.data.keyword.gitrepos}} 中的 Git 存储库。有关在本地设置 Git 的指示信息，请参阅[开始在命令行上使用 Git ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}。

**提示**：{{site.data.keyword.gitrepos}} 仅支持使用 TLS1.2 的 HTTPS 连接。如果您使用 Eclipse 进行连接，那么您可能需要通过将`-Dhttps.protocols=TLSv1.2` 添加到 eclipse.ini 文件，然后重新启动 Eclipse，为您的 Java&trade; 版本指定此协议。

## 使用 GitLab 进行认证  
{: #git_authentication}

要从本地 Git 存储库完成远程 Git 操作（如 `clone` 或 `push`），您必须使用个人访问令牌或 SSH 密钥，以通过 GitLab 进行认证。

### 创建个人访问令牌  
要使用 Git 存储库通过 HTTPS 进行认证，您必须创建个人访问令牌。您的 {{site.data.keyword.Bluemix_notm}} 登录和密码仅在浏览器中使用 {{site.data.keyword.gitrepos}}。您无法使用 {{site.data.keyword.Bluemix_notm}} 用户凭证从外部 Git 客户机进行认证。

1. 在 {{site.data.keyword.gitrepos}}“用户设置”仪表板的[访问令牌页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} 上，键入要创建访问令牌的应用程序的名称。例如，`Git CLI`。
1. 可选：选择访问令牌的到期日期。
1. 选择 **API** 复选框以创建使用 API 作为作用域的个人访问令牌。
1. 单击**创建个人访问令牌**。在安全的位置记下访问令牌以供未来使用。
1. 在[帐户页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} 的“更改用户名”部分中，找到 {{site.data.keyword.gitrepos}} 用户名。您的用户名还会显示为您所创建的任何个人 Git 存储库 URL 的第一个分段。
1. 使用 {{site.data.keyword.gitrepos}} 用户名和个人访问令牌，从外部 Git 客户机对 Git 存储库进行认证。

要了解更多信息，请参阅[个人访问令牌 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}。

### 创建 SSH 密钥  
要创建 SSH 密钥，请参阅[如何创建 SSH 密钥 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}。通过 SSH 认证访问存储库可能需要对代理和防火墙进行更多的配置。

要了解更多信息，请参阅 [SSH ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://git.ng.bluemix.net/help/ssh/README){:new_window}。
