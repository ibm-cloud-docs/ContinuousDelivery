---

copyright: 
  years: 2015, 2023
lastupdated: "2023-01-19"

keywords: IBM Cloud DevOps, enterprise application Developer, IBM Cloud Garage Method, DevOps toolchain, DevSecOps

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.cloud_notm}} DevOps
{: #devops_intro}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

Delivering software and services at the speed the market demands requires teams to iterate and experiment rapidly. They must deploy new versions frequently, driven by feedback and data. The most successful cloud development teams adopt modern DevSecOps culture and practices, embrace cloud-native architectures, and assemble toolchains from best-in-class tools to unleash their productivity. Doing these things quickly is a key competitive advantage.

The [IBM Cloud Garage Method](https://www.ibm.com/cloud/garage){: external} describes architectures, practices, and DevOps toolchains to allow enterprises to innovate at scale. Use the {{site.data.keyword.cloud_notm}} Garage Method to help you to transform your culture and use the tools effectively and fast.

An enterprise application Developer can start building and deploying cloud-native applications in minutes. They can use a full set of services to build cognitive, IoT, blockchain, mobile, and data-intensive applications. With the {{site.data.keyword.cloud_notm}} App Service, an individual Developer can create a project, pick an application starter kit, and deploy a production-ready application to {{site.data.keyword.cloud_notm}}. The platform's code generation technology creates a starter application in the Developer's preferred language and framework, which is tailored to their needs and use case. Any services that are required in support of the use case, such as Watson Conversation, are provisioned automatically. Developers can debug and test on their local workstation or in the cloud, and use a DevOps toolchain to collaborate with others and automate the delivery process.

As team members join a project, they need an integrated set of tools that span development, deployment, and production operations. IBM's Open Toolchain architecture enables a team to rapidly provision best-in-class DevSecOps tools from IBM, open source, and others. Integrations between these tools are configured automatically. Toolchains are a first class concept on the platform, so Developers can quickly organize everything that they need in one place, and evolve the toolchain over time. IBM provides [toolchain templates](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about) and [Terraform resources and examples](/docs/ContinuousDelivery?topic=ContinuousDelivery-terraform-setup) that support Garage Method best practices, which you can customize to promote proven toolchain patterns across your enterprise. IBM also provides [HTTP APIs and programming language SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} for you or for applications that you write to assemble and work with toolchains at a fine grained level.

{{site.data.keyword.contdelivery_full}} provides a core set of tools for any DevSecOps toolchain: {{site.data.keyword.gitrepos}} and Delivery Pipeline. {{site.data.keyword.gitrepos}} is based on the GitLab Community Edition, and offers planning boards and source code collaboration through merge requests. The Delivery Pipeline orchestrates build, test, and deployment jobs across multiple environments as changes progress from the Developer to production. Applications can be deployed in minutes to the Cloud Foundry environment or to a Kubernetes cluster on {{site.data.keyword.cloud_notm}}, to either public or private clouds.

Open toolchain integrates more tools around {{site.data.keyword.contdelivery_short}} such as Slack, Atlassian JIRA, Sonatype Nexus, JFrog Artifactory, Sauce Labs, PagerDuty, {{site.data.keyword.cloud_notm}} Availability Monitoring, and IBM Vulnerability Advisor. You can also substitute other tools for the {{site.data.keyword.contdelivery_short}} capabilities, including GitHub and Jenkins. Developers can also use their favorite IDEs and editors, such as Visual Studio Code, Eclipse, and more.

Code repos, issue tracking systems, build systems, and deployment systems represent a wealth of data that can be used to help you deliver apps more efficiently and effectively. {{site.data.keyword.DRA_full}} uses big data analysis to provide valuable insights to Executives, Managers, and Developers. {{site.data.keyword.DRA_short}} aggregates and analyzes data from your DevOps toolchain to advise you about the risk of deploying specific changes, and areas to improve both your codebase and team productivity. The Delivery Pipeline can automatically gate deployment to an environment based on the risk of a change.

{{site.data.keyword.cloud_notm}} DevOps provides concrete practices and architectures for cloud development. It enables Developers to get started quickly with new projects that employ the rich catalog of services on the {{site.data.keyword.cloud_notm}}. {{site.data.keyword.cloud_notm}} DevOps also provides Developers an open and integrated set of tools for automating delivery with speed and control.
