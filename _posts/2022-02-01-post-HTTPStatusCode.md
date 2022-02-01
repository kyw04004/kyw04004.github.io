---
title: HTTP 상태 코드
categories:
- Network
excerpt: "HTTP 상태 코드에 대한 포스팅입니다."
feature_text: |
  ## HTTP 상태 코드
  HyperText Transfer Protocol
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---
### HTTP 상태  코드란?
- 클라이언트가 보낸 요청의 처리 상태를 응답에서 알려주는 기능
- 1xx (Informational) : 요청이 수신되어 처리중
- 2xx (Successful) : 요청 정상 처리
- 3xx (Redirection) : 요청을 완료하려면 추가 행동이 필요
- 4xx (Client Error) : 클라이언트 오류
	+ 잘못된 문법 등으로 서버가 요청을 수행할 수 없음
- 5xx (Server Error) : 서버 오류
	+ 서버가 정상 요청을 처리하지 못함
- 클라이언트가 모르는 상태 코드가 나타나면?
	+ 상위 상태 코드로 해석해서 처리
	+ 새로운 상태 코드가 추가되어도 클라이언트 변경 안해도 됨
	+ ex) 299 ??? -> 2xx (Successful)

<br>

### HTTP 상태 코드의 종류

<br>

#### 2xx (Successful)
- 클라이언트의 요청을 성공적으로 처리
- 200 OK
	+ 요청 성공
- 201 Created
	+ 요청 성공해서 새로운 리소스가 생성됨
- 202 Accepted
	+ 요청이 접수되었으나 처리가 완료되지 않았음
	+ ex) 요청 접수 후 1시간 뒤 배치 프로세스가 요청을 처리
- 204 Not Content
	+ 서바가 요청을 성공적으로 수행했지만, <br> 응답 페이로드 본문에 보낼 데이터가 없음
	+ ex) 웹 문서 편집기에서 save 버튼

<br>

#### 3xx (Redirection)
- 요청을 완료하기 위해 유저 에이전트의 추가 조치 필요
- 리다이렉션 : 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, <br> Location 위치로 자동 이동
- 영구 리다이렉션 : 301, 308
	+ 특정 리소스의 URI가 영구적 이동
	+ 원래의 URL을 사용 X, 검색 엔진 등에서도 변경 인지
	+ ex) /members -> /users
	+ 301 Moved Permanently
		- 리다이렉트시 요청 메서드가 GET으로 변할 수도, <br> 본문이 제거될 수도 있음
	+ 308 Permanent Redirect
		- 301과 기능은 같음
		- 리다이렉트시 요청 메서드와 본문 유지
- 일시 리다이렉션 : 302, 307, 303
	+ 리소스의 URI가 일시적으로 변경
	+ 따라서 검색 엔진 등에서 URL을 변경하면 안됨
	+ 주문 완료 후 주문 내역 화면으로 이동
	+ 302 Found
		- 리다이렉트시 요청 메서드가 GET으로 변할 수도, <br> 본문이 제거될 수도 있음
	+ 307 Temporary Redirect
		- 302과 기능은 같음
		- 리다이렉트시 요청 메서드와 본문 유지
	+ 303 See Other
		- 302와 기능은 같음
		- 리다이렉트시 요청 메서드가 GET으로 변경
	+ PRG : Post/Redirect/Get (일시 리다이렉션 예시)
		- 사용 전 : POST로 주문 후에 웹 브라우저를 새로고침하면 <br> 새로고침은 다시 요청이기에 중복 주문될 수 있음
		- POST로 주문 후에 새로고침으로 인한 중복 주문 방지
		- POST로 주문 후에 주문 결과 화면을 GET 메서드로 리다이렉트
		- 새로고침해도 결과 화면을 GET으로 조회
		- 중복 주문 대신에 결과 화면만 GET으로 다시 요청
		- <그림자료> <br>
		![image](https://user-images.githubusercontent.com/56823099/151924346-ab7b0ede-88ac-45bb-9d5d-9b80be808dd8.png)
		- 사용 후 : URL이 이미 POST -> GET으로 리다이렉트 됨 <br> 새로고침해도 GET으로 결과 화면만 조회
- 특수 리다이렉션 :  304
	+ 결과 대신 캐시를 이용
	+ 304 Not Modified
		- 캐시를 목적으로 사용
		- 클라이언트에게 리소스가 수정되지 않았음을 알려줌 <br> 따라서 클라이언트는 로컬PC에 저장된 캐시 재사용 (캐시로 리다이렉트)
		- 304 응답은 응답에 메시지 바디 포함하면 안됨 (로컬 캐시 사용해야 함)
		- 조건부 GET, HEAD 요청시 사용

<br>

#### 4xx (Client Error)
- 클라이언트의 요청에 잘못된 문법 등으로 서버가 요청을 수행할 수 없음
- 오류의 원인이 클라이언트에 있음
- 중요! 클라이언트가 이미 잘못된 요청, 잘못된 데이터를 보내고 있기 때문에, <br> 똑같은 재시도가 실패함
- 400 Bad Request
	+ 클라이언트가 잘못된 요청을 해서 서버가 요청을 처리할 수 없음
	+ 요청 구문, 메시지 등등 오류
	+ 클라이언트는 요청 내용을 다시 검토하고 보내야함
	+ ex) 요청 파라미터가 잘못되거나, API 스펙이 맞지 않을 때
- 401 Unauthorized
	+ 클라이언트가 해당 리소스에 대한 인증이 필요함
	+ 인증(Authentication)되지 않음
	+ 401 오류 발생시 응답에 WWW-Authenticate 헤더와 <br> 함께 인증 방법을 설명
- 403 Forbidden
	+ 서버가 요청을 이해했지만 승인을 거부함
	+ 주로 인증 자격 증명은 있지만, 접근 권한이 불충분한 경우
	+ ex) 어드민 등급이 아닌 사용자가 어드민 등급의 리소스에 접근하는 경우
- 404 Not Found
	+ 요청 리소스가 서버에 없음
	+ 또는 클라이언트가 권한이 부족한 리소스에 <br> 접근하는 경우 해당 리소스를 숨기고 싶을 때

<br>

#### 5xx (Server Error)
- 서버 문제로 오류 발생
- 서버에 문제가 있기 때문에 재시도하면 성공할 수도 있음 (복구 되거나 등)
- 500 Internal Server Error
	+ 서버 내부 문제로 오류 발생
	+ 애매하면 500 오류
- 503 Service Unavailable
	+ 서버가 일시적인 과부하 또는 예정된 작업으로 <br> 잠시 요청을 처리할 수 없음
	+ Retry-After 헤더 필드로 얼마 뒤에 복구되는지 보낼 수도 있음

<br>

#### 출처

[모든 개발자를 위한 HTTP 웹 기본 지식 by 김영한](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/) 
