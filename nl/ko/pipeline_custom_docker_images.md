---

Copyright:
  years: 2018
lastupdated: "2018-4-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# 사용자 정의 Docker 이미지에 대한 작업
{: #custom_docker_images}

파이프라인 기본 이미지는 빌드의 모든 요구사항을 지원하지는 않을 수 있습니다. 예를 들어, 노드, Java 또는 다른 도구의 버전에 대해 보다 세분화된 제어가 필요할 수 있습니다. 환경을 설정하기 위해 일련의 새 패키지를 설치하고 `PATH`와 같은 환경 변수를 주의깊게 구성하는
파이프라인 작업에 첫 번째 단계를 포함시킴으로써 이 문제를 해결할 수 있습니다. 그러나 더 나은 접근 방법은 작업의 기본으로 "사용자 정의 Docker 이미지" 실행에 대한 파이프라인의 지원을 사용하는 것입니다. 

빌드, 테스트 또는 배치 작업 유형을 사용 중이든 사용자 정의 Docker 이미지 하위 유형을 선택하여 실행할 스크립트를 지정하고 사용하도록 Docker 이미지 이름을 제공할 수 있습니다. 예를 들어, 다음 옵션을 사용하여 Maven 3.5.3 및 IBM Java로 빌드 작업을 실행하십시오. 

 ![사용자 정의 이미지를 사용하는 Maven 빌드](images/custom-image-maven-build.png)


## Docker 이미지 이름 지정
{: #docker_image_name}

사용자 정의 Docker 이미지 작업의 Docker 이미지 이름은 이미지 이름이 Docker CLI와 작동하는 동일한 방식으로 작동하도록 설계되었습니다. Docker 이미지 이름의 형식은 `[repository][:][tag]`입니다. 예를 들어, `docker run maven:3.5.3-ibmjava`의 경우 Docker 이미지는 `maven:3.5.3-ibmjava`이며 여기서 `maven`은 저장소이며 `3.5.3-ibmjava`는 태그입니다. 사용할 수 있는 Docker 이미지 이름에 대한 제한사항은 없습니다. 올바른 Docker 이미지는 모두 작동합니다. 

**팁**: **Docker 이미지 이름** 필드가 채워지지 않은 경우 표준 파이프라인 기본 이름이 사용됩니다.  

기본적으로 [Docker 허브 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://hub.docker.com/){: new_window}의 저장소가 검색됩니다. IBM Cloud 레지스트리와 같은 다른 Docker 레지스트리를 사용하는 경우 전체 DNS 이름을 사용할 수 있습니다. 또한 Docker 허브의 이미지에 대한 완전한 이름을 사용할 수 있습니다. (예: `registry.hub.docker.com/library/maven:3.5.3-ibmjava`)

Docker 이미지에 대한 `tag`는 선택사항입니다. 태그를 지정하지 않는 경우 기본적으로 `latest`로 설정됩니다. 기본값 `latest`는 저장소 소유자가 관리해야 하는 태그 이름입니다. 이 Docker 이미지가 시간 순서대로 최신 이미지라는 것을 의미하지 않습니다. 

Docker 허브에서 대규모의 저장소 커뮤니티를 찾을 수 있습니다. IBM은 IBM Cloud 팀이 [https://hub.docker.com/u/ibmcom/ ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://hub.docker.com/u/ibmcom/){: new_window}에서 사용하는 많은 공용 저장소를 호스팅합니다. `ibmcom/ibmjava` 및 `ibmcom/ibmnode` 저장소는 빌드하는 데 유용합니다.  

## 개인용 이미지 레지스트리 사용
{: #private_image_registry}

인증이 필요한 개인용 레지스트리를 사용 중인 경우 `DOCKER_USERNAME` 및 `DOCKER_PASSWORD`의 두 가지 추가 단계 환경 특성을 설정해야 합니다. `DOCKER_PASSWORD`를 마스킹하기 위해 보안 특성을 사용할 수 있습니다. 이미지를 가져오기 전에 사용자 정의 Docker 이미지 작업은 사용자 이름 및 비밀번호 신임 정보를 사용하여 `docker login`을 완료합니다.

대부분의 레지스트리의 경우 제공된 사용자 이름 및 비밀번호를 사용할 수 있습니다. IBM Cloud Registry를 사용하여 개인용 이미지를 저장하는 경우 인증을 위해 플랫폼 API 키를 사용해야 합니다.  

1. [플랫폼 API 키를 요청 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/iam/#/apikeys){: new_window}하고 키를 저장하십시오.  
1. `DOCKER_USERNAME`에 `iamapikey`를 사용하고 `DOCKER_PASSWORD`에 대해 저장한 플랫폼 API 키를 사용하여 두 가지 단계 환경 특성을 작성하십시오.

 ![IBM Cloud 레지스트리 신임 정보](images/custom-image-private-repository.png)


## 스크립트 지정
{: #specify_script}

사용자 정의 Docker 이미지 작업의 **스크립트** 블록을 사용하여 태스크 폴더에서 실행하는 스크립트 파일을 작성할 수 있으며
이 스크립트는 정규 파이프라인 작업의 작동 방법과 유사합니다.  

**중요**: Docker 이미지의 Dockerfile의 `ENTRYPOINT` 및 `CMD`는 대체되며 호출되지 않습니다. 일부 경우 스크립트에 초기화 단계를 추가해야 할 수 있습니다. 

사용자 정의 Docker 이미지 작업을 사용하면 스크립트를 실행하는 방법에 대한 유연성이 높아질 수 있으며 특히 명령 해석기를 제어할 수 있습니다. 일반적으로 스크립트의 첫 번째 행이 `#!` 및 명령 해석기의 이름으로 시작하는 경우 해당 항목은 작업에서 명령을 실행하는 데 사용됩니다. 명령 해석기를 지정하지 않은 경우 Docker 이미지의 기본 쉘이 사용됩니다. 보통 `#!/bin/bash` 또는 `#!/bin/sh`가 사용됩니다. 적합한 Docker 이미지를 지정하는 경우 `awk`, `node` 및 `ruby`에 대한 이미지 명령 해석기도 작동합니다. 
