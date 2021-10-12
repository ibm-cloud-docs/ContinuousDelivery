---

copyright:
  years: 2015, 2020
lastupdated: "2020-12-07"

keywords: troubleshoot, Live Edit, Web IDE

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Troubleshooting for {{site.data.keyword.webide}}
{: #troubleshoot-web-ide}

General problems with using the Eclipse Orion {{site.data.keyword.webide}} might include issues with Live Edit mode. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}


## Why is Live Edit unavailable after I commit and push to a repo?
{: #troubleshoot-liveedit}
{: troubleshoot}

When you deploy outside of the Eclipse Orion {{site.data.keyword.webide}}, Live Edit mode is cleared.

You commit and push a change from the command line or the {{site.data.keyword.webide}} and Live Edit is unavailable.
{: tsSymptoms}
   
When you create a toolchain that contains both a {{site.data.keyword.contdelivery_short}} pipeline and the {{site.data.keyword.webide}}, both tool integrations can deploy your application (app). By default, both the pipeline and the {{site.data.keyword.webide}} deploy to the same Cloud Foundry org and space, by using the same Cloud Foundry app and URL. When you deploy outside of the {{site.data.keyword.webide}}, Live Edit mode is cleared.
{: tsCauses}

To rapidly develop a test version of your app by using Live Edit, deploy to a different Cloud Foundry app, space, and URL from the {{site.data.keyword.webide}}. When your code changes are complete, you can commit and push the code to trigger the pipeline to build and deploy the production version of your app.
{: tsResolve}

1. From the run bar, select the launch configuration that you want to edit.
2. Edit the values that are specified for Space and Host.
3. Click **Save** and **Exit**.
4. Click the **Run** button in the run bar. You might need to deploy multiple times to enable the Live Edit button.

For more information about Live Edit, see [Live Edit](/docs/ContinuousDelivery?topic=ContinuousDelivery-live-sync#live-edit).


## What does "not synchronized" mean in the {{site.data.keyword.webide}} run bar?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

The file system in your workspace is out of sync.

In Live Edit mode, the {{site.data.keyword.webide}} synchronizes files from your workspace with the running Cloud Foundry app and the files are out of sync.
{: tsSymptoms}
   
The file system in your workspace might become out of sync if the app is modified outside of the {{site.data.keyword.webide}}. It can also become out of sync if the {{site.data.keyword.webide}} can't retrieve the synchronization state from the app.
{: tsCauses}

The state might clear after a minute or two when normal communications are reestablished and the files are synchronized. Otherwise, you can start and stop the app with Live Edit mode enabled.
{: tsResolve}
