---
title: "Projects"
layout: archive
permalink: /projects/
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.ana_2 %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}