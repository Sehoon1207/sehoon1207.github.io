---
title: "Programming C"
layout: archive
permalink: /_pages/categories/c
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.c %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}