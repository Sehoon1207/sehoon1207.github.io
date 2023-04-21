---
layout: single
title: "[jekyll] 사이드바(sidebar)"
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
typora-root-url: ../

date: 2023-04-21
---

이 글은 minimal-mistake 사용할 때의 기준이고 다른 jekyll thema를 사용하는 분은 참고만 하시면 될 것 같다. 대부분 비슷비슷하기 때문..

# 1/. navigation.yml 파일 수정하기

`_data/navigation.yml`

위와 같은 경로에 있는 파일을 열어 sidebar에 보여질 것을 몇 줄 추가 해준다.

예를 들면 같다.

```yml
sidebar-category:
  - title: Programming
    children:
      - title: "C"
        url: c/
        category: "c"
      - title: "VHDL"
        url: vhdl/
        category: "vhdl"
      - title: "Html&Css"
        url: html&css/
        category: "html&css"
      - title: "JavaScript"
        url: javascript/
        category: "javascript"
  - title: Studium
    children:
      - title: "IntroPro"
        url: intropro/
        category: "intropro"
      - title: "Signale und Systeme"
        url: sus/
        category: "sus"
      - title: "Analysis II"
        url: anaII/
        category: "anaII"
  - title: Etc
    children:
      - title: "Jekyll"
        url: jekyll/
        category: "jekyll"
      - title: "Markdown"
        url: markdown/
        category: "markdown"
      - title: "etc"
        url: etc/
        category: "etc"
```

# 게시글 수 표시

다른 블로그 들을 참고해 보면 해당 카테고리 옆에 게시글의 숫자를 표기하는 경우가 있다. 나름 숫자가 표시되면 동기부여에도 좋은 것 같아서 추가해본다.
해당 기능을 추가하려면 `_includes\nav_list` 이 경로의 파일을 수정해야한다.

아래의 코드를 참고해서 수정 또는 전부 복사 붙여넣기 해주면 끝.
파일의 전체 코드니.. 편하게 복붙해도 좋다.

{% raw %}
```yml
{% assign navigation = site.data.navigation[include.nav] %}

{% assign categories_max = 0 %}
{% for category in site.categories %}
  {% if category[1].size > categories_max %}
    {% assign categories_max = category[1].size %}
  {% endif %}
{% endfor %}

{% assign tags_max = 0 %}
{% for tag in site.tags %}
  {% if tag[1].size > tags_max %}
    {% assign tags_max = tag[1].size %}
  {% endif %}
{% endfor %}

<nav class="nav__list">
  {% if page.sidebar.title %}<h3 class="nav__title" style="padding-left: 0;">{{ page.sidebar.title }}</h3>{% endif %}
  <input id="ac-toc" name="accordion-toc" type="checkbox" />
  <label for="ac-toc">{{ site.data.ui-text[site.locale].menu_label | default: "Toggle Menu" }}</label>
  <ul class="nav__items">
    {% for nav in navigation %}
      <li>
        {% if nav.url %}
          <a href="{{ nav.url | relative_url }}"><span class="nav__sub-title">{{ nav.title }}</span></a>
        {% else %}
          <span class="nav__sub-title">{{ nav.title }}</span>
        {% endif %}

        {% if nav.children != null %}
        <ul>
          {% for child in nav.children %}
          {% assign category = site.categories[child.category] | where_exp: "item", "item.hidden != true" %}
            <li><a href="{{ child.url | relative_url }}"{% if child.url == page.url %} class="active"{% endif %}>{{ child.title }} ({{ category.size }})</a></li>
          {% endfor %}
        </ul>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
</nav>

```
{% endraw %}