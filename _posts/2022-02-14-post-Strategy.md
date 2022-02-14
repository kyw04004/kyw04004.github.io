---
title: 전략 패턴
categories:
- Design Pattern
excerpt: "전략 패턴에 대한 포스팅입니다."
feature_text: |
  ## Strategy Pattern
  Design Pattern
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 전략 패턴이란?
- 변하지 않는 부분을 Context 라는 곳에 두고, 변하는 부분을 Strategy 라는 <br> 인터페이스를 만들고 해당 인터페이스를 구현하도록 해서 문제를 해결
- 상속이 아니라 위임으로 문제를 해결
- 전략 패턴에서 Context 는 변하지 않는 템플릿 역할을 하고, <br> Strategy 는 변하는 알고리즘 역할

<br>

### 전략 패턴 사용 방법
- 필드에 전략을 보관하는 방식
	+ Context와 Strategy를 실행 전에 원하는 모양으로 조립해두고, <br> 그 다음에 Context를 실행하는 선 조립, 후 실행 방식
	+ 스프링 애플리케이션 개발할 때 애플리케이션 로딩 시점에 의존관계 주입을 통해 <br> 필요한 의존관계를 모두 맺어두고 난 다음에 실제 요청을 처리하는 것과 같은 원리
	+ 조립한 이후에 전략을 변경하기 번거롭다.
	+ 실행 순서
		- 1. Context에 원하는 Strategy 구현체를 주입
		- 2. 클라이언트는 context 실행
		- 3. context는 context 로직 시작
		- 4. context 로직 중간에 주입 받은 strategy 로직 실행
		- 5. context는 나머지 로직 실행
- 전략을 파라미터로 전달하는 방식
	+ 실행할 때마다 전략을 유연하게 변경 가능
	+ 실행할 때마다 전략을 계속 지정해주어야 하는 단점
	+ 실행 순서
		- 1. 클라이언트는 Context를 실행하면서 인수로 Strategy를 전달
		- 2. Context는 context 로직 시작
		- 3. Context는 파라미터로 넘어온 strategy 로직 실행
		- 4. context는 나머지 로직 실행
	+ 이 방법을 스프링에서는 템플릿 콜백 패턴이라고 함.
	+ Context가 템플릿 역할, Strategy 부분이 콜백 역할
	+ 스프링에서 XxxTemplate가 있다면 템플릿 콜백 패턴으로 만들어짐.
	+ 다른 코드의 인수로서 넘겨주는 실행 가능한 코드를 콜백(callback)이라함.

<br>

### 사용 예시
- 블로그 특성상 골뱅이는 //로 대체했습니다.
- 익명 내부 클래스를 자바8부터 제공하는 람다로 변경 가능
	+ 람다로 변경하려면 인터페이스에 메서드가 1개만 있으면 됨.
```java

//필드에 전략을 보관하는 형식
//Slf4j
public class ContextV1 {
    private Strategy strategy;

    public ContextV1(Strategy strategy) {
        this.strategy = strategy;
    }

    public void execute() {
        long startTime = System.currentTimeMillis();
        //비즈니스 로직 실행
        strategy.call(); //위임
        //비즈니스 로직 종료
        long endTime = System.currentTimeMillis();
        long resultTime = endTime - startTime;
        log.info("resultTime={}", resultTime);
    }
}

//전략을 파라미터로 전달 받는 방식
//Slf4j
public class ContextV2 {

    public void execute(Strategy strategy) {
        long startTime = System.currentTimeMillis();
        //비즈니스 로직 실행
        strategy.call(); //위임
        //비즈니스 로직 종료
        long endTime = System.currentTimeMillis();
        long resultTime = endTime - startTime;
        log.info("resultTime={}", resultTime);
    }
}

public interface Strategy {
    void call();
}

//Slf4j
public class StrategyLogic1 implements Strategy{
    //Override
    public void call() {
        log.info("비즈니스 로직1 실행");
    }
}

//Slf4j
public class StrategyLogic2 implements Strategy{
    //Override
    public void call() {
        log.info("비즈니스 로직2 실행");
    }
}

//필드에 전략을 보관하는 방식
//Slf4j
public class ContextV1Test {
    /**
     * 전략 패턴 사용
     */
    //Test
    void strategyV1() {
        StrategyLogic1 strategyLogic1 = new StrategyLogic1();
        ContextV1 context1 = new ContextV1(strategyLogic1);
        context1.execute();
        StrategyLogic2 strategyLogic2 = new StrategyLogic2();
        ContextV1 context2 = new ContextV1(strategyLogic2);
        context2.execute();
    }
    
    //익명 내부 클래스 사용
    //Test
    void strategyV2() {
        ContextV1 context1 = new ContextV1(new Strategy() {
            //Override
            public void call() {
                log.info("비즈니스 로직1 실행");
            }
        });
        context1.execute();
        ContextV1 context2 = new ContextV1(new Strategy() {
            //Override
            public void call() {
                log.info("비즈니스 로직2 실행");
            }
        });
        context2.execute();
    }

	//람다 사용
    //Test
    void strategyV4() {
        ContextV1 context1 = new ContextV1(() -> log.info("비즈니스 로직1 실행"));
        context1.execute();
        ContextV1 context2 = new ContextV1(() -> log.info("비즈니스 로직2 실행"));
        context2.execute();
    }
}

//전략을 파라미터로 전달하는 방식
//Slf4j
public class ContextV2Test {

    /**
     * 전략 패턴 적용
     */
    //Test
    void strategyV1() {
        ContextV2 context = new ContextV2();
        context.execute(new StrategyLogic1());
        context.execute(new StrategyLogic2());
    }

    //전략 패턴 익명 내부 클래스
    //Test
    void strategyV2() {
        ContextV2 context = new ContextV2();
        context.execute(new Strategy() {
            //Override
            public void call() {
                log.info("비즈니스 로직1 실행");
            }
        });
        context.execute(new Strategy() {
            //Override
            public void call() {
                log.info("비즈니스 로직2 실행");
            }
        });
    }

    //전략 패턴 익명 내부 클래스2, 람다
    //Test
    void strategyV3() {
        ContextV2 context = new ContextV2();
        context.execute(() -> log.info("비즈니스 로직1 실행"));
        context.execute(() -> log.info("비즈니스 로직2 실행"));
    }

}
```

<br>

### 출처

[스프링 핵심 원리 - 고급편 by 김영한](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%EA%B3%A0%EA%B8%89%ED%8E%B8#)
