---
layout: default
title: Updates
parent: Updates
has_children: true
permalink: /updates/
nav_order: 100
---

# Updates

{% assign postsByYearMonth = site.categories["Updates"] | group_by_exp:"post", "post.date | date: '%Y %B'"  %}
{% for yearMonth in postsByYearMonth %}
<h3>{{ yearMonth.name }}</h3>
<ul>
{% for post in yearMonth.items %}
<li class="pb-2">{{ post.excerpt | markdownify | remove: "<p>" | remove: "</p>" }}&nbsp;<small><a href="{{ post.url }}"><i class="fa fa-link" aria-hidden="true"></i></a></small></li>
{% endfor %}
</ul>
{% endfor %}