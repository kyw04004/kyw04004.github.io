---
title: JPA 영속성 관리
categories:
- JPA
excerpt: "JPA 영속성 관리 대한 포스팅입니다."
feature_text: |
  ## Persistence Context
  JPA 내부 구조
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 영속성 컨텍스트란?
- JPA를 이해하는데 가장 중요한 용어로 "엔티티를 영구 저장하는 환경"을 의미
- 논리적인 개념으로 눈에 보이지 않음
- 엔티티 매니저를 통해서 접근 가능
  
  
### 엔티티의 생명주기 (영속성 컨텍스트에서의 상태)
- 비영속 (new/transient) - 영속성 컨텍스트와 전혀 관계가 없는 새로운 상태
- 영속 (managed) - 영속성 컨텍스트에 관리되는 상태
- 준영속 (detached) - 영속성 컨텍스트에 저장되었다가 분리된 상태
- 삭제 (removed) - 영속성 컨텍스트에서 삭제된 상태
  

![image](https://user-images.githubusercontent.com/56823099/148394274-ade3ec8f-dfff-44c6-aee2-31e960666cd8.png)


### 영속성 컨텍스트의 이점
- 1차 캐시
	+ 영속성 관리된 객체에 대해서 쿼리를 추가적으로 사용하지 않음
	+ 한 트랜잭션안에서만 1차 캐시가 사용되어 성능 자체의 큰 효과는 없음
- 동일성(identity) 보장
	+ 한 트랜잭션에서 같은 객체는 동일성이 보장됨 (1차 캐시 영향)
- 트랜잭션을 지원하는 쓰기 지연(transactional write-behind)
	+ 트랜잭션 커밋시점까지 쓰기 지연 SQL 저장소에 SQL 쿼리를 모아둠
	+ 커밋(플러쉬) 시점에서 SQL쿼리를 한번에 보냄
- 변경 감지(Dirty Checking)
	+ 수정에 대한 명령을 사용하지 않아도 자동으로 DB가 수정됨
	+ 1차 캐시에서 초기 객체에 대한 값과 변경된 엔티티의 값을 비교하여 수정 쿼리 생성 
- 지연 로딩(Lazy Loading)
	+ 사용하지 않은 연관관계 값에 대해서 필요한 시점에 가져오는 것
  
  
### 플러시란?
- 영속성 컨텍스트의 변경내용을 데이터베이스에 반영하는 것
- 영속성 컨텍스트를 비우지 않음
- 커밋 직전에만 동기화하면 됨 (트랜잭션)
- 영속성 컨텍스트 플러시하는 방법
	+ em.flush() - 직접 호출
	+ 트랜잭션 커밋 - 플러시 자동 호출
	+ JPQL 쿼리 실행 - 플러시 자동 호출

  
### 출처

[자바 ORM 표준 JPA 프로그래밍 - 기본편 by 김영한](https://www.inflearn.com/course/ORM-JPA-Basic/dashboard)
