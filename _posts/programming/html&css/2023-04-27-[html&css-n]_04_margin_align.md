---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 04 css로 여백관리 및 정렬" #제목 확인
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

# 01 인라인(inline)과 블럭(block)

HTML에서 inline과 block은 요소가 어떻게 배치되는지를 나타내는 두 가지 기본 디스플레이 속성이다.

## 01-1 블럭(block)

block은 가로폭 전체를 차지하고, 위에서 아래로 쌓이는 박스 모양의 요소다. 기본적으로 가로 너비 전체를 차지하며, 가로폭을 지정하지 않으면 자동으로 100%의 가로폭을 갖게 된다. 대표적인 block 요소로는 **div, h1, p, ul, ol** 등이 있다.

## 01-2 인라인(inline)

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

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/04-n_inline_block.jpg?raw=true" width="1000px"/>

브라우저에서 확인해 보면 span은 가로로, div는 세로로 나열된 것을 확인 할 수 있다. 그리고 span의 너비와 높이를 따로 지정했음에도 변화없이 자동 지정된 높이와 너비값을 갖는 것을 볼 수 있다.

## 01-3 inline과 block 변경(display속성)

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

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/04-n_display.jpg?raw=true" width="1000px"/>

hello텍스트인 span의 너비와 높이가 커지고 div는 사라진 것을 확인 할 수 있다.
span의 너비와 높이가 지정 가능해진 이유는 display속성을 이용해서 inline이 아닌 block이 되었기 때문이다. div의 경우에는 반대로 inline이 되어 너비와 높이가 자동으로 조절되었다. 하지만 div안에는 아무런 내용이 없기 때문에 브라우저에서 아무것도 표현되지 않는 것이다.

<div class="notice--info">
<b>inline-block</b><br>

inline-block은 display의 속성값으로 display: inline-block이라고 사용할 수 있다.<br>

inline-block으로 설정 할 경우, 내부의 contents들은 block으로 인식되어서 각각 너비와 높이값을 가질 수 있게 되며 margin, padding 등도 가질 수 있게된다. 하지만 일반적인 block과 달리 inline처럼 양 옆에 contents들이 나열될 수 있다.<br>

문제점으로는 inline-block은 Responsive Design(반응형 디자인)을 지원하지 않는다는 것이다. 따라서 브라우저의 크기가 달라지면 영향을 받는다.

</div>

# 02 block의 추가적인 특징 (margin, padding, border)

block에는 추가적인 특징이 세가지가 있고 속성으로 부여할 수 있다.

**margin:** 경계(테두리)인 border를 기준으로 외부의 다른 요소와의 간격을 지정한다.

**padding:** 경계(테두리)인 border를 기준으로 내부의 콘텐츠와의 사이의 간격을 지정한다. 즉, padding은 요소 내부의 공간을 만들어준다.

**border:** 요소의 테두리를 지정한다.

이 특징들은 다음 그림을 보면 이해가 쉽다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/04-n_margin_padding_border.jpg?raw=true" width="500px"/>

## 02-1 margin과 padding

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

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/04-n_margin_padding_border_2.jpg?raw=true" width="1000px"/>

<div class="notice--danger">
<b>collapsing margins</b><br>

Collapsing margins는 CSS에서 인접한 블록 요소의 margin이 합쳐지는 현상을 말합니다. 두 요소의 상(top)/하단(bottom) margin 중 큰 값만 적용되는 것이 일반적이다.<br>

Collapsing margins는 예상치 못한 결과를 초래할 수 있기 때문에 주의해야 한다. 예를 들어, 부모 요소의 margin과 자식 요소의 margin이 합쳐지면서 의도하지 않은 간격이 생길 수 있다.<br>

이를 방지하기 위해 margin을 조정하거나 padding, border를 추가하여 문제를 해결할 수 있다.<br>

</div>

## 02-2 border

---

# 03 요소들을 정리하기

## 03-1 flexbox

<div class="notice">
<b>부모-자식 관계</b><br>
<br>
flexbox에 대해 설명하기 전에 한 가지 이야기 해 두어야 할 것이 있다.
요소(contents)의 <b>부모-자식 관계</b>이다. <br>
HTML에서 부모-자식 관계란, 한 요소(element)가 다른 요소 안에 포함되는 관계를 의미한다.<br>

부모 요소는 자식 요소를 포함하는 요소를 의미하며, 자식 요소는 부모 요소 안에서 포함되는 요소를 의미한다. 이러한 구조로 HTML은 요소 간에 계층 구조를 형성하게 된다.<br>
<br>
개념이 명확하지 않다면 아래 예제코드를 보자.<br>
예제코드는 first div가 부모이고 second, third, fourth가 모두 자식인 구조를 보여주고 있다.

</div>
```html
  <!-- 부모-자식 관계의 설명을 위한 예제 코드 -->
  <div id="first">
    <div id="second"></div>
    <div id="third"></div>
    <div id="fourth"></div>
  </div>
```

이제부터 display:flex속성을 이용한 flexbox에 대해서 이야기 하겠다. flexbox는 글자그대로 유연한(flexible)박스로 요소들을 자유롭게 이동시키기 위해 사용된다.  
`여기서 주의할 점은 display:flex 속성을 부여하는 대상이 움직이려는 박스가 아닌, 움직이려는 박스의 부모에게 부여해야 한다는 것이다.`

따라서 위에서 보여준 예제코드에 display:flex 속성을 준다면 다음과 같다.

```css
#first {
  display: flex;
  /* ... */
}
```

부모인 first에게 flex속성을 부여하고 추가로 속성을 부여함으로써 자식인 박스들(예제에 따르면 second, third, fourth)이 추가하는 속성에 따라 이동또는 정렬하게 되는 것이다.

다음으로 알아볼 것은 display:flex와 함께 사용하는 속성들이다.

## 03-2 수평정렬하기 justify-content

justify-content속성을 사용하면 content들을 좌,우,가운데 정렬 등 쉽게 움직일 수 있다. 따라서 그에 해당하는 여러가지 값을 줄 수 있다. margin과는 달리 브라우저에 크기를 변화시키면 자동으로 빈 공간의 크기를 조절해 준다. 사용 가능한 값들은 다음과 같다.

```css
/* 가운데 정렬 */
justify-content: center;
/* 오른쪽 정렬 */
justify-content: flex-end;
/* 왼쪽 정렬, 기본값(default) */
justify-content: flex-start;
/* 빈 공간을 같은 크기로 나누어서 배치 */
justify-content: space-evenly;
justify-content: space-bitween;
```

## 03-3 수직정렬하기

앞서 살펴본 justify-content를 이용하면 수평에 해당하는 부분은 정렬이 가능했다. 그럼 수직은 어떻게 해야할까?

수직정렬을 하기 위해서는 메인축(main axis)과 교차축(cross axis)를 알아야 한다.  
flexbox를 정렬 할 때 사용한 justify-content는 기본으로 메인축이 수평방향인 상태이다. 따라서 정렬속성을 주면 수평을 기준으로 content들이 정렬되는 것이다. 따라서 수직방향을 정렬하려면 두가지 방법이 있는데, 첫번째는 메인 축을 수직으로 바꾸는 방법, 그리고 두번째는 aline-item속성을 사용하는 방법이다. 그 속성이 바로 flex-direction이다.

### 03-3-1 첫번 째 축의 방향을 바꾸기 flex-direction

```css
/* 메인축: 수평, 교차축: 수직 (디폴트)*/
flex-direction: row;
/* 메인축: 수직, 교차축: 수평 */
flex-direction: column;
```

위 예제코드에서 볼 수 있듯이 flex-direction은 row가 기본값(default)이며 변경사항이 없을 경우 이 값이 기본으로 되어 있다. 하지만 flex-direction값을 column으로 변경하면 메인축이 수직이 되면서 해당 부모의 자식요소들을 수직정렬 할 수 있다.

### 03-3-2 두번 째 교차축 정렬하기 aline-items

aline-items 속성도 마찬가지로 display:flex와 함께 사용하는 속성이며 justify-content와 같이 자식들을 정렬할 수 있는 여러가지 방법(값)들이 있다.

```css
align-items: stretch;
/* (기본값): flex 아이템들을 교차 축 방향으로 늘려서 채운다. */
align-items: flex-start;
/*  flex 아이템들을 교차 축 시작점에 정렬. */
align-items: flex-end;
/*  flex 아이템들을 교차 축 끝점에 정렬. */
align-items: center;
/* flex 아이템들을 교차 축 방향으로 중앙에 정렬. */
align-items: baseline;
/*  flex 아이템들을 텍스트의 기준선(baseline)에 맞추어 정렬. */
```

`align-items의 경우 justify-content와 다르게 컨텐츠 간의 간격을 자동 조절하는 space-bitween 등을 사용할 수 없기 때문에 빈 공간을 조절할 필요가 있는 경우, 축을 변경해야만 한다.`

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
