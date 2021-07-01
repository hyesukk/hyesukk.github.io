---
title:  "씹어먹는 C++ 8일차"
excerpt: 7장 클래스의 상속

categories:
  - 'cpp'
tags:
  - cpp
  - book

toc: true
toc_sticky: true

date: 2021-07-01
last_modified_at: 2021-07-01

---

❗참고 : <https://modoocode.com/135>

# 표준 string 클래스

* c++의 표준 문자열 클래스
* 짧은 문자열의 경우, 동적 메모리를 할당하지 않고 지역변수로 보관
* 문자열을 복사할 때, 실제 데이터 복사가 아닌 원래 문자열을 가리키기만 함

```cpp
#include <iostream>
#include <string>

int main() {
    std::string s = "abc";

    std::cout << s << std::endl;

    return 0;
}
```

* string 클래스의 인자를 const char *로 받는 생성자를 호출한 형태

* c 언어와의 차이
    + 문자열 비교를 strcmp와 같은 별도 함수를 이용하지 않고, "==", "!=" 를 사용함
        - 연산자 오버로딩을 이용
    + 이 외에 크기 비교 ">=", "<=" 등도 제공
    + 이 외에, length, insert, erase, replace 등의 함수를 지원
