---
layout: single
title: "[C++] 참조 전달 방식"
categories: cpp
tag: [cpp]
toc: true
typora-root-url: ../
sidebar:
  nav: "docs"
---

# 참조 전달 방식

## 함수의 인자 전달 방식

### 값 전달 방식(Call By Value)

``` c++
Struct StatInfo {
  int hp;
  int attack;
}

void PrintByCopy(StatInfo info) {
  cout << info.hp << endl;
  cout << info.attack << endl;  
}

int main() {
  StatInfo info;
  info.hp = 100;
  info.attack = 10;
  
  printByCopy(info);
}
```

호출하는 코드에 넘겨주는 실인자 값이 함수의 매개변수로 복사되어 전달되는 방식입니다.

실제 객체인 info를 손상 시키지 않는 장점이 있습니다.

그러나 매개변수로 객체를 복사하기에 메모리, 시간적 손실이 일어날 수 있습니다.



### 주소 전달 방식 (Call By Address)

``` c++
Struct StatInfo {
  int hp;
  int attack;
}

void printByPtr(StatInfo* info) {
  cout << info->hp << endl;
  cout << info->attack << endl;  
}

int main() {
  StatInfo info;
  info.hp = 100;
  info.attack = 10;
  
  printByPtr(&info);
}
```

매개변수를 포인터 타입으로  직접 주소로 전달하는 방식입니다.

실제 객체의 주소값을 넘겨 함수 내에서 실제 객체의 값을 변경하고자 할 때 사용됩니다.

값에 의한 호출에 비해 원본 객체를 복사하는 메모리, 시간적 손실이 없습니다.



### 참조 전달 방식(Call By Reference)

``` c++
Struct StatInfo {
  int hp;
  int attack;
}

void printByReference(StatInfo& info) {
  cout << info.hp << endl;
  cout << info.attack << endl;  
}

int main() {
  StatInfo info;
  info.hp = 100;
  info.attack = 10;
  
  printByReference(info);
}
```

c++에서 있는 문법으로 '참조에 대한 호출 방식'으로 많이 사용됩니다.

함수의 매개변수를 참조 타입으로 선언하여 실인와 공간을 공유하도록 하는 인자 전달 방식입니다.

주소 전달 방식에서 매개변수를 주소값으로 전달하고, 함수내에서 ->와 값은 문법을 사용하여 가독성이 떨어지는 것을 보완할 수 있습니다.

## 참조 전달(Call By Reference) 사용 방식

### 문법

``` c++
int main() {
  int number = 1;
  
 	int* ptr = &number; 
  ptr += 4;           // ptr은 주소값 + 4
  
 
  number = 1;
  int& reference = number;
  reference += 4;       //  5
}
```

얼핏보면 참조 전달 방식은 주소 전달 방식과 크게 차이가 나지 않는다고 생각이 들지만 위의 예시를 보면 차이를 알 수 있습니다.

ptr 변수에는 number의 주소값이 들어가 있으며 number의 값을 변경하고자 하면 ptr* += 4;로 작성해야만 합니다.

그러나 참조 전달 방식은 직접으로 reference를 수정하여 값을 변경할 수 있습니다.

``` c++
void printByPtr(StatInfo* info) {
  cout << info->hp << endl;
  cout << info->attack << endl;  
}

void printByReference(StatInfo& info) {
  cout << info.hp << endl;
  cout << info.attack << endl;  
}
```

이는 구조체에서도 주소 전달 방식은 화살표 연산자(->)를 사용하는 반면 참조 전달 방식은 도트 연산자(.)를 사용하는 차이를 보여줍니다.







참조타입 초기화가 필요함!!!

StatInfo* reference;

reference = &info;

--> 오류





