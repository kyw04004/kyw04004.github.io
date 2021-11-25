---
title: MongoDB란?
categories:
- MongoDB
excerpt: "MongoDB 설명 포스팅입니다. "
feature_text: |
  ## MongoDB
  NoSQL
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

#### MongoDB란?

- 문서지향(Document-Oriendted) 저장소를 제공하는 NoSQL 데이터베이스 시스템
  - NoSQL(Not only SQL)이란 관계형 데이터 모델과는 다른 데이터 관리 시스템
  
- JSON 형태(Key-Value 쌍)로 문서(Document) 저장

- 현존하는 NoSQL 데이터베이스 중 인지도 1위
  
- C++로 만들어짐
  
  
#### MongoDB의 특징

- 신뢰성 (Reliability) - 여러 대의 백업 서버 구성이 가능하여 장애 발생 시에도 무중단 서비스가 가능

- 확장성 (Sacalability) - 스케일 아웃에 의한 서버 확장이 용이, auto-sharding 지원

  - 스케일 아웃(scale-out)이란 하나의 장비에서 처리하던 일을 여러 장비에 나눠서 처리할 수 있는 확장 기능
  - sharding이란 데이터를 여러 서버에 분산해서 저장하고 처리할 수 있도록 하는 기술

- 유연성 (Flexibility) - 스키마 선언 없이 필드의 추가 및 삭제가 자유로운 Schema-less 구조

- 인덱스 지원 (Index Support) - RDBMS 같은 인덱스 지원으로 다양한 조건으로 빠른 데이터 검색 가능
  
  
#### MongoDB 장점

- 데이터 구조가 빈번히 변경되는 구조에서 초기 단계에 개발 속도를 단축시켜줌
- 제약조건이 없어 매우 고성능 (RDBMS 속도보다 굉장히 빠름)
- 낮은 진입장벽 (스키마 관리 X, scale-out 구조)
  
  
#### MongoDB 단점

- 트랜잭션을 제공하지 않음

- 복잡한 쿼리 불가 (join 없음)

- 데이터 중복으로 메모리 용량이 증가할 수 있음
  
- SQL을 완전히 이전 불가
  
  
#### MongoDB 용어

| MySQL 용어      | mongoDB 용어 |
| :------: | :------: |
|database|database|
|table|collection|
|index|index|
|row|document|
|column|field|
|join|embedding and linking|
|primary key|_id field|
|group by|aggregation|

  

#### Mongoose란?

- Node.js와 MongoDB를 위한 ODM(Object Data Mapping) 라이브러리
- Object와 MongoDB 데이터를 Mapping하여 호환성을 만들어 간편한 CURD 가능
  
  
#### 레퍼런스

[https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174384/mongodb%EB%9E%80](https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174384/mongodb%EB%9E%80)<br>

[https://rastalion.me/mongodb%EB%9E%80/](https://rastalion.me/mongodb%EB%9E%80/)<br>

[http://dev.youngkyu.kr/22](http://dev.youngkyu.kr/22)<br>

[https://www.byfuls.com/programming/read?id=60](https://www.byfuls.com/programming/read?id=60)<br>
