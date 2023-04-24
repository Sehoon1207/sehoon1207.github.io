---
title: "markdown"
layout: archive
permalink: /_pages/categories/markdown/
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.markdown %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}