---
layout: default
title: Updates
parent: Updates
has_children: true
permalink: /updates/
nav_order: 100
---

# Updates

<ul>
{% assign updates = site.categories["Updates"] %}
{% for update in updates %}
  {% capture tags %}
    <span class="taglist" style="font-size: small; font-color: gray">{% for tag in update.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}</span>
  {% endcapture %}
  <li><strong>{{ update.date | date_to_string: "ordinal", "US" }}:</strong> {{ update.content | remove: "<p>" | remove: "</p>" }} {{ tags }}</li>
{% endfor %}
</ul>