---
layout: single
title: "[C++] 은닉성"
categories: cpp
tag: [cpp]
toc: true
typora-root-url: ../
sidebar:
  nav: "docs"


---

# 은닉성

## 은닉성이란

### 개념

은닉성이란 Data Hiding이라고 하며 멤버 변수나 메서드가 객체에 노출되지 않도록 설정하는 기법입니다. 또한 캡슐화라고도 표현하며 객체의 멤버 변수를 직접 수정하지 못하도록 캡슐로 감싸 보안을 지킵니다.

### 사용 이유

은닉성을 이용하는 이유는 대체적으로 두가지로 아래와 같습니다.

* Data Hiding : 직접 접근하여 수정하면 안되는 데이터, 함수를 감추는 방법
* Encaptualtion : 해당 객체를 접근을 우회하여 하도록 캡슐화 하는 방법

## 접근 지정자란 

### 개념

C++에서는 접근 지정자를 사용하여 변수, 함수에 접근 가능한 범위를 설정합니다.

* public : 접근의 제한이 없음
* protected : 대상 객체를 상속한 하위 객체와 자기 자신의 객체만 접근 가능
* private : 자기 자신의 객체에서만 접근 가능

### 예시

```c++
class Customer 
{
public:
	id = customerId++;  	
public:
 	int id;
};

int customerId = 0;
int main {
  Customer c1;
  c1.id = 20;
  return 0;
}
```

위의 예시에서는 c1의 id는 고정적으로 할당되어 수정되면 안되지만 id의 접근 지정자가 public이라 수정이 가능한 문제점이 있습니다.

해당 내용 아래와 같이 수정 가능합니다.

```c++
class Customer 
{
public:
	id = customerId++;  	
private:
 	int id;
};

int customerId = 0;
int main {
  Customer c1;
  // c1.id = 20;
  return 0;
}
```

위와 같이 수정을 한다면 id를 직접 접근하여 수정할 경우 컴파일러에서 오류가 나게 됩니다. 이로써 수정을 하면 안되는 변수를 ...

TODo

Data Hiding = Encapsulation



사용 유무

위험한 데이터

접근을 우회해서 하도록 





접근 제한자



상속 접근 지정자



public protected private 창



