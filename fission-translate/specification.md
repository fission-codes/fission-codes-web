---
layout: default
parent: FISSION Translate
title: Specification
nav_order: 3
---

## Contract Architecture

Two types of contract: `LocalizationPreferences`, and `Localization`s.

The `LocalizationPreferences` contract functions as a proxy for `tx.origin`.

```diagram
                                                                   +--------------+
                                                                   |              |
                                                          +------> | Localization |
                                                          |        |              |
                                                          |        +--------------+
                                                          |
                                                          |
+-----------+          +-------------------------+        |        +--------------+
|           |          |                         | <------+        |              |
| Requestor | <------> | LocalizationPreferences | <-------------> | Localization |
|           |          |                         | <------+        |              |
+-----------+          +-------------------------+        |        +--------------+
                                                          |
                                                          |
                                                          |        +--------------+
                                                          |        |              |
                                                          +------> | Localization |
                                                                   |              |
                                                                   +--------------+
```

## `Localization`

A contract that holds a simple mapping of codes to their text representations.

```js
interface Localization {
  function textFor(bytes32 _code) external view returns (string _text);
}
```

### `textFor`

Fetches the localized text representation.

```js
function textFor(bytes32 _code) external view returns (string _text);
```

## `LocalizationPreferences`

A proxy contract that allows users to set their preferred `Localization`. Text lookup is delegated to the user's preferred contract.

A fallback `Localization` with all keys filled MUST be available. If the user-specified `Localization` has not explicitly set a loalization (ie. `textFor` returns `""`), the `LocalizationPreferences` MUST redelegate to the fallback `Localization`.

```js
interface LocalizationPreferences {
  function set(Localization _localization) external returns (bool);
  function textFor(bytes32 _code) external view returns (bool _wasFound, string _text);
}
```

### `set`

Registers a user's preferred `Localization`. The registering user SHOULD be considered `tx.origin`.

```js
function set(Localization _localization) external;
```

### `textFor`

Retrieve text for a code found at the user's preferred `Localization` contract.

The first return value (`bool _wasFound`) represents if the text is available from that `Localization`, or if a fallback was used. If the fallback was used in this context, the `textFor`'s first return value MUST be set to `false`, and is `true` otherwise.

```js
function textFor(bytes32 _code) external view returns (bool _wasFound, string _text);
```

## String Format

All strings MUST be encoded as [UTF-8](http://www.ietf.org/rfc/rfc3629.txt).

```js
"Špeĉiäl chârãçtérs are permitted"
"As are non-Latin characters: アルミ缶の上にあるみかん。"
"Emoji are legal: 🙈🙉🙊🎉"
"Feel free to be creative: (ﾉ◕ヮ◕)ﾉ*:･ﾟ✧"
```

## Templates

Template strings are allowed, and MUST follow the [ANSI C `printf`](http://pubs.opengroup.org/onlinepubs/009696799/utilities/printf.html) conventions.

```js
"Satoshi's true identity is %s"
```

Text with 2 or more arguments SHOULD use the POSIX parameter field extension.

```js
"Knock knock. Who's there? %1$s. %1$s who? %2$s!"
```