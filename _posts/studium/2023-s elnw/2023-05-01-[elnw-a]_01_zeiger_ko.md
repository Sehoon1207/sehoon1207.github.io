---
layout: single
title: "[ELNW-p] 01 Zeiger 문제"
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

date: 2023-05-01
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# (기본 공식)

**Imäginare Einheit** [ $$j$$ ]:

$$j^2=-1 \Leftrightarrow j=\sqrt{-1}$$

**Eulersche Formel**:

$$e^{j \varphi} = \cos{\varphi}+j\cdot\sin{\varphi}$$

**Komplexe Zahl**:

$$\underline{x} = R(\underline{x})+j\cdot Im(\underline{x})=\mid\underline{x}\mid\cdot e^{j\varphi}$$

$$\underline{x} = \mid\underline{x}\mid e^{j\varphi_{\underline{x}}}= \mid\underline{x}\mid\cos(\varphi_{\underline{x}})+j\mid\underline{x}\mid\sin(\varphi_{\underline{x}})$$

**Betrag** $$\mid\underline{x}\mid$$:

$$\mid\underline{x}\mid = \sqrt{Re(\underline{x})^2+Im(\underline{x})^2}$$

$$ = \arctan(\frac{Im(\underline{x})}{Re(\underline{x})}), \cdots Re(\underline{x})\geq0$$

**Phase** [ $$\varphi_{\underline{x}}$$ ]:

$$\pi+\arctan(\frac{Im(\underline{x})}{Re(\underline{x})})$$

---

**Impedanz** $$[\Omega]$$:

$$\underline{Z}=\frac{\underline{U}}{\underline{I}}=\frac{\underline{\hat{u}}}{\underline{\hat{i}}}=\frac{\hat{u}e^{j\varphi_u}}{\hat{i}e^{j\varphi_i}}$$

**Admittanz** $$[\frac{1}{\Omega}]$$:

$$\underline{Y}=\frac{I}{\underline{U}}=\frac{\underline{\hat{i}}}{\underline{\hat{u}}}=\frac{\hat{i}e^{\varphi_i}}{\hat{u}e^{\varphi_u}}=\frac{1}{\underline{Z}}$$

---

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_a_groundlage.png?raw=true">

**Wechselspannung**:

$$u(t) = \hat{u}\cos(\omega t'+\varphi_{U})\cdots[V]$$

**Wechselstorm**:

$$i(t) = \hat{i}\cos(\omega t+\varphi_{I})\cdots[A]$$

$$\omega = 2\pi f \cdots[rad/s = Hz]$$

---

$$\underline{u} = \hat{u}\cdot e^{j\varphi_{U}}\cdot e^{j\omega t} = \sqrt{2}\cdot U \cdot e^{j\varphi_{U}}\cdot e^{j\omega t} $$

$$\cdots \underline{\hat{u}} = \hat{u}\cdot e^{j\varphi_{U}},\;\; \underline{U} = \sqrt{2}\cdot U \cdot e^{j\varphi_{U}}$$

$$\underline{i} = \hat{i}\cdot e^{j\varphi_{I}}\cdot e^{j\omega t} = \sqrt{2}\cdot I \cdot e^{j\varphi_{I}}\cdot e^{j\omega t} $$

$$\cdots \underline{\hat{i}} = \hat{i}\cdot e^{j\varphi_{I}},\;\; \underline{I} = \sqrt{2}\cdot I \cdot e^{j\varphi_{I}}$$

---

**ideale passive Bauelemente**

**Widerstand R** $$[\Omega]$$:

$$Z_R=R+j\cdot 0$$

$$\underline{U} = Z_R\cdot\underline{I} \Leftrightarrow U\cdot e^{j\varphi_U} = R\cdot I\cdot e^{j \varphi_I} \rightarrow U = RI \cdots \varphi_U=\varphi_I$$

**Induktivität L** $$[H = \Omega\cdot s]$$:

(nur komplexe Zahl)

$$\underline{Z_L} = j\omega L = \omega L\cdot e^{j \cdot \frac{\pi}{2}}$$

$$\underline{U} = \underline{Z_L}\cdot \underline{I} \Leftrightarrow U\cdot e^{j\varphi_U} = j\omega L \cdot I \cdot e^{j \varphi_I}$$

$$U = \omega L \cdot I$$

$$\varphi_U = \varphi_I + \frac{\pi}{2} \; \; \; \cdots \; \varphi_{Z_\underline{L}} = arctan\left(\frac{Im(\underline{Z_L})}{Re(\underline{Z_L})}\right) = arctan\left(\frac{\omega L}{0}\right) = \frac{\pi}{2}$$

**Kapazität C** :

$$Z_c = \frac{1}{j\omega c}\cdot\frac{j}{j}=j\cdot\frac{1}{j^2\omega c}=-j\frac{1}{\omega c}=\frac{1}{\omega c}\cdot e^{j(-\frac{\pi}{2})}$$

$$U e^{j\varphi_U} = \frac{1}{\omega c} e^{-j \frac{\pi}{2}}\cdot I \cdot e^{j\varphi_I}$$

$$U = \frac{I}{\omega c}$$

$$\varphi_U=\varphi_I-\frac{\pi}{2}$$

---

# Zeigerdiagramm (qualitativ und quantitativ)

## 1. Aufgabe: Qualitatives Zeigerdiagramm

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_a_u1.jpg?raw=true" width="1000px"/>

### 1.1. Zeichnen des Zeigerdiagramms ohne genaue Berechnung

`Zeichnen Sie das qualitative Zeigerdiagramm` aller Ströme und Spannungen des Netzwerks (Abbildung 1). Kennzeichnen Sie dabei im Diagramm alle rechtenWinkel (90◦-Winkel) zwischen einzelnen Größen.
Zeichnen Sie abschließend die reelle und imaginäre Achse ein.  
_Hinweis: Beginnen Sie mit dem Strom_ $$\underline{I_{R1}}$$

**Lsg:**

$$
\begin{align}
\\
&\underline{I}_{R1} = I_{R1}\cdot e^{j\varphi_{R1}}\\
&\underline{I}_C=\underline{I}_{R1}  \\
&\underline{U}_{R1}=R\cdot \underline{I}_{R1} = R\cdot I_{R1}\cdot e^{j\varphi_{I_{R1}}} = U\cdot e^{j\varphi_{U_{R1}}} \\
&\underline{U}_C=\frac{1}{\omega C}e^{-j\frac{\pi}{2}}\cdot I_{R1}\cdot e^{j\varphi{I_{R1}}} \\
\\
&\underline{U}_{R2}=\underline{U}_{R1}+\underline{U}_C \\
&\underline{I}_{R2}=\frac{\underline{U}_{R2}}{R}\\
\\
&\underline{I}_{L} = \underline{I}_{R1}+\underline{I}_{R2}\\
&\underline{I}_0 = \underline{I}_{L}\\
&U\cdot e^{j\varphi_U} = \omega L\cdot e^{j\frac{\pi}{2}}\cdot e^{j\varphi_{\underline{I}_2}}\\
&\underline{U}_0 = \underline{U}_L + \underline{U}_{R2}
\end{align}
$$

## 2. Aufgabe: Quantitatives Zeigerdiagramm

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_a_u2.jpg?raw=true" width="1000px"/>

### 2.1. Berechnung und Zeichnung mit Bezuggröße

Zeichnen Sie das quantitative Zeigerdiagramm aller Ströme und Spannungen des Netzwerks (Abbildung 2). Beginnen Sie am Bauteil C2 und nehmen für das Zeigerdiagramm erst einmal als beliebig gewöhlte Größe $$\underline{U'}_{C,2} = 10V\cdot e^{j0◦}$$ an. Achten Sie bei der `Länge der Zeiger` auf die Größen der Bauteile!  
_Hinweis: Zur Ermittlung der Länge der Zeiger denken Sie an das Ohmsche Gesetz! Orientieren Sie sich an der Länge des vorgegebenen Zeigers. Nutzen Sie das Koordinatensystem aus Abbildung 3_

**Lsg:**

$$
\begin{align}
&\underline{U}_{C_2} = 10V\\
&\underline{I}_{C_2} = j\omega C_2 \cdot \underline{U}_{C_2} = 1 A \cdot e ^{j\frac{\pi}{2}}\\
&\underline{U}_{R_2} = R_2\underline{I}_{C_2} = 3,2V\cdot e^{j\frac{\pi}{2}}\\
\\
&\underline{U}_{R_1} = U_{R_2}+U_{C_2} = \text{10,5}V \cdot e^{j \text{17,74}^\circ }\\
&\underline{I}_{R_1} = \text{1,05} \cdot e^{j\text{17,74}^\circ}\\
\\
&\underline{U}_{C_1} = \text{10,5}V \cdot e^{j\text{17,74}^\circ}\\
&\underline{I}_{C_1}= \text{2,1}A \cdot e^{j\text{107,74}^\circ}\\
\\
&\underline{I}_{L_1}= \text{3,34}A \cdot e^{j\text{83,8}^\circ}\\
&\underline{U}_{L_1} = \text{6,68}V \cdot e^{j\text{173,8}^\circ}\\
\\
&\underline{I}_0= \underline{I}_{L_1}\\
&\underline{U}_0 = \text{5,16}V \cdot e^{j\text{49,4}^\circ}\\
\end{align}
$$

### 2.2. Neuberechnung der Größen bei Bezugsgröße U0

Da im Allgemeinen eine Quelle als Referenzwert f¨ur die Schaltung genutzt wird, m¨ussen alle Werte auf
diese bezogen werden. In diesem Fall wird die Quelle mit $$\underline{U}_0 = 15V\cdot e^{j0◦}$$ vorgegeben. Zeichnen Sie das richtige Koordinatensystem ein. Bestimmen Sie anschließend alle Spannungs- und Stromgrößen bezogen
auf den Referenzwert.

**Lsg:**

$$
\begin{align}
&\underline{U'}= 15V\\
&\underline{U}_0=\underline{K} \cdot \underline{U}_0 \Leftrightarrow K = \frac{15V}{\underline{U}_0}  \\
\end{align}
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
