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

### 01-1-1 명시적/암시적 프로세스 상호작용 Explizite / Implizite Prozessinteraktion

**Implizite Prozessinteraktion**은 프로세스가 시스템 함수를 호출하고 이를 통해 다른 프로세스들과 상호작용하는 경우를 의미한다. 호출하는 프로세스는 이러한 상호작용이 일어나는 것을 인지하지 못한다. 대신, 시스템 함수를 호출하면서 일시적으로 차단되고 상호작용이 끝난 후에 다시 시작된다. 이러한 상호작용은 일반적으로 운영 체제에 의해 관리되며, 프로세스는 결과를 받기 전까지 대기한다. 이러한 방식은 간단하고 사용하기 쉽지만, 다른 프로세스가 호출한 시스템 함수에 영향을 미칠 수 있다는 단점이 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-1_Klassifikation.png?raw=true" width=1000px />

#### Implizite Prozessinteraktion Beispiel

**Unix 프로세스의 고전적인 조합: 파이프**

```
user@machine:~$ ls -l
total 8
rw-r--r-- 1 user user 3 Jun 4 12:24 foo.txt
rw-r--r-- 1 user user 3 Jun 4 12:26 bar.txt
user@machine:~$ ls -l | grep foo
rw-r--r-- 1 user user 3 Jun 4 12:24 foo.txt
```

**생산자에서 소비자 프로세스로 데이터의 단방향 흐름**

```
// ls Prozess
while (Verzeichniseinträge){
  write (stdout , Zeile)
}
```

```
//grep Prozess
while (Datenstrom nicht zu Ende) {
  read (stdin , Zeile);
  if (Zeile passt zu Filter) {
    ausgeben(Zeile);
  }
}
```

<div class="notice--info">
위의 예시는 Unix 파이프(Pipe)를 사용한 Implizite Prozessinteraktion에 대한 예시 이다.<br>
<br>
ls는 디렉토리 내부의 파일 목록을 출력하고, grep은 ls에서 출력된 결과 중에서 주어진 조건에 해당하는 부분만 걸러내는 역할을 한다.<br>
<br>
이러한 두 프로세스는 파이프라는 것을 통해 상호작용하며, ls가 출력하는 결과를 grep이 읽어서 조건에 맞는 결과만을 출력할 수 있다. 이때, 파이프를 통해 ls가 출력하는 결과는 grep이 사용할 수 있도록 표준 입력으로 제공된다.<br>
<br>
이처럼 파이프를 통해 두 프로세스 사이에서 데이터를 주고받는 것은 암묵적인(inter-process communication, IPC) 방식으로 이루어진다. 파이프를 통해 데이터가 전달되는 동안 ls는 자신이 실행되는 동안 grep의 실행에 대해서 전혀 알지 못하며, grep 역시 ls의 실행에 대해서 전혀 알지 못한다. 따라서 이는 암묵적인 방식으로 이루어진 프로세스 간 상호작용이다.<br>
<br>
그러나 ls 프로세스가 데이터를 출력하는 속도가 grep이 읽어들이는 속도보다 느리다면, grep은 데이터를 받을 때까지 대기(block) 상태에 놓이게 된다. 이는 파이프의 한계로, 파이프에는 데이터가 누적되지 않기 때문이다. 따라서 이러한 경우에는 ls 프로세스가 파이프로부터 데이터를 제공하기 전까지는 grep 프로세스가 대기하게 되어, 실행 시간이 늘어날 수 있다. 이는 암묵적인 방식에서도 데이터의 처리 속도에 따른 성능 이슈가 발생할 수 있음을 보여준다.<br>
</div>

### 01-1-2 프로세스 상호 작용: 경쟁 (Prozessinteraktion: Konkurrenz)

Prozesssynchronisation은 두 개 이상의 프로세스가 동시에 배타적으로 사용 가능한 자원, 예를 들어 프린터를 동시에 요청할 때 발생한다. 이러한 경우, 적절한 조정을 통해 액세스 시도의 직렬화를 달성해야 한다. 이처럼 n 개의 경쟁 프로세스가있는 경우, n-1 프로세스가 지연되도록하는 방법 등을 사용하여 경쟁 프로세스의 시간 조정이 필요하다. 이를 위해 사용되는 동기화 메커니즘은 **상호배제, 세마포어, 모니터** 등이 있다.

## 01-2 시그널링 Signalisierung:

프로세스간 통신 및 동기화에 사용되는 기본적인 기술 중 하나다.  
이를 통해 한 프로세스는 다른 프로세스에게 이벤트 또는 상태 변경을 알릴 수 있다.

시그널링은 경쟁 프로세스가 공유 변수 및 신호를 통해 서로 상호 작용하는 프로세스 조정의 한 형태다. 시그널링의 기본 목표는 데이터 일관성을 보장하기 위해 공유 메모리 영역에 대한 독점 액세스를 허용하는 것이다.

### 01-2-1 Grundform der Signalisierung: blockierendes

#### 01-2-1-1 Einfachste Form: Reihenfolgebeziehung (Signalisierung)

신호의 가장 간단한 형태는 선행 관계의 순서로, 한 프로세스가 작업을 완료한 다음 다른 프로세스에 작업을 시작하도록 신호를 보내는 것이다. 그러나 특정 조건을 기다리거나 경쟁 프로세스/스레드에 의한 변수 잠금/잠금 해제와 같은 다른 신호 메커니즘도 있다.

**Operationensignal (s) und wait (s) mit Sperrvariable s**

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-2_Operationen.png?raw=true" width=1000px />

"신호" 및 "대기" 작업은 기본 신호 메커니즘이다. "신호"는 다른 프로세스/스레드에 신호를 주고 "대기"는 신호를 받을 때까지 실행 중인 프로세스/스레드를 차단한다. 이 두 작업은 일반적으로 공유 메모리 영역에 대한 독점 액세스를 허용하는 잠금 변수 s로 수행된다. 프로세스/스레드가 신호를 실행하면 잠금 값이 0에서 1로 변경되며 이는 잠금 범위가 잠겨 있음을 의미한다. 잠금 값이 이미 1로 설정되어 있으면 프로세스/스레드가 차단되고 다른 프로세스/스레드의 신호를 기다린다.

#### 01-2-1-2 Einfachste Realisierung: Busy waiting (aktives Warten)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-3_Busywaiting.png?raw=true" width=1000px />

Busy Waiting (활발한 대기)은 프로세스나 스레드가 어떤 조건을 충족하기 전까지 무한 반복하는 상태다. 이것은 특히 고전적인 신호 보내기 메커니즘에서 사용되며, 신호를 기다리는 프로세스 또는 스레드가 일반적으로 일시 중단된다. 이 상태는 조건이 충족될 때까지 CPU 시간을 낭비하기 때문에 시스템의 전반적인 성능에 부정적인 영향을 미치게 된다. 그러나 매우 짧은 대기 시간이 필요한 경우에는 사용할 수 있다.

Busy Waiting은 하드웨어에 의존하는 동기화 메커니즘과 같이 사용할 때 성능 저하의 원인이 될 수 있다. 따라서 이를 피하기 위해 기다리는 프로세스나 스레드를 중지시키는 슬립 메커니즘을 사용하는 것이 좋다. 이렇게 하면 대기열에서 대기하는 프로세스나 스레드의 수를 줄일 수 있으며, 대기 중인 프로세스나 스레드의 CPU 사용 시간을 줄일 수 있다.

```
//
Signalisierung mit Busy Waiting

struct Signal {                 // Version 1
  boolean s;
} so = { false };               // Initialisierung

void signal( struct Signal *so) {
  so-->s =
}

void wait( struct Signal *so) {
while (so -->s == false) { ; }  // Warten, bis gesetzt
so-->s = false;
}
```

#### 01-2-1-3 Grundform der Signalisierung: blockierendes Warten

신호의 기본 형태: 차단 대기

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-4_blockierendesWarten.png?raw=true" width=1000px />

시그널링의 가장 간단한 구현은 조건이 충족될 때까지 기다리기 위해 조건의 상태를 반복적으로 쿼리하는 활성 대기다. 그러나 이 방법은 CPU 용량을 낭비하고 유용한 작업을 위해 CPU를 차단한다.

따라서 조건을 기다리고 있을 때 대기 중인 프로세스를 "차단된" 상태로 전환하는 차단 대기에 대한 솔루션이 있다. 이 상태에서 프로세스는 CPU를 해제하여 다른 유용한 작업에 사용할 수 있다. 차단된 프로세스는 예를 들어 차단 해제 신호와 같은 외부 신호에 의해서만 다시 준비 상태로 돌아가고 작업을 계속할 수 있다.

```
//Signalisierung mit blockierendem Warten

struct Signal {                       // Version 2
  boolean s;
  process *
} so = { false, NULL };               // Initialisierung

void signal( struct Signal *so) {
  so ->s = true;
  if (so ->wp != NULL) {              // Wartet ein Prozess?
      deblock(so--> wp);              // Blockierung aufheben
      so ->wp = NULL;                 // Struktur zurücksetzen
  }
}

void wait( struct Signal *so) {
  if (so ->s == false) {               // noch kein
      so->wp = MYSELF;
      block();
  }
  so->s = false;
}
```

### 01-2-2 양방향 동기화 Wechselseitige Synchronisierung

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-5_WechselseitigeSynchronisierung.png?raw=true" width=1000px />

상호 동기화는 두 개 이상의 프로세스가 실행을 계속하기 전에 관련된 모든 프로세스가 공통 지점에서 만날 때까지 기다리는 것을 의미한다. 동기화는 "대기" 및 "신호"와 같은 동기화된 작업을 사용하여 이루어진다. "대기" 및 "신호" 작업의 일반적인 대칭 적용을 `"랑데뷰(Rendezvous)"`라고도 한다. 랑데부 작업을 사용하면 프로세스가 동기화되어 작업할 수 있으므로 교착 상태나 경쟁 조건과 같은 잠재적인 문제를 피할 수 있다.

<div class="notice--info">
Rendezvous는 상호 동기화의 하나로, 두 개의 프로세스가 서로를 만날 때까지 서로 기다리게 하는 동기화 기법이다. 이를 위해서는 두 개의 프로세스가 동일한 지점에서 만날 때까지 실행을 지연시켜야 한다. 이러한 지점을 "rendezvous point" 또는 "synchronization point"라고 한다. 이 기법은 경쟁 조건을 방지하기 위해 두 프로세스가 상호작용할 수 있는 환경을 만든다. Rendezvous는 다중 프로세스 간 통신 및 동기화를 달성하는 데 사용된다.
</div>

## 01-3 크리티컬 섹션 Kritische Abschnitte:

공유 자원에 대한 동시 액세스를 제어하기 위한 방법 중 하나다.
이를 통해 오직 하나의 프로세스만이 공유 자원에 액세스하도록 보장할 수 있다.

크리티컬 섹션(크리티컬 영역이라고도 함)은 여러 프로세스 또는 스레드에 의한 동시 또는 동시 실행으로 인해 오류가 발생할 수 있는 프로그램의 작업 시퀀스를 나타낸다. 예를 들어 독점적으로 사용 가능한 리소스에 액세스하거나 연결 목록과 같은 공유 구조를 수정하는 경우가 이에 해당할 수 있다.

크리티컬 섹션을 보호하기 위해 일반적으로 **"잠금 플래그(Sperrflag)"**라는 잠금 변수가 사용된다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-01_99_kritischeAbschnitte.jpg?raw=true" width=500px />

이 변수를 잠그거나 잠금 해제하는 목적은 한 번에 하나의 프로세스나 `스레드(thread)`만 임계 영역에 있고 다른 프로세스나 스레드는 임계 영역이 해제되기를 기다리는 것이다. 이렇게 하면 여러 프로세스나 스레드가 중요한 리소스에 동시에 액세스하여 일관되지 않은 결과를 생성하는 것을 방지할 수 있다.

<div class="notice--info">
스레드(thread)는 프로세스 내에서 실행되는 작업의 단위다. 각 프로세스는 하나 이상의 스레드를 가질 수 있으며, 각 스레드는 동시에 실행될 수 있다. 스레드는 프로세스의 메모리 공간을 공유하므로 스레드간 데이터 전송이 빠르고 효율적이다. 이로 인해 멀티스레드 프로그래밍은 멀티프로세스 프로그래밍보다 더 빠르고 경제적인 해결책이 될 수 있다.<br>

스레드는 프로세스 내에서 실행되는 작업의 단위로, 각각의 스레드는 별도의 스택 메모리를 가지고 있으며 프로세스 내에서 공유하는 데이터 섹션과 힙 메모리를 공유한다. 스레드는 프로세스 내에서 생성 및 종료할 수 있으며, 생성된 스레드는 각각의 실행 흐름을 가지고 작업을 수행한다. 스레드의 생성, 관리 및 동기화를 위한 API는 운영체제 또는 런타임 라이브러리에서 제공된다. 스레드를 사용하면 병렬 처리를 통해 성능을 향상시키고, 반응성이 높은 프로그램을 작성할 수 있다.<br>

</div>

### 01-3-1 크리티컬 섹션을 사용한 프로세스 동기화

여러 프로세스가 공유하는 데이터를 변경하는 코드 영역(크리티컬 섹션)에는 오직 한 프로세스만 들어갈 수 있어야 합니다. 그렇지 않으면 데이터의 일관성이 깨질 수 있다.

프로세스는 상호 배타적이어야 함(상호 배제)

### 01-3-2 크리티컬 섹션 처리에 대한 추가 요구 사항들

• **프로세서 속도에 대한 가정 없음**  
왜냐하면, 프로세스가 빨리 실행될지 느리게 실행될지는 운영체제에서 제어할 수 없기 때문.

• **프로세스의 수와 순서에 대한 가정 없음**  
언제 어떤 프로세스가 실행될지는 운영체제에서 결정되기 때문.

• **중요하지 않은 영역에서 프로세스 지연 없음**  
크리티컬 섹션 이외의 부분에서도 프로세스들이 불필요하게 블록되는 상황을 피해야 함.

• **교착 상태 없음, 즉 프로세스가 서로 차단하면 안 됨**  
두 개 이상의 프로세스가 다른 프로세스를 기다리며 무한정 블록되는 상황이 발생하지 않도록 조치가 필요

• **프로세스는 한정된 시간 후에 임계 영역에 진입할 수 있어야 함**  
언젠가는 크리티컬 섹션에 진입할 수 있도록 모든 프로세스에 공평한 기회를 주어야 함.

• **중요한 영역에서 제한된 체류 시간**  
프로세스가 크리티컬 섹션에서 무한정 머무르는 것을 막기 위해, 프로세스의 처리시간이 일정한 시간 이내에 끝나도록 해야 함.

### 01-3-3 잠금 플래그가 있는 중요 섹션 Kritische Abschnitte mit Sperrflags

• idea : 차단플래그 구간 진입시 초기에 차단플래그를 해제하여 차단플래그 해제 후 타 프로세스 제외

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-7_KritischeAbschnittemitSperrflags.png?raw=true" width=1000px />

#### Beispiel 1 호텔예약

```
Warte auf Signal vom Terminal

if (Freizimmer>0) { //Initial Freizimmer = anzahl;
    i= SucheZimmer
    Zimmer[i].status = belegt;
    Zimmer[i].gast= enterName();
    Freizimmer --;
    PrintMessage (Zimmer i reserviert);
} else PrintMessage (Hotel belegt);
```

`예약프로그램이 동시에 실행되어 충돌발생`

<div class="notice--info">
위의 예시에서, 두 개의 프로세스 A와 B가 호텔 예약 프로그램에 접근하여 동시에 실행될 수 있으며, 결과적으로 예약 정보에 충돌이 발생할 수 있다. 이러한 경우 불일치된 데이터가 발생할 수 있으므로, 프로세스 간의 상호 배제 (mutual exclusion)이 필요하다. 즉, 한 번에 하나의 프로세스만이 임계 구역 (critical section)에 접근할 수 있도록 해야한다. 이러한 방법을 통해 프로세스 간에 상호작용을 동기화하여 불일치된 데이터가 발생하지 않도록 한다.
</div>

#### Beispiel 2 잘못된 동기화의 예

```
/* thread routine */
void *count(void *arg) {
  int i;
  for (i=0; i<NITERS; i++)
    cnt++;
  return NULL;
}
```

```
count:
    [...]
    lw    v0, 40 (gp)
    addiu v0, v0, 1
    sw    v0, 40 (gp)
    [...]
```

```
lw = load word from address
40( gp ) into v0
addiu = add immediate
unsigned no overflow:v0=v0+1
sw = store word at the
specified address
gp = global pointer
```

A: 값 10 → v0을 읽고, v0을 증가시킵니다.  
B로 전환: 다중 패스, cnt가 20으로 증가  
A로 전환: `cnt 변수에 v0(11이 아닌 값)을 사용함.`

<div class="notice--info">
이 예시는 2개의 스레드 A와 B가 같은 변수 cnt에 접근하면서 발생할 수 있는 문제를 보여준다. A는 cnt 값을 읽고 증가시키고 다시 cnt에 저장하는 작업을 수행하는데, 이 작업 중 B가 스케줄링되어 여러 번 반복하는 작업을 수행할 수 있다. 그 후 A가 다시 스케줄링되어 cnt 값을 저장하는데, 그 시점에서 A는 cnt 값이 이미 증가된 값을 읽어들이고 저장하게 된다. 이러한 경우에는 A가 증가시킨 값이 제대로 반영되지 않아서 몇 개의 <b>반복이 누락</b>될 수 있다.<br>
<br>
이러한 문제는 스레드나 프로세스 등이 동시에 공유자원에 접근할 때 발생할 수 있는 문제로, 이를 해결하기 위해서는 동기화 메커니즘을 사용하여 <b>공유자원에 대한 접근을 제어</b>해야 한다. 이를 통해 한 번에 하나의 스레드나 프로세스만이 공유자원에 접근할 수 있도록 보장할 수 있다.<br>
</div>

#### Beispiel 3 잘못된 잠금 플래그 작업

```
/* teste&setze Sperrflag */
void wait(boolean *flag) {
  while (*flag == false)
  { ; }
  *flag = false
}
```

```
wait:
      [...]
T:    lw    v0, 0(a0)
      beqz  v0, T
      [...]
      sw zero , 0(a0)
      [...]
```

```
beqz v0,T --> # branch to T if register
v0 == 0
```

A: 잠금 플래그 읽기 → v0  
조건 테스트 ok

B로 전환:  
잠금 플래그 읽기 → v0  
조건 테스트 ok

그런 다음 A와 B에서:  
`차단 플래그 설정했지만 동시에 영역 진입`

<div class="notice--info">
이 내용은 두 개의 스레드가 Sperrflag를 이용한 동기화 작업을 수행할 때 발생할 수 있는 문제점을 설명하고 있다. 두 스레드 A와 B가 wait 함수에 동시에 진입하게 되면, Sperrflag를 확인하고서 자신이 먼저 들어갈 수 있는지 확인하는 과정에서 두 스레드가 모두 Sperrflag를 확인하고 자신이 먼저 진입할 수 있는 것으로 판단하게 된다. 따라서 둘 다 임계 영역에 진입하게 되어 이상 동작을 하게 된다.<br>
<br>
해결 방법으로는, 스레드 A와 B가 Sperrflag를 사용하기 전에 다른 플래그나 변수를 사용해서 해당 영역이 현재 누구에 의해 사용 중인지 확인해야 한다. 이를 통해 두 스레드가 동시에 진입하는 것을 방지할 수 있다. 또한, 뮤텍스나 세마포어 같은 전용 동기화 기법을 사용하여 이러한 문제를 해결할 수도 있다.<br>
</div>

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-8_Nebenl%C3%A4ufigkeit.png?raw=true" width=1000px />

<div class="notice--danger">
연동 실행의 경우 쿼리와 조건 변경 사이의 전환이 발생하고 그 결과 둘(또는 그 이상)의 프로세스가 임계 영역에 진입할 가능성을 배제할 수 없다.
</div>

### 01-3-4 하드웨어 기반 조치

하드웨어 기반 조치를 사용하여 프로세스 또는 스레드 간의 동기화 문제를 해결할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-9_Hardwaregest%C3%BCtzteMa%C3%9Fnahmen-.png?raw=true" width=1000px />

두 가지 일반적인 접근 방식은 **CAS(Compare and Swap)와 LL/SC(Load Linked/Store Conditional)**가 있다.

이러한 명령을 사용하면 조건을 원자적으로 확인하고 필요한 경우 변경할 수 있다. 조건이 일치하면 새 조건이 설정되고 결과가 반환된다. 이렇게 하면 조건 확인 및 설정과 중요 영역에 들어가는 다른 프로세스 사이의 전환을 방지할 수 있다.

특수 기계 명령어를 사용하면 잠금 플래그 작업을 더 안전하게 만들 수 있다. 이제 원자적으로 실행할 수 있으므로 동시성 문제가 발생하지 않기 때문이다. 이렇게 하면 한 번에 하나의 프로세스만 임계 영역에 들어갈 수 있고 이 프로세스가 유한한 시간 후에 다시 해당 영역을 떠날 수 있다.

## 01-4 운영 체제 지원 프로세스 상호 작용 Betriebssystemgestützte Prozessinteraktion:

• 활성 대기(Aktives Warten)는 리소스를 낭비한다.

현재 프로세스가 임계 영역을 벗어날 때까지 대기 중인 프로세스 차단하는 방법  
대기열에서 다음 프로세스 선택(FCFS, 우선 순위 또는 기타 전략)하는 방법  
두 방법 모두 비효율적이다.

• 프로세스 동기화를 위한 운영 체제 지원 (Betriebssystemunterstützung für Prozesssynchronisation)을 통해 효율적으로 동기화할 수 있다. 운영 체제 지원 프로세스 동기화는 세마포어(Semaphore (Dijkstra, 1965)) 또는 모니터(Monitore)로 구현할 수 있다.

프로세스 상태(준비, 실행, 차단, 종료)에 대한 잠금을 직접 설정하고 해제함으로써 세마포어와 모니터는 한 번에 하나의 프로세스만 중요한 영역에 있도록 할 수 있다. 모든 주요 플랫폼에서 사용할 수 있는 원자 검사/설정 명령 시퀀스를 사용할 수 있다.

### 01-4-1 세마포어(Semaphore)

세마포어는 프로세스를 동기화하는 방법으로, **음수가 아닌 초기화 카운터**와 **관련된 프로세스에 대한 참조 목록**으로 구성됩니다. 세마포어(Semaphor)는 여러 프로세스들 간의 동시 접근을 제어하기 위한 도구로, 초기값으로 설정된 카운터를 기준으로 임계 구역에 들어갈 수 있는 프로세스의 개수를 제어한다.

**기본 연산 "P(s)"("대기"라고도 함)**는 세마포어 카운터의 현재 값이 1씩 감소함을 의미한다. 분자가 음수가 아니면 프로세스는 임계 영역(kritischen Bereich)에 들어갑니다. 카운터가 음수이면 프로세스가 차단된다.

<div class="notice--info">
P-Operation은 Semaphor 카운터가 0보다 작아지면, 즉 이미 Semaphor가 사용중일 때는 현재 프로세스를 차단하고 준비된 다른 프로세스로 전환한다. 이 때, Semaphor의 초기값에 따라 몇 개의 프로세스가 동시에 임계 구역에 진입할 수 있는지 결정된다. 초기값이 1이면 이진 변수로서 상호배제를 구현할 수 있고, k(정수)이면 최대 k개의 프로세스가 동시에 접근 가능하다.
</div>

**기본 작업 "V(s)"(일명 "신호")**는 프로세스가 임계 영역(kritischen Bereich)을 벗어나 세마포어 카운터가 1씩 증가함을 의미한다. 카운트가 음수이면 대기 프로세스가 차단 해제된다.

<div class="notice--info">
V-Operation은 Semaphor의 사용이 끝나면 다른 프로세스가 사용할 수 있도록 차단된 프로세스를 해제한다. 이 때, 대기열에 대기 중인 프로세스는 일반적으로 도착 순서대로 대기열에 추가되며(FIFO), 실시간 운영체제에서는 우선순위 고려 등 다른 요인으로 인해 FIFO 순서와 다르게 대기열을 처리할 수 있다.
</div>

#### Beispiel 1: der Operationen P und V

```
void P(Semaphor s) {
    s.zaehler--;                            // Zähler dekrementieren
    if (s.zaehler < 0) {                    // kleiner 0: Semaphor sperrt
        currentProcess.state = BLOCKED;
        enqueue(s.queue , currentProcess);
        scheduler();                        // anderen Prozess auswählen
    }
}

void V(Semaphor s) {
    if (s.zaehler < 0) {                    // es gibt wartende
        Process p = dequeue (s.queue);      // einen auswählen... (FCFS?)
        p.state = READY;                    // ... und aufwecken
        /* ggf. auch hier: scheduler () (Verdrängung prüfen!) */
    }
    s.zaehler++;                            // Zähler inkrementieren
```

<div class="notice--warning">
zaehler(양수): 세마포어를 통과하도록 허용된 프로세스 수 <br> 
zaehler(음수): 세마포어에서 이미 대기 중인 프로세스 수
</div>

<div class="notice--info">
위 코드는 P-Operation과 V-Operation의 구현을 보여준다.<br>
<br>
P-Operation은 주어진 세마포어의 zaehler 값을 1 감소시킨다. 만약 감소된 값이 0보다 작으면, 현재 프로세스를 BLOCKED 상태로 설정하고 해당 세마포어의 대기열에 enqueue 한다. 그리고 scheduler()를 호출하여 다른 준비된 프로세스를 선택한다.<br>
<br>
V-Operation은 주어진 세마포어의 zaehler 값을 1 증가시킨다. 만약 zaehler 값이 0보다 작으면, 대기열에서 하나의 프로세스를 dequeue하여 READY 상태로 변경한다. 그리고 나서 해당 프로세스가 실행할 수 있도록 스케줄러에 의해 선택된다.<br>
<br>
따라서, 세마포어는 P-Operation으로 임계영역에 진입하는 프로세스 수를 제어하며, V-Operation으로 임계영역에서 나온 프로세스를 해제하여 대기열의 프로세스가 순차적으로 실행될 수 있도록 한다.<br>
</div>

#### Beispiel 2: Einfacher kritischer Abschnitt

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-10_EinfacherkritischerAbschnitt.png?raw=true" width=1000px />

`두 프로세스 P1과 P2가 임계 영역에 진입하기 위해 경쟁하고 있다.`

<div class="notice--warning">
Mutex(상호배제) = Mutual Exclusion (Gegenseitiger Ausschluss, Wechselseitiger Ausschluss)
</div>

#### Beispiel 3: 생산자 소비자 시스템 Erzeuger Verbraucher System

• 생산자는 버퍼를 채운다.  
• 소비자는 버퍼 콘텐츠를 소비한다.

이 두 프로세스는 공통 버퍼를 통해 통신한다고 하자.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-11_VerbrauchermitSemaphoren.png?raw=true" width=1000px />

이 상호작용에서는 버퍼의 용량이 한계가 있기 때문에, 버퍼가 가득 찬 경우 생산자(Erzeuger) 프로세스는 데이터를 추가하지 못하게 되고, 버퍼가 비어 있는 경우 소비자(Verbraucher) 프로세스는 데이터를 소비할 수 없게 된다. 이러한 상황에 대처하기 위해서 각각 "voll"과 "leer"라는 두 개의 세마포어가 도입된다.

만약, 버퍼가 가득 차면, 생산자 프로세스는 "voll" 세마포어를 호출하여 버퍼가 비워질 때까지 기다려야 한다. 반면, 버퍼가 비어 있다면, 소비자 프로세스는 "leer" 세마포어를 호출하여 버퍼에 데이터가 추가될 때까지 기다려야 한다.

이러한 방식으로, 생산자 프로세스와 소비자 프로세스는 공유 자원인 버퍼를 안전하게 접근할 수 있다. 세마포어를 이용하여 각각의 프로세스는 버퍼의 상태를 확인하고, 적절한 시점에 작업을 수행할 수 있도록 보장한다.

<div class="notice--info">
<b>그림 부가설명</b><br>
<br>
"voll" 및 "leer" 세마포어에는 각각 사용 가능한 버퍼 공간의 수를 나타내는 카운터가 있다. "voll" 세마포어는 버퍼가 가득 차서 생산자가 더 이상 추가할 수 없음을 나타내는 데 사용되는 반면, "leer" 세마포어는 버퍼가 비어 있고 소비자가 버퍼에 액세스할 수 없음을 나타낸다.<br>
<br>
생산자가 항목을 버퍼에 넣으려면 사용 가능한 버퍼 슬롯 수를 나타내는 "leer" 세마포어가 해제될 때까지 기다린다. "leer"가 해제되면 생산자는 요소를 버퍼에 삽입하고 세마포어 "voll"을 해제하여 버퍼가 가득 찼음을 나타낸다.<br>
<br>
소비자가 버퍼에서 항목을 팝하려는 경우 버퍼가 가득 차 있고 팝할 항목이 있음을 나타내는 "voll" 세마포어가 릴리스될 때까지 기다린다. "voll"이 해제되자마자 소비자는 버퍼에서 요소를 가져오고 세마포어 "leer"을 해제하여 이제 버퍼에 다시 공간이 있음을 나타낸다.<br>
<br>
"voll" 및 "leer" 세마포어의 "교차(Kreuz)" 순서는 버퍼가 가득 차지 않은 경우에만 생산자가 요소를 버퍼에 넣을 수 있고 소비자는 버퍼가 차있을 경우에만 버퍼에서 요소를 가져올 수 있음을 보장한다. 이렇게 하면 언더플로나 오버플로(unter- und überlauf) 없이 버퍼를 번갈아 사용할 수 있다.<br>
</div>

## 01-5 모니터 Monitore:

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-12_Monitore.png?raw=true" width=1000px />

공유 자원에 대한 접근을 조정하는 데 사용되는 고급 동기화 메커니즘 중 하나다.
이를 통해 프로그래머는 자동으로 동기화 문제를 해결할 수 있다.

모니터는 잠금 처리를 보다 쉽고 안전하게 만드는 동시 프로그램을 구현하기 위한 기술이다. 모니터는 한 번에 하나의 프로세스에서만 사용할 수 있는 프로시저 및 데이터 구조의 모음으로 구성된다.

모니터 이면의 아이디어는 프로그래머가 명시적으로 잠금 작업을 주입할 필요 없이 자동으로 상호 배제를 보장하는 것이다. 프로그래머는 메서드와 데이터 구조로 모니터를 정의한 다음 동기화에 대해 걱정할 필요 없이 프로그램 코드에서 액세스할 수 있다.

동기화는 모니터 개체에 의해 자동으로 수행된다. 프로세스가 모니터의 메서드를 호출하면 메서드가 완료되고 잠금이 해제될 때까지 다른 프로세스가 동일한 메서드에 액세스하지 못하도록 하는 잠금이 자동으로 획득된다. 이 자동 잠금 처리는 동기화 오류의 위험을 줄이고 동시 프로그램 구현을 단순화한다.

### Beispiel 1: 카운터

```
monitor shared_counter {
  int c = 0;

  public void increment () {
  c = c + 1;
  }

  public void decrement () {
  c = c - 1;
  }
};
```

```
class shared_counter {
  private mutex m;
  int c = 0;

  public void increment () {
    mutex_lock (m);
    c = c + 1;
    mutex_unlock(m);
  }

  public void decrement () {
    mutex_lock (m);
    c = c - 1;
    mutex_unlock(m);
  }
};
```

<div class="notice--info">
이 예제는 모니터를 사용하여 공유 카운터를 구현하는 방법을 보여준다. 모니터는 공유 자원을 동기화하기 위한 추상화이며, 모든 함수에서 자동으로 상호 배제를 적용하여 프로그래머가 별도로 잠금 기능을 추가하지 않아도 된다.<br>
<br>
공유 카운터 모니터의 경우, 카운터 값을 증가시키는 increment() 함수와 감소시키는 decrement() 함수가 있다. 이들 함수는 모두 모니터에 진입하기 위해 상호 배제 락(mutex lock)을 사용하며, 함수를 마친 후 락을 해제한다(mutex unlock).<br>
<br>
상호 배제 락을 사용하여 모니터의 공유 자원에 동시에 접근하는 것을 방지한다. 즉, 모니터에 진입한 프로세스는 다른 프로세스가 접근할 때까지 대기해야 한다. 이를 통해 공유 자원에 대한 일관성과 안전성을 보장한다.<br>
</div>

### Beispiel 2: 제한된 버퍼의 예 (Beispiel Bounded Buffer)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20syspro/imgs/03-13_BeispielBoundedBuffer.png?raw=true" width=1000px />

이 예는 모니터를 사용하여 제한된 버퍼 영역에 대한 액세스를 보장하는 방법을 보여준다.

프로세스는 여기에 데이터를 저장할 수 있다 -> deposit(data)  
프로세스는 여기에서 데이터를 가져올 수 있다 ->fetch(data)

<div class="notice--warning">
상호 배제(모니터에 의해 자동으로)를 보장하는 것 외에도 다음과 같은 다른 조건을 분명히 고려해야 한다.<br>
<br>
deposit은 버퍼에 아직 공간이 있는 경우에만 호출.<br>
fetch는 버퍼가 비어 있지 않은 경우에만 호출.<br>
</div>

```c
monitor bounded_buffer {
  Object buffer[n];
  int head = 1;
  int tail = 1; int count = 0;
  ProcessQueue WPD, WPF;

  public void deposit(Object data) {
    while (count == n) block(WPD);            //blockiert auch den Monitor
    buffer[tail] = data;
    tail = (tail + 1) % n; count++;
    if (!queue_empty(WPF)) deblock(WPF);
  }

  public Object fetch() {
    Object result;
    while (count == 0) block(WPF);            //blockiert auch den Monitor
    result = buffer[head];
    head = (head + 1) % n; count
    if ((!queue_empty(WPD))) deblock(WPD);
    return result;
  }
};
```

### 01-5-1 조건 동기화 (Bedingungssynchronisation)

조건 동기화는 프로세스 간의 교착 상태를 피하기 위해 모니터와 함께 작업할 때 사용되는 개념이다. 프로세스가 조건 변수를 기다리고 있을 때 다른 프로세스가 대기하는 동안 계속 작업할 수 있도록 모니터를 해제해야 한다.

조건부 동기화의 개념에는 **cwait(c) 및 csignal(c)**의 두 가지 개념이 있다.

**cwait(c):**
프로세스가 조건 변수 c를 기다리고 있을 때 모니터를 해제하고 자신을 차단한 다음 다른 프로세스가 발생시킨 csignal(c)이 계속되기를 기다린다. 프로세스가 해제되면 다시 모니터를 잡고 작업을 계속한다.

**csignal(c):**
csignal(c) 프로시저는 대기 중인 프로세스를 해제하는 데 사용된다. 대기중인 프로세스가 없으면 이 절차는 효과가 없다.

### 01-5-2 Java에서 사용되는 모니터

자바에서는 'synchronized'라는 키워드로 표시된 객체 메서드를 통해 모니터를 구현할 수 있다. 이를 통해 객체 메서드에 대한 상호배제(mutual exclusion)를 보장한다. 또한, **'wait()'와 'notify()'**라는 메서드를 통해 조건 동기화(Condition Synchronization)를 구현할 수 있다.

**'wait()'** 메서드를 호출하면 해당 객체가 가지고 있는 모든 잠금(lock)을 임시적으로 해제하고 대기 상태로 들어간다. 이 상태에서 다른 스레드가 해당 객체를 잠금(lock)하면, 해당 스레드는 wait() 상태에서 깨어나 모니터를 다시 얻어 작업을 수행할 수 있다.

**'notify()'** 메서드를 호출하면 해당 객체에서 대기(wait) 중인 스레드 중 임의의 하나를 깨워 작업을 수행할 수 있도록 한다. 이때, 깨어난 스레드가 다시 작업을 수행하기 위해서는 다시 잠금(lock)을 얻어야 한다.

```java
public class BoundedBuffer {
    Object buffer[n];
    int head; int tail; int count;
    public BoundedBuffer() { /* initialize */ }

    public synchronized void deposit(Object data) {
        while (count == n) wait();
        buffer[tail] = data;
        tail = (tail + 1) % n; count++;
        notifyAll();
    }

    public synchronized Object fetch() {
        Object result;
        while (count == 0) wait();
        result = buffer[head];
        head = (head + 1) % n; count--;
        notifyAll();
        return result;
    }
};
```

---

Quelle(text):  
pdf dateien, [studocu](https://www.studocu.com/de/course/technische-universitat-berlin/systemprogrammierung/1514199)  
pdf dateien, [studydrive](https://www.studydrive.net/de/course/systemprogrammierung/137292#documents)  
Klausur pdf dateien, [Klausurensammlung der Freitagsrunde](https://docs.freitagsrunde.org/Klausuren/Systemprogrammierung/)  
Vorlesung, Systemprogrammierung, [TU-Berlin](https://www.tu.berlin/dos/)  
Operating System - Process Scheduling, [tutorialspoint](https://www.tutorialspoint.com/operating_system/os_process_scheduling.htm)  
운영체제 CPU 스케줄링 전략들, [site 의지](https://gwnuysw.github.io/jekyll/update/2018/04/11/OperatingSystem.html)  
[tutorialspoint](https://www.tutorialspoint.com/operating_system/os_processes.htm)  
[CourseNotes](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/3_Processes.html)
[Process Synchronization](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/5_Synchronization.html)

Quelle(image):

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
<!-- <sup>[1)](#footnote_1)</sup>

<div class="notice--info">
<a name="footnote_1">1)</a>블라블라<br>
</div> -->
