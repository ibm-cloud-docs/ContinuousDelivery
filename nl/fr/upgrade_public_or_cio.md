---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Mise à niveau des projets IBM Confidentiel vers des chaînes d'outils 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}} évolue vers IBM Bluemix {{site.data.keyword.contdelivery_short}}. Dans le cadre de cette modification, les projets sont mis à niveau vers des chaînes d'outils.

Lorsque votre projet est prêt pour la mise à niveau, un message s'affiche sur sa page Présentation. Vous pouvez alors le mettre à niveau vers une chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public. La chaîne d'outils inclura un référentiel Whitewater {{site.data.keyword.ghe_short}} pour votre code source. Whitewater {{site.data.keyword.ghe_short}} est fourni aux équipes IBM dans un objectif de promotion et d'activation du codage social chez IBM. 
{: shortdesc}

Les chaînes d'outils **{{site.data.keyword.contdelivery_short}} sont approuvées pour les éléments IBM Confidentiel lorsqu'elles sont utilisées avec Whitewater {{site.data.keyword.ghe_short}}.** Les pipelines de distribution qui reçoivent des entrées issues de référentiels Whitewater {{site.data.keyword.ghe_short}} peuvent effectuer des déploiements dans des environnements publics (YP) et de constitution (YS1).

Lors de la mise à niveau, vous êtes invité à autoriser {{site.data.keyword.contdelivery_short}} à accéder à Whitewater {{site.data.keyword.ghe_short}} en votre nom.

## Ajout de membres à votre référentiel Whitewater {{site.data.keyword.ghe_short}} après la mise à niveau

Si votre projet utilise un référentiel hébergé sur JazzHub, un nouveau référentiel est créé sur Whitewater {{site.data.keyword.ghe_short}} au cours de la mise à niveau. Après la mise à niveau, la personne ayant lancé la mise à niveau doit ajouter les membres de l'équipe au référentiel Whitewater {{site.data.keyword.ghe_short}} et s'assurer qu'ils disposent des droits appropriés pour accéder au nouveau référentiel.

## Traitement des incidents

Un problème intermittent se produit parfois lorsque vous essayez de modifier la cible d'une phase de déploiement de pipeline. Lorsque ce problème survient, une erreur apparaît dans les zones **Organisation** et **Espace**.

Ce problème se produit généralement uniquement lorsque vous modifiez la cible du pipeline de telle sorte que le pipeline créé lors de la mise à niveau se déploie correctement sur les mêmes cibles que précédemment.

Si vous tentez de modifier la cible et que ce problème survient, passez d'une cible à l'autre quelques fois jusqu'à ce que les zones **Organisation** et **Espace** soient renseignées.

Un problème associé entraîne parfois l'échec du déploiement vers les cibles YS1. Cette situation est rare ; si cela se produit, exécutez à nouveau le pipeline.

L'équipe IBM DevOps Services travaille activement à la résolution de ces problèmes.
