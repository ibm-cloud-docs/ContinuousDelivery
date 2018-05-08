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

使用 IBM 所管理並以 [GitLab Community Edition ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://about.gitlab.com/){:new_window} 為建置基礎的 Git 儲存庫及問題追蹤器，來與團隊分工合作並且管理原始碼。
{: shortdesc}

{{site.data.keyword.gitrepos}} 工具整合可支援團隊使用多種方式來管理程式碼以及分工合作：
   * 透過讓程式碼更為安全的精密存取控制，來管理 Git 儲存庫
   * 透過合併要求，來檢閱程式碼並加強協同作業
   * 透過問題追蹤器，來追蹤問題與共用構想
   * 在 Wiki 系統上記載專案

**附註：**因為此工具整合是以 GitLab Community Edition 為建置基礎，並由 IBM 於「{{site.data.keyword.Bluemix_notm}} 平台」上進行管理，所以有一些 GitLab 選項無法使用。例如，Delivery Pipeline 提供 {{site.data.keyword.Bluemix_notm}} 的持續整合及持續交付；因此，不支援 GitLab 中的持續整合特性。此外，無法使用管理功能，因為它們是由 IBM 所管理。

## 在本端使用 {{site.data.keyword.gitrepos}}
{: #git_local}

您可以在本端存取 {{site.data.keyword.gitrepos}} 中所儲存的 Git 儲存庫。如需在本端設定 Git 的指示，請參閱[在指令行上開始使用 Git ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}。

**提示**：{{site.data.keyword.gitrepos}} 只支援使用 TLS1.2 的 HTTPS 連線。如果您使用 Eclipse 來連接，您可能需要為您的 Java&trade; 版本指定此通訊協定，新增 `-Dhttps.protocols=TLSv1.2` 至 eclipse.ini 檔，然後重新啟動 Eclipse。

## 向 {{site.data.keyword.gitrepos}} 進行鑑別
{: #git_authentication}

在 Web 瀏覽器中，只會使用您的 {{site.data.keyword.Bluemix_notm}} 登入及密碼向 {{site.data.keyword.gitrepos}} 進行鑑別。您無法使用 {{site.data.keyword.Bluemix_notm}} 使用者認證從外部 Git 用戶端進行鑑別。若要從本端 Git 儲存庫完成遠端 Git 作業（例如 `clone` 或 `push`），您必須使用個人存取記號或 SSH 金鑰來向 {{site.data.keyword.gitrepos}} 進行鑑別。

### 建立個人存取記號
{: #create_pat}

**重要事項**：若要透過 HTTPS 向 Git 儲存庫進行鑑別，您必須建立個人存取記號。

1. 在 {{site.data.keyword.gitrepos}} User Settings 儀表板上的 [Access Tokens 頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}，鍵入您要為其建立存取記號的應用程式名稱。例如 `Git CLI`。
1. 選用項目：選擇存取記號的到期日期。
1. 選取 **api** 勾選框，以建立使用 api 作為範圍的個人存取記號。
1. 按一下 **Create Personal Access Token**。請將您的存取記號記錄在安全的位置，以供未來使用。
1. 在 [Account 頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} 的 Change username 區段，找到您的 {{site.data.keyword.gitrepos}} 使用者名稱。您的使用者名稱也會顯示為您建立之任何個人 Git 儲存庫 URL 的第一個區段。
1. 使用您的 {{site.data.keyword.gitrepos}} 使用者名稱及個人存取記號，從外部 Git 用戶端向 Git 儲存庫進行鑑別。

若要進一步瞭解，請參閱 [Personal Access Tokens ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}。

### 建立 SSH 金鑰  
{:create_ssh }

若要建立 SSH 金鑰，請參閱 [How to create your SSH Keys ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}。使用 SSH 鑑別來存取儲存庫，可能需要額外配置 Proxy 及防火牆。

若要進一步瞭解，請參閱 [SSH ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://git.ng.bluemix.net/help/ssh/README){:new_window}。

## 實體檔及儲存庫大小限制
{: #git_limits}

檔案嚴格限制為 100 MB。建議的儲存庫大小限制為 1 GB。如果您的儲存庫超出 1 GB，則可能會收到含有減少儲存庫大小要求的電子郵件。

## 使用指導教學：{{site.data.keyword.gitrepos}}
{: #git_tutorials}

請參閱 [IBM&reg; Cloud Garage Method ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage){:new_window} 上的其中一個指導教學：

  * [使用「開發 Cloud Foundry 應用程式」工具鏈建立及使用您的第一個工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}。學習如何從範本建立開放式工具鏈，以及使用工具鏈來持續交付 "Hello World" 應用程式。

  * [使用「在 Cloud Foundry 上開發及測試微服務」工具鏈 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}。學習如何從具有三個微服務的範本建立工具鏈，以及使用工具鏈來持續交付線上商店。
