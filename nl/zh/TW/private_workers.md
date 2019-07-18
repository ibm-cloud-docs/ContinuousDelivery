---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

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


# 使用 {{site.data.keyword.deliverypipeline}} 專用工作者節點
{: #private-workers}

{{site.data.keyword.deliverypipeline}} 會使用公用及專用工作者節點來執行管線工作。依預設，管線工作是藉由在 IBM 管理的公用共用基礎架構上使用公用工作者節點來執行。
{: shortdesc}

在某些情境下，您的 {{site.data.keyword.deliverypipeline}} 可能需要存取內部或內部部署資源。在這些情況下，您可以連接及整合「{{site.data.keyword.deliverypipeline}} 專用工作者節點」，以在您自己的 Kuberneges 基礎架構上執行。

## 必要條件
{: #private_workers_prereqs}

在設定專用工作者節點之前，請確定您下列資源就位：

* Kubernetes 叢集。您必須具有叢集，才能安裝專用工作者節點。您可以提供自己的叢集，也可以從 {{site.data.keyword.containerlong_notm}} [設定叢集](https://cloud.ibm.com/kubernetes/clusters){:external}。

* 具有管線且至少包含一個階段的工具鏈。您可以使用現有的工具鏈或[建立工具鏈](https://cloud.ibm.com/devops/create){:external}。

## 設定 {{site.data.keyword.deliverypipeline}} 專用工作者節點
{: #set_up_private_worker}

請完成下列步驟來設定專用工作者節點：

1. 為您的工具鏈配置「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合。
2. 配置您的 Kubernetes 與專用工作者節點搭配。
3. 在您的管線中使用專用工作者節點。

### 配置 {{site.data.keyword.deliverypipeline}} 專用工作者節點工具整合
{: #configure_private_worker_integration}

請完成下列步驟，為您的工具鏈配置「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合：

1. 如果您要在建立工具鏈時配置此工具整合，請按一下「可配置的整合」區段中的 **{{site.data.keyword.deliverypipeline}} 專用工作者節點**。
1. 如果您有工具鏈，並且要在其中新增此工具整合，請在 DevOps 儀表板的「工具鏈」頁面上按一下工具鏈，以開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。

 a. 按一下**新增工具**。

 b. 在「工具整合」區段中，按一下 **{{site.data.keyword.deliverypipeline}} 專用工作者節點**。

1. 鍵入工具整合的名稱。此名稱會在管線階段的**工作者節點**標籤中識別專用工作者節點的儲存區。
1. 鍵入「服務 ID」API 金鑰，以鑑別是否可存取一個以上專用工作者節點可在其中尋找工作的工作佇列。如果您沒有「服務 ID」API 金鑰，請按一下**建立**，為此專用工作者節點產生一個「服務 ID」API 金鑰。
1. 按一下**建立整合**。
1. 從您的工具鏈中，按一下 **{{site.data.keyword.deliverypipeline}} 專用工作者節點**，以檢視一個清單，其中列出使用與此「服務 ID」相關聯之 API 金鑰來登錄的所有工作者節點。

如需 **{{site.data.keyword.deliverypipeline}} 專用工作者節點**工具整合的相關資訊，請參閱[配置 {{site.data.keyword.deliverypipeline}} 專用工作者節點](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker)。

### 配置您的 Kubernetes 叢集
{: #configure_kubernetes_cluster}

配置您的 Kubernetes 與專用工作者節點搭配：

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下您要配置之「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合的卡片。
1. 按一下**開始使用**，然後遵循步驟，在 Kubernetes 叢集上安裝及登錄專用工作者節點。

### 在您的管線中使用 {{site.data.keyword.deliverypipeline}} 專用工作者節點
{: #use_private_worker_pipeline}

請完成下列步驟，以在您的管線中使用專用工作者節點：

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下您要與專用工作者節點搭配使用之管線的卡片。
1. 在「管線」頁面的階段上，按一下**階段配置**圖示，然後按一下**配置階段**。
1. 按一下**工作者節點**標籤。
1. 選取您要在管線中使用的專用工作者節點。 

 依預設，管線階段中的工作是使用 IBM 管理的共用工作者節點的儲存區來執行，而這些工作者節點位於定義管線的地區。
 {: tip}
 
1. 按一下**儲存**。
1. 您可以手動執行階段，或等待觸發程式在相關聯的 Kubbernetes 叢集上使用指定的專用工作者節點，以在階段上執行工作。您可以檢視工作的日誌檔輸出，以判定使用的工作者節點。  


## 修改 {{site.data.keyword.deliverypipeline}} 專用工作者節點工具整合認證
{: #modify_private_worker}

在設定專用工作者節點之後，您可以更新用於工具整合的認證。如果這些認證遭到刪除、過期或遭盜用，您可能想要變更它們。您可以藉由建立新的「服務 ID 」或更新 API 金鑰，來更新認證。

### 建立服務 ID
{: #create_service_id}

請完成下列步驟來建立「服務 ID」：

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 在您要修改之專用工作者節點工具整合的卡片上，按一下功能表來存取配置選項。
1. 按一下**建立**。
1. 輸入「服務 ID」的名稱及說明。
1. 按一下**儲存整合**。
1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下您要為其指定新使用者認證之「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合的卡片。
1. 按一下**開始使用**，並完成步驟 2 及 3 ，以在您的叢集上登錄及驗證專用工作者節點。

### 更新 API 金鑰
{: #update_api_key}

請完成下列步驟來更新 API 金鑰，以與「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合搭配使用：

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 在您要修改之「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合的卡片上，按一下功能表來存取配置選項。
1. 指定新的 API 金鑰。 
1. 按一下**儲存整合**。

## 刪除 {{site.data.keyword.deliverypipeline}} 專用工作者節點
{: #delete_private_worker}

請完成下列步驟來刪除專用工作者節點：

1. 從工作者節點的儲存區中刪除專用工作者節點。
1. 從您的 Kuberneges 叢集中刪除專用工作者節點。

### 從工作者節點的儲存區中刪除 {{site.data.keyword.deliverypipeline}} 專用工作者節點

請完成下列步驟，以從工作者節點的儲存區中刪除專用工作者節點：

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 按一下您要配置之「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合的卡片。
1. 按一下**概觀**。
1. 按一下您要刪除之專用工作者節點的卡片，以存取配置選項。
1. 按一下**移除**，然後按一下**確認**。

### 從您的 Kuberneges 叢集中刪除 {{site.data.keyword.deliverypipeline}} 專用工作者節點

請完成下列步驟，從您的叢集中使用專用工作者節點：

1. 按一下您要配置之「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合的卡片。
1. 按一下**開始使用**，並遵循步驟從您的叢集中刪除專用工作者節點。

## 刪除 {{site.data.keyword.deliverypipeline}} 專用工作者節點工具整合
{: #delete_private_workers_tool_integration}

如果您從工具鏈中刪除「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合，則無法復原刪除。
{: important}

請完成下列步驟，以刪除「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合：

1. 在 DevOps 儀表板的**工具鏈**頁面上，按一下工具鏈來開啟其「概觀」頁面。或者，在應用程式之「概觀」頁面的「持續交付」卡片上，按一下**檢視工具鏈**，然後按一下**概觀**。
1. 在您要刪除之「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合的卡片上，按一下功能表來存取配置選項。
1. 若要從工具鏈中刪除工具整合，請按一下**刪除**。
1. 按一下**刪除**來進行確認。「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合即會從工具鏈中移除，而且在 Delivery Pipeline「階段配置」頁面的**工作者節點**標籤中，不再提供此工具整合。

如果您從工具鏈中刪除「{{site.data.keyword.deliverypipeline}} 專用工作者節點」工具整合，且專用工作者節點是針對管線階段配置的，則它仍會列示在「階段配置」頁面的**工作者節點**標籤中。不過，專用工作者節點已停用並標示為 REMOVED。您必須選取不同的專用工作者節點（如果存在的話），或改用公用工作者節點。
{: tip}
