---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[AlgoDat-p] 01 Start mit Java, Laufzeit (ko)" #제목 확인
folder: "AlgoDat" #폴더 확인
categories:
  - algoDat #카테고리 확인

tags: [blog, algoDat-p, java] #태그 확인

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

# use_math: true                    #숫자 사용 확인

date: 2023-04-26 #날짜 확인
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

# 01 객체 지향 프로그래밍의 주요개념

객체 지향 프로그래밍에서의 주요개념으로는 "캡슐화", "상속", "일반화", "다형성"이 있다.

## 01-1 캡슐화(Kapselung):

캡슐화는 객체의 데이터와 `메서드`를 하나의 묶음으로 만드는 것을 말한다. 이를 통해 객체 내부의 구현 세부사항을 외부에 노출시키지 않고, 외부에서는 객체의 인터페이스만 접근할 수 있다. 즉, 객체가 필요한 정보만 외부에 제공하고, 나머지 정보는 숨기는 것이다.

**keyword: 접근제한자(Zugriffsmodifizierer): private, package, protected, public**

예제 코드는 아래와 같다.

```java
public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void introduce() {
        System.out.println("My name is " + name + " and I am " + age + " years old.");
    }
}
```

위 코드에서 Person 클래스는 이름과 나이를 가지는 사람을 나타내는 클래스이다. name과 age 속성은 private으로 선언되어 있으므로, 외부에서는 직접 접근할 수 없다. 이를 위해 getName(), setName(), getAge(), setAge() 메서드를 public으로 선언하여 외부에서는 이 메서드를 통해 데이터에 접근할 수 있도록 구현되어 있다.

introduce() 메서드는 객체를 소개하는 메서드로, name과 age 속성에 접근하여 문자열을 출력한다. 이 메서드는 public으로 선언되어 있으므로, 외부에서도 이 메서드를 호출할 수 있다.

이렇게 캡슐화를 구현하면, 객체의 데이터와 메서드를 외부에 노출시키지 않고, 외부에서는 인터페이스만 접근할 수 있도록 할 수 있다. 이를 통해 객체의 상태를 보호하고, 객체의 일관성을 유지할 수 있다. 또한, 접근 제한자를 이용하여 데이터와 메서드에 대한 접근 권한을 제어함으로써, 객체의 데이터 무결성을 보호할 수 있다.

<div class="notice--info">
<b>메서드(Method)</b><br>

메서드(Method)는 객체 지향 프로그래밍에서 특정한 동작을 수행하는 코드의 집합이다.<br>
즉, 객체가 가지고 있는 기능을 구현하는 코드 블록이라고 할 수 있다.<br>
<br>
메서드는 클래스 내부에 정의되며, 객체가 생성될 때 해당 객체의 속성 값을 조작하거나 연산을 수행하기 위해 호출된다. 메서드는 객체의 속성 값을 변경하거나, 다른 객체와 상호작용하는 등 다양한 기능을 수행할 수 있다.<br>
<br>
예를 들어, 자동차 클래스에서 accelerate() 메서드는 자동차의 속도를 높이는 기능을 수행할 수 있다. 이 메서드를 호출하면 자동차 객체는 가속도를 계산하고, 현재 속도에 가속도를 더하여 새로운 속도를 설정하게 된다.<br>
<br>
메서드는 보통 매개변수(parameter)와 반환값(return value)을 가진다. 매개변수는 메서드가 호출될 때 메서드 내부로 전달되는 값으로, 이를 통해 메서드가 실행되는 동안에만 사용된다. 반환값은 메서드가 실행된 결과를 호출한 쪽으로 반환하는 값이다.<br>
<br>
객체 지향 프로그래밍에서 메서드는 객체의 상태를 조작하거나 연산을 수행하는 등 다양한 기능을 수행한다. 따라서, 메서드는 객체 지향 프로그래밍에서 핵심적인 역할을 수행하며, 클래스의 인터페이스를 정의하는 중요한 요소 중 하나이다.<br>

</div>

<div class="notice--info">
<b>접근제한자(Zugriffsmodifizierer)</b><br>

- <b>private:</b> 같은 클래스 내에서만 접근 가능. 즉, 외부에서는 해당 데이터와 메서드에 접근할 수 없다.<br>
- <b>package:</b> 같은 패키지 내에서만 접근 가능. 즉, 같은 패키지에 속한 클래스에서는 해당 데이터와 메서드에 접근할 수 있지만, 다른 패키지에 속한 클래스에서는 접근할 수 없다.<br>
- <b>protected:</b> 같은 패키지와 해당 클래스의 하위 클래스에서 접근 가능. 즉, 같은 패키지 내에서는 접근할 수 있고, 다른 패키지에 속한 클래스에서도 상속받은 경우에는 해당 데이터와 메서드에 접근할 수 있다.<br>
- <b>public:</b> 모든 클래스에서 접근 가능. 즉, 외부에서도 해당 데이터와 메서드에 접근할 수 있다.<br>

</div>

## 01-2 상속(Vererbung):

상속은 이미 존재하는 클래스에서 속성과 메서드를 물려받아 새로운 클래스를 만드는 것이다. 이를 통해 상위 클래스의 기능을 재사용하면서 하위 클래스에서는 새로운 기능을 추가할 수 있다. 또한, 코드 재사용성을 높이고, 유지보수성을 개선할 수 있다.

**keyword: extends**

예제 코드는 아래와 같다.

```java
class Animal {
    protected String name;

    public Animal(String name) {
        this.name = name;
    }

    public void makeSound() {
        System.out.println("The animal makes a sound");
    }
}

class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }

    public void makeSound() {
        System.out.println("The dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal("Animal");
        animal.makeSound();

        Dog dog = new Dog("Dog");
        dog.makeSound();
    }
}
```

위 코드에서 Animal 클래스는 이름을 가지는 동물을 나타내는 클래스이다. name 속성과 makeSound() 메서드를 가지고 있다.

Dog 클래스는 Animal 클래스를 상속받아, 개를 나타내는 클래스이다. Dog 클래스는 상속받은 name 속성과 makeSound() 메서드를 그대로 사용하면서, makeSound() 메서드를 오버라이딩하여 개의 짖는 소리를 출력하도록 하였다.

Main 클래스에서는 Animal과 Dog 객체를 생성하여 makeSound() 메서드를 호출한다. Animal 객체에서는 상속받은 makeSound() 메서드를 호출하여 "The animal makes a sound"라는 문자열을 출력하고, Dog 객체에서는 오버라이딩한 makeSound() 메서드를 호출하여 "The dog barks"라는 문자열을 출력한다.

이렇게 상속을 이용하여 코드를 작성하면, Animal 클래스에서 공통적인 속성과 메서드를 정의하고, Dog 클래스에서는 이를 상속받아 새로운 속성과 메서드를 추가하거나 수정하여 코드를 작성할 수 있다. 이를 통해 코드의 재사용성과 가독성을 높일 수 있다.

## 01-3 일반화(Generalisierung, Generalization):

일반화는 클래스와 인터페이스의 추상화된 형태를 만드는 것이다. 이를 통해 공통된 특성을 갖는 클래스나 인터페이스를 만들고, 이를 상속하거나 구현함으로써 코드 재사용성을 높일 수 있다. **추상 클래스와 인터페이스**를 사용하여 일반화를 구현할 수 있다.

### 01-3-1 추상 클래스 (Abstract class)

하위 클래스에서 구체적인 구현을 완성해야 하는 **추상 메서드**와 **일반 메서드**를 함께 가지는 클래스이다. **추상 클래스는 "abstract" 키워드를 사용하여 정의**되며, 하위 클래스에서는 **추상 메서드를 반드시 구현**해야 한다. 추상 클래스는 자체로 객체를 생성할 수 없으며, 상속을 통해 하위 클래스에서만 객체를 생성할 수 있다. `하지만 하나의 하위 클래스가 두개의 추상 클래스를 extends로 받을 수는 없다.`

```java
abstract class Animal {
    protected String name;

    public Animal(String name) {
        this.name = name;
    }

    public abstract void makeSound();
}

class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }

    public void makeSound() {
        System.out.println("The dog barks");
    }
}
```

위 코드에서 Animal 클래스는 추상 클래스로, 하위 클래스에서 makeSound() 메서드를 구현하도록 강제한다. Dog 클래스는 Animal 클래스를 상속받아 makeSound() 메서드를 구현하고 있다.

### 01-3-2 인터페이스 (Interface)

일련의 메서드 집합을 나타내는 추상 형식이다. 인터페이스는 **"interface" 키워드를 사용하여 정의**되며, `클래스와 달리 다중 상속이 가능`하다. 인터페이스에서 선언된 메서드는 모두 추상 메서드이며, 하위 클래스에서는 **인터페이스에서 선언된 모든 메서드를 반드시 구현**해야 한다.

```java
interface Animal {
    public void makeSound();
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("The dog barks");
    }
}
```

위 코드에서 Animal은 인터페이스로, makeSound() 메서드를 선언하고 있다. Dog 클래스는 Animal 인터페이스를 구현하고 있으며, makeSound() 메서드를 구현하고 있다.

Java에서는 추상 클래스와 인터페이스를 함께 사용할 수 있다. 추상 클래스를 상속하면 일반 메서드와 추상 메서드를 모두 상속받을 수 있으며, 인터페이스를 구현하면 모든 메서드를 구현해야 한다. 다중 상속을 지원하지 않는 Java에서는, 추상 클래스와 인터페이스를 적절히 조합하여 일반화(Generalisierung)를 구현할 수 있다.

## 01-4 다형성(Polymorphie, Polymorphism):

다형성은 객체 지향 프로그래밍에서 객체가 다양한 형태를 가질 수 있는 특성을 말한다. 이는 상속과 인터페이스를 통해 구현된다. 다형성을 구현하면 객체가 여러 개의 타입으로 취급될 수 있으므로, 코드 재사용성과 유지보수성을 높일 수 있다.

다형성은 크게 두 가지 형태로 구현된다.

**Overloading(오버로딩):**  
같은 이름의 메서드가 매개변수의 타입이나 개수에 따라 다른 기능을 수행하는 것을 말한다.

**Overriding(오버라이딩):**  
상위 클래스에서 정의된 메서드를 하위 클래스에서 재정의하여 사용하는 것을 말한다.

이렇게 다형성은 상속과 인터페이스를 통해 구현되며, 오버로딩과 오버라이딩을 사용하여 객체의 다양한 형태를 구현한다.

다음은 다형성을 구현한 예제 코드이다.

```java
abstract class Animal {
    public abstract void makeSound();
}

class Dog extends Animal {
    public void makeSound() {
        System.out.println("The dog barks");
    }
}

class Cat extends Animal {
    public void makeSound() {
        System.out.println("The cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal1 = new Dog();
        Animal animal2 = new Cat();

        animal1.makeSound();
        animal2.makeSound();
    }
}
```

위 코드에서 Animal 클래스는 추상 클래스로, makeSound() 메서드를 추상 메서드로 선언하고 있다. Dog 클래스와 Cat 클래스는 Animal 클래스를 상속받아 makeSound() 메서드를 오버라이딩하여 구현하고 있다.

Main 클래스에서는 Animal 타입의 변수를 선언한 후, Dog 객체와 Cat 객체를 생성하여 대입한다. 이 때, Dog 객체와 Cat 객체는 모두 Animal 타입의 객체로서 사용될 수 있다. Animal 타입으로 선언된 변수에서 makeSound() 메서드를 호출하면, 각각 Dog 클래스와 Cat 클래스에서 오버라이딩된 makeSound() 메서드가 실행되어 "The dog barks"와 "The cat meows"라는 문자열을 출력하게 된다.

<div class="notice--info">
<b>메서드(Method)와 함수</b><br>

매서드와 함수는 비슷한 개념이지만, 객체 지향 프로그래밍과 절차 지향 프로그래밍에서 다르게 사용된다. 각각의 특징과 차이점을 알아보자.<br>
<br>

<b>함수(Funktion, function)의 특징</b><br>

- 함수는 프로그램의 실행을 위해 만들어진 독립적인 코드 블록으로, 일련의 작업을 수행하고 결과를 반환한다.<br>
- 함수는 입력값(인자)을 받아서 이를 가지고 작업을 수행하고, 결과를 반환한다.<br>
- 함수는 보통 다른 함수나 메서드에서 호출되며, 호출될 때마다 매번 동일한 결과를 반환한다. - 함수는 주로 절차 지향 프로그래밍에서 사용된다.<br>
  <br>

<b>메서드(Method)의 특징</b><br>

- 반면에 메서드는 객체 지향 프로그래밍에서 사용되는 개념으로, 특정 객체에 속하는 기능을 수행하는 코드 블록이다. <br>
- 메서드는 객체 내부에 존재하며, 객체의 상태를 변경하거나 객체 간의 상호작용을 수행하는 등 객체의 행동을 구현한다. <br>
- 메서드는 호출될 때 객체에 대한 작업을 수행하고, 결과를 반환한다.<br>
  <br>

<b>메서드와 함수의 차이점</b><br>

- 즉, 함수와 메서드 모두 일련의 작업을 수행하고 결과를 반환하지만, 함수는 독립적인 코드 블록이며, 메서드는 객체에 속한 코드 블록이라는 차이가 있다. <br>
- 또한 함수는 입력값을 받아서 작업을 수행하지만, 메서드는 자신이 속한 객체의 상태를 변경하거나, 객체 간의 상호작용을 수행하는 등 객체의 행동을 구현한다.<br>

</div>

---

---

---

<div class="notice--info">
<b>이전 포스트에서 몇가지 기본 확장프로그램들을 알아봤었고, 태그도 몇 가지 해보았다.<br>
못보셨거나 궁금 하신 분들은 <a herf="https://sehoon1207.github.io/htmlcss/html&css-n-_01_Hello_ko/">이 링크</a>를 눌러서 확인 해주시거나 sidebar에 <a herf="https://sehoon1207.github.io/search/">search</a>에서 검색해도 확인 할 수 있다.</b>
</div>

<div class="notice--warning">
html의 태그는 수없이 많기 때문에 모두 외울 수 없다.<br>
따라서 mdn의 사이트로 가면 많은 태그들과 그에 맞는 속성들에 대한 정보를 얻을 수 있다.<br>
해당 사이트에 가려면 <a herf="https://developer.mozilla.org/en-US/docs/Web/HTML/Element">click hier</a>
</div>

---

# 01 HTML 문서의 구조

이전까지는 몇 가지 연습하면서 html파일에 입력한 코드가 어떻게 실행되는지 알아봤다면, 이 포스트에서는 본격적으로 html문서의 기본적인 구조와 규칙들에 대해서 정리해 보겠다.

아래의 코드가 html문서의 기본적인 구조이자 골격이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- 문서 정보, 메타데이터, 스타일 시트 등을 포함하는 요소 -->
  </head>
  <body>
    <!-- 실제로 표시되는 웹 페이지의 본문을 포함하는 요소 -->
  </body>
</html>
```

1\. **<!DOCTYPE html>**코드는 HTML 문서가 어떤 버전의 HTML을 사용하고 있는지 웹 브라우저에게 알리는 선언이다. 이 선언은 HTML 문서의 맨 첫 줄에 작성되고, HTML5에서는 필수적인 선언이다. 이전 버전의 HTML에서는 이 선언이 필수적이지 않았지만, 모든 웹 페이지에서 사용하는 것이 좋다. 이렇게 선언함으로써 웹 브라우저에게 현재 HTML 문서가 어떤 버전의 HTML을 사용하는지 알려주고 올바르게 해석하도록 도와준다.

2\. **<html>**태그는 문서의 시작과 끝을 정의하며, 브라우저에게 현재 문서가 HTML로 작성된 것임을 알리는 역할이다.

3\. HTML 문서에서는 **<head>**와 **<body>**라는 두 가지 주요 부분이 있다.

**<head>**는 브라우저에게 문서 정보를 제공하는 메타데이터와 스타일 시트, 제목 등의 기타 정보를 담는 곳이다. 이 안에 있는 요소들은 브라우저에서 문서를 렌더링하는 데 필요한 정보를 제공하는 것들 이다.

**<body>**는 브라우저 창에 실제로 표시되는 내용이다. 이 안에 있는 요소들은 브라우저에서 보이는 웹 페이지의 본문을 나타내며, 텍스트, 이미지, 비디오, 오디오 등을 포함할 수 있다.

따라서 가장 처음에 입력했던 코드를 지금의 기본 구조에 넣는다면 다음과 같다.

```html
<!DOCTYPE html>
<html>
  <head> </head>
  <body>
    Hello! This is my first HTML file! Nice to meet you!
  </body>
</html>
```

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_home.jpg?raw=true" width="1000px"/>

처음에 기본 구조 없이 입력했던 것과 브라우저에서 보이는 것은 차이가 없다. 하지만 많은 태그들이 추가되면 html의 문서는 더욱 복잡해 지게 되고, 기본 구조를 지킨 문서는 다른 사람이나 또는 자신이 추후에 수정할 때 해당부분을 더욱 편하게 찾을 수 있다.

<div class="notice--info">

<h4>html태그 속성 lang</h4> <br>
<u><b>html lang="en"</b></u>
해당 HTML 문서가 사용하는 언어를 정의하는 데 사용된다. <br>
이 속성은 웹 검색 엔진(google, bing, naver 등)이 해당 문서의 언어를 인식하고 적절한 검색 결과를 제공하는 데 중요한 역할을 한다.

</div>

---

# 02 \<title> 페이지의 타이틀 바꾸기

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_html_title.jpg?raw=true" width="1000px"/>

지금까지 작업했던 html문서는 타이틀이 없었다.  
그래서 이미지에서 보이는 것 처럼, 작성한 파일의 이름이 보여진다.
google이나 netflix 등을 보면 파일 이름이 아닌 title이 표시된다.
해당 부분을 바꾸려면 다음과 같이 작성한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>my Homepage</title>
  </head>
  <body>
    Hello! This is my first HTML file! Nice to meet you!
  </body>
</html>
```

`기본구조에 해당하는 태그들의 열고 닫는 곳에 유의해서 작업하자.`

위의 코드처럼 작성했다면 아래 이미지 처럼 my Homepage로 바뀐 것을 확인 할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_html_title2.jpg?raw=true" width="1000px">

---

# 03 \<meta> 태그

\<meta> 태그는 HTML 문서의 헤더 영역에 사용되고, 문서 정보를 지정하거나, 문서 검색 및 검색 엔진 최적화 (SEO)에 사용된다.

아래 이미지는 구글에서 Deutsch Welle를 검색했을 때 브라우저에서 표시되는 정보들이다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_search_dw.jpg?raw=true" width="700px">

이미지에서 보이는 텍스트들 중에 "Nachrichten & Analysen: der globale..." 라고 되어 있는 부분이 이전에 우리가 작성했던 해당 웹페이지의 title이다. 그리고 그 바로 아래에 있는 "Deutsche Welle: Der internationale Blick auf aktuelle Nachrichten..."이라는 작은 폰트로 보여지는 것(description)이 바로 meta 태그로 만든 것이다. meta 태그는 실제로 html파일을 열었을 때, 그 페이지에서는 보이지 않지만 많은 정보를 담고 있다.

이미지에서 보았던 것처럼 description을 적용하고 싶다면 아래와 같이 코딩을 하면 된다.  
아래와 같이 코딩해도 실제로 보이는 것에는 변화가 없을 것이다. 앞서 말한 것처럼 그 페이지에서는 보이지 않기 때문이다. description은 구글에서 검색할 때 찾는 단어들 이므로 키워드를 잘 적는 것이 좋다.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>my Homepage</title>
    <meta name="description" content="welcome to my website" />
  </head>
  <body>
    Hello! This is my first HTML file! Nice to meet you!
  </body>
</html>
```

meta태그의 속성(attribute)중에는 charset이라는 것이 있는데 이것은 매우 중요한 속성이다.  
특수문자가 있는 언어 같은 경우 이 속성을 추가해야 텍스트가 오류가 나지 않는다.  
아래의 코드를 head 영역에 추가해주면 된다.

```html
<meta charset="utf-8" />
```

---

# 04 \<link rel="shortcut icon"> 웹사이트의 파비콘(favicon)설정

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_html_favicon.jpg?raw=true" width="1000px">

브라우저의 최상단에 있는 구글이나 넷플릭스 등의 탭을 보면 구글 아이콘과 넷플릭스 아이콘이 보여지는데, 그것을 파비콘이라고 한다. 그 작은 아이콘을 넣고 싶다면 아래와 같은 코드를 head에 추가하면 된다.
link의 속성 중 href에 자신이 원하는 이미지의 주소를 넣도록 하자.

```html
<link
  rel="shortcut icon"
  sizes="16x16 32x32 64x64"
  href="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/IS_favicon2_88x88.png?raw=true"
/>
```

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_html_favicon2.jpg?raw=true" width="1000px">

---

# 05 \<form>을 만들어보자.

공지에서도 소개했던 [mdn 사이트](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)로 가면 form태그에 대해 자세히 설명이 되어 있다. 사용이 가능한 속성들도 확인 할 수 있고, 한국어로도 볼 수 있다. 전부 적기는 힘들기 때문에 아래에 form샘플 코드만 적어둔다. 브라우저에서 아래 코드를 확인하면 마치 웹사이트에서 로그인하는 양식 처럼 보일 것이다.  
코드 안에 있는 속성(유형)들의 자세한 설명은 위의 사이트에서 확인하고, 원하는대로 수정해 보자.  
여기서 알아야 할 것은 form이라는 태그가 어떤 역할로 html에서 사용되는지 이해하면 된다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
  </head>
  <body>
    <form>
      <label for="profile">Profile</label>
      <input id="profile" type="file" accept=".jpg, .png, image/*" />

      <label for="name">Name</label>
      <input id="name" required placeholder="Name" type="text" />
      <label for="user-name">User Name</label>
      <input id="user-name" required placeholder="User Name" type="text" />
      <label for="password">Password</label>
      <input
        id="password"
        required
        placeholder="Password"
        minlength="10"
        type="password"
      />
      <input type="submit" value="Create Account" />
    </form>
  </body>
</html>
```

`하나의 태그에 여러가지 속성을 추가할 때는 띄어쓰기에 유의하자!`

`id는 하나의 태그에 하나만 존재할 수 있다.`

<div class="notice--warning">
<b>**labe태그</b><br>
label태그는 input과 같이 사용해줘야 한다.<br>
1. input에 id속성을 주고 이름을 부여해준 후(위의 코드에서는 profile이라는 이름을 부여)<br>
2. label에 for를 이용해서 input과 연결해준다. <br>

</div>

---

# 06 무의미 태그(Non Semantic Tags) \<div>

무의미 태그인 \<div>는 division의 약자로, 구역을 만들기 위해 사용되는 태그다. 쉽게 박스(box)라고 생각하면 된다.  
주로 CSS와 함께 사용하여 구역을 스타일링하거나, 자바스크립트를 이용해 구역에 대한 조작을 수행할 때 유용하게 사용된다.  
하지만 \<div>는 실제로 어떤 역할을 가지는 것이 아니기 때문에 무의미 태그라고 부른다. 그럼 어떻게 사용하는걸까?

예를 들면, form에서 사용한 코드를 실제로 브라우저에서 보면 일렬로 나열된 것을 볼 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_non_semantic_tags.jpg?raw=true" width="1000px">

항목들이 가로로 나열된 것보다 세로로 나열하고 싶을 때, div를 사용하면 정리할 수 있다.  
label과 input을 한세트씩 div로 묶어주면 된다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
  </head>
  <body>
    <form>
      <div>
        <label for="profile">Profile</label>
        <input id="profile" type="file" accept=".jpg, .png, image/*" />
      </div>
      <div>
        <label for="name">Name</label>
        <input id="name" required placeholder="Name" type="text" />
      </div>
      <div>
        <label for="user-name">User Name</label>
        <input id="user-name" required placeholder="User Name" type="text" />
      </div>
      <div>
        <label for="password">Password</label>
        <input
          id="password"
          required
          placeholder="Password"
          minlength="10"
          type="password"
        />
      </div>
      <div>
        <input type="submit" value="Create Account" />
      </div>
    </form>
  </body>
</html>
```

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/02-n_non_semantic_tags2.jpg?raw=true" width="1000px">

기본적으로 box들은 양옆으로 서로 붙어서 나열되지 않는다. 그래서 연속해서 div로 box를 만들어주면 아래로 나열되는 것이다.  
하지만 이러한 div 중에서도 의미가 있는 div도 있다.
예를 들면 `<header>`, `<main>`, `<footer>` 등이 있다.  
div 외에 의미가 없는 태그로는 span, p 등이 있다.

<div class="notice--info">
<b>***의미를 가지는 div태그</b><br>
<br>
header는 웹 페이지의 상단 부분에 위치하며, 로고, 사이트 제목, 주요 내비게이션 링크 등 중요한 내용을 담고 있다. <br>
보통 nav, h1, h2 등과 함께 사용된다.<br>
<br>
main은 웹 페이지의 핵심적인 내용을 담는 부분이다. <br>
보통 한 웹 페이지에는 하나의 main 태그가 있으며, article, section, aside 등과 함께 사용된다.<br>
<br>
footer는 웹 페이지의 하단 부분에 위치하며, 저작권 정보, 연락처, 이메일 구독 양식 등을 포함할 수 있다. <br>
보통 nav, ul 등과 함께 사용된다.<br>

</div>

---

Quelle(text): vorlesung, [nomadcoders](https://nomadcoders.co/)  
Quelle(image):

<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
<!-- <sup>[1)](#footnote_1)</sup>

<div class="notice--info">
<a name="footnote_1">1)</a>블라블라<br>
</div> -->
