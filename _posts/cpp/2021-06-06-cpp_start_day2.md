---
title:  "씹어먹는 C++ 2일차"
excerpt: 2장 c++ 참조자(레퍼런스)의 도입

categories:
  - 'cpp'
tags:
  - cpp
  - book

toc: true
toc_sticky: true

date: 2021-06-06
last_modified_at: 2021-06-06

---

❗참고 : <https://modoocode.com/135>

# 참조자 (Reference)

* C++에서 지원하는 세번째 변수 형태
* reference의 format
  + non-const 값 참조
  + const 값 참조
  + r-value 참조

```
type& 참조자 = 변수;
```

* 참조자(refereence)를 활용한 예제
  + int형 변수 a를 선언
  + 변수 a의 참조자로 another_a를 정의
    - 참조자를 지정하는 방법은 가리키고자 하는 타입 뒤에 &를 붙임
    - ex) int형의 참조자는 int&, double형의 참조자는 double&, int* 형의 참조자는 int*&
  + another_a는 a의 다른 이름임을 컴파일러에게 명시해줌

```cpp
#include <iostream>

int main() {
  int a = 3;
  int& another_a = a;

  another_a = 5;
  std::cout << "a : " << a << std::endl;
  std::cout << "another_a : " << another_a << std::endl;

  return 0;
}
```

# Reference의 format

* non-const 값 참조

```cpp
int a = 10;
int& another_a = a;  // 일반 변수의 reference
```

* const 값 참조

```cpp
#include <iostream>

int main() {
  int& ref = 4;  // literal에 대한 reference를 할 수 없음

  const int &ref = 4;  // const reference로 선언 시, literal에 대한 참조 가능
}
```

* r-value 참조
  + r-value 주소값을 취할 수 없는 값, 코드의 오른쪽에만 있을 수 있는 값
  + 참고 : <https://modoocode.com/189>

* r-value?

```cpp
std::string a = "abc";  // l-value (a) = r-value ("abc")
std::string b = a;      // l-value (b) = l-value (a)
```



# reference와 pointer의 차이점

## 1. reference는 반드시 처음에 누구의 별명이 될 것인지 지정해야 함
* 선언과 동시에 초기화 해야함

```cpp
int& another_a;  // 불가능한 코드
int* p;  // 가능한 코드
```

## 2. reference는 한 번 별명이 되면 다른 이의 별명이 될 수 없다.
* 한 변수의 reference로 지정되면 다른 변수의 reference로 지정될 수 없음
* reference

```cpp
int a = 10;
int& another_a = a;  // another_a는 a의 reference

int b = 20;
int& another_a = b;  // a = b 와 같은 의미

&another_a = b;  // &a = b 와 같은 의미이므로 위험한 코드...
```

* pointer

```c
int a = 10;
int* p = &a;  // p는 a를 가리킴

int b = 3;
p = &b;  // p는 b를 가리킴
```

## 3. reference는 메모리 상에 존재하지 않을 수도 있다.

* reference (경우에 따라 존재할수도, 존재하지 않을 수도 있음)

```cpp
int a = 10;
int& another_a = a;  // 컴파일러가 another_a를 위해 메모리 상 공간을 할당할 필요 없음
```

* pointer

```c
int a = 10;
int*p = &a;  // p는 메모리 상에서 8바이트를 차지
```

* 3-2. 함수의 인자로 reference를 활용
  + 복사에 비용이 추가되지 않아 다양하게 활용됨

```cpp
#include <iostream>

int change_val(int &p) {
  p = 3;

  return 0;
}
int main() {
  int number = 5;

  std::cout << number << std::endl;
  change_val(number);  // int& p = number
  std::cout << number << std::endl;
}
```


# reference의 활용

* reference와 배열
  + reference의 배열
    - C++ 규정 표준안 8.3.2/4 : reference의 reference, reference의 pointer과 함께 존재할 수 없음

```cpp
    int a, b;
    int& arr[2] = {a, b};
```

  + 배열의 reference

```cpp
  #include <iostream>

  int main() {
    int arr[3] = {1, 2, 3};
    int(&ref)[3] = arr;
    // ref 가 arr을 참조하도록 함
    // pointer와 다르게 reference가 배열을 참조하기 위해서는 배열의 크기를 명시해야함

    ref[0] = 2;
    ref[1] = 3;
    ref[2] = 1;

    std::cout << arr[0] << arr[1] << arr[2] << std::endl;
    return 0;
  }
```

* 함수와 reference
  + Call by reference (함수의 매개변수)
  + 주의 : 특정 함수의 지역 변수의 reference
    - 컴파일 warning 및 실행 시 segfault 발생됨

```cpp
int& func() {
  int a = 2;
  return a;
}

int main() {
  int b = func();
  b = 3;
  return 0;
}
```
    
  + 외부 변수의 레퍼런스를 리턴
    - 복사할 변수의 크기와 관계 없이 주소값 1번의 복사만 수행되어 효율적

```cpp
    int& function(int& a) {
      a = 5;
      return a;
    }

    int main() {
      int b = 2;
      int c = function(b);  // c = b
      return 0;
    }
```


- - -

* r-value 참조에 대해서는 추가 공부 필요;
