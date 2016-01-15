---
layout: page
title: Language Specification
permalink: /specification/
---

# Source Files

Apterid code is contained in source files with the extension `.apterid`.  The Apterid compiler compiles the code in one or more source files into one binary, either a library or an executable (in .NET, an assembly).

# Syntax

Apterid syntax delimits scopes by means of indentation.

    public module MyModule =
      public type MyType =
        Field1 : int
        Field2 : string

      Fn1 : MyType -> int
      public Fn x =
        x.Field1

# Modules

Apterid code is organized in modules.  A module may be present in more than one source file, but types and bindings within a multi-file module must be uniquely named.

    public module Name.Space.OuterModule =
      public Fn1 x = InnerModule.Fn2 x

      module InnerModule =
        public Fn2 x = x * 2

- A module may contain zero or more types or bindings.
- A module at the outermost level of a source file may be qualified with a namespace.  Inner modules must be unqualified.
- A `public` module is visible from other binaries.
- `public` types and bindings are visible from outside the module.

# Types

## Primitive Types

The following primitive types are available in Apterid:

| Keyword      | .NET Type                  | Example                          | Remarks                                    |
| ------------ | -------------------------- | -------------------------------- | ------------------------------------------ |
| `bool`       | System.Boolean             | `true` `false`                   |                                            |
| `byte`       | System.Byte                | `1b`                             | Unsigned octet                             |
| `sbyte`      | System.SByte               | `1bs`                            | Signed octet                               |
| `int16`      | System.Int16               | `1s`                             |                                            |
| `uint16`     | System.UInt16              | `1su`                            |                                            |
| `int`        |                            | `1`                              | Alias for `int32`                          |
| `int32`      | System.Int32               | `1`                              |                                            |
| `uint32`     | System.UInt32              | `1u`                             |                                            |
| `int64`      | System.Int64               | `1l`                             |                                            |
| `uint64`     | System.UInt64              | `1lu`                            |                                            |
| `zint`       | System.Numerics.BigInteger | `1z`                             | Arbitrarily large integer                  |
| `ptr`        | System.IntPtr              |                                  | A native pointer as a signed integer       |
| `uptr`       | System.UIntPtr             |                                  |                                            |
| `char`       | System.Char                | `'a'`                            | UTF-16 code point                          |
| `float`      | System.Single              | `1.1f`, `1e2f`, `1.1e2f`, `-1.1e-2f` |                                        |
| `double`     | System.Double              | `1.1`, `1e2`, `1.1e2`, `-1.1e-2`     |                                        |
| `decimal`    | System.Decimal             | `1.1m`                           | Binary-coded decimal                       |
| `complex`    | System.Numerics.Complex    | `1 + 2i`                         | Complex number                             |
| `quaternion` | System.Numerics.Quaternion | `1 + 2i + 3j + 4k`               |                                            |
| `void`       | System.Void                | `()`                             | "unit" type                                |

## Sum Types

## Product Types

# Bindings
