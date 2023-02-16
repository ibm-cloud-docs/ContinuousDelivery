---

copyright:
  years: 2023
lastupdated: "2023-02-15"

keywords: high availability, disaster recovery, toolchains, Git

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Mirroring Git repositories
{: #cd-ha-dr-mirrorgit}

If you use {{site.data.keyword.gitrepos}} for both your source and target repositories (repos), you can use the built-in GitLab mirroring feature. This feature automatically synchronizes your source and target repos. If you use a different Git provider, you must set up your own mirroring solution. Alternatively, to mirror changes in the source repo, manually clone and push your Git repos to the target repo.
{: shortdesc}

If you cannot mirror your projects, you can [export](https://us-south.git.cloud.ibm.com/help/user/project/settings/import_export.md#exporting-a-project-and-its-data){: external} and [import](https://us-south.git.cloud.ibm.com/help/user/project/settings/import_export.md#importing-the-project){: external} your projects instead. However, the source and target repos are not synchronized if changes are made to the source repo.
{: tip}

To mirror a {{site.data.keyword.gitrepos}} repo, complete the following steps:

1. Create a blank GitLab project in the target repo. Do not initialize this project with a readme file.
1. [Create a personal access token](https://us-south.git.cloud.ibm.com/help/user/profile/personal_access_tokens.md#creating-a-personal-access-token){: external} with the `write_repository` scope in the target region. Save a copy of this token.
1. Use [Push mirroring](https://us-south.git.cloud.ibm.com/help/user/project/repository/mirror/push.md){: external} to push the source repo to the target repo:     

   a. From the source repo, select **Settings** > **Repository**.

   b. In **Mirror repository** section of the Repository page, type the URL of the target repo.

   c. Select **Push** to specify the direction of the mirror.

   d. Select **Password** to use the password authentication method.

   e. Type the personal access token that you created in step 2.

   f. Click **Mirror repository** to start the mirroring process. It might take up to five minutes for the process to start.
  
1. In the target region, locate the mirror of your repo to verify that it was successfully mirrored.

