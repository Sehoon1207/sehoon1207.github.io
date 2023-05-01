---
layout: single
title: "[Java-1] 01 기본예제1"
folder: "java"
categories:
  - java

tags: [blog, java]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "list"
toc_icon: "bars"
toc_sticky: true
classes: wide

lang: ko
lang-ref: multilingual

# use_math: true

date: 2023-04-25
---

<div class="notice--info">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
"PDF 자료를 공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."
</div>

처음 프로젝트를 생성할 때, 꼭 새프로젝트 생성으로 만들어야 함.
내려받은 데이터로 작성시 오류발생.

# Aufgabe 1.1

```java
    public static void main(String[] args) {
        int k = 3;
        int[] test1 = {0, 1, 2, 3, 4};
        int[] test2 = new int[5];
        for (int i = 0; i < 5; i++)
            test2[i] = 1;
        sumToTarget(k, test1);
        System.out.println(sumToTarget(k, test2));
    }
```

---

Quelle(text):  
Quelle(image):  
Quelle(code):  
Einführung in Java für AlgoDat,TU Berlin [hier](https://www.studocu.com/de/course/technische-universitat-berlin/algorithmen-und-datenstrukturen/1512781)
Aufgabedateien in der Vorlesung, Algorithmen und Datenstrukturen, TU Berlin [hier](https://www.studocu.com/de/course/technische-universitat-berlin/algorithmen-und-datenstrukturen/1512781)

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
