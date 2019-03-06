---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# 使用工具链  
{: #pipeline-working}

要自动执行构建并部署到 {{site.data.keyword.Bluemix}}，请使用 {{site.data.keyword.contdelivery_full}} 管道。
{: shortdesc}

通过管道，可以从多个构建类型中进行选择。您提供构建脚本，{{site.data.keyword.contdelivery_short}} 运行该脚本；无需设置构建系统。然后，只需单击一下，即可将应用程序自动部署到一个或多个 {{site.data.keyword.Bluemix_notm}} 空间、公共 Cloud Foundry 服务器或 {{site.data.keyword.containerlong}} 上的 Docker 容器。

构建作业会对 Git 存储库中的应用程序源代码进行编译和打包。构建作业会生成可部署的工件，如 WAR 文件或 {{site.data.keyword.containerlong_notm}} 的 Docker 容器。此外，还可以在构建内自动运行单元测试。您可以设置构建作业，以便每次推送落实时，都触发构建。

部署作业从构建作业中获取输出，并将其部署到 {{site.data.keyword.containerlong_notm}} 或 Cloud Foundry 服务器，如 {{site.data.keyword.Bluemix_notm}}。

可以部署到一个或多个区域和服务。例如，您可以设置 {{site.data.keyword.deliverypipeline}} 以使用一个或多个服务，在一个区域中进行测试，然后部署到多个区域中的生产环境。

##创建管道

您可以使用以下任一方法来创建管道：

   * [从现有 Cloud Foundry 应用程序创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}。生成的工具链包含管道。

   * [从模板创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window}（模板至少包含一个管道）。

   * 向现有工具链[添加 {{site.data.keyword.deliverypipeline}} 工具集成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window}。
   
通过 {{site.data.keyword.deliverypipeline}}，可更改配置，检查构建、已部署应用程序和最近部署的状态，查看最新日志和部署详细信息，也可以删除管道。
