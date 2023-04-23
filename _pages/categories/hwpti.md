---
title: "Hardwarepraktikum"
layout: archive
permalink: /categories/hwpti
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.hwpti %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}