---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-5"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Getting started with toolchains after your {{site.data.keyword.jazzhub_short}} project is upgraded
{: #toolchains_post_upgrade}

{{site.data.keyword.jazzhub}} projects at hub.jazz.net are upgraded to toolchains in the {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}} service. 

{{site.data.keyword.jazzhub_short}} at hub.jazz.net is retired. 

For your DevOps projects, use the [{{site.data.keyword.contdelivery_short}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/devops){:new_window}. If you're new to {{site.data.keyword.Bluemix_notm}}, be sure to check out the [{{site.data.keyword.Bluemix_notm}} overview](/docs/overview?topic=overview-whatis-platform).

{: shortdesc}

## Find the toolchain that was created from your project
{: #find_toolchain}

Confirm that the upgrade is complete by going to the [Toolchains page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/devops/toolchains){: new_window} and verifying that you see toolchains with names that match the names of your hub.jazz.net projects. If your projects were automatically upgraded, keep these caveats in mind:
   - If another toolchain already used your project's name before your project was upgraded, the new toolchain that was created for your project might not have the exact name of your project. 
   - If you don't see toolchains for your projects, switch to any other orgs that you belong to and check the toolchains there.
   
## Toolchains overview
{: #compare_toolchains}

If you had one or more projects on hub.jazz.net, they were automatically upgraded to toolchains in the {{site.data.keyword.contdelivery_short}} service, unless the upgrade failed. Upgrades can fail due to invalid IBM Cloud accounts or orgs. These account and org owners were notified by email about the failures and the specific actions that are required on their part to address them. If you need help to locate the toolchain for your upgraded project, contact [support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. 

Toolchains are like projects, with a few important differences:

- Projects can have only one repository (repo) and pipeline. Toolchains can have as many repos and pipelines as you need.
- Toolchains can include tools that aren't available in projects, such as Slack, Sauce Labs, PagerDuty, and {{site.data.keyword.DRA_full}}.

 {{site.data.keyword.DRA_short}} is available in the US South, United Kingdom, and Germany regions.
 {: tip}
 
- In projects, membership was maintained at the project level. Access to toolchains is managed by {{site.data.keyword.Bluemix_notm}} organization (org) and by toolchain. To work with a toolchain, you must be a member of the org that contains the toolchain. The toolchain owner has further control over who can access the toolchain and what they can do. For more information about access control, see step 2 in [Getting started with your toolchain](#upgrade_next_steps).
- Depending on the type of repo you used in your project on hub.jazz.net, your toolchain might contain a GitHub.com repo or a {{site.data.keyword.gitrepos}} repo.

You can learn more about toolchains on [YouTube ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://youtu.be/2SIPE1e7NJ4){: new_window} or from [Getting started with {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_getting_started).

## Getting started with your toolchain
{: #upgrade_next_steps}

1. Give your team members access to the toolchain.
    - Each team member must have a valid {{site.data.keyword.Bluemix_notm}} account. Team members who don't have accounts must [sign up ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/registration){:new_window}.
    - Grant org members access to the toolchain from the toolchain Manage page. Existing project members are added as members of the toolchain as part of the upgrade process. For more information about access control for toolchains, see [Managing access to toolchains in Cloud Foundry orgs ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){:new_window}.
    - If a user is not a member of the org that the toolchain belongs to, add them to the org from the Manage Organizations page.
    - If your toolchain uses {{site.data.keyword.gitrepos}}, all JazzHub project members that have a valid {{site.data.keyword.Bluemix_notm}} ID are added to the {{site.data.keyword.gitrepos}} repo with the same privileges as they had in the JazzHub project. If your JazzHub project includes members that do not have a valid {{site.data.keyword.Bluemix_notm}} ID, they can register for one. After they register, you can add them to the repo.
      For more information about managing organizations, see [Managing organizations and spaces ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/account?topic=account-orgsspacesusers){:new_window}.

2. If you are using {{site.data.keyword.gitrepos}}, authenticate by using a personal access token or an SSH key. For more information about SSH keys, see [Creating a personal access token or SSH key for authentication](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication). To authenticate from an external Git client through https, follow these steps:
    1. Go to the [Access Tokens page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} of your {{site.data.keyword.gitrepos}} user settings.
    2. Create a personal access token that uses **api** as the scope.
    3. Go to the [Account page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/account){:new_window} and find your user name for {{site.data.keyword.gitrepos}}. Your user name is listed in the "Change username" section and it is shown as the first part of the URL for any personal repo that you create.
    4. To authenticate with {{site.data.keyword.gitrepos}} from an external Git client through HTTPS, use your username and your personal access token.
    5. If you want to reuse the local repo of your JazzHub Git repo, point the repo to the new repo in {{site.data.keyword.gitrepos}}. From a terminal shell, change to the directory where the JazzHub Git repo is cloned. Enter the `git remote set-url` command: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        To check which remote URLs are set to which remote names, use the `git remote -v` command. The default remote name is `origin`. If you have a more advanced setup, the form of the command is as follows: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

3. Optional: To explore your project's development maturity, your team's practices, and the quality of your code base, add IBM Cloud {{site.data.keyword.DRA_short}} to your toolchain. {{site.data.keyword.DRA_short}} applies developer, team, and deployment analytics to DevOps projects. For more information, see [Getting started with {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights?topic=DevOpsInsights-getting-started).

  {{site.data.keyword.DRA_short}} is available in the US South, United Kingdom, and Germany regions.
  {: tip}


## Troubleshooting
{: #upgrade_troubleshoot}

If you encounter problems that are related to the upgrade of your project, post a question in the [support forum ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. In your forum post, include the URLs to your {{site.data.keyword.jazzhub_short}} project and your {{site.data.keyword.contdelivery_short}} toolchain, and tag your post with the `devops-services` tag.


## Frequently asked questions
{: #upgrade_faq}

### My JazzHub project was associated with the UK region, but my toolchain is in the US South region. How does this work?
{: #faq_region}

Projects at hub.jazz.net and toolchains are both hosted in the US South region. If your project was configured to deploy apps to a different region, such as the UK region, the toolchain still deploys apps to that region, too. Therefore, nothing is really changing about where the data is hosted. Toolchains will be available in more regions in the future.

### What happened to my work items and dashboards in Track &amp; Plan after the upgrade?
{: #faq_tp}

The {{site.data.keyword.contdelivery_short}} service provides issue-tracking capabilities through {{site.data.keyword.gitrepos}}, which is hosted by IBM and based on GitLab Community Edition. {{site.data.keyword.contdelivery_short}} also supports integrations with other planning and issue-tracking tools, such as GitHub Issues and JIRA.

During the automated upgrade process, your Track & Plan work items were migrated to Git Issues. Both GitHub Issues and {{site.data.keyword.gitrepos}} provide kanban boards and issue tracking for planning. To learn more about Issue Boards, which is the kanban feature in Git Repos and Issue Tracking, see [Issue board ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

If you require the same function as the deprecated JazzHub Track &amp; Plan, a new IBM Track and Plan service on Cloud is available for purchase in selected countries on a per user per month basis. With this cloud service, you get full function, equivalent to Rational Team Concert&trade; contributor licenses, in a single tenant cloud subscription.

This new IBM Track and Plan on Cloud service provides much richer capability than the deprecated JazzHub Track &amp; Plan, supporting process customization, project hierarchies, SAFe&reg; and many other agile and hybrid methods, and scalability to grow beyond a single project. It is based on the latest version of Rational Team Concert 6.0.3 and will be at version 6.0.4 in the next 60 days, while JazzHub Track &amp; Plan was based on Rational Team Concert 5.x. A data migration is possible to IBM Track and Plan on Cloud through extra services. You can contact [Tom Hollowell ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader, for more information.

For information on IBM Track and Plan on Cloud, or to buy online, see the [IBM Marketplace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

To purchase Build Automation and Source Code Management, [Rational Team Concert on Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} is an option.

### What happened to my code repo after the upgrade?
{: #faq_repo}

After you upgrade, your new Git service is comparable to what you had before. If you used github.com with your JazzHub project, your toolchain is connected to the same GitHub repo. If your JazzHub project used IBM Hosted Git, the contents of that repo are cloned to a new repo in {{site.data.keyword.gitrepos}}, which is part of {{site.data.keyword.contdelivery_short}} and hosted by IBM.

For more information about how each type of repo is treated in the upgrade process, see the following table.

|Project repo |Project type	|Toolchain repo |
|:----------|:------------------------------|:------------------|
|github.com 		|Private or public 		|The same github.com repo with {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Private or public 		|A new private or public repo in {{site.data.keyword.gitrepos}} with {{site.data.keyword.Bluemix_notm}} Public.	|
|Jazz SCM		|Private or public 		|A new private or public repo in {{site.data.keyword.gitrepos}} with {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Table 1. Project repos mapped to toolchain repos" caption-side="top"}


### What happened to my build definitions in my project after the upgrade?
{: #faq_build}

If you built your source code by using Jazz instead of Delivery Pipeline, you must manually migrate your build definitions to Delivery Pipeline in your toolchain.

If you used Jazz SCM as a source repo and used Delivery Pipeline to build your code, the source in Jazz SCM was automatically moved to a Git repo. Your Delivery Pipeline configuration remains the same, except that it uses the source from the Git repo instead of the source from Jazz SCM.

### I had to create an organization for my project that was upgraded to a toolchain, so I added a credit card to my account. Will my credit card be charged?
{: #faq_charges}

As a [Pay As You Go customer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, if you use any runtime, service, or component beyond the free allotments that are listed for it in the {{site.data.keyword.Bluemix_notm}} catalog, you will be charged. For a usage estimate, see the [pricing sheet ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. For current pricing for Continuous Delivery, see the [{{site.data.keyword.Bluemix_notm}} catalog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/catalog/services/continuous-delivery){: new_window}.

If you are an IBM employee, internal IBM projects can be billed to departments in lieu of a personal credit card. If you need to use resources beyond the free allotments for IBM employees, create a support ticket.

### I can't find or access my toolchain. What should I do?
{: #faq_find}

Toolchains are hosted in {{site.data.keyword.Bluemix_notm}} organizations. The upgrade process adds all members of the JazzHub project to the toolchain. However, unless the owner of the {{site.data.keyword.Bluemix_notm}} organization adds those users to the organization, they cannot see the toolchain.

To access your toolchain, go to {{site.data.keyword.Bluemix_notm}}, click the menu icon, and click **Services &gt; DevOps**. The Toolchains page opens. Make sure that you are in the US South region and that you are in the organization that contains the toolchain. If your toolchain is not listed on the Toolchains page, see [this FAQ entry](#faq_uk).

### My project is associated with the UK region. After the upgrade, I see error messages, my colleagues can't access the toolchain, and I don't see my toolchain on the Toolchains page on {{site.data.keyword.Bluemix_notm}}. What's wrong?
{: #faq_uk}

**Full question:**

My JazzHub project is associated with the {{site.data.keyword.Bluemix_notm}} UK region according to the project settings. I verified my project settings by going to its overview page on JazzHub, clicking the **Settings** icon, which looks like a gear, and clicking **Options &gt; Make this an {{site.data.keyword.Bluemix_notm}} Project: Region**. After I upgraded the project to toolchain in the US, these problems occur:

   1. When I select the US organization, I see a message saying that the organization doesn't have a space in the US South region, and I'm prompted to create a space. I don't want to run anything in the US.
   
   2. Some of my colleagues can't access it the toolchain, although they were listed as members in the original JazzHub project. If they try to open the toolchain from the app overview page in the UK region by clicking **View Toolchain**, they see an "access denied" message.
   
   3. I don't see the toolchain listed on my Toolchains page at [https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, although I can access the toolchain directly from the app overview page in the UK region by clicking **View Toolchain**. I either get an error that I cannot modify the toolchain or I get an error that I have no toolchain and I need to create one. 

**Answer:**

These issues can occur if you came from a non-US {{site.data.keyword.Bluemix_notm}} organization and didn't explicitly expand your organization to the US South region before you upgraded. You can confirm this issue by opening the Toolchains page. You can see the region and organization at the beginning of the page. 

What happened is that at the time of the upgrade, your non-US organization didn't exist in the US, so the upgrade selected another org for you by looking up another org that you have access to.

If you switch to that {{site.data.keyword.Bluemix_notm}} organization in the US, you can find the toolchain. If you add your colleagues to that organization, they are granted access. This toolchain can continue to deploy to your non-US org. The only problem is that these two organizations are distinct; you can't perform user management across them both automatically.

If you want your toolchain to be in the US organization that matches your non-US organization, follow these steps:

   1. Log in to [https://cloud.ibm.com ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com){: new_window} and select the non-US region and org that you are coming from.
   
   2. In the {{site.data.keyword.Bluemix_notm}} header, switch to the US South region. You are prompted to create a space in that region.
   
   3. Create a space in the US South region to expand your organization into that region. 
   
   4. Delete the toolchain that was created through the upgrade process. 
   
      The Git repo is not automatically deleted. You might want to delete it manually or rename it for now. If you already renamed the Git repo, you can update the future toolchain to use it later.
      {: tip}

   5. Return to the JazzHub project. The project resets itself for another upgrade attempt. If the project doesn't reset, contact hub@jazz.net and provide the URL of the project.
   
   6. Restart the upgrade process and be sure to select the proper organization in the US, matching the name of your organization in the non-US region.
   
   7. If you kept or renamed the Git repo from the previous toolchain upgrade attempt (see step 4), you can reconfigure the Git card in your toolchain to point to this Git repo URL instead. The change is automatically reflected in the pipeline. To confirm, check the Input tab on the Build stage.
