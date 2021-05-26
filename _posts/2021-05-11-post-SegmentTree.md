---
title: 세그먼트 트리 알고리즘
categories:
- Algorithm
excerpt: "세그먼트 트리 알고리즘 설명글입니다."
feature_text: |
  ## 세그먼트 트리
  Segment Treel
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

세그먼트 트리 알고리즘 설명글입니다.  
&nbsp;
세그먼트 트리 알고리즘은 연속된 데이터의 합을 O(logN)만에 구하는 알고리즘입니다.  
데이터의 길이인 O(N)만큼 시간이 걸리지만 이진트리로 구현하면 <strong>O(logN)</strong>만에 구할 수 있습니다.  
&nbsp;

<h3>구현</h3>

---

저는 제가 편한대로 update함수는 Bottom-up방식, query함수는 Top-down방식을 사용합니다!  
<strong>리프노드에 원래 데이터 값을 저장하고 부모 노드에 각 자손 노드의 합을 저장해줍니다.</strong>  
벌써 트리가 완성됩니다. 이것이 예시의 update함수인데 트리의 생성, 수정에 사용 가능합니다.  
이제 데이터를 더해줄 수 있어야 하는데 이때 재귀함수를 이용합니다!  
밑에 query함수를 보시면 매개변수로 now, start, end, left, right가 있습니다.  
now는 트리의 인덱스 번호입니다. 값을 구하는데 사용되며, 루트 노드에서부터 시작합니다.  
start는 데이터의 첫 번째 인덱스 end는 데이터의 마지막 인덱스를 의미합니다.  
left와 right는 우리가 구해줘야 하는 데이터의 인덱스번호 라고 생각하시면 됩니다.   
<strong>start와 end의 값을 이분탐색하듯이 나눠가며 트리의 밑으로 내려가다가 left와 right범위 안에 들어오면 그에 맞는 값을 트리에서 리턴해주면 값을 구할 수 있습니다. </strong>  


&nbsp;
---

예시로 백준 2268번 문제 수들의 합 코드입니다.

```c++
#include<cstring>
#include<string>
#include<algorithm>
#include<iostream>
#include<vector>
using namespace std;
typedef long long ll;
ll h = 1, n, m;
vector<ll> seg; 
void update(int idx, ll val) {// Bottom-up 방식
	idx += h - 1;
	seg[idx] = val; // 리프노드에 값을 저장
	while (idx /= 2) // 트리를 한 층씩 올라가면서 트리의 값을 갱신
		seg[idx] = seg[idx * 2] + seg[idx * 2 + 1];
}
ll query(int now, int start, int end, int left, int right) { // Top-down 방식
	if (end < left || right < start) return 0; // start와 end가 구해야 하는 범위를 넘어가면 return 0 
	if (left <= start && end <= right) return seg[now]; // start와 end가 범위 안에 있으면 그만 내려가고 값을 리턴
	int mid = (start + end) / 2; // 반으로 나눠서 탐색하기 위해 중간값을 구해줍니다.
	return query( now * 2, start, mid, left, right) + query(now * 2 + 1, mid + 1, end, left, right);
}
int main()
{
	cin.tie(NULL);
	cout.tie(NULL);
	ios_base::sync_with_stdio(false);
	cin >> n >> m;
	while (h < n) h *= 2; //h는 2씩 곱해가며 n보다 크거나 같게 만듭니다. 리프노드의 크기와 같아진다!
	seg.resize(h * 2); // 트리의 노드의 갯수는 리프노드의 약 2배이므로 2를 곱해서 만든다!
	for (int i = 1; i <= m; i++) {
		int a, b, c;
		cin >> a >> b >> c;
		if (a == 1) update(b,c);
		else cout << query(1, 1, h, min(b,c), max(b,c)) << '\n';
	}
	return 0;
}
```

출처 : [https://www.acmicpc.net/problem/2268](https://www.acmicpc.net/problem/2268)
