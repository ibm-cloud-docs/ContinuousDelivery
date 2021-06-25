---

copyright:
  years: 2021
lastupdated: "2021-06-24"

keywords: DevSecOps, inventory model, inventory

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

# Inventory
{: #cd-devsecops-inventory}

Learn about the inventory model, role, and purpose.
{: shortdesc}

## Inventory structure and content
{: #inventory-structure}

Our Inventory model tracks the following:

* What artifact is deployed to which environment or region
* Where was an artifact built (pipeline run, commit sha)
* What is the signature of the built artifact

Based on this data, we can keep track of evidence related during artifact builds and deployments and help Change Management and Compliance audits.

### Branches
{: #inventory-brances}

The Inventory is implemented in a Git repo. Git itself helps to keep track of and help the audit of changes.

Branches are used as Environments. The main branch (`master`) is written and updated by the CI pipeline. Other environments are updated from the master by using promotions. For more information, see the [Promotion](#inventory-promotion) section.

### Content
{: #inventory-content}

The Inventory contains an Inventory Entry for every artifact that participates in deployment. One Inventory Entry points to a single artifact. Inventory entries are JSON files, which you can see in the following example. The file name is the entry name, and it can be structured in folders.

Inventory folders are part of the entry name.
{: important}

#### Example
{: #inventory-content-example}

Take the following entry names for a service:

* auth/service
* auth/db
* ui/service
* main_service
* helm-charts/main_service

This is implemented in the following structure in the inventory:

```
/
├── auth
│   ├── service
│   └── db
├── ui
│   └── service
├── helm-charts
│   └── main_service
└ main_service
```
{: screen}


## Inventory entry format
{: #inventory-entry-format}

The `Entry` type represents the schema of the Inventory Entry (using typescript syntax, but it's fairly easy to convert it to JSON schema, for example):

```
interface Entry {
  repository_url: string;
  artifact: string;
  build_number: number;
  commit_sha: string;
  name: string;
  pipeline_run_id: string;
  version: string;

  app_artifacts: {
    signature: string;
    provenance: string;

    [key: string]: any;
  }

  type: string;
  sha256: string;
  provenance: string;
  signature: string;
}
```
{: codeblock}

### Example
{: #entry-format-example}

```
{
  "repository_url": "https://github.ibm.com/cocoa-test/compliance-app-20201211-sanity",
  "artifact": "us.icr.io/attila/hello-compliance-app:20201217081811-master-b85e3d472e9cc35b429c39e8c3f9eb282738c20a@sha256:da36831d5154307ac9ca4b8d900df2da0c6c14754977c32479dc62994b5722d0",
  "build_number": 21,
  "commit_sha": "b85e3d472e9cc35b429c39e8c3f9eb282738c20a",
  "name": "hello-compliance-app",
  "pipeline_run_id": "f21321bf-9054-4bf3-80a8-4fb34743b7d9",
  "version": "v1",
  "app_artifacts": {
    "signature": "owFNUX1IE3EY3vwAEy0VyoSJdkVWtu0+d3eTjNIIi0jETCSU3353cz+83V23myi2BlFgYiUFqSmZLciUzCJkRYJp9IEWFWXB0hAyrBQxEjIIuhFSf70vL8/7vM/zPi3JsaYEc+TnbqG8qrnTPDZ8w2WqiqwtacCghnQEgYQ5GzAkiLKO9PpoLyiwRtSsmugWNVGGIubE/D4bgpoNKXag60gCdo8oSYoVKl5VQsDAWIGqOkmcxAmSYHGO4AjC6gU+3eBxcYxICTRLijyEFOOiSR5SvMhBys2LLpIjWYqDJA6wwHYMeUG1+J8GL5CRW/TpVgFVG8VQ4vMAknE4BUA5OIoQGIKhKZwFkIeAdnECj+OCmxQADh2QoFmG5lkWUiTN8gJ0kDxPuxiWJAU8ekyvV6PegK54EcyGiqwDJItatg9Vy0D3a2IUpKg6UuS/T4KaaIC1fzuMDbfhmMGEvIY64FUxJ+Ew3PMU5SADgdNmKs5kTjBlrtsQ99iyY49nns8o6jsXWgkjPiYahClxVcrK5Flngumz2j7YdmD0ecutytsvxxNPHflKlRV2RyqD69NjC6Smji9XuukFyZ+lvM18gUr7F4NXge9YyZPik411tc1n9bKO/hDz7oGaX/ur94OnNHiwOG6n5ZsrsCsvtyvmkH4zOWlrRWuL7fzgj9zlcCTAhtu2LbeGLNfv3Ju0Jc9PZPk7Pm3Ov2CW+2xj8ReX6ooGamZ610yqRM/+8Qo2XnOeyZzbVKgs+f2+9unpJOve4Tmla+PdqftDWkHPm9Vq3nsyZ2DUkmP/nTb7qNw5l2SfWtiSemJx9nLaYOpx6amlOT18aeIwJQhHg1XOjJF9r18NXQvPuL9rH5tSQqbGhyN/AA==",
    "provenance": "us.icr.io/attila/hello-compliance-app:20201217081811-master-b85e3d472e9cc35b429c39e8c3f9eb282738c20a@sha256:da36831d5154307ac9ca4b8d900df2da0c6c14754977c32479dc62994b5722d0"
  },
  "type": "type",
  "sha256": "da36831d5154307ac9ca4b8d900df2da0c6c14754977c32479dc62994b5722d0",
  "provenance": "us.icr.io/attila/hello-compliance-app:20201217081811-master-b85e3d472e9cc35b429c39e8c3f9eb282738c20a@sha256:da36831d5154307ac9ca4b8d900df2da0c6c14754977c32479dc62994b5722d0",
  "signature": "signature"
}
```
{: codeblock}

## Inventory workflow
{: #inventory-workflow}

Inventory contains several branches other than `master`. These can represent deployment stages, environments or regions, or a mixture. This depends on the setup and usage.

### CI writes to inventory 
{: #ci-writes-to-inventory}

The `master` branch is populated from CI builds. The last commit in the target (in this case named `staging`) has a tag that is attached showing that was the last concluded deployment.

![CI writes to inventory](images/inventory-1.svg "Flow diagram that shows how the master branch is populated")

### Promotion
{: #inventory-promotion}

Promoting to a target branch happens by creating a PR. PR contents fill the Change Request fields. When it is reviewed, the Promotion PR can be merged.

![Promoting a target branch by using a PR](images/inventory-2.svg "Flow diagram that shows how a promotion is done by using a PR")

### Delta and deployment
{: #inventory-delta-deployment}

After the Promotion PR is merged, the Deployment pipeline can start. Deployment delta is the difference between the contents of the last concluded deployment and the current deployment. Deployment delta lists the inventory items that are being deployed.

![Deployment pipeline flow showing deployment delta details](images/inventory-3.svg "Deployment pipeline flow showing deployment delta details")

### Conclude
{: #inventory-conclude}

When the deployment finishes, we move the latest tag ahead.

![Deployment completes](images/inventory-4.svg "Deployment completes")

### Promote to further environments
{: #promote-further-envs}

Promotion and deployment can happen from any branch to another one.

![Promotion using a PR from staging to prod branch](images/inventory-5.svg "Promotion using a PR from staging to prod branch")

### Inventory landscape
{: #inventory-landscape}

The latest deployed state holds the content that is supposed to be deployed to an environment. Every promoted commit in the target branches has the relevant Pipeline Run ID and Change Request ID as a tag. Some commits can have multiple tags. Imagine a scenario of retrying a failed deployment, or doing a redeployment. The Inventory holds every piece of information to replay the deployments.

![Deployment flow diagram with tags](images/inventory-6.svg "Deployment flow diagram with tags")

#### Use of tags
{: #inventory-tags}

* `latest` tags the latest, successfully deployed, and concluded state of the inventory on a branch.

* `pipeline run id` tags the most recent inventory state in the branch, with the pipeline run id or build number of the actual deployment. It can be used to refer to the actual inventory point hash in the branch history, so when parallel deployments are triggered, we can avoid inventory content overlapping.

* `change request id [optional]` when we have a CR ID we can tag the current state, no practical reason, maybe to keep track the CR IDs in inventory in a historical representation

### Single target - multiple region setup
{: #single-target-multi-region}

This is an iteration on this model where we introduce multiple latest tags for a single target environment, so multiple CD pipelines can work on the same target for different kind of use cases.

For example, take the prod target environment and inventory branch. The same target environment can be used for multiple regions, like us-south and eu-de.

Teams should not need to set up a different branch for each region, and run the promotion redundantly, like having a branch prod-us-south and prod-eu-de. We can help them if they are able to specify these additional targets for the same inventory branch, and use them as Git tags.

In this setup, the prod branch would have multiple latest tags on the same branch, like `prod-latest:us-south` and `prod-latest:eu-de`, and each CD pipeline that is responsible for each region can use those to deploy.

![Prod branch with multiple latest tags per region](images/inventory-7.svg "Prod branch with multiple latest tags per region")

As an example scenario, a set of changes that is eventually to be deployed everywhere, might be released to a single region first, then gradually deploying it to other regions, by using CD pipelines targeting those regions.

## Inventory operations
{: #inventory-operations}

Some basic operations on the inventory, which executed with the CLI or using pure Git and GitHub CLI.

### CLI commands
{#inventory-cocoa-cli}

1. Create a Promotion PR from master to target branch staging. 

```
cocoa inventory promote \
  --source="master" \
  --target="staging" \
  --priority="moderate" \
  --assigned-to="cocoa@hu.ibm.com" \
  --description="Change description" \
  --purpose="Change purpose" \
  --impact="Change impact" \
  --backout-plan="Details on backout and rollback")
```
{: codeblock}

2. Conclude a deployment - moving target_latest tag to the same commit as pipeline-run-id tag as a conclusion of deployment.

```
cocoa inventory label move \
  --to-label="${PIPELINE_RUN_ID}" \
  "target_latest"
```
{: codeblock}

### Git and GitHub CLI
{: #inventory-git-gh-cli}

1. Create a Promotion PR from master to target branch.

```
promote() {

  if [ -z $1 ] || [ -z $2 ]; then
    echo "Missing source and target"
    exit 1
  fi

  local source="$1"
  local target="$2"

  if ! git show-ref "refs/remotes/origin/$target"; then
    # Create a new target branch, from the beginning of master
    git checkout master
    git checkout -b "$target" $(git rev-list --max-parents=0 HEAD)
    git_push
  fi

  git checkout "$source"
  git pull --rebase

  # Create a promotion branch for the PR
  # this can be discarded after the Promotion PR merge
  git checkout -b "promote-$source-to-$target"
  git push --set-upstream origin "promote-$source-to-$target"

  # Create PR from promotion branch to target branch
  gh pr create \
    --base "$target" \
    --head "promote-$source-to-$target" \
    --title "Promote $source to $target" \
    --body "" \
    --repo "https://github.ibm.com/org/inventory-repository"

  # promotion branch can be deleted once the PR was merged
}

$ promote master staging
```
{: codeblock}

2. Conclude a deployment - moving `target-latest` tag to the same commit as `pipeline-run-id` tag as a conclusion of deployment.

```
conclude () {
  local target="$1"
  local tag="$2"

  latest="$1-latest"

  # remove the latest tag
  git push origin ":refs/tags/$latest"
  # find the commit hash of the target tag
  sha=$(git rev-list -n 1 $tag)
  
  # add the latest tag to the same commit of the target tag
  git tag -fa "$latest" -m "" $sha
  git push --tags --force
}

$ conclude staging pipeline-run-fe33b05c
```
{: codeblock}

3. Reverting staging to an earlier state (using Git and GitHub CLI)

```
revert () {
  local branch="$1"
  local commit="$2"
  
  # create a revert branch from the target branch
  git checkout "$branch"
  git pull --rebase
  git checkout -b "$branch-revert"

  # revert commits since the target commit, then commit and push
  git revert -n $(git rev-list --no-merges HEAD...$commit)
  git commit -m "revert $branch to $commit"
  git push --set-upstream origin "$branch-revert"

  # create PR from revert branch to the target branch
  gh pr create \
    --base "$branch" \
    --head "$branch-revert" \
    --title "Revert $branch to $commit" \
    --body "" \
    --repo "$REPO"

  # revert branch can be deleted once the PR was merged
}

$ revert staging ba3b8e5ed3320e6b4981077e1a1627f08de4f511
```
{: codeblock}

## Common use cases for working with Git repos
{: #common-use-cases}

Check out the example scenarios outlined in the following docs to learn more about working with Git repos:

* [Promoting to target branches](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-promote-branches)
* [Promoting changes from the master branch](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-promote-master)
* [Deploying content to staging again](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-redeploy-staging)
* [Rolling back apps from production](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-apps-rollback)
