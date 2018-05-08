---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Initiation à Continuous Delivery
{: #cd_getting_started}

Adoptez une approche DevOps en utilisant {{site.data.keyword.contdelivery_full}}, qui inclut une chaîne d'outils ouverte automatisant la génération et le déploiement d'applications. Vous
pouvez commencer en créant une chaîne d'outils de déploiement simple qui prend en charge les tâches de développement, de déploiement et les opérations.
{: shortdesc}

Après avoir créé une instance de {{site.data.keyword.contdelivery_short}} en la sélectionnant dans le catalogue {{site.data.keyword.Bluemix_notm}}, vous pouvez créer une chaîne d'outils Continuous Delivery à partir d'un modèle ou utiliser les chaînes d'outils existantes.
 ![Page d'accueil de Continuous Delivery](images/cd_landing_page2.png)

* Pour créer et configurer une chaîne d'outils Continuous Delivery à partir d'un modèle, cliquez sur **[Démarrer ici](#starting_from_a_toolchain_template)**. La chaîne d'outils intègre des outils destinés à la planification, au développement, au déploiement de pipelines et à la gestion de vos applications. Vous pouvez toujours ajouter ou retirer des outils dans vos chaînes d'outils.
* Si vous possédez déjà des chaînes d'outils, dans la section "Démarrer à partir d'un modèle de chaîne d'outils", cliquez sur **Affichez vos chaînes d'outils**. Pour plus d'informations sur l'utilisation des chaînes d'outils, voir [Utilisation de chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}.

##Présentation de {{site.data.keyword.contdelivery_short}}
{: #cd_overview}

Avec {{site.data.keyword.contdelivery_short}}, vous pouvez construire, tester et livrer des applications en suivant des pratiques DevOps et en utilisant des outils de pointe.
{:shortdesc}

Le service {{site.data.keyword.contdelivery_short}} prend en charge vos flux de travaux DevOps :

 * Vous pouvez créer des [chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window} ouvertes DevOps intégrées activant des intégrations d'outils prenant en charge vos tâches de développement, de déploiement et vos opérations.

  Une chaîne d'outils est un ensemble d'outils intégré que vous pouvez utiliser pour développer, construire, déployer, tester et gérer vos applications en collaborant avec d'autres utilisateurs, et pour faciliter la gestion des opérations reproductibles. Les chaînes d'outils peuvent inclure des outils open source, des services {{site.data.keyword.Bluemix_notm}}, comme [{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window} et des outils tiers, comme GitHub, PagerDuty et Slack. 
  
  **Remarque** : {{site.data.keyword.DRA_short}} est uniquement disponible dans la région sud des Etats-Unis.

 * Distribution continue à l'aide de [pipelines](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window} automatisés.

  Automatisation des générations, des tests unitaires, des déploiements, etc. Générez, testez et déployez de manière reproductible en intervenant le moins possible. Soyez prêt à lancer en production à tout moment.

 * Edition et envoi du code depuis n'importe quel emplacement à l'aide de l'[interface IDE basée sur
le Web](/docs/services/ContinuousDelivery/web_ide.html){: new_window}.

  Création, édition, exécution, débogage et réalisation de tâches de contrôle des sources dans GitHub. Passage transparent de l'édition du code à son déploiement en production. 
  
 * Collaborez avec votre équipe et gérez votre code source avec un [référentiel Git (repos) et le dispositif de suivi de problèmes](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window}, hébergé par IBM et basé sur GitLab Community Edition.

  Gérez les référentiels Git via des contrôles d'accès à granularité fine qui permettent de sécuriser le code. Révisez le code et améliorez la collaboration via des demandes de fusion. Suivez les problèmes et partagez des idées via le dispositif de suivi de problèmes. Documentez des projets sur le système de wiki.


##Démarrage depuis un modèle de chaîne d'outils
{: #starting_from_a_toolchain_template}

Pour créer et configurer une chaîne d'outils de distribution continue depuis un [modèle ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/devops/create){: new_window} :

1. Sur la page **Créer une chaîne d'outils**, cliquez sur un modèle de chaîne d'outils.
1. Examinez le diagramme de la chaîne d'outils que vous être sur le point de créer. Ce diagramme montre chaque intégration d'outils dans sa phase de cycle de vie au sein de la chaîne d'outils.

 **Astuce** : Quelques modèles de chaîne d'outils possèdent plusieurs instances d'intégration d'outils. Par exemple, le modèle de chaîne d'outils Microservices sur {{site.data.keyword.Bluemix_notm}} Public contient trois instances de GitHub et trois instances de Delivery Pipeline, une pour chacun des trois microservices.

 L'image suivante fournit un exemple de diagramme. Lorsque vous créez une chaîne d'outils, le diagramme représente chaque intégration d'outils faisant partie de la chaîne d'outils. ![Diagramme de chaîne d'outils](images/toolchain_diagram2.png)
1. Vérifiez les valeurs par défaut des paramètres de la chaîne d'outils :

 * Le nom de la chaîne d'outils l'identifie dans {{site.data.keyword.Bluemix_notm}}. Si vous désirez utiliser un nom différent, modifiez le nom de la chaîne d'outils.
 * La région de création de la chaîne d'outils. Si vous souhaitez utiliser une région différente, sélectionnez-la dans la liste des régions disponibles.
 * L'organisation dans laquelle la chaîne d'outils doit être créée. Si vous souhaitez utiliser une organisation différente, sélectionnez-la dans la liste des organisations disponibles. 
 
1. Dans la section Intégrations d'outils, sélectionnez chaque intégration d'outils à configurer pour votre chaîne d'outils. Quelques intégrations d'outils ne nécessitent pas de configuration. Pour des informations sur la configuration des intégrations d'outils, voir [Configuration d'intégrations d'outils](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Cliquez sur **Créer**. Plusieurs étapes s'exécutent automatiquement pour configurer votre chaîne d'outils. Les intégrations d'outils configurées varient en fonction du modèle de chaîne d'outils que vous avez sélectionné et selon que vous utilisez {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated. Par exemple, lorsque vous créez une chaîne d'outils Microservices sur {{site.data.keyword.Bluemix_notm}} Public, les étapes suivantes sont exécutées :

 * La chaîne d'outils est créée.
 * Si vous avez configuré Delivery Pipeline, les pipelines sont créés et exécutés.
 * Si vous avez configuré Sauce Labs, la chaîne d'outils est configurée pour ajouter des travaux de test Sauce Labs aux pipelines.
 * Si vous avez configuré PagerDuty, la chaîne d'outils est configurée pour envoyer des notifications d'alerte au service PagerDuty que vous avez indiqué.
 * Si vous avez configuré Slack, la chaîne d'outils est configurée pour envoyer au canal Slack que vous avez spécifié des notifications sur le statut de déploiement.
 * Si vous avez configuré une intégration d'outils de code source, comme GitHub, le référentiel exemple GitHub est cloné dans votre compte GitHub.
