---
title: 스프링 동시성 문제
categories:
- Spring
excerpt: "ThreadLocal에 대한 포스팅입니다."
feature_text: |
  ## Spring 동시성 문제
  Thread Local
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 동시성 문제란?
- 하나의 인스턴스에 여러 쓰레드가 동시에 접근하여 발생하는 문제.
- 동시성 문제는 트래픽이 적은 상황에서는 확률상 잘 나타나지 않고, <br> 트래픽이 점점 많아질수록 자주 발생함.
- 특히 스프링은 싱글톤으로 빈을 관리하기 때문에 동시성 문제에 조심 해야함.
- 이것을 해결하기 위한 방안 중 하나로 쓰레드 로컬이 있음.

<br>

### 쓰레드 로컬이란?
- 해당 쓰레드만 접근할 수 있는 특별한 저장소.
- 각 쓰레드마다 별도의 내부 저장소 제공.
- 같은 인스턴스의 쓰레드 로컬 필드에 접근해도 문제 없음.
- 자바는 언어차원에서 쓰레드 로컬을 지원하기 위한 <br> java.lang.ThreadLocal 클래스 제공
- <그림 자료> <br>
![image](https://user-images.githubusercontent.com/56823099/153154921-29355974-df3c-44ed-944d-78877c0e2e73.png)

<br>

### 쓰레드 로컬 사용법
- 값 저장 : ThreadLocal.set(xxx)
- 값 조회 : ThreadLocal.get()
- 값 제거 : ThreadLocal.remove()
- 예시
```java
//선언
private ThreadLocal<String> str = new ThreadLocal<>();
//값 저장
str.set("abc");
//값 조회
str.get();
//값 제거
str.remove();
```

<br>

### 쓰레드 로컬 주의사항
- 해당 쓰레드가 쓰레드 로컬을 모두 사용하고 나면 <br> 쓰레드 로컬에 저장된 값을 제거해야 함.
- 쓰레드 로컬의 값을 사용 후 제거하지 않고 그냥 두면 WAS(톰캣)처럼 <br> 쓰레드 풀을 사용하는 경우에 심각한 문제가 발생할 수 있음.
- 사용자A 저장 요청
![image](https://user-images.githubusercontent.com/56823099/153157062-b3c3d46f-15a9-4ecc-94d0-7d1546acebdb.png) <br> 
- 사용자A 저장 요청 종료
![image](https://user-images.githubusercontent.com/56823099/153157148-442a5a9c-cd95-4490-ba46-0ecd4e2ba0de.png) <br> 
- 사용자B 조회 요청
![image](https://user-images.githubusercontent.com/56823099/153157259-c11741fc-d5d1-42a2-b34f-e151fd19abc6.png) <br>
- 사용자A를 저장하고 요청을 종료할 때, 쓰레드 로컬의 저장된 값을 지우지 않으면, <br> 사용자B가 조회할 때, 사용자A가 사용했던 같은 쓰레드를 사용하게 된다면, <br> 사용자A를 조회하게 된다.

<br>

### 출처

[스프링 핵심 원리 - 고급편 by 김영한](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B3%A0%EA%B8%89%ED%8E%B8#)
