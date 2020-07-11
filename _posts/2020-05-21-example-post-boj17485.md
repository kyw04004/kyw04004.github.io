---
title: BOJ 17485 | 진우의 달 여행 (Large)
categories:
- Algorithm
excerpt: "이 문제는 DP 혹은 그래프문제입니다."
feature_text: |
  ## BOJ 17485 | 진우의 달 여행 (Large) 
  DP , 그래프이론
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---

이 문제는 DP 혹은 그래프문제입니다. <br>
저는 DP를 공부 중이였기때문에 DP를 사용하여 풀었습니다.

<h4>풀이</h4> 
 문제는 지구에서 달까지 가는데 최소 연료를 사용하는 문제입니다.<br>
정해진 3가지 방향으로 한칸씩 이동 가능하며 두 번 연속 같은 방향에 가지 못합니다.<br>
방향은 각각 0,1,2 로 정의하였고
처음에는 방향이 저장되어있지 않으므로 past값을 3으로 시작해주었습니다. <br>
우주선이 어디서 시작해야 최솟값일줄 모르니 시작점이 (x=1,y=1) (x=1,y=2) ... (x=1,y=m)인 최솟값을 m번 값을 구해서
그 중 최솟값을 정답으로 출력하였습니다. <br>
dp[i][j][전에 이동한 방향] = 최소비용 으로  식을 세웠고
ret = min(ret, go(nx, ny, i) + arr[nx][ny])의 코드로 최소비용을 구했습니다.<br>

```c++
#include<iostream>
#include<cstring>
#include<string>
#include<algorithm>
using namespace std;
int n,m,arr[1001][1001], dp[1001][1001][4], Min = 1e9;
int dx[3] = { 1,1,1 };
int dy[3] = { -1,0,1 };
int go(int x, int y,int past)
{
	if (x == n) return 0;
	int &ret = dp[x][y][past];
	if (ret != -1) return ret;
	ret = 1e9;
	for (int i = 0; i < 3; i++)
	{
		int nx = x + dx[i];
		int ny = y + dy[i];
		if (i == past || nx<1 || nx > n || ny < 1 || ny > m) continue;
		ret = min(ret, go(nx, ny, i) + arr[nx][ny]);
	}
	return ret;
}
int main()
{
	memset(dp, -1, sizeof(dp));
	cin >> n >> m;
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			scanf("%d", &arr[i][j]);
	for (int i = 1; i <= m; i++)
		Min = min(Min, arr[1][i] + go(1, i, 3));
	printf("%d\n", Min);
	return 0;
}
```

출처 : [https://www.acmicpc.net/problem/17485](https://www.acmicpc.net/problem/17485)