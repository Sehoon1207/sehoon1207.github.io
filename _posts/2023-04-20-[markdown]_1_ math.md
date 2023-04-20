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

# 4. 괄호 크기조절

\<input>

```
$(\frac{1}{\frac{1}{3}})$
```

\<output>

$(\frac{1}{\frac{1}{3}})$

일반적인 괄호를 사용하면 위와 같이 크기가 잘 맞지 않기 때문에 해당 부분의 앞뒤에 left와 right를 넣어서 크기를 조절 가능하다.

\<input>

```
$\left(\frac{1}{\frac{1}{3}}\right)$
```

\<output>

$\left(\frac{1}{\frac{1}{3}}\right)$

또한 고정된 크기를 사용하는 방법도 있다.
고정된 크기는 Bigg, bigg, Big, big, 종류가 있으며, 괄호를 그냥 사용시 normal 크기이다.

```
$\Bigg(  Bigg \Bigg), \bigg(  bigg \bigg), \Big(  Big \Big), \big(  big \big), ( normal )$
```

\<output>

$\Bigg(  Bigg \Bigg), \bigg(  bigg \bigg), \Big(  Big \Big), \big(  big \big), ( normal )$

---

# 5. 줄임 및 생략 표기방법 (점, dot)

## 가로 표기

\<input>

```
$\dots$
```

\<output>

$\dots$

## 가로 표기 (가운데 정렬)

\<input>

```
$\cdots$
```

\<output>

$\cdots$

## 세로 표기

\<input>

```
$\vdots$
```

\<output>

$\vdots$

## 대각선 표기

\<input>

```
$\ddots$
```

\<output>

$\ddots$

---

# 6. 루트(Root)표기 방법

\<input>

```
$\sqrt{3}$
```

\<output>

$\sqrt{3}$

---

# 7. 팩토리얼(Factorial)표기 방법

\<input>

```
$n!$
```

\<output>

$n!$

## Product 표기법

\<input>

```
$n! = \prod_{k=1}^n k$
```

\<output>

$n! = \prod_{k=1}^n k$

# 8. 시그마 표기 방법

\<input>

```
$\sum_{i=1}^{10} t_i$

$\displaystyle\sum_{i=1}^{10} t_i$
```

\<output>

$\sum_{i=1}^{9} t_i$

$\displaystyle\sum_{i=1}^{9} t_i$

---

# 9. 극한(limit) 표기

\<input>

```
$\lim_{x \to \infty} \frac{1}{x} = 0$
```

\<output>

$\lim_{x \to \infty} \frac{1}{x} = 0$

---

# 10. 미분과 적분(differential and integral) 표기

## 미분(프라임)

\<input>

```
$f'(x)$
```

\<output>

$f'(x)$

## 미분(dx, dy)

\<input>

```
$\frac{d}{dx} f(x)$

$\displaystyle \frac{d}{dx} f(x)$

```

\<output>

$\frac{d}{dx} f(x)$

$\displaystyle \frac{d}{dx} f(x)$

## 편미분

\<input>

```
$\frac{\partial}{\partial x} f(x, y)$

$\displaystyle \frac{\partial}{\partial x} f(x, y)$

```

\<output>

$\frac{\partial}{\partial x} f(x, y)$

$\displaystyle \frac{\partial}{\partial x} f(x, y)$

## 적분

\<input>

```
$\int _{-\infty} ^{x} {f(t)}$

$\displaystyle \int _{-\infty} ^{x} {f(t)}$

```

\<output>

$\int _{-\infty} ^{x} {f(t)}$

$\displaystyle \int _{-\infty} ^{x} {f(t)}$

---

# 11. 공식에 번호 매기기

논문이나 책 등을 보면 공식끝에 번호를 매기는데 `\tag{number}`를 이용하면 동일하게 표현된다.

\<input>

```
$(x+y)^2=x^2+2xy+y^2 \tag{1}$
```

\<output>

$(x+y)^2=x^2+2xy+y^2 \tag{1}$

# 12. 행렬

\<input>

```
$$X_{m,n} =
 \begin{pmatrix}
  x_{1,1} & x_{1,2} & \cdots & x_{1,n} \\
  x_{2,1} & x_{2,2} & \cdots & x_{2,n} \\
  \vdots  & \vdots  & \ddots & \vdots  \\
  x_{m,1} & x_{m,2} & \cdots & x_{m,n}
 \end{pmatrix}$$

```

\<output>

$X_{m,n} =$

$$
 \begin{pmatrix}
  x_{1,1} & x_{1,2} & \cdots & x_{1,n} \\
  x_{2,1} & x_{2,2} & \cdots & x_{2,n} \\
  \vdots  & \vdots  & \ddots & \vdots  \\
  x_{m,1} & x_{m,2} & \cdots & x_{m,n}
 \end{pmatrix}
$$

# 13. 스칼라, 벡터 (Scalar, Vector)

\<input>

```
$\overline{AB}$

$\vec{AB}$

$\overrightarrow{AB}$
```

\<output>

$\overline{AB}$

$\vec{AB}$

$\overrightarrow{AB}$

# 14. 줄맞춤 (align)

여러 줄의 수식을 정렬하고 싶다면 다음과 같이 `\begin{align}`, `\end{align}` 사이에 &과 \\[줄간격] (\\[0.5em])를 써 주면 된다.

# 15. 조건 분기 (cases)

조건 분기를 만들고 싶다면 `\begin{cases}`, `\end{cases}` 사이에 &과 \\를 써 주면 된다.  
&는 열을 구분하고 \\은 행을 구분한다.

---

참고
Quelle:
<https://wikieducator.org/Help:LaTeX_Symbol_Tables_-_Mathematics>
