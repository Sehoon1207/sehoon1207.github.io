---
layout: single
title: "[ELNW-a] 03 Schaltvorgang 문제"
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

date: 2023-05-23
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
</div>

# 00 (기본 내용 및 공식)

## 00-0 def.Ausgleichvorgänge

> Ausgleichvorgänge: Transie bzw. dynamischer übergang von einem stationären Zustand in den nächsten stationären Zustand

Ausgleichvorgänge은 한 정상 상태에서 다른 정상 상태로의 전환 과정 또는 동적인 전환 과정을 의미한다.

> ⇒ Veränderung von Zustandsgrößen, welche die gesamtheit eines physikalischen Systems beschreiben.
> sind die Zustandsgrößen auflauf, ist das physikalische System im gleichgewicht.

이는 전체 물리 시스템을 설명하는 상태 변수의 변화와 관련이 있다. 상태 변수가 안정적인 경우, 물리 시스템은 균형에 있는 것이다.

> ⇒ $$U_C \;\&\; i_L$$

본 내용에서, 상태 변수는 전압과 전류 ($$U_C \;\&\; i_L$$)에 해당한다.

> ⇒ Die Anzahl der unabhängigen Zustandsgrößen definiert Ordnung eines Systems und somit Ordnung des Ausgleichvorgangs. Sie beschreiben ein technisches System und sind ein indikator für unabhängige Energiespeicher.

독립적인 상태 변수의 수는 시스템의 차수 및 변환 과정의 차수를 정의하며, 독립적인 에너지 저장소를 나타내는 지표로 사용된다.

## 00-1 어디에 에너지가 저장될까?

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_schaltung.jpg?raw=true" width="500px"/>

**① Kondensator**

- ustisches Feld

**② Spule**

- magnetisches Feld

$$
\begin{flalign}
& ω_e=\frac{1}{2}\cdot C\cdot u^2\;,\;Q=c\cdot u &&\\
\\
& ω_m=\frac{1}{2}\cdot L\cdot J^2 &&\\
\end{flalign}
$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_schaltung2.jpg?raw=true" width="500px"/>

$$
\begin{flalign}
& Q = C \cdot u &&\\
\\
& Q(t) = \int_0^{t_0}J(t)dt&&\\
\end{flalign}
$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_schaltung3.jpg?raw=true" width="500px"/>

> `Maschenregel` gilt, sowie Stätigkeit der Spannung des Kondensators

메쉬 규칙과 커패시터 전압의 안정성이 적용

$$
\begin{flalign}
& -U_0+U_R+U_C=0 &&\\
& ⇒ U_0 = U_R + U_C &&\\
\end{flalign}
$$

> Für Strom gilt ohmschesgesetz, dann aber springen.

전류에는 옴의 법칙이 적용된다. 하지만 그 값이 (그래프에서 보면) 갑자기 튀어 오르는 것을 볼 수 있다.

> ① $$i_C = \frac{U_0}{R}$$ Spannung muss sich ergfam Kondensator aufbauen
> ② Elektronen fließen auf heitsplaken, Spannung steigt
> ③ Gleichgewicht $$U_0 = U_C$$ somit $$U_R=0$$ ⇒ kein Stromfluss mehr

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-1_theorie1.png?raw=true" />

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-2_theorie2.png?raw=true" />

$$
\begin{flalign}
& 𝛕 = R\cdot C : 𝛕 = \frac{L}{R} &&\\
& U_C(t)=U_0\cdot(1-e^{-\frac{1}{R\cdot C}\cdot t}) &&\\
\end{flalign}
$$

# 01 밸런싱 프로세스의 기초 Grundlagen zu Ausgleichsvorgängen

## 01.1 이상적인 DC 전압 소스에서 충전되는 커패시터 (Kondensatoraufladung an idealer Gleichspannungsquelle)

> In der Schaltung wird zum Zeitpunkt $$t = 0$$ der Schalter S geschlossen. Geben Sie den zeitlichen Verlauf für $$i_C$$ und $$u_C$$ an! Begründen Sie mit diesem, warum ein idealer Kondensator und eine ideale Spannungsquelle nie alleine in einer Masche vorkommen können.

회로에서 스위치 S는 시간 $$t = 0$$ 에서 닫힙니다. $$i_C$$ 및 $$u_C$$ 에 시간 코스를 제공하십시오! 또한 이것을 사용하여 이상적인 커패시터와 이상적인 전압 소스가 메시에 단독으로 나타날 수 없는 이유를 설명하십시오.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.1.jpg?raw=true" />

**Lsg:**

**wenn S offen:** $$i_C=0,\;u_C=0$$  
**wenn S schließt:** $$i_C=C\frac{du_C}{dt}, \;\; dt = 0 ⇒ i_C=∞$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.1-ant.jpg?raw=true" width="300px"/>

$$
\begin{flalign}
& V_C-V_0 = 0, \;\; u_C = U_0 &&\\
\end{flalign}
$$

**wenn S geschlossen(t>0):** $$u_C=u_0, \; u_C=C\frac{du_C}{dt}=0, \;dt = 0$$  
⇒ unendlicher Strom würde die Bauteile zerstören

## 01.2 이상적인 DC 전압 소스에서 저항을 통해 커패시터 충전 (Kondensatoraufladung über einenWiderstand an idealer Gleichspannungsquelle)

> Geben Sie den zeitlichen Verlauf für $$i_C$$ und $$u_C$$ an!

$$i_C$$ 및 $$u_C$$에 시간 코스를 제공하십시오!

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.2.jpg?raw=true" />

$$u_C = u(1-e^{-(t-t_0)/𝛕})$$  
⇒Spannungsverlauf bei der Aufladung

**wenn S offen:** $$i_C = 0, \; u_R = R \cdot i_C = 0 \;\cdot\; (i_C=0), \; u_C=0$$

**wenn S geschlossen:** $$ u_C = u_0 (1-e^{-t/R\cdot C}), \; u=u_0, \; t_0=0, \; 𝛕:=R\cdot C[Ω\cdot\frac{s}{Ω}]$$

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-3_antwort12.png?raw=true" />

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03-4_antwort12.png?raw=true" />

## 01.3 이상적인 DC 전압 소스에서 저항과 코일을 통해 충전되는 커패시터 (Kondensatoraufladung über einen Widerstand und eine Spule an idealer Gleichspannungsquelle)

> Geben Sie den zeitlichen Verlauf für $$i_C$$ und $$u_C$$ an!

$$i_C$$ 및 $$u_C$$에 시간 코스를 제공하십시오!

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.3.jpg?raw=true" />

**Lsg:**

$$
\begin{flalign}
& i_R = i_L = i_C &&\\
\end{flalign}
$$

(zeitliche Lösung: Siehe Folie 47)

**aperiodischen Grenzfall:**

**① t < 0:**

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.3a.jpg?raw=true" width="300px"/>

konstante Strom wirkt Spule wie Kurzschluss

Kondensatoraufladung: u_C(t=0) = 0V i_C=0

**② t = ∞:**

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.3b.jpg?raw=true" width="300px"/>

$$
\begin{flalign}
& i_C = 0, u_R = R \cdot i_C = 0 , \; \cdots \; i_C = 0 &&\\
& u_0 - u_C - u_R = 0, \; \cdots \; u_C=u_0 &&\\
\end{flalign}
$$

**③ t = 0:**

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.3c.jpg?raw=true" width="300px"/>

$$
\begin{flalign}
& u_R = R\cdot i_C, \; u_L = L\cdot\frac{di_C}{dt}, \; i_C = C\cdot\frac{du_C}{dt} &&\\
& u_C(t=0) ⇒ i_C = C\frac{du_C}{dt} = 0A ⇒ u_R = R\cdot i_C \;\cdots\; (dt = 0,\; i_C = 0A) &&\\
& u_0 - u_L - u_C - u_R = 0 ⇒ u_0 = u_L \;\cdots\; (u_C = 0, u_R = 0) &&\\
& u_L = L\cdot\frac{di_C}{dt} ⇒ \frac{di_C}{dt} = \frac{u_C}{L} = \frac{u_0}{L} > 0 ⇒ i_C \uparrow \uparrow &&\\
\end{flalign}
$$

**④ 0 < t < ∞:**

$$
\begin{flalign}
& i_C \uparrow\uparrow ⇒ u_R = R\cdot i_C ⇒ u_R \uparrow\uparrow, \;\; \frac{du_C}{dt}=\frac{i_C}{C}>0 ⇒ u_C \uparrow\uparrow &&\\
& u_L \downarrow\downarrow, \; \frac{di_c}{dt}=\frac{u_C}{L} \downarrow ⇒ i_C \uparrow &&\\
& u_L = 0 ⇒ \frac{di_c}{dt}=0 ⇒ i_c \; maximal &&\\
& u_L < 0 ⇒ \frac{di_c}{dt}=\frac{u_L}{L}<0 ⇒ i_c \downarrow\downarrow &&\\
\end{flalign}
$$

## 01.4 Ausgleichsvorgängen의 질적 고찰 II (Qualitative Betrachtung von Ausgleichsvorgängen II)

> Geben Sie den qualitativen Verlauf von $$u_C$$ für einen aperiodischen Ausgleichsvorgang ungefähr an, wenn der Schalter $$S_2$$ zum Zeitpunkt $$t =t_1$$ geöffnet wird. Geben Sie anschließend den Verlauf von $$u_C$$ für einen aperiodischen Ausgleichsvorgang ungefähr an, wenn die Schalter $$S_1$$ und $$S_2$$ zum Zeitpunkt $$t = t_2$$ geschlossen werden.

$$t =t_1$$ 시점에 $$S_2$$ 스위치가 열렸을 때 대략 비주기적 과도 프로세스에 대해 $$u_C$$ 의 질적 과정을 제공하십시오. 그런 다음 $$t = t_2$$ 시점에서 $$S_1$$ 및 $$S_2$$ 스위치가 닫힐 때 대략 비주기적 과도 프로세스에 대한 $$u_C$$ 과정을 제공합니다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/studium/2023-s%20elnw/img/03_schaltvorgang/03_a-1_1.4.jpg?raw=true" />

$$U_0 = 1V,\; I_1=2A\;, R_1=4Ω,\; R_2=1Ω$$

**Lsg:**

aperiodischer Ausgleichsvorgang

mehrere Schaltvorgänge

① $$ t < t_1: u_C = -3V $$  
② $$ t_1 ≤ t ≤ t_2: u_C=-3V $$  
③ $$ t\rightarrow ∞: u_C = -2.6V $$

---

---

Quelle(text):  
Groundlagen zur Elektrotechnik, Technische Hochschule Mittelhessen [Pdf datei](https://www.thm.de/iem/images/user/novender-978/get.pdf)  
[ElectronicsTutorials](https://www.electronics-tutorials.ws/accircuits/complex-numbers.html)
매쉬법칙을 이용한 해석법, [서민상의 공학과 실무 강의실](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=seo0511&logNo=10128876195)

Quelle(image):  
Elektrische Netzwerke TU-Berlin [pdf datei](https://isis.tu-berlin.de/pluginfile.php/2756135/mod_resource/content/10/1_Grundlagen_Zeiger-SENSE-2023.pdf)  
StuDoc [pdf datei](https://www.studocu.com/de/course/technische-universitat-berlin/elektrische-netzwerke/124295)

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->

$$
$$
