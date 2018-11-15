---
layout: home
title: Home
nav_order: 1
has_children: false
---

![FISSION Logo](https://s3-ca-central-1.amazonaws.com/images.spade.builders/uploads/upload_55c7620948a74acb1228d308491e3439.png){: .d-none .d-md-inline-block}

# Powering microservices for Web3

<div class="fs-6">
At the beginning of the web, HTTP's status codes empowered the API-driven interoperability of the entire Internet.<br /><br />
<strong>FISSION Codes</strong> are the base foundation for bringing the same level of interoperability and re-use to the entire Web3 Stack.
</div>

---

{% for post in site.posts limit:1 %}
<article style="background-color: RGBA(100,70,250, .2); padding: 0.3em 2.0em 0.5em 2.0em">
  <div class="article-head">
    <h2 class="title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
  </div>
  <div class="article-content">
    {{ post.excerpt | markdownify }}
  </div>
</article>
{% endfor %}

---

# Powered by FISSION

There are a number of projects and supporters using and promoting FISSION.

* The team at [Consensys Diligence](https://consensys.net/diligence/) have given great feedback and support
* [ERC1410](https://github.com/ethereum/EIPs/issues/1410) and related Security Token standards, being developed by a number of teams including [Polymath](https://polymath.network/)

We'd love to hear how you're using FISSION. Let us know!

{% comment %}

    <div class="article-head">
	    <h2 class="title"><a href="/{{ post.url }}/">{{ post.title }}</a></h2>
			  <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
		</div>
		<div class="article-content">
		
		<a href="/{{ post.url }}/" class="readmore">Read more</a>
		</div>
	</article>

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

{% endcomment %}