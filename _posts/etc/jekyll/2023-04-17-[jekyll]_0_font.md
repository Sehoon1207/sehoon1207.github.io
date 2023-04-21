---
layout: single
title: "[jekyll] blog 폰트 크기 변경하기"
folder: "jekyll"
categories:
  - jekyll

tags: [blog, jekyll, minimal-mistakes]

author_profile: true
sidebar:
  nav: "sidebar-category"

# toc: true
# toc_label: "목록"
# toc_icon: "bars"
# toc_sticky: true
classes: wide

use_math: true
typora-root-url: ../

date: 2023-04-17
---

## jekyll blog 폰트 크기 변경하기(minimal-mistakes)

github과 jekyll을 이용하여 블로그를 만들고 보니 네비게이션이나 기타 사용된 폰트가 크다고 느껴졌다.  
전체적인 글자 크기를 조절하는 방법은 다음과 같다.

### 1. \_reset.scss 파일 수정하기 (minimal-mistakes 기준)

글자 크기를 변경하기 위해서는 \_reset.scss파일 내에 몇가지 숫자만 변경하면 간단하게 가능하다.

해당파일은 /\_sass/minimal-mistakes/\_reset.scss 이 경로에 위치하고 있으며 열어보면 다음과 같이 보일 것이다.

```scss
* {
  box-sizing: border-box;
}

html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 16px; // normal

  @include breakpoint($medium) {
    font-size: 18px;
  }

  @include breakpoint($large) {
    font-size: 20px;
  }

  @include breakpoint($x-large) {
    font-size: 22px;
  }

  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
```

수정을 하기 전에는 아마도 위와 같이 폰트들의 크기가 16, 18, 20, 22px로 되어 있을 것이다.

첫번째가 기본 폰트 크기(16px)로 일반적으로 모바일에서 볼 수 있는 크기이다.

나머지 세가지 크기(18,20,22px)는 PC에서 윈도우의 크기에 따라 medium, large, x-large로 구분하고 그에 맞추어 폰트의 사이즈를 변경하도록 되어 있다.

따라서 해당부분에 원하는 만큼의 크기로 수정하면 적용된다.

나의 경우에는 모든 크기를 2px정도씩 줄였다. (14,16,18,18px)
