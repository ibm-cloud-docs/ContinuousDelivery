---

copyright:
  years: 2021
lastupdated: "2021-06-30"

keywords: DevSecOps, cli, IBM Cloud

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
{:deprecated: .deprecated}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# DevSecOps CLI 
{: #cd-devsecops-cli}

A CLI Interface to enable working with services adopting OnePipeline compliance solutions, for example the shift-left reference pipelines. For more information about the Shift-Left compliance architecture, see [DevSecOps with {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-devsecops_intro).
{: shortdesc}

## CLI interface
{: #devsecops-cli-interface}

The CLI uses a multipart structure on the command line that must be specified in this order:

```sh
$ cocoa <command> <subcommand> [options]
```
{: codeblock}

1. The base call to the CLI.

2. The main command, which typically corresponds to a service or a module used by the Shift-Left architecture, for example change request, inventory, tekton.

3. The subcommand that specifies which action to perform.

4. CLI options required by the action. As long as they follow the first three parts, You can specify these in any order.

Some commands use environment variables to get API Keys, or to configure an option value which was not provided in the command line. You need to export these variables before running the command.
{: important}

Command line options can take various types of input values, such as numbers, strings, boolean values, arrays, and JSON objects. The options type is dependent upon the command you specify. Use `cocoa <command> <subcommand> --help` to see the options types.
{: tip}

## CLI commands
{: #devsecops-cli-commands}

### cocoa check pull-request-approval
{: #pull-request-approval}

Checks the approval state of a Pull Request on a given commit hash. If the Pull Request was not approved, it creates a new incident issue in the specified repository. The command can identify emergency pull requests marked with a label. In this case, it will have an exit code of `0`.

Required environment variables:

```
GHE_TOKEN=            # Github Enterprise API Token
GHE_ORG=              # The owner of the repository
GHE_REPO=             # The repository name
INCIDENT_ISSUE_REPO=  # The incident issue repo name
EMERGENCY_LABEL=      # Emergency Label name
GIT_COMMIT=           # Commit hash of the Pull Request
```
{: screen}

Running the command:

```sh
$ cocoa check pull-request-approval
```
{: codeblock}

### cocoa check pull-request-status
{: #pull-request-status}

Checks a given Pull Request's status and the repositories settings.
 - **Branch Protection:** Rules to disable force pushing, prevent branches from being deleted, and optionally require status checks before merging.
 - **Commit Status Check:** External services to mark commits with an `error`, `failure`, `pending`, or `success` state, which is then reflected in pull requests involving those commits.
 - **Check Runs:** Apps that perform continuous integration, code linting, or code scanning services and provide detailed feedback on commits.

Required environment variables:

```
REQUIRED_CHECKS=        # Minimum required checks to be compliant set by client
GIT_BRANCH=             # Branch name for branch protection check
GIT_COMMIT=             # Commit hash of the Pull Request
GHE_TOKEN=              # Github Enterprise API Token
GHE_ORG=                # The owner of the repository
GHE_REPO=               # The repository name
```
{: screen}

`REQUIRED_CHECKS` example:

```json
  [
    {
      "type": "status",
      "name": "unit-test",
      "params": {
        "name": "travis/ci"
      }
    },
    {
      "type": "check-run",
      "name": "secret-detection",
      "params": {
        "name": "whitewater-detect-secrets"
      }
    },
    {
      "type": "branch-protection",
      "name": "code review",
      "params": {
        "checks": ["travis/ci", "whitewater-detect-secrets"]
      }
    },
    {
      "type": "check-run",
      "name": "open-source-license-scan",
      "params": {
        "name": "ossc/ci"
      }
    }
  ]
```
{: screen}

Running the command:

```sh
$ cocoa check pull-request-status
```
{: codeblock}

### cocoa changelog
{: #changelog}

Prints the changelog between two revisions in the given repository to stdout.

Options:

```
--org   # Defaults to GHE_ORG env variable, github organization
--repo  # Defaults to GHE_REPO env variable, name of the github repository
```
{: screen}

Required environment variables:

```sh
GHE_TOKEN=  # Github Enterprise API Token (Required)
GHE_ORG=    # The owner of the repository (optional, when --org is not provided)
GHE_REPO=   # The repository name (optional, when --repo is not provided)
```
{: screen}

This command has three usage methods:

* Check commits in range when both `--from` and `--to` options are provided.

Options:

```
--from  # git commit hash to calculate the changes from
--to    # git commit hash to calculate the changes to
```
{: screen}

Running the command:

```sh
$ cocoa changelog \
  --org=<github-organization> \
  --repo=<github-repo-name> \
  --from=<commit-hash-to-calculcate-changes-from> \
  --to=<commit-hash-to-calculate-changes-to>
```
{: codeblock}

* Contain all commits that belong to a specific pull request, when the `--pr` option is provided.

Options:

```
--pr # pull request number from which the changelog is calculated
```
{: screen}

Running the command:

```sh
$ cocoa changelog \
  --org=<github-organization> \
  --repo=<github-repo-name> \
  --pr=<pull-request-number>
```
{: codeblock}

* If none of the above is provided the changelog contains the changes of the latest merged PR.

Running the command:

```sh
$ cocoa changelog \
  --org=<github-organization> \
  --repo=<github-repo-name>
```
{: codeblock}

### cocoa change-request get
{: #change-request-get}

Queries a Change Request from the ServiceNow API and saves it to a file or prints it to the console.

Required environment variables:

```
SERVICENOW_TOKEN= # ServiceNow API Token
SERVICENOW_URL=   # ServiceNow API URL, default is https://watsontest.service-now.com/api/ibmwc/change
```
{: screen}

Options:

```
--change-request-id='CHGXXXXXX' # (Required) The Change Request ID to query from ServiceNow.
--output='filename.json'         # (Optional) If provided, the Change Request data will be written to this file.
```
{: screen}

Running the command:

```sh
# Read Change Request with number 'CHG123456' and output the JSON Data to the console.
$ cocoa change-request get --change-request-id='CHG123456'

# Read Change Request with number 'CHG123456' and output the JSON Data to the file named 'cr.json'.
$ cocoa change-request get --change-request-id='CHG123456' --output='cr.json'
```
{: codeblock}

### cocoa change-request create
{: #change-request-create}

Creates a change request and posts it to the ServiceNow API.

Two usage methods:

* Provide all required CR fields from CLI options.

Options:

```
--assigned-to      # A ServiceNow validated user (defaults to value found in the pull request)
--system           # the name of the system in ServiceNow
--impact           # impact explanation (defaults to value found in th pull request)
--outage-duration  # duration of the outage (format: 'd HH:mm:ss' or 'none')
--priority         # change priority, valid options: critical, high, moderate, low, planning (defaults to value found in the pull request)
--environment      # the environment for the deployment
--purpose          # purpose explanation (default to value found in the pull request)
--description      # description of the change
--backout-plan     # description of the backout plan (defaults to the value found in the PR)
--planned-start    # planned start time of the change (required format: YYYY-MM-DD HH:mm:ss, e.g 2020-05-13 13:00:12, in UTC)
--planned-end      # planned end time of the change (required format: YYYY-MM-DD HH:mm:ss, e.g 2020-05-13 13:00:12, in UTC)
--deployment-ready # readiness for deployment (choices: 'yes', 'no', default: 'yes')
--type             # change request type, option: standard, emergency
```
{: screen}

* Provide a file name to parse the CR data from. JSON format is expected.

Options:

```
--file --f         # json file name to parse the cr data from
```
{: screen}

Example file:

```json
{
  "type": "emergency",
  "assignedto": "alexandra.szanto@ibm.com",
  "backoutplan": "rollback",
  "priority": "critical",
  "purpose": "bugfix",
  "description": "test description",
  "environment": "crn:v1:bluemix:public::ch-ctu-2::::",
  "impact": "bug",
  "system": "devopsinsights",
  "outageduration": "0 00:00:00",
  "plannedstart": "2020-10-05 14:48:00",
  "plannedend": "2020-10-05 14:49:00",
  "deploymentready": "yes",
}
```
{: screen}

Required environment variables:

```
SERVICENOW_TOKEN=    # ServiceNow API Token
SERVICENOW_URL=      # ServiceNow API URL, default is https://watsontest.service-now.com/api/ibmwc/change
```
{: screen}

Running the command:

```sh
$ cocoa change-request create --file=test.json
```
{: codeblock}

or

```sh
$ cocoa change-request create \
  --assigned-to=<your-ibm-email> \
  --system=<servicenow-configuration-item> \
  --impact=<impact description> \
  --outage-duration='0 00:00:00' \
  --priority=<the-priority> \
  --environment=<involved-environment> \
  --purpose=<purpose-explanation> \
  --description=<description-of-the-change> \
  --backout-plan=<description-of-a-backout-plan> \
  --planned-start='2020-05-13 13:00:12' \
  --planned-end='2020-05-13 13:10:12' \
  --deployment-ready=<yes/no> \
  --type=<change-type> \
```
{: codeblock}

### cocoa change-request change-state-to-implement
{: #change-request-change-state-to-implement}

Changes the state of a Change Request to `implement` through the ServiceNow API.

Required environment variables:

```
SERVICENOW_TOKEN=   # ServiceNow API Token
SERVICENOW_URL=     # ServiceNow API URL, default is https://watsontest.service-now.com/api/ibmwc/change
CHANGE_REQUEST_ID=  # ID of the Change Request to change state to implement
```
{: screen}


Running the command:

```sh
$ cocoa change-request change-state-to-implement
```
{: codeblock}

### cocoa change-request close
{: #change-request-close}

Closes a given Change Request through the ServiceNow API. You can attach 'close notes' via the `--close-notes` option and specify the 'close category' using the `--close-category` option.

Options:

```
--close-category  # Choices: "successful" (default), "successful_issues", "unsuccessful", "cancel"
--close-notes     # String, defaults to "Deployment done."
```
{: screen}

Required environment variables:

```
SERVICENOW_TOKEN=   # ServiceNow API Token
SERVICENOW_URL=     # ServiceNow API URL, default is https://watsontest.service-now.com/api/ibmwc/change
CHANGE_REQUEST_ID=  # ID of the Change Request to be closed
```
{: screen}

Running the command:

```sh
$ cocoa change-request close
```
{: codeblock}

### cocoa change-request check-approval
{: #change-request-check-approval}

Queries the approval status of a given change request. If the Change Request is an emergency, the command will not fail but will prompt for a retroactive approval.

Required environment variables:

```
SERVICENOW_TOKEN=   # ServiceNow API Token
SERVICENOW_URL=     # ServiceNow API URL, default is https://watsontest.service-now.com/api/ibmwc/change
CHANGE_REQUEST_ID=  # ID of the Change Request to be checked
```
{: screen}

Running the command:

```sh
$ cocoa change-request check-approval
```
{: codeblock}

### cocoa change-request prepare
{: #change-request-prepare}

Creates the change request data and prints it to the console or a given file.

Required environment variables:

```
GHE_TOKEN=              # Github Enterprise API Token (only required when parsing from pr)
GHE_ORG=                # The owner of the repository (optional, when --org is not provided)
GHE_REPO=               # The repository name (optional, when --repo is not provided)
EMERGENCY_LABEL=        # Emergency Label (optional, when --emergency-label is not provided)
```
{: screen}

The following fields can be parsed from the pull request body:

```
--assigned-to
--impact
--priority
--purpose
--backout-plan
--type
```
{: screen}

In case they are specifically provided by using the CLI option, the CLI option overrides the value found in the pull request. If all of them are provided, pr is not parsed at all, `--org`, `--repo` and `GHE_TOKEN` is not necessary.

Options:

```
--org              # github organization where the parsed pr is (only needed if fields are parsed from pr, defaults to GHE_ORG)
--repo             # github repository name whre the parsed pr is (only needed if fields are parsed from pr, defaults to GHE_REPO)
--pr               # the pull request number to parse (mutually exclusive with sha and branch)
--sha              # infer the pr number from hash (mutually exclusive with pr and branch)
--branch           # infer PR based on the last merged pr into this branch (defaults to master)
--assigned-to      # A ServiceNow validated user (defaults to value found in the pull request)
--system           # the name of the system in ServiceNow
--impact           # implact explanation (defaults to value found in th pull request)
--outage-duration  # duration of the outage
--planned-start    # planned start time of the change (required format: YYYY-MM-DD HH:mm:ss, e.g 2020-05-13 13:00:12, in UTC)
--planned-end      # planned end time of the change (required format: YYYY-MM-DD HH:mm:ss, e.g 2020-05-13 13:00:12, in UTC)
--priority         # change priority, valid options: critical, high, moderate, low, planning (defaults to value found in the pull request)
--environment      # the environment for the deployment
--purpose          # purpose explanation (default to value found in the pull request)
--backout-plan     # description of the backout plan (defaults to the value found in the PR)
--deployment-ready # description of the change
--type             # change request type, option: standard, emergency
--emergency-label  # emergency label to look for in the pull request
--file             # file name to print the cr data to (optional, prints to stdout by default)
```
{: screen}

Running the command:

```sh
$ cocoa cr prepare \
  --org=<github-organization> \
  --repo=<github-repo-name> \
  --pr=<pr number>
```
{: codeblock}

### cocoa change-request request-approval
{: #change-request-request-approval}

Requests approval for records in the new state with approval not requested. When executed the record follows the manual approval path.

Required environment variables:

```
SERVICENOW_TOKEN=    # ServiceNow API Token
SERVICENOW_URL=      # ServiceNow API URL, default is https://watsontest.service-now.com/api/ibmwc/change
```
{: screen}

Options:

```
--crid="<ID>"
# or
--change-request-id="<ID>"
```
{: screen}

Running the command:

```sh
$ cocoa change-request request-approval --crid="<insert-change-request-id-here>"
```
{: codeblock}

### cocoa change-request task add
{: #change-request-task-add}

Adds a Change Task to a specific Change Request.

Required environment variables:

```
SERVICENOW_TOKEN=    # ServiceNow API Token
SERVICENOW_URL=      # ServiceNow API URL
```
{: screen}

Options:

```
--description  A more detailed description for the Change Task.                         [string]
--name         Name of the Change Task.                                                 [string] [required]
--data         Data for the Change Task or a path prefixed with @ to read the data from. [string] [default: "@/dev/stdin"]
```
{: screen}

Running the command:

```sh
$ cocoa change-request task add "CHGXXXXXXX" \
        --name='<task-name>' \
        --data='<data-for-the-task>'

$ cat data.txt | cocoa change-request task add "CHGXXXXXXX" --name='<task-name>'

$ cocoa change-request task add "CHGXXXXXXX" \
        --name='<task-name>' \
        --data='@<path/to/file>'
```
{: codeblock}

### cocoa change-request task get
{: #change-request-task-get}

Gets a specific Change Task of a given Change Request.

Required environment variables:

```
SERVICENOW_TOKEN=    # ServiceNow API Token
SERVICENOW_URL=      # ServiceNow API URL
```
{: screen}

Running the command:

```sh
$ cocoa change-request task get "CHGXXXXXXX" "CTASKXXXXXXX"
```
{: codeblock}

### cocoa change-request task list
{: change-request-task-list}

Lists Change Tasks for a given Change Request.

Required environment variables:

```
SERVICENOW_TOKEN=    # ServiceNow API Token
SERVICENOW_URL=      # ServiceNow API URL
```
{: screen}

Running the command:

```sh
$ cocoa change-request task list "<insert-change-request-id-here>"
```
{: codeblock}

### cocoa change-request task update
{: #change-request-task-update}

Updates a Change Task in a specific Change Request.

Required environment variables:

```
SERVICENOW_TOKEN=    # ServiceNow API Token
SERVICENOW_URL=      # ServiceNow API URL
```
{: screen}

Options:

```
--change-request-id  The change request the change task belongs to                            [string] [required]
--change-task-id     The change task id to be updated                                         [string] [required]
--description        A more detailed description for the Change Task.                         [string]
--data               Data for the Change Task or a path prefixed with @ to read the data from. [string]
```
{: screen}

Running the command:

```sh
$ cocoa change-request task update
        --change-request-id='CHGXXXXXXX' \
        --change-task-id='CTASKXXXXXXX' \
        --data='<data-for-the-task>' \
        --description='<description>'

$ cat data.txt | cocoa change-request task update --change-request-id='CHGXXXXXXX' --change-task-id='CTASKXXXXXXX' --data='@/dev/stdin'

$ cocoa change-request task update --change-request-id='CHGXXXXXXX' --change-task-id='CTASKXXXXXXX' --data='@<path/to/file>'
```
{: codeblock}

### cocoa evidence create
{: #evidence-create}

Creates an evidence from the specified options and saves it to a file / prints it to the console.

Running the command:

```sh
$ cocoa evidence create \
  --namespace=[choices: "ci", "cd"] \               # Pipeline type the evidence was collected from
  --evidence-name=<evidence-name> \                 # It will be used to name evidence-file in git
  --evidence-type=<evidence-type> \                 # e.g: com.ibm.unit_test
  --evidence-type-version=<evidence-type-version> \
  --result=[choices: "failure", "success"] \        # The result of the scan/test
  --issue=<issue-url> \                             # e.g: --issue=foo --issue=bar || --issue=foo
  --artifact=<artifact_url> <artifact_hash>\        # Url and hash pair(s) to the test artifact(s)
  --log=<log_url> <log_hash> \                      # Url and hash pair(s) to the log(s)
  --pipeline-id=<pipeline-id> \
  --pipeline-run-id=<pipeline-run-id> \
  --pipeline-run-url=<pipeline-run-url> \
  --toolchain-crn=<toolchain-crn> \                 # Name of the toolchain cloud resource
  --output=<filename>                                # If present, the evidence will be saved to the given file.
```
{: codeblock}

CLI options can be also set from environment variables with the exception of `issue`, `log` and `artifact`.
Multiple issues/artifacts should be provided with multiple issue/artifact flags. For example:

```sh
$ cocoa evidence create --artifact <url> <hash>  --artifact <url> <hash> --issue <issue-url> --issue <issue-url>
```
{: codeblock}

`artifact` consists of an url pointing to the artifact file and a hash, they should be provided the same way as in the previous example.
{: note}

### cocoa evidence format-summary
{: #evidence-format-summary}

Formats the evidence summary into a human readable format. It can be fed into the change request content.

Running the command:

```sh
$ cocoa evidence format-summary \
  --input=<filepath> \          # (default: -, referring to stdin) If present, the formatted evidence will be read from the given file.
  --output=<filepath>           # (default: -, referring to stdout) If present, the formatted evidence will be saved to the given file.
```
{: codeblock}

```sh
# Reading from stdin and printing to stdout:
$ cat raw-summary.json | cocoa evidence format-summary -i - -o - | tee formatted-summary.txt
$ cat raw-summary.json | cocoa evidence format-summary | tee formatted-summary.txt
# Reading to and from file:
$ cocoa evidence format-summary --input=raw-summary.json --output=formatted-summary.txt
```
{: codeblock}

### cocoa evidence upload
{: #evidence-upload}

Uploads an evidence to the specified backends. Backends can be different evidence locker types, for example {{site.data.keyword.cos_short}}, GitHub or {{site.data.keyword.DRA_short}}. Different lockers require different parameters to be provided.

{{site.data.keyword.DRA_short}} is not yet supported.
{: note}

Required Options:

```
--backend
```
{: screen}

Required environment variables:

```
GHE_TOKEN=          # Github token (Required if using 'git' backend)
EVIDENCE_REPO_ORG=  # Evidence repo org (Required if using 'git' backend)
EVIDENCE_REPO_NAME= # Evidence repo name (Required if using 'git' backend)
COS_API_KEY=        # Cloud Object Storage API Key (Required if using 'cos' backend)
COS_BUCKET_NAME=    # Bucket Name where the evidence will be uploaded in the COS Instance (Required if using 'cos' backend)
COS_ENDPOINT=       # The COS API Endpoint matching the region where the bucket is located (Required if using 'cos' backend)
```
{: screen}

Running the command:

```sh
$ cocoa evidence upload

$ cocoa evidence upload \
  --backend=[choices: "git", "insights", "cos"] \   # e.g. --backend=cos,git,insights
  --namespace=[choices: "ci", "cd"] \               # Pipeline type the evidence was collected from
  --evidence-name=<evidence-name> \                 # It will be used to name evidence-file in git
  --evidence-type=<evidence-type> \                 # e.g: com.ibm.unit_test
  --evidence-type-version=<evidence-type-version> \
  --result=[choices: "failure", "success"] \        # The result of the scan/test
  --issue=<issue-url> \                             # e.g: --issue=foo --issue=bar || --issue=foo
  --artifact=<artifact_url> <artifact_hash>\        # Url and hash pair(s) to the test artifact(s)
  --log=<log_url> <log_hash> \                      # Url and hash pair(s) to the log(s)
  --pipeline-id=<pipeline-id> \
  --pipeline-run-id=<pipeline-run-id> \
  --pipeline-run-url=<pipeline-run-url> \
  --toolchain-crn=<toolchain-crn>                   # Name of the toolchain cloud resource
```
{: codeblock}

CLI options can be also set from environment variables with the exception of `backend`, `issue`, `log` and `artifact`. Multiple issues/artifacts should be provided with multiple issue/artifact flags. For example:

```sh
$ cocoa evidence upload --backend=git --artifact <url> <hash>  --artifact <url> <hash> --issue <issue-url> --issue <issue-url>
```
{: codeblock}

`artifact` consists of an url pointing to the artifact file and a hash, they should be provided the same way as in the previous example.
{: note}

### cocoa evidence summarize
{: evidence-summaries}

Queries evidences from the Evidence Locker and generates an Evidence Summary from their contents. Backends can be different evidence locker types, for example {{site.data.keyword.cos_short}} or GitHub. Currently `git` and `cos` is supported as backend. Different lockers require different parameters to be provided.

Required environment variables for git:

```
GHE_TOKEN=          # (Required if using 'git' backend) Github token
EVIDENCE_REPO_ORG=  # (Required if using 'git' backend) Use this environment varibale to provide the owner organisation of the evidence repository
EVIDENCE_REPO_NAME= # (Required if using 'git' backend) Use this environment varibale to provide the name of the evidence repository
PIPELINE_RUN_ID=    # Can be used instead of '--pipeline-run-id' option
TOOLCHAIN_CRN=      # Can be used instead of '--toolchain-crn' option
```
{: screen}

Options for git:

```
--backend           # (Required) Specifies the type of locker from where the evidences are queried
--repo              # Evidence Repositories name (can be substituted by EVIDENCE_REPO_NAME environment variable)
--org               # Evidence Repositories owner organisation (can be substituted by EVIDENCE_REPO_ORG environment variable)
--pipeline-run-id   # (Required)
--toolchain-crn     # (Required)
--prefix-list       # (Required) a list of paths separated by comma where evidences can be found in the repository
--output            # (Optional) file name to write the evidence summary into
```
{: screen}

Required environment variables for cos:

```
COS_API_KEY=      # COS api token
COS_BUCKET_NAME=  # COS bucket name where evidences are stored
COS_ENDPOINT=     # COS endpoint where the bucket is available
PIPELINE_RUN_ID=  # Can be used instead of '--pipeline-run-id' option
TOOLCHAIN_CRN=    # Can be used instead of '--toolchain-crn' option
```
{: screen}

Options for cos:

```
--backend         # (Required) Specifies the type of locker from where the evidences are queried
--pipeline-run-id # (Required)
--toolchain-crn   # (Required)
--prefix-list     # (Required) a list of paths separated by comma where evidences can be found in the repository
--output          # (Optional) file name to write the evidence summary into
```
{: screen}

Running the command:

```sh
# Save the evidence summary to 'summary.json' file.
$ cocoa evidence summarize \
  --backend='git' \
  --pipeline-run-id='id-123-123' \
  --toolchain-crn='crn-123-123' \
  --prefix-list='raw/ci/pipeline-run-id-1,raw/ci/pipeline-run-id-2' \
  --output='summary.json'

# Print the evidence summary to the console
$ cocoa evidence summarize \
  --backend='git' \
  --pipeline-run-id='id-123-123' \
  --toolchain-crn='crn-123-123' \
  --prefix-list='raw/ci/pipeline-run-id-1,raw/ci/pipeline-run-id-2'
```
{: codeblock}

### cocoa artifact upload
{: #artifact-upload}

Uploads an artifact to the specified backends. Backends can be different evidence locker types, for example {{site.data.keyword.cos_short}}, GitHub or {{site.data.keyword.DRA_short}}. Different lockers require different parameters to be provided.

Options:

```
--backend           # (Required) Specifies the types of lockers we upload the artifact ('cos', 'git')
--pipeline-run-id   # The ID of the PipelineRun running the CLI command
--namespace         # Specifies the pipeline the evidence is collected from
--upload-path       # If present, it will override the artifact name with the specified value
```
{: screen}

Required environment variables:

```
GHE_TOKEN=          # Github token (Required if using 'git' backend)
EVIDENCE_REPO_ORG=  # The Git repo org (Required if using 'git' backend)
EVIDENCE_REPO_NAME= # The Git repo name (Required if using 'git' backend)
COS_API_KEY=        # Cloud Object Storage API Key (Required if using 'cos' backend)
COS_BUCKET_NAME=    # Bucket Name where the artifact will be uploaded in the COS Instance (Required if using 'cos' backend)
COS_ENDPOINT=       # The COS API Endpoint matching the region where the bucket is located (Required if using 'cos' backend)
PIPELINE_RUN_ID=    # Can be used instead of '--pipeline-run-id' option
NAMESPACE=          # Can be used instead of '--namespace' option
```
{: screen}

Running the command:

```sh
$ cocoa artifact upload

$ cocoa artifact upload \
  --backend=[choices: "git", "cos"] \ # e.g. --backend=cos,git
  --pipeline-run-id=<pipeline-run-id> # can be substituted by PIPELINE_RUN_ID
  --namespace=[choices: "ci", "cd"] \ # Pipeline type the evidence was collected from, can be substituted by NAMESPACE
  <file-path>
```
{: codeblock}

CLI options can be also set from environment variables with the exception of `backend` and `upload-path`.

### cocoa set-status
{: #set-status}

Sets a given commit's status. The current implemetation is tested on GitHub. See documentation about [Github statuses](https://docs.github.com/en/rest/reference/repos#statuses){: external}.

Required environment variables:

```
GHE_TOKEN=    # Github token
GHE_ORG=      # Github organization/username
GHE_REPO=     # Github repository
GHE_COMMIT=   # Github commit hash
```
{: screen}

Running the command:

```sh
$ cocoa set-status \
 --state="pending" \
 --targetURL="https://cloud.ibm.com/devops/pipelines/tekton/some-toolchain/runs/some-pipelinerun/lint/lint?env_id=ibm:yp:us-south" \
 --context="tekton/lint" \
 --description="Tekton linter is running."
```
{: codeblock}

### cocoa inventory add
{: #inventory-add}

Adds a new value to the inventory repository. Creates a new file with the `name` option, if it does not exist otherwise overwrites it.
Currently the `type` `sha256` `provenance` and `signature` fields are optional parameters, but after the upcoming breaking changes they will be mandatory.

Required environment variables:

```
GHE_TOKEN=   # Github Token (required).
GHE_ORG=     # Github Organization (required if --org option is not specified).
GHE_REPO=    # Github Repository (required if --repo option is not specified).
```
{: screen}

Running the command:

```sh
$ cocoa inventory add \
  --artifact=cocoa-script-cli \
  --version=v4 \
  --repository-url=http://validURL.com \
  --pipeline-run-id=123123valid \
  --commit-sha=8e86dc4647ce28632103dce46b756c70d339349a \
  --build-number=33 \
  --name=cocoa-cli \
  --app-artifacts='{"app": "test", "some_value": "value"}' \
  --type=type \
  --sha256=786800e8e48938664fe2397ca14ab8dabd48f34656ef5cfda4143b4519cb714f \
  --provenance=us.icr.io/namespace/hello-compliance-app@sha256:786800e8e48938664fe2397ca14ab8dabd48f34656ef5cfda4143b4519cb714f \
  --signature=123123valid
```
{: codeblock}

### cocoa inventory get
{: #inventory-get}

Gets an entry from the inventory repository. The target can be a specific version or an environment. Either use `--version` or `--environment`, and use only one of them. If the `--property` option is missing, the whole content of the inventory entry is printed.

Required environment variables:

```
GHE_TOKEN= # Github token
```
{: screen}

Running the command:

```sh
# Uses the environment as target, and pretty-prints only a given property of the inventory entry to the console.
$ cocoa inventory get \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --entry='hello-compliance-app' \
  --environment='master' \
  --property='name'

# Uses the version as target, and pretty-prints the whole content of the inventory entry to the console.
$ cocoa inventory get \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --entry='hello-compliance-app' \
  --version='v1'
```
{: codeblock}

### cocoa inventory get-sha
{: #get-sha}

Gets the latest commit hash by a given label or environment from the inventory repository. Either use `--label` or `--environment`, and use only one of them.

Required environment variables:

```
GHE_TOKEN= # Github token
```
{: screen}

Running the command:

```sh
# Get the latest commit hash of the staging branch
$ cocoa inventory get-sha \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --environment='staging'

# Get the commit hash of the "pipeline-run-id" label
$ cocoa inventory get-sha \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --label='pipeline-run-id'
```
{: codeblock}

### cocoa inventory label
{: #inventory-label}

Adds a label to an inventory entry, or moves a label in the inventory. The target can be the latest commit on a specific branch or another label.

Options:

```
--org          # The Github organisation which owns the inventory repository.
--repo         # The name of the inventory repository.
--environment  # The inventory branch
--to-label     # Another label in the inventory, that will be looked up/removed
```
{: screen}

Required environment variables:

```
GHE_TOKEN=   # Github token
GHE_ORG=     # Github Organization (required if --org option is not specified).
GHE_REPO=    # Github Repository (required if --repo option is not specified).
```
{: screen}

Running the command:

```sh
# label the latest state on "staging" branch
$ cocoa inventory label add \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --environment='staging' \
  "new-label-to-add"
```
{: codeblock}

```sh
# attach a label to another label (to the same commit)
$ cocoa inventory label add \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --to-label="some-label" \
  "new-label-to-add"
```
{: codeblock}

```sh
# move or create the `latest-staging` label to another label (to the same commit)
$ cocoa inventory label move \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --to-label="some-label" \
  "label-to-move"
```
{: codeblock}

### cocoa inventory promote
{: #inventory-promote}

Promotes entries from the inventory from one environment to another. The source environment can be either a branch or a tag.

Required environment variables:

```
GHE_TOKEN=        # Github token
GHE_ORG=          # Github Organization (required if --org option is not specified).
GHE_REPO=         # Github Repository (required if --repo option is not specified).
PIPELINE_RUN_ID=  # Can be used instead of --pipeline-run-id (either the option or the variable is required).
```
{: screen}

Running the command:

```
$ cocoa inventory promote \
  --org='Github-ID' \
  --repo='compliance-inventory-repo' \
  --source='master' \
  --target='prod' \
  --priority='Critical' \
  --assigned-to='employee@ibm.com' \
  --description='desc' \
  --purpose='purpose' \
  --impact='impact' \
  --backout-plan='rollback'
```
{: codeblock}

### cocoa incident add
{: #incident-add}

Creates or updates an incident issue for a failing task in a pipeline run based on the commit-hash.

Options:

```
--task              # (Required) The name of the failing task
--commit-hash       # (Required) The commit hash which triggered the pipeline run
--pipeline-run-url  # The pipeline run url where the task ran
--org               # The incident issue repo org
--repo              # The incident issue repo name
--app-repo-url      # The app repo URL
--label             # Label(s) to add to the incident issue (optional) e.g: --label=foo --label=bar
```
{: screen}

Environment variables:

```
GHE_TOKEN=                  # (Required) Github Enterprise API Token
GHE_ORG=                    # Can be used instead of --org (either the option or the variable is required)
GHE_REPO=                   # Can be used instead of --repo (either the option or the variable is required)
PIPELINE_RUN_URL=           # Can be used instead of --pipeline-run-url (either the option or the variable is required)
APP_REPO_URL=               # Can be used instead of --app-repo-url (either the option or the variable is required)
```
{: screen}

Running the command:

```sh
$ cocoa incident add --task=<failing-task-name> --commit-hash=<abc123>
```
{: codeblock}

### cocoa tekton get-pipeline-logs
{: #tekton-get-pipeline-logs}

Creates log files for every step from a pipeline run and saves it to a directory. Use either the environment variables (`PIPELINE_ID`, `PIPELINE_RUN_ID`) or override the environment variables with explicit flags (`--pipeline-id`, `--pipeline-run-id`).

Options:

```
-o --output-dir       # (Required) Specifies the directory where the logs will be saved
   --pipeline-id      # ID of the pipeline
   --pipeline-run-id  # ID of the pipeline run
-u --use-task-ref     # (Optional) Can be used to override the default name of the pipeline task to the taskRef, when creating the directory
```
{: screen}

Required environment variables:

```
IBMCLOUD_API_KEY= # IBM Cloud API Token
TOOLCHAIN_REGION= # Region of the toolchain
PIPELINE_ID=      # Can be used instead of '--pipeline-id option
PIPELINE_RUN_ID=  # Can be used instead of '--pipeline-run-id option
```
{: screen}

Running the command:

```sh
$ cocoa tekton get-pipeline-logs \
  --output-dir=<output-dir> \
  --pipeline-id=<pipeline-id> \
  --pipeline-run-id=<pipeline-run-id> \
  --use-task-ref
```
{: codeblock}


