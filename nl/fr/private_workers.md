---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Utilisation des agents {{site.data.keyword.deliverypipeline}} privés
{: #private-workers}

{{site.data.keyword.deliverypipeline}} utilise des agents publics et privés pour exécuter les travaux de pipeline. Par défaut, les travaux de pipeline sont exécutés à l'aide d'agents publics sur une infrastructure partagée publique gérée par IBM.
{: shortdesc}

Dans certains scénarios, votre {{site.data.keyword.deliverypipeline}} peut nécessiter un accès à des ressources internes ou sur site. Dans ces situations, vous pouvez vous connecter et intégrer un agent {{site.data.keyword.deliverypipeline}} privé pour qu'il s'exécute sur votre propre infrastructure Kubernetes.

## Conditions requises
{: #private_workers_prereqs}

Avant de configurer un agent privé, assurez-vous d'avoir les ressources suivantes en place :

* Un cluster Kubernetes. Vous devez avoir un cluster pour installer un agent privé. Vous pouvez fournir votre propre cluster ou vous pouvez [configurer un cluster](https://cloud.ibm.com/kubernetes/clusters){:external} depuis {{site.data.keyword.containerlong_notm}}.

* Une chaîne d'outils avec un pipeline qui contient au moins une étape. Vous pouvez utiliser une chaîne d'outils existante ou [créer une chaîne d'outils](https://cloud.ibm.com/devops/create){:external}.

## Configuration d'un agent {{site.data.keyword.deliverypipeline}} privé
{: #set_up_private_worker}

Exécutez les étapes suivantes pour configurer un agent privé :

1. Configurez l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker pour votre chaîne d'outils.
2. Configurez votre cluster Kubernetes avec un agent privé.
3. Utilisez l'agent privé dans votre pipeline.

### Configuration de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker
{: #configure_private_worker_integration}

Exécutez les étapes suivantes pour configurer l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker pour votre chaîne d'outils :

1. Si vous configurez cette intégration d'outil lorsque vous créez une chaîne d'outils, dans la section Intégrations configurables, cliquez sur **{{site.data.keyword.deliverypipeline}} Private Worker**.
1. Si vous disposez d'une chaîne d'outils et lui ajoutez cette intégration d'outil, dans le tableau de bord DevOps, dans la page Chaînes d'outils, cliquez sur une chaîne d'outils pour ouvrir sa page d'aperçu. Vous pouvez également, depuis votre page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.

 a. Cliquez sur **Ajouter un outil**.

 b. Dans la section Intégrations d'outils, cliquez sur **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Entrez un nom pour l'intégration d'outil. Ce nom identifie un pool d'agents privés dans l'onglet **Agents** de l'étape de pipeline.
1. Entrez la clé d'API de votre ID de service pour authentifier l'accès à la file d'attente des travaux où un ou plusieurs agents privés peuvent rechercher un travail. Si vous ne disposez pas d'une clé d'API d'ID de service, cliquez sur **Créer** pour en générer une pour cet agent privé.
1. Cliquez sur **Créer une intégration**.
1. Dans votre chaîne d'outils, cliquez sur **{{site.data.keyword.deliverypipeline}} Private Worker** pour afficher une liste de tous les agents enregistrés à l'aide d'une clé d'API associée à cet ID de service.

Pour en savoir plus sur l'intégration d'outil **{{site.data.keyword.deliverypipeline}} Private Worker**, voir [Configuration d'un agent {{site.data.keyword.deliverypipeline}} privé](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker).

### Configuration de votre cluster Kubernetes
{: #configure_kubernetes_cluster}

Configurez votre cluster Kubernetes avec un agent privé :

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur la carte de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker que vous souhaitez configurer.
1. Cliquez sur **Initiation** puis suivez les étapes d'installation et d'enregistrement d'un agent privé sur votre cluster Kubernetes.

### Utilisation de l'agent {{site.data.keyword.deliverypipeline}} privé dans votre pipeline
{: #use_private_worker_pipeline}

Exécutez les étapes suivantes pour utiliser l'agent privé dans votre pipeline :

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur la carte du pipeline avec lequel vous souhaitez utiliser l'agent privé.
1. Sur la page Pipeline, sur l'étape, cliquez sur l'icône **Configuration de l'étape** puis sur **Configurer l'étape**.
1. Cliquez sur l'onglet **Agents**.
1. Sélectionnez l'agent privé que vous souhaitez utiliser dans votre pipeline. 

 Par défaut, les travaux contenus dans une étape de pipeline s'exécutent à l'aide d'un pool d'agents partagés gérés par IBM dans la région dans laquelle le pipeline est défini.
 {: tip}
 
1. Cliquez sur **Sauvegarder**.
1. Vous pouvez exécuter votre étape manuellement ou attendre qu'un déclencheur exécute les travaux sur l'étape à l'aide de l'agent privé spécifié sur le cluster Kubernetes associé. Vous pouvez afficher la sortie du fichier journal correspondant aux travaux pour déterminer quel agent a été utilisé.  


## Modification des données d'identification de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker
{: #modify_private_worker}

Après avoir configuré votre agent privé, vous pouvez mettre à jour les données d'identification qui sont utilisées pour l'intégration d'outil. Vous voudrez peut-être modifier ces informations d'identification si elles sont supprimées, expirées ou endommagées. Vous pouvez mettre à jour les données d'identification en créant un nouvel ID de service ou en mettant à jour la clé d'API.

### Création d'un ID de service
{: #create_service_id}

Exécutez les étapes suivantes pour créer un ID de service :

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Sur la carte de l'intégration d'outil des agents privés à modifier, cliquez sur le menu pour accéder aux options de configuration.
1. Cliquez sur **Créer**.
1. Entrez un nom et une description pour l'ID de service.
1. Cliquez sur **Sauvegarder l'intégration**.
1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur la carte de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker pour laquelle vous souhaitez spécifier de nouvelles données d'identification d'utilisateur. 
1. Cliquez sur **Initiation**, et exécutez les étapes 2 et 3 pour vous enregistrer et vérifier l'agent privé sur votre cluster.

### Mise à jour de la clé d'API
{: #update_api_key}

Exécutez les étapes suivantes pour mettre à jour la clé d'API pour une utilisation avec l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker :

1. Dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Sur la carte de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker que vous souhaitez modifier, cliquez sur le menu pour accéder aux options de configuration.
1. Spécifiez votre nouvelle clé d'API. 
1. Cliquez sur **Sauvegarder l'intégration**.

## Suppression d'un agent {{site.data.keyword.deliverypipeline}} privé 
{: #delete_private_worker}

Exécutez les étapes suivantes pour supprimer un agent privé :

1. Supprimez l'agent privé du pool d'agents.
1. Supprimez l'agent privé de votre cluster Kubernetes.

### Suppression d'un agent {{site.data.keyword.deliverypipeline}} privé du pool d'agents

Exécutez les étapes suivantes pour supprimer l'agent privé du pool d'agents :

1. Dans le tableau de bord DevOps, sur la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur la carte de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker que vous souhaitez configurer.
1. Cliquez sur **Présentation**.
1. Cliquez sur le menu de l'agent privé que vous souhaitez supprimer pour accéder aux options de configuration.
1. Cliquez sur **Retirer** puis sur **Confirmer**.

### Suppression d'un agent {{site.data.keyword.deliverypipeline}} privé de votre cluster Kubernetes

Exécutez les étapes suivantes pour supprimer l'agent privé de votre cluster :

1. Cliquez sur la carte de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker que vous souhaitez configurer.
1. Cliquez sur **Initiation** et suivez les étapes décrites pour supprimer l'agent privé de votre cluster.

## Suppression de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker 
{: #delete_private_workers_tool_integration}

Si vous supprimez l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker de votre chaîne d'outils, la suppression est irréversible.
{: important}

Effectuez les étapes suivantes pour supprimer une intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker :

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur une chaîne d'outils afin d'ouvrir la page d'aperçu correspondante. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Sur la carte de l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker que vous souhaitez supprimer, cliquez sur le menu pour accéder aux options de configuration.
1. Pour supprimer l'intégration d'outils de votre chaîne d'outils, cliquez sur **Supprimer**.
1. Confirmez en cliquant sur **Supprimer**. L'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker est supprimée de la chaîne d'outils et n'est plus disponible dans l'onglet **Agents** dans la page Configuration de l'étape du pipeline de distribution.

Si vous supprimez l'intégration d'outil {{site.data.keyword.deliverypipeline}} Private Worker d'une chaîne d'outils et que l'agent privé est configuré pour une étape de pipeline, il continue d'apparaître dans l'onglet **Agents** de la page Configuration de l'étape. Cependant, l'agent privé est désactivé et affiche l'état Supprimé. Vous devez sélectionner un agent privé différent (s'il existe) ou utiliser un agent public à la place.
{: tip}
