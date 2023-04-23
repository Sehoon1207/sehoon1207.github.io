---
title: "Algorithmen und Datenstrukturen"
layout: archive
permalink: /categories/algoDat
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.algoDat %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}