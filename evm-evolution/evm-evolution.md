---
layout: default
title: EVM Evolution
has_children: true
parent: EVM Evolution
permalink: /evm-evolution/
nav_order: 6
---
# EVM Evolution

## Security, Performance, and other enhancements to the Ethereum Virtual Machine

The Ethereum Virtual Machine, or EVM, is the core part of the Ethereum ecosystem that powers everything from smart contract features to the consensus semantics.

## Updates

<ul>
{% assign evmposts = site.posts | where: "project", "evmevolution" %}
{% for post in evmposts %}
  <li><strong>{{ post.date | date_to_string: "ordinal", "US" }}:</strong> {{ post.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>

