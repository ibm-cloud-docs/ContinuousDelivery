---

Copyright:
 years: 2015, 2018
lastupdated: "2018-9-28"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# {{site.data.keyword.Bluemix_notm}} DevOps
{: #devops_intro}

Delivering software and services at the speed the market demands requires teams to iterate and experiment rapidly. They must deploy new versions frequently, driven by feedback and data. The most successful cloud development teams adopt modern DevOps culture and practices, embrace cloud-native architectures, and assemble toolchains from best-in-class tools to unleash their productivity. Doing these things quickly is a key competitive advantage.

The 
<a href="https://www.ibm.com/cloud/garage">IBM Cloud Garage Method <img src="../../icons/launch-glyph.svg" alt="External link icon"></a> 
describes architectures, practices, and DevOps toolchains to allow enterprises to innovate at scale, enabling you to transform your culture and use the tools effectively—and fast.

An enterprise application developer can start building and deploying cloud-native applications in minutes. They can use a full set of services to build cognitive, IoT, blockchain, mobile, and data-intensive applications. With the IBM Cloud App Service, an individual developer can create a project, pick an application starter kit, and deploy a production-ready application to {{site.data.keyword.Bluemix_notm}}. The platform's code generation technology creates a starter application in the developer's preferred language and framework, which is tailored to their needs and use case. Any services that are required in support of the use case, such as Watson Conversation, are provisioned automatically. Developers can debug and test on their local workstation or in the cloud, and use a DevOps toolchain to collaborate with others and automate the delivery process.

As team members join a project, they need an integrated set of tools that span development, deployment, and production operations. IBM's Open Toolchain architecture enables a team to rapidly provision best-in-class DevOps tools from IBM, open source, and others. Integrations between these tools are configured automatically. Toolchains are a first class concept on the platform, so developers can quickly organize everything that they need in one place, and evolve the toolchain over time. Toolchains are adopting Identity and Access Management (IAM), initially in the US South and US East Public regions, to provide access control. IBM provides toolchain templates that support Garage Method best practices, which you can customize to promote proven toolchain patterns across your enterprise.

{{site.data.keyword.contdelivery_full}} provides a core set of tools for any DevOps toolchain: {{site.data.keyword.gitrepos}}, Delivery Pipeline, and Eclipse Orion {{site.data.keyword.webide}}. {{site.data.keyword.gitrepos}} is based on the GitLab Community Edition, and offers planning boards and source code collaboration through merge requests. The Delivery Pipeline orchestrates build, test, and deployment jobs across multiple environments as changes progress from the developer to production. Applications can be deployed in minutes to the Cloud Foundry environment or to a Kubernetes cluster on {{site.data.keyword.Bluemix_notm}}, to either public or private clouds. The Eclipse Orion {{site.data.keyword.webide}} gives developers quick access to the code from any browser.

Open toolchain integrates additional tools around {{site.data.keyword.contdelivery_short}} such as Slack, Atlassian JIRA, Sonatype Nexus, JFrog Artifactory, Sauce Labs, PagerDuty, IBM Cloud Availability Monitoring, IBM Cloud Alert Notification, IBM Vulnerability Advisor, and IBM Globalization Pipeline. You can also substitute other tools for the {{site.data.keyword.contdelivery_short}} capabilities, including GitHub, GitHub Enterprise, and Jenkins. Developers can also use their favorite IDEs and editors, such as Visual Studio Code, Eclipse, and more.

Code repos, issue tracking systems, build systems, and deployment systems represent a wealth of data that can be used to help you deliver apps more efficiently and effectively. {{site.data.keyword.DRA_full}} uses big data analysis to provide valuable insights to executives, managers and developers. {{site.data.keyword.DRA_short}} aggregates and analyzes data from your DevOps toolchain to advise you about the risk of deploying specific changes, as well as areas to improve both your codebase and team productivity. The Delivery Pipeline can automatically gate deployment to an environment based on the risk of a change.

Resource groups are available in the US South and US East regions. Cloud Foundry orgs are supported in the US South, United Kingdom, and Germany regions.
{: tip}

{{site.data.keyword.Bluemix_notm}} DevOps provides concrete practices and architectures for cloud development, enables developers to get started quickly with new projects that employ the rich catalog of services on the {{site.data.keyword.Bluemix_notm}}, and provides developers an open and integrated set of tools for automating delivery with speed and control.
