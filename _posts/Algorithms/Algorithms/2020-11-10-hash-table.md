---
layout: post
title: "[Data Structure] Hash Table(해시 테이블)"
categories: algorithms
tag : []
---

### 1. Hash Table 자료구조
---

#### 1-1. 정의 
---
![]()

트리는 계층적인 구조를 표현하는 자료구조이다.  

#### 1-2. 특성
---
1. **Search/ Insert/ Delete 연산을 O(1)에 가능**  
적절한 가정 하에 위 연산을 O(1)에 할 수 있음<br>

2. **다양한 해시 함수 사용**
h(k) = k % m 등 다양한 함수를 사용한다. <br>

3. **충돌이 발생할 수 있다.**
해시 함수를 거쳐 생성된 키 값에 이미 다른 데이터가 들어가있는 경우 충돌이 발생한다.<br>

### 2. 충돌 해결 방법
---

#### 2-1. Chaining
---
충돌이 발생한 해쉬 값에 데이터를 연결해서 저장하는 방법<br>

대표적으로 링크드리스트, 트리를 사용해 데이터를 연결한다.<br>


#### 2-2. Open Addressing
---
충돌이 발생하면 다른 곳에 저장하는 방법<br>


<div class="divider"></div>
**[참고 자료]**
- [Introduction to Algorithms, Third Edition](https://en.wikipedia.org/wiki/Introduction_to_Algorithms)
- [권오흠 교수님의 알고리즘 강의](https://www.youtube.com/watch?v=i4ZDgJS0_yM&list=PL52K_8WQO5oUuH06MLOrah4h05TZ4n38l&index=34)