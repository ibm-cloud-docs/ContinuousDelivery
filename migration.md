---

copyright:
  years: 2016, 2017
lastupdated: "2017-1-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Upgrading DevOps Services projects to {{site.data.keyword.contdelivery_short}}
{: #cd_getting_started}

{{site.data.keyword.contdelivery_full}} is the next generation of IBM DevOps tools and services. You can upgrade IBM Bluemix DevOps Services projects to toolchains in {{site.data.keyword.contdelivery_short}}. The source control and issue tracking services that your project uses determine which of several upgrade processes you must follow.  
{: shortdesc}

## Understanding the upgrade process

In most cases, the transition from DevOps Services project to a toolchain is automated. Most of the changes occur on the back end; as a user, the most significant differences have to do with how you integrate tools into your projects, as well as how you access those tools. In short, the upgrade process generates a new toolchain from your DevOps Services project, and then sets the old project as read-only.

### Understanding toolchains

Toolchains are a core {{site.data.keyword.contdelivery_short}} concept. They are sets of tool integrations that support development, deployment, and operations tasks. The collective power of a toolchain is greater than the sum of its parts. A toolchain might be composed of any number of useful tool integrations, but its true value lies in the smooth interoperability of those integrations. You can learn more about toolchains in-depth at [Getting started with {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).

### How working with toolchains differs from DevOps services

{{site.data.keyword.contdelivery_short}} takes one of the core concepts of DevOps Services--that of an integrated set of tools used for rapid, iterative software delivery--and expands it. A {{site.data.keyword.contdelivery_short}} toolchain with Delivery Pipeline, Web IDE, and GitHub tool integrations is functionally identical to a DevOps Services project with GitHub-hosted source control and issue tracking. You can add various integrations, like Sauce Labs for functional testing or PagerDuty for outage alerts, to a toolchain from a convenient catalog. Adding those capabilities to the DevOps Services project would require substantially more effort.

For people who typically work in a local environment, your workflow will remain the same.

People who access their projects through the browser interface will experience a few changes. You'll have access to the same tools that you're used to in DevOps Services, but you'll access them from your toolchain's Overview page, which lists all of the toolchain's tool integrations. To find this menu, click the **Menu** button on Bluemix, click **Services**, and then click **DevOps**. Click a toolchain to go to its Overview page, and click a tool integration to use or configure it.

## Preparing to upgrade your project

### Prerequisites

To access your upgraded project's toolchain, you need a Bluemix ID. Before the upgrade can begin, you must verify that you have an active Bluemix ID. If you don't have an active Bluemix ID, [register for one here](https://console.ng.bluemix.net/registration).

You should ensure that your DevOps Services project owner is correct. The {{site.data.keyword.contdelivery_short}} toolchain that is created from your old project will be part of that owner's Bluemix organization.

### Source control considerations

If your DevOps Services project's repository is hosted on GitHub, your toolchain's GitHub tool integration will be configured to use that repository.

If your DevOps Services project's repository is hosted on Bluemix, that repository will be cloned to GitHub and your toolchains GitHub tool integration will be configured to use the cloned repository.

### Issue tracking considerations

If your DevOps Services project uses GitHub Issues for issue tracking, your toolchain's GitHub tool integration will continue to use that issue tracking configuration.

The toolchain upgrade process does not yet support Track & Plan.

## Upgrading your project

To upgrade your DevOps Services project to a toolchain, click the link in the upgrade message at the top of your project's page.

If you do not see a message, your project is not yet eligible for upgrade.  

<!--
## Verifying a successful project upgrade

TBD -- would this just be opening it up and poking around? Link out to toolchain docs if so.
-->



<!--
# Related Links
{: #rellinks}

## Tutorials and Samples
{: #samples}

* [Create and use your first toolchain (Link opens in a new window)](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_flow){:new_window}
* [Create a custom toolchain (Link opens in a new window)](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_custom){:new_window}
* [Create an application with three microservices (Link opens in a new window)](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_microservices){:new_window}

## Related Links
{: #general}

* [Microservices toolchain (Link opens in a new window)](https://www.ibm.com/devops/method/toolchains/microservices_toolchain){:new_window}
* [Simple toolchain (Link opens in a new window)](https://www.ibm.com/devops/method/toolchains/simple_toolchain){:new_window}
* [IBM Bluemix Garage Method (Link opens in a new window)](https://www.ibm.com/devops/method){:new_window}
-->
