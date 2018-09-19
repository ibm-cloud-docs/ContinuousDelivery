---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Tutoriel d'initiation
{: #cd_getting_started}

Adoptez une approche DevOps en utilisant {{site.data.keyword.contdelivery_full}}, qui inclut une chaîne d'outils ouverte automatisant la génération et le déploiement d'applications. Vous
pouvez commencer en créant une chaîne d'outils de déploiement simple qui prend en charge les tâches de développement, de déploiement et les opérations. 
{: shortdesc}

##Conditions préalables requises
{: #cd_prereqs}

Pour créer une chaîne d’outils de distribution continue à partir d’un modèle, vous devez d'abord créer une instance de {{site.data.keyword.contdelivery_short}} en la sélectionnant dans le catalogue {{site.data.keyword.Bluemix_notm}}. La chaîne d'outils intègre des outils destinés à la planification, au développement, au déploiement de pipelines et à la gestion de vos applications. Vous pouvez toujours ajouter ou retirer des outils dans vos chaînes d'outils. Si vous disposez déjà de chaînes d'outils, vous pouvez [afficher les chaînes d'outils existantes](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}. Pour plus d'informations sur l'utilisation des chaînes d'outils, voir [Utilisation des chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}.

Si vous disposez déjà d'une instance de {{site.data.keyword.contdelivery_short}}, vous pouvez [créer une chaîne d'outils ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/devops/create){: new_window} ou [afficher les chaînes d'outils existantes](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}. {: tip}

##Etape 1 : Sélectionner un modèle de chaîne d'outils 
{: #select_a_toolchain_template}

1. Sur la page **Créer une chaîne d'outils**, cliquez sur un [modèle de chaîne d'outils ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/devops/create){: new_window}.
1. Examinez le diagramme de la chaîne d'outils que vous être sur le point de créer. Ce diagramme montre chaque intégration d'outils dans sa phase de cycle de vie au sein de la chaîne d'outils.

 Quelques modèles de chaîne d'outils possèdent plusieurs instances d'intégration d'outils. Par exemple, le modèle de chaîne d'outils Microservices sur {{site.data.keyword.Bluemix_notm}} Public contient trois instances de GitHub et trois instances de Delivery Pipeline, une pour chacun des trois microservices.
 {: tip}

 L'image suivante fournit un exemple de diagramme. Lorsque vous créez une chaîne d'outils, le diagramme représente chaque intégration d'outils faisant partie de la chaîne d'outils. ![Diagramme de chaîne d'outils](images/toolchain_diagram2.png)
 
##Etape 2 : Créer une chaîne d'outils  
{: #create_a_toolchain}
 
1. Vérifiez les valeurs par défaut des paramètres de la chaîne d'outils :

 * Le nom de la chaîne d'outils l'identifie dans {{site.data.keyword.Bluemix_notm}}. Si vous désirez utiliser un nom différent, modifiez le nom de la chaîne d'outils.
 * La région de création de la chaîne d'outils. Si vous souhaitez utiliser une région différente, sélectionnez-la dans la liste des régions disponibles.
 * Le groupe de ressources ou l'organisation dans laquelle créer la chaîne d'outils. Cliquez sur le lien pour basculer entre la sélection des groupes de ressources et celle des organisations. Si vous souhaitez utiliser un autre groupe de ressources ou une autre organisation, sélectionnez-le dans la liste des groupes de ressources ou des organisations disponibles. 
 
   Les groupes de ressources sont disponibles uniquement dans la région Sud des États-Unis.
   {: tip}
 
1. Dans la section Intégrations d'outils, sélectionnez chaque intégration d'outils à configurer pour votre chaîne d'outils. Quelques intégrations d'outils ne nécessitent pas de configuration. Pour des informations sur la configuration des intégrations d'outils, voir [Configuration d'intégrations d'outils](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Cliquez sur **Créer**. Plusieurs étapes s'exécutent automatiquement pour configurer votre chaîne d'outils. Les intégrations d'outils configurées varient en fonction du modèle de chaîne d'outils que vous avez sélectionné et selon que vous utilisez {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated. Par exemple, lorsque vous créez une chaîne d'outils Microservices sur {{site.data.keyword.Bluemix_notm}} Public, les étapes suivantes sont exécutées :

 * La chaîne d'outils est créée.
 * Si vous avez configuré Delivery Pipeline, les pipelines sont créés et exécutés.
 * Si vous avez configuré Sauce Labs, la chaîne d'outils est configurée pour ajouter des travaux de test Sauce Labs aux pipelines.
 * Si vous avez configuré PagerDuty, la chaîne d'outils est configurée pour envoyer des notifications d'alerte au service PagerDuty que vous avez indiqué.
 * Si vous avez configuré Slack, la chaîne d'outils est configurée pour envoyer au canal Slack que vous avez spécifié des notifications sur le statut de déploiement.
 * Si vous avez configuré une intégration d'outils de code source, comme GitHub, le référentiel exemple GitHub est cloné dans votre compte GitHub.

##Etapes suivantes
{: #next_steps}

Consultez l'un des tutoriels suivants sur [IBM&reg; Cloud Garage Method ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage){:new_window} :

  * [Création et utilisation de votre propre chaîne d'outils à l'aide de la chaîne d'outils "Développer une application Cloud Foundry"![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Ajout d'une chaîne d'outils à une application ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.
