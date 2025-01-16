---
layout: single
title: "[C++] 연산자 오버로딩"
categories: cpp
tag: [cpp]
toc: true
typora-root-url: ../
sidebar:
  nav: "docs"



---

# 연산자 오버로딩

## 연산자 오버로딩이란

### 개념

연산자 오버로딩은 C++에서 제공하는 기본 타입이 아닌 클래스 타입, 즉 사용자 정의 타입에도 연산자를 사용할 수 있게 하는 문법입니다. 

구현 방법은 연산자형, 함수형으로 구분됩니다.

### 연산자형

``` c++
class Position {
  public: operator+ (const Position& arg) {
    Position pos;
    pos._x = _x + arg._x;
    pos._y = _y + arg._y;
    return pos;
  }
  
  public : 
  	int _x;
  	int _y;
}
```



### 함수형 



**연산자 오버로딩**





연산자 오버로딩은



연산자 vs 함수

연산자는 피연산자의 개수 / 타입이 고정되어 있음.



멤버함수로도 전역함수로 두가지 방법으로 가능



멤버 연산자 함수 version

A op b 형태에서 왼쪽으로 기준으로 실행됨 (a가 클래스여야 가능. a를 ‘기준 피연산자’라고 함)

한계 ) a가 클래스가 아니면 안됨



복사 대입 연산자



모든 연산자를 다 오버로딩 안됨 :: *



전위형 (++a) operator++()

후위형 (a++) operator++(int)
