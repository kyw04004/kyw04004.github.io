---
title: 페치 조인
categories:
- JPA
excerpt: "페치 조인에 대한 포스팅입니다."
feature_text: |
  ## fetch join
  JPQL
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

### 페치 조인 (fetch join)
- JPQL에서 성능 최적화를 위해 제공하는 기능
- SQL 조인 종류가 아님
- 연관된 엔티티나 컬렉션을 SQL 한 번에 함께 조회하는 기능
- SQL 한 번에 객체와 연관 객체까지 조회
- 필요한 연관 엔티티들을 미리 가져옴으로써 N + 1 문제 해결
- 조회한 객체들을 영속성 컨텍스트에 등록하고 1차 캐시로 사용
- inner, outer join 둘 다 가능
- 일대다 조인시에는 데이터가 증가될 수 있음
	+ ex) 팀에 속하는 여러 명의 회원
	+ DISTINCT를 사용하여 해결 가능

<br>

### 사용 방법
- 회원을 조회하면서 연관된 팀도 함께 조회(SQL 한 번에)
- [JPQL] select m from Member m join fetch m.team
- [SQL] select m.*, t.* from member m join team t on m.team.id=t.id

<br>

### DISTINCT
- SQL의 DISTINCT는 중복된 결과를 제거하는 명령
- JPQL의 DINSTINCT 2가지 기능 제공
	+ SQL에 DISTINCT를 추가
	+ 애플리케이션에서 엔티티 중복 제거(같은 식별자를 가진 엔티티 제거)

<br>

### 페치 조인과 일반 조인의 차이
- JPQL은 결과를 반환할 때 연관관계 고려X
- SELECT 절에 지정한 엔티티만 조회
- 페치 조인을 사용할 때만 연관된 엔티티도 함께 조회(즉시 로딩)
- 페치 조인은 객체 그래프를 SQL 한번에 조회하는 개념
- 일반 조인 실행시 연관된 엔티티를 함께 조회하지 않음

<br>

### 페치 조인의 특징과 한계
- 페치 조인 대상에는 별칭을 줄 수 없다.
	+ 하이버네이트는 가능, 가급적 사용 X
- 둘 이상의 컬렉션은 페치 조인할 수 없다.
- 컬렉션을 페치 조인하면 페이징 API를 사용할 수 없다.
	+ 일대일, 다대일 같은 단일 값 연관 필드들은 페치 조인해도 페이징 가능
	+ 컬렉션을 페치 조인하면 일대다 조인이 발생하므로 데이터가 예측할 수 없이 증가
	+ 일대다에서 일을 기준으로 페이징을 하는 것이 목적이지만, 다를 기준으로 row가 생성
	+ 하이버네이트는 경고 로그를 남기고 모든 DB 데이터를 읽어서 메모리에서 페이징 시도(매우 위험)
- 연관된 엔티티들을 SQL 한 번으로 조회 - 성능 최적화
- 엔티티에 직접 적용하는 글로벌 로딩 전략보다 우선함
	+ @OneToMany(fetch=FetchType.LAZY) //글로벌 로딩 전략
- 실무에서 글로벌 로딩 전략은 모두 지연 로딩
- 최적화가 필요한 곳은 페치 조인 적용

<br>

### 한계 돌파
- 페이징 + 컬렉션 엔티티를 함께 조회하려면?
- 대부분의 페이징 + 컬렉션 엔티티 조회 문제를 해결하는 강력한 방법
- ToOne 관계를 모두 페치조인
	+ ToOne 관계는 row수를 증가시키지 않으므로 페이징 쿼리에 영향X
- 컬렉션은 지연 로딩으로 조회
- 지연 로딩 성능 최적화를 위해 hibernate.default_batch_size, @BatchSize를 적용
	+ hibernate.default_batch_fetch_size: 글로벌 설정
	+ @BatchSize: 개별 최적화
	+ 이 옵션을 사용하면 컬렉션이나, 프록시 객체를 한꺼번에 설정한 size 만큼 IN 쿼리로 조회
- default_batch_fetch_size의 크기는 100~1000 사이를 선택하는 것을 권장
- 장점
	+ 쿼리 호출 수가 N + 1 -> 1 + 1로 최적화
	+ 조인보다 DB 데이터 전송량 최적화 (중복 데이터가 없음)
	+ 페치 조인 방식보다 쿼리 호출 수가 약간 증가하지만 DB 데이터 전송량 감소
	+ 컬렉션 페치 조인은 페이징 불가능하지만, 이 방법은 페이징 가능

<br>

### 정리
- 모든 것을 페치 조인으로 해결할 수는 없음
- 페치 조인은 객체 그래프를 유지할 때 사용하면 효과적
- 여러 테이블을 조인해서 엔티티가 가진 모양이 아닌 <br> 전혀 다른 결과를 내야 하면, 페치 조인보다는 <br> 일반 조인을 사용하고 필요한 데이터들을 조회해서 <br> DTO로 반환하는 것이 효과적

<br>

### 출처

[자바 ORM 표준 JPA 프로그래밍 - 기본편 by 김영한](https://www.inflearn.com/course/ORM-JPA-Basic/dashboard) <br>
[실전! 스프링 부트와 JPA 활용2 - API 개발과 성능 최적화 by 김영한](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-API%EA%B0%9C%EB%B0%9C-%EC%84%B1%EB%8A%A5%EC%B5%9C%EC%A0%81%ED%99%94/dashboard)
