---

copyright:
  years:  2021, 2023
lastupdated: "2023-01-18"

keywords: security and compliance for continuous delivery, security for continuous delivery, compliance for continuous delivery

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Managing security and compliance with {{site.data.keyword.contdelivery_short}}
{: #cd-manage-security-compliance}

{{site.data.keyword.contdelivery_short}} is integrated with the {{site.data.keyword.compliance_short}} to help you manage security and compliance for your organization. 
{: shortdesc}

With the {{site.data.keyword.compliance_short}}, you can:
- Monitor for controls and goals that pertain to {{site.data.keyword.contdelivery_short}}.
- Define rules for {{site.data.keyword.contdelivery_short}} that can help to standardize resource configuration.

## Monitoring security and compliance posture with {{site.data.keyword.contdelivery_short}}
{: #monitor-cd}

As a security or compliance focal, you can use the {{site.data.keyword.contdelivery_short}} goals to help ensure that your organization is adhering to the external and internal standards for your industry. By using the {{site.data.keyword.compliance_short}} to validate the resource configurations in your account against a profile, you can identify potential issues as they arise.

All of the goals for {{site.data.keyword.contdelivery_short}} are added to the {{site.data.keyword.cloud_notm}} Best Practices Controls 1.0 profile but can also be mapped to other profiles.
{: tip}

To start monitoring your resources, check out [Getting started with {{site.data.keyword.compliance_short}}](/docs/security-compliance?topic=security-compliance-getting-started).

### Available goals for {{site.data.keyword.contdelivery_short}}
{: #cd-available-goals}

#### DevSecOps goals
{: #cd-DevSecOps-goals}

Goals are available as part of the DevSecOps toolchain templates. For more information, see [Managing security and compliance](/docs/security-compliance?topic=security-compliance-getting-started).

#### Toolchain properties
{: #cd-toolchain-goals}

- Ensure that only the tool integrations within the toolchain are included in the allow list parameter array.

#### Identity and Access Management
{: #cd-iam-goals}

- 3000622 - Check whether toolchain has no more than # users with the IAM administrator role.
- 3000629 - Check whether toolchain has no more than # service IDs with the IAM administrator role.
- 3000633 - Check whether {{site.data.keyword.contdelivery_short}} has at least # users with the IAM manager role.
- 3000634 - Check whether {{site.data.keyword.contdelivery_short}} has at least # service IDs with the IAM manager role.
- 3000638 - Check whether toolchain service access is managed only by IAM access groups.

## Governing {{site.data.keyword.contdelivery_short}} resource configuration
{: #govern-cd}

As a security or compliance focal, you can use the {{site.data.keyword.compliance_short}} to define configuration rules for the instances of {{site.data.keyword.contdelivery_short}} that you create.

[Config rules](#x3084914){: term} are used to enforce the configuration standards that you want to implement across your accounts. To learn more about the data that you can use to create a rule for {{site.data.keyword.contdelivery_short}}, review the following table.

| Resource kind | Property | Operator | Value | Description |
|---------------|----------|---------------|-------|-------------|
| *instance* | *toolchain_allowed_tool_integration_ids* | *strings_in_list* | [Services that can be added to the list](https://github.com/open-toolchain/sdk/wiki/services.md){: external} | An array list of Strings that indicates the tools that can be bound to a toolchain. |
{: caption="Table 1. Rule properties for {{site.data.keyword.contdelivery_short}}" caption-side="top"}

To learn more about constructing config rules, check out [Formatting rules and templates](/docs/security-compliance?topic=security-compliance-formatting-rules-templates).
