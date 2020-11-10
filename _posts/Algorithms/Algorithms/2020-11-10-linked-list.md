---
layout: post
title: "[Data Structure] Linked List(링크드 리스트)"
categories: algorithms
tag : []
---

### 1. Linked List 자료구조
---

#### 1-1. 정의 
---
![]()

선형적 순서로 각 항목이 연속적으로 구성되어있는 자료구조이다.  

#### 1-2. 특성
---
1. **데이터의 논리적 순서와 물리적 순서가 일치하지 않는다.**  
연결 리스트는 논리적 순서에 따라 물리적 순서가 정해지는 배열과는 달리 본인 다음의 데이터의 시작 위치를 저장하고 있으므로서 다음 데이터와 연결된다. 

2. **크기가 가변적이다.**  
새로운 데이터를 추가하기 위해 마지막 데이터에 다음 데이터의 시작 주소만 저장하면 크기를 키울 수 있다.  

3. **동일한 데이터 타입만 담을 수 있다.**  
배열은 동알한 크기를 가지는 동일한 데이터 타입만을 담을 수 있다.  

#### 1-3. 장단점
---
- **장점**  
삽입/ 삭제 연산의 비용이 배열에 비해 작다.<br>
크기가 가변적이다.<br>

- **단점**  
index를 통해 바로 접근할 수 없다.(순차접근만 가능)<br>

### 2. Linked List 구현 
---

#### 2-1. 구조체 Node를 만들어 사용
---

<details>
<summary>C++ 구현 코드 보기</summary>
<div markdown="1">

```cpp
#include<iostream>

using namespace std;

class LinkedList{
    struct Node{
        int data;
        Node* next;
        Node(int data):data(data), next(nullptr){}
    };
    Node* head;

public:
    LinkedList():head(nullptr){}
    void insert_front(int data);
    void insert_rear(int data);
    void remove(int data);
    int find(int data);
    void print();
};
void LinkedList::insert_front(int data){
    Node* newNode = new Node(data);
    if(this->head == nullptr){
        head = newNode;
    }
    else{
        newNode->next = this->head;
        this->head = newNode;
    }
}
void LinkedList::insert_rear(int data){
    Node* newNode = new Node(data);
    if(this->head == nullptr){
        head = newNode;
    }
    else{
        Node* p = this->head;
        while(p->next!=nullptr){
            p = p->next;
        }
        p->next = newNode;
    }
}
void LinkedList::remove(int data){
    Node* prev = nullptr;
    Node* cur = this->head;
    //비어있는 링크드 리스트인 경우
    if(this->head == nullptr){
        cout<<"NOT EXIST"<<endl;
        return;
    }
    // 원소가 1개 존재할 경우
    if(this->head->next == nullptr){
        if(this->head->data!=data){
            cout<<"NOT EXIST"<<endl;
            return;
        }
        this->head = nullptr;
    }
    // 지울 원소 찾기
    while(cur != nullptr && cur->data != data){
        prev = cur;
        cur = cur->next;
    }
    // 끝까지 봐도 없는 경우
    if(cur==nullptr){
        cout<<"NOT EXIST"<<endl;
        return;
    }
    // 첫번째 원소가 지울 원소인 경우
    if(prev == nullptr){
        this->head = this->head->next;
    }
    // 그외
    else {
        prev->next = cur->next;
    }
}
int LinkedList::find(int data){
    Node* p = this->head;
    int index = 0;
    bool found = false;
    while(p != nullptr){
        if(p->data == data){
            found = true;
            break;
        }
        p = p->next;
        index++;
    }
    if(found)
        return index;
    return -1;
}
int main(){
    LinkedList llist;

    llist.insert_front(1);
    llist.insert_front(2);
    llist.insert_rear(3);
    llist.print();

    int findidx = llist.find(3);
    if(findidx==-1) cout<<"NOT FOUND"<<endl;
    else cout<<"FOUND: "<<findidx<<endl;

    llist.remove(1);
    llist.print();
    llist.remove(2);
    llist.print();

    return 0;
}
```
</div>
</details>


- 결과   
![](https://krispedia.github.io/assets/images/linked_list_2.jpg)

<div class="divider"></div>
**[참고 자료]**
- [Introduction to Algorithms, Third Edition](https://en.wikipedia.org/wiki/Introduction_to_Algorithms)
- [권오흠 교수님의 알고리즘 강의](https://www.youtube.com/watch?v=i4ZDgJS0_yM&list=PL52K_8WQO5oUuH06MLOrah4h05TZ4n38l&index=34)