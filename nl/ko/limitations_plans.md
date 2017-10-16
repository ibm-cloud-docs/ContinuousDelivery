---

copyright:
  years: 2016, 2017
lastupdated: "2017-7-24"
---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 플랜 제한사항 및 이용
{: #deliverypipeline_plans}
{: #free_deprecation}

{{site.data.keyword.contdelivery_full}}를 사용하는 것은 {{site.data.keyword.Bluemix_notm}} 플랫폼 또는 기타 호환 가능 PaaS(Platform as a Service) 또는 IaaS(Infrastructure as a Service)에서 애플리케이션의 빌드, 배치, 테스트 및 진행 조작으로 한정됩니다. 

다음 행위가 허용되지만 이에 국한되지는 않습니다. 

* 지원되는 프로그래밍 언어에 대한 아티팩트의 컴파일 및 어셈블리
* 애플리케이션 아티팩트, 구성 및 지원 리소스나 서비스의 자동화된 배치
* 테스트, 유효성 검증, 그리고 개발 프로세스의 결과로서 트리거되는 기타 개발 이벤트-생성 행위

허용되지 않는 이용 행위에는 다음 행위가 포함되지만 이에 국한되지는 않습니다. 

* 일반 컴퓨팅 행위에 대한 작업자 또는 파이프라인 작업의 이용(예: 비트코인 마이닝, 분산 서비스 거부 공격, 그리고 일반 인터넷 사용자 또는 IBM 클라우드 플랫폼 내의 사용자 또는 기타 클라이언트에 대한 악의적이거나 공격적인 행위) 
* 혐오 발언 또는 IBM Business Conduct Guidelines를 위반하는 기타 행위를 조장하는 서비스 또는 사이트에 대한 일반 개발 프로세스의 이용
* {{site.data.keyword.Bluemix_notm}} 또는 기타 사이트에 대한 악의적 침해나 공격에 대한 이벤트 생성 행위의 이용

IBM의 재량에 따라, {{site.data.keyword.contdelivery_short}} 서비스의 허용되는 이용 행위나 [IBM Business Conduct Guidelines ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window}를 위반하는 사용자는 통지 없이 사용이 거부될 수 있습니다. IBM의 재량에 따라, 공격적 행위에 대해 통지를 받은 후에 사용자가 해당 이용 행위를 바로잡은 경우에는 일부 서비스가 복원될 수 있습니다. 그렇지 않으면, 계정이 일시중단되거나 중지될 수 있습니다. 

## Git Repos and Issue Tracking 제한사항
{: #git_limitations}

{{site.data.keyword.gitrepos}}은 GitLab Community Edition에 빌드되어 IBM이 {{site.data.keyword.Bluemix_notm}}에서 호스팅하고 있습니다. 그러나 몇 가지 GitLab 옵션은 사용할 수 없습니다. 

 * {{site.data.keyword.deliverypipeline}}이 {{site.data.keyword.Bluemix_notm}}에 대해 지속적 통합 및 지속적 딜리버리를 제공하기 때문에 GitLab에서 지속적 통합 기능은 지원되지 않습니다. 
 * IBM에서 관리하기 때문에 GitLab 관리자 기능은 사용할 수 없습니다. 
 * {{site.data.keyword.gitrepos}}에 완전하게 액세스할 수 없을 수 있습니다.


## Git Repos and Issue Tracking 사용자 정보 및 컨텐츠
{: #git_projects}

다음 세 가지 유형의 {{site.data.keyword.gitrepos}} 프로젝트가 사용 가능합니다. 

  1. 공용 프로젝트는 모든 사이트 방문자에게 표시됩니다. 공용 프로젝트의 컨텐츠는 프로젝트에 초대되지 않은 경우라도 {{site.data.keyword.contdelivery_short}}에 액세스하는 모든 사용자에게 표시됩니다.  
  2. 개인용 프로젝트는 선택한 사용자에게만 표시됩니다. 프로젝트에 사용자 액세스 권한 부여하기에 대한 세부사항은 [프로젝트 사용자![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}를 참조하십시오. 
  3. 내부 프로젝트는 로그인한 모든 사용자들에게 표시됩니다. {{site.data.keyword.Bluemix_notm}} 계정이 있는 사용자는 해당 프로젝트를 볼 수 있습니다. 

프로젝트의 설정에서 프로젝트 유형을 수정할 수 있습니다. 자세한 정보는 [How to change project visibility![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}를 참조하십시오.

{{site.data.keyword.gitrepos}}을 사용할 때 사용자가 프로젝트에 제공하는 컨텐츠는 그 프로젝트에 지정된 조항 아래에서 라이센스가 부여됩니다. 프로젝트를 작성할 때는 컨텐츠에 적용되는 라이센스를 설명하는 파일을 포함하십시오. 프로젝트에 제공할 때 커미트와 연관된 사용자의 이름 및 이메일 주소가 공개적으로 표시될 수 있습니다. {{site.data.keyword.Bluemix_notm}} 계정과 연관된 이메일 주소가 {{site.data.keyword.gitrepos}} 웹 인터페이스를 통해 커미트를 작성할 때 사용됩니다. 

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
