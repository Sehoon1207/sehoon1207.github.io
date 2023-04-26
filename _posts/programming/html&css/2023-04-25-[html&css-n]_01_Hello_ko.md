---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 01 Hello출력 및 기본설정 그리고 태그" #제목 확인
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

date: 2023-04-25 #날짜 확인
---

<div class="notice--info">
“Während ich studiere, schreibe ich hier kurze Zusammenfassungen für eine längere Erinnerung.”<br>
"공부하면서 더 오래 상기시키기 위해 여기에 짧은 요약을 씁니다."<br>

<pre>
OS    : Window
Editor: VScode</pre>
</div>

<div class="notice--danger">
 ### 기본 유의사항<br>
<br>
1. 파일의 경로에 유의할것.(예. 프로젝트 폴더와 생성한 파일 경로 불일치 등.)<br>
2. 폴더명과 파일명은 소문자로 작성할것.<br>
3. 새파일 작성 시 확장자명에 유의할것.(html인지 css인지)

</div>

# 01 home.html

`(workfolder)/home.html`

위와 같이 작업하고 있는 곳에 첫 html파일을 만들어보자.  
그리고 해당 파일에 아래 텍스트를 입력한다.

```html
Hello! This is my first HTML file! Nice to meet you!
```

입력했으면 꼭 저장할 것. (VS code 사용자는 저장을 안할 경우, 파일명 옆에 동그란 점이 표시되어있음.)
그리고 바로 실행.(윈도우 사용자면 파일탐색기에서 더블클릭!)

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_home.jpg?raw=true" width="1000px">

내가 적은 텍스트가 크롬(또는 microsoft edge 등)의 화면 맨 위에 나타난다.
이 방법이 성공했으면 이 다음부터는 코드만 바뀔 뿐 동일하게 실행하면 된다.

# 02 VS Code 확장 프로그램

VS Code에서 편하게 작업하기 위한 몇가지 확장(Extention)들에 대해 알아보자.  
여기에 적어두는 확장프로그램들은 필수가 아니므로 필요한 경우에만 install하면 된다.

## 02-1 Community Material Theme

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_comunitymaterialtheme.jpg?raw=true" width="1000px">

VS Code의 테마를 변경시켜줌. 제공하는 여러가지 테마가 있으며 코드를 더 쉽게 알아볼 수 있도록 하이라이팅 색상도 바꿔준다. 몇가지 적용해 보고 나한테 맞는 것으로 설정하자.(개인적으로는 검정색 바탕을 추천한다.. 오랫동안 하얀 바탕의 화면을 보면 눈이 아프기 때문)

## 02-2 Material Icom Theme

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_material.jpg?raw=true" width="1000px">

아이콘의 모양을 변경시켜주는 확장프로그램. 해당 프로그램을 설정하면 VS코드 왼쪽에 나타나는 Explorer의 조그많한 아이콘들이 조금 더 보기 쉽게 변경된다. 아이콘만 봐도 파일의 확장자가 쉽게 눈에 들어온다.

## 02-3 WakaTime

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_WakaTime.jpg?raw=true" width="1000px">

얼마나 내가 코딩을 했는지 알려주는 확장 프로그램. 많은 사람들이 깃헙을 이용해서 잔디심기 챌린지 같은 것을 하지만. 이 확장프로그램도 꽤나 좋다고 생각한다.
내가 실질적으로 코딩한 시간을 측정해주기도 하고 각종 통계도 내준다. 동기부여에도 도움이 된다.

## 02-4 Prettier

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_prettier.jpg?raw=true" width="1000px">

html과 css등 몇가지 확장자의 프로그래밍 작업에서 코드를 보기 좋게 정렬해주는 확장 프로그램. 이 프로그램을 사용하면 파일을 저장할 때마다 내가 작성한 코드를 자동으로 보기좋게 정렬해준다. 그리고 몇가지 자주 실수하는 부분(예를 들면 / 를 빼먹는 것과 같은)을 자동으로 수정해준다.

# 03 첫 html파일, 첫 tag 만들기

앞서해본 home은 단순한 텍스트를 썻을 뿐 html파일이라고 하기 어렵다.
html에는 다른 프로그램 언어들 처럼 여러가지 규칙들이 존재하고 그것을 지켜야 브라우저에 제대로 표현된다.
html에서 많이 사용하는 tag에 대해알아보자.

## 03-1 tag란?

HTML 태그는 웹 페이지의 구조와 내용을 정의하는 데 사용되는 마크업 언어의 요소다.  
각 태그는 <> 꺾쇠 괄호 안에 기재되고, 대소문자를 구분하지 않는다.

가장 기본적인 HTML 태그는 **\<html>**, **\<head>**, **\<title>**, **\<body>** 들이 있다.

**\<html>** 태그는 문서가 HTML로 작성되었다는 것을 지정하는 것 보통 첫줄에 넣는다  
**\<head>** 태그는 문서의 메타데이터와 스타일 시트를 포함하는 부분을 묶는다.  
**\<title>** 태그는 문서의 제목을 정의하며,  
**\<body>** 태그는 웹 페이지의 본문 내용을 정의한다.

그 외에도 다양한 HTML 태그들이 있고, 이를 이용하여 텍스트, 이미지, 링크, 리스트, 표, 폼 등 다양한 요소들을 추가하고 구성할 수 있다.

예를 들어,

**\<p>** 태그는 문단을 정의하며,  
**\<img>** 태그는 이미지를 추가한다.  
**\<a>** 태그는 링크를 추가하며,  
**\<ul>**과 **\<ol>** 태그는 `각각 순서 없는 리스트`와 `순서 있는 리스트`를 정의한다.

HTML 태그는 여러 속성을 가질 수 있고, 이를 이용하여 추가적인 정보와 스타일을 지정할 수 있다.

예를 들어,
**\<img>** 태그는 **src, alt, width, height** 등 다양한 속성을 가질 수 있다.

tag들을 단순히 나열해서 설명했기 때문에 이해가 힘들 수 있다. 단순히 그렇구나 하고 지나가면 된다.

## 03-2 tag 적용해보기

앞서 만들었던 home.html에 태그를 만들어 보자. 기존에 작성했던 텍스트는 모두 삭제 하고 깨끗한 상태로 해보자.

```html
<fruit>사과</fruit> 포도, 배
```

꺽쇠를 이용해서 나만의 태그로 \<fruit>를 만들어 보았다.
태그는 앞뒤로 적어주되 뒤에는 `/`을 추가해서 닫았음을 표기한다.
해당 태그는 내가 임의로 만들었기 때문에 브라우저에서 보아도 특별한 변화는 없다. 단순히 내가 적은 "사과"라는 텍스트가 보일 뿐이다.

```html
<fruit>사과</fruit> 포도, 배
<a href="https://sehoon1207.github.io/"> welcome to IS </a>
```

태그를 하나 더 밑에 추가해보자. <a>태그는 내가 만든 태그가 아닌 규칙이 정해져있는 태그이다.
해당 태그는 href라는 속성을 가지기 때문에 태그 시작부분에 추가할 수 있다. 임의의 이름의 속성을 만들어서 적는다고 추가할 수 있는 것은 아니다.
추가한 후 저장하고 다시 home.html파일을 열어보면 "wlcome to Is"라는 링크가 생겼음을 확인 할 수 있다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_tag.jpg?raw=true" width="1000px">

브라우저에서 해당 링크를 누르면 내 블로그 첫페이지로 가는 것을 확인 할 수 있다.

다른 태그인 \<h1>도 써보자.

```html
<fruit>사과</fruit> 포도, 배
<a href="https://sehoon1207.github.io/"> welcome to IS </a>
<h1>Hello this is my website!</h1>
```

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_tag_h1.jpg?raw=true" width="1000px">

h1태그를 사용하면 일반 폰트보다 더 굵고 큰 폰트로 변경이 되었음을 볼 수 있다.
h1태그도 a 처럼 규칙이 정해져 있다는 것이다. 하지만 이러한 규칙이 있는 태그를 전부 외울 필요는 없다.
필요한 태그만 찾아서 사용하면 된다.

## 03-3 \<ul>과 \<ol>, \<li> 태그 사용해보기

이제부터는 태그를 하나씩 써보면서 익혀보도록 하자.
앞서 tag설명에도 있었던 \<ul>과 \<ol>, \<li> 태그들을 사용해보자.
태그를 열고 닫는 것에 주의하면서 작성하자.

```html
장보기
<ul>
  <li>쌀</li>
  <li>고기</li>
  <li>우유</li>
</ul>

하루일과
<ol>
  <li>일어나기</li>
  <li>밥먹기</li>
  <li>공부하기</li>
</ol>
```

위의 코드를 작성하면 브라우저에서 아래와 같이 나타난다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_tag_ul.jpg?raw=true" width="1000px">

ul과 ol 두개 모두 항목을 작성하는 태그이다. 차이점은 그 안에 있는 항목들(li태그, list)이 번호가 있는지 없는지 차이일 뿐이다.

<div class="notice--info">
<h4>* ul(Unordered List), ol(Ordered List), li(List Item)</h4><br>
ul(Unordered List)과 ol(Ordered List)은 리스트를 나타내는 태그이며, li(List Item)는 리스트 항목을 나타내는 태그다.<br>
ul 태그는 정렬되지 않은 항목 목록을 나타내며,<br>
ol 태그는 정렬된 항목 목록을 나타내고,<br>
li 태그는 항목을 나타내는 태그이다.
ul과 ol은 기본적으로 다른 모양으로 나열되지만, 추후에 CSS를 사용하여 스타일을 변경할 수 있다.
</div>

## 03-4 \<a> 태그 사용해보기

a태그는 앞서 사용해 봤던 것 처럼 링크를 만들어 주는 태그이다.
하지만 속성(attribute)에 대해서 추가로 이야기 하기 위해서 다시 사용해 보자.

```html
<a> 1 welcome to IS </a>
<a href="https://sehoon1207.github.io/"> 2 welcome to IS </a>
<a href="https://sehoon1207.github.io/" target="_self"> 3 welcome to IS </a>
<a href="https://sehoon1207.github.io/" target="_blank"> 4 welcome to IS </a>
```

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_tag_a.jpg?raw=true" width="1000px">

비슷해 보이는 이 4줄의 코드를 코딩하고 home.html을 브라우저로 열어서 하나씩 눌러보면서 어떤 차이가 있는지 알아보자.

첫번째 태그는 링크가 생기지 않았고 당연히 눌러도 변화가 없다.  
두번째 태그는 링크가 생겼고 누르면 herf 속성에서 적어준 페이지로 간다.  
세번째 태그는 링크가 생겼고 마찬가지로 링크된 페이지로 간다.  
네번째 태그는 링크가 생겼고 누르면? 브라우저에 `새로운 탭이 열리고 그 탭에 링크된 페이지`가 열린다.

따라서 a태그에서 href 속성이 없으면 링크가 형성이 안되고 단순이 텍스트가 될 뿐이며, target이라는 새로운 속성에 따라 현재 페이지에서 링크된 사이트로 갈지 새로운 탭에서 링크된 사이트가 열릴지를 정하는 것이다.  
a태그로 링크를 하나 만들더라도 속성을 추가하는 것에 따라 추가적인 정보나 규칙을 부여할 수 있는 것이다.

## 03-5 \<img /> 태그 사용해보기(self-closing tag)

\<img /> 태그는 HTML에서 이미지를 삽입할 때 사용하는 태그다.  
주의할 점은 img는 **self-closing tag**라서 지금까지 해왔던 `<img> xxx </img>`이런 방법으로 사용하지 않는다.  
self-closing 태그는 `<img attribute="" />` 이렇게 사용하는 것이 올바른 방법이다.  
이 태그는 반드시 src 속성을 가져야 하며, 이 속성은 이미지 파일의 경로를 지정한다.  
(마치 a태그의 href와 비슷한)

이미지의 크기를 조정하기 위해 width와 height 속성을 사용할 수 있다.
또한, 대체 텍스트를 제공하기 위해 alt 속성을 사용할 수도 있다.
alt 속성은 이미지를 불러오지 못할 경우에 대체하여 보여줄 텍스트를 지정하는 속성이다.

```html
<img src="" width="1000px" />
```

img태그를 사용해 보기 위해 위와 같이 작성해본다.  
img태그는 수많은 속성들 중에서도 필수인 속성 src(source)와 width속성을 사용해 보았다.  
저렇게 작성 후에는 인터넷 상에 있는 아무 이미지나 우클릭해서 "이미지 주소 복사"를 누른다.

<img src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_tag_img.jpg?raw=true" width="1000px">

참고를 위해 내 포스트의 이미지를 올려보았다.
복사한 주소는 src의 "" 사이에 붙여서 넣어준다(윈도우의 경우 ctrl + V)

```html
<img
  src="https://github.com/Sehoon1207/sehoon1207.github.io/blob/main/_posts/programming/html&css/imgs/01-n_tag_img.jpg?raw=true"
  width="1000px"
/>
```

그러면 위와 같은 코드가 되고 home.html을 브라우저로 열어서 확인해 보면 이미지가 1000px의 너비로 나타나는 것을 볼 수 있다.

추가로 보여주고자 하는 이미지를 local내에 자신이 가지고 있다면, 해당 주소를 넣어서 보여주는 것도 가능하다. 하지만 가지고 있는 이미지를 넣을 때는 이미지 경로(path notation)에 유의하도록 하자.

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
