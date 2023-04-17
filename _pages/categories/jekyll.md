---
layout: archive
permalink: jekyll
title: "Jekyll"

author_profile: true
sidebar:
  nav: "sidebar-category"
---

<!-- {% assign posts = site.categories.jekyll %}
{% for post in posts %}
{% include custom-archive-single.html type=entries_layout %}
{% endfor %} -->

{% include group-by-array collection=site.posts field="categories" %}
{% for category in group_names %}
{% assign posts = group_items[forloop.index0] %}

  <h2 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
