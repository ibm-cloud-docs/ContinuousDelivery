---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-14"

keywords: ADD STAGE, Run Stage icon, JOBS tab

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Génération et déploiement
{: #deliverypipeline_build_deploy}

{{site.data.keyword.contdelivery_full}} inclut Delivery Pipeline, que vous pouvez utiliser pour implémenter un processus de distribution continue et d'intégration continue reproductibles.
{:shortdesc}

Pour configurer un pipeline, procédez comme suit :

## Ajout d'une étape
{: #deliverypipeline_add_stage}

1. Sur la page Pipeline, cliquez sur **Ajouter une étape**. La page Configuration d'étape s'ouvre.
2. Configurez l'étape.
  1. Sur l'onglet **Entrée**, sélectionnez une entrée pour l'étape.  Pour l'étape de génération, l'onglet d'entrée inclut une zone **Branche** pour spécifier la branche dans le référentiel à utiliser pour l'entrée.
  2. Sur l'onglet **Travaux**, ajoutez et configurez au moins un travail. Généralement, la première étape comporte au moins un travail de génération.
3. Cliquez sur **SAUVEGARDER**.

## Ajout d'un travail à une étape
{: #deliverypipeline_add_job}

1. Sur l'étape, cliquez sur l'icône **Configuration de l'étape**, puis sur **Configurer l'étape**.
2. Cliquez sur l'onglet **Travaux**.
3. Cliquez sur **Ajouter un travail**. Sélectionnez le type de travail à ajouter.
4. Configurez le travail.
5. Cliquez sur **SAUVEGARDER**.

![Ajout d'un travail à une étape](images/AddJob2.png)

## Exécution d'une étape
{: #deliverypipeline_run_stage}

Vous pouvez lancer manuellement une étape en cliquant sur l'icône **Exécuter une étape** sur la page Pipeline.

![Utilisation de l'icône Exécuter une étape](images/RunStage.png)

Vous pouvez également demander des générations et des déploiements à la demande depuis la page de l'historique de génération de l'une des deux façons suivantes :
* Faites glisser une génération vers la zone située sous une étape configurée.
* Dans la section Résultat de la dernière exécution, cliquez sur l'icône **Envoyer à**, puis sélectionnez un espace dans lequel effectuer le déploiement.
  ![Etape d'exécution avec cette icône de génération](images/deploy_to.png)

Pour annuler une étape d'exécution, sur l'étape, cliquez sur **Afficher les journaux et l'historique**. Dans la liste de travaux, cliquez sur le numéro du travail en cours d'exécution, puis cliquez sur **ANNULER**. Vous pouvez également annuler des travaux individuellement en cliquant sur un travail, puis en cliquant sur **ANNULER** ou en cliquant sur l'icône **Arrêter** d'un travail sur son étape.

## Déploiement d'une application
{: #deliverypipeline_deploy}

Un travail de déploiement correctement configuré déploie votre application sur votre cible chaque fois que le travail est exécuté. Pour exécuter manuellement un travail de déploiement, cliquez sur l'icône **Exécuter une étape** de l'étape dans laquelle se trouve le travail.

### Révisions d'entrée
{: #deliverypipeline_input_revisions}

Lorsque vous exécutez une étape manuellement, ou si elle s'exécute car l'étape qui la précède est terminée, l'étape en cours d'exécution sélectionne sa révision d'entrée. Généralement, la révision d'entrée est un numéro de version. Pour
sélectionner la révision d'entrée, l'étape suit les conditions ci-après :

* Si une révision spécifique est sélectionnée, utilisez-la.
* Si aucune révision n'est spécifiée, recherchez les étapes précédentes jusqu'à ce qu'une étape utilisant la même entrée soit trouvée. Recherchez et utilisez la dernière révision d'exécution réussie de cette entrée.
* Si aucune révision n'est spécifiée ni aucune autre étape, utilisez la source indiquée comme entrée, utilisez la révision la plus récente comme entrée.

Vous pouvez déployer une version précédente. A l'étape qui contient la version, cliquez sur **Afficher les journaux et l'historique**. Sur la page qui s'ouvre, cliquez pour développer le numéro d'exécution, puis cliquez sur le travail de génération. Cliquez sur **ENVOYER A** et sélectionnez une cible.
{: tip}

### Ajout de services à des applications
{: #deliverypipeline_add_services}

Vous pouvez ajouter des services à vos applications et gérer ces services à partir de votre tableau de bord {{site.data.keyword.Bluemix_notm}} ou de l'interface de ligne de commande Cloud Foundry. Vous pouvez également exécuter des commandes d'interface de ligne de commande Cloud Foundry dans des scripts pour les travaux de pipeline. Par exemple, vous pouvez ajouter un service à une application dans le script d'un travail de déploiement. Pour plus d'informations sur l'ajout de services, voir [Connexion de services à des applications externes](/docs/resources?topic=resources-externalapp).

## Affichage des journaux
{: #deliverypipeline_view_logs}

Vous pouvez afficher les journaux de travaux et consulter les étapes à mesure qu'elles s'exécutent sur la page Historique des étapes.

1. Pour afficher le journal d'un travail, cliquez sur celui-ci. Sinon, sur une étape, cliquez sur **Afficher les journaux et l'historique**.

2. Pour afficher le journal d'exécution d'une application déployée, cliquez sur **Afficher le journal d'exécution**.

Outre les journaux des travaux, vous pouvez afficher les résultats de tests unitaires, les artefacts générés et les modifications de code pour n'importe quel travail de génération.

Vous pouvez également exécuter, redéployer, annuler ou configurer une étape dans la page Historique des étapes. Cliquez sur **EXECUTER** pour exécuter l'étape, sur **REDEPLOYER** pour redéployer s'il s'agit d'un travail de déploiement ou sur **CONFIGURER** pour configurer une étape. Pendant qu'une étape est en exécution,
vous pouvez l'annuler en cliquant sur son numéro, puis sur **Annuler**.

### Téléchargement des journaux à partir d'un script
{: #deliverypipeline_download_logs}

Vous pouvez télécharger le fichier journal d'un travail de pipeline à partir d'un script et enregistrer le `PIPELINE_LOG_URL` qui est fourni lors de l'exécution du travail de pipeline. L'exemple suivant montre les étapes à suivre pour télécharger le fichier journal du travail de pipeline vers un système différent.


1. Configurez une propriété d'environnement `JOB_LOG` pour votre étape.

1. Dans votre travail de pipeline, enregistrez le `PIPELINE_LOG_URL`.

   ```shell
   export JOB_LOG="$PIPELINE_LOG_URL"
   ```
1. Utilisez le `PIPELINE_LOG_URL` dans un travail ultérieur de la même étape pour télécharger le fichier journal afin de l'exporter vers un système différent. Utilisez un jeton bearer IBM Cloud pour accéder au fichier journal.

   ```shell
   ibmcloud login -a cloud.ibm.com \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   curl -H "Authorization: Bearer $BEARER"  \
     -H "Accept: text/plain" \
     -D /tmp/headers.txt \
     -o job_log.txt \
     "$JOB_LOG"
   ```
1. Vérifiez l'en-tête `X-More-Data`. Si l'en-tête est défini sur `true`, le fichier journal est en cours de génération ou de traitement. Si l'en-tête est défini sur `false`, le fichier journal est prêt a être utilisé.

   ```shell
   grep X-More-Data /tmp/headers.txt
   X-More-Data: false
   ```
1. Téléchargez le fichier journal vers votre système.

   ```shell
   scp job_log.txt user@example.org:/job1/logs
   ```


### Téléchargement des artefacts à partir d'un script
{: #deliverypipeline_download_artifacts}

Vous pouvez télécharger les artefacts pour un travail de génération de pipeline à partir d'un script et enregistrer le `PIPELINE_ARTIFACT_URL` qui est fourni lors de l'exécution du travail de pipeline. L'exemple suivant montre les étapes à suivre pour télécharger les artefacts du travail de pipeline vers un système différent.


1. Configurez une propriété d'environnement `JOB_ARTIFACT` pour votre étape.

1. Dans votre travail de pipeline, enregistrez le `PIPELINE_ARTIFACT_URL`.

   ```shell
   export JOB_ARTIFACT="$PIPELINE_ARTIFACT_URL"
   ```
   
1. Utilisez le `PIPELINE_ARTIFACT_URL` dans un travail ultérieur de la même étape pour télécharger les artefacts afin de les exporter vers un système différent. Utilisez un jeton bearer IBM Cloud pour accéder aux artefacts.

   ```shell
   ibmcloud login -a cloud.ibm.com \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   DOWNLOAD_URL=$( curl -H "Authorization: Bearer $BEARER"  \
     "$JOB_ARTIFACT" )

   curl -O  "$DOWNLOAD_URL"
   ```
   
1. Téléchargez les artefacts vers votre système.

   ```shell
   scp $(basename "$DOWNLOAD_URL") user@example.org:/job1/artifacts
   ```
