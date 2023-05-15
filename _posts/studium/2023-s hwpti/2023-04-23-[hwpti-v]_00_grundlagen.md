---
layout: single
title: "[HWPTI-v] 01 Hardware Programming 시작"
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

date: 2023-04-23
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# 00 간단 용어정리

**RISC(Reduced Instruction Set Computer):**

RISC(Reduced Instruction Set Computer)는 명령어 세트의 크기를 줄여 실행 속도를 향상시키는 방식으로 설계된 프로세서다.

**ARMv4:**

ARMv4는 ARM 프로세서의 이전 버전 중 하나로, 32비트 명령어 세트를 가지고 있으며, 주로 임베디드 시스템에서 사용된다.

**ARM9TDMI:**

ARM9TDMI는 ARM 계열의 임베디드 프로세서이며, 낮은 전력 소비와 높은 성능으로 유명하다.

**StrongArm:**

StrongArm은 Digital Equipment Corporation(Digital)이 개발한 ARM 프로세서 계열의 고성능 버전으로, 주로 태블릿 PC 및 PDA 등에서 사용되었다.

**프로그래머 모델(ISA, Instruction Set Architecture) ARMv4:**

ARM 프로세서가 사용하는 명령어 집합 구조를 말한다. ISA는 프로세서가 이해하고 수행할 수 있는 명령어의 집합과 그 명령어들이 수행되는 방식에 대한 규정을 포함한다.

**다섯 단계 파이프라인:**

ARMv4는 명령어 실행을 위해 파이프라인 구조를 사용한다. 이 구조는 **다섯 단계로 구성**되어 있으며, 명령어를 처리하는 과정을 단계별로 분리하여 **병렬 처리를 가능**하게 한다. 다섯 단계는 **"Instruction Fetch", "Instruction Decode", "Execute", "Memory Access", "Write Back"**이다.

**Harvard Architecture:**

하버드 아키텍처는 **데이터와 명령어를 각각 다른 메모리에 저장**하는 컴퓨터 아키텍처이다. 이 아키텍처에서는 **데이터와 명령어를 병렬로 접근**할 수 있어 성능 향상을 이룰 수 있다. **ARMv4는 Harvard 아키텍처를 기반**으로 한다.

---

# 01 VHDL

VHDL은 대부분의 설계를 Verhaltensebene (행동 수준)에서 수행하며, 일부는 Struktur-Ebene (구조 수준)에서 수행할 수도 있다.  
VHDL을 사용한 디지털 회로 설계는 **ModelSim / QuestaSIM**과 같은 **시뮬레이션 도구**를 사용하여 검증되며, **Vivado Synthesis**와 같은 **합성 도구**를 사용하여 **구현**된다.  
Vivado는 또한 프로젝트 관리를 위한 툴이다.

---

# 02 FPGA(Field Programmable Gate Array)

**FPGA**는 디지털 회로를 구현하기 위한 **IC(집적회로)**이며, 사용 전에 프로그래밍 또는 구성이 이루어져야 함. 이러한 구성은 일반적으로 **비트 스트림 형태**로 제공됨. FPGA는 **단순한 기본 블록들이 규칙적으로 배열된 형태**로 되어 있으며, 이러한 블록들은 프로그램 가능하여 원하는 동작을 수행할 수 있다. 또한 블록들 간의 연결 또한 프로그램이 가능하여 다양한 회로를 구성할 수 있다. **FPGA의 복잡도**는 일반적으로 (NAND2) 게이트 등의 동등 회로 수로 나타내며, CPU나 마이크로컨트롤러와는 달리 **직접 명령어를 수행하는 것이 아니라 프로그램된 회로를 실행**한다.

## 02-1 FPGA의 응용분야

- 빠른 프로토타입 개발 및 테스트 (Intel, Fujitsu 등)
- 소량 생산: ASIC 제작 비용보다 낮음
- 하드웨어 시뮬레이션 (소프트웨어 시뮬레이션보다 빠른 처리속도)
- 실시간 시스템 (FPGA의 시간동작 성능이 잘 알려져 있음)
- 디지털 신호 처리, 예를 들어 AVM의 WLAN 하드웨어
- 가속화기능을 사용한 100GbE 어댑터, PCIe 등
- 우주항공 분야
- SoC(System-on-a-Chip)를 구성하기 위한 다양한 구성요소를 변수로 통합하는 것

## 02-2 workflow

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/00_workflow.png?raw=true" width="700px">

VHDL로 디지털 회로 설계 시 FPGA workflow의 단계는 위의 그림과 같다.

**사양단계(Spezifikation)**
디자인 `요구 사항을 수집하고 명확하게 정의`하는 단계다. 이 단계에서는 제품의 목적, 기능, 성능, 제약 사항 등을 명확하게 정의하고 문서화한다.(일반적으로 요구 사항 문서, 명세서, 설계 문서 등이 작성됨.) 고객과의 소통과 협업이 중요하며, 디자인의 전반적인 목표를 달성하기 위한 전략과 계획을 수립해야 한다.

**합성단계(Synthese):**  
Synthesis 단계에서는 사용되는 FPGA 기술과 제한 사항에 따라 코드를 최적화하고, 불필요한 코드를 제거하여 필요한 논리 회로만을 생성한다. 이 과정에서 VHDL 코드를 입력으로 받아 물리적인 구현을 할 수 있는 **넷리스트(netlist)**로 변환한다. 이렇게 최적화를 수행하여 `회로의 크기를 최소화하고 성능을 최대화`시킨다.

**배치 및 연결 단계(platzieren und Verdrahten):**  
배치(Platzieren, Placement)과 연결(Verdrahten, Routing)단계는 FPGA 디바이스의 논리 구성요소들을 물리적인 위치에 배치하고, 이들을 전기적으로 연결하는 단계다. 이 단계에서는 디바이스 내부의 논리 구성요소들의 위치를 결정하고, 이들 간의 연결을 생성한다. 이렇게 생성된 연결은 이후 Bitstream Generation 단계에서 디바이스가 수행해야 할 동작을 정의하는 `Bitstream` 파일로 저장된다.

**기술적 경계조건 단계(Technische Randbedingungen, Technical Constraints):**
기술적 경계조건 단계에서는 디바이스에 대한 물리적인 제약사항과 성능 명세를 고려하여 설계를 최적화한다.  
이 단계에서는 다음과 같은 요소들을 고려한다:

- 디바이스의 핀 할당(Pin Assignment)
- 타이밍 제약사항(Time Constraints)
- 전원 및 지상(Power and Ground)
- PCB 레이아웃(Layout) 및 신호 노이즈(Signal Noise)
- 온도(Temperature) 및 전압(Voltage) 등 물리적 환경에 대한 제약

이러한 제약사항들을 고려하여 최적화된 설계를 생성하고, 후속 단계인 Bitstream Generation을 위한 기반을 마련한다.

**Bitstream:**

FPGA에서 설계한 디지털 회로를 실제 하드웨어로 구현하기 위해서는 해당 회로의 구성 정보를 FPGA 칩 내부의 논리블록에 프로그래밍해야 한다. 이때 사용되는 것이 바로 Bitstream이다.

Bitstream은 FPGA의 논리블록의 상태를 나타내는 0과 1로 구성된 이진 데이터 파일이다. 이 파일은 FPGA에서 실행할 수 있는 명령어로 변환되어 FPGA에 로드된다. 즉, Bitstream 파일은 FPGA 칩의 SRAM (Static Random Access Memory)에 저장되어, FPGA가 전원이 인가될 때 SRAM에서 Bitstream을 읽어와 FPGA 내부의 논리블록을 구성하게 된다.

이러한 구성 정보를 Bitstream으로 저장하는 이유는 FPGA가 구성 가능한 디바이스이기 때문이다. 사용자는 FPGA를 다양한 용도에 맞게 구성할 수 있으며, 이러한 구성 정보를 Bitstream으로 저장하여 필요에 따라 다시 프로그래밍할 수 있다.

---

# 03 Lookup table

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/00_logische%20Funktion%20dreier%20Variablen.jpg?raw=true">

(위의 그림은 세 변수를 가지는 논리함수(logische Funktion dreier Variablen)를 보여주고 있다.)

Lookup Table(LUT)은 입력 신호와 출력 신호 간의 함수적 관계를 저장하고, 이를 사용하여 디지털 신호를 처리하는 논리 회로를 구현하는 데 사용되는 기본 빌딩 블록 중 하나다.

LUT는 일반적으로 `레지스터 파일과 결합하여 사용`되며, 이러한 조합은 FPGA에서 매우 중요한 역할을 한다. 각 LUT는 작은 메모리 블록으로 구성되며, 주어진 입력값에 대해 `저장된 함수의 결과`를 출력으로 계산한다. LUT는 사용자가 프로그램 가능한 로직을 제공하며, `여러 개의 LUT를 결합`하여 더 복잡한 함수를 만들 수 있다.

<img src="https://www.mdpi.com/electronics/electronics-09-01132/article_deploy/html/images/electronics-09-01132-g002.png">

예를 들어, 4 입력 LUT는 4 비트 입력을 취하여 16개의 가능한 출력 값을 생성할 수 있다. 이러한 출력 값은 프로그래밍 가능한 로직에 따라 지정된 출력 신호에 매핑된다. FPGA는 수천 개의 LUT를 포함할 수 있으므로 매우 복잡한 디지털 신호 처리 회로를 구현할 수 있다.

LUT는 간단한 조합 논리 함수를 구현하는 데 효과적이다. 따라서 많은 수의 LUT를 사용하여 큰 멀티플렉서 또는 논리 함수를 구현하는 것이 일반적이다. 이러한 LUT를 조합하여 계층적으로 더 복잡한 함수를 구현할 수도 있다.

---

# 04 Produktlinie von Xilinx

Xilinx는 다양한 종류의 FPGA를 제공하며, 다음과 같은 제품 라인을 가지고 있다.

Spartan: 비교적 저렴하면서도 높은 입출력(I/O) 기능을 제공.  
**Artix: 저전력 소비로 동작하면서도 높은 직렬 인터페이스와 DSP 처리량을 갖추어 비용을 절감.**<sup>[1)](#footnote_1)</sup>  
Kintex: 가격 대비 성능이 우수하여 가성비가 높은 제품.  
Virtex: 높은 성능을 가진 최상위 제품 라인으로, 최신 기술을 적용하여 높은 성능을 제공.  
UltraScale 및 UltraScale+: 최신 기술과 고도화된 설계를 적용하여 가장 높은 성능을 제공하는 제품.  
Zynq: FPGA와 ARM 프로세서를 결합한 제품으로, 하드웨어/소프트웨어 공동 설계을 위한 제품.

<div class="notice--info">
<a name="footnote_1">1)</a> 가장 범용적으로 쓰기 편한 제품인듯 하다.<br>
</div>

## 04-1 xc7a35tcpg236-1 (Basys 3) 칩

xc7a35tcpg236-1 (Basys 3)는 Xilinx사의 FPGA 칩으로, 236개의 핀으로 구성되어 있으며, 이 중 일부는 GND를 위해 사용되며, 90개의 DSP Slices와 2600개의 CLBs가 있다. 7-Series에서는 각 `CLB`는 2개의 `Slices`로 구성된다. 이 FPGA 칩은 기본적으로 사용되는 기능들을 제공하며, 이를 조합하여 다양한 디지털 회로를 구성할 수 있다.

### 04-1-1 CLB(Configurable Logic Block)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/00_clb.jpg?raw=true">

CLB는 "Configurable Logic Block"의 약어로, FPGA 내에서 논리 회로를 구현하는 데 사용되는 구성 가능한 논리 블록이다. CLB는 입력 및 출력 신호, 논리 게이트, 레지스터 등을 구성하는 논리 셀 또는 논리 슬라이스로 구성된다. 논리 셀 또는 슬라이스는 기본적인 논리 게이트 및 레지스터로 구성되며, 논리 회로의 기본 단위로 사용된다.

### 04-1-2 Slices

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/00_slices.jpg?raw=true">

Slices는 Xilinx FPGA의 7 시리즈에서만 사용되는 용어로, FPGA 내에서 논리 셀을 구현하는 데 사용되는 단위이다. 각 Slice는 논리 연산, 레지스터, 다중화기 및 Look-Up Table (LUT)과 같은 다양한 논리 요소를 포함한다. 이러한 요소는 논리 회로를 구성하는 데 사용된다. 각 CLB는 2 개의 Slice로 구성된다. 따라서 Xilinx 7 시리즈 FPGA에서는 CLB 대신 Slice를 사용하여 논리 회로를 구성한다.

### 04-1-3 SliceM

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20hwpti/imgs/00_SLICEM.jpg?raw=true">

#### 위 그림에 나타나는 요소들:

4개의 룩업 테이블, `인트라커넥트 멀티플렉서`, `인터커넥트 멀티플렉서`,플립플롭 또는 래치, `캐리 체인`

**인트라커넥트 멀티플렉서(Intraconnect Multiplexer):** 인트라커넥트 멀티플렉서는 많은 입력 중 하나를 선택하여 출력으로 전달하는 논리 회로다.

**인터커넥트 멀티플렉서(Interconnect Multiplexer):** 이 멀티플렉서는 인풋과 아웃풋을 각각 가지고 있으며, 여러 입력 중에서 하나를 선택하여 출력으로 전달한다.

**캐리 체인(Carry-Chain):**
캐리 체인은 덧셈기 구현을 위해 사용된다. 여러 비트의 덧셈 연산을 수행하기 위해서는 각 비트의 캐리 비트가 이전 비트로 전달되어야 한다. 캐리 체인은 이러한 캐리 비트들을 연속적으로 전달하여 덧셈기의 연산을 가능하게 한다. 캐리 체인은 각 덧셈기 블록에서 캐리 비트를 생성하여 다음 덧셈기 블록으로 전달한다. 이를 통해 덧셈기의 구현이 가능해 진다.

#### 그 외 추가요소들:

**Block RAM:** FPGA 내부의 메모리 블록으로, 높은 처리량이 필요한 데이터를 빠르게 처리하기 위해 사용된다. 대량의 데이터 스트림 처리와 같은 응용 분야에서 유용하다.

**DSP(Digital Signal Processor) Slices:** FPGA 내부에 있는 디지털 신호 처리 유닛으로, 수치 연산 및 신호 처리 응용 분야에서 높은 처리량을 보장한다.

**Clock Management Tiles(CMT):** FPGA 내부의 클럭 관리 블록으로, 클럭 신호를 생성하고 분배하는 기능을 수행한다. 이를 통해 시스템에서 사용되는 모든 클럭 동기화를 보장하고, 시스템의 안정성 및 성능을 개선할 수 있다.

---

# 05 VHDL code vs. VHDL code in FPGA (참고)

| 구분        | VHDL code                                   | VHDL code in FPGA                        |
| ----------- | ------------------------------------------- | ---------------------------------------- |
| 설계 방식   | Top-down                                    | Bottom-up                                |
| 설계 단계   | Spezifikation, Architektur, Implementierung | Implementierung, Platzierung, 라우팅     |
| 시뮬레이션  | 시뮬레이션 도구 사용                        | FPGA 칩에서 실제 하드웨어 실행           |
| 디버깅      | 시뮬레이션 도구 사용                        | 일부 디버깅은 가능하지만 제한적          |
| 라이브러리  | 기본 라이브러리 사용                        | FPGA 제조사에서 제공하는 라이브러리 사용 |
| 리소스 할당 | 자동                                        | 수동                                     |
| 클럭        | 어디서든 접근 가능                          | 지정된 핀에서만 접근 가능                |
| 시간 제약   | 없음                                        | 설계에서 고려해야 함                     |
| 구현 비용   | 무료                                        | FPGA 칩 구매 및 라이선스 비용            |

---

# 06 Synthese-Report

Synthesis-Report란, Vivado Synthesis 도구에서 자동 생성되는 레포트로서, Synthesis 단계에서 수행된 결과를 사용자가 분석할 수 있도록 구성된 것이다. 이 레포트를 통해 FPGA 설계의 성능 및 리소스 사용에 대한 정보를 확인할 수 있다.

Synthesis-Report는 크게 두 가지 섹션으로 나뉜다. 첫 번째 섹션에서는 모든 VHDL 코드를 분석한 결과로, 모듈의 계층 구조, 리소스 사용량 및 최적화 정보 등이 제공된다. 두 번째 섹션에서는 사용자가 설계한 FPGA의 리소스와 시스템 성능에 대한 정보가 제공된다. 이 정보는 각 리소스의 사용률, 지연 시간 등을 나타내며, 설계의 최적화와 성능 개선에 도움을 줄 수 있다.

Synthesis-Report는 Vivado Synthesis 도구에서 간단한 명령어를 실행하여 생성할 수 있으며, GUI를 통해 쉽게 확인할 수 있다. 이 레포트는 FPGA 설계에 있어 매우 중요한 정보를 제공하므로, Synthesis 단계에서 적극적으로 활용되어야 할 것이다.

---

Quelle(text):  
Vorlesung, Hardware Praktikum, [TU-Berlin](https://www.tu.berlin/aes/)  
Design Guidance, [xilinx](https://www.xilinx.com/support/)  
Vivado Design Suite User Guide: Using the Vivado IDE, [xilinx](https://www.xilinx.com/support/documentation/sw_manuals/xilinx2021_1/ug893-vivado-ide.pdf)  
7 Series FPGAs Configurable Logic Block, [User Guide](https://docs.xilinx.com/v/u/en-US/ug474_7Series_CLB)

Quelle(image):  
pdf datei, Hardware Praktikum, [TU-Berlin](https://www.tu.berlin/aes/)  
Fast Logic Function Extraction of LUT from Bitstream in Xilinx FPGA, Soyeon Choi, Hoyoung Yoo, Published: 11 July 2020 [open Access, Article](https://www.mdpi.com/2079-9292/9/7/1132)  
7 Series FPGAs Configurable Logic Block, [User Guide](https://docs.xilinx.com/v/u/en-US/ug474_7Series_CLB)

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
