---
layout: single
title: "[HWPTI-p] 02 Registersatz: Implementierung von Speichern VHDL/FPGA"
folder: "hwpti"
categories:
  - hwpti

tags: [blog, hwpti]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "list"
toc_icon: "bars"
toc_sticky: true
classes: wide

lang: de
lang-ref: multilingual

use_math: true

date: 2023-05-15
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# 00 Einführung

## 00-1 Registersatz?

Registersatz는 프로세서 또는 CPU 내에서 명령어 실행 중 데이터와 중간 결과를 저장하는 데 사용되는 하드웨어 구성 요소다. Registersatz는 일반적으로 일정한 비트 수를 저장할 수 있는 레지스터의 컬렉션으로 구성된다.

VHDL/FPGA에서 Speicher(메모리)의 구현은 FPGA(융합형 게이트 어레이) 또는 유사한 하드웨어에서 Registersatz를 구현하기 위해 로직 회로를 개발하고 설명하는 것을 의미한다. VHDL(매우 높은 속도의 통합 회로 하드웨어 기술 언어) 또는 다른 하드웨어 설명 언어를 사용하여 회로를 설계하고 기술한다.

Speicher의 구현은 레지스터 유형, 크기 및 기능의 정의를 포함한다. 이는 프로세서 또는 CPU의 요구에 따라 다를 수 있다. FPGA의 메모리 구성 요소는 레지스터셋을 형성하기 위해 해당 구성으로 설정되고 서로 연결된다.

VHDL/FPGA에서 Speicher의 구현은 레지스터에 저장된 데이터의 제어와 관리도 포함한다. 이는 데이터 플로우, 읽기 및 쓰기 작업, 클럭 신호와의 동기화 등을 말한다.

VHDL/FPGA에서 Speicher의 구현은 프로세서 또는 CPU의 성능과 효율성에 결정적인 역할을 한다. 잘 설계된 Registersatz는 실행 속도와 처리량을 향상시키고 사용 가능한 하드웨어 리소스를 최적으로 활용할 수 있도록 도와준다.

# 01 Betriebsmodi im ISA ARMv4

아래는 하드웨어 디버거로 ARM9TDMI의 core 레지스터를 보여 주고 있다. 모두 32bit를 가지고 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/02_2_Betriebsmodi.jpg?raw=true" />

[이미지출처](http://recipes.egloos.com/5618965)

> USR, FIQ, SVC, IRQ, UND, ABT 모드가 있으며, SVC, IRQ, UND, ABT는 3개(FIQ는 8개)의 레지스터가 있다. USR는 총 R0~R14까지 해서 15개가 있다. 그리고 마지막으로 PC, CPSR 있다. ② 에는 현재 6개의 모드 중에 어떤 모드가 사용 중인지 보여주고, ①은 해당 모드에서 사용중인 레지스터 값을 보여 주는 거다. R13, R14는 6개 모두 존재하고 있다. 그 중에서 ②가 어떤 모드인지를 가리키게 되면, 각 모드에서 R13, R14가 사용된다. 따라서 현재 ②에 SVC 모드라고 보여 주기 때문에 SVC 모드에 있는 R13_svc, R14_svc 레지스터가 사용되었고, 레지스터의 값이 ①과 같게 보인다.

레지스터를 정리하면 다음과 같다:

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/02_3_Banked-registers-of-ARM-CPU.png?raw=true" />

[이미지출처](https://www.researchgate.net/figure/Banked-registers-of-ARM-CPU_fig6_29602641)

## 01-1 Privilegierte/nicht privilegierte Modi

Privilegierte/nicht privilegierte 모드는 ARM 아키텍처에서 지원되는 실행 모드 중 하나다.
이러한 모드는 ARM 프로세서의 안정성, 보안 및 성능을 조정하는 데 중요한 역할을 한다.

**Privilegierte 모드**는 시스템 관리와 제어 작업을 처리하는 데 사용되며, 커널 모드 또는 시스템 모드라고도 불린다.
Privilegierte 모드에서는 특권 명령어와 특정한 시스템 리소스에 액세스할 수 있으며, 커널 또는 운영체제 코드를 실행하는 데 사용된다. 이 모드는 **시스템의 안전성과 보안을 유지하기 위해 필요한 특권 작업**을 수행한다.

**Nicht privilegierte 모드**는 **사용자 모드 또는 사용자 애플리케이션 모드**로 불린다.
반면에, nicht privilegierte 모드는 사용자 애플리케이션 및 일반 소프트웨어 코드를 실행하는 데 사용된다. 이 모드에서는 특정한 권한 수준을 가지고 있어 특권 명령어와 특정한 시스템 리소스에 액세스할 수 없다. Nicht privilegierte 모드에서 실행되는 코드는 시스템 리소스에 대한 **제한된 액세스만을 허용**받는다.

# 02 ARM 아키텍처의 레지스터

ARM 아키텍처는 **총 37개의 레지스터**를 갖고 있다. 이 중 **31개는 범용 레지스터이고, 6개는 상태 레지스터**다. 몇 개의 레지스터 주소는 여러 개의 물리적 레지스터와 연결되어 있으며, 이를 **레지스터 뱅크**라고 한다. 현재의 작동 모드에 따라 어떤 레지스터가 해당 레지스터 주소를 통해 액세스되는지를 결정한다.

시스템에서는 **15개의 범용 레지스터(R0-R14같은), 하나 또는 두 개의 상태 레지스터, 그리고 프로그램 카운터(PC)**로 되어 있다. 범용 레지스터는 데이터 저장 및 연산에 사용되며, 상태 레지스터에는 프로세서의 상태와 조건 플래그가 저장된다. 프로그램 카운터는 다음 실행할 명령어의 주소를 가리킨다.

각 작동 모드에서는 특정 레지스터 세트를 사용할 수 있으며, 작동 모드에 따라 해당 모드에서 사용할 수 있는 레지스터가 결정된다. 이를 통해 각 작동 모드에서 필요한 레지스터를 효과적으로 관리하고 사용할 수 있다.

## 02-1 General-purpose Register(일반 범용 레지스터)

일반 범용 레지스터는 3개의 그룹으로 나눌 수 있다.

### 02-1-1 "Unbanked registers" (R0-R7)

각각의 레지스터는 모든 작동 모드에서 동일한 물리적 레지스터를 가리킨다.
특별한 기능이 없으며 일반적인 데이터 저장과 연산에 사용된다.

### 02-1-2 "Banked registers" (R8-R14)

각각의 레지스터는 작동 모드에 따라 다른 물리적 레지스터를 가리킨다.
R8-R12는 각 작동 모드(단, FIQ 모드는 예외)를 위해 하나의 물리적 레지스터를 가지고 있다. FIQ 모드를 위한 레지스터는 빠른 인터럽트 처리를 위해 사용된다.
R13-R14는 각각 6개의 물리적 레지스터를 가지고 있다. 하나는 사용자 모드 및 시스템 모드를 위한 것이고, 나머지 5개는 각 예외 모드(`R13*<mode>`, `R14*<mode>`)를 위한 것이다.

### 02-1-3 R15 - PC (프로그램 카운터)

프로그램 카운터는 명령어 주소를 저장하거나 읽기 위해 사용된다.
현재 실행 중인 명령어의 주소를 가리킨다.
PC 레지스터는 읽기와 쓰기 모두에 사용된다.

### 02-1-4 스택 포인터 R13(Stack Pointer) 와 링크 레지스터 R14(Link Register)

**R13 레지스터는 스택 포인터(Stack Pointer)**로 사용되며, 각 예외 모드마다 고유한 버전이 있다. 각 예외 모드는 해당 모드에 속하는 스택으로 초기화된다. 예외 처리기는 이 스택에 다른 레지스터의 값을 저장하여 사용할 수 있다. 예외 처리가 완료되면 이러한 값들을 다시 레지스터에 로드한다. 이를 통해 예외 처리기는 레지스터의 상태에 영향을 주지 않고 처리를 수행할 수 있다.

**R14는 링크 레지스터(Link Register)**로, **두 가지 특수한 기능**이 있다:

1. 모든 모드에서 R14에는 서브루틴(Subroutine)의 복귀 주소가 저장된다. 서브루틴 실행이 완료되면 R14의 값이 PC(Program Counter)로 복사된다.
2. 예외 발생 시, 해당 예외가 발생한 복귀 주소로 R14가 쓰여진다.

그 외의 경우, R14는 범용 레지스터로 사용될 수 있다.

이를 통해 **예외 모드**에서는 스택 포인터를 통해 상태를 보존하고, 링크 레지스터를 통해 서브루틴의 복귀 주소를 관리할 수 있다. 이는 예외 처리 과정에서 레지스터의 상태를 안전하게 유지하고, 예외 발생 지점으로 다시 돌아갈 수 있도록 도와준다.

## 02-2 Program Status Register (PSR)(프로그램 상태 레지스터)

ARM 아키텍처에서 Program Status Register (PSR)은 프로세서의 **현재 실행 상태**와 **제어 플래그**를 **저장**하는 레지스터다. PSR은 **CPSR(Current Program Status Register)**와 **SPSR(Saved Program Status Register)**로 구성된다.

<div class="notice--info">
현재 프로그램 상태 레지스터(CPSR)는 ARM 프로세서에서 사용되는 레지스터로, 비트 4:0에 인코딩되어 현재 프로세서의 동작 모드를 나타낸다. 이 레지스터는 프로세서의 실행 상태와 관련된 여러 가지 정보를 포함하고 있다.<br>
<br>
CPSR은 프로세서의 현재 동작 모드를 나타내며, 이는 프로세서가 실행 중인 코드의 권한 수준과 특성을 결정한다. 동작 모드는 사용자 모드, 시스템 모드, IRQ 모드, FIQ 모드, 중단 모드** 등 다양한 모드가 있다. 이 모드는 소프트웨어 또는 인터럽트 및 예외 처리에 의해 제어된다.<br>
<br>
프로세서의 동작 모드를 변경하려면 새로운 모드를 CPSR에 기록하는 방식으로 수행된다. 이를 소프트웨어가 제어할 수도 있고, 인터럽트 또는 예외 상황이 발생할 때 자동으로 모드가 변경될 수도 있다. CPSR의 해당 비트를 변경함으로써 프로세서의 동작 모드를 변경하면, 프로세서는 해당 모드에 따라 다른 동작을 수행하게 된다.<br>
<br>
CPSR은 프로세서의 현재 상태를 나타내는 중요한 레지스터로, 프로세서의 제어 및 동작을 제어하는 데 사용됩니다. 동작 모드는 프로세서의 권한 수준, 인터럽트 처리, 예외 처리 등을 결정하는 데 중요한 역할을 한다.<br>
</div>

### 02-2-1 CPSR (Current Program Status Register):

> CPSR은 현재 **실행 중인 프로세서의 상태와 제어 플래그를 저장**한다.  
> CPSR은 **사용자 모드, 시스템 모드, IRQ 모드, FIQ 모드, 중단 모드 등 다양한 모드**에서 동작한다.  
> CPSR의 **비트 필드**에는 **실행 상태, 조건 코드, 인터럽트 비트, 프로세서 모드 등의 정보**가 포함된다.  
> CPSR의 **일부 비트**는 **프로세서 상태**를 나타내며, 예를 들어, 상태 비트는 프로세서의 현재 모드를 나타낸다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/02_1_Betriebsmodi_6mod.png?raw=true" />

[이미지출처](http://recipes.egloos.com/5618965)

CPSR은 또한 **condition flag, reserved, extension, control 구간**으로 나뉜다. 32bit로 구성된 레지스터는 각각의 역할들이 있다.

#### 02-2-1-1 \[bit 31-28] condition flag(조건 플래그):

|N|연산 결과가 마이너스이면 '1'로 셋팅|
|Z|연산 결과가 '0' 이면 '1'로 셋팅|
|C|연산 결과가 32bit를 넘으면 '1'로 셋팅|
|V|연산 결과가 32bit를 넘어 sign bit가 상실되면 '1'로 셋팅|

<div class="notice--info">
<b>N (Negative Flag):</b> 연산 결과가 마이너스인 경우에 '1'로 설정된다. 즉, 연산 결과가 음수인지를 나타내는 플래그다. 이 플래그는 연산 결과의 최상위 비트(비트 31)를 나타낸다.<br>
N[31] 비트는 ALU 연산 결과에서 마이너스(-) 값이 나왔을 때 ALU bus로부터 PSR로 전달되어 N flag를 '1' 바뀐다.<br>
<br>
<b>Z (Zero Flag):</b> 연산 결과가 '0'인 경우에 '1'로 설정된다. 즉, 연산 결과가 0인지를 나타내는 플래그다.<br>
<br>
<b>C (Carry Flag):</b> 연산 결과가 32비트를 넘어가는 경우에 '1'로 설정된다. 이 플래그는 덧셈이나 뺄셈 연산에서 발생하는 overflow을 나타내는 플래그다. 예를 들어, 32비트 연산에서의 캐리 비트(Carry Bit)가 설정되면 C 플래그도 '1'로 설정된다.<b>(자릿수 넘치는 경우)</b><br>
<br>
<b>V (Overflow Flag):</b> 연산 결과가 32비트를 넘어서 sign bit가 변경되는 경우에 '1'로 설정됩니다. 이 플래그는 덧셈이나 뺄셈 연산에서 발생하는 오버플로우(overflow)를 나타내는 플래그다. 예를 들어, 두 양수를 더하다가 결과가 음수가 되면 V 플래그가 설정됩니다.<b>(연산 결과가 원래의 데이터 타입 범위를 넘어서는 경우)</b><br>
</div>

#### 02-2-1-2 \[bit 27-24] Reserved (예약 영역):

CPSR의 중간 4비트 (bit 27에서 bit 24)는 예약된 영역으로, 현재는 사용되지 않는다. 이 영역은 나중에 확장 가능성을 위해 남겨둔 것이다. 특정한 경우 이 영역이 사용되는 경우가 있다.

#### 02-2-1-3 \[bit 23-8] Extension (확장 영역):

CPSR의 다음 8비트 (bit 23에서 bit 8)는 확장 영역이다. 확장 영역은 ARM 아키텍처 확장 기능을 위해 사용될 수 있다.

#### 02-2-1-4 \[bit 7-0] Control (제어 비트):

CPSR의 하위 8비트 (bit 7에서 bit 0)는 제어 비트로, 현재 CPU의 동작 모드를 나타낸다. 각 비트는 특정한 모드를 나타내며, 예를 들어 bit 4가 '1'이면 IRQ 모드를 나타낸다.

#### 02-2-1-5 그 외 특정상황에 추가적으로 사용되는 것들:

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/02_4_Register.jpg?raw=true" />

이미지 출처: [virus](https://www.virusbulletin.com/virusbulletin/2013/01/shellcoding-arm)

\[27] Q-Flag Overflow : Thumb 상태에서 곱셈 연산의 오버플로우를 나타낸다.  
\[24]는 J 비트로, ARM 아키텍처에서 사용된다.  
\*\*J = 0 및 T = 0은 ARM 인스트럭션 세트(Instruktionssets)를 나타낸다.  
\[19:16] ARMv6에서는 Greater than or Equal flags 또는 Halfword flags로 사용된다.  
\[9] 는 E-Bit로, ARMv4에서는 예약된 비트다. ARMv6에서는 Endian(엔디안)을 지정하는 비트로 사용된다.

**I/F 비트 (Interrupt Disable):**  
IRQ 또는 FIQ를 막는 역할을 하는 비트다.(각각 'I', 'F' 비트) 다른 인터럽트를 처리중이거나 더 급한 일이 있을 경우, 또는 인터럽트와 F인터럽트가 동시에 들어오면 인터럽트 컨트롤러에서 관리하게 된다. 예를 들어 IRQ, FIQ가 '1'로 되어 있으면, 인터럽트가 발생해도 허용을 안 한다.

**T 비트 (Thumb):**  
T 비트가 '1'로 설정되면, Thumb 모드로 프로세서가 동작한다. Thumb 모드는 16비트의 Thumb 명령어 세트를 사용하는 모드로, 코드 크기를 줄이고 실행 효율성을 향상시킨다.
T 비트가 '0'으로 설정되면, ARM 모드로 프로세서가 동작한다. ARM 모드는 32비트의 ARM 명령어 세트를 사용하는 모드로, 더 복잡한 연산을 수행할 수 있다.
(BX 명령에 의해서만 제어되며, 프로세서는 내부적으로 적절한 상황에 따라 Thumb 모드 또는 ARM 모드를 자동으로 선택한다. 따라서 사용자가 이 비트에 강제로 값을 write 할 수 없다.)

**Mode bits:(아래에 각각 모드에 따른 자세한 설명이 있음)**

| M[4:0] | Mode   | Accessible Registers                              |
| ------ | ------ | ------------------------------------------------- |
| 10000  | User   | PC, R14 to R0, CPSR                               |
| 10001  | FIQ    | PC, R14_fiq to R8_fiq, R7 to R0, CPSR, SPSR_fiq   |
| 10010  | IRQ    | PC, R14_irq to R13_irq, R12 to R0, CPSR, SPSR_irq |
| 10011  | SVC    | PC, R14_svc to R13_svc, R12 to R0, CPSR, SPSR_svc |
| 10111  | Abort  | PC, R14_abt to R13_abt, R12 to R0, CPSR, SPSR_abt |
| 11011  | Undef  | PC, R14_und to R13_und, R12 to R0, CPSR, SPSR_und |
| 11111  | System | PC, R14 to R0, CPSR (Architecture 4 only)         |

### 02-2-2 SPSR (Saved Program Status Register):

> SPSR은 **예외 처리나 서브루틴 호출 등**의 상황에서 **CPSR 값을 저장하는 레지스터**다.  
> SPSR은 **예외가 발생**했을 때 **CPSR의 값을 보존하고 나중에 복원**하는 데 사용된다.
> 예를 들어, IRQ 예외가 발생했을 때 CPSR의 값을 SPSR에 저장하고, IRQ 예외 처리가 완료된 후에 SPSR의 값을 다시 CPSR에 복원한다.
> 이렇게 함으로써 예외 처리가 끝난 후에 이전 상태로 돌아갈 수 있다.

<div class="notice--info">
SPSR (Saved Program Status Register)은 ARM 아키텍처에서 사용되는 특정 모드에서 실행 중인 프로세스의 이전 상태를 저장하는 레지스터다. 각 모드마다 해당 모드의 SPSR이 존재하며, 모드 전환 시 현재의 PSR(Program Status Register) 값을 해당 모드의 SPSR에 저장한다. 그러면서 모드 전환 이전의 상태를 보존할 수 있게 된다.<br>
<br>
SPSR은 예외(Interrupts, Data Aborts, Undefined Instructions 등) 발생 시에 현재의 상태를 보관하고 복구하는 데 사용된다. 예외가 발생하면 현재의 PSR 값은 SPSR에 저장되고, 예외 처리가 완료된 후에는 SPSR 값에서 다시 복원된다. 이를 통해 예외 처리가 끝난 후에 원래의 실행 상태로 복귀할 수 있다.<br>
<br>
SPSR은 CPSR(Current Program Status Register)와 유사한 구조를 가지고 있으며, 상태 레지스터의 다양한 필드(예: 프로그램 상태 플래그, 모드 비트, 인터럽트 비트 등)를 포함한다. SPSR은 각 모드마다 별도로 존재하며, 해당 모드에서 발생하는 예외 처리에 필요한 상태 정보를 저장한다.<br>
<br>
SPSR은 예외 처리 및 모드 전환이 필요한 상황에서 중요한 역할을 수행하며, ARM 프로세서의 상태 관리에 핵심적인 요소다.<br>
</div>

## 02-3 7-Modi(Mode bits)

각 모드에 대해서 짧게 요약해 보았다.

### 02-3-1 CPU Modus: User (사용자 모드):

일반적인 응용 프로그램이 실행되는 모드로, 가장 일반적인 모드다. 제한된 권한(일부 보호된 메모리 영역에 액세스할 수 없음.)을 갖고 있으며, 애플리케이션의 실행과 일반적인 작업을 수행한다. 사용자 모드의 프로그램은 작동 모드를 독립적으로 변경할 수 없으며 이는 인터럽트를 통해서만 발생한다.

`이러한 제한 사항을 통해 운영 체제는 시스템 리소스를 관리할 수 있다.`

### 02-3-2 CPU Modus: System (시스템 모드):

운영 체제 프로세스에서 사용 사용자 모드와 동일한 레지스터에 액세스할 수 있지만 특권 모드이므로 사용자 모드보다 제한이 적음 독립형 모드 전환, CPSR에 쓸 수 있음

### 02-3-3 CPU Modus: Supervisor (슈퍼바이저 모드):

시스템과 사용자 모드 사이에서 작동하는 모드로, 운영체제의 커널이 작업을 수행하는 모드다. 관리자 모드는 시스템 호출에 의해 사용되며, 시스템 리소스에 대한 접근과 관련된 특권 명령어를 실행할 수 있다. 사용자 모드의 프로그램이 메모리 할당과 같은 특권 명령을 수행하려는 경우 프로세서는 관리자 모드로 전환하고 필요한 경우 명령을 수행할 수 있다.

### 02-3-4 CPU Modus: IRQ (IRQ 모드):

인터럽트 요청(IRQ)을 처리하기 위한 모드다. 하드웨어 인터럽트가 발생하면 CPU는 IRQ 모드로 전환되어 해당 인터럽트를 처리한다.  
예: Hardware Interrupt, 드라이브가 데이터 읽기를 완료하고 데이터를 메모리에 쓸 수 있음을 프로세서에 알린다.

### 02-3-5 CPU Modus: FIQ (FIQ 모드):

빠른 인터럽트 요청(FIQ)를 처리하기 위한 모드다. IRQ 모드보다 더 높은 우선순위의 하드웨어 인터럽트를 처리할 수 있다.(중단과 치료 사이의 최소 대기 시간)

### 02-3-6 CPU Modus: Abort (어보트 모드):

데이터 페치나 명령어 페치 중에 오류가 발생한 경우 해당 오류를 처리하기 위한 모드다.  
예를 들어, 메모리 접근 오류나 페이지 테이블 오류 등이 발생하면 CPU는 어보트 모드로 전환되어 오류 처리를 수행한다. (유효하지 않은 메모리 영역에 대한 액세스)

### 02-3-7 CPU Modus: Undefined (정의되지 않은 모드):

ARM 아키텍처에서 정의되지 않은 명령어를 실행하거나 예약되지 않은 동작을 수행할 때 CPU는 정의되지 않은 모드로 전환된다. 일반적으로 예외 상황을 처리하기 위한 용도로 사용된다. 즉, 프로세서는 이 명령을 알지 못한다.

# 03 Speicher

## 03-1 Modellierung von Speicher in VHDL

개별 레지스터는 std_logic_vector 또는 std_logic을 사용하여 구현할 수 있으며, 메모리는 RAM에서 직접 구현하거나 UltraRAM 프리미티브에서 std_logic_vector의 배열로 구현하고 Vivado에서 추론할 수 있습니다.

## 03-2 Arten von Speicher in Xilinx FPGA

### 03-2-1 Distributed Memory

### 03-2-2 Dedicated Memory

## Typen von Speicherelementen im Xilinx Artix-7 FPGA der Xilinx Artix-7 Series

## Arten von Speicherimplementierung

---

Quelle(text):  
Vorlesung, Hardware Praktikum, [TU-Berlin](https://www.tu.berlin/aes/)  
Design Guidance, [xilinx](https://www.xilinx.com/support/)  
Vivado Design Suite User Guide: Using the Vivado IDE, [xilinx](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2021_1/ug893-vivado-ide.pdf)  
7 Series FPGAs Configurable Logic Block, [User Guide](https://docs.xilinx.com/v/u/en-US/ug474_7Series_CLB)  
[ARM Architecture Reference Manual, 2005](https://documentation-service.arm.com/static/5f8dacc8f86e16515cdb865a?token)  
[HWPR ARM Befehlsarchitektur, 1.0, 2010](https://isis.tu-berlin.de/pluginfile.php/2257017/mod_resource/content/3/HWPR_ARM_Befehlssatzarchitektur_edit2.pdf)  
[HWPTI ISIS Kurs, letzter Abruf: 09.05.2022](https://isis.tu-berlin.de/course/view.php?id=29737)  
[7 Series FPGAs Data Sheet: Overview:](https://docs.xilinx.com/v/u/en-US/ds180_7Series_Overview)

Quelle(image):  
pdf datei, Hardware Praktikum, [TU-Berlin](https://www.tu.berlin/aes/)  
Fast Logic Function Extraction of LUT from Bitstream in Xilinx FPGA, Soyeon Choi, Hoyoung Yoo, Published: 11 July 2020 [open Access, Article](https://www.mdpi.com/2079-9292/9/7/1132)  
7 Series FPGAs Configurable Logic Block, [User Guide](https://docs.xilinx.com/v/u/en-US/ug474_7Series_CLB)
[친절한 임베디드 시스템 개발자 되기 강좌](http://recipes.egloos.com/5618965)

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
