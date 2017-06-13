---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 将 IBM 保密信息项目升级到工具链 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}} 逐步发展到 IBM Bluemix {{site.data.keyword.contdelivery_short}}。作为该变化的一部分，项目将升级到工具链。

当项目已就绪可以进行升级时，在项目的“概述”页面上会显示消息。然后，您可以在 {{site.data.keyword.Bluemix_notm}} Public 上，将项目升级到工具链。工具链将针对您的源代码，包含 Whitewater {{site.data.keyword.ghe_short}} 存储库。Whitewater {{site.data.keyword.ghe_short}} 提供给 IBM 团队，用于在 IBM 内提升和启用社交代码。
{: shortdesc}

**{{site.data.keyword.contdelivery_short}} 工具链与 Whitewater {{site.data.keyword.ghe_short}} 一起使用时，是经过核准的 IBM 保密信息材料。**从 Whitewater {{site.data.keyword.ghe_short}} 存储库接收输入的 Delivery Pipeline 可以部署至编译打包 (YS1) 和公共 (YP) 环境。

在升级期间，系统将提示您授权 {{site.data.keyword.contdelivery_short}} 代表您访问 Whitewater {{site.data.keyword.ghe_short}}。

## 升级后向 Whitewater {{site.data.keyword.ghe_short}} 存储库添加成员

如果项目使用在 JazzHub 上托管的存储库，那么在升级期间，会在 Whitewater {{site.data.keyword.ghe_short}} 上创建新存储库。升级后，启动升级的人员必须向 Whitewater {{site.data.keyword.ghe_short}} 存储库添加团队成员，并确保他们具有正确的特权，然后他们才能访问新存储库。

## 故障诊断

当您尝试更改管道部署阶段的目标时，有时会发生间歇性中断问题。发生此问题时，会在**组织**和**空间**字段中显示错误。

此问题通常仅在您从管道更改目标时发生，因此在升级期间创建的管道将会正确地部署至与其之前相同的目标。

如果您尝试更改目标且发生此问题，请切换目标几次，直到**组织**和**空间**字段填入信息为止。

相关问题有时会导致部署至 YS1 目标失败。此状况很少见；如果发生此状况，请重新运行管道。

IBM DevOps Services 团队正在积极着手解决这些问题。
