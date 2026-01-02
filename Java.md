# Java - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Variables & Data Types](#variables--data-types)
4. [Operators](#operators)
5. [Strings](#strings)
6. [Control Flow](#control-flow)
7. [Arrays](#arrays)
8. [Classes & Objects (OOP)](#classes--objects-oop)
9. [Inheritance](#inheritance)
10. [Abstract Classes & Interfaces](#abstract-classes--interfaces)
11. [Collections Framework](#collections-framework)
12. [Generics](#generics)
13. [Exception Handling](#exception-handling)
14. [Lambda Expressions & Functional Programming](#lambda-expressions--functional-programming)
15. [Streams API](#streams-api)
16. [File I/O](#file-io)
17. [Best Practices](#best-practices)
18. [Common Patterns](#common-patterns)
19. [Resources](#resources)

---

## Introduction

### What is Java?

Java is a high-level, object-oriented, platform-independent programming language developed by Sun Microsystems (now Oracle). It was designed with the principle "Write Once, Run Anywhere" (WORA), meaning compiled Java code can run on any platform that has a Java Virtual Machine (JVM).

Java is widely used in enterprise applications, web development (Spring, Jakarta EE), Android development, big data processing (Hadoop, Spark), and scientific computing.

### Why Learn Java?

Java is valuable for:

1. **Platform Independence**: Write once, run anywhere (JVM)
2. **Enterprise Applications**: Large-scale, mission-critical systems
3. **Android Development**: Native Android app development
4. **Rich Ecosystem**: Extensive libraries and frameworks
5. **Strong Type System**: Compile-time error checking
6. **Memory Management**: Automatic garbage collection
7. **Multithreading**: Built-in concurrency support
8. **Career Opportunities**: High demand in enterprise and Android development

### Key Features

- **Object-Oriented**: Everything is an object (except primitives)
- **Platform Independent**: JVM abstracts hardware differences
- **Secure**: Security features built into the language
- **Robust**: Strong typing, exception handling, memory management
- **Multithreaded**: Built-in support for concurrent programming
- **High Performance**: JIT compilation provides near-native speed
- **Rich Standard Library**: Comprehensive API for common tasks

---

## Getting Started

### Installation

1. Download JDK from: https://www.oracle.com/java/technologies/downloads/
2. Set JAVA_HOME environment variable
3. Add Java bin directory to PATH

### Your First Program

**What this demonstrates:** Basic Java program structure and compilation.

**Code:**
```java
// HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
        System.out.println("Welcome to Java!");
    }
}
```

**Compilation and Execution:**
```bash
javac HelloWorld.java  // Compile
java HelloWorld         // Run
```

**Explanation:**
- File name must match public class name (`HelloWorld.java`)
- `public class HelloWorld` - class declaration
- `public static void main(String[] args)` - entry point
  - `public` - accessible from anywhere
  - `static` - belongs to class, not instance
  - `void` - returns nothing
  - `main` - method name
  - `String[] args` - command-line arguments
- `System.out.println()` - prints to console
- One public class per file

**Key Takeaways:**
- File name must match public class name
- `main` method is entry point
- Compile with `javac`, run with `java`

### Package and Imports

**What this demonstrates:** Organizing code with packages and importing classes.

**Code:**
```java
package com.example.myapp;

import java.util.ArrayList;
import java.util.List;
import java.util.*;  // Import all from package

public class MyClass {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        // Use imported classes
    }
}
```

**Explanation:**
- `package` - groups related classes (optional, but recommended)
- `import` - brings classes from other packages
- Package naming: `com.company.app`
- `import java.util.*` - imports all classes from package (not recommended for clarity)

**Key Takeaways:**
- Packages organize code
- `import` statements access classes from other packages
- Use specific imports when possible

---

## Variables & Data Types

### Overview

Java is a statically-typed language, meaning all variables must be declared with a type before use. Java has primitive types (stored directly) and reference types (stored as references to objects).

### Key Concepts

- **Primitive Types**: 8 built-in types (byte, short, int, long, float, double, char, boolean)
- **Reference Types**: Objects, arrays, interfaces
- **Type Safety**: Strong typing prevents type errors
- **Type Conversion**: Widening (implicit) and narrowing (explicit casting)
- **Wrapper Classes**: Object representations of primitives
- **var Keyword**: Type inference (Java 10+)

### Primitive Types

**What this demonstrates:** The eight primitive data types in Java with their ranges and usage.

**Code:**
```java
public class DataTypes {
    public static void main(String[] args) {
        // INTEGER TYPES
        byte b = 127;           // -128 to 127 (8-bit)
        short s = 32767;        // -32,768 to 32,767 (16-bit)
        int i = 2147483647;     // -2.1B to 2.1B (32-bit)
        long l = 9223372036854775807L;  // 64-bit (note L suffix)
        
        // FLOATING-POINT TYPES
        float f = 3.14f;        // 32-bit (note f suffix)
        double d = 3.14159;     // 64-bit (default for decimals)
        
        // CHARACTER
        char c = 'A';           // 16-bit Unicode
        char unicode = '\u0041'; // Unicode 'A'
        
        // BOOLEAN
        boolean flag = true;
        boolean isFalse = false;
    }
}
```

**Explanation:**
- **byte**: 8-bit signed integer (-128 to 127)
- **short**: 16-bit signed integer (-32,768 to 32,767)
- **int**: 32-bit signed integer (most common integer type)
- **long**: 64-bit signed integer (use L suffix for literals)
- **float**: 32-bit IEEE 754 floating point (use f suffix)
- **double**: 64-bit floating point (default for decimal literals)
- **char**: 16-bit Unicode character (single quotes)
- **boolean**: true or false (not numeric like in C/C++)

**Key Takeaways:**
- Java has 8 primitive types
- Use `int` for most integer calculations
- Use `double` for most floating-point calculations
- `char` is 16-bit Unicode (supports international characters)
- `boolean` is a true boolean type (not 0/1)

### Reference Types

**What this demonstrates:** Reference types including String and arrays.

**Code:**
```java
// STRING (immutable reference type)
String name = "Commander";
String message = new String("Hello");

// ARRAYS
int[] numbers = new int[5];           // Array of 5 integers
int[] nums = {1, 2, 3, 4, 5};        // Array literal
String[] names = {"Alice", "Bob", "Charlie"};
```

**Explanation:**
- **String**: Immutable sequence of characters (objects in heap)
- **Arrays**: Fixed-size collection of elements of the same type
- Reference types store references (pointers) to objects in heap
- String literals are pooled (same string literals share memory)
- Arrays are objects in Java

**Key Takeaways:**
- Strings are immutable (cannot be changed after creation)
- Arrays are objects and have length property
- Array indices start at 0
- Arrays must specify size at creation

### Variables and Constants

**What this demonstrates:** Variable declarations, constants, and type inference.

**Code:**
```java
// Local variables (must be initialized)
int count = 0;

// Constants (final)
final double PI = 3.14159;
final String APP_NAME = "MyApp";

// Type inference (Java 10+)
var x = 10;           // Inferred as int
var text = "hello";   // Inferred as String
var list = new ArrayList<String>();  // Inferred type
```

**Explanation:**
- Local variables must be initialized before use
- `final` keyword makes variables constant (cannot be reassigned)
- Constants use UPPER_CASE naming convention
- `var` keyword (Java 10+) infers type from initializer
- `var` can only be used for local variables with initializers

**Key Takeaways:**
- Local variables must be initialized
- Use `final` for constants
- `var` provides type inference (type still enforced at compile-time)
- Constants are typically named in UPPER_CASE

### Type Conversion

**What this demonstrates:** Implicit (widening) and explicit (narrowing) type conversions.

**Code:**
```java
// Implicit conversion (widening - safe)
int intVal = 100;
long longVal = intVal;        // OK: int fits in long
double doubleVal = intVal;    // OK: int fits in double

// Explicit conversion (narrowing - casting required)
double dbl = 9.78;
int integer = (int) dbl;      // 9 (truncates, loses precision)

// Wrapper classes (boxing/unboxing)
Integer objInt = 42;           // Autoboxing: int -> Integer
int primitiveInt = objInt;     // Unboxing: Integer -> int

// String conversion
String str = String.valueOf(42);
int num = Integer.parseInt("123");
double dblNum = Double.parseDouble("3.14");
```

**Explanation:**
- **Widening**: Converting to larger type (automatic, safe)
- **Narrowing**: Converting to smaller type (requires cast, may lose data)
- **Autoboxing**: Automatic conversion between primitives and wrapper classes
- **Unboxing**: Automatic extraction of primitive from wrapper
- String conversion: `parseInt()`, `parseDouble()`, `valueOf()`

**Key Takeaways:**
- Widening conversions are automatic
- Narrowing conversions require explicit cast
- Autoboxing/unboxing happens automatically
- Use wrapper class parse methods for String to number conversion

---

## Operators

### Overview

Java provides a rich set of operators for arithmetic, comparison, logical operations, bit manipulation, and assignment. Understanding operators is fundamental to Java programming.

### Key Concepts

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `%`
- **Increment/Decrement**: `++`, `--` (pre and post)
- **Comparison Operators**: `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical Operators**: `&&`, `||`, `!` (short-circuit)
- **Bitwise Operators**: `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`
- **Assignment Operators**: `=`, `+=`, `-=`, `*=`, `/=`, etc.
- **Ternary Operator**: `condition ? value1 : value2`
- **instanceof**: Type checking operator

### Arithmetic Operators

**What this demonstrates:** Basic arithmetic operations in Java.

**Code:**
```java
int a = 10, b = 3;

int sum = a + b;        // 13 (addition)
int diff = a - b;       // 7 (subtraction)
int prod = a * b;       // 30 (multiplication)
int quot = a / b;       // 3 (integer division)
int rem = a % b;        // 1 (modulo/remainder)
```

**Explanation:**
- `+`: Addition
- `-`: Subtraction
- `*`: Multiplication
- `/`: Division (integer division for integers, floating-point for floats/doubles)
- `%`: Modulo (remainder after division)

**Key Takeaways:**
- Integer division truncates (no decimal part)
- Use floating-point types for decimal results
- Modulo operator useful for cycles and wraparound operations

### Increment and Decrement

**What this demonstrates:** Pre and post increment/decrement operators.

**Code:**
```java
int x = 5;
x++;    // Post-increment: x becomes 6
++x;    // Pre-increment: x becomes 7
x--;    // Post-decrement: x becomes 6
--x;    // Pre-decrement: x becomes 5

int y = x++;  // y = 5, x = 6 (post: assign then increment)
int z = ++x;  // z = 7, x = 7 (pre: increment then assign)
```

**Explanation:**
- **Post-increment** (`x++`): Use current value, then increment
- **Pre-increment** (`++x`): Increment first, then use value
- Same applies to decrement (`--`)

**Key Takeaways:**
- Post: value used first, then modified
- Pre: value modified first, then used
- Avoid in complex expressions for clarity

### Comparison Operators

**What this demonstrates:** Comparison operators for equality and ordering.

**Code:**
```java
int a = 10, b = 3;

boolean equal = a == b;      // false (equality)
boolean notEqual = a != b;   // true (inequality)
boolean greater = a > b;     // true (greater than)
boolean less = a < b;        // false (less than)
boolean greaterEq = a >= b;  // true (greater or equal)
boolean lessEq = a <= b;     // false (less or equal)
```

**Explanation:**
- `==`: Equality (tests if values are equal)
- `!=`: Inequality
- `>`, `<`, `>=`, `<=`: Comparison operators
- Return `boolean` (true or false)
- For objects, `==` compares references, use `.equals()` for content

**Key Takeaways:**
- `==` compares primitives by value, objects by reference
- Use `.equals()` method to compare object content
- Comparison operators return boolean values

### Logical Operators

**What this demonstrates:** Logical operators for boolean logic.

**Code:**
```java
boolean t = true, f = false;

boolean and = t && f;        // false (short-circuit AND)
boolean or = t || f;         // true (short-circuit OR)
boolean not = !t;            // false (NOT)

// Short-circuit behavior
if (obj != null && obj.getValue() > 0) {
    // obj.getValue() only called if obj != null
}
```

**Explanation:**
- `&&`: Logical AND (short-circuit: stops if first is false)
- `||`: Logical OR (short-circuit: stops if first is true)
- `!`: Logical NOT (negation)
- Short-circuit prevents unnecessary evaluation
- `&` and `|` are bitwise AND/OR (evaluate both sides)

**Key Takeaways:**
- `&&` and `||` are short-circuit (efficient, safe)
- Use short-circuit for null checks
- `!` negates boolean value

### Bitwise Operators

**What this demonstrates:** Bitwise operations on integers.

**Code:**
```java
int p = 5, q = 3;            // 0101, 0011 (binary)

int andInt = p & q;          // 0001 = 1 (bitwise AND)
int orInt = p | q;           // 0111 = 7 (bitwise OR)
int xorInt = p ^ q;          // 0110 = 6 (bitwise XOR)
int complement = ~p;         // Bitwise NOT (all bits flipped)
int leftShift = p << 2;      // 10100 = 20 (shift left 2)
int rightShift = p >> 1;     // 0010 = 2 (signed shift right)
int unsignedRight = p >>> 1; // Unsigned shift right
```

**Explanation:**
- `&`: Bitwise AND (both bits must be 1)
- `|`: Bitwise OR (either bit is 1)
- `^`: Bitwise XOR (bits differ)
- `~`: Bitwise complement (flip all bits)
- `<<`: Left shift (multiply by 2^n)
- `>>`: Signed right shift (divide by 2^n, preserve sign)
- `>>>`: Unsigned right shift (shift right, fill with 0)

**Key Takeaways:**
- Bitwise operators work on individual bits
- Left shift multiplies by powers of 2
- Right shift divides by powers of 2
- Useful for flags, masks, and performance optimization

### Assignment Operators

**What this demonstrates:** Compound assignment operators.

**Code:**
```java
int x = 10;
x += 5;   // x = x + 5
x -= 3;   // x = x - 3
x *= 2;   // x = x * 2
x /= 4;   // x = x / 4
x %= 3;   // x = x % 3
x &= 1;   // x = x & 1
x |= 2;   // x = x | 2
x ^= 1;   // x = x ^ 1
x <<= 1;  // x = x << 1
x >>= 1;  // x = x >> 1
```

**Explanation:**
- Compound assignment: `op=` is shorthand for `x = x op value`
- More concise than full assignment
- Works with arithmetic, bitwise, and logical operators

**Key Takeaways:**
- Shorthand for common operations
- More concise and readable
- Same behavior as full assignment

### Ternary Operator

**What this demonstrates:** Conditional expression operator.

**Code:**
```java
int a = 10, b = 3;
int max = (a > b) ? a : b;                    // max = 10
String result = (x > 0) ? "Positive" : "Non-positive";
```

**Explanation:**
- Syntax: `condition ? valueIfTrue : valueIfFalse`
- Returns one of two values based on condition
- Shorthand for if-else statement
- All parts must be compatible types

**Key Takeaways:**
- Compact conditional expressions
- Use when both branches return values
- Can be nested but avoid for readability

### instanceof Operator

**What this demonstrates:** Type checking with instanceof.

**Code:**
```java
String str = "hello";
boolean isString = str instanceof String;  // true

Object obj = new ArrayList<>();
if (obj instanceof ArrayList) {
    // obj is an ArrayList
}
```

**Explanation:**
- `instanceof`: Tests if object is instance of class/interface
- Returns `boolean`
- Useful for type checking before casting
- Pattern matching (Java 16+): `if (obj instanceof String s)`

**Key Takeaways:**
- Check type before casting
- Returns false for null
- Pattern matching simplifies type checking (Java 16+)

---

## Strings

### Overview

Strings in Java are objects that represent sequences of characters. The `String` class is immutable, meaning once created, strings cannot be changed. Java also provides `StringBuilder` and `StringBuffer` for mutable string operations.

### Key Concepts

- **Immutable Strings**: String objects cannot be modified after creation
- **String Pool**: String literals are pooled for memory efficiency
- **String Methods**: Rich set of methods for manipulation
- **StringBuilder**: Mutable string builder (not thread-safe, faster)
- **StringBuffer**: Thread-safe mutable string buffer
- **String Comparison**: `==` vs `.equals()`

### String Creation

**What this demonstrates:** Different ways to create String objects.

**Code:**
```java
// String literal (pooled in string pool)
String str1 = "Hello";
String str3 = "Hello";  // Same reference as str1

// New String object (not pooled)
String str2 = new String("Hello");

System.out.println(str1 == str3);    // true (same reference)
System.out.println(str1 == str2);    // false (different objects)
System.out.println(str1.equals(str2)); // true (same content)
```

**Explanation:**
- String literals are stored in string pool (reused)
- `new String()` creates new object (not pooled)
- `==` compares references (memory addresses)
- `.equals()` compares content (character sequence)

**Key Takeaways:**
- Use `.equals()` for string content comparison
- String literals are automatically pooled
- `new String()` creates separate object

### String Methods

**What this demonstrates:** Common String methods for manipulation and inspection.

**Code:**
```java
String str1 = "Hello";

// Length and character access
int length = str1.length();          // 5
char firstChar = str1.charAt(0);     // 'H'

// Substring
String sub = str1.substring(1);      // "ello"
String sub2 = str1.substring(1, 4);  // "ell" (end exclusive)

// Concatenation
String full = str1 + " World";
String concat = str1.concat(" World");

// Case conversion
String upper = str1.toUpperCase();   // "HELLO"
String lower = str1.toLowerCase();   // "hello"

// Trimming
String padded = "  hello  ";
String trimmed = padded.trim();      // "hello"
String stripped = padded.strip();    // "hello" (Java 11+)

// Replacing
String replaced = str1.replace('l', 'L');  // "HeLLo"
String replacedAll = str1.replaceAll("l+", "L"); // Regex

// Splitting and joining
String csv = "apple,banana,cherry";
String[] fruits = csv.split(",");
String joined = String.join(", ", fruits);  // Java 8+

// Comparison
boolean equals = str1.equals("Hello");
boolean equalsIgnoreCase = str1.equalsIgnoreCase("hello");
int comparison = str1.compareTo("Hello");  // 0 if equal

// Searching
boolean contains = str1.contains("ell");   // true
boolean startsWith = str1.startsWith("He"); // true
boolean endsWith = str1.endsWith("lo");    // true
int indexOf = str1.indexOf('l');           // 2
int lastIndexOf = str1.lastIndexOf('l');   // 3

// Checking
boolean isEmpty = str1.isEmpty();          // false
boolean isBlank = "   ".isBlank();         // true (Java 11+)

// Formatting
String formatted = String.format("Name: %s, Age: %d", "Alice", 25);
```

**Explanation:**
- `length()`: Returns string length
- `charAt(index)`: Get character at position
- `substring(start, end)`: Extract substring (end exclusive)
- `toUpperCase()`, `toLowerCase()`: Case conversion
- `trim()`, `strip()`: Remove whitespace
- `replace()`, `replaceAll()`: Replace characters/patterns
- `split()`: Split into array by delimiter
- `join()`: Join array elements into string
- `equals()`, `compareTo()`: Comparison
- `contains()`, `startsWith()`, `endsWith()`: Pattern matching
- `indexOf()`, `lastIndexOf()`: Find character position
- `format()`: Format string with placeholders

**Key Takeaways:**
- Strings have extensive method library
- Methods return new strings (immutable)
- Use `strip()` for Unicode-aware trimming (Java 11+)
- `replaceAll()` uses regex patterns

### Text Blocks (Java 15+)

**What this demonstrates:** Multi-line string literals with text blocks.

**Code:**
```java
// Text blocks (Java 15+)
String json = """
    {
        "name": "Commander",
        "age": 25
    }
    """;

// Automatically formats with proper indentation
```

**Explanation:**
- Triple quotes (`"""`) for multi-line strings
- Preserves formatting and newlines
- Automatic indentation handling
- Simplifies JSON, SQL, HTML strings

**Key Takeaways:**
- Cleaner multi-line string syntax
- Preserves formatting
- Useful for templates and embedded code

### StringBuilder and StringBuffer

**What this demonstrates:** Mutable string classes for efficient string building.

**Code:**
```java
// StringBuilder (not thread-safe, faster)
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(" ");
sb.append("World");
sb.insert(6, "Beautiful ");
sb.delete(6, 16);
sb.reverse();
String result = sb.toString();

// StringBuffer (thread-safe, slower)
StringBuffer buffer = new StringBuffer("Hello");
buffer.append(" World");
String bufferResult = buffer.toString();
```

**Explanation:**
- **StringBuilder**: Mutable, not thread-safe, faster
- **StringBuffer**: Mutable, thread-safe, slower
- Use for building strings in loops
- More efficient than string concatenation in loops
- `append()`, `insert()`, `delete()`, `reverse()`: Modification methods

**Key Takeaways:**
- Use StringBuilder for efficient string building
- Use StringBuffer when thread safety needed
- Prefer over string concatenation in loops

---

## Control Flow

### Overview

Control flow statements determine the order in which statements are executed. Java provides conditional statements (if/else, switch), loops (for, while, do-while), and control statements (break, continue, return).

### Key Concepts

- **Conditional Statements**: if/else, switch
- **Loops**: for, enhanced for, while, do-while
- **Control Statements**: break, continue, return
- **Switch Expressions**: Modern switch syntax (Java 14+)
- **Labels**: Named break/continue targets

### If-Else Statements

**What this demonstrates:** Conditional execution with if/else.

**Code:**
```java
int age = 25;

if (age < 13) {
    System.out.println("Child");
} else if (age < 20) {
    System.out.println("Teenager");
} else if (age < 65) {
    System.out.println("Adult");
} else {
    System.out.println("Senior");
}

// Ternary operator (inline conditional)
String status = (age >= 18) ? "Adult" : "Minor";
```

**Explanation:**
- `if`: Executes if condition is true
- `else if`: Additional conditions to test
- `else`: Default case if no condition matches
- Conditions must be boolean expressions
- Curly braces optional for single statements (but recommended)

**Key Takeaways:**
- Use if/else for conditional logic
- Ternary operator for simple conditionals
- Always use braces for clarity

### Switch Statements

**What this demonstrates:** Multi-way branching with switch.

**Code:**
```java
int day = 3;

// Traditional switch
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 4:
    case 5:
        System.out.println("Thursday or Friday");
        break;
    default:
        System.out.println("Weekend");
}

// Switch expression (Java 14+)
String dayName = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    case 4, 5 -> "Thursday or Friday";
    default -> "Weekend";
};

// Switch with yield (Java 14+)
String result = switch (day) {
    case 1, 2, 3, 4, 5 -> {
        yield "Weekday";
    }
    default -> {
        yield "Weekend";
    }
};
```

**Explanation:**
- `switch`: Multi-way branch based on value
- `case`: Match specific value
- `break`: Exit switch (prevents fall-through)
- `default`: Match if no case matches
- Fall-through: Cases continue to next without break
- Switch expressions: Return values directly (Java 14+)
- `yield`: Return value from switch block

**Key Takeaways:**
- Use switch for multiple value comparisons
- Don't forget `break` in traditional switch
- Switch expressions are cleaner (Java 14+)
- Use fall-through intentionally

### For Loops

**What this demonstrates:** Iteration with for loops.

**Code:**
```java
// Traditional for loop
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}

// Enhanced for loop (for-each)
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}

// Enhanced for with collections
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
for (String name : names) {
    System.out.println(name);
}

// Multiple variables in for loop
for (int i = 0, j = 10; i < 5; i++, j--) {
    System.out.println(i + " " + j);
}
```

**Explanation:**
- Traditional: `for (init; condition; update)`
- Enhanced: `for (type var : iterable)` - iterate over collections/arrays
- Enhanced for is simpler and less error-prone
- Multiple variables allowed in init and update
- Loop variable scope is limited to loop

**Key Takeaways:**
- Use enhanced for when iterating collections
- Traditional for for index-based iteration
- Enhanced for is safer (no index errors)

### While and Do-While Loops

**What this demonstrates:** Conditional iteration with while loops.

**Code:**
```java
// While loop
int count = 0;
while (count < 5) {
    System.out.println(count);
    count++;
}

// Do-while loop (executes at least once)
int num = 0;
do {
    System.out.println(num);
    num++;
} while (num < 5);

// Infinite loop (with break)
while (true) {
    if (condition) {
        break;
    }
}
```

**Explanation:**
- **while**: Checks condition before iteration
- **do-while**: Executes once, then checks condition
- Use while when iteration count unknown
- Use do-while when you need at least one iteration
- Infinite loops useful with break conditions

**Key Takeaways:**
- Use while for condition-based iteration
- do-while guarantees at least one execution
- Always ensure loop termination

### Break and Continue

**What this demonstrates:** Loop control with break and continue.

**Code:**
```java
// Break: exit loop immediately
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break;  // Exit loop
    }
    System.out.println(i);
}

// Continue: skip to next iteration
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue;  // Skip even numbers
    }
    System.out.println(i);
}

// Labeled break/continue (break outer loop)
outer: for (int i = 0; i < 3; i++) {
    inner: for (int j = 0; j < 3; j++) {
        if (j == 1) {
            break outer;  // Break outer loop
        }
    }
}
```

**Explanation:**
- `break`: Exit loop immediately
- `continue`: Skip to next iteration
- Labels: Name loops for breaking outer loops
- Useful for nested loops

**Key Takeaways:**
- break exits loop completely
- continue skips current iteration
- Use labels for nested loop control

---

## Arrays

### Overview

Arrays are fixed-size collections of elements of the same type. Arrays in Java are objects and provide indexed access to elements. The `Arrays` utility class provides helpful methods for array operations.

### Key Concepts

- **Fixed Size**: Array size determined at creation, cannot change
- **Indexed Access**: Elements accessed by index (0-based)
- **Single Type**: All elements must be same type
- **Object Type**: Arrays are objects (not primitives)
- **Multi-dimensional**: Support for arrays of arrays
- **Arrays Class**: Utility methods for array operations

### Array Declaration and Initialization

**What this demonstrates:** Creating and initializing arrays.

**Code:**
```java
// Array declaration
int[] numbers = new int[5];        // Default values (0 for int)
int[] nums = {1, 2, 3, 4, 5};      // Array literal

// Alternative syntax (not recommended)
int numbers2[] = new int[5];

// Accessing elements
numbers[0] = 10;
numbers[1] = 20;
int first = numbers[0];

// Array length (property, not method)
int length = numbers.length;       // 5

// Default values
int[] ints = new int[5];           // All 0
boolean[] bools = new boolean[5];  // All false
String[] strings = new String[5];  // All null
```

**Explanation:**
- `new type[size]`: Creates array of specified size
- `{val1, val2, ...}`: Array literal initialization
- Index starts at 0, ends at length-1
- `length` is a property (not method call)
- Default values: 0, false, null depending on type

**Key Takeaways:**
- Arrays have fixed size
- Index starts at 0
- Default values depend on element type
- Array literals are convenient for initialization

### Multi-dimensional Arrays

**What this demonstrates:** Arrays with multiple dimensions.

**Code:**
```java
// Two-dimensional array
int[][] matrix = new int[3][3];
int[][] mat = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Access element
int element = mat[1][1];           // 5

// Jagged arrays (different column sizes)
int[][] jagged = new int[3][];
jagged[0] = new int[2];
jagged[1] = new int[3];
jagged[2] = new int[1];

// Three-dimensional array
int[][][] cube = new int[3][3][3];
```

**Explanation:**
- Multi-dimensional arrays are arrays of arrays
- Rectangular: All rows same length
- Jagged: Rows can have different lengths
- Access with multiple indices: `array[row][col]`
- Can extend to any number of dimensions

**Key Takeaways:**
- Multi-dimensional arrays are arrays of arrays
- Jagged arrays allow different row lengths
- Access with multiple index operators

### Iterating Arrays

**What this demonstrates:** Different ways to iterate over arrays.

**Code:**
```java
int[] nums = {1, 2, 3, 4, 5};

// Traditional for loop
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}

// Enhanced for loop (for-each)
for (int num : nums) {
    System.out.println(num);
}

// Multi-dimensional iteration
int[][] matrix = {{1, 2}, {3, 4}};
for (int[] row : matrix) {
    for (int element : row) {
        System.out.print(element + " ");
    }
    System.out.println();
}
```

**Explanation:**
- Traditional for: Index-based access
- Enhanced for: Direct element access (cleaner)
- Enhanced for works with any iterable
- Multi-dimensional: Nested loops

**Key Takeaways:**
- Use enhanced for when index not needed
- Traditional for for index-based operations
- Enhanced for is cleaner and less error-prone

### Arrays Utility Class

**What this demonstrates:** Useful methods from `java.util.Arrays`.

**Code:**
```java
import java.util.Arrays;

int[] arr = {5, 2, 8, 1, 9};

// Sorting
Arrays.sort(arr);                  // [1, 2, 5, 8, 9]

// Binary search (array must be sorted)
int index = Arrays.binarySearch(arr, 5);  // Returns index

// Fill
int[] filled = new int[5];
Arrays.fill(filled, 7);            // [7, 7, 7, 7, 7]

// Copy
int[] copy = Arrays.copyOf(arr, arr.length);
int[] range = Arrays.copyOfRange(arr, 1, 4);  // [2, 5, 8]

// Comparison
boolean equal = Arrays.equals(arr, copy);      // true

// Convert to String
String str = Arrays.toString(arr);  // "[1, 2, 5, 8, 9]"

// Deep toString for multi-dimensional
int[][] matrix = {{1, 2}, {3, 4}};
String matrixStr = Arrays.deepToString(matrix);

// Convert to List
String[] names = {"Alice", "Bob", "Charlie"};
List<String> list = Arrays.asList(names);  // Fixed-size list

// Stream (Java 8+)
int sum = Arrays.stream(nums).sum();
double avg = Arrays.stream(nums).average().orElse(0);
int[] filtered = Arrays.stream(nums)
    .filter(n -> n > 2)
    .toArray();
```

**Explanation:**
- `sort()`: Sorts array in place
- `binarySearch()`: Fast search in sorted array
- `fill()`: Fill all elements with value
- `copyOf()`, `copyOfRange()`: Copy array or portion
- `equals()`: Compare arrays element by element
- `toString()`: Convert to string representation
- `asList()`: Convert to List (fixed-size)
- `stream()`: Convert to Stream (Java 8+)

**Key Takeaways:**
- Arrays class provides many utility methods
- `sort()` modifies array in place
- `binarySearch()` requires sorted array
- `asList()` returns fixed-size list (cannot add/remove)
- `stream()` enables functional operations

---

## Classes & Objects (OOP)

### Overview

Java is an object-oriented language. Classes define blueprints for objects, encapsulating data (fields) and behavior (methods). Understanding classes and objects is fundamental to Java programming.

### Key Concepts

- **Class**: Blueprint for creating objects
- **Object**: Instance of a class
- **Encapsulation**: Data hiding with private fields, public methods
- **Constructors**: Initialize objects
- **Static Members**: Belong to class, not instances
- **this Keyword**: Reference to current object
- **Method Overloading**: Multiple methods with same name, different parameters

### Basic Class Structure

**What this demonstrates:** Complete class with fields, constructors, and methods.

**Code:**
```java
public class Person {
    // FIELDS (instance variables)
    private String name;
    private int age;
    private String email;
    
    // STATIC FIELDS (class variables)
    private static int personCount = 0;
    
    // CONSTANTS
    public static final String SPECIES = "Homo Sapiens";
    
    // CONSTRUCTORS
    public Person() {
        this.name = "Unknown";
        this.age = 0;
        personCount++;
    }
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
        personCount++;
    }
    
    public Person(String name, int age, String email) {
        this(name, age);  // Call other constructor
        this.email = email;
    }
    
    // GETTERS AND SETTERS (encapsulation)
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public int getAge() {
        return age;
    }
    
    public void setAge(int age) {
        if (age >= 0) {
            this.age = age;
        }
    }
    
    // INSTANCE METHODS
    public void introduce() {
        System.out.println("Hi, I'm " + name + ", " + age + " years old.");
    }
    
    public String getInfo() {
        return String.format("%s (%d years old)", name, age);
    }
    
    // STATIC METHODS
    public static int getPersonCount() {
        return personCount;
    }
    
    // toString override
    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
    
    // equals override
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person person = (Person) obj;
        return age == person.age && name.equals(person.name);
    }
    
    // hashCode override
    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
}
```

**Explanation:**
- `private`: Fields accessible only within class (encapsulation)
- `public`: Methods accessible from anywhere
- `static`: Belongs to class (shared by all instances)
- `final`: Constant (cannot be changed)
- `this`: Reference to current object
- `this()`: Call other constructor
- Constructors: Initialize object state
- Getters/Setters: Access private fields safely
- `@Override`: Indicates method override

**Key Takeaways:**
- Encapsulation: private fields, public methods
- Constructors initialize objects
- Static members belong to class
- Override toString(), equals(), hashCode() appropriately

---

## Inheritance

### Overview

Inheritance allows a class to inherit fields and methods from another class. The child class (subclass) extends the parent class (superclass), enabling code reuse and polymorphism.

### Key Concepts

- **extends Keyword**: Inherit from parent class
- **super Keyword**: Access parent class members
- **Method Overriding**: Replace parent method implementation
- **Polymorphism**: Parent reference, child object
- **Single Inheritance**: Java supports single inheritance (one parent)
- **protected**: Accessible to subclasses

### Basic Inheritance

**What this demonstrates:** Parent and child class with inheritance.

**Code:**
```java
// Base class (superclass)
public class Animal {
    protected String name;
    protected int age;
    
    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public void eat() {
        System.out.println(name + " is eating");
    }
    
    public void makeSound() {
        System.out.println("Some generic sound");
    }
}

// Derived class (subclass)
public class Dog extends Animal {
    private String breed;
    
    public Dog(String name, int age, String breed) {
        super(name, age);  // Call parent constructor
        this.breed = breed;
    }
    
    @Override
    public void makeSound() {
        System.out.println(name + " barks: Woof! Woof!");
    }
    
    public void fetch() {
        System.out.println(name + " is fetching the ball");
    }
    
    public void eat() {
        super.eat();  // Call parent method
        System.out.println(name + " is eating dog food");
    }
}
```

**Explanation:**
- `extends`: Inherit from parent class
- `super()`: Call parent constructor (must be first line)
- `super.method()`: Call parent method
- `protected`: Accessible to subclasses
- `@Override`: Override parent method
- Child inherits all non-private members

**Key Takeaways:**
- Use `extends` to inherit from parent
- Call `super()` in constructor
- Override methods with `@Override`
- `protected` for subclass access

### Polymorphism

**What this demonstrates:** Polymorphism with parent references.

**Code:**
```java
// Polymorphism: parent reference, child object
Animal dog = new Dog("Max", 3, "Golden Retriever");
Animal cat = new Cat("Whiskers", 2);

dog.makeSound();  // Calls Dog's version
cat.makeSound();  // Calls Cat's version

// Array of animals (polymorphism)
Animal[] animals = {
    new Dog("Buddy", 4, "Labrador"),
    new Cat("Mittens", 3),
    new Dog("Rex", 5, "German Shepherd")
};

for (Animal animal : animals) {
    animal.makeSound();  // Calls appropriate version
}

// Downcasting (access child-specific methods)
if (dog instanceof Dog) {
    Dog actualDog = (Dog) dog;
    actualDog.fetch();
}

// Pattern matching for instanceof (Java 16+)
if (dog instanceof Dog d) {
    d.fetch();  // Automatically cast
}
```

**Explanation:**
- Polymorphism: Parent reference can point to child objects
- Runtime polymorphism: Correct method called based on actual object type
- Downcasting: Cast parent reference to child type
- `instanceof`: Check object type before casting
- Pattern matching: Automatic casting (Java 16+)

**Key Takeaways:**
- Polymorphism enables flexible code
- Parent references can hold child objects
- Method called based on actual object type
- Use `instanceof` before downcasting

---

## Abstract Classes & Interfaces

### Overview

Abstract classes and interfaces provide contracts for classes. Abstract classes can have both abstract and concrete methods, while interfaces define contracts that implementing classes must follow.

### Key Concepts

- **Abstract Class**: Cannot be instantiated, can have abstract/concrete methods
- **Interface**: Contract for classes, all methods abstract by default (Java 7-)
- **implements Keyword**: Implement interface
- **Multiple Interfaces**: Class can implement multiple interfaces
- **Default Methods**: Interface methods with implementation (Java 8+)
- **Static Methods**: Interface static methods (Java 8+)

### Abstract Classes

**What this demonstrates:** Abstract class with abstract and concrete methods.

**Code:**
```java
// Abstract class (cannot be instantiated)
public abstract class Shape {
    protected String color;
    
    public Shape(String color) {
        this.color = color;
    }
    
    // Abstract methods (must be implemented by subclasses)
    public abstract double area();
    public abstract double perimeter();
    
    // Concrete method
    public void displayColor() {
        System.out.println("Color: " + color);
    }
}

// Implement abstract class
public class Circle extends Shape {
    private double radius;
    
    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }
    
    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public double perimeter() {
        return 2 * Math.PI * radius;
    }
}
```

**Explanation:**
- `abstract class`: Cannot create instances
- `abstract method`: Must be implemented by subclasses
- Abstract classes can have concrete methods
- Use abstract classes for shared code with required implementation

**Key Takeaways:**
- Abstract classes provide partial implementation
- Abstract methods must be implemented
- Cannot instantiate abstract classes

### Interfaces

**What this demonstrates:** Interfaces with default and static methods.

**Code:**
```java
// Interface (contract)
public interface Drawable {
    // Abstract methods (public abstract by default)
    void draw();
    void erase();
    
    // Default method (Java 8+)
    default void display() {
        System.out.println("Displaying shape");
    }
    
    // Static method (Java 8+)
    static void info() {
        System.out.println("Drawable interface");
    }
    
    // Constants (public static final by default)
    int MAX_SIZE = 1000;
}

// Multiple interfaces
public interface Resizable {
    void resize(double factor);
}

// Implement multiple interfaces
public class Square extends Shape implements Drawable, Resizable {
    private double side;
    
    public Square(String color, double side) {
        super(color);
        this.side = side;
    }
    
    @Override
    public double area() {
        return side * side;
    }
    
    @Override
    public void draw() {
        System.out.println("Drawing square");
    }
    
    @Override
    public void resize(double factor) {
        side *= factor;
    }
}

// Functional interface (for lambdas)
@FunctionalInterface
public interface Calculator {
    int calculate(int a, int b);
    
    default void print(int result) {
        System.out.println("Result: " + result);
    }
}
```

**Explanation:**
- Interface: Contract (all methods abstract by default)
- `implements`: Implement interface
- Multiple interfaces: Class can implement multiple
- Default methods: Provide implementation (Java 8+)
- Static methods: Interface-level methods (Java 8+)
- Functional interface: Single abstract method (for lambdas)

**Key Takeaways:**
- Interfaces define contracts
- Implement multiple interfaces
- Default methods provide default implementation
- Functional interfaces for lambdas

---

## Collections Framework

### Overview

The Java Collections Framework provides a unified architecture for representing and manipulating collections. It includes interfaces (List, Set, Map, Queue), implementations (ArrayList, HashSet, HashMap, etc.), and algorithms.

### Key Concepts

- **List**: Ordered collection, allows duplicates (ArrayList, LinkedList)
- **Set**: Unordered collection, no duplicates (HashSet, TreeSet, LinkedHashSet)
- **Map**: Key-value pairs (HashMap, TreeMap, LinkedHashMap)
- **Queue**: FIFO collection (LinkedList, PriorityQueue)
- **Deque**: Double-ended queue (ArrayDeque)
- **Generics**: Type-safe collections

### List Interface

**What this demonstrates:** List implementations (ArrayList, LinkedList).

**Code:**
```java
import java.util.*;

// ArrayList (dynamic array)
List<String> arrayList = new ArrayList<>();
arrayList.add("Apple");
arrayList.add("Banana");
arrayList.add("Cherry");
arrayList.add("Apple");  // Duplicates allowed

arrayList.add(1, "Avocado");  // Insert at index
arrayList.remove("Banana");
arrayList.remove(0);

String first = arrayList.get(0);
arrayList.set(0, "Apricot");

int size = arrayList.size();
boolean contains = arrayList.contains("Cherry");
int index = arrayList.indexOf("Cherry");

// LinkedList (doubly-linked list)
List<Integer> linkedList = new LinkedList<>();
linkedList.add(1);
linkedList.add(2);
linkedList.add(3);

((LinkedList<Integer>) linkedList).addFirst(0);
((LinkedList<Integer>) linkedList).addLast(4);
```

**Explanation:**
- ArrayList: Dynamic array, fast random access, slower insertions/deletions
- LinkedList: Doubly-linked list, fast insertions/deletions, slower random access
- List: Ordered, indexed, allows duplicates
- Methods: add(), remove(), get(), set(), contains(), indexOf()

**Key Takeaways:**
- Use ArrayList for most cases (better performance)
- Use LinkedList for frequent insertions/deletions at ends
- Lists maintain insertion order
- Duplicates allowed

### Set Interface

**What this demonstrates:** Set implementations (HashSet, TreeSet, LinkedHashSet).

**Code:**
```java
// HashSet (hash table, no order)
Set<String> hashSet = new HashSet<>();
hashSet.add("Apple");
hashSet.add("Banana");
hashSet.add("Apple");  // Duplicate ignored

// TreeSet (sorted)
Set<Integer> treeSet = new TreeSet<>();
treeSet.add(5);
treeSet.add(2);
treeSet.add(8);
treeSet.add(1);
// [1, 2, 5, 8] (sorted)

// LinkedHashSet (insertion order)
Set<String> linkedHashSet = new LinkedHashSet<>();
linkedHashSet.add("Zebra");
linkedHashSet.add("Apple");
linkedHashSet.add("Mango");
// [Zebra, Apple, Mango] (insertion order)
```

**Explanation:**
- HashSet: Fast, no order, hash-based
- TreeSet: Sorted (natural order or comparator), slower
- LinkedHashSet: Insertion order, hash-based with linked list
- Set: No duplicates, no index

**Key Takeaways:**
- Use HashSet for general purpose
- Use TreeSet when sorted order needed
- Use LinkedHashSet for insertion order
- No duplicates in Sets

### Map Interface

**What this demonstrates:** Map implementations (HashMap, TreeMap).

**Code:**
```java
// HashMap (no order)
Map<String, Integer> hashMap = new HashMap<>();
hashMap.put("Alice", 25);
hashMap.put("Bob", 30);
hashMap.put("Charlie", 35);

int age = hashMap.get("Alice");
hashMap.put("Alice", 26);  // Update

boolean hasKey = hashMap.containsKey("Bob");
boolean hasValue = hashMap.containsValue(30);

hashMap.remove("Charlie");

// Iterate map
for (Map.Entry<String, Integer> entry : hashMap.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

// TreeMap (sorted by key)
Map<String, Integer> treeMap = new TreeMap<>();
treeMap.put("Charlie", 35);
treeMap.put("Alice", 25);
treeMap.put("Bob", 30);
// {Alice=25, Bob=30, Charlie=35} (sorted)
```

**Explanation:**
- HashMap: Fast, no order, hash-based
- TreeMap: Sorted by keys, slower
- Map: Key-value pairs, no duplicate keys
- Methods: put(), get(), remove(), containsKey(), containsValue()
- Entry iteration: entrySet(), keySet(), values()

**Key Takeaways:**
- Use HashMap for general purpose
- Use TreeMap when sorted keys needed
- Keys must be unique
- Efficient key lookup

### Queue and Deque

**What this demonstrates:** Queue and Deque implementations.

**Code:**
```java
// Queue (FIFO)
Queue<String> queue = new LinkedList<>();
queue.offer("First");   // Add (returns false if fails)
queue.offer("Second");
queue.offer("Third");

String head = queue.peek();    // "First" (don't remove)
String removed = queue.poll(); // "First" (remove)

// PriorityQueue (natural ordering or comparator)
Queue<Integer> priorityQueue = new PriorityQueue<>();
priorityQueue.offer(5);
priorityQueue.offer(2);
priorityQueue.offer(8);
System.out.println(priorityQueue.poll());  // 2 (smallest)

// Deque (double-ended queue)
Deque<String> deque = new ArrayDeque<>();
deque.addFirst("First");
deque.addLast("Last");
deque.removeFirst();
deque.removeLast();

// Stack (LIFO - use Deque instead)
Deque<Integer> stack = new ArrayDeque<>();
stack.push(1);
stack.push(2);
stack.push(3);
int top = stack.pop();  // 3
```

**Explanation:**
- Queue: FIFO (First In First Out)
- PriorityQueue: Priority-based ordering
- Deque: Double-ended (add/remove from both ends)
- Stack: LIFO (Last In First Out) - use Deque
- Methods: offer(), poll(), peek() for Queue
- Methods: push(), pop() for Stack

**Key Takeaways:**
- Queue for FIFO operations
- Deque for double-ended operations
- Use Deque for Stack (LIFO)
- PriorityQueue for priority-based processing

### Collections Utility Class

**What this demonstrates:** Utility methods from Collections class.

**Code:**
```java
List<Integer> nums = new ArrayList<>(Arrays.asList(5, 2, 8, 1, 9));

Collections.sort(nums);              // Sort
Collections.reverse(nums);           // Reverse
Collections.shuffle(nums);           // Shuffle
int max = Collections.max(nums);     // Maximum
int min = Collections.min(nums);     // Minimum
Collections.fill(nums, 0);           // Fill with value
```

**Explanation:**
- Collections class: Static utility methods
- sort(): Sort list
- reverse(): Reverse list order
- shuffle(): Randomize list
- max(), min(): Find max/min element
- fill(): Fill with value

**Key Takeaways:**
- Collections class provides utility methods
- Works with List implementations
- Sort requires comparable elements

---

## Generics

### Overview

Generics enable types (classes and interfaces) to be parameters when defining classes, interfaces, and methods. Generics provide type safety, eliminate casts, and enable more readable code.

### Key Concepts

- **Type Parameters**: `<T>`, `<K, V>` - placeholders for types
- **Generic Classes**: Classes that use type parameters
- **Generic Methods**: Methods with type parameters
- **Bounded Type Parameters**: `<T extends Type>` - restrict types
- **Wildcards**: `?`, `? extends Type`, `? super Type`

### Generic Classes

**What this demonstrates:** Generic class with type parameter.

**Code:**
```java
// Generic class
public class Box<T> {
    private T item;
    
    public void set(T item) {
        this.item = item;
    }
    
    public T get() {
        return item;
    }
}

// Usage
Box<Integer> intBox = new Box<>();
intBox.set(42);
System.out.println(intBox.get());

Box<String> strBox = new Box<>();
strBox.set("Hello");

// Multiple type parameters
public class Pair<K, V> {
    private K key;
    private V value;
    
    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }
    
    public K getKey() { return key; }
    public V getValue() { return value; }
}

Pair<String, Integer> pair = new Pair<>("Age", 25);
```

**Explanation:**
- `<T>`: Type parameter (placeholder)
- Generic classes: Type-safe container classes
- Type safety: Compile-time type checking
- No casting: Type known at compile time
- Multiple parameters: `<K, V>` for multiple types

**Key Takeaways:**
- Generics provide type safety
- Eliminate need for casting
- Type checked at compile time
- Use angle brackets for type parameters

### Generic Methods

**What this demonstrates:** Generic methods with type parameters.

**Code:**
```java
public class GenericMethods {
    public static <T> void printArray(T[] array) {
        for (T element : array) {
            System.out.print(element + " ");
        }
        System.out.println();
    }
    
    public static <T extends Comparable<T>> T maximum(T a, T b, T c) {
        T max = a;
        if (b.compareTo(max) > 0) max = b;
        if (c.compareTo(max) > 0) max = c;
        return max;
    }
}

// Usage
Integer[] intArray = {1, 2, 3, 4, 5};
String[] strArray = {"A", "B", "C"};

GenericMethods.printArray(intArray);
GenericMethods.printArray(strArray);

Integer max = GenericMethods.maximum(3, 7, 5);
```

**Explanation:**
- `<T>` before return type: Type parameter
- Bounded type parameter: `<T extends Comparable<T>>`
- Type inference: Compiler infers type from arguments
- Works with any type

**Key Takeaways:**
- Generic methods work with any type
- Bounded parameters restrict types
- Type inference simplifies usage

### Bounded Type Parameters

**What this demonstrates:** Restricting type parameters.

**Code:**
```java
// Bounded type parameter
public class NumberBox<T extends Number> {
    private T number;
    
    public void setNumber(T number) {
        this.number = number;
    }
    
    public double doubleValue() {
        return number.doubleValue();
    }
}

// Usage - only Number types allowed
NumberBox<Integer> intBox = new NumberBox<>();
NumberBox<Double> doubleBox = new NumberBox<>();
// NumberBox<String> strBox = new NumberBox<>();  // Error!
```

**Explanation:**
- `extends`: Upper bound (T must be subclass of Number)
- Restricts type parameter to specific types
- Enables access to bounded type methods
- Multiple bounds: `<T extends A & B>`

**Key Takeaways:**
- Bounded parameters restrict types
- `extends` for upper bounds
- Enables type-safe operations

### Wildcards

**What this demonstrates:** Wildcard types for flexibility.

**Code:**
```java
// Upper bounded wildcard (? extends Type)
public static double sum(List<? extends Number> list) {
    double sum = 0.0;
    for (Number num : list) {
        sum += num.doubleValue();
    }
    return sum;
}

// Lower bounded wildcard (? super Type)
public static void addNumbers(List<? super Integer> list) {
    for (int i = 1; i <= 5; i++) {
        list.add(i);
    }
}

// Unbounded wildcard (?)
public static void printList(List<?> list) {
    for (Object elem : list) {
        System.out.print(elem + " ");
    }
}

// Usage
List<Integer> intList = Arrays.asList(1, 2, 3);
List<Double> doubleList = Arrays.asList(1.5, 2.5, 3.5);

System.out.println("Sum: " + sum(intList));
System.out.println("Sum: " + sum(doubleList));
```

**Explanation:**
- `? extends Type`: Upper bound (read-only flexibility)
- `? super Type`: Lower bound (write flexibility)
- `?`: Unbounded (any type)
- Wildcards: Use when exact type doesn't matter

**Key Takeaways:**
- Wildcards provide flexibility
- `? extends` for reading from collection
- `? super` for writing to collection
- `?` for when type doesn't matter

---

## Exception Handling

### Overview

Exception handling allows programs to handle errors and exceptional situations gracefully. Java provides try-catch blocks, finally blocks, and throw/throws keywords for exception management.

### Key Concepts

- **Try-Catch**: Handle exceptions
- **Finally**: Always executes (cleanup code)
- **Try-With-Resources**: Automatic resource management (Java 7+)
- **Throw**: Throw exception
- **Throws**: Declare exception in method signature
- **Checked vs Unchecked**: Compile-time vs runtime exceptions

### Try-Catch Blocks

**What this demonstrates:** Basic exception handling.

**Code:**
```java
// TRY-CATCH
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Error: " + e.getMessage());
}

// MULTIPLE CATCH BLOCKS
try {
    String str = null;
    System.out.println(str.length());
} catch (NullPointerException e) {
    System.out.println("Null pointer: " + e.getMessage());
} catch (Exception e) {
    System.out.println("General exception: " + e.getMessage());
}

// MULTI-CATCH (Java 7+)
try {
    // Some code
} catch (NullPointerException | ArithmeticException e) {
    System.out.println("Error: " + e);
}
```

**Explanation:**
- try: Code that may throw exception
- catch: Handle specific exception type
- Multiple catch: Handle different exception types
- Multi-catch: Handle multiple types in one block
- Order matters: More specific first

**Key Takeaways:**
- Use try-catch to handle exceptions
- Catch specific exceptions first
- Multi-catch for related exceptions

### Try-Catch-Finally

**What this demonstrates:** Finally block for cleanup.

**Code:**
```java
// TRY-CATCH-FINALLY
try {
    System.out.println("Try block");
} catch (Exception e) {
    System.out.println("Catch block");
} finally {
    System.out.println("Finally always executes");
}
```

**Explanation:**
- finally: Always executes (even if exception thrown)
- Use for cleanup: Close files, release resources
- Guaranteed execution

**Key Takeaways:**
- finally always executes
- Use for cleanup code
- Guaranteed execution

### Try-With-Resources

**What this demonstrates:** Automatic resource management.

**Code:**
```java
// TRY-WITH-RESOURCES (Java 7+)
try (FileReader fr = new FileReader("test.txt");
     BufferedReader br = new BufferedReader(fr)) {
    String line = br.readLine();
} catch (IOException e) {
    System.out.println("IO Error: " + e.getMessage());
}
// Resources automatically closed

// Multiple resources
try (FileInputStream fis = new FileInputStream("input.txt");
     FileOutputStream fos = new FileOutputStream("output.txt")) {
    // Use resources
} catch (IOException e) {
    e.printStackTrace();
}
```

**Explanation:**
- try-with-resources: Automatic resource management
- Resources must implement AutoCloseable
- Resources closed automatically (in reverse order)
- Cleaner than manual close() in finally

**Key Takeaways:**
- Use try-with-resources for resource management
- Automatic cleanup
- Cleaner code than manual close()

### Throwing Exceptions

**What this demonstrates:** Throwing and declaring exceptions.

**Code:**
```java
// Method that throws exception
public static void validateAge(int age) throws InvalidAgeException {
    if (age < 18) {
        throw new InvalidAgeException("Age must be 18 or older");
    }
}

// Custom exception
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

// Usage
try {
    validateAge(15);
} catch (InvalidAgeException e) {
    System.out.println(e.getMessage());
}
```

**Explanation:**
- throw: Throw exception explicitly
- throws: Declare exception in method signature
- Custom exceptions: Extend Exception or RuntimeException
- Checked exceptions: Must be declared or handled
- Unchecked exceptions: RuntimeException subclasses

**Key Takeaways:**
- Use throw to throw exceptions
- Use throws to declare exceptions
- Create custom exceptions when needed
- Checked vs unchecked exceptions

### Common Exceptions

**Common Exception Types:**

- **ArithmeticException**: Division by zero
- **NullPointerException**: Null reference access
- **ArrayIndexOutOfBoundsException**: Invalid array index
- **NumberFormatException**: Invalid number format
- **IllegalArgumentException**: Invalid argument
- **IOException**: I/O operation failed
- **ClassNotFoundException**: Class not found
- **IndexOutOfBoundsException**: Index out of bounds
- **UnsupportedOperationException**: Operation not supported

---

## Lambda Expressions & Functional Programming

### Overview

Lambda expressions (Java 8+) provide a way to represent anonymous functions. They enable functional programming style and work with functional interfaces. Java provides built-in functional interfaces for common operations.

### Key Concepts

- **Lambda Syntax**: `(parameters) -> expression` or `(parameters) -> { statements; }`
- **Functional Interface**: Interface with single abstract method
- **Method References**: Shorthand for lambda expressions
- **Built-in Functional Interfaces**: Predicate, Function, Consumer, Supplier, etc.
- **Closure**: Lambda can access variables from enclosing scope

### Lambda Syntax

**What this demonstrates:** Basic lambda expressions.

**Code:**
```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);
}

// Lambda expressions
Calculator add = (a, b) -> a + b;
Calculator multiply = (a, b) -> a * b;
Calculator subtract = (a, b) -> a - b;

// With body
Calculator complex = (a, b) -> {
    int result = a + b;
    return result * 2;
};

System.out.println("Add: " + add.calculate(5, 3));
System.out.println("Multiply: " + multiply.calculate(5, 3));
```

**Explanation:**
- `(parameters) -> expression`: Single expression
- `(parameters) -> { statements; }`: Multiple statements
- Type inference: Types inferred from context
- Functional interface: Required (single abstract method)

**Key Takeaways:**
- Lambda: Anonymous function
- Functional interface required
- Type inference from context
- Cleaner than anonymous classes

### Built-in Functional Interfaces

**What this demonstrates:** Common functional interfaces.

**Code:**
```java
import java.util.function.*;

// Predicate<T> - takes T, returns boolean
Predicate<Integer> isEven = n -> n % 2 == 0;
System.out.println("Is 4 even? " + isEven.test(4));

// Function<T, R> - takes T, returns R
Function<String, Integer> stringLength = s -> s.length();
System.out.println("Length: " + stringLength.apply("Hello"));

// Consumer<T> - takes T, returns void
Consumer<String> printer = s -> System.out.println(s);
printer.accept("Hello, Lambda!");

// Supplier<T> - takes nothing, returns T
Supplier<Double> randomSupplier = () -> Math.random();
System.out.println("Random: " + randomSupplier.get());

// BiFunction<T, U, R> - takes T and U, returns R
BiFunction<Integer, Integer, Integer> adder = (a, b) -> a + b;
System.out.println("Sum: " + adder.apply(10, 20));

// UnaryOperator<T> - Function<T, T>
UnaryOperator<Integer> square = x -> x * x;
System.out.println("Square: " + square.apply(5));

// BinaryOperator<T> - BiFunction<T, T, T>
BinaryOperator<Integer> max = (a, b) -> a > b ? a : b;
System.out.println("Max: " + max.apply(10, 20));
```

**Explanation:**
- Predicate: Boolean function
- Function: Transform one type to another
- Consumer: Perform action (no return)
- Supplier: Provide value (no input)
- BiFunction: Two inputs, one output
- Operators: Special functions (same input/output types)

**Key Takeaways:**
- Built-in functional interfaces for common operations
- Predicate for conditions
- Function for transformations
- Consumer for side effects

### Method References

**What this demonstrates:** Method references as lambda shorthand.

**Code:**
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Static method reference
Function<String, Integer> parser = Integer::parseInt;

// Instance method reference (bound)
String str = "Hello";
Supplier<Integer> lengthSupplier = str::length;

// Instance method reference (unbound)
Function<String, Integer> length = String::length;

// Constructor reference
Supplier<List<String>> listSupplier = ArrayList::new;
List<String> list = listSupplier.get();

// forEach with method reference
names.forEach(System.out::println);
names.forEach(String::toUpperCase);
```

**Explanation:**
- `Class::staticMethod`: Static method reference
- `instance::method`: Bound instance method
- `Class::instanceMethod`: Unbound instance method
- `Class::new`: Constructor reference
- Shorthand for lambda: `s -> System.out.println(s)` = `System.out::println`

**Key Takeaways:**
- Method references: Shorthand for lambdas
- Cleaner syntax when method already exists
- Four types: static, bound, unbound, constructor

---

## Streams API

### Overview

The Streams API (Java 8+) enables functional-style operations on collections. Streams provide a declarative way to process data with operations like filter, map, reduce, and collect.

### Key Concepts

- **Stream**: Sequence of elements supporting functional operations
- **Intermediate Operations**: Return stream (filter, map, sorted, etc.)
- **Terminal Operations**: Return result (collect, reduce, forEach, etc.)
- **Lazy Evaluation**: Intermediate operations are lazy
- **Parallel Streams**: Parallel processing

### Creating Streams

**What this demonstrates:** Different ways to create streams.

**Code:**
```java
import java.util.stream.*;

List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// From collection
Stream<Integer> stream1 = numbers.stream();

// From array
Stream<Integer> stream2 = Stream.of(1, 2, 3, 4, 5);

// Infinite streams
Stream<Integer> stream3 = Stream.iterate(0, n -> n + 2).limit(10);
Stream<Double> stream4 = Stream.generate(Math::random).limit(5);

// From array
int[] arr = {1, 2, 3, 4, 5};
IntStream intStream = Arrays.stream(arr);
```

**Explanation:**
- `stream()`: Create from collection
- `Stream.of()`: Create from values
- `Stream.iterate()`: Infinite stream from seed and function
- `Stream.generate()`: Infinite stream from supplier
- `Arrays.stream()`: Create from array

**Key Takeaways:**
- Multiple ways to create streams
- Streams from collections, arrays, generators
- Infinite streams with limit()

### Intermediate Operations

**What this demonstrates:** Common intermediate operations.

**Code:**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

// filter
List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());

// map
List<Integer> squared = numbers.stream()
    .map(n -> n * n)
    .collect(Collectors.toList());

// flatMap
List<List<Integer>> nested = Arrays.asList(
    Arrays.asList(1, 2),
    Arrays.asList(3, 4)
);
List<Integer> flattened = nested.stream()
    .flatMap(List::stream)
    .collect(Collectors.toList());

// distinct
List<Integer> unique = Arrays.asList(1, 2, 2, 3, 3, 4)
    .stream()
    .distinct()
    .collect(Collectors.toList());

// sorted
List<Integer> sorted = numbers.stream()
    .sorted()
    .collect(Collectors.toList());

// limit and skip
List<Integer> limited = numbers.stream()
    .limit(5)
    .collect(Collectors.toList());

List<Integer> skipped = numbers.stream()
    .skip(5)
    .collect(Collectors.toList());
```

**Explanation:**
- filter: Select elements matching predicate
- map: Transform each element
- flatMap: Flatten nested structures
- distinct: Remove duplicates
- sorted: Sort elements
- limit: Limit number of elements
- skip: Skip first N elements
- Intermediate: Return stream (lazy)

**Key Takeaways:**
- Intermediate operations return stream
- Lazy evaluation (executed on terminal operation)
- Chain multiple operations
- filter, map most common

### Terminal Operations

**What this demonstrates:** Terminal operations that produce results.

**Code:**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// forEach
numbers.stream().forEach(System.out::println);

// collect
List<Integer> list = numbers.stream().collect(Collectors.toList());
Set<Integer> set = numbers.stream().collect(Collectors.toSet());

// toArray
Integer[] array = numbers.stream().toArray(Integer[]::new);

// reduce
int sum = numbers.stream().reduce(0, (a, b) -> a + b);
int product = numbers.stream().reduce(1, (a, b) -> a * b);
Optional<Integer> max = numbers.stream().reduce(Integer::max);

// count
long count = numbers.stream().count();

// anyMatch, allMatch, noneMatch
boolean hasEven = numbers.stream().anyMatch(n -> n % 2 == 0);
boolean allPositive = numbers.stream().allMatch(n -> n > 0);
boolean noneNegative = numbers.stream().noneMatch(n -> n < 0);

// findFirst, findAny
Optional<Integer> first = numbers.stream().findFirst();
Optional<Integer> any = numbers.stream().findAny();

// min, max
Optional<Integer> min = numbers.stream().min(Integer::compareTo);
Optional<Integer> maximum = numbers.stream().max(Integer::compareTo);
```

**Explanation:**
- Terminal operations: Produce result (not stream)
- collect: Collect into collection
- reduce: Reduce to single value
- forEach: Perform action on each element
- Matching: anyMatch, allMatch, noneMatch
- Finding: findFirst, findAny
- Aggregation: min, max, count

**Key Takeaways:**
- Terminal operations produce results
- Stream consumed after terminal operation
- collect most common terminal operation
- reduce for aggregation

### Complex Stream Operations

**What this demonstrates:** Combining multiple operations.

**Code:**
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 35),
    new Person("David", 28)
);

// Filter, map, sort, collect
List<String> names = people.stream()
    .filter(p -> p.getAge() > 25)
    .map(Person::getName)
    .sorted()
    .collect(Collectors.toList());

// Grouping
Map<Integer, List<Person>> byAge = people.stream()
    .collect(Collectors.groupingBy(Person::getAge));

// Partitioning
Map<Boolean, List<Person>> partition = people.stream()
    .collect(Collectors.partitioningBy(p -> p.getAge() > 30));

// Statistics
IntSummaryStatistics stats = people.stream()
    .mapToInt(Person::getAge)
    .summaryStatistics();

System.out.println("Average: " + stats.getAverage());
System.out.println("Max: " + stats.getMax());

// Parallel streams
List<Integer> parallelResult = numbers.parallelStream()
    .map(n -> n * 2)
    .collect(Collectors.toList());
```

**Explanation:**
- Complex operations: Chain multiple intermediate operations
- Grouping: Group by key
- Partitioning: Partition by predicate
- Statistics: Summary statistics (sum, average, min, max, count)
- Parallel streams: Parallel processing for large datasets

**Key Takeaways:**
- Chain operations for complex processing
- Grouping/partitioning for data organization
- Statistics for aggregations
- Parallel streams for performance

---

## File I/O

### Overview

Java provides multiple ways to handle file input and output. Traditional I/O uses streams, while NIO.2 (Java 7+) provides more modern file operations with Path and Files classes.

### Key Concepts

- **Streams**: Character streams (Reader/Writer), byte streams (InputStream/OutputStream)
- **Buffered I/O**: Buffered streams for performance
- **NIO.2**: Modern file operations (Path, Files)
- **Try-With-Resources**: Automatic resource management
- **File Operations**: Create, read, write, delete files and directories

### Writing Files

**What this demonstrates:** Writing to files.

**Code:**
```java
import java.io.*;

// WRITE FILE (traditional)
try {
    FileWriter writer = new FileWriter("output.txt");
    writer.write("Hello, Java!\n");
    writer.write("Line 2\n");
    writer.close();
} catch (IOException e) {
    e.printStackTrace();
}

// WRITE FILE (try-with-resources)
try (FileWriter writer = new FileWriter("output.txt")) {
    writer.write("Hello, World!\n");
} catch (IOException e) {
    e.printStackTrace();
}

// WRITE FILE (BufferedWriter)
try (BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {
    writer.write("Line 1");
    writer.newLine();
    writer.write("Line 2");
} catch (IOException e) {
    e.printStackTrace();
}
```

**Explanation:**
- FileWriter: Character stream for writing
- BufferedWriter: Buffered writing (better performance)
- Try-with-resources: Automatic close
- newLine(): Platform-independent line separator

**Key Takeaways:**
- Use try-with-resources for automatic cleanup
- BufferedWriter for better performance
- FileWriter for text files

### Reading Files

**What this demonstrates:** Reading from files.

**Code:**
```java
// READ FILE (traditional)
try {
    FileReader reader = new FileReader("output.txt");
    int character;
    while ((character = reader.read()) != -1) {
        System.out.print((char) character);
    }
    reader.close();
} catch (IOException e) {
    e.printStackTrace();
}

// READ FILE (BufferedReader)
try (BufferedReader reader = new BufferedReader(new FileReader("output.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

**Explanation:**
- FileReader: Character stream for reading
- BufferedReader: Buffered reading (better performance)
- readLine(): Read entire line
- -1 or null: End of file

**Key Takeaways:**
- Use BufferedReader for line-by-line reading
- readLine() for reading lines
- Check for null (end of file)

### NIO.2 File Operations

**What this demonstrates:** Modern file operations with NIO.2.

**Code:**
```java
import java.nio.file.*;

// Write file
try {
    Path path = Paths.get("output.txt");
    String content = "Hello from NIO!";
    Files.write(path, content.getBytes());
} catch (IOException e) {
    e.printStackTrace();
}

// Read file
try {
    Path path = Paths.get("output.txt");
    List<String> lines = Files.readAllLines(path);
    lines.forEach(System.out::println);
} catch (IOException e) {
    e.printStackTrace();
}

// Read as stream
try {
    Files.lines(Paths.get("output.txt"))
        .forEach(System.out::println);
} catch (IOException e) {
    e.printStackTrace();
}
```

**Explanation:**
- Path: Modern path representation
- Files: Utility class for file operations
- write(): Write bytes or lines
- readAllLines(): Read all lines into list
- lines(): Return stream of lines

**Key Takeaways:**
- NIO.2: Modern file API
- Path and Files classes
- Stream-based operations
- More powerful than traditional I/O

### File Operations

**What this demonstrates:** File and directory operations.

**Code:**
```java
import java.io.File;

// Check if exists
File file = new File("output.txt");
boolean exists = file.exists();

// Create file
try {
    file.createNewFile();
} catch (IOException e) {
    e.printStackTrace();
}

// Delete file
file.delete();

// File info
String name = file.getName();
String path = file.getAbsolutePath();
long size = file.length();
boolean isFile = file.isFile();
boolean isDirectory = file.isDirectory();

// List directory
File dir = new File(".");
String[] files = dir.list();
File[] fileList = dir.listFiles();

// Create directory
File newDir = new File("mydir");
newDir.mkdir();
newDir.mkdirs();  // Create parent directories
```

**Explanation:**
- File class: Represents file or directory
- exists(): Check if file exists
- createNewFile(): Create file
- delete(): Delete file
- listFiles(): List directory contents
- mkdir(), mkdirs(): Create directories

**Key Takeaways:**
- File class for file operations
- Check existence before operations
- mkdirs() creates parent directories

---

## Best Practices

### Code Style

- **Naming Conventions**: camelCase for variables/methods, PascalCase for classes
- **Meaningful Names**: Use descriptive variable and method names
- **Keep Methods Small**: Single responsibility principle
- **Use Braces**: Always use braces for if/for/while (even single statements)
- **Indentation**: Consistent indentation (4 spaces recommended)

### Object-Oriented Design

- **Encapsulation**: Use private fields, public methods
- **Favor Composition Over Inheritance**: Prefer composition when possible
- **Program to Interfaces**: Use interface types, not concrete classes
- **SOLID Principles**: Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion
- **DRY (Don't Repeat Yourself)**: Avoid code duplication

### Exception Handling

- **Use Specific Exceptions**: Catch specific exception types first
- **Try-With-Resources**: Always use for resource management
- **Don't Swallow Exceptions**: Log or handle appropriately
- **Document Exceptions**: Use @throws in Javadoc
- **Custom Exceptions**: Create when standard exceptions don't fit

### Collections and Generics

- **Use Generics**: Always use generics for type safety
- **Choose Right Collection**: ArrayList for most cases, HashSet for uniqueness, HashMap for key-value
- **Use Enhanced For**: Prefer enhanced for loops when index not needed
- **Streams for Complex Operations**: Use streams for filtering, mapping, reducing

### Performance

- **StringBuilder for String Building**: Use StringBuilder in loops
- **ArrayList vs LinkedList**: ArrayList for most cases (better performance)
- **HashMap Initial Capacity**: Specify initial capacity for large maps
- **Parallel Streams**: Use for large datasets only
- **Avoid Premature Optimization**: Profile first, optimize second

### Modern Java Features

- **Use Lambda Expressions**: Cleaner code for functional interfaces
- **Use Streams API**: Declarative data processing
- **Use Optional**: Instead of null checks where appropriate
- **Use Try-With-Resources**: Automatic resource management
- **Use var Keyword**: Type inference where it improves readability (Java 10+)

---

## Common Patterns

### Singleton Pattern

**Code:**
```java
public class Singleton {
    private static Singleton instance;
    
    private Singleton() {}
    
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

// Thread-safe version
public class ThreadSafeSingleton {
    private static volatile ThreadSafeSingleton instance;
    
    private ThreadSafeSingleton() {}
    
    public static ThreadSafeSingleton getInstance() {
        if (instance == null) {
            synchronized (ThreadSafeSingleton.class) {
                if (instance == null) {
                    instance = new ThreadSafeSingleton();
                }
            }
        }
        return instance;
    }
}
```

### Builder Pattern

**Code:**
```java
public class Person {
    private String name;
    private int age;
    private String email;
    
    private Person(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
        this.email = builder.email;
    }
    
    public static class Builder {
        private String name;
        private int age;
        private String email;
        
        public Builder name(String name) {
            this.name = name;
            return this;
        }
        
        public Builder age(int age) {
            this.age = age;
            return this;
        }
        
        public Builder email(String email) {
            this.email = email;
            return this;
        }
        
        public Person build() {
            return new Person(this);
        }
    }
}

// Usage
Person person = new Person.Builder()
    .name("Alice")
    .age(25)
    .email("alice@example.com")
    .build();
```

### Factory Pattern

**Code:**
```java
public interface Shape {
    void draw();
}

public class Circle implements Shape {
    public void draw() {
        System.out.println("Drawing circle");
    }
}

public class Rectangle implements Shape {
    public void draw() {
        System.out.println("Drawing rectangle");
    }
}

public class ShapeFactory {
    public Shape createShape(String type) {
        if (type.equalsIgnoreCase("circle")) {
            return new Circle();
        } else if (type.equalsIgnoreCase("rectangle")) {
            return new Rectangle();
        }
        return null;
    }
}
```

---

## Resources

### Official Documentation

- **Oracle Java Documentation**: https://docs.oracle.com/javase/
- **Java API Documentation**: https://docs.oracle.com/javase/8/docs/api/
- **Java Tutorial**: https://docs.oracle.com/javase/tutorial/

### Learning Resources

- **Oracle Java Tutorials**: https://docs.oracle.com/javase/tutorial/
- **Java Point**: https://www.javatpoint.com/java-tutorial
- **Baeldung**: https://www.baeldung.com/

### Community

- **Stack Overflow**: Tag: java
- **r/java**: Reddit community
- **Java User Groups**: Various JUGs worldwide

### Tools

- **JDK**: Java Development Kit
- **Maven**: Build automation
- **Gradle**: Build automation
- **IntelliJ IDEA**: Popular IDE
- **Eclipse**: Popular IDE
- **Spring Framework**: Enterprise framework

---

