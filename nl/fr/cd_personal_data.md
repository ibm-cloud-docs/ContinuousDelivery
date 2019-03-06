---

copyright:
  years: 2018, 2019
lastupdated: "2019-2-20"

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

# Gestion des données personnelles dans Continuous Delivery
{: #cd_personal_data}

Vous pouvez modifier, exporter ou supprimer des données personnelles dans {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

Par données personnelles, on entend toute information qui concerne ou identifie une personne physique. Par exemple, les données personnelles peuvent être un nom, une adresse e-mail, un avatar, un jeton ou tout autre identifiant utilisé avec {{site.data.keyword.contdelivery_short}}. Les composants {{site.data.keyword.contdelivery_short}} suivants contiennent des données personnelles :

 * Eclipse Orion {{site.data.keyword.webide}}
 * {{site.data.keyword.gitrepos}}
 * Les pipelines {{site.data.keyword.contdelivery_short}}
 * Les chaînes d'outils et intégrations d'outils
 * [GitHub Enterprise sur IBM Cloud ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/ghededicated?topic=ghededicated-ghe_personal_data){: new_window}
 * [{{site.data.keyword.DRA_full}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/DevOpsInsights?topic=DevOpsInsights-insights_personal_data){: new_window}
 
IBM ne gère pas les données dans le service {{site.data.keyword.contdelivery_short}}. Avant de quitter le service {{site.data.keyword.contdelivery_short}} hébergé dans {{site.data.keyword.Bluemix_notm}} Public, vous devez supprimer vos propres données.
{: important}

{{site.data.keyword.contdelivery_short}} fournit les droits nécessaires pour gérer les données dans un groupe de ressources ou une organisation Cloud Foundry. Votre entreprise peut avoir des règles qui limitent ces droits. Si vous ne disposez pas des droits nécessaires, contactez l'administrateur pour votre compte {{site.data.keyword.Bluemix_notm}}.

Pour gérer vos données personnelles, vous devez comprendre comment fonctionnent les comptes IBM Cloud, comment ils sont utilisés et connaître les droits d'accès associés.
 
## Comptes et droits d'accès
{: #accounts_access_rights}

Pour travailler dans IBM Cloud, vous devez vous connecter avec un nom d'utilisateur et un mot de passe. Lorsque vous vous connectez, IBM Cloud associe au moins un compte IBM Cloud à vos données d'identification d'utilisateur. Lorsque vous créez des ressources telles que des organisations Cloud Foundry, des groupes de ressources, des chaînes d'outils et des objets {{site.data.keyword.contdelivery_short}}, elles sont associées à un compte IBM Cloud.

La structure de connexion d'IBM Cloud offre la possibilité de travailler dans différents comptes. L'interface utilisateur d'IBM Cloud vous permet de passer d'un compte à un autre. Lorsque vous vous connectez, l'un des types de comptes suivants peut être associé à vos données d'identification d'utilisateur : 

 * Compte personnel
 * Compte d'entreprise
 * Compte d'entreprise individuel

###Comptes personnels

Généralement, chaque utilisateur possède son propre compte, qui est son compte personnel. Vous pouvez facilement identifier votre compte personnel car il contient généralement votre nom, par exemple : *Compte de John Smith*. 

Vous avez tous les droits sur tous les objets qui sont créés dans votre compte personnel. Vous pouvez inviter d'autres utilisateurs à se joindre à votre compte, leur affecter des droits sur des objets que vous créez et leur affecter des droits pour créer des objets dans votre compte. Cela signifie que les données personnelles d'autres utilisateurs peuvent être dans votre compte et que vos données personnelles peuvent être dans les comptes d'autres utilisateurs. 

Si vous disposez d'un droit pour créer un objet dans un compte, vous avez également le droit de le modifier et de le supprimer, quel que soit le compte dans lequel l'objet est stocké. Lorsque deux utilisateurs collaborent, ils partagent souvent un compte personnel.

###Comptes d'entreprise

Un compte d'entreprise est configuré par votre entreprise. Généralement, vous êtes ajouté automatiquement au compte, au lieu d'être invité. Les comptes d'entreprise offrent aux utilisateurs un lieu de travail, de communication, de partage des ressources et de la facturation. Cependant, il ne s'agit que d'une convention. En réalité, un compte d'entreprise n'est pas différent d'un compte personnel. Les objets qui sont créés dans un compte d'entreprise sont associés au compte et les utilisateurs peuvent être invités au compte.

Les équipes de personnes qui travaillent pour une entreprise collaborent souvent au moyen d'un compte d'entreprise.

###Comptes d'entreprise individuels

Lorsque vous travaillez pour une société, le travail contenu dans votre compte peut appartenir légalement à la société. Beaucoup d'utilisateurs travaillant pour une entreprise possèdent un compte d'entreprise individuel. Si vous vous connectez à votre compte en utilisant des données d'identification qui contiennent le nom de votre société et possédez également une sorte de compte personnel, le travail contenu dans votre compte personnel pourrait appartenir à la société.

Un compte d'entreprise individuel n'est pas différent d'un autre compte. Vous pouvez inviter des utilisateurs à un compte d'entreprise individuel et les objets qui sont créés dans un compte d'entreprise individuel appartiennent au compte.

Si vous travaillez pour une société qui est propriétaire de votre travail, un compte personnel qui contient habituellement votre nom est considéré comme un compte d'entreprise individuel. 

## Modification, exportation et suppression des données personnelles
{: #managing_personal_data}

Quel que soit le type de compte IBM Cloud utilisé, si vous avez des droits sur les objets du compte, vous pouvez les modifier, les exporter et les supprimer. Avant d'apporter des modifications, coordonnez-vous avec les autres utilisateurs pour vous assurer que vous ne modifiez ou supprimez pas inutilement des données.

Avant de supprimer des données d'un compte, déterminez s'il s'agit d'un compte personnel ou d'un compte d'entreprise individuel.

###Compte personnel

Si vous possédez un compte personnel, vous pouvez apporter des modifications et supprimer vos données. Si vous partagez votre compte avec un autre utilisateur, vous possédez les données, mais vous pourriez vouloir les contacter au sujet du travail partagé. 

Si vous ne pouvez pas vous connecter à votre compte IBM Cloud, [contactez le support IBM![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/support){:new_window}
 
###Compte d'entreprise individuel

Si vous possédez un compte d'entreprise individuel, vous devez coordonner tout changement avec votre entreprise et les autres membres de votre équipe. Vous pouvez supprimer vos données personnelles, qu'elles soient stockées dans un compte d'entreprise ou dans un compte d'entreprise individuel. Assurez-vous de ne pas supprimer les travaux que vous avez partagés avec d'autres utilisateurs.

Avant de commencer à gérer vos données personnelles pour les composants {{site.data.keyword.contdelivery_short}}, assurez-vous que vous travaillez dans votre compte IBM Cloud. Pour afficher le compte IBM Cloud dans lequel vous travaillez actuellement, cliquez sur votre avatar de profil dans la barre de menu. 

Si vous ne pouvez pas vous connecter à votre compte IBM Cloud, contactez votre société et travaillez avec elle pour supprimer vos données personnelles.

Si vous souhaitez supprimer toutes vos données personnelles de {{site.data.keyword.contdelivery_short}}, l'ordre dans lequel vous supprimez ces données est important. Supprimez d'abord tous vos espaces de travail {{site.data.keyword.webide}}. Supprimez ensuite vos données {{site.data.keyword.gitrepos}}, puis votre compte {{site.data.keyword.gitrepos}}. Enfin, supprimez vos pipelines de distribution, vos intégrations d'outils et vos chaînes d'outils.
{: tip}

## Exportation et suppression des données de l'interface Web IDE
{: #managing_web_ide_data}

L'interface {{site.data.keyword.webide}} fournit un espace de travail personnel dans le cloud. Vous pouvez utiliser l'interface {{site.data.keyword.webide}} pour cloner les référentiels Git et éditer les fichiers. Vous êtes propriétaire de votre espace de travail {{site.data.keyword.webide}} ; il n'est pas partagé avec un autre compte.

Avant de supprimer vos données dans {{site.data.keyword.webide}}, pensez à exporter votre travail. Une fois supprimés, vos espaces de travail seront retirés de {{site.data.keyword.contdelivery_short}} et tous les fichiers seront supprimés.
{: important}

###Exportation d'un espace de travail de l'interface Web IDE

Pour exporter un espace de travail de l'interface {{site.data.keyword.webide}} :

1. Sélectionnez **Fichier > Exporter > Zip**.
1. Répétez l'opération pour chaque espace de travail devant être exporté.

###Suppression de vos espaces de travail de l'interface Web IDE

Pour supprimer vos espaces de travail de l'interface {{site.data.keyword.webide}}, y compris l'ensemble de vos données personnelles :

1. A partir d'une chaîne d'outils, accédez à l'interface {{site.data.keyword.webide}}.
1. Cliquez sur l'icône **Paramètres** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Icône Paramètres"> dans la barre latérale de navigation de gauche.
1. Cliquez sur **PROFIL UTILISATEUR**.
1. Cliquez sur **Supprimer** pour supprimer toutes les données de l'interface {{site.data.keyword.webide}}.

L'interface {{site.data.keyword.webide}} utilise un mécanisme de connexion unique. La première fois que vous accédez à cet outil d'intégration, un compte {{site.data.keyword.webide}} correspondant (masqué) est créé pour votre compte IBM Cloud. Après avoir supprimé tous les espaces de travail, n'accédez pas à l'interface {{site.data.keyword.webide}}. Si vous accédez à nouveau à l'interface {{site.data.keyword.webide}}, un nouveau compte sera automatiquement créé et vous devrez le supprimer.
{: important}

## Modification, exportation et suppression des données des Git Repos and Issue Tracking
{: #managing_grit_data}

{{site.data.keyword.gitrepos}} fournit un service Git hébergé dans le cloud. Un mécanisme de connexion unique est utilisé pour associer votre compte IBM Cloud à un compte Git. Un nom complet et un nom abrégé sont créés pour vous dans votre compte Git. Les autres utilisateurs peuvent utiliser votre nom abrégé pour se référer à vous dans un commentaire dans un problème Git. Vous pouvez personnaliser votre compte Git et ajouter des données personnelles comme une description de vous ou une image. 

{{site.data.keyword.gitrepos}} fournit un environnement de codage social puissant mais complexe dans lequel les utilisateurs contribuent à différents projets et dans lequel les objets sont partagés. Cet environnement peut rendre difficile la localisation et la suppression de vos données personnelles.

Les profils et paramètres de votre compte, les projets personnels, les groupes et les fragments sont associés à votre compte Git. Si vous supprimez votre compte Git, ces objets sont supprimés. Pour supprimer des données personnelles dans un autre projet, accédez au projet puis modifiez-le afin de supprimer vos données personnelles ou supprimez le projet entier. Assurez-vous de vous coordonner avec les autres membres de votre équipe avant de supprimer des projets partagés.

Avant de supprimer votre compte Git, supprimez vos données personnelles des autres projets. Après avoir supprimé votre compte Git, il peut être difficile ou impossible de trouver tous les projets auxquels vous avez contribué.
{: tip}

###Projets personnels et partagés

Vous pouvez inviter d'autres utilisateurs à collaborer à des projets. Les projets Git que vous créez à l'intérieur de votre compte sont appelés des projets personnels. Vous pouvez également créer des groupes Git dans lesquels des projets peuvent appartenir à plusieurs propriétaires de Git. Vous pouvez créer de nouveaux projets pour le groupe ou transférer la propriété de projets personnels au groupe. Un groupe Git est souvent utilisé pour représenter un compte d'entreprise IBM Cloud pour indiquer que les projets appartiennent à la société.

###Exportation d'un projet dans Git Repos and Issue Tracking

Avant de supprimer un projet dans {{site.data.keyword.gitrepos}}, vous pouvez exporter le projet afin de l'archiver. 

1. Cliquez sur l'icône **Paramètres** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Icône Paramètres"> dans la barre latérale de navigation de gauche.
1. Cliquez sur **Général**.
1. Cliquez sur **Développer** pour développer la section Exporter le projet.
1. Cliquez sur **Exporter le projet**.

Une fois le projet archivé, vous pouvez l'importer dans une autre instance GitLab. 

###Suppression de votre compte Git Repos and Issue Tracking

Vous pouvez supprimer votre compte {{site.data.keyword.gitrepos}} et tout ce qui appartient à ce compte.

1. Sur le tableau de bord Paramètres utilisateur de {{site.data.keyword.gitrepos}}, sur la [page Compte![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, dans la section Supprimer le compte, cliquez sur **Supprimer le compte**.
1. Tous les projets Git, y compris les référentiels et les problèmes sont supprimés. Vous êtes également supprimé de tous les groupes {{site.data.keyword.gitrepos}} auquel vous appartenez.

Une fois votre compte supprimé, certains contenus sont conservés. Ces contenus sont affectés à un utilisateur fantôme à l'échelle du système. Pour en savoir plus sur la suppression d'un compte {{site.data.keyword.gitrepos}}, voir [Suppression d'un compte utilisateur ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/profile/account/delete_account#associated-records){:new_window}.
{: tip}

{{site.data.keyword.gitrepos}} utilise un mécanisme de connexion unique qui crée automatiquement un compte Git correspondant pour votre compte IBM Cloud la première fois que vous accédez à l'intégration d'outils. Après avoir supprimé votre compte, n'accédez pas à {{site.data.keyword.gitrepos}}. Si vous accédez à {{site.data.keyword.gitrepos}} à nouveau, un nouveau compte sera automatiquement créé et vous devrez le supprimer.
{: important}

## Modification, exportation et suppression des données des pipelines Continuous Delivery
{: #managing_pipeline_data}

Les pipelines {{site.data.keyword.contdelivery_short}} exécutent des scripts pour générer, tester et déployer votre application dans IBM Cloud. Pour ceci, les pipelines fournissent des étapes, des travaux, des variables d'environnement et d'autres objets pouvant contenir des données personnelles. Vous pouvez supprimer ces objets individuellement ou supprimer un pipeline entier.

Assurez-vous de vous coordonner avec les autres membres de votre équipe avant de supprimer des pipelines ou des objets partagés. La suppression d'une étape peut entraîner la défaillance d'un pipeline.

Un pipeline ne peut pas exister en dehors d'une chaîne d'outils. Si vous supprimez une chaîne d'outils, tous les pipelines associés à la chaîne d'outils seront également supprimés. Si vous prévoyez de supprimer une chaîne d'outils entière, vous n'avez pas besoin de supprimer chaque pipeline individuellement. Passez plutôt à la section "Modification et suppression de chaînes d'outils et d'intégrations d'outil" et suivez les indications pour supprimer une chaîne d'outils.
{: important}

Les étapes d'un pipeline peuvent inclure des données personnelles comme des données d'identification sous la forme de propriétés d'environnement et une définition de pipeline indiquant l'état actuel du pipeline. Les étapes peuvent également inclure des scripts dans les tâches que vous souhaitez modifier ou supprimer, ainsi que des artefacts et des journaux pour les dernières exécutions de pipeline à exporter. Utilisez les actions Configurer l'étape ou Supprimer l'étape pour modifier ou supprimer une étape. Utilisez l'action Télécharger pour exporter des artefacts ou des journaux à partir d'une étape.

  ![Menu Etapes](images/pipeline_stages.png)

###Modification d'une étape de pipeline

Pour modifier une étape d'un pipeline :

1. Sur la page Pipeline, cliquez sur l'icône **Paramètres**.
1. Cliquez sur **Configurer l'étape**.
1. Sur l'onglet **PROPRIETES D'ENVIRONNEMENT**, éditez ou supprimez des propriétés.
1. Modifiez un script de travail dans une étape du pipeline. Sélectionnez le travail et modifiez les valeurs appartenant à la configuration de génération, de déploiement ou de test.
   
   ![Modifier un script de travail](images/job_script.png)
  
1. Supprimez un travail de l'étape du pipeline. Sur l'onglet **TRAVAUX**, sélectionnez le travail que vous souhaitez supprimer puis cliquez sur **Retirer**.
 
###Exportation d'une étape de pipeline

Pour exporter la définition d'une étape de pipeline, ajoutez `/yaml` à l'URL du pipeline :

`http(s)://<DevOps Services domain>/pipeline/user/project/yaml`


Pour exporter des artefacts et des journaux pour une étape de pipeline :

1. Sur la page Pipeline, cliquez sur **Afficher les journaux et l'historique**.
1. Cliquez sur le numéro de version pour lequel vous souhaitez exporter des artefacts et des journaux.
1. Cliquez sur **Télécharger** > **Artefacts** pour exporter les artefacts pour la version sélectionnée.
1. Cliquez sur **Télécharger** > **Journaux** pour exporter les journaux pour la version sélectionnée.  

###Suppression d'une étape de pipeline

Pour supprimer une étape d'un pipeline :

1. Sur la page Pipeline, cliquez sur l'icône **Paramètres**.
1. Cliquez sur **Supprimer l'étape**.

## Modification et suppression des chaînes d'outils et des intégrations d'outil
{: #managing_toolchains}

En utilisant des chaînes d'outils, les équipes peuvent collaborer et partager différentes intégrations d'outils. 

Il est recommandé de configurer toutes les intégrations {{site.data.keyword.contdelivery_short}} en utilisant des données associées à votre équipe ou à votre entreprise, plutôt que des données qui vous sont associées. Cependant, dans certains cas, vos données personnelles peuvent être utilisées par inadvertance. Dans de tels cas, vous devez identifier toutes les données que vous possédez et les supprimer.

Lorsqu'une intégration d'outil est créée, {{site.data.keyword.contdelivery_short}} ne peut pas enregistrer l'origine de toutes les données. Par exemple, un autre membre de l'équipe peut créer un outil d'intégration pour vous en utilisant les données personnelles que vous fournissez dans un courrier électronique. Vous devez comprendre quelles données vous possédez et vous assurer qu'elles sont supprimées.

Coordonnez-vous avec les autres membres de votre équipe avant de supprimer des chaînes d'outils ou des intégrations d'outils partagées.

###Modification et suppression d'intégrations d'outils

Lorsque vous créez une intégration d'outil, vous devez fournir des informations d'identification et d'autres informations de compte relatives à l'intégration. Si vous avez utilisé vos informations d'identification et informations de compte personnelles, remplacez ces informations par des valeurs différentes ou supprimez l'intégration d'outil.

Pour modifier une intégration d'outil :

1. Sur la carte de l'outil, cliquez sur le menu pour accéder aux options de configuration.

  ![Menu Configuration d'outils](images/toolchain_tile_menu.png)

1. Lorsque vous avez terminé la mise à jour des paramètres, cliquez sur **Sauvegarder l'intégration**.

Pour supprimer une intégration d'outil :

1. Pour supprimer une intégration d'outil de votre chaîne d'outils, cliquez sur **Supprimer**.
1. Confirmez en cliquant sur **Supprimer**.

###Suppression des chaînes d'outils

Lorsque vous supprimez une chaîne d'outils, la suppression est irréversible.

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils à supprimer. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Distribution continue, cliquer sur **Afficher la chaîne d'outils**.
1. Cliquez sur le menu **Plus d'actions**, qui se trouve à côté du menu **Afficher l'appli**.
1. Cliquez sur **Supprimer**. La suppression d'une chaîne d'outils supprime toutes ses intégrations d'outils, y compris les pipelines et donc éventuellement les ressources gérées par ces intégrations.
1. Confirmez la suppression en entrant le nom de la chaîne d'outils et en cliquant sur **Supprimer**. 

Lorsque vous supprimez une chaîne d'outils, les référentiels {{site.data.keyword.gitrepos}} associés ne sont pas supprimés. Les utilisateurs ayant accès à ces référentiels peuvent disposer de copies des données s'ils ont exécuté une commande `git clone` ou créé un espace de travail {{site.data.keyword.webide}}. Pour vous assurer que toutes les données sont supprimées, vous devez demander à ces utilisateurs de supprimer leurs copies des données.
{: tip}

###Suppression de toutes les chaînes d'outils

Vous ne pouvez pas supprimer toutes les chaînes d'outils d'un groupe de ressources ou d'une organisation en même temps. Vous devez supprimer les chaînes d'outils une par une.

Les chaînes d'outils sont délimitées par région IBM Cloud, groupe de ressources et organisation Cloud Foundry. Assurez-vous de sélectionner chaque région et groupe de ressources ou organisation au sein de la région pour supprimer toutes les chaînes d'outils que vous avez créées.
{: tip}
