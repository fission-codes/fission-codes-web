---
layout: default
title: About
has_children: true
parent: About
permalink: /about/
nav_order: 20
---
FISSION implements a standardized set of codes that enables interoperability and messaging between smart contracts. It is blockchain agnostic, as its single byte design can be implemented in any system or programming language. The initial implementation is being done on the Ethereum blockchain and other systems which utilize the Ethereum Virtual Machine.

FISSION is maintained by the [Special Projects & Decentralized Engineering Company](https://spade.builders), a foundation dedicated to supporting sustainable open source.

![FISSION Logo](https://s3-ca-central-1.amazonaws.com/images.spade.builders/uploads/upload_55c7620948a74acb1228d308491e3439.png){: .d-none .d-md-inline-block}

{% comment %}
<!-- Robot Overlord -->
<!-- Consensys Tachyon -->
{% endcomment %}

---

# FISSION Suite

<dl>
  <dt class="fs-5 fw-700"><a href="/fission-codes/">FISSION Codes</a></dt>
  <dd>Broadly applicable status codes for smart contracts implemented in 1 byte. Like HTTP codes, but designed as a rich set of messages for web3 systems. Implementation of ERC1066</dd>

  <dt class="fs-5 fw-700"><a href="/fission-translate/">FISSION Translate</a></dt>
  <dd>Human readable localizations. On-chain translations, selected by the user, for feedback from smart contracts. Implementation of ERC1444</dd>
</dl>

---

## Future planned components:

<dl>
  <dt class="fs-5 fw-700">FISSION Web Bridge</dt>
  <dd>Translating FISSION Codes to HTTP Status Codes for easy web to blockchain interoperability</dd>

  <dt class="fs-5 fw-700">FISSION Interchain</dt>
  <dd>Transferring messages between two or more smart contract-capable blockchains with common FISSION Codes</dd>
</dl>

{% comment %}
## Powering microservices for Web3

Microservices are being used in the traditional web to build small, nimble, pieces of code that communicate to each other through messages.

Today, developers are deploying smart contracts that only talk to their own systems, or at best writing custom code to understand a particular contract's interfaces.

With FISSION, individual smart contracts can be reviewed, verified, and hardened - and have their interactions defined as messages.
{% endcomment %}
