---
layout: post
title: "[cppreference] C++ 소스 코드가 실행 파일이 되는 과정"
categories: cpp
tag : [C++]
---

#### 1단계
1) 소스코드 파일의 각 byte들은 _basic source character set_으로 매핑된다. 특별히 OS에 따라 다른 end-of-line 표식은 newline character로 대체된다. _basic source character set_은 96개의 문자로 이루어져있다. 

- 공백 문자 5개 (space, horizontal tab, vertical tab, form feed, new-line)
- 숫자 10개 ('0'~'9')
- 알파벳 52개 ('a'~'z', 'A'~'Z')
- 문장 부호 29개 (_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " ')  

2) _basic source character set_으로 매핑될 수 없는 몇몇 소스파일 문자는 \u 또는 \U 이스캐이프 시퀀스가 붙는 고유 문자로 대체되거나 따로 정의되어 있는 방식에 따라 대체된다. 

3) trigraph sequence는 그에 해당하는 single-character로 대체된다.  

#### 2단계  
1) 백슬래시가 문장의 끝에 나오고 바로 newline character가 나오면 백슬래시와 newline character가 지워지고 2개의 물리적 소스 라인이 하나의 논리적 소스라인이 된다. 이것은 single-pass operation로 두개의 백슬래시와 빈 라인은 3 줄이 1줄로 합쳐지지 않는다. universal character name이 문장에 있는 경우는 어떻게 할 지 정의되어 있지 않다.  
2) 만약 비어있지 않은 소스파일이 newline 이 없거나 백슬래시로 끝나는 경우 C++11 이전까지는 어떻게 할 지 정의되어 있지 않고 C++11 부터는 newline character를 추가한다.  

#### 3단계 
1) 소스파일은 comment, 공백 문자(space, horizontal tab, newline, vertical tab, form-feed) 그리고 전저리 토큰으로 분해된다.  

전처리 토큰
- 헤더이름 ex)<iostream>, "myfile.h"  
- 식별자  
- 전처리 번호  
- 문자, 문자열  
- 연산자, 특수문자 ex) +, <<=, new, <%, ##, and  
- 카테고리에 포함되지 않는 공백 문자가 아닌 것  

2) 1단계 2단계를 실행시키며 쌍따움표 사이의 글자는 

3) comment는 하나의 space 문자로 대체  



---
**[참고자료]**  
[https://en.cppreference.com/w/cpp/language/translation_phases](https://en.cppreference.com/w/cpp/language/translation_phases)