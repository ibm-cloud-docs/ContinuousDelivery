---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-27"

keywords: error message, toolchains, IBM Cloud, Web IDE, Live Sync

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# FAQs for {{site.data.keyword.webide}}
{: #faq_web_ide}

Get answers to frequently asked questions about using the Eclipse Orion {{site.data.keyword.webide}}.
{:shortdesc} 


## I created an app, why doesn't the run bar show {{site.data.keyword.cloud_notm}} Live Sync icons in the {{site.data.keyword.webide}}?
{: #ts_llz_lkb_3r}
{: faq}

![Run bar](images/webide_runbar_light.png)   

When you edit a Node.js app in the {{site.data.keyword.webide}}, the {{site.data.keyword.cloud_notm}} live edit, quick restart, and debug icons aren't available in the run bar in these circumstances:


* The `manifest.yml` file isn't stored at the top level of your project.
* Your app is stored in a subdirectory rather than root, but the path to the subdirectory isn't specified in the `manifest.yml` file.
* The app does not contain a `package.json` file.


If the `manifest.yml` file isn't stored at the root, store it there. If your app is stored in a subdirectory, specify the path to the subdirectory in the `manifest.yml` file. If the app doesn't contain a `package.json` file, create one that is in the same directory as your app.


## I clicked the {{site.data.keyword.webide}} run button, where are the log files? 
{: #web_ide_log_files}
{: faq}  

When you click the Run button, the contents of your workspace are pushed to Cloud Foundry in the same way that they are deployed if you type `cf push` from your desktop. You can find the log files from the Cloud Foundry dashboard.

For more information about deploying the contents of your workspace, see [Deploying an app from your workspace](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy).


## How do I prevent the {{site.data.keyword.webide}} from automatically selecting all of the changes in the Git view? 
{: #web_ide_git_view}
{: faq} 

The {{site.data.keyword.webide}} assumes by default that you want to push outgoing changes to your code repository each time that you go to the Git page. If you want to manually select which resources to commit, sync, reset, and replace, from the GIT preference page, clear the **Always select changed files** checkbox.


## Why doesn't the {{site.data.keyword.webide}} support the language that I use? 
{: #web_ide_language_support}
{: faq}  

The {{site.data.keyword.webide}} provides extensive tools and support for JavaScript, HTML, and CSS. It also provides syntax highlighting for most popular languages. You can't extend the {{site.data.keyword.webide}} to support a particular language. To view a complete list of the languages that the {{site.data.keyword.webide}} supports, see [Supported languages](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages).
