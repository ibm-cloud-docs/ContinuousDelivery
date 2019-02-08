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

# Setting up local clients to work with Git source control
{: #git_local}


You can manage and work with your source code in a GitHub, GitHub Enterprise, or Git Repos and Issue Tracking repository (repo), locally or in the Eclipse Orion Web IDE. To work locally, clone your repo with a Git client such as the Git command line interface, and edit your code with your favorite editor. If you work in Eclipse, you can install the EGit plug-in for version control.

## Cloning your Git project from the command line


## Before you begin
{: #git_before_clone}

1. To access the Git server outside the browser, you might need to create a personal access token or SSH key for authentication. The following table shows what you need to do to set up authentication.

| Git Type  | HTTPS Setup | HTTPS Use |  SSH Setup |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com) | [Personal access token](/docs/services/ContinuousDelivery/git_working.html#git_authentication) | Git Repos and Issue tracking user name (not your IBM id) and personal access token | [Configure the SSH key](/docs/services/ContinuousDelivery/git_working.html#git_authentication) |
| Public GitHub (github.com) | Personal access token is not required, but you can set one up and use it | GitHub user name and password, or GitHub user name and Personal Access token, or just the personal access token as the user name | [Configure a GitHub SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Personal access token](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) | GitHub Enterprise user name (not your IBM id) and personal access token | [Configure the GitHub Enterprise SSH key](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) |

If you prefer to use SSH, you can reuse a single key across all Git servers. Create or locate your key and configure it in each server as described in the previous links. If you create your key with a passphrase, you are prompted for that passphrase when you use the key.
{: tip}

2. If you are going to use the Git command line, complete the following steps:

    a. Check whether Git is installed. On a command line, type `git version`. If Git is installed, the version number is shown and you can begin.

    b. If Git is not installed, [go to the Git website ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://git-scm.com/downloads){: new_window}.

    c. Download and install the version for your operating system. You can accept the default installation values.


### Cloning your project
{: #git_clone}

Create a local copy of the project files by cloning the Git repo so that you can access the contents of your repo outside the Web IDE by using any desktop tool.

1. From your toolchain's Overview page, click the card for the repo you want to clone.

2. Gather your repo URL:

   a. In GitHub, click **Clone or download**. To use HTTPS, Select **Use HTTPS**.  To use SSH, click **Use SSH**. Click the clipboard icon to copy the URL.

   b. In Git Repos and Issue Tracking, select either **HTTPS** or **SSH** and copy the URL in the field.

3. Open a command line.

4. Change the directory to where you want the local copy of the Git repo to be.

5. Type `git clone`, paste the URL, and press Enter.

6. If you are prompted for authentication, enter the appropriate information, as defined in the previous table.


After the download is complete, you have a local version of the files in your repo. For more information about using Git, [see the Git documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")]](http://git-scm.com/doc){: new_window}.


## Accessing your repo by using Eclipse and the EGit plug-in
{: #git_egit}

If you use Eclipse and have a project that uses Git for source control, you can use the EGit plug-in to manage your repo from Eclipse. For instructions to install and configure EGit, see [EGit tutorial ![External link icon](../../icons/launch-glyph.svg "External link icon")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
If you use Git Repos and Issue Tracking and have any problems, see [Git Repos and Issue Tracking](git_working.html#git_local).
