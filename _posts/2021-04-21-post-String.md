---
title: C++ String 메서드
categories:
- C++
excerpt: "String 메서드 정리"
feature_text: |
  ## C++ String
  String
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---
string 메서드 정리해놓습니다!  
&nbsp;

+ s.insert() -> 원하는 부분에 추가
	- s.insert(a, ss) -> a번째 인덱스에 문자열 ss 추가!
+ s.erase() -> 원하는 부분 삭제
	- s.erase(a) -> a번째 인덱스부터 끝까지 삭제!
	- s.erase(a,n) -> a번째 인덱스부터 n개 삭제!
+ s.replace() -> 원하는 부분 문자열 대체
	- s.replace(a,n,ss) -> a번째 인덱스부터 n개의 문자열을 문자열 ss로 대체 
+ s.clear() -> 문자열 모두 지움!
+ s.substr() -> 원하는 부분 문자열 생성
	- s.substr(a) -> a번째 인덱스부터 끝까지!
	- s.substr(a, n) -> a번째 인덱스부터 n개!!
+ s1.compare(s2)
	- 두 문자열이 같으면 0, s1이 사전순으로 앞이면 -1, 뒤이면 1
+ stoi(s) -> 문자열 s를 int형으로 변환!
+ to_string(i) -> i를 문자열로 변환!
