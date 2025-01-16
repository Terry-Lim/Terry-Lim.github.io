---
layout: single
title: "[C++] 동적 메모리 할당"
categories: cpp
tag: [cpp]
toc: true
typora-root-url: ../
sidebar:
  nav: "docs"





---

# 동적 할당

## 동적 할당이란?

### 개념

### C스타일의 동적 할당

### C++ 스타일의 동적 할당

**동적 할당**





메모리 구조



실행 할 코드 -> 코드 영역

전역 / 정적 변수 -> 데이터 영역

지역 변수 /매개 변수 -> 스택 영역

동적 할당 -> 힙 영역



커널 영역

유저 영역





Malloc free

Void *. 

Heap overflow

Memory Leak



Double free -> crash



Use after free



New delete





Malloc fee / new delete 차이

함수 / 연산자





New delete는 생성하는 타입이 객체인 경우 생성자와 소멸자가 호출됩니다.