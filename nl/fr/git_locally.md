---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-8"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Configuration de clients locaux pour l'utilisation du contrôle des sources Git
{: #git_local}


Vous pouvez gérer votre code source dans un référentiel GitHub, GitHub Enterprise ou Git Repos and Issue Tracking, localement ou dans Eclipse Orion Web IDE. Pour travailler localement, clonez votre référentiel avec un client Git tel que l'interface de ligne de commande Git et éditez votre code avec l'éditeur de votre choix. Si vous travaillez dans Eclipse, vous pouvez installer le plug-in EGit pour le contrôle des versions.

## Clonage de votre projet Git à partir de la ligne de commande


## Avant de commencer
{: #git_before_clone}

1. Pour accéder au serveur Git en dehors du navigateur, il sera éventuellement nécessaire de créer un jeton d'accès personnel ou une clé SSH pour l'authentification. Le tableau suivant indique ce que vous devez faire pour configurer l'authentification.

| Type Git  | Configuration HTTPS | Utilisation HTTPS |  Configuration SSH |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com) | [Jeton d'accès personnel](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) | Nom d'utilisateur Git Repos and Issue Tracking (pas votre ID IBM) et jeton d'accès personnel | [Configurer la clé SSH](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) |
| Public GitHub (github.com) | Le jeton d'accès personnel n'est pas requis, mais vous pouvez en configurer un et l'utiliser | Nom d'utilisateur et mot de passe GitHub ou nom d'utilisateur GitHub et jeton d'accès personnel ou simplement jeton d'accès personnel comme nom d'utilisateur | [Configurer une clé SSH GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Jeton d'accès personnel](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started#ghe_auth) | Nom d'utilisateur GitHub Enterprise (pas votre ID IBM) et jeton d'accès personnel | [Configurer la clé SSH GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started#ghe_auth) |

Si vous préférez utiliser SSH, vous pouvez réutiliser une seule et même clé sur tous les serveurs Git. Créez ou recherchez votre clé et configurez-la dans chaque serveur comme indiqué dans les liens précédents. Si vous créez votre clé avec une phrase passe, vous êtes invité à entrer cette phrase passe lorsque vous utilisez la clé.
{: tip}

2. Si vous allez utiliser la ligne de commande Git, procédez comme suit :

    a. Vérifiez si Git est installé. Sur une ligne de commande, tapez `git version`. Si Git est installé, le numéro de version est affiché et vous pouvez commencer.

    b. Si Git n'est pas installé, [accédez au site Web de Git ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://git-scm.com/downloads){: new_window}.

    c. Téléchargez et installez la version pour votre système d'exploitation Vous pouvez accepter les valeurs d'installation par défaut.


### Clonage de votre projet
{: #git_clone}

Créez une copie locale des fichiers de projet en clonant le référentiel Git de manière à pouvoir accéder au contenu de votre référentiel en dehors de l'interface IDE Web à l'aide de n'importe quel outil du bureau.

1. A partir de la page de présentation de votre chaîne d'outils, cliquez sur la carte du référentiel que vous souhaitez cloner.

2. Constituez l'URL de votre référentiel :

   a. Dans GitHub, cliquez sur **Clone or download**. Pour utiliser HTTPS, sélectionnez **Use HTTPS**.  Pour utiliser SSH, cliquez sur **Use SSH**. Cliquez sur l'icône représentant un presse-papiers pour copier l'URL.

   b. Dans Git Repos and Issue Tracking, sélectionnez **HTTPS** ou **SSH** et copiez l'URL dans la zone.

3. Ouvrez une ligne de commande.

4. Passez dans le répertoire où vous souhaitez placer la copie locale du référentiel Git.

5. Tapez `git clone`, collez l'URL et appuyez sur Entrée.

6. Si vous êtes invité à vous authentifier, entrez les informations appropriées, comme indiqué dans le tableau précédent.


Une fois le téléchargement terminé, vous disposez d'une version locale des fichiers dans votre référentiel. Pour plus d'informations sur l'utilisation de Git, [voir la documentation de Git ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](http://git-scm.com/doc){: new_window}.


## Accès à votre référentiel à l'aide d'Eclipse et du plug-in EGit
{: #git_egit}

Si vous utilisez Eclipse et possédez un projet qui utilise Git pour le contrôle des sources, vous pouvez utiliser le plug-in EGit pour gérer votre référentiel à partir d'Eclipse. Pour savoir comment installer et configurer EGit, voir le [tutoriel EGit ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
Si vous rencontrez des difficultés lors de l'utilisation de Git Repos and Issue Tracking, voir [Git Repos and Issue Tracking](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_local).
