---
layout: default
title: Updates
nav_order: 20
---

# Updates

<ul>
{% assign updates = site.categories["Updates"] | sort: reverse %}
{% for update in updates %}
  {% capture tags %}
    <span class="taglist" style="font-size: small; font-color: gray">{% for tag in update.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}</span>
  {% endcapture %}
  <li><strong>{{ update.date | date_to_string: "ordinal", "US" }}:</strong> {{ update.content | remove: "<p>" | remove: "</p>" }} {{ tags }}</li>
{% endfor %}
</ul>