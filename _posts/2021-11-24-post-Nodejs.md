---
title: Node.js란?
categories:
- Node.js
excerpt: "Node.js 설명문입니다. "
feature_text: |
  ## Node.js
  자바스크립트
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### Node.js란?


- Chrome V8 JavaScript 엔진으로 빌드 된 JavaScript 런타임

  + 런타임이란 특정 언어로 만든프로그램을 실행할 수 있는 환경

- 확장성 있는 네트워크 애플리케이션(특히 서버 사이드) 개발에 사용되는 소프트웨어 플랫폼

- 작성 언어로 자바스크립트를 활용

- Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능

- 내장 HTTP 서버 라이브러리를 포함하고 있어 웹 서버에서 아파치 등의 별도의 소프트웨어 없이 동작하는 것이 가능

- 백엔드, 웹 서버가 아니라 자바스크립트 실행 환경에 불과
  
  
#### 이벤트 기반이란?

-  이벤트가 발생할 때 미리 지정해둔 작업을 수행하는 방식 (이벤트는 클릭이나 네트워크 요청 등)
  
-  이벤트 기반 시스템에서는 특정 이벤트가 발생할 때 무엇을 할지 미리 등록해두어야 함
  
-  이것을 이벤트 리스너에 콜백함수를 등록한다고 표현
  
-  발생한 이벤트가 없거나 다 처리하면 노드는 다음 이벤트가 발생할 때까지 대기
  
- 여러 이벤트가 동시에 발생했을 때 어떤 순서로 콜백 함수를 호출할지 이벤트 루프가 판단
  
  
#### Non-blocking I/O란?

- 이벤트 루프를 잘 활용하면 오래 걸리는 작업을 효율적으로 처리 가능

- 오래 걸리는 함수를 백그라운드로 보내서 다음 코드가 먼저 실행되게 하고, 그 함수가 다시 태스크 큐를 거쳐 호출 스택으로 올라오기를 기다리는 방식, 이 방식이 논블로킹 방식

- 논블로킹이란 이전 작업이 완료될 때까지 멈추지 않고 다음 작업을 수행함을 의미

- 싱글 스레드의 한계로 모든 코드가 이 방식으로 시간적 이득을 보진 않음

- 현재 노드 프로세스 외의 다른 컴퓨팅 자원을 사용할 수 있는 I/O작업이 주로 시간적 이득을 많이 보기 때문에 노드는 논블로킹 방식으로 동작

  - I/O는 입력/출력을 의미, 파일 시스템 접근이나 네트워크 요청 같은 작업이 I/O의 일종 
  
  
####  싱글 스레드란?

- 한 번에 한 가지 일만 처리 (자바스크립트와 노드에서 논블로킹이 중요한 이유)
- 멀티 스레드는 노는 스레드가 존재할 수 있는 것이 문제
- 스레드를 늘리거나 줄이는 것도 비용을 줄일 수 있음
- 내부적으로는 스레드가 여러 개지만 사용자가 제어할 수 있는 스레드가 하나
  
  
#### Express FrameWork

- Node.js의 프레임워크
- Node.js를이용하여 웹 애플리케이션을 만들기 위한 틀을 제공하는 라이브러리의 집합
  
  
### 레퍼런스
[Node.js 교과서](http://www.yes24.com/Product/Goods/91213376)
[https://hanamon.kr/nodejs-%EA%B0%9C%EB%85%90-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0/](https://hanamon.kr/nodejs-%EA%B0%9C%EB%85%90-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0/)
