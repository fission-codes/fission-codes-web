---
layout: home
title: Home
nav_order: 1
has_children: false
---

![FISSION Logo](https://s3-ca-central-1.amazonaws.com/images.spade.builders/uploads/upload_55c7620948a74acb1228d308491e3439.png)

# Powering microservices for Web3

{% comment %}
<!-- Pink RGBA(255,82,116, .2) -->
<!-- Purple RGBA(100,70,250, .2) -->
{% endcomment %}

{% comment %}
## Powering microservices for Web3

Microservices are being used in the traditional web to build small, nimble, pieces of code that communicate to each other through messages.

Today, developers are deploying smart contracts that only talk to their own systems, or at best writing custom code to understand a particular contract's interfaces.

With FISSION, individual smart contracts can be reviewed, verified, and hardened - and have their interactions defined as messages.
{% endcomment %}

<div class="fs-6">
At the beginning of the web, HTTP's status codes empowered the API-driven interoperability of the entire Internet.<br /><br />
<strong>FISSION Codes</strong> are the base foundation for bringing the same level of interoperability and re-use to the entire Web3 Stack.
</div>

---

<div style="background-color: RGBA(100,70,250, .2); padding: 0.3em 2.0em 0.5em 2.0em">
  <h2>November 2018: Completing the Consensys Tachyon Accelerator</h2>
  <img alt="Tachyon Accelerator by Consensys Ventures - Logo" src="/assets/images/tachyon.png"/>
  <p>We're proud to be graduating from the <a href="https://tachyoncv.vc/">Consensys Tachyon Blockchain Accelerator</a> program. Thank you to the whole team for your support and guidance over the last few months! </p>
  <p>The FISSION Suite project is being guided by the <a href="https://spade.builders">Special Projects & Decentralized Engineering Company</a>, a US-based foundation, dedicated to supporting open source projects.</p>
  <p><a href="mailto:hello@spade.builders" class="btn btn-purple">Get in touch with the SPADE team</a></p>
</div>

---

# Powered by FISSION

There are a number of projects and supporters using and promoting FISSION.

* The team at [Consensys Diligence](https://consensys.net/diligence/) have given great feedback and support
* [ERC1410](https://github.com/ethereum/EIPs/issues/1410) and related Security Token standards, being developed by a number of teams including [Polymath](https://polymath.network/)

We'd love to hear how you're using FISSION. Let us know!

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