---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Traitement des incidents liés à {{site.data.keyword.contdelivery_short}}
{: #ts_cd}

Obtenez des réponses aux questions courantes liées au traitement des incidents relatifs à l'utilisation d'{{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Autorisation impossible auprès de GitHub
{: #cannot_authorize_github}

Vous n'êtes pas autorisé auprès de GitHub.
{:shortdesc}

Si {{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à votre compte GitHub, l'une des erreurs suivantes peut se produire :
{: tsSymptoms}

 * Lorsque vous tentez d'ajouter l'intégration d'outils GitHub à votre chaîne d'outils, l'ajout n'a pas lieu.
 * Le pipeline ne s'exécute pas automatiquement lorsque vous envoyez des modifications par commande push à votre référentiel GitHub ou GitHub Enterprise.

{{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à GitHub.  
{: tsCauses}

Si vous configurez l'intégration d'outils GitHub lors de la création de votre chaîne d'outils, procédez comme suit :
{: tsResolve}

  1. A la section Intégrations configurables, cliquez sur **GitHub**.
  1. Si vous créez la chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et si {{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à GitHub, cliquez sur **Autorisation** pour accéder au site Web GitHub. 
  1. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub.

Si vous disposez déjà d'une chaîne d'outils, mettez à jour la configuration de l'intégration d'outils GitHub :

 1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue
d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
 1. Sur la carte GitHub, cliquez sur le menu, puis sur **Configurer**.
 1. Mettez à jour les paramètres de configuration pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à GitHub. Cliquez sur **Autoriser** pour accéder au site Web GitHub. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub.
 1. Lorsque vous avez terminé la mise à jour des paramètres, cliquez sur **Sauvegarder l'intégration**.


## Impossible de créer une chaîne d'outils
{: #cannot_create_toolchain}

Une erreur s'affiche lorsque vous créez une chaîne d'outils.
{:shortdesc}

Lorsque vous créez une chaîne d'outils, le message d'erreur suivant apparaît :
{: tsSymptoms}

`Cette organisation contient 200 chaînes d'outils, ce qui correspond au maximum. Pour pouvoir ajouter une autre chaîne d'outils, retirez une ou plusieurs chaînes d'outils de l'organisation.`

Vous ne pouvez pas avoir plus de 200 chaînes d'outils dans une organisation.  
{: tsCauses}

Supprimez une ou plusieurs chaînes d'outils de votre organisation, puis créez à nouveau votre chaîne d'outils.
{: tsResolve}


## La limite de mémoire de l'organisation a été atteinte
{: #org_outofmemory}

Vous risquez de ne pas pouvoir déployer une application sur {{site.data.keyword.Bluemix_notm}} si vous dépassez la limite de mémoire de votre organisation. Vous pouvez réduire la quantité de mémoire que vos applications utilisent ou augmenter le quota de mémoire de votre compte. Le quota de mémoire maximal pour un compte d'essai est 2 Go. Le quota peut être augmenté lorsque vous procédez à la mise à niveau vers un compte payant. 

Lorsque vous déployez une application dans {{site.data.keyword.Bluemix_notm}}, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

Cette erreur survient lorsque la quantité de mémoire restante pour votre organisation est inférieure à la quantité de mémoire requise par
l'application à déployer. Le quota de mémoire maximal pour un compte d'essai est 2 Go.
{: tsCauses}

Vous pouvez augmenter le quota de mémoire de votre compte ou réduire la mémoire que vos applications utilisent.
{: tsResolve}

  * Pour augmenter le quota de mémoire de votre compte, convertissez votre compte d'essai en compte payant. Pour des informations sur la conversion de votre compte d'essai en compte payant, voir [Comptes payants](/docs/pricing/index.html#pay-accounts).
  * Pour réduire la quantité de mémoire que vos applications utilisent, servez-vous de la console {{site.data.keyword.Bluemix_notm}} ou de l'interface de ligne de commande cf.

    Si vous utilisez la console {{site.data.keyword.Bluemix_notm}}, procédez comme suit :

    1. Dans l'application Applications, sélectionnez votre application. La page des détails de l'application
s'ouvre.
    2. Dans le panneau Contexte d'exécution, vous pouvez réduire la limite de mémoire maximal ou le nombre d'instances d'application, ou les deux,
pour votre application.

    Si vous utilisez l'interface de ligne de commande cf, procédez comme suit :

    1. Vérifiez la quantité de mémoire qui est utilisée par vos applications :

	  ```
	  cf apps
	  ```

	  La commande cf apps répertorie toutes les applications que vous avez déployées dans votre espace en cours. Le statut de chaque application est également affiché.

    2. Pour réduire la quantité de mémoire qui est utilisée par votre application, réduisez le nombre d'instances d'application ou la limite de
mémoire
maximale, ou les deux :

	  ```
	  cf push nom_app -p chemin_app -i nombre_instances -m limite_mémoire
      ```

    3. Redémarrez votre application pour que les modifications soient appliquées.

Pour plus d'informations sur les problèmes généraux liés à la gestion de vos applications, voir [Troubleshooting for managing apps](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps).


## Les icônes Bluemix Live Sync ne sont pas visibles sur la barre d'exécution dans Eclipse Orion Web IDE
{: #ts_llz_lkb_3r}

Vous avez créé une application, mais les icônes IBM Bluemix Live Sync n'apparaissent pas dans la barre d'exécution d'Eclipse Orion Web IDE. Vous ne voyez pas la barre d'exécution complète avec les icônes d'édition directe. 

![ Barre d'exécution](images/webide_runbar_light.png)   

Lorsque vous éditez une application Node.js dans l'interface IDE Web, les icônes d'édition directe, de redémarrage rapide et de débogage de {{site.data.keyword.Bluemix_notm}} n'apparaissent pas sur la barre d'exécution.
{: tsSymptoms}

Les icônes ne sont pas disponibles dans les cas suivants :
{: tsCauses}

* Le fichier `manifest.yml` n'est pas stocké au niveau supérieur de votre projet.
* Votre application est stockée dans un sous-répertoire et non dans le répertoire principal, mais le chemin d'accès au sous-répertoire n'est pas indiqué dans le fichier `manifest.yml`.
* L'application ne contient pas de fichier `package.json`.

Utilisez l'une des méthodes suivantes :
{: tsResolve}

* Si le fichier `manifest.yml` n'est pas stocké dans le répertoire principal, placez-le dedans. 
* Si votre application est stockée dans un sous-répertoire, spécifiez le chemin d'accès au sous-répertoire dans le fichier `manifest.yml`.
   ```
    path: chemin_application
    ```
* Créez un fichier `package.json` dans le répertoire dans lequel se trouve votre application.


## La chaîne d'outils ne se charge pas
{: #toolchains_load}

Lorsque vous cliquez sur une chaîne d'outils pour afficher sa page Présentation, la chaîne d'outils ne se charge pas.
{:shortdesc}

Dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, cliquez sur la chaîne d'outils pour ouvrir sa page Présentation. Vous pouvez également accéder à la page de présentation de l'application et cliquer sur **Afficher la chaîne d'outils** dans la carte Continuous Delivery. Ensuite, cliquez sur **Vue d'ensemble**. La page Présentation de la chaîne d'outils ne s'ouvre pas.
{: tsSymptoms}

Vérifiez le statut de {{site.data.keyword.Bluemix_notm}} pour voir si le problème est dû à une indisponibilité.
{: tsCauses}

Affichez la page Statut de {{site.data.keyword.Bluemix_notm}} pour déterminer si des problèmes connus affectent la plateforme {{site.data.keyword.Bluemix_notm}} et les services principaux {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Vous pouvez afficher la page Statut en choisissant l'une des options suivantes :

  * Connectez vous à la console {{site.data.keyword.Bluemix_notm}}. Dans la barre de menu, cliquez sur **Support** et sélectionnez **Statut**. Recherchez dans les ressources répertoriées l'icône signalant ![des problèmes](../../support/images/some_issues.svg). Celle-ci peut indiquer une indisponibilité.
  * Accédez directement à la page en vous rendant à l'adresse [IBM {{site.data.keyword.Bluemix_notm}} - System Status ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://ibm.biz/bluemixstatus){: new_window}.

Pour plus d'informations sur la page Statut de {{site.data.keyword.Bluemix_notm}}, voir [Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status).


## L'intégration d'outils n'est pas configurée
{: #tool_integration_error}

Une fois que vous avez configuré une intégration d'outils pour votre chaîne d'outils, l'erreur `Echec de la configuration` s'affiche sur la carte de l'outil.
{:shortdesc}

Après avoir configuré une intégration d'outils, vous pouvez afficher sa carte d'outil sur la page de présentation de la chaîne d'outils et constater que la configuration a échoué.
{: tsSymptoms}

 ![Erreur Echec de la configuration](images/tool_setup_failed.png)

Lorsque vous ajoutez une intégration d'outils, la chaîne d'outils communique avec l'outil qui est représenté par l'intégration d'outils pour mettre à disposition les ressources nécessaires et les associer à la chaîne d'outils. Si une erreur se produit pendant le processus de configuration ou si la communication entre la chaîne d'outils et l'outil ne s'établit pas correctement, l'intégration d'outils passe à l'état d'erreur.
{: tsCauses}

Configurez à nouveau l'intégration d'outils :
{: tsResolve}

1. Sur sa carte d'outil, survolez le message `Echec de la configuration` et cliquez sur **Reconfigurer**.

 ![Bouton Reconfigurer](images/tool_reconfigure.png)

1. Assurez-vous que vous utilisez des paramètres de configuration valides. Si l'erreur est due à une configuration non valide, un message d'erreur s'affiche ; par exemple, `Impossible de configurer l'intégration. Vérifiez les paramètres puis réessayez. Motif : api_key:fakeKey non valide`. Mettez à jour les paramètres de l'intégration
d'outils et cliquez sur **Sauvegarder l'intégration**.
1. Si l'erreur a été provoquée par un problème de communication, cliquez sur **Sauvegarder l'intégration** pour réessayer.



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
