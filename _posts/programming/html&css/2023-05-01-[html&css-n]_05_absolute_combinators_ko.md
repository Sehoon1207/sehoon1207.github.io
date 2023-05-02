---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 05 css로 요소의 위치조절 및 추가적인 선택방법" #제목 확인
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

date: 2023-05-01 #날짜 확인
---

<div class="notice">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>
<b>
<pre>
OS    : Window
Editor: VScode</pre></b>
</div>

<div class="notice--info">
이전 포스트에서는 요소들 간의 간격조절 및 정해진 방법으로 요소들을 정렬하는 방법에 대해 정리해 보았다. <br>
이번에는 아주 조금씩 위치를 변경하는 방법에 대해 적어보겠다.
</div>
---

# 01 요소의 위치를 더 미세하게 조절하기 : position

CSS에서 position 속성은 요소의 위치를 조정하는 데 사용된다.  
총 5개의 속성 값이 있으며, 기본 값은 static다.

**static:** 기본값. 일반적인 요소 배치 흐름에 따라 배치된다.  
**fixed:** 뷰포트(화면)의 위치를 기준으로 위치가 고정된다.  
**relative:** 일반적인 요소 배치 흐름에 따라 배치되며, top, right, bottom, left 속성을 사용하여 위치를 상대적으로 조정할 수 있다.  
**absolute:** 가장 가까운 부모 요소 중에 position이 static이 아닌 값을 가진 요소를 기준으로 위치가 결정된다.  
**sticky:** 스크롤 영역 내에서 일반적인 요소 배치 흐름에 따라 배치되며, 스크롤 영역을 벗어날 때 지정된 위치에 고정된다.

## 01-1 position: fixed

**position: fixed** 속성은 요소를 스크롤되더라도 항상 고정된 위치에 두고 싶을 때 사용된다. 이 속성을 사용하면 뷰포트(viewport)를 기준으로 위치를 조정할 수 있다. 이 속성을 적용하면 스크롤되더라도 화면에서 사라지지 않으므로, 네비게이션 메뉴, 광고 배너, 알림 메시지와 같이 화면 상단이나 하단에 고정되어야 하는 요소를 만들 때 유용하다. position: fixed 속성은 top, right, bottom, left 속성과 함께 사용하며, 속성 값으로는 픽셀(px) 또는 비율(%) 등 을 사용할 수 있다.

position: fixed를 적용한 예는 다음과 같다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Fixed Position Example</title>
    <style>
      .banner {
        position: fixed;
        top: 0;
        right: 0;
        background-color: #f5f5f5;
        padding: 10px;
      }
    </style>
  </head>
  <body>
    <div class="banner">
      <h1>Fixed Banner</h1>
      <p>This banner is fixed to the top-right corner of the screen.</p>
    </div>
    <p>
      position: fixed 속성은 요소를 스크롤되더라도 항상 고정된 위치에 두고 싶을
      때 사용된다. 이 속성을 사용하면 뷰포트(viewport)를 기준으로 위치를 조정할
      수 있다. 이 속성을 적용하면 스크롤되더라도 화면에서 사라지지 않으므로,
      네비게이션 메뉴, 광고 배너, 알림 메시지와 같이 화면 상단이나 하단에
      고정되어야 하는 요소를 만들 때 유용하다. position: fixed 속성은 top,
      right, bottom, left 속성과 함께 사용하며, 속성 값으로는 픽셀(px) 또는
      비율(%) 등 을 사용할 수 있다. 따로 요소들의 우선순위를 지정하지 않는 경우
      fixed된 요소가 그렇지 않은 요소 위에 표현된다.
    </p>
  </body>
</html>
```

해당코드를 브라우저에서 확인하면 position: fixed를 적용한 banner가 우측 상단에 고정되어 나타나는 것을 볼 수 있다. 브라우저의 크기를 변경해도 위치가 변하지 않으며, 스크롤해도 이동하지 않는다.

## 01-2 position: relative 와 absolute

이번에는 **position: relative와 absolute**에 대해서 알아보자.

**position: relative**는 해당 요소를 **원래 있던 위치를 기준**으로 이동시킬 때 사용한다. top, bottom, left, right 속성과 함께 사용해서 해당 요소를 이동시킬 수 있다.

**position: absolute**는 해당 요소를 **가장 가까운 부모 요소(position: relative 상태인 부모 요소)를 기준**으로 이동시킬 때 사용한다. 해당하는 부모 요소가 없다면 body를 기준으로 이동한다. relative와 마찬가지로 top, bottom, left, right 속성과 함께 사용해서 해당 요소를 이동시킬 수 있다.

---

# 02 id나 class를 사용하지 않고 특정요소 선택하기: 의사 선택자(pseudo-selector)

**의사 선택자(pseudo-selector)**는 HTML 요소의 상태를 선택할 수 있는 선택자이다. **콜론(:)**으로 표시하며, CSS 규칙의 선택자 부분에 추가해서 사용한다.  
자주 사용되는 의사 선택자로는 **:first-child, :last-child, :nth-child(), :hover, :active, :focus, :visited** 등이 있다.

## 02-1 first-child, last-child, nth-child

**first-child, last-child, nth-child**는 CSS의 선택자(selector) 중 하나로, 해당 요소의 자식 요소 중 특정 조건을 만족하는 요소를 선택할 때 사용된다. 프로젝트를 진행 할 때, 너무 많은 id와 class가 생기는 것을 방지 할 수 있다.

**:first-child:** 해당 요소의 첫번째 자식 요소를 선택한다.

**:last-child:** 해당 요소의 마지막 자식 요소를 선택한다.

**:nth-child(n):** 해당 요소의 n번째 자식 요소를 선택한다.

예를 들어, div에서 7번째 자식을 선택하고 배경색을 red로 지정하고 싶다면 CSS에서 아래와 같이 사용하면 된다.

```css
div:nth-child(7) {
  backgroundcolor: red;
}
```

다음의 코드는 위의 세가지 방법 모두 적용한 예이다.

```css
/* 첫번째 li 요소에 스타일 적용 */
li:first-child {
  color: red;
}

/* 마지막 li 요소에 스타일 적용 */
li:last-child {
  color: blue;
}

/* 2번째, 4번째 li 요소에 스타일 적용 */
li:nth-child(2n) {
  background-color: yellow;
}
```

<div class="notice--info">
<b>짝수, 또는 홀수번 째 요소 선택하는 방법</b><br>
<br>
nth-child(n)를 이용하는 방법으로, n에 해당하는 부분에 수식을 사용하여 원하는 자식 요소를 선택할 수도 있다. <br>
예를 들어, <b>:nth-child(2n)</b>은 해당 요소의 <b>짝수</b>번째 자식 요소를 선택하며, <b>:nth-child(3n+1)</b>은 해당 요소의 <b>1, 4, 7, ...번째</b> 자식 요소를 선택할 때 사용할 수 있다.
</div>

## 02-2 의사 선택자를 사용하지 않고 특정 요소 선택하기: Combinators(조합자)

CSS Combinators(조합자)는 CSS 선택자를 연결하여 복잡한 선택자를 만들 때 사용한다.

아래는 Combinator의 종류와 간단한 설명이다.

### 02-2-1 하위 선택자 (Descendant Selector) : ' ' (띄어쓰기)

첫 번째 선택자의 모든 하위 요소를 선택한다.

```css
div p {
  color: blue;
}
```

div 요소 안에 있는 모든 p 요소의 글자색을 파란색으로 바꾼다.

### 02-2-2 자식 선택자 (Child Selector) : '>'

첫 번째 선택자의 바로 아래 있는 요소를 선택한다.

```css
div > p {
  color: red;
}
```

div 요소 바로 아래 있는 p 요소의 글자색을 빨간색으로 바꾼다.

### 02-2-3 인접 형제 선택자 (Adjacent Sibling Selector) : '+'

첫 번째 선택자의 바로 옆에 있는 형제 요소 중에서 첫 번째와 같은 타입의 요소 하나를 선택한다.

```css
h1 + p {
  font-size: 13px;
}
```

h1 요소 다음에 나오는 p 요소의 글꼴 크기를 13px으로 지정한다.

### 02-2-4 일반 형제 선택자 (General Sibling Selector) : '~'

첫 번째 선택자의 형제 요소 중에서 첫 번째와 같은 타입의 요소 모두를 선택한다.

```css
h1 ~ p {
  text-decoration: underline;
}
```

h1 요소 이후에 나오는 모든 p 요소에 밑줄을 적용한다.

---

# 03 그 외 추가적인 의사 선택자(pseudo-selector) :hover, :active, :focus, :visited

**:hover**: 마우스가 해당 요소 위에 올라가 있을 때 적용된다. 예를 들어, 버튼에 커서를 올리면 배경 색상이 바뀌는 효과를 만들 수 있다.

```css
button:hover {
  background-color: yellow;
  color: black;
}
```

**:active**: 해당 요소가 활성화(active)될 때 적용된다. 예를 들어, 버튼을 클릭하는 동안 색상이 바뀌는 효과를 만들 수 있다.

```css
button:active {
  background-color: green;
  color: white;
}
```

**:focus**: 해당 요소가 포커스(focus)를 받았을 때 적용된다. 예를 들어, 입력 필드에 포커스가 이동하면 테두리가 강조되는 효과를 만들 수 있다.

```css
input:focus {
  border: 2px solid blue;
  outline: none;
}
```

**:focus-within**은 CSS 유효 범위 내에서 포커스가 있는 요소의 부모 요소에 스타일을 적용하는 가상 클래스 선택자이다. 이를 사용하여 입력 요소의 레이블을 스타일링하거나, 포커스가 있는 요소의 부모 요소를 강조하는 등의 디자인을 적용할 수 있다.

간단하게 다음과 같이 사용할 수 있다.

```html
<div class="parent">
  <label for="input">Name:</label>
  <input type="text" id="input" />
</div>
```

```css
.parent:focus-within {
  border: 2px solid blue;
}
```

위 코드는 parent 요소 내의 input 요소(children)가 포커스를 받으면 parent 요소의 테두리에 파란색 테두리가 추가된다. 이때 label 요소를 스타일링하거나, parent 요소 내에 다른 요소들을 스타일링하는 등 다양한 스타일링을 적용할 수 있다.

<div class="notice--danger">
<b>within은 focus에만 적용가능하다.</b>
</div>

**:visited**: 해당 요소가 방문된 상태(visited)일 때 적용된다. 보통 하이퍼링크에 사용되며, 방문한 링크와 아직 방문하지 않은 링크를 구분할 수 있다.

```css
a:visited {
  color: gray;
}
```

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
