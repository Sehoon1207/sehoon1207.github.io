---
title: "jekyll"
layout: archive
permalink: /categories/jekyll
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.jekyll %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}