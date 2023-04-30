---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[Java-c] 01 HelloWorld" #제목 확인
folder: "java" #폴더 확인
categories:
  - java #카테고리 확인

tags: [blog, java] #태그 확인

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "list"
toc_icon: "bars"
toc_sticky: true
classes: wide

lang: ko
lang-ref: multilingual

# use_math: true    #숫자 사용 확인

date: 2023-04-30
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
Quellen für das Schreiben oder den Inhalt befinden sich normalerweise ganz unten.<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
글이나 내용의 출처는 보통 하단에 있습니다.<br>
<b>
<pre>
OS    : Window
Editor: IntelliJ IDEA 2023.1</pre></b>
</div>

---

# 00 IntelliJ IDEA

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/Java/imgs/01_c_IDEA.jpg?raw=true" width="1000px"/>

여기서 사용하는 에디터로는 IntelliJ IDEA를 사용하려고 한다. IntelliJ IDEA는 Jetbrains에서 개발한, 자바와 관련된 다양한 프로그래밍 언어를 지원하는 통합 개발 환경(IDE)이다. Java, Kotlin, Groovy, Scala 등 여러 언어를 지원하며, 코드 작성, 디버깅, 테스트, 빌드, 배포 등 다양한 작업을 수행할 수 있다. IntelliJ IDEA는 코드 자동 완성, 리팩토링, 디버깅 도구, 코드 검사 등 다양한 기능을 제공하여 개발자가 효율적으로 개발할 수 있도록 도와준다. 또한 플러그인 시스템을 통해 다양한 확장 기능을 지원하며, Git, SVN, Mercurial 등의 버전 관리 시스템을 통합하여 사용할 수 있다. IntelliJ IDEA는 유료 라이선스와 무료 커뮤니티 버전이 제공되며, 다양한 운영 체제에서 사용할 수 있다.

더 자세한 내용은 [IntelliJ IDEA 사이트](https://www.jetbrains.com/idea/)에서 확인하자.

---

# 01 HelloWorld!

자바는 Sun Microsystems에서 1995년에 출시된 프로그래밍 언어다. Java는 단순하고 이식 가능하며 안전하고 강력한 특징을 가지고 있다. Java 코드는 Java Virtual Machine을 통해 여러 운영 체제 및 플랫폼에서 실행될 수 있다. Java의 슬로건은 "Write Once, Run Everywhere"이다. 프로그래밍 언어는 구문(java가 이해하는 특정 명령)으로 이루어져 있으며, 구문을 작성하여 컴퓨터에서 실행되는 프로그램을 만든다.

다음 예제 파일을 실행시켜보자.

```java
public class C01_HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

코드를 간단하게 살펴보면 다음과 같다.

각 파일에는 파일 이름을 딴 하나의 기본 클래스가 있다. (클래스에 대해서는 추후에 더 알아보고 당장은 단일 개념으로 생각하자.)클래스 내부에는 프로그램 작업을 나열하는 main() 메서드가 있다. 메서드의 시작과 끝을 표시하기 위해 중괄호를 사용한다. 이 메서드는 public, static, void 등의 구문을 포함한다. String[] args는 프로그램에 전달하려는 정보의 자리 표시자다. print 문을 사용하여 화면에 텍스트를 출력할 수 있다.

---

# 02 출력문 (Print Statements)

Print문을 사용하면 화면에 지정된 정보를 출력한다(출력 터미널이라고도 함).
print문에 함께 사용되는 코드들을 살펴보면...,  
**System**은 프로그램에 유용한 도구가 포함된 내장 Java 클래스다.  
**out**은 "출력"의 줄임말이다.  
**println**은 "print line"의 줄임말이다.  
프로그램이 값을 출력한 후 화면에 새 줄을 생성하기를 원할 때마다 System.out.println()을 사용할 수 있다. 또한 System.out.print()를 사용하여 정보를 출력할 수도 있다. 하지만 System.out.println()과 달리 이 유형의 print 문은 모든 것을 같은 줄에 출력한다.

따라서 출력문을 쓸 때는 이전에 출력문을 어떤 것을 사용했는지에 따라 텍스트가 바로 옆에 이어서 출력이 될 것인지 또는 다음 줄에 출력이 될 것인지 정해진다.

이와 관련해서 예제를 보면 다음과 같다.

\<input>

```java
public class C03_HideAndSeek {
    public static void main(String[] args) {
        System.out.println("3 seconds before start. I will find U.");
        System.out.print("Three...");
        System.out.print("Two...");
        System.out.println("One...");
        System.out.println("Staaart! go, go, go!!");
    }
}
```

\<output>

```
3 seconds before start. I will find U.
Three...Two...One...
Staaart! go, go, go!!
```

# 03 주석(Comment)

코드를 읽는 사람에게 주석과 메모를 작성할 수도 있다. 이러한 주석은 실행되지 않으므로 주석 내에 유효한 구문이 필요없다.

주석이 짧으면 한 줄 구문을 사용: `//`  
주석이 길면 여러 줄 구문을 사용: `/* 주석내용 */`

다른 유형의 주석 옵션은 `/** 주석내용 */` 로 표시되는 Javadoc 주석이 있다. Javadoc 주석은 API(Application Programming Interface)에 대한 문서를 작성하는 데 사용된다. Javadoc 주석은 일반적으로 필드, 메서드 및 클래스 선언 전에 작성된다.

다음 예제를 실행시켜보자.

```java
public class C04_Timeline {
    public static void main(String[] args) {
        System.out.println("Hello Java!");

        System.out.println("You were born in 1995");

        //Sun Microsystems announced the release of Java in 1995

        System.out.println("You were created by James Gosling");
        /*
        James Gosling is a Canadian engineer who
        created Java while working at Sun Microsystems.
        His favorite number is the square root of 2!
        */
                System.out.println("You are a fun language!");
    }
}
```

---

# 04 컴파일 및 실행 (Compiling)

Java는 컴파일된 프로그래밍 언어다. 즉, .java 파일에 작성하는 코드는 컴퓨터의 Java Virtual Machine에서 실행되기 전에 컴파일러에 의해 바이트 코드로 변환된다. 따라서 컴파일러는 인간에게 친숙한 프로그래밍 언어를 컴퓨터가 실행할 수 있는 다른 프로그래밍 언어로 번역하는 프로그램인 것이다.

IntelliJ IDEA를 사용하면 재생버튼으로 간단하게 실행 할 수 있지만, 터미널 명령으로도 컴파일할 수 있다.

```
javac example.java
```

터미널에 위와 같이 입력하면 아무런 오류가 없을 경우 example.class파일이 생성된다.  
오류가 없고 파일이 잘 생성되었다면 다음과 같이 입력한다.

```
java example
```

그러면 example.class 파일이 실행되고 그 결과가 출력된다.

<div class="notice--danger">
<b>컴파일에 실패할 경우</b><br>
<br>
실패한 컴파일은 오류 목록을 생성해서 보여준다. 오류가 수정되고 컴파일 명령이 다시 실행될 때까지 .class 파일이 만들어지지 않는다.
</div>

---

Quelle(text): Lessen, Learn Java [codecademy](https://www.codecademy.com/learn/learn-java)  
Quelle(image):  
Quelle(code): Lessen, Learn Java [codecademy](https://www.codecademy.com/learn/learn-java)
