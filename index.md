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

<section class="pt-4">
  <h3>Projects</h3>
  <ul>
  {% assign pages_list = site.html_pages | sort: "nav_order" %}
  {% for project in pages_list %}
    {% if project.parent == project.title and project.title != "Home" and project.title != "Updates" and project.url != "/404/" %}
    <li class="pb-2"><a href="{{ project.url }}">{{ project.title }}</a></li>
    {% endif %}
  {% endfor %}
  </ul>
</section>

<section class="pt-4 pb-6">
  <h3>Blog</h3>
  <div style="padding-bottom: 0.5em"><script src="//rss2html.herokuapp.com/?url=https%3A%2F%2Fblog.fission.codes%2Frss&detail=-1&limit=3&showtitle=false&type=js"></script></div>
  <a href="https://blog.fission.codes" class="btn">Read the FISSION blog »</a>
</section>