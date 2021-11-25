---
title: Shell script
categories:
- Etc
excerpt: "Shell script 설명과 실습 포스팅입니다. "
feature_text: |
  ## Shell script
  Bash
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

#### 쉘 스크립트란?

- 쉘에게 무슨 명령들을 실행할 지 알려주는 스크립트 파일

  - 쉘이란 사용자와 운영체제 사이의 인터페이스를 제공하는 특수 소프트웨어
  - 사용자로부터 명령어를 입력받아 해석하여 수행해주는 명령어 해석기

- bash shell script가 가장 널리 사용됨 (모든 종류의 유닉스 쉘 스크립트에 관한 실질적인 표준)

- 스크립트 최상단에는 **#!/bin/bash**를 항상 적어두어야 함

- ./파일명 하면 실행됨 (실행안될 시 chmod로 권한 설정)

- .sh 확장자 사용

  

#### 쉘 스크립트를 왜 사용할까?

- 반복되는 작업을 자동화하기 위해 스크립트 형태로 미리 만들어 놓고 실행만 하도록 하기 위함

- 스크립트의 내용을 몰라도 누구나 실행 가능

  

#### 쉘 스크립트 사용 해보기

- 작성자는 평소 데이터베이스 서버와 인텔리제이를 열어 개발을 시작한다. 이 작업을 쉘 스크립트로 자동화 해보겠음

- jobstart라는 이름으로 쉘 스크립트를 작성 (mysql서버 열고 인텔리제이 실행파일 실행하는 스크립트) <br>
  ![스크립트파일생성](https://user-images.githubusercontent.com/56823099/143392221-c2870590-8a5f-467d-829c-334c07b4f1dd.png)

- 실행권한설정 <br>
  ![실행권한](https://user-images.githubusercontent.com/56823099/143392231-dab99ebe-c973-44cc-89a8-c213a3458da1.png)

- 실행 후 화면  <br>
  ![실행성공화면](https://user-images.githubusercontent.com/56823099/143392233-c2282956-1957-4837-a761-e7ed859e7fb4.png)

- 인텔리제이가 열린 것과 데이터베이스 서버의 포트가 열린 것을 확인

  

#### 쉘 스크립트의 장점

- 특별한 툴 없이 개발 가능하고 문법이 쉬워 만들기 쉬움

- 컴파일이 필요 없어 빠름

  

#### 쉘 스크립트의 단점

- 실행되는 각 명령에 대한 잠재적으로 새로운 하부 프로세스의 수많은 필요에 따라 속도가 느려질 수 있음

- 단순 *sh* 스크립트는 다양한 종류의 유닉스, 리눅스, BSD 운영 체제, therof 버전, 시스템 유틸리티와 잘 호환된다는 장점이 있지만 더 복잡한 셸 스크립트는 셸, 유틸리티, 다른 필수 요소 간의 약간의 차이가 많은 경우 실패할 가능성이 있다. [래리 월](https://ko.wikipedia.org/wiki/래리_월)은 다음과 같은 유명한 말을 남겼다: "셸 스크립트보다 셸을 포팅하는 게 더 쉽다"

- 이와 비슷하게, 더 많은 복잡한 스크립트들은 셸 스크립트 언어 자체의 제한 안에서 실행할 수 있다. 이러한 제한 때문에 다양한 셸이 문제를 개선할 목적으로 고품질의 코드와 확장을 기록하기 힘들 수 있음

  

####  쉘 스크립트를 쓰면 안되는 경우

- 리소스에 민감한 작업들, 특히 속도가 중요한 요소일 때(정렬, 해쉬 등등)

- 강력한 산술 연산 작업들, 특히 임의의 정밀도 연산(arbitrary precision)이나 복소수를 써야 할 때(C++이나 포트란을 쓰세요)

- 플랫폼간 이식성이 필요할 때(C를 쓰세요)

- 구조적 프로그래밍이 필요한 복잡한 어플리케이션(변수의 타입체크나 함수 프로토타입등이 필요할 때)

- 업무에 아주 중요하거나 회사의 미래가 걸렸다는 확신이 드는 어플리케이션

- 보안상 중요해서, 여러분 시스템의 무결성을 보장하기 위해 외부의 침입이나 크래킹, 파괴등을 막아야 할 필요가 있을 때

- 서로 의존적인 관계에 있는 여러 콤포넌트로 이루어진 프로젝트

- 과도한 파일 연산이 필요할 때(Bash는 제한적인 직렬적 파일 접근을 하고 , 특히나 불편하고 불충분한 줄단위 접근만 가능)

- 다차원 배열이 필요할 때

- 링크드 리스트나 트리같은 데이타 구조가 필요할 때

- 그래픽이나 GUI를 만들고 변경하는 등의 일이 필요할 때

- 시스템 하드웨어에 직접 접근해야 할 때

- 포트나 소켓 I/O가 필요할 때

- 예전에 쓰던 코드를 사용하는 라이브러리나 인터페이스를 써야 할 필요가 있을 때

- 독점적이고 소스 공개를 안 하는 어플리케이션을 짜야 할 때(쉘 스크립트는 필연적으로 오픈 소스입니다.)

  

#### 배시 쉘 스크립트 문법 참고 블로그

[https://twpower.github.io/131-simple-shell-script-syntax](https://twpower.github.io/131-simple-shell-script-syntax)<br>
[https://www.lesstif.com/lpt/bash-shell-script-programming-26083916.html](https://www.lesstif.com/lpt/bash-shell-script-programming-26083916.html)<br>
[https://blog.gaerae.com/2015/01/bash-hello-world.html](https://blog.gaerae.com/2015/01/bash-hello-world.html)<br>


#### 레퍼런스

[위키피디아](https://ko.wikipedia.org/wiki/%EC%85%B8_%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)<br>
[https://reakwon.tistory.com/136](https://reakwon.tistory.com/136)<br>
[https://wiki.kldp.org/HOWTO/html/Adv-Bash-Scr-HOWTO/why-shell.html](https://wiki.kldp.org/HOWTO/html/Adv-Bash-Scr-HOWTO/why-shell.html)
