---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-11"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# {{site.data.keyword.contdelivery_short}}의 문제점 해결
{: #troubleshoot-cd}

{{site.data.keyword.contdelivery_full}} 사용 중에 발생할 수 있는 일반 문제점에는 GitHub 인증, 파이프라인 작성, 도구 통합 구성 또는 Cloud Foundry 문제가 포함됩니다. 많은 경우에는 몇 가지 간단한 단계에 따라 이러한 문제점을 해결할 수 있습니다.
{:shortdesc}

## GitHub 도구 통합을 내 도구 체인에 추가하려고 시도했습니다. 도구 통합이 왜 추가되지 않습니까?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

{{site.data.keyword.Bluemix_notm}}에 사용자의 GitHub 계정에 액세스할 수 있는 권한이 부여되도록 사용자에게 GitHub에 대한 권한이 부여되어야 합니다. 

GitHub 도구 통합이 도구 체인에 추가되지 않았습니다.
{: tsSymptoms}

{{site.data.keyword.Bluemix_notm}}에 GitHub 계정에 액세스할 권한이 없는 경우 도구 통합이 도구 체인에 추가되지 않습니다.
{: tsCauses}

도구 체인을 작성하는 동안 GitHub 도구 통합을 구성 중인 경우 GitHub에 권한을 부여하려면 다음 단계를 수행하십시오.
{: tsResolve}

  1. 구성 가능한 통합 섹션에서 **GitHub**를 클릭하십시오.
  1. {{site.data.keyword.Bluemix_notm}} 퍼블릭에 도구 체인을 작성 중이고 GitHub에 액세스할 권한이 {{site.data.keyword.Bluemix_notm}}에 없으면 **권한 부여**를 클릭하여 GitHub 웹 사이트로 이동하십시오.
  1. 활성 GitHub 세션이 없으면 로그인을 요구하는 프롬프트가 표시됩니다. **애플리케이션에 권한 부여**를 클릭하여 {{site.data.keyword.Bluemix_notm}}에서 사용자의 GitHub 계정에 액세스할 수 있도록 허용하십시오.

이미 도구 체인이 있으면 GitHub 도구 통합의 구성을 업데이트하십시오.

 1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
 1. GitHub 카드에서 메뉴를 클릭하고 **구성**을 클릭하십시오.
 1. 구성 설정을 업데이트하여 GitHub에 액세스할 수 있도록 {{site.data.keyword.Bluemix_notm}}에 권한 부여하십시오. **권한 부여**를 클릭하여 GitHub 웹 사이트로 이동하십시오. 활성 GitHub 세션이 없으면 로그인을 요구하는 프롬프트가 표시됩니다. **애플리케이션에 권한 부여**를 클릭하여 {{site.data.keyword.Bluemix_notm}}에서 사용자의 GitHub 계정에 액세스할 수 있도록 허용하십시오.
 1. 설정 업데이트를 완료하면 **통합 저장**을 클릭하십시오.
 

## 한 지역의 내 도구 체인에 있는 {{site.data.keyword.gitrepos}} 도구 통합을 다른 지역의 도구 체인에서 사용할 수 없는 이유는 무엇입니까?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

{{site.data.keyword.gitrepos}}의 인스턴스를 여러 지역에 걸쳐 사용할 수는 없습니다. 

내 도구 체인에 {{site.data.keyword.gitrepos}} 도구 통합을 추가하려고 시도하면 다음 오류 메시지가 수신됩니다.
{: tsSymptoms}

`Repository URL is not valid. The repository must be on {local GitLab URL}.`

여기서 `{local GitLab URL}`은 도구 체인이 있는 지역의 {{site.data.keyword.gitrepos}} 도구 통합의 URL입니다. 
   
{{site.data.keyword.gitrepos}}는 실행 중인 지역에 있는 {{site.data.keyword.contdelivery_short}} 서비스와 밀접히 통합되어 있으므로 {{site.data.keyword.gitrepos}}의 인스턴스를 여러 지역에 걸쳐 사용할 수는 없습니다.
{: tsCauses}

{{site.data.keyword.gitrepos}} 도구 통합을 작성하는 대신 일반 GitLab 통합을 작성한 후 이 통합을 사용하여 다른 지역에 있는 {{site.data.keyword.gitrepos}} 저장소를 가리키십시오.
{: tsResolve}

1. DevOps 대시보드의 도구 체인 페이지에서 이 통합을 추가할 도구 체인을 클릭하십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭하고 **개요**를 클릭하십시오.
1. **도구 추가**를 클릭하십시오.
1. 도구 통합 섹션에서 **GitLab**을 클릭하십시오.
1. 사용할 GitLab 서버를 클릭하십시오. 액세스할 저장소가 있는 GitLab 서버가 목록에 표시되지 않는 경우에는 사용자 정의 서버를 추가하십시오. 

 a. **사용자 정의 서버 추가**를 클릭하십시오. 

 b. 서버의 이름을 입력하십시오. 이 서버 이름은 사용 가능한 GitLab 서버의 목록에 표시됩니다. 
 
 c. 사용자 정의 GitLab 서버의 루트 URL을 입력하십시오. 
 
 d. 사용자 정의 GitLab 서버의 개인 액세스 토큰을 입력하십시오. 개인 액세스 토큰이 없는 경우에는 [작성하십시오](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat). 
 
 e. **사용자 정의 통합 저장**을 클릭하십시오. 
 
1. GitLab 저장소가 있으며 이를 사용하려면 저장소 유형에 대해 **기존**을 클릭하고 URL을 입력하십시오.
1. 새 GitLab 저장소를 사용하려는 경우, 해당 저장소의 이름을 입력하고 복제하거나 분기시킬 저장소의 URL을 입력하며 저장소 유형을 선택하십시오.

 a. 빈 저장소를 작성하려면 **새로 작성**을 클릭하십시오.

 b. GitLab 저장소의 사본을 작성하려면 **복제**를 클릭하십시오.

 c. 가져오기 요청을 통해 변경사항을 제공할 수 있도록 GitLab 저장소를 분기하려면 **분기**를 클릭하십시오.

1. 서버에 새 개인용 저장소를 작성하려는 경우 **이 저장소를 개인용으로 설정** 선택란을 선택 취소하십시오.
1. 문제 추적에 GitLab Issues를 사용하려면 **GitLab Issues 사용** 선택란을 선택하십시오.
1. 커미트의 태그와 주석 및 커미트에서 참조하는 문제의 레이블과 주석을 작성하여 코드 변경사항의 배치를 추적하려면 **코드 변경사항의 배치 추적** 선택란을 선택하십시오. 자세한 정보는 [Track where your code is deployed with toolchains![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}를 참조하십시오.
1. **통합 작성**을 클릭하십시오.

GitLab 도구 통합을 구성하는 데 대한 자세한 정보는 [GitLab 구성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)을 참조하십시오. 


## 다른 지역의 개인용 저장소를 사용하는 템플리트로부터 도구 체인을 작성할 수 없는 이유는 무엇입니까?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

사용하고 있는 도구 체인 템플리트가 개인용 {{site.data.keyword.gitrepos}} 저장소를 참조합니다. 

{{site.data.keyword.gitrepos}}는 지역별로 고유합니다. 템플리트로부터 도구 체인을 작성하고 개인용 저장소가 없는 지역을 대상으로 지정하려고 시도하면 Git 통합 설정이 실패합니다.
{: tsSymptoms}
   
특정 지역의 도구 체인에 {{site.data.keyword.gitrepos}} 저장소를 추가하면 사용자의 IBM ID가 해당 지역의 GitLab에 대한 액세스 권한을 사용자에게 부여하는 GitLab 사용자 이름에 맵핑됩니다. 사용자의 GitLab 사용자 이름은 모든 지역에서 동일하게 표시되지만, 각 지역에는 서로 별도의 GitLab 설치가 있으므로 각 지역의 연관된 GitLab 사용자는 서로 다릅니다. GitLab 사용자 이름이 동일하게 표시되는 경우에도 다른 지역의 GitLab 사용자에 대한 액세스 권한은 도구 체인에 자동으로 부여되지 않습니다.
{: tsCauses}

다른 {{site.data.keyword.Bluemix_notm}} 지역을 포함, 어디서든 액세스할 수 있도록 {{site.data.keyword.gitrepos}} 저장소를 공용으로 설정하십시오.
{: tsResolve}

저장소가 반드시 개인용이어야 하는 경우 저장소 소유자는 소스 저장소가 있는 GitLab 서버에서 [개인 액세스 토큰](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat)을 작성하여 이에 대한 액세스 권한을 부여할 수 있습니다. 도구 체인 작성 중에 컨텐츠를 복제하려는 경우에는 개인용 저장소에 대한 액세스 권한만 있으면 됩니다. 개인 액세스 토큰은 수명을 제한(1일 후 만료 등)할 수 있도록 만료 날짜를 사용하여 작성할 수 있습니다.  

개인 액세스 토큰을 확보한 후에는 URL을 작성하여 다른 지역에서 저장소에 액세스할 수 있습니다. 도구 체인을 구성하는 중에, 사용자의 사용자 이름 및 액세스 토큰을 사용하도록 **소스 저장소 URL** 필드의 저장소 URL을 업데이트하십시오. 

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

여기서 `user`는 사용자의 GitLab 사용자 이름이고, `XXXXXXX`는 액세스 토큰이며 [`group` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window}은 저장소가 저장된 그룹이고, `node-hello-world`는 저장소 이름입니다. 

사용자의 GitLab 저장소가 GitLab 그룹 내에 없는 경우 `group`의 값은 사용자 이름과 동일합니다.
{: tip}


## 내 {{site.data.keyword.gitrepos}} 저장소를 https를 통해 복제할 수 없는 이유는 무엇입니까?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Git 오퍼레이션을 수행하려면 개인 액세스 토큰 또는 SSH 키를 사용해야 합니다. 

명령행에서 https를 사용하여 저장소를 푸시하거나 복제하려 시도했으나 올바른 비밀번호를 입력했음에도 인증이 되지 않습니다.
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}}는 명령행의 사용자 이름 및 비밀번호를 사용하는 Git 인증을 지원하지 않는 싱글 사인온 메커니즘을 사용합니다.
{: tsCauses}

복제 또는 푸시와 같은 Git 오퍼레이션을 수행하려면 개인 액세스 토큰 또는 SSH 키를 사용해야 합니다. 개인 액세스 토큰 또는 SSH 키를 작성하는 데 대한 자세한 정보는 [시작하기 튜토리얼](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)을 참조하십시오.
{: tsResolve}

## SSH를 사용하여 {{site.data.keyword.gitrepos}} 저장소를 복제하려고 시도하면 인증하라는 프롬프트가 표시되는 이유는 무엇입니까?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

사용자의 개인용 SSH 키의 위치 또는 권한에 문제가 있거나, Git 명령행이 {{site.data.keyword.gitrepos}}에 인증하는 데 사용자의 개인용 SSH 키를 사용하고 있지 않을 수 있습니다. 

{{site.data.keyword.gitrepos}} 사용자 인터페이스를 통해 내 SSH 공개 키를 추가했습니다. SSH를 사용하여 저장소를 복제하려고 시도하면 비밀번호 또는 보안 코드에 대한 프롬프트가 표시되거나, 인증이 실패했음을 나타내는 오류 메시지가 표시됩니다.
{: tsSymptoms}
   
다음 SSH 문제는 모두 인증에 대한 프롬프트를 표시하거나 오류 메시지를 표시할 수 있습니다.
{: tsCauses}

* Git 명령행이 {{site.data.keyword.gitrepos}}에 인증하는 데 사용자의 개인용 SSH 키를 사용하고 있지 않습니다. 

* 개인용 SSH 키가 기본 ~/.ssh/id_rsa 위치에 없습니다. 

* 개인용 SSH 키에 올바른 권한(600)이 없습니다. 


이 문제를 해결하려면 다음 방법을 사용하십시오.
{: tsResolve}

* 기본 개인용 SSH 키 위치를 사용하는 경우에는 ~/.ssh/ 폴더 및 ~/.ssh/id_rsa 개인 키 파일에 대한 권한을 확인하십시오. 권한이 너무 광범위한 경우에는 기본적으로 SSH가 개인 키를 사용하지 않습니다. ~/.ssh/ 폴더에 대한 권한이 700으로 설정되었으며 ~/.ssh/id_rsa 폴더에 대한 권한이 600으로 설정되었는지 확인하십시오. 

* 개인 키가 기본 위치에 있지 않은 경우에는 다음 명령을 사용하여 환경 변수에서 이를 지정하십시오. 

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* 연결 정보를 사용하여 이 문제를 디버그하려면 `GIT_SSH_COMMAND` 환경 변수에 -v 또는 -vvv 플래그를 추가하십시오. 

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## 이메일을 통해 내 GitLab 프로젝트에 사용자를 추가하려 시도했으나 해당 사용자가 초대를 수신하지 못했습니다. 이들을 내 프로젝트에 추가하는 방법은 무엇입니까?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

초대가 해당 사용자의 이메일에 의해 차단되었을 수 있습니다. 

{{site.data.keyword.gitrepos}}에 나열된 이메일을 사용하여 내 GitLab 프로젝트에 사용자를 초대했으나 해당 사용자가 이메일을 수신하지 못했습니다.
{: tsSymptoms}
   
이메일이 스팸 필터에 의해 해당 사용자의 받은 편지함로부터 차단되었을 수 있습니다.
{: tsCauses}

다음 방법을 사용하여 이 문제점을 해결할 수 있습니다.
{: tsResolve}

* 이메일 스팸 폴더를 확인하여 이메일 초대가 스팸으로 표시되어 있는지 판별하십시오. 이메일은 noreply@ 주소로부터 발송됩니다. 이 주소의 이메일을 허용하도록 스팸 필터를 업데이트하십시오. 

* 해당 사용자가 제어할 수 없는 회사 스팸 필터가 이메일을 차단하고 있는지 조사하십시오. 해당 사용자에게 {{site.data.keyword.gitrepos}} 사용자 인터페이스에 로그인하여 자신의 사용자 ID를 전송하도록 요청하십시오. 이 사용자 ID를 사용하여 해당 사용자를 GitLab 프로젝트에 추가할 수 있습니다. 


## 작성 중인 템플리트로부터 도구 체인을 작성할 때 파이프라인이 올바르게 작성되지 않는 이유는 무엇입니까? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

pipeline.yaml 정의의 오류로 인해 파이프라인에서 작업 및 단계와 같은 리소스가 누락되었을 수 있습니다. 

작성하고 있는 템플리트로부터 도구 체인을 작성하려고 시도하면 파이프라인 페이지에서 다음 오류 메시지가 수신됩니다.
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

일반적으로 이 문제는 pipeline.yaml 정의의 오류로 인해 발생합니다.
{: tsCauses}
   
다음 방법을 사용하여 이 오류를 디버그할 수 있습니다.
{: tsResolve}

* 파이프라인 사용자 인터페이스를 사용하여, 현재 템플리트로 빌드하려고 시도 중인 파이프라인을 복제하는 예제 파이프라인을 작성하십시오. 파이프라인 URL에 `/yaml`을 추가하여, 명백한 차이점을 찾기 위해 사용할 수 있는 유사한 pipeline.yaml 파일을 생성하십시오. 예를 들면 `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`과 같습니다. 

* 명령행 모드 도구 체인 작성 메커니즘을 사용하십시오. **도구 체인 작성** 페이지에서 디버거를 열고 `window.Testflags = {nocreate: 1}` 표현식을 평가하십시오. 이 모드에서 **도구 체인 작성**을 클릭하는 경우에는 도구 체인이 작성되지 않습니다. 대신, API에 전달되는 정보가 검토할 수 있도록 콘솔에 리턴됩니다. 


## 내 도구 체인에 대해 도구 통합을 구성했습니다. 왜 구성되지 않습니까?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

설정 프로세스 중에 오류가 발생하거나 도구 체인과 도구 간의 통신이 올바르게 완료되지 않은 경우에는 구성이 실패합니다. 

도구 체인의 도구 통합을 추가 및 구성하고 나면 설정이 실패했음을 나타내는 오류 메시지가 표시됩니다.
{: tsSymptoms}

도구 통합을 추가하는 경우, 도구 체인은 도구 통합에 의해 표시된 도구와 통신하여 필수 리소스를 프로비저닝하고 이를 도구 체인과 연관시킵니다. 설정 프로세스 중에 오류가 발생하거나 도구 체인과 도구 간의 통신이 제대로 완료되지 않은 경우, 도구 통신은 오류 상태가 됩니다.
{: tsCauses}

 ![설정 실패 오류](images/tool_setup_failed.png)

다음을 수행하여 다시 도구 통합을 구성하도록 시도할 수 있습니다.
{: tsResolve}

1. 해당 도구 카드에서 `Setup failed` 메시지 위에 마우스 커서를 올려놓고 **재구성**을 클릭하십시오.

 ![재구성 단추](images/tool_reconfigure.png)

1. 올바른 구성 매개변수를 사용 중인지 확인하십시오. 올바르지 않은 구성 때문에 오류가 발생한 경우에는 오류 메시지가 표시됩니다. 예: `The integration could not be set up. Check the settings and try again. Reason: Invalid api_key:fakeKey`. 도구 통합에 대한 설정을 업데이트하고 **통합 저장**을 클릭하십시오.
1. 통신 문제점 때문에 오류가 발생한 경우에는 **통합 저장**을 클릭하여 다시 시도하십시오.


## {{site.data.keyword.contdelivery_short}}를 Cloud Foundry 조직에 추가할 수 없는 이유는 무엇입니까?
{: troubleshoot-resource_groups}
{: troubleshoot}

더 이상 Cloud Foundry 조직에 {{site.data.keyword.contdelivery_short}} 서비스의 인스턴스를 작성할 수 없습니다.  

Cloud Foundry 조직에 있는 도구 체인에 대한 도구 체인 페이지에 다음 메시지가 표시됩니다.
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

**서비스 추가**를 클릭해 보면 Cloud Foundry 조직에 {{site.data.keyword.contdelivery_short}}를 작성하는 옵션이 없습니다. 리소스 그룹에만 {{site.data.keyword.contdelivery_short}}를 작성할 수 있습니다. 

서비스 인스턴스에 대해 선호되는 컨테이너가 Cloud Foundry 조직에서 리소스 그룹으로 대체되었습니다. 그러나 Cloud Foundry 조직에 이미 있는 {{site.data.keyword.contdelivery_short}} 인스턴스를 지원하기 위해 Cloud Foundry 조직 내에 도구 체인을 작성하는 것은 여전히 가능합니다.
{: tsCauses}

리소스 그룹에서 도구 체인을 다시 작성한 후 원본 도구 체인을 Cloud Foundry 조직에서 제거하십시오. 또는, Cloud Foundry 조직의 기존 도구 체인을 리소스 그룹으로 마이그레이션하는 방법이 제공될 때까지 이 오류 메시지를 무시할 수도 있습니다.
{: tsResolve}


## `ibmcloud` CLI를 사용하여 도구 체인을 삭제할 수 없는 이유는 무엇입니까?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

현재는 ibmcloud resource CLI를 사용하여 도구 체인을 삭제할 수 없습니다.  

명령행에서 `ibmcloud resource service-instance-delete` 명령을 사용하여 도구 체인을 삭제하려 시도했으나 다음 오류 메시지가 출력되며 명령이 실패합니다.
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

도구 체인은 현재 `ibmcloud resource` CLI를 사용하여 삭제할 수 없는, Cloud 플랫폼의 특수한 리소스 유형입니다.
{: tsCauses}

도구 체인을 삭제하려면 다음 작업을 수행하십시오.
{: tsResolve}

1. DevOps 대시보드의 **도구 체인** 페이지에서 삭제할 도구 체인을 클릭하십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭하십시오.
1. **앱 보기** 옆에 있는 **추가 조치** 메뉴를 클릭하십시오.
1. **삭제**를 클릭하십시오. 도구 체인을 삭제하면 도구 통합이 모두 제거되므로 해당 통합에서 관리하는 리소스를 삭제할 수 있습니다.
1. 도구 체인의 이름을 입력하고 **삭제**를 클릭하여 삭제를 확인하십시오.  


## 커미트하여 저장소에 푸시한 후 Live Edit가 사용 불가능한 이유는 무엇입니까?
{: #troubleshoot-liveedit}
{: troubleshoot}

Eclipse Orion {{site.data.keyword.webide}} 외부에 배치하는 경우에는 Live Edit 모드가 지워집니다. 

명령행 또는 {{site.data.keyword.webide}}에서 변경사항을 커미트하고 푸시한 후 Live Edit가 사용 불가능합니다.
{: tsSymptoms}
   
{{site.data.keyword.webide}} 및 {{site.data.keyword.contdelivery_short}} 파이프라인을 둘 다 포함하는 도구 체인을 작성하는 경우에는 두 도구 통합 모두 사용자의 애플리케이션(앱)을 배치할 수 있습니다. 기본적으로 {{site.data.keyword.webide}} 및 파이프라인은 둘 다 동일한 Cloud Foundry 앱 및 URL을 사용하여 동일한 Cloud Foundry 조직 및 영역에 배치됩니다. {{site.data.keyword.webide}} 외부에 배치하는 경우에는 Live Edit 모드가 지워집니다.
{: tsCauses}

Live Edit를 사용하여 앱의 테스트 버전을 빠르게 개발하려면 {{site.data.keyword.webide}}와 다른 Cloud Foundry 앱, 영역 및 URL에 배치하십시오. 코드 변경이 완료되고 나면 코드를 커미트하고 푸시하여 앱의 프로덕션 버전을 빌드하고 배치하도록 파이프라인을 트리거할 수 있습니다.
{: tsResolve}

1. 실행 표시줄에서 편집할 실행 구성을 선택하십시오. 
2. 영역 및 호스트에 대해 지정된 값을 편집하십시오. 
3. **저장** 및 **종료**를 클릭하십시오. 
4. 실행 표시줄에서 **실행** 단추를 클릭하십시오. Live Edit 단추를 사용으로 설정하려면 여러 번 배치해야 할 수 있습니다. 

Live Edit에 대한 자세한 정보는 [Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit)를 참조하십시오. 


## {{site.data.keyword.webide}} 실행 표시줄에서 "동기화되지 않음"은 무엇을 의미합니까?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

작업공간에 있는 파일 시스템이 동기화되지 않았습니다. 

Live Edit 모드에서 {{site.data.keyword.webide}}는 작업공간의 파일을 실행 중인 Cloud Foundry 앱과 동기화하며, 현재 해당 파일이 동기화되지 않았습니다.
{: tsSymptoms}
   
앱이 {{site.data.keyword.webide}} 외부에서 수정되는 경우에는 작업공간의 파일 시스템이 동기화되지 않을 수 있습니다. {{site.data.keyword.webide}}가 앱으로부터 동기화 상태를 검색할 수 없는 경우에도 파일 시스템이 동기화되지 않을 수 있습니다.
{: tsCauses}

이 상태는 정상 통신이 설정되고 파일이 동기화되고 나면 1 - 2분 후에 사라질 수 있습니다. 그렇지 않은 경우에는 Live Edit 모드가 사용으로 설정된 상태로 앱을 중지한 후 다시 시작하십시오.
{: tsResolve}
