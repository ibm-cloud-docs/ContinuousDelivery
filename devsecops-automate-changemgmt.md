---

copyright:
  years: 2021
lastupdated: "2021-06-25"

keywords: DevSecOps, automate change management, change management

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Automating change management
{: #cd-devsecops-automate-changemgmt}

Change management automation is one of the crucial parts of the one-pipeline reference implementation. With {{site.data.keyword.contdelivery_notm}}, developers, approvers, and auditors can track the compliance aspects of deployments. <staging>Every deployment must follow the [{{site.data.keyword.cloud_notm}} Change Management Policy](https://ibm.ent.box.com/s/z0nklp949ztsjm4vqn0gvo5k4bjx8eya){: external}.</staging>
{: shortdesc}

<!-- Does this first link need to be changed or can anyone access that box link?-->

The pipelines collect [evidence](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-evidence) from every part of the build and deployment lifecycle. Every piece of evidence correlates to a certain build and deployment of the artifacts. So, for each deployed artifact, we should be able to tell, if its build or test deployment had incidents or not. This correlation is implemented through the [inventory model](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-inventory).

In this document you can find answers to the following questions regarding change management automation:

* How are evidence, inventory, and change management connected?
* What are the change request fields in a promotion pull request?
* How does automatic change request approval happen?
* What is deployment readiness?
* What data is included in a change request?
* How can I use an existing change request ID in the CD pipeline?

<staging>
<!-- I expect this next heading section needs to be removed bc it's internal only? -->

## ServiceNow
{: #servicenow-change-management}

Service Framework item OSS015 requires all services to use Service Now as their change management tool.

## Connection between evidence, inventory, and change management
{: #connection-evidence-inventory-change}

![Connection between evidence, inventory, and change management](images/change-management-data-flow.svg "Flow diagram showing the relationship between evidence, inventory, and change management"){: caption="Figure 1. Connection between evidence, inventory, and change management" caption-side="bottom"}

1. CI runs build artifacts and leave evidence behind about what happened during the creation of those artifacts.
2. CI runs create entries about the created artifacts in the inventory.
3. Built artifacts in the Inventory are [promoted](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-inventory) to deployment environments, like staging or pre-production.
4. Change management automation uses data from the inventory, the evidence locker, and the promotion PR to create the change request
deployments, also leaving evidence behind about acceptance tests for example. Successfully deployed and tested artifacts are further promoted to production environments, like production.

Every deployment to every environment and region needs to file a change request to the change management system Service Now. Change management automation helps you to create these change requests based on all the evidence and information that is collected from the pipelines.

</staging>

## Change request fields in promotion PR
{: #cr-fields-promotion-pr}

To start filling out the fields of a change request (CR), we provide a PR template in the inventory for the promotion PRs.

* These fields are the ones that can't be determined automatically. The teams who want to promote changes should fill these out.
* Filling out these fields is a manual step that can trigger deployment itself and continue automatic data collection for the rest of the CR.

![Promotion PR template example](images/promotion-pr.png "Promotion PR example showing the fields to be filled out"){: caption="Figure 2. Promotion PR template example" caption-side="bottom"}

Review the following fields shown in the example:

* **Priority**
    The priority of the change must be one of the following:
    `Critical | High | Moderate | Low | Planning`

* **Change Request assignee**
    The email address of the person who will be assigned to the CR.
    Must be an existing user in Service Now.

* **Additional Description**
    Explain the change process.
    Additional content by the automation process is appended here.

* **Purpose/Goal**  
    Explain the purpose of the change.

* **Explanation of Impact** 
    The possible impact of the change.

* **Backout Plan**  
    Explain a rollback or backout plan.

<!-- Emergency mode links go to what looks like the planned topic for this content even though it isn't there as of 6/21-->

For the change type, Service Now supports two types of change, Emergency or Regular. If the current change is an Emergency change, add the Emergency label to the Promotion PR. For more information, see [Emergency mode](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-approve-cr) and [Promotion Pipeline](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-promotion-pipeline).

## Automatic CR approval and deployment readiness
{: #automatic-cr-approval}

Service Now automatically approves CRs on the following conditions:

* Implementing the change costs no downtime (outage duration is zero)
* Deployment Readiness is true

The change management automation in the one-pipeline reference implementation assumes that all changes are implemented without planned downtime. If your planned changes require planned downtime, you must create the CR manually and send it to approval. When it is approved, you can start deployment by providing the CR ID. The pipeline skips ahead to check its approval, and run the deployment.

Deployment Readiness is calculated from the evidence that is collected in CI and CD stages. If any of the collected evidence suggests a deviation, a non-successful check, scan, or test that is related to the deployed set of artifacts, the Deployment Readiness is set to false, and the CR won't be auto-approved. In this case, the deployment stops and prevents further steps, until the CR is approved.

You can read the created CR ID from the pipeline logs, await approval, and restart deployment by providing the same CR ID. The pipeline skips ahead to checking its approval and continues deployment.

If the change is a type of `emergency`, the CR is supposed to be retroactively reviewed and approved. For more information, see [Emergency mode](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-approve-cr).

## Data included in the change requests
{: #cr-data}

The reference implementation standardizes the way a CR is populated, in particular, the following sections:

* Description & Plan section
* Change Tasks
* Rollback

The content of the CR is populated in such a way as to simplify a compliance audit. Thus it points to the key evidence generated by the CI/CD process. It is important not to disclose to the CR readers/approvers any more information than is needed. For example, the CR contains references to scan logs but not the actual logs, it contains the reference to the build BOM but not the build BOM itself. It is the adopter's responsibility to honor the "need to know" and "minimum privilege" principles when granting access to the required information resources and assets.
{: note}

### Description and Plan section
{: #description-plan-section}

The content of the Description & Plan section is organized in the following way:

* CI INVENTORY COMMIT URL
    Here there is the pointer to the GitHub commit ID that represents your CI inventory. The CI inventory contains information about the code level that is getting deployed and the artifacts with their signature/checksums that are going to be deployed with this CR.

    Example: https://github.ibm.com///commit/

* CHANGE LOG
    Here there is the list of all commit IDs with the respective description included in the code level that is getting deployed.

    ```
    Git changelog for mymicroservice:

    Git changelog of artifact '"uk.icr.io/mycontainerregistrynamespace/mymicroservice:one-pipeline4@sha256:733e74a13ad26d77a741204bcdc9c5f8f77023b26620ddaa7842d29b600014a0"' 
 
    COMMITS:
    94de4256c346c00fee9fd5f7bbfb114ed4da7c81 - implemented myfunction
    ```

* PULL REQUESTS
    `mymicroservicerepo: <PR #> - (Merge pull request #15 implemented myfunction)`

* TEST AND SCANS RESULTS
    “No issues” found if no failures reported in the evidence summary or the list of failed IDs, (for example: com.ibm.cloud.image_vulnerability_scan: failed; com.ibm.unit_tests: failed), with the abstract of the issues opened so that the approver can have an idea about what is failing.

### Change tasks
{: #change-tasks}

<!-- next two links need new targets or to be removed most likely -->

Change tasks are currently used to append data attachments to the CR. Three change tasks are created to include the evidence summary and the deployment BOM.

* EVIDENCE SUMMARY
    Here the key information about tests and scans results and which issues have been opened while running them. The entries in this section are reformatted version of the `summary.json` file. For more information, see https://github.ibm.com/cocoa/evidence-summary/.

*  DEPLOYMENT BOM
    This is the list of all artifacts, together with their digital signature/checksum that is transferred into the target environment to successfully perform the deployment (see https://github.ibm.com/CloudEngineering/system_architecture/blob/master/docs/devops/appendix.md#recommended-deployment-bom-format)

* CLOSING SUMMARY
    The summary of all evidence that relates to the current deployment at the point of closing the CR

### Rollback
{: #cr-rollback}

The rollback section should be describing:

* The version to roll back to
* The exact steps to follow in case the rollback is not just deployment of the previous version

## Using an existing change request ID
{: #existing-cr-id}

<!-- Again, not sure about the use of this box link below-->

There are a few use cases when you don't want to use the automated Change Management but provide a previously created and approved CR.

* The latest automatically created CR was not ready for deployment, and the CR was not auto-approved. You got approval for the CR and must restart deployment using that CR again
* The deployment requires downtime. You've created the CR, got it approved, and followed the required steps in the [{{site.data.keyword.cloud_notm}} Change Management Policy](https://ibm.ent.box.com/s/z0nklp949ztsjm4vqn0gvo5k4bjx8eya){: external}
* No code or configuration was changed. You've created the CR, explaining what was changed if not your application code, got it approved, and start a deployment by using the approved Change Request.

You can start the one-pipeline reference CD pipeline with a pre-approved CR by providing the CR ID in the field `change-request-id`.

![Preapproved CR](images/pre-approved-cr.png "change-request-id field set to notAvailable"){: caption="Figure 3. Preapproved CR" caption-side="bottom"}

If the `change-request-id` is available, the pipeline skips data collection for the CR and jumps ahead to check the approval state of the CR.
