---
layout: default
parent: FISSION Codes
title: Motivation
nav_order: 1
---

### Semantic Density

HTTP status codes are widely used for this purpose. BEAM languages use atoms and tagged tuples to signify much the same information. Both provide a lot of information both to the programmer (debugging for instance), and to the program that needs to decide what to do next.

Status codes convey a much richer set of information [than Booleans](https://existentialtype.wordpress.com/2011/03/15/boolean-blindness/), and are able to be reacted to autonomously unlike arbitrary strings.

### User Experience (UX)

_End users get little to no feedback, and there is no translation layer._

Since ERC1066 status codes are finite and known in advance, we can leverage [ERC1444](https://eips.ethereum.org/EIPS/eip-1444) to provide global, human-readable sets of status messages. These may also be translated into any language, differing levels of technical detail, added as `revert` messages, natspecs, and so on.

Status codes convey a much richer set of information than Booleans, and are able to be reacted to autonomously unlike arbitrary strings.

### Developer Experience (DX)

_Developers currently have very little context exposed by their smart contracts._

At time of writing, other than stepping through EVM execution and inspecting memory dumps directly, it is very difficult to understand what is happening during smart contract execution. By returning more context, developers can write well-decomposed tests and assert certain codes are returned as an expression of where the smart contract got to. This includes status codes as bare values, `event`s, and `revert`s.

Having a fixed set of codes also makes it possible to write common helper functions to react in common ways to certain signals. This can live off- or on-chain library, lowering the overhead in building smart contracts, and helping raise code quality with trusted shared components.

We also see a desire for this [in transactions](http://eips.ethereum.org/EIPS/eip-658), and there's no reason that these status codes couldn't be used by the EVM itself.

### Smart Contract Autonomy

_Smart contracts don’t know much about the result of a request beyond pass/fail; they can be smarter with more context._

Smart contracts are largely intended to be autonomous. While each contract may define a specific interface, having a common set of semantic codes can help developers write code that can react appropriately to various situations.

While clearly related, status codes are complementary to `revert`-with-reason. Status codes are not limited to rolling back the transaction, and may represent known error states without halting execution. They may also represent off-chain conditions, supply a string to revert, signal time delays, and more.

All of this enables contracts to share a common vocabulary of state transitions, results, and internal changes, without having to deeply understand custom status enums or the internal business logic of collaborator contracts.