---

copyright:
  years: 2017, 2018
lastupdated: "2018-8-2"

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 사용자 정의 도구 체인 템플리트 작성
{: #toolchains_custom}

사용자 정의 도구 체인 템플리트를 작성하여 DevOps 워크플로우를 향상시키십시오. 기존의 도구 체인 템플리트로 빠르게 시작하거나 필요한 통합만 포함된 도구 체인 템플리트를 작성할 수 있습니다. 언제든지 도구 체인의 통합을 추가하거나 제거할 수 있습니다.
{:shortdesc}

여러 가지 방법으로 [도구 체인을 작성](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started){: new_window}할 수 있습니다. 사용자 정의 도구 체인 템플리트를 작성하고 나면 [{{site.data.keyword.Bluemix_notm}}로 배치 작성 단추](/docs/services/ContinuousDelivery/deploy_button.html#deploy-button){: new_window}를 사용하여 공유할 수 있습니다.   도구 체인 템플리트 SDK에 대한 세부사항은 [Open Toolchain SDK](https://github.com/open-toolchain/sdk/wiki/){:new_window}를 참조하십시오. 단계별 튜토리얼은 [Garage Method 사이트](https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain/){:new_window}에서 확인할 수 있습니다.


## 시작하기
{: #toolchains_custom_gettingstarted}

사용자 정의 도구 체인 템플리트를 작성하려면 단순 Cloud Foundry 도구 체인 템플리트를 복제하여 시작하십시오. 기존 템플리트를 복제하면 사용자 정의된 도구 체인을 위한 시작점이 제공됩니다.

1. GitHub의 [단순 도구 체인](https://github.com/open-toolchain/simple-toolchain){: new_window} 템플리트를 복제하려면 원하는 Git 클라이언트를 사용하여 다음 명령을 입력하십시오.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 이 템플리트는 단일 GitHub 저장소에서 기본 Hello World 애플리케이션을 배치하고 지속적 딜리버리, 소스 제어, 문제 추적 및 온라인 제어를 위해 사전 구성된 단순 도구 체인을 포함합니다.

2. 좀 더 복잡한 도구 체인 템플리트로 시작하려면 [마이크로서비스용 클라우드 네이티브 도구 체인](https://github.com/open-toolchain/toolchain-demo){: new_window}을 복제하여 시작할 수 있습니다.

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

마이크로서비스 템플리트는 자체 GitHub 저장소에 각각 포함되어 있는 세 개의 마이크로서비스로 구성된 온라인 저장소를 배치합니다. 또한 좀 더 복잡한 도구 체인으로, 다음에 대해 사전 구성됩니다.
* Continuous Delivery
* 소스 제어
* Blue-green 배치
* 기능 테스트
* 문제 추적
* 온라인 편집
* 메시징

선택한 템플리트에 관계없이, 일반적으로 사용자가 작성한 도구 체인을 사용자 정의하기 위한 프로세스는 동일합니다.

템플리트를 복제하면 readme 파일 및 `.bluemix` 디렉토리가 포함된 기본 GitHub 디렉토리가 제공됩니다. 디렉토리에는 도구 체인에서 작동하는 데 필요한 모든 구성 파일이 필요합니다. 최소한 `.bluemix` 디렉토리에는 다음 파일이 포함되어야 합니다.

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![도구 체인을 정의하는 데 필요한 최소 파일](images/min_files_for_a_toolchain.png)


다음 섹션에는 각 파일에 대한 설명이 있습니다. 각 섹션에는 도구 체인이 향상될 때 참조할 수 있는 구성 정보가 포함됩니다.
YAML은 엄격한 JSON 수퍼 세트인 데이터 직렬화 언어로 구문론상 중요한 줄바꿈 및 들여쓰기가 추가되어 있습니다. 그러나 YAML은 리터럴 탭 문자를 전혀 허용하지 않습니다.

## 구성 파일 이해
{: #toolchains_custom_config_files}


도구 체인 템플리트 구성 파일은 주로 YAML 형식 파일로 구성됩니다. 각 파일에는 도구 체인의 다른 부분에 대해 설명하는 메타데이터가 포함됩니다. 메타데이터에 포함되는 항목은 다음과 같습니다.
* 도구 체인 및 저장소에 대한 정보
* 코드의 빌드 및 배치 방법에 대한 세부사항
* 도구 체인에 있는 도구의 구성 특성

도구 체인이 더욱 복잡해짐에 따라 구성 파일도 복잡해질 수 있습니다.

YAML 파일을 작업할 때 다음 사항에 유의하십시오.

* 공백에만 공백을 사용하십시오. 탭은 사용할 수 없습니다.
* 모든 특성 및 목록은 하나의 공백 이상 들여쓰기되어야 합니다.
* 모든 키와 특성은 대소문자를 구분합니다.

오류가 발생하지 않도록 YAML 파일의 형식화에 주의하십시오.
오류를 검사하기 위해 [이 구문 분석기](http://wiki.ess3.net/yaml/){: new_window}와 같은 단순한 유효성 검증기를 사용하려고 할 수 있습니다.
{: tip}

## 서비스 섹션 계획
각 서비스 하위 섹션에는 다음 정보가 포함되어 있습니다.

* name - 사용자가 생성한 문자열로 현재 파일의 컨텍스트에서 이 서비스를 식별하는 데 사용됩니다. 이 이름은 필요에 따라 서비스를 표시하는 데 사용할 수 있습니다.

* service_id - 서비스를 식별하는 고유 문자열입니다. 이 문자열은 [서비스 카탈로그](https://github.com/open-toolchain/sdk/wiki/services.md){: new_window}에서 직접 제공됩니다.

* parameters - 서비스에 대한 제로(0) 또는 추가 구성 매개변수입니다. 이러한 매개변수는 서비스에 따라 달라집니다. 사용자는 특정 서비스에 어떤 매개변수가 필요한지 알아내기 위해 카탈로그를 참조해야 합니다.

### 다른 파일의 텍스트 포함

도구 체인에 대한 모든 정보는 `toolchain.yml` 파일에 있을 수 있습니다.  그러나 `$text`를 사용하여 각 도구 통합 UI에 대한 별도의 파일을 작성하려고 할 수 있습니다. 이를 통해 도구 체인을 더 쉽게 유지보수할 뿐만 아니라 구성 파일을 편집하는 데 드는 시간을 최소화할 수 있습니다.  `toolchain.yml`의 이 예제 스니펫은 `content`에 대한 값으로 `pipeline.yml` 파일의 컨텐츠를 사용하는 방법을 보여줍니다.

```
  configuration:
    content:
      $text: pipeline.yml
```

### 도구 체인 템플리트 현지화

도구 체인의 문자열이 사용자가 원하는 언어로 표시되도록 `nls` 디렉토리에서 UI 문자열을 구체화하여 도구 체인을 현지화할 수 있습니다.
`toolchain.yml` 파일은 `$i18n` 참조를 포함해야 합니다.  
다음 예제는 `messages.yml` 파일에 대한 `$i18n` 참조를 보여줍니다.

```
messages:
  $i18n: messages.yml
```

  영어 문자열은 `messages.yml`에 있으며 다른 언어는 `messages_de.yml`과 같이 언어 코드를 사용합니다.   언어 코드 목록은
  [언어 식별을 위한 태그](https://tools.ietf.org/html/rfc5646){: new_window}에서 찾을 수 있습니다.

   구체화된 문자열을 참조하려면 `$ref`를 사용하여 문자열을 검색하십시오.  예를 들면, 다음과 같습니다.

```
  template:
    name:
      $ref: "#/messages/template.name"
```

  구체화된 문자열을 사용하지 않는 경우에는 다음을 사용할 수 있습니다.

```
  template:
    name: my_template
```

자세히 알아보려면 [Open Toolchain SDK의 메시지 섹션](https://github.com/open-toolchain/sdk/wiki/Template-File-Format#messages-section){: new_window}을 참조하십시오.

## 도구 체인 파일 구성
{: #toolchains_custom_toolchain_yml}

`toolchain.yml` 파일은 도구 체인의 핵심입니다. 가져올 저장소, 포함시킬 서비스 및 빌드 세부사항과 같은 도구 체인의 상세 항목이 이 파일에 모두 요약되어 있습니다. 해당 컨텐츠를 이해하기 위해 여러 섹션으로 구분할 수 있습니다.

1\. **도구 체인 소개 정보:**

 파일의 이 섹션에서는 사용자가 도구 체인 작성 페이지에서 볼 수 있는 도구 체인에 대한 간단한 세부사항을 제공합니다. 도구 체인의 이름 및 도구 체인의 용도에 대한 설명이 포함됩니다. 또한 도구 체인의 로고 또는 시각적 묘사가 포함될 수도 있습니다.

 도구 체인에 대한 소개 컨텐츠를 제공할 뿐만 아니라, 이 섹션에는 도구 체인의 일부인 도구를 정의하는 `required`라는 키가 포함되어 있습니다. 도구 체인의 작성자는 템플리트에서 도구 체인을 작성할 때 이 도구를 구성합니다. 도구 체인 작성 페이지에 구성될 수 있는 각 도구에 `required` 키의 특성으로 `toolchain.yml` 파일에 정의된 대로 도구의 상위 키를 추가하십시오.

 이 스니펫에는 이 섹션에 대한 예가 표시됩니다.

 ```
 ---
template
  name: "Simple Toolchain"
  description: "This Hello World application uses Node.js and includes a toolchain that is preconfigured for continuous delivery, source control, issue tracking, and online editing.\n\nTo get started, click **Create**."
  header: '![](toolchain.svg)'
  icon: icon.svg
  required:
   - sample-build
   - sample-repo
  info:
    git url: >-
      [https://github.com/my-toolchain/simple-toolchain](https://github.com/open-toolchain/simple-toolchain)
    git branch: >-
      [master](https://github.com/my-toolchain/simple-toolchain/tree/master)
  ```
 {: codeblock}

이 예에서 Git URL 및 Git 분기는 새 도구 체인 템플리트를 위한 항목입니다.

2\. **저장소 정의:**

 도구 체인은 GitHub, GitHub 엔터프라이즈, Git 저장소와 문제 추적 및 GitLab을 포함하여 여러 Git 저장소를 위한 지속적 딜리버리를 제공할 수 있습니다. `toolchain.yml` 파일의 이 섹션에 각 저장소가 정의되어 있습니다.

 도구 체인에 추가되는 각 저장소의 경우 다음 특성과 함께 저장소의 이름을 나타내는 상위 키를 추가하십시오.

|항목 |키/특성 |값 |설명 |
|------|--------------|-------|-------------|
|repo-name |키 |  |조장소 이름. 이 키는 이름과 일치합니다(sample-repo). |
|service_id |특성 |<`githubpublic` , `githubprivate`, `hostedgit`, `gitlab`> |저장소의 유형 |
|parameters: |키 |  |  |
|repo_name |특성 |  |repo-name의 패턴. 다음 예에서는 repo 이름으로 도구 체인 이름을 사용합니다. |
|repo_url |특성 |  |저장소의 URL |
|type |특성 |<`new`, `fork`, `clone`, `link`> |새 저장소를 작성하는 방법 |
|has_issues |특성 |<`true`, `false`> |사용 문제 |
|enable_traceability |properties |<`true`, `false`> |커미트, 가져오기 요청 및 참조된 문제에 대한 태그, 레이블 및 주석을 작성하여 코드 변경사항의 배치를 추적하는지 여부를 결정합니다.|

 여러 저장소를 정의하고 `has_issues: true`로 저장소를 구성하는 경우 GitHub Issue 트래커의 단일 인스턴스가 도구 체인에 추가됩니다. 트래커는 `true`로 설정된 모든 저장소의 문제를 계속 다룹니다.
 {: tip}

 이 스니펫에는 이 섹션에 대한 예가 표시됩니다.

 ```
 # Github repos
 services:
  sample-repo:
    service_id: githubpublic
    parameters:
      repo_name: '{{toolchain.name}}'
      repo_url: 'https://github.com/open-toolchain/node-hello-world'
      type: clone
      has_issues: true
      enable_traceability: true
 ```
 {: codeblock}

3\. **파이프라인 정보:**

 파이프라인을 사용하여 프로젝트를 지속적으로 딜리버리할 수 있습니다. 파일의 이 섹션에서는 각 GitHub 및 Git Repo and Issue Tracking 저장소에 코드를 빌드하고 배치하는 데 사용되는 구성 세부사항을 정의합니다.

 시작하려면 도구 체인에 정의된 각 저장소에 파이프라인의 이름을 나타내는 상위 키를 추가하십시오. GitHub 또는 Git Repo and Issue Tracking 저장소의 이름에서 이 키를 가져올 것을 고려하십시오. 다음 특성을 추가하십시오.

|항목 |키/특성 |값 |설명 |
|------|--------------|-------|-------------|
|pipeline-name |키 |  |파이프라인의 이름(sample-build) |
|service_id |특성 |<`pipeline`> |사용될 서비스의 이름 |
|parameters |키 |  |  |
|이름 |특성 |<`repo_name`> |repos 섹션에 정의된 이름과 동일 |
|ui-pipeline |특성 |<`true`, `false`> |이 파이프라인이 배치하는 애플리케이션이 도구 체인 페이지의 **앱 보기** 메뉴에 표시되는 경우 True  |
|configuration |키 |  |  |
|content |특성 |<`$ref(pipeline.yml)`> |파이프라인 정의를 정의하는 파일 |
|env |키 |  |  |
|SAMPLE_REPO |키 |<`repo-name-key`> |저장소 상위 키와 동일한 이름 |
|CF_APP_NAME |특성 | <`'{{form.pipeline.parameters.prod-app-name}}'`> |Cloud Foundry에 사용되는 이름. 저장소 상위 키 이름을 이 특성에 포함시키는 것을 고려하십시오. |
|PROD_SPACE_NAME |특성 | <`'{{form.pipeline.parameters.prod-space}}'`> |배치할 {{site.data.keyword.Bluemix_notm}} 영역의 이름 |
|PROD_ORG_NAME |특성 | <`'{{form.pipeline.parameters.prod-organization}}'`> |배치할 {{site.data.keyword.Bluemix_notm}} 조직의 이름 |
|PROD_REGION_ID |특성 | <`'{{form.pipeline.parameters.prod-region}}'`> |배치할 {{site.data.keyword.Bluemix_notm}} 지역의 이름 |
|execute |특성 |<`true`, `false`> |작성 후 파이프라인 시작 |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 `pipeline.yml` 파일 작성에 대한 정보는 [다음 섹션](#toolchains_custom_pipeline_yml)에 있습니다.

 이 스니펫에는 파일의 이 섹션에 대한 예가 표시됩니다.

 ```
 # Pipelines
  sample-build:
    service_id: pipeline
    parameters:
      services:
        - sample-repo
      name: '{{services.sample-repo.parameters.repo_name}}'
      ui-pipeline: true
      configuration:
        content:
          $ref: pipeline.yml
        env:
          SAMPLE_REPO: sample-repo
          CF_APP_NAME: '{{form.pipeline.parameters.prod-app-name}}'
          PROD_SPACE_NAME: '{{form.pipeline.parameters.prod-space}}'
          PROD_ORG_NAME: '{{form.pipeline.parameters.prod-organization}}'
          PROD_REGION_ID: '{{form.pipeline.parameters.prod-region}}'
       execute: true
 ```
 {: codeblock}

4\. **배치 세부사항:**

 Continuous Delivery 프로세스의 일부로 사용자에게 액세스 권한이 있는 {{site.data.keyword.Bluemix_notm}} 지역, 조직 또는 영역에 애플리케이션을 배치하도록 도구 체인을 구성할 수 있습니다. 애플리케이션을 배치하는 위치에 대한 특정 세부사항은 도구 체인 작성 페이지에서 선택할 수 있습니다.

 ![Delivery Pipeline 구성 설정](images/deploy_configuration.png)

 `toolchain.yml` 파일의 이 섹션은 도구 체인 작성 페이지에서 구성될 수 있는 파이프라인 단계를 정의합니다.

 시작하기 위해 상위 키 `deploy`가 배치 구성 특성을 식별하는 데 사용됩니다. 다음 특성은 섹션의 나머지 부분을 구성합니다.

|항목 |키/특성 |값 |설명 |
|------|--------------|-------|-------------|
|deploy |키 |  |배치 섹션의 이름 |
|schema |특성 |<`deploy.json`> |배치 세부사항 구성을 위한 UI의 레이아웃을 정의하는 파일 |
|service-category |특성 |<`pipeline`> |배치 구성을 사용하는 서비스 |
|parameters |키 |  |  |
|prod-region |특성 | <`"{{region}}"`> |프로덕션 단계에 대한 {{site.data.keyword.Bluemix_notm}} 지역을 정의합니다. |
|prod-organization |특성 | <`"{{organization}}"`> |프로덕션 단계에 대한 {{site.data.keyword.Bluemix_notm}} 조직을 정의합니다. |
|prod-space |특성 |<`prod`> |프로덕션 단계에 대한 {{site.data.keyword.Bluemix_notm}} 영역을 정의합니다. |
|github-repo-name |특성 | <`"{{repo-name-key.parameters.repo_name}}"`> |GitHub 저장소 이름을 도구 체인 작성 페이지에 전달하는 변수 |

`deploy.json` 파일 작성에 대한 자세한 정보는 [이 섹션]을 참조하십시오. (#toolchains_custom_deploy_json)

 다음 예에서는 프로덕션 환경에 배치하는 단일 단계를 정의합니다.

 ```
 ## Configuring a deployment stage
 deploy:
   schema: deploy.json
   service-category: pipeline
   parameters:
 	prod-region: "{{region}}"
 	prod-organization: "{{organization}}"
 	prod-space: prod
 	hello-world-name: "{{hello-world-repo.parameters.repo_name}}"
 ```
 {: codeblock}

 코드 예제를 대부분 그대로 사용할 수 있으며 약간의 수정만 필요합니다. 이 섹션을 사용자 정의하려면, `github-repo-name`을 저장소의 이름과 일치하도록 설정하십시오. [`deploy.json`](#toolchains_custom_deploy_json) 파일의 세부사항도 업데이트해야 합니다.

 dev, QA 및 Prod 단계를 포함하는 보다 복잡한 파이프라인을 작성하기 위해 `parameters` 키 아래에서 다음 특성을 대체할 수 있습니다.

 ```
   매개변수:
 	dev-region: "{{region}}"
 	qa-region: "{{region}}"
 	prod-region: "{{region}}"
 	dev-organization: "{{organization}}"
 	qa-organization: "{{organization}}"
 	prod-organization: "{{organization}}"
 	dev-space: dev
 	qa-space: qa
 	prod-space: prod
 ```
 {: codeblock}

 ## 파이프라인 구성
 {: #toolchains_custom_pipeline_yml}

 `pipeline.yml` 파일에는 파이프라인의 단계에 대한 모든 구성 세부사항이 포함되어 있습니다. 기존의 pipeline.yml으로 시작할 수 있고 사용자의 필요에 맞게 사용자 정의할 수 있습니다.

 도구 체인에 하나 이상의 파이프라인이 포함되어 있는 경우 각 `pipeline.yml` 파일에 대한 고유 이름을 제공하십시오.

 다음은 `pipeline.yml` 파일의 예제입니다.

 ```
 ---
stages:
- name: BUILD
  inputs:
  - type: git
    branch: master
    service: ${SAMPLE_REPO}
  triggers:
  - type: commit
  jobs:
  - name: Build
    type: builder
- name: DEPLOY
  inputs:
  - type: job
    stage: BUILD
    job: Build
  triggers:
  - type: stage
  properties:
  - name: CF_APP_NAME
    value: undefined
    type: text
  - name: APP_URL
    value: undefined
    type: text
  jobs:
  - name: Blue-Green Deploy
    type: deployer
    target:
      region_id: ${PROD_REGION_ID}
      organization: ${PROD_ORG_NAME}
      space: ${PROD_SPACE_NAME}
      application: ${CF_APP_NAME}
    script: |
      #!/bin/bash
      # Push app
      if ! cf app $CF_APP; then  
        cf push $CF_APP
      else
        OLD_CF_APP=${CF_APP}-OLD-$(date +"%s")
        rollback() {
          set +e  
          if cf app $OLD_CF_APP; then
            cf logs $CF_APP --recent
            cf delete $CF_APP -f
            cf rename $OLD_CF_APP $CF_APP
          fi
          exit 1
        }
        set -e
        trap rollback ERR
        cf rename $CF_APP $OLD_CF_APP
        cf push $CF_APP
        cf delete $OLD_CF_APP -f
      fi
      # Export app name and URL for use in later Pipeline jobs
      export CF_APP_NAME="$CF_APP"
      export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
      # View logs
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## 파이프라인 인터페이스 구성
 {: #toolchains_custom_deploy_json}

 도구 체인 작성 페이지에서 구성 가능한 통합 섹션에서 Delivery Pipeline을 선택하는 경우 섹션이 펼쳐지고 다음 항목이 표시됩니다.

 	* 애플리케이션의 이름
 	* 파이프라인 단계가 배치되는 지역, 조직 및 영역

각 도구에 맞는 항목을 구성할 수 있습니다.

 ![Delivery Pipeline 구성 설정](images/deploy_configuration.png)

 UI에서 이 섹션의 레이아웃은 `deploy.json` 스키마에 의해 정의됩니다.

 스키마 내에서 다음 특성이 애플리케이션의 세부사항과 일치하도록 업데이트됩니다.

 	* 제목
 	* 설명
 	* 긴 설명
 	* `hello-world-name`의 모든 인스턴스 및 연관된 세부사항을 애플리케이션의 정보와 일치하도록 수정해야 합니다.

 다음 스니펫은 `deploy.json` 파일의 예제입니다.

 ```
 {
    "$schema": "http://json-schema.org/draft-04/schema#",
    "messages": {
        "$i18n": "locales.yml"
    },
    "title": {
        "$ref": "#/messages/deploy.title"
    },
    "description": {
        "$ref": "#/messages/deploy.description"
    },
    "longDescription": {
        "$ref": "#/messages/deploy.longDescription"
    },
    "type": "object",
    "properties": {
        "prod-region": {
            "description": "The {{site.data.keyword.Bluemix_notm}} region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The {{site.data.keyword.Bluemix_notm}} org",
            "type": "string"
        },
        "prod-space": {
            "description": "The {{site.data.keyword.Bluemix_notm}} space",
            "type": "string"
        },
        "prod-app-name": {
            "description": {
                "$ref": "#/messages/deploy.appDescription"
            },
            "type": "string",
            "pattern": "\\S"
        }
    },
    "required": [
        "prod-region",
        "prod-organization",
        "prod-space",
        "prod-app-name"
    ],
    "form": [
        {
            "type": "validator",
            "url": "/devops/setup/bm-helper/helper.html"
        },
        {
            "type": "text",
            "readonly": false,
            "title": {
                "$ref": "#/messages/deploy.appName"
            },
            "key": "prod-app-name"
        },
        {
            "type": "table",
            "columnCount": 4,
            "widths": [
                "15%",
                "28%",
                "28%",
                "28%"
            ],
            "items": [
                {
                    "type": "label",
                    "title": ""
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/region"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/organization"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/space"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/prodStage"
                    }
                },
                {
                    "type": "select",
                    "key": "prod-region"
                },
                {
                    "type": "select",
                    "key": "prod-organization"
                },
                {
                    "type": "select",
                    "key": "prod-space",
                    "readonly": false
                }
            ]
        }
    ]
}
 ```
 {: codeblock}


## 기타 도구 구성

 도구 체인의 코어 컴포넌트를 구성하고 나면 도구 체인에 기능을 추가하는 다른 도구 통합을 포함할 수 있습니다. 모든 추가 도구는 `toolchain.yml` 파일에 고유 항목이 필요합니다. 일부 도구는 별도의 YAML 구성 파일을 `.bluemix` 디렉토리에 추가해야 합니다.

 ![도구 체인을 정의하는 데 필요한 파일](images/files_for_toolchain_with_additional_tools.png)

사용 가능한 도구 체인 통합의 목록을 보려면 <a href="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">도구 체인 템플리트에 사용 가능한 서비스</a>를 참조하십시오. 다음 예는 도구 체인 YAML 파일에 대한 추가사항을 형식화하는 방법을 보여줍니다.

### **Slack**

#### toolchain.yml
{: #slack_toolchain_yaml}

```
messaging:
	  service_id: slack
	  $ref: slack.yml
```
{: codeblock}

#### slack.yml
{: #slack_slack_yaml}

```
---YAML
parameters:
  api_token: ""
  channel_name: ""
```
{: codeblock}

### **Sauce Labs**

#### toolchain.yml
{: #sauce_toolchain_yaml}

```YAML
test:
	  service_id: saucelabs
	  $ref: saucelabs.yml
```
{: codeblock}

#### saucelabs.yml
{: #sauce_slack_yaml}

```YAML
---
parameters:
  username: ""
  key: ""
```
{: codeblock}

### **Eclipse Orion Web IDE**

####	toolchain.yml
{: #eclipse_toolchain_yaml}

```YAML
webide:
	  service_id: orion
```
{: codeblock}
