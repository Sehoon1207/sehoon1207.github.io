---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[syspro-v] 03 동기화(Synchronisation)" #제목 확인
folder: "syspro" #폴더 확인
categories:
  - syspro #카테고리 확인

tags: [blog, syspro] #태그 확인

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

# use_math: true                    #숫자 사용 확인

date: 2023-05-08 #날짜 확인
---

<div class="notice--info">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>

<pre>
OS    : Window
Editor: VScode</pre>
</div>

---

# 01 동시 프로세스 조정 (Koordination nebenläufiger Prozesse)

시스템이 병렬적으로 실행되고 여러 작업을 처리

## 01-1 기본 조정 작업 Elementare Koordinationsoperationen:

서로 격리되고 독립적으로 실행되는 프로세스는 조정될 필요가 없다.

그러나 이러한 경우는 드물며 ...

• 일부 시스템 자원은 독점적으로 만 사용되어진다.
• 여러 개의 프로세스가 공통된 작업을 수행하기 위해 사용될 수 있다.
• 프로세스들은 서로 다른 소스에서 데이터를 교환할 수 있다.

프로세스 및 쓰레드 상호작용을 지원하는 것은 시스템 소프트웨어의 기본적인 작업 중 하나이다.

기본적으로 **두 가지 상호작용 형태**가 있다.

**경쟁 (Concurrent, Konkurrenz)**: 프로세스들이 동시에 실행되며 자원을 경쟁적으로 사용한다.

<div class="notice--info">
예를 들어, 한 프로세스가 자원을 사용하고 있으면, 다른 프로세스는 그 자원을 사용할 수 없으므로 대기해야 한다. 경쟁은 불필요한 대기 시간을 발생시키고, 시스템 성능을 저하시키는 원인이 된다.
</div>

**협력 (Cooperative, Kooperation)**: 프로세스들이 서로 협력하여 자원을 공유하거나 메시지를 교환하여 작업을 수행한다.

<div class="notice--info">
협력은 여러 프로세스가 동일한 작업을 수행하거나, 서로 다른 작업을 수행하더라도 서로의 작업에 영향을 미칠 수 있는 경우 발생한다. 이 경우, 프로세스 간에 데이터를 교환하거나, 서로의 작업을 동기화하여 상호작용을 수행한다. 협력은 시스템 성능을 향상시키는 역할을 한다.
</div>

기본적인 코디네이션 작업으로는 뮤텍스, 세마포어, 스핀락 등이 있다.
이러한 작업은 공유 자원에 대한 액세스를 조정하고, 경쟁 상태 및 데드락과 같은 문제를 해결하기 위해 사용된다.

## 01-2 시그널링 Signalisierung:

프로세스간 통신 및 동기화에 사용되는 기본적인 기술 중 하나다.
이를 통해 한 프로세스는 다른 프로세스에게 이벤트 또는 상태 변경을 알릴 수 있다.

## 01-3 크리티컬 섹션 Kritische Abschnitte:

공유 자원에 대한 동시 액세스를 제어하기 위한 방법 중 하나다.
이를 통해 오직 하나의 프로세스만이 공유 자원에 액세스하도록 보장할 수 있다.

## 01-4 운영 체제 지원 프로세스 상호 작용 Betriebssystemgestützte Prozessinteraktion:

운영 체제는 프로세스 간 통신 및 동기화를 지원하기 위한 다양한 메커니즘을 제공한다.
이를 통해 프로세스 간 메시지 전송, 공유 메모리, 파이프 및 소켓 등을 사용할 수 있다.

## 01-5 모니터 Monitore:

공유 자원에 대한 접근을 조정하는 데 사용되는 고급 동기화 메커니즘 중 하나다.
이를 통해 프로그래머는 자동으로 동기화 문제를 해결할 수 있다.

---

Quelle(text):  
pdf dateien, [studocu](https://www.studocu.com/de/course/technische-universitat-berlin/systemprogrammierung/1514199)  
pdf dateien, [studydrive](https://www.studydrive.net/de/course/systemprogrammierung/137292#documents)  
Klausur pdf dateien, [Klausurensammlung der Freitagsrunde](https://docs.freitagsrunde.org/Klausuren/Systemprogrammierung/)  
Vorlesung, Systemprogrammierung, [TU-Berlin](https://www.tu.berlin/dos/)  
Operating System - Process Scheduling, [tutorialspoint](https://www.tutorialspoint.com/operating_system/os_process_scheduling.htm)  
운영체제 CPU 스케줄링 전략들, [site 의지](https://gwnuysw.github.io/jekyll/update/2018/04/11/OperatingSystem.html)

Quelle(image):

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
<!-- <sup>[1)](#footnote_1)</sup>

<div class="notice--info">
<a name="footnote_1">1)</a>블라블라<br>
</div> -->
