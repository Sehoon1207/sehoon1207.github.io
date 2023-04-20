---
layout: single
title: "[jekyll] Notice(텍스트 강조)"
folder: "jekyll"
categories:
  - jekyll

tags: [blog, jekyll]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "목록"
toc_icon: "bars"
toc_sticky: true
classes: wide

use_math: true

date: 2023-04-20
---

간단한 단어 같은 부분은 하이라이트나 코드블럭으로 처리하는 방법이 있지만
minimal-mistakes를 이용한다면 notice 블럭을 쉽게 만들 수 있다.
기본 6개의 타입이 있고 추가도 가능하다고 한다.

6개의 Notice 타입은 아래와 같다.

**Default, Primary, Info, Warning, Success, Danger**

\<input>

```
Default
{: .notice}

Primary
{: .notice--primary}

Info
{: .notice--info}

Warning
{: .notice--warning}

Success
{: .notice--success}

Danger
{: .notice--danger}

```

\<output>

Default
{: .notice}

Primary
{: .notice--primary}

Info
{: .notice--info}

Warning
{: .notice--warning}

Success
{: .notice--success}

Danger
{: .notice--danger}
