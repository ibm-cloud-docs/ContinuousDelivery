---



copyright:
  years: 2015，2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

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

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

Se você estiver construindo um aplicativo Node.js, será possível usar o {{site.data.keyword.Bluemix}} Live Sync para atualizar rapidamente a instância do aplicativo no {{site.data.keyword.Bluemix_notm}} e desenvolver sem reimplementar manualmente.   
{: shortdesc}

Quando você fizer uma mudança, será possível ver essa mudança no aplicativo {{site.data.keyword.Bluemix_notm}} em execução imediatamente. O {{site.data.keyword.Bluemix_notm}} Live Sync funciona
<!--from both the command line and -->
no Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}). 

##Live Edit
{: #live-edit}

É possível editar um aplicativo Node.js que é executado no {{site.data.keyword.Bluemix_notm}} e testá-lo em seu navegador imediatamente. Quaisquer mudanças feitas no {{site.data.keyword.webide}} são propagadas para o sistema de arquivos de aplicativo imediatamente.

Se você está construindo um aplicativo Node.js que é executado no {{site.data.keyword.Bluemix_notm}}, o recurso Live Edit do {{site.data.keyword.Bluemix_notm}} Live Sync pode atualizar rapidamente a instância do aplicativo. O Live Edit está disponível no {{site.data.keyword.webide}} somente. É possível usar o Live Edit para desenvolver tal como você faria na área de trabalho sem reimplementar.

O Live Edit é suportado para aplicativos Node.js apenas
{: important}

No {{site.data.keyword.webide}}, na barra de execução, clique em **Live Edit**.

![Imagem da barra de execução com edição em tempo real](images/cloud-live-sync-light.png)

Use o Live Edit para visualizar rapidamente as mudanças nos aplicativos Node.js que são executados no {{site.data.keyword.Bluemix_notm}}. Ao atualizar seu código com o Live Edit ligado, é possível atualizar sua janela do navegador de aplicativo da Web para ver essas mudanças refletidas segundos após criá-los.

Para obter um tutorial sobre como usar o recurso do Live Edit do {{site.data.keyword.Bluemix_notm}} Live Sync, consulte [Use o {{site.data.keyword.Bluemix_notm}} Live Sync para desenvolver, depurar e implementar seu app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}.

Quando você muda os arquivos em seu {{site.data.keyword.webide}}, eles são automaticamente reimplementados para sua instância do aplicativo no {{site.data.keyword.Bluemix_notm}}. Se você precisar reiniciar o aplicativo Node, clique no botão **Reiniciar** na barra de execução.

Para obter uma experiência mais consistente, ao usar o recurso Live Edit do {{site.data.keyword.Bluemix_notm}} Live Sync, 256 MB de memória extra serão necessários e incluídos.
{: tip}
