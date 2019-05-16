---
layout: home
title: Home
nav_order: 1
has_children: false
---

{% assign newsposts = site.categories["News"] | where: "featured", true %}
{% for post in newsposts limit:1 %}
<article style="background-color: RGBA(100,70,250, .2); padding: 0.3em 2.0em 1.5em 2.0em">
  <div class="article-head">
    <h2 class="title">New home page, blog</h2>
  </div>
  <div class="article-content">
    <p>We've recently setup both a <a href="https://blog.fission.codes">new blog</a> and a <a href="https://fission.codes">new home page</a>. There may be some dust as we transition this site to be fully focused on documentation for our open source code, Ethereum working groups, and other projects.</p>
  </div>
  <a href="https://fission.codes" class="btn btn-purple">Check out the new FISSION home page »</a>
</article>
{% endfor %}

<section class="pt-4 pb-6">
  <h3>Updates</h3>
  <ul>
  {% assign updates = site.categories["Updates"] | where: "featured", true %}
  {% for update in updates limit: 1 %}
    <li class="pb-2">{{ update.content | remove: "<p>" | remove: "</p>" }} <small class="pl-3">{{ update.date | date_to_string: "ordinal", "US" }}&nbsp;<a href="{{ update.url }}"><i class="fa fa-link" aria-hidden="true"></i></a></small></li>
  {% endfor %}
  </ul>
  <a href="/updates/" class="btn">Read all updates »</a>
</section>