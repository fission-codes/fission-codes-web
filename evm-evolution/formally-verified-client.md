---
layout: default
parent: EVM Evolution
title: Formally Verified Client
permalink: /evm-evolution/formally-verified-client/
nav_order: 5
---

# Formally Verified Client

There is desire for a complete, formally verified Ethereumm client implementation. We have two options on our radar:

## Strategy 1: Correct-by-Construction
### Idris, F*, Coq, Lean, or (maybe) Dependent Haskell

Programs and proofs are equivalent in this paradigm. A major advantage of this approach is “propositions as types” coupled with a highly expressive type system. A program created with these techniques is an intuitionistic logic proof of itself. Invariants encoded in dependent types are enforced at compile-time (removing entire large classes of bugs), can be enforced on future modifications to the code, reference values, and remain highly modular.

With dependent types, we can encode complex rules into our programs at the type level. The tradeoff is that inductive proofs can sometimes become equally involved. Several of these languages provide a tactic sublanguage to help solve for these cases.

The syntax of these languages are generally familiar to programmers with a background in typed functional languages like Haskell, Elm, and OCaml. As a warmup to this end, we have been working on the “EeVeeM,” a Haskell EVM (not yet publicly available). It is geared towards rapid R&D, but also is modular and with clean abstractions for tuning performance or plugging in external code, while remaining readable.

## Strategy 2: High Level Program Synthesis or Constraint Programming
### K, TLA+, or Prolog

This strategy is primarily spec-driven. A formal specification that gets translated into a runnable program. The tradeoff is lack of fine-grained control over the output, which is sometimes more efficient, but also sometimes generates slow or indecipherable code. This strategy could be as straightforward as extending the KEVM to include the rest of the client, or writing constraints for Prolog.
