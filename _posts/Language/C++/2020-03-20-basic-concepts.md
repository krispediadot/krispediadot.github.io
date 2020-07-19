---
layout: post
title: "[cppreference] Basic_concepts"
categories: cpp
tag : [C++]
---

C++ 프로그램은 주로 헤더와 소스 파일로 이루어진 text file의 묶음이고 C++ implementation이 main 함수를 부를 때 실행된다.  
특별한 의미를 가진 '키워드'라 불리는 단어들이 있고 그 외 단어는 식별자로 쓰인다. Comment는 번역될 때 무시되며 몇몇 문자들은 escape sequence와 함께 사용된다.  

#### C++ 프로그램 엔터티 12가지  

- 변수(variable)  
    Variable is an object or a reference, that is not a non-static data member  
- 객체(object)  
    Object is a region of storage  
- 참조(reference)  
    Reference is an alias to an already-existing object of function
- 구조적 바인딩(structured binding)(C++17)  
    Structured binding is an alias to an already-existing object  
    출력을 묶어서 한번에 받을 수 있음  
- 함수(fuction)  
    Functions associate a sequence of statement with name and a list of zero or more function parameters  
- 열거형(enumerator)  
    Enumerator is a distinct type whose value is restricted to arange of value  
- 타입(type)  
    Type provide semantic meaning to the otherwise generic sequence of bits  
- 클래스 멤버(class member)  
- 탬플릭(template)  
    Template defines a family of class/ a family of function/ an alias to a family of type/ a family of variable/ a concept(C++20)
- 네임스페이스(namespace)  
    Namespace provide a method for preventing name conflict in large project  
- 매개변수 팩(parameter pack)  

**전처기리 매크로는 C++프로그램 엔터티가 아님!**

모든 개체들은 선언을 해야하고 선언에는 이들 가 요소의 구성요소가 정의외어야 한다. 선선은 해당 요소가 사용되지 위한 필수 정의이다.  
함수의 정의에는 명령어, 함수가 수행할 틍정 연산이 포함되어야 한다.  
프로그램 내의 이름은 미리 정의된 선언을 name lookup을 통해 참조해 가져온다.  
각 이름은 정의된 scope에서만 사용 가능하며 다른 scope 또는 unit에서 사용하기 위해 linkage를 가지고 있는 것도 있다.  
각 객체, 참조, 함수, 연산은 C++이 제공하거나 사용자가 정의한 type이 기본요소이다.  
non-static data member인 선언된 객체, 참조는 모두 변수이다.  






---
**[참고자료]**  

[https://en.cppreference.com/w/cpp/language/basic_concepts](https://en.cppreference.com/w/cpp/language/basic_concepts)_
