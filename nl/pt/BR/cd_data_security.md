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


# Protegendo seus dados    
{: #cd_data_security}  

O {{site.data.keyword.contdelivery_full}} hospeda os seus bancos de dados em um ambiente altamente disponível e seguro:
   * Os dados são criptografados em repouso (GPFS, LUKS e disco integrado) e em andamento (HTTPS e SSH). As credenciais do cliente e do sistema são armazenadas em discos criptografados.
   * O aplicativo e os dados são configurados para alta disponibilidade.
   * O acesso aos dados é limitado a apenas aqueles usuários que requerem os dados para suportar e manter o serviço.
