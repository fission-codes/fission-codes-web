---
layout: default
parent: FISSION Translate
title: Rationale
nav_order: 5
---

## `bytes32` Keys

`bytes32` is very efficient since it is the EVM's base word size. Given the enormous number of elements (```|A| > 1.1579 × 10```<sup>77</sup>), it can embed nearly any practical signal, enum, or state. In cases where an application's key is longer than `bytes32`, hashing that long key can map that value into the correct width.

Designs that use datatypes with small widths than `bytes32` (such as `bytes1` in [ERC-1066](https://eips.ethereum.org/EIPS/eip-1066)) can be directly embedded into the larger width. This is a trivial one-to-one mapping of the smaller set into the the larger one.

## Local vs Globals and Singletons

This spec has opted to not _force_ a single global registry, and rather allow any contract and use case deploy their own system. This allows for more flexibility, and does not restrict the community for opting to use singleton `LocalizationPreference` contracts for common use cases, share `Localization`s between different proxys, delegate translations between `Localization`s, and so on.

There are many practical uses of agreed upon singletons. For instance, translating codes that aim to be fairly universal and integrated directly into the broader ecosystem (wallets, frameworks, debuggers, and the like) will want to have a single `LocalizationPreference`.

Rather the dispersing several `LocalizationPreference`s for different use cases and codes, one could imagine a global "registry of registries". While this approach allows for a unified lookups of all translations in all use cases, it is antithetical to the spirit of decentralization and freedom. Such a system also increases the lookup complexity, places an onus on getting the code right the first time (or adding the overhead of an upgradable contract), and need to account for use case conflicts with a "unified" or centralized numbering system. Further, lookups should be lightweight (especially in cases like looking up revert text).

For these reasons, this spec chooses the more decentralized, lightweight, free approach, at the cost of on-chain discoverability. A registry could still be compiled, but would be difficult to enforce, and is out of scope of this spec.

## Off Chain Storage

A very viable alternative is to store text off chain, with a pointer to the translations on-chain, and emit or return a `bytes32` code for another party to do the lookup. It is difficult to guarantee that off-chain resources will be available, and requires coordination from some other system like a web server to do the code-to-text matching. This is also not compatible with `revert` messages.

## ASCII vs UTF-8 vs UTF-16

UTF-8 is the most widely used encoding at time of writing. It contains a direct embedding of ASCII, while providing characters for most natural languages, emoji, and special characters.

Please see the [UTF-8 Everywhere Manifesto](http://utf8everywhere.org/) for more information.

## When No Text is Found

Returning a blank string to the requestor fully defeats the purpose of a localization system. The two options for handling missing text are:

1. A generic "text not found" message in the preferred language
2. The actual message, in a different language

### Generic Option

This design opted to not use generic fallback text. It does not provide any useful information to the user other than to potentially contact the `Localization` maintainer (if one even exists and updating is even possible).

### Fallback Option

The design outlined in this proposal is to providing text in a commonly used language (ex. English or Mandarin). First, this is the language that will be routed to if the user has yet to set a preference. Second, there is a good chance that a user may have _some_ proficiency with the language, or at least be able to use an automated translation service.

Knowing that the text fell back via `textFor`s first return field boolean is _much_ simpler than attempting language detection after the fact. This information is useful for certain UI cases. for example where there may be a desire to explain why localization fell back.

## Decentralized Text Crowdsourcing

In order for Ethereum to gain mass adoption, users must be able to interact with it in the language, phrasing, and level of detail that they are most comfortable with. Rather than imposing a fixed set of translations as in a traditional, centralized application, this EIP provides a way for anyone to create, curate, and use translations. This empowers the crowd to supply culturally and linguistically diverse messaging, leading to broader and more distributed access to information.

## `printf`-style Format Strings

C-style `printf` templates have been the de facto standard for some time. They have wide compatibility across most languages (either in standard or third-party libraries). This makes it much easier for the consuming program to interpolate strings with low developer overhead.

### Parameter Fields

The POSIX parameter field extension is important since languages do not share a common word order. Parameter fields enable the reuse and rearrangement of arguments in different localizations.

```js
("%1$s is an element with the atomic number %2$d!", "Mercury", 80);
// => "Mercury is an element with the atomic number 80!"
```

### Simplified Localizations

Localization text does not require use of all parameters, and may simply ignore values. This can be useful for not exposing more technical information to users that would otherwise find it confusing.

```ruby
#!/usr/bin/env ruby

sprintf("%1$s é um elemento", "Mercurio", 80)
# => "Mercurio é um elemento"
```

```clojure
#!/usr/bin/env clojure

(format "Element #%2$s" "Mercury" 80)
;; => Element #80
```

## Interpolation Strategy

Please note that it is highly advisable to return the template string _as is_, with arguments as multiple return values or fields in an `event`, leaving the actual interpolation to be done off chain.


```js
event AtomMessage {
  bytes32 templateCode;
  bytes32 atomCode;
  uint256 atomicNumber;
}
```

```javascript
#!/usr/bin/env node

var printf = require('printf');

const { returnValues: { templateCode, atomCode, atomicNumber } } = eventResponse;

const template = await AppText.textFor(templateCode);
// => "%1$s ist ein Element mit der Ordnungszahl %2$d!"

const atomName = await PeriodicTableText.textFor(atomCode);
// => "Merkur"

printf(template, atomName, 80);
// => "Merkur ist ein Element mit der Ordnungszahl 80!"
```

## Unspecified Behaviour

This spec does not specify:

* Public or private access to the default `Localization`
* Who may set text
  * Deployer
  * `onlyOwner`
  * Anyone
  * Whitelisted users
  * and so on
* When text is set
  * `constructor`
  * Any time
  * Write to empty slots, but not overwrite existing text
  * and so on

These are intentionally left open. There are many cases for each of these, and restricting any is fully beyond the scope of this proposal.