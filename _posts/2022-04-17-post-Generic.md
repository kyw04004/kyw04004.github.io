---
title: 제네릭(Generic)
categories:
- JAVA
excerpt: "Java의 제네릭 타입에 대한 포스팅입니다."
feature_text: |
  ## 타입 매개변수
  JAVA
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### 제네릭이란?
- 데이터 타입을 프로그래밍할 때 결정하는 것이 아니고 실행할 때 결정하게 하는 기능
- 데이터 타입을 매개변수로 지정하는 것
- 클래스, 인터페이스, 메서드에서 사용 
- 자바 5부터 추가된 기능

<br>

### 제네릭의 장점
- 강한 타입 검사
	+ 상위 클래스에 각각 다른 하위 클래스를 주입 받으면  같은 타입으로 인식하지만, <br> 제네릭 클래스는 다른 타입으로 인식
- 타입 변환 제거
	+ 상위 클래스로 선언해서 필요한 타입들을 받는 것은 타입 변경 필요

<br>

### 제네릭 사용법
- 멀티 타입 매개변수
	+ 2개 이상의 타입 매개변수를 선언할 땐 콤마로 구분
	+ <T, N>
- 타입 제한
	+ 특정 클래스나  그것의 하위 클래스로 제한
		- < T extends SuperClass>
	+ 와일드 카드
		- 현재 타입 매개변수와 달라도 가능
		- <?>
		- 상위 제한, 하위 제한 존재
		- <? extends SuperClass>, <? super SubClass>
- 사용 코드 

<br>

```java
//제네릭 클래스 참조, 생성
클래스명<타입인자> 참조명 = new 클래스명<타입인자>(new 타입클래스());

//제네릭 클래스
class 클래스명<T> {...}

//제네릭 인터페이스
interface 인터페이스명<T> {...}

//제네릭 메서드
<T, N> 반환형 함수명(T t, N n) {...}
```

<br>

### 출처
[IT 분야에서 밥 먹고 살기 프로젝트](https://slow-and-steady-wins-the-race.tistory.com/104) <br>
