---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Upgrade your {{site.data.keyword.jazzhub_short}} project to a toolchain
{: #upgrade_projects}

{{site.data.keyword.jazzhub}} is evolving into {{site.data.keyword.contdelivery_full}}. As part of that change, projects will be upgraded to toolchains.

You can upgrade your project or wait for it to be automatically upgraded. For the best experience, make sure that you meet the [prerequisites](#upgrade_prereqs) and upgrade your project as soon as possible so that you can control what your toolchain's name is and which organization it is created in.
{: shortdesc}

**Frequently asked questions**

- [My JazzHub project is associated with the UK region, but my toolchain will be in the US South region. How will this work?](#faq_region)
- [What will happen to my work items and dashboards in Track &amp; Plan when I upgrade?](#faq_tp)
- [What will happen to my code repo when I upgrade?](#faq_repo)
- [What will happen to my build definitions in my project when I upgrade to a toolchain?](#faq_build)
- [I need to create an organization for my project that will be upgraded to a toolchain. I understand that I need to add a credit card to my account before I can create an organization. Will my credit card be charged?](#faq_charges)
- [I can't find or access my toolchain. What should I do?](#faq_find)
- [My project is associated with the UK region. After the upgrade, I see error messages, my colleagues can't access the toolchain, and I don't see my toolchain on the Toolchains page on the {{site.data.keyword.Bluemix_notm}} Platform. What's wrong?](#faq_uk)

## Toolchains
{: #compare_toolchains}

Toolchains are like projects, with a few important differences:

- Projects can have only one repository (repo) and pipeline. Toolchains can have as many repos and pipelines as you need.
- Toolchains can include tools that aren't available in projects, such as Slack, Sauce Labs, PagerDuty, and {{site.data.keyword.DRA_full}}.
- Access to toolchains is managed through standard {{site.data.keyword.Bluemix_notm}} organizations. Membership is maintained at the organization level, unlike projects, where membership was maintained at the project level.

You can learn about toolchains on [YouTube ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://youtu.be/2SIPE1e7NJ4){: new_window} or from [Getting started with {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![External link to YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Prerequisites
{: #upgrade_prereqs}

- To access your upgraded project's toolchain, you need a {{site.data.keyword.Bluemix_notm}} ID. Before you upgrade, you must verify that you have an active {{site.data.keyword.Bluemix_notm}} ID. If you don't have one, [sign up](https://console.ng.bluemix.net/registration/).
- Make sure that your {{site.data.keyword.jazzhub_short}} project owner is correct. The toolchain that is created from your project will be part of that owner's {{site.data.keyword.Bluemix_notm}} organization.
- Make sure that the organization and space where you want to create your toolchain are on {{site.data.keyword.Bluemix_notm}} Public in the US South region. To confirm that you have a valid organization and space in US South, log in to [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} and create a space if you are prompted to create one.
- If you're planning to start the upgrade, make sure that you're a member of every organization and space that the pipeline deploys to. Any project admin can start the upgrade. However, if the admin who starts the upgrade is not a member of every organization and space that the pipeline deploys to, the pipeline cannot be created. The person who starts the upgrade becomes the owner of the repo in the toolchain.
- The Eclipse Orion {{site.data.keyword.webide}} in the toolchain is separate from the {{site.data.keyword.webide}} that is associated with your project. If you use the {{site.data.keyword.webide}} and you have uncommitted changes, commit them before you upgrade.


## Upgrading from a project to a toolchain
{: #project_to_toolchain}

**Important:** Projects at hub.jazz.net and toolchains are both hosted in the US South region. If your project was configured to deploy apps to a different region, it will still deploy apps to that region after it is upgraded to a toolchain.

When your project is ready to be upgraded, a message is displayed on the project's card and Overview page.

![Image of card with the Ready To Upgrade label](images/card-project-to-upgrade.png)

![Time to Upgrade message](images/banner-ready-to-upgrade.png)

**Tip:** You can find projects that are ready to upgrade from the menu on the My Projects page:

![Image of the Projects To Upgrade menu item](images/menu-projects-to-upgrade.png)

When you start the upgrade, the pipeline stages in your project are locked. You won't be able to run or modify them. If you revert the upgrade by deleting the toolchain, the pipeline is unlocked.

If your project uses a Git repo that is hosted on JazzHub, after you start the upgrade, the repo is locked to ensure the integrity of the data that is moved to the toolchain. If you revert the upgrade by deleting the toolchain, the repo on JazzHub is unlocked.

For full details about how each type of repo is treated in the upgrade process, see the following table.

|Project repo |Project type	|Toolchain repo |
|:----------|:------------------------------|:------------------|
|github.com 		|Private or public 		|The same github.com repo with {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Private or public 		|A new repo in {{site.data.keyword.gitrepos}} with {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Table 1. Project repos mapped to toolchain repos" caption-side="top"}

## Starting the upgrade process
{: #start_upgrade}

Before you start the upgrade process, you can watch it in action on [YouTube ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://youtu.be/LSr2e3uvyLs){: new_window}.
[![External link to YouTube](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

To upgrade your project to a toolchain, follow these steps:

1. To start the upgrade process, on the banner message, click **upgrade now**. The "Project upgrade toolchain" page opens.

   ![Example of an upgrade page](images/project-upgrade-toolchain.png)

   For an overview of the upgrade process, read the description on that page. The toolchain will include a new pipeline that contains the same stages and jobs as the project's pipeline. In addition, the toolchain will contain a pointer to the Eclipse Orion {{site.data.keyword.webide}} that runs in {{site.data.keyword.contdelivery_short}}.

   In this example, because the project uses a public repo on github.com, the toolchain will be connected to the same GitHub repo. If your project uses a Git repo that is hosted on JazzHub, the contents of that repo will be cloned to a new repo in {{site.data.keyword.gitrepos}}, which is part of {{site.data.keyword.contdelivery_short}}.

2. To customize the toolchain, you can configure a few settings:

   - To change the name of the toolchain, edit the **Name** field.

      ![Name field](images/name-change.png)

   - To change which {{site.data.keyword.Bluemix_notm}} organization to create the toolchain in, select the organization from your account menu:

      ![{{site.data.keyword.Bluemix_notm}} Organization chooser](images/bluemix-organization-chooser.png)

   Because toolchains are managed at the organization level, be sure to select an organization where the project members that need to access the toolchain exist, or can be added.

3. If you used Track & Plan in your project, you can transfer your Track & Plan data to GitHub Issues.

   ![Track and Plan options](images/upgrade-tutorial-track-and-plan.png)

   - Indicate whether you want to migrate your Track & Plan data.
   - By default, all of your Track & Plan data is migrated. If you prefer to migrate only the work items that are part of a specific query, specify that query.
   - Select any work item attributes that you want to map to labels in GitHub Issues.

4. Click **Create**. The new toolchain is created, and its Overview page is displayed.

   ![Overview of the upgraded toolchain](images/new-toolchain-page.png)

   - To access your GitHub repo or the associated issue tracker, click **GitHub** or **Issues**.
   - To access your pipeline, click **Delivery Pipeline**.
   - To access the {{site.data.keyword.webide}}, which contains the contents of your repo that were checked out into the workspace, click **Eclipse Orion {{site.data.keyword.webide}}**.

   If you return to your project during the upgrade, the banner message might state that the upgrade is in progress, especially if the upgrade process involves importing source code to a new repo or importing Track &amp; Plan work items as issues.

   ![Message about project being upgraded to a toolchain](images/project-being-upgraded-banner.png)

## Revisiting your project
{: #revisit_projects}

You are ready to use your new toolchain. Your project is now labeled as "Upgraded," and on the Overview page, a confirmation message is displayed.

![Image of project card with the Upgraded label](images/card-upgraded-project.png)

![Upgraded project](images/banner-upgraded.png)

You can see which projects are upgraded by selecting **Upgraded Projects** from the menu on the My Projects page:

![Image of the Upgraded Projects menu item](images/menu-upgraded-projects.png)

If you need to revert the upgrade, delete your toolchain. You can delete your toolchain from the **More Actions** menu on the toolchain's Overview page:

![image of Delete action in More Actions menu](images/upgrade-tutorial-delete-toolchain.png)

When you return to your project, the upgrade message is displayed again, and you can upgrade again when you are ready.

## Next steps
{: #upgrade_next_steps}

1. Confirm that the upgrade is complete by refreshing your browser and checking for the message that your project was "upgraded to this toolchain" on the project Overview page:

   ![Message in banner indicating the project was upgraded](images/banner-upgraded.png)

   **Note:** If the message says "upgrade now," your upgrade failed. Click the **upgrade now** link to try again.

   ![Message in banner indicating the project is ready to upgrade](images/banner-ready-to-upgrade.png)

2. Give your team members access to the toolchain.
    - Each team member must have a valid {{site.data.keyword.Bluemix_notm}} account. Team members who don't have accounts must [sign up ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/registration){:new_window}.
    - Grant organization members access to the toolchain from the toolchain Manage page. Existing project members are added as members of the toolchain as part of the upgrade process. For more information about access control for toolchains, see [Managing access ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - If a user is not a member of the organization that the toolchain belongs to, add them to the organization from the Manage Organizations page.
    - If your toolchain uses {{site.data.keyword.gitrepos}}, all JazzHub project members that have a valid {{site.data.keyword.Bluemix_notm}} ID are added to the {{site.data.keyword.gitrepos}} repo with the same privileges as they had in the JazzHub project. If your JazzHub project includes members that do not have a valid {{site.data.keyword.Bluemix_notm}} ID, they should register for one and be added to the repo.
      For more information about managing organizations, see [Managing organizations and spaces ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Use the tools from your toolchain instead of the tools from your {{site.data.keyword.jazzhub_short}} project. For example, to edit code from a browser, use the Web IDE from your toolchain.

4. If you are using {{site.data.keyword.gitrepos}}, authenticate by using a personal access token or an SSH key. For more information about SSH keys, see [Creating a personal access token or SSH key for authentication](/docs/services/ContinuousDelivery/git_working.html#git_authentication). To authenticate from an external Git client through https, follow these steps:
    1. Go to the [Access Tokens page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} of your {{site.data.keyword.gitrepos}} user settings.
    2. Create a personal access token that uses **api** as the scope.
    3. Go to the [Account page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/account){:new_window} and find your username for {{site.data.keyword.gitrepos}}. Your username is listed in the "Change username" section and it is shown as the first part of the URL for any personal repo that you create.
    4. To authenticate with {{site.data.keyword.gitrepos}} from an external Git client through https, use your username and your personal access token.
    5. If you want to reuse the local repo of your JazzHub Git repo, point the repo to the new repo in {{site.data.keyword.gitrepos}}. From a shell in a terminal, change to the directory where the JazzHub Git repo is cloned. Enter the `git remote set-url` command: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        **Tip:** To check which remote URLs are set to which remote names, use the `git remote -v` command. The default remote name is `origin`. If you have a more advanced setup, the form of the command is as follows: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

5. When your toolchain is set up and you have started to use it, consider taking all or any of these steps to ensure that no one uses your project:
    - Add a suffix to your project name to indicate that it must not be used. You might add `_DO_NOT_USE` to the end of the project name.
    - Update the project's description to mention that it is no longer used, and add a pointer to the toolchain.
    - Remove the members from the project.
    - When you no longer need the project, delete it.

6. Optional: To explore your project's development maturity, your team's practices, and the quality of your code base, add IBM Cloud {{site.data.keyword.DRA_short}} to your toolchain. {{site.data.keyword.DRA_short}} applies developer, team, and deployment analytics to DevOps projects. For more information, see [Getting started with {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Troubleshooting
{: #upgrade_troubleshoot}

If you encounter a problem during the upgrade process, try one or more of these troubleshooting steps:

- Check the [prerequisites](#upgrade_prereqs) to make sure that you meet them. In particular, make sure that you're a member of every organization and space that the pipeline deploys to.
- If the problem occurred during your first attempt to upgrade and you meet all the prerequisites, try the upgrade again.
- If your project uses Jazz SCM or IBM Hosted Git for source control, check the size of the repo. If it is larger than 500 MB, [contact the DevOps services team ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.
- If you can't find your toolchain or access your toolchain, see [this FAQ entry](#faq_find).
- If you continue to encounter problems, post a question in the [support forum ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. In your forum post, include the URLs to your {{site.data.keyword.jazzhub_short}} project and your {{site.data.keyword.contdelivery_short}} toolchain, and tag your post with the `devops-services` tag.


## Frequently asked questions
{: #upgrade_faq}

### My JazzHub project is associated with the UK region, but my toolchain will be in the US South region. How will this work?
{: #faq_region}

Projects at hub.jazz.net and toolchains are both hosted in the US South region. If your project was configured to deploy apps to a different region, such as the UK region, it will still deploy apps to that region after it is upgraded to a toolchain. Therefore, nothing is really changing with respect to where the data is hosted. Toolchains will be available in more regions in the future.

### What will happen to my work items and dashboards in Track &amp; Plan when I upgrade?
{: #faq_tp}

The {{site.data.keyword.contdelivery_short}} service provides issue-tracking capabilities through {{site.data.keyword.gitrepos}}, which is hosted by IBM and based on GitLab Community Edition. {{site.data.keyword.contdelivery_short}} also supports integrations with other planning and issue-tracking tools, such as GitHub Issues and JIRA.

During the upgrade process, you can choose to migrate your Track &amp; Plan work items to Git Issues. Both GitHub Issues and {{site.data.keyword.gitrepos}} provide kanban boards and issue tracking for planning. To learn more about Issue Boards, which is the kanban feature in Git Repos and Issue Tracking, see [Issue board ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

For customers who require the same function as the deprecated JazzHub Track &amp; Plan, a new IBM Track and Plan service on Cloud is available for purchase separately in selected countries on a per user per month basis. With this cloud service, you get full function, equivalent to Rational Team Concert&trade; contributor licenses, in a single tenant cloud subscription.

This new IBM Track and Plan on Cloud service provides much richer capability than the deprecated JazzHub Track &amp; Plan, supporting process customization, project hierarchies, SAFe&reg; and many other agile and hybrid methods, and scalability to grow beyond a single project. It is based on the latest version of Rational Team Concert 6.0.3 and will be at version 6.0.4 in the next 60 days, while JazzHub Track &amp; Plan was based on Rational Team Concert 5.x. A data migration is possible to IBM Track and Plan on Cloud through additional services. You can contact [Tom Hollowell ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader, for more information.

For information on IBM Track and Plan on Cloud, or to buy online, go to [IBM Marketplace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

To additionally purchase Build Automation and Source Code Management, [Rational Team Concert on Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} is an option.

### What will happen to my code repo when I upgrade?
{: #faq_repo}

After you upgrade, your new Git service will be comparable to what you had before. If you used github.com with your JazzHub project, your toolchain will be connected to the same GitHub repo. If your JazzHub project used IBM Hosted Git, the contents of that repo will be cloned to a new repo in {{site.data.keyword.gitrepos}}, which is part of {{site.data.keyword.contdelivery_short}} and hosted by IBM.

For full details about how each type of repo is treated in the upgrade process, see the following table.

|Project repo |Project type	|Toolchain repo |
|:----------|:------------------------------|:------------------|
|github.com 		|Private or public 		|The same github.com repo with {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Private or public 		|A new private or public repo in {{site.data.keyword.gitrepos}} with {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Table 1. Project repos mapped to toolchain repos" caption-side="top"}


### What will happen to my build definitions in my project when I upgrade to a toolchain?
{: #faq_build}

If you're building your source code by using Jazz instead of Delivery Pipeline, you must manually migrate your build definitions to Delivery Pipeline in your toolchain.

If you're using Jazz SCM as a source repo and using Delivery Pipeline to build your code, the source in Jazz SCM will be automatically moved to a Git repo. Your Delivery Pipeline configuration will remain the same except that it will consume the source from the Git repo instead of the source from Jazz SCM.

### I need to create an organization for my project that will be upgraded to a toolchain. I understand that I need to add a credit card to my account before I can create an organization. Will my credit card be charged?
{: #faq_charges}

As a [Pay As You Go customer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, if you use any runtime, service, or component beyond the free allotments that are listed for it in the {{site.data.keyword.Bluemix_notm}} catalog, you will be charged. For a usage estimate, see the [pricing sheet ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. For current pricing for Continuous Delivery, see the [{{site.data.keyword.Bluemix_notm}} catalog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

If you're an IBM employee, internal IBM projects can be billed to departments in lieu of a personal credit card. If you need to use resources beyond the free allotments for IBM employees, create a support ticket.

### I can't find or access my toolchain. What should I do?
{: #faq_find}

Toolchains are hosted in {{site.data.keyword.Bluemix_notm}} organizations. The upgrade process adds all members of the JazzHub project to the toolchain. However, unless the owner of the {{site.data.keyword.Bluemix_notm}} organization adds those users to the organization, they cannot see the toolchain.

To access your toolchain, go to the {{site.data.keyword.Bluemix_notm}} Platform, click the menu icon, and click **Services &gt; DevOps**. The Toolchains page opens. Make sure that you are in the US South region and that you are in the organization that contains the toolchain. If your toolchain is not listed on the Toolchains page, see [this FAQ entry](#faq_uk).

Alternatively, while the JazzHub site is still available, you can go to your toolchain by clicking the link in the banner on your project's Overview page.

### My project is associated with the UK region. After the upgrade, I see error messages, my colleagues can't access the toolchain, and I don't see my toolchain on the Toolchains page on {{site.data.keyword.Bluemix_notm}}. What's wrong?
{: #faq_uk}

**Full question:**

My JazzHub project is associated with the {{site.data.keyword.Bluemix_notm}} UK region according to the project settings. I verified my project settings by going to its overview page on JazzHub, clicking the **Settings** icon, which looks like a gear, and clicking **Options &gt; Make this an {{site.data.keyword.Bluemix_notm}} Project: Region**. After I upgraded the project to toolchain in the US, these problems occur:

   1. When I select the US organization, I see a message saying that the organization doesn't have a space in the US South region, and I'm prompted to create a space. I don't want to run anything in the US.
   
   2. Some of my colleagues can't access it the toolchain, although they were listed as members in the original JazzHub project. If they try to open the toolchain from the app overview page in the UK region by clicking **View Toolchain**, they see an "access denied" message.
   
   3. I don't see the toolchain listed on my Toolchains page at [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, although I can access the toolchain directly from the app overview page in the UK region by clicking **View Toolchain**. I either get an error that I cannot modify the toolchain or I get an error that I have no toolchain and I need to create one. 

**Answer:**

These issues can occur if you came from a non-US {{site.data.keyword.Bluemix_notm}} organization and didn't explicitly expand your organization to the US South region before you upgraded. You can confirm this in two ways:

   * When you open the toolchain URL, check the {{site.data.keyword.Bluemix_notm}} header. Most likely, you'll see your organization name and no space will be indicated.
   
   * From your toolchain's Overview page, click **Manage**. On the Access Control page, click the **Org managers** link. The organization that contains the toolchain is listed on the main page.

What happened is that at the time of the upgrade, your non-US organization didn't exist in the US, so the upgrade selected another org for you by looking up another one you happen to have access to.

If you switch to that {{site.data.keyword.Bluemix_notm}} organization in the US, you can find the toolchain. If you add your colleagues to that organization, they will be granted access. This toolchain can continue to deploy to your non-US org. The only problem is that these two organizations are distinct; you can't perform user management across them both automatically.

If you want your toolchain to be in a US organization that matches your non-US organization, follow these steps:

   1. Log in to [https://console.bluemix.net ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window} and select the non-US region and org that you are coming from.
   
   2. In the {{site.data.keyword.Bluemix_notm}} header, switch to the US South region. You will be prompted to create a space in that region.
   
   3. Create a space in the US South region to expand your organization into that region. 
   
   4. Delete the toolchain that was created through the upgrade process. 
   
      **Note:** The Git repo is not automatically deleted. You might want to delete it manually or rename it for now. If you already changed the repo, you can switch the future toolchain to use it later.

   5. Return to the JazzHub project. It should reset itself for another upgrade attempt. If it doesn't reset, contact hub@jazz.net and provide the URL of the project.
   
   6. Restart the upgrade process and be sure to select the proper organization in the US, matching the name of your organization in the non-US region.
   
   7. If you kept or renamed the Git repo from the previous toolchain upgrade attempt (see step 4), you can reconfigure the Git card in your toolchain to point to this Git repo URL instead. The change is automatically reflected in the pipeline. To confirm, check the Input tab on the Build stage.
