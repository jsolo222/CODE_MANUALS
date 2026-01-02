# Go (Golang) - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Variables & Constants](#variables--constants)
4. [Data Types](#data-types)
5. [Operators](#operators)
6. [Control Flow](#control-flow)
7. [Functions](#functions)
8. [Arrays & Slices](#arrays--slices)
9. [Maps](#maps)
10. [Structs](#structs)
11. [Interfaces](#interfaces)
12. [Pointers](#pointers)
13. [Error Handling](#error-handling)
14. [Goroutines & Concurrency](#goroutines--concurrency)
15. [Channels](#channels)
16. [Sync Package](#sync-package)
17. [Packages & Modules](#packages--modules)
18. [File I/O](#file-io)
19. [JSON](#json)
20. [Testing](#testing)
21. [Best Practices](#best-practices)
22. [Common Patterns](#common-patterns)
23. [Resources](#resources)

---

## Introduction

### What is Go?

Go (often referred to as Golang) is an open-source programming language developed by Google in 2007 and released in 2012. Go was designed to be simple, fast, and efficient for building scalable network services and large-scale distributed systems. It combines the ease of programming of an interpreted, dynamically typed language with the efficiency and safety of a statically typed, compiled language.

### Why Learn Go?

Go is valuable for:

1. **Simplicity**: Clean syntax, minimal keywords, easy to learn
2. **Performance**: Compiled to native code, fast execution
3. **Concurrency**: Built-in goroutines and channels for concurrent programming
4. **Compilation Speed**: Extremely fast compilation times
5. **Cloud Native**: Used in Docker, Kubernetes, and many cloud services
6. **Backend Services**: Excellent for microservices, APIs, and web servers
7. **Standard Library**: Rich standard library for common tasks
8. **Growing Ecosystem**: Active community and growing package ecosystem

### Key Features

- **Static Typing**: Type safety with type inference
- **Garbage Collected**: Automatic memory management
- **Fast Compilation**: Compiles quickly even for large codebases
- **Goroutines**: Lightweight threads for concurrency
- **Channels**: First-class communication mechanism for goroutines
- **Simple Syntax**: Minimalist design, easy to read and write
- **Tooling**: Excellent standard tools (go fmt, go test, go doc)

---

## Getting Started

### Installation

**Install Go:**
1. Visit https://golang.org/dl/
2. Download installer for your platform
3. Run installer

**Verify Installation:**
```bash
go version
```

### Your First Program

**What this demonstrates:** Basic Go program structure.

**Code:**
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
    fmt.Println("Welcome to Go!")
}
```

**Explanation:**
- `package main`: Declares package (executable program needs `main` package)
- `import "fmt"`: Imports package (fmt for formatting/printing)
- `func main()`: Entry point (must be in `main` package)
- `fmt.Println()`: Prints to console with newline

**To Run:**
1. Save as `main.go`
2. Run: `go run main.go`
3. Build: `go build` (creates executable)

**Key Takeaways:**
- `package main` for executable programs
- `func main()` is entry point
- `import` for packages

### Package Structure

**What this demonstrates:** Understanding packages.

**Code:**
```go
// Executable program
package main

func main() {
    // Must have main function
}

// Library package
package mypackage

// No main function
func HelperFunction() {
    // Exported function (capitalized)
}
```

**Explanation:**
- `package main`: Executable program (must have `main()`)
- `package name`: Library package (no `main()`)
- Exported: Capitalized names (public)
- Unexported: Lowercase names (private)

**Key Takeaways:**
- `package main` for executables
- Other packages for libraries
- Capitalized = exported (public)

### Imports

**What this demonstrates:** Importing packages.

**Code:**
```go
// Single import
import "fmt"

// Multiple imports (preferred style)
import (
    "fmt"
    "math"
    "strings"
)
```

**Explanation:**
- `import "package"`: Single import
- Grouped imports: Preferred style (go fmt formats this way)
- Standard library: `fmt`, `math`, `strings`, `os`, etc.
- Third-party: Import by module path

**Key Takeaways:**
- Grouped imports preferred
- Standard library packages available
- Third-party via module path

---

## Variables & Constants

### Overview

Go has explicit variable declarations and type inference. Variables can be declared with explicit types or inferred. Constants are compile-time values.

### Key Concepts

- **Variable Declaration**: `var name type = value`
- **Type Inference**: `var name = value` (compiler infers type)
- **Short Declaration**: `name := value` (inside functions only)
- **Zero Values**: Default values for uninitialized variables
- **Constants**: `const name = value` (compile-time constants)
- **Iota**: Auto-incrementing constant generator

### Variable Declaration

**What this demonstrates:** Different ways to declare variables.

**Code:**
```go
func variablesDemo() {
    // Explicit type
    var name string = "Commander"
    var age int = 25
    var salary float64 = 75000.50
    var isActive bool = true
    
    // Type inference
    var x = 42           // int
    var y = 3.14         // float64
    var z = "hello"      // string
    
    // Short declaration (inside functions only)
    count := 10
    message := "Hello"
    
    // Multiple variables
    var a, b, c int = 1, 2, 3
    var d, e = 4, "four"
    x, y, z := 1, 2.0, "three"
    
    // Zero values (default values)
    var i int        // 0
    var f float64    // 0.0
    var s string     // ""
    var b bool       // false
    var p *int       // nil
    
    fmt.Println(name, age, salary, isActive)
}
```

**Explanation:**
- `var name type = value`: Explicit type declaration
- `var name = value`: Type inferred
- `name := value`: Short declaration (inside functions, type inferred)
- Multiple: `var a, b, c = 1, 2, 3`
- Zero values: Uninitialized variables have default values
- `:=` is declaration, `=` is assignment

**Key Takeaways:**
- `var` for package-level or explicit declaration
- `:=` for short declaration (inside functions)
- Zero values for uninitialized variables

### Constants

**What this demonstrates:** Working with constants.

**Code:**
```go
func constantsDemo() {
    // Constants
    const PI = 3.14159
    const AppName = "MyApp"
    
    // Typed constants
    const MaxUsers int = 100
    
    // Multiple constants
    const (
        StatusOK    = 200
        StatusError = 500
    )
    
    // Iota (auto-incrementing constant)
    const (
        Sunday    = iota  // 0
        Monday            // 1
        Tuesday           // 2
        Wednesday         // 3
        Thursday          // 4
        Friday            // 5
        Saturday          // 6
    )
    
    // Iota with expressions
    const (
        _  = iota                // 0 (blank identifier, ignored)
        KB = 1 << (10 * iota)    // 1024
        MB                        // 1048576
        GB                        // 1073741824
    )
}
```

**Explanation:**
- `const name = value`: Untyped constant
- `const name type = value`: Typed constant
- Constant block: Multiple constants in parentheses
- `iota`: Starts at 0, increments by 1 for each constant in block
- `iota` resets: New `const` block resets iota
- Expressions: Can use `iota` in expressions

**Key Takeaways:**
- `const` for constants
- `iota` for auto-incrementing (starts at 0)
- Constants are compile-time values

---

## Data Types

### Overview

Go has a rich set of built-in types: integers, floats, complex numbers, booleans, strings, and more. Go is statically typed with type inference.

### Key Concepts

- **Basic Types**: Integers, floats, complex, bool, string
- **Type Sizes**: Multiple integer and float sizes
- **Type Conversion**: Explicit (no implicit conversion)
- **Aliases**: `byte` (uint8), `rune` (int32)
- **Zero Values**: Default values for each type

### Basic Types

**What this demonstrates:** Go's basic data types.

**Code:**
```go
func dataTypesDemo() {
    // Integers
    var i8 int8 = 127          // -128 to 127
    var i16 int16 = 32767      // -32768 to 32767
    var i32 int32 = 2147483647
    var i64 int64 = 9223372036854775807
    
    var u8 uint8 = 255         // 0 to 255
    var u16 uint16 = 65535
    var u32 uint32 = 4294967295
    var u64 uint64 = 18446744073709551615
    
    var i int = 42             // Platform dependent (32 or 64 bit)
    var u uint = 42            // Platform dependent unsigned
    
    var b byte = 255           // Alias for uint8
    var r rune = 'A'           // Alias for int32 (Unicode code point)
    
    // Floating point
    var f32 float32 = 3.14
    var f64 float64 = 3.14159265359
    
    // Complex numbers
    var c64 complex64 = 1 + 2i
    var c128 complex128 = 3 + 4i
    
    // Boolean
    var flag bool = true
    
    // String
    var str string = "Hello, Go!"
    
    fmt.Println(i8, u8, f32, c64, flag, str)
}
```

**Explanation:**
- Integers: Signed (`int8`, `int16`, `int32`, `int64`) and unsigned (`uint8`, etc.)
- `int`/`uint`: Platform-dependent size (32 or 64 bit)
- `byte`: Alias for `uint8`
- `rune`: Alias for `int32` (Unicode code point)
- Floats: `float32`, `float64`
- Complex: `complex64`, `complex128`
- Boolean: `bool` (true/false)
- String: `string` (UTF-8 encoded)

**Key Takeaways:**
- Multiple integer sizes (signed and unsigned)
- `int`/`uint` are platform-dependent
- `byte` = uint8, `rune` = int32
- Complex numbers built-in

### Type Conversion

**What this demonstrates:** Converting between types.

**Code:**
```go
func typeConversion() {
    // Type conversion (explicit, no implicit)
    var x int = 42
    var y float64 = float64(x)  // Must be explicit
    var z uint = uint(y)
    
    // Cannot do: var y float64 = x  // ERROR: implicit conversion
}
```

**Explanation:**
- Explicit conversion: `Type(value)`
- No implicit conversion: Must be explicit
- Safe conversions: Compiler checks if conversion is valid
- Lossy conversions: May lose precision (e.g., float to int)

**Key Takeaways:**
- Type conversion: `Type(value)`
- No implicit conversion
- Must be explicit

---

## Operators

### Overview

Go provides arithmetic, comparison, logical, bitwise, and assignment operators. Understanding operators is essential for writing expressions.

### Key Concepts

- **Arithmetic**: `+`, `-`, `*`, `/`, `%`
- **Comparison**: `==`, `!=`, `<`, `>`, `<=`, `>=`
- **Logical**: `&&`, `||`, `!`
- **Bitwise**: `&`, `|`, `^`, `<<`, `>>`, `&^`
- **Assignment**: `=`, `+=`, `-=`, etc.

### Arithmetic Operators

**What this demonstrates:** Basic arithmetic operations.

**Code:**
```go
func arithmeticDemo() {
    a, b := 10, 3
    
    sum := a + b        // 13
    diff := a - b       // 7
    prod := a * b       // 30
    quot := a / b       // 3 (integer division)
    rem := a % b        // 1 (modulo)
    
    // Increment/Decrement (statements, not expressions)
    x := 5
    x++  // x = x + 1
    x--  // x = x - 1
    // y := x++  // ERROR: ++ is a statement, not expression
}
```

**Explanation:**
- Standard arithmetic: `+`, `-`, `*`, `/`, `%`
- Integer division: `/` with integers does integer division
- Modulo: `%` returns remainder
- Increment/decrement: `++`, `--` are statements (not expressions)
- Cannot use `++` in expressions (unlike C)

**Key Takeaways:**
- Standard arithmetic operators
- `/` with integers = integer division
- `++`/`--` are statements, not expressions

### Comparison and Logical Operators

**What this demonstrates:** Comparison and logical operations.

**Code:**
```go
func comparisonLogicalDemo() {
    a, b := 10, 3
    
    // Comparison
    equal := a == b      // false
    notEqual := a != b   // true
    greater := a > b     // true
    less := a < b        // false
    greaterEq := a >= b  // true
    lessEq := a <= b     // false
    
    // Logical
    t, f := true, false
    and := t && f        // false
    or := t || f         // true
    not := !t            // false
}
```

**Explanation:**
- Comparison: Returns `bool`
- Logical: `&&` (AND), `||` (OR), `!` (NOT)
- Short-circuit: `&&` and `||` short-circuit
- All comparisons must be valid types

**Key Takeaways:**
- Comparison operators return `bool`
- Logical: `&&`, `||`, `!`
- Short-circuit evaluation

### Bitwise Operators

**What this demonstrates:** Bitwise operations.

**Code:**
```go
func bitwiseDemo() {
    p, q := 5, 3         // 0101, 0011
    
    andBit := p & q      // 0001 = 1
    orBit := p | q       // 0111 = 7
    xorBit := p ^ q      // 0110 = 6
    leftShift := p << 2  // 10100 = 20
    rightShift := p >> 1 // 0010 = 2
    andNot := p &^ q     // bit clear (AND NOT)
}
```

**Explanation:**
- `&`: Bitwise AND
- `|`: Bitwise OR
- `^`: Bitwise XOR
- `<<`: Left shift
- `>>`: Right shift
- `&^`: Bit clear (AND NOT)

**Key Takeaways:**
- Bitwise operators for bit manipulation
- `&^` is bit clear (AND NOT)

---

## Control Flow

### Overview

Go provides `if/else`, `switch`, and loops (`for`) for control flow. Go's `switch` is more flexible than in many languages.

### Key Concepts

- **If/Else**: Conditional execution with optional short statement
- **Switch**: Multiple cases, can work like if-else chains
- **Type Switch**: Switch on type
- **For Loop**: Only loop type (can be used like while)
- **Range**: Iterate over slices, maps, strings, channels

### If/Else Statements

**What this demonstrates:** Conditional execution.

**Code:**
```go
func ifElseDemo() {
    x := 10
    
    // Basic if/else
    if x > 0 {
        fmt.Println("Positive")
    } else if x < 0 {
        fmt.Println("Negative")
    } else {
        fmt.Println("Zero")
    }
    
    // If with short statement
    if num := 9; num < 0 {
        fmt.Println("Negative")
    } else if num < 10 {
        fmt.Println("Single digit")
    } else {
        fmt.Println("Multiple digits")
    }
    // num not accessible here (scope)
}
```

**Explanation:**
- `if condition { }`: Basic conditional
- `else if` / `else`: Additional branches
- Short statement: `if stmt; condition { }` (variable in scope of if block only)
- Scope: Variables declared in short statement limited to if/else blocks

**Key Takeaways:**
- `if/else` for conditionals
- Short statement: `if stmt; condition { }`
- Scope: Short statement variables limited to if/else

### Switch Statements

**What this demonstrates:** Switch statements (more flexible than in other languages).

**Code:**
```go
func switchDemo() {
    day := 3
    
    // Basic switch
    switch day {
    case 1:
        fmt.Println("Monday")
    case 2:
        fmt.Println("Tuesday")
    case 3:
        fmt.Println("Wednesday")
    case 4, 5:  // Multiple values
        fmt.Println("Thursday or Friday")
    default:
        fmt.Println("Weekend")
    }
    
    // Switch with short statement
    switch num := 15; {
    case num < 10:
        fmt.Println("Less than 10")
    case num < 20:
        fmt.Println("Between 10 and 20")
    default:
        fmt.Println("20 or more")
    }
    
    // Switch without expression (replaces if-else chain)
    age := 25
    switch {
    case age < 13:
        fmt.Println("Child")
    case age < 20:
        fmt.Println("Teenager")
    case age < 65:
        fmt.Println("Adult")
    default:
        fmt.Println("Senior")
    }
    
    // Type switch
    var i interface{} = "hello"
    switch v := i.(type) {
    case int:
        fmt.Printf("Integer: %d\n", v)
    case string:
        fmt.Printf("String: %s\n", v)
    case bool:
        fmt.Printf("Boolean: %t\n", v)
    default:
        fmt.Printf("Unknown type: %T\n", v)
    }
}
```

**Explanation:**
- `switch value { case ... }`: Switch on value
- Multiple values: `case 4, 5:`
- Short statement: `switch stmt; { }`
- No expression: `switch { }` (like if-else chain)
- Type switch: `switch v := x.(type) { }`
- No fall-through: Cases don't fall through (use `fallthrough` if needed)

**Key Takeaways:**
- `switch` is flexible (can work like if-else)
- Multiple values: `case 4, 5:`
- Type switch: `switch v := x.(type) { }`
- No automatic fall-through

### For Loops

**What this demonstrates:** For loops (Go's only loop).

**Code:**
```go
func forLoopDemo() {
    // Traditional for loop
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }
    
    // While-style (condition only)
    sum := 1
    for sum < 1000 {
        sum += sum
    }
    
    // Infinite loop
    for {
        // Break with condition
        if condition {
            break
        }
    }
    
    // Range over slice
    nums := []int{1, 2, 3}
    for index, value := range nums {
        fmt.Printf("Index: %d, Value: %d\n", index, value)
    }
    
    // Range over map
    m := map[string]int{"a": 1, "b": 2}
    for key, value := range m {
        fmt.Printf("Key: %s, Value: %d\n", key, value)
    }
    
    // Range over string (runes)
    for i, r := range "Hello" {
        fmt.Printf("Index: %d, Rune: %c\n", i, r)
    }
    
    // Skip index/value with _
    for _, value := range nums {
        fmt.Println(value)
    }
}
```

**Explanation:**
- Traditional: `for init; condition; post { }`
- While-style: `for condition { }`
- Infinite: `for { }`
- Range: `for index, value := range collection { }`
- Range works: Slices, arrays, maps, strings, channels
- Skip values: Use `_` to ignore index or value

**Key Takeaways:**
- `for` is the only loop type
- Can be used like while: `for condition { }`
- `range` iterates over collections
- Use `_` to ignore values

---

## Functions

### Overview

Functions are first-class citizens in Go. They can be assigned to variables, passed as parameters, and returned as values. Go also supports closures and variadic functions.

### Key Concepts

- **Function Declaration**: `func name(params) returnType { }`
- **Multiple Returns**: Functions can return multiple values
- **Named Returns**: Return values can be named
- **Variadic Functions**: Functions with variable arguments (`...`)
- **First-Class**: Functions are values
- **Closures**: Functions that capture variables
- **Defer**: Execute code after function returns
- **Panic/Recover**: Error handling mechanism

### Basic Functions

**What this demonstrates:** Defining and calling functions.

**Code:**
```go
// Basic function
func greet(name string) {
    fmt.Printf("Hello, %s!\n", name)
}

// Function with return value
func add(x int, y int) int {
    return x + y
}

// Shorthand parameters (same type)
func multiply(x, y int) int {
    return x * y
}

// Multiple return values
func swap(x, y string) (string, string) {
    return y, x
}

// Named return values
func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return  // Naked return (returns x, y)
}
```

**Explanation:**
- `func name(params) returnType { }`: Function syntax
- Parameters: `name type` or `name1, name2 type` (same type)
- Return type: `returnType` or `(type1, type2)` for multiple
- Named returns: `(x, y int)` - can use naked return
- Naked return: `return` without values (uses named returns)

**Key Takeaways:**
- Functions: `func name(params) returnType { }`
- Multiple returns: `(type1, type2)`
- Named returns: Can use naked return

### Variadic Functions

**What this demonstrates:** Functions with variable arguments.

**Code:**
```go
// Variadic function (variable arguments)
func sum(numbers ...int) int {
    total := 0
    for _, num := range numbers {
        total += num
    }
    return total
}

func variadicDemo() {
    result := sum(1, 2, 3, 4, 5)  // 15
    result = sum()                 // 0 (empty)
    
    // Pass slice with ...
    nums := []int{1, 2, 3}
    result = sum(nums...)          // Unpack slice
}
```

**Explanation:**
- `...type`: Variadic parameter (accepts zero or more values)
- Variadic parameter: Becomes slice inside function
- Unpack: `slice...` unpacks slice as arguments
- Must be last parameter

**Key Takeaways:**
- `...type` for variadic parameters
- Becomes slice inside function
- `slice...` unpacks slice

### Functions as Values

**What this demonstrates:** Functions as first-class values.

**Code:**
```go
func functionsAsValues() {
    // Assign function to variable
    add := func(a, b int) int {
        return a + b
    }
    
    result := add(5, 3)
    fmt.Println(result)
    
    // Function as parameter
    compute := func(fn func(int, int) int, a, b int) int {
        return fn(a, b)
    }
    
    result = compute(add, 10, 20)
    fmt.Println(result)
}
```

**Explanation:**
- Functions are values: Can assign to variables
- Function types: `func(int, int) int`
- Can pass functions as parameters
- Can return functions

**Key Takeaways:**
- Functions are first-class values
- Can assign, pass, return functions
- Function type: `func(params) returnType`

### Closures

**What this demonstrates:** Functions that capture variables.

**Code:**
```go
// Closure (function that captures variables)
func adder() func(int) int {
    sum := 0
    return func(x int) int {
        sum += x
        return sum
    }
}

func closuresDemo() {
    pos := adder()
    fmt.Println(pos(1))  // 1
    fmt.Println(pos(2))  // 3
    fmt.Println(pos(3))  // 6
    
    // Each closure has its own captured variables
    neg := adder()
    fmt.Println(neg(-1)) // -1
    fmt.Println(neg(-2)) // -3
}
```

**Explanation:**
- Closure: Function that captures variables from enclosing scope
- Captured variables: Live as long as closure exists
- Each closure: Has its own captured variables
- Useful for: Stateful functions, callbacks

**Key Takeaways:**
- Closures capture variables from outer scope
- Variables live as long as closure exists
- Each closure has independent captured variables

### Defer

**What this demonstrates:** Deferred execution.

**Code:**
```go
func deferDemo() {
    defer fmt.Println("World")  // Executed last
    fmt.Println("Hello")        // Executed first
    // Output: Hello \n World
    
    // Multiple defers (LIFO - stack)
    for i := 0; i < 3; i++ {
        defer fmt.Println(i)  // Executed in reverse order
    }
    // Output: 2, 1, 0
    
    // Common use: Close files
    file := openFile("data.txt")
    defer file.Close()  // Always closes, even if error
    
    // Process file...
}
```

**Explanation:**
- `defer statement`: Executes after function returns
- LIFO order: Multiple defers execute in reverse order
- Common use: Cleanup (close files, unlock mutexes)
- Arguments evaluated immediately: Values captured, not expressions

**Key Takeaways:**
- `defer` executes after function returns
- LIFO order for multiple defers
- Common for cleanup operations

### Panic and Recover

**What this demonstrates:** Panic and recovery mechanism.

**Code:**
```go
func panicDemo() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from:", r)
        }
    }()
    
    fmt.Println("Starting")
    panic("Something went wrong!")
    fmt.Println("This won't print")
}

func recoverDemo() {
    // Recover only works in deferred functions
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered:", r)
        }
    }()
    
    panic("Panic!")
}
```

**Explanation:**
- `panic(value)`: Stops normal execution, starts panicking
- Panic propagates: Up call stack until recovered or program exits
- `recover()`: Captures panic value, stops panicking
- Recover: Only works in deferred functions
- Use sparingly: Prefer returning errors in most cases

**Key Takeaways:**
- `panic()` stops execution
- `recover()` in deferred function catches panic
- Prefer error returns over panic

---

## Arrays & Slices

### Overview

Arrays are fixed-size sequences, while slices are dynamic arrays built on top of arrays. Slices are more commonly used than arrays in Go.

### Key Concepts

- **Arrays**: Fixed size `[n]T`
- **Slices**: Dynamic `[]T` (built on arrays)
- **Slicing**: Create slice from array/slice `[start:end]`
- **Append**: Add elements to slice
- **Length and Capacity**: `len()` and `cap()`
- **Make**: Create slice with specified length/capacity

### Arrays

**What this demonstrates:** Working with arrays.

**Code:**
```go
func arraysDemo() {
    // Arrays (fixed size)
    var arr [5]int                    // [0 0 0 0 0]
    arr[0] = 10
    arr[1] = 20
    
    arr2 := [5]int{1, 2, 3, 4, 5}     // Initialize
    arr3 := [...]int{1, 2, 3}         // Compiler counts size
    
    length := len(arr2)                // 5
    
    // Arrays are value types (copied)
    arr4 := arr2
    arr4[0] = 100
    fmt.Println(arr2[0])  // Still 1 (not modified)
    
    fmt.Println(arr2, arr3)
}
```

**Explanation:**
- `[n]T`: Array of n elements of type T
- Fixed size: Size is part of type
- `[...]T`: Compiler infers size
- Value type: Assigning copies array
- Less common: Slices are preferred

**Key Takeaways:**
- Arrays: `[n]T`, fixed size
- Value type (copied on assignment)
- Less commonly used (slices preferred)

### Slices

**What this demonstrates:** Working with slices.

**Code:**
```go
func slicesDemo() {
    // Slices (dynamic arrays)
    var s []int                        // nil slice
    s = make([]int, 5)                 // Length 5, capacity 5
    s = make([]int, 5, 10)            // Length 5, capacity 10
    
    slice := []int{1, 2, 3, 4, 5}     // Slice literal
    
    // Length and capacity
    length := len(slice)                // 5
    capacity := cap(slice)             // 5
    
    // Slicing (creates new slice, shares underlying array)
    sub := slice[1:3]                  // [2, 3]
    sub2 := slice[:3]                  // [1, 2, 3]
    sub3 := slice[2:]                  // [3, 4, 5]
    sub4 := slice[:]                   // [1, 2, 3, 4, 5] (copy reference)
    
    // Append (returns new slice if capacity exceeded)
    slice = append(slice, 6)           // [1, 2, 3, 4, 5, 6]
    slice = append(slice, 7, 8, 9)     // Multiple values
    
    // Append slice to slice
    slice2 := []int{10, 11, 12}
    slice = append(slice, slice2...)   // ... unpacks slice
    
    // Copy
    destination := make([]int, len(slice))
    copy(destination, slice)
    
    // 2D slice
    matrix := [][]int{
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9},
    }
    
    fmt.Println(slice, matrix)
}
```

**Explanation:**
- `[]T`: Slice of type T
- Dynamic: Can grow and shrink
- Backed by array: Slice is view into underlying array
- Length: `len(slice)` - number of elements
- Capacity: `cap(slice)` - underlying array size
- Slicing: `[start:end]` (end exclusive, shares array)
- `append()`: Adds elements, may allocate new array if capacity exceeded
- `copy()`: Copies elements to destination slice

**Key Takeaways:**
- Slices: `[]T`, dynamic size
- `len()` and `cap()` for length and capacity
- `append()` for adding elements
- Slicing shares underlying array

---

## Maps

### Overview

Maps are key-value data structures (hash tables). They're widely used for lookups and associations.

### Key Concepts

- **Map Type**: `map[KeyType]ValueType`
- **Nil Maps**: Cannot add keys to nil map (must use `make`)
- **Zero Value**: `nil` for maps
- **Key Existence**: Two-value assignment checks existence
- **Iteration**: `range` over maps (order is random)

### Maps

**What this demonstrates:** Working with maps.

**Code:**
```go
func mapsDemo() {
    // Map declaration
    var m map[string]int               // nil map (can't add keys)
    
    // Make (initialize)
    m = make(map[string]int)
    
    // Map literal
    ages := map[string]int{
        "Alice":   25,
        "Bob":     30,
        "Charlie": 35,
    }
    
    // Add/Update
    ages["David"] = 40
    ages["Alice"] = 26  // Update
    
    // Get value
    age := ages["Bob"]                 // 30
    age = ages["Unknown"]              // 0 (zero value)
    
    // Check if key exists
    age, exists := ages["Bob"]
    if exists {
        fmt.Println("Bob's age:", age)
    }
    
    // Delete
    delete(ages, "Charlie")
    
    // Iterate (order is random)
    for name, age := range ages {
        fmt.Printf("%s: %d\n", name, age)
    }
    
    // Map of maps
    users := map[string]map[string]string{
        "user1": {
            "name":  "Alice",
            "email": "alice@example.com",
        },
        "user2": {
            "name":  "Bob",
            "email": "bob@example.com",
        },
    }
    
    fmt.Println(ages, users)
}
```

**Explanation:**
- `map[KeyType]ValueType`: Map type
- Keys: Must be comparable (not slices, maps, functions)
- Nil map: Cannot add keys (use `make` first)
- Access: `map[key]` returns zero value if key doesn't exist
- Two-value assignment: `value, ok := map[key]` checks existence
- Delete: `delete(map, key)`
- Iteration: Order is random (not insertion order)

**Key Takeaways:**
- Maps: `map[KeyType]ValueType`
- Use `make()` or literal to initialize
- Two-value assignment checks key existence
- Iteration order is random

---

## Structs

### Overview

Structs are collections of fields. They're used to group related data together. Go supports methods on structs and embedding for composition.

### Key Concepts

- **Struct Definition**: `type Name struct { }`
- **Fields**: Named fields with types
- **Methods**: Functions with receivers
- **Pointers**: Can use pointer receivers
- **Embedding**: Composition (not inheritance)
- **Tags**: Metadata for fields (JSON, etc.)

### Struct Definition

**What this demonstrates:** Creating and using structs.

**Code:**
```go
// Define struct
type Person struct {
    Name    string
    Age     int
    Email   string
    Address Address  // Embedded struct
}

type Address struct {
    Street string
    City   string
    State  string
    Zip    string
}

// Struct with tags
type User struct {
    ID       int    `json:"id"`
    Username string `json:"username"`
    Email    string `json:"email,omitempty"`
}

func structsDemo() {
    // Create struct
    p1 := Person{
        Name:  "Alice",
        Age:   25,
        Email: "alice@example.com",
    }
    
    // Positional (not recommended)
    p2 := Person{"Bob", 30, "bob@example.com", Address{}}
    
    // Zero values
    var p3 Person  // Name: "", Age: 0, Email: ""
    
    // Pointer to struct
    p4 := &Person{
        Name: "Charlie",
        Age:  35,
    }
    
    // Access fields
    fmt.Println(p1.Name)
    fmt.Println(p4.Name)  // Auto-dereferenced
    
    // Modify
    p1.Age = 26
    p4.Email = "charlie@example.com"
    
    // Anonymous struct
    dog := struct {
        Name  string
        Breed string
    }{
        Name:  "Max",
        Breed: "Golden Retriever",
    }
    
    fmt.Println(p1, dog)
}
```

**Explanation:**
- `type Name struct { }`: Struct definition
- Fields: Named with types
- Initialization: Field names (recommended) or positional
- Zero values: Fields get zero values
- Pointer: `&Struct{ }` creates pointer
- Auto-dereference: Can access fields on pointer
- Anonymous struct: Struct without type name

**Key Takeaways:**
- `type Name struct { }` defines struct
- Use field names for initialization
- Pointers auto-dereference for field access

### Methods

**What this demonstrates:** Methods on structs.

**Code:**
```go
type Person struct {
    Name string
    Age  int
}

// Value receiver (cannot modify)
func (p Person) Greet() {
    fmt.Printf("Hello, I'm %s!\n", p.Name)
}

// Pointer receiver (can modify)
func (p *Person) Birthday() {
    p.Age++
}

func methodsDemo() {
    person := Person{Name: "Alice", Age: 25}
    person.Greet()
    person.Birthday()  // Works with value too (auto-converts)
    fmt.Println(person.Age)  // 26
    
    // Pointer receiver preferred when:
    // - Method needs to modify receiver
    // - Receiver is large (avoids copying)
}
```

**Explanation:**
- `func (receiver Type) Method() { }`: Method syntax
- Value receiver: `(p Person)` - receives copy
- Pointer receiver: `(p *Person)` - receives pointer
- Auto-conversion: Can call pointer method on value (and vice versa)
- Pointer receiver: Preferred when modifying or receiver is large

**Key Takeaways:**
- Methods: `func (receiver) Method() { }`
- Value receiver: Copy, cannot modify
- Pointer receiver: Can modify, avoids copying

### Embedding

**What this demonstrates:** Composition with embedding.

**Code:**
```go
// Embedding (composition)
type Employee struct {
    Person           // Embedded struct (no field name)
    Company  string
    Position string
}

func embeddingDemo() {
    emp := Employee{
        Person: Person{
            Name: "Bob",
            Age:  30,
        },
        Company:  "Acme Corp",
        Position: "Engineer",
    }
    
    // Access embedded fields directly
    fmt.Println(emp.Name)     // From Person
    fmt.Println(emp.Company)  // From Employee
    
    // Call embedded methods
    emp.Greet()               // From Person
    
    // Can also use explicit field name
    fmt.Println(emp.Person.Name)
}
```

**Explanation:**
- Embedding: Include struct without field name
- Promoted fields: Embedded struct fields accessible directly
- Promoted methods: Embedded struct methods accessible
- Composition: Prefer over inheritance
- Explicit access: Can use `embedded.Struct.Field` if needed

**Key Takeaways:**
- Embedding: Composition over inheritance
- Fields and methods are promoted
- Access directly or via embedded type name

---

## Interfaces

### Overview

Interfaces define behavior (set of methods). Types implement interfaces implicitly - no explicit declaration needed. Go's interfaces are powerful and flexible.

### Key Concepts

- **Interface Definition**: `type Name interface { }`
- **Implicit Implementation**: Types implement interfaces automatically
- **Polymorphism**: Interface variables can hold any implementing type
- **Empty Interface**: `interface{}` or `any` (any type)
- **Type Assertion**: Extract concrete type from interface
- **Type Switch**: Switch on interface type

### Interfaces

**What this demonstrates:** Defining and implementing interfaces.

**Code:**
```go
// Define interface
type Shape interface {
    Area() float64
    Perimeter() float64
}

type Rectangle struct {
    Width  float64
    Height float64
}

type Circle struct {
    Radius float64
}

// Implement interface (implicit - no explicit declaration)
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
    return 2 * (r.Width + r.Height)
}

func (c Circle) Area() float64 {
    return 3.14159 * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * 3.14159 * c.Radius
}

func interfacesDemo() {
    // Polymorphism
    var s Shape
    
    s = Rectangle{Width: 10, Height: 5}
    fmt.Printf("Rectangle area: %.2f\n", s.Area())
    
    s = Circle{Radius: 7}
    fmt.Printf("Circle area: %.2f\n", s.Area())
    
    // Interface slice
    shapes := []Shape{
        Rectangle{Width: 10, Height: 5},
        Circle{Radius: 7},
    }
    
    for _, shape := range shapes {
        fmt.Printf("Area: %.2f\n", shape.Area())
    }
}
```

**Explanation:**
- `type Name interface { }`: Interface definition
- Methods: List of method signatures
- Implicit: Types implement interfaces automatically
- Polymorphism: Interface variable can hold any implementing type
- Interface values: Store (value, type) pair
- Interface slices: Can store different types implementing interface

**Key Takeaways:**
- Interfaces: Define behavior (methods)
- Implicit implementation
- Polymorphism with interface variables

### Empty Interface

**What this demonstrates:** Empty interface (`interface{}` or `any`).

**Code:**
```go
func emptyInterfaceDemo() {
    // Empty interface (any type)
    var i interface{}  // or: var i any (Go 1.18+)
    
    i = 42
    i = "hello"
    i = true
    
    // Type assertion
    str, ok := i.(string)
    if ok {
        fmt.Println("String:", str)
    }
    
    // Type switch
    switch v := i.(type) {
    case int:
        fmt.Printf("Integer: %d\n", v)
    case string:
        fmt.Printf("String: %s\n", v)
    case bool:
        fmt.Printf("Boolean: %t\n", v)
    default:
        fmt.Printf("Unknown type: %T\n", v)
    }
}
```

**Explanation:**
- `interface{}` or `any`: Empty interface (any type)
- Type assertion: `value, ok := i.(Type)` extracts concrete type
- Type switch: `switch v := i.(type) { }` switches on type
- Useful for: Generic code, accepting any type

**Key Takeaways:**
- `interface{}` or `any`: Any type
- Type assertion: Extract concrete type
- Type switch: Switch on type

---

## Pointers

### Overview

Pointers hold memory addresses. Go has pointers but no pointer arithmetic. Pointers are used for efficiency and modifying values.

### Key Concepts

- **Pointer Type**: `*Type`
- **Address Operator**: `&variable` (get address)
- **Dereference**: `*pointer` (get value)
- **Nil Pointers**: Zero value is `nil`
- **New**: `new(Type)` allocates and returns pointer
- **Auto-dereference**: Struct fields auto-dereference on pointers

### Pointers

**What this demonstrates:** Working with pointers.

**Code:**
```go
func pointersDemo() {
    // Pointer basics
    x := 42
    p := &x      // p is pointer to x
    
    fmt.Println(*p)  // Dereference: 42
    *p = 21          // Modify through pointer
    fmt.Println(x)   // 21
    
    // Nil pointer
    var ptr *int
    fmt.Println(ptr == nil)  // true
    
    // New (allocates memory, returns pointer)
    ptr = new(int)
    *ptr = 100
    fmt.Println(*ptr)  // 100
    
    // Pointer to struct
    type Person struct {
        Name string
        Age  int
    }
    
    p1 := &Person{Name: "Alice", Age: 25}
    p1.Age = 26  // Auto-dereferenced
    
    // Passing pointers to functions
    increment := func(n *int) {
        *n++
    }
    
    num := 10
    increment(&num)
    fmt.Println(num)  // 11
}
```

**Explanation:**
- `*Type`: Pointer type
- `&variable`: Get address (reference operator)
- `*pointer`: Dereference (get value)
- `new(Type)`: Allocates zero value, returns pointer
- Auto-dereference: Struct fields auto-dereference on pointers
- No arithmetic: Cannot do pointer arithmetic (unlike C)

**Key Takeaways:**
- `*Type`: Pointer type
- `&` gets address, `*` dereferences
- `new()` allocates and returns pointer
- No pointer arithmetic

---

## Error Handling

### Overview

Go uses explicit error returns instead of exceptions. Functions return errors as the last return value. This makes error handling explicit and visible.

### Key Concepts

- **Error Interface**: `error` interface (has `Error() string` method)
- **Error Returns**: Functions return `(value, error)`
- **Error Checking**: Always check errors
- **Custom Errors**: Define error types
- **Error Wrapping**: Wrap errors with context (Go 1.13+)
- **Error Unwrapping**: Unwrap wrapped errors

### Error Handling

**What this demonstrates:** Handling errors in Go.

**Code:**
```go
import (
    "errors"
    "fmt"
)

// Functions return errors
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}

// Custom error
type MyError struct {
    Message string
    Code    int
}

func (e *MyError) Error() string {
    return fmt.Sprintf("Error %d: %s", e.Code, e.Message)
}

func doSomething() error {
    return &MyError{
        Message: "Something went wrong",
        Code:    500,
    }
}

func errorHandlingDemo() {
    // Basic error handling
    result, err := divide(10, 2)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    fmt.Println("Result:", result)
    
    // Custom error
    err = doSomething()
    if err != nil {
        fmt.Println(err)
    }
    
    // Error wrapping (Go 1.13+)
    err = fmt.Errorf("failed to process: %w", err)
    
    // Error unwrapping
    originalErr := errors.Unwrap(err)
    fmt.Println(originalErr)
    
    // Error checking
    if errors.Is(err, originalErr) {
        fmt.Println("Errors match")
    }
}
```

**Explanation:**
- Error interface: `error` interface with `Error() string` method
- Error returns: `(value, error)` pattern
- Always check: Check error before using value
- Custom errors: Define types implementing `error` interface
- Error wrapping: `fmt.Errorf("...: %w", err)` wraps error
- Error unwrapping: `errors.Unwrap()` gets wrapped error
- Error checking: `errors.Is()` checks if error matches

**Key Takeaways:**
- Errors are returned, not thrown
- Always check errors
- Custom errors implement `error` interface
- Error wrapping adds context

---

## Goroutines & Concurrency

### Overview

Goroutines are lightweight threads managed by the Go runtime. They enable concurrent programming with very low overhead. Go's concurrency model is based on "communicating sequential processes" (CSP).

### Key Concepts

- **Goroutines**: `go function()` - lightweight threads
- **Concurrent**: Multiple goroutines run concurrently
- **Parallel**: May run in parallel (if multiple CPUs)
- **Runtime**: Go runtime schedules goroutines
- **Lightweight**: Very low overhead (can have thousands)
- **Channels**: Communication mechanism (covered in next section)

### Goroutines

**What this demonstrates:** Creating and running goroutines.

**Code:**
```go
import (
    "fmt"
    "time"
)

func say(s string) {
    for i := 0; i < 5; i++ {
        time.Sleep(100 * time.Millisecond)
        fmt.Println(s)
    }
}

func goroutinesDemo() {
    // Start goroutine
    go say("world")
    say("hello")
    
    // Anonymous goroutine
    go func() {
        fmt.Println("Anonymous goroutine")
    }()
    
    // Wait for goroutines
    time.Sleep(1 * time.Second)
}
```

**Explanation:**
- `go function()`: Starts goroutine (non-blocking)
- Concurrent: Goroutines run concurrently
- Main goroutine: Program starts with main goroutine
- Exit: Program exits when main goroutine finishes
- Scheduling: Go runtime schedules goroutines

**Key Takeaways:**
- `go` keyword starts goroutine
- Non-blocking (continues immediately)
- Program exits when main goroutine finishes

---

## Channels

### Overview

Channels are typed conduits for communication between goroutines. They enable safe communication and synchronization. "Don't communicate by sharing memory; share memory by communicating."

### Key Concepts

- **Channel Type**: `chan Type`
- **Send/Receive**: `channel <- value` (send), `<-channel` (receive)
- **Blocking**: Send/receive blocks until other side ready
- **Buffered Channels**: Can buffer values
- **Close**: Close channels when done
- **Range**: Iterate over channel
- **Select**: Multiplex channels

### Channels

**What this demonstrates:** Creating and using channels.

**Code:**
```go
func channelsDemo() {
    // Create channel
    ch := make(chan int)
    
    // Send and receive (blocking)
    go func() {
        ch <- 42  // Send to channel
    }()
    
    value := <-ch  // Receive from channel (blocks)
    fmt.Println(value)
    
    // Buffered channel
    buffered := make(chan int, 2)
    buffered <- 1
    buffered <- 2
    // buffered <- 3  // Would block (buffer full)
    
    fmt.Println(<-buffered)  // 1
    fmt.Println(<-buffered)  // 2
    
    // Close channel
    ch2 := make(chan int, 2)
    ch2 <- 1
    ch2 <- 2
    close(ch2)
    
    // Range over channel (receives until closed)
    for val := range ch2 {
        fmt.Println(val)
    }
    
    // Check if closed
    val, ok := <-ch2
    if !ok {
        fmt.Println("Channel closed")
    }
}
```

**Explanation:**
- `make(chan Type)`: Unbuffered channel
- `make(chan Type, n)`: Buffered channel (buffer size n)
- Send: `channel <- value`
- Receive: `value := <-channel` or `<-channel` (discard)
- Blocking: Unbuffered channels block until both sides ready
- Buffered: Can send up to buffer size without blocking
- Close: `close(channel)` closes channel
- Range: Iterates until channel closed
- Two-value receive: `value, ok := <-channel` (ok is false if closed)

**Key Takeaways:**
- Channels: Communication between goroutines
- Unbuffered: Blocks until both sides ready
- Buffered: Can buffer values
- Close channel when done

### Select Statement

**What this demonstrates:** Multiplexing channels with select.

**Code:**
```go
func selectDemo() {
    ch1 := make(chan string)
    ch2 := make(chan string)
    
    go func() {
        time.Sleep(1 * time.Second)
        ch1 <- "one"
    }()
    
    go func() {
        time.Sleep(2 * time.Second)
        ch2 <- "two"
    }()
    
    for i := 0; i < 2; i++ {
        select {
        case msg1 := <-ch1:
            fmt.Println("Received:", msg1)
        case msg2 := <-ch2:
            fmt.Println("Received:", msg2)
        case <-time.After(3 * time.Second):
            fmt.Println("Timeout")
        }
    }
}
```

**Explanation:**
- `select`: Waits on multiple channel operations
- Cases: Each case is channel operation
- Random: If multiple cases ready, one chosen randomly
- Default: Non-blocking if default case present
- Timeout: Use `time.After()` for timeouts
- Useful for: Multiplexing, timeouts, non-blocking operations

**Key Takeaways:**
- `select` waits on multiple channels
- Random selection if multiple ready
- Use `default` for non-blocking
- Use `time.After()` for timeouts

### Worker Pool Pattern

**What this demonstrates:** Common pattern using channels.

**Code:**
```go
func worker(id int, jobs <-chan int, results chan<- int) {
    for j := range jobs {
        fmt.Printf("Worker %d processing job %d\n", id, j)
        time.Sleep(time.Second)
        results <- j * 2
    }
}

func workerPoolDemo() {
    jobs := make(chan int, 100)
    results := make(chan int, 100)
    
    // Start workers
    for w := 1; w <= 3; w++ {
        go worker(w, jobs, results)
    }
    
    // Send jobs
    for j := 1; j <= 5; j++ {
        jobs <- j
    }
    close(jobs)
    
    // Collect results
    for a := 1; a <= 5; a++ {
        <-results
    }
}
```

**Explanation:**
- Worker pool: Multiple workers process jobs
- Job channel: Send jobs to workers
- Results channel: Workers send results
- Close: Close jobs channel when done
- Range: Workers range over jobs channel
- Pattern: Common concurrent pattern

**Key Takeaways:**
- Worker pool: Common concurrent pattern
- Channels for job distribution and result collection
- Close channel to signal completion

---

## Sync Package

### Overview

The `sync` package provides synchronization primitives: mutexes, wait groups, and more. Use when channels aren't appropriate for synchronization.

### Key Concepts

- **Mutex**: Mutual exclusion lock
- **RWMutex**: Read-write mutex (multiple readers, single writer)
- **WaitGroup**: Wait for goroutines to complete
- **Once**: Execute function exactly once
- **Map**: Thread-safe map

### Mutex

**What this demonstrates:** Using mutexes for synchronization.

**Code:**
```go
import (
    "sync"
    "fmt"
)

func syncDemo() {
    // MUTEX (mutual exclusion)
    var mu sync.Mutex
    counter := 0
    
    increment := func() {
        mu.Lock()
        counter++
        mu.Unlock()
    }
    
    for i := 0; i < 1000; i++ {
        go increment()
    }
    
    time.Sleep(time.Second)
    fmt.Println("Counter:", counter)
}
```

**Explanation:**
- `sync.Mutex`: Mutual exclusion lock
- `Lock()`: Acquire lock (blocks if locked)
- `Unlock()`: Release lock
- Use: Protect shared mutable state
- Prefer channels: Use channels when possible

**Key Takeaways:**
- Mutex: Protect shared state
- `Lock()` and `Unlock()` around critical sections
- Prefer channels when possible

### RWMutex

**What this demonstrates:** Read-write mutex for multiple readers.

**Code:**
```go
func rwMutexDemo() {
    // RWMutex (read-write mutex)
    var rwMu sync.RWMutex
    data := make(map[string]int)
    
    // Multiple readers
    read := func() {
        rwMu.RLock()
        _ = data["key"]
        rwMu.RUnlock()
    }
    
    // Single writer
    write := func() {
        rwMu.Lock()
        data["key"] = 42
        rwMu.Unlock()
    }
}
```

**Explanation:**
- `sync.RWMutex`: Read-write mutex
- `RLock()`/`RUnlock()`: Read lock (multiple readers)
- `Lock()`/`Unlock()`: Write lock (exclusive)
- Use when: Many reads, few writes
- Better than Mutex: When reads are common

**Key Takeaways:**
- RWMutex: Multiple readers, single writer
- `RLock()` for reads, `Lock()` for writes
- Better performance with many reads

### WaitGroup

**What this demonstrates:** Waiting for goroutines to complete.

**Code:**
```go
func waitGroupDemo() {
    // WAITGROUP (wait for goroutines)
    var wg sync.WaitGroup
    
    for i := 0; i < 5; i++ {
        wg.Add(1)  // Increment counter
        go func(id int) {
            defer wg.Done()  // Decrement counter when done
            fmt.Printf("Goroutine %d\n", id)
        }(i)
    }
    
    wg.Wait()  // Wait for counter to reach 0
    fmt.Println("All goroutines finished")
}
```

**Explanation:**
- `sync.WaitGroup`: Wait for goroutines
- `Add(n)`: Increment counter by n
- `Done()`: Decrement counter by 1
- `Wait()`: Block until counter is 0
- Use: Wait for multiple goroutines to complete
- Prefer: Over `time.Sleep()` for synchronization

**Key Takeaways:**
- WaitGroup: Wait for goroutines
- `Add()` increment, `Done()` decrement, `Wait()` blocks
- Better than `time.Sleep()` for synchronization

### Once

**What this demonstrates:** Execute function exactly once.

**Code:**
```go
func onceDemo() {
    // ONCE (run once)
    var once sync.Once
    initialize := func() {
        fmt.Println("Initialized")
    }
    
    for i := 0; i < 10; i++ {
        once.Do(initialize)  // Only runs once
    }
}
```

**Explanation:**
- `sync.Once`: Execute function exactly once
- `Do(func)`: Executes function once (even if called multiple times)
- Thread-safe: Safe to call from multiple goroutines
- Use: One-time initialization

**Key Takeaways:**
- `sync.Once`: Execute once
- Thread-safe one-time initialization

---

## Packages & Modules

### Overview

Go code is organized into packages. Modules (introduced in Go 1.11) manage dependencies and versioning. Understanding packages and modules is essential for Go development.

### Key Concepts

- **Packages**: Collection of related code
- **Modules**: Collection of packages with versioning
- **Import Path**: How to import packages
- **Exported/Unexported**: Capitalization determines visibility
- **Init Function**: Package initialization
- **Module System**: `go.mod` file

### Packages

**What this demonstrates:** Creating and using packages.

**Code:**
```go
// File: mypackage/mypackage.go
package mypackage

// Exported (capitalized)
func PublicFunction() {
    // Public
}

// Unexported (lowercase)
func privateFunction() {
    // Private
}

// File: main.go
package main

import "mymodule/mypackage"

func main() {
    mypackage.PublicFunction()
    // mypackage.privateFunction()  // ERROR: unexported
}
```

**Explanation:**
- Package declaration: `package name` at top of file
- Package name: Usually matches directory name
- Exported: Capitalized names (public)
- Unexported: Lowercase names (private)
- Import: `import "path/to/package"`

**Key Takeaways:**
- Packages: Organize code
- Capitalized = exported (public)
- Lowercase = unexported (private)

### Modules

**What this demonstrates:** Working with modules.

**Commands:**
```bash
# Initialize module
go mod init mymodule

# Add dependency
go get github.com/example/package

# Update dependencies
go mod tidy

# Vendor dependencies
go mod vendor
```

**Explanation:**
- `go.mod`: Module file (defines module path, Go version, dependencies)
- `go.sum`: Checksums for dependencies
- `go mod init`: Initialize new module
- `go get`: Add/update dependency
- `go mod tidy`: Clean up dependencies
- Modules: Enable dependency management and versioning

**Key Takeaways:**
- Modules: Dependency management
- `go mod init` to create module
- `go get` to add dependencies
- `go.mod` tracks dependencies

---

## File I/O

### Overview

Go's standard library provides comprehensive file I/O capabilities. The `os` and `io` packages are commonly used for file operations.

### Key Concepts

- **Opening Files**: `os.Open()`, `os.Create()`
- **Reading**: `ioutil.ReadFile()`, `bufio.Scanner`
- **Writing**: `os.WriteFile()`, `bufio.Writer`
- **File Operations**: Read, write, append
- **Buffered I/O**: `bufio` package for efficiency
- **Paths**: `filepath` package for path operations

### File I/O

**What this demonstrates:** Reading and writing files.

**Code:**
```go
import (
    "os"
    "io/ioutil"
    "bufio"
    "fmt"
)

func fileIODemo() {
    // Write file
    data := []byte("Hello, Go!")
    err := os.WriteFile("data.txt", data, 0644)
    if err != nil {
        fmt.Println("Error:", err)
    }
    
    // Read file
    content, err := os.ReadFile("data.txt")
    if err != nil {
        fmt.Println("Error:", err)
    }
    fmt.Println(string(content))
    
    // Open file for reading
    file, err := os.Open("data.txt")
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    defer file.Close()
    
    // Read with scanner (line by line)
    scanner := bufio.NewScanner(file)
    for scanner.Scan() {
        fmt.Println(scanner.Text())
    }
    
    // Open file for writing
    f, err := os.Create("output.txt")
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    defer f.Close()
    
    // Write to file
    writer := bufio.NewWriter(f)
    fmt.Fprintln(writer, "Line 1")
    fmt.Fprintln(writer, "Line 2")
    writer.Flush()
}
```

**Explanation:**
- `os.WriteFile()`: Write entire file
- `os.ReadFile()`: Read entire file
- `os.Open()`: Open file for reading
- `os.Create()`: Create file for writing
- `bufio.Scanner`: Efficient line-by-line reading
- `bufio.Writer`: Buffered writing
- `defer file.Close()`: Always close files

**Key Takeaways:**
- `os.ReadFile()`/`os.WriteFile()` for simple operations
- `bufio` for efficient I/O
- Always close files (use `defer`)

---

## JSON

### Overview

Go's `encoding/json` package provides JSON encoding and decoding. It's commonly used for APIs and data serialization.

### Key Concepts

- **Marshal**: Convert Go value to JSON
- **Unmarshal**: Convert JSON to Go value
- **Struct Tags**: Control JSON field names
- **Omitempty**: Omit empty values
- **Embedded Structs**: Flatten in JSON

### JSON

**What this demonstrates:** Working with JSON.

**Code:**
```go
import (
    "encoding/json"
    "fmt"
)

type Person struct {
    Name  string `json:"name"`
    Age   int    `json:"age"`
    Email string `json:"email,omitempty"`
}

func jsonDemo() {
    // Marshal (Go to JSON)
    p := Person{Name: "Alice", Age: 25}
    jsonData, err := json.Marshal(p)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    fmt.Println(string(jsonData))  // {"name":"Alice","age":25}
    
    // Unmarshal (JSON to Go)
    jsonStr := `{"name":"Bob","age":30,"email":"bob@example.com"}`
    var p2 Person
    err = json.Unmarshal([]byte(jsonStr), &p2)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    fmt.Printf("%+v\n", p2)
    
    // Pretty print (indent)
    jsonData, _ = json.MarshalIndent(p, "", "  ")
    fmt.Println(string(jsonData))
}
```

**Explanation:**
- `json.Marshal()`: Convert Go value to JSON bytes
- `json.Unmarshal()`: Convert JSON bytes to Go value
- Struct tags: `` `json:"fieldname"` `` control JSON field names
- `omitempty`: Omit field if empty
- Pointer: Unmarshal into pointer

**Key Takeaways:**
- `json.Marshal()` and `json.Unmarshal()`
- Struct tags control JSON representation
- `omitempty` omits empty values

---

## Testing

### Overview

Go has built-in testing support. Tests are in files ending with `_test.go`. The `go test` command runs tests.

### Key Concepts

- **Test Functions**: `func TestName(t *testing.T)`
- **Test Files**: `*_test.go` files
- **Running Tests**: `go test`
- **Benchmarks**: `func BenchmarkName(b *testing.B)`
- **Examples**: Example functions for documentation
- **Table Tests**: Testing multiple cases

### Testing

**What this demonstrates:** Writing and running tests.

**Code:**
```go
// File: math_test.go
package main

import "testing"

func TestAdd(t *testing.T) {
    result := add(2, 3)
    expected := 5
    if result != expected {
        t.Errorf("Expected %d, got %d", expected, result)
    }
}

func TestDivide(t *testing.T) {
    result, err := divide(10, 2)
    if err != nil {
        t.Fatalf("Unexpected error: %v", err)
    }
    if result != 5 {
        t.Errorf("Expected 5, got %f", result)
    }
}

// Table test
func TestMultiply(t *testing.T) {
    tests := []struct {
        a, b, expected int
    }{
        {2, 3, 6},
        {4, 5, 20},
        {0, 100, 0},
    }
    
    for _, tt := range tests {
        result := multiply(tt.a, tt.b)
        if result != tt.expected {
            t.Errorf("multiply(%d, %d) = %d; expected %d", 
                tt.a, tt.b, result, tt.expected)
        }
    }
}
```

**Commands:**
```bash
# Run tests
go test

# Run with verbose output
go test -v

# Run specific test
go test -run TestAdd

# Run benchmarks
go test -bench=.
```

**Explanation:**
- Test functions: `func TestName(t *testing.T)`
- Test file: `*_test.go`
- `testing.T`: Test state and utilities
- `t.Error()`: Log error, continue test
- `t.Fatal()`: Log error, stop test
- Table tests: Test multiple cases in loop
- `go test`: Run tests

**Key Takeaways:**
- Tests in `*_test.go` files
- `func TestName(t *testing.T)`
- `go test` runs tests
- Table tests for multiple cases

---

## Best Practices

### Code Style

- **Formatting**: Always run `go fmt`
- **Naming**: Use short, clear names
- **Package Names**: Short, lowercase
- **Error Handling**: Always check errors
- **Documentation**: Write doc comments

### Concurrency

- **Channels First**: Prefer channels over shared state
- **Avoid Race Conditions**: Use channels or sync primitives
- **Goroutine Leaks**: Ensure goroutines complete
- **Context**: Use `context` package for cancellation

### Performance

- **Profiling**: Use `go tool pprof` for profiling
- **Benchmarks**: Write benchmarks for performance-critical code
- **Avoid Premature Optimization**: Write clear code first
- **Garbage Collection**: Be aware of GC pressure

### Error Handling

- **Always Check**: Check all errors
- **Wrap Errors**: Add context to errors
- **Error Types**: Use custom error types when appropriate
- **Error Messages**: Make error messages helpful

---

## Common Patterns

### Error Wrapping

```go
if err != nil {
    return fmt.Errorf("failed to process: %w", err)
}
```

### Context with Timeout

```go
ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
defer cancel()
```

### Worker Pool

```go
// Jobs channel, results channel, workers
jobs := make(chan Job, 100)
results := make(chan Result, 100)
for w := 0; w < numWorkers; w++ {
    go worker(jobs, results)
}
```

### Singleton Pattern

```go
var (
    instance *MyType
    once     sync.Once
)

func GetInstance() *MyType {
    once.Do(func() {
        instance = &MyType{}
    })
    return instance
}
```

---

## Resources

### Official Documentation

- **Go Documentation**: https://golang.org/doc/
- **Go Language Specification**: https://golang.org/ref/spec
- **Go Standard Library**: https://pkg.go.dev/std

### Learning Resources

- **A Tour of Go**: https://go.dev/tour/
- **Effective Go**: https://go.dev/doc/effective_go
- **Go by Example**: https://gobyexample.com/

### Community

- **Stack Overflow**: Tag: go
- **r/golang**: Reddit community
- **Go Blog**: https://go.dev/blog/

### Tools

- **Go Compiler**: Built-in compiler (go build)
- **go fmt**: Code formatter
- **go test**: Testing framework
- **go mod**: Module management
- **VS Code Go Extension**: IDE support
- **Delve**: Debugger

---

