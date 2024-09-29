# Plan for OSSDev 2024

The goal of this semester is to contribute to the Rust compiler by developing a new code generation backend — the C codegen backend.

## Background

The Rust compiler, *rustc*, supports multiple code generation backends to target various architectures. The most prominent and mature backend is LLVM, which powers the default binary distribution of *rustc*.

While LLVM provides extensive architecture coverage, it does not support every platform with a C compiler. For niche architectures such as NonStop, AIX, and Solaris, *rustc* can rely on a C backend. This backend translates Rust code into C, which can then be compiled using the system's C compiler, bridging gaps in LLVM’s architecture support.

## Objectives

The primary objective of this project is to implement a C codegen backend for *rustc*, allowing Rust code to be translated into C and subsequently compiled with standard C compilers.

The project will be carried out in the following phases:

- **Development of the C Codegen Backend**: Implement the C codegen backend as an extension to *rustc*. This will involve translating Rust's intermediate representation (MIR) into valid C code.
- **Compilation of the Standard Library**: Compile the Rust standard library using the newly developed C backend, ensuring its ability to handle core functionalities present in most Rust programs.
- **Validation through Test Suites**: Execute the Rust test suite using the C backend to ensure that it generates C code functionally equivalent to the original Rust code.
- **Code Optimization**: Enhance the performance and readability of the generated C code by implementing optimizations, potentially incorporating transformations and tailoring the output for specific C compiler optimizations.
