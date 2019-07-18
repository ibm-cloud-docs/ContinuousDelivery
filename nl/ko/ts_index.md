---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# 자주 묻는 질문(FAQ)
{: #ts_cd}

{{site.data.keyword.contdelivery_full}} 사용에 대한 자주 묻는 질문의 답변을 확인하십시오.
{:shortdesc}

## 도구 체인 페이지에 {{site.data.keyword.contdelivery_short}} 서비스 Lite 플랜이 초과되었다고 표시되는 이유는 무엇입니까?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}}는 Lite와 프로페셔널이라는 두 가지 플랜을 제공합니다. {{site.data.keyword.contdelivery_short}} Lite 플랜을 사용하는 경우 플랜의 한계까지 도구 체인을 무료로 사용할 수 있습니다. 오류 메시지에 하나 이상의 Lite 플랜 한계를 초과했다고 표시됩니다. 예를 들어, {{site.data.keyword.contdelivery_short}} 서비스 인스턴스와 연관된 권한 부여된 사용자가 너무 많거나 최대 수의 {{site.data.keyword.deliverypipeline}} 작업을 실행한 경우 플랜을 초과할 수 있습니다. 플랜의 조항에 대한 자세한 정보는 [플랜 한계 및 사용](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)을 참조하십시오.


## 내 {{site.data.keyword.contdelivery_short}} 서비스에서 30일 넘게 비활성 상태인 경우 Lite 플랜 서비스가 삭제된다고 합니다. 비활성 상태란 무엇을 의미합니까?
{: #plan_inactivity}
{: faq}

{{site.data.keyword.contdelivery_short}} 서비스는 동일한 리소스 그룹 또는 Cloud Foundry 조직에 있는 하나 이상의 도구 체인이 활성 상태인 경우 활성 상태로 간주됩니다. 도구 체인은 사용자가 사용자 인터페이스를 통해 이와 상호작용하거나, Delivery Pipeline 작업이 트리거되거나, {{site.data.keyword.gitrepos}}에서 관리하는 저장소가 액세스되거나, Eclipse Orion {{site.data.keyword.webide}} 작업공간이 사용 중인 경우 활성 상태로 간주됩니다. 비활성 상태로 간주되려면 {{site.data.keyword.contdelivery_short}} 서비스와 연관된 모든 도구 체인에서 이러한 상태가 30일동안 없어야 합니다.


## 도구 체인을 작성했습니다. 도구 체인 페이지에 Continuous Delivery 서비스가 필요하다고 표시되는 이유는 무엇입니까?
{: #service_required_resource_group}
{: faq}

도구 체인과 동일한 리소스 그룹 또는 조직에 있는 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스에 대한 플랜의 조항을 통해 서비스에 포함된 몇 가지 도구 통합({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} 및 {{site.data.keyword.gitrepos}}) 사용을 관리합니다. 오류 메시지에 리소스 그룹 또는 조직에 {{site.data.keyword.contdelivery_short}} 서비스의 필수 인스턴스가 없다고 표시됩니다. 플랜의 조항에 대한 자세한 정보는 [플랜 한계 및 사용](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)을 참조하십시오.


## Cloud Foundry 조직에서 도구 체인에 대한 정보를 업데이트했으나 해당 도구 체인에서 변경사항이 반영되지 않은 것으로 보이는 이유는 무엇입니까?
{: #updates_in_cloud_foundry}
{: faq}

Cloud Foundry에서 직접 도구 체인 정보를 업데이트하는 경우에는 {{site.data.keyword.contdelivery_short}} 서비스가 새로 고쳐져 변경사항을 표시하는 데 몇 분 정도 소요될 수 있습니다. 예를 들어, Cloud Foundry 조직에서 사용자를 추가하거나 제거하는 경우 {{site.data.keyword.contdelivery_short}}에서 새 사용자가 있음을 인식하고 이 사용자에게 도구 체인에 대한 액세스를 허용하는 데는 몇 분 정도 소요될 수 있습니다.


## Cloud Foundry 조직에서 도구 체인을 작성했습니다. 도구 체인 페이지에 Continuous Delivery 서비스가 필요하다고 표시되는 이유는 무엇입니까?
{: #service_required_cloud_foundry}
{: faq}

{{site.data.keyword.contdelivery_short}} 서비스의 인스턴스가 없는 리소스 그룹이나 조직에서 도구 체인을 작성하는 경우 도구 체인 플랫폼이 Lite 플랜을 사용하여 서비스의 인스턴스를 자동으로 작성하려고 시도합니다. 오류 메시지에 도구 체인 플랫폼이 서비스 인스턴스를 작성할 수 없다고 표시됩니다.

{{site.data.keyword.contdelivery_short}}의 인스턴스가 아직 없는 Cloud Foundry 조직 및 미국 남부 지역에서 도구 체인을 작성하는 경우에 이 오류가 발생할 수 있습니다. 미국 남부 지역에서는 리소스 그룹에 있는 {{site.data.keyword.contdelivery_short}} 서비스의 모든 인스턴스를 새로 작성해야 합니다. 

{{site.data.keyword.contdelivery_short}}의 인스턴스가 이미 있는 조직에서 도구 체인을 작성하거나 리소스 그룹에서 도구 체인을 작성할 수 있습니다.
  

## Cloud Foundry 조직에서 리소스 그룹으로 도구 체인을 이동하는 방법은 무엇입니까?
{: #toolchain_move_to_resource_group}
{: faq}

Cloud Foundry 조직에서 리소스 그룹으로 도구 체인을 자동으로 마이그레이션하는 기능은 아직 출시되지 않았습니다. 대신 리소스 그룹에서 도구 체인을 수동으로 다시 작성한 후 원본 도구 체인을 Cloud Foundry 조직에서 제거할 수 있습니다.


## 앱을 {{site.data.keyword.Bluemix_notm}}에 배치하려고 시도했습니다. 왜 오류가 발생합니까?
{: #org_outofmemory}
{: faq}

앱을 {{site.data.keyword.Bluemix_notm}}에 베치하려고 시도할 때 다음 오류 메시지가 발생하는 경우 조직에 남아 있는 메모리의 양이 배치하려는 앱에서 필요한 메모리 양보다 적습니다.

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

계정의 메모리 할당량을 늘리거나 앱이 사용하는 메모리를 줄일 수 있습니다. 평가판 계정의 최대 메모리 할당량은 2GB입니다. 계정의 메모리 할당량을 늘리려면 평가판 계정을 유료 계정으로 변환하십시오. 평가판 계정을 유료 계정으로 변환하는 방법에 대한 정보는 [내 계정을 업그레이드하거나 변경하려면 어떻게 해야 합니까?](/docs/account?topic=account-accountfaqs#changeacct)를 참조하십시오. 앱이 사용하는 메모리를 줄이려면 {{site.data.keyword.Bluemix_notm}} 콘솔 또는 cf 명령행 인터페이스를 사용하십시오.

{{site.data.keyword.Bluemix_notm}} 콘솔을 사용하는 경우 다음 단계를 완료하십시오.

1. 앱 대시보드에서 앱을 선택하십시오. 앱 세부사항 페이지가 열립니다.
1. 런타임 페이지에서 사용자의 앱에 대한 최대 메모리 한계 또는 앱 인스턴스 수를 줄이거나 둘 다 줄일 수 있습니다.

cf 명령행 인터페이스를 사용하는 경우 다음 단계를 완료하십시오.

1. 앱에 사용되는 메모리의 양을 확인하십시오. cf 앱 명령은 현재 영역에 배치된 앱을 모두 나열합니다. 각 앱의 상태도 표시됩니다.

	  ```
	  cf apps
	  ```

1. 앱에서 사용하는 메모리의 양을 줄이려면 앱 인스턴스 수 또는 최대 메모리 한계를 줄이거나 둘 다 줄이십시오.

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```
    
1. 변경사항이 적용되도록 앱을 다시 시작하십시오.


## 앱을 작성했지만 실행 표시줄이 {{site.data.keyword.webide}}에서 {{site.data.keyword.Bluemix_notm}} Live Sync 아이콘을 표시하지 않는 이유는 무엇입니까?
{: #ts_llz_lkb_3r}
{: faq}

![실행 표시줄](images/webide_runbar_light.png)   

{{site.data.keyword.webide}}에서 Node.js 앱을 편집하는 경우, 다음 상황에서는 실행 표시줄에서 {{site.data.keyword.Bluemix_notm}} Live Edit, 빠른 다시 시작 및 디버그 아이콘을 사용할 수 없습니다.


* `manifest.yml` 파일이 프로젝트의 상위 레벨에 저장되지 않습니다.
* 앱이 루트가 아닌 서브디렉토리에 저장되지만 서브디렉토리의 경로가 `manifest.yml` 파일에 지정되지 않습니다.
* 앱에 `package.json` 파일이 없습니다.


`manifest.yml` 파일이 루트에 저장되지 않은 경우 루트에 저장하십시오. 앱이 서브디렉토리에 저장된 경우 `manifest.yml` 파일에 서브디렉토리의 경로를 지정하십시오. 앱에 `package.json` 파일이 없는 경우 앱과 동일한 디렉토리에 파일을 작성하십시오.


## {{site.data.keyword.webide}} 실행 단추를 클릭했습니다. 로그 파일은 어디에 있습니까? 
{: #web_ide_log_files}
{: faq}  

실행 단추를 클릭하면 데스크탑에서 `cf push`를 입력한 경우 배치되는 것과 같은 방식으로 작업공간의 컨텐츠가 Cloud Foundry에 푸시됩니다. 로그 파일은 Cloud Foundry 대시보드에서 찾을 수 있습니다.

작업공간의 컨텐츠를 배치하는 데 대한 자세한 정보는 [작업공간에서 앱 배치](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy)를 참조하십시오.


## {{site.data.keyword.webide}}가 Git 보기에서 모든 변경사항을 자동으로 선택하지 않도록 하는 방법은 무엇입니까? 
{: #web_ide_git_view}
{: faq} 

{{site.data.keyword.webide}}에서는 기본적으로 사용자가 Git 페이지로 이동할 때마다 발신 변경사항을 코드 저장소에 푸시하려 한다고 가정합니다. 커미트하고, 동기화하고, 재설정하고 대체할 리소스를 수동으로 선택하려는 경우에는 GIT 환경 설정 페이지에서 **변경된 파일 항상 선택** 선택란을 선택 취소하십시오.


## 내가 사용하는 언어를 {{site.data.keyword.webide}}가 지원하지 않는 이유는 무엇입니까? 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}}는 JavaScript, HTML 및 CSS를 위한 광범위한 도구 및 지원을 제공합니다. 이는 가장 많이 사용되는 언어들에 대한 구문 강조표시 또한 제공합니다. 특정 언어를 지원하도록 {{site.data.keyword.webide}}를 확장할 수는 없습니다. {{site.data.keyword.webide}}에서 지원하는 언어의 전체 목록을 보려면 [지원되는 언어](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages)를 참조하십시오.


## {{site.data.keyword.Bluemix_notm}} 및 {{site.data.keyword.contdelivery_short}} 서비스의 상태는 어떻게 찾아볼 수 있습니까?
{: #toolchains_load}
{: faq}

{{site.data.keyword.Bluemix_notm}} 상태 페이지를 확인하여 알려진 문제가 {{site.data.keyword.Bluemix_notm}} Platform 및 {{site.data.keyword.Bluemix_notm}}의 주요 서비스에 영향을 주는지 판별하십시오.

다음 옵션 중 하나를 선택하여 상태 페이지를 찾을 수 있습니다.

  * {{site.data.keyword.Bluemix_notm}} 콘솔에 로그인하십시오. 메뉴 표시줄에서 **지원**을 클릭하고 **상태**를 선택하십시오. ![몇 가지 문제](../../get-support/images/some_issues.svg) 아이콘에 대해 나열된 리소스를 확인하십시오. 이 아이콘은 가동 중단을 표시합니다.
  * [{{site.data.keyword.Bluemix_notm}} - 시스템 상태](https://cloud.ibm.com/status){: external}에서 직접 액세스하십시오.

{{site.data.keyword.Bluemix_notm}} 상태 페이지에 대한 자세한 정보는 [{{site.data.keyword.Bluemix_notm}} 상태 보기](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status)를 참조하십시오.


## 파이프라인 작업 간에 아티팩트를 전달하는 방법은 무엇입니까?
{: #artifacts_pipeline_jobs}
{: faq}

특정 단계의 모든 파이프라인은 동일한 단계 입력을 수신하므로 동일한 단계에 있는 작업 간에 아티팩트를 전달할 수는 없습니다. 그러나 빌드 작업은 다른 단계의 작업에서 사용할 수 있는 아티팩트를 생성합니다. 두 작업 간에 아티팩트를 전달하려면 각 작업을 별도의 단계로 이동하십시오. 파이프라인 작업에 대한 자세한 정보는 [작업](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs)을 참조하십시오.


## 파이프라인 작업이 실행될 수 있는 최대 시간 한계가 있습니까?
{: #pipeline_jobs_time_limit}
{: faq}

각 파이프라인 작업은 최대 60분 동안 실행될 수 있습니다. 특정 작업이 시간 한계를 초과하면 해당 작업이 실패합니다. 파이프라인 작업이 수행하는 작업을 더 작은 단계로 나눌 수 있는지 검사하십시오. 하나의 파이프라인 작업을 60분 내에 실행되는 몇 개의 더 작은 파이프라인 작업으로 나눌 수 있습니다.


## 파이프라인 보안 특성의 보안성은 어느 정도입니까?
{: #pipeline_secure_properties}
{: faq}

파이프라인 보안 특성은 AES-128을 사용하여 암호화되며 파이프라인 스크립트에 전달되기 직전에 복호화됩니다. 이러한 특성은 또한 특성 사용자 인터페이스 및 파이프라인 로그 파일에서 별표를 사용하여 마스킹됩니다. 데이터는 파이프라인 작업에 대한 로그 파일에 기록되기 전에, 파이프라인 보안 특성에 있는 모든 값과 정확히 일치하는 항목이 있는지 스캔됩니다. 일치 항목이 발견되는 경우 이는 별표를 사용하여 마스킹됩니다. 정확히 일치하는 항목만 마스킹되므로 보안 특성 및 로그 파일에 대해 작업할 때는 주의하십시오. 
