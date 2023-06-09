---
layout: single
title: "[ELNW-v] 01 Zeiger의 기초(Grundlagen der Zeiger)"
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

date: 2023-04-21
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# Zeiger의 기초(Grundlagen der Zeiger)

표기법

**𝑈, 𝐼:** `시간에 따라 변하지 않는`, 즉 정상상태인(reelle zeitunabhängige) 전압과 전류를 나타내는 실수값.

**𝑢, 𝑖:** `시간에 따라 변하는`, 즉 transiente 상태인(reelle zeitveränderliche) 전압과 전류를 나타내는 실수값.

$$\boldsymbol{\underline{U}}$$, $$\boldsymbol{\underline{I}}$$: `시간에 따라 변하지 않는`(reelle zeitunabhängige) 전압과 전류의 phasor 형태(즉, 복소수 형태)를 나타내는 값. 이러한 값을 복소수 형태로 표현하면 쉽게 계산이 가능해진다. 예를 들어 𝑈̂ = 𝑈_0∠𝜑는 크기가 𝑈_0이고 위상이 𝜑인 복소수를 나타낸다.

$$\boldsymbol{\hat{u}}$$, $$\boldsymbol{\hat{i}}$$: 복소수 형태의 전압과 전류의 크기, 즉 amplitude를 나타내는 값이다. 이러한 값을 Scheitelwerte(peak values)라고 한다.

복소수 형태의 값은 크기와 위상을 동시에 나타낼 수 있으므로, 전압과 전류 사이의 위상 차이 등을 쉽게 계산할 수 있다. Scheitelwerte는 주로 실제 전기 회로에서 사용되는 AC 전압 및 전류의 최대 크기를 나타내기 위해 사용된다.

## 01 주기함수(periodische Funktionen)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_PeriodischeFunktion-100.jpg?raw=true">

정의 : 정의역 상의 모든 점에서 같은 값을 가지는 함수로, 일정한 주기를 가지고 있다. 이러한 주기는 함수의 시간적인 특성을 설명해준다. 예를 들어, 함수 f(t)가 T 주기를 가진 주기함수라면, f(t)는 모든 t에 대해 f(t+T) = f(t)를 만족한다. 이는 f(t)의 시간적인 특성이 T 시간 간격마다 반복된다는 것을 의미한다.  
예. sin함수나 cos함수

## 02 harmonische Größen

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_HarmonischeGr%C3%B6%C3%9Fen-100.jpg?raw=true">
  
**harmonische Größen**은 주기적으로 반복되는 신호를 나타내는데 사용되는 용어이다.  
이러한 신호는 일정한 주파수를 가지며, 주로 사인파(sinusoidal wave) 또는 코사인파(cosinusoidal wave)와 같은 파형을 가진다.

$$u(t) = \hat{u}\cdot\cos(\omega t + \varphi)$$

$$\boldsymbol{\hat{u}}$$: 진폭(amplitude)  
$$\boldsymbol{\omega}$$: 각 주파수(Kreisfrequenz)  
$$\boldsymbol{\varphi}$$: 위상각 또는 상대위상(Phasenwinkel)

> **Phasenwinkel 또는 Phasenverschiebung :**
> "Phasenwinkel" 또는 "Phasenverschiebung"은 주기적인 신호에서 파형의 시간적인 차이를 나타내는데 사용되는 용어다. 일반적으로 라디안(radian)이나 도(degree)로 표현된다.

예를 들어, AC 전압 신호의 경우, 그 크기는 주기적으로 변하지만, 주기는 일정하게 유지된다. 주로 코사인(cosine) 함수의 형태를 가지며, 그 크기는 해당 전압 신호의 최대값(peak value)을 나타낸다. 또한 이러한 신호는 전기공학 분야에서 매우 중요한 역할을 한다.

전기 회로에서 발생하는 AC 전압 및 전류 신호는 "Harmonische Größen"을 기반으로 하며, 이러한 신호는 주기적으로 변하는 특성을 가지기 때문에, 푸리에 변환과 같은 주파수 분석 기술을 사용하여 분석된다. 이러한 분석을 통해 전압 및 전류 신호의 주파수 성분을 분석할 수 있으며, 이를 통해 전력 시스템에서 발생하는 "Oberschwingungen"과 같은 문제를 해결할 수 있다.

## 03 elektrische Bauteile an Wechselspannung

### 03-1 저항(옴)에 교류전압이 가해지는 경우(Wechselspannung an Ohmschem Widerstand)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_OhmschemWiderstand-100.jpg?raw=true">
  
$$i(t) = \frac{U_R(t)}{R} = \frac{\hat{u}}{R}\cdot\cos(\omega t) = \hat{i}\cdot\cos(\omega t)$$

Ohmsches Gesetz에 따르면, 전압과 전류의 크기는 저항(R)에 비례한다.  
따라서, AC 전압이 저항(Ohmschen Widerstand)에 가해질 때, 전압과 전류의 크기는 옴의 법칙에 따라 비례하게 된다.

AC 전압은 시간에 따라 변하는데 주로 사인파 또는 코사인파와 같은 파형을 가진다.  
따라서 전압과 전류의 크기는 위에 제시한 것과 같이 계산된다.

<!-- 여기서, Vp는 AC 전압의 최대값(peak value), Ip는 AC 전류의 최대값(peak value), ω는 각주파수를 나타내며, t는 시간을 나타낸다.

따라서, AC 전압이 Ohmschen Widerstand에 가해질 때, 전압과 전류의 크기는 최대값에 따라 결정되며, 이를 통해 전압, 전류 및 저항과 같은 전기적인 크기들을 계산하고 분석할 수 있다. -->

### 03-2 코일에 교류전압이 가해지는 경우 (Wechselspannung an Spule mit Induktivität L)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_%20Induktivit%C3%A4t_L-100.jpg?raw=true">

$$i(t)=\frac{1}{L}\int u_L(t) dt=\frac{\hat{u}}{L}\int\cos(\omega t)dt=\frac{\hat{u}}{\omega L}\sin(\omega t)+I_0=I_0+\frac{\hat{u}}{\omega L}\sin(\omega t)$$

$$i(t)=I_0+\frac{\hat{u}}{\omega L}\cos(\omega t-\frac{\pi}{2})$$

교류전압이 코일(Spule, L)에 인가되면, 코일에 전류가 유도된다. 이때 전류의 크기와 방향은 인가된 전압의 크기 및 주파수, 그리고 코일의 인덕턴스(L)에 따라 결정된다.
AC전압은 마찬가지로 파형을 가지므로, 전압과 전류의 크기는 위에 제시한 것과 같이 계산된다.

### 03-3 콘덴서에 교류전압이 가해지는 경우 (Wechselstrom an Kondensator mit Kapazität C)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Kapazit%C3%A4t_C-100.jpg?raw=true">

$$u_c(t)=\frac{1}{C}\int i_c(C)dt=\frac{\hat{i}}{C}\int - \sin(\omega t)dt=\frac{\hat{i}}{\omega C}\cos(\omega t)+U_0$$

$$u_c(t) = U_0+\frac{\hat{i}}{\omega C}\cos(\omega t)$$

교류전압이 캐패시터(C)에 인가되면, 캐패시터 내부에 전하가 축적된다. 이때 축적된 전하는 인가된 전압의 크기 및 주파수, 그리고 캐패시터의 용량(C)에 따라 결정된다.

캐패시터(C)에 가해지는 AC 전압은 시간에 따라 변하는 전압이며, 주로 사인파 또는 코사인파와 같은 파형을 가진다. 이러한 AC 전압이 캐패시터(C)에 가해지면, 전압과 전류의 크기는 위에 제시한 것과 같이 계산된다.

<div class="notice--info">
<h3>캐패시터(Kapazität)</h3>
캐패시터(C)의 용량은 축적된 전하량에 대한 전압의 비례상수이며, 다음과 같이 계산된다.<br>
<br>  
<b>C = Q/V</b><br>
<br>
여기서, Q는 축적된 전하량을 나타내고, V는 전압을 나타낸다.<br>
따라서, 캐패시터(C)에 가해지는 AC 전압은 위상각(Phase Angle)에 따라 전류에 대한 전압의 크기와 방향이 결정된다. <br>
이를 통해 캐패시터(C) 내부에 축적된 전하의 크기와 방향을 분석하고 계산할 수 있다.
</div>

## 04 Projektion der Eulerdarstellung

Euler 표현법을 사용하면, 복소수는 크기와 각도로 표현될 수 있다.  
복소수 z = x + jy는 크기(r)와 각도(θ)를 사용하여 z = r∠θ로 표현할 수 있다.  
(여기서 j는 허수 단위(i)와 같은 역할을 한다.)

**Zeigerdiagramm:**
Zeigerdiagramm은 r의 크기와 θ의 각도를 사용하여 복소수를 나타내는 방법이다. r의 크기는 Zeiger의 길이를 결정하며, θ는 Zeiger의 각도를 결정한다. 이를 통해 Zeigerdiagramm은 복소수의 크기와 각도를 직관적으로 이해할 수 있다.

**Projektion der Eulerdarstellung:**
Projektion der Eulerdarstellung은 Zeigerdiagramm과 시간 함수의 관계를 나타내는 방법 중 하나이다. 이를 통해 Zeigerdiagramm에서 파생되는 시간 함수를 계산할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Eulerdarstellung-100.jpg?raw=true">

시작 시점에서 Zeiger는 Realteilachse(실수축)에 있으며, 각도는 0도 이다. 이 상태에서는 실수부가 최대이며, 허수부는 0이다. 이후 시간이 지남에 따라 Zeiger는 원형을 따라 회전하며, 각도는 증가한다.

이러한 Zeiger의 회전은 시간 함수에서 주기적인 신호를 생성하게 된다. 이때 Zeiger의 회전 속도는 각주파수(ω)에 비례하며, 각도는 시간(t)에 비례한다. 즉, 각도의 증가량은 시간에 따라 선형적으로 증가한다.

(위에 projektion의 결과로 실수 축은 cos함수, 허수 축은 sin함수인 것을 알 수 있다.)

따라서, Projektion der Eulerdarstellung은 Zeigerdiagramm과 시간 함수의 관계를 시각적으로 이해할 수 있게 해주는 방법이다. 이를 통해 복소수와 관련된 전기적 크기들을 계산하고 분석할 수 있다.

## 05 Darstellung mit komplexen Amplituden

"Darstellung mit komplexen Amplituden"은 복소수 형태의 효과적인 값을 사용하여 전기 회로를 분석하는 방법이다. 이 방법은 실수부를 복소수로 확장하고, 그와 수직인 허수부를 추가하여 구성된다. 이 방법은 코사인 함수와 사인 함수의 효과적인 값을 나타내기 때문에 매우 효율적이며 정확하다.
복소수 형태를 사용하면, 덧셈, 뺄셈, 곱셈과 같은 복잡한 계산을 쉽게 수행할 수 있다.
(복소수의 실수부와 허수부를 각각 더하거나 빼고, 곱하면 됨.)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_komplexen_Amplituden-100.jpg?raw=true">

$$u(t) = \hat{u}(\cos(\omega t+\varphi_u)+ j\sin(\omega t +\varphi_u))$$  
$$Re(\underline{u}(t))=\hat{u}\cos(\omega t+\varphi_u)$$  
$$Im(\underline{u}(t))=\hat{u}\sin(\omega t+\varphi_u)$$

여기에 `오일러 공식(Eulerschen Form)`을 적용하면..

$$e^{jx}=\cos(x)+j\sin(x)$$  
$$\underline{u}(t)=\hat{u}e^{j(\omega t + \varphi_u)}$$  
$$\underline{u}(t)=\hat{u}e^{j\varphi_u}e^{j\omega t}$$

그리고 시간에 따라 변하는 부분과 변하지 않는 부분(시변과 시불변)으로 나누면 다음과 같이 정리된다.

komplexe Amplitude: $$\underline{\hat{u}}(t)=\hat{u}e^{j\varphi_u}$$  
drehender Zeiger: $$\underline{u}(t)=e^{j\omega t}$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_komplexen_Amplituden2-100.jpg?raw=true">

$$\underline{u}(t)=\hat{u}e^{j(\omega t + \varphi_u)}=\sqrt{2}Ue^{j(\omega t+\varphi_u)}$$  
$$\underline{i}(t)=\hat{i}e^{j(\omega t + \varphi_i)}=\sqrt{2}Ie^{j(\omega t+\varphi_i)}$$

<div class="notice--info">
<h3>오일러 공식(Eulerschen Form)</h3>
복소수 형태는 <b>z = a + bj</b>와 같이 실수부(a)와 허수부(b)를 가지는 복소수를 표현하는 방법이다. (여기서 j는 허수 단위(i)와 같은 역할을 한다.)<br>
오일러(Euler) 형식은 복소수를 다음과 같이 표현하는 방법이다.<br>
<br>
<b>z = r e^(jθ)</b><br>
<br>
여기서, r은 복소수의 크기, θ는 복소수의 위상각(phase angle)을 나타내며, e는 자연 상수를 나타낸다. 이와같이 위상각을 사용하는 오일러(Euler) 형식은 복소수를 극좌표계(polar coordinate)로 표현하는 방법이다. <br>

<h3>오일러 형식과 삼각함수와의 관계</h3>

오일러(Euler) 형식으로 나타낸 복소수 z = r e^(jθ)를 살펴보면, 코사인, 사인 함수로 정리할 수 있다. 우선, 오일러(Euler) 공식은 다음과 같다.<br>
<br>
<b>e^(jθ) = cos(θ) + j sin(θ)</b><br>
<br>
따라서, 복소수 z는 다음과 같이 나타낼 수 있다.<br>
<br>
<b>z = r e^(jθ) = r (cos(θ) + j sin(θ))</b><br>
<br>
여기서, a = r cos(θ)는 복소수의 실수부로, b = r sin(θ)는 복소수의 허수부라고 하면,복소수 z는 다음과 같이 정리할 수 있다.<br>
<br>
<b>z = a + jb = r cos(θ) + j r sin(θ) = r cos(θ) + j r sin(θ)</b><br>
<br>
<b>a = r cos(θ) = Re(z)</b><br>
<b>b = r sin(θ) = Im(z)</b><br>

</div>
  
  
## 06 임피던스와 어드미턴스(Impedanz und Admittanz)
  
`임피던스와 어드미턴스`도 복소수로 표현되기 때문에, 지수형태(Exponentielle Form)와 직교 좌표 형태(Karthesische Form)로 나타낼 수 있다.

### 06-1 임피던스(Impedanz)

**Definition Impedanz**

$$\underline{Z}=\frac{\underline{U}}{\underline{I}}=\frac{\underline{\hat{u}}}{\underline{\hat{i}}}=\frac{\hat{u}e^{j\varphi_u}}{\hat{i}e^{j\varphi_i}}$$

**Exponentielle Form**

$$\underline{Z}=\frac{\hat{u}}{\hat{i}}e^{j(\varphi_u-\varphi_i)}$$

**Karthesische Form**

$$\underline{Z}=R+jX$$

여기서 R은 저항(Wirkwiderstand, Resistanz), X는 `리액턴스(Blindwiderstand, Reaktanz)`

### 06-2 어드미턴스(Admittanz)

**Definition Admittanz**

$$\underline{Y}=\frac{I}{\underline{U}}=\frac{\underline{\hat{i}}}{\underline{\hat{u}}}=\frac{\hat{i}e^{\varphi_i}}{\hat{u}e^{\varphi_u}}=\frac{1}{\underline{Z}}$$

**Exponentielle Form**

$$\underline{Y}=\frac{\hat{i}}{\hat{u}}e^{j(\varphi_i-\varphi_u)}$$

**Karthesische Form**

$$\underline{Y}=G+jB$$

여기서 G는 컨덕턴스(Wirkleitwert, Konduktanz), B는 `서셉턴스(Blindleitwert, Suszeptanz)`

<div class="notice--info">
<h3>임피던스와 어드미턴스의 기초(grundlage der Impedanz und Admittanz)</h3>
<br>
<h4>임피던스(Impedanz):</h4>  
Impedanz는 회로에서 전압과 전류 간의 관계를 설명하며, Admittanz는 전류와 전압 간의 관계를 설명한다.<br>
Impedanz는 전기 회로에서 저항(R), 인덕턴스(L), 그리고 캐패시턴스(C)가 결합되어 생기는 효과이며 복소수로 표현된다.<br>
저항, 인덕턴스, 캐패시턴스가 각각 R, L, C일 때, Impedanz Z는 다음과 같다.<br>
<br>
<b>Z = R + j(ωL - 1/ωC)</b><br>
<br>
여기서 ω는 각주파수를 나타내며, j는 허수임을 나타낸다.<br>
<br>
<h4>어드미턴스(Admittan):</h4> 
Admittanz는 Impedanz의 역수다. 따라서 Admittanz Y는 다음과 같다.<br>
<br>
<b>Y = 1/Z = G + jB</b><br>
<br>
여기서 G는 회로의 전도도(Conductance), B는 회로의 서셉턴스(Susceptance)다.<br>
서셉턴스(Susceptance)는 캐패시턴스와 인덕턴스의 비율에 따라 결정된다.<br>
</div>

<div class="notice--info">
<h3>리액턴스와 서셉턴스의 차이(Unterschied zwischen Reaktanz und Suszeptanz)</h3>
<br>
서셉턴스와 리액턴스 모두 AC 회로에서 발생하는 전기 신호의 주파수 변화에 따라 변화하는 값을 의미하지만, 두 값은 서로 다른 의미를 가진다.<br>
<br>
<h4>리액턴스(Reaktanz, Blindwiderstand):</h4> 
리액턴스는 AC 회로에서 발생하는 총 저항성을 의미한다. 이는 캐패시터와 인덕터 모두가 가지는 저항성을 포함한다. 리액턴스는 캐패시터와 인덕터 모두에서 발생하는 값을 합산한 것으로, 복소수로 표현되며, 리액턴스의 크기는 전압과 전류의 크기 비율에 의해 결정된다.<br>
<br>
<h4>서셉턴스(Suszeptanz):</h4> 
반면, 서셉턴스는 AC 회로에서 발생하는 리액턴스 중에서도, <b>캐패시터</b>의 특성으로 인해 발생하는 값을 의미한다. 따라서, 서셉턴스는 캐패시터에서 발생하는 리액턴스만을 나타내며, 캐패시터가 가지는 고유한 특성을 반영한다.<br>
<br>
결론적으로, 리액턴스는 AC 회로에서 전기 신호의 주파수 변화에 따라 전체적으로 변화하는 저항성을 나타내며, 서셉턴스는 캐패시터가 가지는 고유한 특성으로 인해 변화하는 값입니다.
</div>

## 08 komplexe Widerstände

### 08-1 Idealer Wirkwiderstand

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Idealer_Wirkwiderstand-100.jpg?raw=true">

### 08-2 Induktiver Blindwiderstand

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Induktiver_Blindwiderstand-100.jpg?raw=true">

### 08-3 Kapazitiver Blindwiderstand

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Kapazitiver%20Blindwiderstand-100.jpg?raw=true">

### 08-4 Wechselspannung an Ohmschem Widerstand

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Wechselspannung_an_Ohmschem_Widerstand-100.jpg?raw=true">

### 08-5 Wechselspannung an Induktivität

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Wechselspannung_an_Induktivit%C3%A4t-100.jpg?raw=true">

### 08-6 Wechselstrom an Kapazität

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Wechselstrom_an_Kapazit%C3%A4t-100.jpg?raw=true">

## 09 Kirchhoffsche Gesetze

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Kirchhoffsche_Gesetze-100.jpg?raw=true">

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/01_zeiger/01_Kirchhoffsche_Gesetze2-100.jpg?raw=true">

## 10 Reihen- und Parallelschaltung

### 10-1 Reihenschaltung

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/elnw/img/01_zeiger/01_Reihenschaltung-100.jpg?raw=true">

### 10-2 Parallelschaltung

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/elnw/img/01_zeiger/01_Parallelschaltung-100.jpg?raw=true">

### Umrechnung zwischen Impedanz und Admittanz

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/elnw/img/01_zeiger/01_Umrechnung_zwischen_Impedanz-100.jpg?raw=true">

---

Quelle(text):  
Groundlagen zur Elektrotechnik, Technische Hochschule Mittelhessen Pdf datei: <https://www.thm.de/iem/images/user/novender-978/get.pdf>  
ElectronicsTutorials: <https://www.electronics-tutorials.ws/accircuits/complex-numbers.html>
Quelle(image): Elektrische Netzwerke TU-Berlin pdf datei
<https://isis.tu-berlin.de/pluginfile.php/2756135/mod_resource/content/10/1_Grundlagen_Zeiger-SENSE-2023.pdf>

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
