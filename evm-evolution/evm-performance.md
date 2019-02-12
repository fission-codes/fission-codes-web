---
layout: default
title: EVM Performance
parent: EVM Evolution
permalink: /evm-evolution/evm-performance/
nav_order: 5
---

# EVM Performance

blah blah

## Opcodes

### Single Instruction / Multiple Data (SIMD Parallelism)

To quote [EIP-616](https://github.com/ethereum/EIPs/issues/616):

> Most all modern CPUs include SIMD hardware that operates on wide registers of data, applying a Single Instruction to Multiple Data lanes in parallel, where lanes divide a register into a vector of scalar elements of equal size. This model is an excellent fit for the wide stack items of the EVM, offering substantial performance boosts for operations that can be expressed as parallel operations on vectors of scalars. For some examples, a brief literature search finds SIMD speedups of
>   * up to 7X for [SHA-512](http://keccak.noekeon.org/sw_performance.html)
>   * 4X for [elliptic curve scalar multiplication](http://link.springer.com/chapter/10.1007/3-540-45439-X_16)
>   * 3X to 4X for [BLAKE2b](https://github.com/minio/blake2b-simd)
>   * up to 3X for [OpenSSL](https://software.intel.com/en-us/articles/improving-openssl-performance)
>   * 2X to 3X for [elliptic curve modular multiplication](http://ieee-hpec.org/2013/index_htm_files/24-Simd-acceleration-Pabbuleti-2886999.pdf)
>   * 1.7X to 1.9X for [SHA-256](https://github.com/minio/sha256-simd)
>   * 1.3X for [RSA encryption](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.738.1218&rep=rep1&type=pdf)

### Multiple Instruction / Multiple Data (MIMD Parallelism)
(maybe)

### Variable-Width VM Word Size

(example: flag to enable native 32-bit arithmetic on the EVM)

## Memory

### Arbitrary local memory alignment (easier to solve for and much faster symbolic execution than byte-aligned)

## Analytic Optimization

client-specific, but can write general guidelines and reference implementations in Parity, EeVeeM, &c

## Tail Call Optimization
VM-level

## Incremental JIT optimization

## EVM-to-native smart contract compilation

## Automatic naive wordsize detection (ex. sequences of `ADDMOD 32` don’t need to store as 256-bit)
Adjust gas cost to make native wordsize (or easily aligned) operations cheaper

## Decoupled gas metering / gas aggregation

## Shared bytecode linking (contract size)

# Simplicity / Clean Up
## Deprecate dynamic jumps
## Deprecate Precompiles (controversial!)
      ▪ Move cryptographic primitives into the mostly empty 0x20 opcode range
