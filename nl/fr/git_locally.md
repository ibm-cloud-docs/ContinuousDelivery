---

copyright:
  years: 2015, 2017
lastupdated: "2017-7-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# Configuration de clients locaux pour l'utilisation du contrôle des sources Git
{: #git_local}


Vous pouvez gérer votre code source dans un référentiel GitHub, GitHub Enterprise ou Git Repos and Issue Tracking, localement ou dans Eclipse Orion Web IDE. Pour l'utiliser localement, clonez votre référentiel avec un client Git, tel que l'interface de ligne de commande Git, puis éditez votre code à l'aide de votre éditeur préféré. Si vous travaillez dans Eclipse, vous pouvez installer le plug-in EGit pour le contrôle des versions. 

## Clonage de votre projet Git à partir de la ligne de commande


## Avant de commencer
{: #git_before_clone}

1. Pour accéder au serveur Git en dehors de votre navigateur, vous devez créer un jeton d'accès personnel ou une clé SSH à des fins d'authentification. Le tableau suivant répertorie ce que vous devez faire pour configurer l'authentification. 

| Type Git   | Configuration HTTPS | Utilisation HTTPS |  Configuration SSH |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com) | [Jeton d'accès personnel](/docs/ContinuousDelivery/git_working.html#create_pat) | Nom d'utilisateur Git Repos and Issue Tracking (pas votre ID IBM) et jeton d'accès personnel | [Configurer la clé SSH](/docs/ContinuousDelivery/git_working.html#create_ssh) |
| Public GitHub (github.com) | Le jeton d'accès personnel n'est pas requis, mais vous pouvez en configurer un et l'utiliser | Nom d'utilisateur et mot de passe GitHub ou nom d'utilisateur GitHub et jeton d'accès personnel ou simplement jeton d'accès personnel comme nom d'utilisateur | [Configurer  une clé SSH GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Jeton d'accès personnel](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) | Nom d'utilisateur GitHub Enterprise (pas votre ID IBM) et jeton d'accès personnel | [Configurer la clé SSH GitHub Enterprise](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) |

**Remarque** : si vous préférez utiliser SSH, vous pouvez réutiliser une seule et même clé sur tous les serveurs Git. Créez ou recherchez votre clé et configurez-la dans chaque serveur comme indiqué dans les liens précédents. Si vous créez votre clé avec une phrase passe, vous serez invité à la saisir cette phrase passe lorsque vous utiliserez la clé. 

2. Si vous avez l'intention d'utiliser la ligne de commande Git, procédez comme suit :

    a. Vérifiez si Git est installé. Sur une ligne de commande, tapez `git version`. Si Git est installé, le numéro de version est affiché et vous pouvez commencer.

    b. Si Git n'est pas installé, [accédez au site Web de Git ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://git-scm.com/downloads){: new_window}.

    c. Téléchargez et installez la version pour votre système d'exploitation Vous pouvez accepter les valeurs d'installation par défaut. 


### Clonage de votre projet
{: #git_clone}

Créez une copie locale des fichiers de projet en clonant le référentiel Git de manière à pouvoir accéder au contenu de votre référentiel en dehors de l'interface IDE Web à l'aide de n'importe quel outil du bureau. 

1. A partir de la page de présentation de votre chaîne d'outils, cliquez sur la carte du référentiel que vous souhaitez cloner. 

2. Constituez l'URL de votre référentiel :

   a. Dans GitHub, cliquez sur **Clone or download**. Pour utiliser HTTPS, sélectionnez **Use HTTPS**. Pour utiliser SSH, cliquez sur  **Use SSH**. Cliquez sur l'icône représentant un presse-papiers pour copier l'URL. 

   b. Dans Git Repos and Issue Tracking, sélectionnez **HTTPS** ou **SSH** et copiez l'URL dans la zone.

3. Ouvrez une ligne de commande.

4. Passez dans le répertoire où vous souhaitez placer la copie locale du référentiel Git. 

5. Tapez `git clone`, collez l'URL et appuyez sur Entrée. 

6. Si vous êtes invité à vous authentifier, entrez les informations appropriées, comme indiqué dans le tableau précédent. 


Une fois le téléchargement terminé, vous disposez d'une version locale des fichiers dans votre référentiel. Pour plus d'informations sur l'utilisation de Git, [voir la documentation de Git ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](http://git-scm.com/doc){: new_window}.


## Accès à votre référentiel à l'aide d'Eclipse et du plug-in EGit
{: #git_egit}

Si vous utilisez Eclipse et possédez un projet qui utilise Git pour le contrôle des sources, vous pouvez utiliser le plug-in EGit pour gérer votre référentiel à partir d'Eclipse. Pour savoir comment installer et configurer EGit, voir [tutoriel EGit ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
Si vous rencontrez des difficultés lors de l'utilisation de Git Repos and Issue Tracking, voir [Git Repos and Issue Tracking](git_working.html#git_local).

## Développement à l'aide d'IBM Eclipse Tools
{: #git_eclipse_tools}

IBM Eclipse Tools for Bluemix fournit des plug-ins que vous pouvez installer dans un environnement Eclipse pour intégrer votre interface IDE à Bluemix.

Avec les outils, vous pouvez déployer les types de fichiers et de serveurs suivants sur le serveur Bluemix directement depuis votre interface Eclipse IDE ou d'IBM WebSphere&reg; Application Server Developer Tools (WDT):

* Fichiers JavaScript
* Fichiers WAR (archive Web)
* Fichiers EAR (archive d'entreprise)
* Serveurs de packages Liberty Profile

Vous pouvez également créer des services et les lier à votre application, et définir des variables d'environnement dans le cadre du déploiement. Pour plus d'informations sur IBM Eclipse Tools, [voir Déploiement d'applications à l'aide d'IBM Eclipse Tools for Bluemix](../../manageapps/eclipsetools/eclipsetools.html).
