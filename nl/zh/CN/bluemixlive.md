---



copyright:
  years: 2015，2017
lastupdated: "2017-09-20"

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}

#Bluemix Live Sync
{: #live-sync}


如果要构建 Node.js 应用程序，您可以使用 {{site.data.keyword.Bluemix}} Live Sync 来快速更新 {{site.data.keyword.Bluemix_notm}} 上的应用程序实例并进行开发，而无需手动重新部署。   
{: shortdesc}

执行更改后，您可以立即在运行中的 {{site.data.keyword.Bluemix_notm}} 应用程序中看到该更改。{{site.data.keyword.Bluemix_notm}} Live Sync 
<!--from both the command line and -->
在 Eclipse Orion Web IDE (Web IDE) 中运行。可以使用 {{site.data.keyword.Bluemix_notm}} Live Sync 来调试用 Node.js 编写的应用程序。  

{{site.data.keyword.Bluemix_notm}} Live Sync 由两个功能部件组成。
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**实时编辑**

可以编辑在 {{site.data.keyword.Bluemix_notm}} 上运行的 Node.js 应用程序，然后立即在浏览器中对其进行测试。在 Web IDE 中进行的任何更改都会立即传播到应用程序的文件系统。  

**调试**  

当 Node.js 应用程序处于“实时编辑”方式时，您可以创建 shell 并在其中进行调试。可以使用 Node Inspector 调试器来执行动态编辑代码、插入断点、单步执行代码、重新启动运行时等操作。  


##实时编辑
{: #live-edit}

如果要构建在 {{site.data.keyword.Bluemix_notm}} 上运行的 Node.js 应用程序，那么 {{site.data.keyword.Bluemix_notm}} Live Sync 的“实时编辑”功能可快速更新应用程序实例。“实时编辑”仅在 Web IDE 中可用。通过“实时编辑”，无需重新部署即可像在桌面上一样进行开发。

“实时编辑”仅支持用于 Node.js 应用程序。

在 Eclipse Orion Web IDE (Web IDE) 中，单击运行栏中的**实时编辑**。

![带“实时编辑”的“运行”栏的图像](images/bluemix-live-sync-light.png)

通过“实时编辑”，可以快速预览对在 {{site.data.keyword.Bluemix_notm}} 上运行的 Node.js 应用程序的更改。如果在开启“实时编辑”的情况下更新代码，那么在执行更改之后仅需几秒钟的时间，就可以通过刷新 Web 应用程序浏览器窗口看到这些更改反映出来。

<!--
For a tutorial on using the Live Edit feature of {{site.data.keyword.Bluemix_notm}} Live Sync, see the tutorial [Test and debug a Node.js app with Bluemix Live Sync![External link icon](../icons/launch-glyph.svg "External link icon")](https://hub.jazz.net/tutorials/livesync){:new_window}.
-->

在 Web IDE 中更改文件时，这些文件将自动重新部署到 {{site.data.keyword.Bluemix_notm}} 上的应用程序实例。如果需要重新启动 Node 应用程序，那么可以使用运行栏中的**重新启动**按钮。

**注**：为了在使用 {{site.data.keyword.Bluemix_notm}} Live Sync 的“实时编辑”功能时体验更好的一致性，需要额外添加 256 MB 内存。

## Bluemix 实时调试
{: #live-debug}

{{site.data.keyword.Bluemix_notm}} Live Sync“调试”使用 [Node Inspector ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/node-inspector/node-inspector){:new_window} 来提供调试功能。由于更高版本的 Node.js 并不包含 Node Inspector，所以您需要使用 Node V4 才可获得调试器。

为 Node.js 应用程序启用了 {{site.data.keyword.Bluemix_notm}}“实时编辑”后，可以访问 {{site.data.keyword.Bluemix_notm}} 实时调试。  

通过调试，可以执行动态编辑代码、插入断点、单步调试代码、重新启动运行时等操作，而且所有这些操作都可在 {{site.data.keyword.Bluemix_notm}} 为应用程序提供服务期间来执行。{{site.data.keyword.Bluemix_notm}} 提供大量服务，您可以从列表中选择服务，灵活地进行递增式应用程序开发。

{{site.data.keyword.Bluemix_notm}} 实时调试包括以下功能：

* 应用程序运行时控件
* 使用 [Node Inspector ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/node-inspector/node-inspector){:new_window} 进行调试
* Shell 访问

### 应用程序运行时控件 {: #app-runtime}

通过应用程序运行时控件，可以使用“调试”在启动时检测应用程序的状态。在对启动时崩溃的应用程序进行故障诊断时，此功能很有用。

开发应用程序时，可以从以下操作中进行选择：

* 执行应用程序的快速重新启动
* 运行任何应用程序代码之前暂挂应用程序

登录后，将打开 {{site.data.keyword.Bluemix_notm}}“实时调试”页面。

![调试 UI](images/live_sync_debug.png)


### 调试 {: #debug}

**限制**：Google Chrome 和 Node 4 是必需的。

调试包括以下功能：  
* 在应用程序代码中设置断点，以在特定行暂停执行。**注**：主程序不支持断点，但入口点支持。
* 编辑断点条件以仅在满足特定条件时暂停执行。
* 检查局部变量和字段的状态。
* 立即查看 `console.log()` 调用的调试输出。此操作比监视 cf 日志速度更快。
* 使用内置源代码编辑器对正在运行的应用程序代码立即执行临时更改。

### Shell {: #shell}

使用此工具，可以通过 shell 访问正在运行应用程序的容器。通过使用此终端，可以远程运行诊断 shell 命令来管理应用程序。所有版本的 Node.js 都支持 Shell 功能。

使用标准 Linux 命令（例如，**top**、**ps** 和 **kill**），监视实例中的内存和 CPU 使用量。

### 将应用程序配置为启用 {{site.data.keyword.Bluemix_notm}} 实时调试 {: #configure_app_debug}

1. Bluemix 实时调试器使用的是 Node Inspector。为此，您需要使用 Node V4。还需要允许 buildpack 检测应用程序 start 命令。start 命令必须由 buildpack 自动检测，而不是在 manifest.yml 文件中设置。 
  
   支持 {{site.data.keyword.Bluemix_notm}} 实时调试的 `package.json` 文件为：
   
  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. 增大内存。  

    a. 在应用程序 `manifest.yml` 文件中，向为内存属性指定的值添加 128 M 或更多内存。

在安装 {{site.data.keyword.Bluemix_notm}} 实时调试后，即可以使用调试工具。

推送应用程序，然后浏览到 `https://_app-host.mybluemix.net_/bluemix-debug/manage` 以访问 {{site.data.keyword.Bluemix_notm}} 调试用户界面。当系统提示您进行认证时，请输入您的 IBM 标识用户名和密码或一次性密码。    

**注**：调试器可能需要大约一分钟才能完成初始化。

<!--
   **Note**: Your user ID for DevOps Services can be either an IBMid or a federated ID (corporate ID). If you use federated authentication, to log in to your Bluemix Live Sync command-line client, you must use a personal access token instead of a password. If you don't use federated authentication, your IBMid and password work with all clients. For more information about creating a personal access token, see [What's federated authentication and how does it affect me?![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2016/06/23/whats-federated-authentication-and-how-does-it-affect-me/){:new_window}
   -->

### 复原应用程序配置并禁用 {{site.data.keyword.Bluemix_notm}} 实时调试 {: #restore_live_debug}

1. 复原应用程序的原始 Node.js 版本、start 命令和内存值。

2. 推送应用程序。

### 有关更多信息

* 请参阅[用于 Bluemix 的 Eclipse 工具 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.bluemix.net/docs/manageapps/eclipsetools/eclipsetools.html){:new_window}
