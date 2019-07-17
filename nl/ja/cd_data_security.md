---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-31"

keywords: secure environment, data, IBM Cloud Continuous Delivery, Data

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# データの保護    
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} は、可用性の高い安全な環境でデータベースをホストします。
   * データの暗号化は、保存時 (GPFS、LUKS、組み込みディスク) にも、処理時 (HTTPS、SSH) にも行われます。クライアント資格情報とシステム資格情報は、暗号化ディスクに保管されます。
   * アプリケーションとデータは、高可用性に対応するように構成されます。
   * データへのアクセスは、サービスのサポートと維持のためにデータを必要とするユーザーのみに限定されます。
