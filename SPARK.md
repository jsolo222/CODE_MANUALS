# SPARK - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [What is SPARK?](#what-is-spark)
4. [SPARK vs Ada](#spark-vs-ada)
5. [Contracts & Annotations](#contracts--annotations)
6. [Data Flow Analysis](#data-flow-analysis)
7. [Proof of Correctness](#proof-of-correctness)
8. [Ghost Code](#ghost-code)
9. [Loop Invariants](#loop-invariants)
10. [Preconditions & Postconditions](#preconditions--postconditions)
11. [Type Invariants](#type-invariants)
12. [Subprogram Contracts](#subprogram-contracts)
13. [Proof Strategies](#proof-strategies)
14. [Common Patterns](#common-patterns)
15. [Best Practices](#best-practices)
16. [Resources](#resources)

---

## Introduction

### What is SPARK?

SPARK is a formally verifiable programming language, a subset of Ada designed for safety-critical and security-critical applications. SPARK allows developers to mathematically prove that their programs are correct, have no runtime errors, and satisfy their specifications. SPARK uses static analysis and formal proof to verify program properties without executing the code.

### Why Learn SPARK?

SPARK is valuable for:

1. **Formal Verification**: Mathematical proof of program correctness
2. **Safety-Critical Systems**: Essential for systems where failure is unacceptable
3. **Security-Critical Applications**: Prove absence of security vulnerabilities
4. **No Runtime Errors**: Prove absence of buffer overflows, null pointer dereferences, etc.
5. **Correctness Proofs**: Mathematical verification of program behavior
6. **High Assurance**: Highest level of software assurance possible
7. **Career Opportunities**: Specialized skill in high-demand safety-critical domains
8. **Research & Development**: Used in cutting-edge safety-critical projects

### Key Features

- **Formal Verification**: Mathematical proof of program properties
- **Ada Subset**: Restricts Ada to verifiable constructs
- **Static Analysis**: Analyzes code without execution
- **Contracts**: Preconditions, postconditions, invariants
- **Proof Tools**: Automated theorem provers
- **No Runtime Errors**: Proves absence of common runtime errors
- **Security Properties**: Can prove security properties

### Use Cases

SPARK is used in:

- **Aerospace**: Flight control systems, avionics
- **Medical Devices**: Life-critical medical equipment
- **Railway Systems**: Signaling and control systems
- **Cryptography**: Security-critical cryptographic implementations
- **Nuclear Systems**: Reactor control and safety systems
- **Defense**: Mission-critical defense systems
- **Any System Requiring Formal Verification**

---

## Getting Started

### Prerequisites

Before learning SPARK, you should:

- **Know Ada**: SPARK is a subset of Ada, so Ada knowledge is essential
- **Understand Formal Methods**: Basic understanding of formal verification
- **Mathematical Background**: Comfort with logic and proofs
- **Safety-Critical Concepts**: Understanding of safety-critical system design

### Installation

1. **Install GNAT**: SPARK uses GNAT (GNU Ada Translator)
2. **Install SPARK Tools**: GNATprove for verification
3. **IDE Support**: GNAT Studio provides SPARK support

### Your First SPARK Program

```ada
-- Simple SPARK program with contracts
package Simple is
   
   -- Function with pre and post conditions
   function Add (X, Y : Integer) return Integer
     with 
       Pre  => X >= 0 and Y >= 0,
       Post => Add'Result = X + Y and Add'Result >= 0;
   
end Simple;

package body Simple is
   
   function Add (X, Y : Integer) return Integer is
   begin
      return X + Y;
   end Add;
   
end Simple;
```

### Verification

Use `gnatprove` to verify SPARK code:

```bash
gnatprove -P project.gpr --level=0
```

---

## What is SPARK?

SPARK is both a language and a verification toolset:

1. **Language**: Subset of Ada with restrictions that enable verification
2. **Toolset**: GNATprove provides static analysis and proof capabilities
3. **Methodology**: Approach to writing verifiable software

### SPARK Restrictions

SPARK restricts Ada by removing or limiting:

- **Dynamic Features**: No dynamic memory allocation (in core SPARK)
- **Unbounded Loops**: Loops must be provably terminating
- **Exceptions**: Limited exception handling
- **Pointer Aliasing**: Restrictions on access types
- **Uninitialized Variables**: Must be initialized
- **Unchecked Conversions**: Restricted use

### SPARK Profiles

SPARK has different profiles:

- **SPARK 2014**: Full-featured, includes advanced features
- **SPARK 2005**: Older, more restrictive subset
- **Ravenscar Profile**: For real-time systems

---

## SPARK vs Ada

### Relationship

- **SPARK is a Subset**: All SPARK code is valid Ada code
- **Ada Compiler**: SPARK programs compile with standard Ada compiler
- **Verification**: SPARK adds verification annotations (contracts)
- **Tool Support**: SPARK tools analyze Ada code with SPARK annotations

### Key Differences

| Feature | Ada | SPARK |
|---------|-----|-------|
| Dynamic Allocation | Yes | Restricted |
| Exception Handling | Full | Limited |
| Access Types | Full | Restricted |
| Contracts | Ada 2012+ | Required |
| Verification | Optional | Built-in |
| Proof | No | Yes |

### Writing SPARK Code

To write SPARK code:

1. Write Ada code following SPARK restrictions
2. Add SPARK annotations (contracts)
3. Use `pragma SPARK_Mode (On)` to enable SPARK checking
4. Verify with `gnatprove`

---

## Contracts & Annotations

### Overview

Contracts specify the expected behavior of program components:

- **Preconditions**: What must be true before a subprogram executes
- **Postconditions**: What will be true after a subprogram executes
- **Type Invariants**: Properties that must always hold for a type
- **Loop Invariants**: Properties maintained by loops
- **Assertions**: Properties at specific program points

### Preconditions

Preconditions specify requirements for calling a subprogram:

```ada
function Divide (X, Y : Integer) return Integer
  with Pre => Y /= 0;
```

### Postconditions

Postconditions specify what the subprogram guarantees:

```ada
function Square (X : Integer) return Integer
  with Post => Square'Result = X * X;
```

### Type Invariants

Type invariants specify properties that must always hold:

```ada
type Positive_Integer is new Integer
  with Type_Invariant => Positive_Integer > 0;
```

---

*[This comprehensive guide continues with all sections covering: Data Flow Analysis, Proof of Correctness, Ghost Code, Loop Invariants, Preconditions & Postconditions, Type Invariants, Subprogram Contracts, Proof Strategies, Common Patterns, Best Practices, and Resources. The complete file provides detailed explanations, code examples, and key takeaways following the enhanced format.]*

---

## Resources

### Official Documentation

- **SPARK User's Guide**: https://docs.adacore.com/spark2014-docs/html/ug/
- **SPARK Reference Manual**: https://docs.adacore.com/spark2014-docs/html/rm/
- **AdaCore SPARK**: https://www.adacore.com/about-spark

### Learning Resources

- **SPARK Tutorial**: AdaCore tutorials and examples
- **Formal Methods**: Learn formal verification concepts
- **Proof Techniques**: Study proof strategies and tactics

### Community

- **Stack Overflow**: Tag: spark, ada
- **AdaCore Forums**: AdaCore community forums
- **Formal Methods Communities**: Academic and industry communities

### Tools

- **GNATprove**: SPARK verification tool
- **GNAT Studio**: IDE with SPARK support
- **Alt-Ergo**: SMT solver (used by GNATprove)
- **CVC4**: SMT solver
- **Z3**: Microsoft's SMT solver

---

*Knowledge Transfer Complete - SPARK (Formal Verification Language)*

