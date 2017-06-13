---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-6"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# Git Repos and Issue Tracking
{: #git_working}

Collaborez avec votre équipe et gérez votre code source avec un référentiel Git et le dispositif de suivi des problèmes qui est hébergé par IBM et basé sur [GitLab Community Edition ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://about.gitlab.com/){:new_window}.
{: shortdesc}

L'intégration de l'outil {{site.data.keyword.gitrepos}} aide les équipes à gérer le code et à collaborer de diverses manières :
   * Gestion de référentiels Git via des contrôles d'accès à granularité fine qui permettent de sécuriser le code
   * Révision du code et amélioration de la collaboration via des demandes de fusion
   * Suivi des problèmes et partage d'idées via le dispositif de suivi de problème
   * Documentation de projets sur le système wiki

**Remarque :** cette intégration d'outils étant basée sur GitLab Community Edition et hébergée par IBM sur Bluemix, certaines options GitLab ne sont pas disponibles. Par exemple, Delivery Pipeline fournit une intégration et une distribution continues pour Bluemix ; par conséquent, les fonctions d'intégration continue dans GitLab ne sont pas prises en charge. En outre, les fonctions d'administration ne sont pas disponibles car elles sont gérées par IBM.

## Limites de taille de fichier et de référentiel
{: #git_limits}

La taille des fichiers est strictement limitée à 100 Mo. La limite de taille suggérée pour les référentiels est 1 Go. Si votre référentiel dépasse 1 Go, vous risquez de recevoir un courrier électronique vous demandant de réduire sa taille.

## Utilisation locale de Git Repos and Issue Tracking
{: #git_local}

Vous pouvez accéder localement aux référentiels Git stockés dans {{site.data.keyword.gitrepos}}. Pour savoir comment configurer un référentiel Git localement, voir [Start using Git on the command line ![Icône de
lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}.

**Astuce** : {{site.data.keyword.gitrepos}} prend uniquement en charge les connexions HTTPS qui utilisent TLS1.2. Si vous utilisez Eclipse pour vous connecter, il se peut que vous deviez indiquer ce protocole pour votre version de Java&trade; en ajoutant `-Dhttps.protocols=TLSv1.2` à votre fichier eclipse.ini, puis en redémarrant Eclipse.

## Authentification auprès de GitLab  
{: #git_authentication}

Pour effectuer des opérations Git distantes, telles que `clone` ou `push`, à partir de votre référentiel Git local, vous devez utiliser un jeton d'accès personnel ou une clé SSH pour vous authentifier auprès de GitLab.

### Création d'un jeton d'accès personnel  
Pour vous authentifier auprès de votre référentiel Git via HTTPS, vous devez créer un jeton d'accès personnel. Votre identifiant et votre mot de passe {{site.data.keyword.Bluemix_notm}} fonctionnent avec {{site.data.keyword.gitrepos}} uniquement dans un navigateur. Vous ne pouvez pas utiliser vos données d'identification {{site.data.keyword.Bluemix_notm}} pour vous authentifier à partir de clients Git externes.

1. Dans le tableau de bord {{site.data.keyword.gitrepos}} User Settings, sur la [page Access Tokens ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, entrez le nom de l'application pour laquelle vous souhaitez créer un jeton d'accès. Par exemple, `Git CLI`.
1. Facultatif : choisissez une date d'expiration pour le jeton d'accès. 
1. Cochez la case **api** pour créer un jeton d'accès personnel qui utilise l'API comme portée. 
1. Cliquez sur **Create Personal Access Token**. Notez votre jeton d'accès dans un emplacement sécurisé en vue d'une utilisation ultérieure. 
1. Sur la [page Account ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, dans la section Change username, recherchez votre nom d'utilisateur {{site.data.keyword.gitrepos}}. Votre nom d'utilisateur apparaît également en tant que premier segment de l'URL des référentiels Git personnels que vous créez.
1. Utilisez votre nom d'utilisateur {{site.data.keyword.gitrepos}} et votre jeton d'accès personnel pour vous authentifier auprès de votre référentiel Git à partir d'un client Git externe.

Pour en savoir plus, voir [Personal access tokens ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}.

### Création d'une clé SSH  
Pour créer une clé SSH, voir [How to create your SSH Keys ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}. L'accès à vos référentiels à l'aide d'une authentification SSH peut nécessiter une configuration supplémentaire pour les proxy et les pare-feux.

Pour en savoir plus, voir [SSH ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/ssh/README){:new_window}.
