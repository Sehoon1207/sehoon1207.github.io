---
layout: single
title: "[ELNW-v] 04 Quellen und Lasten"
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

date: 2023-05-09
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# 01 Effektivwert

Effektivwert는 전기 및 전자 공학에서 사용되는 용어로, 주로 교류 신호의 크기를 나타내는 데 사용된다. Effektivwert는 신호의 "평균 제곱 값"을 의미한다.

실제로 많은 교류 신호는 시간에 따라 변하는 값이며, 이러한 신호의 크기를 평가하기 위해 주파수를 고려해야 한다. 이때 Effektivwert는 교류 신호의 효과적인 크기를 나타내는 지표로 사용된다.

평균값은 동일한 크기의 경우 특히 중요하다

$$𝑈_{av}=\frac{1}{T} \int_{0}^{T}{u(t)}\;dt$$

Effektivwert는 주기 T 동안의 신호의 제곱을 평균한 값의 제곱근으로 정의됩니다. 수학적으로는 다음과 같이 표현된다:

$$𝑈_{rms}=\sqrt{\frac{1}{T}\int_{0}^{T}u^2(t)\;dt} = \sqrt{\frac{1}{2\pi}\int_{0}{2\pi}u^2(\omega t)\;d(\omega t)}$$

# Ideale Quellen

# Reale Quellen

# Quellen mit Last

# Leistungsanpassung

# Gesteuerte Quellen

# Ersatzquellen

# Zweipol

# 00 용어 정의 (Begriffsdefinitionen)

• **정상 상태(stationärer Zustand)**:
전환 작업 전 또는 후에 정상 상태

• **균형 과정(Ausgleichsvorgang)**:
하나의 정상 상태에서 다른 정상 상태로 전환

• **스위치(Schalter)**:
스위치는 이상적이라고 가정한다. 즉,

스위치는 즉시 전환됨  
$$R_{auf}\rightarrow\infty, R_{zu}=0$$  
매우 높은 전압 및 전류를 견딜 수 있음

• DGL(ODE)는 **미분 방정식**의 약자이다.

• 전압 $$u_x$$ 의 **시간 도함수에 대한 표기**법

$$\frac{du_x}{dt}=\frac{d}{dt}u_x=\dot{u}_x$$

# 01 DC 전압을 사용하는 네트워크의 스위칭과정 (Schaltvorgang in Netzwerken mit Gleichspannung)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-1_Schaltvorgang.jpg?raw=true" />

## 01-1 커패시터 방전 Entladen eines Kondensators

정지 상태:  
• 전원 끄기 전 상태: 𝑡 < 𝑡0  
• 전원이 꺼진 후 오랜 시간이 지난 상태: 𝑡 → ∞  
균형 과정(Ausgleichvorgang)은 𝑡 = 𝑡0에서 시작.

<div class="notice--info">
정상상태에서 스위치가 닫혀 있을 때, Capacitor에 충전된 전압이 존재한다. 이 상태에서 스위치가 열리게 되면, Capacitor에 저장된 전하가 점점 방전되면서 전압이 줄어들게 된다. 이를 Capacitor의 방전 과정 및 방전 상태라고 할 수 있다.
</div>

**1) 스위치를 올리기 전과 후**

• **𝑡 ≤ 𝑡0의 경우**:

`메쉬 방정식(Maschengleichung)`: $$U = u_R + u_C$$  
커패시터 𝐶가 충전됨  
전류 흐름 없음 $$i_R=i_C=0$$  
왜냐하면 $$u_R=R\cdot i_R  \rightarrow  u_R = 0$$  
따라서 $$u_C = U$$ 이다.

• **𝑡 > 𝑡0의 경우**:

$$0=u_R + u_C = R\cdot i_R + u_C = R \cdot i_C + u_C$$

이렇게 정리할 수 있다.  
커패시터에는 다음과 같이 적용된다: $$i_C = C\frac{du_C}{dt} = C\dot{u}_C$$  
따라서 다음은 미분방정식(DGL, ODE)의 `균형 과정(Ausgleichsvorgang)`이다.

$$0=R\cdot C\frac{du_C}{dt}+u_C$$

<div class="notice--info">
이때, 스위치가 열린 시점을 t0이라고 하면, t < t0에서는 Capacitor에 충전된 전압이 존재하므로, 전류가 흐르지 않는다. 그리고 t > t0에서는 Capacitor에서 전하가 방전되면서 전류가 흐르게 되며, 이 때 Capacitor의 방전을 설명하는 미분방정식을 구할 수 있다.
</div>

<div class="notice--danger">
메쉬 방정식(Maschengleichung)<br>
Maschengleichung은 전기회로의 법칙 중 하나로, 회로의 모든 루프(링)에 대한 전압합이 0이 되어야 한다는 원리다. 수식적으로는 다음과 같이 나타낼 수 있다.
</div>

$$\sum_k U_k = 0$$

k: 루프(링)의 번호  
$$U_K$$ : 해당 루프(링)를 따라 일어나는 전압 차이

<div class="notice--danger">
예를 들어, 회로에서 전류나 전압의 특정 값을 알고 있을 때, Maschengleichung을 이용하여 다른 값을 계산할 수 있다.
</div>

**2) 동차 선형 미분방정식**

$$0=R\cdot C\frac{du_C}{dt}+u_C$$

• 모든 항들이 $$𝑢_C$$ 또는 그것의 미분에 의존한다. -> **동차 선형 미분방정식(homogene Differentialgleichung)**

따라서 $$𝑢_C = 𝑘 \cdot e^{pt}$$ 을 대입하면,

$$0=RC\cdot\frac{d}{dt}(k\cdot e^{pt})+k\cdot e^{pt}$$
$$0=RC\cdot kp \cdot e^{pt} + k\cdot e^{pt}$$
$$0=(RC\cdot + 1)\cdot k \cdot e^{pt}$$

• $$𝑘 \cdot e^{𝑝𝑡}$$ 는 0이 아니므로 괄호 안의 부분이 0이 되어야 한다.

$$0 = RC\cdot p +1 \rightarrow p = -\frac{1}{RC} = -\frac{1}{\tau}$$

**3) 동차 선형 미분방정식(homogene Differentialgleichung)의 풀이**

• 이제 𝑝를 𝜏로 바꿔쓸 수 있음: $$𝑢_C=𝑘\cdot e^{𝑝𝑡}=𝑘\cdot e^{−𝑡/𝜏}$$  
• 𝑘를 결정하려면 조건을 하나 더 고려해야 한다.  
• 이것은 시간 $$𝑡=𝑡_0$$ 에서 $$𝑢_C$$ 에 대한 초기 조건으로 가능하다.

따라서...  
$$𝑢_C(𝑡=𝑡0)=𝑘\cdot e^{−𝑡_0/𝜏}=𝑈$$  
$$𝑘=𝑈\cdot e^𝑡0/𝜏$$

• 따라서 동차 선형 미분방정식은 다음과 같이 변형된다.  
$$𝑢_C=𝑈\cdot e^{𝑡0/𝜏}\cdot e^{−𝑡_0/𝜏}=𝑈\cdot e{−(𝑡−𝑡_0)/𝜏}, 𝑡−𝑡0≥0$$

• 𝜏는 시간상수(Zeitkonstante)이며, 이 경우 𝜏=𝑅∙𝐶

<div class="notice--info">
여기서 𝜏는 저항 𝑅과 커패시터의 커패시턴스 𝐶의 곱과 같으며, 소위 RC 요소의 시간상수(Zeitkonstante)를 의미한다. 특정 저항을 가진 커패시터의 충전 또는 방전 프로세스가 얼마나 빨리 발생하는지 나타낸다.<br> 
𝜏 값이 클수록 커패시터를 충전 또는 방전하는 과정이 느려진다. 𝜏이 작아질수록 커패시터를 완전히 충전하거나 방전하는 데 걸리는 시간이 줄어든다.<br> 
</div>

## 01-2 방전 중 전압 곡선 Spannungsverlauf bei der Entladung

$$u_C = U\cdot e^{-\frac{t-t_0}{𝜏}}, 𝑡−𝑡0≥0$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-2_Spannungsverlauf.jpg?raw=true" />

## 01-3 방전 중 전류 곡선 Stromverlauf bei der Entladung

$$i_c = C\frac{du_C}{dt} = C\frac{d}{dt}(U\cdot e^{-(t-t_0)/𝜏}),  𝑡−𝑡_0≥0$$

$$-\frac{CU}{𝜏}\cdot e^{-(t-t_0)/𝜏=-\frac{U}{R}\cdot e^{-(t-t_0)/𝜏}}$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-3_Stromverlauf.jpg?raw=true" />

## 01-4 커패시터 충전(Aufladen eines Kondensators)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-4_Schaltvorgang2.jpg?raw=true" />

정지 상태:  
• 전원 끄기 전 상태: 𝑡 < 𝑡0  
• 전원이 꺼진 후 오랜 시간이 지난 상태: 𝑡 → ∞  
균형 과정(Ausgleichvorgang)은 𝑡 = 𝑡0에서 시작.

**1) 스위치를 올리기 전과 후**

$$t≤t_0$$ 일 때:

커패시터 𝐶가 충전되지 않음: $$u_C = 0$$

$$t→∞$$ 일 때:

커패시터 𝐶가 충전됨  
전류 흐름 없음, $$𝑢_C(𝑡)$$ 더 이상 변경되지 않음

$$u_C = U$$

$$t>t_0$$ 일 때:

$$ 𝑈 = 𝑢_R + 𝑢_C = 𝑅 \cdot 𝑖_R + 𝑢_C = 𝑅 \cdot 𝑖_C + 𝑢_C $$

커패시터에는 다음이 적용된다: $$i_C = C \frac{du_c}{dt} = C\dot{u}_C$$

따라서 다음은 미분방정식(DGL, ODE)의 **균형 과정(Ausgleichsvorgang)**이다.

$$U = R \cdot C \frac{du_C}{dt}+u_C$$

**2) 비동차 선형 미분방정식(imhomogene Differentialgleichung)의 풀이**

$$U = R \cdot C \frac{du_C}{dt}+u_C$$

𝑈는 $$𝑢_C$$ 또는 그 미분에 의존하지 않는다. --> **비동차 선형방정식(inhomogene DGL)**

따라서 $$u_C$$ 는 **동차 선형 미분방정식** 부분과 **비 동차적 특수해** 부분으로 나눌 수 있다.

$$u_C = u_{Ch} + u_{Cp}$$

**동차 선형 미분방정식(homogener Teil der DGL)**:  
(초기부분의 과도응답을 설명 Einschwingverhalten, wenn Erregung=0)

$$0 = R\cdot C \frac{du_{Ch}}{dt}+ u_{Ch}$$

**비동차적 특수해(partikulärer Teil der DGL)**:  
(최종 끝부분을 설명 Endzustand)

$$U = R \cdot C \frac{du_{Cp}}{dt}+ u_{Cp}$$

**3) 미분방정식(homogene Differentialgleichung)의 풀이**

**동차 선형 미분방정식(homogener Teil der DGL)**:  
(방전상태와 동일한 풀이)

$$u_{Ch} = k\cdot e^{-t/RC} = k \cdot e^{-t/𝜏}$$

**비동차적 특수해(partikulärer Teil der DGL)**:  
(DC 여기로 인해 최종 상태 𝑡→∞, 미분 = 0)

$$u_{Cp} = U$$

임시 해는 다음과 같다.

$$𝑢_C=𝑢_{Ch}+𝑢_{Cp}=𝑘\cdot e^{−𝑡/𝜏} + 𝑈$$

k를 정하기 위해서 시간 $$t = t_0$$ 일 때의 $$u_C$$ 를 이용함.

$$u_C(t=t_0) = k \cdot e^{-t_0/𝜏}+ U != 0$$

$$k = -U \cdot e^{t_0/𝜏}$$

따라서 결과는 다음과 같다:

$$u_C = -U \cdot e^{t_0/𝜏} \cdot e^{-t/𝜏} + U, \cdots t-t_0≥0$$

$$= U(1-e^{-(t-t_0)/𝜏})$$

## 01-5 충전 중 전압 곡선 Spannungsverlauf bei der Aufladung

$$u_{C} = U(1-e^{-(t-t_0)/𝜏}), \cdots t-t_0≥0$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-5_Spannungsverlauf2.jpg?raw=true" />

## 01-6 충전 중 전류 곡선 Stromverlauf bei der Aufladung

커패시터 양단의 전압은 꾸준히 증가하므로

$$
\begin{align}
& i_C = C\frac{du_C}{dt} = C\frac{d}{dt}U(1-e^{-\frac{t-t_0}{𝜏}}), \cdots t-t_0≥0 \\
& \;\;\;\; =\frac{CU}{𝜏} \cdot e^{-(t-t_0)/𝜏} = \frac{CU}{RC}\cdot e^{-(t-t_0)/𝜏} \\
& \;\;\;\; =\frac{U}{R}\cdot e^{-(t-t_0)/𝜏}
\end{align}
$$

`전류는 𝑈/𝑅 값으로 점프한 다음 다시 감소한다`

$$i_C=\frac{U}{R}\cdot e^{-(t-t_0)/𝜏}, \cdots t-t_0≥0$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-6_Stromverlauf2.jpg?raw=true" />

## 01-7 동차/비동차 선형방정식 정리

미분 방정식의 해는 두 부분으로 구성: **동차 선형 미분방정식** 부분과 **비 동차적 특수해** 부분

**동차 선형 미분방정식(homogener Teil der DGL)**:
동차 선형 미분방정식의 해는 동적 전송 동작과 안정성을 설명

$$RC\frac{du_h(t)}{dt}+u_h(t) = 0$$

**비동차적 특수해(partikulärer Teil der DGL)**:
비동차적 특수해는 고정된 최종 상태에서 전송 동작을 설명

$$RC\frac{du_p(t)}{dt}+u_p(t) = U$$

---

---

# 02 AC 전압을 사용하는 네트워크의 스위칭 프로세스 (Schaltvorgang in Netzwerken mit Wechselspannung)

## 02-1 RL회로 직렬연결 (Einschalten einer RL-Reihenschaltung)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-7_RL-Reihenschaltung.jpg?raw=true" />

균형 과정(Ausgleichsvorgang) 𝑡 = 𝑡0으로 시작

RL 시리즈 연결에 AC 전압이 적용 : $$\hat{u} cos(\omega t + \varphi_u)$$

**미분 방정식 설정**

메쉬 순환을 이용하여 다음과 같은 방정식을 얻는다.

$$
\begin{align}
&-\hat{u} cos(\omega t + \varphi_u) + u_L(t) + u_R(t) = 0 \\
&-\hat{u} cos(\omega t + \varphi_u) + L \frac{di_L(t)}{dt} + Ri_L(t) = 0
\end{align}
$$

$$𝑖_L$$ 의 해는 균질부분과 미립부분으로 구성되어 있다.

$$
\begin{align}
& i_L(t) = i_{Lh}(t) + i_{Lp}(t) \\
& L\frac{d}{dt}(i_{Lh}(t)+i_{Lp}(t)) + R(i_{Lh}(t)+i_{Lp}(t)) = \hat{u} cos(\omega t + \varphi_u)
\end{align}
$$

𝑡→∞ 경우 동차 선형 미분방정식 부분이 남아 있다.

$$L\frac{d}{dt}i_{Lp}(t)+Ri_{Lp}(t) = \hat{u} cos(\omega t + \varphi_u)$$

동차 선형 미분방정식부분:

$$L\frac{d}{dt}i_{Lh}(t)+ Ri_{Lh}(t) = 0$$

## 02-2 균일해와 특수해 (homogene und partikuläre Lösung)

### 02-2-1 (비동차적) 특수해(partikulärer Teil der DGL)

𝑡 → ∞로 고정된 경우 복소수 계산으로 특수해를 구할 수 있다.

$$u(t) = \hat{u} cos(\omega t + \varphi_u)$$

**접근방법: komplexer Zeiger**

$$\hat{u} cos(\omega t + \varphi_u) = Re\{\hat{u} e^{j(\omega t + \varphi_u)}\}$$

고정된 경우이므로 복소진폭은 다음과 같다.

$$\underline{\hat{u}} = \hat{u} e^{j(\varphi_u)}$$

전류는 다음과 같다.

$$\underline{\hat{i}}_L = \hat{i}_L e^{j(\varphi_i)}$$

<div class="notice--info">
위 부분은 전기 회로에서 복소수 표기법을 사용하여 전압과 전류의 복소진폭을 나타내고 있으며, 주파수 영역에서 신호를 분석하는 방법을 설명하고 있다. 
</div>

복소수 인피던스 계산:

$$\underline{Z} = R + j \omega L = \mid \underline{Z} \mid e^{j\varphi_Z} = \mid \underline{Z} \mid e^{j(\arctan(\frac{\omega L}{R}))}$$

$$\mid \underline{Z} \mid = \sqrt{R^2+\omega^2L^2}$$ 이므로,

$$\underline{\hat{i}}_L = \frac{\underline{\hat{u}}}{\underline{Z}} = \frac{\hat{u}}{\mid \underline{Z} \mid}e^{j(\varphi_u-\varphi_Z)}$$

$$i_L(t)=Re{\underline{\hat{i}}_L e^{j\omega t}}$$ 이기 때문에 특수해는 다음과 같다.

**(비동차적) 특수해:**

$$i_{Lp}(t) = \frac{\hat{u}}{\sqrt{R^2+\omega^2L^2}}\cos(\omega t+\varphi_i)$$

mit $$\varphi_i = \varphi_u - arg(\underline{Z}) = \varphi_u - arctan(\frac{\omega L}{R})$$

### 02-2-2 (동차적) 균일해(Homogene Lösung)

$$L\frac{d}{dt}i_{Lh}(t)+Ri_{Lh}(t) = 0$$

접근방법: $$i_{Lh}(t)=ke^{pt}$$

적용하면, $$Lpke^{pt}+Rke^{pt} = (Lp + R)ke^{pt} = 0, \cdots \cdots ke^{pt} ≠ 0$$

따라서 p는: $$Lp+R=0$$ 이어야 하므로, $$p = -\frac{R}{L}$$

균일해는 다음과 같다.

$$i_{Lh}(t) = ke^{(R/L)t} = ke^{-t/𝜏}$$

위 식에서 𝑡→∞ 인 경우, 𝜏=𝐿/𝑅가 되며, 𝜏는 시간상수가 된다.

k는 경계조건(Randbedingungen)에 의해 결정되는데

$$t = t_0$$ 일 때, $$i_L(t_0) = 0$$ 이므로,

$$
\begin{align}
& i_L(t_0) = i_{Lh}(t_0) + i_{Lp}(t_0) \\
& \;\;\;\;\;\;\;\;\; = k e^{-\frac{t_0}{𝜏}} + \hat{i}\cos(\omega t_0 + \varphi_i) = 0 \\
& \;\;\;\;\;\;k = -\hat{i}\cos(\omega t_0 + \varphi_i) \cdot e^{\frac{t_0}{𝜏}}
\end{align}
$$

### 02-2-3 Gesamtlösung

소스전압(Quellenspannung)이 $$u(t) = \hat{u}cos(\omega t + \varphi_u)$$ 일 때, 스위칭프로세스 후(𝑡≥𝑡0) 전류흐름은 다음과 같다:

$$
\begin{align}
& i_L(t) = i_{Lh}(t) + i_{Lp}(t) \\
& i_L(t) = -\hat{i}\cos(\omega t_0 + \varphi_i) e^{-\frac{(t-t_0)}{𝜏}} + \hat{i} cos(\omega t + \varphi_i)
\end{align}
$$

mit $$\varphi_i = \varphi_u - arg(\underline{Z}) = \varphi_u - archtan\frac{\omega L}{R}, \;\cdots\; 𝜏=𝐿/𝑅$$

**Gesamtlösung**

Bsp.: $$u(t) = 10 V cos(\omega t + 0), \;\; f = 50 Hz,\;\; t_0 = 2,5ms,\;\; R=100Ω$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-8_gesamtloesung.jpg?raw=true" />

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-9_Zeitkonstante.jpg?raw=true" />

### 02-2-4 혼합 소스 유도 부하(Induktive Last an Gemischter Quelle)

내부 저항이 있는 전체 소스로 변환할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-10_InduktiveLast.jpg?raw=true" />

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-11_InduktiveLast2.jpg?raw=true" />

다음과 같은 DGL값을 얻을 수 있다.

$$\frac{L}{R}\frac{d}{dt}i_L(t)+i_L(t)=\frac{u_f(t)}{R}$$

특수해(die partikuläre DGL): $$𝜏\frac{d}{dt}i_{Lp}(t)+i_{Lp}(t) = \frac{u_f(t)}{R}$$

균일해(die homogene DGL): $$𝜏\frac{d}{dt}i_{Lh}(t)+i_{Lh}(t) = 0$$

또한 $$u_f(t) = 10 V cos(\omega t)$$ 라면,

**특수해 방법 (partikulärer Lösungsansatz):**

$$i_{Lp}(t) = \hat{i}\cos(\omega t + \varphi_i)$$

---

---

# 03 여러 에너지 저장 장치가 있는 네트워크(Netzwerk mit Mehreren Energiespeichern)

네트워크에는 여러 개의 에너지 저장 장치가 포함될 수 있다. 이 경우, 각 에너지 저장 장치는 독립적인 시간상수를 가진다. 이러한 시간상수는 각 저장 장치의 내부 저항과 커패시턴스 또는 인덕턴스에 의해 결정된다.

에너지 저장 장치가 여러 개인 경우, 해당 회로의 미분 방정식은 여러 변수를 포함하게 된다. 따라서 일반적으로 각 에너지 저장 장치의 초기 조건이 필요하다.

## 03-1 DC 전압을 사용하는 RLC 시리즈 공진 회로 RLC-Reihenschwingkreis an Gleichspannung

직렬 공진 회로를 시간 𝑡 = 0에서 DC 전압 𝑈으로 전환

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-12_RLC-Reihenschwingkreis.jpg?raw=true" />

## 03-2 DGL 설정(Aufstellen der DGL)

메시 순환(Maschenumlauf):

$$𝑢_L+𝑢_R+𝑢_C=𝑈$$

각각 다음 관계가 적용:

$$i = C\frac{du_C}{dt}, \;\;\; u_R=R\cdot i=RC\frac{du_C}{dt}, \;\;\; u_L=L\frac{di}{dt}=LC\frac{d^2u_C}{dt^2}$$

적용 후 결과는 다음과 같음:

$$LC\frac{d^2u_C}{dt^2}+RC\frac{du_C}{dt}+u_C = U$$

미분 방정식으로 정리(Differenzialgleichung in Normalform:):

$$\frac{d^2u_C}{dt^2}+\frac{R}{L}\frac{du_C}{dt}+\frac{1}{LC}u_C = \frac{U}{LC}$$

## 03-3 특수해(partikuläre Lösung)

• 입력전압 𝑈은 직류전압이다.

• 𝑡→∞ 인 경우:

– 𝐿는 단락으로 대체됨.(𝐿 wird durch Kurzschluss ersetzt) << 저항이 없는것과 마찬가지  
– 커패시터 양단의 전압은 𝑈  
– 전류 𝑖 사라짐

• 균일해는 다음과 같다.

$$u_cp(t) = U, \;\;\;\;\;\; i_{Lp}(t)=0$$

종합하면,

$$u_C(t) = u_{Ch}(t) + U$$

## 03-4 균일해(homogene Lösung)

$$
\begin{align}
u_{Ch}(t) = ke^{𝑝t} \; in \; \frac{d^2u_C}{dt^2}+\frac{R}{L}\frac{du_C}{dt} + \frac{1}{LC}u_C = 0 &\\
𝑝^2k e^{𝑝t}+\frac{R}{L}pke^{𝑝t} + \frac{1}{LC}ke^{𝑝t} = 0 &\\
\left( 𝑝^2+\frac{R}{L}p + \frac{1}{LC} \right) \cdot k e^{𝑝t} = 0&
\end{align}
$$

**die charakteristische Gleichung:**

$$𝑝^2+\frac{R}{L}𝑝+\frac{1}{LC}=0$$

다음과 같은 해(고유값\_Eigenwerte)가 있다:

$$𝑝_1 = -\frac{R}{2L}+\sqrt{\frac{R^2}{4L^2}-\frac{1}{LC}}$$

$$𝑝_2 = -\frac{R}{2L}-\sqrt{\frac{R^2}{4L^2}-\frac{1}{LC}}$$

• `감쇠 상수(Abklingkonstante)`:

$$𝛿 = \frac{R}{2L}$$

• `공진 각 주파수(Resonanzkreisfrequenz)`:

$$𝜔^2_0 = \frac{1}{LC}$$

따라서 다음과 같이 바꿀 수 있다:

$$𝑝_1 = -𝛿 + \sqrt{𝛿^2-\omega^2_0}$$

$$𝑝_2 = -𝛿 - \sqrt{𝛿^2-\omega^2_0}$$

`루트에 필요한 경우들의 구분 Fallunterscheidung für die Wurzel notwendig`

<div class="notice--info">
<b>감쇠 상수(Abklingkonstante) 𝛿</b>는 시간이 지남에 따라 진동의 진폭(amplitude)이 감소하는 정도를 나타내는 상수다. 이 값은 회로의 저항과 인덕턴스에 의해 결정된다.<br>
<br>
<b>공진 주파수(Resonanzkreisfrequenz) 𝜔</b>는 회로가 진동을 가장 잘 유지할 수 있는 주파수다. 이 값은 회로의 캐패시터와 인덕턴스에 의해 결정된다. 공진 주파수에서 회로의 저항이 작을수록(또는 0에 가까울수록), 진폭은 커진다.<br>
</div>

## 03-5 주기적인 경우 (Periodischer Fall)

$$𝛿^2<𝜔^2_0$$ 인 경우, ($$\Rightarrow \frac{R^2}{4L^2}-\frac{1}{LC}<0$$ )

mit: $$p_1=-𝛿+j𝜔_d, \;\; p_2=-𝛿-j𝜔_d, \;\; 𝜔_d = \sqrt{𝜔^2_0-𝛿^2}  $$

**균일해 Homogene Lösung**:

$$𝑢_{Ch}(𝑡)=(𝑘_1\cos(𝜔_d𝑡)+𝑘_2\sin(𝜔_d𝑡))e^{−𝛿𝑡}$$

**종합해 Gesamte Lösung**:

$$𝑢_{C}(𝑡)=(𝑘_1\cos(𝜔_d𝑡)+𝑘_2\sin(𝜔_d𝑡))e^{−𝛿𝑡} + 𝑈$$

## 03-6 비주기적 특수한 경우 (Aperiodischer Grenzfall)

$$𝛿^2=𝜔^2_0$$ 인 경우, ($$\Rightarrow \frac{R^2}{4L^2}-\frac{1}{LC}=0$$ )

mit: $$p_1=p_2=-𝛿$$

**균일해 Homogene Lösung**:

$$𝑢_{Ch}(𝑡)=(𝑘_1+𝑘_2𝑡)e^{−𝛿𝑡}$$

**종합해 Gesamte Lösung**:

$$𝑢_{C}(𝑡)=(𝑘_1+𝑘_2𝑡)e^{−𝛿𝑡} + 𝑈$$

## 03-7 비주기적인 경우 (Aperiodischer Fall)

## 03-8 상수 결정 (Bestimmung der Konstanten)

### 03-8-1 주기적인 경우 (Periodischer Fall)

### 03-8-2 비주기적 특수한 경우 (Aperiodischer Grenzfall)

### 03-8-3 비주기적인 경우 (Aperiodischer Fall)

## 03-9 시간에 따른 전류 및 전압 (Zeitabhängiger Strom und Spannungsverlauf)

**Periodischer Fall**

**Aperiodischer Grenzfall**

**Aperiodischer Fall**

## 03-10 2차 미분 방정식의 실용적인 접근(Praktisches Vorgehen für DGL 2. Ordnung)\*\*\*

1. 미분방정식 설정 Aufstellen der Differenzialgleichung

2. 특수해 결정 Bestimmen der partikulären Lösung

3. 균일해 결정 Bestimmen der homogenen Lösung

&ensp;&ensp;&ensp;– 접근 방법 Ansatz machen  
&ensp;&ensp;&ensp;– 미분 결정 Ableitungen bestimmen  
&ensp;&ensp;&ensp;– 특성 방정식 결정 charakteristische Gleichung aufstellen  
&ensp;&ensp;&ensp;– 고유값 결정 Bestimmung der Eigenwerte  
&ensp;&ensp;&ensp;– Fallunterscheidung

4. 상수 결정 Bestimmen der Konstanten

## 03-11 일반적인 ODE 설정 (Aufstellen der DGL im Allgemeinen)

• 𝑛독립 에너지 저장소는 𝑛1차 미분방정식을 생성한다.  
• 종속 에너지 저장소는 직렬 연결된 유도성 또는 병렬 연결된 용량이며 결합될 수 있다.

• 모든 1차 ODE를 요약하면 𝑛차 ODE가 생성된다.

• 𝑦(𝑡)는 네트워크에서 상태변수로 정의된다.

• ODE 𝑛차

$$\frac{d^n}{dt^n}y(t)+a_{n-1}\frac{d^{n-1}}{dt{n-1}}y(t)+\cdot+a_1\frac{d}{dt}y(t)+a_0y(t) = f(t)$$

<div class="notice--info">
예를 들어, 전기회로에서 2개의 에너지 저장소(커패시터, 인덕턴스)가 있는 경우를 생각해보자.<br>
<br>
커패시터과 인덕턴스는 각각 전하와 자기장 에너지를 저장하는데 사용되는 구성 요소다. 이러한 구성 요소들은 전기회로에서 중요한 역할을 하며, 전류와 전압의 변화를 조절하고 제어한다.<br>
<br>
만약 전기회로에 용량과 인덕턴스 두 개의 에너지 저장소가 있다면, 이는 각각 1차 미분 방정식으로 표현될 수 있다. 즉, 전하와 자기장 에너지의 변화율은 각각 용량과 인덕턴스의 값에 따라 변화한다.<br>
<br>
이러한 두 개의 1차 미분 방정식을 조합하면, 전기회로 전체의 동작을 나타내는 미분 방정식을 얻을 수 있다. 이렇게 얻은 미분 방정식은 상태변수로 정의된 전압, 전류, 전하 등과 같은 다양한 변수들을 포함할 수 있으며, 시간의 변화에 따라 이러한 변수들이 어떻게 변하는지를 설명할 수 있다.<br>
</div>

## 03-12 일반적인 특수해 Partikuläre Lösung im Allgemeinen

## 03-13 일반적인 균일해 Homogene Lösung im Allgemeinen

## 03-14 일반적인 특성 방정식 Charakteristische Gleichung im Allgemeinen

## 03-15 일반적인 고유값 및 상수 Eigenwerte und Konstanten im Allgemeinen

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
