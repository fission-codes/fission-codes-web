---
layout: default
title: Jello Paper as Canonical Specification for the EVM
parent: Projects
nav_order: 8
tags:
  - Jello Paper
  - KEVM
  - EVM
  - specification
status: "In Progress"
---
# Jello Paper as Canonical Specification for the EVM

The Yellow Paper was the original specification of the Ethereum Virtual Machine (EVM).

The [Jello Paper](https://jellopaper.org/) defines the semantics of the EVM using the [KEVM project](https://github.com/kframework/evm-semantics).

> The KEVM semantics described by the Jello Paper is the first machine-executable, mathematically formal, human readable, and complete semantics of the EVM. KEVM is capable of passing the full EVM VMTests and GeneralStateTests testing suites, and can also be used in smart contract formal verification, debugging, and more.

## Completed

* Purchased and setup a redirect for yellowpaper-dot-io, so that [yellowpaper.club](https://yellowpaper.club) points to the PDF
* Kicked off [discussion on EthMagicians on this topic](https://ethereum-magicians.org/t/jello-paper-as-canonical-evm-spec/2389)
* Requested filing of an issue to [generate the Jello Paper as part of CI job](https://github.com/kframework/evm-semantics/issues/293)


## Next Steps

* Write up and submit an Informational EIP to have the Jello Paper accepted as the Canonical Specificatio for the EVM
* Post issues / bounty for defining the Constantinople EIPs as part of the Jello Paper
* (potential) K-EVM workshop around Council of Paris 2019 / ETHCC



