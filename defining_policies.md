---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-17"

keywords: devops insights, create, policy, rule, gate, edit rule, add rule, define policy, code coverage, test, tests, gate failing, verification, risk

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Defining policies and rules
{: #defining-policies-rules}

A policy is a set of rules that you can customize, and a rule is the passing criteria that you define for each type of test data you upload. Policy rules can be evaluated by gates. Gates are the mechanism that is implemented in continuous integration and continuous delivery (CI/CD) tools to hold back your build if it doesn't meet the passing threshold. If your code doesn't meet or exceed a policy that is enacted at a particular gate, the deployment is stopped to prevent risky changes from being promoted to the next environment.
{: shortdesc}


## Creating policies and rules
{: #create_policies}

A policy is a set of rules that define the criteria that your gate uses to determine whether a build will be promoted to the next stage in a CI/CD tool. For example, you can create a policy that contains a unit test rule that requires 100 percent success and a test coverage rule that requires 80 percent coverage. A gate refers to this policy to prevent builds that don't satisfy both rules from proceeding.

To create a policy, complete the following steps:
1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**.
2. Select your toolchain from the table.  
3. Click the **{{site.data.keyword.DRA_short}}** tile.
4. Select **Policies**.  
5. Click **Create Policy**.  
6. Complete all required fields, and click **Next**.  
7. Click **Create Rule**.
8. Complete all required fields.
9. Optional: Select **Regression Check** box to opt out of test case regression. This option is only available for data sets Unit Tests, Code Coverage, and Functional Verification Tests.   
10. Click **Save**.

If you want to add another rule, repeat from step 3.

For more information about data sets, see [Managing data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-adding-data-sets). 


## Adding a rule to an already established policy
{: #add-rule-policy}  

You can add rules to policies that are already defined.

1. From the Policies page, select the policy to add the rule.
2. Click **Create Rule**.
3. Complete all required fields, then click **Save**.


## Editing rules
{: #editing-rules}

You can edit the rules that you established with your policies. You can change the rule description, the results file format, and the minimum code coverage required.

To edit rules, complete the following steps:
1. From the Policies page, select the policy that has the rule you want to edit.
2. Click the Edit icon ![write icon](images/icon_write.svg) for the rule.  
3. Complete all required fields, and click **Save**.
