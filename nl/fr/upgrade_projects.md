---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Mise à niveau de votre projet {{site.data.keyword.jazzhub_short}} vers une chaîne d'outils
{: #upgrade_projects}

{{site.data.keyword.jazzhub}} évolue vers {{site.data.keyword.contdelivery_full}}. Dans le cadre de cette modification, les projets sont mis à niveau vers des chaînes d'outils.

Vous pouvez mettre à niveau votre projet ou attendre qu'il soit automatiquement mis à niveau. Pour obtenir de meilleurs résultats, assurez-vous de répondre aux
[conditions requises](#upgrade_prereqs) et mettez à niveau votre projet dès que possible afin de pouvoir contrôler le nom de votre chaîne d'outils et dans quelle organisation
elle est créée.
{: shortdesc}

**Foire aux questions**

- [Mon projet JazzHub est associé à la région Royaume-Uni, mais ma chaîne d'outils se trouvera dans la région Sud des Etats-Unis. Comment cela va-t-il fonctionner ?](#faq_region)
- [Qu'arrivera-t-il à mes éléments de travail et mes tableaux de bord dans Track &amp; Plan lors de la mise à niveau ?](#faq_tp)
- [Qu'arrivera-t-il à mon référentiel de code lors de la mise à niveau ?](#faq_repo)
- [Qu'arrivera-t-il à mes définitions de génération dans mon projet lors de la mise à niveau vers une chaîne d'outils ?](#faq_build)
- [Je dois créer une organisation pour mon projet qui va être mis à jour vers une chaîne d'outils. Je comprends que je dois ajouter une carte de crédit à mon compte avant de créer une organisation. Ma carte de crédit sera-t-elle débitée ?](#faq_charges)
- [Ma chaîne d'outils est introuvable ou inaccessible. Que dois-je faire ?](#faq_find)
- [Mon projet est associé à la région Royaume-Uni. Après la mise à niveau, des messages d'erreur apparaissent, mes collègues ne peuvent pas accéder à la chaîne d'outils et ma chaîne d'outils n'apparaît pas sur la page Chaînes d'outils de la plateforme {{site.data.keyword.Bluemix_notm}}. Qu'est-ce qui ne va pas ?](#faq_uk)

## Chaînes d'outils
{: #compare_toolchains}

Les chaînes d'outils sont semblables à des projets, à quelques différences importantes près :

- Les projets ne peuvent avoir qu'un seul référentiel et qu'un seul pipeline. Les chaînes d'outils peuvent avoir autant de référentiels et de pipelines que nécessaire.
- Les chaînes d'outils peuvent inclure des outils qui ne sont pas disponibles dans des projets, tels que Slack, Sauce Labs, PagerDuty et {{site.data.keyword.DRA_full}}.
- L'accès aux chaînes d'outils est géré à travers les organisations {{site.data.keyword.Bluemix_notm}} standard. L'appartenance est gérée au niveau de l'organisation, contrairement aux projets, où elle est gérée au niveau du projet.

Pour en savoir plus sur les chaînes d'outils, consultez [YouTube ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://youtu.be/2SIPE1e7NJ4){: new_window} ou la rubrique [Initiation à {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Lien externe vers YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Conditions préalables requises
{: #upgrade_prereqs}

- Pour accéder à la chaîne d'outils de votre projet actualisé, vous avez besoin d'un ID {{site.data.keyword.Bluemix_notm}}. Avant de procéder à la mise à niveau, vous devez
vérifier que vous avez un ID {{site.data.keyword.Bluemix_notm}} actif. Si vous n'en possédez pas, [enregistrez-vous](https://console.ng.bluemix.net/registration/) pour en obtenir un.
- Vérifiez que votre propriétaire de projet {{site.data.keyword.jazzhub_short}} est correct. La chaîne d'outil qui est créée dans votre projet appartiendra à l'organisation
{{site.data.keyword.Bluemix_notm}} de ce propriétaire.
- Assurez-vous que l'organisation et l'espace sur lesquels vous souhaitez créer votre chaîne d'outils se trouvent sur {{site.data.keyword.Bluemix_notm}} Public dans la région Sud des Etats-Unis. Pour vérifier que vous disposez d'une organisation et d'un espace valides dans la région Sud des Etats-Unis, connectez-vous à [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} et créez un espace si vous êtes invité à le faire.
- Si vous prévoyez de lancer la mise à niveau, vérifiez que vous êtes membre de chaque organisation et de chaque espace sur lesquels le pipeline sera déployé. N'importe quel administrateur
du projet peut démarrer la mise à niveau. Cependant, si l'administrateur qui lance la mise à niveau n'est pas membre de chaque organisation et de chaque espace sur lesquels le pipeline sera déployé, celui-ci ne peut pas être créé. La personne qui lance la mise à niveau devient le propriétaire du référentiel dans la chaîne d'outils.
- Eclipse Orion {{site.data.keyword.webide}} dans la chaîne d'outils est séparée de l'interface {{site.data.keyword.webide}} qui est associée à votre
projet. Si vous utilisez {{site.data.keyword.webide}} et que certaines modifications ne sont pas validées, validez-les avant la mise à niveau.


## Mise à niveau d'un projet vers une chaîne d'outils
{: #project_to_toolchain}

Les projets sur hub.jazz.net et les chaînes d'outils sont hébergés dans la région Sud des Etats-Unis. Si votre projet a été configuré pour déployer des
applications dans une autre région, il déploiera quand même les applications dans cette région après avoir été mis à niveau dans une chaîne d'outils.
{: tip}

Lorsque votre projet est prêt pour la mise à niveau, un message s'affiche sur la carte du projet et la page de présentation.

![Image comportant le libellé Prêt pour la mise à niveau](images/card-project-to-upgrade.png)

![Message indiquant que la mise à niveau peut être démarrée](images/banner-ready-to-upgrade.png)

Les projets prêts pour la mise à niveau se trouvent dans le menu de la page Mes projets :

![Image illustrant l'élément de menu Projets à mettre à niveau](images/menu-projects-to-upgrade.png)
{: tip}

Lorsque vous démarrez la mise à niveau, les étapes du pipeline dans votre projet sont bloquées. Vous ne pourrez pas les exécuter ni les modifier. Si vous annulez la mise à jour en
supprimant la chaîne d'outils, le pipeline est débloqué.

Si votre projet utilise un référentiel Git qui est hébergé sur JazzHub, après avoir lancé la mise à niveau, le référentiel est bloqué pour assurer l'intégrité des données qui sont
déplacées vers la chaîne d'outils. Si vous annulez la mise à niveau en supprimant la chaîne d'outils, le référentiel hébergé sur JazzHub est débloqué.

Pour obtenir des informations détaillées sur la manière dont chaque type de référentiel est traité lors de la mise à niveau, veuillez vous reporter au tableau ci-dessous.

|Référentiel de projet |Type de projet	|Référentiel de chaîne d'outils |
|:----------|:------------------------------|:------------------|
|github.com 		|Privé ou public 		|Le même référentiel github.com avec {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privé ou public 		|Un nouveau référentiel dans {{site.data.keyword.gitrepos}} avec {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tableau 1. Référentiels de projet mappés à des référentiels de chaîne d'outils" caption-side="top"}

## Démarrage du processus de mise à niveau
{: #start_upgrade}

Avant de débuter le processus de mise à niveau, vous pouvez l'observer en action sur [YouTube ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://youtu.be/LSr2e3uvyLs){: new_window}.
[![Lien externe vers YouTube](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

Pour mettre à niveau votre projet vers une chaîne d'outils, procédez comme suit :

1. Pour démarrer le processus de mise à niveau, dans le message de la bannière, cliquez sur **upgrade now**. La page "Project upgrade toolchain" s'ouvre.

   ![Exemple de page de mise à niveau](images/project-upgrade-toolchain.png)

   Pour une présentation du processus de mise à niveau, lisez la description sur cette page. La chaîne d'outils inclut un nouveau pipeline qui contient les mêmes étapes et travaux que le pipeline du projet. En outre, la chaîne d'outils contient un pointeur vers l'interface Eclipse Orion {{site.data.keyword.webide}} qui s'exécute dans {{site.data.keyword.contdelivery_short}}.

   Dans cet exemple, le projet utilise un référentiel public sur github.com et la chaîne d'outils sera donc connectée au même référentiel GitHub. Si votre projet utilise un référentiel Git
hébergé sur JazzHub, le contenu de ce référentiel sera cloné dans un nouveau référentiel dans {{site.data.keyword.gitrepos}} qui appartient à {{site.data.keyword.contdelivery_short}}.

2. Pour personnaliser la chaîne d'outils, vous pouvez configurer quelques paramètres :

   - Pour changer le nom de la chaîne d'outils, modifiez la zone **Nom**.

      ![Zone Nom](images/name-change.png)

   - Pour modifier l'organisation {{site.data.keyword.Bluemix_notm}} dans laquelle créer la chaîne d'outils, sélectionnez l'organisation dans le menu de votre compte :

      ![{{site.data.keyword.Bluemix_notm}} Sélecteur d'organisation](images/bluemix-organization-chooser.png)

   Les chaînes d'outils étant gérées au niveau de l'organisation, veillez à sélectionner une organisation où les membres du projet qui ont besoin d'accéder à la chaîne d'outils existent ou peuvent être ajoutés.

3. Si vous avez utilisé Track & Plan dans votre projet, vous pouvez transférer vos données Track & Plan à GitHub Issues.

   ![Options de Track and Plan](images/upgrade-tutorial-track-and-plan.png)

   - Indiquez si vous souhaitez faire migrer vos données Track & Plan.
   - Par défaut, toutes vos données Track & Plan sont migrées. Si vous préférez faire migrer uniquement les éléments de travail appartenant à une requête spécifique, indiquez
cette requête.
   - Sélectionnez les attributs d'éléments de travail que vous souhaitez mapper aux étiquettes dans GitHub Issues.

4. Cliquez sur **Créer**. La chaîne d'outils est créée et sa page de présentation s'affiche.

   ![Présentation de la chaîne d'outils mise à niveau](images/new-toolchain-page.png)

   - Pour accéder à votre référentiel GitHub ou au suivi de problème associé, cliquez sur **GitHub** ou **Issues**.
   - Pour accéder à votre pipeline, cliquez sur **Delivery Pipeline**.
   - Pour accéder à l'interface {{site.data.keyword.webide}}, qui inclut le contenu de votre référentiel qui a été réservé dans l'espace de travail, cliquez sur l'interface **Eclipse Orion {{site.data.keyword.webide}}**.

   Si vous retournez à votre projet durant la mise à niveau, le message de la bannière risque d'indiquer que la mise à niveau est en cours, en particulier si le processus de mise à
jour implique l'importation d'un code source dans un nouveau référentiel ou l'importation d'éléments de travail Track &amp; Plan comme problèmes.

   ![Message indiquant qu'un projet est en cours de mise à niveau vers une chaîne d'outils](images/project-being-upgraded-banner.png)

## Révision de votre projet
{: #revisit_projects}

Vous êtes prêt à utiliser votre nouvelle chaîne d'outils. Votre projet s'intitule maintenant "Upgraded" et un message de confirmation s'affiche sur la page de présentation.

![Image comportant le libellé Mis à niveau](images/card-upgraded-project.png)

![Projet mis à niveau](images/banner-upgraded.png)

Vous pouvez voir quels projets sont mis à niveau en sélectionnant **Projets mis à niveau** dans le menu de la page Mes projets.

![Image illustrant l'élément de menu Projets mis à niveau](images/menu-upgraded-projects.png)

Pour annuler la mise à niveau, supprimez votre chaîne d'outils. Vous pouvez supprimer votre chaîne d'outils du menu **Plus d'actions** sur la page de présentation de
la chaîne d'outils :

![Image illustrant l'option Supprimer du menu Plus d'actions](images/upgrade-tutorial-delete-toolchain.png)

Lorsque vous retournez à votre projet, le message de mise à niveau s'affiche à nouveau et vous pouvez renouveler la mise à niveau lorsque vous êtes prêt.

## Etapes suivantes
{: #upgrade_next_steps}

1. Confirmez que la mise à niveau est terminée en actualisant votre navigateur et en recherchant le message indiquant que votre projet "a été mis à niveau vers cette chaîne d'outils" sur
la page de présentation du projet :

   ![Message indiquant que le projet a été mis à niveau](images/banner-upgraded.png)

   Si le message indique "mettre à niveau maintenant", votre mise à niveau a échoué. Cliquez sur le lien **mettre à niveau maintenant**
pour faire une nouvelle tentative.
   {: tip}

   ![Message indiquant que le projet est prêt à être mis à niveau](images/banner-ready-to-upgrade.png)

2. Accordez l'accès à la chaîne d'outils aux membres de votre équipe.
    - Chaque membre d'équipe doit disposer d'un compte {{site.data.keyword.Bluemix_notm}} valide. Les membres de l'équipe qui ne possèdent pas de comptes doivent [s'enregistrer![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/registration){:new_window}.
    - Accordez aux membres de l'organisation un accès à la chaîne d'outils depuis la page Gérer de la chaîne d'outils. Des membres de projet existants sont ajoutés en tant que membres de la chaîne d'outils dans le cadre du processus de mise à niveau. Pour en savoir plus sur le contrôle d'accès aux chaînes d'outils, voir [Gestion des accès ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Si un utilisateur n'est pas membre de l'organisation à laquelle appartient la chaîne d'outils, ajoutez-le à l'organisation depuis la page Gérer les organisations.
    - Si votre chaîne d'outils utilise {{site.data.keyword.gitrepos}}, tous les membres du projet JazzHub dotés d'un ID {{site.data.keyword.Bluemix_notm}} valide sont ajoutés au référentiel {{site.data.keyword.gitrepos}} avec les mêmes privilèges que ceux qu'ils avaient dans le projet JazzHub. Si votre projet JazzHub comprend des membres qui ne disposent pas d'un ID {{site.data.keyword.Bluemix_notm}} valide, ceux-ci peuvent s'inscrire pour en obtenir un et être ajoutés au référentiel.
      Pour obtenir des informations complémentaires sur la gestion des organisations, voir [Gestion des organisations et des espaces ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Utilisez les outils de votre chaîne d'outils au lieu des outils de votre projet {{site.data.keyword.jazzhub_short}}. Par exemple, pour modifier le code à partir d'un navigateur, utilisez l'interface IDE Web de votre chaîne d'outils.

4. Si vous utilisez {{site.data.keyword.gitrepos}}, authentifiez-vous à l'aide d'un jeton d'accès personnel ou d'une clé SSH. Pour en savoir plus sur les clés SSH, voir [Création d'un jeton d'accès personnel ou d'une clé SSH pour l'authentification](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Pour s'authentifier depuis un client Git externe via https, procédez comme suit :
    1. Accédez à la page [Jetons d'accès ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} de vos paramètres utilisateurs {{site.data.keyword.gitrepos}}.
    2. Créez un jeton d'accès personnel utilisant **api** comme portée.
    3. Accédez à la page [Compte ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/account){:new_window} et recherchez votre nom d'utilisateur pour {{site.data.keyword.gitrepos}}. Votre nom d'utilisateur est répertorié dans la section "Changer le nom d'utilisateur" et apparaît dans la première partie de l'URL des référentiels personnels que vous créez.
    4. Pour vous authentifier avec {{site.data.keyword.gitrepos}} depuis un client Git externe via https, utilisez votre nom d'utilisateur et votre jeton d'accès personnel.
    5. Si vous souhaitez réutiliser le référentiel local de votre référentiel JazzHub Git, faites pointer le référentiel vers le nouveau référentiel dans {{site.data.keyword.gitrepos}}. Depuis un interpréteur de commande shell dans un terminal, accédez au répertoire dans lequel le référentiel JazzHub Git est cloné. Entrez la commande `git remote set-url` : `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        Pour vérifier quelles URL distantes sont définies sur quels noms distants, utilisez la commande `git remote -v`. Le nom distant par défaut est `origin`. Si vous disposez d'une configuration plus avancée, le format de la commande est le suivant : `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

5. Lorsque votre chaîne d'outils est configurée et vous avez commencé de l'utiliser, pensez à suivre toutes ou partie de ces étapes afin de vous assurer que personne n'utilise
votre projet :
    - Ajoutez un suffixe à votre nom de projet indiquant qu'il ne doit pas être utilisé. Par exemple, vous pouvez ajouter `_NE_PAS_UTILISER` à la fin du nom de projet.
    - Mettez à jour la description du projet pour indiquer qu'elle n'est plus utilisée et ajoutez un pointeur à la chaîne d'outils.
    - Supprimez les membres du projet.
    - Lorsque vous n'avez plus besoin du projet, supprimez-le.

6. Facultatif : pour explorer la maturité du développement de votre projet, les pratiques de votre équipe et la qualité de votre codebase, ajoutez IBM Cloud
{{site.data.keyword.DRA_short}} à votre chaîne d'outils. {{site.data.keyword.DRA_short}} applique les analyses de déploiement, le développeur et l'équipe aux projets DevOps. Pour
plus d'informations, voir [Initiation à {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Traitement des incidents
{: #upgrade_troubleshoot}

Si un problème se produit lors du processus de mise à niveau, essayez une ou plusieurs des étapes de traitement des incidents suivantes :

- Vérifiez que les [prérequis](#upgrade_prereqs) ont été respectés. Plus spécifiquement, assurez-vous que vous êtes membre de chaque organisation et de chaque espace sur lesquels le pipeline sera déployé.
- Si le problème s'est produit lors de votre première tentative de mise à niveau et que tous les prérequis sont respectés, relancez l'opération.
- Si votre projet utilise Jazz SCM ou IBM Hosted Git pour le contrôle des sources, vérifiez la taille du référentiel. Si celui-ci fait plus de 500 Mo, [contactez l'équipe de services DevOps![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.
- Si votre chaîne d'outils est introuvable ou inaccessible, consultez [cette entrée de FAQ](#faq_find).
- Si les problèmes persistent, publiez une question sur le [forum de support ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. Dans votre
publication de forum, incluez les URL à votre projet {{site.data.keyword.jazzhub_short}} et votre chaîne d'outils {{site.data.keyword.contdelivery_short}} et signalez votre
publication avec l'étiquette `devops-services`.


## Foire aux questions
{: #upgrade_faq}

### Mon projet JazzHub est associé à la région Royaume-Uni, mais ma chaîne d'outils se trouvera dans la région Sud des Etats-Unis. Comment cela va-t-il fonctionner ?
{: #faq_region}

Les projets sur hub.jazz.net et les chaînes d'outils sont hébergés dans la région Sud des Etats-Unis. Si votre projet a été configuré pour déployer des applications dans une autre région, comme la région Royaume-Uni, il déploiera quand même les applications dans cette région après avoir été mis à niveau dans une chaîne d'outils. Aucune modification n'est donc réellement apportée quant à l'emplacement d'hébergement des données. A l'avenir, les chaînes d'outils seront disponibles dans davantage de régions.

### Qu'arrivera-t-il à mes éléments de travail et mes tableaux de bord dans Track &amp; Plan lors de la mise à niveau ?
{: #faq_tp}

Le service {{site.data.keyword.contdelivery_short}} fournit des fonctions de suivi des problèmes grâce à {{site.data.keyword.gitrepos}}, hébergé par IBM et basé sur GitLab Community Edition. {{site.data.keyword.contdelivery_short}} prend également en charge les intégrations dotées d'autres outils de planification et de suivi des problèmes, tels que GitHub Issues et JIRA.

Pendant le processus de mise à niveau, vous pouvez choisir de migrer vos éléments de travail Track &amp; Plan vers Git Issues. GitHub Issues et {{site.data.keyword.gitrepos}} fournissent des tableaux Kanban et un système de suivi des problèmes pour la planification. Pour en savoir plus sur Issue Boards, qui est la fonction kanban de Git Repos and Issue Tracking, voir [Issue board ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Pour les clients qui exigent la même fonction que JazzHub Track &amp; Plan désormais obsolète, un nouveau service IBM Track and Plan on Cloud est disponible et peut être acheté séparément dans certains pays sur une base mensuelle par utilisateur. Ce service de cloud vous permet de bénéficier de fonctions complètes, équivalentes aux licences contributeur Rational Team Concert&trade;, avec un abonnement de cloud à service exclusif.

Ce nouveau service IBM Track and Plan on Cloud propose une fonctionnalité beaucoup plus riche que la fonction obsolète JazzHub Track &amp; Plan, en prenant en charge la personnalisation des processus, les hiérarchies de projet, SAFe&reg; et de nombreuses autres méthodes hybrides et agiles, tout en garantissant l'évolutivité qui permet une croissance au-delà d'un simple projet. Il repose sur la version la plus récente de Rational Team Concert 6.0.3 et sera au niveau de la version 6.0.4 dans les 60 prochains jours, alors que JazzHub Track &amp; Plan était basé sur Rational Team Concert 5.x. Il est possible de migrer les données vers IBM Track and Plan on Cloud grâce à des services supplémentaires. Pour plus d'informations, vous pouvez contacter [Tom Hollowell ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](mailto:trhollow@us.ibm.com){:new_window}, Responsable des ventes SaaS des produits connectés.

Pour obtenir des informations sur IBM Track and Plan on Cloud, ou pour effectuer un achat en ligne, accédez à [IBM Marketplace ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

[Rational Team Concert on Cloud ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} vous permet également de bénéficier en plus des fonctions d'automatisation de la construction et de gestion du code source.

### Qu'arrivera-t-il à mon référentiel de code lors de la mise à niveau ?
{: #faq_repo}

Une fois la mise à niveau effectuée, votre nouveau service Git sera comparable à ce dont vous disposiez auparavant. Si vous utilisiez github.com avec votre projet JazzHub, votre chaîne d'outils est connectée au même référentiel GitHub. Si votre projet JazzHub utilisait le référentiel Git hébergé par IBM, le contenu de ce référentiel est cloné vers un nouveau référentiel dans {{site.data.keyword.gitrepos}}, qui fait partie de {{site.data.keyword.contdelivery_short}} et est hébergé par IBM.

Pour obtenir des informations détaillées sur la manière dont chaque type de référentiel est traité lors de la mise à niveau, veuillez vous reporter au tableau ci-dessous.

|Référentiel de projet |Type de projet	|Référentiel de chaîne d'outils |
|:----------|:------------------------------|:------------------|
|github.com 		|Privé ou public 		|Le même référentiel github.com avec {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privé ou public 		|Un nouveau référentiel privé ou public dans {{site.data.keyword.gitrepos}} avec {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tableau 1. Référentiels de projet mappés à des référentiels de chaîne d'outils" caption-side="top"}


### Qu'arrivera-t-il à mes définitions de génération dans mon projet lors de la mise à niveau vers une chaîne d'outils ?
{: #faq_build}

Si vous générez votre code source avec Jazz à la place de Delivery Pipeline, vous devez migrer manuellement vos définitions de génération vers Delivery Pipeline dans votre chaîne d'outils.

Si vous utilisez Jazz SCM comme référentiel source et Delivery Pipeline pour générer votre code, le code source de Jazz SCM est automatiquement déplacé vers un référentiel Git. Votre configuration de Delivery Pipeline reste la même mais consomme le code source du référentiel Git au lieu du code source de Jazz SCM.

### Je dois créer une organisation pour mon projet qui va être mis à jour vers une chaîne d'outils. Je comprends que je dois ajouter une carte de crédit à mon compte avant de créer une organisation. Ma carte de crédit sera-t-elle débitée ?
{: #faq_charges}

En tant que [client de type Paiement à la carte ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, si vous utilisez un contexte d'exécution, un service ou un composant au-delà des allocations gratuites répertoriées dans le catalogue {{site.data.keyword.Bluemix_notm}}, vous êtes facturé. Pour avoir une estimation de votre utilisation, reportez-vous à la  [fiche de prix ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Pour connaître la tarification en vigueur de Continuous Delivery, voir le [catalogue {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Si vous êtes un employé IBM, les projets IBM internes peuvent être facturés aux départements, à la place d'une carte de crédit personnelle. Si vous avez besoin d'utiliser des ressources au-delà des allocations gratuites destinées aux employés IBM, créez un ticket de demande de service.

### Ma chaîne d'outils est introuvable ou inaccessible. Que dois-je faire ?
{: #faq_find}

Les chaînes d'outils sont hébergées dans les organisations {{site.data.keyword.Bluemix_notm}}. Le processus de mise à niveau ajoute tous les membres du projet JazzHub à la chaîne d'outils. Cela dit, si ces utilisateurs ne sont pas ajoutés à l'organisation {{site.data.keyword.Bluemix_notm}} par le propriétaire de cette dernière, ils ne peuvent pas voir la chaîne d'outils.

Pour accéder à votre chaîne d'outils, accédez à la plateforme {{site.data.keyword.Bluemix_notm}}, cliquez sur l'icône de menu, puis sur **Services &gt; DevOps**. La page Chaîne d'outils s'affiche. Vérifiez que vous vous trouvez dans la région Sud des Etats-Unis et que vous avez été ajouté à l'organisation qui contient la chaîne d'outils. Si votre chaîne d'outils n'apparaît pas sur la page Chaînes d'outils, consultez [cette entrée de FAQ](#faq_uk).

Sinon, tant que le site JazzHub est encore disponible, vous pouvez aussi accéder à votre chaîne d'outils en cliquant sur le lien dans la bannière figurant sur la page de présentation de votre projet.

### Mon projet est associé à la région Royaume-Uni. Après la mise à niveau, des messages d'erreur apparaissent, mes collègues ne peuvent pas accéder à la chaîne d'outils et ma chaîne d'outils n'apparaît pas sur la page Chaînes d'outils de {{site.data.keyword.Bluemix_notm}}. Qu'est-ce qui ne va pas ?
{: #faq_uk}

**Question complète :**

Mon projet JazzHub est associé à la région Royaume-Uni de {{site.data.keyword.Bluemix_notm}} conformément aux paramètres du projet. J'ai vérifié les paramètres de mon projet en accédant à la page de présentation le concernant sur JazzHub, en cliquant sur l'icône **Settings** (qui ressemble à un engrenage) et en cliquant sur **Options &gt; Make this a {{site.data.keyword.Bluemix_notm}} Project: Region**. Après la mise à niveau du projet vers une chaîne d'outils aux Etats-Unis, les problèmes suivants se sont produits :

   1. Lorsque je sélectionne l'organisation américaine, un message indiquant que cette organisation ne comporte pas d'espace dans la région Sud des Etats-Unis s'affiche et je suis invité à créer un espace. Je ne veux rien exécuter aux Etats-Unis.
   
   2. Certains de mes collègues ne peuvent pas accéder à la chaîne d'outils, pourtant ils apparaissaient en tant que membres dans le projet JazzHub initial. S'ils tentent d'ouvrir la chaîne d'outils à partir de la page de présentation de l'application dans la région Etats-Unis en cliquant sur **Afficher la chaîne d'outils**, un message "accès refusé"  s'affiche.
   
   3. La chaîne d'outils répertoriée sur ma page Chaînes d'outils n'apparaît pas sur [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, en revanche, je peux y accéder directement à partir de la page de présentation de l'application dans la région Etats-Unis en cliquant sur **Afficher la chaîne d'outils**. J'obtiens un message d'erreur indiquant que je ne peux pas modifier la chaîne d'outils ou que je possède pas de chaîne d'outils et que je dois en créer une. 

**Réponse :**

Ces problèmes peuvent se produire si vous êtes issu d'une organisation {{site.data.keyword.Bluemix_notm}} non américaine et que vous n'avez pas étendu explicitement votre organisation dans la région Sud des Etats-Unis avant la mise à niveau. Vous pouvez vérifier cela de deux façons :

   * Lorsque vous ouvrez l'URL de chaîne d'outils, vérifiez l'en-tête {{site.data.keyword.Bluemix_notm}}. La plupart du temps, seul le nom de votre organisation apparaît et aucun espace n'est indiqué.
   
   * A partir de la page de présentation de votre chaîne d'outils, cliquez sur **Gérer**. Sur la page de contrôle d'accès, cliquez sur **Responsables de l'organisation**. L'organisation qui contient la chaîne d'outils s'affiche sur la page principale.

Voici ce qu'il s'est passé : au moment de la mise à niveau, votre organisation non américaine n'existait pas aux Etats-Unis, par conséquent, la mise à niveau a sélectionné une autre organisation pour vous en recherchant une autre à laquelle il vous est arrivé d'accéder.

Si vous passez dans cette organisation {{site.data.keyword.Bluemix_notm}} américaine, la chaîne d'outils apparaîtra. Si vous ajoutez vos collègues à cette organisation, un accès leur sera accordé. Cette chaîne d'outils peut continuer à être déployée sur votre organisation non américaine. Le seul problème est que ces deux organisations sont distinctes ; la gestion des utilisateurs ne peut pas s'effectuer automatiquement sur les deux.

Si vous souhaitez que votre chaîne d'outils figure dans une organisation américaine correspondant à votre organisation non américaine, procédez comme suit :

   1. Connectez-vous à [https://console.bluemix.net ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net){: new_window} et sélectionnez la région et l'organisation non américaines dont vous provenez.
   
   2. Dans l'en-tête {{site.data.keyword.Bluemix_notm}}, passez dans la région Sud des Etats-Unis. Vous serez invité à créer un espace dans cette région.
   
   3. Créez un espace dans la région Sud des Etats pour étendre votre organisations dans cette région. 
   
   4. Supprimez la chaîne d'outils qui a été créée via le processus de mise à niveau. 
   
      Le référentiel Git n'est pas supprimé automatiquement. Vous souhaiterez peut-être le supprimer manuellement ou le renommer pour le moment. Si vous avez déjà modifié le référentiel, vous pourrez mettre à jour la future chaîne d'outils pour l'utiliser ultérieurement.
{: tip}

   5. Revenez au projet JazzHub. Normalement, il doit être automatiquement réinitialisé pour permettre une autre tentative de mise à niveau. Si tel n'est pas le cas, contactez hub@jazz.net en indiquant l'URL du projet.
   
   6. Redémarrez le processus de mise à niveau en prenant soin de sélectionner l'organisation dans la région Etats-Unis qui correspond au nom de votre organisation dans la région hors des Etats-Unis.
   
   7. Si vous avez conservé ou renommé le référentiel Git issu de votre précédente tentative de mise à niveau de chaîne d'outils (voir l'étape 4), vous pouvez reconfigurer la carte Git dans votre chaîne d'outils pour qu'elle pointe vers l'URL du référentiel Git. Cette modification est automatiquement répercutée dans le pipeline. Pour le vérifier, consultez l'onglet Entrée sur l'étape Génération.
