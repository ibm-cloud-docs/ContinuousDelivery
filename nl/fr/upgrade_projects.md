---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-5"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

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

## Chaînes d'outils
{: #compare_toolchains}

Les chaînes d'outils sont semblables à des projets, à quelques différences importantes près :

- Les projets ne peuvent avoir qu'un seul référentiel et qu'un seul pipeline. Les chaînes d'outils peuvent avoir autant de référentiels et de pipelines que nécessaire.
- Les chaînes d'outils peuvent inclure des outils qui ne sont pas disponibles dans des projets, tels que Slack, Sauce Labs, PagerDuty et {{site.data.keyword.DRA_full}}.
- L'accès aux chaînes d'outils est géré à travers les organisations {{site.data.keyword.Bluemix_notm}} standard. L'appartenance est gérée au niveau de l'organisation, contrairement aux projets, où elle est gérée au niveau du projet.

Pour en savoir plus sur les chaînes d'outils, consultez [YouTube![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://youtu.be/2SIPE1e7NJ4){: new_window} ou la section [Initiation à {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Lien externe vers YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Conditions préalables requises
{: #upgrade_prereqs}

- Pour accéder à la chaîne d'outils de votre projet actualisé, vous avez besoin d'un ID {{site.data.keyword.Bluemix_notm}}. Avant de procéder à la mise à niveau, vous devez
vérifier que vous avez un ID {{site.data.keyword.Bluemix_notm}} actif. Si vous n'en possédez pas, [enregistrez-vous](https://console.ng.bluemix.net/registration/) pour en obtenir un.
- Vérifiez que votre propriétaire de projet {{site.data.keyword.jazzhub_short}} est correct. La chaîne d'outil qui est créée dans votre projet appartiendra à l'organisation
{{site.data.keyword.Bluemix_notm}} de ce propriétaire.
- Si vous prévoyez de lancer la mise à niveau, vérifiez que vous êtes membre de chaque organisation et de chaque espace que le pipeline a pour cible de déploiement. N'importe quel administrateur
du projet peut démarrer la mise à niveau. Cependant, si l'administrateur qui lance la mise à niveau n'est pas membre de chaque organisation et de chaque espace que le pipeline a pour
cible de déploiement, le pipeline ne peut pas être créé. La personne qui lance la mise à niveau devient le propriétaire du référentiel dans la chaîne d'outils.
- L'interface Eclipse Orion {{site.data.keyword.webide}} dans la chaîne d'outils est séparée de l'interface {{site.data.keyword.webide}} qui est associée à votre
projet. Si vous utilisez l'interface {{site.data.keyword.webide}} et que certaines modifications ne sont pas validées, validez-les avant la mise à niveau.


## Mise à niveau d'un projet vers une chaîne d'outils
{: #project_to_toolchain}

**Important :** les projets sur hub.jazz.net et les chaînes d'outils sont hébergés dans la région sud des Etats-Unis. Si votre projet a été configuré pour déployer des
applications dans une autre région, il déploiera quand même les applications dans cette région après avoir été mis à niveau dans une chaîne d'outils.

Lorsque votre projet est prêt pour la mise à niveau, un message s'affiche sur la carte du projet et la page de présentation.

![Image d'une carte portant le libellé Ready To Upgrade](images/card-project-to-upgrade.png)

![Message Time to Upgrade](images/banner-ready-to-upgrade.png)

**Astuce :** Les projets prêts pour la mise à niveau se trouvent dans le menu de la page Mes projets :

![Image de l'élément de menu Projects To Upgrade](images/menu-projects-to-upgrade.png)

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

Avant de débuter le processus de mise à niveau, vous pouvez l'observer en action sur [YouTube![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://youtu.be/LSr2e3uvyLs){: new_window}.
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

      ![Choix de l'organisation Bluemix](images/bluemix-organization-chooser.png)

   Les chaînes d'outils étant gérées au niveau de l'organisation, veillez à sélectionner une organisation où les membres du projet qui ont besoin d'accéder à la chaîne d'outils existent déjà ou peuvent être ajoutés.

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

   ![Message concernant un projet en cours de mise à niveau vers une chaîne d'outils](images/project-being-upgraded-banner.png)

## Révision de votre projet
{: #revisit_projects}

Vous êtes prêt à utiliser votre nouvelle chaîne d'outils. Votre projet s'intitule maintenant "Upgraded" et un message de confirmation s'affiche sur la page de présentation.

![Image de la carte du projet avec le libellé Upgraded](images/card-upgraded-project.png)

![Projet mis à niveau](images/banner-upgraded.png)

Vous pouvez voir quels projets sont mis à niveau en sélectionnant **Upgraded Projects** dans le menu de la page Mes projets.

![Image de l'élément de menu Upgraded Projects](images/menu-upgraded-projects.png)

Pour annuler la mise à niveau, supprimez votre chaîne d'outils. Vous pouvez supprimer votre chaîne d'outils du menu **Plus d'actions** sur la page de présentation de
la chaîne d'outils :

![Image de l'action Supprimer dans le menu Plus d'actions](images/upgrade-tutorial-delete-toolchain.png)

Lorsque vous retournez à votre projet, le message de mise à niveau s'affiche à nouveau et vous pouvez renouveler la mise à niveau lorsque vous êtes prêt.

## Etapes suivantes
{: #upgrade_next_steps}

1. Confirmez que la mise à niveau est terminée en actualisant votre navigateur et en recherchant le message indiquant que votre projet "a été mis à niveau vers cette chaîne d'outils" sur
la page de présentation du projet :

   ![Message dans la bannière indiquant que le projet a été mis à niveau](images/banner-upgraded.png)

   **Remarque :** si le message indique "mettre à niveau maintenant", votre mise à niveau a échoué. Cliquez sur le lien **mettre à niveau maintenant**
pour faire une nouvelle tentative.

   ![Message dans la bannière indiquant que le projet est prêt à être mis à niveau](images/banner-ready-to-upgrade.png)

2. Accordez l'accès à la chaîne d'outils aux membres de votre équipe.
    - Chaque membre d'équipe doit disposer d'un compte {{site.data.keyword.Bluemix_notm}} valide. Les membres de l'équipe qui ne possèdent pas de comptes doivent [s'enregistrer![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/registration){:new_window}.
    - Accordez aux membres de l'organisation (org) un accès à la chaîne d'outils depuis la page Gérer de la chaîne d'outils. Pour en savoir plus sur le contrôle d'accès aux chaînes d'outils, voir [Gestion des accès ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Si un utilisateur n'est pas membre de l'organisation à laquelle appartient la chaîne d'outils, ajoutez-le à l'organisation depuis la page Gérer les organisations.
      Pour obtenir des informations complémentaires sur la gestions des organisations, voir [Gestion des organisations et des espaces ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Utilisez les outils de votre chaîne d'outils au lieu des outils de votre projet {{site.data.keyword.jazzhub_short}}. Par exemple, pour modifier le code à partir d'un navigateur, utilisez l'interface IDE Web de votre chaîne d'outils.

4. Si vous utilisez {{site.data.keyword.gitrepos}}, authentifiez-vous à l'aide d'un jeton d'accès personnel ou d'une clé SSH. Pour en savoir plus sur les clés SSH, voir [Création d'un jeton d'accès personnel ou d'une clé SSH pour l'authentification](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Pour s'authentifier depuis un client Git externe via https, procédez comme suit :
    1. Accédez à la page [Jetons d'accès ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} de vos paramètres utilisateurs {{site.data.keyword.gitrepos}}.
    2. Créez un jeton d'accès personnel utilisant **api** comme portée.
    3. Accédez à la page [Compte ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/account){:new_window} et recherchez votre nom d'utilisateur pour {{site.data.keyword.gitrepos}}. Votre nom d'utilisateur est répertorié dans la section "Changer le nom d'utilisateur" et apparaît dans la première partie de l'URL des référentiels personnels que vous créez.
    4. Pour vous authentifier avec {{site.data.keyword.gitrepos}} depuis un client Git externe via https, utilisez votre nom d'utilisateur et votre jeton d'accès personnel.
    5. Si vous souhaitez réutiliser le référentiel local de votre référentiel JazzHub Git, faites pointer le référentiel vers le nouveau référentiel dans {{site.data.keyword.gitrepos}}. Depuis un interpréteur de commande shell dans un terminal, accédez au répertoire dans lequel le référentiel JazzHub Git est cloné. Entrez la commande `git remote set-url` : `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        **Astuce :** pour vérifier quelles URL distantes sont définies sur quels noms distants, utilisez la commande `git remote -v`. Le nom distant
par défaut est `origin`. Si vous disposez d'une configuration plus avancée, le format de la commande est le suivant : `git remote set-url
<nom-distant-qui-utilise-le-référentiel-jazzhub>
https://git.ng.bluemix.net/<userid>/<nom-du-nouveau-référentiel>`

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

Si vous avez des questions ou des problèmes, accédez au [forum de support](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services). Dans votre
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

Pour plus d'informations sur IBM Track and Plan on Cloud, ou pour effectuer un achat en ligne, visitez le site Web [IBM Marketplace ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

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

Si vous utilisez Jazz SCM comme référentiel source et Delivery Pipeline pour générer votre code, le source de Jazz SCM est automatiquement déplacé vers un référentiel Git. Votre configuration Delivery Pipeline reste la même, mais consomme le source issu du référentiel Git à la place du source de Jazz SCM.

### Je dois créer une organisation pour mon projet qui va être mis à jour vers une chaîne d'outils. Je comprends que je dois ajouter une carte de crédit à mon compte avant de créer une organisation. Ma carte de crédit sera-t-elle débitée ?
{: #faq_charges}

En tant que [client de type Paiement à la carte ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, si vous utilisez un contexte d'exécution, un service ou un composant au-delà des allocations gratuites répertoriées dans le catalogue Bluemix, vous êtes facturé. Pour avoir une estimation de votre utilisation, reportez-vous à la  [fiche de prix ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Pour connaître la tarification en cours de Continuous Delivery, voir le [catalogue Bluemix ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Si vous êtes un employé IBM, les projets IBM internes peuvent être facturés aux départements, à la place d'une carte de crédit personnelle. Si vous avez besoin d'utiliser des ressources au-delà des allocations gratuites destinées aux employés IBM, créez un ticket de demande de service. 
