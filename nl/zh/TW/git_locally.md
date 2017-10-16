---

copyright:
  years: 2015, 2017
lastupdated: "2017-7-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# 設定本端用戶端使用 Git 來源控制
{: #git_local}


您可以在 GitHub、GitHub Enterprise 或 Git Repos and Issue Tracking 儲存庫中、在本端或在 Eclipse Orion Web IDE 中管理及使用原始碼。若要在本端運作，請使用 Git 用戶端（例如 Git 指令行介面）來複製儲存庫，並使用您最愛的編輯器來編輯程式碼。如果您在 Eclipse 中運作，則可以安裝 EGit 外掛程式來進行版本控制。

## 從指令行複製 Git 專案


## 開始之前
{: #git_before_clone}

1. 若要在瀏覽器外部存取 Git 伺服器，您可能需要建立個人存取記號或 SSH 金鑰來進行鑑別。下表顯示設定鑑別所需進行的作業。

| Git 類型  | HTTPS 設定 | HTTPS 使用 |  SSH 設定 |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com) | [個人存取記號](/docs/ContinuousDelivery/git_working.html#create_pat) | Git Repos and Issue tracking 使用者名稱（非 IBM ID）及個人存取記號 | [配置 SSH 金鑰](/docs/ContinuousDelivery/git_working.html#create_ssh) |
| 公用 GitHub (github.com) | 不需要個人存取記號，但您可以設定並使用它 | GitHub 使用者名稱和密碼，或 GitHub 使用者名稱及「個人存取記號」，或只是以個人存取記號作為使用者名稱 | [配置 GitHub SSH 金鑰](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [個人存取記號](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) | GitHub Enterprise 使用者名稱（非 IBM ID）及個人存取記號 | [配置 GitHub Enterprise SSH 金鑰](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) |

**附註**：如果您偏好使用 SSH，則可以跨所有 Git 伺服器重複使用單一金鑰。建立或找到金鑰，並在每一部伺服器中進行配置（如先前鏈結所述）。如果您使用通行詞組來建立金鑰，則系統會在您使用金鑰時提示您輸入該通行詞組。

2. 如果您要使用 Git 指令行，請執行下列動作：

    a. 檢查是否已安裝 Git。在指令行上，鍵入 `git version`。如果已安裝 Git，則會顯示版本號碼，而且您可以開始使用。

    b. 如果未安裝 Git，請[移至 Git 網站 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://git-scm.com/downloads){: new_window}。

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


完成下載之後，儲存庫中就會有檔案的本端版本。如需使用 Git 的相關資訊，請參閱 [Git 文件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]](http://git-scm.com/doc){: new_window}.


## 使用 Eclipse 及 EGit 外掛程式存取儲存庫
{: #git_egit}

如果您使用 Eclipse，並且具有使用 Git 進行來源控制的專案，則可以使用 EGit 外掛程式，以從 Eclipse 管理儲存庫。如需安裝及配置 EGit 的指示，請參閱 [EGit 指導教學 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
如果您使用 Git Repos and Issue Tracking 並且發生任何問題，請參閱 [Git Repos and Issue Tracking](git_working.html#git_local)。

## 使用 IBM Eclipse Tools 進行開發
{: #git_eclipse_tools}

您可以將 IBM Eclipse Tools for Bluemix 所提供的外掛程式安裝至 Eclipse 環境，以整合 IDE 與 Bluemix。

您可以使用這些工具，直接從 Eclipse IDE 或 IBM WebSphere&reg; Application Server Developer Tools (WDT) 將下列類型的檔案及伺服器部署至 Bluemix 伺服器：

* JavaScript 檔案
* WAR（Web 保存）檔案
* EAR（企業保存）檔案
* Liberty 設定檔包裝伺服器

您也可以建立服務，並將它們鏈結至應用程式，並在部署期間定義環境變數。如需 IBM Eclipse Tools 的相關資訊，請參閱[使用 IBM Eclipse Tools for Bluemix 部署應用程式](../../manageapps/eclipsetools/eclipsetools.html)。
