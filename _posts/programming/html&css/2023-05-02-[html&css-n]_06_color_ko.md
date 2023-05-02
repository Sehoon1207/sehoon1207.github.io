---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 06 css 색상과 변수" #제목 확인
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

date: 2023-05-02 #날짜 확인
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

CSS에서 색상을 선택하는 방법에 대해 알아보자.

# 01 색상 이름을 지정하는 방법

지금까지 사용한 red, blue, teal등의 색상(color)들은 css에서 지정된 색상 값들의 이름이었다.  
다양한 색상들이 있으며 다음 사이트에서 색상과 이름을 확인할 수 있다.

[색상표보기](https://developer.mozilla.org/en-US/docs/Web/CSS/named-color)

```css
.color1 {
  color: red;
}
.color2 {
  background-color: blue;
}
```

---

# 02 HEX코드를 이용한 방법: 16진수 색상(hexadecial color)

```css
.color1 {
  color: #ff0000; /* 빨강 */
}
.color2 {
  background-color: #00ff00; /* 초록 */
}
```

---

# 03 RGB값을 이용하는 방법

```css
.color1 {
  color: rgb(255, 0, 0); /* 빨강 */
}
.color2 {
  background-color: rgb(0, 255, 0); /* 초록 */
}
```

<div class="notice--info">
<b>RGBA (Red Green Blue Alpha)</b>
<br>
RGB 값에 투명도(Alpha) 값을 추가한 색상 표현 방법인 RGBA (Red Green Blue Alpha)도 있다.<br>
RGB는 빨강, 초록, 파랑의 각각의 색상값을 조합하여 색상을 표현하는 방식인데, 이 방식에 Alpha 값을 추가하여 투명도를 조절할 수 있게 된 것이 RGBA다. Alpha 값은 0 ~ 1 사이의 소수로 표현되며, 0에 가까울수록 투명하고 1에 가까울수록 불투명한 색상을 나타낸다.<br>
<br>
예를 들면, rgba(255, 0, 0, 0)은 빨간색을 나타내지만 Alpha 값이 0이므로 완전히 불투명해 아무것도 안보이게 된다. rgba(0, 0, 255, 0.5)는 파란색을 나타내며, Alpha 값이 0.5(50%)이므로 반투명한 효과가 나타난다.
</div>

---

# 04 색 추출 크롬 확장 도구: ColorZilla

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/05-n_colorZilla.jpg?raw=true" width="1000px"/>

웹사이트에서 마음에 드는 색상을 보았을 때, 색상값을 추출하게 해주는 크롬확장프로그램이다. Color picker라는 다른 프로그램을 많이 쓰는 것으로 알고 있는데, 못찾아서 이걸 쓰고 있다. 나름 쓸만하다.

해당프로그램은 검색하면 바로 나오지만 편의를 위해 여기에 링크도 함께 올렸다.

[colorZilla](https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp)

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
