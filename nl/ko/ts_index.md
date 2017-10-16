---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# {{site.data.keyword.contdelivery_short}} 문제점 해결
{: #ts_cd}

{{site.data.keyword.contdelivery_full}}의 사용에 대한 공통 문제점 해결 질문에 대한 답변을 얻습니다.
{:shortdesc}


## GitHub에서 권한을 부여할 수 없음
{: #cannot_authorize_github}

GitHub에서 권한이 부여되지 않았습니다.
{:shortdesc}

GitHub 계정에 액세스할 권한이 {{site.data.keyword.Bluemix_notm}}에 없으면 다음과 같은 문제가 발생할 수 있습니다.
{: tsSymptoms}

 * 도구 체인에 GitHub 도구 통합을 추가하려고 시도할 때 도구 통합이 추가되지 않습니다. 
 * GitHub 또는 GitHub Enterprise 저장소에 변경사항을 푸시할 때 파이프라인이 자동으로 실행되지 않습니다. 

GitHub에 액세스할 권한이 {{site.data.keyword.Bluemix_notm}}에 없습니다.   
{: tsCauses}

도구 체인을 작성하는 동안 GitHub 도구 통합을 구성 중이면 다음 단계를 따르십시오.
{: tsResolve}

  1. 구성 가능한 통합 섹션에서 **GitHub**를 클릭하십시오. 
  1. {{site.data.keyword.Bluemix_notm}} 퍼블릭에 도구 체인을 작성 중이고 GitHub에 액세스할 권한이 {{site.data.keyword.Bluemix_notm}}에 없으면 **권한 부여**를 클릭하여 GitHub 웹 사이트로 이동하십시오. 
  1. 활성 GitHub 세션이 없으면 로그인을 요구하는 프롬프트가 표시됩니다. **애플리케이션에 권한 부여**를 클릭하여 {{site.data.keyword.Bluemix_notm}}에서 사용자의 GitHub 계정에 액세스할 수 있도록 허용하십시오. 

이미 도구 체인이 있으면 GitHub 도구 통합의 구성을 업데이트하십시오. 

 1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오. 
 1. GitHub 카드에서 메뉴를 클릭하고 **구성**을 클릭하십시오. 
 1. 구성 설정을 업데이트하여 GitHub에 액세스할 수 있도록 {{site.data.keyword.Bluemix_notm}}에 권한 부여하십시오. **권한 부여**를 클릭하여 GitHub 웹 사이트로 이동하십시오. 활성 GitHub 세션이 없으면 로그인을 요구하는 프롬프트가 표시됩니다. **애플리케이션에 권한 부여**를 클릭하여 {{site.data.keyword.Bluemix_notm}}에서 사용자의 GitHub 계정에 액세스할 수 있도록 허용하십시오. 
 1. 설정 업데이트를 완료하면 **통합 저장**을 클릭하십시오. 


## 도구 체인을 작성할 수 없음
{: #cannot_create_toolchain}

도구 체인을 작성할 때 오류가 표시됩니다.
{:shortdesc}

도구 체인을 작성할 때 다음과 같은 오류 메시지가 표시됩니다.
{: tsSymptoms}

`This organization contains 200 toolchains, which is the maximum limit. Before you can add another toolchain, remove one or more toolchains from the organization.`

조직(org)에 200개가 넘는 도구 체인을 소유할 수 없습니다.   
{: tsCauses}

조직에서 하나 이상의 도구 체인을 제거한 후에 도구 체인을 다시 작성하십시오.
{: tsResolve}


## 조직의 메모리 한계를 초과함
{: #org_outofmemory}

조직의 메모리 한계가 초과된 경우 {{site.data.keyword.Bluemix_notm}}에 앱을 배치하지 못할 수 있습니다. 앱에서 사용하는 메모리를 줄이거나 계정의 메모리 할당량을 늘릴 수 있습니다. 평가판 계정의 최대 메모리 할당량은 2GB입니다. 이 할당량은 유료 계정으로 업그레이드할 때 늘릴 수 있습니다.

{{site.data.keyword.Bluemix_notm}}에 앱을 배치할 때 다음과 같은 오류 메시지가 표시됩니다.
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

이 오류는 조직의 남아 있는 메모리의 양이 배치하려는 앱에 필요한 메모리의 양보다 적을 경우에 발생합니다. 평가판 계정의 최대 메모리 할당량은 2GB입니다.
{: tsCauses}

계정의 메모리 할당량을 늘리거나 앱에서 사용하는 메모리를 줄일 수 있습니다.
{: tsResolve}

  * 계정의 메모리 할당량을 늘리려면 평가판 계정을 유료 계정으로 변환하십시오. 평가판 계정을 유료 계정으로 변환하는 방법은 [유료 계정](/docs/pricing/index.html#pay-accounts)을 참조하십시오.
  * 앱에서 사용하는 메모리를 줄이려면 {{site.data.keyword.Bluemix_notm}} 콘솔 또는 cf 명령행 인터페이스를 사용하십시오. 

    {{site.data.keyword.Bluemix_notm}} 콘솔을 사용하는 경우 다음 단계를 완료하십시오. 

    1. 앱 대시보드에서 앱을 선택하십시오. 앱 세부사항 페이지가 열립니다.
    2. 런타임 페이지에서 사용자의 앱에 대한 최대 메모리 한계 또는 앱 인스턴스 수를 줄이거나 둘 다 줄일 수 있습니다.

    cf 명령행 인터페이스를 사용하는 경우 다음 단계를 완료하십시오. 

    1. 앱에 사용 중인 메모리의 양을 확인하십시오.

	  ```
	  cf apps
	  ```

	  cf 앱 명령은 현재 영역에 배치된 앱을 모두 나열합니다. 각 앱의 상태도 표시됩니다.

    2. 앱에서 사용하는 메모리의 양을 줄이려면 앱 인스턴스 수 또는 최대 메모리 한계를 줄이거나 둘 다 줄이십시오.

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. 변경사항이 적용되도록 앱을 다시 시작하십시오.

앱 관리에 대한 일반 문제점에 대한 자세한 정보는 [앱 관리 문제점 해결](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps)을 참조하십시오.


## 실행 표시줄에 Eclipse Orion Web IDE에 Bluemix Live Sync 아이콘이 표시되지 않습니다.
{: #ts_llz_lkb_3r}

앱을 작성했으나 Eclipse Orion Web IDE 실행 표시줄에 IBM Bluemix Live Sync 아이콘이 표시되지 않습니다. Live Edit 아이콘이 포함된 전체 표시줄을 볼 수 없습니다. 

![실행 표시줄](images/webide_runbar_light.png)   

Web IDE의 Node.js 앱을 편집하는 경우 {{site.data.keyword.Bluemix_notm}} 라이브 편집, 빠른 다시 시작 및 디버그 아이콘이 실행 표시줄에 표시되지 않습니다.
{: tsSymptoms}

다음 상황에서는 아이콘을 사용할 수 없습니다.
{: tsCauses}

* `manifest.yml` 파일이 프로젝트의 상위 레벨에 저장되지 않습니다.
* 앱이 루트가 아닌 서브디렉토리에 저장되지만 서브디렉토리의 경로가 `manifest.yml` 파일에 지정되지 않습니다. 
* 앱에 `package.json` 파일이 없습니다. 

다음 방법 중 하나를 사용하십시오.
{: tsResolve}

* `manifest.yml` 파일이 루트에 저장되지 않은 경우 루트에 저장하십시오. 
* 앱이 서브디렉토리에 저장된 경우 `manifest.yml` 파일에 서브디렉토리의 경로를 지정하십시오.
   ```
    path: path_to_application
    ```
* 앱과 동일한 디렉토리에 있는 `package.json` 파일을 작성하십시오.


## 도구 체인이 로드되지 않음
{: #toolchains_load}

해당 개요 페이지를 보기 위해 도구 체인을 클릭할 때 도구 체인이 로드되지 않습니다.
{:shortdesc}

DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭하십시오. 그런 다음 **개요**를 클릭하십시오. 도구 체인에 대한 개요 페이지가 열리지 않습니다.
{: tsSymptoms}

문제점이 가동 중단으로 인한 것인지 보려면 {{site.data.keyword.Bluemix_notm}} 상태를 확인하십시오.
{: tsCauses}

알려진 문제점이 {{site.data.keyword.Bluemix_notm}} 플랫폼 및 {{site.data.keyword.Bluemix_notm}}의 주요 서비스에 영향을 미치는지 여부를 판별하기 위해 {{site.data.keyword.Bluemix_notm}} 상태 페이지를 확인하십시오.
{: tsResolve}

다음 옵션 중 하나를 선택하여 상태 페이지를 찾을 수 있습니다.

  * {{site.data.keyword.Bluemix_notm}} 콘솔에 로그인하십시오. 메뉴 표시줄에서 **지원**을 클릭하고 **상태**를 선택하십시오. ![몇 가지 문제](../../support/images/some_issues.svg) 아이콘에 대해 나열된 리소스를 확인하십시오. 이 아이콘은 가동 중단을 표시합니다.
  * [IBM {{site.data.keyword.Bluemix_notm}} - 시스템 상태 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://ibm.biz/bluemixstatus){: new_window}에서 직접 액세스하십시오.

{{site.data.keyword.Bluemix_notm}} 상태 페이지에 대한 자세한 정보는 [{{site.data.keyword.Bluemix_notm}} 상태 보기](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status)를 참조하십시오.


## 도구 통합이 구성되지 않음
{: #tool_integration_error}

도구 체인에 대한 도구 통합이 구성되면 `Setup failed` 오류가 해당 도구 카드에 표시됩니다.
{:shortdesc}

도구 통합이 구성된 후에 사용자는 도구 체인의 개요 페이지에서 해당 도구 카드를 보고 설정이 실패했음을 파악합니다.
{: tsSymptoms}

 ![설정 실패 오류](images/tool_setup_failed.png)

도구 통합을 추가하는 경우, 도구 체인은 도구 통합에 의해 표시된 도구와 통신하여 필수 리소스를 프로비저닝하고 이를 도구 체인과 연관시킵니다. 설정 프로세스 중에 오류가 발생하거나 도구 체인과 도구 간의 통신이 제대로 완료되지 않은 경우, 도구 통신은 오류 상태가 됩니다.
{: tsCauses}

도구 통합을 다시 구성하십시오.
{: tsResolve}

1. 해당 도구 카드에서 `Setup failed` 메시지 위에 마우스 커서를 올려놓고 **재구성**을 클릭하십시오. 

 ![재구성 단추](images/tool_reconfigure.png)

1. 올바른 구성 매개변수를 사용 중인지 확인하십시오. 올바르지 않은 구성 때문에 오류가 발생한 경우에는 오류 메시지가 표시됩니다. 예: `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`. 도구 통합에 대한 설정을 업데이트하고 **통합 저장**을 클릭하십시오. 
1. 통신 문제점 때문에 오류가 발생한 경우에는 **통합 저장**을 클릭하여 다시 시도하십시오. 



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
