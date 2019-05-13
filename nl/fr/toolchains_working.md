---

copyright:
  years: 2015, 2019

lastupdated: "2019-03-07"

keywords: set of tool integrations, collective power of a toolchain, IBM Cloud

subcollection: ContinuousDelivery

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

# Création de chaînes d'outils
{: #toolchains_getting_started}

Une *chaîne d'outils* est un ensemble d'intégrations d'outils prenant en charge des tâches de développement, de déploiement et d'opérations. La puissance collective d'une chaîne d'outils est supérieure à la somme de ses intégrations d'outils individuelles.
{: shortdesc}

Des chaînes d'outils ouvertes sont disponibles dans les environnements {{site.data.keyword.Bluemix}} Public et Dedicated. Vous pouvez créer une chaîne d'outils de deux façons : à l'aide d'un modèle ou à partir d'une application.

Chaque chaîne d'outils est associée à un groupe de ressources ou à une organisation (org) spécifique. Si une chaîne d'outils est associée à un groupe de ressources, tout utilisateur disposant de l'autorisation d'Afficheur Identity and Access Management (IAM) pour la ressource de chaîne d'outils ou le groupe de ressources qui la contient peut accéder à la chaîne d'outils. Si la chaîne d'outils est associée à une organisation, tout utilisateur membre de cette organisation peut être ajouté à la liste de contrôle d'accès de l'une des chaînes d'outils associées. Pour plus d'informations sur le contrôle d'accès aux chaînes d'outils dans les organisations Cloud Foundry, voir [Gestion de l'accès aux chaînes d'outils dans les organisations Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}. Pour plus d'informations sur le contrôle d'accès aux chaînes d'outils dans les groupes de ressources, voir [Gestion de l'accès aux chaînes d'outils dans les groupes de ressources](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups){: new_window}.

##Création d'une chaîne d'outils à partir d'un modèle   
{: #creating_a_toolchain_from_a_template}

Vous pouvez utiliser un modèle comme point de départ pour [créer une chaîne d'outils![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/devops/create){: new_window} incluant un ensemble spécifique d'intégrations d'outils. Pour en savoir plus sur l'utilisation des modèles, consultez [IBM Cloud Garage Method ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/category/tools){:new_window}.

1. Si vous utilisez {{site.data.keyword.Bluemix_notm}} Public, connectez-vous à [{{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://cloud.ibm.com){:new_window}.
1. Si vous utilisez {{site.data.keyword.Bluemix_notm}} Dedicated, connectez-vous à votre environnement Dedicated sur {{site.data.keyword.Bluemix_notm}}.
1. Dans le menu de la barre de menus {{site.data.keyword.Bluemix_notm}}, cliquez sur **DevOps**.
1. Dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, cliquez sur **Créer une chaîne d'outils**.
1. Sur la page **Créer une chaîne d'outils**, cliquez sur un modèle de chaîne d'outils.
1. Examinez le diagramme de la chaîne d'outils que vous être sur le point de créer. Ce diagramme montre chaque intégration d'outils dans sa phase de cycle de vie au sein de la chaîne d'outils.

 Quelques modèles de chaîne d'outils possèdent plusieurs instances d'intégration d'outils. Par exemple, le modèle de chaîne d'outils Microservices sur {{site.data.keyword.Bluemix_notm}} Public contient trois instances de GitHub et trois instances de Delivery Pipeline, une pour chacun des trois microservices.
 {: tip}

 L'image suivante fournit un exemple de diagramme. Lorsque vous créez une chaîne d'outils, le diagramme représente chaque intégration d'outils faisant partie de la chaîne d'outils.
![Diagramme de chaîne d'outils](images/toolchain_diagram2.png)

1. Vérifiez les valeurs par défaut des paramètres de la chaîne d'outils :

 * Le nom de la chaîne d'outils l'identifie dans {{site.data.keyword.Bluemix_notm}}. Si vous désirez utiliser un nom différent, modifiez le nom de la chaîne d'outils.
 * La région de création de la chaîne d'outils. Si vous souhaitez utiliser une région différente, sélectionnez-la dans la liste des régions disponibles.
 * Le groupe de ressources ou l'organisation dans laquelle créer la chaîne d'outils. Cliquez sur le lien pour basculer entre la sélection des groupes de ressources et celle des organisations. Si vous souhaitez utiliser un autre groupe de ressources ou une autre organisation, sélectionnez-le dans la liste des groupes de ressources ou des organisations disponibles.
 
   Les groupes de ressources sont disponibles dans les régions Sud des Etats-Unis, Est des Etats-Unis, Royaume-Uni, Allemagne et Tokyo. Les organisations Cloud Foundry sont prises en charge dans les régions Sud des Etats-Unis, Royaume-Uni et Allemagne.
   {: important}

1. Dans la section Intégrations d'outils, sélectionnez chaque intégration d'outils à configurer pour votre chaîne d'outils. Quelques intégrations d'outils ne nécessitent pas de configuration. Pour des informations sur la configuration des intégrations d'outils, voir [Configuration d'intégrations d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}.
1. Cliquez sur **Créer**. Plusieurs étapes s'exécutent automatiquement pour configurer votre chaîne d'outils. Les intégrations d'outils configurées varient en fonction du modèle de chaîne d'outils que vous avez sélectionné et selon que vous utilisez {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated. Par exemple, lorsque vous créez une chaîne d'outils Microservices sur {{site.data.keyword.Bluemix_notm}} Public, les étapes suivantes sont exécutées :

 * La chaîne d'outils est créée.
 * Si vous avez configuré Delivery Pipeline, les pipelines sont créés et déclenchés.
 * Si vous avez configuré Sauce Labs, la chaîne d'outils est configurée pour ajouter des travaux de test Sauce Labs aux pipelines.
 * Si vous avez configuré PagerDuty, la chaîne d'outils est configurée pour envoyer des notifications d'alerte au service PagerDuty que vous avez indiqué.
 * Si vous avez configuré Slack, la chaîne d'outils est configurée pour envoyer au canal Slack que vous avez spécifié des notifications sur le statut de déploiement.
 * Si vous avez configuré une intégration d'outils de code source, comme GitHub, le référentiel exemple GitHub est cloné dans votre compte GitHub.


##Création d'une chaîne d'outils à partir d'une application
{: #creating_a_toolchain_from_an_app}

Vous pouvez créer une chaîne d'outils à partir de votre application. La chaîne d'outils peut prendre en charge le développement, le déploiement, la surveillance, etc. en continu, et elle est associée à votre application. Chaque application peut être associée à une chaîne d'outils. Lorsque vous envoyez des modifications au référentiel GitHub ou {{site.data.keyword.ghe_short}} de la chaîne d'outils, le pipeline génère et déploie automatiquement l'application.

Si vous avez créé votre application à l'aide de votre propre référentiel de code, cliquez sur **Configurer la distribution continue** sur la page d'information de votre application. Ensuite, suivez la procédure décrite dans [Création d'application à partir de votre propre référentiel de code](/docs/apps?topic=creating-apps-tutorial-byoc#tutorial-byoc).
{: note}

1. Si vous avez créé votre application à l'aide d'un kit de démarrage, cliquez sur **Configurer la distribution continue** sur la page d'informations de votre application. Sélectionnez ensuite une cible de déploiement. Si vous utilisez {{site.data.keyword.Bluemix_notm}} Public, votre application est configurée pour la distribution continue depuis un nouveau référentiel GitHub rempli avec le code de démarrage d'application. Si vous utilisez {{site.data.keyword.Bluemix_notm}} Dedicated, votre application est configurée pour la distribution continue depuis un nouveau référentiel GitHub ou {{site.data.keyword.ghe_short}} rempli avec le code de démarrage d'application.
1. Sur la page de configuration des chaînes d'outils, passez en revue le diagramme de la chaîne d'outils que vous êtes sur le point de créer. Ce diagramme montre chaque intégration d'outils dans sa phase de cycle de vie au sein de la chaîne d'outils.
1. Passez en revue les informations par défaut des paramètres de chaîne d'outils. Le nom de la chaîne d'outils l'identifie dans {{site.data.keyword.Bluemix_notm}}. Si vous désirez utiliser un nom différent, modifiez le nom de la chaîne d'outils.
1. Dans la section Intégrations d'outils, sélectionnez chaque intégration d'outils à configurer pour votre chaîne d'outils. Quelques intégrations d'outils ne nécessitent pas de configuration. Pour des informations sur la configuration des intégrations d'outils, voir [Configuration d'intégrations d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}.
1. Cliquez sur **Créer**. Plusieurs étapes s'exécutent automatiquement pour configurer votre chaîne d'outils. Les intégrations d'outils configurées varient selon que vous utilisez des chaînes d'outils sur {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated. Par exemple, lorsque vous créez une chaîne d'outils à partir d'une application sur {{site.data.keyword.Bluemix_notm}} Public, les étapes suivantes sont exécutées :

 * La chaîne d'outils est créée.
 * Si vous avez configuré Delivery Pipeline, les pipelines sont créés et déclenchés.
 * Si vous avez configuré GitHub, le référentiel exemple GitHub est cloné dans votre compte GitHub.


##Affichage d'une chaîne d'outils
{: #viewing_a_toolchain}

Une fois que vous avez configuré la chaîne d'outils et ses intégrations d'outils, vous pouvez afficher une représentation visuelle de la chaîne d'outils.

Vous pouvez afficher une chaîne d'outils à partir d'une application en cliquant sur **Afficher la chaîne d'outils** sur la page d'informations de votre application.
{: tip}

1. Dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, sélectionnez un **GROUPE DE RESSOURCES** ou une **ORGANISATION CLOUD FOUNDRY**. Toutes les chaînes d’outils contenues dans le groupe de ressources sélectionné ou l’organisation Cloud Foundry sont affichées. Cliquez sur la chaîne d'outils à afficher pour ouvrir sa page Vue d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**. Ensuite, cliquez sur **Vue d'ensemble**.
2. Pour accéder à une intégration d'outils de votre chaîne d'outils, cliquez sur l'outil.

 Si vous disposez de plusieurs référentiels GitHub, {{site.data.keyword.ghe_short}} ou Git, plusieurs cartes peuvent être disponibles pour une même intégration d'outils car chaque référentiel dispose de sa propre carte. Si vous disposez de plusieurs pipelines, plusieurs cartes peuvent être disponibles pour la même intégration d'outils car chaque pipeline est représenté par sa propre carte. Par exemple, lorsque vous créez une chaîne d'outils Microservices, chacun des trois microservices dispose de son propre référentiel GitHub, {{site.data.keyword.ghe_short}} ou Git et de son propre pipeline.
 {: tip}

## Suivre un tutoriel : Utilisation de chaînes d'outils
{: #toolchain_tutorials}

Consultez l'un des tutoriels suivants sur [IBM&reg; Cloud Garage Method ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage){:new_window} :

  * [Création et utilisation de votre propre chaîne d'outils à l'aide de la chaîne d'outils "Développer une application Cloud Foundry"![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Ajout d'une chaîne d'outils à une application ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.

  * [Utilisation de la chaîne d'outils "Développer et tester des microservices sur Cloud Foundry" ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
