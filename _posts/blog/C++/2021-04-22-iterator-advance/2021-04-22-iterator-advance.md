---
layout: post
title: C++. <iterator> advance
date: 2021-04-22 23:00:00 +09:00
modified: 
category: cpp
tags: [ps, c++]
image: "/assets/img/avatar_code.png"
cover: "../puzzle.jpg"
---

### advance

#### 설명
iterator 사용 시 random access 하듯 특정 위치로 바로 이동할 수 있도록 돕는 함수<br>

#### 사용법
```cpp
#include <iostream>     // std::cout
#include <iterator>     // std::advance
#include <list>         // std::list

int main () {
  std::list<int> mylist;
  for (int i=0; i<10; i++) mylist.push_back (i*10);

  std::list<int>::iterator it = mylist.begin();

  std::advance (it,5);

  std::cout << "The sixth element in mylist is: " << *it << '\n';

  return 0;
}
```

---
**참고자료:**<br>
- [https://en.cppreference.com/w/cpp/iterator/advance](https://en.cppreference.com/w/cpp/iterator/advance)
- [https://www.cplusplus.com/reference/iterator/advance/](https://www.cplusplus.com/reference/iterator/advance/)
