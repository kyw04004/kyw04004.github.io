---
title: equals & hashcode
categories:
- JAVA
excerpt: "equals와 hashcode에 대한 포스팅입니다."
feature_text: |
  ## equals & hashcode
  JAVA
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

### equals란?
- Object 클래스에 정의된 메서드
- 2개의 객체가 동일한지 검사하기 위한 메서드
- 즉, 2개의 객체가 가리키는 곳이 동일한 메모리 주소인지
- 동일한 문자열 2개를 생성하면 2개의 문자열은 서로 다른 메모리 상에 할당되지만,<br> String  클래스는 eqauls를 재정의해서 true를 반환

<br>

### equals 메서드 구현 방법
- == 연산자를 사용해 입력이 자기 자신의 참조인지 확인
- instanceof 연산자로 입력이 올바른 타입인지 확인
- 입력을 올바른 타입으로 형변환
- 입력 객체와 자기 자신의 대응되는 핵심필드들이 모두 일치하는지 하나씩 검사

<br>

### equals 주의사항
- 대칭적, 추이성, 일관성 확인
- equals 재정의할 땐 hashCode도 반드시 재정의
- 너무 복잡하게 해결 X
- Object 외의 타입을 매개변수로 받지 말아라
- 꼭 필요한 경우가 아니면 재정의하지 말아라
	+ 많은 경우에 Object의 equals가 원하는 비교를 정확히 해줌

<br>

### hashCode란?
- Object 클래스에 정의된 메서드
- 객체를 식별하는 하나의 정수값
- HashTable과 같은 자료구조를 사용할 때 <br>데이터가 저장되는 위치를 결정하기 위해 사용
- 재정의한 hashCode는 Object의 API 문서에 기술된 일반 규약을 따라야하며, <br> 서로 다른 인스턴스라면 되도록 해시코드도 서로 다르게 구현해야 한다.

<br>

### equals와 hashcode
- 동일한 객체는 동일한 메모리 주소를 갖는다는 것을 의미하므로, <br>동일한 객체는 동일한 해시코드를 가져야 함
- 하지만, 서로 다른 객체도 동일한 해시코드를 가질 수 있다.
- 단, 다른 객체에 대해서는 다른 값을 반환해야 해시테이블의 성능이 좋아진다.
- equals를 재정의한다면, hashCode도 재정의해야 함
- 그렇지 않으면 hashCode 일반 규약을 어기게 되어 해당 클래스의 인스턴스를 <br>HashMap이나 HashSet 같은 컬렉션의 원소로 사용할 때 문제를 일으킴
- AutoValue 프레임워크를 사용하면 멋진 equals와 hashCode를 알아서 작성해주고 테스트를 건너뛰어도 됨.
	+ IDE들도 이런 기능을 일부 제공

<br>

### 출처
[https://mangkyu.tistory.com/101](https://mangkyu.tistory.com/101) <br>
[이펙티브 자바](https://book.naver.com/bookdb/book_detail.nhn?bid=14097515) <br>
