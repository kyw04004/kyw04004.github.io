---
title: 프록시 패턴과 데코레이터 패턴
categories:
- Design Pattern
excerpt: "프록시 패턴과 데코레이터 패턴에 대한 포스팅입니다."
feature_text: |
  ## Proxy Pattern and Decorator Pattern
  Design Pattern
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 프록시란?
- 클라이언트가 요청한 결과를 서버에 직접 요청하는 것이 아니라 <br> 어떤 대리자를 통해서 대신 간접적으로 서버에 요청할 때, 대리자
- 객체에서 프록시가 되려면, 클라이언트는 서버에 요청한 것인지, <br> 프록시에 요청한 것인지 몰라야 함
	+ 서버와 프록시는 같은 인터페이스를 사용해야 함
	+ 서버 객체를 프록시 객체로 변경해도 코드 변경이 일어나지 않아야 함
- 그림자료 

<br>

![image](https://user-images.githubusercontent.com/56823099/154016730-f479850d-1cc8-4358-88d2-d55d0a1efd36.png)

<br>

![image](https://user-images.githubusercontent.com/56823099/154016933-9ca2a220-f05c-4f75-8143-2ce177f57323.png)


<br>

### 프록시의 주요 기능
- 접근 제어 - 권한에 따른 접근 차단, 캐싱, 지연 로딩
- 부가 기능 추가 - 원래 서버가 제공하는 기능에 더해서 부가 기능 수행(값 변형, 로그 등)
- 이 기능들은 의도에 따라서 프록시 패턴과 데코레이터 패턴으로 구분

<br>

### 프록시 패턴
- 접근 제어가 목적인 프록시를 사용하는 디자인 패턴
- 다른 개체에 대한 접근을 제어하기 위해 대리자를 제공

<br>

### 데코레이터 패턴
- 새로운 기능 추가가 목적인 프록시를 사용하는 디자인 패턴
- 객체에 추가 책임(기능)을 동적으로 추가하고, 기능 확장을 위한 유연한 대안 제공

<br>

### 사용 예시
- 코드가 너무 길어지는 것을 방지하기 위해 클라이언트 코드만 사용

<br>

```java

public class ProxyPatternTest {
    @Test
    void noProxy() { //매번 3번의 실행 로직 사용
        RealSubject realSubject = new RealSubject();
        ProxyPatternClient client = new ProxyPatternClient(realSubject);
        client.execute();
        client.execute();
        client.execute();
    }

    @Test
    void cacheProxy() { //1번의 실행 로직 후 저장된 값 실행
        RealSubject realSubject = new RealSubject();
        CacheProxy cacheProxy = new CacheProxy(realSubject);
        ProxyPatternClient client = new ProxyPatternClient(cacheProxy);
        client.execute();
        client.execute();
        client.execute();
    }
}

@Slf4j
public class DecoratorPatternTest {

    @Test
    void noDecorator() { //realComponent의 기능 사용
        Component realComponent = new RealComponent();
        DecoratorPatternClient client = new DecoratorPatternClient(realComponent);
        client.execute();
    }

    @Test
    void decorator() { //realComponent의 기능에서 데코레이터들로 추가 기능 부여
        Component realComponent = new RealComponent();
        Component messageDecorator = new MessageDecorator(realComponent);
        Component timeDecorator = new TimeDecorator(messageDecorator);
        DecoratorPatternClient client = new DecoratorPatternClient(timeDecorator);
        client.execute();
    }

}

```

<br>

### 출처

[스프링 핵심 원리 - 고급편 by 김영한](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B3%A0%EA%B8%89%ED%8E%B8#)
