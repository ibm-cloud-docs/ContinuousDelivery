---



copyright:
  years: 2015，2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}


Si vous construisez une application Node.js, vous pouvez utiliser {{site.data.keyword.Bluemix}} Live Sync pour mettre rapidement à jour l'instance d'application dans {{site.data.keyword.Bluemix_notm}} et procéder au développement sans avoir à effectuer un redéploiement manuel.   
{: shortdesc}

Lorsque vous apportez une modification, vous pouvez immédiatement voir cette modification dans votre application
{{site.data.keyword.Bluemix_notm}} en cours d'exécution. {{site.data.keyword.Bluemix_notm}} Live Sync fonctionne
<!--from both the command line and -->
dans l'interface IDE Web Eclipse Orion. Vous pouvez déboguer des applications qui sont écrites dans Node.js à l'aide de {{site.data.keyword.Bluemix_notm}} Live Sync.  

{{site.data.keyword.Bluemix_notm}} Live Sync se compose de deux fonctions.
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**Live Edit**

Vous pouvez éditer une application Node.js qui s'exécute sur {{site.data.keyword.Bluemix_notm}} et la tester tout de suite dans votre navigateur. Les modifications que vous apportez dans l'interface IDE Web sont immédiatement propagées dans le système de fichiers de l'application.  

**Debug**  

Lorsqu'une application Node.js est en mode édition directe, vous pouvez ouvrir un shell et la déboguer. Vous pouvez éditer le code de manière dynamique, insérer des points d'arrêt, parcourir le code, redémarrer le contexte d'exécution, etc. à l'aide du débogueur Node Inspector.  


##Live Edit
{: #live-edit}

Si vous construisez une application Node.js qui s'exécute sur {{site.data.keyword.Bluemix_notm}}, la fonction Live Edit de {{site.data.keyword.Bluemix_notm}} Live Sync  peut mettre rapidement à jour l'instance d'application. La fonction Live Edit est disponible uniquement dans l'interface IDE Web. Live Edit vous permet de procéder au développement comme sur le bureau, sans redéploiement.

La fonction Live Edit est prise en charge uniquement pour les applications Node.js.

Dans l'interface IDE Web Eclipse Orion, dans la barre d'exécution, cliquez sur **Live Edit**.

![Image illustrant la barre d'exécution avec la fonction Live Edit](images/bluemix-live-sync-light.png)

La fonction Live Edit vous permet de prévisualiser rapidement les modifications que vous avez apportées aux applications Node.js s'exécutant sur{{site.data.keyword.Bluemix_notm}}. Lorsque vous mettez à jour
votre code alors que la fonction Live Edit est activée, vous pouvez actualiser la fenêtre de navigateur de votre application Web pour afficher ces
modifications quelques secondes après les avoir effectuées.

Consultez le tutoriel sur l'utilisation de la fonction Live Edit de {{site.data.keyword.Bluemix_notm}} Live Sync sous [Utilisation de {{site.data.keyword.Bluemix_notm}} Live Sync pour développer, dégoguer et déployer votre application![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window}.

Lorsque vous modifiez les fichiers dans votre interface IDE Web, ils sont redéployés automatiquement sur votre instance d'application sur {{site.data.keyword.Bluemix_notm}}. Si vous avez besoin de redémarrer l'application Node, cliquez sur le bouton **Redémarrer** dans la barre d'exécution.

Pour que votre expérience soit plus cohérente lorsque vous utilisez la fonction Live Edit de {{site.data.keyword.Bluemix_notm}} Live Sync, 256 Mo de mémoire supplémentaire est requise et ajoutée.{: tip}

## {{site.data.keyword.Bluemix_notm}} Live Debug
{: #live-debug}

{{site.data.keyword.Bluemix_notm}} Live Sync Debug utilise
[Node Inspector ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/node-inspector/node-inspector){:new_window}
pour fournir les fonctions de débogage. Vous devez utiliser la version 4 de l'application Node pour que le débogueur soit disponible puisque les versions ultérieures de Node.js n'incluent pas Node Inspector.

Vous pouvez accéder à {{site.data.keyword.Bluemix_notm}} Live Debug lorsque {{site.data.keyword.Bluemix_notm}} Live Edit est activé pour votre application Node.js.  

La fonction debug permet d'éditer le code, d'insérer des points d'arrêt, de parcourir le code, de redémarrer le contexte d'exécution et d'effectuer d'autres opérations de manière dynamique, pendant que votre application est exécutée par {{site.data.keyword.Bluemix_notm}}. Vous pouvez développer votre application de façon incrémentielle avec agilité en effectuant votre choix dans une longue liste de services
{{site.data.keyword.Bluemix_notm}}.

{{site.data.keyword.Bluemix_notm}} Live Debug inclut les fonctions suivantes :

* Contrôle du contexte d'exécution d'application
* Débogage à l'aide de [Node Inspector ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/node-inspector/node-inspector){:new_window}
* L'accès au shell

### Contrôle du contexte d'exécution d'application {: #app-runtime}

Avec le contrôle du contexte d'exécution d'application, vous pouvez utiliser la fonction Debug afin d'inspecter l'état de l'application
au démarrage. Cette capacité est utile lorsque vous traitez les incidents liés à une application qui tombe en panne au démarrage.

Lorsque vous développez votre application, vous pouvez choisir une action parmi les suivantes :

* Procéder à un redémarrage rapide de l'application
* Suspendre l'application avant l'exécution du code de l'application

Une fois que vous êtes connecté, la page {{site.data.keyword.Bluemix_notm}} Live Debug s'ouvre.

![Interface utilisateur Debug](images/live_sync_debug.png)


### Debug {: #debug}

**Restriction :** Google Chrome et Node 4 sont requis.

La fonction Debug inclut les capacités suivantes :  
* Définir des points d'arrêt dans le code de l'application pour interrompre l'exécution à une ligne spécifique.
  Les points d'arrêt ne sont pas pris en charge dans le programme principal, mais dans des points d'entrée.{: tip}
* Editer les conditions de point d'arrêt pour interrompre l'exécution uniquement lorsque certains critères sont remplis.
* Inspecter l'état des zones et des variables locales.
* Afficher immédiatement la sortie de débogage des appels de `console.log()`. Cette action est plus rapide que la surveillance des journaux cf.
* Utiliser l'éditeur de code source intégré pour apporter des modifications immédiates mais temporaires au code d'application en cours d'exécution.

### Shell {: #shell}

Cet outil permet d'accéder au conteneur dans lequel votre application est en cours d'exécution via un shell. Avec ce terminal, vous pouvez
exécuter des commandes shell de diagnostic à distance afin d'administrer votre application. Toutes les versions de Node.js prennent en charge la fonction Shell.

Surveillez l'utilisation de la mémoire et de l'unité centrale dans l'instance qui utilise des commandes Linux standard, comme
**top**, **ps** et **kill**.

### Configuration d'une application pour activer {{site.data.keyword.Bluemix_notm}} Live Debug {: #configure_app_debug}

1. {{site.data.keyword.Bluemix_notm}} Live Debugger utilise Node Inspector. Vous devez utiliser Node version 4. Vous devez également autoriser le pack de construction à détecter la commande app start. La commande start doit être détectée automatiquement par
le pack de construction et ne doit pas être définie dans le fichier manifest.yml.

   Un fichier `package.json` qui prend en charge {{site.data.keyword.Bluemix_notm}} Live Debug se présente comme suit :

  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. Augmentez la mémoire.  

    a. Dans le fichier `manifest.yml` de l'application, ajoutez 128 Mo ou plus à la valeur spécifiée pour l'attribut de mémoire.

Une fois {{site.data.keyword.Bluemix_notm}} Live
Debug installé, vous pouvez utiliser les outils de débogage.

Transférez l'application, puis accéder à `https://_app-host.mybluemix.net_/bluemix-debug/manage` pour accéder à l'interface utilisateur {{site.data.keyword.Bluemix_notm}} Debug. Lorsque vous êtes invité à vous authentifier, entrez vos nom d'utilisateur et mot de passe IBM ou un code d'accès à usage unique.    

L'initialisation du débogueur peut durer environ une minute. {: tip}

### Restauration des configurations d'application et désactivation de {{site.data.keyword.Bluemix_notm}} Live Debug {: #restore_live_debug}

1. Restaurez la version Node.js, la commande start et la valeur de mémoire d'origine de l'application.

2. Déployez l'application.

### Informations complémentaires

* Voir [Eclipse tools for {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.bluemix.net/docs/manageapps/eclipsetools/eclipsetools.html){:new_window}
