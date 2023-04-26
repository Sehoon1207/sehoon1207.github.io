---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 02 html문서의 기본 규칙과 태그들" #제목 확인
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

date: 2023-04-26 #날짜 확인
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
      <input id ="name" required placeholder="Name" type="text" />
      <label for="user-name">User Name</label>
      <input id ="user-name" required placeholder="User Name" type="text" />
      <label for="password">Password</label>
      <input id ="password" required placeholder="Password" minlength="10" type="password" />
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
      <input id ="name" required placeholder="Name" type="text" />
      </div>
      <div>
      <label for="user-name">User Name</label>
      <input id ="user-name" required placeholder="User Name" type="text" />
      </div>
      <div>
      <label for="password">Password</label>
      <input id ="password" required placeholder="Password" minlength="10" type="password" />
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
예를 들면 `<header>`,  `<main>`, `<footer>` 등이 있다.  
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
