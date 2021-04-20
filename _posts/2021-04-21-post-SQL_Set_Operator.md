---
title: SQL 집합 연산자
categories:
- SQL
excerpt: "SQL 집합 연산자 정리입니다."
feature_text: |
  ## SQL 집합 연산자
  집합 연산자
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---
집합 연산자란? 테이블을 집합 개념으로 보고, 두 테이블 연산에 집합 연산자를 사용하는 방식!
+ UNION -> 중복 행이 제거된 쿼리 결과 반환!
+ UNOIN ALL -> 중복 행이 제거되지 않은 쿼리 결과 반환!
+ INTERSECT -> 두 쿼리 결과에 공통적으로 존재하는 결과 반환!
+ MINUS -> 첫 쿼리에 있고 두 번째 쿼리에 없는 결과 반환!

```
select절 집합 연산자 select절;
```

