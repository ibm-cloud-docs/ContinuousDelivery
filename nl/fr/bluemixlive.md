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

Si vous construisez une application Node.js, vous pouvez utiliser {{site.data.keyword.Bluemix}} Live Sync pour mettre rapidement à jour l'instance d'application dans {{site.data.keyword.Bluemix_notm}} et procéder au développement sans avoir à effectuer un redéploiement manuel.   
{: shortdesc}

Lorsque vous apportez une modification, vous pouvez immédiatement voir cette modification dans votre application
{{site.data.keyword.Bluemix_notm}} en cours d'exécution. {{site.data.keyword.Bluemix_notm}} Live Sync fonctionne
<!--from both the command line and -->
dans Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}). 

##Edition directe
{: #live-edit}

Vous pouvez éditer une application Node.js qui s'exécute sur {{site.data.keyword.Bluemix_notm}} et la tester tout de suite dans votre navigateur. Les modifications que vous apportez dans l'interface {{site.data.keyword.webide}} sont immédiatement propagées dans le système de fichiers de l'application.

Si vous générez une application Node.js qui s'exécute sur {{site.data.keyword.Bluemix_notm}}, la fonction Edition directe d'{{site.data.keyword.Bluemix_notm}} Live Sync peut mettre rapidement à jour l'instance d'application. la fonction Edition directe est uniquement disponible dans l'interface {{site.data.keyword.webide}}. Vous pouvez utiliser le mode Edition directe pour développer comme vous le feriez sur le bureau, sans avoir à redéployer.

La fonction Edition directe est uniquement prise en charge pour les applications Node.js.
{: important}

Dans l'interface {{site.data.keyword.webide}}, dans la barre d'exécution, cliquez sur **Edition directe**.

![Image illustrant la barre d'exécution avec la fonction Edition directe](images/cloud-live-sync-light.png)

Utilisez la fonction Edition directe pour prévisualiser rapidement les modifications apportées aux applications Node.js s'exécutant sur {{site.data.keyword.Bluemix_notm}}. Lorsque vous mettez à jour votre code alors que la fonction Edition directe est activée, vous pouvez actualiser la fenêtre de navigateur de votre application Web pour afficher ces modifications quelques secondes après les avoir effectuées.

Consultez le tutoriel sur l'utilisation de la fonction Edition directe d'{{site.data.keyword.Bluemix_notm}} Live Sync sous [Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop, debug, and deploy your app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}.

Lorsque vous modifiez les fichiers dans votre interface {{site.data.keyword.webide}}, ils sont automatiquement redéployés sur votre instance d'application sur {{site.data.keyword.Bluemix_notm}}. Si vous avez besoin de redémarrer l'application Node, cliquez sur le bouton **Redémarrer** dans la barre d'exécution.

Pour une expérience plus cohérente, lorsque vous utilisez la fonction Edition directe d'{{site.data.keyword.Bluemix_notm}} Live Sync, 256 Mo de mémoire supplémentaire sont requis et ajoutés.
{: tip}
