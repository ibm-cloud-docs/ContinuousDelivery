---

Copyright:
  years: 2015, 2019
lastupdated: "2019-2-5"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Disponibilité des chaînes d'outils, modèles et tutoriels  
{: #cd_about}  

Les chaînes d'outils sont disponibles sur {{site.data.keyword.Bluemix_notm}} Public et Dedicated. Vous pouvez utiliser un modèle comme point de départ pour créer une chaîne d'outils.
{:shortdesc}

## Disponibilité des chaînes d'outils sur {{site.data.keyword.Bluemix_notm}} Public et sur {{site.data.keyword.Bluemix_notm}} Dedicated
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} Public est une plateforme de cloud à norme ouverte qui vous permet de créer, d'exécuter et de gérer des applications accessibles via [http://cloud.ibm.com ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://cloud.ibm.com){:new_window}. {{site.data.keyword.Bluemix_notm}} Dedicated fournit les fonctionnalités d'{{site.data.keyword.Bluemix_notm}} dans un environnement SoftLayer dédié qui établit une connexion sécurisée à la fois à l'environnement {{site.data.keyword.Bluemix_notm}} Public et à votre réseau. L'environnement {{site.data.keyword.Bluemix_notm}} Dedicated de votre société peut ne pas contenir les mêmes intégrations d'outils que le site {{site.data.keyword.Bluemix_notm}} Public.

Pour la gestion du code source et le suivi des problèmes, {{site.data.keyword.Bluemix_notm}} Public utilise généralement {{site.data.keyword.gitrepos}} (hébergé par IBM et basé sur [GitLab Community Edition ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://about.gitlab.com/){:new_window}) ou GitHub (github.com). {{site.data.keyword.Bluemix_notm}} Dedicated peut également utiliser github.com, mais se sert généralement de {{site.data.keyword.ghe_short}}, qui est installé par votre société ou géré par IBM.

{{site.data.keyword.contdelivery_short}} est disponible sur {{site.data.keyword.Bluemix_notm}} Public dans des régions sélectionnées et sur {{site.data.keyword.Bluemix_notm}} Dedicated. Les chaînes d'outils varient selon que vous utilisez {{site.data.keyword.contdelivery_short}} sur {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated.

Bien que les chaînes d'outils ne soient pas disponibles dans toutes les régions actuellement, vous pouvez configurer votre chaîne d'outils pour déployer vos applications dans toutes les régions. Pour en savoir plus, essayez le tutoriel [Déploiement d'une application Web sécurisée dans plusieurs régions](/docs/tutorials?topic=solution-tutorials-multi-region-webapp){: new_window}.
{: tip}

|Chaînes d'outils |{{site.data.keyword.Bluemix_notm}} Public	|{{site.data.keyword.Bluemix_notm}} Dedicated |
|:----------|:------------------------------|:------------------|
|Intégrations d'outils 		|Pour obtenir une liste des intégrations d'outils prises en charge, voir [Configuration d'intégrations d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}. 		|Les intégrations d'outils disponibles dépendent de la configuration de {{site.data.keyword.contdelivery_short}} dans votre environnement.			|
|Création d'une chaîne d'outils à partir d'un modèle		|Connectez-vous à [{{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://cloud.ibm.com/devops){:new_window}		|Connectez-vous à votre environnement Dedicated sur {{site.data.keyword.Bluemix_notm}}.			|
|Création d'une chaîne d'outils à partir d'une application		|L'application est configurée pour la distribution continue depuis un nouveau référentiel GitHub rempli avec le code de démarrage d'application.		|L'application est configurée pour la distribution continue depuis un nouveau référentiel GitHub ou GitHub Enterprise rempli avec le code de démarrage d'application.		|  
|Régions de déploiement du pipeline de distribution		|Toutes les régions {{site.data.keyword.Bluemix_notm}} Public sont disponibles pour des travaux de déploiement Cloud Foundry. 		|La région {{site.data.keyword.Bluemix_notm}} Dedicated est disponible. D'autres régions dédiées ou locales au sein du même compte client peuvent également être disponibles en fonction de la configuration de {{site.data.keyword.contdelivery_short}} dans votre environnement spécifique.		|
|Travaux de déploiement du pipeline de distribution		|Tous les [types de travaux](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs) sont disponibles.		|Les types de travaux dépendant de services {{site.data.keyword.Bluemix_notm}} qui ne sont pas installés dans l'environnement dédié risquent de ne pas être disponibles.	Par exemple, les types de travaux de génération et de déploiement de conteneur peuvent ne pas être disponibles dans les environnements ne disposant pas de {{site.data.keyword.containerlong_notm}}.	|
{: caption="Tableau 1. Différences entre les chaînes d'outils sur {{site.data.keyword.Bluemix_notm}} Dedicated et {{site.data.keyword.Bluemix_notm}} Public" caption-side="top"}


## Modèles de chaîne d'outils
{: #templates}

Vous pouvez utiliser un modèle comme point de départ pour [créer une chaîne d'outils ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/devops/create){: new_window}. Les modèles de chaîne d'outils incluent des ensembles spécifiques d'intégrations d'outils prenant en charge des tâches de développement, de déploiement et d'opérations.

L'environnement {{site.data.keyword.Bluemix_notm}} Dedicated de votre société peut ne pas contenir les mêmes modèles de chaîne d'outils que le site {{site.data.keyword.Bluemix_notm}} Public. Les modèles de chaîne d'outils qui sont disponibles à la fois sur {{site.data.keyword.Bluemix_notm}} Public et {{site.data.keyword.Bluemix_notm}} Dedicated peuvent contenir un ensemble d'intégrations d'outils différent sur {{site.data.keyword.Bluemix_notm}} Dedicated.
{: note}

Certains modèles de chaîne d'outils incluent des intégrations d'outils qui font partie du service {{site.data.keyword.contdelivery_short}}. Si une instance de ce service n'existe pas déjà dans votre groupe de ressources ou organisation, lorsque vous cliquez sur **Créer** pour créer la chaîne d'outils, le service est automatiquement ajouté avec le plan Lite gratuit sélectionné. Pour obtenir plus d'informations et pour consulter les dispositions légales, consultez le [catalogue {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/catalog/services/continuous-delivery/){:new_window}.

La chaîne d'outils "Développer et tester des microservices sur Cloud Foundry" déploie une application avec des API Catalogue et Commandes qui sont sauvegardées par un magasin Cloudant. Dans le cadre du déploiement de l'application, une instance de service Cloudant gratuite est créée. Pour obtenir plus d'informations et pour connaître les dispositions légales, consultez le [catalogue {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){:new_window}.

Les modèles prédéfinis de chaînes d'outils DevOps sont des exemples recommandés qui résolvent des scénarios réels et chacun contient un exemple d'application.  Vous pouvez utiliser votre propre application en spécifiant votre référentiel git lorsque vous créez la chaîne d'outils à partir du modèle.

<table valign="top" padding="2px">
  <caption>Tableau 2. Modèles de chaînes d'outils</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">Modèle et régions disponibles</th>
    <th style="width:50%; text-align:left; vertical-align:top">Description et tutoriels disponibles</th>
    <th style="text-align:left; vertical-align:top">Outils inclus</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">Chaîne d'outils “Développer une application Cloud Foundry” <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

  </td><td>
  Cette chaîne d'outils vous permet de développer et de déployer une application Cloud Foundry. Par défaut, cette chaîne d'outils utilise une application exemple Node.js "Hello World", mais vous pouvez établir une liaison vers votre propre référentiel GitHub à la place. La chaîne d'outils est préconfigurée pour la distribution continue, le contrôle des sources, le suivi des problèmes et l'édition en ligne.	<br><br>

  Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">Introduction aux chaînes d'outils à l'aide de la chaîne d'outils “Développer une application Cloud Foundry” <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">Chaîne d'outils "Développer une application Kubernetes"<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

  </td><td>
  Cette chaîne d'outils vous permet de développer et de déployer une application de manière sûre dans un cluster Kubernetes géré par {{site.data.keyword.containerlong_notm}}. Par défaut, la chaîne d'outils utilise un exemple d'application Node.js "Hello World", mais vous pouvez établir une liaison vers votre propre référentiel GitHub à la place. Cette chaîne d'outils est préconfigurée pour la distribution continue avec Vulnerability Advisor, le contrôle des sources, le suivi des problèmes et l'édition en ligne. <br><br>
  Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">Utilisation de la chaîne d'outils "Développer une application Kubernetes" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.containerlong_notm}} (cluster Kubernetes)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">Chaîne d'outils "Développer une application Kubernetes avec Helm"<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

  </td><td>
  Cette chaîne d'outils vous permet de développer une application Docker et sa charte Helm dans le contrôle des sources, puis de la générer et de la déployer automatiquement dans un cluster Kubernetes. La chaîne d'outils réalise des tests de fumée avant une génération o un déploiement et assure la confidentialité en utilisant un registre de conteneurs privé et des espaces de noms pour le registre de conteneurs et le cluster Kubernetes. Cette chaîne d'outils utilise également Vulnerability Advisor pour s'assurer que seules les images sécurisées sont déployées. <br><br>
  Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">Utilisation de la chaîne d'outils "Développer une application Kubernetes avec Helm" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.containerlong_notm}} (cluster Kubernetes) avec charte Helm
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">Chaîne d'outils "Développer et tester une application Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans le sud des Etats-Unis, en Allemagne et au Royaume-Uni

  </td><td>
  Cette chaîne d'outils native pour le cloud vous permet d'utiliser DevOps Insights pour mettre en place le déploiement d'une application Cloud Foundry simple. Par défaut, la chaîne d'outils utilise un exemple d'application météo Node.js mais vous pouvez établir une liaison vers votre propre référentiel GitHub. La chaîne d'outils exécute des tests d'unité avec Mocha et vérifie le taux de couverture de code avec Istanbul.<br><br>
  Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">Utilisation de la chaîne d'outils "Développer et tester une application Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  Chaîne d'outils "Développer et tester des microservices sur Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans le sud des Etats-Unis, en Allemagne et au Royaume-Uni

  </td><td>
  Cette chaîne d'outils native pour le cloud permet de construire, à partir d'un exemple, un magasin en ligne comprenant trois microservices : une API Catalog, une API Orders et une interface graphique qui appelle les deux API. Cette chaîne d'outils est préconfigurée pour la distribution continue, le contrôle des sources, les tests fonctionnels, le suivi des problèmes, l'édition en ligne et la notification d'alerte. <br><br>
  Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">Utilisation de la chaîne d'outils "Développer et tester des microservices sur Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">
Chaîne d'outils "Tutoriel Garage Method avec Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

</td><td>
Cette chaîne d'outils illustre les pratiques DevOps qui sont appliquées dans la méthode Garage. Elle est préconfigurée pour la distribution continue, le contrôle des sources et l'automatisation des tests, ainsi que pour la surveillance et les opérations automatisées. Elle est fournie avec un modèle d'application écrit en Node.js Express 4, que vous pouvez continuer de développer. <br><br>Essayez le cours : <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Become a Garage Method advocate <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>.
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>GitHub and Issues
</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevopsinsights-toolchain" target="_blank">Chaîne d'outils "Analyse des risques de déploiement avec GitHub et Jenkins" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans le sud des Etats-Unis

</td><td>Cette chaîne d'outils vous permet d'analyser votre processus Jenkins en vue d'une intégration et d'une distribution continues. Vous pouvez configurer le serveur Jenkins pour qu'il envoie des données à {{site.data.keyword.DRA_short}} lorsque les travaux sont exécutés par Jenkins. Vous pouvez également implémenter des seuils de qualité afin de bloquer des déploiements en fonction de règles. Vous pouvez afficher les résultats sur le tableau de bord Deployment Risk de {{site.data.keyword.DRA_short}}. Si vous configurez un référentiel GitHub pour qu'il indique le référentiel source utilisé par Jenkins, la traçabilité des modifications est disponible.  
<br><br>
Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain" target="_blank">Garantir des déploiements de qualité à l'aide de la chaîne d'outils "Analyse des risques de déploiement avec GitHub et Jenkins" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>  <br><br>
</td><td><ul><li>
GitHub and Issues
</li><li>Jenkins
</li><li>{{site.data.keyword.DRA_full}}
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevteaminsights-toolchain" target="_blank">Chaîne d'outils "Developer Insights et Team Dynamics avec GitHub et JIRA" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans le sud des Etats-Unis

</td><td>
Cette chaîne d'outils vous permet d'explorer les risques liés au développement de votre projet et d'utiliser une analyse du codage social afin de comprendre les modèles d'interaction entre les développeurs. Vous pouvez analyser le code source GitHub ainsi que les problèmes de GitHub, les problèmes JIRA ou les deux. Utilisez Developer Insights pour identifier les fichiers plus susceptibles de générer des erreurs et examiner la conformité du projet avec les pratiques DevOps. L'analyse du codage social dans Team Dynamics identifie le niveau d'interaction entre les membres d'une équipe pour leur permettre de remédier à des pratiques non productives.<br><br>
Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain" target="_blank">Obtenez des informations en utilisant la chaîne d'outils "Developer Insights et Team Dynamics avec GitHub et JIRA" <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>
</td><td><ul><li>
GitHub and Issues
</li><li>{{site.data.keyword.DRA_full}}
</li><li>JIRA
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">Construire sa propre chaîne d'outils <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a> <br><br>

  Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

</td><td>
Cette chaîne d'outils ne comporte aucun outil préconfiguré. Si vous connaissez déjà les chaînes d'outils, vous pouvez configurer votre propre chaîne d'outils. <br><br>
Essayez le tutoriel : <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Créer une chaîne d'outils personnalisée  <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>
</td><td> &nbsp;&nbsp; N/D
</td></tr>

<tr><td>Chaîne d'outils Continuous Delivery <br><br>

 Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

</td><td>
Cette chaîne d'outils est utilisée lorsque vous activez la distribution continue pour une application. <br><br>
Essayez les tutoriels :

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Ajouter une chaîne d'outils à une application <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Créer une chaîne d'outils personnalisée <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>
GitHub and Issues
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>Modèle de chaîne d'outils personnalisée <br><br>

 Disponible dans les régions Sud des Etats-Unis, Est des Etats-Unis, Allemagne, Tokyo et Royaume-Uni

</td><td>
<br><br>
Vous pouvez créer un modèle de chaîne d'outils personnalisée pouvant être utilisée par d'autres personnes. <br><br>

Voir la documentation :
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">Création de modèles de chaînes d'outils personnalisées <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a>
 <br><br>
Essayez le tutoriel :
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">Créer un modèle pour une chaîne d'outils personnalisée <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe"></a></td>
<td>N/D
</td></tr>

</table>
