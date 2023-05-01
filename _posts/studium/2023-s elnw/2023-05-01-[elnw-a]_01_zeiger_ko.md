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

# 00 기본 공식

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

---

Quelle(text):  
Groundlagen zur Elektrotechnik, Technische Hochschule Mittelhessen Pdf datei: <https://www.thm.de/iem/images/user/novender-978/get.pdf>  
ElectronicsTutorials: <https://www.electronics-tutorials.ws/accircuits/complex-numbers.html>
Quelle(image): Elektrische Netzwerke TU-Berlin pdf datei
<https://isis.tu-berlin.de/pluginfile.php/2756135/mod_resource/content/10/1_Grundlagen_Zeiger-SENSE-2023.pdf>

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
