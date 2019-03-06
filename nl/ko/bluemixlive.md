---



copyright:
  years: 2015，2019
lastupdated: "2019-2-1"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}


Node.js 애플리케이션을 빌드 중인 경우 {{site.data.keyword.Bluemix}} Live Sync를 사용하여 수동 재배치 없이 {{site.data.keyword.Bluemix_notm}}에서 애플리케이션 인스턴스를 신속하게 업데이트하고 개발할 수 있습니다.   
{: shortdesc}

변경할 경우 실행 중인 {{site.data.keyword.Bluemix_notm}} 애플리케이션에서 변경사항을 즉시 확인할 수 있습니다. {{site.data.keyword.Bluemix_notm}} Live Sync는 
<!--from both the command line and -->
Eclipse Orion Web IDE(Web IDE)에서 작동합니다. {{site.data.keyword.Bluemix_notm}} Live Sync를 사용하여 Node.js에 작성된 애플리케이션을 디버그할 수 있습니다.  

{{site.data.keyword.Bluemix_notm}} Live Sync는 두 가지 기능으로 구성됩니다.
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**Live Edit**

{{site.data.keyword.Bluemix_notm}}에서 실행되는 Node.js 애플리케이션을 편집하여 브라우저에서 바로 테스트할 수 있습니다. Web IDE에서 변경한 사항은 애플리케이션의 파일 시스템으로 즉시 전파됩니다.  

**Debug**  

Node.js 애플리케이션이 Live Edit 모드에 있는 경우 쉘로 전환하여 디버그할 수 있습니다. 노드 검사기 디버거를 사용하여 코드 동적 편집, 중단점 삽입, 코드 스텝 스루, 런타임 다시 시작 등을 수행할 수 있습니다.  


##Live Edit
{: #live-edit}

{{site.data.keyword.Bluemix_notm}}에서 실행되는 Node.js 애플리케이션을 빌드 중인 경우 {{site.data.keyword.Bluemix_notm}} Live Sync의 Live Edit 기능으로 애플리케이션 인스턴스를 신속하게 업데이트할 수 있습니다. Live Edit는 Web IDE에서만 사용할 수 있습니다. Live Edit를 사용하여 재배치하지 않고 데스크탑에서와 같이 개발할 수 있습니다.

Live Edit는 Node.js 애플리케이션에서만 지원됩니다.

Eclipse Orion Web IDE(Web IDE)의 실행 표시줄에서 **Live Edit**를 클릭하십시오.

![Live Edit가 포함된 실행 표시줄의 이미지](images/bluemix-live-sync-light.png)

Live Edit를 사용하여 {{site.data.keyword.Bluemix_notm}}에서 실행되는 Node.js 애플리케이션에 대한 변경사항을 신속하게 미리보십시오. Live Edit를 켠 상태에서 코드를 업데이트하는 경우 웹 애플리케이션의 브라우저 창을 새로 고치면 변경 후 몇 초 이내에 변경사항이 적용되어 표시됩니다.

{{site.data.keyword.Bluemix_notm}} Live Sync의 Live Edit 기능 사용에 대한 튜토리얼은 [Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop, debug, and deploy your app ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window}을 참조하십시오.

Web IDE에서 변경한 파일은 {{site.data.keyword.Bluemix_notm}}의 애플리케이션에 자동으로 재배치됩니다. 노드 애플리케이션을 다시 시작해야 하는 경우 실행 표시줄에 있는 **다시 시작** 단추를 클릭하십시오.

{{site.data.keyword.Bluemix_notm}} Live Sync의 Live Edit 기능을 사용할 때, 보다 일관된 경험을 위해서 256MB의 추가 메모리가 필요함에 따라 추가됩니다.
{: tip}

## {{site.data.keyword.Bluemix_notm}} Live Debug
{: #live-debug}

{{site.data.keyword.Bluemix_notm}} Live Sync Debug는
[노드 검사기![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/node-inspector/node-inspector){:new_window}를 사용하여
Debug 기능을 제공할 수 있습니다. Node.js의 이후 버전에 노드 검사기가 포함되지 않기 때문에 디버거를 사용하려면 Node의 버전 4를 사용해야 합니다.

{{site.data.keyword.Bluemix_notm}} Live Edit가 Node.js 앱에 사용되는 경우 {{site.data.keyword.Bluemix_notm}} Live Debug에 액세스할 수 있습니다.  

{{site.data.keyword.Bluemix_notm}}에서 앱을 제공하는 동안 Debug 기능을 사용하여 코드 편집, 중단점 삽입, 코드 스텝 스루, 런타임 다시 시작 등을 동적으로 수행할 수 있습니다. 또한 Agile 방식으로 앱을 점진적으로 개발하는 중에 대규모의 {{site.data.keyword.Bluemix_notm}} 서비스 목록에서 서비스를 선택할 수 있습니다.

{{site.data.keyword.Bluemix_notm}} Live Debug에는 다음과 같은 기능이 포함되어 있습니다.

* 애플리케이션 런타임 제어
* [노드 검사기![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/node-inspector/node-inspector){:new_window}를 사용하여 디버그
* 쉘 액세스

### 애플리케이션 런타임 제어 {: #app-runtime}

애플리케이션 런타임 제어를 사용하여 Debug 기능을 통해 시작 시 앱의 상태를 검사할 수 있습니다. 이 기능은 시작 시 오류가 발생한 앱의 문제점을 해결할 때 유용합니다.

앱을 개발하는 중에 다음 조치 중에서 선택할 수 있습니다.

* 앱을 빠르게 다시 시작합니다.
* 앱 코드 실행 전에 앱을 일시중단합니다.

로그인하면 {{site.data.keyword.Bluemix_notm}} Live Debug 페이지가 열립니다.

### Debug {: #debug}

**제한사항:** Google Chrome 및 Node 4가 필요합니다.

Debug에는 다음과 같은 기능이 포함되어 있습니다.  
* 특정 행에서 실행을 일시정지하도록 앱 코드에 중단점을 설정합니다.
  중단점이 기본 프로그램에 지원되지 않지만 시작점에는 지원됩니다.
  {: tip}
* 특정 기준이 충족되는 경우에만 실행을 일시정지하도록 중단점 조건을 편집합니다.
* 로컬 변수 및 필드의 상태를 검사합니다.
* `console.log()` 호출의 디버그 출력을 즉시 표시합니다. 이 조치는 cf 로그를 모니터링하는 것보다 빠릅니다.
* 기본 제공 소스 편집기를 사용하여 실행 중인 앱 코드를 임시적으로 즉시 변경합니다.

### 쉘 {: #shell}

이 도구는 앱이 실행 중인 컨테이너에 대한 쉘 액세스를 제공합니다. 이 터미널을 사용하면 진단 쉘 명령을 원격으로 실행하여 앱을 관리할 수 있습니다. Node.js의 모든 버전은 쉘 기능을 지원합니다.

표준 Linux 명령(예: **top**, **ps** 및 **kill**)을 사용하여 인스턴스 내에서 메모리 및 CPU 사용량을 모니터하십시오.

### {{site.data.keyword.Bluemix_notm}} Live Debug를 사용하도록 앱 설정 {: #configure_app_debug}

1. {{site.data.keyword.Bluemix_notm}} Live Debugger는 노드 검사기를 사용합니다. Node 버전 4를 사용해야 하며 빌드팩이 앱 시작 명령을 발견하도록 설정해야 합니다. 시작 명령은 manifest.yml 파일에 설정되는 것이 아니라 빌드팩에서 자동 발견되어야 합니다.

   {{site.data.keyword.Bluemix_notm}} Live Debug를 지원하는 `package.json` 파일은 다음과 같습니다.

  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. 메모리를 늘리십시오.  

    a. 앱 `manifest.yml` 파일에서 메모리 속성에 지정되는 값에 128MB 이상을 추가하십시오.

{{site.data.keyword.Bluemix_notm}} Live Debug가 설치된 후 디버그 도구를 사용할 수 있습니다.

앱을 푸시한 후 `https://_app-host.mybluemix.net_/bluemix-debug/manage`으로 이동하여 {{site.data.keyword.Bluemix_notm}} 디버그 사용자 인터페이스에 액세스하십시오. 인증하도록 프롬프트가 표시되는 경우 IBM ID 사용자 이름 및 비밀번호 또는 일회성 패스코드를 입력하십시오.    

Debugger를 초기화하는 데 몇 분 정도 걸릴 수 있습니다.
{: tip}

### 앱 구성 복원 및 {{site.data.keyword.Bluemix_notm}} Live Debug 사용 안함 {: #restore_live_debug}

1. 앱의 원래 Node.js 버전, 시작 명령 및 메모리 값을 복원하십시오.

2. 앱을 푸시하십시오.
