---
layout: default
title: FISSION Translate
has_children: true
parent: FISSION Translate
permalink: /fission-translate/
nav_order: 3
---
# FISSION Translate

## A method of converting machine codes to human-readable text in any language and phrasing.

An on-chain system for providing user feedback by converting machine-efficient codes into human-readable strings in any language or phrasing. The system does not impose a list of languages, but rather lets users create, share, and use the localizated text of their choice.

## Motivation

There are many cases where an end user needs feedback or instruction from a smart contact. Directly exposing numeric codes does not make for good UX or DX. If Ethereum is to be a truly global system usable by experts and lay persons alike, systems to provide feedback on what happened during a transaction are needed in as many languages as possible.

Returning a hard-coded string (typically in English) only serves a small segment of the global population. This standard proposes a method to allow users to create, register, share, and use a decentralized collection of translations, enabling richer messaging that is more culturally and linguistically diverse.

There are several machine efficient ways of representing intent, status, state transition, and other semantic signals including booleans, enums and [ERC-1066 codes](https://eips.ethereum.org/EIPS/eip-1066). By providing human-readable messages for these signals, the developer experience is enhanced by returning easier to consume information with more context (ex. `revert`). End user experience is enhanced by providing text that can be propagated up to the UI.

## Implementation

Reference cases and helper libraries (Solidity and JS) can be found at:

* [Package on npm](https://www.npmjs.com/package/ethereum-localized-messaging)
* [FISSION Translate](https://github.com/fission-suite/fission-translate)
