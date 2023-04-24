---
layout: single
title: "[html&css] 00 Intro"
folder: "html&css"
categories:
  - htmlcss

tags: [blog, htmlcss]

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

# use_math: true

date: 2023-04-24
---
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”

# 기본 개념

## 0 웹사이트와 브라우저

일단, 아무 웹사이트나 들어가보자.  

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/00_dw.jpg?raw=true">
웹사이트 출처: <https://www.dw.com/en/>

**apple iso      : view보기 > Developer개발자정보 > view Source소스보기**  
**Window (crome) : F12**  

해당 경로를 따라가거나 F12를 누르면 위 이미지의 오른쪽에 나오는 것 처럼 웹사이트의 소스를 볼 수 있다.  
  
웹사이트 소스를 보면 복잡한 문자가 많이 쓰인다.  
이런 복잡한 문자들을 하나하나 전부 알 필요는 없다는게 중요하다!  
물론 알면 좋겠지만, 시간이 엄청나게 필요할 것이다.  
  
때문에 전부가 아닌 몇가지의 문법만 일단 이해하고 활용하는 것만 하는 것이 시작단계에서 좋다.  
문법을 알면 구조가 눈에 보일 것이고 추후에 해당 일부분을 바꾸거나 변경할 수도 있을 정도로 저 복잡한 것들이 이해될 것이다.  

### 0-1 웹사이트(website)

웹사이트는 인터넷에 연결된 컴퓨터에서 사용자들이 접속해서 정보를 확인하거나 서비스를 이용할 수 있는 웹페이지나 애플리케이션을 말한다.  
  
웹사이트를 만들기 위해서는 HTML, CSS, JavaScript 등의 프로그래밍 언어를 사용하여 웹페이지를 구성하고, 이를 인터넷에 배포하기 위해서는 웹호스팅 서비스를 이용하거나 클라우드 서버를 구축하여 호스팅할 수 있다.  

### 0-2 브라우저

반면에 브라우저는 사용자가 인터넷을 통해 웹사이트에 접속하여 정보를 확인하거나 서비스를 이용할 때 사용하는 소프트웨어이다. 대표적인 브라우저로는 크롬, 파이어폭스, 사파리, 엣지 등이 있다.

브라우저는 웹사이트를 불러와서 HTML, CSS, JavaScript 등의 파일을 해석하여 사용자에게 웹페이지를 보여주고, 사용자의 요청에 따라 서버와 통신하여 필요한 정보를 가져온다. 그래서 웹사이트의 소스에서 보았던 복잡한 글자들이 마법처럼 화면에 나타나는 것이다. 이러한 과정에서 브라우저는 웹사이트의 레이아웃, 콘텐츠, 기능 등을 구성하고, 사용자와 웹사이트 간의 상호작용을 지원한다.

## 1 HTML, CSS, Javascript

이 세가지는 웹사이트를 만들 때(웹 개발을 할 때) 기본적으로 사용되는 언어이다.

**HTML(HyperText Markup Language):**  
HTML은 웹 `페이지의 내용과 구조를 정의`하는 `마크업 언어`<sup>[1)](#footnote_1)</sup>이다. HTML을 사용하여 웹사이트의 형태를 구상하고 그것에 맞게 텍스트, 이미지, 비디오 등 다양한 콘텐츠를 웹 페이지에 추가할 수 있다.

**CSS(Cascading Style Sheets):**  
CSS는 웹 페이지의 `디자인과 레이아웃`을 다루는 `스타일링(디자인) 언어`<sup>[2)](#footnote_1)</sup>다. CSS를 사용하여 웹 페이지의 색상, 폰트, 레이아웃, 크기 등을 조정할 수 있다. 따라서 CSS는 꾸며주는 역할이므로, CSS를 사용하지 않고 HTML만 이용해서 website를 만들 수 있다.

**JavaScript:**  
JavaScript는 웹 페이지에서 `동적인 기능을 추가`하는 `프로그래밍 언어`<sup>[3)](#footnote_1)</sup>다. CSS에서 구현하지 못했던 다이나믹한 또는 화려한 website를 만들 수 있게 도와줄 것이다. JavaScript를 사용하여 웹 페이지에 인터랙티브한 요소를 추가하거나, 사용자 입력을 처리하거나, 웹 페이지 내의 데이터를 동적으로 업데이트할 수 있다. JavaScript는 클라이언트 측에서 실행되며, 웹 브라우저에서 실행된다. JavaScript역시 CSS처럼 부가적인 요소이므로 사용하지 않더라도(HTML만 사용하더라도) 웹페이지를 만들 수 있다.


<div class="notice--info">
<a name="footnote_1">1)</a>마크업 언어: 마크업 언어는 문서의 구조를 정의하기 위해 사용됨. 예. HTML, XML, Markdown, LaTeX, YAML 등.<br>
<a name="footnote_1">2)</a>디자인 언어: 디자인 언어는 문서나 애플리케이션의 디자인을 정의하기 위해 사용됨. 예. CSS, SCSS, LESS, Stylus, SASS 등. <br> 
<a name="footnote_1">3)</a>프로그래밍 언어: 프로그래밍 언어는 컴퓨터의 동작을 제어하기 위해 사용됨. 예. JavaScript, Python, Java, Ruby, C++ 등.<br>
</div>

---

Quelle(text): vorlesung, [nomadcoders]<https://nomadcoders.co/>
Quelle(image): main page, [Deutsch_Welle]<https://www.dw.com/en/>


<!-- &nbsp; 1칸 띄어쓰기 -->
<!-- &ensp; 2칸 띄어쓰기 -->
<!-- &emsp; 3칸 띄어쓰기 -->
