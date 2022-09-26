---  
title: 자바 리플렉션 (Reflection)
categories:
- JAVA  
excerpt: "리플렉션에 대한 포스팅입니다."  
feature_text: |
  ## Reflection
  리플렉션
feature_image: "https://picsum.photos/2560/600?image=733"  
image: "https://picsum.photos/2560/600?image=733"
---  
### 리플렉션이란?
- 구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API
- 컴파일 시간이 아닌 실행 시간에 동적으로 특정 클래스의 정보를 추출할 수있는 프로그래밍 기법

<br>

#### 사용할 때
- 동적으로 클래스를 사용할 때
- 애노테이션이 지정되어 있는지 파악할 때 (특히 스프링 프레임워크)

<br>  

#### 사용법
```java
Class<?> c = Class.forName("클래스명"); //클래스 정보 가져오기

Object o = c.newInstance(); //인스턴스 생성

Method[] m = c.getDeclareMethods(); //모든 메서드들 가져오기

Method[] ma = c.getMethods(); // public 메서드들,  상속 받은 메서드들 가져오기

Method m = c.getMethod("함수명", 매개변수 자료형.class); //특정 함수

m.invoke(객체 포인터, 매개변수); //함수 실행

Field[] fields = c.getFields(); //상속받은 객체의 public 필드까지 찾아줌

Field field = c.getField("필드명"); //특정 public 필드 찾기

Field field = c.getDeclaredField("필드명"); //특정 필드 찾기

int parameterCount = m.getParameterCount(); //파리미터 갯수

Class<?>[] parameterTypes = c.getParameterTypes(); //파라미터 타입

Annotation[][] a = m.getParameterAnnotations(); //파라미터의 애노테이션들

...

```

<br>  

### 출처
[https://kdg-is.tistory.com/entry/JAVA-%EB%A6%AC%ED%94%8C%EB%A0%89%EC%85%98-Reflection%EC%9D%B4%EB%9E%80](https://kdg-is.tistory.com/entry/JAVA-%EB%A6%AC%ED%94%8C%EB%A0%89%EC%85%98-Reflection%EC%9D%B4%EB%9E%80) <br> 
