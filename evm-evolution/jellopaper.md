---
layout: default
parent: EVM Evolution
title: EVM Specification
permalink: /evm-evolution/specification/
nav_order: 2
---

# EVM Specification

Improving and maintaining the Ethereum Virtual Machine (EVM) specification, including a focus on the Jello Paper as a more complete specification for implementers and testers.

---

The Yellow Paper was the original specification of the Ethereum Virtual Machine (EVM).

The [Jello Paper](https://jellopaper.org/) defines the semantics of the EVM using the [KEVM project](https://github.com/kframework/evm-semantics).

> The KEVM semantics described by the Jello Paper is the first machine-executable, mathematically formal, human readable, and complete semantics of the EVM. KEVM is capable of passing the full EVM VMTests and GeneralStateTests testing suites, and can also be used in smart contract formal verification, debugging, and more.

## Formally Verified Full Client Specification

The Yellow Paper has served us fairly well, but has some underspecified behaviours. It also tends to lag behind the actual running clients. We also could have caught nasty surprises such as the [“Constanti-NOPE-le” bug](https://www.coindesk.com/ethereums-constantinople-upgrade-faces-delay-due-to-security-vulnerability) could have been much earlier were there a formalized and checked spec prior to implementation.

Having a test suite is vastly better than not having one, but can’t handle the combinatorial explosion when multiple factors may interact. A formal model has the distinct advantage of working for all cases (universally quantified), whereas tests only spot-test a small subset of possible inputs and scenarios.

We propose extending the Jello Paper (or similar) to cover the entire client, verify it, generate tests cases, and so on. There have been some concerns about the K being unfamiliar for existing client implementers; the good news is that we can generate notation in any style from such a spec either automatically or by hand.

## Completed

* Purchased and setup a redirect for yellowpaper-dot-io, so that [yellowpaper.club](http://yellowpaper.club) points to the PDF
* Kicked off [discussion on EthMagicians on making the Jello Paper the canonical representation of the EVM spec](https://ethereum-magicians.org/t/jello-paper-as-canonical-evm-spec/2389)
* Requested filing of an issue to [generate the Jello Paper as part of CI job](https://github.com/kframework/evm-semantics/issues/293)
* Joined the new [Yellow Paper Maintenance SIG](https://hackmd.io/uIW3cqMrR6uOyKutQ-BwiQ#)

## Next Steps

* Write up and submit an Informational EIP to have the Jello Paper accepted as the Canonical Specification for the EVM
* Post issues / bounty for defining the Constantinople EIPs as part of the Jello Paper
* (potential) K-EVM workshop around Council of Paris 2019 / ETHCC
