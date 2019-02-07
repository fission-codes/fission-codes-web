---
layout: default
parent: EVM Evolution
title: LLVM-to-EVM
permalink: /evm-evolution/llvm-to-evm/
nav_order: 4
---

# LLVM-to-EVM

Creating an LLVM to EVM backend gives a number of benefits to the EVM Ecosystem. 

## Access to Toolchain

The LLVM ecosystem is very large, and has many excellent toolchain technologies.

> The LLVM Project is a collection of modular and reusable compiler and toolchain technologies. Despite its name, LLVM has little to do with traditional virtual machines. The name "LLVM" itself is not an acronym; it is the full name of the project.
>
> — [llvm.org](https://llvm.org/)

## Develop Specialized IRs

IRs (Intermediate Representations) can be tuned for different use cases. [Trail of Bits](https://www.trailofbits.com/) has created [SlithIR](https://github.com/trailofbits/slither/wiki/SlithIR), a security optimized Intermediate Representation. LLVM assists in creating and maintaining these IRs.

## Language Support

Languages with compilers that use LLVM include[^llvmwikipedia]: ActionScript, Ada, C#, Common Lisp, Crystal, CUDA, D, Delphi, Fortran, Graphical G Programming Language, Halide, Haskell, Java bytecode, Julia, Kotlin, Lua, Objective-C, OpenGL Shading Language, Pony, Python, R, Ruby, Rust, Scala, Swift, and Xojo.

Any of these languages could be used to develop smart contracts that could be compiled down to EVM bytecode and deployed on the current Ethereum network.


---

## Completed

* Early discussion with [Trail of Bits](https://www.trailofbits.com/) -- they are interested and have specialized team members who can help, would connect it as well with their SlithIR

## Next Steps

* Funding and grants -- early work included in 6 month 2019 EF grant, need 3 months of funding for at least FISSION & Trail of Bits collaborators
* work with Trail of Bits on SlithIR & LLVM
* Scope the LLVM codes to accept
* Write a bytecode validator to enforce the above
* Write an LLVM backend (to EVM target)
* Output EVM bytecode

---

[^llvmwikipedia]: From the [LLVM Wikipedia page](https://en.wikipedia.org/wiki/LLVM)