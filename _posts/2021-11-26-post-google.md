---
title: 브라우저에 'www.google.com'을 치면 일어나는 일
categories:
- Network
excerpt: "웹의 동작방식에 대한 포스팅입니다."
feature_text: |
  ## 브라우저에 'www.google.com'을 치면 일어나는 일
  Network
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

#### 1. 브라우저에 'www.google.com' 을 입력

#### 2. 브라우저는 캐싱된 DNS 기록들을 통해 해당 도메인 주소의 IP 주소 확인

- 캐시 확인 순서 (브라우저, OS, router, ISP)
- DNS(Domain Name System)란 도메인 주소와 IP 주소를 저장하고 있는 데이터베이스

#### 3.  요청한 URL이 캐시에 없으면, ISP의 DNS 서버가 DNS Query를 통해 검색하여 IP 주소를 찾음

- ISP란 인터넷 서비스 공급자의 약자로 유료로 집이나 사업장에 인터넷을 제공하는 공급자

- DNS query의 목적은 여러 다른 DNS 서버들을 검색해서 해당 사이트의 IP 주소를 찾는 것
- IP 주소를 찾을 때까지 DNS 서버에서 다른 DNS 서버를 오가면서 반복적으로 검색하던지 못 찾아서 에러가 발생할 때까지 검색을 진행

#### 4. 브라우저가 서버와 TCP connection

- 클라이언트와 서버간 데이터 패킷들이 오가게 하기 위함
- TCP/IP 3 way handshake를 통해 connection

#### 5. 브라우저가 웹 서버에 HTTP Request

#### 6. 서버가 요청을 처리하고, response를 생성하여 브라우저에 반환

#### 7. 브라우저가 HTML content를 보여줌

   

#### <그림 자료>
![사진](http://tcpschool.com/lectures/img_webbasic_10.png)<br>
사진 출처 : [http://tcpschool.com/lectures/img_webbasic_10.png](http://tcpschool.com/lectures/img_webbasic_10.png)

  

#### 레퍼런스

[https://devjin-blog.com/what-happen-browser-search/](https://devjin-blog.com/what-happen-browser-search/)<br>
