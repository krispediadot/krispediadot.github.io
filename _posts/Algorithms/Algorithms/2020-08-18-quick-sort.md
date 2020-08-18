---
layout: post
title: "[Algorithm] Quick Sort(퀵 정렬) "
categories: algorithms
tag : [Sort]
---

### 1. 퀵 정렬 알고리즘 
---
분할 정복법을 사용한 정렬 방법이다.  

### 2. 퀵 정렬 동작 방법
--- 

### 3. 시간복잡도
---
최선 : O(nlogn)  
최악 : O(n²)  

### 4. 구현 
---
- Pseudo Code
```
partition(A, p, r){
    x = A[r]
    i = p-1;
    for j = p->r-1{
        if A[j] < x then
            i = i+1
            swap(A[i], A[j])
    }
    swap(A[i+1], A[r])
    return i+1
}
quickSort(A, p, r){
    if p<r then
        q = partition(A, p, r)
        quickSort(A, p, q-1)
        quickSort(A, q+1, r)
}
```

#### 4-1. 배열의 마지막 값을 pivot으로 사용한 경우 

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void swap(int *a, int *b){
    int *temp = a;
    *a = *b;
    b = temp;
}
int partition(int *A, int p, int r){
    int pivot = A[r];
    int i = p-1;
    for(int j=p; j<r; j++){
        if(A[j]<pivot){
            i+=1;
            swap(A[i], A[j]);
        }
    }
    swap(A[i+1], A[r]);
    return i+1;
}
void quickSort(int *A, int p, int r){
    if(p<r){
        int q = partition(A, p, r);
        quickSort(A, p, q-1);
        quickSort(A, q+1, r);
    }
}
```
</div>
</details>

#### 4-2. first, middle, last 값 중 중간 값을 선택한 경우  

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
void swap(int *a, int *b){
    int *temp = a;
    *a = *b;
    b = temp;
}
int getMedianValueIndex(int *A, int begin, int middle, int end){
   if((A[middle]<=A[begin]&&A[begin]<=A[end])||(A[end]<=A[begin]&&A[begin]<=A[middle]))
       return begin;
    if((A[begin]<=A[middle]&&A[middle]<=A[end])||(A[end]<=A[middle]&&A[middle]<=A[begin]))
        return middle;
    if((A[begin]<=A[end]&&A[end]<=A[middle])||(A[middle]<=A[end]&&A[end]<=A[begin]))
        return end;
}
int partition(int *A, int p, int r){
    int pivotIndex = getMedianValueIndex(A, p, int((p+r)/2), r);
    swap(A[pivotIndex], A[r]);

    int pivot = A[r];
    int i = p-1;
    for(int j=p; j<r; j++){
        if(A[j]<pivot){
            i+=1;
            swap(A[i], A[j]);
        }
    }
    swap(A[i+1], A[r]);
    return i+1;
}
void quickSort(int *A, int p, int r){
    if(p<r){
        int q = partition(A, p, r);
        quickSort(A, p, q-1);
        quickSort(A, q+1, r);
    }
}
```
</div>
</details>

#### 4-3. 랜덤한 pivot 선택한 경우  

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
#include<random>

void swap(int *a, int *b){
    int *temp = a;
    *a = *b;
    b = temp;
}
int partition(int *A, int p, int r){
    random_device rd;
    mt19937 gen(rd());
    uniform_int_distribution<int> dis(p, r);

    int pivotIndex = dis(gen);
    swap(A[pivotIndex], A[r]);

    int pivot = A[r];
    int i = p-1;
    for(int j=p; j<r; j++){
        if(A[j]<pivot){
            i+=1;
            swap(A[i], A[j]);
        }
    }
    swap(A[i+1], A[r]);
    return i+1;
}
void quickSort(int *A, int p, int r){
    if(p<r){
        int q = partition(A, p, r);
        quickSort(A, p, q-1);
        quickSort(A, q+1, r);
    }
}
```
</div>
</details>