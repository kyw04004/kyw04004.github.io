---
title: C++ 우선순위 큐 compare 함수 만들기
categories:
- C++
excerpt: "우선순위 큐 compare 함수 설명글입니다."
feature_text: |
  ## C++ 우선순위 큐 compare 함수 만들기
  priority_queue compare
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"





---

C++에서 우선순위 큐에서 compare 함수 사용법 포스팅합니다!  

그냥 배열이나 벡터에서 compare 함수를 정의할 때는 bool compare(int a, int b) {...}  

이런 식으로 정의하면 사용이 가능했었는데 priority_queue에서는 다릅니다!  

struct compare 안에 bool operator() (int a, int b) {...} 이런 식으로 사용합니다!  

bool operator 함수 안에는 기존에 bool compare 만들었던 것처럼 하시면 됩니다.  

기존에 less나 greater을 사용했던 자리에 compare을 적어주시면 사용가능합니다.  

밑에 코드는 a, b, c 중에서 c, b, a순의 우선순위로 내림차순으로 정렬하는 코드입니다.  

배열이나 벡터에서 compare 함수를 정의할 때와 반대로 동작합니다.



```c++
struct element {
	int a;
	int b;
	int c;
};
struct compare {
	bool operator() (element A, element B) {
		if (A.a != B.a) return A.a < B.a;
		else if (A.b != B.b) return A.b < B.b;
		else if (A.c != B.c) return A.c < B.c;
	}
};
priority_queue<element, vector<element>, compare> pq;
```
