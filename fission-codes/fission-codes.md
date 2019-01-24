---
layout: default
title: FISSION Codes
has_children: true
parent: FISSION Codes
permalink: /fission-codes/
nav_order: 2
---

## Broadly applicable status codes for smart contracts.

This standard outlines a common set of status codes in a similar vein to HTTP statuses. This provides a shared set of signals to allow smart contracts to react to situations autonomously, expose localized error messages to users, and so on.

The current state of the art is to either `revert` on anything other than a clear success (ie: require human intervention), or return a low-context `true` or `false`. Status codes are similar-but-orthogonal to `revert`ing with a reason, but aimed at automation, debugging, and end-user feedback (including translation). _They are fully compatible with both `revert` and `revert`-with-reason._

As is the case with HTTP, having a standard set of known codes has many benefits for developers. They remove friction from needing to develop your own schemes for every contract, makes inter-contract automation easier, and makes it easier to broadly understand which of the finite states your request produced. Importantly, it makes it much easier to distinguish between expected errors states, truly exceptional conditions that require halting execution, normal state transitions, and various success cases.

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

