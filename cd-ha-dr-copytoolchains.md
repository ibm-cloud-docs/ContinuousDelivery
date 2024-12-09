---

copyright:
  years: 2023, 2024
lastupdated: "2024-12-09"

keywords: high availability, disaster recovery, toolchains

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Saving and restoring toolchains
{: #cd-ha-dr-copytoolchains}

If you have an existing toolchain, such as one that is not defined by using Terraform, you can save a backup of your existing toolchain, and then restore a copy into an alternative region. If you use {{site.data.keyword.gitrepos}}, you can also [mirror your Git repos](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-ha-dr-mirrorgit) from the primary region to the alternative region.
{: shortdesc}

To save a toolchain, download and run a script on your local workstation that creates a toolchain template in text form. This template is used to instantiate a copy of the source toolchain. For security reasons, secrets are not included in this toolchain template.

After you create a toolchain by using this template, you must configure your tool integrations. Then, restore secrets from the source toolchain by copying their values from the source toolchain to the target toolchain. Unlike GitLab mirroring, this procedure creates a one-time copy of the toolchain. Any subsequent changes to the source toolchain are not reflected in the copied version of the toolchain.

Because the toolchain template is a copy, when instantiated, it references the source Git repo. To fix this issue, reconfigure the target toolchain with the target repo.
{: tip}

To save and restore a toolchain, complete the following steps:

1. Create a temporary directory on your local workstation.
1. Change directory into the temporary directory.
1. Generate a textual representation of the source toolchain in the temporary directory by using the [toolchain-to-template script](https://github.com/open-toolchain/toolchain-to-template){: external}.
1. Create a temporary blank GitLab project in the target region.
1. Type the following commands to initialize the temporary directory for Git operations and push the contents to the temporary GitLab project:

   a. git init

   b. git add --all

   c. git remote add origin *target repository url*

   d. git commit -m "add template yaml files"

   e. git push -u origin --all

1. [Create a personal access token](https://us-south.git.cloud.ibm.com/help/user/profile/personal_access_tokens.md#creating-a-personal-access-token){: external} in the target region with the `api`, `read_user`, `read_api`, `read_repository`, and `write_repository` scope.
1. Create a toolchain in the target region by constructing a URL and pasting it into your browser:

   a. Construct a target toolchain URL that contains the temporary repo, personal access token, and target region:

   ```text
   https://cloud.ibm.com/devops/setup/deploy?repository=<temporary repository>&repository_token=<personal-access-token>&env_id=ibm:yp:<target region>
   ```
   For example, `https://cloud.ibm.com/devops/setup/deploy?repository=https://us-east.git.cloud.ibm.com/user/temp-repo&repository_token=aG7junk9dafiiT6w6&env_id=ibm:yp:us-east`.

   b. Replace the source repo URL with the target repo URL that you created when mirroring your Git repos.

   c. Click **Create**. Because you didn't update your secrets, your pipeline runs but does not succeed.

1. [Revoke the personal access token](https://us-south.git.cloud.ibm.com/help/user/profile/personal_access_tokens.md#creating-a-personal-access-token){: external} that you created in step 6.
1. [Configure pipeline secrets](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#environment_properties) by adding the secure property values that are required by your pipeline.
1. [Run your target pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_stages) to make sure that they are working.
1. If you are mirroring repos, disable commit triggers so that your target pipelines don't run when a change is mirrored from the target repo to the source repo:

   a. Select the **Run jobs only when this stage is run manually** option for the [Input stage](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_stages) of your pipeline.

   b. Verify that your pipelines can be [started manually](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_stages).

## Known limitations
{: #backup_known_limitations}

Backing up your toolchain creates a copy of the toolchain itself, but it does not copy all of the data that is referenced by the toolchain. Consider the following limitations when you back up a toolchain to a different region:

* Pipeline logs and artifacts are not included in the copied toolchain.
* Tool configuration secrets that are stored in Key Protect or HashiCorp Vault are not included in the copied toolchain.
* {{site.data.keyword.DRA_short}} data is not included in the copied toolchain.

If your toolchain is subject to these limitations, you cannot use the script to back up and restore these aspects of your toolchain. Whenever the original toolchain is updated, you must keep the backup copy current.

## Using your backup toolchain
{: #use_backup_toolchain}

Backup or alternative toolchains are intended to provide short-term continuity if issues exist in a particular region. Do not commit to target (alternative) repos directly or enable pipeline commit triggers on target pipelines. If you commit to the target repo directly and then return to using the source (primary) repo, you risk conflicts and inconsistencies because the repos are not synchronized. If you enable commit triggers and then return to using the source repo, both pipelines run when code is updated. To avoid these scenarios, run your pipelines manually and return to the source toolchain as soon as possible.
