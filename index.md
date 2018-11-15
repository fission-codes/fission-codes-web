---
layout: home
title: Home
nav_order: 5
has_children: false
---

![FISSION Logo](https://s3-ca-central-1.amazonaws.com/images.spade.builders/uploads/upload_55c7620948a74acb1228d308491e3439.png)

# Powering microservices for Web3

<!-- Pink RGBA(255,82,116, .2) -->
<!-- Purple RGBA(100,70,250, .2) -->

<div style="background-color: RGBA(100,70,250, .2); padding: 0.3em 2.0em 0.5em 2.0em">
  <h2>Completing the Consensys Tachyon Accelerator</h2>
  <p>We're proud to be graduating from the <a href="https://tachyoncv.vc/">Consensys Tachyon Blockchain Accelerator</a> program.</p>
  <p>The FISSION Suite project is being guided by the Special Projects & Decentralized Engineering Company, a US-based foundation, dedicated to supporting open source projects.</p>
</div>

---

<div class="fs-6">
At the beginning of the web, HTTP's status codes empowered the API-driven interoperability of the entire Internet.<br /><br />
<strong>FISSION Codes</strong> are the base foundation for bringing the same level of interoperability and re-use to the entire Web3 Stack.
</div>

---

# Powered by FISSION

There are a number of projects and supporters using and promoting FISSION. We'd love to hear how you're using it!

* Consensys Diligence
* Security Token Standards, Polymath
*

{% comment %}

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

{% endcomment %}