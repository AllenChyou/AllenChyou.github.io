---
layout: page
title: Reference
permalink: /refer/
---

  <ul>
    {% assign sorted_categories = site.categories | sort %}
    {% for category in sorted_categories %}
    <li>
			<a href="#{{ category[0] }}">{{ category | first }}</a>
	    <span class="badge">[{{ category[1].size }}]</span>
    </li>
    {% endfor %}
  </ul>

<section>
	{% assign sorted_categories = site.categories | sort %}
	{% for category in sorted_categories %}
	<h3>{{ category | first }}</h3>
	<ol id="{{ category[0] }}">
		{% for post in category.last %}
		<li>
			<span>{{ post.date | date:"%Y-%m-%d" }}</span>
			<a href="{{ post.url }}">{{ post.title }}</a>
		</li>
		{% endfor %}
	</ol>
	{% endfor %}
</section>
