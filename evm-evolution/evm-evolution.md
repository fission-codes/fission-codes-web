---
layout: default
title: EVM Evolution
has_children: true
parent: EVM Evolution
permalink: /evm-evolution/
nav_order: 6
---
# EVM Evolution
{:.no_toc}

![](https://spade.builders/img/posts/ethereum-rainbow.jpeg)

## Security, Performance, and other enhancements to the Ethereum Virtual Machine
{:.no_toc}

In the 21st century, on a blockchain holding billions USD in value, formal specification and verification are an essential tool. Yet the design of the EVM makes this unnecessarily difficult. Further, the design of the EVM makes low-gas-cost, high-performance execution difficult. We propose to move forward with proposals to resolve these problems by tightening the security guarantees and pushing the performance limits of the EVM.

---

The Ethereum Virtual Machine, or EVM, is the core part of the Ethereum ecosystem that powers everything from smart contract features to the consensus semantics.

"EVM Evolution" is what we're calling our collected efforts to improve and extend the EVM, from it's specification, formal verification, to supporting a variety of implementations.

Sub-pages of this page list additional major components and initiatives that are part of EVM Evolution.

1. Table of Contents
{:toc}
## Roadmap

Inspired by [Alexey Akhunov's @realLedgerwatch](https://twitter.com/realLedgerwatch) work on ETH1x State Management planning, we will be working on produce a [Fork Roadmap Planning Doc](https://docs.google.com/presentation/d/1pk7smp2k65CWCpXrEiZ9BURr8VzNqWdPyRk2mLZ7Jpo/edit).

Our 6 month scope that we submitted to the Ethereum Foundation as part of our updated grant proposal is [available on Google Docs](https://docs.google.com/document/d/1fabffVByusQK7Arh8Jx5yYYQi_OL1rVt9mgr9f5Vg1M/). We're in the midst of moving all that content here.

Our goal is a fully formalized EVM that implements an interpreter and a compiler that is formally specified and freely available under a permission Apache 2 license.

## Funding

We are a bootstrapped team who are working on low-level, open source infrastructure for the wider EVM ecosystem. We are open to prioritizing specific work or performing primary research related to EVM improvements. [Please get in touch if you're interested in working with us](https://spade.builders).

### EF Grant Application

We have an outstanding grant application to the Ethereum Foundation suggesting 6 months of funding to begin with. This will allow the team to dedicate our time to preparing [EIP 615 Static Jumps](eip-615/) for the [Istanbul hardfork](https://en.ethereum.wiki/roadmap/istanbul), including supporting client teams.

### Gitcoin Grants

We have setup a Gitcoin Grant asking for the monthly amount we need to fully focus on this.

<a href="https://gitcoin.co/grants/47/evm-evolution" class="btn btn-purple">Contribute to Gitcoin Grant</a>

## Updates

Besides our own updates that are EVM Evolution related, you can also view [EVM Evolution topics on the EthMagicians forum](https://ethereum-magicians.org/tags/evm-evolution).

<ul>
{% assign evmposts = site.posts | where: "project", "evmevolution" %}
{% for post in evmposts %}
  <li><strong>{{ post.date | date_to_string: "ordinal", "US" }}:</strong> {{ post.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>

