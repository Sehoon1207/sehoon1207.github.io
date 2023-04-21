---
title: "Einführung in die Programmierung"
layout: archive
permalink: /categories/intropro
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.intropro %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}