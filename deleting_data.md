---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-17"

keywords: devops insights, manage, data, quality, delete, test, tests, app, dashboard

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Deleting your {{site.data.keyword.DRA_short}} data
{: #deleting_data}

{{site.data.keyword.DRA_full}} hosts your data in a highly available and secure environment. Client and system credentials are stored on encrypted disks. Access to data is limited to only those users that require the data to support and maintain {{site.data.keyword.DRA_short}}. Data that is stored in {{site.data.keyword.DRA_short}} is indexed by a toolchain ID. When you delete a toolchain, all of the data that is related to repos that was collected as part of the toolchain is deleted.
{: shortdesc}

You can delete data in following ways:

- Delete build, test, and deploy records
- Delete {{site.data.keyword.DRA_short}} data for a repo by disabling
- Delete integration between Toolchain and {{site.data.keyword.DRA_short}}
- Delete a repo from your toolchain

For more information about toolchains, see [Creating a toolchain from an app](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app).

{{site.data.keyword.IBM_notm}} doesn't manage data in {{site.data.keyword.DRA_short}}. If you stop using {{site.data.keyword.DRA_short}}, you must delete your own data. To delete your data, delete the {{site.data.keyword.DRA_short}} tool integration from your toolchain. If the {{site.data.keyword.DRA_short}} tool integration is not added again to the toolchain within seven days, the data is deleted.
{: important}


## Deleting {{site.data.keyword.DRA_short}} data sets
{: #deleting-data-sets}

With the Manage data dashboard, you can delete {{site.data.keyword.DRA_short}} data for a toolchain, an environment, an application, or a branch. All {{site.data.keyword.DRA_short}} data for builds, test results, and deployment records are deleted. This data includes predefined and custom data, but not repo data. 

Data can’t be recovered after it is deleted.
{: note}

To see your manage data dashboard, complete the following steps: 

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**.
2. Select your toolchain.
3. Select the **{{site.data.keyword.DRA_short}}** tile.
4. Select **Manage Data**.
5. Select **Quality Data**.

### Deleting toolchain data
{: #deleting-toolchain-data}

Toolchain data is all of the data that is associated with that toolchain. Deleting toolchain data doesn't delete the toolchain, or the tools that are associated with it. It deletes the data that is used by all of the tools that are attached to that toolchain.

1. To delete toolchain data, go to **Manage Data** > **Quality Data**.
2. Select **Toolchain data**. 
3. Click **Delete**.

### Deleting environment data
{: #deleting-environment-data}

Environment data refers to data that is associated with a specific location. For example, dallas-dev, dallas-prod, frankfurt-prod, or frankfurt-staging. To delete the environment data, complete the following steps:

1. Go to **Manage Data > Quality Data**.
2. Select **Environment data**. 
3. Select the environment that has the data that you want to delete
4. Click **Delete**.

### Deleting application data
{: #deleting-application-data}

Application data is all of the data that is associated with a certain app that is attached to a toolchain. To delete the environment data sets, complete the following steps:

1. Go to **Manage Data** > **Quality Data**.
2. Select **Application data**.
2. Select the app that has the data you want to delete, and click **Delete**.

### Deleting branch data for an application
{: #deleting-branch-application}

Branch data for an application is the data that is associated with a specific repo of an application. For example, the master branch or staging repo. 

1. To delete the environment data, go to **Manage Data** > **Quality Data**.
2. Select **Branch data for an application**.
3. Select the app and the branch that has the data you want to delete.
4. Click **Delete**.


## Deleting a {{site.data.keyword.DRA_short}} tool integration
{: #insights-delete-integration}

To delete the {{site.data.keyword.DRA_short}} tool integration, you must delete {{site.data.keyword.DRA_short}} from your toolchain. To delete {{site.data.keyword.DRA_short}} from your toolchain, complete the following steps:

1. Click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select your toolchain.
3. On the {{site.data.keyword.DRA_short}} tile, click the Overflow icon ![ellipsis icon](images/overflow-icon-2.svg) > **Delete**.


## Deleting a repo
{: #deleting-repo}

When you delete a repo, all of the data that is related to that repo is also deleted.

1. To delete a repo, click the **menu** icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select your toolchain from the table.
3. From the repo tile, click the Overflow icon ![ellipsis icon](images/overflow-icon-2.svg) > **Delete**.
