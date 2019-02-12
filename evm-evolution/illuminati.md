---
layout: default
title: Illuminati Client
parent: EVM Evolution
permalink: /evm-evolution/illuminati/
nav_order: 7
---

# The Illuminati Client
{:.no_toc}

![](/assets/images/illuminati-pyramid.png)

## A Formally Verified Ethereum Client
### Correct... by Construction!

{:.no_toc}

Programs and proofs are equivalent in this paradigm. A major advantage of this approach is “propositions as types” coupled with a highly expressive type system. A program created with these techniques is an intuitionistic logic proof of itself. Invariants encoded in dependent types are enforced at compile-time (removing entire large classes of bugs), can be enforced on future modifications to the code, reference values, and remain highly modular.

With dependent types, we can encode complex rules into our programs at the type level. The tradeoff is that inductive proofs can sometimes become equally involved. Several of these languages provide a tactic sublanguage to help solve for these cases.

The syntax of these languages are generally familiar to programmers with a background in typed functional languages like Haskell, Elm, and OCaml. As a warmup to this end, we have been working on the “EeVeeM,” a Haskell EVM (not yet publicly available). It is geared towards rapid R&D, but also is modular and with clean abstractions for tuning performance or plugging in external code, while remaining readable.
