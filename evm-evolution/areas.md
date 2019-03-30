---
layout: default
parent: EVM Evolution
title: Areas
permalink: /evm-evolution/areas/
nav_order: 2
---

# EVM Evolution Areas

These are some broad research and development areas that we are investigating and discussing that fit under the scope of EVM Evolution.

## High Level Overview

![](/assets/images/evm-evolution-deps.png)

### Safety / Correctness

#### Opcodes

* Subroutines
* Static jumps
* Non-overflowing arithmetic
* Ephemeral storage (ie: single transaction lifetime)

#### Memory
* Arbitrary local memory alignment (easier to solve for and much faster symbolic execution than byte-aligned)

### Raw Performance

#### Opcodes
* SIMD
* MIMD (maybe)
* Variable-width VM word size (example: flag to enable native 32-bit arithmetic on the EVM)

#### Analytic Optimization

Client-specific, but can write general guidelines and reference implementations in Parity, EeVeeM, &c

* VM-level tail call optimization
* Incremental JIT optimization
* EVM-to-native smart contract compilation
* Automatic naive wordsize detection (ex. sequences of `ADDMOD 32` don’t need to store as 256-bit)
  * Adjust gas cost to make native wordsize (or easily aligned) operations cheaper
* Decoupled gas metering / gas aggregation
* Shared bytecode linking (contract size)

### Simplicity / Clean Up

* Deprecate dynamic jumps
* Deprecate Precompiles (controversial!)
  * Move cryptographic primitives into the mostly empty 0x20 opcode range

## LLVM-to-EVM Compiler Backend

As a first step towards enabling (many) more languages on the EVM, we can solve for an entire class of languages by writing an LLVM-to-EVM backend. We could later get further improvements with additional bespoke optimization. This would unlock many languages for smart contract development, including but not limited to: C, C++, C#, JavaScript, Rust, Lua, Objective-C, Swift, Python, Ruby, Scala, Fortran, Haskell, Common Lisp, Ada, Crystal, D, Delphi, Julia, Kotlin. It would also allow people to use all of the optimizers, static analysis tools, and compile targets that LLVM ecosystem enjoys.

## Formally Verified Client

### Strategy 1: Correct-by-Construction [Idris, F*, Coq, Lean, or (maybe) Dependent Haskell]

Programs and proofs are equivalent in this paradigm. A major advantage of this approach is “propositions as types” coupled with a highly expressive type system. A program created with these techniques is an intuitionistic logic proof of itself. Invariants encoded in dependent types are enforced at compile-time (removing entire large classes of bugs), can be enforced on future modifications to the code, reference values, and remain highly modular.

With dependent types, we can encode arbitrarily complex rules into our programs at the type level. The tradeoff is that inductive proofs can sometimes become equally involved. Several of these languages provide a tactic sublanguage to help solve for these cases.

The syntax of these languages are generally familiar to programmers with a background in typed functional languages like Haskell, Elm, and OCaml. As a warmup to this end, we’ve been working on the “EeVeeM,” a Haskell EVM (not yet publicly available). It is geared towards rapid R&D, but also is modular and with clean abstractions for tuning performance or plugging in external code, while remaining readable.

### Strategy 2: High Level Program Synthesis or Constraint Programming [K, TLA+, or Prolog]

This strategy is primarily spec-driven. A formal specification that gets translated into a runnable program. The tradeoff is lack of fine-grained control over the output, which is sometimes more efficient, but also sometimes generates slow or indecipherable code. This strategy could be as straightforward as extending the KEVM to include the rest of the client, or writing constraints for Prolog.

## Formally Verified Full Client Specification

The Yellow Paper has served us fairly well, but has some underspecified behaviours. It also tends to lag behind the actual running clients. We also could have caught nasty surprises such as the “Constanti-NOPE-le” bug could have been much earlier were there a formalized and checked spec prior to implementation.

Having a test suite is vastly better than not having one, but can’t handle the combinatorial explosion when multiple factors may interact. A formal model has the distinct advantage of working for all cases (universally quantified), whereas tests only spot-test a small subset of possible inputs and scenarios.

We propose extending the Jello Paper (or similar) to cover the entire client, verify it, generate tests cases, and so on. There have been some concerns about the K being unfamiliar for existing client implementers; the good news is that we can generate notation in any style from such a spec either automatically or by hand.
