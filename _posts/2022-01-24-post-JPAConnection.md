---
title: JPA 연관관계
categories:
- JPA
excerpt: "JPA 연관관계 설정에 대한 포스팅입니다."
feature_text: |
  ## JPA 연관관계
  연관관계 매핑
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### 연관관계란?
- 객체의 참조와 테이블의 외래 키를 매핑하는 것.
- 연관관계를 사용하지 않으면 객체를 테이블에 맞추어 데이터 중심으로 모델링하게 됨.

<br>

### 연관관계 종류
- 다대일 (N:1) - @ManyToOne
- 일대다 (1:N) - @OneToMany
- 일대일 (1:1)  - @OneToOne
- 다대다 (N:M) - @ManyToMany

<br>

### 연관관계 사용 방법
- 연관관계의 주인 : 양방향 연관관계일 때 관리 해주는 객체
	+ ex) @ManyToOne(fetch = FetchType.LAZY) <br> @JoinColumn(name="테이블의 외래키")
- 반대쪽 (양방향 연관관계시 사용)
	+ ex) @OneToMany(mappedBy = "연관관계 주인의 매핑 객체명")

<br>

### 연관관계 매핑 팁
- 연관관계의 주인 쪽에서 값을 변경해야 하며, 반대 쪽은 조회용으로만 사용해라.
	+ 외래키가 있는 곳을 연관관계의 주인으로 설정.
- 웬만해서는 단방향 연관관계 사용.
	+ 단방향으로 매핑해놓고 양방향이 필요할 경우 한 줄만 추가하면 됨.
	+ 단방향과 양방향은 테이블에 차이가 없음.
- 일대다 단방향보다는 다대일 양방향으로 설정해라.
	+ 다쪽에서 일로 참조할 일이 없고 객체적으로는 손해일지라도 <br> 디비 입장으로는 도움이 될 수 있음.
- 다대다 관계는 사용하면 안되며, 일대다, 다대일 관계로 풀어서 사용해라.
- 모든 연관관계는 지연로딩으로 설정해라.
	+ 일대일, 다대일에서 적어줘야함, 다른 관계는 디폴트가 지연로딩.
- 컬렉션은 필드에서 초기화 하자.
	+ null 문제에서 안전해짐.
	+ 메서드에서 컬렉션을 잘못 생성하면 <br> 하이버네이트 내부 메커니즘에 문제가 발생할 수 있음.

<br>

### 즉시 로딩과 지연로딩
- 즉시 로딩은 연관관계를 처음부터 모두 가져오는 것.
	+ 처음부터 연관관계를 가져오기 위해 많은 조인 쿼리를 날리기 때문에 <br> 성능상의 문제를 야기할 수 있음. <br> ex) N+1의 문제
	+ 사용 예시) @ManyToOne(fetch = FetchType.EAGER) 
- 지연 로딩은 연관관계를 필요할때만 가져오는 것.
	+ 연관관계가 사용할 때만 조인 쿼리를 사용하기 때문에 성능상 이점이 있음. 
	+ 사용 예시) @ManyToOne(fetch = FetchType.LAZY) 

<br>

### 영속성 전이 : CASCADE
- 특정 엔티티를 영속 상태로 만들 때 연관된 엔티티도 함께 <br> 영속 상태로 만들고 싶을 때 사용.
- ex) 부모 엔티티를 저장할 때 자식 엔티티도 함께 저장.
- 사용 예시) @OneToMany(mappedBy="parent", cascade=CascadeType.????)
	+ ALL : 모두 적용, PERSIST : 영속, REMOVE : 삭제

<br>

### 고아 객체
- 부모 엔티티와 연관관계가 끊어진 자식 엔티티.
- orphanRemoval = true 를 적어주면 고아 객체가 자동으로 삭제됨.
	+ 참조하는 곳이 하나일 때 사용해야 함.
	+ @OneToOne, @OneToMany만 가능.

<br>

### 출처

[자바 ORM 표준 JPA 프로그래밍 - 기본편 by 김영한](https://www.inflearn.com/course/ORM-JPA-Basic/dashboard)
