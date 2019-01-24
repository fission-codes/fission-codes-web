---
layout: default
parent: FISSION Codes
title: Rationale
nav_order: 6
---

## Encoding

Status Codes are encoded as a `byte`. Hex values break nicely into high and low nibbles:
`category` and `reason`. For instance, `hex"01"` stands for general success
and `hex"00"` for general failure.

`byte` is quite lightweight, and can be easily packed with multiple codes into
a `bytes32` (or similar) if desired. It is also easily interoperable with `uint8`,
cast from `enum`s, and so on.

## Alternatives

Alternate schemes include `bytes32` and `uint8`. While these work reasonably
well, they have drawbacks.

`uint8` feels even more similar to HTTP status codes, and enums don't require
as much casting. However does not break as evenly as a square table
(256 doesn't look as nice in base 10).

Packing multiple codes into a single `bytes32` is nice in theory, but poses additional
challenges. Unused space may be interpeted as `0x00 Failure`, you can only efficiently
pack four codes at once, and there is a challenge in ensuring that code combinations
are sensible. Forcing four codes into a packed representation encourages multiple
status codes to be returned, which is often more information than strictly nessesary.
This can lead to paradoxical results (ex `0x00` and `0x01` together),
or greater resorces allocated to interpreting 256<sup>4</sup> (4.3 billion) permutations.

## Multiple Returns

While there may be cases where packing a byte array of ESCs may make sense, the simplest,
most forwards-compatible method of transmission is as the first value of a multiple return.

Familiarity is also a motivating factor. A consistent position and encoding together
follow the principle of least surprise. It is both viewable as a "header" in the HTTP analogy,
or like the "tag" in BEAM tagged tupples.

## Human Readable

Developers should not be required to memorize 256 codes. However, they break nicely into a table.
Cognitive load is lowered by organizing the table into categories and reasons.
`0x10` and `0x11` belong to the same category, and `0x04` shares a reason with `0x24`

While this repository includes helper enums, we have found working directly in
the hex values to be quite natural. ESC `0x10` is just as comfortable as HTTP 401, for example.

## Extensiblilty

The `0xA` category is reserved for application-specific statuses.
In the case that 256 codes become insufficient, `bytes1` may be embedded in larger byte arrays.

## EVM Codes

The EVM also returns a status code in transactions; specifically `0x00` and `0x01`.
This proposal both matches the meanings of those two codes, and could later be used
at the EVM level.

## Empty Space

Much like how HTTP status codes have large unused ranges, there are totally empty
sections in this proposal. The intent is to not impose a complete set of codes up front,
and to allow users to suggest uses for these spaces as time progresses.

## Nibble Order

Nibble order makes no difference to the machine, and is purely mnemonic.
This design was originally in opposite order, but changed it for a few convenience factors.
Since it's a different scheme from HTTP, it may feel strange initially,
but becomes very natural after a couple hours of use.

## Short Forms

Generic is `0x0_`, general codes are consistent with their integer representations

```js
hex"1" == hex"01" == 1 // with casting
```

## Contract Categories

Many applications will always be part of the same category.
For instance, validation will generally be in the `0x10` range.

```js
contract Whitelist {
    mapping(address => bool) private whitelist;
    uint256 private deadline;
    byte constant private prefix = hex"10";

    check(address _, address _user) returns (byte _status) {
        if (now >= deadline)  { return prefix | 5; }
        if (whitelist[_user]) { return prefix | 1; }
        return prefix;
    }
}
```

## Helpers

This above also means that working with app-specific enums is slightly easier:

```js
enum Sleep {
    Awake,
    Asleep,
    REM,
    FallingAsleep
}

// From the helper library

function appCode(Sleep _state) returns (byte code) {
    return byte(160 + _state); // 160 = 0xA0
}

// Versus

function appCode(Sleep _state) returns (byte code) {
    return byte((16 * _state) + 10); // 10 = 0xA
}
```
