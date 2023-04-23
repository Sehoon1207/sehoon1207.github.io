---
layout: single
title: "[AlgoDat]Grundlagen der Algorithmen und Datenstrukturen"
folder: "algoDat"
categories:
  - algoDat

tags: [blog, algoDat, java]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "목록"
toc_icon: "bars"
toc_sticky: true
classes: wide

lang: de
lang-ref: multilingual

date: 2023-04-19
---

Während ich das PDF-Material studiere,
schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.

#### Was ist java?

> Java, das als Softwareprojekt für Unterhaltungselektronik begann, wurde als Programmiersprache für das Internet entwickelt.
> Java ist `Open Source` und eine der am weitesten verbreiteten Programmiersprachen.
> Java ist eine sichere und einfache `objektorientierte Programmiersprache`, die unabhängig von Betriebssystemen und Plattformen ausgeführt werden kann.
> Java wurde durch das Konzept von `JVM (Java Virtual Machine)` implementiert.
> Die JVM bildet eine `virtuelle Maschine` für jedes aufgerufene Java-Programm.

#### Funktionen von Java

> 1. Alle Programme werden zur <u>Laufzeit überprüft (Bytecode Verifier)</u> und die Speicherverwaltung ist bereits in die JVM integriert.
> 2. Bekannte Zeiger in C oder C++ werden im Allgemeinen nicht unterstützt, <u>Java verwendet stattdessen Referenzen</u>.
> 3. Andere <u>Sicherheitsmaßnahmen</u> sind in die Programmiersprache eingebaut, wie z. B. die Möglichkeit, den Zugriff auf bestimmte Teile des Programms einzuschränken.
> 4. Mit der hervorragenden Leistung von Java gibt es eine `JIT (Just-In-Time)`-Kompilierung, die Bytecode in Maschinencode (Maschinencode) umwandelt, während das Programm läuft. Damit lässt sich beispielsweise die Laufzeit dynamisch optimieren</u>, indem Variablen, die ihren Wert nicht mehr ändern, als Konstanten behandelt werden.

---

**Stichworte: Open Source, Objektorientierte Programmiersprache, Java Virtual Machine (JVM), Virtuelle Maschine, Just-In-Time (JIT)**

`Open Source`: Open-Source-Software bezieht sich auf Software, die eine Lizenz erfüllt, die jeder sehen und verwenden kann, indem er den Quellcode öffnet.

`Objektorientierte Programmierung`: Auch als imperative Programmierung bekannt. Die objektorientierte Programmierung sieht jede der zahlreichen Rollen, die für die Programmierung erforderlich sind, als Objekte und drückt sie als ihre Interaktionen aus. Abstrakte Daten zur Steuerung der Systemkomplexität durch Vererbung, polymorphe Konzepte und dynamische Bindung. Weitere Details werden später geklärt.

`JVM (Java Virtual Machine)`: Sie können es sich als eine virtuelle Maschine zum Ausführen von Java vorstellen, also einen Computer. Daher kann es unabhängig vom Betriebssystem ausgeführt werden.

`Virtuelle Maschine`: Mit anderen Worten, ein Computer.

`JIT (Just-In-Time)`: Der Fluss von Java-Code > Bytecode > Maschinensprache konvertiert die in Java eingegebene Sprache, damit der Computer sie verstehen kann. JIT bezieht sich auf den Prozess der Konvertierung von Bytecode > Maschinensprache. es wird JIT (Just-In-Time) genannt, weil die Konvertierung gleichzeitig mit dem Programmablauf erfolgt.

---

Quelle: Einführung in Java für AlgoDat, Vera Röhr und Benjamin Blankertz
