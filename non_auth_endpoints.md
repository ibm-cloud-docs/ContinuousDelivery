---

copyright:
  years: 2025
lastupdated: "2025-01-01"

keywords: endpoints, authentication, IBM Cloud Public

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}  
  
# Endpoints that do not require authentication in {{site.data.keyword.contdelivery_short}}  
{: #non-auth-endpoints-cd}  
  
{{site.data.keyword.contdelivery_full}} provides many internet-accessible endpoints. Although most endpoints authenticate the caller before processing requests, some endpoints intentionally do not authenticate the caller.  
{: shortdesc}

The following inventory of endpoints that do not require authentication is organized by the major components of the {{site.data.keyword.contdelivery_short}} service.  

{{site.data.keyword.contdelivery_short}} is a regional service. In each of the documented endpoints, `[region]` represents the ID of [any region in which {{site.data.keyword.contdelivery_short}} is available](/docs/overview?topic=overview-locations#table-mzr). For example, regions include `us-south`, `us-east`, `eu-gb`, and `jp-tok`.
{: tip}

## Code Risk Analyzer
{: #code_risk_analyzer}

The following table lists the Code Risk Analyzer endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://clairupdater.[region].devopsinsights.cloud.ibm.com/alive` | Get the liveness status of the service component |
| `https://clairupdater.[region].devopsinsights.cloud.ibm.com/ready` | Get the readiness status of the service component |
| `https://clairupdater.[region].devopsinsights.cloud.ibm.com/status` | Get the status of the service component |
| `https://gitsecure.[region].devopsinsights.cloud.ibm.com/alive` | Get the liveness status of the service component |
| `https://gitsecure.[region].devopsinsights.cloud.ibm.com/ready` | Get the readiness status of the service component |
| `https://gitsecure.[region].devopsinsights.cloud.ibm.com/status` | Get the status of the service component |
| `https://vcurator.[region].devopsinsights.cloud.ibm.com/alive` | Get the liveness status of the service component |
| `https://vcurator.[region].devopsinsights.cloud.ibm.com/ready` | Get the readiness status of the service component |
| `https://vcurator.[region].devopsinsights.cloud.ibm.com/status` | Get the status of the service component |
{: caption="Table 1. Code Risk Analyzer" caption-side="top"}

## {{site.data.keyword.deliverypipeline}}
{: #delivery_pipeline}

The following table lists the {{site.data.keyword.deliverypipeline}} endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://blade-pipeline-broker.[region].devops.cloud.ibm.com/status` | Get the status of the Blade Pipeline Broker service component |
| `https://blade-pipeline-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pipeline-consumption.[region].devops.cloud.ibm.com/healthcheck` | Get the health check status for service component |
| `https://pipeline-consumption.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline Consumption service component |
| `https://pipeline-consumption.[region].devops.cloud.ibm.com/tekton_healthcheck` | Get the Tekton health check status for service component |
| `https://pipeline-consumption.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pipeline-event-service.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline Event Service service component |
| `https://pipeline-event-service.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pipeline-log-service.[region].devops.cloud.ibm.com/readiness` | Get the readiness status of the service component |
| `https://pipeline-log-service.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline Log Service service component |
| `https://pipeline-log-service.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pipeline-support-service.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline Support Service service component |
| `https://pipeline-support-service.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pipeline-ui.[region].devops.cloud.ibm.com/readiness` | Get the readiness status of the service component |
| `https://pipeline-ui.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline UI service component |
| `https://pipeline-ui.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://private-worker-service.[region].devops.cloud.ibm.com/chains/public_key` | Get the public key used by chains for signing |
| `https://private-worker-service.[region].devops.cloud.ibm.com/install` | Get the install script to install the private worker agent on the internal or external platform |
| `https://private-worker-service.[region].devops.cloud.ibm.com/status` | Get the status of the Private Worker Service service component |
| `https://private-worker-service.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pwp-meter.[region].devops.cloud.ibm.com/pwprun` |  |
| `https://pwp-meter.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline Worker Pool meter |
| `https://pwp-meter.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://pwp-service.[region].devops.cloud.ibm.com/:poolId/subscriptions/:subscriptionId` |  |
| `https://pwp-service.[region].devops.cloud.ibm.com/status` | Get the status of the Pipeline Worker Pool Service service component |
| `https://pwp-service.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://tekton-pipeline-service.[region].devops.cloud.ibm.com/status` | Get the status of the Tekton Pipeline Service service component |
| `https://tekton-pipeline-service.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
{: caption="Table 2. {{site.data.keyword.deliverypipeline}}" caption-side="top"}

## {{site.data.keyword.DRA_short}}
{: #devops_insights}

The following table lists the {{site.data.keyword.DRA_short}} endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://dlms.[region].devopsinsights.cloud.ibm.com/status` | Get the readiness status of the service component |
| `https://dlms.[region].devopsinsights.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otcbroker.[region].devopsinsights.cloud.ibm.com/livenessprobe` | Get the liveness status of the service component |
| `https://otcbroker.[region].devopsinsights.cloud.ibm.com/readinessprobe` | Get the readiness status of the service component |
| `https://otcbroker.[region].devopsinsights.cloud.ibm.com/status` | Get the status of the service component |
| `https://pipelinemetrics.[region].devopsinsights.cloud.ibm.com/status` | Get the readiness status of the service component |
| `https://pipelinemetrics.[region].devopsinsights.cloud.ibm.com/version` | Get the build version of the service component |
| `https://rcbroker.[region].devopsinsights.cloud.ibm.com/cluster-healthcheck` | Get the cluster health check status for service component |
| `https://rcbroker.[region].devopsinsights.cloud.ibm.com/healthcheck` | Get the health check status for service component |
| `https://rcbroker.[region].devopsinsights.cloud.ibm.com/livenessprobe` | Get the liveness status of the service component |
| `https://rcbroker.[region].devopsinsights.cloud.ibm.com/readinessprobe` | Get the readiness status of the service component |
| `https://rcbroker.[region].devopsinsights.cloud.ibm.com/status` | Get the status of the service component |
| `https://tagging.[region].devopsinsights.cloud.ibm.com/livenessprobe` | Get the liveness status of the service component |
| `https://tagging.[region].devopsinsights.cloud.ibm.com/status` | Get the readiness status of the service component |
{: caption="Table 3. {{site.data.keyword.DRA_short}}" caption-side="top"}

## {{site.data.keyword.gitrepos}}
{: #git_repos_and_issue_tracking}

The following table lists the {{site.data.keyword.gitrepos}} endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://hosted-git-metrics.[region].devops.cloud.ibm.com/health` | Get the health of the service component |
| `https://hosted-git-metrics.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://hosted-git-metrics.[region].devops.cloud.ibm.com/status-all` | Get the status of the service component and its dependencies |
| `https://hosted-git-metrics.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://hosted-git-monitor.[region].devops.cloud.ibm.com/health` | Get the health of the service component |
| `https://hosted-git-monitor.[region].devops.cloud.ibm.com/load_balancer` | Get the status of the load balancer |
| `https://hosted-git-monitor.[region].devops.cloud.ibm.com/scorecard` | Get the status of the scorecard |
| `https://hosted-git-monitor.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://hosted-git-monitor.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
{: caption="Table 4. {{site.data.keyword.gitrepos}}" caption-side="top"}

## Metrics
{: #metrics}

The following table lists the Metrics endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://otc-consumption.[region].devops.cloud.ibm.com/healthcheck` | Get the current aggregated status of the consumption monitors that this application watches |
| `https://otc-consumption.[region].devops.cloud.ibm.com/status` | Get the current health status of the application |
| `https://otc-consumption.[region].devops.cloud.ibm.com/version` | Get the version of the application |
| `https://otc-metrics-listener.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://otc-metrics-listener.[region].devops.cloud.ibm.com/version` | Get the version of the service component |
{: caption="Table 5. Metrics" caption-side="top"}

## Third-party tool integrations
{: #third-party_tool_integrations}

The following table lists the third-party tool integration endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://otc-cti-broker.[region].devops.cloud.ibm.com/status` | Get the status of the Custom Tool Integration Broker service component |
| `https://otc-cti-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-github-broker.[region].devops.cloud.ibm.com/spec` | Get the static assets of the service component |
| `https://otc-github-broker.[region].devops.cloud.ibm.com/static` | Get the static assets of the service component |
| `https://otc-github-broker.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://otc-github-broker.[region].devops.cloud.ibm.com/status-all` | Get the status of the service component and its dependencies |
| `https://otc-github-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-pagerduty-broker.[region].devops.cloud.ibm.com/status` | Get the status of the Pagerduty Broker service component |
| `https://otc-pagerduty-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-saucelabs-broker.[region].devops.cloud.ibm.com/nls` | Get the Sauce Labs error messages |
| `https://otc-saucelabs-broker.[region].devops.cloud.ibm.com/status` | Get the status of the Sauce Labs Broker service component |
| `https://otc-saucelabs-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-slack-broker.[region].devops.cloud.ibm.com/status` | Get the status of the Slack Broker service component |
| `https://otc-slack-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-toolint-broker.[region].devops.cloud.ibm.com/status` | Get the status of the Tools Integration Broker service component |
| `https://otc-toolint-broker.[region].devops.cloud.ibm.com/toolint-broker/api/v1/form` | Forwards the Authenticate, Populate, and Validate (APV) requests to the appropriate broker |
| `https://otc-toolint-broker.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
{: caption="Table 6. Third-party tool integrations" caption-side="top"}

## Toolchain platform
{: #toolchain_platform}

The following table lists the Toolchain platform endpoints that do not require authentication:

|Endpoint|Description|
|:-------------------------------------------|:------------------|
| `https://otc-api.[region].devops.cloud.ibm.com/` | Get the status of the service component |
| `https://otc-api.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://otc-api.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-status.[region].devops.cloud.ibm.com/clusterhealth` | Get the cluster health check status for service component |
| `https://otc-status.[region].devops.cloud.ibm.com/dependencies` | Get the otc dependency status |
| `https://otc-status.[region].devops.cloud.ibm.com/monitoring/cache/current/{service}` | Get the cached status of the service component |
| `https://otc-status.[region].devops.cloud.ibm.com/monitoring/cache/latestFailure/{service}` | Get the latest failure of the service component |
| `https://otc-status.[region].devops.cloud.ibm.com/monitoring/service` | Get the list of services |
| `https://otc-status.[region].devops.cloud.ibm.com/monitoring/status` | Get the list of monitored services |
| `https://otc-status.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://otc-status.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-status.[region].devops.cloud.ibm.com/versioncheck` | Get the versions of all apps in the clusters |
| `https://otc-status.[region].devops.cloud.ibm.com/versioncheck/info` | Get information about the cluster version |
| `https://otc-ui.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://otc-ui.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
| `https://otc-webhook-manager.[region].devops.cloud.ibm.com/status` | Get the status of the service component |
| `https://otc-webhook-manager.[region].devops.cloud.ibm.com/version` | Get the build version of the service component |
{: caption="Table 7. Toolchain platform" caption-side="top"}
