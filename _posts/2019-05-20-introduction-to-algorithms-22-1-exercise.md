---
layout: post
title: "[Introduction To Algorithms] 22.1 연습문제"
comments: true
description: "algorithms"
tag : [Introduction To Algorithms, Exercise]
---

### 22.1-1
> 방향 그래프 하나를 인접 리스트로 표현하는 경우, 모든 정점의 바깥으로 나가는 간선의 개수를 계산하는데 걸리는 시간은 얼마인가, 그리고 안으로 들어오는 정점을 계산하는데 걸리는 시간은 얼마인가?

(1) 모든 정점의 바깥으로 나가는 간선의 개수는 인접 리스트의 전체 degree를 계산하면 되므로 `O(|E|+|V|)` 시간이 걸린다. 

(2) 정점의 안으로 들어오는 간선의 개수는 바깥으로 나가는 간선의 개수를 구하는것과 같이 모든 간선을 확인해 보아야 하므로 `O(|E|+|V|)` 시간이 걸린다.  

--- 

### 22.1-2
> 7개의 정점으로 이루어진 완전 이진 트리에 대한 인접 리스트 표현을 보여라. 그리고 인접행렬 표현도 보여라. 이진 힙에서와 같이 모든 정점에서 1에서 7까지의 번호가 매겨져 있다고 가정한다.

![gtree](https://krispedia.github.io/assets/images/exercise22_2_tree.jpg)

(1) 인접 리스트를 만들 경우  
    노드 1~3의 adj 리스트에는 해당 노드의 자식 노드 값이 들어가 있음.  
    노드 4~7의 ajd 리스트에는 해당 노드의 부모 노드 값이 들어가 있음  

    1: 2,3  
    2: 4,5  
    3: 6,7  
    4: 2  
    5: 2  
    6: 3  
    7: 3  

(2) 인접 행렬을 만들 경우  

![array](https://krispedia.github.io/assets/images/exercise22_2_adj_array.jpg)
    




