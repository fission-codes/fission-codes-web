---
layout: default
title: FISSION Codes
has_children: true
parent: FISSION Codes
permalink: /fission-codes/
nav_order: 2
---
# FISSION Codes
{:.no_toc}
## Broadly applicable status codes for smart contracts.
{:.no_toc}
This standard outlines a common set of status codes in a similar vein to HTTP statuses. This provides a shared set of signals to allow smart contracts to react to situations autonomously, expose localized error messages to users, and so on.

The current state of the art is to either `revert` on anything other than a clear success (ie: require human intervention), or return a low-context `true` or `false`. Status codes are similar-but-orthogonal to `revert`ing with a reason, but aimed at automation, debugging, and end-user feedback (including translation). _They are fully compatible with both `revert` and `revert`-with-reason._

As is the case with HTTP, having a standard set of known codes has many benefits for developers. They remove friction from needing to develop your own schemes for every contract, makes inter-contract automation easier, and makes it easier to broadly understand which of the finite states your request produced. Importantly, it makes it much easier to distinguish between expected errors states, truly exceptional conditions that require halting execution, normal state transitions, and various success cases.

1. Table of Contents
{:toc}

## Funding

### Gitcoin Grants

We would like to fund more work with bounties on implementation of contracts that use status codes, audits of re-usable contracts, and continue growing the number of languages supported by FISSION Translate. This grant will allow us to commit on-going maintenance, new standard creation, implementation for other smart contract and programming languages, other blockchains, and actively dedicate time to continuing to improve, evolve, and support the system.

<a href="https://gitcoin.co/grants/43/fission-codes" class="btn btn-purple">Contribute to Gitcoin Grant</a>

### Tachyon18 by ConsenSys Ventures

We were part of the ConsenSys Ventures Tachyon accelerator program 2018 fall cohort. Thank you to ConsenSys for the generous open source grant. We [completed the program in mid November 2018](https://fission.codes/post/consensys-tachyon).

## Updates

<ul>
{% assign projectposts = site.posts | where: "project", "fissioncodes" %}
{% for post in projectposts limit: 5 %}
  <li><strong>{{ post.date | date_to_string: "ordinal", "US" }}:</strong> {{ post.content | remove: "<p>" | remove: "</p>" }}</li>
{% endfor %}
</ul>

---

## Presentations

### ERC1066: Better UX & DX in Just One Byte - DevCon4 - Nov 1, 2018

<div id="presentation-embed-38911936"></div>
<script src='https://slideslive.com/embed_presentation.js'></script>
<script>
    embed = new SlidesLiveEmbed('presentation-embed-38911936', {
        presentationId: '38911936',
        autoPlay: false // change to true to autoplay the embedded presentation
    });
</script>


## Implementation

Reference cases and helper libraries (Solidity and JS) can be found at:
* [Source Code](https://github.com/fission-suite/fission-codes/)
* [Package on npm](https://www.npmjs.com/package/fission-codes/)

## Example Function Change

```solidity
uint256 private startTime;
mapping(address => uint) private counters;

// Before
function increase() public returns (bool _available) {
    if (now < startTime && counters[msg.sender] == 0) {
        return false;
    };

    counters[msg.sender] += 1;
    return true;
}

// After
function increase() public returns (byte _status) {
    if (now < start) { return hex"44"; } // Not yet available
    if (counters[msg.sender] == 0) { return hex"10"; } // Not authorized

    counters[msg.sender] += 1;
    return hex"01"; // Success
}
```

## Example Sequence Diagrams

```
0x03 = Waiting
0x31 = Other Party (ie: not you) Agreed
0x41 = Available
0x44 = Not Yet Available


                          Exchange


AwesomeCoin                 DEX                     TraderBot
     +                       +                          +
     |                       |       buy(AwesomeCoin)   |
     |                       | <------------------------+
     |         buy()         |                          |
     | <---------------------+                          |
     |                       |                          |
     |     Status [0x44]     |                          |
     +---------------------> |       Status [0x44]      |
     |                       +------------------------> |
     |                       |                          |
     |                       |        isDoneYet()       |
     |                       | <------------------------+
     |                       |                          |
     |                       |       Status [0x44]      |
     |                       +------------------------> |
     |                       |                          |
     |                       |                          |
     |     Status [0x41]     |                          |
     +---------------------> |                          |
     |                       |                          |
     |       buy()           |                          |
     | <---------------------+                          |
     |                       |                          |
     |                       |                          |
     |     Status [0x31]     |                          |
     +---------------------> |      Status [0x31]       |
     |                       +------------------------> |
     |                       |                          |
     |                       |                          |
     |                       |                          |
     |                       |                          |
     +                       +                          +
```



```
0x01 = Generic Success
0x10 = Disallowed
0x11 = Allowed

                                              Token Validation


           Buyer                  RegulatedToken           TokenValidator               IDChecker          SpendLimiter
             +                          +                         +                         +                   +
             |        buy()             |                         |                         |                   |
             +------------------------> |          check()        |                         |                   |
             |                          +-----------------------> |          check()        |                   |
             |                          |                         +-----------------------> |                   |
             |                          |                         |                         |                   |
             |                          |                         |         Status [0x10]   |                   |
             |                          |       Status [0x10]     | <-----------------------+                   |
             |        revert()          | <-----------------------+                         |                   |
             | <------------------------+                         |                         |                   |
             |                          |                         |                         |                   |
+---------------------------+           |                         |                         |                   |
|                           |           |                         |                         |                   |
| Updates ID with provider  |           |                         |                         |                   |
|                           |           |                         |                         |                   |
+---------------------------+           |                         |                         |                   |
             |                          |                         |                         |                   |
             |         buy()            |                         |                         |                   |
             +------------------------> |        check()          |                         |                   |
             |                          +-----------------------> |         check()         |                   |
             |                          |                         +-----------------------> |                   |
             |                          |                         |                         |                   |
             |                          |                         |       Status [0x11]     |                   |
             |                          |                         | <-----------------------+                   |
             |                          |                         |                         |                   |
             |                          |                         |                         |   check()         |
             |                          |                         +-------------------------------------------> |
             |                          |                         |                         |                   |
             |                          |                         |                         |  Status [0x11]    |
             |                          |       Status [0x11]     | <-------------------------------------------+
             |        Status [0x01]     | <-----------------------+                         |                   |
             | <------------------------+                         |                         |                   |
             |                          |                         |                         |                   |
             |                          |                         |                         |                   |
             |                          |                         |                         |                   |
             +                          +                         +                         +                   +
```

