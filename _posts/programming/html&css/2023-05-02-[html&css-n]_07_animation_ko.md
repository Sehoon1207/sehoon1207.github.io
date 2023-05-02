---
layout: single # 새로운 포스트 작성시 확인할 것
title: "[html&css-n] 07 css로 간단한 애니메이션 만들기" #제목 확인
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

# 01 transition

CSS의 transition 속성은 요소의 상태 변화에 따라서 부드러운 애니메이션 효과를 주는 방법이다. 이 속성을 이용하면 CSS 속성값의 변화를 일정 시간 동안 부드럽게 처리할 수 있다.

transition 속성에는 대상 속성(property), 지속시간(duration), 변화유형(function)을 설정할 수 있다.

예를 들면, 아래 코드는 hover 상태에서 background-color 속성이 0.5초 동안 부드럽게 바뀌는 애니메이션을 구현한 것이다.

```css
.box {
  background-color: #ccc;
  transition: background-color 0.5s ease-in-out;
}

.box:hover {
  background-color: #ff0;
}
```

이 코드에서 transition 속성은 background-color 속성이 변할 때, 0.5초 동안 부드럽게 애니메이션을 처리한다는 것을 의미한다. ease-in-out는 변화유형을 지정하는데, 이는 처음과 끝에서는 느리게, 중간에서는 빠르게 변경되도록 하는 함수이다.

변화 유형에는 ease-in-out외에도 ease-in, ease-out, linear 등의 값이 있다.

**ease-in-out** : 기본값으로, 느리게 시작해서 중간에 빨라졌다가 느려진다.  
**ease-in** : 천천히 시작해서 점점 빨라진다.  
**ease-out** : 빠르게 시작해서 천천히 끝나며 느려진다.  
**linear** : 등속운동처럼 일정한 속도로 변화한다.

ease-in-out에 대한 설정을 더 세밀하게 만들고 싶다면 아래 사이트에 가보자.

[ease-in_function](https://matthewlein.com/tools/ceaser)

<div class="notice--info">
이 외에도 cubic-bezier() 함수를 사용해 사용자가 직접 커스텀한 값으로 애니메이션을 지정할 수도 있다.
</div>
<div class="notice--info">
또한 transition 속성은 CSS 속성 중 많은 속성에 적용될 수 있다. <br>
예를 들어, color, font-size, border-radius, transform 등등의 속성에 모두 적용될 수 있다.
</div>

---

# 02 transformation

CSS transformation은 요소의 크기, 위치, 회전, 기울기 등을 변경하여 2D 또는 3D 애니메이션 효과를 만들 수 있는 CSS 속성이다.

transformation은 요소에 대한 변형을 나타내며, 변형의 기준점은 transform-origin 속성으로 설정할 수 있다. transformation은 다음과 같은 함수를 사용하여 구현한다.

**translate()** : 요소를 이동시킨다.  
**rotate()** : 요소를 회전시킨다.  
**scale()** : 요소의 크기를 변경한다.  
**skew()** : 요소를 기울인다.

또한, transformation을 함께 사용할 수 있는 다른 속성으로는 transform-origin, transform-style, perspective 등이 있다.

아래는 transformation을 사용한 간단한 예시 코드다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Transformation Example</title>
    <style>
      .box {
        width: 100px;
        height: 100px;
        background-color: red;
        transform: translateX(100px) rotate(45deg);
        transform-origin: bottom right;
      }
    </style>
  </head>
  <body>
    <div class="box"></div>
  </body>
</html>
```

위 코드를 실행하면, 가로 100px, 세로 100px 크기의 빨간색 박스를 생성한 후, transform: translateX(100px) rotate(45deg); 를 적용하여 오른쪽으로 100px 이동시키고 45도 회전시킨 결과를 보여준다.

예제 외에도 더 다양한 방법을 보고 싶다면, 아래의 링크에서 확인하자.

[mozillaMDN](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)

# 03 animation

앞서 해보았던 transition과 transformation은 focus나 hover등을 이용해 하나의 상태에서 다른 상태로 바뀌는 것만 가능했다. 그래서 계속 반복하게 하려면 다른 방법이 필요하다. 그 중 하나가 @keyframes를 이용한 방법이다.

@keyframes를 이용한 animation은 CSS에서 요소(element)에 대해 애니메이션을 적용할 수 있는 방법 중 하나로 @keyframes 규칙은 애니메이션에 대한 세부 정보를 정의하며, 애니메이션을 실행하려는 요소에 애니메이션 속성을 추가하는 방식으로 작동한다.

@keyframes를 이용해서 정의하는 방법으로는 두가지가 있는데 다음과 같다.

## 03-1 from to로 정의하는 방법

```css
@keyframes animationName {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(360deg);
  }
}
```

## 03-2 단계별(%)로 정의하는 방법

```css
@keyframes animationName {
  0% {
    left: 0px;
    top: 0px;
  }
  25% {
    left: 200px;
    top: 0px;
  }
  50% {
    left: 200px;
    top: 200px;
  }
  75% {
    left: 0px;
    top: 200px;
  }
  100% {
    left: 0px;
    top: 0px;
  }
}
```

아래의 예제코드를 실행하면 5원짜리 동전이 계속해서 회전하는 것을 볼 수 있다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Coin Flip Animation</title>
    <style>
      .coin {
        width: 300px;
        height: 300px;
      }

      @keyframes flip {
        from {
          transform: rotateY(0deg);
        }
        to {
          transform: rotateY(360deg);
        }
      }

      .coin img {
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
        animation: flip 3s ease-in-out infinite;
      }
    </style>
  </head>
  <body>
    <div class="coin">
      <img
        src="https://m.화폐수집.com/web/product/big/202201/8a5e8b7b307c5cebe653ee4a6875cfd6.png"
      />
    </div>
  </body>
</html>
```

---

## 03-3 애니메이션 지연시키기

animation-delay는 CSS animation 속성에서 지연시간을 조정하는 속성이다. 이 속성을 사용하면 애니메이션 시작 전에 대기하는 시간을 설정할 수 있다.

animation-delay 속성값은 초(second) 또는 밀리초(millisecond)로 지정하며, 음수값도 사용이 가능하다. 음수값을 사용하면 애니메이션이 시작하기 전에 이미 시작된 것처럼 보이게 할 수 있다.

예를 들어, 다음과 같이 animation-delay 속성을 사용하여 애니메이션이 2초 후에 시작되도록 설정할 수 있다.

```css
.animationbox__bar:nth-child(2) {
  animation-delay: 2s;
}
```

만약에 animationbox\_\_bar가 여러개가 있는데 그 중에 2번째 요소만 늦게 시작하게 만들고 싶다면 위와 같이 만들면 된다. 이와 같이 응용하면 계단식으로 차례대로 애니메이션이 시작하도록 만들 수도 있다.

css를 이용한 애니메이션은 다양한 방법으로 만들 수 있기 때문에 인터넷을 통해 검색해서 찾는 것이 더 좋다.

몇가지 참고에 유용한 사이트는 여기에 링크로 남겨둔다.

[animista](https://animista.net/)

[mozillaMDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)

[Animate.css](https://animate.style/)

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
