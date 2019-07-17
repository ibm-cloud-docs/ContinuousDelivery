---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository

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

# {{site.data.keyword.gitrepos}}
{: #git_working}

Collaborez avec votre équipe et gérez votre code source avec un référentiel Git et un dispositif de suivi des problèmes hébergé par IBM et basé sur [GitLab Community Edition](https://about.gitlab.com/){: external}.
{: shortdesc}

Invitez uniquement les personnes avec qui vous avez une relation personnelle ou d'affaires à collaborer à un projet. Les utilisateurs qui utilisent une invitation à un référentiel Git à des fins autres que pour collaborer sur un projet peuvent voir leur accès au service suspendu ou révoqué.
{: important}

GitHub et la ligne de commande Git sont deux alternatives à GitLab auxquelles vous pouvez accéder.
{: note}

Ne stockez pas des données réglementées dans des fichiers ou des problèmes dans des référentiels Git. Les procédures relatives aux données réglementées ne sont pas encore en place.
{: tip}

L'intégration de l'outil {{site.data.keyword.gitrepos}} aide les équipes à gérer le code et à collaborer de diverses manières :
   * Gestion des référentiels Git via des contrôles d'accès à granularité fine qui permettent de sécuriser le code
   * Révision du code et amélioration de la collaboration via des demandes de fusion
   * Suivi des problèmes et partage d'idées via le dispositif de suivi de problème
   * Documentation de projets sur le système wiki

Cette intégration d'outil étant basée sur GitLab Community Edition et hébergée par IBM sur la plateforme {{site.data.keyword.Bluemix_notm}}, certaines options de GitLab ne sont pas disponibles. Par exemple, Delivery Pipeline fournit une intégration continue et une distribution continue pour {{site.data.keyword.Bluemix_notm}}, par conséquent, les fonctions d'intégration continue dans GitLab ne sont pas prises en charge. En outre, les fonctions d'administration ne sont pas disponibles car elles sont gérées par IBM.
{: tip}


## Utilisation de {{site.data.keyword.gitrepos}} localement
{: #git_locally}

Vous pouvez accéder localement aux référentiels Git stockés dans {{site.data.keyword.gitrepos}}. Pour savoir comment configurer un référentiel Git localement, voir [Start using Git on the command line](https://us-south.git.cloud.ibm.com/help/gitlab-basics/start-using-git){: external}.

{{site.data.keyword.gitrepos}} prend uniquement en charge les connexions HTTPS qui utilisent TLS1.2. Si vous utilisez Eclipse pour vous connecter, il se peut que vous deviez indiquer ce protocole pour votre version de Java&trade; en ajoutant `-Dhttps.protocols=TLSv1.2` à votre fichier eclipse.ini, puis en redémarrant Eclipse.
{: tip}

## Authentification avec {{site.data.keyword.gitrepos}}
{: #git_authentication}

Votre ID de connexion et votre mot de passe {{site.data.keyword.Bluemix_notm}} sont uniquement utilisés à des fins d'authentification auprès de{{site.data.keyword.gitrepos}} dans un navigateur Web. Vous ne pouvez pas utiliser vos données d'identification {{site.data.keyword.Bluemix_notm}} pour vous authentifier à partir de clients Git externes. Pour effectuer des opérations Git distantes, telles que `clone` ou `push`, à partir de votre référentiel Git local, vous devez utiliser un jeton d'accès personnel ou une clé SSH pour vous authentifier auprès de {{site.data.keyword.gitrepos}}.

### Création d'un jeton d'accès personnel
{: #create_pat}

Pour vous authentifier auprès de votre référentiel Git via HTTPS, vous devez créer un jeton d'accès personnel.
{: tip}

1. Sur le tableau de bord Paramètres utilisateurs de {{site.data.keyword.gitrepos}}, sur la [page Jetons d'accès](https://us-south.git.cloud.ibm.com/profile/personal_access_tokens){: external}, entrez le nom de l'application pour laquelle vous souhaitez créer un jeton d'accès. Par exemple, `Git CLI`.
1. Facultatif : choisissez une date d'expiration pour le jeton d'accès.
1. Cochez la case **api** pour créer un jeton d'accès personnel qui utilise l'API comme portée.
1. Cliquez sur **Créer un jeton d'accès personnel**. Notez votre jeton d'accès dans un emplacement sécurisé en vue d'une utilisation ultérieure.
1. Sur la [page Compte](https://us-south.git.cloud.ibm.com/profile/account){: external}, dans la section Changer le nom d'utilisateur, recherchez votre nom d'utilisateur {{site.data.keyword.gitrepos}}. Votre nom d'utilisateur apparaît également en tant que premier segment de l'URL des référentiels Git personnels que vous créez.
1. Utilisez votre nom d'utilisateur {{site.data.keyword.gitrepos}} et votre jeton d'accès personnel pour vous authentifier auprès de votre référentiel Git à partir d'un client Git externe.

Pour en savoir plus, voir [Jetons d'accès personnels](https://us-south.git.cloud.ibm.com/help/api/README.html#personal-access-tokens){: external}.

### Création d'une clé SSH  
{:create_ssh }

Pour créer une clé SSH, voir [Comment créer vos clés SSH](https://us-south.git.cloud.ibm.com/help/gitlab-basics/create-your-ssh-keys){: external}. L'accès à vos référentiels à l'aide d'une authentification SSH peut nécessiter une configuration supplémentaire pour les proxy et les pare-feux.

Pour en savoir plus, voir [SSH](https://us-south.git.cloud.ibm.com/help/ssh/README){: external}.

## Limites de taille des référentiels et des fichiers physiques
{: #git_limits}

La taille des fichiers est strictement limitée à 100 Mo. La limite de taille suggérée pour les référentiels est 1 Go. Si votre référentiel dépasse 1 Go, vous risquez de recevoir un courrier électronique vous demandant de réduire sa taille.

## Suivre un tutoriel : {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Consultez l'un des tutoriels suivants sur [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external} :

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}. Apprenez à créer une chaîne d'outils ouverte à partir d'un modèle et utilisez-la pour distribuer en continu une application "Hello World".

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. Apprenez à créer une chaîne d'outils à partir d'un modèle avec trois microservices et utilisez-la pour distribuer un magasin en ligne en continu.
