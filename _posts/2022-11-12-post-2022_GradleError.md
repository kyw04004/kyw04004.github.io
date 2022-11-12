---
title: IntelliJ Gradle 인식 안될 때
categories:
- Spring
excerpt: "에러 해결 정리글입니다. "
feature_text: |
  ## SpringBoot
  에러해결
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### 문제
- 해당 프로젝트에서 Gradle 인식이 안됨
- 다른 프로젝트에서 Maven이나 Gradle이 정상 동작했음
- 자바 버전을 바꾸고 빌드툴을 바꾸면서 인텔리제이 설정을 지속적으로 바꾸어서 <br/> 문제가 생겼나 싶어 인텔리제이 설정 초기화도 해보았으나 문제가 해결안되었음.

    <br/>

#### 해결 방법
-  첫 번째, .idea 삭제해보고 인텔리제이 재부팅
	- .idea를 삭제하면 해당 프로젝트에 인텔리제이 설정이 삭제되어 import를 다시 한다고 함.
- 두 번째, edit configurations에서 메인 클래스 add 해보기
-  세 번째, build.gradle 파일에서 마우스 우클릭 rink Gradle Project 해보기
	- 다른 블로그에서는 위에 방법으로 하라고 했으나 나는 이걸로 해결되었음

   <br/>

### 레퍼런스
[인프런 게시판](https://www.inflearn.com/questions/272493) <br/>
[하이데거의 공부개발기록](https://hi-degger.tistory.com/26)

