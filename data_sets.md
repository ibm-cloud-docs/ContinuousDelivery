---

copyright:
  years: 2019, 2023
lastupdated: "2023-05-25"

keywords: devops insights, quality, dashboard, trends, data sets, configure data, quality data, managing data sets, code coverage, test, tests, verification, app, sonarqube

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Managing data sets
{: #adding-data-sets}

Data sets are defined to identify the types of tests that you run in your development process to define the passing criteria for an application. When you define rules in a policy, {{site.data.keyword.DRA_full}} provides seven pre-defined data sets that you can use to run in your development process. Or, use custom data sets to represent the various types of tests. You can have policy rules for each data set and define rules for custom data sets. Separate policies can be created for each application. Data sets appear on the Quality Dashboard page after you start populating data for the data set. 
{: shortdesc}

For more information about viewing the Quality Dashboard, see [DevOps data aggregation](/docs/ContinuousDelivery?topic=ContinuousDelivery-devops-data-aggregation).

For more information about defining a policy, see [Defining policies and rules](/docs/ContinuousDelivery?topic=ContinuousDelivery-defining-policies-rules).


## Viewing data sets
{: #viewing-data-sets}

View your current data sets by browsing your Quality Dashboard page. You can rearrange your data in the table to be in a more convenient order. To view your data sets, use the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. On the Toolchains page, select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Select **Quality Dashboard**.
5. Click the **Overflow** icon ![ellipsis icon](images/overflow-icon-2.svg) > **Configure data set**.


## Adding predefined data sets
{: #predefined-data-sets}

To add a data set to the application's test, use the following steps:

1. Click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. On the Toolchains page, select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Quality Dashboard**.
5. Click the **Overflow** icon ![ellipsis icon](images/overflow-icon-2.svg) > **Configure data set**.
6. Click **Add Quality Data Set**.
7. Select **Predefined Quality Data Sets**.
8. Complete all required fields, and click **Submit**

The following are the seven pre-defined tags that are provided by {{site.data.keyword.DRA_short}}. 

| Pre-defined Data Set Tag | Display label            | Data Type             | Supported Data Formats                                     |
|--------------------------|-------------------------------|-----------------------|------------------------------------------------------------|
| `unittest`                 | Unit Tests                    | Test Case             | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON) |
| `code`                     | Code Coverage                 | Code Coverage         | Cobertura (xml), lcov (info), JaCoCo (xml)|
| `fvt`                      | Functional Verification Tests | Test Case             | JUnit (JSON), xUnit (xml), Mocha (JSON), KarmaMocha (JSON) |
| `sonarqube`                | SonarQube                     | SonarQube             | SonarQube                                                  |
| `dynamicsecurityscan`      | Dynamic Security Scan         | Dynamic Security Scan | {{site.data.keyword.Bluemix}} Application Security (xml)   |
| `staticsecurityscan`       | Static Security Scan          | Static Security Scan  | {{site.data.keyword.Bluemix}} Application Security (xml)   |
| `vulnerabilityadvisor`     | Vulnerability Advisor         | Vulnerability Advisor | Vulnerability Advisor (JSON)                               |
{: caption="Table 1. Default {{site.data.keyword.DRA_short}} data sets" caption-side="top"}


## Adding custom data sets
{: #custom-data-sets}

You can add your own custom data sets. Custom data sets support JUnit or XUnit, Mocha, Cobertura, lcov, and JaCoCo. To add custom data sets, use the following steps:

1. Click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. On the Toolchains page, select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Quality Dashboard**.
5. Click the **Overflow** icon ![ellipsis icon](images/overflow-icon-2.svg) > **Configure data set**.
6. Click **Add Quality Data Set**.
7. Select **Custom Quality Data Sets**.
8. Complete all required fields, and click **Submit**

If a custom data set is deleted, any test results for that custom data set are deleted. For more information about deleting data sets, see [Deleting your {{site.data.keyword.DRA_short}} data](/docs/ContinuousDelivery?topic=ContinuousDelivery-deleting_data).
{: tip}
