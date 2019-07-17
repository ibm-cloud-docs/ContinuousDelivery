---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# FAQ
{: #ts_cd}

Obtenez des réponses aux questions fréquentes relatives à l'utilisation d'{{site.data.keyword.contdelivery_full}}.
{:shortdesc}

## Pourquoi la page Chaînes d'outils indique-t-elle que le plan Lite du service {{site.data.keyword.contdelivery_short}} est dépassé ?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} propose deux plans : Lite et Professional. Si vous utilisez le plan Lite de {{site.data.keyword.contdelivery_short}}, vous pouvez utiliser les chaînes d'outils gratuitement, dans les limites du plan. Le message d'erreur indique que vous avez dépassé une ou plusieurs limites du plan Lite. Par exemple, vous pouvez dépasser le plan si un trop grand nombre d'utilisateurs autorisés sont associés à l'instance de service {{site.data.keyword.contdelivery_short}} ou si vous avez exécuté le nombre maximal de travaux {{site.data.keyword.deliverypipeline}} défini. Pour plus d'informations sur les conditions de votre plan, voir [Utilisations des plans et limitations](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## Mon service {{site.data.keyword.contdelivery_short}} indique que les services du plan Lite sont supprimés après 30 jours d'inactivité. Que signifie inactivité ?
{: #plan_inactivity}
{: faq}

Une instance du service {{site.data.keyword.contdelivery_short}} est considérée active lorsqu'une ou plusieurs chaînes d'outils sont actives dans le même groupe de ressources ou dans la même organisation Cloud Foundry. Une chaîne d'outils est considérée active si les utilisateurs interagissent avec elle par le biais de l'interface utilisateur, si des travaux Delivery Pipeline sont déclenchés, si l'on accède à des référentiels gérés par {{site.data.keyword.gitrepos}}, ou si des espaces de travail Eclipse Orion {{site.data.keyword.webide}} sont utilisés. Pour qu'une chaîne d'outils soit considérée inactive, toutes ces conditions doivent être absentes pour toutes les chaînes d'outils qui sont associées au service {{site.data.keyword.contdelivery_short}} pendant une durée de 30 jours.


## J'ai créé une chaîne d'outils, pourquoi la page Chaînes d'outils indique-t-elle qu'un service Continuous Delivery est requis ?
{: #service_required_resource_group}
{: faq}

Les dispositions du plan de l'instance du service {{site.data.keyword.contdelivery_short}} qui se trouve dans le même groupe de ressources ou la même organisation que la chaîne d'outils gèrent l'utilisation de certaines intégrations d'outils ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} et {{site.data.keyword.gitrepos}}) contenues dans le service. Le message d'erreur indique que le groupe de ressources ou l'organisation ne contient pas l'instance requise du service {{site.data.keyword.contdelivery_short}}. Pour plus d'informations sur les conditions de votre plan, voir [Utilisations des plans et limitations](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## J'ai mis à jour les informations d'une chaîne d'outils d'une organisation Cloud Foundry, pourquoi est-ce que mes changements ne s'affichent pas dans la chaîne d'outils ?
{: #updates_in_cloud_foundry}
{: faq}

Lorsque vous mettez à jour les informations de chaîne d'outils directement dans Cloud Foundry, cela peut prendre quelques minutes avant que le service {{site.data.keyword.contdelivery_short}} ne s'actualise et affiche les modifications. Par exemple, si vous ajoutez ou supprimez un utilisateur dans une organisation Cloud Foundry, cela peut prendre plusieurs minutes avant que {{site.data.keyword.contdelivery_short}} ne détecte le nouvel utilisateur et lui permette d'accéder à la chaîne d'outils.


## J'ai créé une chaîne d'outils dans une organisation Cloud Foundry, pourquoi la page Chaînes d'outils indique-t-elle qu'un service Continuous Delivery est requis ?
{: #service_required_cloud_foundry}
{: faq}

Lorsque vous créez une chaîne d'outils dans un groupe de ressources ou une organisation qui ne possède pas d'instance du service {{site.data.keyword.contdelivery_short}}, la plateforme de chaîne d'outils tente de créer automatiquement une instance du service à l'aide du plan Lite. Le message d'erreur indique que la plateforme de chaîne d'outils n'a pas pu créer l'instance de service.

Cette erreur peut se produire lorsque vous créez une chaîne d'outils dans la région Sud des Etats-Unis et dans une organisation Cloud Foundry qui ne possède pas déjà une instance de {{site.data.keyword.contdelivery_short}}. Dans la région Sud des Etats-Unis, vous devez créer toutes les nouvelles instances du service {{site.data.keyword.contdelivery_short}} dans des groupes de ressources. 

Vous pouvez créer la chaîne d'outils dans un groupe de ressources ou créer la chaîne d'outils dans une organisation qui possède déjà une instance de {{site.data.keyword.contdelivery_short}}.
  

## Comment puis-je déplacer ma chaîne d'outils d'une organisation Cloud Foundry vers un groupe de ressources ?
{: #toolchain_move_to_resource_group}
{: faq}

Il n'existe pas encore de fonction permettant de migrer automatiquement les chaînes d'outils d'une organisation Cloud Foundry vers un groupe de ressources. Au lieu de cela, vous pouvez créer manuellement la chaîne d'outils à nouveau dans un groupe de ressources, puis supprimer la chaîne d'outils originale de l'organisation Cloud Foundry.


## J'ai essayé de déployer une application dans {{site.data.keyword.Bluemix_notm}}, pourquoi ai-je reçu une erreur ?
{: #org_outofmemory}
{: faq}

Lorsque vous essayez de déployer une application dans {{site.data.keyword.Bluemix_notm}}, si vous obtenez le message d'erreur suivant, la quantité de mémoire restant dans votre organisation est inférieure à celle de la mémoire requise par l'application que vous souhaitez déployer.

`FAILED Erreur de serveur, code statut : 400, code d'erreur : 100005, message : vous avez dépassé la limite mémoire de votre organisation.`

Vous pouvez soit augmenter le quota de mémoire de votre compte ou réduire la mémoire utilisée par vos applications. Le quota de mémoire maximal pour un compte d'essai est 2 Go. Pour augmenter le quota de mémoire de votre compte, convertissez votre compte d'essai en compte payant. Pour obtenir des informations sur la conversion de votre compte d'essai en compte payant, voir [Comment mettre à niveau ou modifier mon compte ?](/docs/account?topic=account-accountfaqs#changeacct). Pour réduire la mémoire utilisée par vos applications, utilisez la console {{site.data.keyword.Bluemix_notm}} ou l'interface de ligne de commande cf.

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


## J'ai créé une application. Pourquoi la barre d'exécution n'affiche-t-elle pas les icônes Live Sync d'{{site.data.keyword.Bluemix_notm}} dans {{site.data.keyword.webide}} ?
{: #ts_llz_lkb_3r}
{: faq}

![ Barre d'exécution](images/webide_runbar_light.png)   

Lorsque vous éditez une application Node.js dans l'interface {{site.data.keyword.webide}}, les icônes d'édition directe, de redémarrage rapide et de débogage d'{{site.data.keyword.Bluemix_notm}} ne sont pas disponibles dans la barre d'exécution dans les circonstances suivantes :


* Le fichier `manifest.yml` n'est pas stocké au niveau supérieur de votre projet.
* Votre application est stockée dans un sous-répertoire et non dans le répertoire principal, et le chemin d'accès au sous-répertoire n'est pas indiqué dans le fichier `manifest.yml`.
* L'application ne contient pas de fichier `package.json`.


Si le fichier `manifest.yml` n'est pas stocké dans le répertoire principal, placez-le dedans. Si votre application est stockée dans un sous-répertoire, spécifiez le chemin d'accès au sous-répertoire dans le fichier `manifest.yml`. Si l'application ne contient pas de fichier `package.json`, créez-en un dans le même répertoire que votre application.


## J'ai cliqué sur le bouton d'exécution de {{site.data.keyword.webide}}. Où se trouvent les fichiers journaux ? 
{: #web_ide_log_files}
{: faq}  

Lorsque vous cliquez sur le bouton d'exécution, les contenus de votre espace de travail sont envoyés à Cloud Foundry de la même manière qu'ils sont déployés si vous tapez sur `cf push` à partir de votre bureau. Vous trouverez les fichiers journaux dans le tableau de bord Cloud Foundry.

Pour en savoir plus sur le déploiement des contenus de votre espace de travail, voir [Déploiement d'une application à partir de votre espace de travail](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy).


## Comment puis-je éviter que l'interface {{site.data.keyword.webide}} sélectionne automatiquement tous les changements de la vue Git ? 
{: #web_ide_git_view}
{: faq} 

{{site.data.keyword.webide}} suppose par défaut que vous souhaitez envoyer les changements sortants à votre référentiel de code à chaque fois que vous accédez à la page du référentiel Git. Si vous souhaitez sélectionner manuellement les ressources que vous souhaitez valider, synchroniser, redéfinir et remplacer, décochez la case **Toujours sélectionner les fichiers modifiés** sur la page des préférences de GIT.


## Pourquoi {{site.data.keyword.webide}} ne prend-il pas en charge le langage que j'utilise ? 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}} fournit des outils complets et un support pour JavaScript, HTML et CSS. Il fournit également une coloration syntaxique pour la plupart des langages populaires. Vous ne pouvez pas étendre {{site.data.keyword.webide}} pour prendre en charge un langage particulier. Pour afficher une liste complète des langages pris en charge par {{site.data.keyword.webide}}, voir [Langages pris en charge](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages).


## Comment affiche-t-on le statut d'{{site.data.keyword.Bluemix_notm}} et du service {{site.data.keyword.contdelivery_short}} ?
{: #toolchains_load}
{: faq}

Vérifiez la page Statut d'{{site.data.keyword.Bluemix_notm}} pour déterminer si des problèmes connus affectent la plateforme {{site.data.keyword.Bluemix_notm}} et les principaux services dans {{site.data.keyword.Bluemix_notm}}.

Vous pouvez afficher la page Statut en choisissant l'une des options suivantes :

  * Connectez vous à la console {{site.data.keyword.Bluemix_notm}}. Dans la barre de menus, cliquez sur **Support** et sélectionnez **Statut**. Recherchez dans les ressources répertoriées l'icône ![](../../get-support/images/some_issues.svg) signalant un problème. Celle-ci peut indiquer une indisponibilité.
  * Un accès direct est disponible sous [{{site.data.keyword.Bluemix_notm}} - Statut du système](https://cloud.ibm.com/status){: external}.

Pour plus d'informations sur la page Statut d'{{site.data.keyword.Bluemix_notm}}, voir [Viewing {{site.data.keyword.Bluemix_notm}} status](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status).


## Comment puis-je transférer des artefacts entre les travaux de pipeline ?
{: #artifacts_pipeline_jobs}
{: faq}

Etant donné que tous les travaux de pipeline d'une étape reçoivent la même entrée d'étape, vous ne pouvez pas transférer des artefacts entre des travaux qui appartiennent à la même étape. Cependant, les travaux de génération génèrent des artefacts que les travaux se trouvant à d'autres étapes peuvent utiliser. Pour transférer des artefacts entre deux travaux, déplacez chaque travail dans une étape distincte. Pour plus d'informations sur les travaux de pipeline, voir [Travaux](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs).


## Existe-t-il une limite de temps maximale pour l'exécution de mes travaux de pipeline ?
{: #pipeline_jobs_time_limit}
{: faq}

Chaque travail de pipeline peut durer un maximum de 60 minutes. Si un travail dépasse cette limite de temps, le travail échoue. Déterminez si le travail que le pipeline accomplit peut être divisé en étapes plus petites. Vous pouvez diviser le travail de pipeline en plusieurs travaux de pipeline plus courts dont la durée d'exécution est inférieure à 60 minutes.


## À quel point les propriétés sécurisées du pipeline sont-elles sûres ?
{: #pipeline_secure_properties}
{: faq}

Les propriétés sécurisées du pipeline sont chiffrées avec AES-128 et déchiffrées immédiatement avant leur transmission à votre script de pipeline. Ces propriétés sont également masquées à l'aide d'astérisques dans l'interface utilisateur des propriétés et dans les fichiers journaux de votre pipeline. Avant que les données ne soient écrites dans le fichier journal de votre travail de pipeline, elles sont analysées pour trouver des correspondances exactes avec toutes les valeurs des propriétés sécurisées du pipeline. Si une correspondance est trouvée, elle est masquée par des astérisques. Soyez prudent lorsque vous travaillez avec des propriétés sécurisées et des fichiers journaux car seules les correspondances exactes sont masquées. 
