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

## Preconditions & Postconditions

### Overview

Preconditions and postconditions are the fundamental contracts in SPARK. They specify what must be true before and after subprogram execution.

### Key Concepts

- **Preconditions**: Requirements that must be met when calling a subprogram
- **Postconditions**: Guarantees provided by the subprogram after execution
- **Function Results**: Use 'Result attribute in postconditions
- **Contract Verification**: SPARK verifies contracts statically

### Preconditions & Postconditions

**What this demonstrates:** Using preconditions and postconditions.

**Code:**
```ada
package Math_Contracts is
   
   -- Function with precondition and postcondition
   function Divide (X, Y : Integer) return Integer
     with 
       Pre  => Y /= 0,
       Post => Divide'Result = X / Y;
   
   -- Function with multiple postconditions
   function Factorial (N : Natural) return Natural
     with 
       Pre  => N <= 12,  -- Prevent overflow
       Post => Factorial'Result > 0 
               and then (N = 0 or Factorial'Result mod N = 0);
   
   -- Procedure with contracts
   procedure Increment (X : in out Integer)
     with 
       Pre  => X < Integer'Last,
       Post => X = X'Old + 1;
   
end Math_Contracts;

package body Math_Contracts is
   
   function Divide (X, Y : Integer) return Integer is
   begin
      return X / Y;
   end Divide;
   
   function Factorial (N : Natural) return Natural is
      Result : Natural := 1;
   begin
      for I in 1 .. N loop
         Result := Result * I;
      end loop;
      return Result;
   end Factorial;
   
   procedure Increment (X : in out Integer) is
   begin
      X := X + 1;
   end Increment;
   
end Math_Contracts;
```

**Explanation:**
- Pre: Condition that must hold before execution
- Post: Condition that must hold after execution
- 'Result: Function result in postconditions
- 'Old: Previous value in postconditions (for in out parameters)
- Contract checking: SPARK verifies these statically

**Key Takeaways:**
- Preconditions specify caller obligations
- Postconditions specify callee guarantees
- Use 'Result for function return values
- Use 'Old for previous parameter values

---

## Type Invariants

### Overview

Type invariants specify properties that must always hold for values of a type. They're checked after construction and modification.

### Key Concepts

- **Type Invariant**: Property that must always hold
- **Default Values**: Must satisfy invariant
- **Assignment**: Must maintain invariant
- **Type Safety**: Ensures type properties

### Type Invariants

**What this demonstrates:** Defining type invariants.

**Code:**
```ada
package Safe_Types is
   
   -- Type with invariant
   type Positive_Integer is new Integer
     with Type_Invariant => Positive_Integer > 0;
   
   -- Record type with invariant
   type Temperature is record
      Value : Integer;
   end record
     with Type_Invariant => Temperature.Value >= -273;
   
   -- Bounded type
   type Angle is new Float
     with Type_Invariant => Angle >= 0.0 and Angle < 360.0;
   
   -- Default values must satisfy invariant
   Default_Temp : constant Temperature := (Value => 20);
   
   function Create_Temperature (Val : Integer) return Temperature
     with Pre  => Val >= -273,
          Post => Create_Temperature'Result.Value = Val;
   
end Safe_Types;

package body Safe_Types is
   
   function Create_Temperature (Val : Integer) return Temperature is
   begin
      return (Value => Val);
   end Create_Temperature;
   
end Safe_Types;
```

**Explanation:**
- Type_Invariant: Property that must always hold
- Default values: Must satisfy invariant
- Assignment: SPARK verifies invariant maintained
- Constructor functions: Create values satisfying invariant

**Key Takeaways:**
- Use invariants for domain constraints
- Default values must satisfy invariants
- SPARK verifies invariants are maintained
- Constructors help create valid values

---

## Subprogram Contracts

### Overview

Subprogram contracts combine preconditions, postconditions, and other annotations to fully specify subprogram behavior.

### Key Concepts

- **Complete Contracts**: Preconditions + postconditions
- **Frame Conditions**: What the subprogram can modify
- **Global Annotations**: Dependencies on global state
- **Depends Clauses**: Input-output dependencies

### Subprogram Contracts

**What this demonstrates:** Complete subprogram contracts.

**Code:**
```ada
package Contract_Examples is
   
   -- Complete contract with all annotations
   procedure Swap (X, Y : in out Integer)
     with 
       Global => null,
       Depends => (X => Y, Y => X),
       Post => X = Y'Old and Y = X'Old;
   
   -- Function with global state
   Counter : Integer := 0;
   
   procedure Increment_Counter
     with 
       Global => (In_Out => Counter),
       Post => Counter = Counter'Old + 1;
   
   -- Function with dependencies
   function Maximum (A, B : Integer) return Integer
     with 
       Pre  => True,
       Post => Maximum'Result >= A 
               and Maximum'Result >= B
               and (Maximum'Result = A or Maximum'Result = B);
   
end Contract_Examples;

package body Contract_Examples is
   
   procedure Swap (X, Y : in out Integer) is
      Temp : Integer;
   begin
      Temp := X;
      X := Y;
      Y := Temp;
   end Swap;
   
   procedure Increment_Counter is
   begin
      Counter := Counter + 1;
   end Increment_Counter;
   
   function Maximum (A, B : Integer) return Integer is
   begin
      if A >= B then
         return A;
      else
         return B;
      end if;
   end Maximum;
   
end Contract_Examples;
```

**Explanation:**
- Global: Specifies global state accessed
- Depends: Specifies input-output dependencies
- Complete contracts: Full specification
- Verification: SPARK verifies all contracts

**Key Takeaways:**
- Use Global to specify global state access
- Use Depends for input-output dependencies
- Complete contracts enable full verification
- SPARK verifies all contract aspects

---

## Loop Invariants

### Overview

Loop invariants specify properties that hold before, during, and after each loop iteration. They're essential for proving loop correctness.

### Key Concepts

- **Loop Invariant**: Property maintained by loop
- **Variant**: Expression showing loop termination
- **Verification**: SPARK proves invariant maintained
- **Termination**: Variant proves loop terminates

### Loop Invariants

**What this demonstrates:** Using loop invariants.

**Code:**
```ada
package Loop_Examples is
   
   function Sum (A : Integer_Array) return Integer
     with Pre => A'Length > 0;
   
   function Find (A : Integer_Array; Value : Integer) return Natural
     with Post => (if Find'Result > 0 then A(Find'Result) = Value 
                   else (for all I in A'Range => A(I) /= Value));
   
end Loop_Examples;

package body Loop_Examples is
   
   function Sum (A : Integer_Array) return Integer is
      Result : Integer := 0;
   begin
      for I in A'Range loop
         Result := Result + A(I);
         pragma Loop_Invariant (Result = (for all J in A'First .. I => 
                                          (if J = A'First then A(J) 
                                           else Result - A(I) + A(J))));
      end loop;
      return Result;
   end Sum;
   
   function Find (A : Integer_Array; Value : Integer) return Natural is
   begin
      for I in A'Range loop
         pragma Loop_Invariant 
           (for all J in A'First .. I - 1 => A(J) /= Value);
         if A(I) = Value then
            return I;
         end if;
      end loop;
      return 0;
   end Find;
   
end Loop_Examples;
```

**Explanation:**
- Loop_Invariant: Property maintained by loop
- Variant: Expression decreasing (proves termination)
- Verification: SPARK proves invariant holds
- Termination: Variant proves loop terminates

**Key Takeaways:**
- Loop invariants specify loop properties
- Variants prove termination
- SPARK verifies invariants
- Invariants help prove correctness

---

## Data Flow Analysis

### Overview

SPARK performs data flow analysis to verify that variables are initialized before use and that data dependencies are correct.

### Key Concepts

- **Initialization**: Variables must be initialized
- **Data Flow**: Tracks how data flows through program
- **Uninitialized Variables**: Detected by SPARK
- **Dependencies**: Verified by data flow analysis

### Data Flow Analysis

**What this demonstrates:** SPARK data flow checking.

**Code:**
```ada
package Data_Flow is
   
   procedure Process_Data (Input : in Integer; Output : out Integer)
     with Post => Output = Input * 2;
   
   procedure Initialize_Array (A : out Integer_Array)
     with Post => (for all I in A'Range => A(I) = 0);
   
end Data_Flow;

package body Data_Flow is
   
   procedure Process_Data (Input : in Integer; Output : out Integer) is
   begin
      Output := Input * 2;  -- OK: Input is initialized (in parameter)
   end Process_Data;
   
   procedure Initialize_Array (A : out Integer_Array) is
   begin
      for I in A'Range loop
         A(I) := 0;  -- Initialize each element
      end loop;
      -- SPARK verifies all elements initialized
   end Initialize_Array;
   
end Data_Flow;
```

**Explanation:**
- Initialization: SPARK checks variables initialized
- Data flow: Tracks data through program
- Uninitialized: SPARK detects uninitialized use
- Verification: Automatic data flow checking

**Key Takeaways:**
- SPARK verifies initialization
- Data flow analysis is automatic
- Uninitialized variables detected
- Helps prevent runtime errors

---

## Proof of Correctness

### Overview

SPARK can prove that programs satisfy their contracts and are free from runtime errors. Proof provides mathematical certainty.

### Key Concepts

- **Proof**: Mathematical verification of properties
- **Runtime Errors**: Proves absence of errors
- **Contract Satisfaction**: Proves contracts hold
- **Proof Levels**: Different levels of verification

### Proof Levels

**What this demonstrates:** Understanding proof levels.

**SPARK Proof Levels:**
- **Level 0**: Flow analysis only (fastest)
- **Level 1**: Flow + some proofs (balanced)
- **Level 2**: Flow + more proofs (thorough)
- **Level 3**: Flow + all proofs (most thorough)
- **Level 4**: Flow + all proofs + counterexamples

**Code:**
```ada
package Proof_Example is
   
   -- Function with provable postcondition
   function Absolute (X : Integer) return Natural
     with Post => Absolute'Result = (if X >= 0 then X else -X)
                  and Absolute'Result >= 0;
   
end Proof_Example;

package body Proof_Example is
   
   function Absolute (X : Integer) return Natural is
   begin
      if X >= 0 then
         return Natural(X);
      else
         return Natural(-X);
      end if;
   end Absolute;
   
end Proof_Example;
```

**Explanation:**
- Proof levels: Different verification depths
- Runtime errors: Proved absent
- Contracts: Proved to hold
- Mathematical certainty: Formal verification

**Key Takeaways:**
- Proof provides mathematical certainty
- Different levels for different needs
- Proves absence of runtime errors
- Proves contract satisfaction

---

## Ghost Code

### Overview

Ghost code is code that exists only for verification and is removed during compilation. It helps with proofs without affecting execution.

### Key Concepts

- **Ghost**: Code for verification only
- **Compilation**: Ghost code removed
- **Proofs**: Helps with verification
- **Specifications**: Can use ghost variables

### Ghost Code

**What this demonstrates:** Using ghost code.

**Code:**
```ada
package Ghost_Example is
   
   function Factorial (N : Natural) return Natural
     with Post => Factorial'Result > 0;
   
end Ghost_Example;

package body Ghost_Example is
   
   function Factorial (N : Natural) return Natural is
      Result : Natural := 1;
      Ghost_Product : Natural := 1 with Ghost;  -- Ghost variable
   begin
      for I in 1 .. N loop
         Result := Result * I;
         Ghost_Product := Ghost_Product * I;  -- Track for proof
         pragma Loop_Invariant (Result = Ghost_Product);
         pragma Loop_Invariant (Ghost_Product > 0);
      end loop;
      return Result;
   end Factorial;
   
end Ghost_Example;
```

**Explanation:**
- Ghost: Marked with Ghost aspect
- Verification: Used only for proofs
- Compilation: Removed from executable
- Proofs: Helps with verification

**Key Takeaways:**
- Ghost code for verification only
- Removed during compilation
- Helps with proofs
- Useful for complex verifications

---

## Proof Strategies

### Overview

Proof strategies help guide SPARK's proof process. Understanding strategies improves verification success.

### Key Concepts

- **Lemma Functions**: Helper functions for proofs
- **Assert Statements**: Guide proofs
- **Proof Context**: Provide additional information
- **Manual Proof**: Sometimes needed for complex cases

### Proof Strategies

**What this demonstrates:** Proof strategies.

**Code:**
```ada
package Proof_Strategies is
   
   -- Helper lemma function
   function Lemma_Mult_Non_Neg (X, Y : Natural) return Boolean
     with Ghost,
          Post => Lemma_Mult_Non_Neg'Result = (X * Y >= 0);
   
   function Multiply (X, Y : Natural) return Natural
     with Post => Multiply'Result = X * Y 
                  and Multiply'Result >= 0;
   
end Proof_Strategies;

package body Proof_Strategies is
   
   function Lemma_Mult_Non_Neg (X, Y : Natural) return Boolean is
   begin
      return X * Y >= 0;
   end Lemma_Mult_Non_Neg;
   
   function Multiply (X, Y : Natural) return Natural is
      Result : Natural;
      Unused : Boolean with Ghost;
   begin
      Result := X * Y;
      Unused := Lemma_Mult_Non_Neg (X, Y);  -- Help proof
      pragma Assert (Result >= 0);
      return Result;
   end Multiply;
   
end Proof_Strategies;
```

**Explanation:**
- Lemma functions: Helper functions for proofs
- Assert: Guide proof process
- Ghost code: Can use ghost variables
- Manual proof: Sometimes necessary

**Key Takeaways:**
- Use lemma functions for complex proofs
- Assert statements guide proofs
- Ghost code helps with verification
- Sometimes manual proof needed

---

## Common Patterns

### Overview

Common SPARK patterns help with verification. Understanding patterns improves code verification.

### Common Patterns

**Bounded Search:**
```ada
function Binary_Search (A : Sorted_Array; Value : Integer) return Natural
  with 
    Post => (if Binary_Search'Result > 0 
             then A(Binary_Search'Result) = Value
             else (for all I in A'Range => A(I) /= Value));
```

**Accumulator Pattern:**
```ada
function Sum_Array (A : Integer_Array) return Integer is
   Result : Integer := 0;
begin
   for I in A'Range loop
      Result := Result + A(I);
      pragma Loop_Invariant (Result = (for all J in A'First .. I => 
                                       A(J) summed));
   end loop;
   return Result;
end Sum_Array;
```

**Key Takeaways:**
- Use common patterns for verification
- Patterns help with proofs
- Loop invariants for loops
- Postconditions for results

---

## Best Practices

### Code Organization

- **Start Simple**: Begin with simple contracts
- **Incremental**: Add contracts incrementally
- **Clear Contracts**: Write clear, precise contracts
- **Documentation**: Document proof strategies

### Verification

- **Level Selection**: Choose appropriate proof level
- **Iterative**: Iterate on proofs
- **Counterexamples**: Use counterexamples for debugging
- **Patience**: Proofs can be time-consuming

### Contracts

- **Complete**: Write complete contracts
- **Precise**: Be precise in specifications
- **Minimal**: Don't over-specify
- **Testable**: Contracts should be verifiable

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

