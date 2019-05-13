---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-11"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Traitement des incidents dans {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

Lorsque vous utilisez {{site.data.data.keyword.contdelivery_full}}, vous pouvez rencontrer des problèmes lors de l'authentification GitHub, la création d'un pipeline, la configuration de l'intégration d'outils ou avec Cloud Foundry. Dans de nombreux cas, vous pouvez résoudre ces problèmes en suivant quelques étapes simples.
{:shortdesc}

## J'ai essayé d'ajouter l'intégration d'outils GitHub à ma chaîne d'outils, pourquoi l'intégration d'outils n'a-t-elle pas été ajoutée ?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

Vous devez permettre l'accès à GitHub pour qu'{{site.data.data.keyword.Bluemix_notm}} soit autorisé à accéder à votre compte GitHub.

L'intégration d'outils GitHub n'a pas été ajoutée à votre chaîne d'outils.
{: tsSymptoms}

Si {{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à votre compte GitHub, l'intégration d'outils n'est pas ajoutée à votre chaîne d'outils.
{: tsCauses}

Si vous configurez l'intégration d'outils GitHub pendant que vous créez votre chaîne d'outils, suivez les étapes suivantes pour autoriser l'accès à GitHub :
{: tsResolve}

  1. A la section Intégrations configurables, cliquez sur **GitHub**.
  1. Si vous créez la chaîne d'outils sur {{site.data.keyword.Bluemix_notm}} Public et si {{site.data.keyword.Bluemix_notm}} n'est pas autorisé à accéder à GitHub, cliquez sur **Autorisation** pour accéder au site Web GitHub.
  1. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub.

Si vous disposez déjà d'une chaîne d'outils, mettez à jour la configuration de l'intégration d'outils GitHub :

 1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils afin d'ouvrir sa page Vue
d'ensemble. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
 1. Sur la carte GitHub, cliquez sur le menu, puis sur **Configurer**.
 1. Mettez à jour les paramètres de configuration pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à GitHub. Cliquez sur **Autoriser** pour accéder au site Web GitHub. Si vous n'avez pas de session GitHub active, vous êtes invité à vous connecter. Cliquez sur **Authorize Application** pour autoriser {{site.data.keyword.Bluemix_notm}} à accéder à votre compte GitHub.
 1. Lorsque vous avez terminé la mise à jour des paramètres, cliquez sur **Sauvegarder l'intégration**.
 

## Pourquoi ne puis-je pas utiliser l'intégration d'outil de {{site.data.keyword.gitrepos}} de la chaîne d'outils de ma région dans une chaîne d'outils appartenant à une autre région ?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

Vous ne pouvez pas utiliser une instance de {{site.data.data.gitrepos}} dans plusieurs régions.

Lorsque j'essaie d'ajouter l'intégration d'outil de {{site.data.data.keyword.gitrepos}} à ma chaîne d'outils, je reçois le message d'erreur suivant :
{: tsSymptoms}

`URL de référentiel non valide. Le référentiel doit se trouver sur {URL GitLab locale}.`

où `{URL GitLab locale}` est l'URL de l'intégration d'outil de {{site.data.keyword.gitrepos}} de la région dans laquelle réside la chaîne d'outils.
   
Etant donné que {{site.data.keyword.gitrepos}} est étroitement intégré au service {{site.data.keyword.contdelivery_short}} dans la région dans laquelle ils sont exécutés, vous ne pouvez pas utiliser une instance {{site.data.data.keyword.gitrepos}} dans plusieurs régions.
{: tsCauses}

Au lieu de créer une intégration d'outil dans {{site.data.keyword.gitrepos}}, créez une intégration GitLab générique et utilisez cette intégration pour pointer vers le référentiel {{site.data.keyword.gitrepos}} dans une région différente.
{: tsResolve}

1. Sur le tableau de bord DevOps, sur la page Chaînes d'outils, cliquez sur la chaîne d'outils à laquelle vous souhaitez ajouter cette intégration. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**, puis sur **Présentation**.
1. Cliquez sur **Ajouter un outil**.
1. Dans la section Intégrations d'outils, cliquez sur **GitLab**.
1. Cliquez sur le serveur GitLab que vous souhaitez utiliser. Si le serveur GitLab où réside le référentiel auquel vous souhaitez accéder n'apparaît pas dans cette liste, ajoutez un serveur personnalisé : 

 a. Cliquez sur **Ajouter un serveur personnalisé**.

 b. Entrez un nom pour le serveur. Ce nom de serveur apparaîtra dans la liste des serveurs GitLab disponibles.
 
 c. Entrez l'adresse URL racine du serveur GitLab personnalisé.
 
 d. Entrez un jeton d'accès personnel de votre serveur GitLab personnalisé. Si vous n'avez pas de jeton d'accès personnel, [créez-en un](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat).
 
 e. Cliquez sur **Sauvegarder l'intégration personnalisée**.
 
1. Si vous disposez d'un référentiel GitLab et désirez l'utiliser, cliquez sur **Existant** pour le type de référentiel et saisissez l'URL.
1. Si vous souhaitez utiliser un nouveau référentiel GitLab, indiquez un nom pour le référentiel, entrez l'URL du référentiel que vous clonez ou déviez, puis sélectionnez le type de référentiel :

 a. Pour créer un référentiel vide, cliquez sur **Nouveau**.

 b. Pour créer une copie d'un référentiel GitLab, cliquez sur **Cloner**.

 c. Pour dévier un référentiel GitLab afin de pouvoir participer aux modifications via des demandes d'extraction, cliquez sur **Dévier**.

1. Si vous souhaitez créer un référentiel public sur le serveur, désélectionnez la case **Rendre ce référentiel privé**.
1. Si vous souhaitez utiliser GitLab Issues pour le suivi des problèmes, sélectionnez la case **Activer GitLab Issues**.
1. Si vous voulez suivre le déploiement des modifications du code en créant des étiquettes et des commentaires sur les validations, ainsi que des libellés et des commentaires sur les problèmes référencés par les validations, cochez la case **Suivi du déploiement des modifications du code**. Pour plus d'informations, voir [Suivi de l'emplacement du déploiement du code avec des chaînes d'outils ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Cliquez sur **Créer une intégration**.

Pour en savoir plus sur la configuration d'une intégration d'outil GitLab, voir [Configuration de GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab).


## Pourquoi ne puis-je pas créer une chaîne d'outils à partir d'un modèle qui utilise un référentiel privé dans une autre région ?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

Le modèle de chaîne d'outils que vous utilisez fait référence à un référentiel {{site.data.keyword.gitrepos}} privé.

{{site.data.keyword.gitrepos}} est spécifique à une région. Lorsque vous essayez de créer une chaîne d'outils à partir d'un modèle et de cibler une région dans laquelle le référentiel privé n'est pas situé, la configuration de l'intégration Git échoue.
{: tsSymptoms}
   
Lorsque vous ajoutez un référentiel {{site.data.data.keyword.gitrepos}} à une chaîne d'outils dans une région spécifique, votre identifiant IBM est associé à un nom d'utilisateur GitLab qui vous donne accès au GitLab dans cette région. Même si votre nom d'utilisateur GitLab est le même dans toutes les régions, l'utilisateur GitLab associé est différent dans chaque région car chaque région a une installation séparée de GitLab. L'accès aux utilisateurs de GitLab dans d'autres régions n'est pas automatiquement accordé aux chaînes d'outils même lorsque le nom d'utilisateur GitLab semble être le même.
{: tsCauses}

Rendez public le référentiel {{site.data.data.site.gitrepos}} afin qu'il soit accessible de n'importe où, y compris à partir d'autres régions {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Si le référentiel doit être privé, le propriétaire du référentiel peut y donner accès en créant un [jeton d'accès personnel](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) sur le serveur GitLab où le référentiel source est situé. Vous n'avez besoin d'accéder qu'au référentiel privé pour cloner le contenu lors de la création de la chaîne d'outils. Le jeton d'accès personnel peut être créé avec une date d'expiration pour limiter sa durée de vie à un jour. 

Une fois que vous avez un jeton d'accès personnel, vous pouvez créer une URL pour accéder au référentiel à partir d'autres régions. Pendant que vous configurez l'intégration d'outil, dans la zone **URL du référentiel source**, mettez à jour l'URL du référentiel avec votre nom d'utilisateur et votre jeton d'accès.

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

où `user` est votre nom d'utilisateur GitLab, `XXXXXXX` est le jeton d'accès, [`group` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window} est le groupe où le référentiel est stocké et `node-hello-world` est le nom du référentiel.

Si votre référentiel GitLab n'est pas situé dans un groupe GitLab, la valeur de `group` est la même que votre nom d'utilisateur.
{: tip}


## Pourquoi ne puis-je pas cloner mon référentiel {{site.data.keyword.gitrepos}} sur https ?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Vous devez utiliser un jeton d'accès personnel ou une clé SSH pour effectuer des opérations Git.

Vous essayez d'envoyer ou de cloner un référentiel à partir de la ligne de commande en utilisant https et vous ne pouvez pas vous authentifier même si le mot de passe que vous entrez est correct.
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} utilise un mécanisme de connexion unique qui ne prend pas en charge l'authentification Git qui utilise un nom d'utilisateur et un mot de passe sur la ligne de commande.
{: tsCauses}

Pour effectuer des opérations Git comme des opérations de clonage ou d'envoi, vous devez utiliser un jeton d'accès personnel ou une clé SSH. Pour en savoir plus sur la création d'un jeton d'accès personnel, voir le [tutoriel d'initiation](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## Pourquoi me demande-t-on de m'authentifier lorsque j'essaie de cloner mon référentiel {{site.data.keyword.gitrepos}} avec SSH ?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

Il est possible qu'il y ait des problèmes au niveau de l'emplacement ou des autorisations de votre clé privée SSH, ou que la ligne de commande Git n'utilise pas votre clé privée SSH pour s'authentifier dans {{site.data.keyword.gitrepos}}.

J'ai ajouté ma clé publique SSH via l'interface utilisateur {{site.data.keyword.gitrepos}}. Lorsque j'essaie de cloner un référentiel avec SSH, un mot de passe ou un code de sécurité m'est demandé ou un message d'erreur s'affiche indiquant que l'authentification a échoué.
{: tsSymptoms}
   
Les problèmes SSH suivants peuvent vous inviter à vous authentifier ou faire apparaître un message d'erreur :
{: tsCauses}

* La ligne de commande Git peut ne pas utiliser votre clé privée SSH pour s'authentifier dans {{site.data.keyword.gitrepos}}.

* Votre clé privée SSH n'est peut-être pas dans l'emplacement par défaut ~/.ssh/id_rsa.

* Votre clé privée SSH peut ne pas avoir les autorisations correctes (600).


Utilisez l'une des méthodes suivantes pour résoudre ce problème :
{: tsResolve}

* Si vous utilisez l'emplacement par défaut de la clé SSH privée, vérifiez les autorisations pour le dossier ~/.ssh/ et le fichier de clé privée ~/.ssh/id_rsa. Si les autorisations sont trop vastes, SSH n'utilise pas de clé privée par défaut. Assurez-vous que les autorisations pour le dossier ~/.ssh/ sont définies à 700 et que les autorisations pour le dossier ~/.ssh/id_rsa sont définies à 600.

* Si votre clé privée n'est pas dans l'emplacement par défaut, utilisez la commande suivante pour la spécifier dans une variable d'environnement :

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* Pour résoudre ce problème en utilisant les informations de connexion, ajoutez l'indicateur -vv ou -vvv à la variable d'environnement `GIT_SSH_COMMAND` :

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## J'ai essayé d'ajouter un utilisateur à mon projet GitLab par email, mais il n'a pas reçu l'invitation. Comment puis-je l'ajouter à mon projet ?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

L'invitation a pu être bloquée par la messagerie de l'utilisateur.

J'ai invité un utilisateur à mon projet GitLab en utilisant son adresse e-mail qui est listée dans {{site.data.keyword.gitrepos}}, mais il n'a pas reçu l'e-mail.
{: tsSymptoms}
   
L'e-mail a peut-être été bloqué par le filtre antispam de la boîte de réception de l'utilisateur.
{: tsCauses}

Vous pouvez utiliser l'une des méthodes suivantes pour résoudre ce problème :
{: tsResolve}

* Consultez de dossier spam de votre messagerie pour déterminer si le courrier d'invitation a été marqué en tant que spam. Les e-mails sont envoyés à partir d'une adresse noreply@. Mettez à jour vos filtres antispam pour autoriser les e-mails en provenance de cette adresse.

* Vérifiez si les filtres anti-spam de l'entreprise qui sont hors du contrôle de l'utilisateur bloquent l'e-mail. Demandez à l'utilisateur de se connecter à l'interface utilisateur de {{site.data.keyword.gitrepos}} et de vous envoyer son ID utilisateur. Vous pouvez ajouter l'utilisateur au projet GitLab en utilisant son ID utilisateur.


## Pourquoi le pipeline n'est-il pas créé correctement lorsque je crée une chaîne d'outils à partir du modèle que j'écris ? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

Il se peut que votre pipeline manque de ressources telles que des travaux et des étapes en raison d'une erreur dans la définition de votre fichier pipeline.yaml.

Lorsque j'essaie de créer une chaîne d'outils à partir d'un modèle que j'écris, je reçois le message d'erreur suivant sur la page Pipeline :
{: tsSymptoms}

`Ce pipeline a été créé, mais il manque peut-être des travaux, des étapes ou d'autres ressources. Vous pouvez utiliser ce pipeline, ou si vous préférez, vous pouvez le supprimer et en créer un autre.`

Ce problème est généralement causé par une erreur dans la définition de votre fichier pipeline.yaml.
{: tsCauses}
   
Vous pouvez utiliser les méthodes suivantes pour corriger cette erreur :
{: tsResolve}

* Utilisez l'interface utilisateur du pipeline pour créer un exemple de pipeline qui réplique le pipeline que vous essayez de construire avec votre modèle. Ajoutez `/yaml` à l'URL du pipeline pour générer un fichier pipeline.yaml similaire que vous pouvez utiliser pour rechercher les différences évidentes. Par exemple, `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`.

* Utilisez le mécanisme de création de chaîne d'outils sans interface graphique. Sur la page **Créer une chaîne d'outils**, ouvrez le débogueur et évaluez l'expression `window.Testflags = {nocreate: 1}`. Lorsque vous cliquez sur **Créer une chaîne d'outils** dans ce mode, la chaîne d'outils n'est pas créée. Au lieu de cela, les informations qui sont transmises à l'API sont renvoyées à la console où vous pouvez les examiner.


## J'ai configuré une intégration d'outil pour ma chaîne d'outils, pourquoi n'a-t-elle pas été configurée ?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

Si une erreur se produit pendant le processus de configuration ou si la communication entre la chaîne d'outils et l'outil ne se termine pas correctement, la configuration échoue.

Après avoir ajouté et configuré une intégration d'outil pour votre chaîne d'outils, un message d'erreur s'affiche pour indiquer que la configuration a échoué.
{: tsSymptoms}

Lorsque vous ajoutez une intégration d'outil, la chaîne d'outils communique avec l'outil qui est représenté par l'intégration d'outil pour mettre à disposition les ressources nécessaires et les associer à la chaîne d'outils. Si une erreur se produit pendant le processus de configuration ou si la communication entre la chaîne d'outils et l'outil ne s'établit pas correctement, l'intégration d'outil passe à l'état d'erreur.
{: tsCauses}

 ![Erreur Echec de la configuration](images/tool_setup_failed.png)

Vous pouvez tenter de reconfigurer l'intégration d'outil :
{: tsResolve}

1. Sur sa carte d'outil, survolez le message `Echec de la configuration` et cliquez sur **Reconfigurer**.

 ![Bouton Reconfigurer](images/tool_reconfigure.png)

1. Assurez-vous que vous utilisez des paramètres de configuration valides. Si l'erreur est due à une configuration non valide, un message d'erreur s'affiche, par exemple : `Impossible de configurer l'intégration. Vérifiez les paramètres puis réessayez. Motif : api_key:fakeKey non valide`. Mettez à jour les paramètres de l'intégration
d'outil et cliquez sur **Sauvegarder l'intégration**.
1. Si l'erreur a été provoquée par un problème de communication, cliquez sur **Sauvegarder l'intégration** pour réessayer.


## Pourquoi ne puis-je pas ajouter {{site.data.keyword.contdelivery_short}} à une organisation Cloud Foundry ?
{: troubleshoot-resource_groups}
{: troubleshoot}

Vous ne pouvez plus créer des instances du service {{site.data.keyword.contdelivery_short}} dans les organisations Cloud Foundry. 

Le message suivant s'affiche sur la page Chaînes d'outils pour votre chaîne d'outils dans une organisation Cloud Foundry :
{: tsSymptoms}

`Le service Continuous Delivery est requis : Ajoutez le service à votre groupe de ressources pour garantir l'utilisation ininterrompue des fonctions du service.` 

Lorsque vous cliquez sur **Ajouter le service**, il n'est pas possible de créer {{site.data.keyword.contdelivery_short}} dans une organisation Cloud Foundry. Vous pouvez uniquement créer {{site.data.keyword.contdelivery_short}} dans un groupe de ressources.

Les groupes de ressources ont remplacé les organisations Cloud Foundry comme conteneurs préférés pour les instances de service. Cependant, vous pouvez continuer de créer des chaînes d'outils dans les organisations Cloud Foundry pour prendre en charge les instances {{site.data.keyword.contdelivery_short}} préexistantes dans les organisations Cloud Foundry.
{: tsCauses}

Créez votre chaîne d'outils à nouveau dans les groupes de ressources puis supprimez la chaîne d'outils originale de l'organisation Cloud Foundry. Vous pouvez également ignorer le message d'erreur jusqu'à ce qu'une méthode permettant de migrer les chaînes d'outils existantes des organisations Cloud Foundry aux groupes de ressources soit fournie.
{: tsResolve}


## Pourquoi n'est-il pas possible de supprimer les chaînes d'outils à l'aide de l'interface de ligne de commande `ibmcloud` ?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

Actuellement, vous ne pouvez pas supprimer les chaînes d'outils à l'aide de l'interface de ligne de commande ibmcloud resource. 

J'ai essayé de supprimer une chaîne d'outils à partir de la ligne de commande à l'aide de la commande `ibmcloud resource service-instance-delete` et la commande échoue avec le message d'erreur suivant :
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

Les chaînes d'outils sont un type de ressource spéciale sur la plateforme Cloud que vous ne pouvez pas supprimer actuellement à l'aide de l'interface de ligne de commande `ibmcloud resource`.
{: tsCauses}

Pour supprimer une chaîne d'outils :
{: tsResolve}

1. Dans le tableau de bord DevOps, dans la page **Chaînes d'outils**, cliquez sur la chaîne d'outils à supprimer. Vous pouvez également, depuis la page de présentation de l'application, sur la carte Continuous delivery, cliquer sur **Afficher la chaîne d'outils**.
1. Cliquez sur le menu **Plus d'actions**, qui se trouve à côté du menu **Afficher l'appli**.
1. Cliquez sur **Supprimer**. La suppression d'une chaîne d'outils supprime toutes ses intégrations d'outils, et donc éventuellement les ressources gérées par ces intégrations.
1. Confirmez la suppression en entrant le nom de la chaîne d'outils et en cliquant sur **Supprimer**.  


## Pourquoi la fonction d'édition directe Live Edit n'est-elle pas disponible après une validation et un envoi vers un référentiel ?
{: #troubleshoot-liveedit}
{: troubleshoot}

Lorsque vous déployez en dehors d'Eclipse Orion {{site.data.keyword.webide}}, le mode Live Edit est désactivé.

Vous validez et envoyez une modification à partir d'une ligne de commande ou de {{site.data.keyword.webide}} et le mode Live Edit n'est pas disponible.
{: tsSymptoms}
   
Lorsque vous créez une chaîne d'outils contenant un pipeline {{site.data.keyword.contdelivery_short}} et {{site.data.keyword.webide}}, les deux intégrations d'outils peuvent déployer votre application. Par défaut, le pipeline et {{site.data.keyword.webide}} déploient vers la même organisation Cloud Foundry et le même espace, à l'aide de la même application Cloud Foundry et de la même URL. Lorsque vous déployez en dehors de {{site.data.keyword.webide}}, le mode Live Edit est désactivé.
{: tsCauses}

Pour développer rapidement une version test de votre application avec Live Edit, déployez vers une application Cloud Foundry, une URL et un espace différents de {{site.data.keyword.webide}}. Lorsque vos modifications de code sont terminées, vous pouvez valider et envoyer le code pour déclencher le pipeline pour générer et déployer la version de production de votre application.
{: tsResolve}

1. Dans la barre d'exécution, sélectionnez la configuration de lancement que vous souhaitez éditer.
2. Editez les valeurs qui sont spécifiées pour Espace et Hôte.
3. Cliquez sur **Sauvegarder** et **Quitter**.
4. Cliquez sur le bouton **Exécuter** dans la barre d'exécution. Vous aurez peut-être besoin de déployer plusieurs fois pour activer le bouton Live Edit.

Pour en savoir plus sur Live Edit, voir [Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit).


## Que signifie "non synchronisé" dans la barre d'exécution de {{site.data.keyword.webide}} ?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

Le système de fichiers de votre espace de travail n'est pas synchronisé.

Dans le mode Live Edit, {{site.data.keyword.webide}} synchronise les fichiers à partir de votre espace de travail avec l'application Cloud Foundry en cours d'exécution et les fichiers ne sont pas synchronisés.
{: tsSymptoms}
   
Le système de fichiers de votre espace de travail peut être désynchronisé si l'application est modifiée en dehors de {{site.data.keyword.webide}}. Il peut également être désynchronisé si {{site.data.keyword.webide}} ne peut pas récupérer l'état de synchronisation de l'application.
{: tsCauses}

L'état peut s'effacer après une minute ou deux lorsque les communications normales sont rétablies et que les fichiers sont synchronisés. Sinon, vous pouvez démarrer et arrêter l'application avec le mode Live Edit activé.
{: tsResolve}
