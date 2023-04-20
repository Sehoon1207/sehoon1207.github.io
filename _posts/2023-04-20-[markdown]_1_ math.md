---
layout: single
title: "[Markdown] 수학기호 및 수식"
folder: "markdown"
categories:
  - markdown

tags: [blog, markdown]

author_profile: true
sidebar:
  nav: "sidebar-category"

toc: true
toc_label: "목록"
toc_icon: "bars"
toc_sticky: true
classes: wide

use_math: true

date: 2023-04-17
---

# 0. 마크다운 문법 정리

이곳은 마크다운(md형식)의 문법 특히 수학적인 부분을 정리한 곳이다.
LaTex와 거의 동일하다. 다른부분이 있는지 모르겠다.
새롭게 확인되는 대로 추가할 예정이다.
`아래는 MathJax를 적용 했을 때의 결과들이다.`

---

# 1. 사칙연산

사칙연산은 수식의 시작과 끝에 $를 붙여주면서 간단하게 표현 가능하다.
간단한 수식의 경우, 사실 곱셈과 나눗셈을 제외하고는 특별히 다른 부분은 없다.

---

## 덧셈

\<input>

```
$1+1=2$
```

\<output>

$1+1=2$

---

## 뺄셈

\<input>

```
$2-1=1$
```

\<output>

$2-1=1$

---

## 곱셈

곱셈에는 `\times` 사용.

\<input>

```
$2 \times 2=4$
```

\<output>

$2 \times 2=4$

---

## 나눗셈

나눗셈에는 `\div` 사용.

\<input>

```
$4 \div 2=2$
```

\<output>

$4 \div 2=2$

---

# 2. 분수의 표현(fraction)

\<input>

```
$\frac{1}{3}$
```

\<output>

$\frac{1}{3}$

또는

\<input>

```
$^1/_3$
```

\<output>

$^1/_3$

---

# 3. 아래/위 첨자

아래 첨자는 `_` 위 첨자는 `^` 사용.

\<input>

```
$X_1^2$
```

\<output>

$X_1^2$

또는 `중괄호({})`로 묶어서 표현

\<input>

```
${X_{1,a}}^{20}$
```

\<output>

${X_{1,a}}^{20}$

---

# 9. 공식에 번호 매기기

논문이나 책 등을 보면 공식끝에 번호를 매기는데 `\tag{number}`를 이용하면 동일하게 표현된다.

\<input>

```
$(x+y)^2=x^2+2xy+y^2 \tag{1}$
```

\<output>

$(x+y)^2=x^2+2xy+y^2 \tag{1}$
