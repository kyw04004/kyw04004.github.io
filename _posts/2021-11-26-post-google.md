---
title: 브라우저에 'www.google.com'을 치면?
categories:
- Network
excerpt: "웹의 동작방식에 대한 포스팅입니다."
feature_text: |
  ## 브라우저에 'www.google.com'을 치면?
  Network
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

#### 1. 브라우저에 'www.google.com' 을 입력

<br>

#### 2. 브라우저는 캐싱된 DNS 기록들을 통해 해당 도메인 주소의 IP 주소 확인
- 캐시 확인 순서 (브라우저, OS, router, ISP)
- DNS(Domain Name System)란 도메인 주소와 IP 주소를 저장하고 있는 데이터베이스

<br>

#### 3.  요청한 URL이 캐시에 없으면, ISP의 DNS 서버가 DNS Query를 통해 검색하여 IP 주소를 찾음
- ISP란 인터넷 서비스 공급자의 약자로 유료로 집이나 사업장에 인터넷을 제공하는 공급자
- DNS query의 목적은 여러 다른 DNS 서버들을 검색해서 해당 사이트의 IP 주소를 찾는 것
- IP 주소를 찾을 때까지 DNS 서버에서 다른 DNS 서버를 오가면서 반복적으로 검색하던지 못 찾아서 에러가 발생할 때까지 검색을 진행

<br>

#### 4. 브라우저가 HTTP 요청 메시지 생성
- HTTP 메서드 종류, URL 일부, HTTP 버전 정보, 호스트 정보 등 포함 <br>
![image](https://user-images.githubusercontent.com/56823099/151653931-655e7e02-da75-4db7-838c-3a3eea0479c5.png)

<br>

#### 5. SOCKET 라이브러리를 통해 TCP/IP에 전달
- TCP/IP 3 way handshake를 통해 connection
- HTTP 요청 메시지 전달

<br>

#### 6. TCP/IP 패킷 생성
- 패킷에 HTTP 요청 메시지를 포함

<br>

#### 7. 브라우저가 웹 서버에 HTTP Request
- TCP/IP 패킷을 인터넷망으로 전달

<br>

#### 8. 서버가 요청을 처리
- TCP/IP 패킷을 버리고 HTTP 요청 메시지를 받아서 처리

<br>

#### 9. HTTP 응답 메시지를 생성하여 브라우저에 반환
- 아까와 같이 응답 메시지를 TCP/IP 패킷에 포함시켜서 반환
- HTTP 버전, 상태 코드, 상태 메시지, 컨텐트 정보 등 포함 <br>
![image](https://user-images.githubusercontent.com/56823099/151653947-9b705bdd-dad4-4721-989e-6daf5b58a15b.png)

<br>

#### 10. 브라우저가 HTML content를 보여줌
- HTTP 응답 메시지의 데이터(HTML)를 렌더링

<br>

#### <그림 자료>
![사진](http://tcpschool.com/lectures/img_webbasic_10.png) <br>
사진 출처 : [http://tcpschool.com/lectures/img_webbasic_10.png](http://tcpschool.com/lectures/img_webbasic_10.png)

<br>

#### 출처
[https://devjin-blog.com/what-happen-browser-search/](https://devjin-blog.com/what-happen-browser-search/)<br>
[모든 개발자를 위한 HTTP 웹 기본 지식 by 김영한](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/) 
