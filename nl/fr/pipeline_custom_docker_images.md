---

Copyright:
  years: 2018
lastupdated: "2018-12-6"

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


# Utilisation des images Docker personnalisées
{: #custom_docker_images}

Il est possible que l'image de base du pipeline ne réponde pas à toutes les exigences de votre build. Par exemple, vous pourriez avoir besoin d'un contrôle plus fin sur les versions de node, java, ou autres outils. Vous pouvez résoudre ce problème en incluant une première étape dans vos travaux de pipeline qui installe une série de nouveaux paquets et configure soigneusement les variables d'environnement, telles que `PATH`, pour configurer votre environnement. Cependant, il est préférable d'utiliser la prise en charge par le pipeline de l'exécution d'une "image Docker personnalisée" comme base de votre travail.

Que le travail soit de type Génération, Test ou Déploiement, vous pouvez sélectionner un sous-type Image Docker personnalisée pour fournir le nom de l'image Docker à utiliser et spécifier le script devant être exécuté. Par exemple, utilisez les options suivantes pour exécuter un travail de génération avec Maven 3.5.3 et IBM Java :

 ![Génération Maven avec image personnalisée](images/custom-image-maven-build.png)


## Spécification du nom de l'image Docker
{: #docker_image_name}

Le nom de l'image Docker dans les travaux d'images Docker personnalisées est conçu pour fonctionner de la même manière que les noms d'image fonctionnent avec l'interface de ligne de commande Docker. Le format d'un nom d'image Docker est : `[repository][:][tag]`. Par exemple, pour `docker run maven:3.5.3-ibmjava`, le nom de l'image Docker est `maven:3.5.3-ibmjava`, où `maven` est le référentiel et `3.5.3-ibmjava` est l'étiquette. Il n'y a aucune restriction sur le nom de l'image Docker que vous pouvez utiliser ; n'importe quelle image Docker valide fonctionne.

Si la zone **Nom d'image Docker** n'est pas renseignée, l'image de base du pipeline standard est utilisée. 
{: tip}

Par défaut, votre référentiel est recherché sur [Docker Hub ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://hub.docker.com/){: new_window}. Si vous utilisez un autre registre Docker, tel que {{site.data.keyword.registrylong}}, vous pouvez utiliser le nom de DNS complet. Vous pouvez également utiliser le nom complet pour les images sur Docker Hub. Par exemple, `registry.hub.docker.com/library/maven:3.5.3-ibmjava`.

La balise (`tag`) d'une image Docker est facultative. Si vous ne spécifiez pas une balise, elle sera définie par défaut sur `latest`. Une valeur par défaut `latest` est juste un nom de balise que le propriétaire du référentiel doit gérer. Cela ne signifie pas que cette image Docker est la dernière image du point de vue chronologique.

Vous trouverez une vaste communauté de référentiels sur Docker Hub. IBM héberge une série de référentiels publics que l'équipe IBM Cloud utilise à l'adresse [https://hub.docker.com/u/ibmcom/ ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://hub.docker.com/u/ibmcom/){: new_window}. Les référentiels `ibmcom/ibmjava` et `ibmcom/ibmnode` sont utiles comme base pour la génération. 

## Utilisation d'un registre d'images privé
{: #private_image_registry}

Si vous utilisez un registre privé nécessitant une authentification, vous devez définir deux propriétés d'environnement d'étape supplémentaires : `DOCKER_USERNAME` et `DOCKER_PASSWORD`. Vous pouvez utiliser une propriété sécurisée pour masquer votre `DOCKER_PASSWORD`. Avant que votre image ne soit extraite, le travail d'image Docker personnalisée utilise votre nom d'utilisateur et votre mot de passe pour effectuer un `docker login`.

Dans la plupart des registres, vous pouvez utiliser le nom d'utilisateur et le mot de passe qui vous ont été fournis. Si vous utilisez {{site.data.keyword.registrylong_notm}} pour stocker vos images privées, vous devez utiliser une clé d'API de plateforme pour l'authentification. 

1. [Demandez une clé d'API de plateforme ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/iam/#/apikeys){: new_window} et sauvegardez la clé. 
1. Créez les propriétés d'environnement en deux étapes en utilisant `iamapikey` comme votre `DOCKER_USERNAME` et la clé d'API de plateforme sauvegardée comme `DOCKER_PASSWORD`.

 Données d'identification ![{{site.data.keyword.registrylong_notm}}](images/custom-image-private-repository.png)


## Spécification du script
{: #specify_script}

Vous pouvez utiliser le bloc de **script** dans les travaux d'images Docker personnalisées pour créer un fichier script qui s'exécute dans un dossier de tâches, de la même manière que les travaux de pipeline réguliers. 

`ENTRYPOINT` et `CMD` du fichier Docker de votre image Docker sont écrasés et ne sont pas appelés. Dans certains cas, cela peut signifier que vous devez ajouter des étapes d'initialisation à votre script.
{: tip}

Les travaux d'images Docker personnalisées offrent une plus grande flexibilité dans le mode d'exécution de votre script, notamment car vous pouvez contrôler l'interpréteur de commandes. Généralement, si la première ligne du script commence par `#!` et le nom d'un interpréteur de commandes, cette entrée est utilisée pour exécuter les commandes dans le travail. Si vous ne spécifiez pas d'interpréteur de commandes, l'interpréteur de commandes par défaut de l'image Docker est utilisé. Généralement, `#!/bin/bash` ou `#!/bin/sh` sont utilisés. Les interpréteurs de commandes d'images de `awk`, `node` et `ruby` fonctionnent également si vous spécifiez une image Docker appropriée.
