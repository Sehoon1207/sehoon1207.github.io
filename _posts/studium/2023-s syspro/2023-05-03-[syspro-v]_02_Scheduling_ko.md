---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[syspro-v] 02 스케줄링(Scheduling)" #제목 확인
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

date: 2023-05-03 #날짜 확인
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

# 01 스케줄링 (Introduction Scheduling, Einführung Scheduling)

스케줄링은 컴퓨터에서 실행되는 작업들을 일정에 맞추어 적절하게 분배하는 것을 의미한다. 이때 스케줄링 알고리즘이 사용되며, 이를 적용하여 프로세스를 관리하는 운영체제 요소(모듈)를 스케줄러라고 한다. 이는 사용자가 컴퓨터의 성능을 주관적으로 느끼는데 큰 영향을 미치게 된다.

<div class="notice--danger">
<b>주관적인 인식이 중요한 스케줄링</b><br>
<br>
예를 들어, 이메일을 보내는 작업도 2초가 걸리고, 윈도우 창을 닫는 작업이 2초가 걸린다고 가정해 보자.  
이 두 작업이 순서대로 실행된다면, 사용자는 이메일이 보내지는 데 2초의 딜레이를 느끼게 된다. 반면에, 먼저 창을 닫은 다음에 이메일을 보내는 작업을 실행한다면, 2초의 딜레이는 눈에 띄지 않을 것이다. 이러한 예시처럼, 스케줄링은 사용자의 경험을 좌우하는 중요한 요소이다.
</div>

## 01-1 스케줄링 시간단위 Zeitskalen

### 01-1-1 Long Term Scheduling (LTS):

(프로세스의 생성(충분한 자원이 있는지 확인) 및 종료)

장기 스케줄링(Long-Term Scheduling)은 프로세스 생성 및 종료와 같은 오랜 시간이 걸리는 작업을 처리한다. 그래서 작업 스케줄러(job scheduler)라고도 한다. 장기 스케줄러는 어떤 프로그램이 처리를 위해 시스템에 허용될 지를 결정한다. 대기열(queue)에서 프로세스를 선택하고 실행을 위해 메모리에 로드하는 것이다. CPU 스케줄링을 위해 프로세스 로드를 메모리로 로드합니다.

작업 스케줄러의 기본 목표는 I/O 바운드 및 프로세서 바운드와 같은 균형 잡힌 작업 조합을 제공하는 것이다. 또한 다중 프로그래밍의 정도(the degree of multiprogramming)를 제어한다. 제어를 통해 다중 프로그래밍의 정도가 안정적이라면, 프로세스 생성되는 평균 속도와 시스템을 떠나는 프로세스의 평균 이탈 속도가 같다는 것이다.

일부 시스템에서는 장기 스케줄러를 사용할 수 없거나 최소화할 수 있으며, 시분할 운영 체제(Time-sharing operating systems)에는 장기 스케줄러가 없다. 프로세스가 상태를 new에서 ready로 변경한다면, 장기 스케줄러가 사용되고 있다는 것이다.

### 01-1-2 Medium Term Scheduling (MTS):

(프로세스의 적재 및 제거)

중기 스케줄링(Medium-Term Scheduling)은 메모리에 로드된 프로세스를 보조 저장장치로 이동하거나, 그 반대로 보조 저장장치에서 메모리로 로드한다.

중기 스케줄링(Medium-Term Scheduling)은 일종의 스와핑(swapping)이다. 중기 스케줄링은 메모리에서 프로세스를 제거하여 다중 프로그래밍의 정도를 줄인다. 중기 스케줄러는 교체된(스왑된) 아웃 프로세스를 처리하는 역할을 한다.

실행 중인 프로세스가 I/O 요청을 하면 일시 중단될 수 있다. 일시 중단된 프로세스는 완료를 향해 진행할 수 없습니다. 이 상태에서 프로세스를 메모리에서 제거하고 다른 프로세스를 위한 공간을 만들기 위해 일시 ​​중단된 프로세스를 보조 저장소로 이동시킨다. 이 프로세스를 스와핑(swapping)이라고 하며 이 프로세스를 스왑 아웃(swapped out) 또는 롤아웃(rolled out)이라고 한다. 프로세스가 섞이는 것을 개선하기 위해 스왑의 과정이 필요하다.

### 01-1-3 Short Term Scheduling (STS):

(준비된 프로세스에 대한 CPU 할당)  
(그리고 Dispatching (CPU 할당 수행)도 포함)

단기 스케줄링(Short-Term Scheduling)은 CPU를 할당할 준비가 된 프로세스를 선택한다. 이러한 프로세스는 대기 큐에서 대기하며, 선택된 프로세스는 CPU를 할당받아 실행된다.

CPU 스케줄러(CPU scheduler)라고도 한다. 주요 목표는 선택한 기준 세트에 따라 시스템 성능을 향상시키는 것이다. (프로세스의 준비 상태에서 실행 상태로의 변경 등 Ready -> Running) CPU 스케줄러는 실행할 준비가 된 프로세스 중에서 하나의 프로세스를 선택하고 그 중 하나에 CPU를 할당한다.

디스패처(dispatcher)라고도 하는 단기 스케줄러는 다음에 실행할 프로세스를 결정한다. 단기 스케줄러는 장기 스케줄러보다 빠르다.

<div class="notice--info">
"스케줄링"이라는 용어는 일반적으로 "CPU 스케줄링", 즉 STS를 의미한다.<br>
STS를 통해 프로세서를 프로세스에 할당하기 위한 간단하고 효율적으로 실행 가능한 전략을 고안할 수 있다.
</div>

간단한 스케줄링 문제에 대한 예를 들면 다음과 같다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/02_schedulingProblem.png?raw=true" width="1000px"/>

## 01-2 스케줄링을 위한 매개변수 8가지(Gestaltungsparameter für Scheduling)

스케줄링을 하기전에 몇 가지 확인해야할 항목들이 있다.

- **01-2-1 프로세스 수량이 정적인지 또는 동적인지(Prozessmenge statisch oder dynamisch)**

**정적 프로세스**: 더 이상 프로세스가 추가되지 않는다. 즉, 모든 프로세스가 지정되고 실행 가능하다.  
**동적 프로세스**: 실행 중에 응답이 필요한 새 프로세스를 추가될 수 있다.

- **01-2-2 온라인 또는 오프라인 스케줄링(On line oder Off line Scheduling)**

**Off line** (이전): 향후 도착을 포함한 모든 프로세스를 미리 알고 있는 상태.  
**On line** (runtime중): 실행 중인 프로세스에 대한 정보만을 가지고 판단해야 하는지.(현재 프로세스만 알고 불완전한 정보에 기반한 의사결정)

- **01-2-3 플랫폼이 단일 프로세서/다중 프로세서인지**

**단일 프로세서**: 하나의 프로세서만 사용 가능  
**다중 프로세서**: 동일하거나 다를 수 있는 다중 프로세서. 프로세서의 실행 속도가 다를 수도 있다.

- **01-2-4 선점 또는 비선점**

**비선점 스케줄링**: 어떤 프로세스가 CPU를 점유하고 있다면 해당 프로세스의 작업이 완료될 때까지 다른 프로세스가 강제로 CPU를 빼앗아 사용할 수 없는 스케줄링 기법  
종류 : FCFS, SJF, 우선순위, HRN, 기한부 알고리즘  
**선점 스케줄링**: 하나의 프로세스가 CPU를 점유하고 있을 때, 우선순위가 높은 다른 프로세스가 CPU를 강제로 빼앗아 사용할 수 있는 스케줄링 기법  
종류 : Round Robin, SRT, 선점 우선순위, 다단계 큐, 다단계 피드백 큐 알고리즘

- **01-2-5 프로세스간에 종속성이 있는지**

**순서관계, 프로그램의 병렬 프로세스 동기화 순서, 통신시간, 전환시간** 등  
Reihenfolgebeziehung (partielle Ordnung), Synchronisierte Zuordnung der parallelen Prozesse eines Programms, Kommunikationszeiten, Rüstzeiten (Umschaltzeiten)

- **01-2-6 고려해야할 우선순위가 있는지**

**정적인 우선순위**: 외부로부터 주어짐.  
**동적 우선순위**: 실행 중에 결정됨.

- **01-2-7 고려해야 할 목표 시간이 있는지**

특정시간에 프로세스를 종료해야 하거나 **마감시간(Deadline)**이 있는 경우.

- **01-2-8 정기적으로 반복되는 프로세스가 있는지**

## 01-3 고려한 매개변수에 따른 결정해야할 사항들

- **일정 기간** (Länge des Ablaufplans) -> min
- **최대 응답 시간** (Maximale Antwortzeit) -> min
- **평균(가중) 응답 시간** (Mittlere (gewichtete) Antwortzeit) -> min
- **프로세서 수** (Anzahl Prozessoren) -> min
- **처리량** (Durchsatz) -> max
- **프로세서 활용** (Prozessorauslastung) -> max
- **최대 지연** (Maximale Verspätung) -> min

<div class="notice--info">
<b>스케줄링 목표에 대한 세부적인 고려사항</b><br>
<br>
<b>모든 시스템 유형의 대상 (Ziele für alle Systemarten)</b><br>
-공정성: 컴퓨팅 시간을 지원자에게 공정하게 분배<br>
-정책 집행: 투명한 의사 결정 기준<br>
-균형: 시스템의 모든 부분이 사용 중인 상태.<br>
<br>
<b>일괄(단계별) 처리 시스템의 대상 (Ziele bei Stapelverarbeitungssystemen)</b><br>
-처리량 최대화(예: 작업/시간 단위, 예: 작업/시간)<br>
-처리 시간 최소화: 주문 시작과 주문 종료 사이의 시간<br>
<br>
<b>인터랙티브 시스템 (Interaktive Systeme)</b><br>
-사용자 작업에 대한 응답 시간 최소화<br>
-"단순" 요청은 빠르게 진행되어야 한다.<br>
<br>
<b>실시간 시스템 (Echtzeitsysteme)</b><br>
-목표 시간 준수
</div>

---

# 02 스케줄링 전략 10가지 (Schedulingstrategien)

일반적인 스케줄링 전략에는 선입선처리, 우선순위, 라운드 로빈 등이 있다. 이러한 전략은 작업의 특성에 따라 선택된다. 이러한 전략을 통해 달성하고자 하는 목표는 높은 효율성, 프로세서의 높은 활용도, 인터랙티브 프로세스의 낮은 응답시간, CPU의 공정한 분배를 통한 공정성, 그리고 프로세스 간의 성능과 대기시간이 있다.

## 02-1 선입 선처리 (FCFS: First-Come First-Served) 스케줄링

프로세스들이 **도착한 순서대로 CPU를 할당하는 방법**이다. 도착 순서란, **프로세스들이 준비 대기열(Ready Queue)에 연결되는 순서**를 말한다. **비선점형**이다.

이 처럼 먼저 온 프로세스가 뒤에 온 프로세스에 영향을 많이 주는데 이런 현상을 **호위 효과(Convoy Effect)** 라고 한다.

## 02-2 후입 선처리 LCFS (Last Come First Served) 스케줄링

## 02-3 LCFS PR (Last Come First Served Preemptive Resume)

## 02-4 Zeitscheibenbetrieb (Time Sharing Mode)

## 02-5 라운드 로빈 RR (Round Robin): Zeitscheibenlänge

RR은 전형적인 **선점형 스케줄링전략**으로, 모든 프로세스에게 **동일한 최대 CPU 점유 시간** 즉, 타임 권텀을 설정하고 처리중인 프로세스의 CPU실행 시간이 타임 퀀텀을 초과하면 CPU를 강제로 회수하여 다음 프로세스에게 할당하는 방식이다. **현대 대부분의 시분할 운영체제에서 채택한 방식**이다.

RR스케줄링 전략에서 적절한 타임 퀀텀의 설정은 매우 중요하다. 만약 타임 퀀텀을 아주 작게 설정하면 CPU할당이 교체될 때마다 일어나는 프로세스 문맥 교환 횟수가 증가하여 시스템 부담을 증가시키고, 이는 전체적인 처리율의 감소로 이어진다. 또한 타임 퀀텀을 늘리는 것도 평균응답시간이 늘어난다.

## 02-6 PRIO-NP (Priorities Non preemptive)

## 02-7 PRIO-P (Priorities Preemptive)

Prioritätsinvertierung

## 02-8 최단 작업 우선 (SJF: Shortest Job First)

준비 대기열에 존재하는 프로세스들을 도착한 순서대로 처리하는 것이 아니라, 이들 중 **CPU버스트가 가장 짧은 프로세스에게 CPU를 먼저 할당하는 전략**이다. SPN(Shortest Process Next)라 부르기도 한다. **비선점형**이다.

그러나, 계산 위주의 긴 프로세스에게 CPU가 할당된 상태에서 다수의 입출력 위주 짧은 프로세스들이 도착한다면 FCFS에서와 마찬가지로 **호위 효과** 가 나타날 수 있다. 또한 CPU가 짧은 프로세스에게 할당된 상태에서 짧은 프로세스만 지속적으로 도착한다면, 상대적으로 긴 프로세스는 계속해서 지연되는 단점이 있는데 이를 **기아상태(Starvation)** 라고한다.

## 02-9 최단 잔여 시간 우선 SRTN (Shortest Remaining Time Next)

(SRTF : Shortest Remaining Time First 라고도 함.)

SJF스케줄링의 단점을 보완하기 위해, 준비 대기열에 새로운 프로세스가 도착하면, 현재 진행 중인 프로세스의 잔여 실행 시간과 새로운 프로세스의 CPU버스트 시간을 비교하여 새 프로세스의 실행 시간이 더 짧으면 CPU를 강제 회수하여 새로운 프로세스에게 할당하는 **선점형 스케줄링** 전략이다.

CPU나 입출력 장치의 **이용률 저하 현상 발생을 억제**할 수 있으나, **기아 상태 발생 가능성은 더 높인다.**

## 02-10 최고 응답률 우선 HRRN (Highest Response Ratio Next)

(HRRF : Highest Response Ratio First 라고도 함.)

각 프로세스의 응답률을 계산하여 **응답률이 가장 큰 프로세스를 먼저 처리**한다.

`응답률 = (준비 큐 대기 시간 + CPU 버스트 시간) / (CPU 버스트 시간) = 1 + ((준비 큐 대기 시간) / (CPU 버스트 시간))`

CPU버스트 시간에 대한 준비 대기열 대기 시간이 상대적으로 클수록 응답률이 높아져 CPU스케줄링 우선 순위가 높아진다. 만약 대기 시간이 동일하다면 즉, 동일 시각에 도착한 프로세스들에게는 CPU버스트 시간이 짧을수록 응답률이 높아져 SJF나 SRTF와 동일한 스케줄링이 적용된다. HRN(Highest Response Next)라고 하기도 한다. **선점형이나 비선점형 중 어느 형태로도 운영이 가능**하다.

---

# 03 Multilevel-Scheduling

다단계 스케줄링은 우선순위, I/O 사용률 등을 고려하여 작업을 여러 그룹으로 분류하고 각 그룹에서 서로 다른 스케줄링 전략을 사용한다.

다단계 큐(MQ : Multi-level Queue)
다단계 피드백 큐(MFQ : Multi-level Feedback Queue) 스케줄링

# 04 Scheduling mit Sollzeitpunkten

Scheduling with deadline은 작업이 완료되어야 하는 시간을 고려하여 스케줄링한다. 이러한 전략은 실시간 시스템에서 중요하다.

# 05 Fallbeispiele (Linux und Windows)

Linux 및 Windows에서는 스케줄러가 사용되며, 각각의 운영 체제에서는 다른 스케줄링 전략이 사용된다. Linux에서는 Completely Fair Scheduler (CFS) 및 Real-Time Scheduler가 사용되며, Windows에서는 Multilevel Feedback Queue Scheduler가 사용된다.

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
