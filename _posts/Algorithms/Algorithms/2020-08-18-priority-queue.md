---
layout: post
title: "[Data Structure] Priority Queue(우선순위 큐)"
categories: algorithms
tag : []
---

### 1. Priority Queue 자료구조
---

#### 1-1. 정의 
---
![](https://krispediadot.github.io/assets/images/priority_queue_1.jpg)
우선순위의 값이 최대 또는 최소인 값을 꺼낼 수 있는 큐  

#### 1-2. 종류 
---

| 종류       | 설명           |
| ------------- | ------------- |
| Max priority queue | 큰 값이 먼저 extract |
| Min priority queue | 작은 값이 먼저 extract |
 
#### 1-3. 표현 시 사용되는 자료구조 
---
![](https://krispediadot.github.io/assets/images/heap_2.jpg)

heap으로 priority queue(우선순위 큐)를 구현할 수 있다.  

Tree의 특성상 heap은 root/ parent/ child 를 가진다.  

- root = 배열의 1번째 Index
- parent = 현재 Index/2(소수점 제외)
- left-child = 현재 Index*2
- right-child = 현재 Index*2+1

### 2. Priority Queue 구현 
---

#### 2-1. 구현해야 할 연산 
---
- **Insert**  
새로운 데이터가 들어오는 경우 우선순위에 따라 적정한 위치에 정렬되어야 한다.  

- **Extract Max(Min)**  
최대(또는 최소) 우선순위 데이터가 dequeue  
dequeue가 되고 난 후 남은 데이터를 heap property에 맞게 정리해줘야한다.   

#### 2-2. Insert 구현
---
- 시간복잡도  
O(logn)

- Pseudo Code
```
maxHeapInsert(A, key){
    heapSize = A size+1
    A[heapSize] = key
    i = heapSize
    while i>1 and A[parent(i)] < A[i]{
        swap(A[parent(i)], A[i])
        i = parent(i)
    }
}
```

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void swap(int *a, int *b){
    int *temp = a;
    *a = *b;
    b = temp;
}
void maxHeapInsert(int *arr, int n, int key){
    int heapSize = n+1;
    arr[heapSize] = key;
    int i = heapSize;
    while(i>1 && arr[int(i/2)] < arr[i]){
        swap(arr[i], arr[int(i/2)]);
        i = int(i/2);
    }
}
```
</div>
</details>


#### 2-3. Extract Max 구현 
---
- 시간복잡도  
O(logn)

- Pseudo Code
```
extractMax(A){
    if A size<1
        큐에 값 없음 
    max = A[1]
    swap(A[1], A[heapSize])
    heapSize = heapSize-1
    maxHeapify(A, 1, heapSize)
    return max
}
```

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void swap(int *a, int *b){
    int *temp = a;
    *a = *b;
    b = temp;
}
int extractMax(int *arr, int n){
    if(n<1)
        return NULL;
    int max = arr[1];
    swap(arr[1], arr[n]);
    n-=1;
    maxHeapify_iterative(arr, 1, n);
    return max;
}
```
</div>
</details>

#### 2-4. 전체 코드 및 예시 결과
---
<details>
<summary>전체 코드 보기</summary>
<div markdown="1">

```cpp
#include<iostream>
using namespace std;

void swap(int *a, int *b){
    int *temp = a;
    *a = *b;
    b = temp;
}
void maxHeapify_recursive(int *arr, int root, int n) {
    if(root*2>n)
        return;
    int k = root*2;
    if(root*2+1<=n)
        k = arr[root*2]>arr[root*2+1]? root*2:root*2+1;

    if(arr[root]>=arr[k])
        return;
    swap(arr[root], arr[k]);
    maxHeapify_recursive(arr, k, n);
}
void maxHeapify_iterative(int *arr, int root, int n){
    while(root*2<=n){
        int k = root*2;
        if(root*2+1<=n)
            k = arr[root*2]>arr[root*2+1]? root*2:root*2+1;

        if(arr[root]>=arr[k])
            return;
        swap(arr[root], arr[k]);
        root = k;
    }
}
void buildMaxHeap(int *arr, int n){
    for(int i=int(n/2); i>0; i--){
        //maxHeapify_recursive(arr, i, n);
        maxHeapify_iterative(arr, i, n);
    }
}
void maxHeapInsert(int *arr, int n, int key){
    int heapSize = n+1;
    arr[heapSize] = key;
    int i = heapSize;
    while(i>1 && arr[int(i/2)] < arr[i]){
        swap(arr[i], arr[int(i/2)]);
        i = int(i/2);
    }
}
int extractMax(int *arr, int n){
    if(n<1)
        return NULL;
    int max = arr[1];
    swap(arr[1], arr[n]);
    n-=1;
    maxHeapify_iterative(arr, 1, n);
    return max;
}
int main(){
    int n=10;
    int arr[] = {0,4,1,3,2,16,9,10,14,8,7};

    buildMaxHeap(arr, n);
    //heapSort(arr, n);
    //maxHeapInsert(arr, n, 18);
    for(int i=1; i<=n; i++) cout<<arr[i]<<" ";
    cout<<endl;
    cout<<extractMax(arr, n)<<endl;
    for(int i=1; i<=n-1; i++) cout<<arr[i]<<" ";
    cout<<endl;


    return 0;
}
```
</div>
</details>

<div class="divider"></div>
**[참고 자료]**
- [Introduction to Algorithms, Third Edition](https://en.wikipedia.org/wiki/Introduction_to_Algorithms)
- [권오흠 교수님의 알고리즘 강의](https://www.youtube.com/watch?v=i4ZDgJS0_yM&list=PL52K_8WQO5oUuH06MLOrah4h05TZ4n38l&index=34)