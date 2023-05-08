---
layout: single
title: "[ELNW-v] 02 Ortskurven"
folder: "elnw"
categories:
  - elnw

tags: [blog, elnw]

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

date: 2023-05-07
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# 01 궤적곡선(Ortskurven)이란

궤적곡선(Ortskurven)은 여러 변수가 변화할 때, 하나의 변수를 고정하고 나머지 변수를 변화시키면서 얻은 결과값들의 좌표를 평면에 그리면 얻어지는 곡선을 의미한다. 전기공학에서는 이러한 방법을 이용하여 전기회로의 특성을 분석한다.

궤적곡선(Ortskurven)은 주로 **임피던스, 어드미턴스, 전류, 전압** 등을 그래프로 표현할 때 사용된다. 이러한 값들은 복소수 형태로 표현되기 때문에, 그래프 상에서는 직교좌표계를 사용한다. 궤적곡선(Ortskurven)은 이러한 좌표계 상에서 표현되며, **진폭응답(Amplitudengang)과 위상응답(Phasengang)**을 동시에 나타낼 수 있다. 임피던스의 경우, 이러한 Ortskurve를 **Impedanzkurve**라고 부르기도 한다.

## 01-1 RL-Reihenschaltung

• 예) RL직렬연결한 경우의 임피던스 (Impedanz der RL-Reihenschaltung)

$$\underline{Z} = R + j\omega L = \sqrt{R^2+(\omega L)^2} e^{arctan(\frac{\omega L}{R})}$$

## 01-2 연결방식에 따른 임피던스와 어드미턴스 활용

• 직렬연결: 임피던스의 합

• 병렬연결: 어드미턴스의 합

$$\underline{Z} = \frac{1}{\underline{Y}}$$

$$\mid\underline{Z}\mid e^{j\varphi} = \frac{1}{\mid\underline{Y}\mid e^{-j\varphi}}$$

---

Quelle(text):  
Groundlagen zur Elektrotechnik, Technische Hochschule Mittelhessen [Pdf datei](https://www.thm.de/iem/images/user/novender-978/get.pdf)  
[ElectronicsTutorials](https://www.electronics-tutorials.ws/accircuits/complex-numbers.html)

Quelle(image):  
Elektrische Netzwerke TU-Berlin [pdf datei](https://isis.tu-berlin.de/pluginfile.php/2756135/mod_resource/content/10/1_Grundlagen_Zeiger-SENSE-2023.pdf)  
StuDoc [pdf datei](https://www.studocu.com/de/course/technische-universitat-berlin/elektrische-netzwerke/124295)

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
