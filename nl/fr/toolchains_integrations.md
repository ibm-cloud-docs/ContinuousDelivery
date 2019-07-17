---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-27"

keywords: tool integrations, IBM Cloud Public, Alert Notification, Configuring Artifactory

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

# Configuration des intégrations d'outils
{: #integrations}

Vous pouvez configurer des intégrations d'outils prenant en charge des tâches de développement, de déploiement et d'opérations lors de la création d'une chaîne d'outils ouverte, ou bien vous pouvez ajouter et configurer des intégrations d'outils afin de personnaliser une chaîne d'outils existante.  
{:shortdesc}

Les intégrations d'outils disponibles pour ajouter et configurer votre chaîne d'outils varient selon que vous utilisez des chaînes d'outils sur {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated. Si vous utilisez des chaînes d'outils sur {{site.data.keyword.Bluemix_notm}} Public, les intégrations d'outils qui sont disponibles dépendent de la région de votre chaîne d'outils et de la disponibilité des intégrations d'outils dans cette région. Si
vous utilisez des chaînes d'outils sur
{{site.data.keyword.Bluemix_notm}} Dedicated, les
intégrations d'outils qui sont disponibles dépendent de la manière
dont {{site.data.keyword.contdelivery_full}} a été configuré dans
votre environnement spécifique.

|Intégration d'outil |Disponible sur {{site.data.keyword.Bluemix_notm}} Public	|Disponible sur {{site.data.keyword.Bluemix_notm}} Dedicated (dépendant de l'environnement)|
|:----------|:------------------------------|:------------------|
|{{site.data.keyword.alertnotificationshort}}		|Sud des Etats-Unis		|Non		|
|Artifactory		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|Availability Monitoring		|Sud des Etats-Unis		|Non		|
|Bitbucket		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Non		|
|Cloud Event Management		|Sud des Etats-Unis		|Non		|
|{{site.data.keyword.deliverypipeline}} 		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni	   	|Oui  		|
|{{site.data.keyword.deliverypipeline}} Private Worker			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Non		|
|{{site.data.keyword.DRA_short}} 		|Sud des Etats-Unis, Allemagne, Royaume-Uni		|Non			|
|Eclipse Orion {{site.data.keyword.webide}}		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui			|
|{{site.data.keyword.gitrepos}}	|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Non		|
|GitHub		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|Dedicated {{site.data.keyword.ghe_short}} and Issues			|Non		|Oui		|
|GitLab		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Non		|
|Jenkins		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|JIRA		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|Nexus			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|Autre outil			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|PagerDuty			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|Rational Team Concert			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|Sauce Labs		|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Non		|
|Slack			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
|SonarQube			|Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo, Royaume-Uni		|Oui		|
{: caption="Tableau 1. Intégrations d'outils disponibles pour les chaînes d'outils sur {{site.data.keyword.Bluemix_notm}} Public et Dedicated" caption-side="top"}

Si vous souhaitez commencer à développer avec votre code source sur {{site.data.keyword.Bluemix_notm}} Public, configurez l'intégration d'outils GitHub ou l'intégration d'outils {{site.data.keyword.gitrepos}} avant de configurer {{site.data.keyword.deliverypipeline}}. Si vous souhaitez débuter le développement par votre code source sur {{site.data.keyword.Bluemix_notm}} Dedicated, configurez l'intégration d'outils {{site.data.keyword.ghe_short}} ou l'intégration d'outils GitHub avant de configurer {{site.data.keyword.deliverypipeline}}.
{: tip}


## Configuration de l'application Alert Notification
{: #alertnotification}

{{site.data.keyword.alertnotificationfull}} est une solution hybride basée sur le cloud, que vous pouvez utiliser pour centraliser et simplifier votre stratégie de notification. Elle fonctionne avec d'autres applications sur site et basées sur le cloud. Les alertes sont envoyées à {{site.data.keyword.alertnotificationshort}} à l'aide d'une API RESTful sécurisée.

Configurez {{site.data.keyword.alertnotificationshort}} pour recevoir des notifications sur les problèmes qui surviennent au cours de votre processus DevOps.

### Conditions préalables requises

1. Si vous ne disposez pas d'un compte {{site.data.keyword.alertnotificationshort}}, inscrivez-vous pour en obtenir un :

 a. Ouvrez la page [IBM {{site.data.keyword.alertnotificationshort}}](https://www.ibm.com/us-en/marketplace/alert-notification){:external} dans IBM Marketplace.

 b. Achetez un abonnement ou inscrivez-vous à l'essai gratuit pendant 90 jours.

1. Une fois que votre compte {{site.data.keyword.alertnotificationshort}} est configuré, ouvrez votre [tableau de bord My IBM](https://myibm.ibm.com/dashboard/){:external}.
1. En regard d'IBM {{site.data.keyword.alertnotificationshort}}, cliquez sur **Lancer**.
1. Cliquez sur **Gérer les clés d'API**, puis sur **Créer une clé d'API**.
1. Dans la zone **Créer une clé d'API**, saisissez une description.
1. Cliquez sur **Générer**. Les informations relatives à la nouvelle clé d'API, notamment son nom et son mot de passe, s'affichent. Etant donné que vous aurez besoin de ces informations pour la configuration de l'intégration d'outils, gardez la fenêtre Nouvelle clé d'API ouverte. A des fins de sécurité, vous ne pouvez pas récupérer le mot de passe de la clé d'API ultérieurement.

### Configuration de l'application Alert Notification

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **{{site.data.keyword.alertnotificationshort}}**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.alertnotificationshort}}**.

1. Saisissez l'URL de l'API {{site.data.keyword.alertnotificationshort}} que vous souhaitez utiliser. Vous trouverez cette adresse sur la page Gestion des clés d'API du service {{site.data.keyword.alertnotificationshort}} ; par exemple, `https://ibmnotifybm.mybluemix.net/api/alerts/v1`.
1. Saisissez le nom de la clé d'API pour {{site.data.keyword.alertnotificationshort}}. Vous le trouverez dans la fenêtre Nouvelle clé d'API.
1. Saisissez le mot de passe généré par {{site.data.keyword.alertnotificationshort}} pour la clé d'API. Vous le trouverez dans la fenêtre Nouvelle clé d'API.
1. Cliquez sur **Créer une intégration**.
1. A partir de votre chaîne d'outils, cliquez sur **{{site.data.keyword.alertnotificationshort}}**.

### Plus d'informations sur l'application Alert Notification

Pour en savoir plus sur {{site.data.keyword.alertnotificationshort}}, lisez l'[article sur IBM {{site.data.keyword.alertnotificationshort}}](https://www.ibm.com/cloud/garage/content/manage/tool_alert_notification/){:external} sur IBM Cloud Garage Method ou consultez ces tutoriels :

  * [Add a tool integration to a toolchain](https://www.ibm.com/cloud/garage/tutorials/add-a-tool-integration-to-a-toolchain){:external}

  * [Manage your {{site.data.keyword.Bluemix_notm}} application by using {{site.data.keyword.Bluemix_notm}} Availability Monitoring and Alert Notification](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:external}


## Configuration d'Artifactory
{: #artifactory}

Configurez le gestionnaire de référentiels Artifactory afin de stocker les artefacts de génération dans votre référentiel Artifactory :

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **Artifactory**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Artifactory**.

1. Saisissez l'URL du référentiel Artifactory qui doit s'ouvrir lorsque vous cliquez sur la carte Artifactory.
1. Sélectionnez le type de référentiel auquel vous souhaitez vous connecter.
1. Si vous utilisez un registre npm Artifactory, procédez comme suit :

 a. Saisissez l'adresse électronique associée à votre registre.

 b. Saisissez le jeton d'authentification associé à votre registre.

 c. Saisissez l'URL de votre référentiel d'édition Artifactory, qui est votre registre privé sur le serveur Artifactory.

 d. Saisissez l'URL du registre miroir ou public que vous utilisez pour combiner plusieurs registres npm publics et privés. Par exemple, cette URL peut être l'adresse du registre virtuel sur votre serveur Artifactory, qui peut accéder à la fois à votre registre privé et à un cache du registre npm global.

1. Si vous utilisez un référentiel Maven Artifactory, procédez comme suit :

 a. Saisissez l'ID utilisateur associé à votre référentiel.

 b. Saisissez le mot de passe associé à votre référentiel.

 c. Saisissez l'URL de votre référentiel d'édition Artifactory, qui est votre référentiel d'édition privé sur le serveur Artifactory.

 d. Saisissez l'URL de votre référentiel d'image instantanée Artifactory, qui est votre référentiel d'image instantanée privé sur le serveur Artifactory.

 e. Saisissez l'URL du référentiel miroir ou public que vous utilisez pour combiner plusieurs référentiels Maven publics et privés. Par exemple, cette URL peut être l'adresse du référentiel virtuel sur votre serveur Artifactory, qui peut accéder à la fois à vos référentiels privés et à un cache du référentiel Maven central.

1. Cliquez sur **Créer une intégration**.
1. Cliquez sur la carte du référentiel Artifactory à utiliser. Le site Web Artifactory s'ouvre ; vous pouvez y afficher le contenu du référentiel.
1. Facultatif : Si vous utilisez une chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous voulez générez votre application à l'aide d'Artifactory avec npm, configurez votre pipeline pour ajouter un travail de génération npm. Pour des instructions de configuration du travail de génération, voir la section [Configuration d'un travail de génération npm Artifactory sur votre pipeline](#config_artifactory_npm).
1. Facultatif : Si vous utilisez une chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous voulez générer votre application à l'aide d'Artifactory avec Maven, configurez votre pipeline pour ajouter un travail de génération Maven. Pour des instructions de configuration du travail de génération, voir la section [Configuration d'un travail de génération Maven Artifactory sur votre pipeline](#config_artifactory_maven).

### Configuration d'un travail de génération npm Artifactory sur votre pipeline
{: #config_artifactory_npm}

Avant de configurer un travail de génération npm dans votre pipeline, vous devez disposer d'un pipeline opérationnel qui peut utiliser votre référentiel SCM de génération en entrée. Vous devez également configurer Artifactory pour votre chaîne d'outils. Pour les instructions de configuration d'Artifactory, voir la section [Artifactory](#artifactory).

Configurez {{site.data.keyword.deliverypipeline}} pour ajouter un travail de génération npm :

1. Créez une étape et définissez l'entrée sur le référentiel SCM approprié.
1. Dans l'étape, ajoutez un travail de génération.
1. Configurez le travail de génération :
  ![travail de génération npm](images/artifactory_npm_job.png)

  a. Pour le type de générateur, sélectionnez **NPM Build**.

  b. Si vous avez configuré plusieurs instances de l'intégration d'outils Artifactory, saisissez le nom de l'intégration d'outils Artifactory pour laquelle vous souhaitez configurer le travail de génération npm.

  c. Pour le type d'intégration d'outils, sélectionnez **Artifactory**.

  d. Pour la commande de génération, saisissez les commandes permettant de générer votre module npm ou de le publier dans votre registre. Cet exemple montre les commandes de génération ou de publication du module.
     ```
     npm install
     # ou
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  Vous pouvez trouver l'URL et les données d'identification de l'utilisateur dont vous vous êtes servi pour vous connecter à votre registre dans les paramètres de configuration pour l'intégration des outils Artifactory.
  {: tip}

  e. Si votre travail de génération est publié dans le registre Artifactory et si le format de votre version de module de noeud est `x.y.z-SNAPSHOT.w`, cochez la case **Incrémenter la version du module d'instantané**. Le travail de génération met automatiquement à jour la version du module avant que le travail ne soit publié dans le registre Artifactory. Le travail sélectionne la version la plus élevée du module à partir du registre npm et du fichier local `package.json`, et incrémente la version du module à l'aide de semver. Le travail de génération ne répercute pas les modifications dans le référentiel SCM.

1. Cliquez sur **SAUVEGARDER**. Lors de l'exécution de votre pipeline, ce travail de génération utilise les informations de configuration provenant de l'intégration d'outils pour la connexion à votre registre npm.

### Configuration d'un travail de génération Maven Artifactory sur votre pipeline
{: #config_artifactory_maven}

Avant de configurer un travail de génération Maven sur votre pipeline, vous devez disposer d'un pipeline opérationnel qui peut utiliser votre référentiel SCM de génération en entrée et vous devez configurer Artifactory pour votre chaîne d'outils. Pour les instructions de configuration d'Artifactory, voir la section [Artifactory](#artifactory).

Configurez {{site.data.keyword.deliverypipeline}} pour ajouter un travail de génération Maven :

1. Créez une étape et définissez l'entrée sur le référentiel SCM approprié.
1. Dans l'étape, ajoutez un travail de génération.
1. Configurez le travail de génération :
  ![travail de génération Maven](images/artifactory_maven_job.png)

  a. Pour le type de générateur, sélectionnez **Maven Build**.

  b. Si vous avez configuré plusieurs instances de l'intégration d'outils Artifactory, saisissez le nom de l'intégration d'outils Artifactory pour laquelle vous souhaitez configurer le travail de génération Maven.

  c. Pour le type d'intégration d'outils, sélectionnez **Artifactory**.

  d. Pour la commande de génération, saisissez les commandes permettant de générer votre module Maven ou de le publier dans votre registre d'image instantanée. Cet exemple montre les commandes permettant de générer le module ou de le publier dans un registre d'image instantanée.
     ```
     mvn -B clean package
     # ou
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  Vous pouvez trouver l'URL et les données d'identification de l'utilisateur dont vous vous êtes servi pour vous connecter à votre registre dans les paramètres de configuration pour l'intégration des outils Artifactory.
  {: tip}

1. Cliquez sur **SAUVEGARDER**. Lors de l'exécution de votre pipeline, ce travail de génération utilise les informations de configuration provenant de l'intégration d'outils pour la connexion à votre référentiel Maven.

### Plus d'informations sur Artifactory

Pour en savoir plus sur Artifactory, lisez l'[article sur Artifactory](https://www.ibm.com/cloud/garage/content/deliver/tool_artifactory/){:external} sur IBM Cloud Garage Method.


## Ajout d'Availability Monitoring
{: #availabilitymonitoring}

{{site.data.keyword.prf_hublong}} isole les problèmes, identifie les masques et améliore les performances avant que les utilisateurs ne s'en trouvent affectés. Vous pouvez tester votre application depuis le monde entier, l'intégrer à des pipelines de distribution et gagner en connaissance sur la façon d'optimiser en permanence votre code.

Cette intégration d'outils est préconfigurée et ne nécessite aucun paramètre de configuration. Vous ne pouvez pas la reconfigurer.
{: tip}

Pour tester, surveiller et améliorer la santé de votre application au fur et à mesure de sa création, ajoutez l'intégration d'outils {{site.data.keyword.prf_hubshort}}.

1. Sur le tableau de bord DevOps, sur la page Chaîne d'outils, cliquez sur la chaîne d'outils à laquelle vous souhaitez ajouter {{site.data.keyword.prf_hubshort}}. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.prf_hubshort}}**.

1. Cliquez sur **Créer une intégration**.
1. Cliquez sur **{{site.data.keyword.prf_hubshort}}** pour ouvrir le tableau de bord {{site.data.keyword.prf_hubshort}}, sélectionner une application et configurer sa surveillance.

### Plus d'informations sur Availability Monitoring

Pour en savoir plus sur {{site.data.keyword.prf_hubshort}}, lisez l'article [{{site.data.keyword.prf_hublong}}](https://www.ibm.com/cloud/garage/practices/manage/tool_bluemix_availability_monitoring/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel :

  * [Manage your {{site.data.keyword.Bluemix_notm}} application by using {{site.data.keyword.Bluemix_notm}} Availability Monitoring and Alert Notification](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:external}


## Configuration de Bitbucket
{: #bitbucket}

Stockez votre code source dans un référentiel nouveau ou existant sur bitbucket.org et engagez-vous dans le codage social à travers les wikis, le suivi des problèmes et les demandes d'extraction.

Configurez Bitbucket pour collaborer avec votre équipe sur le code :

1. Sur le tableau de bord DevOps, cliquez sur **Chaînes d'outils**. Cliquez sur la chaîne d'outils à laquelle vous souhaitez ajouter Bitbucket. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Bitbucket**.

   Si vous configurez cette intégration d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous n'avez pas autorisé {{site.data.keyword.Bluemix_notm}} à accéder à Bitbucket, cliquez sur **Autorisation** pour accéder au site Web Bitbucket. Si vous n'avez pas de session Bitbucket active, vous êtes invité à vous connecter. Cliquez sur **Accorder l'accès** pour autoriser {{site.data.keyword.Bluemix_notm}} Toolchains à accéder aux parties suivantes de votre compte Bitbucket :
   
   * **Lisez vos informations de compte**. Obtenez des informations de base sur l'utilisateur pour remplir l'interface utilisateur.
   
   * **Lisez et modifiez les problèmes des référentiels**. Autorisez {{site.data.keyword.contdelivery_short}} à mettre à jour les problèmes pour indiquer le moment où le pipeline déploie les validations associées à ces problèmes. 
   
   * **Lisez les paramètres de projet de votre équipe ainsi que les référentiels contenus dans les projets de votre équipe.**. Autorisez {{site.data.keyword.contdelivery_short}} à intégrer les référentiels appartenant à des équipes.
   
   * **Lisez et modifiez vos référentiels et leurs demandes d'extraction**. Autorisez {{site.data.keyword.contdelivery_short}} à envoyer un exemple de code dans des référentiels, lorsque les utilisateurs demandent le code.
   
   * **Administrez vos référentiels**. Autorisez {{site.data.keyword.contdelivery_short}} à créer des référentiels, à la demande des utilisateurs.
   
   * **Lisez les informations d'appartenance à votre équipe**. Autorisez {{site.data.keyword.contdelivery_short}} à afficher une liste de vos équipes dans le menu **Propriétaire** qui s'affiche lorsque vous créez un nouveau référentiel.
   
   * **Lisez et modifiez les webhooks de vos référentiels**. Autorisez le pipeline à déclencher des générations lorsque des validations sont envoyées dans un référentiel.
   {: tip}
   
   Si vous disposez d'une session Bitbucket active mais n'avez pas saisi votre mot de passe récemment, vous êtes invité à entrer votre mot de passe Bitbucket pour confirmation.

1. Cliquez sur le serveur Bitbucket que vous souhaitez utiliser.
1. Si vous souhaitez utiliser un référentiel Bitbucket en particulier, entrez son URL. Pour le type de référentiel, cliquez sur **Existant**.
1. Si vous souhaitez utiliser un nouveau référentiel Bitbucket, saisissez un nom pour le référentiel, entrez l'URL du référentiel que vous clonez ou déviez, puis sélectionnez le type de référentiel :

 a. Pour créer un référentiel vide, cliquez sur **Nouveau**.

 b. Pour créer une copie d'un référentiel, cliquez sur **Cloner**.

 c. Pour dévier un référentiel afin de pouvoir participer aux modifications via des demandes d'extraction, cliquez sur **Dévier**.

1. Pour créer un référentiel privé sur le serveur, sélectionnez la case **Rendre ce référentiel privé**.
1. Pour utiliser Bitbucket Issues pour le suivi des problèmes, sélectionnez la case **Activer Bitbucket Issues**.
1. Pour suivre le déploiement des modifications du code en créant des étiquettes et des commentaires sur les validations, ainsi que des libellés et des commentaires sur les problèmes référencés par les validations, cochez la case **Suivi du déploiement des modifications du code**. Pour plus d'informations, voir [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Cliquez sur **Créer une intégration**.
1. A partir de votre chaîne d'outils, cliquez sur la carte du référentiel Bitbucket que vous souhaitez utiliser. Le site Web de Bitbucket s'ouvre avec le contenu du référentiel.
1. Si vous avez activé Bitbucket Issues, cliquez sur **Bitbucket Issues** pour l'ouvrir. Vous pouvez utiliser cette instance de Bitbucket Issues pour l'ensemble de votre chaîne d'outils, même si cette dernière contient plusieurs référentiels Bitbucket.

Si vous ne disposez pas d'un droit maître ou propriétaire sur le référentiel avec lequel vous établissez une liaison, votre intégration sera limitée car vous ne pouvez pas utiliser un webhook. Les webhooks sont nécessaires pour exécuter un pipeline automatiquement lorsqu'une validation est envoyée par commande push au référentiel. Sans
webhook, vous devez démarrer manuellement vos pipelines.
{: tip}

### Plus d'informations sur Bitbucket

Pour en savoir plus sur Bitbucket, lisez l'[article sur Bitbucket](https://www.ibm.com/cloud/garage/content/code/tool_bitbucket/){:external} sur IBM Cloud Garage Method.


## Ajout de Cloud Event Management
{: #cloudeventmanagement}

{{site.data.keyword.evtmgt_full}} fournit une vue d'ensemble des problèmes qui surviennent dans vos services, vos applications et votre infrastructure. Vous pouvez configurer la gestion des incidents en temps réel pour résoudre les problèmes plus efficacement.

Cette intégration d'outils est préconfigurée et ne nécessite aucun paramètre de configuration. Vous ne pouvez pas la reconfigurer.
{: tip}

Pour aider votre équipe DevOps à atteindre des objectifs fiables et opérationnels en matière de santé, de qualité de service et d'amélioration continue, ajoutez Cloud Event Management à votre chaîne d'outils :

1. Sur le tableau de bord DevOps, cliquez sur **Chaînes d'outils**. Cliquez sur la chaîne d'outils à laquelle vous souhaitez ajouter Cloud Event Management. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Cloud Event Management**.

1. Cliquez sur **Créer une intégration**.
1. A partir de votre chaîne d'outils, cliquez sur l'une des cartes d'outils suivantes :

 * **Cloud Event Management** pour vous initier à Cloud Event Management.

 * **{{site.data.keyword.alertnotificationshort}}** pour créer des règles qui déterminent le moment où les utilisateurs reçoivent des notifications d'incident.

 * **Runbook Automation** pour gérer votre catalogue de dossiers d'exploitation dans Cloud Event Management.

### Plus d'informations sur Cloud Event Management

Pour en savoir plus sur Cloud Event Management, lisez l'[article sur Cloud Event Management](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){:external} sur IBM Cloud Garage Method.


## Configuration de Delivery Pipeline
{: #deliverypipeline}

{{site.data.keyword.deliverypipeline}} automatise le déploiement continu de vos projets via des séquences d'étapes qui extraient des travaux en entrée et d'exécution tels que des générations, des tests et des déploiements.

Configurez {{site.data.keyword.deliverypipeline}} afin d'automatiser la génération, le test et le déploiement en continu de vos applications.

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **{{site.data.keyword.deliverypipeline}}**. En fonction du modèle utilisé, des zones différentes peuvent être disponibles. Passez en revue les valeurs de zone par défaut et, si nécessaire, modifiez ces paramètres.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.deliverypipeline}}**.

1. Indiquez un nom pour votre nouveau pipeline.
1. Si vous comptez utiliser votre pipeline pour déployer une interface utilisateur, cochez la case **Afficher les applications dans le menu AFFICHER
L'APPLICATION**. Toutes les applications créées par votre pipeline sont affichées dans la liste **Afficher l'application** de la page
Présentation de la chaîne d'outils.
1. Cliquez sur **Créer une intégration** pour ajouter {{site.data.keyword.deliverypipeline}} à votre chaîne d'outils.
1. Cliquez sur **{{site.data.keyword.deliverypipeline}}** pour afficher le pipeline et le configurer. Pour en savoir plus sur les notions de base et la configuration d'un pipeline, voir [Génération et déploiement de pipelines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

  Si vous souhaitez que le pipeline s'exécute automatiquement lorsqu'une validation est envoyée à votre référentiel GitHub, {{site.data.keyword.ghe_short}} ou Git, procédez comme suit :

   a. Configurez GitHub, {{site.data.keyword.ghe_short}} ou {{site.data.keyword.gitrepos}} pour votre chaîne d'outils avant de définir les étapes pour votre pipeline. Ces étapes requièrent les URL de vos référentiels. Chaque étape de pipeline peut faire référence à un seul des référentiels GitHub, {{site.data.keyword.ghe_short}} ou Git associés à votre chaîne d'outils. Pour
savoir comment configurer GitHub, voir la section [GitHub](#github). Pour la configuration de {{site.data.keyword.ghe_short}} Dedicated, voir [Initiation à {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-getting-started). Pour les instructions de configuration de {{site.data.keyword.gitrepos}}, voir la section [{{site.data.keyword.gitrepos}}](#grit).

   b. Utilisez un webhook. Sans webhook, vous pouvez seulement exécuter les pipelines manuellement. Pour utiliser un webhook lorsque vous vous connectez à un référentiel GitHub
ou {{site.data.keyword.ghe_short}}, vous devez disposer d'un droit d'administrateur. Pour associer un référentiel {{site.data.keyword.gitrepos}}, vous devez disposer d'un droit Maître ou Propriétaire.

1. Facultatif : si vous utilisez une chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} public et souhaitez que Sauce Labs exécute des tests sur votre application, configurez {{site.data.keyword.deliverypipeline}} pour ajouter un travail de test Sauce Labs. Pour des instructions de configuration du travail de test, voir la section [Configuration d'un travail de test Sauce Labs sur votre pipeline](#config_saucelabs).

### Configuration d'un travail de test Sauce Labs sur votre pipeline
{: #config_saucelabs}

Avant de configurer un travail de test Sauce Labs sur votre pipeline, vous avez besoin d'un pipeline opérationnel qui comporte des étapes pour la génération et le déploiement de votre application. Vous devez également configurer Sauce Labs pour votre chaîne d'outils. Pour des instructions de configuration de Sauce Labs, voir la section [Configuration de Sauce Labs](#saucelabs).

Configurez {{site.data.keyword.deliverypipeline}} pour ajouter un travail de test Sauce Labs.

1. Si vous n'avez pas d'étape pour le déploiement d'une version de test de votre application, créez-en une.
1. Dans l'étape, ajoutez un travail de test après le travail de déploiement. Le fait de placer ces travaux dans la même étape leur permet d'accéder au même ensemble de propriétés d'environnement.   
  ![Travail de test](images/toolchain_test_job.png)

1. Configurez l'étape. Sur l'onglet **PROPRIETES D'ENVIRONNEMENT**, créez la propriété CF_APP_NAME.

  Le nom d'utilisateur et la clé d'accès Sauce Labs sont disponibles dans le script de travail de test via les variables d'environnement SAUCE_USERNAME et SAUCE_ACCESS_KEY. Lorsque vous rédigez vos tests, vous devez utiliser ces variables d'environnement pour vous authentifier auprès de Sauce Labs.
  {: tip}

1. Configurez le travail de déploiement. Dans la zone **Script de déploiement**, ajoutez la commande suivante : `export CF_APP_NAME="$CF_APP"`. Cette commande exporte le nom d'application en tant que propriété d'environnement.
1. Configurez le travail de test. 

  Les zones d'**instance de service**, de **cible**, d'**organisation** et d'**espace** sont renseignées avec les informations Sauce Labs de nom d'utilisateur, région, organisation et espace que vous utilisez.
  {: tip}

  a. Pour le type d'outil de test, sélectionnez **Sauce Labs**.

  b. Pour l'instance de service, sélectionnez le nom d'utilisateur Sauce Labs utilisé lors de la configuration de Sauce Labs pour votre chaîne d'outils.

   Pour afficher le nom d'utilisateur et la clé d'accès dont vous vous êtes servi lorsque vous avez configuré Sauce Labs pour votre chaîne d'outils, cliquez sur **Configurer**.
   {: tip}

  c. Dans la zone **Commande d'exécution de test**, entrez les commandes d'installation des dépendances qui sont requises par vos tests, puis exécutez les tests. Par exemple, pour une application Node.js, vous pourriez entrer les commandes suivantes :
     ```
     npm install
     node_modules/grunt-cli/bin/grunt test:sauce:parallel
     ```

    d. Si vous souhaitez voir vos rapports de test dans les journaux de travail, sélectionnez la case **Activer le rapport de test** et définissez le masque de fichiers de résultats de test sur `test/*.xml`.

1. Cliquez sur **SAUVEGARDER**. A chaque exécution de votre pipeline, vos tests Sauce Labs s'exécuteront.

### Plus d'informations sur Delivery Pipeline

Pour en savoir plus sur {{site.data.keyword.deliverypipeline}}, lisez [Utilisation de pipelines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline-working) et l'[article sur Delivery Pipeline](https://www.ibm.com/cloud/garage/content/deliver/tool_delivery_pipeline/){:external} sur IBM Cloud Garage Method ou consultez ces tutoriels :

  * [Create a pipeline](https://www.ibm.com/cloud/garage/tutorials/create-a-pipeline){:external}

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}


## Configuration de {{site.data.keyword.deliverypipeline}} Private Worker
{: #privateworker}

{{site.data.keyword.deliverypipeline}} Private Worker se connecte à un ou plusieurs agents privés qui exécutent des charges de travail {{site.data.keyword.deliverypipeline}} isolées.

Configurez l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker pour rendre les agents privés disponibles dans les pipelines, dans une chaîne d'outils :

1. Si vous configurez cette intégration d'outil lorsque vous créez une chaîne d'outils, dans la section Intégrations configurables, cliquez sur **{{site.data.keyword.deliverypipeline}} Private Worker**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Entrez un nom pour l'intégration d'outil. Ce nom identifie un pool d'agents privés dans l'onglet **Agents** de l'étape de pipeline.
1. Entrez la clé d'API de votre ID de service pour authentifier l'accès à la file d'attente des travaux où un ou plusieurs agents privés peuvent rechercher un travail. Si vous ne disposez pas d'une clé d'API ID de service, cliquez sur **Créer** pour en générer une pour cet agent privé.
1. Cliquez sur **Créer une intégration**.
1. Dans votre chaîne d'outils, cliquez sur **{{site.data.keyword.deliverypipeline}} Private Worker** pour afficher une liste de tous les agents enregistrés à l'aide d'une clé d'API associée à cet ID de service.


## Ajout de DevOps Insights
{: #dra}

{{site.data.keyword.DRA_full}} collecte et analyse les résultats provenant de tests unitaires, de tests fonctionnels et d'outils de couverture de code afin de déterminer si votre code satisfait les critères prédéfinis à certains stades de votre processus de déploiement. Si votre code ne satisfait pas ou dépasse les critères, le déploiement est interrompu afin de prévenir tout risque. Vous pouvez utiliser {{site.data.keyword.DRA_short}} comme filet de sécurité pour votre environnement de distribution continue ou comme moyen d'implémenter et d'améliorer les normes de qualité.

 Cette intégration d'outils est uniquement disponible sur {{site.data.keyword.Bluemix_notm}} Public. Elle est préconfigurée et ne nécessite aucun paramètre de configuration. Vous ne pouvez pas la reconfigurer.
 {: tip}

Ajoutez {{site.data.keyword.DRA_short}} afin de gérer et d'améliorer la qualité de votre code dans {{site.data.keyword.Bluemix_notm}} en surveillant vos déploiements afin d'identifier les risques avant la publication.

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **{{site.data.keyword.DRA_short}}**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.DRA_short}}**.

1. Cliquez sur **Créer une intégration**.
1. Cliquez sur **{{site.data.keyword.DRA_short}}**, puis complétez les étapes de mise en route : créez des critères, connectez-les au pipeline, puis exécutez ce dernier.

### Plus d'informations sur DevOps Insights

Pour en savoir plus sur {{site.data.keyword.DRA_short}}, lisez l'[article sur {{site.data.keyword.DRA_short}}](https://www.ibm.com/cloud/garage/content/learn/tool_devops_insights/){:external} sur IBM Cloud Garage Method ou consultez ces tutoriels :

  * [Use the "Develop and test a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:external}

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}

  * [Explore {{site.data.keyword.DRA_full}}](https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights){:external}


## Ajout d'Eclipse Orion Web IDE
{: #webide}

Eclipse Orion {{site.data.keyword.webide}} est un environnement de développement Web intégré dans lequel vous pouvez créer, éditer, exécuter, déboguer et terminer des tâches de contrôle des sources. Vous pouvez facilement passer de l'édition à l'exécution, à la soumission, puis au développement.

 Cette intégration d'outils est préconfigurée. Elle ne requiert aucun paramètre de configuration et vous ne pouvez pas la reconfigurer.
 {: tip}

Pour effectuer des tâches de contrôle des sources, ajoutez l'intégration d'outils Eclipse Orion {{site.data.keyword.webide}} :

1. Si vous configurez cette intégration d'outils en même temps que vous créez la chaîne d'outils, dans la section Intégrations configurables, cliquez sur **Eclipse Orion {{site.data.keyword.webide}}**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Eclipse Orion {{site.data.keyword.webide}}**.

1. Cliquez sur **Créer une intégration**.
1. Cliquez sur **Eclipse Orion {{site.data.keyword.webide}}**. Votre espace de travail est prérempli avec vos référentiels GitHub ou {{site.data.keyword.ghe_short}}. Les référentiels associés à votre chaîne d'outils en cours sont mis en évidence.

### Plus d'informations sur Eclipse Orion Web IDE

Pour en savoir plus sur Eclipse Orion {{site.data.keyword.webide}}, voir [Edition de code avec Eclipse Orion {{site.data.keyword.webide}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide). Vous pouvez également lire l'[article sur Eclipse Orion {{site.data.keyword.webide}}](https://www.ibm.com/cloud/garage/content/code/tool_eclipse_orion_web_ide/){:external} sur IBM Cloud Garage Method. Consultez ces tutoriels pour essayer d'utiliser Eclipse Orion {{site.data.keyword.webide}} :

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}


## Configuration de Git Repos and Issue Tracking
{: #grit}

L'intégration d'outils {{site.data.keyword.gitrepos}} est basée sur GitLab Community Edition, un service d'hébergement Web pour les référentiels Git. Vous pouvez avoir des copies en local et à distance de vos référentiels. Pour en savoir plus, voir [{{site.data.keyword.gitrepos}}](https://us-south.git.cloud.ibm.com/help){:external}.

Si vous configurez {{site.data.keyword.gitrepos}} lors de la création de la chaîne d'outils, procédez comme suit :    

1. A la section Intégrations configurables, cliquez sur **Git Repos and Issue Tracking**.
1. Passez en revue les emplacements cible par défaut pour les référentiels Git. Ces référentiels sont clonés à partir des référentiels exemple. Si nécessaire, modifiez les noms des référentiels cible.

Si vous disposez d'une chaîne d'outils et que vous souhaitez faire migrer un référentiel Git de votre chaîne d'outils vers {{site.data.keyword.gitrepos}}, procédez comme suit :

Ces instructions s'appliquent aux chaînes d'outils qui contiennent déjà le référentiel Git que vous souhaitez faire migrer vers {{site.data.keyword.gitrepos}}. Pour savoir comment ajouter différents types de référentiels Git à votre chaîne d'outils, voir les sections [Configuration de GitHub](#github), [Configuration de GitHub Enterprise et Issues sur {{site.data.keyword.Bluemix_notm}} Dedicated](#configghe) et [Configuration de GitLab](#gitlab).
{: tip}

1. Dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur **Ajouter un outil**.
1. A la section Intégrations d'outils, cliquez sur **Git Repos and Issue Tracking**.
1. Pour créer une copie d'un référentiel Git, cliquez sur **Cloner** pour le type de référentiel. Saisissez un nouveau nom de référentiel et l'URL du référentiel source.
1. Si vous souhaitez utiliser l'option Problèmes pour le suivi des problèmes, cochez la case **Activer les problèmes**.
1. Si vous voulez suivre le déploiement des modifications du code en créant des étiquettes et des commentaires sur les validations, ainsi que des libellés et des commentaires sur les problèmes référencés par les validations, cochez la case **Suivi du déploiement des modifications du code**. Pour plus d'informations, voir [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Cliquez sur **Créer une intégration**.

Après avoir cloné le référentiel Git, vous pouvez le retirer de votre chaîne d'outils.
{: tip}

Si vous disposez d'une chaîne d'outils et que vous lui ajoutez {{site.data.keyword.gitrepos}}, procédez comme suit :    

1. Dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur **Ajouter un outil**.
1. A la section Intégrations d'outils, cliquez sur **Git Repos and Issue Tracking**.
1. Sélectionnez un type de référentiel :     

  a. Pour créer un référentiel vide, cliquez sur **Nouveau** pour le type de référentiel et saisissez un nom de référentiel.    
  b. Pour dévier un référentiel Git afin de pouvoir participer aux modifications via des demandes de fusion, cliquez sur **Dévier** pour le type de référentiel. Saisissez
l'URL du référentiel source.    
  c. Pour créer une copie d'un référentiel Git, cliquez sur **Cloner** pour le type de référentiel. Saisissez un nouveau nom de référentiel et l'URL du référentiel source.     
  d. Si vous disposez d'un référentiel Git et désirez l'utiliser, cliquez sur **Existant** pour le type de référentiel. Entrez l'adresse URL.    

1. Si vous souhaitez utiliser l'option Problèmes pour le suivi des problèmes, cochez la case **Activer les problèmes**.
1. Si vous voulez suivre le déploiement des modifications du code en créant des étiquettes et des commentaires sur les validations, ainsi que des libellés et des commentaires sur les problèmes référencés par les validations, cochez la case **Suivi du déploiement des modifications du code**. Pour plus d'informations, voir [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Cliquez sur **Créer une intégration**.
1. Cliquez sur la carte du référentiel Git à utiliser. La page de présentation de votre projet s'ouvre.    

Si vous ne disposez pas d'un droit Maître ou Propriétaire sur le référentiel que vous liez, votre intégration sera limitée car vous ne pouvez pas utiliser un webhook. Les webhooks sont nécessaires pour exécuter un pipeline automatiquement lorsqu'une validation est envoyée par commande push au référentiel. Sans
webhook, vous devez démarrer manuellement vos pipelines.
{: tip}

### Plus d'informations sur Git Repos and Issue Tracking

Pour en savoir plus sur {{site.data.keyword.gitrepos}}, lisez l'article [{{site.data.keyword.gitrepos}}: Social coding hosted by IBM](https://www.ibm.com/cloud/garage/content/code/tool_git_repos_and_issue_tracking/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel :

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}


## Configuration de GitHub
{: #github}

GitHub est un service d'hébergement Web pour les référentiels Git. Vous pouvez avoir des copies en local et à distance de vos référentiels, ce qui simplifie la collaboration.

{{site.data.keyword.ghe_short}} est un service d'hébergement Web sur site pour les référentiels Git.

GitHub Issues est un outil de suivi qui conserve votre travail et vos plans à un seul et même emplacement. Il est intégré à votre référentiel de développement pour vous permettre de vous concentrer sur les tâches importantes.

Vous pouvez configurer GitHub en tant qu'intégration d'outils dans votre chaîne d'outils afin de pouvoir gérer le code source dans un référentiel nouveau ou existant sur GitHub.com ou dans l'instance {{site.data.keyword.ghe_short}} de votre société. Lancez-vous dans le codage social via les wikis, le suivi des problèmes et les demandes d'extraction.

Si vous configurez cette intégration d'outils lors de la création de la chaîne d'outils, procédez comme suit :

1. Si vous stockez votre code source dans un référentiel GitHub, dans la section Intégrations configurables, cliquez sur **GitHub**. Si vous configurez cette intégration d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous n'avez pas autorisé {{site.data.keyword.Bluemix_notm}} à accéder à GitHub, cliquez sur **Autorisation** pour accéder au site Web GitHub. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub. Si vous disposez d'une session GitHub active mais n'avez pas saisi votre mot de passe récemment, vous êtes invité à entrer votre mot de passe GitHub pour confirmation.
1. Si vous utilisez un référentiel sur votre propre serveur {{site.data.keyword.ghe_short}}, dans la section Intégrations configurables, cliquez sur **Ajouter un serveur personnalisé**.

 Le réseau doit être capable d'accéder au serveur Git cible à partir d'un environnement {{site.data.keyword.Bluemix_notm}} Dedicated. Si votre serveur GitHub n'est pas disponible sur le réseau Internet public ou si le nom d'hôte n'est pas résolu sur le DNS public, [ouvrez un ticket de support](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_support#support-ticket). Vous pouvez utiliser le ticket de support pour soumettre une demande pour ouvrir les itinéraires réseau ou mettre à jour les paramètres DNS.
 {: important}

 Entrez un titre pour votre serveur GitHub personnalisé et spécifiez l'URL racine de votre serveur. Entrez votre jeton d'accès personnel, puis cliquez sur **Enregistrer l'intégration personnalisée**.

  Si vous ne possédez pas de jeton d'accès personnel, vous pouvez en créer un :

     a. Sur n'importe quelle page GitHub, cliquez sur l'icône de votre profil, puis sur **Paramètres**.

     b. Dans la barre d'options latérale, cliquez sur **Personal access tokens**.

     c. Cliquez sur **Créer un jeton**.

     d. Ajoutez une description relative au jeton.

     e. Cochez les cases **repo** et **user** afin de définir l'accès pour le jeton personnel.

     f. Cliquez sur **Créer un jeton**.

     g. Copiez le jeton dans un endroit sûr ou dans l'application de gestion de mot de passe. Pour des raisons de sécurité, lorsque vous quittez la page, le jeton disparaît.

1. Passez en revue les emplacements de référentiel cible par défaut pour les référentiels GitHub. Ces référentiels sont clonés à partir des référentiels exemple. Si nécessaire, modifiez les noms des référentiels cible.
 ![Emplacements de référentiel cible par défaut](images/toolchain_github_config.png)

Si vous disposez d'une chaîne d'outils et que vous lui ajoutez cette intégration d'outils, procédez comme suit :

1. Dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur **Ajouter un outil**.
1. Dans la section Intégrations d'outils, cliquez sur **GitHub**.
1. Cliquez sur le serveur GitHub que vous souhaitez utiliser.
1. Si vous disposez d'un référentiel GitHub ou {{site.data.keyword.ghe_short}} et désirez l'utiliser, cliquez sur **Existant** pour le type de référentiel et saisissez l'URL.
1. Si vous souhaitez utiliser un nouveau référentiel GitHub ou {{site.data.keyword.ghe_short}}, indiquez un nom pour le référentiel, entrez l'URL du référentiel que vous clonez ou déviez, puis sélectionnez le type de référentiel :

 a. Pour créer un référentiel vide, cliquez sur **Nouveau**.

 b. Pour créer une copie d'un référentiel GitHub ou {{site.data.keyword.ghe_short}}, cliquez sur **Cloner**.

 c. Pour dévier un référentiel GitHub ou {{site.data.keyword.ghe_short}} afin de pouvoir participer aux modifications via des demandes d'extraction, cliquez sur **Dévier**.

1. Si vous êtes un utilisateur GitHub.com avec un compte mis à niveau ou si vous avez sélectionné un serveur {{site.data.keyword.ghe_short}} et que vous souhaitez rendre un nouveau référentiel privé sur le serveur, cochez la case **Rendre ce référentiel privé**.
1. Si vous souhaitez utiliser GitHub Issues pour le suivi des problèmes, sélectionnez la case **Activer GitHub Issues**.
1. Si vous voulez suivre le déploiement des modifications du code en créant des étiquettes et des commentaires sur les validations, ainsi que des libellés et des commentaires sur les problèmes référencés par les validations, cochez la case **Suivi du déploiement des modifications du code**. Pour plus d'informations, voir [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Cliquez sur **Créer une intégration**.
1. Cliquez sur la carte du référentiel GitHub ou {{site.data.keyword.ghe_short}} à utiliser. Selon le référentiel que vous avez sélectionné, le site Web GitHub ou le référentiel {{site.data.keyword.ghe_short}} de votre société s'ouvre afin de vous permettre de visualiser le contenu du référentiel.

  Vous pouvez utiliser les outils de gestion des codes source intégrés dans Eclipse Orion {{site.data.keyword.webide}} pour éditer le référentiel GitHub et déployer une application depuis votre espace de travail.
  {: tip}

1. Si vous avez activé GitHub Issues, cliquez sur **GitHub Issues** pour l'ouvrir. Vous pouvez utiliser cette instance de GitHub Issues pour l'ensemble de votre chaîne d'outils, même si cette dernière contient plusieurs référentiels GitHub ou {{site.data.keyword.ghe_short}}.

Si vous ne disposez pas d'un droit d'administrateur sur le référentiel que vous liez, votre intégration sera limitée car vous ne pouvez pas utiliser un webhook. Les webhooks sont nécessaires pour exécuter un pipeline automatiquement lorsqu'une validation est envoyée par commande push au référentiel. Sans
webhook, vous devez démarrer manuellement vos pipelines.
{: tip}

### Plus d'informations sur GitHub

Pour en savoir plus sur GitHub, lisez l'[article sur GitHub](https://www.ibm.com/cloud/garage/content/code/tool_github/){:external} et l'[article sur GitHub Issues](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){:external} sur IBM Cloud Garage Method ou consultez ces tutoriels :

 * [Use the "Develop and test a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:external}
 * [Ensure quality deployments by using the "Deployment Risk Analytics with GitHub and Jenkins" toolchain](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:external}

 * [Create a custom toolchain](https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain){:external}


## Configuration de GitHub Enterprise et Issues sur {{site.data.keyword.Bluemix_notm}} Dedicated
{: #configghe}

 Ces instructions s'appliquent à {{site.data.keyword.Bluemix_notm}} Dedicated pour {{site.data.keyword.ghe_short}}. Si vous utilisez votre propre version gérée de {{site.data.keyword.ghe_short}}, certaines étapes peuvent varier en fonction de vos procédures internes.
 {: important}

{{site.data.keyword.ghe_long}} est un service d'hébergement Web sur site pour les référentiels Git. {{site.data.keyword.ghe_short}} Dedicated est destiné aux clients {{site.data.keyword.Bluemix_notm}} Dedicated uniquement. GitHub Issues est un outil de suivi qui conserve votre travail et vos plans à un seul et même emplacement. Il est intégré à votre référentiel de développement pour vous permettre de vous concentrer sur les tâches importantes. Pour en savoir plus sur Dedicated {{site.data.keyword.ghe_short}} et GitHub Issues, voir [Initiation à {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-getting-started) et l'[article sur GitHub Issues](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){:external} sur IBM Cloud Garage Method.

Vous pouvez configurer {{site.data.keyword.ghe_short}} en tant qu'intégration d'outils dans votre chaîne d'outils afin de pouvoir gérer le code source depuis l'instance de l'environnement [{{site.data.keyword.Bluemix_notm}} Dedicated](/docs/dedicated?topic=dedicated-dedicated#dedicated) de votre société.

1. Si vous configurez cette intégration d'outils lors de la création de la chaîne d'outils, procédez comme suit :

 a. Avant de vous connecter à {{site.data.keyword.ghe_short}} Dedicated pour la première fois, demandez à l'administrateur régional de votre société d'ajouter votre ID utilisateur à votre instance {{site.data.keyword.Bluemix_notm}} Dedicated à partir du registre d'utilisateurs de la société, via LDAP. Pour plus d'informations sur la configuration de votre compte {{site.data.keyword.ghe_short}}, voir [Initiation à {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-getting-started).

 b. Dans la section Intégrations configurables, cliquez sur **{{site.data.keyword.ghe_short}}**.    

 c. Vérifiez le nom par défaut pour le nouveau référentiel {{site.data.keyword.ghe_short}}. Si nécessaire, changez le nom du nouveau référentiel. L'image suivante montre un exemple de référentiel cloné à partir d'un référentiel exemple. Vous pouvez utiliser un référentiel existant ou un nouveau référentiel. Pour utiliser un nouveau référentiel, vous pouvez créer un référentiel vide, cloner un référentiel ou dévier un référentiel.
 ![Emplacements de référentiel par défaut](images/toolchain_ghe_config.png)

1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.ghe_short}}**.

1. Si vous disposez d'un référentiel {{site.data.keyword.ghe_short}} que vous souhaitez utiliser, entrez l'URL du référentiel. Pour le type de référentiel, cliquez sur **Existant**.
1. Si vous souhaitez utiliser un nouveau référentiel {{site.data.keyword.ghe_short}}, indiquez un nom pour le référentiel, entrez l'URL du référentiel que vous clonez ou déviez, puis sélectionnez le type de référentiel :

 a. Pour créer un référentiel vide, cliquez sur **Nouveau**.

 b. Pour créer une copie d'un référentiel, cliquez sur **Cloner**.

 c. Pour dévier un référentiel afin de pouvoir participer aux modifications via des demandes d'extraction, cliquez sur **Dévier**.

1. Pour utiliser GitHub Issues pour le suivi des problèmes, sélectionnez la case **Activer GitHub Issues**.
1. Cliquez sur **Créer une intégration**.
1. Cliquez sur la carte du référentiel {{site.data.keyword.ghe_short}} à utiliser. Le référentiel {{site.data.keyword.ghe_short}} de votre société s'ouvre.

  Vous pouvez utiliser les outils de gestion des codes source intégrés dans Eclipse Orion {{site.data.keyword.webide}} pour éditer le référentiel {{site.data.keyword.ghe_short}} et déployer une application depuis votre espace de travail.
  {: tip}

1. Si vous avez activé GitHub Issues, cliquez sur **GitHub Issues**. Vous pouvez utiliser cette instance de GitHub Issues pour l'ensemble de votre chaîne d'outils, même si cette dernière contient plusieurs référentiels GitHub.    

Si vous ne disposez pas d'un droit d'administrateur sur le référentiel que vous liez, votre intégration sera limitée car vous ne pouvez pas utiliser un webhook. Les webhooks sont nécessaires pour exécuter un pipeline automatiquement lorsqu'une validation est envoyée par commande push au référentiel. Sans
webhook, vous devez démarrer manuellement vos pipelines.
{: tip}


## Configuration de GitLab
{: #gitlab}

GitLab est un service d'hébergement Web pour les référentiels Git. Vous pouvez avoir des copies en local et à distance de vos référentiels, ce qui simplifie la collaboration.

Vous pouvez configurer GitLab en tant qu'intégration d'outils dans votre chaîne d'outils afin de pouvoir gérer le code source dans un référentiel nouveau ou existant sur GitLab.com ou dans l'instance GitLab de votre société. Lancez-vous dans le codage social via les wikis, le suivi des problèmes et les demandes de fusion.

Si vous configurez cette intégration d'outils lors de la création de la chaîne d'outils, procédez comme suit :

1. Si vous stockez votre code source dans un référentiel GitLab, dans la section Intégrations configurables, cliquez sur **GitLab**. Si vous configurez cette intégration d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous n'avez pas autorisé {{site.data.keyword.Bluemix_notm}} à accéder à GitLab, cliquez sur **Autorisation** pour accéder au site Web GitLab. Si vous n'avez pas de session GitLab active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitLab. Si vous disposez d'une session GitLab active mais n'avez pas saisi votre mot de passe récemment, vous êtes invité à entrer votre mot de passe GitLab pour confirmation.
1. Si vous utilisez un référentiel sur votre propre serveur GitLab, dans la section Intégrations configurables, cliquez sur **Ajouter un serveur personnalisé**.

 Le réseau doit être capable d'accéder au serveur GitLab cible à partir d'un environnement {{site.data.keyword.Bluemix_notm}} Dedicated.
 {: tip}

 Entrez un titre pour votre serveur GitLab personnalisé et spécifiez l'URL racine de votre serveur. Entrez votre jeton d'accès personnel, puis cliquez sur **Enregistrer l'intégration personnalisée**.

  Si vous ne possédez pas de jeton d'accès personnel, vous pouvez en créer un :

     a. Sur n'importe quelle page GitLab, cliquez sur l'icône de votre profil, puis sur **Paramètres**.

     b. Sur la page Jetons d'accès, saisissez le nom de l'application pour laquelle vous souhaitez créer un jeton d'accès personnel.

     c. Facultatif. Choisissez une date d'expiration pour le jeton d'accès.

     d. Cochez la case **api** afin de définir l'accès pour le jeton personnel.

     e. Cliquez sur **Créer un jeton d'accès personnel**.

     f. Copiez le jeton dans un endroit sûr ou dans l'application de gestion de mot de passe. Pour des raisons de sécurité, lorsque vous quittez la page, le jeton disparaît.

1. b. Passez en revue les emplacements de référentiel cible par défaut pour les référentiels GitLab. Ces référentiels sont clonés à partir des référentiels exemple. Si nécessaire, modifiez les noms des référentiels cible.

Si vous disposez d'une chaîne d'outils et que vous lui ajoutez cette intégration d'outils, procédez comme suit :

1. Dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur **Ajouter un outil**.
1. Dans la section Intégrations d'outils, cliquez sur **GitLab**.
1. Cliquez sur le serveur GitLab que vous souhaitez utiliser.
1. Si vous disposez d'un référentiel GitLab et désirez l'utiliser, cliquez sur **Existant** pour le type de référentiel et saisissez l'URL.
1. Si vous souhaitez utiliser un nouveau référentiel GitLab, indiquez un nom pour le référentiel, entrez l'URL du référentiel que vous clonez ou déviez, puis sélectionnez le type de référentiel :

 a. Pour créer un référentiel vide, cliquez sur **Nouveau**.

 b. Pour créer une copie d'un référentiel GitLab, cliquez sur **Cloner**.

 c. Pour dévier un référentiel GitLab afin de pouvoir participer aux modifications via des demandes d'extraction, cliquez sur **Dévier**.

1. Si vous souhaitez créer un référentiel public sur le serveur, désélectionnez la case **Rendre ce référentiel privé**.
1. Si vous souhaitez utiliser GitLab Issues pour le suivi des problèmes, sélectionnez la case **Activer GitLab Issues**.
1. Si vous voulez suivre le déploiement des modifications du code en créant des étiquettes et des commentaires sur les validations, ainsi que des libellés et des commentaires sur les problèmes référencés par les validations, cochez la case **Suivi du déploiement des modifications du code**. Pour plus d'informations, voir [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Cliquez sur **Créer une intégration**.
1. Cliquez sur la carte du référentiel GitLab à utiliser. Selon le référentiel que vous avez sélectionné, le site Web GitLab ou le référentiel GitLab de votre société s'ouvre afin de vous permettre de visualiser le contenu du référentiel.

  Vous pouvez utiliser les outils de gestion des codes source intégrés dans Eclipse Orion {{site.data.keyword.webide}} pour éditer le référentiel GitLab et déployer une application depuis votre espace de travail.
  {: tip}

1. Si vous avez activé GitLab Issues, cliquez sur **GitLab Issues** pour l'ouvrir. Vous pouvez utiliser cette instance de GitLab Issues pour l'ensemble de votre chaîne d'outils, même si cette dernière contient plusieurs référentiels GitLab.

Si vous ne disposez pas d'un droit maître ou propriétaire sur le référentiel avec lequel vous établissez une liaison, votre intégration sera limitée car vous ne pouvez pas utiliser un webhook. Les webhooks sont nécessaires pour exécuter un pipeline automatiquement lorsqu'une validation est envoyée par commande push au référentiel. Sans
webhook, vous devez démarrer manuellement vos pipelines.
{: tip}

### Plus d'informations sur GitLab

Pour en savoir plus sur GitLab, voir l'[article sur GitLab](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){:external} sur IBM Cloud Garage Method.


## Configuration de Jenkins
{: #jenkins}

Jenkins est un outil open source basé sur un serveur, qui génère et teste des logiciels en continu, en prenant en charge les pratiques d'intégration et de distribution continues.

Avant de créer une intégration d'outils Jenkins, vous devez disposer d'un serveur Jenkins.
{: important}

L'intégration d'outil Jenkins vous permet d'envoyer des notifications de travail Jenkins à d'autres outils de votre chaîne d'outils, comme Slack et PagerDuty. Pour tracer le code dans les déploiements, vous pouvez ajouter des messages de déploiement dans vos validations Git et les problèmes Git ou JIRA associés. Vous pouvez également visualiser vos déploiements dans la page Toolchain Connections. Vous pouvez fournir les résultats de test à {{site.data.keyword.DRA_short}}, ajouter des seuils de qualité automatisés et procéder au suivi des risques de déploiement.

Configurez Jenkins afin d'automatiser la génération, le test et le déploiement en continu de vos applications.

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **Jenkins**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Jenkins**.

1. Entrez le nom que vous souhaitez afficher pour cette intégration d'outils sur la carte Jenkins de votre chaîne d'outils.
1. Saisissez l'URL du serveur Jenkins qui doit s'ouvrir lorsque vous cliquez sur la carte Jenkins à partir de votre chaîne d'outils.
1. Copiez le webhook de la chaîne d'outils généré.
1. Dans votre serveur Jenkins, procédez comme suit :

 a. [Install the IBM Cloud DevOps plug-in](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Installingtheplugin){:external}.

 b. [Configure Jenkins to notify toolchains](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Notifyingtoolchains){:external}.

 c. Retournez à la page Configurer l'intégration pour l'intégration d'outils Jenkins.

1. Cliquez sur **Créer une intégration**.
1. A partir de votre chaîne d'outils, cliquez sur **Jenkins** pour afficher le serveur Jenkins.  

### Plus d'informations sur Jenkins

Pour en savoir plus sur Jenkins, voir l'[article sur Jenkins](https://www.ibm.com/cloud/garage/content/deliver/tool_jenkins/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel :

  * [Ensure quality deployments by using the "Deployment Risk Analytics with GitHub and Jenkins" toolchain](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:external}

## Configuration de JIRA
{: #jira}

JIRA est un outil qui assure le suivi des bogues et des problèmes liés à votre logiciel. L'intégration d'outils JIRA met à jour les problèmes de votre projet lorsque Jenkins ou {{site.data.keyword.deliverypipeline}} exécute un déploiement. Pour que l'intégration d'outils JIRA puisse assurer le suivi des problèmes, vous devez utiliser JIRA Smart Commits dans vos messages de validation. Pour en savoir plus sur JIRA Smart Commits, voir [Using Smart Commits](https://confluence.atlassian.com/fisheye/using-smart-commits-298976812.html){:external}.

Configurez JIRA pour planifier, suivre et distribuer un code de qualité :

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **JIRA**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **JIRA**.

1. Si vous disposez d'un projet JIRA et que vous voulez vous y connecter, cliquez sur **Existant** pour le type JIRA :

 a. Saisissez la clé de projet JIRA pour le projet JIRA. Vous la trouverez dans l'URL du projet JIRA.

 b. Entrez l'URL de l'API de base de votre instance JIRA. Vous la trouverez dans l'en-tête de votre instance JIRA. Cliquez sur l'icône **Administration**, puis sur **Système**.

 c. Si vous vous connectez à une instance JIRA privée ou si vous souhaitez recevoir des informations de traçabilité de la part d'une instance JIRA publique, entrez votre nom d'utilisateur et votre mot de passe JIRA.

 d. Pour suivre le déploiement des modifications du code en créant des libellés et des commentaires pour les problèmes référencés, cochez la case **Suivi du déploiement
des modifications du code**. Prenez soin d'utiliser JIRA Smart Commit pour référencer les problèmes JIRA dans vos validations GitHub. Si vous ne sélectionnez pas cette option, l'intégration d'outils JIRA ignore les validations.

1. Si vous souhaitez créer un projet JIRA, cliquez sur **Nouveau** pour le type JIRA :

 a. Saisissez une clé de projet JIRA à utiliser pour le nouveau projet. Cette clé est utilisée comme identificateur unique dans l'URL du projet.

 b. Saisissez un nom pour le projet JIRA.

 c. Entrez l'URL de l'API de base de votre instance JIRA. Vous la trouverez dans l'en-tête de votre instance JIRA. Cliquez sur l'icône **Administration**, puis sur **Système**.

 d. Saisissez le nom d'utilisateur du chef de projet JIRA que vous voulez utiliser pour ce projet. La personne que vous spécifiez comme chef de projet JIRA doit disposer de droits de chef de projet dans JIRA.

 e. Saisissez le nom d'utilisateur de l'administrateur pour cette instance de JIRA.

 f. Saisissez le mot de passe de l'administrateur pour cette instance de JIRA.

 g. Pour suivre le déploiement des modifications du code en créant des libellés et des commentaires pour les problèmes référencés, cochez la case **Suivi du déploiement
des modifications du code**. Prenez soin d'utiliser JIRA Smart Commit pour référencer les problèmes JIRA dans vos validations GitHub. Si vous ne sélectionnez pas cette option, l'intégration d'outils JIRA ignore les validations.

1. Cliquez sur **Créer une intégration**.
1. A partir de cette chaîne d'outils, cliquez sur **JIRA** pour afficher le tableau de bord du projet JIRA auquel vous êtes connecté.

### Plus d'informations sur JIRA

Pour en savoir plus sur JIRA, voir l'[article sur JIRA](https://www.ibm.com/cloud/garage/content/code/tool_jira/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel :

  * [Gain insights by using the "Developer Insights and Team Dynamics with GitHub and JIRA" toolchain](https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain){:external}


## Configuration de Nexus
{: #nexus}

Configurez le gestionnaire de référentiels Nexus pour stocker les artefacts de génération dans votre référentiel Nexus :

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **Nexus**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Nexus**.

1. Saisissez un nom pour cette instance de l'intégration d'outils Nexus.
1. Saisissez l'URL du référentiel Nexus qui doit s'ouvrir lorsque vous cliquez sur la carte Nexus à partir de votre chaîne d'outils.
1. Sélectionnez le type de référentiel auquel vous souhaitez vous connecter.
1. Si vous avez sélectionné **Registre npm**, procédez comme suit :

 a. Saisissez l'adresse électronique associée à votre registre.

 b. Saisissez le jeton d'authentification associé à votre registre.

 c. Saisissez l'URL de votre référentiel d'édition Nexus, qui est votre registre privé sur le serveur Nexus.

 d. Saisissez l'URL du registre miroir ou public que vous utilisez pour combiner plusieurs registres npm publics et privés. Par exemple, cette URL peut être l'adresse du registre virtuel sur votre serveur Nexus, qui peut accéder à la fois à votre registre privé et à un cache du registre npm global.

1. Si vous avez sélectionné **Référentiel Maven**, procédez comme suit :

 a. Saisissez l'ID utilisateur associé à votre référentiel.

 b. Saisissez le mot de passe associé à votre référentiel.

 c. Saisissez l'URL de votre référentiel d'édition Nexus, qui est votre référentiel d'édition privé sur le serveur Nexus.

 d. Saisissez l'URL de votre référentiel d'image instantanée Nexus, qui est votre référentiel d'image instantanée privé sur le serveur Nexus.

 e. Saisissez l'URL du référentiel miroir ou public que vous utilisez pour combiner plusieurs référentiels Maven publics et privés. Par exemple, cette URL peut être l'adresse du référentiel virtuel sur votre serveur Nexus, qui peut accéder à la fois à vos référentiels privés et à un cache du référentiel Maven central.

1. Cliquez sur **Créer une intégration**.
1. A partir de votre chaîne d'outils, cliquez sur la carte du référentiel Nexus que vous souhaitez utiliser. Le site Web Nexus s'ouvre ; vous pouvez y afficher le contenu du référentiel.
1. Facultatif : Si vous utilisez une chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous voulez générez votre application à l'aide de Nexus avec npm, configurez votre pipeline pour ajouter un travail de génération npm. Pour des instructions de configuration du travail de génération, voir la section [Configuration d'un travail de génération npm Nexus sur votre pipeline](#config_nexus_npm).
1. Facultatif : Si vous utilisez une chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et que vous voulez générer votre application à l'aide de Nexus avec Maven, configurez votre pipeline pour ajouter un travail de génération Maven. Pour des instructions de configuration du travail de génération, voir la section [Configuration d'un travail de génération Maven Nexus sur votre pipeline](#config_nexus_maven).

### Configuration d'un travail de génération npm Nexus sur votre pipeline
{: #config_nexus_npm}

Avant de configurer un travail de génération npm sur votre pipeline, vous devez disposer d'un pipeline opérationnel qui peut utiliser votre référentiel SCM de génération en entrée et vous devez configurer Nexus pour votre chaîne d'outils. Pour les instructions de configuration de Nexus, voir la section [Nexus](#nexus).

Configurez {{site.data.keyword.deliverypipeline}} pour ajouter un travail de génération npm :

1. Créez une étape et définissez l'entrée sur le référentiel SCM approprié.
1. Dans l'étape, ajoutez un travail de génération.
1. Configurez le travail de génération :
  ![travail de génération npm](images/nexus_npm_job.png)

  a. Pour le type de générateur, sélectionnez **NPM Build**.

  b. Si vous avez configuré plusieurs instances de l'intégration d'outils Nexus, saisissez le nom de l'intégration d'outils Nexus pour laquelle vous souhaitez configurer le travail de génération npm.

  c. Pour le type d'intégration d'outils, sélectionnez **Nexus**.

  d. Pour la commande de génération, saisissez les commandes permettant de générer votre module npm ou de le publier dans votre registre. Cet exemple montre les commandes de génération ou de publication du module.
     ```
     npm install
     # ou
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  **Astuce :** vous pouvez trouver l'URL et les données d'identification de l'utilisateur dont vous vous êtes servi pour vous connecter à votre registre dans les paramètres de
configuration pour l'intégration des outils Nexus.

  e. Si votre travail de génération est publié dans le registre Nexus et si le format de votre version de module de noeud est `x.y.z-SNAPSHOT.w`, cochez la case **Incrémenter la version du module d'instantané**. Le travail de génération met automatiquement à jour la version du module avant qu'il ne soit publié dans le registre Nexus. Le travail de génération sélectionne la version la plus élevée du module à partir du registre npm et du fichier local `package.json`, et incrémente la version du module à l'aide de semver. Le travail de génération ne répercute pas les modifications dans le référentiel SCM.

1. Cliquez sur **SAUVEGARDER**. Lors de l'exécution de votre pipeline, ce travail de génération utilise les informations de configuration provenant de l'intégration d'outils Nexus pour la connexion à votre registre npm.

### Configuration d'un travail de génération Maven Nexus sur votre pipeline
{: #config_nexus_maven}

Avant de configurer un travail de génération Maven sur votre pipeline, vous devez disposer d'un pipeline opérationnel qui peut utiliser votre référentiel SCM de génération en entrée et vous devez configurer Nexus pour votre chaîne d'outils. Pour les instructions de configuration de Nexus, voir la section [Nexus](#nexus).

Configurez {{site.data.keyword.deliverypipeline}} pour ajouter un travail de génération Maven :

1. Créez une étape et définissez l'entrée sur le référentiel SCM approprié.
1. Dans l'étape, ajoutez un travail de génération.
1. Configurez le travail de génération :
  ![travail de génération Maven](images/nexus_maven_job.png)

  a. Pour le type de générateur, sélectionnez **Maven Build**.

  b. Si vous avez configuré plusieurs instances de l'intégration d'outils Nexus, saisissez le nom de l'intégration d'outils Nexus pour laquelle vous souhaitez configurer le travail de génération Maven.

  c. Pour le type d'intégration d'outils, sélectionnez **Nexus**.

  d. Pour la commande de génération, saisissez les commandes permettant de générer votre module Maven ou de le publier dans votre registre d'image instantanée. Cet exemple montre les commandes de génération ou de publication du module.
     ```
     mvn -B clean package
     # ou
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  Vous pouvez trouver l'URL et les données d'identification de l'utilisateur dont vous vous êtes servi pour vous connecter à votre registre dans les paramètres de configuration pour l'intégration des outils Nexus.
  {: tip}

1. Cliquez sur **SAUVEGARDER**. Lors de l'exécution de votre pipeline, ce travail de génération utilise les informations de configuration provenant de l'intégration d'outils Nexus pour la connexion à votre référentiel Maven.

### Plus d'informations sur Nexus

Pour en savoir plus sur Nexus, voir l'[article sur Nexus](https://www.ibm.com/cloud/garage/content/deliver/tool_nexus/){:external} sur IBM Cloud Garage Method.


## Configuration d'un outil personnalisé (autre outil)
{: #othertool}

Si votre équipe utilise un outil qui n'est pas inclus dans la liste des intégrations de chaînes d'outils, vous pouvez intégrer un
outil personnalisé.

Configurez un outil personnalisé qui puisse fonctionner avec
les autres outils de votre chaîne d'outils et qui soit disponible
pour votre équipe :

1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Other Tool**.

1. Saisissez le nom de l'outil.
1. Sélectionnez la phase de cycle de vie qui est la plus étroitement associée à l'outil. Cette sélection détermine la catégorie sous laquelle votre outil est répertorié sur la page Vue d'ensemble.
1. Ajoutez une URL d'icône. L'icône s'affiche dans la carte de votre intégration d'outils.
1. Ajoutez une URL de documentation.
1. Indiquez un nom d'instance d'outil. Par exemple, Mon outil d'équipe.
1. Ajoutez une URL d'instance de l'outil. Cette URL s'ouvre chaque fois que vous cliquez sur la carte d'intégration d'outils.
1. Ajoutez une description de votre outil.
1. (Avancé) Ajoutez des propriétés supplémentaires si besoin. Par exemple, indiquez les informations ou les attributs qui sont
requis pour l'intégration de votre outil aux autres outils de la chaîne d'outils.  
1. Cliquez sur **Créer une intégration**.

### Plus d'informations sur l'outil personnalisé

Pour en savoir plus sur l'outil personnalisé, voir [Introducing custom tool integration for {{site.data.keyword.Bluemix_notm}} toolchains](https://www.ibm.com/cloud/blog/introducing-custom-tool-integration-for-bluemix-toolchains/){:external} ou consultez ce tutoriel :

  * [Add a custom tool integration to a toolchain](https://www.ibm.com/cloud/garage/tutorials/add-a-custom-tool-integration-to-a-toolchain){:external}


## Configuration de PagerDuty
{: #pagerduty}

PagerDuty intègre dans une vue unique les données provenant de plusieurs systèmes de surveillance. Quand un problème survient, PagerDuty s'assure que le membre d'équipe le plus à même de le résoudre reçoit une notification. Si le membre d'équipe ne répond pas au problème, des remontées d'information peuvent être configurées pour l'acheminer aux représentants secondaires ou aux directeurs des opérations.

Configurez PagerDuty pour l'envoi de notifications en cas d'échec d'étape de pipeline afin de pouvoir résoudre les problèmes plus rapidement et de réduire le temps d'indisponibilité.

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **PagerDuty**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **PagerDuty**.

1. Si vous souhaitez intégrer PagerDuty ay niveau de compte en utilisant une clé d'API, cliquez sur **Compte**:

 a. Entrez la clé d'accès d'API pour votre compte PagerDuty. Si vous ne possédez pas de compte PagerDuty, [inscrivez-vous pour en obtenir un](https://www.pagerduty.com/sign-up/){:external}. Pour savoir comment obtenir la clé, voir [Generating an API Key](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){:external}.

 b. Entrez le nom de votre service PagerDuty.

 c. Entrez l'adresse électronique du contact PagerDuty principal.

 d. Entrez le numéro de téléphone du contact PagerDuty principal.

1. Si vous souhaitez intégrer PagerDuty au niveau du service à l'aide d'une clé d'intégration, cliquez sur **Service** :

 a. Saisissez l'URL du service PagerDuty pour lequel vous souhaitez publier des alertes.

 b. Saisissez votre clé d'intégration PagerDuty. Vous pouvez rechercher cette clé ou en créer une dans la section Intégrations de la page de service PagerDuty.

1. Cliquez sur **Créer une intégration**.
1. Cliquez sur **PagerDuty** pour accéder au site pagerduty.com. Vous pouvez afficher les événements associés au service PagerDuty spécifié lors de la configuration de cette intégration d'outils pour votre chaîne d'outils.

### Plus d'informations sur PagerDuty

Pour en savoir plus sur PagerDuty, voir l'[article sur PagerDuty](https://www.ibm.com/cloud/garage/content/manage/tool_pagerduty/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel et le cours "Garage Method advocate" :

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}

  * [Become a Garage Method advocate](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:external}


## Configuration de Rational Team Concert
{: #rationalteamconcert}

IBM Rational Team Concert&trade; est un outil de collaboration des équipes qui intègre des tâches de développement, notamment la planification d'itérations, la gestion des changements, le suivi des problèmes, le contrôle des sources, l'automatisation de la construction et la génération de rapports.

Configurez Rational Team Concert pour pouvoir bénéficier d'une approche DevOps et de la distribution continue dans votre environnement de développement :

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **Rational Team Concert**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Rational Team Concert**.

1. Saisissez l'URL du serveur Rational Team Concert qui doit s'ouvrir lorsque vous cliquez sur la carte Rational Team Concert à partir de votre chaîne d'outils.
1. Entrez l'ID utilisateur que vous utilisez pour accéder au serveur Rational Team Concert.
1. Indiquez le mot de passe que vous utilisez pour accéder au serveur Rational Team Concert.
1. Si vous disposez d'une zone de projet Rational Team Concert que vous souhaitez ajouter à votre chaîne d'outils, procédez comme suit :

 a. Dans la liste **Type de zone de projet**, sélectionnez **Zone de projet existante**.

 b. Indiquez le nom de la zone de projet à ajouter à la chaîne d'outils.

1. Si vous souhaitez créer une zone de projet Rational Team Concert à ajouter à votre chaîne d'outils, procédez comme suit :

 a. Dans la liste **Type de zone de projet**, sélectionnez **Nouvelle zone de projet**.

 b. Indiquez le nom de la nouvelle zone de projet à ajouter à la chaîne d'outils.

 c. Entrez le nom du modèle de processus Rational Team Concert à utiliser pour créer le projet.

1. Pour suivre le déploiement des modifications du code du projet en créant des étiquettes et des commentaires sur les éléments de travail, cochez la case **Suivi du déploiement des modifications du code**.
1. Cliquez sur **Créer une intégration**.
1. A partir de la chaîne d'outils, cliquez sur **Rational Team Concert** pour ouvrir le tableau de bord Rational Team Concert que vous avez configuré.

### Plus d'informations sur Rational Team Concert

Pour en savoir plus sur Rational Team Concert, lisez l'[article sur IBM Rational Team Concert](https://www.ibm.com/cloud/garage/content/think/tool_rtc/){:external} sur IBM Cloud Garage Method.


## Configuration de Sauce Labs
{: #saucelabs}

Sauce Labs exécute des tests unitaires fonctionnels. Quand une suite de tests Sauce Labs est configurée comme travail de test dans {{site.data.keyword.deliverypipeline}}, cette suite de tests peut exécuter des tests en fonction de votre application Web ou mobile dans le cadre de votre processus de distribution continue. Ces tests peuvent fournir un contrôle de flux de valeur pour vos projets, agissant comme des barrières pour empêcher le déploiement de code incorrect.

 Cette intégration d'outils est uniquement disponible sur {{site.data.keyword.Bluemix_notm}} Public.
 {: tip}

Configurez Sauce Labs pour l'exécution de tests fonctionnels automatisés sur plusieurs systèmes d'exploitation et navigateurs afin de pouvoir émuler la façon dont un utilisateur peut utiliser un site Web ou une application :

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **Sauce Labs**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Sauce Labs**.

1. Entrez le nom d'utilisateur associé à votre compte Sauce Labs. Vous [trouverez votre nom d'utilisateur dans le message de bienvenue figurant sur la page de votre compte Sauce Labs](https://app.saucelabs.com/user-settings){:external}.
1. Entrez la clé d'accès de votre compte Sauce Labs. Vous [trouverez la clé sur la page de votre compte Sauce Labs](https://app.saucelabs.com/user-settings){:external}.
1. Cliquez sur **Créer une intégration**.
1. Cliquez sur **Sauce Labs** pour accéder à saucelabs.com et afficher l'activité de test pour la chaîne d'outils.

 Si vous avez ajouté une tâche test Sauce Labs à {{site.data.keyword.deliverypipeline}}, vous pouvez sélectionner l'instance de service. Pour connaître les instructions de configuration d'un travail de test dans votre pipeline, voir [Configuration d'un travail de test Sauce Labs sur votre pipeline](#config_saucelabs).
 {: tip}

### Plus d'informations sur Sauce Labs

Pour en savoir plus sur Sauce Labs, lisez l'[article sur Sauce Labs](https://www.ibm.com/cloud/garage/content/deliver/tool_sauce_labs/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel :

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}


## Configuration de Slack
{: #slack}

Les notifications publiées sur les canaux Slack publics sont visibles par tous les membre de l'équipe. Vous êtes responsable du contenu que vous publiez.
{: important}

Slack est un système de messagerie et de notification en temps réel, basé sur le cloud. Slack fournit un système de discussion permanente, alternative plus interactive au courrier électronique pour la collaboration des équipes. Vous pouvez communiquer avec votre équipe sur un canal dédié ou sur un ensemble de canaux directement liés à votre travail. Vous pouvez également partager des fichiers et des images via ces canaux, ou dans des messages directs entre deux personnes ou plus. Les communications dans les messages directs ou sur les canaux sont conservées pour que vous puissiez y faire des recherches.

Configurez Slack pour la réception de notifications concernant votre chaîne d'outils depuis les intégrations d'outils, par exemple les activités de test et de déploiement :

1. Si vous configurez cette intégration d'outils lorsque vous créez la chaîne d'outils, à la section Intégrations configurables, cliquez sur **Slack**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outils, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **Slack**.

1. Entrez l'URL de webhook Slack, qui est générée par Slack en tant que webhook entrant. Vous avez besoin d'une URL de webhook Slack pour un canal Slack afin de recevoir des notifications concernant votre chaîne d'outils depuis les intégrations d'outils. Pour savoir comment créer ou trouver votre webhook, voir [Incoming Webhooks](https://api.slack.com/incoming-webhooks){:external}.

 Si vous utilisez une clé d'API pour que votre canal Slack reçoive des notifications sur votre chaîne d'outils depuis les intégrations d'outils, vous devez mettre à jour votre configuration pour utiliser un webhook à la place.
 {: tip}

1. Entrez le nom du canal Slack sur lequel vous souhaitez recevoir les notifications. La chaîne doit exister et être active dans votre équipe Slack.
1. Saisissez le nom d'hôte d'URL pour votre équipe Slack, qui est le mot ou l'expression avant `.slack.com` dans l'URL de votre équipe. Par exemple, si l'URL de votre équipe est `https://team.slack.com`, le nom d'hôte est `team`.
1. Cliquez sur **Créer une intégration**.

 Si le canal Slack et l'équipe que vous avez spécifiés ne sont pas accessibles, l'erreur `Echec de la configuration` s'affiche sur la carte Slack. Survolez le message `Echec de la configuration` et cliquez sur **Reconfigurer**. Assurez-vous que vous utilisez des paramètres de configuration valides pour l'URL de webhook Slack, le canal Slack et le nom d'hôte d'URL de votre équipe Slack. Mettez à jour les paramètres si nécessaire et cliquez sur **Sauvegarder l'intégration**.
 {: tip}

1. Cliquez sur **Slack**. Vous pouvez afficher toutes les activités de votre chaîne d'outils dans le canal Slack configuré.

### Plus d'informations sur Slack

Pour en savoir plus sur Slack, lisez l'[article sur Slack](https://www.ibm.com/cloud/garage/content/culture/tool_slack/){:external} sur IBM Cloud Garage Method ou consultez ce tutoriel et le cours Garage Method advocate :

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}

  * [Become a Garage Method advocate](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:external}


## Configuration de SonarQube
{: #sonarqube}

SonarQube offre un aperçu de la qualité et de la santé générale de votre code source et met en évidence les problèmes détectés dans le nouveau code. Les analyseurs de code détectent les
bogues sensibles, comme par exemple les déréférences d'un pointeur NULL, les erreurs logiques et les fuites de ressources dans plus de 20 langages de code.

Configurez SonarQube pour analyser et mesurer en continu la qualité de votre code source :

1. Sur le tableau de bord DevOps, cliquez sur **Chaînes d'outils**. Cliquez sur la chaîne d'outils à laquelle vous souhaitez ajouter SonarQube. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.  

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **SonarQube**.

1. Saisissez un nom pour cette instance de l'intégration d'outils SonarQube.
1. Entrez l'URL de l'instance SonarQube que vous souhaitez ouvrir lorsque vous cliquez sur la carte SonarQube depuis votre chaîne d'outils.
1. Facultatif : entrez le nom d'utilisateur que vous utilisez pour vous connecter au serveur SonarQube.

 Vous devez uniquement spécifier un nom d'utilisateur si vous utilisez un mot de passe pour vous connecter au serveur SonarQube. Si vous utilisez un jeton d'authentification pour la connexion, laissez cette zone vide.
 {: tip}

1. Entrez le mot de passe ou le jeton d'authentification que vous utilisez pour vous connecter au serveur SonarQube.
1. Cliquez sur **Créer une intégration**.
1. Dans la chaîne d'outils, cliquez sur **SonarQube** pour afficher le tableau de bord pour l'instance SonarQube à laquelle vous vous êtes connecté.

### Plus d'informations sur SonarQube

Pour en savoir plus sur SonarQube, lisez l'[article sur SonarQube](https://www.ibm.com/cloud/garage/content/learn/tool_sonarqube/){:external} sur IBM Cloud Garage Method. 
