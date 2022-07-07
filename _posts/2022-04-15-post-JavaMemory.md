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

<br>

#### Method (Static) Area 
- 클래스에 대한 정보와 클래스 변수(static variable)가 저장되는 영역
- 모든 스레드가 공유하는 영역
- 어디서든 접근 가능
- JVM이 종료될 때까지 유지

<br>

#### Heap Area
- 모든 인스턴스 변수가 저장되는 영역
- 참조형 변수도 저장
- new 키워드를 사용하여 생성된 인스턴스의 정보를 저장
- 모든 스레드가 공유하는 영역
- GC가 정리전까지 남아있음

<br>

#### Stack Area
- 메소드가 호출될 때 메소드의 스택 프레임이 저장되는 영역
	+ 스택 프레임이란 스택 영역에 저장되는 메소드의 호출 정보
- 메소드 호출과 관계되는 지역 변수와 매개변수를 스택 영역에 저장
- 기본형 변수 저장
- 스레드 별로 1개만 생성
- 메소드의 호출과 함께 할당되며, 메소드의 호출이 완료되면 소멸

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
[https://steady-coding.tistory.com/305](https://steady-coding.tistory.com/305)
