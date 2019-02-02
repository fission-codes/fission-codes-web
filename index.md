---
layout: home
title: Home
nav_order: 1
has_children: false
---

{% assign newsposts = site.categories["News"] | where: "featured", true %}
{% for post in newsposts limit:1 %}
<article style="background-color: RGBA(100,70,250, .2); padding: 0.3em 2.0em 1em 2.0em">
  <div class="article-head">
    <h2 class="title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
  </div>
  <div class="article-content">
    {{ post.excerpt | markdownify }}
  </div>
</article>
{% endfor %}

<section class="pt-6 pb-6">
  <ul>
  {% assign updates = site.categories["Updates"] | where: "featured", true %}
  {% for update in updates limit: 5 %}
    <li class="pb-2">{{ update.content | remove: "<p>" | remove: "</p>" }} <small class="pl-3">{{ update.date | date_to_string: "ordinal", "US" }}&nbsp;<a href="{{ update.url }}"><i class="fa fa-link" aria-hidden="true"></i></a></small></li>
  {% endfor %}
  </ul>
  <a href="/updates/" class="btn">Read all updates »</a>
</section>

![FISSION Logo](https://s3-ca-central-1.amazonaws.com/images.spade.builders/uploads/upload_55c7620948a74acb1228d308491e3439.png){: .d-none .d-md-inline-block .pt-6}

# Powering microservices for Web3

<a href="/about/" class="btn btn-purple">Read more about FISSION »</a>