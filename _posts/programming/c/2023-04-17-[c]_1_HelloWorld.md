---
layout: single
title: "HelloWorld"
folder: "c"
categories:
  - c

tags: [blog, c]

author_profile: true
sidebar:
  nav: "sidebar-category"

# toc: true
# toc_label: "목록"
# toc_icon: "bars"
# toc_sticky: true
classes: wide
# sidebar:
#     nav: "counts"

date: 2023-04-17
---

## C 시작하기 Hello World!

이곳에는 c언어를 공부한 내용을 바탕으로 정리하려고 한다.  
시작은 역시 어느 언어든 마찬가지로 Hello World!출력이다.

\<input>

```c
#include <stdio.h>

int main() {
  // output a line
  printf("Hello World!\n");
}
```

사용하는 운영체제나 프로그램에 따라 컴파일 하는 방법 또는 실행 방법도 다양하지만  
여기서는 gcc 또는 clang으로 컴파일 하려고 한다.

컴파일하기 :

clang -std=c11 -Wall -g helloWorld.c -o helloWorld  
또는 gcc helloWorld.c -o helloWorld

실행하기 :

./helloWorld

\<output>

```
Hello World!
```

---
