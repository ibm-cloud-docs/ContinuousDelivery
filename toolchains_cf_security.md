---

copyright:
  years:  2019, 2020
lastupdated: "2019-10-15"

keywords: Cloud Foundry org, user access, toolchains

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Managing user access to toolchains in Cloud Foundry orgs
{: #toolchains-cf-security}

You can grant users access to a toolchain by adding them to both the org that the toolchain is associated with and the access control list for the toolchain. Each toolchain is associated with a specific org, and any user that is a member of that org can be added to the access control list for any of the associated toolchains. The org that you are currently working in is displayed on the menu bar. To access a different set of toolchains, switch to a different org.
{: shortdesc}

You must add users to the toolchain's org in the region where the toolchain is hosted. If the toolchain is configured to deploy apps to a different region, it will still deploy apps to that region.
{: important}

If you are using {{site.data.keyword.Bluemix_notm}} Dedicated for {{site.data.keyword.ghe_short}}, when you add users to your {{site.data.keyword.Bluemix_notm}} org and spaces, the users can log in to {{site.data.keyword.ghe_short}} by using their {{site.data.keyword.Bluemix_notm}} ID and password. When the users log in, accounts are created for them. When you add users to your {{site.data.keyword.Bluemix_notm}} org and spaces, they are not automatically added to the {{site.data.keyword.ghe_short}} repo. Someone who has admin privileges for the repo must add them. For more information, see [Using Dedicated GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-getting-started). If you are using your own managed version of {{site.data.keyword.ghe_short}}, follow your internal procedures.

## Tips for managing access to a toolchain

* To manage toolchain access, on the DevOps dashboard, on the **Toolchains** page, click the toolchain to manage and then click **Manage**. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain** and then click **Manage**.

* To grant access to all of the members of the toolchain's org, click **Add org**. All of the members of that org can view the toolchain.

* You can grant admin privileges to an org or a user. Admins can modify and delete the toolchain. To grant admin privileges, select the **ADMIN** checkbox for the org or user.

* If you select the **ADMIN** checkbox for an org, all of the members of that org become admins. If you add members to the org after you grant admin privileges to the org, those members are given the same access as the rest of the org.

* To grant access to a user who is a member of the toolchain's org, enter the user's ID and click **Add user**. The user can view the toolchain.

* To grant access to a user who is not a member of the toolchain's org, follow these steps:

   a. From the menu bar, click **Manage > Access (IAM)**.

   b. Click **Access starts with the user**.
   
   c. From the row for the user that you want to assign access, select the **Actions** menu, and then click **Assign access**.
   
   d. Select **Assign access by using Cloud Foundry**.

   e. Select **Assign organization**.

   f. Assign the user access:

     * Choose an organization to add the user to.

     * Assign an organization role.

     * Choose a region.

     * Choose a space.

     * Assign a role for the selected space in the organization.

     By default, org managers have full admin privileges for all of the toolchains that are associated with the org. To grant full admin privileges to the user, select the **Manager** role. The Billing Manager and Auditor roles do not affect toolchain access. You can change the roles later on the Team Directory page. For more information, see [Cloud Foundry roles](/docs/iam?topic=iam-cfaccess#cfaccess).
     {: tip}

   After the user is a member of the org, return to the toolchain's Manage page and add the user to the toolchain.  
