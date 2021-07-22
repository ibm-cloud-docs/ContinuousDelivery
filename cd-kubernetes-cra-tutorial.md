---

copyright:
   years: 2021
lastupdated: "2021-04-20"

keywords: Code Risk Analyzer, code repositories, DevOps Insights, scan pull requests, Tekton pipelines

subcollection: ContinuousDelivery

content-type: tutorial
account-plan: lite
completion-time: 40m

---

{:shortdesc: .shortdesc}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Use the Develop a Kubernetes app toolchain with Code Risk Analyzer
{: #tutorial-cd-kube-cra}
{: toc-content-type="tutorial"}
{: toc-completion-time="40m"}

In this tutorial, you use {{site.data.keyword.contdelivery_full}} to create an open toolchain that includes {{site.data.keyword.gitrepos}}, a Tekton-based delivery pipeline, and Code Risk Analyzer.
{: shortdesc}

Use [Code Risk Analyzer](https://www.ibm.com/cloud/blog/announcements/find-source-code-vulnerabilities-with-code-risk-analyzer){: external} to discover vulnerabilities in your Python, Node.js, and Java&reg; applications (apps), and in your operating system stacks (base image). Code Risk Analyzer uses rich threat intelligence from [Snyk](https://snyk.io){: external} and [Clair](https://github.com/quay/clair){: external} and then provides fix recommendations. Code Risk Analyzer also integrates the comprehensive security coverage in Snyk to help you to automatically find, prioritize, and fix vulnerabilities in open-source dependencies and containers early in your workflow.

After you create the toolchain, you use it and DevOps practices to develop a simple Hello World web app that you deploy to an [{{site.data.keyword.containerlong}}](/docs/containers) cluster.

The pipeline builds the Hello World app into a container image that is stored in the {{site.data.keyword.cloud_notm}} Container Registry. The image is checked for security issues by using [Vulnerability Advisor](/docs/Registry?topic=va-va_index) before it is deployed to your Kubernetes cluster.

![Architectural diagram](images/image.svg)
{: figure caption="Figure 1. A diagram that shows the architecture for my tutorial."}

The pipeline that you create has the following architecture:
1. Workflow step 1
1. Workflow step 2
1. Workflow step 3
1. Workflow step 4

## Before you begin
{: #cd-kube-prereqs-cra}

* [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started).
* [Set up the {{site.data.keyword.cloud_notm}} Container Registry CLI and your registry namespace](/docs/services/Registry?topic=registry-registry_setup_cli_namespace). 
* [Understand the basics of Kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/){: external}.

## Create the toolchain
{: #cd-kube-create-toolchain}
{: step}

In this task, you create a Develop a Kubernetes app toolchain. 

1. To create your Develop a Kubernetes app toolchain, click

 [![Create toolchain](images/create_toolchain_button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain&env_id=ibm:yp:us-south&branch=dual-template&pipeline_type=tekton){: external}

 Alternatively, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. On the **Toolchains** page, click **Create a Toolchain**. On the **Create a Toolchain** page, select **Delivery Pipeline - Tekton**, and then click **Develop a Kubernetes app**.

   ![Develop a Kubernetes App](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Develop-Kubernetes-Template-CRA.png)

  * If you already have a Kubernetes cluster, go to <a href="https://cloud.ibm.com?cm_mmc=IBMBluemixGarageMethod-_-MethodSite-_-10-19-15::12-31-18-_-ibm-bluemix-website" target="_blank">cloud.ibm.com</a>. From the menu in the upper-left corner, click **Kubernetes**. Click **Clusters** and click your cluster. On the cluster dashboard, click the **DevOps** tab and click **Create a Toolchain**. From the **Filters** list on the left side of the page, select **Delivery Pipeline - Tekton**. Click the **Develop a Kubernetes App** tile. 

2. On the "Develop a Kubernetes app" creation page, click the **About** tab to review the diagram of the toolchain that you're about to create. The diagram shows each tool integration in its lifecycle phase in the toolchain.<br/><br/> 

  ![Simple container toolchain settings](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/kube-app-tc-cra-diagram.png)

3. Click the **Create** tab. Review the default information for the toolchain settings. The toolchain's name identifies it in IBM Cloud.

  ![Simple container toolchain region settings](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/kube-app-tc-cra-region.png)

   **Notes:** 
      * The URL to access your app must be unique. By default, the toolchain's name is used in constructing that URL. Make sure that the toolchain's name is unique within IBM Cloud.
      * By default, you create your source repository (repo) in IBM Cloud Continuous Delivery Git Repos and Issue Tracking. However, if you want to use a different Git repo provider, you can select one from the options in the **Select a source provider** drop-down list.
   
   Each toolchain is associated with a specific region and resource group. For this tutorial, select **Dallas** for the region. You can have up to 200 toolchains per resource group.

4. Review your Git Repo and Issue Tracking settings and, if needed, change them. Each toolchain comes with a sample app, but you can select another repo to use.

5. Click the **Delivery Pipeline** tool integration. If you want to modify the app name, you can. Add the IBM Cloud API key that you created in step 3 of the Prerequisites. To see your key, you can click and hold on the eye icon. Alternatively, next to the **IBM Cloud API Key** field, click **Create** and in the window that opens, click **Create**. If you want to, you can change the name for your new API Key.

   If the API key is valid, the container registry region and namespace cluster region, name, namespace, and resource group are automatically populated. You can change any of these fields to match your configuration if needed.

   **Important:** The namespace must be 4 - 30 characters and use only lowercase letters, numbers, or underscores.

   ![Configure the delivery pipeline](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/secure-kube-pipeline-config.png)

6. Click **Create**. After a few moments, your new toolchain's Overview page opens.

   ![Secure Kubernetes toolchain overview](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/secure-kube-overview.png)

## Create a Pull Request in Git
{: #cd-kube-create-pr}
{: step}

In this task, you modify the app and create a pull request to merge it into the main branch. You can see how your Tekton-based delivery pipeline automatically picks up the pull request on commit and uses Code Risk Analyzer to scan the app. 

1. On the toolchain's Overview page, right-click the **Git** tile for your app and open it in a new tab.

   **Tip:** You can also use the built-in Eclipse Orion-based Web IDE, a local IDE, or your favorite editor to change the files in your repo.

2. In the repo directory tree, open the `utils.js` file.

   ![Git file browser](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Git-File-Browser.png)

3. Edit the text message code to change the welcome message.
  
   ![Editing the text in Git](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Git-File-Edit.png)

4.	Type a commit message and change the target branch to **demo**. Make sure that the **Start a new merge request with these changes** checkbox is selected. Click **Commit changes**.

   ![Commit pull request](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/commit-pr.png)

5. On the subsequent confirmation page, click **Submit Merge Request**.

6. Return to the tab that shows your toolchain's Overview page.

## Run Code Risk Analyzer
{: #cd-kube-run-cra}
{: step}

In this task, you run the Code Risk Analyzer pipeline and review the results of your scan in Git.

1. Click the **pr-pipeline** tile.

      ![PR pipeline tile](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/PR-Pipeline-Tile.png)

2. With a Tekton-based delivery pipeline, you can automate the continuous building, testing, and deployment of your apps. 

   The pr-pipeline dashboard displays an empty table until at least one Tekton pipeline runs. After a Tekton pipeline runs, either manually or as the result of external Git events, the table lists the run, its status, and the last updated time of the run definition.

   Your submission of a merge request in the Git repo triggered pr-pipeline to run. The pipeline started to run and you can see the progress on the dashboard.

      ![Run pipeline](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/PR-Pipeline-Run.png)

   Pipeline runs can be in any of the following states:

   * Pending: The PipelineRun definition is queued and waiting to run.

   * Running: The PipelineRun definition is running in the cluster.

   * Succeeded: The PipelineRun definition was completed in the cluster.

   * Failed: The PipelineRun definition run failed. Review the log file for the run to determine the cause of failure.<br/>  

   For more information about the pr-pipeline run that you triggered, click the link in the Name column of the top row in the table. You can view the task definition and the steps in each PipelineRun definition. You can also view the status, logs, and details of each task definition and step and the overall status of the PipelineRun definition.
   
      ![Pipeline details](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/PR-Pipeline-Details.png)

   The pipeline definition is stored in the `pr-pipeline.yaml` file in the `.pipeline` folder of the secure-kube-pipeline GitHub repo that was added to your toolchain. This repo is where the template files are kept. Each task has a separate section of this file. 

3. As the pipeline is running, you can see each step as it is completed. The steps in pr-pipeline are as shown in this image:

      ![Pipeline execution](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/PR-Pipeline-Exec.png)

   * **cra-discovery-scan** is a discovery and setup task. It accesses various source artifacts from the repo and conducts deep discovery to identify all dependencies, including transitive dependencies. It parses the following assets:
   
    * Dockerfile: All build stages, base images in every stage, lists of packages from base images, and any add-on packages that are installed on top of base images
      
    * Package manifest files: `requirements.txt` (Python), `package-lock.json` (Node.js), and `pom.xml` (Java)
   
   * **code-vulnerability-scan** and **code-vulnerability-scan-status-finished** are code vulnerability scanning tasks. These tasks find vulnerabilities for all application package dependencies, container base images, and operating system packages.

   * **code-cis-scan-status-pending**, **cra-cis-check**, and **code-cis-scan-status-finished** are deployment configuration scanning tasks. They run configuration checks on Kubernetes deployment manifest files. Docker CIS provides prescriptive guidance to establish a secure configuration posture for the Docker container. Code Risk Analyzer takes these security configurations as a point of reference and identifies security controls that can be checked in the deployment artifacts (`xxx.yaml`) for Kubernetes applications. In addition, this task also provides a security risk for every control failure.
   
   * **code-bom-check-status-pending**, **cra-bom**, and **code-bom-check-status-finished** are tasks that generate the bill of materials (BOM). The BOM for a repo captures the pedigree of all the dependencies. It is collected at different granularities. For instance, it captures a list of base images that are used in the build, a list of packages from the base images, and a list of application packages that are installed over the base image. The BOM acts as ground truth for your analytic results and can potentially be used to enforce policy gates.

4. After the pipeline run is completed, click the **Git repo** tab to return to the merge request. You can see an inventory of the results of the Code Risk Analyzer scans.

      ![Scan overview](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Scan-Overview.png)
      
5. From the Git merge request, you can access the Bill of Materials report through the DevOps Insights dashboard. The merge request also shows any differences in the bill of materials from the previous run.

      ![BOM overview](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/BOM-Overview.png)
      
6. Click the **[JSON Format]** link in the Bill of Materials report to see the DevOps Insights entry. Every package, version, and source that was accessed by the configuration files is listed.
      
   ![BOM results](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/BOM-Results.png)

   The Vulnerability report shows the two files that were scanned: the Dockerfile and the `package-lock.json` file.<br/><br/> 

   ![Vulnerability overview](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Vuln-Overview.png)

   * The Dockerfile is scanned by using vulnerability data that is provided by Clair. <a href="https://github.com/quay/clair" target="_blank">Clair</a> is an open-source project for the static analysis of vulnerabilities in application containers. It currently includes OCI and Docker. The Clair API is used to index container images, which are then matched against known vulnerabilities.

   * The `package-lock.json` file is scanned by using <a href="https://snyk.io/" target="_blank">Snyk</a>. The Snyk Intel Vulnerability Database is integrated into IBM Cloud Continuous Delivery to enhance security for enterprise workloads. The Snyk security platform is powered by its industry-leading proprietary vulnerability database and maintained by the expert Snyk security research team.

   The deployment `.yaml` files are scanned for configuration risks and compared to industry best practices and community databases.

   ![Configuration overview](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Config-Overview.png)

## Merge Code and Deploy App
{: #cd-kube-step-desc}
{: step}

In the last task, you reviewed the results from Code Risk Analyzer in the merge request that you submitted into your Git repo. Now, you merge the change in Git and deploy the updated app to Kubernetes.

1. On the merge request page in Git, click **Merge**.

      ![Git merge](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Git-Merge.png)

2. Return to your toolchain home page. Click the **ci-pipeline** Delivery Pipeline tile.

      ![CI pipeline tile](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/CI-Pipeline-Tile.png)

3. On the pipeline dashboard, you can see that the pipeline run automatically started when the merge was submitted. Click the running pipeline and follow along as the tasks are completed.

      ![CI pipeline dashboard](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/CI-Pipeline-Dash.png)

4. Review the pipeline setup tasks. These tasks consists of a git clone of the repo followed by two steps:

    * **docker-lint**: This step checks for the mandatory Dockerfile and runs a lint tool. 
   
    * **unit-tests**: This step acts as a placeholder for running unit tests against the app. Tests should be added to the `run-tests.sh` script.
   
5. Review the tasks to build the container image:
 
    * **containerize**: This task runs the check-registry-and-build-image step. The pipeline checks the registry current plan and quota before it creates the image registry namespace if needed. It then creates the Docker image by using the <a href="https://www.ibm.com/cloud/container-registry" target="_blank">IBM Cloud Container Registry</a> build service through the `ibmcloud cr build` CLI script. The script stores the output image into the private IBM Cloud Container Registry and copies other app scripts with the build results into the `ARCHIVE_DIR` folder.
   
    * **vulnerability-advisor**: This task runs the run-vulnerability-advisor-scan step. This step runs <a href="https://cloud.ibm.com/docs/services/Registry?topic=va-va_index" target="_blank"> Vulnerability Advisor</a> on the image to check for known vulnerabilities. If it finds a vulnerability, the job fails, preventing the image from being deployed. This safety feature prevents apps with security holes from being deployed. The image has no vulnerabilities, so it passes. 
   
    * **publish-doi-va-scan-record**: This task runs the publish-restrecord step, which captures the result of the Vulnerability Analysis run into a JSON file and publishes it to the DevOps Insights dashboard.

6. Review the task to deploy the container image to your Kubernetes cluster. The **deploy-to-kubernetes** step checks whether the IBM Kubernetes cluster is ready and has a namespace that is configured with access to the private image registry by using an IBM Cloud API Key. It then configures the cluster namespace, updates the `deployment.yml` manifest file and grants access to the private image registry. It also sets environment variables and uses the deployment manifest file to deploy the app into the Kubernetes cluster.

7. After all the steps in the pipeline are completed, a green status is shown for each task. Click the **deploy-to-kubernetes** task, click the **execute** step, and click the **Logs** tab to see the successful completion of this step.

   ![Tekton success](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/CI-Tekton-Success.png)

8. Scroll to the end of the log. The `DEPLOYMENT SUCCEEDED` message is shown at the end of the log.

   ![Tekton deployment success](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Tekton-Deployment-Success.png)

9. Click the URL to see the running app.

   ![Running app](/cloud/architecture/images/tutorials/toolchains/develop-kubernetes-app-with-code-risk-analyzer/Tekton-Running-App.png)

## Next steps
{: #cd-kube-step-next-cra}

Want to start fresh? Remove the following resources that you created as a part of this tutorial:

* Delete the Git repository.
* Delete the toolchain.
* Delete the cluster.
