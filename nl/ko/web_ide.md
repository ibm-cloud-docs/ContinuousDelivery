---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Eclipse Orion Web IDE를 사용하여 개발
{: #web_ide}

Eclipse Orion {{site.data.keyword.webide}}는 브라우저 기반의 개발 환경이며 컨텐츠 지원, 코드 자동 완성 및 오류 검사 기능을 통해 JavaScript, HTML 및 CSS로 웹을 개발할 수 있습니다. {{site.data.keyword.webide}}는 거의 모든 언어에서 작동하며, 대부분의 파일 유형에 대한 구문을 강조표시합니다. 소스 제어는 내장되어 있으며, 사용자는 로컬로 코드를 배치하여 앱을 테스트하고 디버그할 수 있습니다.
{:shortdesc}

특히 {{site.data.keyword.webide}}는 웹에서 구동됩니다. 설치, 관리 및 스케일링이 필요 없습니다. 인터넷이 연결되어 있으면 어디서든 개발할 수 있습니다.

{{site.data.keyword.webide}} 내의 파일에 규제된 데이터를 저장하지 마십시오. 규제된 데이터에 대한 프로시저는 현재 시행되지 않고 있습니다.
{: tip}

## IDE 설정
{: #editorsetup}

{{site.data.keyword.webide}}는 사용자 정의할 수 있으므로 개발 요구사항에 맞는 색상 구성표, 기술 도구 및 설정을 선택할 수 있습니다. 설정을 보고 수정하려면 왼쪽 탐색 사이드바의 **설정** 아이콘 <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="설정 아이콘">을 클릭하십시오.

편집 중에 종종 특정 설정을 변경해야 하는 경우에는 **로컬 편집기 설정** 아이콘 <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="로컬 편집기 설정 아이콘">에서 해당 설정에 바로 액세스할 수 있습니다.

![로컬 편집기 설정](images/webide_local_editor_settings_light.png)

기본적으로 편집기 스타일 및 글꼴 크기 설정은 항상 표시됩니다. 메뉴에 다른 편집기 설정을 포함시키려면 다음 단계를 따르십시오.

1. **로컬 편집기 설정** 아이콘 <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="로컬 편집기 설정 아이콘">을 클릭하십시오.

2. **편집기 설정**을 클릭하십시오.

3. **로컬 편집기 설정** 메뉴에서 설정을 포함하거나 제외하려면 각 설정에 대해 별표를 클릭하십시오.

![편집기 설정 토글](images/webide_editor_settings_toggle_light.png)


## 코드 편집
{: #editcode}

{{site.data.keyword.webide}}에는 두 개의 기본 섹션이 있습니다. 첫 번째 섹션은 트리 구조로 프로젝트 파일을 표시하는 파일 네비게이터입니다. 파일 네비게이터에서 파일 및 폴더를 작성, 이름 바꾸기, 삭제 및 관리할 수 있습니다.

파일 네비게이터에 파일을 업로드하려면 컴퓨터에서 파일 네비게이터로 파일을 끌어 오십시오.
{: tip}

두 번째 섹션은 편집기 분할창입니다. 편집기는 컨텐츠 지원과 구문 유효성 검증을 포함하여 여러 코딩 기능을 제공합니다.

![Web IDE](images/webide_light.png)

### 여러 파일에 대한 작업
1. 동시에 두 개의 파일로 작업하려면 **편집기 분할 모드 변경** 아이콘 <img class="inline" src="images/webide_split_editor_icon_light_small.png"  alt="편집기 분할 아이콘">을 클릭하십시오.
2. 메뉴가 열리면 보기를 선택하십시오.

 보기를 선택한 후 편집기에 파일이 이미 열려 있으면 해당 파일이 양쪽 편집기 보기에 표시됩니다.

 편집기 보기 중 하나에 표시되는 파일을 열거나 변경하려면 다음을 수행하십시오.
 1. 커서를 변경할 편집기 보기로 이동하십시오.
 2. 파일 네비게이터에서 파일을 클릭하십시오.

### 키보드 단축키
{{site.data.keyword.webide}}에서 다수의 명령은 키보드 단축키를 통해 액세스할 수 있습니다.

편집기에서 키보드 단축키 목록을 보려면 **도구** > **키 표시**를 누르십시오. 또는, Alt+Shift+?를 눌러 목록을 볼 수 있습니다(MacOS의 경우 Ctrl+Shift+?). 키 위로 마우스를 이동하고 연필을 클릭하고 새 키 바인딩을 입력하여 단축키를 사용자 정의할 수 있습니다.

## 소스 코드 관리
{: #sourcecontrol}

{{site.data.keyword.webide}}는 소스 코드 관리 도구와 통합됩니다. Git 저장소에 대해 작업하려면 **Git 저장소** 아이콘 <img class="inline" src="images/webide_git_icon_light_small.png"  alt="Git 저장소 아이콘">을 클릭하십시오.  자세한 정보는 [Eclipse Orion Web IDE에서 Git에 대해 작업](/docs/services/ContinuousDelivery/git_web_ide.html#git_web_ide)을 참조하십시오.

## 작업공간에서 앱 배치
{: #deploy}

1. 앱을 배치하려면 실행 표시줄에서 실행 구성을 선택하거나 작성하십시오.
   ![실행 표시줄](images/webide_runbar_light.png)   
1. 배치 아이콘 <img class="inline" src="images/webide_deploy_button_light_small.png"  alt="배치 아이콘">을 클릭하십시오. 작업공간의 현재 컨텐츠와 실행 구성에 정의된 환경을 사용하여 앱의 인스턴스가 배치됩니다.
2. 앱이 배치되면 실행 표시줄을 사용하여 앱을 중지, 다시 시작 또는 디버그하고 로그를 보는 등의 작업을 수행할 수 있습니다.

<table role="presentation">
<tr><td><img src="./images/stop_button.png"  alt="중지 아이콘"></td><td>앱을 중지합니다.</td></tr>
<tr><td> <img src="./images/open_app_url.png"  alt="앱 URL 열기 아이콘"></td><td> 배치된 앱을 엽니다.</td></tr>
<tr><td><img src="./images/view_logs.png"  alt="로그 보기 아이콘"></td><td>배치된 앱의 로그를 봅니다.</td></tr>
<tr><td><img src="./images/open_dashboard.png"  alt="대시보드 열기 아이콘"></td><td>앱의 대시보드를 엽니다.</td></tr>
</table>

Node.js 앱을 개발하는 경우, 라이브 편집 모드를 사용하십시오. <img  src="./images/enable_live_edit.png"  alt="라이브 편집 슬라이더 사용">

<table role="presentation"><tr><td><img src="./images/live_edit_restart.png"  alt="라이브 편집 다시 시작 아이콘"></td><td>라이브 편집 모드를 사용하여 재배치하지 않고 앱을 신속하게 다시 시작합니다.</td></tr>
<tr><td> <img src="./images/debug_icon.png"  alt="디버그 아이콘"></td>
<td>라이브 편집 모드를 사용하여 디버거에 액세스합니다.
</td></tr>
</table>

<!-- 3/6/2016: bl commands don't work with V2/CD
## Editing outside of the {{site.data.keyword.webide}}
{: #editlocal}

To use an editor besides the {{site.data.keyword.webide}}, set up {{site.data.keyword.Bluemix_live}} so that you can work directly with your project files in any tool. {{site.data.keyword.Bluemix_live_notm}} is a command-line application that synchronizes the changes in your local file system with your cloud workspace in {{site.data.keyword.Bluemix_short}}.

### Before you begin

Download and install the [{{site.data.keyword.Bluemix_live_notm}} command-line interface ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://livesyncdownload.ng.bluemix.net){: new_window}.

### Synchronizing your local environment with {{site.data.keyword.Bluemix_notm}}
{: #edit_local_download}

1. Open a command-line window.
2. Sign in to {{site.data.keyword.Bluemix_notm}}:

	```
	bl login
	```
	{: pre}

3. When you are prompted, enter your IBMid and password.
4. View a list of your {{site.data.keyword.Bluemix_notm}} projects:

	```
	bl projects
	```
	{: pre}

4. Synchronize your local environment with your project on {{site.data.keyword.Bluemix_notm}}:

	```
	bl sync projectName
	```
	{: pre}

where `projectName` is your {{site.data.keyword.Bluemix_notm}} app's name.

When you are finished editing, enter `q` to end synchronization.

### Enabling the Desktop Sync feature to edit code locally

The Desktop Sync feature is like Live Edit mode for the command line. You need the Desktop Sync feature to debug on the command line.
1. In another command-line window, enable the Desktop Sync feature:

	```
	cd localDirectory
	bl start
	```
	{: codeblock}

2. Use the launch configuration that you created in the {{site.data.keyword.webide}}. After you select the launch configuration, the Desktop Sync feature is enabled in your local environment. In the command-line window that you just opened, you can view the app's URL, the debug URL, the manage URL, and view the {{site.data.keyword.Bluemix_live_notm}} state.

3. Refresh the browser and verify that you can see the changes that you saved to static files in the local workspace.

### Disabling the Desktop Sync feature

1. In the second command-line window, enter `bl stop`.
2. In the first command-line window, enter `q`.

-->

## 지원 언어
{: #supported_languages}

Eclipse Orion {{site.data.keyword.webide}}는 컨텐츠 지원, 도구 팁, 미리보기, 유효성 검증을 제공하며 JavaScript, HTML, CSS, 마크다운 파일에 대한 구문을 강조표시합니다. 다음 파일 유형에 대한 구문을 강조표시할 수도 있습니다.

<table role="presentation">
<tr>
<td>
<ul><li>Arduino
</li><li>C</li>
<li>C#
</li><li>C++
</li><li>CoffeeScript
</li><li>CSHTML
</li><li>Embedded JavaScript(ejs)
</li><li>Erlang
</li><li>Go
</li><li>HTML 추상 마크업 언어(Haml)
</li><li>Jade
</li><li>Java
</li><li>JSON
</li><li>Less  
</li><li>Lua  
</li><li>Objective-C
</li><li>PHP
</li><li>Python</li></ul>
</td>
<td>
<ul><li>Ruby
</li><li>Sass/SCSS
</li><li>SQL
</li><li>Swift
</li><li>TypeScript
</li><li>Visual Basic(vb)
</li><li>VMHTML
</li><li>XHTML
</li><li>XML
</li><li>XQuery
</li><li>YAML
</li><li>시작 파일 	
</li><li>Dockerfile
</li><li>gitignore
</li><li>git config
</li><li>cfignore
</li><li>properties
</li></ul>
</td>
</tr>
</table>

## 튜토리얼 보기: Eclipse Orion Web IDE
{: #toolchain_tutorials}

[IBM&reg; Cloud Garage Method![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage){:new_window}에 있는 다음 튜토리얼 중 하나를 확인하십시오.

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
