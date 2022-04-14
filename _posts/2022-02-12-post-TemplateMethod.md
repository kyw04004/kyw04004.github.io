---
title: 템플릿 메서드 패턴
categories:
- Design Pattern
excerpt: "템플릿 메서드 패턴에 대한 포스팅입니다."
feature_text: |
  ## Template Method Pattern
  Design Pattern
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 템플릿 메서드 패턴이란?
- 부모 클래스에 알고리즘의 골격인 템플릿을 정의하고, <br> 일부 변경되는 로직은 자식 클래스에 정의하는 디자인 패턴
- 상속과 오버라이딩을 통한 다형성을 이용한 패턴

<br>

### 템플릿 메서드 패턴 장점
- 핵심 기능(비즈니스 로직)과 부가 기능(시간 측정 등)을 분리할 수 있음
- 변경 지점을 하나로 모아 변경에 쉽게 대처할 수 있는 구조
	+ 코드의 재사용성과 유지보수성이 높은 설계

<br>

### 템플릿 메서드 패턴 단점
- 자식 클래스가 부모 클래스를 강하게 의존
	+ 부모 클래스의 기능을 사용하지 않아도 알아야 함
	+ 즉, 부모 클래스를 수정하면 자식 클래스에도 영향을 줌
- 상속 구조를 사용하여 별도의 클래스나 익명 내부 클래스를 만들어야해 복잡
	+ 익명 내부 클래스란? 이름없이 클래스 내부에서 선언되는 클래스
- 전략 패턴을 사용하면 상속의 단점을 제거하면서 비슷하게 사용 가능

<br>

### 사용 예시
- 시간을 측정하는 부가기능이 있다고 하자.
- 템플릿 메서드를 사용하지 않으면, <br> 매번 부모 클래스의 코드를 부가 기능 사용시 마다 작성해야 한다.
- 그에 반해, 확연히 코드가 간결해 보임을 확인할 수 있다.

<br>

```java

//부모 클래스
@Slf4j
public abstract class AbstractTemplate {

    public void execute() {
        long startTime = System.currentTimeMillis();
        //비즈니스 로직 실행
        call(); //상속
        //비즈니스 로직 종료
        long endTime = System.currentTimeMillis();
        long resultTime = endTime - startTime;
        log.info("resultTime={}", resultTime);
    }

    protected abstract void call();
}

//자식 클래스
@Slf4j
public class SubClassLogic extends AbstractTemplate {

    @Override
    protected void call() {
        log.info("비즈니스 로직 실행");
    }
}

@Slf4j
public class TemplateMethodTest {

	//별도의 클래스 사용
    void templateMethod1() {
        AbstractTemplate template = new SubClassLogic();
        template.execute();
    }

	//익명 내부 클래스 사용
    void templateMethod2() {
        AbstractTemplate template = new AbstractTemplate() {
            @Override
            protected void call() {
                log.info("비즈니스 로직 실행");
            }
        };
        template.execute();
    }
}

```

<br>

### 출처

[스프링 핵심 원리 - 고급편 by 김영한](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B3%A0%EA%B8%89%ED%8E%B8#)
