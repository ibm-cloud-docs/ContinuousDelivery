---

copyright:
  years: 2016, 2017
lastupdated: "2017-7-24"
---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Limites et utilisation du plan
{: #deliverypipeline_plans}
{: #free_deprecation}

L'utilisation d'{{site.data.keyword.contdelivery_full}} est limitée à la génération, au déploiement, au test et aux opérations en cours des applications sur la plateforme {{site.data.keyword.Bluemix_notm}} ou toute autre plateforme ou infrastructure en tant que service compatible.

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
  2. Les projets privés sont visibles uniquement par les utilisateurs sélectionnés. Pour plus de détails sur l'octroi de l'accès à un projet aux utilisateurs, voir [Project users ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}.
  3. Les projets internes sont visibles par tous les utilisateurs connectés. Tout utilisateur doté d'un compte {{site.data.keyword.Bluemix_notm}} peut visualiser ces projets.

Vous pouvez modifier le type de projet dans les paramètres du projet. Pour plus d'informations, voir [How to change project visibility ![Icône de lien externe](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

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
