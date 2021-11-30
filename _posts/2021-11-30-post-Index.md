---
title: 데이터베이스 인덱스
categories:
- Database
excerpt: "데이터베이스 인덱스에 대한 포스팅입니다. "
feature_text: |
  ## 데이터베이스 인덱스
  B+ Tree
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

#### 인덱스란?
- 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조
- 없으면 Full scan해서 처리속도 낮음
- 사용 이유 데이터들이 정렬되어 있는 점 
- 구현하기 위해서 B+ Tree(MySQL) 사용할 수 있음
	+ Hash Table이 안되는 이유는   단 하나의 데이터를 탐색에 최적화
	+ RedBlackTree가 안되는 이유는 하나의 노드가 가지는 데이터 개수가 1개
  
  
#### B+ Tree란?
- B-Tree의 확장개념으로, B-Tree의 경우 leaf 또는 branch 노드에 key와 data를 담을 수 있음
- 하지만, B+Tree의 경우 branch 노드에 key만 담아두고, data는 담음
- 오직 leaf 노드에 key와 data를 저장하고, leaf 노드끼리 linked list로 연결됨
- leaf 노드를 제외하고 데이터를 담아두지 않기 때문에 메모리를 더 확보함으로써
더 많은 key들을 수용 
- 하나의 노드에 더 많은 key들을 담을 수 있기에 트리의 높이는 더 낮음
- Full Scan 시, B+Tree는 leaf 노드에 모든 데이터가 있기에 한 번의 선형탐색만 하면 되기에 B-Tree보다 빠름
- 단점으로 B-Tree의 경우 루트에서 끝날 수도 있는 것을 B+Tree에서는 무조건 leaf까지 내려가야함
- 균형 트리이므로 어떤 값에 대해서도 같은 시간에 결과를 얻을 수 있다 (logN)
  
  
#### 인덱스 관리
- insert : 새로운 데이터에 대한 인덱스 추가
- delete : 삭제하는 데이터의 인덱스를 사용하지 않음
- update : 기존의 인덱스를 사용하지 않고, 갱신된 데이터에 대해 새로운 인덱스 추가
  
  
#### 인덱스의 장점

- 테이블을 조회하는 속도와 그에 따른 성능 향상
- 전반적인 시스템 부하를 줄임
  
  
#### 인덱스의 단점
- 정렬 상태 유지해야 함
- 저장 공간 필요 (전체의 약 10프로)
- 전체 데이터의 10~15프로이하 검색만 효율적
  
  
#### 레퍼런스

[https://mangkyu.tistory.com/96](https://mangkyu.tistory.com/96)<br>
