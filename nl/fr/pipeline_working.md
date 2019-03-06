---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# Utilisation de pipelines 
{: #pipeline-working}

Pour automatiser vos générations et déploiements vers {{site.data.keyword.Bluemix}}, utilisez
des pipelines {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

Avec des pipelines, vous pouvez choisir entre plusieurs types de génération. Vous fournissez le script de génération et {{site.data.keyword.contdelivery_short}} l'exécute ; il n'est pas nécessaire de configurer des systèmes de génération. Ensuite, en un clic, vous pouvez déployer automatiquement votre application sur un ou plusieurs espaces {{site.data.keyword.Bluemix_notm}}, serveurs Cloud Foundry publics ou conteneurs Docker sur {{site.data.keyword.containerlong}}.

Les travaux de génération compilent et assemblent en package le code source de votre application depuis les référentiels Git. Ils génèrent des artefacts pouvant être déployés, tels que des fichiers WAR ou des conteneurs Docker pour {{site.data.keyword.containerlong_notm}}. De plus, vous pouvez
exécuter des tests unitaires dans votre génération automatiquement. Vous pouvez configurer les travaux de génération de sorte que chaque fois qu'une validation est
envoyée, une génération est déclenchée.

Un travail de déploiement déploie la sortie d'un travail de génération sur les serveurs {{site.data.keyword.containerlong_notm}} ou Cloud Foundry tels que {{site.data.keyword.Bluemix_notm}}.

Vous pouvez effectuer le déploiement dans une ou plusieurs régions et dans un ou plusieurs services. Par exemple, vous pouvez configurer votre {{site.data.keyword.deliverypipeline}} en vue d'utiliser un ou plusieurs services, le tester dans une région, et le déployer en production dans plusieurs régions.

##Création d'un pipeline

Vous pouvez utiliser l'une des méthodes suivantes pour créer un pipeline :

   * [Créer une chaîne d'outils à partir d'une application Cloud Foundry existante](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}. La chaîne d'outils obtenue contient un pipeline.

   * [Créer une chaîne d'outils à partir d'un modèle](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window} comprenant au moins un pipeline.

   * [Ajouter l'intégration d'outils {{site.data.keyword.deliverypipeline}} ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window} à une chaîne d'outils existante. 
   
A partir de {{site.data.keyword.deliverypipeline}}, modifiez votre configuration, vérifiez le statut des générations, l'application déployée et les déploiements récents, examinez les journaux les plus récents et les détails du déploiement, ou supprimez votre pipeline.
