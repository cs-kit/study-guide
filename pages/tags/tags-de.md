---
layout: post
title: Tags
permalink: /tags-de/
ref: tags
date: 2018-08-30 14:00:00 +0100
excerpt: Eine Übersicht über alle Posts und ihre Tags.
lang: de
nav_order: 0
---

Ein Post kann mehrere Tags benutzen, um gefunden werden zu können. 
Sie sind vergleichbar mit spezifischen Suchbegriffen.


{% assign rawtags = "" %}
{% for post in site.posts %}
	{% assign ttags = post.tags | join:'|' | append:'|' %}
	{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}


{% assign tags = "" %}
{% for tag in rawtags %}
	{% if tag != "" %}
		{% if tags == "" %}
			{% assign tags = tag | split:'|' %}
		{% endif %}
		{% unless tags contains tag %}
			{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
		{% endunless %}
	{% endif %}
{% endfor %}



{% for tag in tags %}
<h1 id="{{ tag | slugify }}">Tag: {{ tag }}</h1>

{% assign posts = site.posts | where:'title', 'this title is left blank intentionally' %}

 {% for post in site.posts %}
	 {% if post.tags contains tag %}
	 	{% assign posts = posts | push: post %}
	 {% endif %}
 {% endfor %}

 
  {% include post_list.html %}
 
  

{% endfor %}

