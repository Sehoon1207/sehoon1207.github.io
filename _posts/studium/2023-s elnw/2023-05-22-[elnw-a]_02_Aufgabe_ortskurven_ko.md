---
layout: single
title: "[ELNW-a] 02 Ortskurven 문제"
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

date: 2023-05-22
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# 00 (기본 내용 및 공식)

## 00-1 def. Ortskurve

> **def. Ortskurve:** Menge aller Zeigerendpunkte bei Variation eines Parameters (zB. ω,L,R,C) in der Komplexen Ebene.

Ortskurve는 복소 평면에서 매개 변수 (예: ω, L, R, C)의 변화에 따른 모든 벡터 끝점의 집합을 말한다.

> Anwendung: Z.B Nyquist-Stabilitätskriterium

> Impedanzkurven: kreisfrequenz ω = 2πf variabel

## 00-2 Widerstand R, Induktivität L, Kapazität C

**● Widerstand R:** $$\underline{Z}_R=R$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/02_Ortskurve/02-1_R.png?raw=true"/>

$$
\begin{flalign}
&\underline{Z}_R\mid _{ω=0}=R &&\\
&\underline{Z}_R\mid _{ω=∞}=R &&
\end{flalign}
$$

**● Induktivität L:** $$\underline{Z}_L=jωL$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/02_Ortskurve/02-2_L.png?raw=true"/>

<!-- $$
\begin{flalign}
&\underline{Z}_L\mid _{ω=0}=0 ➨ das bedeutet.. wirkt wie kurzschluss&&\\
&\underline{Z}_L\mid _{ω=∞}=R &&
\end{flalign}
$$ -->

$$\underline{Z}_L\mid _{ω=0}=0 $$➨ das bedeutet.. wirkt wie kurzschluss  
➨$$\underline{U}_L=jωL\cdot \underline{I}_{L} =0$$ ➨ jωL=0

$$\underline{Z}_{L}\mid _{ω=∞}=j\cdot ∞$$➨ das bedeutet.. wirkt wie offene Klemme  
➨$$\frac{\underline{U}_{L}}{jωL}\mid _{ω=0}=\underline{I}_{L} =0$$

**● Kapazität C:**$$\underline{Z}_C=-j\frac{1}{ωC}$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/02_Ortskurve/02-3_C.png?raw=true"/>

$$\underline{Z}_C\mid _{ω=0}=-j∞ $$➨ das bedeutet.. wirkt wie offene Klemme

$$\underline{Z}_{L}\mid _{ω=∞}=0$$➨ das bedeutet.. wirkt wie kurzschluss

## 00-3 직렬연결 Reihenschaltung, 병렬연결 Parallelschaltung

직렬연결 (Reihenschaltung): $$\underline{Z}_{ges} = \sum_{k=1}^{n}\underline{Z}_k$$

병렬연결 (Parallelschaltun)g: $$\frac{1}{\underline{Z}_{ges}} = \sum_{k=1}^{n}\frac{1}{\underline{Z}_k}$$

⇒ $$\underline{Z}_{ges}=\frac{1}{\sum_{k=1}^{n}\frac{1}{\underline{Z}_k}}$$  
⇒ $$\underline{Y}_{ges}=\sum_{k=1}^{n}\underline{Y}_k$$

---

# 1. Aufgabe: 임피던스의 궤적곡선 Ortskurve der Impedanz (Impedanzkurve)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/02_Ortskurve/02_1_Teilnetzwerk.jpg?raw=true" >

$$
\begin{align}
& C_1 = 100 nF, C_2 = 10nF, R_2 = 1kΩ\\
\end{align}
$$

## 1.1. 질적 궤적곡선 Qualitative Ortskurve

> Geben Sie rein qualitativ den Verlauf der Ortskurve der Impedanz $$\underline{Z}(f)$$ an. Leiten Sie diese aus den
> Ortskurven der Teilimpedanzen $$\underline{Z}_1(f)$$ und $$\underline{Z}_2(f)$$ her. Siehe dazu auch Abbildung 1.

그림 1을 보고, 임피던스 Z(f)의 Ortskurve의 질적인 변화를 설명해라. 이를 Teilimpedanzen인 Z1(f)와 Z2(f)의 궤적곡선(Ortskurv)로 표현해라.

**Lsg:**

$$
\begin{flalign}
& \omega = 2\pi f &&\\
\\
& \underline{Z}_{ges}(ω) = \underline{Z}_1(ω) + \underline{Z}_2(ω) &&\\
\\
& ① \underline{Z}_1(ω) = -j\frac{1}{ωC_1}\\
\end{flalign}
$$

$$
\begin{flalign}
& ② \underline{Z}_2(ω) =\frac{1}{\frac{1}{\underline{Z}_{R_2}}+\frac{1}{\underline{Z}_{C_2}}} &&\\
&\;\;\;\;\;\;\;\;\;\;\;\;\;=\frac{1}{\frac{1}{\underline{Z}_{R_2}}+\frac{1}{\frac{1}{jωC_2}}} &&\\
&\;\;\;\;\;\;\;\;\;\;\;\;\;=\frac{1}{\frac{1}{R_2}+jωC_2} \cdot \frac{R_2}{R_2} &&\\
&\;\;\;\;\;\;\;\;\;\;\;\;\;=\frac{R_2}{1+jωC_2R_2} \cdot \frac{1-jωC_2R_2}{1-jωC_2R_2} &&\\
&\;\;\;\;\;\;\;\;\;\;\;\;\;=\frac{R_2}{1+ω^2(C_2R_2)^2} - j\frac{ωC_2R_2}{1+ω^2(C_2R_2)^2} &&\\
&\;\;\;\;\;\;\;\;\;\;\;\;\;=\frac{R_2}{\sqrt{1+ω^2(C_2R_2)^2}}\cdot e^{-j\arctan(ωC_2)} &&\\
\\
\end{flalign}
$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/02_Ortskurve/02-4_ortskurv_1.png?raw=true" >

## 1.2. 정량적인 궤적곡선 Ortskurve der Admittanz

> Um die exakte Impedanzkurve für die Schaltung aus Abbildung 1 zeichnen (oder plotten) zu können,
> wird die Berechnung von Punkten auf der Kurve benötigt. Stellen Sie dafür zuerst allgemein die Formel
> für $$\underline{Z}(f)$$ auf und trennen Sie diese nach Real- und Imaginärteil. Berechnen Sie anschließend für die
> quantitative Ortskurve die Zahlenwerte für $$\underline{Z}(f)$$ an den Stellen f = 1kHz, 10kHz und 50kHz.

그림 1의 회로에 대한 정확한 임피던스커브를 그리거나 또는 그리기 위해, 곡선 위의 점들을 계산해야 한다. 이를 위해 $$\underline{Z}(f)$$ 의 일반적인 공식을 작성하고, 실수부와 허수부로 분리해라. 그런 다음, 정량적인 궤적곡선(Ortskurv)에서 f = 1kHz, 10kHz 및 50kHz에서의 Z(f)의 숫자 값을 계산하라.

**Lsg:**

$$
\begin{flalign}
& \underline{Y}_{ges}(f=0.1kHz) = 0.2307 \frac{1}{Ω} -j\;0.0243\frac{1}{Ω} && \\
& \underline{Y}_{ges}(f=1kHz) = 0.25\frac{1}{Ω}-j\;0.0024\frac{1}{Ω} && \\
& \underline{Y}_{ges}(f=20kHz) = 0.236\frac{1}{Ω}-j\;0.0225\frac{1}{Ω} && \\
\end{flalign}
$$

# 2. Aufgabe: 어드미턴스의 궤적곡선 Ortskurve der Impedanz (Impedanzkurve)

## 1.1. 질적 궤적곡선 Qualitative Ortskurve

> Geben Sie rein qualitativ den Verlauf der Ortskurve der Admittanz $$\underline{Y}(f)$$ an. Leiten Sie diese aus den
> Ortskurven der Teiladmittanzen $$\underline{Y}_3(f)$$ und $$\underline{Y}_4(f)$$ her. Siehe dazu auch Abbildung 3.

**Lsg:**

$$
\begin{flalign}
& \underline{Y}_{ges} = \underline{Y}_3 + \underline{Y}_4 &&\\
\\
& \underline{Y}_4 = \frac{1}{R_4} &&\\
\\
& \underline{Y}_3(ω) = \frac{1}{\underline{Z}_3(ω)} = \frac{1}{R_3+jωL_3+\frac{1}{jωC_3}} &&\\
&\;\;\;\;\;\;\;\;\;\;\;\;\;= \frac{1}{R_3+j(ωL_3-\frac{1}{ωC_3})} \; , \; \cdots \; ωL_3-\frac{1}{ωC_3} = 0  &&\\
\\
& \underline{Y}_3(ω=0) = 0 &&\\
& \underline{Y}_3(ω=∞) = 0
\end{flalign}
$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/02_Ortskurve/02-5_ortskurv_2.png?raw=true" >

## 1.2. 정량적인 궤적곡선 Ortskurve der Admittanz

> Stellen Sie allgemein die Formel für $$\underline{Y}(f)$$. Trennen Sie dabei den Real- und den Imaginärteil. Berechnen Sie die Punkte auf der Admittanzkurve $$\underline{Y}(f)$$ an den Stellen f = 0,1Hz, 1Hz und 20Hz.

**Lsg:**

$$
\begin{flalign}
& \underline{Y}_{ges}(f=0.1kHz) = 0.2307 \frac{1}{Ω} -j\;0.0243\frac{1}{Ω} && \\
& \underline{Y}_{ges}(f=1kHz) = 0.25\frac{1}{Ω}-j\;0.0024\frac{1}{Ω} && \\
& \underline{Y}_{ges}(f=20kHz) = 0.236\frac{1}{Ω}-j\;0.0225\frac{1}{Ω} && \\
\end{flalign}
$$

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

$$
$$
