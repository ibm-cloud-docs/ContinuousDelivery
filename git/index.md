---

copyright:
  years: 2015, 2017
lastupdated: "2017-2-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# Getting started with GitLab on Bluemix
{: #git_working}

Collaborate with your team and manage your source code in a new or existing Git repository that is hosted by IBM and built on [GitLab Community Edition ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://about.gitlab.com/){:new_window}. 
{: shortdesc}

With GitLab on {{site.data.keyword.contdelivery_full}}, you can:
* Manage access to your Git repositories to keep your code secure
* Collaborate by using code reviews and merge requests
* Track defects and share ideas in the built-in issue tracker
* Document your project with the built-in wiki

**Note:** Because GitLab is hosted by IBM on Bluemix, a few familiar GitLab options, such as admin functions and continuous integration, are not available.

## File and repository size limits
{: #git_limits}

Files that are stored on GitLab on Bluemix are strictly limited to 100 MB. The recommended repository size limit is 1 GB. If your repository exceeds 1 GB, we will send you an email reminder requesting that you reduce the size of the repository.

## Creating a personal access token or SSH key for authentication    
{: #git_authentication}

To perform remote Git operations, such as `clone` or `push`, from your local Git repository, you must use a personal access token or SSH key to authenticate with GitLab.

* To set up a personal access token, see [Personal access tokens ![External link icon](../../../icons/launch-glyph.svg "External link icon")](docs.gitlab.com/ce/user/profile/account/two_factor_authentication.html#personal-access-tokens){:new_window}.
* To set up an SSH key, see [SSH ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://git.stage1.ng.bluemix.net/help/ssh/README){:new_window}.

**Note:** To use a personal access token or SSH key for authentication, you must set up Git locally. For instructions, see [Start using Git on the command line ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://git.stage1.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}.

For details on GitLab, see the [GitLab on IBM Bluemix ![External link icon](../../../icons/launch-glyph.svg "External link icon")](https://git.stage1.ng.bluemix.net/help){:new_window} help. To get started with GitLab on Bluemix using toolchains, see [Configuring GitLab on Bluemix](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlabbluemix).
