---
title: "Jekyll 개념 및 관련 설정"
layout: archive
permalink: categories/jekyll


author_profile: true
sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.jekyll %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
