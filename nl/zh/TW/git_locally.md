---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: Git source control, personal access token, Git repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# 設定本端用戶端使用 Git 來源控制
{: #git_local}


您可以在 GitHub、GitHub Enterprise 或 {{site.data.keyword.gitrepos}} 儲存庫中、在本端或者在 Eclipse Orion {{site.data.keyword.webide}} 中管理及使用原始碼。若要在本端運作，請使用 Git 指令行介面這類 Git 用戶端來複製儲存庫，並使用您最愛的編輯器來編輯程式碼。如果您在 Eclipse 中運作，則可以安裝 EGit 外掛程式來進行版本控制。

## 從指令行複製 Git 專案


## 開始之前
{: #git_before_clone}

1. 若要在瀏覽器外部存取 Git 伺服器，您必須建立個人存取記號或 SSH 金鑰來進行鑑別。下表顯示設定鑑別所需進行的作業。

|Git 類型  |HTTPS 設定 |HTTPS 使用 |SSH 設定 |
|:-----------|:-------------|:------------|:-------------|
|Git Repos and Issue Tracking|[個人存取記號](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) |Git Repos and Issue tracking 使用者名稱（非 IBM ID）及個人存取記號 |[配置 SSH 金鑰](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#creating-an-ssh-key) |
| Public GitHub (github.com) |不需要個人存取記號，但您可以設定並使用它 |GitHub 使用者名稱和密碼，或 GitHub 使用者名稱及「個人存取記號」，或只是以個人存取記號作為使用者名稱 |[配置 GitHub SSH 金鑰](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: external} |
|GitHub Enterprise |[個人存取記號](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) |GitHub Enterprise 使用者名稱（非 IBM ID）及個人存取記號 |[配置 GitHub Enterprise SSH 金鑰](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) |
{: caption="表 1. Git 鑑別設定" caption-side="top"}

如果您偏好使用 SSH，則可以跨所有 Git 伺服器重複使用單一金鑰。建立或找到金鑰，並在每一部伺服器中進行配置（如先前鏈結所述）。如果您使用通行詞組來建立金鑰，則系統會在您使用金鑰時提示您輸入該通行詞組。
{: tip}

2. 如果您要使用 Git 指令行，請完成下列步驟：

    a. 檢查是否已安裝 Git。在指令行上，鍵入 `git version`。如果已安裝 Git，則會顯示版本號碼，而且您可以開始使用。

    b. 如果未安裝 Git，請[移至 Git 網站](http://git-scm.com/downloads){: external}。

    c. 下載並安裝您作業系統的版本。您可以接受預設安裝值。


### 複製專案
{: #git_clone}

複製 Git 儲存庫，以建立專案檔的本端副本，因此，可以使用任何桌面工具在 Web IDE 外部存取儲存庫內容。

1. 從工具鏈的「概觀」頁面中，按一下您要複製的儲存庫卡片。

2. 收集儲存庫 URL：

   a. 在 GitHub 中，按一下**複製或下載**。若要使用 HTTPS，請選取**使用 HTTPS**。若要使用 SSH，請按一下**使用 SSH**。按一下剪貼簿圖示，以複製 URL。

   b. 在 Git Repos and Issue Tracking 中，選取 **HTTPS** 或 **SSH**，並複製欄位中的 URL。

3. 開啟指令行。

4. 將目錄切換至您要放置 Git 儲存庫本端副本的位置。

5. 鍵入 `git clone`，貼上 URL，然後按 Enter 鍵。

6. 如果系統提示您進行鑑別，請輸入適當的資訊（如上表所定義）。


完成下載之後，儲存庫中就會有檔案的本端版本。如需使用 Git 的相關資訊，請參閱 [Git 文件](http://git-scm.com/doc){: external}。


## 使用 Eclipse 及 EGit 外掛程式存取儲存庫
{: #git_egit}

如果您使用 Eclipse，並且具有使用 Git 進行來源控制的專案，則可以使用 EGit 外掛程式，以從 Eclipse 管理儲存庫。如需如何安裝及配置 EGit 的相關資訊，請參閱 [EGit 指導教學](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: external}。

如果您使用 {{site.data.keyword.gitrepos}} 並且發生任何問題，則請參閱 [{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_local) 文件。
