---
layout: single
title: "포스트 제목 밑에 카테고리, 게시날짜, 태그 추가하기"
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

date: 2023-04-17
---

## 포스트 제목 밑에 카테고리, 게시날짜, 태그 추가하기

포스트 밑줄을 없애고 난 후, 최근 포스트 목록을 보니 포스트 제목의 하단이 너무 비어있다는 느낌에 몇가지 추가해 보았다. 추가할 사항으로는 날짜(달력), 카테고리 그리고 태그이다.

### 1. archive-single.html 파일 수정하기

`/_includes/archive-single.html`

minimal-mistake를 사용시 위의 경로로 가면 해당 파일이 존재한다.
열어보면 아래와 같은 코드가 보인다.

```scss
{% raw %}    <h2 class="archive__item-title no_toc" itemprop="headline">
      {% if post.link %}
        <a href="{{ post.link }}">{{ title }}</a>
        <a href="{{ post.url | relative_url }}" rel="permalink">
        <i class="fas fa-link" aria-hidden="true" title="permalink"></i>
        <span class="sr-only">Permalink</span></a>
      {% else %}
        <a href="{{ post.url | relative_url }}" rel="permalink">{{ title }}</a>
      {% endif %}
    </h2>
    // 이곳에 수정사항을 추가할 예정
    {% include page__meta.html type=include.type %}
    {% if post.excerpt %}
        <p class="archive__item-excerpt" itemprop="description">
        {{ post.excerpt | markdownify | strip_html | truncate: 160 }}
        </p>
    {% endif %}    {% endraw %}
```

중간에 주석이 있는 부분에 아래의 코드를 붙여 넣으면 끝.

```scss
    {% raw %}// 달력과 카테고리 추가
    {% if post.categories[0] != null %}
		<p class="archive__item-excerpt"><i class="far fa-calendar-alt"></i>
        {{ post.date | date: "%m/%d/%Y" }}
        &nbsp; <i class="far fa-folder-open"></i>
        {{ post.categories }}</p>
	{% else %}
		<p class="archive__item-excerpt"><i class="far fa-calendar-alt"></i>
        {{ post.date | date: "%m/%d/%Y" }}</p>
	{% endif %}
    // 태그추가
    {% if post.tags[0] != null %}
        <p class="archive__item-excerpt"><i class="fas fa-tags"></i> {{ post.tags }} </p>
	{% endif %}{% endraw %}
```

수정 후의 모습은 아래와 같다.

```scss
{% raw %}    <h2 class="archive__item-title no_toc" itemprop="headline">
      {% if post.link %}
        <a href="{{ post.link }}">{{ title }}</a>
        <a href="{{ post.url | relative_url }}" rel="permalink">
        <i class="fas fa-link" aria-hidden="true" title="permalink"></i>
        <span class="sr-only">Permalink</span></a>
      {% else %}
        <a href="{{ post.url | relative_url }}" rel="permalink">{{ title }}</a>
      {% endif %}
    </h2>

    // 달력과 카테고리 추가
    {% if post.categories[0] != null %}
		<p class="archive__item-excerpt"><i class="far fa-calendar-alt"></i>
        {{ post.date | date: "%m/%d/%Y" }}
        &nbsp; <i class="far fa-folder-open"></i>
        {{ post.categories }}</p>
	{% else %}
		<p class="archive__item-excerpt"><i class="far fa-calendar-alt"></i>
        {{ post.date | date: "%m/%d/%Y" }}</p>
	{% endif %}
    // 태그추가
    {% if post.tags[0] != null %}
		<p class="archive__item-excerpt"><i class="fas fa-tags"></i> {{ post.tags }} </p>
	{% endif %}
    // 수정사항 끝

    {% include page__meta.html type=include.type %}
    {% if post.excerpt %}
        <p class="archive__item-excerpt" itemprop="description">
        {{ post.excerpt | markdownify | strip_html | truncate: 160 }}
        </p>
    {% endif %}    {% endraw %}
```
