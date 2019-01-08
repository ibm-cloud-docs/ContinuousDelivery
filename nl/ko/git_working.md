---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-5"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

IBM에서 호스팅하고 [GitLab Community Edition ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://about.gitlab.com/){:new_window}에서 빌드된 Git 저장소(repo) 및 문제 트래커를 사용하여 사용자의 팀과 협업하고 소스 코드를 관리합니다.
{: shortdesc}

프로젝트에 협업하도록 개인 또는 비즈니스 관계가 있는 사용자만 초대하십시오. 프로젝트에 대한 협업 이외의 목적으로 Git 저장소에 초대를 사용하는 사용자에게는 일시중단되거나 취소된 서비스에 대한 액세스 권한이 있습니다.
{: important}

Git 저장소 내의 파일 또는 문제에 규제된 데이터를 저장하지 마십시오. 규제된 데이터에 대한 프로시저는 현재 시행되지 않고 있습니다.
{: tip}

{{site.data.keyword.gitrepos}} 도구 통합은 코드를 관리하고 다양한 방법으로 협업할 수 있도록 팀을 지원합니다.
   * 코드의 보안을 유지하는 미세 조정된 액세스 제어를 통해 Git 저장소를 관리함
   * 코드를 검토하고 병합 요청을 통해 협업을 개선함
   * 문제 트래커를 통해 문제를 추적하고 아이디어를 공유함
   * 위키 시스템에서 프로젝트를 문서화함

이 도구 통합은 GitLab Community Edition을 기반으로 빌드되며 {{site.data.keyword.Bluemix_notm}} Platform에서 IBM에 의해 호스팅되므로 몇 가지 GitLab 옵션을 사용할 수 없습니다. 예를 들어, Delivery Pipeline은 {{site.data.keyword.Bluemix_notm}}에 대해 지속적 통합 및 지속적 딜리버리를 제공하므로 GitLab의 지속적 통합 기능은 지원되지 않습니다. 또한 IBM에서 관리하므로 관리자 기능은 사용할 수 없습니다.
{: tip}

## 로컬로 {{site.data.keyword.gitrepos}} 사용
{: #git_local}

{{site.data.keyword.gitrepos}}에 저장된 Git 저장소에 로컬로 액세스할 수 있습니다. 로컬에 Git를 설정하는 지시사항은 [Start using Git on the command line![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}을 참조하십시오.

{{site.data.keyword.gitrepos}}는 TLS1.2를 사용하는 HTTPS 연결만 지원합니다. 연결하기 위해 Eclipse를 사용하는 경우, `-Dhttps.protocols=TLSv1.2`를 eclipse.ini 파일에 추가하고 Eclipse를 다시 시작하여 사용자의 Java&trade; 버전에 이 프로토콜을 지정해야 할 수 있습니다.
{: tip}

## {{site.data.keyword.gitrepos}}에 인증
{: #git_authentication}

{{site.data.keyword.Bluemix_notm}} 로그인 및 비밀번호는 웹 브라우저에서 {{site.data.keyword.gitrepos}}를 인증하는 경우에만 사용됩니다. 외부 Git 클라이언트에서 인증하기 위해 {{site.data.keyword.Bluemix_notm}} 사용자 신임 정보를 사용할 수 없습니다.  `clone` 또는 `push` 등의 원격 Git 조작을 완료하려면, 로컬 Git 저장소에서 개인 액세스 토큰 또는 SSH 키를 사용하여 {{site.data.keyword.gitrepos}}을 인증해야 합니다.

### 개인 액세스 토큰 작성
{: #create_pat}

HTTPS를 통해 Git 저장소로 인증하려면 개인 액세스 토큰을 작성해야 합니다.
{: tip}

1. {{site.data.keyword.gitrepos}} 사용자 설정 대시보드의 [액세스 토큰 페이지에서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, 액세스 토큰을 작성하려는 애플리케이션의 이름을 입력하십시오. 예: `Git CLI`
1. 선택사항: 액세스 토큰의 만료 날짜를 선택하십시오.
1. **api** 선택란을 선택하여 api를 범위로 사용하는 개인 액세스 토큰을 작성하십시오.
1. **개인 액세스 토큰 작성**을 클릭하십시오. 나중에 사용할 수 있도록 보안이 유지되는 위치에 액세스 토큰을 기록해 놓으십시오.
1. [계정 페이지에서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, 사용자 이름 변경 섹션에서 {{site.data.keyword.gitrepos}} 사용자 이름을 찾으십시오. 작성하는 개인 Git 저장소에 대한 URL의 첫 번째 세그먼트로 사용자 이름이 표시됩니다.
1. {{site.data.keyword.gitrepos}} 사용자 이름 및 개인 액세스 토큰을 사용하여 외부 Git 클라이언트에서 Git 저장소로 인증하십시오.

자세히 알아보려면 [Personal Access Tokens![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}를 참조하십시오.

### SSH 키 작성  
{:create_ssh }

SSH 키를 작성하려면 [How to create your SSH Keys![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}를 참조하십시오. SSH 인증으로 저장소에 액세스하려면 프록시 및 방화벽에 대한 추가 구성이 필요할 수 있습니다.

자세히 알아보려면 [SSH![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/ssh/README){:new_window}를 참조하십시오.

## 실제 파일 및 저장소 크기 한계
{: #git_limits}

파일 크기는 100MB로 엄격히 제한됩니다. 권장되는 저장소 크기 한계는 1GB입니다. 저장소가 1GB를 초과하면 저장소 크기를 줄여달라는 요청 이메일을 받을 수 있습니다.

## 튜토리얼 보기: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

[IBM&reg; Cloud Garage Method![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage){:new_window}에 있는 다음 튜토리얼 중 하나를 확인하십시오.

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}. 템플리트에서 오픈 도구 체인을 작성하고 이 도구 체인을 사용하여 "Hello World" 앱의 지속적 딜리버리를 제공하는 방법을 알아봅니다.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}. 세 가지 마이크로서비스를 사용하여 템플리트에서 도구 체인을 작성하고 이 도구 체인을 사용하여 온라인 상점의 지속적 딜리버리를 제공하는 방법을 알아봅니다.
