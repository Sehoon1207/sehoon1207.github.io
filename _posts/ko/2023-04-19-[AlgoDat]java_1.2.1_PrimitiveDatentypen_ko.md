---
layout: single
title: "[AlgoDat]기본 데이터 유형"
folder: "AlgoDat"
categories:
  - AlgoDat

tags: [blog, AlgoDat, java]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "목록"
toc_icon: "bars"
toc_sticky: true
classes: wide

lang: de
lang-ref: multilingual

use_math: true

date: 2023-04-19
---

"PDF 자료를 공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."

> 데이터 유형은 어떤 종류의 변수인지, 어떤 작업을 수행할 수 있는지, 변수가 메모리에 어떻게 표시되는지, 즉 어떤 비트가 어떤 의미를 가지며 얼마나 많은 변수가 있는지를 결정합니다. 원시 데이터 유형은 단순한 데이터 유형으로 구성되지 않으며 데이터 유형의 기본 빌딩 블록입니다. Java에는 다음이 있습니다.

| Datentyp | Inhalt                                   | Wertebereich                           |
| -------- | ---------------------------------------- | -------------------------------------- |
| boolean  | 1 BitWahrheitswert (Größe undefiniert)   | true, false                            |
| char     | 16 Bit Unicode                           | Unicode Characters, z.B. a oder b oder |
| byte     | vorzeichenbehaftete ganze Zahl in 8 Bit  | $-2^7 ... 2^7-1 = 127 $                |
| short    | vorzeichenbehaftete ganze Zahl in 16 Bit | $-2^1^5 ... 215-1 = 32767 $            |
| int      |                                          |                                        |
| long     |                                          |                                        |
| float    |                                          |                                        |
| double   |                                          |                                        |

---

**keyword: 오픈 소스, 객체 지향 프로그래밍 언어, JVM(Java Virtual Machine), 가상 머신, JIT(Just-In-Time)**

`오픈 소스` : 오픈 소스 소프트웨어라고 하며, 소스의 코드를 공개해 누구나 보고 사용할 수 있는 라이선스를 만족하는 소프트웨어를 말한다.

`객체 지향 프로그래밍` : 명령형 프로그래밍이라고도 함. 객체 지향 프로그래밍은 프로그래밍에 필요한 수많은 역할을 각각 객체로 보고 이들의 상호작용으로 표현한다. 자료를 추상화하여 상속, 다형 개념, 동적 바인딩 등으로 시스템의 복잡성을 제어한다.

`JVM(Java Virtual Machine)` : 자바를 실행하기 위한 가상머신, 즉 컴퓨터라고 생각하면 된다. 따라서 OS에 구애받지 않고 실행 가능하다.

`가상 머신` : 즉, 쉽게말해 컴퓨터.

`JIT(Just-In-Time)`: 자바코드 > 바이트 코드 > 기계어의 흐름으로 자바에서 입력한 언어가 컴퓨터가 이해할 수 있게 변환되어지는데, JIT는 바이트코드 > 기계어로 변환되는 과정에서 이루어지는 것을 말하며, 프로그램이 실행되는 순간에 변환도 동시에 이루어지기 때문에 JIT(Just-In-Time)라고 말한다.

---

Quelle: Einführung in Java für AlgoDat, Vera Röhr und Benjamin Blankertz
