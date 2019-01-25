---
layout: default
title: Blog
parent: Updates
nav_order: 20
---

# Blog

{% assign newsposts = site.categories["News"] %}
{% for post in newsposts %}
<article style="padding: 0.3em 2.0em 0.5em 2.0em">
  <div class="article-head">
    <h2 class="title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
  </div>
  <div class="article-content">
    {{ post.excerpt | markdownify }}
  </div>
</article>
{% endfor %}
