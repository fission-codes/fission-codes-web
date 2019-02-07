---
layout: default
parent: FAQ
title: Precompiles vs. Opcodes
nav_order: 2
---

# Precompiles vs. Opcodes

The Ethereum Virtual Machine (EVM) specification and implementations contain both precompiles and opcodes. Precompiles is a specific term used by the Ethereum community. Various cryptographic functions are currently too slow to be run directly by the EVM, so instead the concept of a 'precompile' is used.

Rather than an opcode, smart contract code makes a call to a special Ethereum account address which corresponds to a specific precompile.

When an Ethereum client's EVM executes this, it checks the address, and if it is one of the precompiles, and executes it with natively implemented code.

For opcodes, smart contract languages (Solidity, Vyper, etc.) need to explicitly have support for the opcode built in.

For precompiles, smart contract languages see it just as any other call to an external smart contract library. So, the one benefit to precompiles, is that it can be deployed and implemented in Ethereum clients without having to have specific support in the smart contract language. For alternate chains, this is one way they might launch different, unique features

Since hardforks are typically planned well in advance, and smart contract languages. 

## Can we add more opcodes / implement precompiles as opcodes?

Yes! No reason not to do this. There's lots of room.