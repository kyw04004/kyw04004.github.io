---
title: 다익스트라 알고리즘
categories:
- Algorithm
excerpt: "다익스트라 알고리즘 설명글입니다."
feature_text: |
  ## 다익스트라
  Dijkstra
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

다익스트라 알고리즘 설명글입니다. <br>
다익스트라 알고리즘은 <strong>하나의 정점에서 다른 모든 정점으로 가는 최단 경로</strong>를 구하는 알고리즘입니다. <br>
<strong>가중치는 양수의 값만</strong> 가져야 한다! 그렇지않으면 무한대로 갱신되서 프로그램이 종료되지 않습니다!
다이나믹 프로그래밍을 활용하며, 우선순위 큐를 사용하는 것이 특징입니다.<br>
시작 정점을 기준으로 연결된 정점이 최단 거리를 갱신할 수 있다면 갱신해가면서 정점들을 탐색하면서 동작합니다. <br>
시간복잡도는 우선순위 큐를 사용하기에 <strong>O(ElogV)</strong> 입니다. <br><br>
다익스트라 코드 예시입니다. 백준 1753번 최단경로 문제입니다.<br>

```c++
#include <vector>
#include <iostream>
#include <algorithm>
#include <queue>
#include <functional>
using namespace std;
typedef pair<int, int> P;
int V, E, S, dist[20005];
vector<P> v[20005];
priority_queue<P, vector<P>, greater<P>> pq;
void dijk(int st) {
	dist[st] = 0;
	pq.push({0, st});
	while (!pq.empty()) {
		int node = pq.top().second;
		int costSum = pq.top().first;
		pq.pop();
		if (costSum > dist[node]) continue;
		for (int i = 0; i < v[node].size(); i++) {
			int nextNode = v[node][i].first;
			int nextCost = v[node][i].second;
			if (costSum + nextCost < dist[nextNode]) {
				dist[nextNode] = costSum + nextCost;
				pq.push({dist[nextNode], nextNode});
			}
		}
	}
}
int main() {
	cin.tie(NULL);
	cout.tie(NULL);
	ios_base::sync_with_stdio(false);
	cin >> V >> E >> S;
	for (int i = 1; i <= V; i++) dist[i] = 1e9;
	for (int i = 1; i <= E; i++) {
		int s, e, w;
		cin >> s >> e >> w;
		v[s].push_back({ e, w });
	}
	dijk(S);
	for (int i = 1; i <= V; i++) {
		if (dist[i] == 1e9) cout << "INF\n";
		else cout << dist[i] << '\n';
	}
	return 0;
}
```

출처 : [https://www.acmicpc.net/problem/1753](https://www.acmicpc.net/problem/1753)
