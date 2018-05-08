---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 將 IBM 機密專案升級至工具鏈 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}} 將會逐漸發展成 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}}。進行該變更時，會將專案升級至工具鏈。

準備好升級專案時，會在專案的「概觀」頁面上顯示一則訊息。然後，您可以在「{{site.data.keyword.Bluemix_notm}} 公用」將專案升級至工具鏈。工具鏈會包含原始碼的 Whitewater {{site.data.keyword.ghe_short}} 儲存庫。Whitewater {{site.data.keyword.ghe_short}} 提供給 IBM 團隊以便在 IBM 內提倡和啟用社交編碼。
{: shortdesc}

**{{site.data.keyword.contdelivery_short}} 工具鏈搭配 Whitewater {{site.data.keyword.ghe_short}} 使用時，已經過核准用於 IBM 機密資料。**從 Whitewater {{site.data.keyword.ghe_short}} 儲存庫接收輸入的 Delivery Pipelines 可以部署至編譯打包 (YS1) 和公用 (YP) 環境。

During在升級期間，會提示您授權 {{site.data.keyword.contdelivery_short}} 代表您存取 Whitewater {{site.data.keyword.ghe_short}}。

## 升級之後將成員新增至 Whitewater {{site.data.keyword.ghe_short}} 儲存庫

如果您的專案使用在 JazzHub 上管理的儲存庫，在升級期間，會在 Whitewater {{site.data.keyword.ghe_short}} 上建立新的儲存庫。升級之後，啟動升級的人必須將團隊成員新增至 Whitewater {{site.data.keyword.ghe_short}} 儲存庫，並確定他們具有正確的專用權，才能存取新的儲存庫。

## 疑難排解

當您嘗試變更管線部署階段的目標時，有時會發生間歇性的問題。發生此問題時，會在**組織**和**空間**欄位顯示錯誤。

此問題一般只發生在您從管線變更目標，使得在升級時建立的管線能正確部署到與之前相同的目標時。

如果您嘗試變更目標，然後發生此問題，請切換目標數次，直到完成**組織**及**空間**欄位。

相關的問題有時會導致部署至 YS1 目標失敗。這種狀況極為少見；如果發生，請重新執行管線。

IBM DevOps Services 團隊正在積極解決這些問題。
