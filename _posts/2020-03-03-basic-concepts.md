---
layout: post
title: "[cppreference] Basic concepts"
categories: cpp
tag : [C++]
---

_원문 : [https://en.cppreference.com/w/cpp/language/basic_concepts](https://en.cppreference.com/w/cpp/language/basic_concepts)_
<div class="divider"></div>

C++ 언어의 특별한 용어와 기본 개념 소개  

C++ 프로그램은 정의를 포함한 텍스트 파일의 연속이다. 이 텍스트 파일은 메인 함수를 부르면 실행되는 실행 프로그램으로 번역된다.  

C++ 프로그램은 특별한 의미를 지닌 단어들이 있고 이는 키워드라 불린다. 그외 다른 단어들은 식별자로 쓰일 수 있다. 그리고 몇몇 글자들은 이스케이프 시퀀스와 함께 쓰인다.  

C++ 프로그램은 값, 객체, 레버런드 , 바인딩, 함수, enumerator, 타입  클래스 멤버, 텝플릿, 탬플릿 specialization, 네임스페이스 그리고 파라미터 팩으로 구성된다. 전처리 매크로는 C++ 요소가 아니다.  

각 요소는 이름과 해당 요소를 정의해줘야 한다. 하나의 프로그램은 오직 하나의 정의만 가질 수 있다. 

함수는 프로그램이 수행할 일을 코드로 작성한 명령어, 수식으로 정의한다.   

프로그램에서 사용되는 이름은 name lookup에 정의되어 있는 내용과 연결된다. 각 이름은 그것의 scope라 불리는  부분에서만 사용 가능하다. 어떤 이름들은 다른 scope에서도 사용 가능하도록 하는 linkage를 가지고 있다.  

C++ 언어의 각 객체, reference, 함수, 수식은 각각의 타입이 있고 이 타입은 기본적으로 제공하는 것, 사용자 정의 타입 등이 있다.  

선언된 객체와 선언된 reference는 정적 데이터가 아니며 이를 변수라 부른다.  