---

copyright:
  years:  2018
lastupdated: "2018-8-2"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gestion de l'accès utilisateur aux chaînes d'outils avec Identity and Access Management 

L'accès aux chaînes d'outils des groupes de ressources pour les utilisateurs de votre compte est contrôlé par {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM).  

**Remarques **: 

* L'accès utilisateur pour les instances de chaîne d'outils et les instances de service {{site.data.keyword.contdelivery_short}} est géré séparément. Pour plus d'informations sur la gestion de l'accès utilisateur aux instances de service {{site.data.keyword.contdelivery_short}} dans les groupes de ressources, voir [Gestion de l'accès utilisateur à {{site.data.keyword.contdelivery_short}} avec Identity and Access Management](/docs/services/ContinuousDelivery/cd_iam_security.html){: new_window}.

* L'accès des utilisateurs aux chaînes d'outils dans les organisations Cloud Foundry est géré différemment de l'accès utilisateur aux instances de service {{site.data.keyword.contdelivery_short}} dans les groupes de ressources. Pour plus d'informations sur la gestion de l'accès utilisateur aux chaînes d'outils dans les organisations Cloud Foundry, voir [Gestion de l'accès aux chaînes d'outils dans les organisations Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs.html){: new_window}.

Chaque utilisateur qui accède aux chaînes d'outils de votre compte doit se voir attribuer une règle d'accès avec un rôle d'utilisateur IAM défini. Cette règle détermine les actions que l'utilisateur peut effectuer dans le contexte du service ou de l'instance que vous sélectionnez.
Les actions autorisées sont personnalisées et définies par le service {{site.data.keyword.Bluemix_notm}} en tant qu'opérations pouvant être réalisées sur le service. Les actions sont ensuite mappées à des rôles utilisateur IAM.

Les règles permettent d'activer les accès à différents niveaux. Certaines des options sont les suivantes :  

* Accès à l'ensemble des instances du service sur votre compte
* Accès à une instance de service individuelle de votre compte
* Accès à une ressource spécifique dans une instance
* Accès à tous les services activés pour IAM sur votre compte

Après avoir défini la portée de la règle d'accès, vous lui affectez un rôle. Examinez les tableaux suivants qui décrivent les actions que chaque rôle autorise dans les chaînes d'outils. 

Le tableau suivant détaille les actions mappées sur les rôles de gestion de plateforme. Les rôles de gestion de plateforme permettent aux utilisateurs d'effectuer des tâches sur les ressources de service au niveau de la plateforme. Par exemple, attribuer un accès utilisateur au service, créer ou supprimer des ID de service, créer des instances et lier des instances aux applications.

| Rôle Gestion de la plateforme | Description des actions |Exemples d'action|
|:-----------------|:-----------------|:-----------------|
|Afficheur, Opérateur | Voir les chaînes d'outils et les pipelines de distribution. Exécuter les pipelines de distribution. | <ul><li>Cliquez sur une chaîne d'outils pour ouvrir sa page Vue d'ensemble. </li><li>Cliquez sur l'icône **Exécuter une étape** de l'étape dans laquelle se trouve votre travail de pipeline. </li></ul> |
|Editeur, Administrateur| Créer, afficher, mettre à jour et supprimer les chaînes d'outils et les pipelines de distribution. |<ul><li>Dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, cliquez sur **Créer une chaîne d'outils**.</li><li>Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue
d'ensemble.</li><li>Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils à supprimer. Cliquez sur le menu **Plus d'actions**, qui se trouve à côté du menu **Afficher l'appli**. Cliquez sur **Supprimer**.</li></ul> |
{: caption="Tableau 1. Rôles et actions des utilisateurs IAM " caption-side="top"}

 Pour les chaînes d'outils, les actions suivantes existent : 

| Action | Opération sur le service | Rôle
|:-----------------|:-----------------|:--------------|
| create |Créer une chaîne d'outils dans un groupe de ressources. |Administrateur, Editeur |
| update | Mettre à jour une chaîne d'outils dans un groupe de ressources. Par exemple, renommer la chaîne d'outils. Modifier les pipelines de distribution liés aux chaînes d'outils dans un groupe de ressources. |Administrateur, Editeur |
| update_plan | Non applicable. |Administrateur, Editeur |
| delete | Supprimer une chaîne d'outils d'un groupe de ressources. |Administrateur, Editeur |
| retrieve | Afficher les détails d'une chaîne d'outils dans un groupe de ressources. Voir et exécuter les pipelines de distribution liés aux chaînes d'outils dans un groupe de ressources. |Administrateur, Editeur, Opérateur, Afficheur|
| list-bindings | Afficher les intégrations d'outils liées à une chaîne d'outils dans un groupe de ressources. |Administrateur, Editeur, Afficheur|
| create-bindings | Ajouter une intégration d'outils à une chaîne d'outils dans un groupe de ressources. |Administrateur, Editeur |
| delete-bindings | Supprimer une intégration d'outils d'une chaîne d'outils dans un groupe de ressources. |Administrateur, Editeur |
{: caption="Tableau 2. Actions et opérations de service " caption-side="top"}

Pour plus d'informations sur l'affectation de rôles utilisateur dans l'interface utilisateur, voir [Gestion de l'accès IAM](/docs/iam/mngiam.html#iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
