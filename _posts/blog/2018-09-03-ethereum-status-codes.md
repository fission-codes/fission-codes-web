---
layout: post
title:  "Ethereum Status Codes"
date:   2018-09-03 10:27:20 -0800
category:
  - News
tags:
  - FISSION Codes
  - Ethereum
featured: true
author: Brooklyn Zelenka
excerpt: "Ethereum enables individuals and organizations to host and run code on a shared
system. While this allows us to inspect and run software as a community,
smart contracts are currently isolated by default, connecting them
requires a bespoke work, and lack of user feedback is a frequent complaint. The Ethereum Status Codes (ESC) project aims to solve these problems with
a well thought out, lightweight, platform- and language-agnostic set of codes"
---

_Note: this is an old blog post. We have, of course, renamed and expanded to have Ethereum Status Codes. The original blog post has been trimmed of some content and links that are no longer valid._

# A Smarter Contract Protocol

Ethereum enables individuals and organizations to host and run code on a shared
system. While this allows us to inspect and run software as a community,
smart contracts are currently isolated by default, connecting them
requires a bespoke work, and lack of user feedback is a frequent complaint.

The Ethereum Status Codes (ESC) project aims to solve these problems with
a well thought out, lightweight, platform- and language-agnostic set of codes which:

1. Improve end user feedback
2. Help you understand your code at runtime, and
3. Make contracts interoperable and more autonomous

## Lessons from Web 1.0

> Those who fail to learn from history are condemned to repeat it
>
> -- <cite>George Santayana</cite>

The modern web is able to exist because browsers know how to talk to servers,
and servers can easily communicate with each other. The HTTP protocol
underlies everything that we do online.

Ethereum Status Codes ("ESC") are a cross between HTTP and an API that works
with any deployed smart contract. This project gets us much closer to the
promise of autonomous code and interoperability, plus human language feedback
that’s clearer and broader than error codes.

# An Open Standard

[ERC1066: Status Codes](https://eips.ethereum.org/EIPS/eip-1066) is an open standard,
freely usable by anyone, forever. It is built from the bottom up with
decentralization of control in mind, from the formal spec, up to how users
create and choose translations.

We already have a [published EIP](https://eips.ethereum.org/EIPS/eip-1066)
in the Draft stage on the official EIPs site, plus early
[helper libraries](https://www.npmjs.com/package/ethereum-status-codes)
 published to `npm`.

# Project Goals

## Translations

Yes, we’re building in global communication from Day 1!

Since it is practical to translate 256 messages, ESCs can be translated into
human-readable messages in any language. The current state of the art is to
return hard-coded text, and typically only if something goes wrong
and the transaction fails.

The ESC localization system enables users to decide on which translation they
want for all contracts when they run it, as opposed to the language being
set by the developer. Users can also create their own translations, with differing
levels of technical detail, and share them in a fully distributed way!

## Integrations
One central project aim is to integrate user and developer feedback capabilities
into wallets and development tools to make smart contracts more contextual,
and give more control to users, and fewer headaches for development teams.

## Language Agnostic

ESCs are not bound to JS, Solidity, or Vyper; they can be run directly
on the EVM with no high-level language in between. They are designed to be
flexible, extensible, highly efficient, fully opt-in, and work with existing
development tools with no need for a hard fork.

# Resources

* Community 🙌
  * [ESC Discord Channel](https://discord.gg/hQfgyz2)
  * [Ethereum Magicians Topic](https://ethereum-magicians.org/t/erc-1066-ethereum-status-codes-esc/283)

* Technical 🤓
  * [Lightning Talk](https://view.ly/v/eljSU6DKXpyC)
  * [Ethereum Improvement Proposal](https://eips.ethereum.org/EIPS/eip-1066)

# Core Team

* [Brooklyn Zelenka](https://github.com/expede), Project Lead & Principal Engineer
* [Jennifer Cooper](https://github.com/jenncoop), Senior Integrations Engineer
* [Boris Mann](https://twitter.com/bmann), Community Manager & Operations
