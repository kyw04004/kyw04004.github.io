---
title: HTTP 메서드
categories:
- Network
excerpt: "HTTP 메서드에 대한 포스팅입니다."
feature_text: |
  ## HTTP 메서드
  HTTP 
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---
### HTTP 메서드 종류
- GET : 리소스 조회
	+ 서버에 전달하고 싶은 데이터는 <br> query(쿼리 파라미터, 쿼리스트링)를 통해서 전달
	+ 메시지 바디를 사용해서 데이터 전달 가능 <br> 지원하지 않는 곳이 많아 권장 X
- POST : 요청 데이터 처리
	+ 메시지 바디를 통해 서버로 요청 데이터 전달
	+ 서버는 요청 데이터 처리
		- 메시지 바디를 통해 들어온 데이터를 처리하는 모든 기능 수행
	+ 주로 전달된 데이터로 신규 리소스 등록, 프로세스 처리에 사용
- PUT : 리소스를 대체, 해당 리소스가 없으면 생성
	+ 리소스를 덮어버림
	+ 클라이언트가 리소스를 식별
		- 클라이언트가 리소스 위치를 알고 URI 지정
		- POST와 차이점
- PATCH : 리소스 부분 변경
- DELETE : 리소스 삭제
- HEAD : GET과 동일하지만 메시지 부분을 제외하고, 상태 줄과 헤더만 반환
- OPTIONS : 대상 리소스에 대한 통신 가능 옵션(메서드) 설명
- CONNECT : 대상 자원으로 식별되는 서버에 대한 터널 설정
- TRACE : 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트 수행

<br>

### HTTP 메서드의 속성
- 안전 (Safe Methods)
	+ 호출해도 리소스 변경 X
- 멱등 (Idempotent Methods)
	+ f(f(x)) = f(x)
	+ 한 번 호출, 두번 호출, 100번 호출 모두 결과가 같음
	+ 멱등 메서드 - GET, PUT, DELETE
	+ 활용 - 자동 복구 메커니즘
		- 서버가 TIMEOUT 등으로 정상 응답을 못주었을 때, <br> 클라이언트가 같은 요청을 다시 해도 되는가의 판단 근거
- 캐시가능 (Cacheable Methods)
	+ 응답 결과 리소스를 캐시해서 사용해도 되는가
	+ GET, HEAD, POST, PATCH 캐시 가능
	+ 실제로는 GET, HEAD 정도만 사용
		- POST, PATCH는 본문 내용까지 캐시 키로 <br> 고려해야 하는데, 구현이 쉽지 않음

<br>

### HTTP API URI 설계
- 리소스와 행위를 분리
	+ 가장 중요한 것은 리소스 식별
- URI는 리소스만 식별
- 리소스와 해당 리소스를 대상으로 하는 행위를 분리
	+ ex) 리소스 : 회원
	+ ex) 행위 : 조회, 등록, 삭제, 변경
- 리소스는 명사, 행위는 동사
- 행위(메서드)는 HTTP 메서드로 구분
- 메서드로만 행위를 구분하기 어려울 때, 컨트롤 URI 사용
	+ 컨트롤 URI는 동사로 된 리소스 경로
	+ POST의 /new, /edit, /delete 등

<br>

### 클라이언트에서 서버로 데이터 전송
#### 데이터 전달 방식
- 쿼리 파라미터를 통한 데이터 전송
	+ GET
	+ 주로 정렬 필터(검색어)
- 메시지 바디를 통한 데이터 전송
	+ POST, PUT, PATCH
	+ 회원 가입, 상품 주문, 리소스 등록, 리소스 변경
#### 4가지 상황
- 정적 데이터 조회
	+ 이미지, 정적 텍스트 문서
	+ 일반적으로 쿼리 파라미터 없이 <br> 리소스 경로로 단순하게 조회 가능
- 동적 데이터 조회
	+ 주로 검색, 게시판 목록에서 정렬 필터(검색어)
	+ GET은 쿼리 파라미터를 사용해서 데이터 전달
- HTML Form을 통한 데이터 전송
	+ 회원 가입, 상품 주문, 데이터 변경
	+ GET, POST만 지원
- HTML API를 통한 데이터 전송
	+ 회원 가입, 상품 주문, 데이터 변경
	+ 서버 to 서버, 앱 클라이언트, 웹 클라이언트(AJAX)
	+ POST, PUT, PATCH : 메시지 바디를 통해 데이터 전송
	+ GET : 조회, 쿼리 파라미터로 데이터 전달

<br>

#### 출처

[모든 개발자를 위한 HTTP 웹 기본 지식 by 김영한](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/) 
