---

copyright:
  years:  2018, 2019
lastupdated: "2019-2-1"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gestion de l'accès utilisateur à la Distribution continue avec Identity and Access Management
{: #cd-iam-security}

L'accès aux instances de service {{site.data.keyword.contdelivery_full}} dans les groupes de ressources pour les utilisateurs de votre compte est contrôlé par {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Remarques **: 

* L'accès utilisateur pour les instances de service {{site.data.keyword.contdelivery_short}} et les instances de chaîne d'outils est géré séparément. Pour plus d'informations sur la gestion de l'accès utilisateur aux chaînes d'outils dans les groupes de ressources, voir [Gestion de l'accès utilisateur aux chaînes d'outils avec Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}.

* L'accès utilisateurs aux chaînes d'outils dans les organisations Cloud Foundry est géré différemment de l'accès utilisateur aux chaînes d'outils dans les groupes de ressources. Pour plus d'informations sur la gestion de l'accès utilisateur aux chaînes d'outils dans les organisations Cloud Foundry, voir [Gestion de l'accès aux chaînes d'outils dans les organisations Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.

Une règle d'accès avec un rôle utilisateur IAM doit être affectée à chaque utilisateur disposant d'un accès au service {{site.data.keyword.contdelivery_short}} sur votre compte. Cette règle détermine les actions que l'utilisateur peut effectuer dans le contexte du service ou de l'instance que vous sélectionnez. Les actions autorisées sont personnalisées et définies par le service {{site.data.keyword.Bluemix_notm}} en tant qu'opérations pouvant être réalisées sur le service. Les actions sont ensuite mappées à des rôles utilisateur IAM.

Les règles permettent d'activer les accès à différents niveaux. Certaines des options sont les suivantes : 

* Accès à l'ensemble des instances du service sur votre compte
* Accès à une instance de service individuelle de votre compte
* Accès à une ressource spécifique dans une instance
* Accès à tous les services activés pour IAM sur votre compte

Après avoir défini la portée de la règle d'accès, vous lui affectez un rôle. Consultez les tableaux suivants qui décrivent les actions que chaque rôle autorise dans le service {{site.data.keyword.contdelivery_short}}.

Le tableau suivant détaille les actions mappées sur les rôles de gestion de plateforme. Les rôles de gestion de plateforme permettent aux utilisateurs d'effectuer des tâches sur les ressources de service au niveau de la plateforme. Par exemple, attribuer un accès utilisateur au service, créer ou supprimer des ID de service, créer des instances et lier des instances aux applications.

| Rôle Gestion de plateforme | Description des actions | Exemples d'action|
|:-----------------|:-----------------|:-----------------|
| Afficheur, Opérateur | Afficher les instances du service {{site.data.keyword.contdelivery_short}}. | <ul><li>Cliquer sur une instance de service {{site.data.keyword.contdelivery_short}} pour ouvrir son tableau de bord.</li></ul>|
| Editeur, Administrateur | Créer, afficher, mettre à jour, modifier le plan et supprimer des instances du service {{site.data.keyword.contdelivery_short}}. |<ul><li>Mettre à disposition une instance de {{site.data.keyword.contdelivery_short}} dans un groupe de ressources.</li><li>Supprimer une instance de {{site.data.keyword.contdelivery_short}} dans un groupe de ressources.</li><li>Modifier un plan d'instance {{site.data.keyword.contdelivery_short}} de Lite à Professional.</li></ul> |
| Administrateur | Mettre à jour la liste des utilisateurs autorisés.| <ul><li>Ajouter un utilisateur à la liste des utilisateurs autorisés.</li><li>Supprimer un utilisateur de la liste des utilisateurs autorisés.</li></ul> |
{: caption="Tableau 1. Rôles et actions des utilisateurs IAM" caption-side="top"}

 Pour {{site.data.keyword.contdelivery_short}}, les actions suivantes existent :

| Action | Opération sur le service | Rôle
|:-----------------|:-----------------|:--------------|
| create | Mettre à disposition une instance de service {{site.data.keyword.contdelivery_short}} dans un groupe de ressources. | Administrateur, Editeur |
| update | Mettre à jour une instance de service {{site.data.keyword.contdelivery_short}} dans un groupe de ressources. Par exemple, renommer l'instance de service. | Administrateur, Editeur |
| update_plan | Modifier le plan pour l'instance de service {{site.data.keyword.contdelivery_short}} dans un groupe de ressources. | Administrateur, Editeur |
| delete | Supprimer une instance de service {{site.data.keyword.contdelivery_short}} dans un groupe de ressources. | Administrateur, Editeur |
| retrieve | Afficher une instance de service {{site.data.keyword.contdelivery_short}} dans un groupe de ressources. | Administrateur, Editeur, Opérateur, Afficheur |
| add-auth-users | Ajouter des entrées à la liste Utilisateurs autorisés dans l'onglet Gérer de l'instance de service {{site.data.keyword.contdelivery_short}}. | Administrateur, Rédacteur, Responsable |
| remove-auth-users | Retirer des entrées de la liste Utilisateurs autorisés dans l'onglet Gérer de l'instance de service {{site.data.keyword.contdelivery_short}}. | Administrateur, Rédacteur, Responsable |
{: caption="Tableau 2. Actions et opérations de service" caption-side="top"}

Le tableau ci-dessous détaille les actions qui sont mappées aux rôles d'accès de service. Les rôles d'accès aux services permettent aux utilisateurs d'accéder à {{site.data.keyword.contdelivery_short}} ainsi que la possibilité d'appeler l'API {{site.data.keyword.contdelivery_short}}.

| Rôle Accès au service | Description des actions | Exemples d'action|
|:-----------------|:-----------------|:-----------------|
| Rédacteur, gestionnaire | Ajouter et supprimer des utilisateurs de la liste Utilisateurs autorisés de l'onglet Gérer d'une instance de service {{site.data.keyword.contdelivery_short}}. | <ul><li>Ajouter un utilisateur autorisé.</li><li>Retirer l'utilisateur autorisé.</li></ul>|
{: caption="Tableau 3. Rôles et actions d'accès au service IAM" caption-side="top"}

Pour plus d'informations sur l'affectation de rôles utilisateur dans l'interface utilisateur, voir [Gestion de l'accès IAM](/docs/iam?topic=iam-iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
