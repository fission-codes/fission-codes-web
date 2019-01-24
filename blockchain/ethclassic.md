---
layout: default
title: Ethereum Classic
has_children: false
parent: Blockchain
nav_order: 6
---

<h2>Notes for Ethereum Classic specific usages of the FISSION Suite</h2>

<p>Please follow the Ethereum Classic Improvement Proposal <a href="https://github.com/ethereumclassic/ECIPs">ECIP process</a> to track progress of inclusion, or join the <a href="https://discord.gg/y9WwZZy">#ethclassic channel on our Discord</a>.</p>

<h2>Updates</h2>

<ul>
{% assign etcposts = site.tags["Ethereum Classic"] | sort: reverse %}
{% for update in etcposts %}
  <li><strong>{{ update.date | date_to_string: "ordinal", "US" }}:</strong> {{ update.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>