---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-15"

keywords: devops insights, tagging

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}

# Tagging your applications
{: #tagging}

A tag is a label that you assign to an application for improved organization and to solve problems of scale. You can use tags to organize your applications and easily find them later. If you have several applications, you can group them with specific tags so that you can easily find and analyze the information that you want. To easily filter and search for the information you need, you can attach a tag to an application for region, production, development, and more. 
{:shortdesc}


## Tagging rules and limitations
{: #tagging-rules-limits}

Tags are case-sensitive. The maximum length of a tag is 128 characters. The recognized characters are A-Z, 0-9, white space, underscore, hyphen, period, and colon. Colons turn the tag into a string where you can isolate two logical parts, like a key:value pair. You can't use a colon in a tag without creating this pairing. A comma separates tags and can't be used within the tag name itself.
<!-- the only different between these limitations and the resource limitations is that in DevOps Insights, the tags are case sensitive. -->

## Adding and removing tags
{: #adding-removing-tags}

You can add or remove tags from the {{site.data.keyword.DRA_full}} Quality Dashboard page:

1. Click the menu icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. Select your toolchain > **{{site.data.keyword.DRA_short}}** > **Quality Dashboard**.
3. Click **Add tags** for the associated application, type in your tag, and click **Save**. 

Use tags to organize your resources. If your tags are billing related, consider writing tags as key:value pairs to help group-related tags, such as costctr:124.
{: tip}

To remove a tag, click the **Edit** icon ![Pencil icon](../icons/edit-tagging.svg). Then, click the **Remove** icon ![X icon](../icons/close-tagging.svg) next to the tag. You can also remove your tag from the Manage Data page. 

## Editing tags
{: #editing-tags}

You can easily edit your tags without having to delete the original tag. 

1. From {{site.data.keyword.DRA_short}}, go to **Manage Data > Tags**. 
2. Click the **Edit** icon ![Pencil icon](../icons/edit-tagging.svg). 
3. Click **Save**.  

## Searching for tags
{: #searching-tags}

You can search for you tagged applications from the {{site.data.keyword.DRA_short}} Quality Dashboard page. Use the **Filter by name or tag** field. 
