---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[syspro-v] 00 인트로(Intro)" #제목 확인
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

date: 2023-04-25 #날짜 확인
---

<div class="notice--info">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>

<pre>
OS    : Window
Editor: VScode</pre>
</div>

# 00 systemprogramming이 뭐야?

시스템 프로그래밍은 운영 체제, 하드웨어 및 네트워크와 같은 시스템 수준에서 동작하는 프로그램을 개발하는 기술을 말함.

# 01 앞으로 이 카테고리에 정리 할 내용

## 01-1 프로세스와 쓰레드(Prozesse und Threads)

프로세스는 운영 체제에서 실행되는 프로그램의 인스턴스이고 쓰레드는 프로세스 내에서 실행되는 실행 흐름이다. 이 주제에서는 프로세스와 쓰레드의 개념과 차이점, 프로세스와 쓰레드의 생성과 동기화 등의 내용이 중점적으로 다루어진다.

**1. Arbeitsspeicher und Caching:**  
시스템에서 사용되는 메모리의 종류와 관리 방법을 이해하고, 캐싱 기술에 대해 정리한다.  
(keyword 가상 메모리, 페이지 교체 알고리즘, 캐시 메모리의 동작 원리 등)

**2. Scheduling:**  
운영 체제에서 프로세스와 쓰레드의 실행을 관리하는 스케줄링 기술에 대해 정리한다.  
(keyword 스케줄링 알고리즘, 우선순위, 멀티코어 시스템에서의 스케줄링 등)

**3. Prozesskommunikation:**  
프로세스와 쓰레드 간에 정보를 공유하고 통신하는 방법을 정리한다.  
(keyword 프로세스 간 통신(IPC) 방법, 공유 메모리, 파이프, 소켓 등의 개념과 구현 방법 등)

## 01-2 자원관리(Ressourcenmanagement)

자원 관리에서는 시스템에서 공유 자원에 대한 **모델링, 동기화, 협업, 교착 상태**와 같은 문제에 대해 정리한다.

**모델링(Modellierung):**
프로세스나 쓰레드 사이의 관계를 모델링하고 표현하는 방법을 정리한다.  
(예를 들어, 생산자-소비자 문제와 같은 문제를 모델링하고 해결하는 방법.)

**동기화(Synchronisation):**
다수의 프로세스나 쓰레드가 공유 자원에 동시에 접근하게 되면, 데이터 불일치, 경쟁 상태, 교착 상태 등의 문제가 발생할 수 있다. 동기화 기술은 이러한 문제를 해결하기 위한 기술이다. 동기화 기술에는 뮤텍스, 세마포어, 조건 변수 등을 포함한다.

**협력(Kooperation):**
다수의 프로세스나 쓰레드가 상호 협력하여 작업을 수행하는 방법에 대해 정리한다.  
이를 위해 프로세스나 쓰레드 간의 메시지 전달, 공유 데이터 구조, 동기화 기술 등을 사용한다.

**교착 상태(Verklemmungen):**
두 개 이상의 프로세스나 쓰레드가 서로 자원을 점유한 채로 상대방이 점유한 자원을 기다리는 상태로, 상태를 벗어나기 위해선 자원 해제 또는 강제로 자원을 해제하는 방법을 사용해야 한다. 이 주제에서는 교착 상태의 개념, 발생 원인, 감지 및 회피 기술 등을 중점으로 정리한다.

## 01-3 안정성(Sicherheit)

시스템 보안에 대한 기본 개념과 보안 취약점, 공격 유형, 보안 솔루션 등을 다룬다.

## 01-4 병렬 처리 및 분산 시스템(Parallele Systeme)

병렬 처리 및 분산 시스템에 대한 기본 개념과 이에 대한 알고리즘 및 기술을 정리한다.  
(keyword 병렬 처리, 분산 컴퓨팅, 클러스터링, 그리드 컴퓨팅 등)

# 02 운영체제의 역사적 흐름(Geschichte der Betriebssysteme)

(좀 지루할 수 있으니 가볍게 읽고 빠르게 넘어갑시다.)

## Erste Generation (1945-1955):

key: 진공관과 드럼 메모리가 있는 컴퓨터 아키텍처.  
이 시기에는 컴퓨터가 개발되는 초기 단계로, 기계어로만 작성된 프로그램을 실행했다. 운영 체제가 없었으며, 프로그램은 물리적인 스위치나 토글 스위치를 사용하여 입력되었다.

## Zweite Generation (1955-1965):

key: 트랜지스터로 신뢰성 향상됨, 프로그래밍은 펀치 카드로 수행.  
이 시기에는 어셈블리어가 개발되어 기계어 대신 사용되었다. 이 시기의 운영 체제는 배치 처리(Batch Processing) 시스템으로, 여러 개의 작업을 일괄 처리하는 방식으로 동작했다.

## Dritte Generation (1965-1980):

key: `집적 회로`, 고급 프로그래밍 언어를 사용하여 운영체제 구현, 소프트웨어 공학의 탄생.  
이 시기에는 시분할(Time Sharing) 시스템과 다중 프로그래밍(Multiprogramming) 시스템이 개발되었다. 시분할 시스템은 여러 사용자가 동시에 컴퓨터를 사용할 수 있도록 하고, 다중 프로그래밍 시스템은 여러 개의 프로그램을 메모리에 로드하여 동시에 실행할 수 있도록 하였다. 이 시기에는 대표적으로 UNIX와 같은 운영 체제가 등장하였다.

<div class="notice--info">
<h4>집적회로(Integrated Circuit):</h4>

대규모 집적회로(Large Scale Integration, LSI)와 초대규모 집적회로(Very Large Scale Integration, VLSI)가 있다. <br>
집적회로는 다수의 전자소자(저항, 커패시터, 다이오드, 트랜지스터 등)를 한 개의 칩에 집적하여 제조하는 기술이다. <br>
이전에는 하나의 칩에 하나의 전기소자를 접적했지만, LSI와 VLSI 기술의 발전으로 인해 더 많은 전자소자를 작은 칩에 집적가능하게 됨.<br>
이를 통해 컴퓨터의 성능과 소비 전력이 개선되고, 작고 경제적인 컴퓨터 시스템의 제작이 가능해짐.

</div>

## 1980 이후(CTSS > MULTICS > UNICS):

**CTSS(Compatible Time Sharing System):**  
key: 가상화 기술(프로세서 가상화)  
CTSS는 MIT에서 개발된 최초의 시분할 운영 체제.여러 사용자가 동시에 컴퓨터를 사용하고, 컴퓨터와 사용자 간의 통신을 위한 터미널(Terminal)을 이용한다. 그래서 사용자는 기다릴 필요없이 자신이 필요한 작업을 입력하고, 컴퓨터는 각 작업을 순차적으로 처리한다.

**MULTICS (MULTIplexed Information and Computing System):**
key: 나무와 같은 파일 시스템, 사용자 간 데이터 공유 기능, 다중 처리, 페이지 단위 메모리 관리(페이징), 광범위한 라이브러리

MULTICS의 개발 목표는 필요할 때 컴퓨팅 리소스를 사용할 수 있는 유틸리티와 같은 시스템을 구현하는 것.
다수의 사용자가 하나의 컴퓨터 시스템을 공유하도록 하는 시분할 운영 체제를 개발

**UNIX:**  
MULTICS프로젝트 중단 이후 MULTICS의 주요 개발자인 Ken Thompson는 UNIX를 만들게 됨. UNIX는 다양한 PDP 기반의 시스템에서 실행되도록 지원되어, 전 세계의 많은 사용자들이 사용하게 되었다. 나아가 UNIX는 대규모 시스템에서도 동작할 수 있는 운영 체제로 발전하게 됨.

**(1987)MINIX:**  
MINIX는 운영 체제 교육을 목적으로 개발된 운영 체제이다. Andrew S. Tanenbaum 교수가 개발하였으며, 미니멀리즘(minimalism)의 철학을 바탕으로 설계되었다. MINIX는 UNIX와 호환되며, 다양한 시스템에서 동작할 수 있다.

**(1988)POSIX(Portable Operating System Interface):**  
POSIX(Portable Operating System Interface)는 유닉스(UNIX) 운영 체제를 포함한 다양한 운영 체제에서 사용되는 API(Application Programming Interface)를 표준화하기 위한 국제 표준이다. POSIX는 이식성이 좋은 응용 프로그램과 운영 체제를 만들기 위한 표준 인터페이스를 제공한다.

**(1991)Linux:**  
Linux는 리눅스 토발즈가 개발한 운영 체제다. 리눅스는 UNIX와 호환되며, 오픈 소스 기반으로 개발되었다. 이 운영 체제는 다양한 컴퓨팅 환경에서 사용되며, 대부분의 컴퓨터 기술 분야에서 널리 사용된다. 또한, 리눅스는 다양한 플랫폼에서 실행되는 응용 프로그램을 개발하기 위한 많은 도구와 라이브러리를 제공한다.

## Vierte Generation (1980-1990)

**마이크로컴퓨터의 발달과 컴퓨터의 등장**

4세대는 다양한 새로운 기술과 도전적인 환경 속에서 운영 체제가 발전하였다. 이 시기에는 대규모 컴퓨팅 시스템이 더욱 보편화되었고, 다양한 플랫폼에서 운영 체제가 실행될 수 있도록 지원되었다.

**Lightweight Processes (Threads)의 도입:**  
이전 세대의 운영 체제는 하나의 프로세스가 하나의 실행 스레드를 가지는 것이 일반적이었다. 하지만 이제는 경량 프로세스인 스레드를 사용하여 여러 실행 스레드를 동시에 실행할 수 있게 되었다.

**Parallelitäts 개념의 도입:**  
운영 체제와 프로그래밍 언어는 대규모 병렬 처리, 부하 분산 등을 지원하도록 발전하였다.

**멀티미디어 기능의 지원:**  
운영 체제는 이미지, 오디오 및 비디오 스트림 등의 멀티미디어 기능을 지원하도록 발전하였다.

**임베디드 시스템의 발전:**  
운영 체제는 임베디드 시스템에 적합하도록 최적화되어 개발되었다. 이러한 시스템은 특정한 용도로 설계된 소형 컴퓨터 시스템으로, 실시간 처리가 중요한 경우가 많다.

**상호 운용성의 개선:**  
운영 체제는 다양한 플랫폼에서 상호 운용성을 보장할 수 있도록 개발되었다. 이를 위해 네트워크 프로토콜과 같은 표준이 개발되었고, 서로 다른 운영 체제 간의 데이터 교환도 가능하게 되었다.

## Mobilgeräte (1995-…):

**2008년 이후: "스마트폰"(iPhone, 최초의 Android 장치)이 "피처폰"을 대체.**  
이후에 "스마트폰"이 출시되면서 휴대 전화와 PDA의 기능이 통합되었다. iOS는 BSD UNIX와 Mach Mikro 커널에서 파생된 운영 체제다. Android는 수정된 Linux와 특수 시스템 라이브러리를 사용한다. 이들 운영 체제는 기기의 배터리 수명을 고려하여 리소스를 절약하고 성능을 유지하면서 더욱 강력한 기능을 제공한다.

## 가상화 기술(Virtualisierung)

가상화 기술은 하드웨어 자원을 가상적으로 분리하여 하나의 물리적 시스템에서 여러 가상 시스템을 실행할 수 있도록 한다.

최근 가상화 기술은 운영 체제에 대한 보안 기능을 가상화하기 위해 CPU의 보호 메커니즘까지 가상화한다. 이를 위해 Hypervisor라는 새로운 절대적인 제어 장치가 도입되었다. 이것은 운영 체제와 비슷한 방식으로 동작하지만, 더 높은 수준의 추상화를 제공한다. 이로 인해 하나의 물리적 시스템에서 여러 운영 체제를 실행할 수 있게 되었다.

## 클라우드 컴퓨팅(Cloud Computing)

네트워크를 통해 접근 가능한 공유 가능한 자원 풀(예: 네트워크, 서버, 스토리지, 애플리케이션 및 서비스)을 제공하여 적은 관리 노력이나 서비스 제공자와의 최소한의 상호 작용으로 신속하게 제공하고 해제할 수 있는 모델이다.

중요한 요소로 사용자는 클라우드 서비스 제공자의 표준 서비스를 통해 필요한 컴퓨팅 자원을 쉽게 이용할 수 있어야 한다. 즉, 요청한 자원이 빠르게 프로비저닝되어 사용 가능해야 하며, 공유 자원 풀을 사용하므로 다른 사용자와 자원을 공유한다는 것이다. 또한, 이러한 서비스는 사용자가 최소한의 관리 노력을 들이거나 서비스 제공자와 최소한의 상호 작용을 하여 신속하게 제공되어야 한다.

---

Quelle(text):

pdf dateien, [studocu](https://www.studocu.com/de/course/technische-universitat-berlin/systemprogrammierung/1514199)
pdf dateien, [studydrive](https://www.studydrive.net/de/course/systemprogrammierung/137292#documents)
Klausur pdf dateien, [Klausurensammlung der Freitagsrunde](https://docs.freitagsrunde.org/Klausuren/Systemprogrammierung/)
Vorlesung, Systemprogrammierung, [TU-Berlin]<https://www.tu.berlin/dos/>

Quelle(image):

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
<!-- <sup>[1)](#footnote_1)</sup>

<div class="notice--info">
<a name="footnote_1">1)</a>블라블라<br>
</div> -->
