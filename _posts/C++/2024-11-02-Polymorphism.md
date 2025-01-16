---
layout: single
title: "[C++] 다형성"
categories: cpp
tag: [cpp]
toc: true
typora-root-url: ../
sidebar:
  nav: "docs"


---

# 다형성

## 다형성이란

### 개념

다형성(polymorphism)이란 같은 자료형에 여러가지 타입의 데이터를 대입하여 다양한 결과를 얻어낼 수 있는 성질을 의미합니다.

다형성을 나타내는 기법은 여러가지가 있지만 공통적인 기법으로는 오버로딩과 오버라이딩이 있습니다.

### 오버로딩

``` c++
	
```

오버로딩이란 함수를 만들때 매개변수의 차이를 두어 하나의 함수를 여러 기능으로 하도록 하는 기법입니다. 이는 다형성 나타내는 대표적인 기능입니다.

### 오버라이딩

``` c++
	
```

오버라이딩은 상속 관계에 있는 상태에서 부모의 함수를 자식이 재정의 하여 나타는 기법으로 이 또한 다형성을 보여줍니다.

#### 가상함수

``` c++
	
```

가상함수는 상속 관계에 있는 객체 중 함수를 오버라이딩을 한 경우 그 함수가 타입을 캐스팅한 상태에 따라 오버라이딩 되지 않은 부모의 함수를 호출할지, 오버라이딩한 자신의 함수를 호출할지가 정해집니다.

이러한 경우에 의도하지 않게 자기 자신의 함수를 호출하도록 가상 함수라는 기능을 사용하게 됩니다.

어떻게 이렇게 동작되는지를 확인해보면 가상함수를 선언한 경우 객체 생성시 가상 함수 테이블이 생성되며 이것에 따라 함수 호출이 이루짐을 알 수 있습니다.

**다형성 - 10 /31**







다형성 (Polymorphism) 겉은 똑같은데 기능은 다르게 동작

오버로딩 / 오버라이딩



바인딩

정적 바인딩 (Static Binding) - 컴파일 시점

동적 바인팅 (Dynamic Binding) - 런타임 시점



가상 함수

Virtual

가상 함수 테이블 



순수 가상 함수