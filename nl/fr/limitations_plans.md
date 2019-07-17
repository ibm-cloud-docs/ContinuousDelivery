---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# Utilisation des plans et limitations
{: #limitations_usage}

L'utilisation d'{{site.data.keyword.contdelivery_full}} est limitée à la génération, au déploiement, au test et aux opérations en cours des applications sur la plateforme {{site.data.keyword.Bluemix_notm}} ou toute autre plateforme ou infrastructure en tant que service compatible.

## Portée d'une instance de service
{: #service_scope}

Vous devez avoir une [instance de service](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} {{site.data.keyword.contdelivery_short}} pour créer et utiliser des chaînes d'outils DevOps. Une instance de service peut appartenir à un [groupe de ressources](/docs/services/resources?topic=resources-rgs) {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) ou à une organisation {{site.data.keyword.Bluemix_notm}}.

Vous pouvez uniquement créer des *nouvelles* instances du service {{site.data.keyword.contdelivery_short}} dans les groupes de ressources. La migration des chaînes d'outils des organisations aux groupes de ressources n'est pas prise en charge actuellement. Si vous avez besoin d'un service {{site.data.keyword.contdelivery_short}} d'une organisation contenant des chaînes d'outils, vous pouvez recréer les chaînes d'outils dans un groupe de ressources ou bien contacter le [support IBM](https://cloud.ibm.com/unifiedsupport){:external} pour obtenir de l'aide.

Vous ne pouvez avoir qu'un service Lite par compte. Il est recommandé d'utiliser le plan Professional si vous voulez travailler avec des chaînes d'outils dans plusieurs organisations ou groupes de ressources, ou dans plusieurs régions.
{: tip}


## Utilisateurs autorisés
{: #authorized_users}

Les [plans de service](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} {{site.data.keyword.contdelivery_short}} sont définis et tarifés en fonction du nombre d'utilisateurs autorisés pour une instance de service. Toute personne qui contribue à un effort doit être considérée comme un utilisateur autorisé, y compris :

 * Les utilisateurs qui interagissent avec des problèmes, des tableaux de problèmes, du code source ou d'autres artefacts dans un référentiel {{site.data.keyword.gitrepos}}.
 * Les utilisateurs qui manipulent, déclenchent (soit directement dans l'interface utilisateur, soit indirectement en s'engageant dans un référentiel), ou visualisent l'état d'un pipeline de distribution.
 * Les utilisateurs qui interagissent avec Eclipse Orion {{site.data.keyword.webide}}.
 
Le plan Lite est soumis à des limitations. Pour en savoir plus sur le plan Lite et le plan Professional, consultez le [catalogue de service](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}
 
### Comment les utilisateurs sont-ils comptabilisés pour les instances de {{site.data.keyword.contdelivery_short}} dans les groupes de ressources ?

Les utilisateurs autorisés sont comptabilités et gérés pour chaque instance de service conformément à la liste des utilisateurs autorisés pour la facturation et les limites du plan Lite. Les utilisateurs du service {{site.data.keyword.contdelivery_short}} sont automatiquement ajoutés à cette liste. Vous pouvez empêcher les utilisateurs d'accéder aux chaînes d'outils et d'être automatiquement ajoutés à une instance de service {{site.data.keyword.contdelivery_short}}. Pour en savoir plus sur l'utilisation de l'IAM pour supprimer l'accès des utilisateurs depuis le groupe de ressources contenant la chaîne d'outils (ou depuis la chaîne d'outils elle-même), voir [Gestion de l'accès des utilisateurs à {{site.data.keyword.contdelivery_short}} avec Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security). 

La méthode que vous utilisez pour organiser les chaînes d'outils dans les groupes de ressources a un impact direct sur l'accès des utilisateurs et la facturation. Lorsqu'un utilisateur utilise des chaînes d'outils dans plusieurs groupes de ressources, elles sont comptabilisées et facturées pour chaque service dans ces groupes de ressources.
{: tip}

Vous pouvez gérer la liste des utilisateurs autorisés sur l'onglet **Gérer** dans l'instance de service {{site.data.keyword.contdelivery_short}}.

1. Accédez à la [liste des ressources](https://cloud.ibm.com/resources){:external} de votre compte {{site.data.keyword.Bluemix_notm}}.
2. Dans la colonne **Nom**, dans la zone de texte du filtre, entrez **Continuous Delivery** pour afficher vos services existants.
3. Pour chaque service, cliquez sur le lien hypertexte dans la colonne **Nom**.
4. Dans l'onglet **Gérer**, vous pouvez afficher, ajouter ou supprimer des utilisateurs de la liste des utilisateurs autorisés, en fonction des besoins.

Les utilisateurs sont ajoutés automatiquement et ajoutés à nouveau lorsqu'ils utilisent le service {{site.data.keyword.contdelivery_short}}.
{: tip}

### Comment les utilisateurs sont-ils comptabilisés pour les instances de {{site.data.keyword.contdelivery_short}} dans les organisations ?

Les utilisateurs autorisés sont comptabilisés en comptant tous les utilisateurs de l'organisation {{site.data.keyword.Bluemix_notm}} qui contiennent le service {{site.data.keyword.contdelivery_short}}. Pour en savoir plus sur les organisations et les espaces, voir [Création des organisations et des espaces](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

Pour afficher la liste des utilisateurs de votre organisation dans un environnement {{site.data.keyword.Bluemix_notm}} Public, cliquez sur **Gérer > Compte** dans la barre de menus. Ensuite, cliquez sur **Organisations Cloud Foundry**.

### Comment puis-je afficher les informations de facturation et d'utilisation ?

Vous pouvez afficher toutes les instances du service {{site.data.keyword.contdelivery_short}} dans votre compte et le nombre d'utilisateurs et d'exécutions de pipeline répertoriés dans chaque instance dans un environnement {{site.data.keyword.Bluemix_notm}} Public.

1. Dans la barre de menus, cliquez sur **Gérer > Facturation et utilisation**.
2. Cliquez sur **Utilisation**.
3. Dans la section **Services**, cliquez sur **Afficher les plans** pour le service {{site.data.keyword.contdelivery_short}}.
4. Cliquez sur **Afficher les détails** pour le plan sur lequel vous souhaitez afficher des informations.
5. Cliquez sur **Afficher les détails de l'instance** pour l'instance de {{site.data.keyword.contdelivery_short}} pour laquelle vous souhaitez afficher des informations d'utilisation.

La métrique `AUTHORIZED_USERS_PER_MONTH` est calculée sur la base d'une moyenne mensuelle d'utilisateurs qui est comptée chaque jour.
{: tip}

### Que se passe-t-il lorsque vous dépassez les limites de votre plan de service ?

Le plan de service Lite comporte d'autres limitations, comme le nombre de travaux Delivery Pipeline qui peuvent s'exécuter ou la consommation de mémoire. Pour en savoir plus sur la description des plans, voir le [catalogue de service](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. Si l'une des limites du plan est dépassée dans une période de facturation, le service s'interrompt. Par exemple, les travaux Delivery Pipeline ne seront pas exécutés durant tout le reste de la période de facturation. 

## Utilisation de Delivery Pipeline
{: #pipeline_usage}

Les comportements acceptables en matière d'utilisation sont les suivants, sans s'y limiter :

* La compilation et l'assemblage d'artefacts pour les langages de programmation pris en charge.
* Le déploiement automatisé d'artefacts d'application, de configurations et de ressources ou services pertinents.
* Le test, la validation et tout autre comportement généré par un événement de développement déclenché dans le cadre d'un processus de développement.

Les comportements non autorisés en matière d'utilisation sont les suivants, sans s'y limiter :

* L'utilisation de travaux ou d'agents de pipeline pour des comportements de calcul généraux, tels que le minage de Bitcoin, les attaques par refus de service distribuées et un comportement malveillant ou offensant envers d'autres clients ou utilisateurs de la plateforme {{site.data.keyword.Bluemix_notm}} ou des utilisateurs généraux d'Internet.
* L'utilisation dans le processus de développement normal de sites ou de services faisant la promotion d'un discours haineux ou d'autres activités violant les Principes de conduite des affaires d'IBM.
* L'utilisation d'un comportement généré par un événement pour une intrusion malveillante ou des attaques contre {{site.data.keyword.Bluemix_notm}} ou d'autres sites.

A la discrétion d'IBM, les utilisateurs qui violent les comportements d'utilisation acceptables des services {{site.data.keyword.contdelivery_short}} ou les [Principes de conduite des affaires d'IBM](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} peuvent être désactivés sans préavis. A la discrétion d'IBM, certains services peuvent être restaurés si les utilisateurs corrigent leurs comportements d'utilisation après avoir été informés de l'action offensante en cause. Sinon, les comptes peuvent être suspendus ou clôturés.

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
  2. Les projets privés sont uniquement visibles par les utilisateurs sélectionnés. Pour en savoir plus sur l'octroi de l'accès à un projet aux utilisateurs, voir [Project users](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. Les projets internes sont visibles par tous les utilisateurs connectés. Tout utilisateur doté d'un compte {{site.data.keyword.Bluemix_notm}} peut visualiser ces projets.

Vous pouvez modifier le type de projet dans les paramètres du projet. Pour plus d'informations sur les paramètres du projet, voir [How to change project visibility](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

Lorsque vous utilisez {{site.data.keyword.gitrepos}}, le contenu que vous apportez à un projet est soumis à une licence aux conditions spécifiées dans ce projet. Lorsque vous créez un projet, incluez un fichier qui décrit la licence applicable au contenu. Lorsque vous contribuez à un projet, votre nom et votre adresse électronique associée à vos validations sont susceptibles d'être visibles par le public. L'adresse électronique associée à votre compte {{site.data.keyword.Bluemix_notm}} est utilisée lorsque vous créez des validations via l'interface Web de {{site.data.keyword.gitrepos}}.
