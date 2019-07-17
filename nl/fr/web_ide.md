---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: Eclipse Orion {{site.data.keyword.webide}}, file types, Local Editor Settings icon

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:download: .download}

# Développement avec l'interface Eclipse Orion Web IDE
{: #web_ide}

L'interface Eclipse Orion {{site.data.keyword.webide}} est un environnement de développement basé sur un navigateur dans lequel vous pouvez développer pour le Web en JavaScript, HTML et CSS en vous aidant de l'assistant de contenu, la validation de code et le contrôle des erreurs. L'interface {{site.data.keyword.webide}} fonctionne avec presque toutes les langues et vous pouvez mettre en évidence la syntaxe pour la plupart des types de fichiers. Le contrôle des sources est intégré et vous pouvez déployer le code en local afin de tester et déboguer vos applications.
{:shortdesc}

Mais surtout, {{site.data.keyword.webide}} est basé sur le Web. Vous n'avez rien à installer, rien à gérer ni rien à mettre à l'échelle. Vous pouvez faire du développement depuis n'importe quel endroit, dans la mesure où vous disposez d'une connexion Internet.

Ne stockez pas les données réglementées dans des fichiers situés dans l'interface {{site.data.keyword.webide}}. Les procédures relatives aux données réglementées ne sont pas encore en place.
{: tip}

L'interface {{site.data.keyword.webide}} est accessible avec le clavier et fonctionne bien avec un lecteur d'écran. Vous pouvez utiliser {{site.data.keyword.webide}} pour éditer le code ou, si vous le préférez, vous pouvez éditer le code à l'aide de votre éditeur de code ou de texte favori. Vous pouvez également utiliser les fonctionnalités Git qui sont fournies avec {{site.data.keyword.webide}} ou bien utiliser la ligne de commande Git ou github.com pour accéder aux fonctionnalités Git de {{site.data.keyword.webide}}.
{: note}

## Configuration de l'interface IDE
{: #editorsetup}

{{site.data.keyword.webide}} est personnalisable : vous pouvez choisir les schémas de couleurs, les outils techniques et les paramètres correspondant à vos besoins de développement. Pour afficher et modifier les paramètres, dans la barre de navigation de gauche, cliquez sur l'icône **Paramètres** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Icône Paramètres">.

Si vous changez souvent certains paramètres au cours de l'édition, vous pouvez accéder à ces paramètres rapidement via l'icône **Paramètres de l'éditeur local**
<img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Icône Paramètres de l'éditeur local">.

![Paramètres de l'éditeur local](images/webide_local_editor_settings_light.png)

Par défaut, les paramètres de style et de taille de police de l'éditeur sont toujours affichés. Pour inclure d'autres paramètres de l'éditeur dans le menu, procédez comme suit :

1. Cliquez sur l'icône **Paramètres de l'éditeur local** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Icône Paramètres de l'éditeur local">.

2. Cliquez sur **Paramètres de l'éditeur**.

3. Pour inclure ou exclure un paramètre du menu **Paramètres de l'éditeur local**, cliquez sur l'étoile en regard de chaque paramètre.

![Activation/désactivation des Paramètres de l'éditeur](images/webide_editor_settings_toggle_light.png)


## Edition de code
{: #editcode}

{{site.data.keyword.webide}} comporte deux sections principales. La première section correspond au navigateur de fichiers, qui affiche vos fichiers de projet dans une structure arborescente. Depuis le navigateur de fichiers, vous pouvez créer, renommer, supprimer et gérer vos fichiers et dossiers.

Pour télécharger des fichiers dans le navigateur de fichiers, faites-les glisser depuis votre ordinateur vers le navigateur.
{: tip}

La seconde section correspond à la sous-fenêtre de l'éditeur. L'éditeur fournit plusieurs fonctions de codage, notamment l'assistant de contenu et la validation de la syntaxe.

![Web IDE](images/webide_light.png)

### Utilisation de plusieurs fichiers
1. Pour utiliser deux fichiers en même temps, cliquez sur l'icône **Changer le mode de fractionnement de l'éditeur**
<img class="inline" src="images/webide_split_editor_icon_light_small.png"  alt="Icône de fractionnement de l'éditeur">.
2. Dans le menu qui s'ouvre, sélectionnez une vue.

 Une fois que vous avez sélectionné une vue, si un fichier était déjà ouvert dans l'éditeur, il s'affiche dans les deux vues.

 Pour ouvrir ou changer un fichier affiché dans l'une des vues de l'éditeur :
 1. Placez le curseur sur la vue que vous souhaitez changer.
 2. Dans le navigateur de fichiers, cliquez sur un fichier.

### Raccourcis-clavier
De nombreuses commandes {{site.data.keyword.webide}} sont accessibles via des raccourcis-clavier.

Pour afficher la liste des raccourcis-clavier dans l'éditeur, cliquez sur **Outils** > **Afficher des outils**. Vous pouvez aussi afficher la liste en appuyant sur Alt+Maj+?, ou sur MacOS, en appuyant sur Ctrl+Maj+?. Vous pouvez personnaliser un raccourci en survolant la touche, en cliquant sur le crayon et en tapant la nouvelle définition de raccourci clavier.

## Gestion du code source
{: #sourcecontrol}

{{site.data.keyword.webide}} est intégré aux outils de gestion du code source. Pour utiliser votre référentiel Git, cliquez sur l'icône **Référentiel Git**
<img class="inline" src="images/webide_git_icon_light_small.png"  alt="Icône Référentiel Git">.  Pour en savoir plus, voir [Utilisation de Git dans Eclipse Orion Web IDE](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_web_ide#git_web_ide).

## Déploiement d'une application depuis votre espace de travail
{: #deploy}

1. Pour déployer votre application, depuis la barre d'exécution, sélectionnez ou créez une configuration de lancement.
   ![Barre d'exécution](images/webide_runbar_light.png)   
1. Cliquez sur l'icône de déploiement <img class="inline" src="images/webide_deploy_button_light_small.png"  alt="Icône de déploiement">. Une instance de votre application est déployée à l'aide du contenu actuel de votre espace de travail et de l'environnement défini dans votre configuration de lancement.
2. Une fois votre application déployée, vous pouvez utiliser la barre d'exécution pour arrêter, redémarrer ou déboguer votre application, consulter des journaux, etc.

<table role="presentation">
<tr><td><img src="./images/stop_button.png"  alt="Icône d'arrêt"></td><td>Arrêter l'application.</td></tr>
<tr><td> <img src="./images/open_app_url.png"  alt="Icône d'ouverture de l'URL de l'application"></td><td> Ouvrir l'application déployée.</td></tr>
<tr><td><img src="./images/view_logs.png"  alt="Icône d'affichage des journaux"></td><td>Afficher les journaux de l'application déployée.</td></tr>
<tr><td><img src="./images/open_dashboard.png"  alt="Icône d'ouverture du tableau de bord"></td><td>Ouvrir le tableau de bord de l'application.</td></tr>
</table>

Si vous développez une application Node.js, activez le mode Edition directe : <img  src="./images/enable_live_edit.png"  alt="Curseur d'activation de l'édition directe">

<table role="presentation"><tr><td><img src="./images/live_edit_restart.png"  alt="Icône de redémarrage de l'édition directe"></td><td>Activez le mode Edition directe pour redémarrer l'application rapidement, sans nécessité de redéploiement.</td></tr>
<tr><td> <img src="./images/debug_icon.png"  alt="Icône de débogage"></td>
<td>En mode Edition directe, accédez au débogueur.
</td></tr>
</table>

## Langages pris en charge
{: #supported_languages}

Eclipse Orion {{site.data.keyword.webide}} fournit une aide au contenu, des infobulles, des prévisualisations, une validation et une syntaxe pour les fichiers JavaScript, HTML, CSS et Markdown. Vous pouvez également mettre en évidence la syntaxe pour ces types de fichiers :

<table role="presentation">
<tr>
<td>
<ul><li>Arduino
</li><li>C</li>
<li>C#
</li><li>C++
</li><li>CoffeeScript
</li><li>CSHTML
</li><li>Embedded JavaScript (ejs)
</li><li>Erlang
</li><li>Go
</li><li>HTML abstraction markup language (Haml)
</li><li>Jade
</li><li>Java
</li><li>JSON
</li><li>Less  
</li><li>Lua  
</li><li>Objective-C
</li><li>PHP
</li><li>Python</li></ul>
</td>
<td>
<ul><li>Ruby
</li><li>Sass/SCSS
</li><li>SQL
</li><li>Swift
</li><li>TypeScript
</li><li>Visual Basic (vb)
</li><li>VMHTML
</li><li>XHTML
</li><li>XML
</li><li>XQuery
</li><li>YAML
</li><li>Launch file 	
</li><li>Dockerfile
</li><li>gitignore
</li><li>git config
</li><li>cfignore
</li><li>properties
</li></ul>
</td>
</tr>
</table>

## Suivre un tutoriel : Eclipse Orion Web IDE
{: #toolchain_web_ide_tutorials}

Consultez l'un des tutoriels suivants sur [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external} :

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. 
