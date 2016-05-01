---
layout: page
title: Wiki
permalink: /wiki/
---

> How much times to repeat can wake you up? Remember the map.

<ul>
  {% for post in site.posts %}
    {% if post.layout  == "wiki" %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
	{% endfor %}
</ul>
