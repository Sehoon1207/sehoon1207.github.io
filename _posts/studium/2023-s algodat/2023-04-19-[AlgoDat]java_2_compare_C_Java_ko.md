---
layout: single
title: "[AlgoDat]C와 Java의 비교"
folder: "AlgoDat"
categories:
  - algoDat

tags: [blog, algoDat, java]

author_profile: true
sidebar:
  nav: "sidebar-category"

# toc: true
# toc_label: "목록"
# toc_icon: "bars"
# toc_sticky: true
classes: wide

lang: de
lang-ref: multilingual

date: 2023-04-19
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>

<pre>
OS    : Window
Editor: IntelliJ IDEA</pre>
</div>

객체 지향(Java) 프로그래밍 언어와 절차적(C) 프로그래밍 언어 간의 개념적 차이 외에도 C에는 JVM, 자동 메모리 관리 등이 없습니다. 다음은 차이점을 나타낸 표입니다.

| Thing                                           | C                                                                                        | Java                                                                                                                             |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 언어의 종류                                     | 기능 지향적                                                                              | 객체 지향                                                                                                                        |
| 기본 프로그래밍 단위                            | function                                                                                 | class = ADT                                                                                                                      |
| 소스 코드의 이식성                              | 규율로 가능                                                                              | yes                                                                                                                              |
| 컴파일된 코드의 이식성                          | 아니요, 각 아키텍처에 대해 다시 컴파일합니다.                                            | 예, 바이트코드는 "한 번 작성하고 어디서나 실행"입니다.                                                                           |
| 보안                                            | 제한된                                                                                   | 언어에 내장                                                                                                                      |
| 편집                                            | gcc hello.c ....기계어 코드 생성                                                         | javac Hello.java ....JVM(Java Virtual Machine Language) 바이트코드 생성                                                          |
| Math library 연결                               | gcc -lm calculate.c                                                                      | no special flags needed                                                                                                          |
| joint compilation                               | gcc main.c helper1.c helper2.c                                                           | javac Main.java - any dependent files are automatically re-compiled if needed                                                    |
| `execution`                                     | `a.out loads and executes program`                                                       | `java Hello interprets byte code`                                                                                                |
| `hello, world`                                  | `#include<stdio.h> int main(void) { printf("Hello\n"); return 0;}`                       | `public class HelloWorld {public static void main(String[] args) {System.out.println("Hello");}}`                                |
| integer types                                   | int usually 32 bit 2's complement; long usually 32 bit 2's complement                    | int is 32 bit 2's complement; long is 32 bit 2's complement                                                                      |
| floating point types                            | float usually 32 bit 2's complement; double usually 32 bit 2's complement                | float is 32 bit IEEE 754 binary floating point; double is 64 bit IEEE 754                                                        |
| `boolean type`                                  | `use int: 0 for false, nonzero for true`                                                 | `boolean is its own type - stores value true or false`                                                                           |
| character type                                  | char is usually 8 bit ASCII                                                              | char is 16 bit UNICODE                                                                                                           |
| for loops                                       | for (i = 0; i < N; i++)                                                                  | for (int i = 0; i < N; i++)                                                                                                      |
| `array declarations `                           | `int _a = malloc(N _ sizeof(\*a));`                                                      | `int[] a = new int[N];`                                                                                                          |
| `array size`                                    | `arrays don't know their own size`                                                       | `a.length`                                                                                                                       |
| `strings`                                       | `'\0'-terminated character array `                                                       | `built-in immutable String data type`                                                                                            |
| `accessing a library`                           | `#include <stdio.h>`                                                                     | `import java.io.File;`                                                                                                           |
| `accessing a library function`                  | `#include "math.h" x = sqrt(2.2); all function and variables names are global`           | `x = Math.sqrt(2.2); functions have different namespaces`                                                                        |
| printing to standard output                     | printf("sum = %d", x);                                                                   | System.out.println("sum = " + x);                                                                                                |
| formatted printing                              | printf("avg = %3.2f", avg);                                                              | System.out.printf("avg = %3.2f", avg)                                                                                            |
| reading from stdin                              | scanf("%d", &x);                                                                         | Java library support, but easier to use our library int x = StdIn.readInt();                                                     |
| `memory address`                                | `pointer`                                                                                | `reference`                                                                                                                      |
| manipulating pointers                           | \*, &, +                                                                                 | no direct manipulation permitted                                                                                                 |
| functions                                       | int max(int a, int b)                                                                    | public static int max(int a, int b)                                                                                              |
| pass-by-value                                   | primitive data types, structs, and pointers are passed by value; array decays to pointer | all primitive data types and references (which includes arrays), are passed by value                                             |
| `defining a data structure`                     | `struct`                                                                                 | `class - key difference is language support for defining methods to manipulate data`                                             |
| accessing a data structure                      | a.numerator for elements                                                                 | a.numerator for instance variables, c = a.plus(b) for methods                                                                    |
| pointer chasing                                 | x->left->right                                                                           | x.left.right                                                                                                                     |
| `allocating memory`                             | `malloc`                                                                                 | `new`                                                                                                                            |
| `de-allocating memory`                          | `free`                                                                                   | `automatic garbage collection`                                                                                                   |
| memory allocation of data structures and arrays | heap, stack, data, or bss                                                                | heap                                                                                                                             |
| buffer overflow                                 | segmentation fault, core dump, unpredicatable program                                    | checked run-time error exception                                                                                                 |
| declaring constants                             | const and #define                                                                        | final                                                                                                                            |
| `variable auto-initialization`                  | `not guaranteed`                                                                         | `instance variables (and array elements) initialized to 0, null, or false, compile-time error to access uninitialized variables` |
| data hiding                                     | opaque pointers and static                                                               | private                                                                                                                          |
| interface method                                | non-static function                                                                      | public method                                                                                                                    |
| `data type for generic item`                    | `void \`                                                                                 | `Object`                                                                                                                         |
| casting                                         | anything goes                                                                            | checked exception at run-time or compile-time                                                                                    |
| demotions                                       | automatic, but might lose precision                                                      | must explicitly cast, e.g., to convert from long to int                                                                          |
| polymorphism                                    | union                                                                                    | inheritence                                                                                                                      |
| overloading                                     | no                                                                                       | yes for methods, no for operators                                                                                                |
| graphics                                        | use external libraries                                                                   | Java library support, use our standard drawing library                                                                           |
| `null`                                          | `NULL`                                                                                   | `null`                                                                                                                           |
| enumeration                                     | enum                                                                                     | typesafe enum                                                                                                                    |
| preprocessor                                    | yes                                                                                      | no                                                                                                                               |
| `variable declaration`                          | `at beginning of a block`                                                                | `before you use it`                                                                                                              |
| `variable naming conventions`                   | `sum_of_squares`                                                                         | `sumOfSquares`                                                                                                                   |
| `commenting`                                    | `/* */`                                                                                  | `/* */ or //`                                                                                                                    |
| `file naming conventions`                       | `stack.c, stack.h`                                                                       | `Stack.java - file name matches name of class`                                                                                   |
| callbacks                                       | pointers to global functions                                                             | use interfaces for commmand dispatching                                                                                          |
| variable number of arguments                    | varargs                                                                                  | String ...                                                                                                                       |
| assertions                                      | assert                                                                                   | assert                                                                                                                           |
| exit and return value to OS                     | exit(1)                                                                                  | System.exit(1)                                                                                                                   |

Quelle: <https://introcs.cs.princeton.edu/java/faq/c2java.html>

---
