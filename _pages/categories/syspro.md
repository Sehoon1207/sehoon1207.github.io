---
title: "Systemprogrammierung"
layout: archive
permalink: /_pages/categories/syspro
author_profile: true

sidebar:
  nav: "sidebar-category"
---

{% assign posts = site.categories.syspro %} {% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}