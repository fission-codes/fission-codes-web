---
layout: default
title: Community
has_children: true
parent: Community
permalink: /community/
nav_order: 8
---

We work with a wide variety of different communities.

1. Table of Contents
{:toc}

## Ethereum Improvement Proposals (EIPs)

<ul>
{% assign posts = site.tags["EIPs"] %}
{% for update in posts %}
  <li><strong>{{ update.date | date_to_string: "ordinal", "US" }}:</strong> {{ update.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>

## Ethereum Classic

<ul>
{% assign posts = site.tags["Ethereum Classic"] %}
{% for update in posts %}
  <li><strong>{{ update.date | date_to_string: "ordinal", "US" }}:</strong> {{ update.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>

## ChainID

<ul>
{% assign posts = site.posts | where: "project", "chainid" %}
{% for update in posts %}
  <li><strong>{{ update.date | date_to_string: "ordinal", "US" }}:</strong> {{ update.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>