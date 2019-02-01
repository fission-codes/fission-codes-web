---
layout: default
parent: FISSION Codes
title: Codes
nav_order: 4
---

## Format
{:no_toc}

Codes are returned either on their own, or as the first value of a multiple return.

```solidity
// Status only

function isInt(uint num) public pure returns (byte status) {
    return hex"01";
}

// Status and value

uint8 private counter;

function safeIncrement(uint8 interval) public returns (byte status, uint8 newCounter) {
    uint8 updated = counter + interval;

    if (updated >= counter) {
        counter = updated;
        return (hex"01", updated);
    } else {
        return (hex"00", counter);
    }
}
```

Codes break nicely into a 16x16 matrix, represented as a 2-digit hex number. The high nibble represents the code's kind or "category", and the low nibble contains the state or "reason". We present them below as separate tables per range for explanatory and layout reasons.

**NB: Unspecified codes are _not_ free for arbitrary use, but rather open for further specification.**

1. Table of Contents
{:toc}

#### `0x0*` Generic

General codes. These double as bare "reasons", since `0x01 == 1`.

| Code   | Description                             |
|--------|-----------------------------------------|
| `0x00` | Failure                                 |
| `0x01` | Success                                 |
| `0x02` | Awaiting Others                         |
| `0x03` | Accepted                                |
| `0x04` | Lower Limit or Insufficient             |
| `0x05` | Reciever Action Requested               |
| `0x06` | Upper Limit                             |
| `0x07` | [reserved]                              |
| `0x08` | Duplicate, Unnessesary, or Inapplicable |
| `0x09` | [reserved]                              |
| `0x0A` | [reserved]                              |
| `0x0B` | [reserved]                              |
| `0x0C` | [reserved]                              |
| `0x0D` | [reserved]                              |
| `0x0E` | [reserved]                              |
| `0x0F` | Informational or Metadata               |

#### `0x1*` Permission & Control

Also used for common state machine actions (ex. "stoplight" actions).

| Code   | Description                                       |
|--------|---------------------------------------------------|
| `0x10` | Disallowed or Stop                                |
| `0x11` | Allowed or Go                                     |
| `0x12` | Awaiting Other's Permission                       |
| `0x13` | Permission Requested                              |
| `0x14` | Too Open / Insecure                               |
| `0x15` | Needs Your Permission or Request for Continuation |
| `0x16` | Revoked or Banned                                 |
| `0x17` | [reserved]                                        |
| `0x18` | Not Applicatable to Current State                 |
| `0x19` | [reserved]                                        |
| `0x1A` | [reserved]                                        |
| `0x1B` | [reserved]                                        |
| `0x1C` | [reserved]                                        |
| `0x1D` | [reserved]                                        |
| `0x1E` | [reserved]                                        |
| `0x1F` | Permission Details or Control Conditions          |

#### `0x2*` Find, Inequalities & Range

This range is broadly intended for finding and matching. Data lookups and order matching are two common use cases.

| Code   | Description                         |
|--------|-------------------------------------|
| `0x20` | Not Found, Unequal, or Out of Range |
| `0x21` | Found, Equal or In Range            |
| `0x22` | Awaiting Match                      |
| `0x23` | Match Request Sent                  |
| `0x24` | Below Range or Underflow            |
| `0x25` | Request for Match                   |
| `0x26` | Above Range or Overflow             |
| `0x27` | [reserved]                          |
| `0x28` | Duplicate, Conflict, or Collision   |
| `0x29` | [reserved]                          |
| `0x2A` | [reserved]                          |
| `0x2B` | [reserved]                          |
| `0x2C` | [reserved]                          |
| `0x2D` | [reserved]                          |
| `0x2E` | [reserved]                          |
| `0x2F` | Matching Meta or Info               |

#### `0x3*` Negotiation & Governance

Negotiation, and very broadly the flow of such transactions. Note that "other party" may be more than one actor (not necessarily the sender).

| Code   | Description                             |
|--------|-----------------------------------------|
| `0x30` | Sender Disagrees or Nay                 |
| `0x31` | Sender Agrees or Yea                    |
| `0x32` | Awaiting Ratification                   |
| `0x33` | Offer Sent or Voted                     |
| `0x34` | Quorum Not Reached                      |
| `0x35` | Receiver's Ratification Requested       |
| `0x36` | Offer or Vote Limit Reached             |
| `0x37` | [reserved]                              |
| `0x38` | Already Voted                           |
| `0x39` | [reserved]                              |
| `0x3A` | [reserved]                              |
| `0x3B` | [reserved]                              |
| `0x3C` | [reserved]                              |
| `0x3D` | [reserved]                              |
| `0x3E` | [reserved]                              |
| `0x3F` | Negotiation Rules or Participation Info |

#### `0x4*` Availability & Time

Service or action availability.

| Code   | Description                                          |
|--------|------------------------------------------------------|
| `0x40` | Unavailable                                          |
| `0x41` | Available                                            |
| `0x42` | Paused                                               |
| `0x43` | Queued                                               |
| `0x44` | Not Available Yet                                    |
| `0x45` | Awaiting Your Availability                           |
| `0x46` | Expired                                              |
| `0x47` | [reserved]                                           |
| `0x48` | Already Done                                         |
| `0x49` | [reserved]                                           |
| `0x4A` | [reserved]                                           |
| `0x4B` | [reserved]                                           |
| `0x4C` | [reserved]                                           |
| `0x4D` | [reserved]                                           |
| `0x4E` | [reserved]                                           |
| `0x4F` | Availability Rules or Info (ex. time since or until) |

#### `0x5*` Tokens, Funds & Finance

Special token and financial concepts. Many related concepts are included in other ranges.

| Code   | Description                     |
|--------|---------------------------------|
| `0x50` | Transfer Failed                 |
| `0x51` | Transfer Successful             |
| `0x52` | Awaiting Payment From Others    |
| `0x53` | Hold or Escrow                  |
| `0x54` | Insufficient Funds              |
| `0x55` | Funds Requested                 |
| `0x56` | Transfer Volume Exceeded        |
| `0x57` | [reserved]                      |
| `0x58` | Funds Not Required              |
| `0x59` | [reserved]                      |
| `0x5A` | [reserved]                      |
| `0x5B` | [reserved]                      |
| `0x5C` | [reserved]                      |
| `0x5D` | [reserved]                      |
| `0x5E` | [reserved]                      |
| `0x5F` | Token or Financial Information |

#### `0x6*` TBD

Currently unspecified. (Full range reserved)

#### `0x7*` TBD

Currently unspecifie. (Full range reserved)

#### `0x8*` TBD

Currently unspecified. (Full range reserved)

#### `0x9*` TBD

Currently unspecified. (Full range reserved)

#### `0xA*` Application-Specific Codes

Contracts may have special states that they need to signal. This proposal only outlines the broadest meanings, but implementers may have very specific meanings for each, as long as they are coherent with the broader definition.

| Code   | Description                            |
|--------|----------------------------------------|
| `0xA0` | App-Specific Failure                   |
| `0xA1` | App-Specific Success                   |
| `0xA2` | App-Specific Awaiting Others           |
| `0xA3` | App-Specific Acceptance                |
| `0xA4` | App-Specific Below Condition           |
| `0xA5` | App-Specific Receiver Action Requested |
| `0xA6` | App-Specific Expiry or Limit           |
| `0xA7` | [reserved]                             |
| `0xA8` | App-Specific Inapplicable Condition    |
| `0xA9` | [reserved]                             |
| `0xAA` | [reserved]                             |
| `0xAB` | [reserved]                             |
| `0xAC` | [reserved]                             |
| `0xAD` | [reserved]                             |
| `0xAE` | [reserved]                             |
| `0xAF` | App-Specific Meta or Info              |

#### `0xB*` TBD

Currently unspecified. (Full range reserved)

#### `0xC*` TBD

Currently unspecified. (Full range reserved)

#### `0xD*` TBD

Currently unspecified. (Full range reserved)

#### `0xE*` Encryption, Identity & Proofs

Actions around signatures, cryptography, signing, and application-level authentication.

The meta code `0xEF` is often used to signal a payload descibing the algorithm or process used.

| Code   | Description                         |
|--------|-------------------------------------|
| `0xE0` | Decrypt Failure                     |
| `0xE1` | Decrypt Success                     |
| `0xE2` | Awaiting Other Signatures or Keys   |
| `0xE3` | Signed                              |
| `0xE4` | Unsigned or Untrusted               |
| `0xE5` | Signature Required                  |
| `0xE6` | Known to be Compromised             |
| `0xE7` | [reserved]                          |
| `0xE8` | Already Signed or Not Encrypted     |
| `0xE9` | [reserved]                          |
| `0xEA` | [reserved]                          |
| `0xEB` | [reserved]                          |
| `0xEC` | [reserved]                          |
| `0xED` | [reserved]                          |
| `0xEE` | [reserved]                          |
| `0xEF` | Cryptography, ID, or Proof Metadata |

#### `0xF*` Off-Chain

For off-chain actions. Much like th `0x0*: Generic` range, `0xF*` is very general, and does little to modify the reason.

Among other things, the meta code `0xFF` may be used to describe what the off-chain process is.

| Code   | Description                       |
|--------|-----------------------------------|
| `0xF0` | Off-Chain Failure                 |
| `0xF1` | Off-Chain Success                 |
| `0xF2` | Awaiting Off-Chain Process        |
| `0xF3` | Off-Chain Process Started         |
| `0xF4` | Off-Chain Service Unreachable     |
| `0xF5` | Off-Chain Action Required         |
| `0xF6` | Off-Chain Expiry or Limit Reached |
| `0xF7` | [reserved]                        |
| `0xF8` | Duplicate Off-Chain Request       |
| `0xF9` | [reserved]                        |
| `0xFA` | [reserved]                        |
| `0xFB` | [reserved]                        |
| `0xFC` | [reserved]                        |
| `0xFD` | [reserved]                        |
| `0xFE` | [reserved]                        |
| `0xFF` | Off-Chain Info or Meta            |

