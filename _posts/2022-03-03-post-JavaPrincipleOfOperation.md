---
title: Java의 동작 원리
categories:
- JAVA
excerpt: "Java의 동작 원리에 대한 포스팅입니다."
feature_text: |
  ## Java's Principle of Operation
  JAVA
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### 자바의 동작 원리
![그림자료](http://www.tcpschool.com/lectures/img_java_programming.png)
- 자바 클래스 파일을 자바 컴파일러에 의해 <br> 자바 바이트 코드로 변환
	+ 자바 바이트 코드란 자바 가상 머신이  <br>이해할 수 있는 언어로 변환된 자바 소스 코드
	+ 자바 컴파일러에 의해 변환되는 코드의 명령어 크기가 <br> 1바이트라서 자바 바이트 코드라 불림
	+ 자바 바이트 코드는 자바 가상 머신만 설치되어 있으면,  <br> 어떤 운영체제에서라도 실행 가능
- 자바 바이트 코드를 JVM의 클래스 로더에 전달
	+ JVM이란 자바 바이트 코드를 실행시키기 위한 가상의 기계
	+ 자바로 작성된 모든 프로그램은 JVM에서만 실행될 수 있음
	+ 한 번 프로그램을 작성하면, 모든 운영체제에서 사용 가능
	+ JVM은 운영체제에 종속적이므로, 운영체제에 맞는 JVM 필요
	+ 자바 프로그램은 JVM을 거쳐야하므로 타 프로그램보다 비교적 느림
- 클래스 로더는 런타임시 자바 바이트 코드를 JVM이 운영체제로부터 <br>  할당받은 메모리 영역인 Runtime Data Area에 적재
- 실행 엔진에 의해 Runtime Data Area(메모리 영역)에 적재된 <br> 자바 바이트 코드를 기계어로 변경하여 실행
	+ JVM이 운영체제가 실행할 수 있는 형태로 변경하는 것
	+ 실행 방식은 JIT컴파일러와 인터프리터 방식이 존재

<br>

### 자바 가상 머신의 구성
- 자바 인터프리터(interpreter)
	+ 자바 바이트 코드를 한줄씩 읽고 해석하는 역할
- 클래스 로더(class loader)
	+ 동적으로 클래스를 로딩해주는 역할
	+ 런타임시 자바 바이트 코드를 JVM이 운영체제로부터 <br>  할당받은 메모리 영역인 Runtime Data Area에 적재
- JIT 컴파일러(Just-In-Time compiler)
	+ 자바 바이트 코드를 런타임에 바로 기계어로 변환
	+ 자주 반복되는 코드를 캐싱
	+ 실행 속도 향상시키기 위해 개발
- 가비지 컬렉터(garbage collector)
	+ 사용하지 않는 메모리 자동 회수
	+ Heap 메모리 영역에 적재된 객체들 중 참조되지 않는 객체들을 제거

<br>

### 출처
[TCPSCHOOL](http://www.tcpschool.com/) <br>
[더기 블로그](https://dev-monkey-dugi.tistory.com/68)
