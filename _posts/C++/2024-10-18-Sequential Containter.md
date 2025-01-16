---
layout: single
title: "[C++] 시퀀스 컨테이너(Sequence Containter)"
categories: cpp
tag: [cpp]
toc: true
typora-root-url: ../
sidebar:
  nav: "docs"
---

# 순차 컨테이너(Sequential Container)

## 순차 컨테이너란

### 개념

**순차 컨테이너(Sequential Container)는 데이터를 일정한 순서대로 저장하고 관리하는 자료구조입니다**. 순차적으로 요소를 배열하고, 요소의 삽입과 삭제 작업이 주로 특정 위치에서 이루어지는 특징이 있습니다. 대표적인 순차 컨테이너로는 **배열(Array)**, **벡터(Vector)**, **리스트(List)**, **덱(Deque)** 등이 있으며, 각 컨테이너는 특정 용도와 상황에 맞는 특화된 기능을 제공합니다.

순차 컨테이너는 주로 C++ STL(Standard Template Library)에서 사용되며 이 컨테이너들은 빠른 순차 접근이 필요하거나, 동적 크기 조정이 필요한 상황에서 유용하게 쓰입니다.

## 순차 컨테이너의 종류

### 배열(Array)

배열은 **고정 크기의 연속적인 메모리 블록에 요소를 저장**하는 가장 기본적인 자료구조입니다. 모든 요소는 메모리상에서 연속적으로 배치되며 특정 인덱스의 요소에 빠르게 접근 가능 합니다.

```c++
int main() {
  // 배열의 초기화 방법
  int array[10];
  for (int i = 0; i < 10; i++) {
    array[i] = i;                      // 배열에 임의 접근 
  }  
  int numbers1[5] = {};                // 초기화 하지 않으면 가비지 값이 들어가게 됨.
  int numbers2[10] = {1,2,3,4,5};      //  0~4 인덱스 까지는 선언한 값이 들어가고 나머지 인덱스에는 0으로 초기화가 됨
  int numbers3[] = {1,2,3,4,5};        // 선언한 값의 크기만큼 인덱스가 할당되게 됨. 이 예시에서는 5.
	const int size = 3;                             
  int arr[size];                       // Stack영역에 고정 크기로 선언해야하기에 상수로만 크기를 선언할 수 있습니다.
}
```

아래와 같이 포인터를 이용하여 힙(Heap)영역에 배열을 선언 가능합니다.

```c++
int main()
{ 
    int *arr = new int[5]{1, 2, 3, 4, 5};

    for (int i = 0; i < 5; i++)
        cout << *(arr + i) << endl;
		
 		delete arr;
  
    return 0;
}
```

### 벡터(Vector)

벡터(vector)는 **크기를 동적으로 변경할 수 있는 배열**입니다. **추가적인 메모리를 할당하여 요소를 추가하거나 제거할 수 있으며, 이는 C++의 `std::vector`에서 지원됩니다.** 

#### 벡터의 선언 및 초기화

```c++
#include <vector>
int main() {
  std::vector<int> vec = {1, 2, 3, 4, 5};  // 벡터 선언 및 초기화 1)
 	std::vector<int> vec2(10, 0);            // 백터 선언 및 초기화 2) 10의 사이즈로 선언하며, 0으로 초기화
	std::vector<int> vec3 = vec2;            // 백터 선언 및 초기화 3) 복사 생성자를 이용
 	
  vec3.resize(11);                         // 10인 사이즈를 11로 설정
  vec3.reserve(100);                       // capacity의 값을 100으로 설정
  
  return 0;
}
```

벡터는 앞서 설명한 배열과 다르게 동적으로 크기가 조절됩니다. 크기를 조절하는 방식은 기존 벡터에 새로 요소를 추가하여 임계점을 넘는다면 새로운 메모를 할당하고 기존의 벡터의 데이터를 복사하는 방식으로 크기가 증가됩니다.

여기서 임계점이라고 한 이유는 요소를 추가하는 매번 메모리를 할당한다면 비효율적이기에 vector가 가지고 있는 capacity 값과 증가된 size의 값이 같은 경우 새로 메모리를 할당하는 방식으로 메모리가 수정됩니다.

여기서 Reverse() 함수는 capacity 값을 임의 설정하여 메모리의 크기 원하는 크기로 할당하는 방식이며, resize() 함수는 현재 vector가 가지고 있는 값들의 사이즈를 수정하는 방식입니다. reverse를 통하여 매번 메모리를 재할당하는 현상을 줄일 수 있습니다.

#### 데이터 삽입 / 삭제 / 접근

``` C++
#include <vector>
int main() {
	vector<int> vec1 = {1,2,3,4};
  // 끝 삽입/삭제 
  vec1.push_back(5);										// 요소 추가 {1,2,3,4,5}
  vec1.pop_back();                      // 요소 제거 {1,2,3,4}
  
  // 맨앞 삽입/삭제
  vector<int>::iterator it = v.begin();
  v.insert(it, 2);                      // 요소 추가 {2,1,2,3,4}
  v.erase(v.begin);                     // 요소 제거 {1,2,3,4}
  
  // 중간 삽입/삭제
  v.insert(v.begin()+1, 2, 3);          // 요소 추가 {1,3,3,2,3,4} 
  v.erase(v.begin()+1, v.begin()+3);    // 요소 삭제 {1,2,3,4}
  
  int arr[] = {10, 20, 30};
  v.insert(v.begin()+1, arr, a+2);      // 요소 추가 {1,10,20,2,3,4} 
  v.erase(v.begin()+1, v.begin()+3);    // 요소 삭제 {1,2,3,4}
  
  // 접근
  cout << vec1.back() << endl;          // 마지막 요소를 반환 / 출력 : 4
  cout << vec1.front() << endl;         // 첫 요소를 반환    / 출력 : 1
  
  // 임의 접근
  for (int i = 0; i < vec1.size(); i++)
 		cout << vec1[i] << endl; 	          // 출력 : 1 2 3 4 5
  
  return 0;
}
```

벡터는 삽입/삭제로 push_back/pop_back을 제공합니다. 마지막 요소를 삽입/삭제하는 함수이며, 벡터는 연속된 자료구조이기에 다른 삽입/삭제는 비효율적입니다. 또한 연속적인 자료구조이기에 임의 접근이 가능합니다.

#### 반복자(Iterator)

STL은 이터레이터(Iterator)를 지원합니다. 이는 컨테이너 원소를 순회하는 방법을 추상화한 객체들을 뜻하며, 이를 이용하면 STL 내부의 자료에 접근하는 방법을 표준화할 수 있습니다.

```c++
#include <vector>
int main() {
  vector<int> v = {1,2,3,4};
  vetor<int>::iterator it = v.begin();
  
  for (vector<int>::iterator i = it; i != v.end(); it++)
    cout << *it << endl;
  
  return 0;
}
```

### 리스트

연결 리스트

동작 원리

중간 삭제 /삽입

처음 / 끝 삽입

임의 접근

단일 / 이중 /연결

Node

단일

[1] -> [2]

이중

[1] <-> [2]

### 디큐(Deque)

**Deque**



Double-ended queue



배열을 이용하나 여러가지의 배열을 사용하여 이어붙이는 형태의 시퀀스 컨테이너

중간 삽입 삭제

처음 /끝 삽입 삭제

임의 접근
