---
layout: archive
title: "C/C++"
permalink: /C-C++/
author_profile: true
header:
   image: "/images/C++ wallpaper.jpg"
---

{% include list-posts entries='3' offset='1' category='C/C++' %}

{% assign selcat = include.category %}
{% assign seltg = include.tag %}


{% if selcat == NULL and seltg == NULL %}
  {% for post in site.posts limit:include.entries offset:include.offset %}
    {% include archive-single.html %}
  {% endfor %}


{% elsif selcat!="" and seltg!="" %}
  {% for post in site.categories.[selcat] %}
    {% if post.tags contains seltg %}
      {% include archive-single.html %}
    {% endif %}
  {% endfor %}


{% elsif selcat %}
  {% for post in site.categories.[selcat] limit:include.entries offset:include.offset %}
    {% include archive-single.html %}
  {% endfor %}


{% elsif seltg %}
  {% for post in site.tags.[seltg] limit:include.entries %}
    {% include archive-single.html %}
  {% endfor %}

{% endif %}
