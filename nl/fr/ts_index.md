---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-21"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# FAQ
{: #ts_cd}

Obtenez des réponses aux questions fréquentes relatives à l'utilisation d'{{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## J'ai essayé d'ajouter l'intégration d'outil GitHub à ma chaîne d'outils, pourquoi l'intégration d'outil n'a-t-elle pas été ajoutée ?
{: #cannot_authorize_github}

Si {{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à votre compte GitHub, l'intégration d'outil n'est pas ajoutée à votre chaîne d'outils.

Si vous configurez l'intégration d'outils GitHub pendant que vous créez votre chaîne d'outils, suivez les étapes suivantes pour autoriser l'accès à GitHub :

  1. A la section Intégrations configurables, cliquez sur **GitHub**.
  1. Si vous créez la chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et si {{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à GitHub, cliquez sur **Autorisation** pour accéder au site Web GitHub.
  1. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub.

Si vous disposez déjà d'une chaîne d'outils, mettez à jour la configuration de l'intégration d'outils GitHub :

 1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue
d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
 1. Sur la carte GitHub, cliquez sur le menu, puis sur **Configurer**.
 1. Mettez à jour les paramètres de configuration pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à GitHub. Cliquez sur **Autoriser** pour accéder au site Web GitHub. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub.
 1. Lorsque vous avez terminé la mise à jour des paramètres, cliquez sur **Sauvegarder l'intégration**.


## J'ai essayé de créer une chaîne d'outils, pourquoi ai-je reçu une erreur ?
{: #cannot_create_toolchain}

Lorsque vous tentez de créer une chaîne d'outils, si vous obtenez le message d'erreur suivant, supprimez une ou plusieurs chaînes d'outils de votre organisation puis créez votre chaîne d'outils à nouveau.

`Cette organisation contient 200 chaînes d'outils, ce qui correspond au maximum. Pour pouvoir ajouter une autre chaîne d'outils, retirez une ou plusieurs chaînes d'outils de l'organisation.`


## J'ai essayé de déployer une application dans {{site.data.keyword.Bluemix_notm}}, pourquoi ai-je reçu une erreur ?
{: #org_outofmemory}

Lorsque vous essayez de déployer une application dans {{site.data.keyword.Bluemix_notm}}, si vous obtenez le message d'erreur suivant, la quantité de mémoire restant dans votre organisation est inférieure à celle de la mémoire requise par l'application que vous souhaitez déployer.

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

Vous pouvez soit augmenter le quota de mémoire de votre compte ou réduire la mémoire utilisée par vos applications. Le quota de mémoire maximal pour un compte d'essai est 2 Go. Pour augmenter le quota de mémoire de votre compte, convertissez votre compte d'essai en compte payant. Pour obtenir des informations sur la conversion de votre compte d'essai en compte payant, voir [Comptes payants](/docs/pricing/index.html#pay-accounts). Pour réduire la mémoire utilisée par vos applications, utilisez la console {{site.data.keyword.Bluemix_notm}} ou l'interface de ligne de commande cf.

Si vous utilisez la console {{site.data.keyword.Bluemix_notm}}, procédez comme suit :

1. Dans l'application Applications, sélectionnez votre application. La page des détails de l'application
s'ouvre.
1. Dans le panneau Contexte d'exécution, vous pouvez réduire la limite de mémoire maximal ou le nombre d'instances d'application, ou les deux,
pour votre application.

Si vous utilisez l'interface de ligne de commande cf, procédez comme suit :

1. Vérifiez la quantité de mémoire utilisée par vos applications. La commande cf apps répertorie toutes les applications que vous avez déployées dans votre espace en cours. Le statut de chaque application est également affiché.

	  ```
	  cf apps
	  ```

1. Pour réduire la quantité de mémoire qui est utilisée par votre application, réduisez le nombre d'instances d'application ou la limite de
mémoire
maximale, ou les deux :

	  ```
	  cf push nom_app -p chemin_app -i nombre_instances -m limite_mémoire
      ```
    
1. Redémarrez votre application pour que les modifications soient appliquées.


## J'ai créé une application. Pourquoi la barre d'exécution n'affiche-t-elle pas les icônes {{site.data.keyword.Bluemix_notm}} Live Sync dans l'Eclipse Orion Web IDE ?
{: #ts_llz_lkb_3r}

![ Barre d'exécution](images/webide_runbar_light.png)   

Lorsque vous éditez une application Node.js dans l'interface Web IDE, les icônes  {{site.data.keyword.Bluemix_notm}} d'édition directe, de redémarrage rapide et de débogage ne sont pas disponibles dans la barre d'exécution dans ces circonstances :


* Le fichier `manifest.yml` n'est pas stocké au niveau supérieur de votre projet.
* Votre application est stockée dans un sous-répertoire et non dans le répertoire principal, mais le chemin d'accès au sous-répertoire n'est pas indiqué dans le fichier `manifest.yml`.
* L'application ne contient pas de fichier `package.json`.


Si le fichier `manifest.yml` n'est pas stocké dans le répertoire principal, placez-le dedans. Si votre application est stockée dans un sous-répertoire, spécifiez le chemin d'accès au sous-répertoire dans le fichier `manifest.yml`. Si l'application ne contient pas de fichier `package.json`, créez-en un dans le même répertoire que votre application.


## J'ai cliqué sur une chaîne d'outils pour afficher sa page Présentation, pourquoi la chaîne d'outils ne se charge-t-elle pas ?
{: #toolchains_load}

Vérifiez la page Statut d'{{site.data.keyword.Bluemix_notm}} pour déterminer si des problèmes connus affectent la plateforme {{site.data.keyword.Bluemix_notm}} et les principaux services dans {{site.data.keyword.Bluemix_notm}}.

Vous pouvez afficher la page Statut en choisissant l'une des options suivantes :

  * Connectez vous à la console {{site.data.keyword.Bluemix_notm}}. Dans la barre de menus, cliquez sur **Support** et sélectionnez **Statut**. Recherchez dans les ressources répertoriées l'icône signalant ![des problèmes](../../get-support/images/some_issues.svg). Celle-ci peut indiquer une indisponibilité.
  * Accédez directement à [{{site.data.keyword.Bluemix_notm}} - Statut du système ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/status){: new_window}.

Pour plus d'informations sur la page Statut d'{{site.data.keyword.Bluemix_notm}}, voir [Viewing {{site.data.keyword.Bluemix_notm}} status](https://console.bluemix.net/docs/get-support/ViewStatus.html#viewing-bluemix-status).


## J'ai configuré une intégration d'outil pour ma chaîne d'outils, pourquoi n'a-t-elle pas été configurée ?
{: #tool_integration_error}

Lorsque vous ajoutez une intégration d'outils, la chaîne d'outils communique avec l'outil qui est représenté par l'intégration d'outils pour mettre à disposition les ressources nécessaires et les associer à la chaîne d'outils. Si une erreur se produit pendant le processus de configuration ou si la communication entre la chaîne d'outils et l'outil ne s'établit pas correctement, l'intégration d'outils passe à l'état d'erreur.

 ![Erreur Echec de la configuration](images/tool_setup_failed.png)

Vous pouvez tenter de reconfigurer l'intégration d'outil :

1. Sur sa carte d'outil, survolez le message `Echec de la configuration` et cliquez sur **Reconfigurer**.

 ![Bouton Reconfigurer](images/tool_reconfigure.png)

1. Assurez-vous que vous utilisez des paramètres de configuration valides. Si l'erreur est due à une configuration non valide, un message d'erreur s'affiche ; par exemple, `Impossible de configurer l'intégration. Vérifiez les paramètres puis réessayez. Motif : api_key:fakeKey non valide`. Mettez à jour les paramètres de l'intégration
d'outils et cliquez sur **Sauvegarder l'intégration**.
1. Si l'erreur a été provoquée par un problème de communication, cliquez sur **Sauvegarder l'intégration** pour réessayer.
