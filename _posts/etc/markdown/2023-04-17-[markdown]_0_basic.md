---
layout: single
title: "Markdown 문법정리"
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

date: 2023-04-17
---

## 마크다운 문법 정리

이곳은 마크다운(md형식)의 문법을 정리한 곳이다.
새롭게 확인되는 대로 추가할 예정이다.

---

### 1. 제목(header)

h1 부터 h6까지 제목 표현

```
# <h1제목>
## <h2제목>
### <h3제목>
#### <h4제목>
##### <h5제목>
###### <h6제목>
```

---

### 2. 강조표현

마크다운도 일반적인 문서들처럼 강조표현이 가능하다.

| 종류     | 방법                                                                                          |
| -------- | --------------------------------------------------------------------------------------------- |
| 이텔릭체 | 해당 단어 또는 문장의 시작과 끝에 \_언더바(underscore)\_ 또는 \*별표(asterisks)\*             |
| 볼드체   | 해당 단어 또는 문장의 시작과 끝에 \_\_언더바(underscore)x2\_\_ 또는 \*\*별표(asterisks)x2\*\* |
| 취소선   | 해당 단어 또는 문장의 \~\~물결(tilde)x2\~\~                                                   |

---

### 3. 목록(list)

순서가 필요하지 않은 목록에는 -,\*,+ 로 표기 가능하다.

- \- 대쉬(hyphen)
- \* 별표(asterisks)
- \+ 더하기(plus sign)

---

### 4. 링크(link)

일반적으로 문서 내의 url이나 꺽쇠 괄호를 이용하면 자동으로 링크가 생긴다.
대괄호[]를 이용하여 표시할 이름을 적고 괄호()를 이용하여 해당 링크를 적는다.
작성하는 문서 내에서 이동할 링크를 만드는 방법도 가능하다: #이동할 헤드 제목
다만, 제목에 공백 또는 띄어쓰기 한 경우에는 '-'로 채워주어야 한다.

\<input>

```
 구글 : https://www.google.com

 네이버 : <https://www.naver.com>

 \[링크이름](url주소)

 [마크다운 문법 정리](#마크다운-문법-정리)
```

\<output>

구글 : <https://www.google.com>

네이버 : <https://www.naver.com>

[링크이름](url주소)

[마크다운 문법 정리](#마크다운-문법-정리)

---

### 5. 각주(footnote)

각주를 사용하고 싶은 경우 아래와 같이 사용한다.
(추후에 예시 추가)

\<input>

```md
각주[^id]
[^id]: 각주설명
```

---

### 6. 드롭다운 기능(접기)

\<input>

```
<details><summary>옆에 삼각형 모양을 눌러주세요</summary>
추가적인 메모가 가능합니다.
</details>
```

\<output>

<details><summary>옆에 삼각형 모양을 눌러주세요</summary>
추가적인 메모가 가능합니다.
</details>

---

### 7. 특수문자 사용

마크다운 문서를 작성하다 보면 몇몇 특수문자(\*,\_)를 사용 할 때 마크다운 문법때문에 불가능한 경우가 있다.
그럴 때 backslash '\'를 사용하면 가능하다.

\<input>

```
\*이렇게 하면 안됩니다
- 이렇게 해도 안되요.
\* 이렇게 하면 잘 나옵니다
\_ 참 쉽죠
```

\<output>

- 이렇게 하면 안됩니다.

* 이렇게 해도 안되요.

\* 이렇게 하면 잘 나옵니다
\_ 참 쉽죠

---

### 8. 이미지 넣고 활용하기

마크다운 문서에 이미지를 넣는 방법은 아래와 같다.

\<input>

```md
![Alt text](파일경로)
![Alt text](파일경로 "title")
```

\<output>

![Alt text](https://www.markdownguide.org/assets/images/markdown-guide-og.jpg)

#### 1) 이미지의 크기를 지정하는 방법

\<input>

```md
<img src="https://www.markdownguide.org/assets/images/markdown-guide-og.jpg" width="500" height="300">
```

\<output>

<img src="https://www.markdownguide.org/assets/images/markdown-guide-og.jpg" width="500" height="300">

#### 2) 이미지의 비율을 지정하는 방법

\<input>

```md
<img src="https://www.markdownguide.org/assets/images/markdown-guide-og.jpg" width="30%" height="30%">
```

\<output>

<img src="https://www.markdownguide.org/assets/images/markdown-guide-og.jpg" width="30%" height="30%">

---

### 9. 수평선(가로 구분선) 그리기

--- 또는 \*\*\* , \_\_\_ 를 입력하면 쉽게 가로 구분선을 그릴 수 있다.

### 10. 줄바꿈 하기

줄바꿈의 경우 문장의 끝에 간단히 spacebar로 2번이상 띄어주면 된다.

\<input>

```md
줄바꿈의 경우 문장의  
끝에 간단히 spacebar로  
2번이상 띄어주면 된다.
```

\<output>

줄바꿈의 경우 문장의  
끝에 간단히 spacebar로  
2번이상 띄어주면 된다.

---

### 10. 표 만들기

헤더 셀을 구분할 때 3개 이상의 -(hyphen/dash) 기호가 필요
헤더 셀을 구분하고 양끝에 :(Colons) 기호를 추가 하는 것으로 해당 열 또는 칸의 내용이 어느 쪽으로 정렬시킬 지 정할 수 있다.

\<input>

```
| 없음 | 좌측정렬 | 가운데정렬 | 우측정렬 |
| ---| :--- | :---: | ---: |
| 바나나 | 사과 | 포도 | 오렌지 |
```

\<output>

| 없음   | 좌측정렬 | 가운데정렬 | 우측정렬 |
| ------ | :------- | :--------: | -------: |
| 바나나 | 사과     |    포도    |   오렌지 |

---

### 11. 코드블럭(code block)

마크다운 문서에서 코드부분을 시각적으로 표현할 때 코드블록을 많이 사용한다.
해당 코드의 시작 끝에 ```를 이용하면 블록처리된다.

또한 특정 언어를 강조하고 싶다면 시작점의 ```입력후 바로 해당 언어를 적어주면 코드블록 내의 코드가 하이라이트 된다.
아래는 강조가 가능한 언어리스트이다.
더 많은 언어들도 지원 가능하니 목록에 안보이더라도 한번 써보는 것도 좋다.

| 언어      | Markdown | 언어       | Markdown   |
| --------- | -------- | ---------- | ---------- |
| Bash      | bash     | JSON       | json       |
| C#        | cs       | Java       | java       |
| C++       | cpp      | JavaScript | javascript |
| CSS       | css      | PHP        | php        |
| Diff      | diff     | Perl       | perl       |
| HTML, XML | html     | Python     | python     |
| HTTP      | http     | Ruby       | ruby       |
| Ini       | ini      | SQL        | sql        |

활용방법은 아래와 같다.

\<input>

````md
```Language type
code
```
````

\<output>

```
  code
```

ex. c언어로 예를 들면 아래와 같다.

\<input>

```md
#include <stdio.h>

int main() {
// output a line
printf("Hello World!\n");
}
```

\<output>

```c
#include <stdio.h>

int main() {
  // output a line
  printf("Hello World!\n");
}
```

코드블럭을 사용하다보니 번호를 매기고 싶어질 경우가 있다.
그런 경우에는 \_config.yml 파일에 가서 아래 3줄만 추가해주면 된다.

```yml
kramdown:
input: GFM
hard_wrap: false
auto_ids: true
footnote_nr: 1
entity_output: as_char
toc_levels: 1..6
smart_quotes: lsquo,rsquo,ldquo,rdquo
enable_coderay: false
syntax_highlighter_opts: // 여기부터
block:
line_numbers: true // 여기까지
```

해당 3줄을 추가해도 바로 적용이 되지 않는 경우가 있는데, 그럴 때는 서버를 한번 종료했다가 다시 켜서 확인해 보길 바란다.

번호를 추가하고 나면 복사 할 때 번호까지 복사가 되므로 라인번호까지 복사되지 않도록 하는 것이 좋다.

`_sass/minimal-mistakes/_syntax.scss`

그것은 위에 경로의 파일로 가서 아래와 같이 마지막 6줄을 추가하면 된다.

```scss
/* line numbers*/
&.gutter,
&.rouge-gutter {
  padding-right: 1em;
  width: 1em;
  color: $base04;
  border-right: 1px solid $base04;
  text-align: right;
  -webkit-touch-callout: none; //여기부터
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none; //여기까지
}
```

코드블럭을 사용하다 보면 코드가 정상적로 보이지 않는 경우가 있다.
확인한 오류로는 중괄호가 두개씩 있는 경우였다.

`{% raw %}{{}}{% endraw %}`

이러한 경우 해당코드의 시작부분에 {% raw %} 끝부분에 {% endraw %}를 넣어주면 코드가 정상적으로 잘 보이게 된다.
