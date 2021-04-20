---
title: SQL DML 명령어
categories:
- SQL
excerpt: "SQL DML 요약입니다."
feature_text: |
  ## SQL DML 요약
  DML
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---
DML 명령어
+ SELECT -> 데이터의 내용을 조회할 때 사용하는 명령어!
+ INSERT -> 데이터의 내용을 삽입할 때 사용하는 명령어!
+ UPDATE -> 데이터의 내용을 변경할 때 사용하는 명령어!
+ DELETE -> 데이터의 내용을 삭제할 때 사용하는 명령어!

```
select [all | distinct] 속성명1, 속성명2, ...
from 테이블명1, ...
[where 조건]
[group by 속성명1, ...]
[having 그룹조건]
[order by 속성 [asc | desc]];

insert into 테이블명(속성명1, ...) values(데이터1, ...);

update 테이블명 set 속성명 = 데이터 where 조건;

delete from 테이블명 조건;
	
```
