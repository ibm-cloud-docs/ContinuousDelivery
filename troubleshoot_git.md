---

copyright:
  years: 2015, 2024
lastupdated: "2024-04-16"

keywords: troubleshoot, GitHub integration, Git Repos and Issue Tracking integration, GitLab project, tool integrations

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for GitHub, GitLab, and {{site.data.keyword.gitrepos}}
{: #troubleshoot-git}

General problems with using GitHub, GitLab, and {{site.data.keyword.gitrepos}} might include GitHub authentication or tool integration configuration issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

## I tried to add the GitHub tool integration to my toolchain, why wasn't the tool integration added?
{: #troubleshoot-cannot-authorize-github}
{: troubleshoot}

You must authorize with GitHub so that {{site.data.keyword.cloud_notm}} is authorized to access your GitHub account.

The GitHub tool integration wasn't added to your toolchain. If you are using Terraform or the API to create the GitHub tool integration, the attempt fails with the `User is not authorized with https://api.github.com` error message.
{: tsSymptoms}

If {{site.data.keyword.cloud_notm}} is not authorized to access your GitHub account, the tool integration is not added to your toolchain.
{: tsCauses}

If you are configuring the GitHub tool integration by using the console while you are creating your toolchain, follow these steps to authorize with GitHub:
{: tsResolve}

1. In the Configurable Integrations section, click **GitHub**.
1. If you are creating the toolchain on {{site.data.keyword.cloud_notm}} Public and {{site.data.keyword.cloud_notm}} is not authorized to access GitHub, select the method of authentication that will be used to access Github.
 
   * If you choose `OAuth`, click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize IBM-Cloud** to allow {{site.data.keyword.cloud_notm}} to access your GitHub account.
   * If you choose `Personal Access Token`, specify a valid personal access token for GitHub.
     
If you are using the console and you already have a toolchain, update the GitHub tool integration's configuration:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View toolchain**, and then click **Overview**.
1. On the Toolchain's Overview page, on the **Repositories** card, locate the GitHub tool integration.
1. Click the menu to access the configuration options and update the configuration settings to authorize {{site.data.keyword.cloud_notm}} to access GitHub.

   * If you choose `OAuth`, click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize IBM-Cloud** to allow {{site.data.keyword.cloud_notm}} to access your GitHub account.
   * If you choose `Personal Access Token`, provide a valid personal access token for GitHub.
   
1. When you are finished updating the settings, click **Save Integration**.

If you are using Terraform or the API with the `OAuth` authentication method, switch to using a Personal Access Token (PAT) to provide granular access to a specific user or repo. Authorizing with a PAT is recommended when you use Terraform or the API. Otherwise, you can use the console to authorize {{site.data.keyword.cloud_notm}} to access your GitHub account:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the **Toolchains** page, locate the toolchain to which you want to add the GitHub tool integration. Click the toolchain to open its Overview page.
1. On the Toolchain's Overview page, click **Add**.
1. On the **Add tool integration** page, click the **GitHub** tool card.
1. On the **Configure GitHub** page, click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize IBM-Cloud** to allow {{site.data.keyword.cloud_notm}} to access your GitHub account. You are redirected to the **Configure GitHub** page.
1. Close the page without taking any further action in the console, and then try to create the GitHub tool integration with Terraform or the API again.

## Why can't I use the {{site.data.keyword.gitrepos}} tool integration in my toolchain from one region in a toolchain within a different region?
{: #troubleshoot-cd-grit-integration}
{: troubleshoot}

You cannot use an instance of {{site.data.keyword.gitrepos}} across multiple regions.

When I attempt to add the {{site.data.keyword.gitrepos}} tool integration to my toolchain, I receive the following error message:
{: tsSymptoms}

`Repository URL is not valid. The repository must be on {local GitLab URL}.`

Where `{local GitLab URL}` is the URL of the {{site.data.keyword.gitrepos}} tool integration, in the region where the toolchain resides.

Because {{site.data.keyword.gitrepos}} is tightly integrated with the {{site.data.keyword.contdelivery_short}} service in the region in which they are running, you cannot use an instance of {{site.data.keyword.gitrepos}} across multiple regions.
{: tsCauses}

Instead of creating a {{site.data.keyword.gitrepos}} tool integration, create a generic GitLab integration and use this integration to point to the {{site.data.keyword.gitrepos}} repository (repo) in a different region.
{: tsResolve}

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the Toolchains page, click the toolchain that you want to add this integration to. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View toolchain** and click **Overview**.
1. Click **Add tool**.
1. In the Tool Integrations section, click **GitLab**.
1. Click the GitLab server that you want to use. If the GitLab server where the repo you want to access resides does not appear in this list, add a custom server:

   a. Click **Custom Server**.

   b. Type a name for the server. This server name will appear in the list of available GitLab servers.

   c. Type the Root URL of the custom GitLab server.

   d. Enter a personal access token for your custom GitLab server. If you don't have a personal access token, [create one](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat).

1. If you have a GitLab repo and want to use it, for the repository type, click **Existing** and type the URL.
1. If you want to use a new GitLab repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

   a. To create an empty repo, click **New**.

   b. To create a copy of a GitLab repo, click **Clone**.

   c. To fork a GitLab repo so that you can contribute changes through merge requests, click **Fork**.

1. If you want to create a public repo on the server, clear the **Make this repository private** checkbox.
1. If you want to use GitLab's Issues for issue tracking, select the **Enable GitLab Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.

For more information about configuring a GitLab tool integration, see [Configuring GitLab](/docs/ContinuousDelivery?topic=ContinuousDelivery-gitlab).


## Why can't I clone my {{site.data.keyword.gitrepos}} repo over https?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

You must use a personal access token or an SSH key to perform Git operations.

You try to push or clone a repo from the command line by using https and cannot authenticate even though you entered the correct password.
{: tsSymptoms}

{{site.data.keyword.gitrepos}} uses a single sign-on mechanism that does not support Git authentication that uses a user name and password on the command line.
{: tsCauses}

To perform Git operations such as clone or push, you must use a personal access token or an SSH key. For more information about creating a personal access token or SSH key, see the [Getting started tutorial](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## Why am I prompted to authenticate when I try to clone my {{site.data.keyword.gitrepos}} repo by using SSH?
{: #troubleshoot-cd-grit-ssh}
{: troubleshoot}

There might be issues with the location or the permissions for your private SSH key, or the Git command line might not be using your private SSH key to authenticate with {{site.data.keyword.gitrepos}}.

I added my SSH public key by way of the {{site.data.keyword.gitrepos}} user interface. When I try to clone a repo by using SSH, I am prompted for a password or security code, or an error message is displayed indicating that the authentication failed.
{: tsSymptoms}

Any of the following SSH issues might prompt you to authenticate, or display an error message:
{: tsCauses}

* The Git command line might not be using your private SSH key to authenticate with {{site.data.keyword.gitrepos}}.

* Your private SSH key might not be in the default ~/.ssh/id_rsa location.

* Your private SSH key might not have the correct permissions (600).


Use any of the following methods to resolve this issue:
{: tsResolve}

* If you use the default private SSH key location, verify the permissions for the ~/.ssh/ folder and the ~/.ssh/id_rsa private key file. If the permissions are too broad, by default SSH does not use a private key. Make sure that the permissions for the  ~/.ssh/ folder are set to 700 and the permissions for the ~/.ssh/id_rsa folder are set to 600.

* If your private key is not in the default location, use the following command to specify it in an environment variable:

```text
  GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git
```

* To debug this issue by using connection information, add the -v or the -vvv flag to the `GIT_SSH_COMMAND` environment variable:

```text
  GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git
```
```text
  GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git
```


## I tried to fetch changes from my {{site.data.keyword.gitrepos}} repo, why am I getting a `504 Gateway Time-out` error?
{: #troubleshoot-grit-timeout-error}
{: troubleshoot}

Your repo is larger than 1 GB. The Git source control management system isn't designed to store large binary files.

When I attempt to complete an operation on a {{site.data.keyword.gitrepos}} repo (such as a fetch or clone), I receive an error message:
{: tsSymptoms}

`git fetch
error: RPC failed; HTTP 504 curl 22 The requested URL returned error: 504 Gateway Time-out
fatal: The remote end hung up unexpectedly`

You have a large repo that is greater than 1 GB. The repo might also contain binary files that require more space than text files that are stored in a compressed format.
{: tsCauses}

You can use any of the following methods to resolve this problem:
{: tsResolve}

* Reduce the size of your {{site.data.keyword.gitrepos}} repo. For more information about reducing the size of your repo, see [Reducing the repository size using Git](https://docs.gitlab.com/ee/user/project/repository/reducing_the_repo_size_using_git.html){: external}.

* Use SSH to bypass the default clone timeout of 180 seconds.

* If you are attempting to clone a repo, complete a shallow clone (`git clone --depth`) to reduce the amount of data that is transferred by truncating the commit history. For more information about completing a shallow clone, see the [Git Reference documentation](https://git-scm.com/docs/git-clone#Documentation/git-clone.txt---depthltdepthgt){: external}.


## I tried adding a user to my GitLab project by way of email, but they didn't receive the invitation. How do I add them to my project?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

The invitation might be blocked by the user's email.

I invited a user to my GitLab project by using their email address that is listed in {{site.data.keyword.gitrepos}}, but they didn't receive the email.
{: tsSymptoms}

The email might be blocked from the user's inbox by spam filters.
{: tsCauses}

You can use any of the following methods to resolve this problem:
{: tsResolve}

* Check your email spam folder to determine whether the email invitation was marked as spam. Emails are sent from a noreply@ address. Update your spam filters to allow emails from this address.

* Investigate whether corporate spam filters that are outside of the user's control are blocking the email. Ask the user to log in to the {{site.data.keyword.gitrepos}} user interface and send you their user ID. You can add the user to the GitLab project by using their user ID.

## When I use Terraform to update the configuration of an existing Git tool integration, why does the configuration fail?
{: #troubleshoot-target-repo-exists}
{: troubleshoot}

The Git tool integration resource specifies a `type` of `clone`, `fork`, or `new`, and it specifies an existing target repo.

When you use Terraform to update a Git tool integration, the configuration fails with the `The nonempty repository _REPO-URL_ already exists. Either delete the repository or change the Repository Type to 'Existing'` error message, where `REPO-URL` is the URL of the target repo.
{: tsSymptoms}

This error is often caused by the following actions:
{: tsCauses}

* Your Git tool integration Terraform resource specifies a `type` of `clone`, `fork`, or `new`. You changed the `repo_url` within the `initialization` block of the resource to the URL of a repo that exists.
* Your Git tool integration Terraform resource specifies a `type` of `clone`, `fork`, or `new`. You did not change the `repo_url`, but you changed one or more other arguments within the `initialization` block of the resource. In this situation, the repo exists because it was created when the Git tool integration resource was previously applied by Terraform.

The `clone`, `fork`, and `new` types instruct the Git tool integration to create the target repo (`repo_url`) on the premise that this repo does not exist. If the tool integration finds the target repo, it fails by design.

Change the `type` from `clone`, `fork`, or `new` to `clone_if_not_exists`, `fork_if_not_exists`, or `new_if_not_exists`. These types instruct the Git tool integration to create the target repo if it does not exist, or to use the target repo as-is if it does exist.
{: tsResolve}

Although you can use other methods to resolve this error, these methods are not recommended because you might lose information. These methods also might require changes to your Terraform that are not good practices.

* Change `repo_url` to a repo that is created when you apply your Terraform again. Changing a Terraform resource after the initial creation to avoid errors during subsequent updates is an anti-pattern. This method also leaves the previously created repos intact, but no longer bound to the toolchain.
* Change `type` to `existing`, and then apply your Terraform again. Changing a Terraform resource after the initial creation to avoid errors during subsequent updates is an anti-pattern.
* Manually delete the target repo, and then apply your Terraform again. Manual changes between otherwise automated Terraform operations are not recommended. If you delete the repo, the deletion cannot be undone, and can cause permanent data loss.
