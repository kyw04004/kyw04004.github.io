---
title: SQL DDL 명령어
categories:
- SQL
excerpt: "SQL DDL 요약입니다."
feature_text: |
  ## SQL DDL 요약
  DDL
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---
DDL 명령어
+ CREATE -> 생성하는 명령어!
+ ALTER -> 수정하는 명령어!
+ DROP -> 삭제하는 명령어!
	- cascade 옵션은 참조하는 테이블까지 삭제
	- restrict 옵션은 다른 테이블이 해당 테이블을 참조 중이면 제거 X
+ TRUNCATE -> 테이블 내의 데이터들을 삭제하는 명령어!

```
테이블 생성, 수정, 삭제

	create table 테이블명
	(
		컬럼명 데이터타입 primary key,
	 	컬럼명 데이터타입 foreign key references 참조테이블(기본키),
	 	컬럼명 데이터타입 unique,
	 	컬럼명 데이터타입 not null,
	 	컬럼명 데이터타입 check(조건식),
	 	컬럼명 데이터타입 defalut 값
	);
	
	alter table 테이블명 [add|modify|drop] 컬럼명 데이터타입 [제약조건];
	
	drop table 테이블명 [cascade|restrict];
	
	truncate table 테이블명;
	
인덱스 생성, 수정, 삭제

	create [unique] index 인덱스명 on 테이블명(컬럼명1, 컬럼명2, ...);
	
	alter [unique] index 인덱스명 on 테이블명(컬럼명1, 컬럼명2, ...);
	
	drop index 인덱스명;
	
```
