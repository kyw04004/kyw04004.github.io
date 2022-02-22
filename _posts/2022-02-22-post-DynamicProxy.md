---
title: 동적 프록시 기술
categories:
- JAVA
excerpt: "동적 프록시 기술에 대한 포스팅입니다."
feature_text: |
  ## Dynamic Proxy Skill
  JAVA
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 동적 프록시 기술이란?
- 개발자가 직접 프록시 클래스를 만들지 않고, <br> 동적으로 런타임에 개발자 대신 만들어주는 기술
- 부가 기능 로직을 한번만 개발해서 공통으로 적용 가능
- 사용하지 않고 프록시를 사용하려면, 적용 대상의 숫자만큼 프록시 클래스를 만들어야 함
- 리플렉션 기술 사용, 런타임에 동작해서 컴파일 오류 잡을 수 없음
	+ 클래스나 메서드의 메타정보를 동적으로 획득하고, 코드도 동적으로 호출 가능
	+ 일반적으로 사용하면 안되며, 필요시 부분적으로 주의해서 사용

<br>

### 동적 프록시 기술 종류
- JDK 동적 프록시
	+ 인터페이스를 기반으로 프록시를 동적으로 만들어 줌
	+ 인터페이스가 필수
	+ InvocationHandler를 공통로직으로 구현
	+ 그림자료 <br>
	![image](https://user-images.githubusercontent.com/56823099/155094439-c3e24448-3de8-4833-92ff-bd2804454ec5.png)
	

<br>

- CGLIB : Code Generator Library
	+ 바이트코드를 조작해서 동적으로 클래스를 생성하는 기술을 <br> 제공하는 라이브러리
	+ 인터페이스없이 구체 클래스만 가지고 동적 프록시를 만듦
	+ 외부 라이브러리이나, 스프링 내부 소스 코드에 포함
	+ MethodInterceptor를 공통로직으로 구현
	+ 상속을 사용하기에 제약이 있음
		- 부모 클래스 생성자 체크 (기본 생성자 필요)
		- 클래스에 final 키워드 붙으면 상속 불가
		- 메서드에 final 키워드 붙으면 오버라이딩 불가
	+ 그림자료 <br>
	![image](https://user-images.githubusercontent.com/56823099/155095069-830c58c7-afe3-49ac-a21a-d027d17e60ad.png)

<br>

### 사용법
- [사용 예시 코드](https://github.com/kyw04004/proxy/commit/f9bad586e15ecf8d89be2036fcc6dd9384301b89)

<br>

### 출처

[스프링 핵심 원리 - 고급편 by 김영한](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B3%A0%EA%B8%89%ED%8E%B8#)