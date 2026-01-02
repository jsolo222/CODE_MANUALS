# Ada Programming Language - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Fundamentals & Program Structure](#fundamentals--program-structure)
4. [Data Types & Declarations](#data-types--declarations)
5. [Operators & Expressions](#operators--expressions)
6. [Control Flow](#control-flow)
7. [Subprograms (Procedures & Functions)](#subprograms-procedures--functions)
8. [Packages (Modules)](#packages-modules)
9. [Arrays](#arrays)
10. [Records & Discriminants](#records--discriminants)
11. [Access Types (Pointers)](#access-types-pointers)
12. [Generics](#generics)
13. [Exception Handling](#exception-handling)
14. [Tasking (Concurrency)](#tasking-concurrency)
15. [Real-Time Features](#real-time-features)
16. [Advanced Features (OOP, Contracts)](#advanced-features-oop-contracts)
17. [Pragmas & Attributes](#pragmas--attributes)
18. [Best Practices](#best-practices)
19. [Common Patterns](#common-patterns)
20. [Common Errors & Troubleshooting](#common-errors--troubleshooting)
21. [Resources](#resources)

---

## Introduction

### What is Ada?

Ada is a high-level, strongly-typed, imperative programming language named after Ada Lovelace (often considered the first computer programmer). It was originally designed by Jean Ichbiah's team at CII-Honeywell-Bull under contract to the U.S. Department of Defense (DoD) from 1977 to 1983.

Ada was designed specifically for reliability, safety, maintainability, and efficiency in long-lived systems. It emphasizes compile-time error detection, strong typing, modularity, and explicit specification of requirements. Ada is widely used in safety-critical and mission-critical systems where reliability is paramount.

### Why Learn Ada?

Ada is particularly valuable for:

1. **Safety-Critical Systems**: Used in aerospace (Boeing 777, Airbus A380), defense systems, medical devices, and nuclear power plants
2. **Reliability**: Strong typing and compile-time checks catch many errors before runtime
3. **Maintainability**: Code is self-documenting and designed for long-term maintenance
4. **Real-Time Systems**: Built-in support for real-time programming with tasks, protected objects, and timing
5. **Career Opportunities**: High demand in aerospace, defense, and safety-critical industries
6. **Modern Features**: Ada 2012/2022 includes contracts, expression functions, and modern language features
7. **Formal Verification**: Ada/SPARK subset enables mathematical proof of correctness

### Key Features

- **Strong Typing**: Compile-time type checking prevents many classes of errors
- **Packages**: Modular organization with clear public/private interfaces
- **Generics**: Type-safe code reuse through generics (templates)
- **Exceptions**: Comprehensive exception handling
- **Tasking**: Built-in concurrent programming support
- **Real-Time**: Precise timing and scheduling primitives
- **Contracts**: Design by contract (preconditions, postconditions, invariants) in Ada 2012+
- **Object-Oriented**: Tagged types, inheritance, polymorphism (Ada 95+)
- **Range Checking**: Automatic bounds checking prevents buffer overflows
- **Readability**: Self-documenting code with clear syntax

### Use Cases

Ada is used in:

- **Aerospace**: Boeing 777, Airbus A380, Space Shuttle (some systems), satellites
- **Defense**: Missile systems, radar systems, command and control
- **Transportation**: Railway signaling, air traffic control
- **Medical Devices**: Pacemakers, infusion pumps, diagnostic equipment
- **Nuclear Power**: Reactor control systems
- **Financial Systems**: High-reliability trading systems
- **Any Safety-Critical Application**: Where failure could result in loss of life or significant damage

### Prerequisites

Before learning Ada, you should have:

- **Programming Fundamentals**: Understanding of variables, control flow, functions, data structures
- **Strong Typing Concepts**: Understanding of type safety (helpful but not required)
- **Systems Programming** (helpful): Understanding of memory management, pointers (though Ada handles this differently)
- **Software Engineering** (helpful): Understanding of modular design, interfaces, contracts

Ada is designed to be learnable, but some concepts (like generics, tasking) are more advanced.

---

## Getting Started

### Installation

**Windows:**
1. Download GNAT (GNU Ada Compiler) from https://www.adacore.com/download
2. Or use GNAT Community Edition (free): https://www.adacore.com/community
3. Run installer and follow instructions
4. Verify: Open command prompt, run `gnat --version`

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get update
sudo apt-get install gnat
gnat --version
```

**Linux (Fedora/RHEL):**
```bash
sudo dnf install gcc-gnat
gnat --version
```

**macOS:**
```bash
# Using Homebrew
brew install gcc  # Includes GNAT

# Or download from Adacore
gnat --version
```

### Your First Program

**What this demonstrates:** Simple "Hello, World!" program showing basic Ada structure.

**Code:**
```ada
with Ada.Text_IO;
use Ada.Text_IO;

procedure Hello_World is
begin
   Put_Line("Hello, World!");
end Hello_World;
```

**Explanation:**
- `with Ada.Text_IO;`: Imports the Text_IO package for text input/output
- `use Ada.Text_IO;`: Makes package contents directly accessible (so we can write `Put_Line` instead of `Ada.Text_IO.Put_Line`)
- `procedure Hello_World is`: Declares a procedure named Hello_World. Procedures are the main program units in Ada
- `begin`: Marks the start of executable statements
- `Put_Line(...)`: Outputs a line of text (similar to `printf` or `System.out.println`)
- `end Hello_World;`: Ends the procedure

**To Compile and Run:**
```bash
gnat compile hello_world.adb
./hello_world
# Or compile and run in one step:
gnat make hello_world.adb
./hello_world
```

**Output:**
```
Hello, World!
```

**Key Takeaways:**
- Ada uses packages (modules) for organization
- `with` imports packages, `use` makes their contents directly accessible
- Procedures are the main program units
- Code is organized with `is`, `begin`, and `end`
- File extension is typically `.adb` (Ada Body)

### More Complete Example

**What this demonstrates:** A more complete program showing multiple packages, variable declarations, and different output methods.

**Code:**
```ada
with Ada.Text_IO;
with Ada.Integer_Text_IO;

procedure Complete_Example is
   -- Declarations
   Age : Integer := 25;
   Name : String(1..20) := "Commander           ";
   Pi : constant Float := 3.14159;
begin
   -- Executable statements
   Ada.Text_IO.Put("Name: ");
   Ada.Text_IO.Put_Line(Name);
   
   Ada.Text_IO.Put("Age: ");
   Ada.Integer_Text_IO.Put(Age);
   Ada.Text_IO.New_Line;
   
   Ada.Text_IO.Put("Pi: ");
   Ada.Text_IO.Put(Float'Image(Pi));
   Ada.Text_IO.New_Line;
end Complete_Example;
```

**Explanation:**
- `Ada.Integer_Text_IO`: Package for integer I/O operations
- `Age : Integer := 25;`: Declares an Integer variable with initial value
- `Name : String(1..20)`: Declares a String with fixed bounds (20 characters)
- `Pi : constant Float := 3.14159;`: Declares a constant Float value
- `Float'Image(Pi)`: Attribute function to convert Float to String
- `Ada.Text_IO.Put(...)`: Outputs text without newline
- `Ada.Text_IO.New_Line;`: Outputs a newline character

**Key Takeaways:**
- Variables are declared with type and optional initial value
- Strings have fixed bounds (size must be known at compile time)
- Constants use the `constant` keyword
- Attributes (like `'Image`) provide type information and conversions
- Different packages provide different I/O capabilities

### Development Tools

**Recommended IDEs:**

1. **GNAT Studio** (Adacore)
   - Full-featured IDE specifically for Ada
   - Free with GNAT Community Edition
   - Debugging, refactoring, code completion

2. **GPS (GNAT Programming Studio)**
   - Legacy name for GNAT Studio
   - Still widely used

3. **VS Code**
   - Install Ada extension
   - Basic support for Ada development

4. **Emacs/Vim**
   - ada-mode for Emacs
   - Various plugins available

**Essential Tools:**

- `gnat compile`: Compile Ada source files
- `gnat make`: Compile with automatic dependency resolution
- `gnat bind`: Bind object files
- `gnat link`: Link executable
- `gnatmake`: All-in-one compile/bind/link
- `gnatcheck`: Style checking
- `gnatmetric`: Code metrics

---

## Fundamentals & Program Structure

### Overview

Ada programs are organized into units (procedures, functions, packages). Understanding the basic structure is essential for writing Ada code.

### Key Concepts

- **Procedure**: Main program unit (can also be used as subprograms)
- **Function**: Subprogram that returns a value
- **Package**: Module that groups related declarations
- **with/use**: Import and use packages
- **Declarations**: Variables, constants, types declared before executable code
- **begin/end**: Delimit executable code sections

### Program Structure

**What this demonstrates:** Complete program structure showing declarations and executable code sections.

**Code:**
```ada
with Ada.Text_IO;

procedure Program_Structure is
   -- Variable declarations
   X : Integer := 10;
   Y : Integer := 20;
   Sum : Integer;
   
   -- Constant declarations
   Max_Value : constant Integer := 100;
   
begin
   -- Executable statements
   Sum := X + Y;
   Ada.Text_IO.Put_Line("Sum: " & Integer'Image(Sum));
end Program_Structure;
```

**Explanation:**
- Declarations come after `is` and before `begin`
- Variables: `Name : Type := Initial_Value;` (initial value optional)
- Constants: `Name : constant Type := Value;`
- Executable code goes between `begin` and `end`
- `&` operator: String concatenation
- `Integer'Image`: Converts integer to string for output

**Key Takeaways:**
- Clear separation: declarations → executable code
- All variables must be declared before use
- Type comes after variable name (`Name : Type`)
- Constants use `constant` keyword
- Ada uses `:=` for assignment (not `=`)

---

## Data Types & Declarations

### Overview

Ada has a rich type system with strong typing, user-defined types, and range constraints. Understanding types is crucial for writing correct Ada code.

### Key Concepts

- **Strong Typing**: Types are not automatically converted
- **Type Safety**: Compile-time checking prevents type errors
- **Range Constraints**: Types can have value ranges
- **Type Attributes**: Built-in information about types
- **User-Defined Types**: Create your own types for domain modeling

### Integer Types

**What this demonstrates:** Various integer types including standard, constrained, and modular types.

**Code:**
```ada
procedure Integer_Types_Demo is
   -- Standard integer types
   Age : Integer;                          -- Standard integer
   Count : Natural;                        -- 0 to Integer'Last (non-negative)
   Index : Positive;                       -- 1 to Integer'Last (positive only)
   
   -- Custom integer range
   type Day_Number is range 1..31;
   Day : Day_Number := 15;
   
   type Temperature is range -273..1000;   -- Celsius range
   Room_Temp : Temperature;
   
   -- Modular types (unsigned, wrap-around)
   type Byte is mod 2**8;                  -- 0..255 (wraps around)
   Data : Byte;
   
begin
   -- Type conversions (explicit required)
   Room_Temp := Temperature(Age);          -- Must explicitly convert
   
   -- Range checking is automatic
   Day := 15;                              -- OK (in range 1..31)
   -- Day := 32;                           -- Runtime error: Constraint_Error
   
   -- Attributes provide type information
   Ada.Text_IO.Put_Line("Integer'First: " & Integer'Image(Integer'First));
   Ada.Text_IO.Put_Line("Integer'Last: " & Integer'Image(Integer'Last));
   Ada.Text_IO.Put_Line("Day_Number range: " & 
      Day_Number'Image(Day_Number'First) & ".." & 
      Day_Number'Image(Day_Number'Last));
end Integer_Types_Demo;
```

**Explanation:**
- `Integer`: Standard signed integer (size implementation-defined, typically 32-bit)
- `Natural`: Subtype of Integer from 0 to Integer'Last (non-negative)
- `Positive`: Subtype of Integer from 1 to Integer'Last (positive only)
- `type X is range A..B`: Defines a new integer type with range constraint
- `type X is mod N`: Defines a modular (unsigned, wrap-around) type
- `'First`, `'Last`, `'Image`: Type attributes (first value, last value, string representation)
- Range violations raise `Constraint_Error` at runtime

**Key Takeaways:**
- Use `Natural` for non-negative values
- Use `Positive` for positive values only
- Range constraints prevent invalid values automatically
- Type conversions must be explicit (prevents accidental conversions)
- Attributes provide type information at compile time

### Floating Point Types

**What this demonstrates:** Floating-point types with precision control.

**Code:**
```ada
procedure Float_Types_Demo is
   -- Standard floating point
   Height : Float;                         -- Single precision
   Distance : Long_Float;                  -- Double precision
   
   -- Custom floating point with precision
   type Real is digits 6;                  -- At least 6 decimal digits
   type Precise is digits 15 range -1.0E10..1.0E10;  -- High precision with range
   
   -- Fixed point (exact decimal arithmetic)
   type Money is delta 0.01 range 0.00..1_000_000.00;
   Balance : Money := 1234.56;
   
begin
   Height := 6.0;
   Distance := 3.14159265358979;
   Balance := 999.99;  -- Exact representation
end Float_Types_Demo;
```

**Explanation:**
- `Float`: Single precision (typically 32-bit)
- `Long_Float`: Double precision (typically 64-bit)
- `digits N`: Specifies minimum decimal precision
- `delta X`: Fixed-point type with exact decimal increments
- Fixed-point types: Exact representation for decimal values (good for money)
- Floating-point: Approximate representation, wider range

**Key Takeaways:**
- Use `digits` to specify precision requirements
- Fixed-point (`delta`) for exact decimal arithmetic (money, measurements)
- Floating-point for scientific calculations (wider range, approximate)
- Range constraints work with floating-point types too

### Boolean, Character & String Types

**What this demonstrates:** Boolean, character, and string types.

**Code:**
```ada
procedure Boolean_String_Demo is
   -- BOOLEAN
   Flag : Boolean := True;
   Is_Valid : Boolean := False;
   
   -- CHARACTER & STRING
   Letter : Character := 'A';
   Message : String(1..10) := "Hello Ada!";
   
   -- Variable-length strings (unbounded)
   use Ada.Strings.Unbounded;
   Text : Unbounded_String := To_Unbounded_String("Dynamic text");
   
begin
   -- Boolean operations
   Flag := not Flag;
   Is_Valid := Flag and True;
   
   -- String operations
   Ada.Text_IO.Put_Line(Message);
   Ada.Text_IO.Put_Line(To_String(Text));
end Boolean_String_Demo;
```

**Explanation:**
- `Boolean`: Logical type (True/False)
- `Character`: Single character (8-bit)
- `String(bounds)`: Fixed-length string (array of Character)
- `Unbounded_String`: Variable-length string (from Ada.Strings.Unbounded)
- Strings have fixed bounds (must specify size at declaration)
- Unbounded_String for dynamic strings

**Key Takeaways:**
- Boolean for logical values
- String has fixed size (bounds required)
- Unbounded_String for variable-length strings
- Character = single character

### Enumeration Types

**What this demonstrates:** User-defined enumeration types.

**Code:**
```ada
procedure Enumeration_Demo is
   -- ENUMERATION TYPES
   type Color is (Red, Green, Blue, Yellow);
   type Day_Of_Week is (Monday, Tuesday, Wednesday, Thursday, 
                        Friday, Saturday, Sunday);
   
   Favorite_Color : Color := Blue;
   Today : Day_Of_Week := Monday;
   
begin
   -- Enumeration operations
   if Favorite_Color = Blue then
      Ada.Text_IO.Put_Line("Blue is selected");
   end if;
   
   -- Attributes
   Ada.Text_IO.Put_Line("First color: " & Color'Image(Color'First));
   Ada.Text_IO.Put_Line("Last day: " & Day_Of_Week'Image(Day_Of_Week'Last));
end Enumeration_Demo;
```

**Explanation:**
- `type Name is (value1, value2, ...);` defines enumeration
- Enumeration values are ordered
- `'First`, `'Last`, `'Image` attributes available
- Type-safe (no implicit conversion)
- Useful for domain modeling

**Key Takeaways:**
- Enumeration types for discrete sets of values
- Type-safe (no implicit conversion)
- Attributes: `'First`, `'Last`, `'Image`
- Good for domain modeling

---

## Operators & Expressions

### Overview

Ada provides a comprehensive set of operators for arithmetic, logical, relational operations, and type-specific operations. Understanding operators is fundamental to writing Ada expressions.

### Key Concepts

- **Arithmetic Operators**: +, -, *, /, **, mod, rem
- **Relational Operators**: =, /=, <, >, <=, >=
- **Logical Operators**: and, or, xor, not (with short-circuit variants)
- **Membership Tests**: in, not in
- **Concatenation**: & (for arrays/strings)

### Arithmetic Operators

**What this demonstrates:** Arithmetic operations in Ada.

**Code:**
```ada
procedure Operators_Demo is
   A : Integer := 10;
   B : Integer := 3;
   X : Float := 5.0;
   Y : Float := 2.0;
   
   -- ARITHMETIC OPERATORS
   Sum : Integer := A + B;                 -- 13
   Diff : Integer := A - B;                -- 7
   Prod : Integer := A * B;                -- 30
   Quot : Integer := A / B;                -- 3 (integer division)
   Remain : Integer := A mod B;            -- 1 (modulo)
   Remainder : Integer := A rem B;         -- 1 (remainder)
   Power : Integer := A ** 2;              -- 100 (exponentiation)
   Neg : Integer := -A;                    -- -10
   
   -- Floating point division
   F_Quot : Float := X / Y;                -- 2.5
   
begin
   null;
end Operators_Demo;
```

**Explanation:**
- `+`, `-`, `*` standard arithmetic
- `/` = integer division for Integer types, floating-point division for Float types
- `mod` = modulo (result has sign of divisor)
- `rem` = remainder (result has sign of dividend)
- `**` = exponentiation (A ** 2 = A squared)
- Integer `/` truncates (3, not 3.33...)
- Float `/` gives floating-point result

**Key Takeaways:**
- Integer `/` = integer division (truncates)
- Float `/` = floating-point division
- `mod` vs `rem` differ in sign handling
- `**` for exponentiation
- Type determines operation behavior

### Relational & Logical Operators

**What this demonstrates:** Comparison and logical operations.

**Code:**
```ada
procedure Relational_Logical_Demo is
   A : Integer := 10;
   B : Integer := 3;
   Flag1 : Boolean := True;
   Flag2 : Boolean := False;
   
   -- RELATIONAL OPERATORS
   Equal : Boolean := A = B;               -- False
   Not_Equal : Boolean := A /= B;          -- True (/= is not-equal)
   Less : Boolean := A < B;                -- False
   Greater : Boolean := A > B;             -- True
   Less_Eq : Boolean := A <= B;            -- False
   Greater_Eq : Boolean := A >= B;         -- True
   
   -- LOGICAL OPERATORS (short-circuit evaluation)
   And_Result : Boolean := Flag1 and then Flag2;  -- False (short-circuit)
   Or_Result : Boolean := Flag1 or else Flag2;    -- True (short-circuit)
   Not_Result : Boolean := not Flag1;             -- False
   
   -- Non-short-circuit (both sides always evaluated)
   And_Full : Boolean := Flag1 and Flag2;
   Or_Full : Boolean := Flag1 or Flag2;
   Xor_Result : Boolean := Flag1 xor Flag2;       -- True
   
begin
   null;
end Relational_Logical_Demo;
```

**Explanation:**
- `/=` is "not equal" operator (≠)
- `and then` = short-circuit AND (stops if first is False)
- `or else` = short-circuit OR (stops if first is True)
- `and`, `or` = non-short-circuit (both sides always evaluated)
- `xor` = exclusive OR (True if exactly one is True)
- `not` = logical NOT

**Key Takeaways:**
- `/=` is not-equal operator
- `and then` / `or else` = short-circuit evaluation
- `and` / `or` = always evaluate both sides
- `xor` = exclusive OR
- Short-circuit useful for safety (avoid evaluation errors)

### Membership Tests & Concatenation

**What this demonstrates:** Membership testing and string concatenation.

**Code:**
```ada
procedure Membership_Concat_Demo is
   type Range_Type is range 1..100;
   Value : Integer := 50;
   In_Range : Boolean := Value in Range_Type;    -- True
   Not_In_Range : Boolean := Value not in 1..10; -- True
   
   -- CONCATENATION (for arrays and strings)
   Str1 : String := "Hello";
   Str2 : String := "World";
   Result : String := Str1 & " " & Str2;          -- "Hello World"
   
begin
   null;
end Membership_Concat_Demo;
```

**Explanation:**
- `in` tests if value is in range/type
- `not in` tests if value is NOT in range/type
- `&` operator concatenates arrays/strings
- Membership tests useful for range validation
- Concatenation creates new string/array

**Key Takeaways:**
- `in` / `not in` for membership testing
- `&` for concatenation
- Useful for validation and string building

---

## Control Flow

### Overview

Ada provides standard control flow constructs: IF statements, CASE statements, loops (FOR, WHILE, LOOP), and EXIT statements. Understanding control flow is essential for program logic.

### Key Concepts

- **IF Statements**: Conditional execution (if, elsif, else)
- **CASE Statements**: Multi-way branching (must cover all cases)
- **FOR Loops**: Iteration over discrete ranges
- **WHILE Loops**: Conditional iteration
- **LOOP**: Infinite loop with EXIT
- **EXIT**: Break out of loops

### IF Statements

**What this demonstrates:** Conditional execution with IF.

**Code:**
```ada
procedure Control_Flow_Demo is
   X : Integer := 10;
   
begin
   -- IF STATEMENT
   if X > 0 then
      Ada.Text_IO.Put_Line("Positive");
   elsif X < 0 then
      Ada.Text_IO.Put_Line("Negative");
   else
      Ada.Text_IO.Put_Line("Zero");
   end if;
end Control_Flow_Demo;
```

**Explanation:**
- `if condition then` starts conditional
- `elsif` = else-if (multiple conditions)
- `else` = default case
- `end if` closes IF statement
- Conditions must be Boolean expressions
- All IF statements must be properly closed

**Key Takeaways:**
- `if ... then ... elsif ... else ... end if`
- `elsif` (not "else if")
- Must close with `end if`
- Conditions must be Boolean

### CASE Statements

**What this demonstrates:** Multi-way branching with CASE.

**Code:**
```ada
procedure Case_Demo is
   Day : Integer := 3;
   
begin
   -- CASE STATEMENT (all cases must be covered)
   case Day is
      when 1 =>
         Ada.Text_IO.Put_Line("Monday");
      when 2 =>
         Ada.Text_IO.Put_Line("Tuesday");
      when 3 =>
         Ada.Text_IO.Put_Line("Wednesday");
      when 4..5 =>
         Ada.Text_IO.Put_Line("Thursday or Friday");
      when 6 | 7 =>
         Ada.Text_IO.Put_Line("Weekend");
      when others =>
         Ada.Text_IO.Put_Line("Invalid day");
   end case;
end Case_Demo;
```

**Explanation:**
- `case expression is` starts case statement
- `when value =>` specifies case value
- `when range =>` matches range (4..5)
- `when value1 | value2 =>` matches multiple values (6 | 7)
- `when others =>` default case (covers all remaining values)
- All possible values must be covered (or use `others`)
- `end case` closes CASE statement

**Key Takeaways:**
- All cases must be covered (or use `others`)
- `when range =>` for ranges
- `when val1 | val2 =>` for multiple values
- `others` covers all remaining cases
- Exhaustive coverage enforced by compiler

### FOR Loops

**What this demonstrates:** Iteration with FOR loops.

**Code:**
```ada
procedure For_Loop_Demo is
begin
   -- FOR LOOP (discrete range)
   for I in 1..10 loop
      Ada.Text_IO.Put(Integer'Image(I));
   end loop;
   Ada.Text_IO.New_Line;
   
   -- Reverse iteration
   for I in reverse 1..5 loop
      Ada.Text_IO.Put(Integer'Image(I));
   end loop;
   Ada.Text_IO.New_Line;
end For_Loop_Demo;
```

**Explanation:**
- `for variable in range loop` iterates over range
- Range is inclusive (1..10 includes both 1 and 10)
- Loop variable is local to loop (read-only)
- `reverse` iterates in reverse order
- `end loop` closes FOR loop
- Loop variable type inferred from range

**Key Takeaways:**
- `for var in range loop ... end loop`
- Range is inclusive
- Loop variable is read-only and local
- `reverse` for reverse iteration
- Type-safe iteration

### WHILE Loops & LOOP with EXIT

**What this demonstrates:** Conditional loops and infinite loops.

**Code:**
```ada
procedure While_Loop_Demo is
   Count : Integer;
   
begin
   -- WHILE LOOP
   Count := 1;
   while Count <= 5 loop
      Ada.Text_IO.Put(Integer'Image(Count));
      Count := Count + 1;
   end loop;
   Ada.Text_IO.New_Line;
   
   -- LOOP with EXIT
   Count := 1;
   loop
      Ada.Text_IO.Put(Integer'Image(Count));
      Count := Count + 1;
      exit when Count > 5;
   end loop;
   Ada.Text_IO.New_Line;
   
   -- Named loops and exit
   Outer_Loop:
   for I in 1..3 loop
      Inner_Loop:
      for J in 1..3 loop
         if I = 2 and J = 2 then
            exit Outer_Loop;  -- Exit outer loop
         end if;
         Ada.Text_IO.Put(Integer'Image(I) & "," & Integer'Image(J) & " ");
      end loop Inner_Loop;
   end loop Outer_Loop;
   Ada.Text_IO.New_Line;
end While_Loop_Demo;
```

**Explanation:**
- `while condition loop` continues while condition is True
- `loop ... end loop` is infinite loop
- `exit when condition;` breaks loop when condition is True
- `exit;` (no label) exits innermost loop
- Labels name loops: `Label: loop ... end loop Label;`
- `exit Label;` exits named loop (useful for nested loops)

**Key Takeaways:**
- `while condition loop ... end loop`
- `loop ... end loop` = infinite loop
- `exit when condition;` breaks loop
- Labels enable exiting nested loops
- `exit Label;` exits named loop

---

## Subprograms (Procedures & Functions)

### Overview

Ada provides procedures (subroutines) and functions (return values). Subprograms enable code reuse, modularity, and abstraction. Understanding subprograms is fundamental to Ada programming.

### Key Concepts

- **Procedure**: Subroutine that doesn't return a value
- **Function**: Subprogram that returns a value
- **Parameter Modes**: `in` (read-only), `out` (write-only), `in out` (read-write)
- **Overloading**: Multiple subprograms with same name, different parameters
- **Default Parameters**: Optional parameters with default values
- **Nested Subprograms**: Subprograms defined inside other subprograms

### Procedures

**What this demonstrates:** Procedures (subroutines without return values).

**Code:**
```ada
-- PROCEDURE (no return value)
procedure Swap(X, Y : in out Integer) is
   Temp : Integer;
begin
   Temp := X;
   X := Y;
   Y := Temp;
end Swap;
```

**Explanation:**
- `procedure name(parameters) is ... end name;` declares procedure
- `in out` parameters can be read and modified
- Procedures don't return values (but can modify `out` or `in out` parameters)
- Procedure calls: `Swap(a, b);` (no return value)

**Key Takeaways:**
- Procedures use `procedure ... is ... end`
- `in out` parameters can be modified
- No return value (but can modify parameters)

### Functions

**What this demonstrates:** Functions that return values.

**Code:**
```ada
-- FUNCTION (returns value)
function Square(X : Integer) return Integer is
begin
   return X * X;
end Square;

-- Function with multiple parameters
function Max(A, B : Integer) return Integer is
begin
   if A > B then
      return A;
   else
      return B;
   end if;
end Max;
```

**Explanation:**
- `function name(parameters) return Type is ... end name;` declares function
- `return expression;` returns value from function
- Functions can have multiple `return` statements
- Function calls: `result := Square(5);`
- Function parameters are `in` by default (read-only)

**Key Takeaways:**
- Functions use `function ... return Type`
- `return value;` returns value
- Parameters are `in` by default
- Functions can have multiple return statements

### Parameter Modes

**What this demonstrates:** Parameter modes (`in`, `out`, `in out`).

**Code:**
```ada
procedure Parameter_Modes_Demo is
   procedure Process(
      Input  : in Integer;      -- Cannot be modified
      Output : out Integer;     -- Must be assigned before return
      Both   : in out Integer   -- Can read and modify
   ) is
   begin
      Output := Input * 2;
      Both := Both + Input;
   end Process;
   
   X : Integer := 5;
   Y : Integer;
   Z : Integer := 10;
begin
   Process(X, Y, Z);
   -- X is still 5 (in - not modified)
   -- Y is now 10 (out - assigned in procedure)
   -- Z is now 15 (in out - modified: 10 + 5)
end Parameter_Modes_Demo;
```

**Explanation:**
- `in`: Read-only (default for functions), value cannot be modified
- `out`: Write-only (uninitialized on entry), must be assigned before return
- `in out`: Read-write, can read and modify
- Parameter modes are explicit (enhances clarity and safety)
- `out` parameters are uninitialized (must assign before use)

**Key Takeaways:**
- `in` = read-only (default for functions)
- `out` = write-only (must assign)
- `in out` = read-write
- Explicit modes enhance clarity and safety

### Overloading & Recursion

**What this demonstrates:** Function overloading and recursion.

**Code:**
```ada
-- OVERLOADING (same name, different parameters)
function "+"(Left : Integer; Right : Integer) return Integer is
begin
   return Left + Right;
end "+";

-- RECURSIVE FUNCTION
function Factorial(N : Natural) return Positive is
begin
   if N = 0 then
      return 1;
   else
      return N * Factorial(N - 1);
   end if;
end Factorial;
```

**Explanation:**
- Overloading: Multiple subprograms with same name, different parameter types
- Compiler selects appropriate version based on argument types
- Recursion: Functions can call themselves
- Base case required to terminate recursion
- Operators can be overloaded

**Key Takeaways:**
- Overloading = same name, different parameters
- Compiler selects based on argument types
- Supports recursion
- Operators can be overloaded

---

## Packages (Modules)

### Overview

Packages are Ada's primary mechanism for modularization. They provide encapsulation, information hiding, and code organization. Packages are essential for building large Ada programs.

### Key Concepts

- **Package Specification**: Public interface (`.ads` file)
- **Package Body**: Implementation (`.adb` file)
- **Public/Private**: Control visibility of declarations
- **Child Packages**: Hierarchical organization
- **With/Use**: Import and use packages

### Package Specification & Body

**What this demonstrates:** Complete package with specification and body.

**Code:**
```ada
-- PACKAGE SPECIFICATION (interface) - math_operations.ads
package Math_Operations is
   PI : constant Float := 3.14159;
   type Complex is record
      Real : Float;
      Imag : Float;
   end record;
   function Add(A, B : Complex) return Complex;
private
   -- Private declarations
end Math_Operations;

-- PACKAGE BODY (implementation) - math_operations.adb
package body Math_Operations is
   function Add(A, B : Complex) return Complex is
   begin
      return (Real => A.Real + B.Real, Imag => A.Imag + B.Imag);
   end Add;
end Math_Operations;
```

**Explanation:**
- Package specification (`.ads`) = public interface
- Package body (`.adb`) = implementation
- `private` section hides implementation details
- Public declarations visible to users
- Private declarations only visible to package body

**Key Takeaways:**
- Specification = interface (`.ads`), Body = implementation (`.adb`)
- `private` section hides implementation
- Separates interface from implementation

### Using Packages

**What this demonstrates:** Importing and using packages.

**Code:**
```ada
with Math_Operations;
use Math_Operations;

procedure Use_Package is
   C1 : Complex := (Real => 3.0, Imag => 4.0);
begin
   Result := Add(C1, C2);  -- Can use directly with "use"
end Use_Package;
```

**Explanation:**
- `with Package_Name;` imports package
- `use Package_Name;` makes package contents directly accessible
- Without `use`, must qualify: `Package_Name.Item`

**Key Takeaways:**
- `with` imports package
- `use` makes contents directly accessible
- Use `use` sparingly to avoid name conflicts

---

## Arrays

### Overview

Ada provides powerful array facilities including constrained arrays, unconstrained arrays, multidimensional arrays, slices, and array attributes.

### Key Concepts

- **Constrained Arrays**: Fixed bounds
- **Unconstrained Arrays**: Bounds determined at runtime
- **Array Attributes**: `'First`, `'Last`, `'Length`, `'Range`
- **Array Slices**: Portions of arrays
- **Array Aggregates**: Initialization syntax

### Constrained Arrays

**What this demonstrates:** Arrays with fixed bounds.

**Code:**
```ada
type Vector is array (1..10) of Integer;
Numbers : Vector := (1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
Zeros : Vector := (others => 0);

Numbers(1) := 100;
for I in Numbers'Range loop
   Ada.Text_IO.Put(Integer'Image(Numbers(I)));
end loop;
```

**Explanation:**
- `type Name is array (bounds) of Element_Type;` declares array type
- Array aggregates: `(value1, value2, ...)` for initialization
- `others => value` sets all unspecified elements
- `'Range` attribute for iteration

**Key Takeaways:**
- Constrained arrays have fixed bounds
- Array aggregates for initialization
- `others => value` for default values
- `'Range` attribute for bounds

---

## Records & Discriminants

### Overview

Records group related data together. Discriminants enable variant records (records with conditional fields based on discriminant value).

### Key Concepts

- **Record**: Grouping of related fields
- **Discriminant**: Field that determines record variant
- **Variant Records**: Records with conditional fields
- **Default Values**: Records can have default field values

### Basic Records

**What this demonstrates:** Simple record types.

**Code:**
```ada
type Person is record
   Name : String(1..50);
   Age : Natural;
   Height : Float;
end record;

User : Person := (Name => "Commander" & (11..50 => ' '),
                  Age => 25,
                  Height => 6.0);
User.Age := 26;
```

**Explanation:**
- `type Name is record ... end record;` declares record type
- Fields accessed with dot notation: `Record.Field`
- Record aggregates: `(Field1 => Value1, Field2 => Value2)`
- Records group related data

**Key Takeaways:**
- Records group related data
- Dot notation for field access
- Record aggregates for initialization
- Essential for data modeling

### Variant Records (Discriminants)

**What this demonstrates:** Records with discriminants (variant records).

**Code:**
```ada
type Shape_Kind is (Circle, Rectangle, Triangle);

type Shape(Kind : Shape_Kind) is record
   X, Y : Float;  -- Common fields
   case Kind is
      when Circle => Radius : Float;
      when Rectangle => Width, Height : Float;
      when Triangle => Base, Altitude : Float;
   end case;
end record;

Circle_Shape : Shape(Circle) := (Kind => Circle, X => 0.0, Y => 0.0, Radius => 5.0);
```

**Explanation:**
- Discriminant determines which fields are present
- `case Kind is ... end case;` defines variant fields
- Each variant has different fields
- Discriminant value fixed at object creation

**Key Takeaways:**
- Discriminants create variant records
- `case` statement defines variants
- Type-safe variant records
- Useful for representing alternatives

---

## Access Types (Pointers)

### Overview

Access types are Ada's pointer types. They provide dynamic allocation, but with safety features that prevent common pointer errors.

### Key Concepts

- **Access Type**: Pointer type
- **Allocation**: `new` creates dynamically allocated objects
- **Dereferencing**: `.all` explicitly dereferences (often implicit)
- **Null**: Special value for uninitialized pointers
- **Unchecked_Deallocation**: Manual memory deallocation (rarely needed)

### Access Types

**What this demonstrates:** Using access types (pointers).

**Code:**
```ada
type Int_Ptr is access Integer;
Ptr1 : Int_Ptr;
Ptr2 : Int_Ptr;

Ptr1 := new Integer;          -- Allocate uninitialized
Ptr2 := new Integer'(100);    -- Allocate with initial value

Ptr1.all := 50;               -- Explicit dereference
Ada.Text_IO.Put_Line(Integer'Image(Ptr1.all));

if Ptr1 = null then
   Ada.Text_IO.Put_Line("Pointer is null");
end if;
```

**Explanation:**
- `type Name is access Type;` declares access type (pointer)
- `new Type` allocates dynamic object
- `.all` explicitly dereferences (often implicit for records/arrays)
- `null` is uninitialized pointer value
- Access types are garbage collected (typically)

**Key Takeaways:**
- `access Type` declares pointer type
- `new Type` allocates dynamically
- `.all` dereferences (often implicit)
- `null` for uninitialized pointers

---

## Generics

### Overview

Generics provide code reuse through parameterized types and subprograms. Generics are Ada's equivalent of templates, but with strong type safety.

### Key Concepts

- **Generic Units**: Parameterized packages/subprograms
- **Generic Parameters**: Type parameters, value parameters, subprogram parameters
- **Instantiation**: Creating concrete instance from generic
- **Constraints**: Restrictions on generic type parameters

### Generic Package Example

**What this demonstrates:** Generic stack package.

**Code:**
```ada
generic
   type Element is private;
   Max_Size : Positive;
package Generic_Stack is
   procedure Push(Item : Element);
   function Pop return Element;
   function Is_Empty return Boolean;
   Stack_Overflow : exception;
   Stack_Underflow : exception;
end Generic_Stack;

package body Generic_Stack is
   type Stack_Array is array (1..Max_Size) of Element;
   Stack : Stack_Array;
   Top : Natural := 0;
   
   procedure Push(Item : Element) is
   begin
      if Top >= Max_Size then
         raise Stack_Overflow;
      end if;
      Top := Top + 1;
      Stack(Top) := Item;
   end Push;
   -- ... Pop, Is_Empty implementations
end Generic_Stack;

-- INSTANTIATION
package Int_Stack is new Generic_Stack(Element => Integer, Max_Size => 100);
use Int_Stack;
begin
   Push(10);
   Push(20);
   Result := Pop;  -- Returns 20
end;
```

**Explanation:**
- `generic ... package ... end` declares generic package
- Generic parameters: types, values, subprograms
- `is new Generic_Name(parameters);` instantiates generic
- Each instantiation creates separate type-safe instance
- Generics enable code reuse with type safety

**Key Takeaways:**
- Generics provide parameterized code
- `is new Generic(...)` instantiates
- Type-safe code reuse
- Each instantiation is separate type

---

## Exception Handling

### Overview

Ada provides comprehensive exception handling for robust error management. Exceptions separate error handling from normal program flow.

### Key Concepts

- **Exceptions**: Named error conditions
- **Raise**: Trigger exception
- **Exception Handler**: Catch and handle exceptions
- **Predefined Exceptions**: Constraint_Error, Program_Error, Storage_Error, Tasking_Error
- **Exception Messages**: Associating messages with exceptions

### Exception Handling

**What this demonstrates:** Exception handling in Ada.

**Code:**
```ada
Invalid_Input : exception;

function Safe_Divide(A, B : Integer) return Float is
begin
   if B = 0 then
      raise Division_Error;
   end if;
   return Float(A) / Float(B);
end Safe_Divide;

begin
   begin
      Result := Safe_Divide(10, 0);
   exception
      when Division_Error =>
         Ada.Text_IO.Put_Line("Cannot divide by zero");
      when Constraint_Error =>
         Ada.Text_IO.Put_Line("Constraint error occurred");
      when others =>
         Ada.Text_IO.Put_Line("Unknown error occurred");
         raise;  -- Re-raise the exception
   end;
end;
```

**Explanation:**
- `exception Name;` declares exception
- `raise Exception;` triggers exception
- `exception when Exception => ...` handles exception
- `when others =>` catches all unhandled exceptions
- `raise;` re-raises exception
- Predefined exceptions: Constraint_Error, Program_Error, Storage_Error, Tasking_Error

**Key Takeaways:**
- `raise Exception;` triggers exception
- `exception when ... =>` handles exception
- `when others =>` catches all
- `raise;` re-raises exception

---

## Tasking (Concurrency)

### Overview

Ada provides built-in support for concurrent programming through tasks and protected objects. Tasking enables parallel execution and synchronization.

### Key Concepts

- **Tasks**: Concurrent execution units
- **Entries**: Synchronization points (rendezvous)
- **Protected Objects**: Shared data with mutual exclusion
- **Rendezvous**: Synchronous communication between tasks
- **Select Statements**: Conditional/selective entry acceptance

### Tasks

**What this demonstrates:** Basic task usage.

**Code:**
```ada
task Simple_Task is
   entry Start;
end Simple_Task;

task body Simple_Task is
begin
   accept Start do
      Ada.Text_IO.Put_Line("Task started");
   end Start;
   
   for I in 1..5 loop
      Ada.Text_IO.Put_Line("Task iteration: " & Integer'Image(I));
      delay 1.0;
   end loop;
end Simple_Task;

-- Usage:
Simple_Task.Start;  -- Rendezvous
```

**Explanation:**
- `task Name is entry ... end Name;` declares task interface
- `task body Name is ... end Name;` implements task
- `entry` provides synchronization point
- `accept Entry_Name do ... end Entry_Name;` accepts entry call (rendezvous)
- Rendezvous: caller waits until task accepts entry
- Tasks execute concurrently

**Key Takeaways:**
- Tasks provide concurrent execution
- Entries enable synchronization (rendezvous)
- `accept` accepts entry call
- Rendezvous = synchronous communication

### Protected Objects

**What this demonstrates:** Protected objects for shared data.

**Code:**
```ada
protected Counter is
   procedure Increment;
   function Value return Integer;
private
   Count : Integer := 0;
end Counter;

protected body Counter is
   procedure Increment is
   begin
      Count := Count + 1;
   end Increment;
   
   function Value return Integer is
   begin
      return Count;
   end Value;
end Counter;

-- Usage:
Counter.Increment;  -- Mutually exclusive
X := Counter.Value;
```

**Explanation:**
- `protected Name is ... end Name;` declares protected object
- Protected procedures: mutually exclusive (only one at a time)
- Protected functions: concurrent read access (multiple readers)
- Automatic mutual exclusion (no manual locks needed)
- Type-safe shared data

**Key Takeaways:**
- Protected objects provide mutual exclusion
- Procedures = exclusive access
- Functions = concurrent read access
- Type-safe shared data

---

## Real-Time Features

### Overview

Ada provides comprehensive real-time features including precise timing, scheduling, and real-time tasking primitives. Essential for real-time systems.

### Key Concepts

- **Ada.Real_Time**: Real-time timing package
- **Time**: Absolute time type
- **Time_Span**: Duration type
- **delay**: Relative delay
- **delay until**: Absolute delay
- **Clock**: Current time

### Real-Time Timing

**What this demonstrates:** Real-time timing operations.

**Code:**
```ada
with Ada.Real_Time;
use Ada.Real_Time;

procedure Real_Time_Demo is
   Start_Time : Time := Clock;
   Period : Time_Span := Milliseconds(100);
   Next_Time : Time := Start_Time + Period;
begin
   delay 1.0;                    -- Delay at least 1 second
   delay until Next_Time;        -- Delay until absolute time
   
   declare
      Start : Time := Clock;
      Finish : Time;
      Elapsed : Time_Span;
   begin
      -- Do work
      Finish := Clock;
      Elapsed := Finish - Start;
   end;
end Real_Time_Demo;
```

**Explanation:**
- `Ada.Real_Time` provides real-time timing
- `Clock` returns current time
- `Time_Span` represents duration
- `delay Duration;` relative delay
- `delay until Time;` absolute delay (precise timing)
- Essential for periodic tasks and real-time systems

**Key Takeaways:**
- `Ada.Real_Time` for real-time timing
- `Clock` for current time
- `delay until` for precise absolute timing
- Essential for real-time systems

---

## Advanced Features (OOP, Contracts)

### Overview

Ada 95+ adds object-oriented programming features (tagged types, inheritance, polymorphism). Ada 2012+ adds contracts (preconditions, postconditions, invariants) for design by contract.

### Key Concepts

- **Tagged Types**: Base types for OOP
- **Inheritance**: Derived types extend base types
- **Polymorphism**: Class-wide types
- **Abstract Types**: Cannot instantiate
- **Interfaces**: Multiple inheritance (Ada 2005+)
- **Contracts**: Preconditions, postconditions, invariants (Ada 2012+)

### Object-Oriented Programming

**What this demonstrates:** Tagged types and inheritance.

**Code:**
```ada
package OOP_Demo is
   -- TAGGED TYPE (class)
   type Vehicle is tagged record
      Speed : Float;
      Position : Float;
   end record;
   
   procedure Accelerate(V : in out Vehicle; Amount : Float);
   
   -- DERIVED TYPE (inheritance)
   type Car is new Vehicle with record
      Fuel : Float;
   end record;
   
   -- Override inherited operation
   procedure Accelerate(C : in out Car; Amount : Float);
   
   -- CLASS-WIDE TYPE (polymorphism)
   type Vehicle_Access is access Vehicle'Class;
end OOP_Demo;
```

**Explanation:**
- `tagged record` creates class (tagged type)
- `new Base_Type with record` creates derived type (inheritance)
- `'Class` creates class-wide type (polymorphism)
- Tagged types enable dynamic dispatch
- Interfaces support multiple inheritance (Ada 2005+)

**Key Takeaways:**
- `tagged` enables OOP
- `new Type with record` = inheritance
- `'Class` = class-wide (polymorphism)
- Interfaces for multiple inheritance

### Contracts (Ada 2012+)

**What this demonstrates:** Design by contract with preconditions and postconditions.

**Code:**
```ada
function Sqrt(X : Float) return Float
   with Pre => X >= 0.0,           -- Precondition
        Post => Sqrt'Result >= 0.0; -- Postcondition;

function Sqrt(X : Float) return Float is
begin
   -- Implementation
   return Float(Sqrt(Float(X)));
end Sqrt;
```

**Explanation:**
- `with Pre => condition;` specifies precondition
- `with Post => condition;` specifies postcondition
- `with Type_Invariant => condition;` for type invariants
- Contracts verified at runtime (can be disabled)
- SPARK can prove contracts statically

**Key Takeaways:**
- Contracts specify requirements (Ada 2012+)
- Preconditions: required before call
- Postconditions: guaranteed after call
- SPARK can prove contracts statically

---

## Pragmas & Attributes

### Overview

Pragmas are compiler directives. Attributes provide information about types and objects. Both are essential for advanced Ada programming.

### Key Concepts

- **Pragmas**: Compiler directives (`pragma ...`)
- **Attributes**: Type/object properties (`'Attribute`)
- **Type Attributes**: Information about types
- **Object Attributes**: Information about objects
- **Aspect Specifications**: Modern way to specify attributes (Ada 2012+)

### Pragmas

**What this demonstrates:** Common pragmas.

**Code:**
```ada
pragma Optimize(Time);              -- Optimize for speed
pragma Suppress(Range_Check);       -- Disable range checking (dangerous!)
pragma Assert(X > 0, "X must be positive");
pragma Inline(My_Function);         -- Inline function
pragma Pure;                        -- Pure package (no side effects)
```

**Explanation:**
- Pragmas control compiler behavior
- `pragma Optimize` controls optimization
- `pragma Suppress` disables checks (dangerous, use carefully)
- `pragma Assert` adds runtime assertions
- `pragma Inline` suggests inlining
- `pragma Pure` marks package as pure (no side effects)

**Key Takeaways:**
- Pragmas control compiler
- Use pragmas carefully
- `pragma Assert` for debugging
- `pragma Pure` for functional packages

### Attributes

**What this demonstrates:** Type and object attributes.

**Code:**
```ada
-- TYPE ATTRIBUTES
First : Integer := Integer'First;        -- Minimum value
Last : Integer := Integer'Last;          -- Maximum value
Size : Integer := Integer'Size;          -- Size in bits

-- ARRAY ATTRIBUTES
type Arr is array (1..10) of Integer;
A : Arr;
First_Idx : Integer := A'First;          -- First index
Last_Idx : Integer := A'Last;            -- Last index
Length : Integer := A'Length;            -- Array length
```

**Explanation:**
- Attributes provide type/object information
- `'First`, `'Last`, `'Size` for scalar types
- `'First`, `'Last`, `'Length`, `'Range` for arrays
- Many attributes available (see language reference)
- Attributes enable generic programming

**Key Takeaways:**
- Attributes provide type/object info
- `'First`, `'Last`, `'Size` for scalars
- `'First`, `'Last`, `'Length`, `'Range` for arrays
- Many attributes available

---

## Best Practices

### Code Organization

- Use packages to organize code into logical modules
- Keep package specifications (interfaces) small and clear
- Use private sections to hide implementation details
- Follow naming conventions: Mixed_Case_With_Underscores

### Type Safety

- Define appropriate types for your domain (don't overuse Integer)
- Use range constraints to prevent invalid values
- Prefer strong typing over weak typing
- Use type conversions explicitly

### Error Handling

- Use exceptions for exceptional conditions
- Provide meaningful error messages
- Handle exceptions at appropriate levels
- Consider using contracts (pre/postconditions) in Ada 2012+

### Concurrency

- Use protected objects for shared data
- Prefer protected objects over tasks for simple synchronization
- Use tasks for concurrent execution
- Be careful with task termination

### Performance

- Use appropriate numeric types (don't use Long_Float when Float suffices)
- Consider using pragma Inline for small frequently-called procedures
- Profile before optimizing
- Use Unchecked_Conversion/Deallocation only when necessary

---

## Common Patterns

### Package Pattern

**Standard package organization:**
```ada
package My_Package is
   -- Public declarations
   type Public_Type is ...;
   procedure Public_Procedure(...);
private
   -- Private declarations
   type Private_Type is ...;
end My_Package;
```

### Error Handling Pattern

**Exception handling pattern:**
```ada
begin
   -- Operation that might fail
   Process_Data;
exception
   when Constraint_Error =>
      -- Handle constraint error
      Log_Error;
      Recover;
   when others =>
      -- Handle unexpected errors
      Log_Error;
      raise;  -- Re-raise if can't handle
end;
```

### Task Pattern

**Standard task pattern:**
```ada
task Worker_Task is
   entry Start;
   entry Stop;
end Worker_Task;

task body Worker_Task is
   Running : Boolean := True;
begin
   accept Start;
   while Running loop
      -- Do work
      select
         accept Stop do
            Running := False;
         end Stop;
      or
         delay 0.1;  -- Don't block forever
      end select;
   end loop;
end Worker_Task;
```

### Protected Object Pattern

**Protected object for shared data:**
```ada
protected Shared_Data is
   procedure Update(Value : Integer);
   function Read return Integer;
private
   Data : Integer := 0;
end Shared_Data;

protected body Shared_Data is
   procedure Update(Value : Integer) is
   begin
      Data := Value;
   end Update;
   
   function Read return Integer is
   begin
      return Data;
   end Read;
end Shared_Data;
```

---

## Common Errors & Troubleshooting

### Type Conversion Errors

**Problem:** Type mismatch errors
```ada
-- ERROR: Type mismatch
X : Integer := 10;
Y : Float := X;  -- ERROR: Cannot convert Integer to Float
```

**Solution:** Explicit type conversion required
```ada
X : Integer := 10;
Y : Float := Float(X);  -- OK: Explicit conversion
```

### Range Constraint Errors

**Problem:** Value out of range
```ada
type Day_Number is range 1..31;
Day : Day_Number;
Day := 32;  -- ERROR: Constraint_Error (32 not in 1..31)
```

**Solution:** Check range before assignment
```ada
if Value in Day_Number'Range then
   Day := Day_Number(Value);
else
   raise Constraint_Error with "Day out of range";
end if;
```

### Array Bounds Errors

**Problem:** Array index out of bounds
```ada
type Vector is array (1..10) of Integer;
A : Vector;
A(11) := 100;  -- ERROR: Constraint_Error (11 > 10)
```

**Solution:** Use attributes for bounds checking
```ada
if Index in A'Range then
   A(Index) := 100;
else
   raise Constraint_Error;
end if;
```

### Package Import Errors

**Problem:** Package not found
```ada
with Non_Existent_Package;  -- ERROR: Package not found
```

**Solution:** Check package name and compilation order
- Ensure package is compiled
- Check package name spelling
- Verify package is in compilation path

### Task Termination Errors

**Problem:** Program hangs waiting for tasks
```ada
-- Task never terminates, program hangs
task Body Never_Terminates is
begin
   loop
      -- Infinite loop, never terminates
   end loop;
end Never_Terminates;
```

**Solution:** Ensure tasks have termination conditions
```ada
task Body Terminates_Properly is
   Done : Boolean := False;
begin
   while not Done loop
      -- Work with exit condition
      select
         accept Stop do
            Done := True;
         end Stop;
      or
         delay 0.1;
      end select;
   end loop;
end Terminates_Properly;
```

---

## Resources

### Official Documentation

- **Ada Reference Manual**: http://www.ada-auth.org/standards/ada22.html
- **Ada Information Clearinghouse**: http://www.adaic.org/
- **Adacore Documentation**: https://docs.adacore.com/

### Learning Resources

- **Ada Programming Wikibook**: https://en.wikibooks.org/wiki/Ada_Programming
- **Learn Ada**: Various online tutorials
- **GNAT User's Guide**: https://gcc.gnu.org/onlinedocs/gnat_ugn/

### Community

- **Ada User Journal**: https://www.ada-europe.org/
- **comp.lang.ada**: Usenet newsgroup
- **Ada on Stack Overflow**: Tag: ada

### Tools

- **GNAT**: GNU Ada Compiler (open source)
- **GNAT Studio**: IDE for Ada development
- **SPARK**: Formal verification tool for Ada subset

