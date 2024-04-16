---

copyright:
  years: 2016, 2024
lastupdated: "2024-04-15"

keywords: code quality, risk management, interactions of your team, devops insights, getting started, devops, insights, tutorial, code coverage, test, tests, gate, gate failing, verification, install, app, dashboard

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Working with {{site.data.keyword.DRA_short}}
{: #di_working}

{{site.data.keyword.DRA_full}} is a tool that aggregates code, test, build, and deployment data to provide visibility of quality for all of your teams. This tutorial walks you through the quickest steps for setting up {{site.data.keyword.DRA_short}} with {{site.data.keyword.contdelivery_full}} so that you can explore the features in {{site.data.keyword.DRA_short}}.
{: shortdesc}

With {{site.data.keyword.DRA_short}}, you can maintain and improve the quality of your code in {{site.data.keyword.cloud}}. You can monitor your deployments to identify risks before they are released, analyze development changes for error probability, and improve the interactions of your team.

{{site.data.keyword.DRA_short}} collects and analyzes the results from unit tests, functional tests, and code coverage tools. It uses these results to determine whether your code meets predefined policies at specified gates in your deployment process. If your code does not meet or exceed a policy, the deployment is halted, preventing risks from being released. You can use {{site.data.keyword.DRA_short}} as a safety net for your continuous delivery environment or as a way to implement and improve quality standards.

## Before you begin
{: #prereq-devops-insights}

Authorize the use of GitHub repos. For more information, see [Authenticating with Git Repos and Issue Tracking](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication). 


## Step 1. Add the toolchain by using a template
{: #1-add-toolchain}

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Expand the **Location** menu, and select a location for your deployment. {{site.data.keyword.DRA_short}} is available in Dallas, London, and Frankfurt. 
3. Click **Create a Toolchain**.
4. Select the **{{site.data.keyword.DRA_short}} Quick Start Demo** tile.  
5. In the Tool Integrations section, create an API key for {{site.data.keyword.deliverypipeline}}. 
6. Click **Create** to finish creating the toolchain.

If you need to authorize {{site.data.keyword.cloud_notm}} to use GitHub, click **GitHub** > **Authorize**.
{: tip}

You can also create and manage a toolchain that includes a {{site.data.keyword.DRA_short}} tool integration by using Terraform. For more information about using Terraform, see [Setting up Terraform for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-terraform-setup).
{: tip}

## Step 2. Run a build to send data to {{site.data.keyword.DRA_short}}
{: #2-run-build}

You run builds to see data within {{site.data.keyword.DRA_short}}. When you created this template, a build ran automatically in the {{site.data.keyword.deliverypipeline}}. You will see data within {{site.data.keyword.DRA_short}} after the build stage completes. 

Click the **{{site.data.keyword.deliverypipeline}}** tile to view the build process. The process might take several minutes to finish. When the build stage completes, continue to step 3. 

For more information about pipelines, see [{{site.data.keyword.deliverypipeline}} overview](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_about).


## Step 3. View the data analyzed by {{site.data.keyword.DRA_short}}
{: #3-view-data}

Explore the Quality Dashboard page to see the data aggregated from {{site.data.keyword.deliverypipeline}}. The quality dashboard provides quality data sets for each application.  

1. Click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. On the Toolchains page, click the {{site.data.keyword.DRA_short}} toolchain to open its Overview page.
3. On the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration. 
4. Click **Quality Dashboard**.

You can view details about the Weather Application and the quality of the code that was analyzed. These tests are available where the policy gates passed: code coverage, unit test, and the functional verification test. You can click the build ID, for example, `master:1`, to view a summary for that specific test. Click **View trends** to view trend details.

For more information about the quality dashboard, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).


## Step 4. Test a gate against a {{site.data.keyword.DRA_short}} policy decision
{: #4-test-gate}

A gate is created when you enact a policy. A policy is a set of rules that you can customize, and a rule is the passing criteria that you define for each type of test data you upload. The gate passes or fails a build based on the quality standards that you choose. So, if your code doesn't meet or exceed a policy that is enacted at a particular gate, the deployment is stopped to prevent risky changes from being released. 

For the Weather Application, the code coverage rule set for the policy is that the minimum code coverage required is 80%. The gate is placed before the production stage within the pipeline. When you first create this template, the app passes all current gates, but gates sometimes fail. 

To make a gate fail, edit the code in the `routes/apivl.js` file so that the code coverage reaches only 60%. The gate fails because the code doesn't reach the necessary quality and deployment isn't pushed to production.  

1. Open the `routes/apivl.js` file in an editor.
2. Uncomment lines 42-72 and save the file.
3. From a Git client, commit and push your changes.
4. On your toolchain's Overview page, on the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration to observe the gate fail in real time. 

## Step 5. Analyze the failed gate
{: #5-risk-analysis}

The gate fails because the code coverage isn't met. When you gate your own deployments, you can determine whether it failed or passed by looking at the Risk Analysis page. Also, you can define, change, and customize policies and rules to fit your needs when it comes to gating deployments. View the policies and rules that make the gate. 

1. Click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. On the Toolchains page, click the {{site.data.keyword.DRA_short}} toolchain to open its Overview page.
3. On the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration. 
4. Click **Policies** > **Weather Unit Test, Code Coverage, and FVT Checks**. 
5. Click **Code coverage** to view the minimum code coverage required. Anything equal to or over 80% will release to the next stage.  
6. Click **Risk analysis** to check whether your deployment passed or failed the gate. Risk is evaluated based on the defined policies within {{site.data.keyword.DRA_short}}.
7. Select the build with the failed policy to view the test summary details.

## Next steps
{: #tutorial-next-steps}

You might want to create your own toolchain with {{site.data.keyword.DRA_short}} or add {{site.data.keyword.DRA_short}} to an existing project. For more information, see [Adding {{site.data.keyword.DRA_short}} to your toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-add-devops-insights).
