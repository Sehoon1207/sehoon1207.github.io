---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 03 css 시작하기" #제목 확인
folder: "html&css" #폴더 확인
categories:
  - htmlcss #카테고리 확인

tags: [blog, htmlcss] #태그 확인

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

date: 2023-04-27 #날짜 확인
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
<b>
<pre>
OS    : Window
Editor: VScode</pre></b>
</div>

---

# CSS가 뭐야?

CSS(Cascading Style Sheets)는 웹 페이지의 디자인, 레이아웃, 스타일을 정의하기 위한 스타일 시트 언어이다. HTML과 함께 사용하여 글꼴 크기, 색상, 배경 이미지, 마진, 패딩 등 다양한 속성을 사용하여 HTML 요소를 스타일링할 수 있다.

CSS는 **선택자(selector)와 속성(property)**으로 이루어져 있다. **선택자**는 스타일을 적용할 HTML 요소를 선택하는데 사용되며, **속성**은 선택한 요소에 적용할 스타일을 지정한다.

CSS는 **외부 스타일 시트 파일, 내부 스타일 시트, 인라인 스타일**과 같이 세 가지 방법으로 HTML 문서에 포함될 수 있다. **외부 스타일 시트**는 별도의 CSS 파일을 만들어 HTML 문서와 연결하여 사용하는 것을 말하며, **내부 스타일 시트(인라인 스타일)**는 HTML 문서 내부에 \style 태그를 사용하여 스타일을 정의하는 것이다.

---

# 01 css를 추가하는 두가지 방법

<div class="notice">
앞서 간단히 설명한 것 처럼 css를 사용하는 방법은 두가지가 있는데, 처음 시작할 때는 html파일 안에 입력하는 내부 스타일 시트로 진행하는 것이 좋다고 생각한다. CSS파일을 외부로 따로 둘 정도로 많은 내용을 아직 할 필요가 없기 때문이다. 후반부에는 외부에 .css 파일을 만들고 적용하는 방법으로 정리할 예정이다.  
</div>

## 01-1 내부 스타일 시트

html문서 안에 css로 스타일을 지정하는 것은 간단하다.  
css작업을 위해 **head 부분에 style태그를 사용**하고 그 안에서 작업하면 끝이다.  
아래의 코드는 간단히 html로 뼈대만 만든 상태에서 style태그를 추가한 모습이다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
    <style>
      /* 내부 스타일 시트 방법: 여기에 css관련한 작업이 진행된다. */
    </style>
  </head>
  <body>
    <form>
      <header>
        <h1>Hello, this is my Homepage</h1>
      </header>
      <main>
        <p>nice to meet you</p>
      </main>
      <footer>email: abcd@google.com</footer>
    </form>
  </body>
</html>
```

## 01-2 외부 스타일 시트

html문서 외부에 스타일을 지정하는 방법은 다음과 같다.

1.새로운 .css파일을 생성한다.
2.head부분에 link태그를 이용해서 새로만든 css파일과 연결해준다.

아래의 코드를 참고하자.  
(style.css파일이 home.html와 같은 경로 상에 있을 경우를 가정한다.)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
    <link href="style.css" rel="stylesheet" />
    <!-- 위 코드를 추가해서 외부파일과 연결한다 -->
  </head>
  <body>
    <form>
      <header>
        <h1>Hello, this is my Homepage</h1>
      </header>
      <main>
        <p>nice to meet you</p>
      </main>
      <footer>email: abcd@google.com</footer>
    </form>
  </body>
</html>
```

# 02 css 적용하기

일단 예제 코드를 보자.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
    <style>
      h1 {
        color: blue;
      }
    </style>
  </head>
  <body>
    <form>
      <header>
        <h1>Hello, this is my Homepage</h1>
      </header>
      <main>
        <p>nice to meet you</p>
      </main>
      <footer>email: abcd@google.com</footer>
    </form>
  </body>
</html>
```

style 태그안에 아래와 같은 새로운 코드가 추가되어 있다.

```css
h1 {
  color: blue;
}
```

여기서 h1은 선택자(selector)라고 하며 스타일(색변경 등)을 변경하기 위해 html코드 안에 있는 h1태그를 선택한 상태이다. 따라서 중괄호 안에 추가하는 모든 변경사항은 h1에만 적용된다.

`css속성 이름에는 공백이 존재하지 않으므로 유의`

중괄호 안에 있는 color는 속성(property)이라고 하며, 매우 많은 종류가 있다. color는 그 중에 하나로 선택자에 해당하는 부분의 색을 바꿔준다. 그 값이 blue라고 지정되어 있으므로 h1의 글자색은 파란색이 될 것이다.

브라우저에서 확인하면 다음과 같다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/03-n_color.jpg?raw=true" width="1000px"/>

제대로 적용되는 것을 확인했다면 다른 속성도 추가해 보면서 변화를 확인 해보자.

```css
h1 {
  color: blue;
  font-weight: 800px;
  font-size: 50px;
}
```

# 03 DevTools

DevTools는 웹 브라우저에서 개발자가 웹 페이지를 디버깅하고 분석하며, 웹 사이트를 개발할 때 도움을 주는 도구 모음이다. 대부분의 모던 웹 브라우저(Chrome, Firefox, Safari, Edge 등)에서 DevTools를 지원하며, 브라우저 창에서 F12 키를 누르면 열 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/03-n_devtools.jpg?raw=true" width="1000px"/>

요소(elements)부분을 보면 해당 페이지의 html코드를 볼 수 있다. netflix나 google 등 모든 페이지에서도 html코드를 볼 수 있다. 또한 해당 요소들을 클릭하면 적용된 스타일이 이떤 것이 있는지도 확인 할 수 있다.

# 04 Cascading

Cascading은 CSS에서 스타일 규칙이 우선순위에 따라 적용되는 방식을 의미한다.

CSS는 여러 가지 스타일 규칙을 가지고 있을 때, 이 규칙들이 서로 충돌할 경우 어떤 규칙을 우선하여 적용할지 결정해야 한다. 이때 Cascading이라는 개념이 사용된다.

Cascading은 세 가지 규칙을 기반으로 동작한다.

**Specificity(구체성)**  
선택자가 구체적일수록 우선순위가 높다.  
예를 들어, #id 선택자는 .class 선택자보다 우선순위가 높다.

**Inheritance(상속)**  
상위 요소에 적용된 스타일이 하위 요소에도 적용된다.  
하위 요소에서 직접 스타일이 적용되지 않은 경우, 상위 요소에서 적용된 스타일이 상속된다.

**Source Order(출처 순서)**  
나중에 작성된 규칙이 우선순위가 높다.  
같은 스타일 규칙이라면, 마지막(가장 하단)에 작성된 규칙이 우선된다.

세 가지 규칙 중 출처 순서에 대한 코딩을 예를 들면 다음과 같다.

```css
h1 {
  color: blue;
  color: yellow;
  color: red;
}
```

h1의 부분을 위와 같이 변경해보자.

이렇게 동일한 선택자인 h1에 세가지 색을 중복해서 적용하면 가장 마지막에 입력한 color: red만 적용되어 글자색이 붉은색이 되는 것이다.

---

# 05 인라인(inline)과 블럭(block)

HTML에서 inline과 block은 요소가 어떻게 배치되는지를 나타내는 두 가지 기본 디스플레이 속성이다.

## 05-1 블럭(block)

block은 가로폭 전체를 차지하고, 위에서 아래로 쌓이는 박스 모양의 요소다. 기본적으로 가로 너비 전체를 차지하며, 가로폭을 지정하지 않으면 자동으로 100%의 가로폭을 갖게 된다. 대표적인 block 요소로는 **div, h1, p, ul, ol** 등이 있다.

## 05-2 인라인(inline)

inline은 요소의 내용만큼만 차지하며, 좌우로 쌓이는 형태의 요소다. 너비와 높이의 폭이 내용에 맞게 자동 조절되므로, 따로 지정할 수 없다. 대표적인 inline 요소로는 **a, span, img, input** 등이 있다.

인라인과 블록을 비교하기 위한 예제코드는 다음과 같다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
    <style>
      span {
        width: 100px;
        height: 100px;
        background-color: tomato;
      }
      div {
        width: 100px;
        height: 100px;
        background-color: teal;
      }
    </style>
  </head>
  <body>
    <form>
      <header>
        <h1>Hello, this is my Homepage</h1>
      </header>
      <main>
        <span>Hello</span>
        <span>Hello</span>
        <span>Hello</span>

        <div></div>
        <div></div>
        <div></div>
      </main>
      <footer>email: abcd@google.com</footer>
    </form>
  </body>
</html>
```

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/03-n_inline_block.jpg?raw=true" width="1000px"/>

브라우저에서 확인해 보면 span은 가로로, div는 세로로 나열된 것을 확인 할 수 있다. 그리고 span의 너비와 높이를 따로 지정했음에도 변화없이 자동 지정된 높이와 너비값을 갖는 것을 볼 수 있다.

## 04-3 inline-block

`인라인 요소는 기본적으로 높이를 지정할 수 없다. 하지만 높이를 지정할 수 있도록 만들 수 있다.`  
그 방법으로는 display속성으로 지정하는 것이다.

예제코드를 보면 다음과 같다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
    <style>
      span {
        display: block;
        width: 100px;
        height: 100px;
        margin-bottom: 10px;
        background-color: tomato;
      }
      div {
        display: inline;
        width: 100px;
        height: 100px;
        margin-bottom: 10px;
        background-color: teal;
      }
    </style>
  </head>
  <body>
    <form>
      <header>
        <h1>Hello, this is my Homepage</h1>
      </header>
      <main>
        <span>Hello</span>
        <span>Hello</span>
        <span>Hello</span>

        <div></div>
        <div></div>
        <div></div>
      </main>
      <footer>email: abcd@google.com</footer>
    </form>
  </body>
</html>
```

위와 같이 display를 사용해서 span은 block으로 div는 inline으로 강제로 변경해 주었다.  
브라우저에서 확인하면 다음과 같다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/03-n_display.jpg?raw=true" width="1000px"/>

hello텍스트인 span의 너비와 높이가 커지고 div는 사라진 것을 확인 할 수 있다.
span의 너비와 높이가 지정 가능해진 이유는 display속성을 이용해서 inline이 아닌 block이 되었기 때문이다. div의 경우에는 반대로 inline이 되어 너비와 높이가 자동으로 조절되었다. 하지만 div안에는 아무런 내용이 없기 때문에 브라우저에서 아무것도 표현되지 않는 것이다.

# 05 block의 추가적인 특징 (margin, padding, border)

block에는 추가적인 특징이 세가지가 있고 속성으로 부여할 수 있다.

**margin:** 경계(테두리)인 border를 기준으로 외부의 다른 요소와의 간격을 지정한다.

**padding:** 경계(테두리)인 border를 기준으로 내부의 콘텐츠와의 사이의 간격을 지정한다. 즉, padding은 요소 내부의 공간을 만들어준다.

**border:** 요소의 테두리를 지정한다.

이 특징들은 다음 그림을 보면 이해가 쉽다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/03-n_margin_padding_border.jpg?raw=true" width="500px"/>

## 05-1 margin과 padding

margin, padding은 다음과 같이 사용 가능하다.

```css
div {
  margin: 10px; // all 10px
  margin: 10px 5px; // top bottom 10px, right left 5px
  margin: 5px 10px 15px 20px; // top 5px right 10px bottom 15px left 20px
  margin-top: 10px; // right, bottom, left도 동일하게 가능하다.

  padding: 10px; // all 10px
  padding: 10px 5px; // top bottom 10px, right left 5px
  padding: 5px 10px 15px 20px; // top 5px right 10px bottom 15px left 20px
  padding-top: 10px; // right, bottom, left도 동일하게 가능하다.
}
```

margin, padding을 위에 사용하는 방법을 참고해서 코드로 작성해 보았다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>my Homepage</title>
    <style>
      span {
        display: block;
      }
      div {
        width: 100px;
        height: 100px;
        background-color: teal;
        margin: 10px 5px;
        padding: 10px 5px;
      }
    </style>
  </head>
  <body>
    <form>
      <header>
        <h1>Hello, this is my Homepage</h1>
      </header>
      <main>
        <div><span>Hello</span></div>
        <div><span>Hello</span></div>
        <div><span>Hello</span></div>
      </main>
      <footer>email: abcd@google.com</footer>
    </form>
  </body>
</html>
```

해당 코드를 브라우저에서 확인하면 다음과 같이 나오는데 DevTools(F12)를 이용해서 해당 div를 선택하면 margin과 padding이 어떻게 적용되었는지 확인 할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/03-n_margin_padding_border_2.jpg?raw=true" width="1000px"/>

## 05-2 border

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
