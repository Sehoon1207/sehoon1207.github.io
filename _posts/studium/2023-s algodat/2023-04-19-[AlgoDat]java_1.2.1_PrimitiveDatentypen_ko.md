---
layout: single
title: "[AlgoDat]기본 데이터 유형"
folder: "AlgoDat"
categories:
  - algoDat

tags: [blog, algoDat, java]

author_profile: true
sidebar:
  nav: "sidebar-category"

# toc: true
# toc_label: "목록"
# toc_icon: "bars"
# toc_sticky: true
classes: wide

lang: de
lang-ref: multilingual

use_math: true

date: 2023-04-19
---

"PDF 자료를 공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."

> `자료형(data type)`은 어떤 종류의 변수인지, 어떤 작업을 수행할 수 있는지, 변수가 메모리에 어떻게 표시되는지, 즉 어떤 비트가 어떤 의미를 가지며 얼마나 많은 변수가 있는지를 결정한다.
> `기본 데이터 유형(primitive data types)`은 단순한 데이터 유형으로 구성되지 않으며 Java에는 다음과 같다.

| Datentyp | Inhalt                                   | Wertebereich                                             |
| -------- | ---------------------------------------- | -------------------------------------------------------- |
| boolean  | 1 BitWahrheitswert (Größe undefiniert)   | true, false                                              |
| char     | 16 Bit Unicode                           | Unicode Characters, z.B. a oder b oder                   |
| byte     | vorzeichenbehaftete ganze Zahl in 8 Bit  | $-2^7$ $\dots$ $2^7-1 = 127 $                            |
| short    | vorzeichenbehaftete ganze Zahl in 16 Bit | $-2^{15}$ $\dots$ $2^{15}-1 = 32767 $                    |
| int      | vorzeichenbehaftete ganze Zahl in 32 Bit | $-2^{31}$ $\dots$ $2^{31}-1 = 2147483647$                |
| long     | vorzeichenbehaftete ganze Zahl in 64 Bit | $-2^{63}$ $\dots$ $2^{63}-1 = 9223372036854775807$       |
| float    | Gleitkommazahl in 32 Bit                 | $\pm 2^{127} \approx 10^{38} $ 7 signifikante Stellen    |
| double   | Gleitkommazahl in 64 Bit                 | $\pm 2^{1023} \approx 10^{308} $ 15 signifikante Stellen |

> 위 표 외에도 `String(추상 데이터 유형)`도 자주 사용된다.
> 이러한 데이터 유형에 값이 할당되지 않은 경우에는 자동으로 false 또는 0 (char의 경우에는 null 문자)로 초기화된다.

---

**keyword: 자료형(data type), 기본 데이터 유형(primitive data types), 추상 데이터 유형**

`자료형(data type)` :

`기본 데이터 유형(primitive data types)` :

`추상 데이터 유형` :

---

Quelle: Einführung in Java für AlgoDat, Vera Röhr und Benjamin Blankertz
