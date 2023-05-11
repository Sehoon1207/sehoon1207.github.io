---
layout: single
title: "[AlgoDat]알고리즘과 데이터구조 기초"
folder: "algoDat"
categories:
  - algoDat

tags: [blog, algoDat, java]

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

date: 2023-04-19
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>

<pre>
OS    : Window
Editor: IntelliJ IDEA</pre>
</div>

#### Java가 뭐야?

> 가전제품용 소프트웨어 프로젝트에서 시작된 Java는 인터넷 용 프로그래밍 언어로 개발되었다.  
> Java는 `오픈 소스`이며 가장 널리 사용되는 프로그래밍 언어 중 하나이다.  
> Java는 운영 체제 및 플랫폼과 독립적으로 실행할 수 있는 안전하고 간단한 `객체 지향 프로그래밍 언어`이다.
> Java는 `JVM(Java Virtual Machine)` 개념을 통해 구현되었습니다.  
> JVM은 호출된 각 Java 프로그램에 대해 `가상 머신`을 형성한다.

#### Java의 특징

> 1. 모든 프로그램은 <u>런타임(바이트코드 검증기)에 검사</u>되며 메모리 관리는 이미 JVM에 통합되어 있습니다.
> 2. C 또는 C++에서 알려진 포인터는 일반적으로 지원되지 않으며 대신 <u>Java는 참조를 사용</u>합니다.
> 3. 프로그램의 특정 부분에 대한 액세스를 제한하는 기능과 같은 기타 <u>보안 조치가 프로그래밍 언어에 내장</u>되어 있습니다.
> 4. Java의 우수한 성능으로 프로그램이 실행되는 동안 바이트 코드를 기계 코드(기계어)로 변환하는 `JIT(Just-In-Time)` 컴파일이 있다. 이를 통해 예를 들어 더 이상 값을 변경하지 않는 변수를 상수로 처리하여 <u>런타임을 동적으로 최적화</u>할 수 있습니다.

---

**keyword: 오픈 소스, 객체 지향 프로그래밍 언어, JVM(Java Virtual Machine), 가상 머신, JIT(Just-In-Time)**

`오픈 소스` : 오픈 소스 소프트웨어라고 하며, 소스의 코드를 공개해 누구나 보고 사용할 수 있는 라이선스를 만족하는 소프트웨어를 말한다.

`객체 지향 프로그래밍` : 명령형 프로그래밍이라고도 함. 객체 지향 프로그래밍은 프로그래밍에 필요한 수많은 역할을 각각 객체로 보고 이들의 상호작용으로 표현한다. 자료를 추상화하여 상속, 다형 개념, 동적 바인딩 등으로 시스템의 복잡성을 제어한다.

`JVM(Java Virtual Machine)` : 자바를 실행하기 위한 가상머신, 즉 컴퓨터라고 생각하면 된다. 따라서 OS에 구애받지 않고 실행 가능하다.

`가상 머신` : 즉, 쉽게말해 컴퓨터.

`JIT(Just-In-Time)`: 자바코드 > 바이트 코드 > 기계어의 흐름으로 자바에서 입력한 언어가 컴퓨터가 이해할 수 있게 변환되어지는데, JIT는 바이트코드 > 기계어로 변환되는 과정에서 이루어지는 것을 말하며, 프로그램이 실행되는 순간에 변환도 동시에 이루어지기 때문에 JIT(Just-In-Time)라고 말한다.

---

Quelle: Einführung in Java für AlgoDat, Vera Röhr und Benjamin Blankertz
