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

# Utilisation de chaînes d'outils
{: #toolchains-using}

Des chaînes d'outils ouvertes sont disponibles dans les environnements {{site.data.keyword.Bluemix}} Public et Dedicated. Vous pouvez utiliser une chaîne d'outils pour améliorer la productivité de votre travail quotidien de développement, de déploiement et de vos opérations. Après avoir configuré une chaîne d'outils, vous pouvez ajouter, supprimer ou configurer des intégrations d'outils et gérer l'accès à la chaîne d'outils.
{: shortdesc}

Vous pouvez gérer des chaînes d'outils dans la région publique du Sud des Etats-Unis en utilisant des groupes de ressources ou des organisations (orgs) Cloud Foundry. Le contrôle d'accès et la gestion des utilisateurs autorisés fonctionnent différemment pour les chaînes d'outils, selon qu'elles sont contenues dans un groupe de ressources ou une organisation Cloud Foundry. {: tip}

## Configuration d'une intégration d'outils
{: #configuring_a_tool_integration}

Si vous avez différé la configuration d'une intégration d'outils lors de la création d'une chaîne d'outils, un bouton **Configurer** s'affiche sur sa carte. Si vous avez configuré une intégration d'outils à la création d'une chaîne d'outils, vous pouvez mettre à jour les paramètres de configuration.

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page Vue d'ensemble correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Si vous devez configurer une intégration d'outils pour la première fois, depuis sa carte, cliquez sur **Configurer**.

  ![Bouton Configurer](images/toolchain_tile_configure.png)

 Lorsque vous avez terminé la configuration de l'intégration d'outils, cliquez sur **Sauvegarder l'intégration**.

1. Si vous devez mettre à jour la configuration d'une intégration d'outils, depuis sa carte, cliquez sur le menu pour accéder aux options de configuration.

  ![Menu Configuration](images/toolchain_tile_menu.png)

 Quelques intégrations d'outils sont préconfigurées et ne requièrent aucun paramètre de configuration. Vous pouvez mettre à jour les paramètres de configuration uniquement pour les intégrations d'outils que vous avez configurées.
 {: tip}

 Lorsque vous avez terminé la mise à jour des paramètres, cliquez sur **Sauvegarder l'intégration**. Pour plus d'informations sur la configuration des intégrations d'outils spécifiques, voir [Configuration d'intégrations d'outils](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.

## Ajout d'une intégration d'outils
{: #adding_a_tool_integration}

Vous pouvez ajouter et configurer des intégrations d'outils pour votre chaîne d'outils. Les intégrations d'outils disponibles varient selon que vous utilisez {{site.data.keyword.Bluemix_notm}} Public ou {{site.data.keyword.Bluemix_notm}} Dedicated.

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page Vue d'ensemble correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Pour afficher la liste des intégrations d'outils à ajouter, cliquez sur **Ajouter un outil**.
1. Cliquez sur une intégration d'outils à ajouter.
1. Entrez les informations requises pour configurer l'intégration d'outils.
1. Cliquez sur **Créer une intégration** pour ajouter l'intégration d'outils à votre chaîne d'outils.

## Suppression d'une intégration d'outils
{: #deleting_a_tool_integration}

Si vous supprimez une intégration d'outils de votre chaîne d'outils, la suppression est irréversible.

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page Vue d'ensemble correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Sur la carte de l'intégration d'outil à supprimer, cliquez sur le menu pour accéder aux options de configuration.
1. Pour supprimer l'intégration d'outils de votre chaîne d'outils, cliquez sur **Supprimer**.
1. Confirmez en cliquant sur **Supprimer**.  

## Gestion de l'accès aux chaînes d'outils dans les groupes de ressources 
{: #managing_access_resource_groups}

Vous pouvez utiliser le service Identity and Access Management (IAM) pour gérer l'accès des utilisateurs aux chaînes d'outils. Pour plus d'informations sur la gestion du contrôle d'accès avec IAM, voir [Gestion de l'accès utilisateur aux chaînes d'outils avec Identity and Access Management](/docs/services/ContinuousDelivery/toolchains_iam_security.html){: new_window}.  

Seuls les utilisateurs faisant partie de la liste des utilisateurs autorisés pour l'instance sélectionnée de {{site.data.keyword.contdelivery_short}} peuvent utiliser les fonctionnalités Delivery Pipeline, Eclipse Orion {{site.data.keyword.webide}} et {{site.data.keyword.gitrepos}} des chaînes d'outils {{site.data.keyword.contdelivery_short}}. Vous pouvez gérer les autorisations d'utilisation pour un utilisateur autorisé à partir de l'onglet Gérer de l'instance sélectionnée de {{site.data.keyword.contdelivery_short}}, dans le groupe de ressources spécifié. 

Pour accéder aux fonctionnalités clés de {{site.data.keyword.contdelivery_short}} dans une chaîne d'outils, telle que Delivery Pipeline, un utilisateur doit avoir accès à la chaîne d'outils dans IAM et il doit également faire partie de la liste des utilisateurs autorisés de l'instance {{site.data.keyword.contdelivery_short}}. {: tip}

L'autorisation d'utilisation pour un utilisateur autorisé s'applique à toutes les chaînes d'outils contenues dans le même groupe de ressources que l'instance de {{site.data.keyword.contdelivery_short}}.
{: tip}


## Gestion de l'accès aux chaînes d'outils dans les organisations Cloud Foundry 
{: #managing_access_orgs}

Vous pouvez accorder l'accès à une chaîne d'outils à des utilisateurs en les ajoutant à la fois à l'organisation à laquelle la chaîne d'outils est associée et à la liste de contrôle d'accès de la chaîne d'outils. Chaque chaîne d'outils est associée à une organisation spécifique, et tout membre de cette organisation peut être ajouté à la liste de contrôle d'accès de l'une des chaînes d'outils associées. L'organisation au sein de laquelle vous travaillez actuellement s'affiche dans la barre de menus. Pour accéder à un ensemble différent de chaînes d'outils, changez d'organisation.

Vous devez ajouter des utilisateurs à l'organisation de la chaîne d'outils dans la région où la chaîne d'outils est hébergée. Si la chaîne d'outils est configurée pour déployer des applications dans une autre région, elle déploiera quand même les applications dans cette région.
{: tip}

Si vous utilisez {{site.data.keyword.Bluemix_notm}} Dedicated pour {{site.data.keyword.ghe_short}}, lorsque vous ajoutez des utilisateurs à votre organisation et vos espaces {{site.data.keyword.Bluemix_notm}}, ces utilisateurs peuvent se connecter à {{site.data.keyword.ghe_short}} à l'aide de leurs ID et mot de passe {{site.data.keyword.Bluemix_notm}}. Lorsque les utilisateurs se connectent, les comptes correspondants sont créés. Lorsque vous ajoutez des utilisateurs à votre organisation et vos espaces {{site.data.keyword.Bluemix_notm}}, ils ne sont pas automatiquement ajoutés au référentiel {{site.data.keyword.ghe_short}}. Une personne dotée de privilèges d'administrateur pour le référentiel doit les ajouter. Pour
plus d'informations, voir [Utilisation de Dedicated GitHub Enterprise](/docs/services/ghededicated/index.html){: new_window}. Si vous utilisez votre propre version gérée de {{site.data.keyword.ghe_short}}, suivez vos procédures internes.

###Conseils pour la gestion de l'accès à une chaîne d'outils

* Pour gérer l'accès à une chaîne d'outils, dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, cliquez sur la chaîne d'outils à gérer, puis cliquez sur **Gérer**. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**, puis sur **Gérer**.

* Pour accorder l'accès à tous les membres de l'organisation de la chaîne d'outils, cliquez sur **Ajouter une organisation**. Tous les membres de cette organisation peuvent afficher la chaîne d'outils.

* Vous pouvez accorder des privilèges d'administrateur à une organisation ou un utilisateur. Les administrateurs peuvent modifier et supprimer la chaîne d'outils. Pour accorder des privilèges d'administrateur, cochez la case **ADMIN** pour l'organisation ou l'utilisateur.

* Si vous cochez la case **ADMIN** pour une organisation, tous les membres de cette dernière deviennent des administrateurs. Si vous ajoutez des membres à l'organisation après lui avoir accordé des privilèges d'administrateur, ces membres bénéficient du même accès que le reste de l'organisation.

* Pour accorder un accès à un utilisateur qui est membre de l'organisation de la chaîne d'outils, saisissez l'ID de l'utilisateur et cliquez sur **Ajouter un utilisateur**. L'utilisateur peut visualiser la chaîne d'outils.

* Pour accorder un accès à un utilisateur qui n'est pas membre de l'organisation de la chaîne d'outils, procédez comme suit :

   a. Dans la barre de menus, cliquez sur **Gérer > Sécurité > Identité et accès**.

   b. Sur la ligne de l'utilisateur auquel vous voulez affecter un accès, sélectionnez le menu **Actions**, puis cliquez sur **Affecter un accès**.

   c. Sélectionnez **Affecter l'accès à l'aide de Cloud Foundry**.

   d. Sélectionnez **Affecter une organisation**.

   e. Affectez l'accès utilisateur :

     * Sélectionnez l'organisation à laquelle vous souhaitez ajouter l'utilisateur.

     * Affectez un rôle d'organisation.

     * Sélectionnez une région.

     * Sélectionnez un espace.

     * Affectez un rôle pour l'espace sélectionné dans l'organisation.

     Par défaut, les responsables de l'organisation disposent de privilèges d'administrateur complets pour toutes les chaînes d'outils qui sont associées à l'organisation. Pour accorder des privilèges d'administrateur complets à l'utilisateur, sélectionnez le rôle **Responsable**. Les rôles Responsable de la facturation et Auditeur n'ont pas d'impact sur l'accès à la chaîne d'outils. Vous pouvez changer les rôles
ultérieurement dans la page Répertoire d'équipe. Pour en savoir plus, voir [Rôles de Cloud Foundry](/docs/iam/cfaccess.html#cfaccess){: new_window}.
     {: tip}

   Une fois que l'utilisateur est membre de l'organisation, retournez à la page Gérer de la chaîne d'outils et ajoutez l'utilisateur à la chaîne d'outils.  


## Suppression d'une chaîne d'outils
{: #deleting_a_toolchain}

Vous pouvez supprimer une chaîne d'outils et spécifier les intégrations d'outils associées à supprimer. Lorsque vous supprimez une chaîne d'outils, la suppression est irréversible.

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils à supprimer. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**.
1. Cliquez sur le menu **Plus d'actions**, qui se trouve à côté du menu **Afficher l'appli**.
1. Cliquez sur **Supprimer**. La suppression d'une chaîne d'outils supprime toutes ses intégrations d'outils, et donc éventuellement les ressources gérées par ces intégrations.
1. Confirmez la suppression en entrant le nom de la chaîne d'outils et en cliquant sur **Supprimer**.  

 Lorsque vous supprimez une intégration d'outils GitHub, {{site.data.keyword.ghe_short}} ou {{site.data.keyword.gitrepos}}, le référentiel associé n'est pas supprimé de GitHub, de {{site.data.keyword.ghe_short}} ou de {{site.data.keyword.gitrepos}}. Vous devez le supprimer manuellement.
 {: tip}

##Suivre un tutoriel : Utilisation de chaînes d'outils
{: #toolchain-tutorial}

Consultez les tutoriels suivants sur [IBM&reg; Cloud Garage Method ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage){:new_window} :

  * [Création et utilisation de votre propre chaîne d'outils à l'aide de la chaîne d'outils "Développer une application Cloud Foundry"![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Ajout d'une chaîne d'outils à une application ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.

  * [Utilisation de la chaîne d'outils "Développer et tester des microservices sur Cloud Foundry" ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
