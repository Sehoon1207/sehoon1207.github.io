---
layout: single
title: "포스트 제목 밑에 카테고리, 게시날짜, 태그 추가하기"
folder: "ekyll"
categories:
  - ekyll

tags: [blog, ekyll, minimal-mistakes]

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

포스트 밑줄을 없애고 난 후, 포스트 하단이 너무 비어있다는 느낌에 몇가지 추가해 보았다. 






````scss
    <h2 class="archive__item-title no_toc" itemprop="headline">
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
    {% endif %}

````



```scss

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

```