---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-7"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}
{:pre: .pre}

# Setting up local clients to work with Git source control 
{: #git_local}


You can manage your GitHub, GitHub Enterprise, or Git Repos and Issue Tracking repo and work locally or in the Eclipse Orion  Web IDE. To work locally, you can either use the command line to access your repo or, if you work in Eclipse, install the EGit plug-in for version control.  Once you have a local version of your repo, you can use any tools to develop your app.

If you are using Git Repos and Issue Tracking, please see [Authorizing access](https://console.stage1.bluemix.net/docs/services/ContinuousDelivery/git_working.html#git_authentication).


## Cloning your Git project from the command line

Create a local copy of the project files by cloning the Git repo so that you can access the contents of your repo outside the Web IDE. 

### Before you begin
{: #git_before_clone}

Check whether Git is installed. On a command line, type `git version`. If Git is installed, the version number is shown and you can begin. If Git is not installed, [go to the Git website](http://git-scm.com/downloads). Download and install the version for your operating system. You can accept the default installation values.

### Cloning your project
{: #git_clone}

1. From the Toolchain Overview page, click the GitHub, GitHub Enterprise, or Git Repos and Issue Tracking card.

2. In GitHub, click on the **Clone or download** button and select  HTTPS or SSH.  Click the Clipboard icon to copy the URL .  In Git Repos and Issue Tracking, Select the HTTPS or SSH and copy the URL in the next field.

3. Open a command line.

4. Change the directory to where you want the local copy of the Git repo to be.

5. Type `git clone`, paste the URL, and press Enter. 

6. When you are prompted, type your IBMid and password.   

After the download is complete, you have a local repo of the files for your project. For more information about using Git, [see the Git documentation](http://git-scm.com/doc).


## Accessing your repo by using Eclipse and the EGit plug-in
{: #git_egit}

If you use Eclipse and have a project that uses Git for source control, you can use the EGit plug-in to manage your repo from Eclipse. For more information and instructions on how to install and configure EGit, please see [EGit tutorial](http://eclipsesource.com/blogs/tutorials/egit-tutorial/).

<a name='etools'></a>
## Developing with IBM Eclipse Tools

IBM&reg; Eclipse Tools for Bluemix&trade; provides plug-ins that you can install into an existing Eclipse environment to assist in integrating your IDE with Bluemix.

With the tools, you can deploy the following types of files and servers to the Bluemix server directly from your Eclipse IDE or from IBM&reg; WebSphere&reg; Application Server Developer Tools (WDT):
* JavaScript files
* WAR (web archive) files
* EAR (enterprise archive) files
* Liberty Profile packaged servers

You can also create services and link them to your app, and define environment variables as part of the deployment. For more information about IBM Eclipse Tools, [see Deploying apps with IBM Eclipse Tools for Bluemix][https://www.ng.bluemix.net/docs/manageapps/eclipsetools/eclipsetools.html].

