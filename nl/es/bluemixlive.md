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

Si está creando una aplicación Node.js, puede utilizar {{site.data.keyword.Bluemix}} Live Sync para actualizar rápidamente la instancia de aplicación en {{site.data.keyword.Bluemix_notm}} y desarrollar sin redesplegar manualmente.   
{: shortdesc}

Cuando realice un cambio, puede verlo de inmediato en la aplicación de {{site.data.keyword.Bluemix_notm}} en ejecución. {{site.data.keyword.Bluemix_notm}} Live Sync funciona
<!--from both the command line and -->
en Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}). 

##Edición en directo
{: #live-edit}

Puede editar una aplicación Node.js que se ejecuta en {{site.data.keyword.Bluemix_notm}} y probarla en el navegador inmediatamente. Los cambios que realice en el {{site.data.keyword.webide}} se propagarán inmediatamente al sistema de archivos de la aplicación.

Si está creando una aplicación Node.js que se ejecuta en {{site.data.keyword.Bluemix_notm}}, la característica Edición en directo de {{site.data.keyword.Bluemix_notm}} Live Sync puede actualizar rápidamente la instancia de aplicación. La característica Edición en directo solo está disponible en {{site.data.keyword.webide}}. Puede utilizar Edición en directo para desarrollar como lo haría en el escritorio sin tener que volver a desplegar.

La característica Edición en directo solo se admite en las aplicaciones Node.js.
{: important}

En {{site.data.keyword.webide}}, en la barra de ejecución, pulse **Edición en directo**.

![Imagen de la barra de Ejecución con la edición en directo](images/cloud-live-sync-light.png)

Utilice Edición en directo para obtener una vista previa rápida de los cambios en las aplicaciones Node.js que se ejecutan en {{site.data.keyword.Bluemix_notm}}. Al actualizar
el código con la característica Edición en directo activada, puede renovar la ventana del navegador de su aplicación web
para ver dichos cambios reflejados pocos segundos después de efectuarlos.

Para ver una guía de aprendizaje sobre cómo utilizar la característica Edición en directo de {{site.data.keyword.Bluemix_notm}} Live Sync, consulte [Utilice {{site.data.keyword.Bluemix_notm}} Live Sync para desarrollar, depurar y desplegar la app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}.

Cuando modifique los archivos en {{site.data.keyword.webide}}, se redesplegarán automáticamente a su instancia de aplicación en {{site.data.keyword.Bluemix_notm}}. Si tiene que reiniciar la aplicación Node, pulse el botón **Reiniciar** de la barra de ejecución.

Para obtener una experiencia más coherente al utilizar la característica de Live Edit de {{site.data.keyword.Bluemix_notm}} Live Sync, se necesitan 256 MB de memoria adicional y se añade.
{: tip}
