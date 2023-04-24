---
layout: single
title: "[HWPTI] 01 Hardware Programming 시작"
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
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”

# 간단 용어정리

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

# VHDL

VHDL은 대부분의 설계를 Verhaltensebene (행동 수준)에서 수행하며, 일부는 Struktur-Ebene (구조 수준)에서 수행할 수도 있다.  
VHDL을 사용한 디지털 회로 설계는 **ModelSim / QuestaSIM**과 같은 **시뮬레이션 도구**를 사용하여 검증되며, **Vivado Synthesis**와 같은 **합성 도구**를 사용하여 **구현**된다.   
Vivado는 또한 프로젝트 관리를 위한 툴이다.

---

# FPGA-Einführung

**FPGA**는 디지털 회로를 구현하기 위한 **IC(집적회로)**이며, 사용 전에 프로그래밍 또는 구성이 이루어져야 함. 이러한 구성은 일반적으로 **비트 스트림 형태**로 제공됨. FPGA는 **단순한 기본 블록들이 규칙적으로 배열된 형태**로 되어 있으며, 이러한 블록들은 프로그램 가능하여 원하는 동작을 수행할 수 있다. 또한 블록들 간의 연결 또한 프로그램이 가능하여 다양한 회로를 구성할 수 있다. **FPGA의 복잡도**는 일반적으로 (NAND2) 게이트 등의 동등 회로 수로 나타내며, CPU나 마이크로컨트롤러와는 달리 **직접 명령어를 수행하는 것이 아니라 프로그램된 회로를 실행**합니다.

---

Quelle(text):   
Quelle(image): Hardware Praktikum TU-Berlin pdf datei


<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
