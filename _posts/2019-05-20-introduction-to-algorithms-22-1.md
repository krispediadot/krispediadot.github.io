---
layout: post
title: "[Introduction To Algorithms] 22.1 그래프의 표현"
categories: ita
tag : [algorithms]
---
---
### 그래프 표현 용어
- `V = 정점(Vertex)`
- `E = 간선(Edge)`
- `|V| = 정점의 개수`
- `|E| = 간선의 개수`

---  


#### 그래프 G = (V,E) 를 표현하기 위해서는 두가지 표준 방법이 있습니다.  

  ![adj list 1](https://krispedia.github.io/assets/images/22_adj_1.jpg)  
  ![adj list 2](https://krispedia.github.io/assets/images/22_adj_2.jpg)  

##### 1.인접 리스트의 집합<br>

리스트를 이용해 인접 관계를 표현  
위 이미지 (b)  

**장점**
- 인접 행렬 표현법에 비해 메모리 사용량을 줄일 수 있다.  

**단점**
- 주어진 간선(u,v)가 그래프에 있는지 확인하기 위해서 `O(u의 degree)`의 시간복잡도를 가지게 된다.

##### 2.인접 행렬

행렬을 이용해 인접 관계를 표현  
위 이미지 (c)  

**장점**  
- 가중치 없는 그래프의 경우 행렬 원소마다 1bit만 필요하다.  
- 주어진 간선이 그래프에 있는지 확인하기 위해서 `O(1)`의 시간 복잡도를 가진다. 

**단점**  
- 메모리 사용량이 많다.

  
---
**Reference**:

Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein - `Introduction to algorithms` (2009, The MIT Press)