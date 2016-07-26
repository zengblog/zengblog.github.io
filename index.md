---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
  
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
	{% case site.excerpt %}
	{% when "truncate_words" %}
	    <span class="teaser"><p>{{ post.content | strip_html | truncatewords: 20 }}</p>
	{% when "teaser" %}
	    <span class="teaser">{{ post.content  | split:'<!--more-->' | first }}
	{% else %}
	    <span> 
		{% if post.description %}{{ post.description }}
		{% else %} {{ post.content | split:'</p>' | first }} </p>
		{% endif %}
	{% endcase %}
	</span>
  {% endfor %}
</ul>
