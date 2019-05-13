---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-29"

keywords: Activity Tracker events, tool-instance, List of events

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

<!-- Name your file `at-events.md` and include it in the Reference nav group in your toc file. -->

# {{site.data.keyword.cloudaccesstrailshort}}  eventos
{: #at_events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e aplicativos interagem com o serviço {{site.data.keyword.contdelivery_short}} no {{site.data.keyword.Bluemix}}. 
{: shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.Bluemix_notm}}. Para obter mais informações, consulte o [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

<!-- You can create different sections to group events by area. -->

## Lista de eventos
{: #events}

A tabela a seguir lista as ações que geram um evento:

| Ação | Descrição | 
|:-----------------|:-----------------|
| continuous-delivery.toolchain.create | Criar uma cadeia de ferramentas | 
| continuous-delivery.toolchain.delete | Excluir uma cadeia de ferramentas |
| toolchain.tool-instance.deploy | Criar uma integração de ferramenta |
| toolchain.tool-instance.undeploy | Excluir uma integração de ferramenta |
{: caption="Tabela 1. Ações que geram eventos" caption-side="top"}

## Onde visualizar os eventos
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no
{{site.data.keyword.cloudaccesstrailshort}} **domínio de contas** disponível na região do
{{site.data.keyword.Bluemix_notm}} na qual eles são gerados.
