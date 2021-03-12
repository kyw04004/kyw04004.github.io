---
title: C++ 띄워쓰기 입력 받기
categories:
- C++
excerpt: "C++ getline함수 설명글입니다."
feature_text: |
  ## C++ 띄워쓰기 입력 받기
  getline
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"





---

C++에서 띄워쓰기를 입력받는 것을 잘 까먹게 되서 포스팅합니다!  

getline함수를 이용하면 되는데요. getline(cin, 문자열 변수);를 하시면 됩니다.  

getline을 한번 사용하시면 버퍼에 입력이 남게 되기때문에 버퍼를 비워주셔야 합니다.  

그래서 저는 cin.clear(); 를 사용해줍니다!  

```c++
#include<iostream>
#include<cstring>
#include<string>
#include<algorithm>
using namespace std;
int main() {
	cin.tie(NULL);
	cout.tie(NULL);
	ios_base::sync_with_stdio(false);
	string str;
	getline(cin, str);
	cin.clear();
	cout << str << '\n';
	return 0;
}
```
