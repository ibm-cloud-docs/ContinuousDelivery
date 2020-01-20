---

copyright:
  years: 2015, 2020
lastupdated: "2019-09-27"

keywords: Eclipse Orion {{site.data.keyword.webide}}, file types, Local Editor Settings icon, edit code, deploy apps, supported languages

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
{:table: .aria-labeledby="caption"}

# Developing with the Eclipse Orion Web IDE
{: #web_ide}

The Eclipse Orion {{site.data.keyword.webide}} is a browser-based development environment where you can develop for the web in JavaScript, HTML, and CSS with the help of content assist, code completion, and error checking. The {{site.data.keyword.webide}} works with nearly any language and you can highlight syntax for most file types. Source control is built in, and you can deploy code locally to test and debug your apps.
{:shortdesc}

Best of all, the {{site.data.keyword.webide}} is powered by the web. You have nothing to install, nothing to maintain, and nothing to scale. You can develop anywhere that you have an internet connection.

Don't store regulated data in files within the {{site.data.keyword.webide}}. The procedures for regulated data are currently not in place.
{: tip}

The {{site.data.keyword.webide}} is keyboard accessible and works well with a screen reader. You can use the {{site.data.keyword.webide}} to edit code or, if you prefer, you can edit code by using your favorite code editor or text editor. You can also use the Git capabilities that are provided with the {{site.data.keyword.webide}}; alternatively, you can use the Git command line or github.com to access the {{site.data.keyword.webide}} Git capabilities.
{: note}

## Setting up the IDE
{: #editorsetup}

The {{site.data.keyword.webide}} is customizable so that you can choose the color schemes, technical tools, and settings that meet your development needs. To view and modify the settings, from the navigation sidebar on the left, click the **Settings** icon ![Settings icon](images/webide_settings_icon_light_small.png).

If you often need to change certain settings while you edit, you can access those settings quickly from the **Local Editor Settings** icon ![Local Editor Settings icon](images/webide_local_settings_icon_light_small.png).

![Local Editor Settings](images/webide_local_editor_settings_light.png)

By default, the settings for the editor style and font size are always shown. To include other editor settings in the menu, follow these steps:

1. Click the **Local Editor Settings** icon ![Local Editor Settings icon](images/webide_local_settings_icon_light_small.png).

2. Click **Editor Settings**.

3. To include or exclude a setting from the **Local Editor Settings** menu, click the star for each setting.

![Editor Settings toggle](images/webide_editor_settings_toggle_light.png)


## Editing code
{: #editcode}

The {{site.data.keyword.webide}} has two main sections. The first section is the file navigator, which shows your project files in a tree structure. From the file navigator, you can create, rename, delete, and manage your files and folders.

To upload files to the file navigator, drag them from your computer to the file navigator.
{: tip}

The second section is the editor pane. The editor provides several coding features, including content assist and syntax validation.

![Web IDE](images/webide_light.png)

### Working with multiple files
1. To work with two files at the same time, click the **Change split editor mode** icon ![Split Editor icon](images/webide_split_editor_icon_light_small.png).
2. From the menu that opens, select a view.

 After you select a view, if a file was already open in the editor, it is shown in both editor views.

 To open or change a file that is shown in one of the editor views:
 1. Move the cursor to the editor view that you want to change.
 2. In the file navigator, click a file.

### Keyboard shortcuts
Many of the commands in the {{site.data.keyword.webide}} are accessible through keyboard shortcuts.

To see a list of the keyboard shortcuts in the editor, click **Tools** > **Show keys**. Alternatively, you can see the list by pressing Alt+Shift+?, or on MacOS, Ctrl+Shift+?. You can customize a shortcut by hovering over the key, clicking the pencil, and typing the new key binding.

## Managing source code
{: #sourcecontrol}

The {{site.data.keyword.webide}} is integrated with source code management tools. To work with your Git repository, click the **Git Repository** icon ![Git Repository icon](images/webide_git_icon_light_small.png). For more information, see [Working with Git in the Eclipse Orion Web IDE](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_web_ide#git_web_ide).

## Deploying an app from your workspace
{: #deploy}

1. To deploy your app, from the run bar, either select or create a launch configuration.
   ![Run bar](images/webide_runbar_light.png)   
1. Click the deploy icon ![deploy icon](images/webide_deploy_button_light_small.png). An instance of your app is deployed by using the current contents of your workspace and the environment that is defined in your launch configuration.
2. After your app is deployed, you can use the run bar to stop, restart, or debug your app, view logs, and more.

| Run Bar Icon | Description | 
|:-----------------|:-----------------|
| ![Stop icon](images/stop_button.png) | Stop the app. |
| ![Open app URL icon](images/open_app_url.png) | Open the deployed app. |
| ![View logs icon](images/view_logs.png) | View the logs of the deployed app. |
| ![Open dashboard icon](images/open_dashboard.png) | Open the app's dashboard. |
{: caption="Table 1. Run bar icons" caption-side="top"}

If you are developing a Node.js app, enable Live Edit mode to restart the app and access the debugger: ![The enable live edit slider](images/enable_live_edit.png)

| Run Bar Icon | Description | 
|:-----------------|:-----------------|
| ![The Live Edit restart icon](images/live_edit_restart.png) | With Live Edit mode enabled, restart the app quickly, without redeployment. |
| ![The debug icon](images/debug_icon.png) | With Live Edit mode enabled, access the debugger. |
{: caption="Table 2. Live Edit mode icons" caption-side="top"}

## Supported languages
{: #supported_languages}

The Eclipse Orion {{site.data.keyword.webide}} provides content assist, tooltips, previews, validation, and highlights syntax for JavaScript, HTML, CSS, and Markdown files. You can also highlight syntax for these file types:

* Arduino
* C#
* C++
* CoffeeScript
* CSHTML
* Embedded JavaScript (ejs)
* Erlang
* Go
* HTML abstraction markup language (Haml)
* Jade
* Java
* JSON
* Less  
* Lua  
* Objective-C
* PHP
* Python
* Ruby
* Sass/SCSS
* SQL
* Swift
* TypeScript
* Visual Basic (vb)
* VMHTML
* XHTML
* XML
* XQuery
* YAML
* Launch file 	
* Dockerfile
* gitignore
* git config
* cfignore
* properties

## Take a tutorial: Eclipse Orion Web IDE
{: #toolchain_web_ide_tutorials}

Check out one of these tutorials on the [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. 
