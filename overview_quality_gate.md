---

copyright:
  years: 2016, 2024
lastupdated: "2024-11-20"

keywords: devops insights, create, policy, rule, gate, code coverage, test, tests, gate failing, verification, app, dashboard

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Using gate policies to ensure quality
{: #gate-ensure-quality}

A gate policy is a set of rules that can be used to ensure that a build meets certain quality criteria before being deployed to your chosen environment. Gates check if your test results comply with a defined policy. If the policy is not met, the {{site.data.keyword.DRA_short}} gate fails by default and the build will not deploy. You can also configure gates to act in an advisory role to allow pipeline progression even after failure.
{: shortdesc}

{{site.data.keyword.DRA_full}} supports many popular formats for test data like unit tests, functional verification tests, and custom data sets, {{site.data.keyword.DRA_short}} supports JUnit or XUnit, and Mocha. For code coverage and custom data sets, {{site.data.keyword.DRA_short}} supports Cobertura, lcov, and JaCoCo. You can use any tool within your toolchain to run your unit tests, code coverage tests, functional verification tests, and then capture your test results in any one of the supported formats.

For more information about toolchains, see [Creating a toolchain from an app](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app). For more information about data sets, see [Managing data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-adding-data-sets).

![Deployment Risk Policy](images/DRA_policy.png){: caption="Policy and rules page" caption-side="bottom"}

To go to the Policy Rules page within {{site.data.keyword.DRA_short}}, complete the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
1. On the Toolchains page, click your toolchain to open its Overview page.
1. On the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration.
1. From the menu, select **Policies** and then select a policy.

## Gate decisions
{: #gate-decisions}

In your pipeline, you can enter a command by using the {{site.data.keyword.Bluemix_notm}} CLI to check the quality of a build against a predefined policy. When the policy is evaluated, you can check the decision in the {{site.data.keyword.DRA_short}} tool.

### Build detail page
{: #build_detail_page}

![Deployment Risk details](images/DRA_risk_details.png){: caption="Build detail" caption-side="bottom"}

From the Risk Analysis page, you can view gate decision reports on the Build detail page. The Build detail page has information about your latest report.

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
1. On the Toolchains page, click your toolchain to open its Overview page.
1. On the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration.
1. From the menu, select **Risk Analysis** and then click the **Application** tab.
1. From the table, select the application that you want to view and then select the build.

### Decision report
{: #decision_report}

You can also view data for particular decisions based on the policy assigned to a build. From the Build detail page, navigate to the Decision report page. Select **View details** from the Decisions for this build table for the policiy decision you want to view.

## Defining policies and rules
{: #defining-policies-rules}

A policy is a set of rules that you can customize, and a rule is the passing criteria that you define for each type of test data you upload. Policy rules can be evaluated by gates. Gates are the mechanism that is implemented in continuous integration and continuous delivery (CI/CD) tools to hold back your build if it doesn't meet the passing threshold. If your code doesn't meet or exceed a policy that is enacted at a particular gate, the deployment is stopped to prevent risky changes from being promoted to the next environment.
{: shortdesc}


### Creating policies and rules
{: #create_policies}

A policy is a set of rules that define the criteria that your gate uses to determine whether a build will be promoted to the next stage in a CI/CD tool. For example, you can create a policy that contains a unit test rule that requires 100 percent success and a test coverage rule that requires 80 percent coverage. A gate refers to this policy to prevent builds that don't satisfy both rules from proceeding.

To create a policy, complete the following steps:
1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
1. On the Toolchains page, select your toolchain.
1. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
1. Select **Policies**.
1. Click **Create Policy**.
1. Complete all of the required fields, and click **Next**.
1. Click **Create Rule**.
1. Complete all of the required fields.
1. Optional. Select the **Regression Check** box to opt out of test case regression. This option is available only for data sets, Unit Tests, Code Coverage, and Functional Verification Tests.
1. Click **Save**.

If you want to add another rule, repeat from step 3.

For more information about data sets, see [Managing data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-adding-data-sets).


### Adding a rule to an already established policy
{: #add-rule-policy}

You can add rules to policies that are already defined.

1. From the Policies page, select the policy to add the rule.
1. Click **Create Rule**.
1. Complete all required fields, then click **Save**.


### Editing rules
{: #editing-rules}

You can edit the rules that you established with your policies. You can change the rule description, the results file format, and the minimum code coverage required.

To edit rules, complete the following steps:
1. From the Policies page, select the policy that has the rule you want to edit.
1. Click the Edit icon ![write icon](images/icon_write.svg) for the rule.
1. Complete all required fields, and click **Save**.
