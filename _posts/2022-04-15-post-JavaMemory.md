---
title: Java의 메모리 구조
categories:
- JAVA
excerpt: "Java의 메모리 구조에 대한 포스팅입니다."
feature_text: |
  ## Java's Memory Structure
  JAVA
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### 자바의 메모리 구조
- 모든 자바 프로그램은 JVM을 통해서 실행
- JVM의 런타임 데이터 영역은 크게 5가지로 분류
	+ 런타임 데이터 영역은 JVM의 메모리 영역으로 자바 애플리케이션을 <br> 실행할 때 사용되는 데이터들을 적재하는 영역
	+ 간단한 예시
![image](https://github.com/kyw04004/kyw04004.github.io/assets/56823099/b30c0696-547f-43bc-9a31-9b0e2dd2e8f4)
<br>

#### Method Area (메서드 영역)
- 프로그램을 실행하는데 필요한 공통 데이터 관리
	+ 클래스에 대한 정보와 클래스 변수(static variable) 그리고 상수 풀이 저장되는 영역
	+ 모든 스레드가 공유하는 영역 (프로그램 모든 영역에서 공유)
- 어디서든 접근 가능
- JVM이 종료될 때까지 유지

<br>

#### Heap Area (힙 영역)
- 객체(인스턴스)와 배열이 생성되는 영역 (모든 인스턴스 변수가 저장되는 영역)
- 가비지 컬렉션(GC)이 이루어지는 주요 영역, 더 이상 참조되지 않는 객체는 GC에 의해 제거
- 모든 스레드가 공유하는 영역

<br>

#### Stack Area (스택 영역)
- 메소드가 호출될 때 메소드의 스택 프레임이 저장되는 영역
	+ 스택 프레임이란 스택 영역에 저장되는 메소드의 호출 정보
- 메소드 호출과 관계되는 지역 변수와 매개변수 등을 스택 영역에 저장
- 메소드의 호출과 함께 할당되며, 메소드의 호출이 완료되면 소멸
- 스레드 별로 1개만 생성/사용

<br>

#### PC Register
- 스레드가 시작될 때 생성되며, 생성될 때마다 생성되는 공간으로 스레드마다 하나씩 존재
- 스레드가 어떤 부분을 무슨 명령으로 실행해야할 지 기록하는 부분으로 현재 수행 중인 JVM 명령 주소를 갖음

<br>

#### Native Method Stack
- 자바 외 언어로 작성된 네이티브 코드를 위한 메모리 영역

<br>

### 출처
[TCPSchool](http://www.tcpschool.com/java/java_array_memory) <br>
[https://tape22.tistory.com/28](https://tape22.tistory.com/28) <br>
[https://steady-coding.tistory.com/305](https://steady-coding.tistory.com/305) <br>
[김영한의 실전 자바 - 기본편](https://www.inflearn.com/course/%EA%B9%80%EC%98%81%ED%95%9C%EC%9D%98-%EC%8B%A4%EC%A0%84-%EC%9E%90%EB%B0%94-%EA%B8%B0%EB%B3%B8%ED%8E%B8/dashboard)
