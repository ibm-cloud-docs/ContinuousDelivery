---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-25"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Utilisations des plans et limitations
{: #limitations_usage}

L'utilisation d'{{site.data.keyword.contdelivery_full}} est limitée à la génération, au déploiement, au test et aux opérations en cours des applications sur la plateforme {{site.data.keyword.Bluemix_notm}} ou toute autre plateforme ou infrastructure en tant que service compatible.

## Utilisateurs autorisés
{: #authorized_users}

Les plans de service de {{site.data.keyword.contdelivery_short}} sont définis et tarifés en fonction du nombre d'utilisateurs autorisés d'une instance de service. Toute personne qui contribue à un effort doit être considérée comme un utilisateur autorisé, y compris :

 * Les utilisateurs qui interagissent avec des problèmes, des tableaux de problèmes, du code source ou d'autres artefacts dans un référentiel {{site.data.keyword.gitrepos}}.
 * Les utilisateurs qui manipulent, déclenchent (soit directement dans l'interface utilisateur, soit indirectement en s'engageant dans un référentiel), ou visualisent l'état d'un pipeline de distribution.
 * Les utilisateurs qui interagissent avec Eclipse Orion {{site.data.keyword.webide}}.

### Comment les utilisateurs sont-ils comptabilisés pour les instances de {{site.data.keyword.contdelivery_short}} dans les organisations ?

Les utilisateurs autorisés sont comptabilisés en consultant tous les utilisateurs dans l'organisation Cloud contenus par le service {{site.data.keyword.contdelivery_short}}.

Pour afficher la liste des utilisateurs de votre organisation dans un environnement {{site.data.keyword.Bluemix_notm}} Public, cliquez sur **Gérer > Compte** dans la barre de menus. Ensuite, cliquez sur **Organisations Cloud Foundry**.

Pour afficher la liste des utilisateurs de votre organisation dans un environnement {{site.data.keyword.Bluemix_notm}} Dedicated, cliquez sur **Compte > Gérer les organisations** dans la barre de menus.

Vous pouvez également afficher toutes les instances du service {{site.data.keyword.contdelivery_short}} dans votre compte ainsi que le nombre d'utilisateurs répertoriés dans chaque instance, dans un environnement {{site.data.keyword.Bluemix_notm}} Public.

1. Dans la barre de menus, cliquez sur **Gérer > Facturation et utilisation**.
2. Cliquez sur **Utilisation**.
3. Dans la section **Services**, cliquez sur **Afficher les plans** pour le service {{site.data.keyword.contdelivery_short}}.
4. Cliquez sur **Afficher les détails** pour le plan sur lequel vous souhaitez afficher des informations.
5. Cliquez sur **Afficher les détails de l'instance** pour l'instance de {{site.data.keyword.contdelivery_short}} pour laquelle vous souhaitez afficher des informations d'utilisation.

Pour afficher toutes les instances du service {{site.data.keyword.contdelivery_short}} dans votre compte ainsi que le nombre d'utilisateurs répertoriés dans chaque instance, dans un environnement {{site.data.keyword.Bluemix_notm}} Dedicated :

1. Dans la barre de menus, cliquez sur **Compte > Gérer les organisations**.
2. Cliquez sur **Tableau de bord de l'utilisation**.

### Comment les utilisateurs sont-ils comptabilisés pour les instances de {{site.data.keyword.contdelivery_short}} dans les groupes de ressources ?

Les utilisateurs autorisés sont comptabilisés en consultant la liste des utilisateurs de l'onglet Gérer de l'instance du service {{site.data.keyword.contdelivery_short}}.

Pour afficher la liste des utilisateurs autorisés, ouvrez le tableau de bord de l'instance de service et cliquez sur l'onglet Gérer.

Vous pouvez également afficher toutes les instances du service {{site.data.keyword.contdelivery_short}} dans votre compte ainsi que le nombre d'utilisateurs répertoriés dans chaque instance.

1. Dans la barre de menus, cliquez sur **Gérer > Facturation et utilisation**.
2. Cliquez sur **Utilisation**.
3. Dans la section **Services**, cliquez sur **Afficher les plans** pour le service {{site.data.keyword.contdelivery_short}}.
4. Cliquez sur **Afficher les détails** pour le plan sur lequel vous souhaitez afficher des informations.
5. Cliquez sur **Afficher les détails de l'instance** pour le groupe de ressources pour lequel vous souhaitez afficher des informations d'utilisation.

### Que se passe-t-il lorsque vous dépassez les limites de votre plan de service ?

Certains plans de service peuvent avoir d'autres limitations, telles que le nombre de travaux Delivery Pipeline pouvant être exécutés ou la consommation de mémoire. Pour en savoir plus, consultez la description du plan dans le catalogue. Si l'une des limitations du plan est dépassée dans une période de facturation, le service peut être suspendu. Par exemple, les travaux de Delivery Pipeline peuvent ne pas s'exécuter durant le restant de la période de facturation.

## Utilisation de Delivery Pipeline
{: #pipeline_usage}

Les comportements acceptables en matière d'utilisation sont les suivants, sans s'y limiter :

* La compilation et l'assemblage d'artefacts pour les langages de programmation pris en charge
* Le déploiement automatisé d'artefacts d'application, de configurations et de ressources ou services pertinents
* Le test, la validation et tout autre comportement généré par un événement de développement déclenché dans le cadre d'un processus de développement

Les comportements non autorisés en matière d'utilisation sont les suivants, sans s'y limiter :

* L'utilisation de travaux ou d'agents de pipeline pour des comportements de calcul généraux, tels que le minage de Bitcoin, les attaques par refus de service distribuées et un comportement malveillant ou offensant envers d'autres clients ou utilisateurs de la plateforme IBM Cloud ou des utilisateurs généraux d'Internet
* L'utilisation dans le processus de développement normal de sites ou de services faisant la promotion d'un discours haineux ou d'autres activités violant les Principes de conduite dans les affaires d'IBM
* L'utilisation d'un comportement généré par un événement pour une intrusion malveillante ou des attaques contre {{site.data.keyword.Bluemix_notm}} ou d'autres sites

A la discrétion d'IBM, les utilisateurs qui violent les comportements d'utilisation acceptables des services {{site.data.keyword.contdelivery_short}} ou les [Principes de conduite dans les affaires d'IBM ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} peuvent être désactivés sans préavis. A la discrétion d'IBM, certains services peuvent être restaurés si les utilisateurs corrigent leurs comportements d'utilisation après avoir été informés de l'action offensante en cause. Sinon, les comptes peuvent être suspendus ou clôturés.

## Limitations liées à Git Repos and Issue Tracking
{: #git_limitations}

{{site.data.keyword.gitrepos}} repose sur GitLab Community Edition et est hébergé par IBM sur {{site.data.keyword.Bluemix_notm}}. Certaines options GitLab ne sont toutefois pas disponibles :

 * Etant donné que {{site.data.keyword.deliverypipeline}} fournit l'intégration continue et la distribution continue pour {{site.data.keyword.Bluemix_notm}}, les fonctions d'intégration continue de GitLab ne sont pas prises en charge.
 * Les fonctions d'administration de GitLab ne sont pas disponibles car elles sont gérées par IBM.
 * {{site.data.keyword.gitrepos}} risque de ne pas être entièrement accessible.

## Informations utilisateur et contenu de Git Repos and Issue Tracking
{: #git_projects}

Trois types de projet {{site.data.keyword.gitrepos}} sont disponibles :

  1. Les projets publics sont visibles par tous les visiteurs du site. Le contenu d'un projet public est visible par toutes les personnes qui accèdent à {{site.data.keyword.contdelivery_short}}, même si elles ne sont pas invitées dans le projet.
  2. Les projets privés sont visibles uniquement par les utilisateurs sélectionnés. Pour en savoir plus sur l'octroi de l'accès à un projet aux utilisateurs, voir [Project users ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}.
  3. Les projets internes sont visibles par tous les utilisateurs connectés. Tout utilisateur doté d'un compte {{site.data.keyword.Bluemix_notm}} peut visualiser ces projets.

Vous pouvez modifier le type de projet dans les paramètres du projet. Pour plus d'informations, voir [How to change project visibility ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

Lorsque vous utilisez {{site.data.keyword.gitrepos}}, le contenu que vous apportez à un projet est soumis à une licence aux conditions spécifiées dans ce projet. Lorsque vous créez un projet, incluez un fichier qui décrit la licence applicable au contenu. Lorsque vous contribuez à un projet, votre nom et votre adresse électronique associée à vos validations sont susceptibles d'être visibles par le public. L'adresse électronique associée à votre compte {{site.data.keyword.Bluemix_notm}} est utilisée lorsque vous créez des validations via l'interface Web de {{site.data.keyword.gitrepos}}.

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
