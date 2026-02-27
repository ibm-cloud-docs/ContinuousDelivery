---

copyright:
  years: 2026
lastupdated: "2026-02-02"

keywords: IBM Cloud, cd, Continuous Delivery, insights, cra, regions, deprecation

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for Continuous Delivery region and feature consolidation
{: #faq_region_feature_consolidation}

{{site.data.keyword.contdelivery_short}} is being discontinued in select regions and deprecating [Code Risk Analyzer (CRA)](/docs/ContinuousDelivery?topic=ContinuousDelivery-cra-cli-plugin) and [DevOps Insights (DOI)](/docs/ContinuousDelivery?topic=ContinuousDelivery-di_working) across all regions to focus on the most in-demand capabilities and locations. We're providing a self-service [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) to help you migrate smoothly.
{: shortdesc}


## Which regions are being discontinued?
{: #which_regions_affected}
{: faq}
{: support}

{{site.data.keyword.contdelivery_short}} is being discontinued in the following regions:
* Sydney (au-syd)
* Montreal (ca-mon)
* Toronto (ca-tor)
* Madrid (eu-es)
* Osaka (jp-osa)
* Washington DC (us-east)

{{site.data.keyword.contdelivery_short}} will continue to be available in the remaining regions:
* Sao Paulo (br-sao)
* Frankfurt (eu-de)
* London (eu-gb)
* Tokyo (jp-tok)
* Dallas (us-south)

The Code Risk Analyzer (CRA) and DevOps Insights (DOI) features of {{site.data.keyword.contdelivery_short}} are being discontinued in all regions.


## What is the timeline for the discontinuation?
{: #timeline}
{: faq}
{: support}

* End of Marketing: 12 June 2026. After this date, customers will no longer be able to create new resources in the affected regions. However, if a region has no active usage before this date, the Continuous Delivery service in that region may be discontinued earlier and stop accepting new resource creation.
* End of Service: 12 February 2027. This is the planned date when the Continuous Delivery service will no longer be available in the affected regions. However, if a region has no active usage before this date, or if all customers in the region complete their migrations early, the service in that region may be discontinued earlier.

In regions where there is no active usage of the service, or where customers have already completed their migrations before the scheduled end-of-service date, the service may be discontinued earlier than previously communicated. If any regional changes are planned, customers will receive advance notification to ensure they have sufficient time to prepare and take any necessary actions.
{: note}


## Will my existing toolchains and pipelines work until the cutoff date?
{: #will_existing_work}
{: faq}
{: support}

* Toolchains and pipelines will continue to operate in affected regions until 12 February 2027, unless the service in a region is discontinued earlier due to no active usage or completed migrations.
* Users will not be able to create new resources in the affected regions starting 12 June 2026, However, if a region has no active usage before this date, or if all customers in a region complete their migrations early, the service in that region may discontinue earlier.


## What happens to my data and configurations after the service is discontinued?
{: #data_configurations}
{: faq}
{: support}

After the End of Service date, data and configurations in affected regions will be removed and cannot be recovered. If a region is discontinued earlier due to inactive usage, data and configurations in that region will be removed at the time of closure. Please complete your migration before the cutoff using the [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region).


## Are there recommended migration paths to other regions or services?
{: #migration_paths}
{: faq}
{: support}

Yes. Use the [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) to migrate {{site.data.keyword.contdelivery_short}} resources:
* Migrate Git Repos and Issue Tracking projects across regions via direct transfer (GitLab feature).
* Copy toolchains (including Tekton pipelines) to another region using the migration guide.
* Securely export and move secrets to Secrets Manager.


## What should I do if I cannot migrate to the supported IBM Cloud Continuous Delivery region?
{: #cannot_migrate}
{: faq}
{: support}

IBM Cloud Continuous Delivery does not provide a managed alternative in regions where the service is being discontinued. Customers who cannot migrate to another region may choose to deploy their own CI/CD or orchestration environments using IBM Cloud infrastructure, such as [IBM Cloud VPC](/docs/vpc), or use capabilities available through [Red Hat OpenShift on IBM Cloud](/docs/openshift?topic=openshift-getting-started), including [OpenShift Pipelines](https://docs.redhat.com/en/documentation/red_hat_openshift_pipelines/1.21){: external}. These environments are fully customer‑managed, and IBM does not provide guidance on designing, deploying, or operating custom CI/CD solutions. Customers should refer to the relevant vendor documentation and best practices for setup and configuration.


## Will IBM provide automated migration tools or assistance?
{: #migration_tools}
{: faq}
{: support}

Yes. The step-by-step [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) helps in migration of toolchains and associated resources.


## Will pricing or billing change during the transition period?
{: #pricing}
{: faq}
{: support}

* After migration, you should disable instances in the discontinued region to avoid duplicate billing.
* Migration guidance will include steps to optimize billing during transition.

Customers must verify migrated resources and manage deprovisioning according to their schedule.
{: note}


## How will this affect compliance and security requirements?
{: #compliance_security}
{: faq}
{: support}

* Evaluate regional data regulations based on your data type and residency requirements.
* All data transferred during migration is encrypted in transit.
* Best practices for secrets handling and secure migration will be included in the documentation.
* If you require EU-managed environments, migrate to a supported EU region (e.g., Frankfurt)


## What alternatives exist for CI/CD on {{site.data.keyword.cloud_notm}} after discontinuation?
{: #alternatives}
{: faq}
{: support}

The recommended option is to migrate to a supported {{site.data.keyword.cloud_notm}} region using the [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region). Future updates will be shared through customer notifications and email.


## Who can I contact for support or more information?
{: #contact}
{: faq}
{: support}

For any product related queries reach out to [IBM Cloud Support](https://www.ibm.com/products/cloud/support){: external} or corresponding IBM Cloud Partners.


## What does the migration guide do, and how do I use it?
{: #tool}
{: faq}
{: support}

The [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) allows you to:
* Copy Git Repos and Issue Tracking projects (GRIT) using direct transfer between regions.
* Copy toolchains (including Tekton pipelines) to other regions by serializing the toolchains to [Terraform](https://developer.hashicorp.com/terraform){: external}  and then applying the Terraform to recreate the toolchain in the new region.

Follow the [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) to migrate resources.


## Will migrating toolchains impact my deployment configurations or network rules?
{: #deployment_config_network_rules}
{: faq}
{: support}

Potential updates that might be required are:
* If you have firewall rules in your network to allow traffic from pipeline workers or webhooks from Git Repos and Issue Tracking, the IPs will be different across regions and you may need to update those rules.
* Hard-coded or configured urls or assumptions about region in your pipelines or scripts would need to be updated in order to run in a new region.


## Do I need to act now?
{: #act_now}
{: faq}
{: support}

No immediate action is required. However, we recommend planning and testing your migration well before 12 February 2027. If a region is discontinued earlier due to inactive usage, we encourage completing migration ahead of that earlier closure to ensure a smooth transition.


## Can I test migration before the cutoff?
{: #test_before}
{: faq}
{: support}

Yes. You can use the [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) in a sandbox/test environment and perform a dry-run before migrating production workloads.


## Is there a cost for migration tools or support?
{: #cost}
{: faq}
{: support}

The self-service [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) is provided at no additional cost. Standard {{site.data.keyword.cloud_notm}} service usage charges apply in the target region.


## Can I automate migration for multiple toolchains?
{: #automate_multiple}
{: faq}
{: support}

Yes. The [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) supports bulk export/import using Terraform, enabling standardized, repeatable migration flows.


## Will secrets remain secure during migration?
{: #secrets_secure}
{: faq}
{: support}

Yes. Secrets are not stored locally during migration; a tool is provided to export secrets securely to Secrets Manager. The [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) provides best practices.


## Where can I find all documentation in one place?
{: #documentation}
{: faq}
{: support}

The [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) provides:
* Toolchain migration steps
* Git Repos & Issue Tracking (GRIT) direct transfer instructions
* Secrets export to Secrets Manager
* Post-migration validation & billing optimization


## What are the main capabilities of DevOps Insights (DOI)?
{: #doi_capabilities}
{: faq}
{: support}

DOI provided advanced analytics and dashboards for pipeline quality, deployment risk, and compliance checks. It integrated with pipelines to enforce policies and visualize metrics like test coverage, build success rates, and vulnerability scans.


## What are the main capabilities of Code Risk Analyzer (CRA)?
{: #cra_capabilities}
{: faq}
{: support}

CRA analyzes application code and dependencies for security vulnerabilities and license compliance issues. It also generated SBOM (Software Bill of Materials) reports and validated Terraform plans against compliance rules, helping enforce security and governance policies before infrastructure changes were applied.


## Will my DOI dashboards or CRA reports be accessible after the cutoff date?
{: #doi_cra_accessible}
{: faq}
{: support}

No. All DOI dashboards and CRA reports will be removed after 12 February 2027. If a region is discontinued earlier due to inactive usage, dashboards and reports in that region will be removed at the time of closure. Please export any required data before the End of Service date or any earlier regional closure.


## What are the recommended alternatives for DevOps Insights (DOI)?
{: #doi_alternatives}
{: faq}
{: support}

For DevOps Insights (DOI): IBM recommends using [IBM Concert](https://www.ibm.com/products/concert){: external}, which provides governance, compliance, and risk management capabilities for DevOps processes.


## What are the recommended alternatives for Code Risk Analyzer (CRA)?
{: #cra_alternatives}
{: faq}
{: support}

For SBOM generation and vulnerability scanning, consider third-party or open-source tools such as [Syft](https://github.com/anchore/syft){: external} or [Grype](https://github.com/anchore/grype){: external}.
