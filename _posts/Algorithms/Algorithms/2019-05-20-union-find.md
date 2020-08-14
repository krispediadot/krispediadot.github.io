---
layout: post
title: "[Algorithm] Union-Find(Disjoint Set)"
categories: algorithms
tag : [Algorithms]
---

_2020.08.14 내용 업데이트_

### 1. Union Find 알고리즘
---
n개의 서로 다른 원소를 서로 소인 집합으로 그룹 짓고 연산을 수행해야하는 경우  

- union - 집합 합하기  
- find - 어떤 집합에 속하는지 확인하기  

위 두가지 연산이 필요하다.  

이러한 연산을 지원하는 자료구조를 유지 관리 하는 방법은 다양하다.  

### 2. Union Find 알고리즘 사용 사례 
---
Union Find 알고리즘은 그래프 알고리즘인 Kruskal 알고리즘 내부에서 간선을 선택하고 MST(Minimum Spanning Tree)를 찾는 과정에서 사용된다.  

### 3. Union Find 기본 프로시저 
---
- Pseudo Code
    ```
    CONNECTED-COMPONETS(G){
        for each vertex v ∈ G.V
            MAKE-SET(v)
        for each edge (u,v) ∈ G.E
            if FIND-SET(u) ≠ FIND-SET(v)
                UNION(u,v)
    }
    ```

- 시간복잡도  
    O(n²)

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void CONNECTED_COMPONENTS(char vertex[], Edge *edge[], SetItem *set[]){
    for(int vIndex=0; vIndex<10; vIndex++){
        set = MAKE_SET(vIndex, vertex[vIndex], set);
    }
    for(int eIndex=0; eIndex<7; eIndex++){
        if(FIND_SET(edge[eIndex]->e1, set) != FIND_SET(edge[eIndex]->e2, set))
            set = UNION(edge[eIndex]->e1,edge[eIndex]->e2, set);
    }
    return;
}
```
</div>
</details>


#### 3-1. MAKE-SET 
---
집합 초기화 

- Pseudo Code
```
MAKE-SET(G){
    for each v in G.v
        v->parent = v
}
```

<details>
<summary>C++ 코드 보기</summary>
<div markdown="1">

```cpp
SetItem **MAKE_SET(int index, char in, SetItem **set){
    *(set+index) = new SetItem(in, in);
    return set;
}
```
</div>
</details>

#### 3-2. FIND-SET
---
각 원소가 해당되는 집합 찾기 

- Pseudo Code
```
FIND-SET(x){
    if x->parent != x
        x->parent = FIND-SET(x->parent)
    return x->parent
}
```

<details>
<summary>C++ 코드 보기</summary>
<div markdown="1">

```cpp
char FIND_SET(char target, SetItem **set){
    // 구조체의 인덱스 찾는 부분 
    int targetIndex;
    for(int sIndex=0; sIndex<10; sIndex++){
        if(set[sIndex]->origin == target) {
            targetIndex = sIndex;
            break;
        }
    }
    // pseudo code에 맞춰 작성한 부분 
    if(set[targetIndex]->parent != set[targetIndex]->origin){
        set[targetIndex]->parent = FIND_SET(set[targetIndex]->parent, set);
    }
    return set[targetIndex]->parent;
}
```
</div>
</details>

#### 3-3. UNION
---
집합 합치기 

- Pseudo Code 
```
UNION(u,v){
    x = FIND-SET(u)
    y = FIND-SET(v)
    y->parent = x
}
```

<details>
<summary>C++ 코드 보기</summary>
<div markdown="1">

```cpp
SetItem **UNION(char e1, char e2, SetItem **set){
    char x = FIND_SET(e1, set);
    char y = FIND_SET(e2, set);
    int xIndex, yIndex;

    for(int sIndex=0; sIndex<10; sIndex++){
        if(set[sIndex]->origin == x)
            xIndex = sIndex;
        if(set[sIndex]->origin == y)
            yIndex = sIndex;
    }

    set[yIndex]->parent = x;

    return set;
}
```
</div>
</details>

#### 3-4. 실행 예시  
---
![](https://krispedia.github.io/assets/images/union_find_ex1.jpg)
![](https://krispedia.github.io/assets/images/union_find_ex2.jpg)

<details>
<summary>전체 코드 보기</summary>
<div markdown="1">

```cpp
#include<iostream>

using namespace std;

struct Edge{
    char e1;
    char e2;
    Edge(char e1, char e2):e1(e1), e2(e2){}
};
struct SetItem{
    char origin;
    char parent;
    SetItem(char origin, char parent): origin(origin), parent(parent){}
};

char FIND_SET(char target, SetItem **set);

////////////////// 출력용 /////////////////////////////
///
void checkSet(SetItem *set[]){
    for(int i=0; i<10; i++)
        cout<<set[i]->origin<<" ";
    cout<<endl;
    for(int i=0; i<10; i++)
        cout<<set[i]->parent<<" ";
    cout<<endl;
}
void printSet(SetItem *set[]){
    bool done[10] = {false};
    bool head[10] = {false};
    for(int setIndex=0; setIndex<10; setIndex++){
        char headChar = set[setIndex]->parent;
        for(int subIndex=0; subIndex<10; subIndex++){
            if(set[subIndex]->origin == headChar)
                head[subIndex] = true;
        }
    }
    for(int index=0; index<10; index++){
        if(head[index]){
            char headChar = set[index]->origin;
            cout<<"{ ";
            for(int setIndex=0; setIndex<10; setIndex++){
                if(FIND_SET(set[setIndex]->origin, set) == headChar)
                    cout<<set[setIndex]->origin<<" ";
            }
            cout<<"} ";
        }
    }
    cout<<endl;
}
///
////////////////////////////////////////////////////////

SetItem **MAKE_SET(int index, char in, SetItem **set){
    *(set+index) = new SetItem(in, in);
    return set;
}
char FIND_SET(char target, SetItem **set){
    int targetIndex;
    for(int sIndex=0; sIndex<10; sIndex++){
        if(set[sIndex]->origin == target) {
            targetIndex = sIndex;
            break;
        }
    }
    if(set[targetIndex]->parent != set[targetIndex]->origin){
        set[targetIndex]->parent = FIND_SET(set[targetIndex]->parent, set);
    }
    return set[targetIndex]->parent;
}
SetItem **UNION(char e1, char e2, SetItem **set){
    char x = FIND_SET(e1, set);
    char y = FIND_SET(e2, set);
    int xIndex, yIndex;

    for(int sIndex=0; sIndex<10; sIndex++){
        if(set[sIndex]->origin == x)
            xIndex = sIndex;
        if(set[sIndex]->origin == y)
            yIndex = sIndex;
    }

    set[yIndex]->parent = x;

    return set;
}

void CONNECTED_COMPONENTS(char vertex[], Edge *edge[], SetItem *set[]){
    for(int vIndex=0; vIndex<10; vIndex++){
        set = MAKE_SET(vIndex, vertex[vIndex], set);
    }
    cout<<" INIT ";
    printSet(set);
    for(int eIndex=0; eIndex<7; eIndex++){
        if(FIND_SET(edge[eIndex]->e1, set) != FIND_SET(edge[eIndex]->e2, set))
            set = UNION(edge[eIndex]->e1,edge[eIndex]->e2, set);
        cout<<"("<<edge[eIndex]->e1<<'-'<<edge[eIndex]->e2<<") ";
        printSet(set);
        //checkSet(set);
    }
    return;
}

int main(){
    SetItem *set[10];
    char vertex[] = {'a','b','c','d','e','f','g','h','i','j'};
    Edge *edge[] = { new Edge('b','d'),
                    new Edge('e','g'),
                    new Edge('a','c'),
                    new Edge('h','i'),
                    new Edge('a','b'),
                    new Edge('e','f'),
                    new Edge('b','c')
                    };

    CONNECTED_COMPONENTS(vertex, edge, set);

    return 0;
}
```
</div>
</details>

- 전체 코드 실행 결과  
    ![](https://krispedia.github.io/assets/images/union_find_ex3.jpg)

### 4. Union Find 프로시저 성능 향상
--- 

Union Find 에서 시간이 가장 많이 소요되는 구간이 최종 부모를 찾는 부분이다.  
이 시간을 줄이기 위해, 즉, 트리의 높이를 줄이기 위한 방법이 Weighted-Union, Path Compression 2가지 있다.  

#### 4-1. 방법 1. Weighted-Union 
---
기존의 방법으로 코드 작성 시 시간 'CONNECTED-COMPONETS(G)' 함수의 시간복잡도는 O(n²) 이었다. 이를 줄이는 방법 중 하나가 UNION -> Weighted-Union 으로 변경하는 것이다.  

##### 4-1-1. 기존 UNION

- Pseudo Code 
```
UNION(u,v){
    x = FIND-SET(u)
    y = FIND-SET(v)
    y->parent = x
}
```

##### 4-1-2. Weighted-Union

기존 UNION 함수의 시간복잡도는 하나의 집합을 단순히 다른 집합의 하위에 두면 되므로 O(1)이다.  
그러나 UNION 함수의 결과로 FIND-SET(x)를 할 경우, 특히 최악의 경우 x가 최종 부모와 거리가 멀리 있는 원소라면 최종 부모를 찾는 시간이 최대 해당 집합의 원소 크기가 될 수 있다.  

Weighted-Union에서는 최종 부모와를 찾는 시간을 줄이기 위해, 즉, 최종 부모와의 거리를 좁히기 위해 기존의 UNION 코드에 집합을 합할 때 조건을 추가해준다. 추가할 조건은 두 집합 중 높이가 작은 것을 높이가 높은 집합 아래에 두는 것이다. 높이는 각 집합의 연결 상태를 말하는데 높이를 코드상에서 하나하나 측정하기 힘드니 각 집합의 크기로 대신한다.  

- Pseudo Code
```
Weighted-Union(u,v){
    x = FIND-SET(u)
    y = FIND-SET(v)
    if(size[x] < size[y])
        u->parent = v
        size[y] = size[y]+size[x]
    if(size[y] < size[x])
        v->parent = u
        size[x] = size[x]+size[y]
}
```

- 시간복잡도  
O(nlogn)  

<details>
<summary>C++ 코드 보기</summary>
<div markdown="1">

```cpp
int size[10] = {1};

SetItem **UNION(char e1, char e2, SetItem **set){
    char x = FIND_SET(e1, set);
    char y = FIND_SET(e2, set);
    int xIndex, yIndex;

    for(int sIndex=0; sIndex<10; sIndex++){
        if(set[sIndex]->origin == x)
            xIndex = sIndex;
        if(set[sIndex]->origin == y)
            yIndex = sIndex;
    }

    if(size[xIndex] < size[yIndex]) {
        set[xIndex]->parent = y;
        size[y] = size[y] + size[x];
    }
    else{
        set[yIndex]->parent = x;
        size[x] = size[x] + size[y];
    }

    return set;
}
```
</div>
</details>

#### 4-2. 방법 2. Path Compression
---
기존의 방법으로 코드 작성 시 시간 'CONNECTED-COMPONETS(G)' 함수의 시간복잡도는 O(n²) 이었다. 이를 줄이는 방법 중 하나가 FIND-SET -> FIND-SET-PC 로 변경하는 것이다. 

##### 4-2-1. 기존 FIND-SET
- Pseudo Code
```
FIND-SET(x){
    if x->parent != x
        x->parent = FIND-SET(x->parent)
    return x->parent
}
```

##### 4-2-2. Path Compression 

기존의 코드에서 최종 부모를 찾기 위해 순회하는 과정에 본인의 부모의 부모 정보를 저장하도록 한다. 이러한 과정을 통해 트리의 높이를 줄일 수 있다.  

- Pseudo Code
```
FIND-SET-PS(x){
    while x->parnet != x
        x->parent = x->parent->parent
        x = x->parent
    return x->parentt
}
```

- 시간복잡도  
O(nlogn)

