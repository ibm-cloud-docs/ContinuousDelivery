---

copyright:
  years: 2015, 2017
lastupdated: "2017-7-5"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Getting started with toolchains after your {{site.data.keyword.jazzhub_short}} project is upgraded
{: #toolchains_post_upgrade}

{{site.data.keyword.jazzhub}} projects at hub.jazz.net have been upgraded to toolchains in the IBM Bluemix {{site.data.keyword.contdelivery_short}} service. 

{{site.data.keyword.jazzhub_short}} at hub.jazz.net is retired. Do not use your projects at hub.jazz.net. 

   - The Git repositories (repos) for your projects on hub.jazz.net are now read-only.
   - Any changes that you make to the pipeline or work items on hub.jazz.net might be lost.
   - Access to hub.jazz.net can be disabled at any time, without warning.

For your DevOps projects, use the [{{site.data.keyword.contdelivery_short}} service ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops){:new_window}. If you're new to {{site.data.keyword.Bluemix_notm}}, be sure to check out the [Bluemix overview](/docs/overview/whatisbluemix.html#bluemixoverview).
{: shortdesc}

## Toolchains overview
{: #compare_toolchains}

If you had one or more projects on hub.jazz.net, they have been upgraded to toolchains in the {{site.data.keyword.contdelivery_short}} service. If you don't see the toolchain for your project and you need immediate access to it, contact [support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. 

Toolchains are like projects, with a few important differences:

- Projects can have only one repository (repo) and pipeline. Toolchains can have as many repos and pipelines as you need.
- Toolchains can include tools that aren't available in projects, such as Slack, Sauce Labs, PagerDuty, and {{site.data.keyword.DRA_full}}.
- In projects, membership was maintained at the project level. Access to toolchains is managed by {{site.data.keyword.Bluemix_notm}} organization (org) and by toolchain. To work with a toolchain, you must be a member of the org that contains the toolchain. The toolchain owner has further control over who can access the toolchain and what they can do. For details, see step 2 in [Getting started with your toolchain](#upgrade_next_steps).

You can learn about toolchains on [YouTube ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://youtu.be/2SIPE1e7NJ4){: new_window} or from [Getting started with {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![External link to YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}


## Getting started with your toolchain
{: #upgrade_next_steps}

1. Confirm that the upgrade is complete by going to the [Toolchains page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/devops/toolchains){: new_window} and verifying that you see toolchains with names that match the names of your hub.jazz.net projects. If your projects were automatically upgraded, keep these caveats in mind:
   - If another toolchain already used your project's name before your project was upgraded, the new toolchain that was created for your project might not have the exact name of your project. 
   - If you don't see toolchains for your projects, switch to any other orgs that you belong to and check the toolchains there.
   - If you still can't find the toolchain for one of your projects, the upgrade for it might still be in progress. If you need immediate access to that toolchain, contact [support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.

2. Give your team members access to the toolchain.
    - Each team member must have a valid {{site.data.keyword.Bluemix_notm}} account. Team members who don't have accounts must [sign up ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/registration){:new_window}.
    - Grant org members access to the toolchain from the toolchain Manage page. Existing project members are added as members of the toolchain as part of the upgrade process. For more information about access control for toolchains, see [Managing access ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - If a user is not a member of the org that the toolchain belongs to, add them to the org from the Manage Organizations page.
    - If your toolchain uses {{site.data.keyword.gitrepos}}, all JazzHub project members that have a valid Bluemix ID are added to the {{site.data.keyword.gitrepos}} repo with the same privileges as they had in the JazzHub project. If your JazzHub project includes members that do not have a valid Bluemix ID, they should register for one and be added to the repo.
      For more information about managing organizations, see [Managing organizations and spaces ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. For all work going forward, use the tools from your toolchain instead of the tools from your project on hub.jazz.net. For example, to edit code for a project, go to the corresponding toolchain for that project and click **Web IDE**.

4. If you are using {{site.data.keyword.gitrepos}}, authenticate by using a personal access token or an SSH key. For more information about SSH keys, see [Creating a personal access token or SSH key for authentication](/docs/services/ContinuousDelivery/git_working.html#git_authentication). To authenticate from an external Git client through https, follow these steps:
    1. Go to the [Access Tokens page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} of your {{site.data.keyword.gitrepos}} user settings.
    2. Create a personal access token that uses **api** as the scope.
    3. Go to the [Account page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/profile/account){:new_window} and find your username for {{site.data.keyword.gitrepos}}. Your username is listed in the "Change username" section and it is shown as the first part of the URL for any personal repo that you create.
    4. To authenticate with {{site.data.keyword.gitrepos}} from an external Git client through https, use your username and your personal access token.
    5. If you want to reuse the local repo of your JazzHub Git repo, point the repo to the new repo in {{site.data.keyword.gitrepos}}. From a shell in a terminal, change to the directory where the JazzHub Git repo is cloned. Enter the `git remote set-url` command: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        **Tip:** To check which remote URLs are set to which remote names, use the `git remote -v` command. The default remote name is `origin`. If you have a more advanced setup, the form of the command is as follows: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

5. Optional: To explore your project's development maturity, your team's practices, and the quality of your code base, add IBM Cloud {{site.data.keyword.DRA_short}} to your toolchain. {{site.data.keyword.DRA_short}} applies developer, team, and deployment analytics to DevOps projects. For more information, see [Getting started with {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Troubleshooting
{: #upgrade_troubleshoot}

If you encounter problems related to the upgrade of your project, post a question in the [support forum ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. In your forum post, include the URLs to your {{site.data.keyword.jazzhub_short}} project and your {{site.data.keyword.contdelivery_short}} toolchain, and tag your post with the `devops-services` tag.


## Frequently asked questions
{: #upgrade_faq}

### My JazzHub project was associated with the UK region, but my toolchain is in the US South region. How will this work?
{: #faq_region}

Projects at hub.jazz.net and toolchains are both hosted in the US South region. If your project was configured to deploy apps to a different region, such as the UK region, it will still deploy apps to that region after it is upgraded to a toolchain. Therefore, nothing is really changing with respect to where the data is hosted. Toolchains will be available in more regions in the future.

### What happened to my work items and dashboards in Track &amp; Plan after the upgrade?
{: #faq_tp}

The {{site.data.keyword.contdelivery_short}} service provides issue-tracking capabilities through {{site.data.keyword.gitrepos}}, which is hosted by IBM and based on GitLab Community Edition. {{site.data.keyword.contdelivery_short}} also supports integrations with other planning and issue-tracking tools, such as GitHub Issues and JIRA.

During the upgrade process, you can choose to migrate your Track &amp; Plan work items to Git Issues. Both GitHub Issues and {{site.data.keyword.gitrepos}} provide kanban boards and issue tracking for planning. To learn more about Issue Boards, which is the kanban feature in Git Repos and Issue Tracking, see [Issue board ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

For customers who require the same function as the deprecated JazzHub Track &amp; Plan, a new IBM Track and Plan service on Cloud is available for purchase separately in selected countries on a per user per month basis. With this cloud service, you get full function, equivalent to Rational Team Concert&trade; contributor licenses, in a single tenant cloud subscription.

This new IBM Track and Plan on Cloud service provides much richer capability than the deprecated JazzHub Track &amp; Plan, supporting process customization, project hierarchies, SAFe&reg; and many other agile and hybrid methods, and scalability to grow beyond a single project. It is based on the latest version of Rational Team Concert 6.0.3 and will be at version 6.0.4 in the next 60 days, while JazzHub Track &amp; Plan was based on Rational Team Concert 5.x. A data migration is possible to IBM Track and Plan on Cloud through additional services. You can contact [Tom Hollowell ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader, for more information.

For information on IBM Track and Plan on Cloud, or to buy online, visit [IBM Marketplace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

To additionally purchase Build Automation and Source Code Management, [Rational Team Concert on Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} is an option.

### What happened to my code repo after the upgrade?
{: #faq_repo}

After you upgrade, your new Git service will be comparable to what you had before. If you used github.com with your JazzHub project, your toolchain will be connected to the same GitHub repo. If your JazzHub project used IBM Hosted Git, the contents of that repo will be cloned to a new repo in {{site.data.keyword.gitrepos}}, which is part of {{site.data.keyword.contdelivery_short}} and hosted by IBM.

For full details about how each type of repo is treated in the upgrade process, see the following table.

|Project repo |Project type	|Toolchain repo |
|:----------|:------------------------------|:------------------|
|github.com 		|Private or public 		|The same github.com repo with {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Private or public 		|A new private or public repo in {{site.data.keyword.gitrepos}} with {{site.data.keyword.Bluemix_notm}} Public.	|
|Jazz SCM		|Private or public 		|A new private or public repo in {{site.data.keyword.gitrepos}} with {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Table 1. Project repos mapped to toolchain repos" caption-side="top"}


### What happened to my build definitions in my project after the upgrade?
{: #faq_build}

If you're building your source code by using Jazz instead of Delivery Pipeline, you must manually migrate your build definitions to Delivery Pipeline in your toolchain.

If you're using Jazz SCM as a source repo and using Delivery Pipeline to build your code, the source in Jazz SCM will be automatically moved to a Git repo. Your Delivery Pipeline configuration will remain the same except it will consume the source from the Git repo instead of the source from Jazz SCM.

### I had to create an organization for my project that was upgraded to a toolchain, so I added a credit card to my account. Will my credit card be charged?
{: #faq_charges}

As a [Pay As You Go customer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, if you use any runtime, service, or component beyond the free allotments that are listed for it in the Bluemix catalog, you will be charged. For a usage estimate, see the [pricing sheet ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. For current pricing for Continuous Delivery, see the [Bluemix catalog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

If you're an IBM employee, internal IBM projects can be billed to departments in lieu of a personal credit card. If you need to use resources beyond the free allotments for IBM employees, create a support ticket.
