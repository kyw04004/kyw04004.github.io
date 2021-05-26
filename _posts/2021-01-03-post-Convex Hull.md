---
title: 기하 알고리즘 - Convex Hull편
categories:
- Algorithm
excerpt: "기하 알고리즘 Convex Hull 설명글입니다."
feature_text: |
  ## 기하 알고리즘
  Convex Hull
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"




---

기하 알고리즘 Convex Hull 설명글입니다.

이번에는 Convex Hull에 대해서 설명하겠습니다.

Convex Hull은 볼록 껍질을 구하는 것인데 볼록 껍질이란 2차원 평면 상에서 주어진 점들을 일부 이용하여 만든 볼록 다각형이다. 이때 나머지 점들은 모두 볼록 다각형 안에 있어야 한다. 

볼록껍질을 구하는 알고리즘에는 대표적으로 그라함 스캔(Graham's Scan) 알고리즘이 있다.



동작 원리

1.기준점을 잡는다.

- 보통 제일 아래에 있는 점을 기준으로 한다. (y값이 같은게 존재한다면 그 중 제일 왼쪽인 점)

* 제일 왼쪽인 점을 기준으로 하여 동작할 수도 있다.

2.정렬을 한다

* 기준점이 x축 위에 있다고 생각할 때 나머지 점들과의 각도로 오름차순정렬을 한다.

* 어떻게? 비교할 두 점 A와 B가 있다고 할 때, CCW(기준점, A, B)를 해서 양수값이 나온다면, 즉 반시계방향이라면 A보다 B가 더 큰 각도를 가졌음을 알 수 있다. 시계방향이라면 A가 각도가 더 크다. 일직선이면? y축 기준으로 정렬하자. 같다면 x축 기준. 물론 오름차순

3.볼록 껍질을 구한다.

* 정렬된 점들을 돌면서 반시계 방향이라면 push하고 시계 방향이거나 일직선이면 pop한다.

```c++
vector <int> s;
s.push_back(0);
s.push_back(1);
	int idx = 2;
	while (idx < n) {
		if (s.size() >= 2 && ccw(dot[s[s.size()-2]], dot[s[s.size() - 1]], dot[idx]) <= 0)
			s.pop_back();
		else s.push_back(idx++);
	}
```
