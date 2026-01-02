# Rust - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Variables & Data Types](#variables--data-types)
4. [Functions](#functions)
5. [Control Flow](#control-flow)
6. [Ownership](#ownership)
7. [References & Borrowing](#references--borrowing)
8. [Slices](#slices)
9. [Structs](#structs)
10. [Enums & Pattern Matching](#enums--pattern-matching)
11. [Collections](#collections)
12. [Error Handling](#error-handling)
13. [Generics](#generics)
14. [Traits](#traits)
15. [Lifetimes](#lifetimes)
16. [Closures & Iterators](#closures--iterators)
17. [Smart Pointers](#smart-pointers)
18. [Concurrency](#concurrency)
19. [Macros](#macros)
20. [Best Practices](#best-practices)
21. [Common Patterns](#common-patterns)
22. [Resources](#resources)

---

## Introduction

### What is Rust?

Rust is a systems programming language developed by Mozilla Research, first released in 2010. It was designed to provide memory safety without garbage collection, making it suitable for systems programming where performance and safety are critical. Rust combines low-level control with high-level ergonomics.

### Why Learn Rust?

Rust is valuable for:

1. **Memory Safety**: Prevents common bugs (null pointers, data races) at compile time
2. **Performance**: Zero-cost abstractions, no garbage collector overhead
3. **Concurrency**: Ownership system enables safe concurrent programming
4. **Systems Programming**: OS kernels, device drivers, embedded systems
5. **WebAssembly**: Growing ecosystem for web performance
6. **Modern Language**: Pattern matching, algebraic data types, powerful type system
7. **Growing Ecosystem**: Active community and expanding library ecosystem
8. **Career Opportunities**: Increasing demand, especially in systems and infrastructure

### Key Features

- **Ownership System**: Unique memory management model without GC
- **Zero-Cost Abstractions**: High-level features compile to efficient code
- **Type Safety**: Strong static typing prevents many classes of errors
- **Pattern Matching**: Powerful destructuring and control flow
- **Trait System**: Flexible interface-like system for polymorphism
- **Cargo**: Excellent package manager and build tool
- **No Null**: Option type prevents null pointer errors

---

## Getting Started

### Installation

**Install Rust:**
1. Visit https://rustup.rs/
2. Run installer: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
3. Or download installer for Windows

**Verify Installation:**
```bash
rustc --version
cargo --version
```

### Your First Program

**What this demonstrates:** Basic Rust program structure.

**Code:**
```rust
fn main() {
    println!("Hello, World!");
    println!("Commander says: {}", "Hello, Rust!");
}
```

**Explanation:**
- `fn main()`: Entry point (must be named `main`)
- `println!()`: Macro for printing (note the `!`)
- `{}`: Placeholder for values
- Semicolons: End statements (expressions don't need semicolons)

**To Run:**
1. Save as `main.rs`
2. Compile: `rustc main.rs`
3. Run: `./main` (Linux/macOS) or `main.exe` (Windows)

**Or use Cargo:**
```bash
cargo new my_project
cd my_project
cargo run
```

**Key Takeaways:**
- `fn main()` is entry point
- `println!` is a macro (note `!`)
- Cargo is Rust's package manager and build tool

### Cargo (Package Manager)

**What this demonstrates:** Using Cargo for projects.

**Commands:**
```bash
cargo new my_project      # Create new project
cargo build               # Build project
cargo run                 # Build and run
cargo test                # Run tests
cargo check               # Check code without building
cargo doc                 # Generate documentation
```

**Project Structure:**
```
my_project/
├── Cargo.toml           # Project configuration
├── src/
│   └── main.rs          # Main source file
└── target/              # Build output (generated)
```

**Key Takeaways:**
- Cargo: Package manager and build tool
- `cargo new` creates project structure
- `cargo run` builds and runs

---

## Variables & Data Types

### Overview

Rust is statically typed but has type inference. Variables are immutable by default, which is a key safety feature. Understanding Rust's type system is fundamental.

### Key Concepts

- **Immutability**: Variables immutable by default (`let`)
- **Mutability**: Explicitly mutable with `mut`
- **Shadowing**: Redefine variable in same scope
- **Type Inference**: Compiler infers types
- **Type Annotations**: Explicit types when needed
- **Scalar Types**: Integers, floats, booleans, characters
- **Compound Types**: Tuples, arrays

### Variables

**What this demonstrates:** Variable declarations and mutability.

**Code:**
```rust
fn variables_demo() {
    // VARIABLES (immutable by default)
    let x = 5;
    // x = 6; // ERROR: cannot assign twice to immutable variable
    
    // Mutable variables
    let mut y = 5;
    y = 6; // OK
    
    // Constants (always immutable, type must be annotated)
    const MAX_POINTS: u32 = 100_000;
    const PI: f64 = 3.14159;
    
    // Shadowing (redefine variable in same scope)
    let x = 5;
    let x = x + 1; // New variable, shadows previous
    let x = x * 2;
    println!("x = {}", x); // 12
    
    // Type annotation
    let x: i32 = 42;
    let y: f64 = 3.14;
    
    // Type inference
    let z = 42; // Rust infers i32
}
```

**Explanation:**
- `let`: Declares variable (immutable by default)
- `mut`: Makes variable mutable
- `const`: Constants (must have type annotation, compile-time constant)
- Shadowing: Create new variable with same name (different variable)
- Type annotation: `let name: Type = value;`
- Type inference: Compiler infers type from usage

**Key Takeaways:**
- Variables immutable by default
- Use `mut` for mutable variables
- Shadowing creates new variable (can change type)
- Constants require type annotation

### Scalar Types

**What this demonstrates:** Rust's scalar (primitive) types.

**Code:**
```rust
fn data_types_demo() {
    // Integers (signed and unsigned)
    let a: i8 = -128;      // -128 to 127 (8-bit signed)
    let b: i16 = 32767;    // -32,768 to 32,767 (16-bit signed)
    let c: i32 = 2147483647; // Default integer type (32-bit signed)
    let d: i64 = 9223372036854775807; // 64-bit signed
    let e: i128 = 1;       // 128-bit signed
    let f: isize = 1;      // Architecture-dependent (pointer-sized)
    
    let g: u8 = 255;       // 0 to 255 (8-bit unsigned)
    let h: u16 = 65535;    // 16-bit unsigned
    let i: u32 = 4294967295; // 32-bit unsigned
    let j: u64 = 1;        // 64-bit unsigned
    let k: u128 = 1;       // 128-bit unsigned
    let l: usize = 1;      // Architecture-dependent (pointer-sized)
    
    // Number literals
    let decimal = 98_222;  // Underscores for readability
    let hex = 0xff;        // Hexadecimal
    let octal = 0o77;      // Octal
    let binary = 0b1111_0000; // Binary
    let byte = b'A';       // Byte (u8 only)
    
    // Floating point
    let x: f32 = 2.0;      // 32-bit float
    let y: f64 = 3.14;     // Default float type (64-bit)
    
    // Boolean
    let t: bool = true;
    let f = false;         // Type inferred
    
    // Character (4 bytes, Unicode scalar value)
    let c: char = 'z';
    let z = 'ℤ';
    let heart_eyed_cat = '😻'; // Emoji (single character in Rust)
}
```

**Explanation:**
- Integers: `i8`, `i16`, `i32`, `i64`, `i128`, `isize` (signed)
- Unsigned: `u8`, `u16`, `u32`, `u64`, `u128`, `usize`
- `i32` and `f64` are defaults (when type not specified)
- `isize`/`usize`: Size depends on architecture (32-bit or 64-bit)
- Number literals: Underscores for readability (`98_222`)
- Floating point: `f32` (single precision), `f64` (double precision)
- Boolean: `true` or `false`
- Character: 4 bytes, Unicode scalar (not ASCII, can hold emoji)

**Key Takeaways:**
- Integers: Signed (`i*`) and unsigned (`u*`)
- `i32` and `f64` are default types
- `char` is 4 bytes (Unicode, not ASCII)
- Underscores in numbers improve readability

### Compound Types

**What this demonstrates:** Tuples and arrays.

**Code:**
```rust
fn compound_types_demo() {
    // Tuple (fixed size, mixed types)
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    let (x, y, z) = tup;      // Destructuring
    let five_hundred = tup.0; // Access by index
    let six_four = tup.1;     // Access by index
    let one = tup.2;
    
    // Unit type (empty tuple)
    let unit = (); // Used when no meaningful value returned
    
    // Array (fixed size, same type)
    let arr: [i32; 5] = [1, 2, 3, 4, 5];
    let first = arr[0];
    let last = arr[4];
    
    // Array with same value
    let arr = [3; 5]; // [3, 3, 3, 3, 3] (5 elements, all value 3)
}
```

**Explanation:**
- Tuple: Fixed-size, can contain different types
- Destructuring: `let (x, y, z) = tuple;`
- Index access: `tuple.0`, `tuple.1` (zero-indexed)
- Unit type: `()` (empty tuple, similar to `void`)
- Array: Fixed size, same type, stack-allocated
- Array syntax: `[type; size]` or `[value; count]`
- Arrays are fixed-size (use `Vec` for dynamic arrays)

**Key Takeaways:**
- Tuples: Fixed size, mixed types
- Arrays: Fixed size, same type, stack-allocated
- Destructuring: `let (x, y) = tuple;`
- Access: `tuple.0` or destructure

---

## Functions

### Overview

Functions are the primary way to organize code in Rust. Understanding function syntax, return values, and expressions vs statements is crucial.

### Key Concepts

- **Function Definition**: `fn name(params) -> return_type { body }`
- **Return Values**: Last expression (no semicolon) or `return` statement
- **Expressions vs Statements**: Expressions return values, statements don't
- **Function Pointers**: Functions as first-class values

### Basic Functions

**What this demonstrates:** Defining and calling functions.

**Code:**
```rust
// Basic function (no return value)
fn greet() {
    println!("Hello!");
}

// Function with parameters and return value
fn add(x: i32, y: i32) -> i32 {
    x + y // No semicolon = expression (return value)
}

// Explicit return
fn subtract(x: i32, y: i32) -> i32 {
    return x - y; // Explicit return statement
}

// Multiple return values (tuple)
fn swap(x: i32, y: i32) -> (i32, i32) {
    (y, x) // Return tuple
}

// Function with unit return type (implicit)
fn print_number(n: i32) {
    println!("Number: {}", n);
    // Implicitly returns () (unit type)
}
```

**Explanation:**
- `fn name(params) -> return_type { body }`: Function syntax
- Parameters: Type annotation required: `param: Type`
- Return type: `-> Type` (optional if unit type `()`)
- Expression (no semicolon): Last expression is return value
- Statement (semicolon): Doesn't return value
- `return`: Explicit return (usually not needed)
- Unit type: `()` when no return value

**Key Takeaways:**
- Functions: `fn name(params) -> return_type { }`
- Last expression (no `;`) is return value
- Type annotations required for parameters
- Return multiple values with tuple

### Statements vs Expressions

**What this demonstrates:** Difference between statements and expressions.

**Code:**
```rust
fn statement_vs_expression() {
    // Statement (does not return value, ends with semicolon)
    let x = 5;
    
    // Expression (returns value, no semicolon)
    let y = {
        let x = 3;
        x + 1  // No semicolon = expression (returns 4)
    };
    
    println!("y = {}", y); // 4
    
    // Block is expression
    let z = {
        let a = 10;
        let b = 20;
        a + b  // Block returns 30
    };
    
    // If expression (returns value)
    let condition = true;
    let number = if condition { 5 } else { 6 };
}
```

**Explanation:**
- Statement: Performs action, doesn't return value (ends with `;`)
- Expression: Evaluates to value (no `;`)
- Block `{ }`: Can be expression if last line has no semicolon
- `if` can be expression: `let x = if condition { value1 } else { value2 };`
- Function body: Last expression is return value

**Key Takeaways:**
- No semicolon = expression (returns value)
- Semicolon = statement (doesn't return value)
- Blocks can be expressions
- `if` can be used as expression

### Function Pointers

**What this demonstrates:** Functions as values.

**Code:**
```rust
fn apply(f: fn(i32) -> i32, value: i32) -> i32 {
    f(value)
}

fn double(x: i32) -> i32 {
    x * 2
}

fn square(x: i32) -> i32 {
    x * x
}

fn functions_demo() {
    let result1 = apply(double, 5);   // 10
    let result2 = apply(square, 5);   // 25
    
    // Function pointer type
    let func: fn(i32) -> i32 = double;
    let result = func(10); // 20
}
```

**Explanation:**
- Function pointer: `fn(param_types) -> return_type`
- Functions are first-class: Can be passed as arguments
- Function pointers: Type of function signature
- Useful for callbacks, higher-order functions

**Key Takeaways:**
- Function pointers: `fn(Type) -> Type`
- Functions can be passed as arguments
- Useful for callbacks

---

## Control Flow

### Overview

Rust provides `if/else` for conditionals, `loop`, `while`, and `for` for iteration. Understanding control flow is essential for programming.

### Key Concepts

- **If/Else**: Conditional execution
- **If Expression**: `if` can return value
- **Loop**: Infinite loop
- **While**: Conditional loop
- **For**: Iterator-based loop
- **Break/Continue**: Control loop execution

### If/Else Statements

**What this demonstrates:** Conditional execution.

**Code:**
```rust
fn control_flow_demo() {
    let number = 6;
    
    if number % 4 == 0 {
        println!("divisible by 4");
    } else if number % 3 == 0 {
        println!("divisible by 3");
    } else {
        println!("not divisible by 4 or 3");
    }
    
    // If in expression (must return same type in all branches)
    let condition = true;
    let number = if condition { 5 } else { 6 };
    // let invalid = if condition { 5 } else { "six" }; // ERROR: types must match
}
```

**Explanation:**
- `if condition { }`: Conditional execution
- `else if`: Additional conditions
- `else`: Default case
- If expression: `let x = if condition { value1 } else { value2 };`
- Branches must return same type
- No parentheses around condition (unlike C/Java)

**Key Takeaways:**
- `if/else` for conditionals
- If can be expression (returns value)
- All branches must return same type
- No parentheses around condition

### Loops

**What this demonstrates:** Different loop types.

**Code:**
```rust
fn loops_demo() {
    // Loop (infinite loop)
    let mut counter = 0;
    loop {
        counter += 1;
        if counter == 5 {
            break; // Exit loop
        }
    }
    
    // Loop with return value
    let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2; // Return value from loop
        }
    };
    
    // While loop
    let mut number = 3;
    while number != 0 {
        println!("{}!", number);
        number -= 1;
    }
    
    // For loop (iterator-based)
    let arr = [10, 20, 30, 40, 50];
    for element in arr.iter() {
        println!("value: {}", element);
    }
    
    // For with range
    for number in 1..4 {  // 1, 2, 3 (exclusive end)
        println!("{}", number);
    }
    
    for number in 1..=4 {  // 1, 2, 3, 4 (inclusive end)
        println!("{}", number);
    }
}
```

**Explanation:**
- `loop { }`: Infinite loop (must use `break`)
- `break value`: Return value from loop
- `while condition { }`: Conditional loop
- `for item in iterable { }`: Iterator-based loop
- Range: `1..4` (exclusive), `1..=4` (inclusive)
- `iter()`: Get iterator over collection

**Key Takeaways:**
- `loop` for infinite loops
- `while` for conditional loops
- `for` for iterating over collections
- `break value` returns value from loop

---

## Ownership

### Overview

Ownership is Rust's unique memory management system. It ensures memory safety without garbage collection by tracking which variable owns each value.

### Key Concepts

- **Ownership Rules**: Each value has single owner
- **Move Semantics**: Values are moved (not copied) on assignment
- **Scope**: Owner goes out of scope → value dropped
- **Stack vs Heap**: Stack for fixed-size, heap for dynamic
- **No Garbage Collection**: Ownership handles cleanup

### Ownership Rules

**What this demonstrates:** Basic ownership rules.

**Code:**
```rust
fn ownership_demo() {
    // String is heap-allocated
    let s1 = String::from("hello");
    let s2 = s1;  // s1 is MOVED to s2 (s1 no longer valid)
    // println!("{}", s1); // ERROR: value borrowed after move
    
    // Copy types (stack-allocated, implements Copy trait)
    let x = 5;
    let y = x;  // x is COPIED (both valid)
    println!("x = {}, y = {}", x, y); // OK
    
    // Ownership and functions
    let s = String::from("hello");
    takes_ownership(s);  // s moved into function
    // println!("{}", s); // ERROR: s no longer valid
    
    let x = 5;
    makes_copy(x);  // x copied (Copy type)
    println!("x = {}", x); // OK (x still valid)
}

fn takes_ownership(some_string: String) {
    println!("{}", some_string);
} // some_string goes out of scope, dropped

fn makes_copy(some_integer: i32) {
    println!("{}", some_integer);
} // some_integer goes out of scope, but Copy type (nothing special)
```

**Explanation:**
- Ownership: Each value has single owner
- Move: Assignment moves ownership (original invalid)
- Copy types: Integers, booleans, chars (stack-allocated, implement `Copy`)
- Move types: `String`, `Vec` (heap-allocated, don't implement `Copy`)
- Function call: Moves or copies based on type
- Drop: Value dropped when owner goes out of scope

**Key Takeaways:**
- Each value has single owner
- Assignment moves ownership (for non-Copy types)
- Copy types: Simple types (i32, bool, char)
- Move types: Heap-allocated (String, Vec)
- Value dropped when owner goes out of scope

### Return Values and Ownership

**What this demonstrates:** Ownership with function returns.

**Code:**
```rust
fn ownership_returns() {
    let s1 = gives_ownership();  // Moves return value to s1
    
    let s2 = String::from("hello");
    let s3 = takes_and_gives_back(s2);  // s2 moved in, return moved to s3
    
    // Multiple values with tuple
    let s1 = String::from("hello");
    let (s2, len) = calculate_length(s1);
}

fn gives_ownership() -> String {
    let some_string = String::from("yours");
    some_string  // Moves ownership to caller
}

fn takes_and_gives_back(a_string: String) -> String {
    a_string  // Moves ownership back to caller
}

fn calculate_length(s: String) -> (String, usize) {
    let length = s.len();
    (s, length)  // Return tuple (move s back)
}
```

**Explanation:**
- Return value: Moves ownership to caller
- Returning ownership: Give value back to caller
- Tuple: Return multiple values (including ownership)
- Pattern: Often take ownership, then give back

**Key Takeaways:**
- Return moves ownership
- Can return ownership to caller
- Use tuples for multiple return values

---

## References & Borrowing

### Overview

References allow you to refer to a value without taking ownership. This is called "borrowing" and is a key feature of Rust's memory safety system.

### Key Concepts

- **Immutable References**: `&T` - read-only access
- **Mutable References**: `&mut T` - can modify
- **Borrowing Rules**: 
  - At any time: either one mutable reference OR any number of immutable references
  - References must always be valid
- **No Dangling References**: Compiler prevents references to invalid memory

### Immutable References

**What this demonstrates:** Borrowing without taking ownership.

**Code:**
```rust
fn references_demo() {
    let s1 = String::from("hello");
    let len = calculate_length(&s1); // Borrow s1 (immutable reference)
    println!("Length of '{}' is {}", s1, len); // s1 still valid
}

fn calculate_length(s: &String) -> usize {
    s.len() // s is a reference, doesn't take ownership
} // s goes out of scope but doesn't drop (no ownership)
```

**Explanation:**
- `&variable`: Creates immutable reference (borrows)
- Reference type: `&String` (reference to String)
- Function receives reference: Doesn't take ownership
- Original value still valid after function call
- Reference automatically dereferenced (no `*` needed in most cases)

**Key Takeaways:**
- `&` creates immutable reference
- References don't take ownership
- Original value remains valid

### Mutable References

**What this demonstrates:** Borrowing with ability to modify.

**Code:**
```rust
fn mutable_references() {
    let mut s = String::from("hello");
    change(&mut s); // Mutable reference
    println!("{}", s); // "hello, world"
}

fn change(s: &mut String) {
    s.push_str(", world");
}
```

**Explanation:**
- `&mut variable`: Creates mutable reference
- Variable must be `mut` to create mutable reference
- Can modify through mutable reference
- Only one mutable reference at a time

**Key Takeaways:**
- `&mut` creates mutable reference
- Variable must be `mut`
- Can modify through reference

### Borrowing Rules

**What this demonstrates:** Rust's borrowing rules prevent data races.

**Code:**
```rust
fn borrowing_rules() {
    let mut s = String::from("hello");
    
    // Multiple immutable references - OK
    let r1 = &s;
    let r2 = &s;
    println!("{}, {}", r1, r2);
    
    // Cannot create mutable reference while immutable refs exist
    // let r3 = &mut s; // ERROR: cannot borrow as mutable
    
    // After immutable refs no longer used, can create mutable ref
    let r3 = &mut s; // OK now
    r3.push_str(" world");
}
```

**Explanation:**
- Rule 1: At any time, you can have EITHER:
  - One mutable reference, OR
  - Any number of immutable references
- Rule 2: References must always be valid (prevents dangling references)
- These rules prevent data races at compile time
- Scope matters: references only conflict if they overlap in scope

**Key Takeaways:**
- Either one mutable OR multiple immutable (not both)
- Prevents data races at compile time
- Scope determines when references conflict

---

## Slices

### Overview

Slices let you reference a contiguous sequence of elements in a collection rather than the whole collection. They are references and don't have ownership.

### Key Concepts

- **String Slices**: `&str` - reference to part of string
- **Array Slices**: `&[T]` - reference to part of array
- **Range Syntax**: `[start..end]` (end exclusive)
- **No Ownership**: Slices are references
- **UTF-8 Safe**: String slices respect UTF-8 boundaries

### String Slices

**What this demonstrates:** Working with string slices.

**Code:**
```rust
fn slices_demo() {
    let s = String::from("hello world");
    
    // String slice
    let hello = &s[0..5];   // "hello" (indices 0 to 4)
    let world = &s[6..11];  // "world" (indices 6 to 10)
    
    // Shortcuts
    let hello = &s[..5];    // Same as [0..5]
    let world = &s[6..];    // From 6 to end
    let whole = &s[..];     // Entire string
    
    // String literals are slices
    let s: &str = "Hello, world!"; // &str type (string slice)
}
```

**Explanation:**
- `&string[start..end]`: Creates slice from start to end-1
- `[start..]`: From start to end of string
- `[..end]`: From beginning to end-1
- `[..]`: Entire string
- String literals: Type is `&str` (immutable string slice)
- Slices store reference to start position and length

**Key Takeaways:**
- `[start..end]` creates slice (end exclusive)
- `[..]`, `[start..]`, `[..end]` shortcuts
- String literals are `&str` (string slice)

### Array Slices

**What this demonstrates:** Working with array slices.

**Code:**
```rust
fn array_slices() {
    let arr = [1, 2, 3, 4, 5];
    let slice = &arr[1..3]; // [2, 3] (slice of array)
    
    // Function accepting slice
    let result = sum_slice(&arr[1..4]);
}

fn sum_slice(slice: &[i32]) -> i32 {
    slice.iter().sum()
}
```

**Explanation:**
- `&array[start..end]`: Creates slice of array
- Slice type: `&[T]` (not `&[T; N]`)
- Works with any size array/vector
- Functions often take slices for flexibility

**Key Takeaways:**
- `&[T]` is slice type (works with any size)
- More flexible than fixed-size arrays
- Functions should prefer slices over arrays

### String vs String Slice

**What this demonstrates:** Difference between `String` and `&str`.

**Code:**
```rust
fn string_types() {
    // String (owned, heap-allocated, growable)
    let mut s = String::from("hello");
    s.push_str(" world");
    
    // &str (string slice, reference, immutable)
    let literal: &str = "hello world";
    let slice = &s[0..5]; // &str from String
    
    // Function accepting string slice (more flexible)
    fn print_string(s: &str) {
        println!("{}", s);
    }
    
    print_string("literal");        // Works
    print_string(&s);               // Works (String derefs to &str)
    print_string(&s[0..5]);         // Works
}
```

**Explanation:**
- `String`: Owned, growable, heap-allocated
- `&str`: String slice, reference, immutable
- Functions should prefer `&str` parameter (more flexible)
- `String` automatically dereferences to `&str`

**Key Takeaways:**
- `String`: owned, mutable
- `&str`: slice, reference, immutable
- Prefer `&str` in function parameters

---

## Structs

### Overview

Structs are custom data types that let you name and package together multiple related values. They're similar to classes in other languages but don't have methods by default (methods are added via `impl` blocks).

### Key Concepts

- **Struct Definition**: Define structure with named fields
- **Tuple Structs**: Structs with unnamed fields
- **Unit Structs**: Structs with no fields
- **Methods**: Functions associated with struct (`impl` block)
- **Associated Functions**: Functions without `self` (like static methods)

### Struct Definition

**What this demonstrates:** Creating and using structs.

**Code:**
```rust
// Define struct
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}

fn structs_demo() {
    // Create instance
    let mut user1 = User {
        email: String::from("someone@example.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count: 1,
    };
    
    // Access fields
    user1.email = String::from("another@example.com");
    
    // Field init shorthand (when field name = variable name)
    let email = String::from("user@example.com");
    let username = String::from("user123");
    let user2 = User {
        email,    // Same as email: email
        username, // Same as username: username
        active: true,
        sign_in_count: 1,
    };
    
    // Struct update syntax (copy remaining fields)
    let user3 = User {
        email: String::from("new@example.com"),
        ..user2  // Copy remaining fields from user2
    };
}
```

**Explanation:**
- `struct Name { field: Type }`: Define struct
- Create instance: `StructName { field: value, ... }`
- Access: `instance.field`
- Field init shorthand: `field` when variable name matches
- Struct update: `..other_instance` copies remaining fields
- Update syntax moves/copies fields (depending on types)

**Key Takeaways:**
- `struct` defines custom type
- Field init shorthand: `field` = `field: field`
- `..instance` copies remaining fields

### Tuple Structs

**What this demonstrates:** Structs with unnamed fields.

**Code:**
```rust
// Tuple struct (fields accessed by index)
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);

fn tuple_structs() {
    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
    
    // Access by index
    println!("Color: {}, {}, {}", black.0, black.1, black.2);
    
    // Different types even with same fields
    // let p: Point = black; // ERROR: different types
}
```

**Explanation:**
- `struct Name(Type1, Type2, ...)`: Tuple struct
- Fields accessed by index: `.0`, `.1`, etc.
- Different types even with same field types
- Useful when you want named types but tuple-like access

**Key Takeaways:**
- Tuple structs: unnamed fields, accessed by index
- Each tuple struct is distinct type
- Use when you want named type but tuple access

### Methods

**What this demonstrates:** Adding methods to structs.

**Code:**
```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    // Method (takes &self)
    fn area(&self) -> u32 {
        self.width * self.height
    }
    
    // Method with parameters
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
    
    // Associated function (no self, like static method)
    fn square(size: u32) -> Rectangle {
        Rectangle {
            width: size,
            height: size,
        }
    }
}

fn methods_demo() {
    let rect1 = Rectangle { width: 30, height: 50 };
    let rect2 = Rectangle { width: 10, height: 40 };
    
    // Call method
    println!("Area: {}", rect1.area());
    println!("Can hold: {}", rect1.can_hold(&rect2));
    
    // Call associated function
    let square = Rectangle::square(20);
}
```

**Explanation:**
- `impl StructName { }`: Implementation block
- Methods: Functions with `&self` (or `&mut self`, `self`)
- `&self`: Immutable reference to instance
- `&mut self`: Mutable reference to instance
- `self`: Takes ownership (rare)
- Associated functions: No `self`, called with `::`
- Multiple `impl` blocks allowed

**Key Takeaways:**
- `impl` block adds methods
- Methods: `&self`, `&mut self`, or `self`
- Associated functions: no `self`, called with `::`

---

## Enums & Pattern Matching

### Overview

Enums allow you to define a type by enumerating its possible variants. Pattern matching with `match` provides exhaustive checking. Rust's `Option` and `Result` types are powerful enums that eliminate null pointer errors.

### Key Concepts

- **Enum Definition**: Define enum with variants
- **Enum with Data**: Variants can hold data
- **Pattern Matching**: `match` for exhaustive pattern matching
- **Option**: `Some(T)` or `None` (no null)
- **Result**: `Ok(T)` or `Err(E)` (error handling)
- **if let**: Shorthand for single pattern match

### Enums

**What this demonstrates:** Defining and using enums.

**Code:**
```rust
// Basic enum
enum IpAddrKind {
    V4,
    V6,
}

// Enum with data
enum IpAddr {
    V4(u8, u8, u8, u8),        // Tuple variant
    V6(String),                // Single value variant
}

// Enum with different types
enum Message {
    Quit,                      // No data
    Move { x: i32, y: i32 },   // Named fields
    Write(String),             // Single value
    ChangeColor(i32, i32, i32), // Tuple
}

fn enums_demo() {
    let four = IpAddrKind::V4;
    let six = IpAddrKind::V6;
    
    let home = IpAddr::V4(127, 0, 0, 1);
    let loopback = IpAddr::V6(String::from("::1"));
}
```

**Explanation:**
- `enum Name { Variant1, Variant2 }`: Define enum
- Variants can have no data, tuple data, or named fields
- Each variant is a distinct type
- Use `::` to access variants: `Enum::Variant`
- Enums can hold different types in different variants

**Key Takeaways:**
- Enums: Multiple variants, each can have different data
- Access with `Enum::Variant`
- Variants can have no data, tuple data, or named fields

### Option Enum

**What this demonstrates:** Rust's `Option` type (no null).

**Code:**
```rust
// Option<T> is built-in (no need to define)
// enum Option<T> {
//     Some(T),
//     None,
// }

fn option_demo() {
    let some_number = Some(5);        // Option<i32>
    let some_string = Some("a string"); // Option<&str>
    let absent_number: Option<i32> = None; // Must specify type for None
    
    // Match on Option
    match some_number {
        Some(value) => println!("Got value: {}", value),
        None => println!("No value"),
    }
}
```

**Explanation:**
- `Option<T>`: Built-in enum, no null needed
- `Some(T)`: Contains value
- `None`: No value (must specify type)
- Forces you to handle the "no value" case
- Eliminates null pointer errors

**Key Takeaways:**
- `Option<T>`: `Some(T)` or `None`
- No null in Rust
- Must handle both cases

### Pattern Matching with match

**What this demonstrates:** Exhaustive pattern matching.

**Code:**
```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

#[derive(Debug)]
enum UsState {
    Alabama,
    Alaska,
}

fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("Quarter from {:?}", state);
            25
        }
    }
}

fn match_demo() {
    let coin = Coin::Penny;
    println!("Value: {}", value_in_cents(coin));
    
    // Match with Option
    let five = Some(5);
    let six = plus_one(five);      // Some(6)
    let none = plus_one(None);     // None
    
    // Match with catch-all
    let dice_roll = 9;
    match dice_roll {
        3 => add_fancy_hat(),
        7 => remove_fancy_hat(),
        other => move_player(other), // Catch-all with value
    }
    
    // Match with _ (ignore value)
    match dice_roll {
        3 => add_fancy_hat(),
        7 => remove_fancy_hat(),
        _ => (), // Do nothing for other values
    }
}

fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i) => Some(i + 1),
    }
}

fn add_fancy_hat() {}
fn remove_fancy_hat() {}
fn move_player(num: u8) {}
```

**Explanation:**
- `match value { pattern => expression, ... }`: Pattern matching
- Exhaustive: Must cover all possibilities
- Patterns: Variants, values, catch-all (`_` or variable)
- Can bind values: `Variant(value) => use value`
- Each arm returns same type
- `_`: Ignore pattern (catch-all)

**Key Takeaways:**
- `match` is exhaustive (must cover all cases)
- Patterns can bind values
- `_` for catch-all (ignore value)
- Each arm must return same type

### if let

**What this demonstrates:** Shorthand for single pattern match.

**Code:**
```rust
fn if_let_demo() {
    let config_max = Some(3u8);
    
    // Match (verbose)
    match config_max {
        Some(max) => println!("Max: {}", max),
        _ => (),
    }
    
    // if let (shorthand)
    if let Some(max) = config_max {
        println!("Max: {}", max);
    }
    
    // if let with else
    let mut count = 0;
    let coin = Coin::Quarter(UsState::Alaska);
    if let Coin::Quarter(state) = coin {
        println!("Quarter from {:?}", state);
    } else {
        count += 1;
    }
}
```

**Explanation:**
- `if let pattern = value { }`: Shorthand for match with one pattern
- More concise when you only care about one case
- Can have `else` clause
- Less exhaustive than `match`

**Key Takeaways:**
- `if let` for single pattern match
- More concise than `match` for one case
- Can have `else`

---

## Collections

### Overview

Rust's standard library includes several useful collection types. The most common are `Vec` (vector/dynamic array), `String`, and `HashMap`.

### Key Concepts

- **Vec**: Dynamic array, heap-allocated
- **String**: Growable UTF-8 string
- **HashMap**: Key-value mapping
- **Ownership**: Collections own their data
- **Iteration**: Iterate over collections safely

### Vectors (Vec)

**What this demonstrates:** Working with vectors.

**Code:**
```rust
use std::collections::HashMap;

fn vectors_demo() {
    // Create vector
    let mut v: Vec<i32> = Vec::new();
    v.push(1);
    v.push(2);
    v.push(3);
    
    // vec! macro (convenient)
    let v = vec![1, 2, 3];
    
    // Accessing elements
    let third = &v[2];        // Panic if out of bounds
    let third = v.get(2);     // Returns Option<&i32>
    
    match v.get(2) {
        Some(third) => println!("Third: {}", third),
        None => println!("No third element"),
    }
    
    // Iterating
    for i in &v {
        println!("{}", i);
    }
    
    // Mutating while iterating
    let mut v = vec![100, 32, 57];
    for i in &mut v {
        *i += 50; // Dereference to modify
    }
    
    // Vectors with enums (store different types)
    enum SpreadsheetCell {
        Int(i32),
        Float(f64),
        Text(String),
    }
    
    let row = vec![
        SpreadsheetCell::Int(3),
        SpreadsheetCell::Text(String::from("blue")),
        SpreadsheetCell::Float(10.12),
    ];
}
```

**Explanation:**
- `Vec<T>`: Dynamic array, heap-allocated
- `Vec::new()`: Create empty vector
- `vec![...]`: Macro to create vector with values
- `push()`: Add element
- `&v[index]`: Access (panics if out of bounds)
- `v.get(index)`: Safe access (returns `Option`)
- Iterate: `for item in &v`
- Mutate: `for item in &mut v` (need `*` to dereference)

**Key Takeaways:**
- `Vec<T>`: dynamic array
- `&v[i]` panics, `v.get(i)` returns `Option`
- Use enums to store different types in vector

### Strings

**What this demonstrates:** Working with strings.

**Code:**
```rust
fn strings_demo() {
    // Create String
    let mut s = String::new();
    let s = "initial contents".to_string();
    let s = String::from("initial contents");
    
    // Appending
    let mut s = String::from("foo");
    s.push_str("bar");    // "foobar" (appends string slice)
    s.push('!');          // "foobar!" (appends single char)
    
    // Concatenation
    let s1 = String::from("Hello, ");
    let s2 = String::from("world!");
    let s3 = s1 + &s2;    // s1 moved, s2 borrowed
    
    // format! macro (doesn't take ownership)
    let s1 = String::from("tic");
    let s2 = String::from("tac");
    let s3 = String::from("toe");
    let s = format!("{}-{}-{}", s1, s2, s3); // All still valid
    
    // Iterating (UTF-8 aware)
    for c in "नमस्ते".chars() {
        println!("{}", c);
    }
    
    for b in "नमस्ते".bytes() {
        println!("{}", b);
    }
}
```

**Explanation:**
- `String`: Growable, owned, UTF-8 encoded
- `&str`: String slice, reference
- `push_str()`: Append string slice
- `push()`: Append single character
- `+` operator: Moves left operand, borrows right
- `format!`: Creates string without taking ownership
- Iteration: `.chars()` for characters, `.bytes()` for bytes
- UTF-8: Strings are UTF-8, indexing by bytes is unsafe

**Key Takeaways:**
- `String`: owned, growable
- `&str`: slice, reference
- `format!` doesn't take ownership
- Strings are UTF-8, iterate with `.chars()`

### Hash Maps

**What this demonstrates:** Working with hash maps.

**Code:**
```rust
use std::collections::HashMap;

fn hashmap_demo() {
    // Create hash map
    let mut scores = HashMap::new();
    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);
    
    // Accessing values
    let team_name = String::from("Blue");
    let score = scores.get(&team_name); // Returns Option<&i32>
    
    // Iterating
    for (key, value) in &scores {
        println!("{}: {}", key, value);
    }
    
    // Updating
    scores.insert(String::from("Blue"), 25); // Overwrites
    
    // Only insert if key doesn't exist
    scores.entry(String::from("Blue")).or_insert(50);
    
    // Update based on old value
    let text = "hello world wonderful world";
    let mut map = HashMap::new();
    for word in text.split_whitespace() {
        let count = map.entry(word).or_insert(0);
        *count += 1;
    }
}
```

**Explanation:**
- `HashMap<K, V>`: Key-value mapping
- `insert()`: Insert or overwrite
- `get()`: Returns `Option<&V>`
- `entry()`: Returns `Entry` enum for complex operations
- `.or_insert()`: Insert if key doesn't exist
- Keys must implement `Eq` and `Hash`
- Ownership: Inserting owned values moves them

**Key Takeaways:**
- `HashMap<K, V>`: key-value mapping
- `get()` returns `Option`
- `entry().or_insert()` for conditional insert
- Inserting owned values moves them

---

## Error Handling

### Overview

Rust groups errors into two categories: recoverable (`Result<T, E>`) and unrecoverable (`panic!`). Rust doesn't have exceptions - errors are explicit and must be handled.

### Key Concepts

- **panic!**: Unrecoverable errors (program stops)
- **Result<T, E>**: Recoverable errors (`Ok(T)` or `Err(E)`)
- **match**: Handle Result variants
- **unwrap()**: Panic on error (quick prototyping)
- **expect()**: Panic with custom message
- **? operator**: Propagate errors (shorthand)

### Panic

**What this demonstrates:** Unrecoverable errors.

**Code:**
```rust
fn panic_demo() {
    // Explicit panic
    // panic!("crash and burn");
    
    // Panic on out of bounds
    // let v = vec![1, 2, 3];
    // v[99]; // panic!
}
```

**Explanation:**
- `panic!`: Unrecoverable error, program stops
- Backtrace: Shows call stack (set `RUST_BACKTRACE=1`)
- Use for programming errors (bugs)
- Recoverable errors should use `Result`

**Key Takeaways:**
- `panic!` for unrecoverable errors
- Use `Result` for recoverable errors
- Set `RUST_BACKTRACE=1` for backtraces

### Result Type

**What this demonstrates:** Handling recoverable errors.

**Code:**
```rust
use std::fs::File;
use std::io::ErrorKind;

fn result_demo() {
    let f = File::open("hello.txt");
    
    // Match on Result
    let f = match f {
        Ok(file) => file,
        Err(error) => match error.kind() {
            ErrorKind::NotFound => match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => panic!("Problem creating file: {:?}", e),
            },
            other_error => {
                panic!("Problem opening file: {:?}", other_error)
            }
        },
    };
    
    // unwrap (panic on error)
    let f = File::open("hello.txt").unwrap();
    
    // expect (panic with custom message)
    let f = File::open("hello.txt")
        .expect("Failed to open hello.txt");
}
```

**Explanation:**
- `Result<T, E>`: `Ok(T)` or `Err(E)`
- `match`: Handle both variants
- `unwrap()`: Returns value or panics
- `expect()`: Like `unwrap()` but with custom message
- Nested matches: Can get verbose (use `?` operator instead)

**Key Takeaways:**
- `Result<T, E>`: `Ok(T)` or `Err(E)`
- `match` to handle both cases
- `unwrap()`/`expect()` for quick prototyping

### Propagating Errors

**What this demonstrates:** Returning errors to caller.

**Code:**
```rust
use std::fs::File;
use std::io::{self, Read};

// Manual propagation with match
fn read_username_from_file() -> Result<String, io::Error> {
    let f = File::open("hello.txt");
    
    let mut f = match f {
        Ok(file) => file,
        Err(e) => return Err(e),
    };
    
    let mut s = String::new();
    match f.read_to_string(&mut s) {
        Ok(_) => Ok(s),
        Err(e) => Err(e),
    }
}

// ? operator (shorthand)
fn read_username_short() -> Result<String, io::Error> {
    let mut f = File::open("hello.txt")?;
    let mut s = String::new();
    f.read_to_string(&mut s)?;
    Ok(s)
}

// Even shorter
fn read_username_shorter() -> Result<String, io::Error> {
    let mut s = String::new();
    File::open("hello.txt")?.read_to_string(&mut s)?;
    Ok(s)
}
```

**Explanation:**
- `?` operator: Shortcut for error propagation
- If `Ok`, unwraps value
- If `Err`, returns error early
- Can only be used in functions returning `Result`
- Much cleaner than nested matches

**Key Takeaways:**
- `?` operator propagates errors
- Much cleaner than nested matches
- Only works in functions returning `Result`

---

## Generics

### Overview

Generics allow you to write code that works with multiple types without duplicating code. Rust's generics are zero-cost abstractions - they have no runtime overhead.

### Key Concepts

- **Generic Functions**: Functions that work with multiple types
- **Generic Structs**: Structs with type parameters
- **Generic Enums**: Enums with type parameters (like `Option<T>`, `Result<T, E>`)
- **Trait Bounds**: Constrain generic types to types that implement specific traits
- **Performance**: Generics are compiled away (monomorphization)

### Generic Functions

**What this demonstrates:** Functions that work with multiple types.

**Code:**
```rust
// Generic function with trait bound
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];
    
    for item in list {
        if item > largest {
            largest = item;
        }
    }
    
    largest
}

fn generics_demo() {
    let number_list = vec![34, 50, 25, 100, 65];
    let result = largest(&number_list);
    println!("Largest: {}", result);
    
    let char_list = vec!['y', 'm', 'a', 'q'];
    let result = largest(&char_list);
    println!("Largest: {}", result);
}
```

**Explanation:**
- `fn name<T>(params)` or `fn name<T: Trait>(params)`: Generic function
- Type parameter: `T` (convention, can be any name)
- Trait bound: `T: PartialOrd` means T must implement PartialOrd
- Works with any type that satisfies the trait bounds
- Compiler generates specialized versions (monomorphization)

**Key Takeaways:**
- `fn name<T>(params)`: Generic function
- Trait bounds: `T: Trait` constrain generic types
- Zero-cost: Compiled away, no runtime overhead

### Generic Structs

**What this demonstrates:** Structs with type parameters.

**Code:**
```rust
// Generic struct
struct Point<T> {
    x: T,
    y: T,
}

// Multiple type parameters
struct Point2<T, U> {
    x: T,
    y: U,
}

fn structs_demo() {
    let integer = Point { x: 5, y: 10 };
    let float = Point { x: 1.0, y: 4.0 };
    let mixed = Point2 { x: 5, y: 4.0 };
}
```

**Explanation:**
- `struct Name<T> { }`: Generic struct
- All fields can use same type parameter or different ones
- `Point2<T, U>`: Multiple type parameters
- Instance specifies concrete types
- Each generic combination is different type

**Key Takeaways:**
- `struct Name<T> { }`: Generic struct
- Multiple type parameters: `<T, U>`
- Each combination is distinct type

### Generic Methods

**What this demonstrates:** Methods on generic structs.

**Code:**
```rust
struct Point<T> {
    x: T,
    y: T,
}

impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}

// Method for specific type
impl Point<f32> {
    fn distance_from_origin(&self) -> f32 {
        (self.x.powi(2) + self.y.powi(2)).sqrt()
    }
}

fn methods_demo() {
    let p = Point { x: 5, y: 10 };
    println!("x = {}", p.x());
    
    let p_f32 = Point { x: 3.0, y: 4.0 };
    println!("Distance: {}", p_f32.distance_from_origin());
}
```

**Explanation:**
- `impl<T> Struct<T>`: Generic implementation
- Can implement methods for all types or specific types
- `impl Point<f32>`: Implementation only for `Point<f32>`
- Specific implementations can add methods not available to generic

**Key Takeaways:**
- `impl<T> Struct<T>`: Generic implementation
- Can implement for specific types: `impl Struct<ConcreteType>`
- Specific implementations can have additional methods

---

## Traits

### Overview

Traits define shared behavior. They're similar to interfaces in other languages but more powerful. Traits enable polymorphism and code reuse.

### Key Concepts

- **Trait Definition**: Define shared interface
- **Trait Implementation**: Implement trait for types (`impl Trait for Type`)
- **Default Methods**: Traits can provide default implementations
- **Trait Bounds**: Constrain generics to types implementing trait
- **Trait Objects**: Runtime polymorphism (`dyn Trait`)

### Defining and Implementing Traits

**What this demonstrates:** Creating and implementing traits.

**Code:**
```rust
// Define trait
trait Summary {
    fn summarize(&self) -> String;
    
    // Default implementation
    fn summarize_author(&self) -> String {
        String::from("(Read more...)")
    }
}

struct NewsArticle {
    headline: String,
    location: String,
    author: String,
    content: String,
}

// Implement trait
impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}

struct Tweet {
    username: String,
    content: String,
    reply: bool,
    retweet: bool,
}

impl Summary for Tweet {
    fn summarize(&self) -> String {
        format!("{}: {}", self.username, self.content)
    }
    
    // Can override default implementation
    fn summarize_author(&self) -> String {
        format!("@{}", self.username)
    }
}

fn traits_demo() {
    let article = NewsArticle {
        headline: String::from("Penguins win!"),
        location: String::from("Pittsburgh, PA, USA"),
        author: String::from("Iceburgh"),
        content: String::from("The Pittsburgh Penguins won!"),
    };
    
    println!("New article: {}", article.summarize());
    println!("Author: {}", article.summarize_author()); // Uses default
    
    let tweet = Tweet {
        username: String::from("horse_ebooks"),
        content: String::from("of course"),
        reply: false,
        retweet: false,
    };
    
    println!("New tweet: {}", tweet.summarize());
    println!("Author: {}", tweet.summarize_author()); // Uses override
}
```

**Explanation:**
- `trait Name { }`: Define trait with methods
- `impl Trait for Type { }`: Implement trait for type
- Default methods: Provide default implementation
- Can override defaults: Implement in `impl` block
- Multiple traits: Type can implement multiple traits
- Orphan rule: Can't implement external trait for external type

**Key Takeaways:**
- `trait` defines shared behavior
- `impl Trait for Type` implements trait
- Default methods can be overridden
- Types can implement multiple traits

### Traits as Parameters

**What this demonstrates:** Using traits to constrain function parameters.

**Code:**
```rust
// Trait as parameter (impl Trait syntax)
fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}

// Trait bound syntax (equivalent)
fn notify2<T: Summary>(item: &T) {
    println!("Breaking news! {}", item.summarize());
}

// Multiple trait bounds
fn notify3<T: Summary + std::fmt::Display>(item: &T) {
    println!("{}", item.summarize());
}

// Where clause (cleaner for complex bounds)
fn some_function<T, U>(t: &T, u: &U) -> i32
where
    T: std::fmt::Display + Clone,
    U: Clone + std::fmt::Debug,
{
    42
}

fn parameters_demo() {
    let article = NewsArticle { /* ... */ };
    notify(&article);
    notify2(&article);
}
```

**Explanation:**
- `&impl Trait`: Trait as parameter (impl Trait syntax)
- `T: Trait`: Trait bound (equivalent, more explicit)
- Multiple bounds: `T: Trait1 + Trait2`
- `where` clause: Cleaner for complex bounds
- Both syntaxes are equivalent

**Key Takeaways:**
- `&impl Trait` or `T: Trait` for trait parameters
- Multiple bounds: `T: Trait1 + Trait2`
- `where` clause for complex bounds

### Returning Types That Implement Traits

**What this demonstrates:** Functions that return trait implementors.

**Code:**
```rust
// Return type implementing trait
fn returns_summarizable() -> impl Summary {
    Tweet {
        username: String::from("horse_ebooks"),
        content: String::from("of course"),
        reply: false,
        retweet: false,
    }
}

// Useful for closures and iterators
fn returns_closure() -> impl Fn(i32) -> i32 {
    |x| x + 1
}
```

**Explanation:**
- `-> impl Trait`: Return type implementing trait
- Returns concrete type (not trait object)
- Useful for closures and iterators
- Can only return single concrete type (not conditionally different types)

**Key Takeaways:**
- `-> impl Trait` for return types
- Returns concrete type, not trait object
- Single concrete type only

### Common Traits

**What this demonstrates:** Useful built-in traits.

**Code:**
```rust
// Derive common traits
#[derive(Debug, Clone, Copy, PartialEq, Eq, PartialOrd, Ord, Hash)]
struct Person {
    name: String,
    age: u32,
}

fn common_traits() {
    let p1 = Person { name: String::from("Alice"), age: 30 };
    let p2 = p1.clone(); // Clone trait
    println!("{:?}", p1); // Debug trait
    
    if p1 == p2 { // PartialEq trait
        println!("Equal");
    }
}
```

**Explanation:**
- `#[derive(...)]`: Automatically implement traits
- Common traits: `Debug`, `Clone`, `Copy`, `PartialEq`, `Eq`, `PartialOrd`, `Ord`, `Hash`
- `Debug`: For `{:?}` formatting
- `Clone`: Deep copy
- `Copy`: Shallow copy (stack-only types)
- `PartialEq`/`Eq`: Equality comparison
- `PartialOrd`/`Ord`: Ordering comparison

**Key Takeaways:**
- `#[derive(Trait)]` auto-implements traits
- Common: `Debug`, `Clone`, `Copy`, `PartialEq`, `Eq`
- Use `derive` when possible

---

## Lifetimes

### Overview

Lifetimes ensure that references are valid for as long as we need them. The compiler uses lifetime annotations to ensure memory safety without runtime cost.

### Key Concepts

- **Lifetime Annotations**: `'a`, `'b`, etc. - name lifetime parameters
- **Lifetime Elision**: Compiler infers lifetimes in common cases
- **Lifetime Rules**: Three rules for elision
- **Static Lifetime**: `'static` - lives for entire program duration
- **Struct Lifetimes**: Structs can hold references with lifetimes

### Lifetime Annotations

**What this demonstrates:** Explicit lifetime annotations.

**Code:**
```rust
// Lifetime annotation
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

fn lifetime_demo() {
    let string1 = String::from("long string is long");
    {
        let string2 = String::from("xyz");
        let result = longest(string1.as_str(), string2.as_str());
        println!("Longest: {}", result);
    }
    // result no longer valid here (string2 dropped)
}
```

**Explanation:**
- `'a`: Lifetime annotation (single quote, lowercase, usually short names)
- `&'a str`: Reference with lifetime `'a`
- `<'a>`: Declares lifetime parameter
- Lifetime: How long reference is valid
- Compiler ensures returned reference is valid

**Key Takeaways:**
- `'a` syntax for lifetime annotations
- `&'a T`: Reference with lifetime `'a`
- Compiler ensures references are valid

### Structs with Lifetimes

**What this demonstrates:** Structs holding references.

**Code:**
```rust
// Struct with lifetime
struct ImportantExcerpt<'a> {
    part: &'a str,
}

impl<'a> ImportantExcerpt<'a> {
    fn level(&self) -> i32 {
        3
    }
    
    fn announce_and_return_part(&self, announcement: &str) -> &str {
        println!("Attention: {}", announcement);
        self.part // Returns reference with struct's lifetime
    }
}

fn struct_lifetimes() {
    let novel = String::from("Call me Ishmael. Some years ago...");
    let first_sentence = novel.split('.').next().expect("No '.'");
    let i = ImportantExcerpt {
        part: first_sentence,
    };
}
```

**Explanation:**
- `struct Name<'a> { field: &'a T }`: Struct with lifetime
- Lifetime on struct: All references in struct must live at least as long
- `impl<'a> Struct<'a>`: Implementation needs lifetime parameter
- Methods can return references with struct's lifetime

**Key Takeaways:**
- Structs with references need lifetime parameters
- `impl<'a> Struct<'a>` for implementations
- Lifetime ensures struct doesn't outlive its data

### Static Lifetime

**What this demonstrates:** The `'static` lifetime.

**Code:**
```rust
// Static lifetime (entire program duration)
fn static_lifetime() {
    let s: &'static str = "I have a static lifetime";
    // String literals have 'static lifetime
}
```

**Explanation:**
- `'static`: Lifetime for entire program duration
- String literals: Stored in binary, have `'static` lifetime
- Rarely needed: Most lifetimes are inferred
- Don't use `'static` unless necessary

**Key Takeaways:**
- `'static`: Entire program lifetime
- String literals have `'static` lifetime
- Use only when necessary

### Lifetime Elision Rules

**What this demonstrates:** Compiler's lifetime inference rules.

**Explanation:**
1. Each reference parameter gets its own lifetime parameter
2. If exactly one input lifetime, it's assigned to all output lifetimes
3. If `&self` or `&mut self`, lifetime of `self` is assigned to all output lifetimes

**Key Takeaways:**
- Compiler infers lifetimes in common cases
- Three rules cover most situations
- Only need explicit annotations when compiler can't infer

---

## Closures & Iterators

### Overview

Closures are anonymous functions that can capture their environment. Iterators process sequences of items. Both are zero-cost abstractions.

### Key Concepts

- **Closures**: Anonymous functions that capture environment
- **Fn Traits**: `Fn`, `FnMut`, `FnOnce` - how closure captures
- **Iterators**: Process sequences lazily
- **Iterator Methods**: `map`, `filter`, `collect`, etc.
- **Zero-Cost**: No runtime overhead

### Closures

**What this demonstrates:** Creating and using closures.

**Code:**
```rust
fn closures_demo() {
    // Closure syntax (type annotations optional)
    let add_one = |x| x + 1;
    println!("5 + 1 = {}", add_one(5));
    
    // With type annotations
    let add_one = |x: i32| -> i32 { x + 1 };
    
    // Capturing environment
    let x = 4;
    let equal_to_x = |z| z == x; // Captures x immutably
    let y = 4;
    assert!(equal_to_x(y));
    
    // Move ownership into closure
    let x = vec![1, 2, 3];
    let equal_to_x = move |z| z == x; // x moved into closure
    // println!("{:?}", x); // ERROR: x moved
    
    // Storing closures
    let expensive_closure = |num| {
        println!("Calculating...");
        num
    };
    
    expensive_closure(5);
}
```

**Explanation:**
- `|params| body`: Closure syntax
- Type annotations optional (inferred from usage)
- Can capture variables from environment
- `move`: Moves ownership into closure
- Three Fn traits: `Fn` (immutable borrow), `FnMut` (mutable borrow), `FnOnce` (takes ownership)

**Key Takeaways:**
- `|params| body`: Closure syntax
- Captures environment
- `move` keyword moves ownership
- Three Fn traits: `Fn`, `FnMut`, `FnOnce`

### Iterators

**What this demonstrates:** Working with iterators.

**Code:**
```rust
fn iterators_demo() {
    let v1 = vec![1, 2, 3];
    
    // Iterator (lazy, doesn't do anything until consumed)
    let v1_iter = v1.iter();
    
    // Consume iterator (for loop)
    for val in v1_iter {
        println!("Got: {}", val);
    }
    
    // Iterator methods
    let v1: Vec<i32> = vec![1, 2, 3];
    
    // map and collect
    let v2: Vec<_> = v1.iter().map(|x| x + 1).collect();
    println!("{:?}", v2); // [2, 3, 4]
    
    // filter
    let v3: Vec<_> = v1.iter().filter(|x| *x > 1).collect();
    println!("{:?}", v3); // [2, 3]
    
    // Chaining
    let sum: i32 = v1
        .iter()
        .filter(|x| *x > 1)
        .map(|x| x * 2)
        .sum();
    println!("Sum: {}", sum); // 10
    
    // Different iterator types
    let v = vec![1, 2, 3];
    v.iter();      // Iterator over &T
    v.iter_mut();  // Iterator over &mut T
    v.into_iter(); // Iterator over T (takes ownership)
}
```

**Explanation:**
- Iterators: Lazy (don't do work until consumed)
- `iter()`: Iterator over references
- `iter_mut()`: Iterator over mutable references
- `into_iter()`: Iterator that takes ownership
- Methods: `map`, `filter`, `collect`, `sum`, `fold`, etc.
- Chaining: Chain multiple iterator methods

**Key Takeaways:**
- Iterators are lazy (not executed until consumed)
- `iter()`, `iter_mut()`, `into_iter()` - different iterator types
- Chain methods: `iter().map().filter().collect()`

### Custom Iterators

**What this demonstrates:** Creating custom iterators.

**Code:**
```rust
struct Counter {
    count: u32,
}

impl Counter {
    fn new() -> Counter {
        Counter { count: 0 }
    }
}

impl Iterator for Counter {
    type Item = u32;
    
    fn next(&mut self) -> Option<Self::Item> {
        if self.count < 5 {
            self.count += 1;
            Some(self.count)
        } else {
            None
        }
    }
}

fn custom_iterator() {
    let mut counter = Counter::new();
    
    // Can use all iterator methods
    let sum: u32 = counter.sum();
    
    // Or manually
    let mut counter = Counter::new();
    assert_eq!(counter.next(), Some(1));
    assert_eq!(counter.next(), Some(2));
}
```

**Explanation:**
- Implement `Iterator` trait
- `type Item = T`: Associated type for iterator item
- `next(&mut self) -> Option<Self::Item>`: Required method
- Returns `Some(value)` or `None` when done
- Once implemented, all iterator methods available

**Key Takeaways:**
- Implement `Iterator` trait
- Define `type Item` and `next()` method
- Then all iterator methods work

---

## Smart Pointers

### Overview

Smart pointers are data structures that act like pointers but also have additional metadata and capabilities. Common smart pointers: `Box<T>`, `Rc<T>`, `RefCell<T>`.

### Key Concepts

- **Box<T>**: Heap allocation, single ownership
- **Rc<T>**: Reference counting, multiple ownership (single-threaded)
- **RefCell<T>**: Interior mutability, runtime borrow checking
- **Deref Trait**: Customize dereference operator (`*`)
- **Drop Trait**: Customize cleanup when value goes out of scope

### Box<T>

**What this demonstrates:** Heap allocation with Box.

**Code:**
```rust
fn box_demo() {
    // Box stores data on heap
    let b = Box::new(5);
    println!("b = {}", b);
    
    // Recursive types need Box (indirection)
    enum List {
        Cons(i32, Box<List>),
        Nil,
    }
    
    use List::{Cons, Nil};
    
    let list = Cons(1, Box::new(Cons(2, Box::new(Cons(3, Box::new(Nil))))));
}
```

**Explanation:**
- `Box<T>`: Allocates value on heap
- Single ownership (like owned values)
- Used for: Large data, recursive types, trait objects
- `Box::new(value)`: Creates box
- Automatically dereferenced (can use `*` or methods directly)

**Key Takeaways:**
- `Box<T>`: Heap allocation, single ownership
- Used for recursive types, large data
- Automatically dereferenced

### Rc<T> (Reference Counting)

**What this demonstrates:** Multiple ownership with reference counting.

**Code:**
```rust
use std::rc::Rc;

enum List {
    Cons(i32, Rc<List>),
    Nil,
}

use List::{Cons, Nil};

fn rc_demo() {
    let a = Rc::new(Cons(5, Rc::new(Cons(10, Rc::new(Nil)))));
    println!("count after creating a = {}", Rc::strong_count(&a));
    
    let b = Cons(3, Rc::clone(&a)); // Clone increases count
    println!("count after creating b = {}", Rc::strong_count(&a));
    
    {
        let c = Cons(4, Rc::clone(&a));
        println!("count after creating c = {}", Rc::strong_count(&a));
    } // c goes out of scope
    
    println!("count after c goes out of scope = {}", Rc::strong_count(&a));
}
```

**Explanation:**
- `Rc<T>`: Reference counting (single-threaded)
- Multiple ownership: Multiple variables can own same data
- `Rc::clone(&rc)`: Increments count (doesn't clone data)
- `Rc::strong_count(&rc)`: Get reference count
- Dropped when count reaches zero
- Only immutable access (use `RefCell` for interior mutability)

**Key Takeaways:**
- `Rc<T>`: Multiple ownership, reference counting
- `Rc::clone()` increments count (cheap)
- Only immutable access

### RefCell<T> (Interior Mutability)

**What this demonstrates:** Mutable borrows of immutable values.

**Code:**
```rust
use std::cell::RefCell;

fn refcell_demo() {
    let x = RefCell::new(5);
    
    {
        let mut r1 = x.borrow_mut(); // Mutable borrow
        *r1 += 1;
    } // r1 goes out of scope, borrow ends
    
    let r2 = x.borrow(); // Immutable borrow
    println!("{}", r2);
}

// Combine Rc and RefCell for multiple owners with mutability
use std::rc::Rc;
use std::cell::RefCell;

#[derive(Debug)]
enum List {
    Cons(Rc<RefCell<i32>>, Rc<List>),
    Nil,
}

fn rc_refcell_demo() {
    let value = Rc::new(RefCell::new(5));
    
    let a = Rc::new(Cons(Rc::clone(&value), Rc::new(Nil)));
    let b = Cons(Rc::clone(&value), Rc::clone(&a));
    
    *value.borrow_mut() += 10;
    
    println!("a after = {:?}", a);
    println!("b after = {:?}", b);
}
```

**Explanation:**
- `RefCell<T>`: Interior mutability (runtime borrow checking)
- `borrow()`: Immutable borrow (returns `Ref<T>`)
- `borrow_mut()`: Mutable borrow (returns `RefMut<T>`)
- Runtime checks: Panics if borrowing rules violated
- Combine with `Rc`: Multiple owners with mutability
- Trade-off: Runtime checks instead of compile-time

**Key Takeaways:**
- `RefCell<T>`: Interior mutability, runtime checks
- `borrow()` and `borrow_mut()` for access
- Combine with `Rc` for multiple owners with mutability

---

## Concurrency

### Overview

Rust's ownership system enables "fearless concurrency" - preventing data races at compile time. Common concurrency primitives: threads, channels, mutexes.

### Key Concepts

- **Threads**: Spawn parallel execution
- **Message Passing**: Channels for communication between threads
- **Shared State**: Mutex for shared mutable state
- **Arc<T>**: Atomic reference counting (thread-safe Rc)
- **Send and Sync**: Trait markers for thread safety

### Threads

**What this demonstrates:** Spawning threads.

**Code:**
```rust
use std::thread;
use std::time::Duration;

fn threads_demo() {
    // Spawn thread
    let handle = thread::spawn(|| {
        for i in 1..10 {
            println!("spawned thread: {}", i);
            thread::sleep(Duration::from_millis(1));
        }
    });
    
    // Main thread continues
    for i in 1..5 {
        println!("main thread: {}", i);
        thread::sleep(Duration::from_millis(1));
    }
    
    handle.join().unwrap(); // Wait for thread to finish
    
    // Move closure (take ownership)
    let v = vec![1, 2, 3];
    let handle = thread::spawn(move || {
        println!("vector: {:?}", v);
    });
    handle.join().unwrap();
}
```

**Explanation:**
- `thread::spawn(|| { })`: Spawn new thread
- Returns `JoinHandle`
- `handle.join()`: Wait for thread to finish
- `move` closure: Takes ownership of captured variables
- Threads run concurrently

**Key Takeaways:**
- `thread::spawn()` spawns thread
- `move` closure takes ownership
- `join()` waits for completion

### Message Passing (Channels)

**What this demonstrates:** Communication between threads.

**Code:**
```rust
use std::sync::mpsc;

fn channels_demo() {
    // Create channel
    let (tx, rx) = mpsc::channel();
    
    // Spawn thread to send
    thread::spawn(move || {
        let val = String::from("hi");
        tx.send(val).unwrap();
        // val moved, can't use it here
    });
    
    // Receive message
    let received = rx.recv().unwrap();
    println!("Got: {}", received);
    
    // Multiple producers
    let (tx, rx) = mpsc::channel();
    let tx1 = tx.clone();
    
    thread::spawn(move || {
        tx.send(String::from("hi from first")).unwrap();
    });
    
    thread::spawn(move || {
        tx1.send(String::from("hi from second")).unwrap();
    });
    
    for received in rx {
        println!("Got: {}", received);
    }
}
```

**Explanation:**
- `mpsc::channel()`: Creates channel (multiple producer, single consumer)
- `tx`: Transmitter (sender)
- `rx`: Receiver
- `send()`: Send value (takes ownership)
- `recv()`: Receive (blocks until message)
- `rx` can be iterated (receives until channel closed)
- `tx.clone()`: Create multiple senders

**Key Takeaways:**
- Channels: Message passing between threads
- `send()` takes ownership
- `rx` can be iterated
- `tx.clone()` for multiple senders

### Shared State (Mutex)

**What this demonstrates:** Shared mutable state with Mutex.

**Code:**
```rust
use std::sync::{Mutex, Arc};

fn mutex_demo() {
    // Mutex (single-threaded example)
    let m = Mutex::new(5);
    
    {
        let mut num = m.lock().unwrap();
        *num = 6;
    } // Lock released here
    
    println!("m = {:?}", m);
    
    // Multiple threads with Arc (Atomic Rc)
    let counter = Arc::new(Mutex::new(0));
    let mut handles = vec![];
    
    for _ in 0..10 {
        let counter = Arc::clone(&counter);
        let handle = thread::spawn(move || {
            let mut num = counter.lock().unwrap();
            *num += 1;
        });
        handles.push(handle);
    }
    
    for handle in handles {
        handle.join().unwrap();
    }
    
    println!("Result: {}", *counter.lock().unwrap());
}
```

**Explanation:**
- `Mutex<T>`: Mutual exclusion (lock)
- `lock()`: Acquires lock (returns `MutexGuard`)
- Lock released when guard goes out of scope
- `Arc<T>`: Atomic reference counting (thread-safe `Rc`)
- Combine `Arc<Mutex<T>>`: Multiple owners with mutability
- `lock().unwrap()`: Panics if poisoned (another thread panicked while holding lock)

**Key Takeaways:**
- `Mutex<T>`: Lock for shared state
- `Arc<T>`: Thread-safe reference counting
- `Arc<Mutex<T>>`: Multiple owners with mutability

---

## Macros

### Overview

Macros are a way of writing code that writes other code (metaprogramming). Rust has declarative macros (`macro_rules!`) and procedural macros.

### Key Concepts

- **Declarative Macros**: `macro_rules!` (pattern matching)
- **Procedural Macros**: Custom derive, attribute-like, function-like
- **Metaprogramming**: Code that generates code
- **Compile-time**: Macros expanded at compile time
- **Common Macros**: `println!`, `vec!`, `format!`

### Declarative Macros

**What this demonstrates:** Creating declarative macros.

**Code:**
```rust
// Simple macro
macro_rules! say_hello {
    () => {
        println!("Hello!");
    };
}

// Macro with parameters
macro_rules! create_function {
    ($func_name:ident) => {
        fn $func_name() {
            println!("Function {:?} called", stringify!($func_name));
        }
    };
}

// More complex macro (like vec!)
macro_rules! vec {
    ( $( $x:expr ),* ) => {
        {
            let mut temp_vec = Vec::new();
            $(
                temp_vec.push($x);
            )*
            temp_vec
        }
    };
}

fn macros_demo() {
    say_hello!();
    
    create_function!(foo);
    foo();
    
    let v = vec![1, 2, 3];
}
```

**Explanation:**
- `macro_rules! name { (pattern) => { code }; }`: Macro definition
- `$name:type`: Capture with type (ident, expr, ty, etc.)
- `$( ... )*`: Repeat (zero or more times)
- `stringify!()`: Convert to string literal
- Expanded at compile time
- More powerful but complex than functions

**Key Takeaways:**
- `macro_rules!` for declarative macros
- Pattern matching with `$name:type`
- `$(...)*` for repetition
- Expanded at compile time

---

## Best Practices

### Code Organization

- **Modules**: Organize code into modules
- **Visibility**: Use `pub` for public API
- **Documentation**: Use `///` for doc comments
- **Tests**: Write tests in `tests/` or `#[cfg(test)]`

### Error Handling

- **Result over Panic**: Use `Result` for recoverable errors
- **? Operator**: Use `?` for error propagation
- **Custom Errors**: Create error types for your domain
- **Error Libraries**: Consider `thiserror` or `anyhow` for complex error handling

### Ownership and Borrowing

- **Prefer Borrowing**: Use references when possible
- **Slice Parameters**: Prefer `&str` over `&String`, `&[T]` over `&Vec<T>`
- **Clone Sparingly**: Only clone when necessary
- **Understand Moves**: Know when values are moved

### Performance

- **Zero-Cost Abstractions**: Use high-level features (they're optimized)
- **Iterators**: Prefer iterators over loops (often faster)
- **Avoid Premature Optimization**: Write clear code first
- **Profile**: Use tools like `cargo flamegraph` for profiling

### Testing

- **Unit Tests**: `#[cfg(test)]` mod tests
- **Integration Tests**: `tests/` directory
- **Documentation Tests**: Examples in doc comments
- **Test Coverage**: Aim for good coverage

---

## Common Patterns

### Builder Pattern

```rust
struct Config {
    host: String,
    port: u16,
    timeout: u64,
}

impl Config {
    fn new() -> Self {
        Config {
            host: String::from("localhost"),
            port: 8080,
            timeout: 30,
        }
    }
    
    fn host(mut self, host: String) -> Self {
        self.host = host;
        self
    }
    
    fn port(mut self, port: u16) -> Self {
        self.port = port;
        self
    }
}

let config = Config::new()
    .host(String::from("example.com"))
    .port(443);
```

### Newtype Pattern

```rust
// Wrap type to add type safety
struct Meters(f64);
struct Feet(f64);

fn distance_in_meters(d: Meters) -> f64 {
    d.0
}

// Prevents mixing up Meters and Feet
```

### RAII Pattern

```rust
// Resource Acquisition Is Initialization
// Automatically clean up when value goes out of scope
struct Guard {
    // Resource held here
}

impl Drop for Guard {
    fn drop(&mut self) {
        // Cleanup code
    }
}
```

---

## Resources

### Official Documentation

- **Rust Book**: https://doc.rust-lang.org/book/
- **Rust Reference**: https://doc.rust-lang.org/reference/
- **Rust API Documentation**: https://doc.rust-lang.org/std/

### Learning Resources

- **Rust by Example**: https://doc.rust-lang.org/rust-by-example/
- **Rustlings**: Interactive exercises
- **Rustlings Repository**: https://github.com/rust-lang/rustlings

### Community

- **Stack Overflow**: Tag: rust
- **r/rust**: Reddit community
- **Rust Users Forum**: https://users.rust-lang.org/

### Tools

- **rustup**: Rust toolchain installer
- **cargo**: Package manager and build tool
- **rustfmt**: Code formatter
- **clippy**: Linter
- **rust-analyzer**: IDE support

---

