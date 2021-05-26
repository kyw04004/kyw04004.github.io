---
title: 유니온 파인드 && 크루스칼 알고리즘
categories:
- Algorithm
excerpt: "유니온파인드, 크루스칼 알고리즘 설명글입니다."
feature_text: |
  ## 유니온파인드 && 크루스칼
  Union-Find && Kruskal
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"

---

유니온 파인드와 크루스칼 알고리즘 설명글입니다.  

<h3>유니온 파인드(Union-Find)</h3>

두 개의 정점이 서로 같은 그래프에 속하는지 판별하는 알고리즘이다.  
find 함수를 통해서 최상위 부모를 찾는다.  재귀 함수를 통해서 배열을 타고 올라가서 확인한다.  
merge 함수를 통해서 그래프를 합친다.  가장 최상위 부모에서 밑으로 연결해서 편중 현상을 피한다.   
isUnion 함수를 통해서 같은 그래프인지 아닌지(사이클을 만드는지 아닌지) 확인할 수 있다! 

시간복잡도는 <strong>O(logV)</strong> 이다!

&nbsp;

<h3>크루스칼(Kruskal)</h3>

음수 가중치가 없는 무향 그래프가 주어질 때, <strong>그리디하게 최소 스패닝 트리를 만드는 알고리즘</strong>이다. 
최소 스패닝 트리(MST)란? 간선 가중치의 합이 가장 작은 스패닝 트리!  
스패닝 트리란? 모든 정점을 포함하는 트리 형태의 서브 그래프!  
우선순위 큐를 사용하므로 시간복잡도는 <strong>O(ElogE)</strong> 이다!  
프림의 시간복잡도는 O(ElogV)이므로 비교해서 사용하길 권장한다.    

&nbsp;
동작방식!  

1. 모든 간선을 우선 순위 큐에 저장!
2. 제일 가중치가 작은 간선부터 쭉 보면서 간선이 사이클을 만들지 않으면 연결해준다!
3. 끝!  간단!

```c++
#include <iostream>
#include <algorithm>
#include <queue>
#include <functional>
using namespace std;
typedef pair<int, pair<int, int>> P;
priority_queue<P, vector<P>, greater<P>> pq;
int V, E, parent[10005],ans;
int find(int x) { // 부모 찾기!
	if (parent[x] == x) return x;
	return parent[x] = find(parent[x]);
}
void merge(int x, int y) { // 두 개의 정점의 포함된 그래프를 합친다!
	x = find(x);
	y = find(y);
	if (x == y) return;
	parent[y] = x;
}
bool isUnion(int x, int y) { // 같은 그래프인지 아닌지 확인!
	x = find(x);
	y = find(y);
	if (x == y) return true;
	else return false;
}
void kruskal() {
	while (!pq.empty()) {
		int x = pq.top().second.first, y = pq.top().second.second;
		if (!isUnion(x, y)) {
			merge(x, y);
			ans += pq.top().first;
		}
		pq.pop();
	}
}
int main() {
	cin.tie(NULL);
	cout.tie(NULL);
	ios_base::sync_with_stdio(false);
	cin >> V >> E;
	for (int i = 1; i <= V; i++) parent[i] = i;
	for (int i = 1; i <= E; i++) {
		int s, e, w;
		cin >> s >> e >> w;
		pq.push({ w, {s, e} });
	}
	kruskal();
	cout << ans;
	return 0;
}
```

출처 : [https://www.acmicpc.net/problem/1197](https://www.acmicpc.net/problem/1197)
