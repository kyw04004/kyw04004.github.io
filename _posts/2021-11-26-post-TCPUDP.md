---
title: TCP와 UDP
categories:
- Network
excerpt: "TCP와 UDP에 대한 포스팅입니다."
feature_text: |
  ## TCP, UDP
  Network
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

TCP와 UDP는 전송 계층에서 데이터를 보내기 위해 사용하는 프로토콜입니다.
기본적이지만 중요한 내용이기에 포스팅하겠습니다.



#### 공통점

- 포트 번호를 이용하여 어떤 서비스에게 데이터를 전달할지 식별
- 데이터 오류 검사를 위한 CheckSum 필드가 존재
  
  
### TCP (Transmission Control Protocol)

- 인터넷상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜
  - IP는 데이터 전송, TCP는 패킷 추적 및 관리
- 연결형 서비스로 가상 회선 방식 제공
  - 발신지와 수신지를 연결하여 패킷을 전송하기 위한 논리적 경로 배정
- 3-way handshaking 과정을 통해 연결 설정
  - 목적지와 수신지를 확실히 하여 정확한 전송을 보장하기 위해 세션을 수립하는 과정
- 4-way handshaking 과정을 통해 연결 해제
- 흐름 제어 및 혼잡 제어
  - UDP보다 느리지만 높은 신뢰성 보장
  - 흐름제어는 데이터 처리 속도를 조절하여 버퍼 오버 플로우 방지
  - 혼잡제어는 네트워크 내의 패킷 수를 넘치게 증가하지 않도록 방지
- 전이중(Full-Duplex) 방식 : 양방향 전송
- 점대점(Point to Point) 방식 : 각 연결이 2개의 종단점
- 연속성보다 신뢰성있는 전송이 중요할 때에 사용하는 프로토콜
- ex) 파일 전송
  
  
### UDP (User Datagram Protocol)

- 데이터를 데이터그램 단위로 처리하는 프로토콜
- 비연결형 서비스로 데이터그램 방식 제공
  - 연결을 위해 할당되는 논리적 경로 없음
- 정보를 주고 받을 때 정보를 보내거나 받는다는 신호절차를 거치지 않음
- UDP헤더의 CheckSum 필드를 통해 최소한의 오류만 검출
  - TCP보다 빠르지만 낮은 신뢰성
- 신뢰성보다는 연속성이 중요한 서비스에 사용하는 프로토콜
- ex) 실시간 서비스 (streaming)
  
  
#### 레퍼런스

[https://mangkyu.tistory.com/15](https://mangkyu.tistory.com/15)<br>
