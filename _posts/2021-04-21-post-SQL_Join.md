---
title: SQL Join
categories:
- SQL
excerpt: "SQL Join 요약입니다."
feature_text: |
  ## SQL Join 요약
  Join
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---
Join이란? 두 개 이상의 테이블을 연결하여 데이터를 검색하는 방법!
+ inner join -> 컬럼의 값이 같은 경우 추출!
+ outer join -> 조건에 만족 못하면 null값으로 추출됨! 없애고 싶다면? where 컬럼 is null 사용!
	- left outer join -> 왼쪽 테이블의 모든 데이터와 오른쪽 데이터의 동일 데이터를 추출!
	- right outer join > 오른쪽 테이블의 모든 데이터와 왼쪽 데이터의 동일 데이터를 추출!
	- full outer join -> 양쪽의 모든 데이터를 추출!
+ cross join -> 조인 조건이 없는 모든 데이터 조합을 추출 (on절이 없다!)
+ self join -> 자신에게 별칭을 지정한 후 다시 조인 (같은 테이블에 별칭을 다르게!)

```
내부 조인
select A.컬럼, B.컬럼, ...
from 테이블1 A [inner] join 테이블2 B
on 조인조건
[where 검색조건];

외부 조인
select A.컬럼, B.컬럼, ...
from 테이블1 A [left | right | full] [outer] join 테이블2 B
on 조인조건
[where 검색조건];

교차 조인
select 컬럼1, 컬럼2, ...
from 테이블1 cross join 테이블2

셀프 조인
select A.컬럼, B.컬럼, ...
from 테이블 A [inner] join 테이블 B
on 조인조건
[where 검색조건];
	
```
