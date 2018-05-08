---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-21"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 자주 묻는 질문(FAQ)
{: #ts_cd}

{{site.data.keyword.contdelivery_full}} 사용에 대한 자주 묻는 질문의 답변을 확인하십시오.
{:shortdesc}


## GitHub 도구 통합을 내 도구 체인에 추가하려고 시도했습니다. 도구 통합이 왜 추가되지 않습니까? 
{: #cannot_authorize_github}

{{site.data.keyword.Bluemix_notm}}에 GitHub 계정에 액세스할 권한이 없는 경우 도구 통합이 도구 체인에 추가되지 않습니다. 

도구 체인을 작성하는 동안 GitHub 도구 통합을 구성 중인 경우 GitHub에 권한을 부여하려면 다음 단계를 수행하십시오. 

  1. 구성 가능한 통합 섹션에서 **GitHub**를 클릭하십시오.
  1. {{site.data.keyword.Bluemix_notm}} 퍼블릭에 도구 체인을 작성 중이고 GitHub에 액세스할 권한이 {{site.data.keyword.Bluemix_notm}}에 없으면 **권한 부여**를 클릭하여 GitHub 웹 사이트로 이동하십시오.
  1. 활성 GitHub 세션이 없으면 로그인을 요구하는 프롬프트가 표시됩니다. **애플리케이션에 권한 부여**를 클릭하여 {{site.data.keyword.Bluemix_notm}}에서 사용자의 GitHub 계정에 액세스할 수 있도록 허용하십시오.

이미 도구 체인이 있으면 GitHub 도구 통합의 구성을 업데이트하십시오.

 1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
 1. GitHub 카드에서 메뉴를 클릭하고 **구성**을 클릭하십시오.
 1. 구성 설정을 업데이트하여 GitHub에 액세스할 수 있도록 {{site.data.keyword.Bluemix_notm}}에 권한 부여하십시오. **권한 부여**를 클릭하여 GitHub 웹 사이트로 이동하십시오. 활성 GitHub 세션이 없으면 로그인을 요구하는 프롬프트가 표시됩니다. **애플리케이션에 권한 부여**를 클릭하여 {{site.data.keyword.Bluemix_notm}}에서 사용자의 GitHub 계정에 액세스할 수 있도록 허용하십시오.
 1. 설정 업데이트를 완료하면 **통합 저장**을 클릭하십시오.


## 도구 체인을 작성하려고 시도했습니다. 왜 오류가 발생합니까?
{: #cannot_create_toolchain}

도구 체인을 작성하려고 시도할 때 다음 오류 메시지가 발생하는 경우 조직에서 하나 이상의 도구 체인을 제거한 후 도구 체인을 다시 작성하십시오. 

`This organization contains 200 toolchains, which is the maximum limit. Before you can add another toolchain, remove one or more toolchains from the organization.`


## 앱을 {{site.data.keyword.Bluemix_notm}}에 배치하려고 시도했습니다. 왜 오류가 발생합니까?
{: #org_outofmemory}

앱을 {{site.data.keyword.Bluemix_notm}}에 베치하려고 시도할 때 다음 오류 메시지가 발생하는 경우 조직에 남아 있는 메모리의 양이 배치하려는 앱에서 필요한 메모리 양보다 적습니다. 

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

계정의 메모리 할당량을 늘리거나 앱이 사용하는 메모리를 줄일 수 있습니다. 평가판 계정의 최대 메모리 할당량은 2GB입니다. 계정의 메모리 할당량을 늘리려면 평가판 계정을 유료 계정으로 변환하십시오. 평가판 계정을 유료 계정으로 변환하는 방법은 [유료 계정](/docs/pricing/index.html#pay-accounts)을 참조하십시오. 앱이 사용하는 메모리를 줄이려면 {{site.data.keyword.Bluemix_notm}} 콘솔 또는 cf 명령행 인터페이스를 사용하십시오. 

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


## 앱을 작성했습니다. 왜 실행 표시줄이 Eclipse Orion Web IDE에서 {{site.data.keyword.Bluemix_notm}} Live Sync 아이콘을 표시하지 않습니까?
{: #ts_llz_lkb_3r}

![실행 표시줄](images/webide_runbar_light.png)   

Web ID에서 Node.js 앱을 편집하는 경우 {{site.data.keyword.Bluemix_notm}} Live Edit, 빠른 다시 시작 및 디버그 아이콘은 다음 환경의 실행 표시줄에서 사용할 수 없습니다. 


* `manifest.yml` 파일이 프로젝트의 상위 레벨에 저장되지 않습니다.
* 앱이 루트가 아닌 서브디렉토리에 저장되지만 서브디렉토리의 경로가 `manifest.yml` 파일에 지정되지 않습니다.
* 앱에 `package.json` 파일이 없습니다.


`manifest.yml` 파일이 루트에 저장되지 않은 경우 루트에 저장하십시오. 앱이 서브디렉토리에 저장된 경우 `manifest.yml` 파일에 서브디렉토리의 경로를 지정하십시오. 앱에 `package.json` 파일이 없는 경우 앱과 동일한 디렉토리에 파일을 작성하십시오. 


## 개요 페이지를 보기 위해 해당 도구 체인을 클릭했습니다. 왜 도구 체인이 로드되지 않습니까? 
{: #toolchains_load}

{{site.data.keyword.Bluemix_notm}} 상태 페이지를 확인하여 알려진 문제가 {{site.data.keyword.Bluemix_notm}} Platform 및 {{site.data.keyword.Bluemix_notm}}의 주요 서비스에 영향을 주는지 판별하십시오.

다음 옵션 중 하나를 선택하여 상태 페이지를 찾을 수 있습니다.

  * {{site.data.keyword.Bluemix_notm}} 콘솔에 로그인하십시오. 메뉴 표시줄에서 **지원**을 클릭하고 **상태**를 선택하십시오. ![몇 가지 문제](../../get-support/images/some_issues.svg) 아이콘에 대해 나열된 리소스를 확인하십시오. 이 아이콘은 가동 중단을 표시합니다.
  * [{{site.data.keyword.Bluemix_notm}} - 시스템 상태 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/status){: new_window}에서 직접 액세스하십시오.

{{site.data.keyword.Bluemix_notm}} 상태 페이지에 대한 자세한 정보는 [{{site.data.keyword.Bluemix_notm}} 상태 보기](https://console.bluemix.net/docs/get-support/ViewStatus.html#viewing-bluemix-status)를 참조하십시오. 


## 내 도구 체인에 대해 도구 통합을 구성했습니다. 왜 구성되지 않습니까? 
{: #tool_integration_error}

도구 통합을 추가하는 경우, 도구 체인은 도구 통합에 의해 표시된 도구와 통신하여 필수 리소스를 프로비저닝하고 이를 도구 체인과 연관시킵니다. 설정 프로세스 중에 오류가 발생하거나 도구 체인과 도구 간의 통신이 제대로 완료되지 않은 경우, 도구 통신은 오류 상태가 됩니다.

 ![설정 실패 오류](images/tool_setup_failed.png)

다음을 수행하여 다시 도구 통합을 구성하도록 시도할 수 있습니다. 

1. 해당 도구 카드에서 `Setup failed` 메시지 위에 마우스 커서를 올려놓고 **재구성**을 클릭하십시오.

 ![재구성 단추](images/tool_reconfigure.png)

1. 올바른 구성 매개변수를 사용 중인지 확인하십시오. 올바르지 않은 구성 때문에 오류가 발생한 경우에는 오류 메시지가 표시됩니다. 예: `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`. 도구 통합에 대한 설정을 업데이트하고 **통합 저장**을 클릭하십시오.
1. 통신 문제점 때문에 오류가 발생한 경우에는 **통합 저장**을 클릭하여 다시 시도하십시오.
