---
layout: page
permalink: /home/
---

<h2 class="smallcap">Posts</h2>
<ul class="post-list">
	{% for post in site.posts %}
	{% if post.layout == "post" %}
	<li>
		<span>{{ post.date | date: "%Y/%m/%d" }}</span>
		<a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
	</li>
	{% endif %}
	{% endfor %}
</ul>
