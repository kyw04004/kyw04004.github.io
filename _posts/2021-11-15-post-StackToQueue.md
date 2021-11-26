---
title: 스택 2개로 큐 구현
categories:
- Etc
excerpt: "스택 2개로 큐 구현한 소스코드입니다."
feature_text: |
  ## 스택 2개로 큐 구현
  스택 2개로 큐 구현
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"
---
## 스택 2개로 큐 구현

- 스택 2개로 큐를 구현한 소스코드입니다. 백준의 큐(10845번) AC 받은 코드입니다.

```c++
#include<iostream>
#include<string>
#include<stack>
using namespace std;
stack<int> s1, s2;
int N;
int main(void) {
	cin.tie(NULL);
	cout.tie(NULL);
	ios_base::sync_with_stdio(false);
	cin >> N;
	for (int i = 0; i < N; i++) {
		string command;
		cin >> command;
		if (command == "push") { //push는 첫 번째 스택에 그대로 쌓으면 됩니다.
			int num; cin >> num;
			s1.push(num);
		}
		if (command == "pop") { 
			if (!s2.empty()) {//두 번째 스택이 비지 않았으면 top
				cout << s2.top() << '\n';
				s2.pop();
			}
			else {//두 번재 스택이 비었으면
				while (!s1.empty()) {//첫 번째 스택을 두 번째 스택으로 이동
					s2.push(s1.top());
					s1.pop();
				}
				if (s2.empty()) cout << "-1\n";//두 번재 스택이 또 비면 -1
				else {
					cout << s2.top() <<'\n';// 아니면 top
					s2.pop();
				}
			}
		}
		if (command == "size") { // 스택 2개의 size의 합
			cout << s1.size() + s2.size() << '\n';
		}
		if (command == "empty") { // 스택 2개다 비었으면 1 아니면 0
			if (s1.empty() && s2.empty()) cout << "1\n";
			else cout << "0\n";
		}
		if (command == "front") { // 큐의 맨 앞 원소 출력
			if (!s2.empty()) {// 두 번째 스택이 비지 않았으면 top
				cout << s2.top() << '\n';
			}
			else { // 두 번째 스택이 비었으면
				while (!s1.empty()) { // 첫 번째 스택을 두 번째 스택으로 이동
					s2.push(s1.top());
					s1.pop();
				}
				if (s2.empty()) cout << "-1\n";//두 번째 스택이 비었으면 -1
				else cout << s2.top() << '\n';//두 번째 스택이 비지 않았으면 top
			}
		}
		if (command == "back") { // 큐의 맨 마지막 원소 출력
			if (!s1.empty()) { //첫 번째 스택이 비지 않았으면 top
				cout << s1.top() << '\n';
			}
			else { // 첫 번째 스택이 비었으면
				while (!s2.empty()) { //두 번째 스택을 첫 번째 스택으로 이동
					s1.push(s2.top());
					s2.pop();
				}
				if (s1.empty()) cout << "-1\n";// 첫 번째 스택이 비었으면 -1
				else cout << s1.top() << '\n';//첫 번째 스택 비지 않았으면 top
			}
		}
	}
	return 0;
}
```

문제 출처 :  [https://www.acmicpc.net/problem/10845](https://www.acmicpc.net/problem/10845)
