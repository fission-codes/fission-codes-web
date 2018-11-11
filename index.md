---
layout: home
title: Home
nav_order: 5
has_children: false
---

![FISSION Logo](https://s3-ca-central-1.amazonaws.com/images.spade.builders/uploads/upload_55c7620948a74acb1228d308491e3439.png)

# Powering microservices for Web3

At the beginning of the web, HTTP's status codes empowered the API-driven interoperability of the entire Internet.

FISSION Codes are the base foundation for bringing the same level of interoperability and re-use to the entire Web3 Stack.

{% for post in site.posts limit:1 %}
  <article style="border: 1px black; background: cream">
    <div class="article-head">
	    <h2 class="title"><a href="/{{ post.url }}/">{{ post.title }}</a></h2>
			  <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
		</div>
		<div class="article-content">
		{{ post.excerpt }}
		<a href="/{{ post.url }}/" class="readmore">Read more</a>
		</div>
	</article>
  {% unless forloop.last %}<div class="separater"></div>{% endunless %}
{% endfor %}

# Updates

{% for post in site.posts offset:1 %}
  <article>
    <div class="article-head">
	    <h2 class="title"><a href="/{{ post.url }}/">{{ post.title }}</a></h2>
			  <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
		</div>
		<div class="article-content">
		{{ post.excerpt }}
		<a href="/{{ post.url }}/" class="readmore">Read more</a>
		</div>
	</article>
  {% unless forloop.last %}<div class="separater"></div>{% endunless %}
{% endfor %}

# Components

* [FISSION Codes](/fission-codes/)
* [FISSION Translate](/fission-translate)

## Planned

* FISSION Web Bridge
* FISSION Interchain