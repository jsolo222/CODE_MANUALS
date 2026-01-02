# HAL/S (High-order Assembly Language) - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Program Structure & Basics](#program-structure--basics)
4. [Data Types](#data-types)
5. [Operators & Expressions](#operators--expressions)
6. [Control Flow](#control-flow)
7. [Procedures (Functions & Subroutines)](#procedures-functions--subroutines)
8. [Arrays & Subscripting](#arrays--subscripting)
9. [Real-Time Features](#real-time-features)
10. [COMPOOLS (Shared Data)](#com pools-shared-data)
11. [I/O Operations](#io-operations)
12. [Error Handling](#error-handling)
13. [Aerospace Applications](#aerospace-applications)
14. [Complete Example - Space Shuttle Abort Modes](#complete-example---space-shuttle-abort-modes)
15. [Bit Manipulation](#bit-manipulation)
16. [Advanced Matrix Operations](#advanced-matrix-operations)
17. [Timing & Synchronization](#timing--synchronization)
18. [Best Practices](#best-practices)
19. [Common Patterns](#common-patterns)
20. [Historical Significance](#historical-significance)
21. [Resources](#resources)

---

## Introduction

### What is HAL/S?

**HAL** (High-order Assembly Language) is the general name for a family of real-time aerospace programming languages developed by Intermetrics. **HAL/S** (High-order Assembly Language/Space, sometimes written HAL-S) is the specific variant developed in the 1970s for NASA's Space Shuttle Primary Flight Software.

This manual covers HAL/S, which represents one of the most sophisticated safety-critical programming languages of its era. HAL/S combines high-level programming constructs with the precision and control needed for real-time aerospace applications. It was used extensively in the Space Shuttle program and influenced the development of modern safety-critical languages like Ada.

**Note**: In practice, when people refer to "HAL" in the aerospace context, they are typically referring to HAL/S (the Space Shuttle variant), as it was the most widely used and well-documented version. This manual covers HAL/S specifically.

### Why Learn HAL/S?

While HAL/S is primarily of historical interest today, understanding it provides valuable insights into:

1. **Safety-Critical Systems Design**: HAL/S demonstrates how to design languages for systems where failure is not an option
2. **Real-Time Programming**: Built-in support for real-time execution, scheduling, and synchronization
3. **Aerospace Applications**: Native support for vector/matrix operations, orbital mechanics, and attitude control
4. **Language Design**: Shows how domain-specific languages can be optimized for particular problem domains
5. **Historical Context**: Understanding the evolution of programming languages and their application to space systems

### Key Features

- **Real-Time Execution**: Built-in support for periodic tasks, event handling, and priority-based scheduling
- **Native Vector/Matrix Operations**: Direct support for 3D vectors and matrices common in aerospace applications
- **COMPOOLs**: Shared data pools for inter-process communication
- **Strong Typing**: Type safety for reliability
- **Deterministic Execution**: Predictable behavior essential for safety-critical systems
- **Built-in Mathematical Functions**: Comprehensive library for aerospace calculations
- **Tasking Model**: Concurrent programming with tasks, events, and synchronization primitives

### Use Cases

HAL/S was primarily used for:

- **Space Shuttle Primary Flight Software**: Guidance, Navigation, and Control (GN&C) systems
- **Flight Control Systems**: Attitude control, orbital maneuvering, entry/descent/landing
- **Abort Mode Management**: Return-to-Launch-Site (RTLS), Transatlantic Abort Landing (TAL), Abort-to-Orbit (ATO)
- **Skylab Operations**: Space station control software
- **Real-Time Aerospace Systems**: Any application requiring deterministic real-time execution

### Prerequisites

Before learning HAL/S, you should have:

- **Programming Fundamentals**: Understanding of basic programming concepts (variables, control flow, functions)
- **Mathematics**: Familiarity with linear algebra (vectors, matrices) and basic calculus
- **Aerospace Background** (helpful but not required): Understanding of orbital mechanics and flight dynamics
- **Real-Time Systems** (helpful but not required): Understanding of real-time programming concepts

**Note**: HAL/S is primarily of historical interest. Modern safety-critical systems use Ada, SPARK, or other contemporary languages.

---

## Getting Started

### Historical Context

HAL/S was developed in the 1970s by Intermetrics under contract to NASA. Key historical points:

- **1970s**: Development for Space Shuttle program
- **Space Shuttle Era**: Used in all Space Shuttle flights from 1981-2011
- **Influence**: Helped shape modern safety-critical languages (particularly Ada)
- **Legacy**: Represented state-of-the-art in real-time aerospace programming

### Development Environment

**Historical Note**: HAL/S was typically developed on specialized development systems. Modern development would require:

- HAL/S compiler (historically provided by Intermetrics/Veridian)
- Target execution environment (typically flight computers)
- Cross-compilation tools
- Real-time operating system support

**Note**: This guide is educational. Actual HAL/S development environments are rare today.

### Your First Program

**What this demonstrates:** Basic HAL/S program structure with COMPOOL declarations and simple computations.

**Code:**
```hal/s
PROGRAM EXAMPLE;

   /* COMPOOL (Common Pool) - Shared data declarations */
   COMPOOL GLOBAL_DATA;
      DECLARE MISSION_TIME SCALAR;
      DECLARE ORBIT_NUMBER INTEGER;
   CLOSE GLOBAL_DATA;

   /* Local declarations */
   DECLARE X SCALAR;
   DECLARE Y SCALAR;
   DECLARE Z SCALAR;

   /* Program body */
   X = 10.5;
   Y = 20.3;
   Z = X + Y;
   
   WRITE(6) 'RESULT = ', Z;

CLOSE EXAMPLE;
```

**Explanation:**
- `PROGRAM EXAMPLE;`: Declares the start of a program named EXAMPLE
- `COMPOOL GLOBAL_DATA;`: Begins a COMPOOL (common pool) declaration for shared data. COMPOOLs allow data to be shared across multiple programs/tasks
- `DECLARE`: Variable declaration keyword
- `SCALAR`: Floating-point number type (single precision)
- `INTEGER`: Integer number type
- `CLOSE GLOBAL_DATA;`: Ends the COMPOOL declaration
- `WRITE(6)`: Outputs to device 6 (typically console/printer). Device numbers are platform-specific
- `CLOSE EXAMPLE;`: Ends the program

**Key Takeaways:**
- HAL/S programs start with `PROGRAM` and end with `CLOSE`
- COMPOOLs are used for shared data across programs/tasks
- Device numbers (like 6) are platform-specific
- Variable declarations use `DECLARE` keyword
- Assignment uses `=` operator

---

## Program Structure & Basics

### Overview

HAL/S programs have a clear structure designed for modularity and safety. Understanding this structure is essential for writing correct HAL/S code.

### Key Concepts

- **PROGRAM**: Main program unit
- **COMPOOL**: Shared data pool for inter-program communication
- **TASK**: Real-time concurrent process
- **PROCEDURE/FUNCTION**: Subprograms for code reuse
- **DECLARE**: Variable declaration keyword
- **CLOSE**: Ends blocks (PROGRAM, COMPOOL, TASK, etc.)

### Basic Program Structure

**What this demonstrates:** The standard structure of a HAL/S program including COMPOOL declarations and local variables.

**Code:**
```hal/s
PROGRAM STRUCTURE_DEMO;

   /* COMPOOL declaration (optional, for shared data) */
   COMPOOL SHARED_DATA;
      DECLARE GLOBAL_COUNTER INTEGER;
      DECLARE SYSTEM_STATUS BIT(8);
   CLOSE SHARED_DATA;

   /* Local variable declarations */
   DECLARE TEMPERATURE SCALAR;
   DECLARE PRESSURE SCALAR;
   DECLARE FLAG BIT(1);

   /* Program executable code */
   TEMPERATURE = 98.6;
   PRESSURE = 14.7;
   FLAG = TRUE;

CLOSE STRUCTURE_DEMO;
```

**Explanation:**
- Programs begin with `PROGRAM` and end with `CLOSE`
- COMPOOLs are declared before local variables
- All variables must be declared before use
- Executable statements follow declarations
- Statements are terminated implicitly (no semicolons required)

**Key Takeaways:**
- Clear separation between declarations and executable code
- COMPOOLs provide shared memory across programs
- Type safety through explicit declarations
- Structured organization promotes reliability

---

## Data Types

### Overview

HAL/S provides a rich set of data types optimized for aerospace applications, including native vector and matrix types that make 3D calculations straightforward.

### Key Concepts

- **SCALAR**: Floating-point numbers (single and double precision)
- **INTEGER**: Whole numbers
- **BIT**: Boolean and bit-field types
- **CHARACTER**: Text data
- **VECTOR**: 3-element arrays (standard for 3D space)
- **MATRIX**: 2D arrays for transformations
- **ARRAY**: General multidimensional arrays
- **STRUCTURE**: Record types for grouping related data

### Scalar Types

**What this demonstrates:** Floating-point and integer numeric types in HAL/S.

**Code:**
```hal/s
PROGRAM DATA_TYPES;

   /* SCALAR - Floating point (single precision) */
   DECLARE TEMPERATURE SCALAR;
   DECLARE PRESSURE SCALAR INITIAL(14.7);
   
   /* DOUBLE PRECISION SCALAR */
   DECLARE PI SCALAR DOUBLE PRECISION INITIAL(3.14159265358979);
   
   /* INTEGER */
   DECLARE COUNTER INTEGER;
   DECLARE INDEX INTEGER INITIAL(0);
   
   /* Assignments */
   TEMPERATURE = 98.6;
   COUNTER = 42;
   PI = 3.14159265358979;

CLOSE DATA_TYPES;
```

**Explanation:**
- `SCALAR`: Single-precision floating-point number (typically 32-bit IEEE 754)
- `SCALAR DOUBLE PRECISION`: Double-precision floating-point (64-bit)
- `INTEGER`: Signed integer (size platform-dependent, typically 32-bit)
- `INITIAL(value)`: Optional initialization in declaration
- All numeric types support standard arithmetic operations

**Key Takeaways:**
- SCALAR is the default floating-point type
- Use DOUBLE PRECISION when more precision is needed
- INTEGER for whole numbers
- Initialization can be done in declaration or with assignment

### Bit Types

**What this demonstrates:** Boolean and bit-field types for flags and status indicators.

**Code:**
```hal/s
PROGRAM BIT_TYPES;

   /* BIT - Boolean */
   DECLARE SWITCH BIT(1);            /* Single bit */
   DECLARE FLAGS BIT(8);             /* 8-bit field */
   DECLARE ENGINE_STATUS BIT(1) INITIAL(TRUE);
   
   /* Assignments */
   SWITCH = TRUE;
   FLAGS = X'FF';  /* Hexadecimal literal */
   ENGINE_STATUS = FALSE;

CLOSE BIT_TYPES;
```

**Explanation:**
- `BIT(n)`: Declares a bit field of n bits
- `BIT(1)`: Single-bit boolean value
- `TRUE` and `FALSE`: Boolean constants
- Hexadecimal literals: `X'FF'` for hex, `B'10101010'` for binary
- Used extensively for status flags and control signals

**Key Takeaways:**
- BIT types are essential for hardware interface
- Multi-bit BIT fields allow compact status storage
- TRUE/FALSE for single-bit operations
- Hexadecimal notation (`X'...'`) for multi-bit values

### Vector Types

**What this demonstrates:** Native 3D vector type, essential for aerospace applications.

**Code:**
```hal/s
PROGRAM VECTOR_TYPES;

   /* VECTOR - 3-element array (aerospace standard) */
   DECLARE POSITION VECTOR(3);
   DECLARE VELOCITY VECTOR(3) INITIAL(100.0, 200.0, 300.0);
   
   /* Vector operations */
   POSITION = VECTOR(1000.0, 2000.0, 3000.0);
   POSITION$(1) = 1500.0;  /* Access first element ($ is subscript operator) */
   POSITION$(2) = 2500.0;  /* Access second element */
   POSITION$(3) = 3500.0;  /* Access third element */

CLOSE VECTOR_TYPES;
```

**Explanation:**
- `VECTOR(3)`: 3-element vector (standard for 3D space: X, Y, Z)
- `$` operator: Subscript operator for array/vector element access (1-indexed)
- `VECTOR(x, y, z)`: Vector constructor literal
- Initialization can provide all three components
- Vectors support built-in operations: addition, subtraction, dot product, cross product

**Key Takeaways:**
- Vectors are first-class types in HAL/S (not just arrays)
- 3-element vectors are standard for 3D space
- $ operator accesses elements (1-indexed, not 0-indexed)
- Built-in vector operations make aerospace calculations straightforward

### Matrix Types

**What this demonstrates:** 2D matrix types for transformations and linear algebra.

**Code:**
```hal/s
PROGRAM MATRIX_TYPES;

   /* MATRIX - 2D array */
   DECLARE ROTATION_MATRIX MATRIX(3,3);
   DECLARE IDENTITY MATRIX(3,3) INITIAL(
      1.0, 0.0, 0.0,
      0.0, 1.0, 0.0,
      0.0, 0.0, 1.0
   );
   
   /* Matrix element access */
   ROTATION_MATRIX$(1,1) = 1.0;
   ROTATION_MATRIX$(1,2) = 0.0;
   ROTATION_MATRIX$(2,1) = 0.0;
   ROTATION_MATRIX$(2,2) = 1.0;

CLOSE MATRIX_TYPES;
```

**Explanation:**
- `MATRIX(rows, cols)`: Declares a 2D matrix
- `MATRIX(3,3)`: Standard 3x3 matrix for 3D rotations
- Matrix initialization uses row-major order (all values in one list)
- `$(row, col)`: Access element at row, col (1-indexed)
- Matrices support: addition, subtraction, multiplication, transpose, inverse, determinant

**Key Takeaways:**
- Matrices are first-class types like vectors
- 3x3 matrices standard for 3D rotations and transformations
- Matrix operations are built into the language
- Essential for coordinate transformations in aerospace applications

### Structures

**What this demonstrates:** Record types for grouping related data.

**Code:**
```hal/s
PROGRAM STRUCTURE_TYPES;

   /* STRUCTURE (Record type) */
   DECLARE STRUCT TELEMETRY:
      1 TIME SCALAR,
      1 ALTITUDE SCALAR,
      1 VELOCITY VECTOR(3),
      1 STATUS BIT(8);
   
   DECLARE TLM TELEMETRY;
   
   /* Structure access */
   TLM.TIME = 12345.67;
   TLM.ALTITUDE = 50000.0;
   TLM.VELOCITY = VECTOR(7000.0, 0.0, 0.0);
   TLM.STATUS = X'FF';

CLOSE STRUCTURE_TYPES;
```

**Explanation:**
- `DECLARE STRUCT name:`: Begins structure type definition
- Level numbers (like `1`) indicate structure hierarchy (similar to COBOL)
- Structures can contain any types (scalars, vectors, matrices, bit fields)
- `.` operator: Accesses structure members
- Structures allow grouping related data logically

**Key Takeaways:**
- Structures organize related data into logical units
- Level numbers (1, 2, etc.) indicate hierarchy
- Member access uses dot notation
- Essential for organizing complex aerospace data

### Constants

**What this demonstrates:** Declaring named constants.

**Code:**
```hal/s
PROGRAM CONSTANTS;

   /* Constants */
   DECLARE CONST GRAVITY SCALAR CONSTANT(9.81);
   DECLARE CONST MAX_THRUST SCALAR CONSTANT(1000000.0);
   DECLARE CONST EARTH_RADIUS SCALAR CONSTANT(6371000.0);
   
   DECLARE ALTITUDE SCALAR;
   
   /* Use constants */
   ALTITUDE = EARTH_RADIUS + 400000.0;  /* 400 km altitude */

CLOSE CONSTANTS;
```

**Explanation:**
- `DECLARE CONST`: Declares a constant
- `CONSTANT(value)`: Specifies the constant's value
- Constants cannot be modified after declaration
- Use constants for physical constants, limits, and configuration values
- Improves code readability and maintainability

**Key Takeaways:**
- Constants provide named values that cannot change
- Use for physical constants (gravity, Earth radius, etc.)
- Improves code clarity and prevents magic numbers
- Compile-time checking ensures constants aren't modified

---

## Operators & Expressions

### Overview

HAL/S provides a comprehensive set of operators for arithmetic, logical, relational, and specialized vector/matrix operations. Understanding these operators is essential for aerospace calculations.

### Key Concepts

- **Arithmetic Operators**: Standard math operations (+, -, *, /, **)
- **Relational Operators**: Comparisons (=, ~=, <, >, <=, >=)
- **Logical Operators**: Boolean operations (&, |, ~, CAT)
- **Vector Operations**: Built-in dot product, cross product, magnitude
- **Matrix Operations**: Multiplication, transpose, inverse, determinant
- **Built-in Functions**: Mathematical library (SIN, COS, SQRT, etc.)

### Arithmetic Operators

**What this demonstrates:** Basic arithmetic operations in HAL/S.

**Code:**
```hal/s
PROGRAM OPERATORS;

   DECLARE A SCALAR;
   DECLARE B SCALAR;
   DECLARE C SCALAR;
   DECLARE I INTEGER;
   DECLARE J INTEGER;
   
   /* Arithmetic operators */
   C = A + B;          /* Addition */
   C = A - B;          /* Subtraction */
   C = A * B;          /* Multiplication */
   C = A / B;          /* Division */
   C = A ** 2;         /* Exponentiation */
   C = -A;             /* Negation */
   
   /* Integer division and modulo */
   I = J DIV 3;        /* Integer division */
   I = J MOD 3;        /* Modulo */

CLOSE OPERATORS;
```

**Explanation:**
- Standard arithmetic operators work with SCALAR (floating-point) types
- `**` is exponentiation (A ** 2 means A squared)
- `DIV` is integer division (result is INTEGER, truncates fractional part)
- `MOD` is modulo (remainder after integer division)
- Operator precedence follows standard mathematical rules

**Key Takeaways:**
- Use `/` for floating-point division
- Use `DIV` and `MOD` for integer operations
- `**` for exponentiation
- Precedence: ** > * / > + - > relational > logical

### Relational & Logical Operators

**What this demonstrates:** Comparison and logical operations.

**Code:**
```hal/s
PROGRAM RELATIONAL_LOGICAL;

   DECLARE A SCALAR;
   DECLARE B SCALAR;
   DECLARE FLAG BIT(1);
   
   /* Relational operators */
   FLAG = A = B;       /* Equal */
   FLAG = A ~= B;      /* Not equal */
   FLAG = A < B;       /* Less than */
   FLAG = A > B;       /* Greater than */
   FLAG = A <= B;      /* Less or equal */
   FLAG = A >= B;      /* Greater or equal */
   
   /* Logical operators (for BIT types) */
   FLAG = TRUE & FALSE;    /* AND */
   FLAG = TRUE | FALSE;    /* OR */
   FLAG = ~TRUE;           /* NOT */
   FLAG = TRUE CAT FALSE;  /* Concatenation */

CLOSE RELATIONAL_LOGICAL;
```

**Explanation:**
- Relational operators return BIT(1) (TRUE or FALSE)
- `~=` is "not equal" (alternative to ≠)
- `&` is logical AND, `|` is logical OR, `~` is logical NOT
- `CAT` concatenates BIT values
- Logical operators work with BIT types

**Key Takeaways:**
- Relational operators return boolean (BIT) results
- `~=` is not-equal operator
- `&`, `|`, `~` for logical operations
- `CAT` for bit concatenation

### Vector Operations

**What this demonstrates:** Built-in vector operations essential for aerospace applications.

**Code:**
```hal/s
PROGRAM VECTOR_OPS;

   DECLARE V1 VECTOR(3);
   DECLARE V2 VECTOR(3);
   DECLARE C SCALAR;
   
   /* Vector initialization */
   V1 = VECTOR(1.0, 2.0, 3.0);
   V2 = VECTOR(4.0, 5.0, 6.0);
   
   /* Vector operations */
   V1 = V2;                /* Vector assignment */
   V1 = V1 + V2;           /* Vector addition (element-wise) */
   V1 = V1 - V2;           /* Vector subtraction (element-wise) */
   C = V1 * V2;            /* Dot product (scalar result) */
   V1 = V1 CROSS V2;       /* Cross product (vector result) */
   C = ABVAL(V1);          /* Vector magnitude (length) */
   V1 = UNIT(V1);          /* Unit vector (normalized) */

CLOSE VECTOR_OPS;
```

**Explanation:**
- `*` between vectors computes dot product (returns SCALAR)
- `CROSS` computes cross product (returns VECTOR)
- `ABVAL(v)` returns vector magnitude (length): √(x² + y² + z²)
- `UNIT(v)` returns normalized vector (magnitude = 1.0)
- Vector addition/subtraction is element-wise
- These operations are built into the language (not library functions)

**Key Takeaways:**
- Vector `*` operator = dot product (scalar result)
- `CROSS` operator = cross product (vector result)
- `ABVAL` = vector magnitude (length)
- `UNIT` = normalized (unit length) vector
- Essential for 3D aerospace calculations

### Matrix Operations

**What this demonstrates:** Matrix operations for transformations and linear algebra.

**Code:**
```hal/s
PROGRAM MATRIX_OPS;

   DECLARE M1 MATRIX(3,3);
   DECLARE M2 MATRIX(3,3);
   DECLARE V1 VECTOR(3);
   DECLARE C SCALAR;
   
   /* Matrix operations */
   M1 = M2;                /* Matrix assignment */
   M1 = M1 + M2;           /* Matrix addition (element-wise) */
   M1 = M1 - M2;           /* Matrix subtraction (element-wise) */
   M1 = M1 * M2;           /* Matrix multiplication */
   V1 = M1 * V2;           /* Matrix-vector multiply */
   M1 = TRANSPOSE(M2);     /* Matrix transpose */
   M1 = INVERSE(M2);       /* Matrix inverse */
   C = DETERMINANT(M1);    /* Determinant */

CLOSE MATRIX_OPS;
```

**Explanation:**
- `*` between matrices = matrix multiplication (not element-wise)
- `*` between matrix and vector = matrix-vector multiplication
- `TRANSPOSE(M)` returns transposed matrix (rows ↔ columns)
- `INVERSE(M)` returns inverse matrix (M × M⁻¹ = Identity)
- `DETERMINANT(M)` returns scalar determinant
- Essential for coordinate transformations and rotations

**Key Takeaways:**
- Matrix `*` = matrix multiplication (not element-wise)
- `TRANSPOSE`, `INVERSE`, `DETERMINANT` are built-in functions
- Matrix-vector multiply: M * V (common in transformations)
- Essential for 3D rotations and coordinate systems

### Built-in Mathematical Functions

**What this demonstrates:** Standard mathematical library functions.

**Code:**
```hal/s
PROGRAM MATH_FUNCTIONS;

   DECLARE A SCALAR;
   DECLARE C SCALAR;
   DECLARE I INTEGER;
   
   /* Basic functions */
   C = ABS(A);             /* Absolute value */
   C = SQRT(A);            /* Square root */
   C = EXP(A);             /* e^x (exponential) */
   C = LOG(A);             /* Natural logarithm */
   
   /* Trigonometric functions */
   C = SIN(A);             /* Sine (radians) */
   C = COS(A);             /* Cosine (radians) */
   C = TAN(A);             /* Tangent (radians) */
   C = ARCSIN(A);          /* Arcsine */
   C = ARCCOS(A);          /* Arccosine */
   C = ARCTAN(A);          /* Arctangent */
   C = ARCTAN(A, B);       /* Two-argument arctangent (atan2) */
   
   /* Rounding functions */
   I = TRUNC(A);           /* Truncate to integer */
   I = ROUND(A);           /* Round to nearest integer */
   C = REMAINDER(A, B);    /* Floating point remainder */
   
   /* Type conversion */
   C = SCALAR(I);          /* Integer to scalar */
   I = INTEGER(C);         /* Scalar to integer */

CLOSE MATH_FUNCTIONS;
```

**Explanation:**
- Trigonometric functions use radians (not degrees)
- `ARCTAN(A, B)` is two-argument atan2 (handles all quadrants)
- `TRUNC` truncates toward zero (removes fractional part)
- `ROUND` rounds to nearest integer
- `SCALAR(I)` and `INTEGER(C)` perform type conversions
- Functions are built into the language

**Key Takeaways:**
- All trigonometric functions use radians
- `ARCTAN(A, B)` = atan2 (handles quadrants correctly)
- `TRUNC` vs `ROUND` for integer conversion
- Explicit type conversion required

---

## Control Flow

### Overview

HAL/S provides standard control flow constructs (IF, DO loops, CASE) essential for program logic. Understanding these is fundamental to writing HAL/S programs.

### Key Concepts

- **IF Statements**: Conditional execution
- **DO Loops**: FOR, WHILE, UNTIL loops
- **CASE Statement**: Multi-way branching
- **Labels**: Named blocks for EXIT control
- **EXIT**: Break out of loops

### IF Statements

**What this demonstrates:** Conditional execution with IF statements.

**Code:**
```hal/s
PROGRAM CONTROL_FLOW;

   DECLARE X SCALAR;
   
   /* IF statement */
   IF X > 0.0 THEN
      DO;
         WRITE(6) 'POSITIVE';
      END;
   
   /* IF-ELSE */
   IF X > 0.0 THEN
      WRITE(6) 'POSITIVE';
   ELSE
      WRITE(6) 'NON-POSITIVE';
   
   /* Multi-way IF */
   IF X > 0.0 THEN
      WRITE(6) 'POSITIVE';
   ELSE IF X < 0.0 THEN
      WRITE(6) 'NEGATIVE';
   ELSE
      WRITE(6) 'ZERO';

CLOSE CONTROL_FLOW;
```

**Explanation:**
- `IF condition THEN` starts conditional block
- `ELSE` provides alternative path
- `ELSE IF` chains multiple conditions
- `DO; ... END;` groups multiple statements
- Single statements don't need DO/END
- Conditions evaluate to BIT(1) (TRUE/FALSE)

**Key Takeaways:**
- `IF ... THEN ... ELSE` standard conditional
- `DO; ... END;` for multiple statements
- `ELSE IF` for chained conditions
- Conditions must be boolean (BIT) expressions

### DO Loops

**What this demonstrates:** Various loop constructs in HAL/S.

**Code:**
```hal/s
PROGRAM LOOPS;

   DECLARE I INTEGER;
   DECLARE COUNT INTEGER;
   DECLARE FLAG BIT(1);
   
   /* DO FOR loop (basic) */
   DO FOR I = 1 TO 10;
      WRITE(6) I;
   END;
   
   /* DO FOR loop with step */
   DO FOR I = 0 TO 100 BY 10;
      WRITE(6) I;
   END;
   
   /* DO WHILE loop */
   COUNT = 0;
   DO WHILE COUNT < 10;
      COUNT = COUNT + 1;
      WRITE(6) COUNT;
   END;
   
   /* DO UNTIL loop */
   COUNT = 0;
   DO UNTIL COUNT >= 10;
      COUNT = COUNT + 1;
      WRITE(6) COUNT;
   END;
   
   /* Infinite loop with exit */
   DO WHILE TRUE;
      /* Process */
      IF DONE THEN
         EXIT;
   END;

CLOSE LOOPS;
```

**Explanation:**
- `DO FOR I = start TO end;` - counts from start to end (inclusive)
- `BY step` - optional step size (default is 1)
- `DO WHILE condition;` - continues while condition is TRUE
- `DO UNTIL condition;` - continues until condition is TRUE
- `EXIT;` - breaks out of current loop
- Loop variable is local to the loop

**Key Takeaways:**
- `DO FOR` = counted loop (like for-loop)
- `DO WHILE` = pre-condition loop
- `DO UNTIL` = post-condition loop (continues until true)
- `EXIT` breaks out of loop
- `BY step` for non-unit increments

### Nested Loops & Labels

**What this demonstrates:** Nested loops with labels for control.

**Code:**
```hal/s
PROGRAM NESTED_LOOPS;

   DECLARE I INTEGER;
   DECLARE J INTEGER;
   
   /* Nested loops with labels */
   OUTER:
   DO FOR I = 1 TO 5;
      INNER:
      DO FOR J = 1 TO 5;
         IF I * J > 10 THEN
            EXIT OUTER;  /* Exit outer loop */
         WRITE(6) I, J;
      END INNER;
   END OUTER;

CLOSE NESTED_LOOPS;
```

**Explanation:**
- Labels (OUTER:, INNER:) name loops
- `EXIT label;` exits the named loop (not just current)
- `EXIT;` (no label) exits innermost loop
- Labels must match exactly (case-sensitive)
- Useful for breaking out of nested loops

**Key Takeaways:**
- Labels name loops for EXIT control
- `EXIT label;` exits named loop
- `EXIT;` (no label) exits innermost loop
- Labels enable breaking out of nested loops

### CASE Statement

**What this demonstrates:** Multi-way branching with CASE.

**Code:**
```hal/s
PROGRAM CASE_STATEMENT;

   DECLARE I INTEGER;
   
   /* CASE statement (like switch) */
   DO CASE I;
      /* CASE 0 */
      WRITE(6) 'ZERO';
      
      /* CASE 1 */
      WRITE(6) 'ONE';
      
      /* CASE 2 */
      WRITE(6) 'TWO';
      
      /* Default case */
      ELSE
         WRITE(6) 'OTHER';
   END;

CLOSE CASE_STATEMENT;
```

**Explanation:**
- `DO CASE expression;` starts case statement
- Cases are ordered by value (0, 1, 2, ...)
- `ELSE` is default case (optional but recommended)
- Expression value selects which case executes
- Falls through to next case if no EXIT/END

**Key Takeaways:**
- `DO CASE` provides multi-way branching
- Cases ordered by value
- `ELSE` for default case
- Similar to switch statement in other languages

---

## Procedures (Functions & Subroutines)

### Overview

HAL/S supports both functions (return values) and procedures (subroutines). Understanding subprograms is essential for code organization and reuse.

### Key Concepts

- **FUNCTION**: Returns a value
- **PROCEDURE**: Subroutine (no return value, but can modify parameters)
- **ASSIGN**: Pass by reference (parameters can be modified)
- **CALL**: Invoke procedures
- **TASK**: Real-time concurrent process
- **RETURN**: Return value from function

### Functions

**What this demonstrates:** Functions that return values.

**Code:**
```hal/s
/* FUNCTION - Returns a value */
FUNCTION SQUARE(X);
   DECLARE X SCALAR;
   DECLARE RESULT SCALAR;
   
   RESULT = X * X;
   RETURN RESULT;
   
CLOSE SQUARE;

/* Function with vector arguments */
FUNCTION DOT_PRODUCT(V1, V2);
   DECLARE V1 VECTOR(3);
   DECLARE V2 VECTOR(3);
   DECLARE RESULT SCALAR;
   
   RESULT = V1 * V2;  /* Built-in dot product */
   RETURN RESULT;
   
CLOSE DOT_PRODUCT;

/* Recursive function (Fibonacci) */
FUNCTION FIBONACCI(N);
   DECLARE N INTEGER;
   DECLARE RESULT INTEGER;
   
   IF N <= 1 THEN
      RESULT = N;
   ELSE
      RESULT = FIBONACCI(N-1) + FIBONACCI(N-2);
   
   RETURN RESULT;
   
CLOSE FIBONACCI;
```

**Explanation:**
- `FUNCTION name(parameters);` declares a function
- `RETURN value;` returns a value from the function
- Functions can take any types as parameters (scalar, vector, matrix, etc.)
- Functions can be recursive (call themselves)
- Function name used like a variable: `result = SQUARE(x);`

**Key Takeaways:**
- Functions return values using `RETURN`
- Functions called like variables: `result = FUNCTION_NAME(args)`
- Can pass vectors, matrices, structures as parameters
- Supports recursion

### Procedures

**What this demonstrates:** Procedures (subroutines) with parameter modes.

**Code:**
```hal/s
/* PROCEDURE - Like a subroutine */
PROCEDURE SWAP(A, B);
   DECLARE A SCALAR ASSIGN;      /* ASSIGN = pass by reference */
   DECLARE B SCALAR ASSIGN;
   DECLARE TEMP SCALAR;
   
   TEMP = A;
   A = B;
   B = TEMP;
   
CLOSE SWAP;

/* Procedure with multiple outputs */
PROCEDURE COMPUTE_ORBIT(POSITION, VELOCITY, ALTITUDE, PERIOD);
   DECLARE POSITION VECTOR(3);
   DECLARE VELOCITY VECTOR(3);
   DECLARE ALTITUDE SCALAR ASSIGN;   /* Output parameter */
   DECLARE PERIOD SCALAR ASSIGN;     /* Output parameter */
   
   DECLARE R SCALAR;
   DECLARE V SCALAR;
   DECLARE MU SCALAR CONSTANT(3.986E14);  /* Earth's gravitational parameter */
   
   /* Calculate orbital parameters */
   R = ABVAL(POSITION);
   V = ABVAL(VELOCITY);
   
   ALTITUDE = R - 6371000.0;  /* Subtract Earth radius */
   PERIOD = 2.0 * 3.14159 * SQRT(R**3 / MU);
   
CLOSE COMPUTE_ORBIT;
```

**Explanation:**
- `PROCEDURE name(parameters);` declares a procedure
- `ASSIGN` keyword means pass-by-reference (parameter can be modified)
- Parameters without `ASSIGN` are pass-by-value (read-only)
- Procedures called with `CALL procedure_name(args);`
- Use `ASSIGN` for output parameters (multiple return values)

**Key Takeaways:**
- Procedures don't return values (use `CALL`)
- `ASSIGN` keyword = pass-by-reference (modifiable)
- Parameters without `ASSIGN` = pass-by-value (read-only)
- Use `ASSIGN` for output parameters

### Tasks (Real-Time Processes)

**What this demonstrates:** Tasks for real-time concurrent execution.

**Code:**
```hal/s
/* Task (real-time process) */
TASK GUIDANCE_CONTROL;
   DECLARE STATE VECTOR(6);
   DECLARE THRUST VECTOR(3);
   
   /* Initialization */
   SCHEDULE GUIDANCE_CONTROL ON DELTA_TIME(0.1);  /* Execute every 0.1 sec */
   
   /* Main task loop */
   DO WHILE TRUE;
      /* Read sensors */
      CALL READ_IMU(STATE);
      
      /* Compute control */
      CALL COMPUTE_THRUST(STATE, THRUST);
      
      /* Apply thrust */
      CALL APPLY_THRUST(THRUST);
      
      /* Wait for next cycle */
      WAIT;
   END;
   
CLOSE GUIDANCE_CONTROL;
```

**Explanation:**
- `TASK name;` declares a concurrent process
- `SCHEDULE task ON DELTA_TIME(period);` schedules periodic execution
- `WAIT;` suspends task until next scheduled time
- Tasks run concurrently with other tasks/programs
- Used for real-time control loops

**Key Takeaways:**
- Tasks are concurrent processes
- `SCHEDULE ... ON DELTA_TIME` for periodic execution
- `WAIT;` suspends until next period
- Essential for real-time systems

### Using Procedures

**What this demonstrates:** Calling functions and procedures.

**Code:**
```hal/s
PROGRAM PROCEDURE_DEMO;

   DECLARE X SCALAR;
   DECLARE Y SCALAR;
   DECLARE RESULT SCALAR;
   DECLARE POS VECTOR(3);
   DECLARE VEL VECTOR(3);
   DECLARE ALT SCALAR;
   DECLARE PER SCALAR;
   
   /* Call function */
   X = 5.0;
   RESULT = SQUARE(X);
   WRITE(6) 'SQUARE OF ', X, ' IS ', RESULT;
   
   /* Call procedure */
   X = 10.0;
   Y = 20.0;
   CALL SWAP(X, Y);
   WRITE(6) 'AFTER SWAP: X=', X, ' Y=', Y;
   
   /* Call with vector arguments */
   POS = VECTOR(7000000.0, 0.0, 0.0);
   VEL = VECTOR(0.0, 7500.0, 0.0);
   CALL COMPUTE_ORBIT(POS, VEL, ALT, PER);
   WRITE(6) 'ALTITUDE=', ALT, ' PERIOD=', PER;

CLOSE PROCEDURE_DEMO;
```

**Explanation:**
- Functions called like variables: `result = FUNCTION(args)`
- Procedures called with `CALL`: `CALL PROCEDURE(args)`
- Parameters with `ASSIGN` are modified by procedure
- Vector/matrix parameters passed naturally

**Key Takeaways:**
- Functions: `result = FUNCTION(args)`
- Procedures: `CALL PROCEDURE(args)`
- `ASSIGN` parameters are modified
- Works with any parameter types

---

## Arrays & Subscripting

### Overview

HAL/S provides powerful array operations including slicing, whole-array operations, and built-in array functions. Essential for data processing.

### Key Concepts

- **ARRAY**: Multidimensional arrays
- **Subscripting**: `$` operator for element access
- **Slicing**: Partial subscripts (`*` for whole dimension)
- **Whole-Array Operations**: Operations on entire arrays
- **Array Functions**: MIN, MAX, SUM, etc.

### Array Declaration & Initialization

**What this demonstrates:** Declaring and initializing arrays.

**Code:**
```hal/s
PROGRAM ARRAY_OPERATIONS;

   DECLARE DATA ARRAY(10) SCALAR;
   DECLARE MATRIX MATRIX(5,5);
   DECLARE I INTEGER;
   DECLARE J INTEGER;
   
   /* Array initialization */
   DO FOR I = 1 TO 10;
      DATA$(I) = SCALAR(I * 10);
   END;
   
   /* Matrix initialization */
   DO FOR I = 1 TO 5;
      DO FOR J = 1 TO 5;
         MATRIX$(I,J) = SCALAR(I * J);
      END;
   END;

CLOSE ARRAY_OPERATIONS;
```

**Explanation:**
- `ARRAY(size) type` declares 1D array
- `MATRIX(rows, cols)` declares 2D matrix (specialized array type)
- `$` operator accesses elements: `ARRAY$(index)` (1-indexed)
- `MATRIX$(row, col)` accesses matrix elements
- Arrays are 1-indexed (first element is index 1)

**Key Takeaways:**
- `ARRAY(size) type` for general arrays
- `MATRIX(rows, cols)` for 2D matrices
- `$` operator for element access (1-indexed)
- Use loops for initialization

### Array Slicing

**What this demonstrates:** Extracting rows, columns, and slices from arrays.

**Code:**
```hal/s
PROGRAM ARRAY_SLICING;

   DECLARE MATRIX MATRIX(5,5);
   DECLARE ROW VECTOR(5);
   DECLARE COL VECTOR(5);
   
   /* Array slicing (partial subscript) */
   ROW = MATRIX$(3,*);      /* Get row 3 (all columns) */
   COL = MATRIX$(*,2);      /* Get column 2 (all rows) */

CLOSE ARRAY_SLICING;
```

**Explanation:**
- `*` in subscript means "all elements" in that dimension
- `MATRIX$(row, *)` extracts entire row (vector)
- `MATRIX$(*, col)` extracts entire column (vector)
- Slicing creates new arrays/vectors
- Useful for row/column operations

**Key Takeaways:**
- `*` = all elements in dimension
- `MATRIX$(row, *)` = entire row
- `MATRIX$(*, col)` = entire column
- Slicing creates new arrays

### Whole-Array Operations

**What this demonstrates:** Operations on entire arrays.

**Code:**
```hal/s
PROGRAM WHOLE_ARRAY_OPS;

   DECLARE A ARRAY(10) SCALAR;
   DECLARE B ARRAY(10) SCALAR;
   DECLARE C ARRAY(10) SCALAR;
   
   /* Whole array operations */
   A = 0.0;                 /* Initialize all elements to 0.0 */
   B = A;                   /* Copy array */
   C = A + B;               /* Element-wise addition */
   C = A * 2.0;             /* Scalar multiplication (all elements) */

CLOSE WHOLE_ARRAY_OPS;
```

**Explanation:**
- `ARRAY = scalar;` sets all elements to scalar value
- `ARRAY1 = ARRAY2;` copies entire array
- `ARRAY1 + ARRAY2;` element-wise addition
- `ARRAY * scalar;` multiplies all elements by scalar
- Operations are element-wise (not matrix operations)

**Key Takeaways:**
- Whole-array assignment: `A = value;` (sets all elements)
- Array copy: `A = B;`
- Element-wise operations: `C = A + B;`
- Scalar operations: `C = A * 2.0;` (applies to all elements)

### Array Functions

**What this demonstrates:** Built-in array reduction functions.

**Code:**
```hal/s
PROGRAM ARRAY_FUNCTIONS;

   DECLARE DATA ARRAY(10) SCALAR;
   DECLARE MIN_VAL SCALAR;
   DECLARE MAX_VAL SCALAR;
   DECLARE SUM_VAL SCALAR;
   
   /* Array functions */
   MIN_VAL = MIN(DATA);     /* Minimum value */
   MAX_VAL = MAX(DATA);     /* Maximum value */
   SUM_VAL = SUM(DATA);     /* Sum of all elements */

CLOSE ARRAY_FUNCTIONS;
```

**Explanation:**
- `MIN(ARRAY)` returns minimum element value
- `MAX(ARRAY)` returns maximum element value
- `SUM(ARRAY)` returns sum of all elements
- Functions operate on entire array
- Return scalar results

**Key Takeaways:**
- `MIN`, `MAX`, `SUM` are built-in array functions
- Operate on entire array
- Return scalar results
- Useful for data analysis

---

## Real-Time Features

### Overview

HAL/S was designed for real-time aerospace applications. It provides built-in support for events, task scheduling, priority-based execution, and synchronization primitives.

### Key Concepts

- **EVENT**: Synchronization primitive for task coordination
- **TASK**: Concurrent real-time process
- **SCHEDULE**: Periodic task scheduling
- **PRIORITY**: Task priority levels
- **WAIT**: Suspend execution
- **LOCK**: Mutual exclusion for shared data

### Event Handling

**What this demonstrates:** Using events for synchronization.

**Code:**
```hal/s
/* Event handling */
PROGRAM EVENT_HANDLING;

   DECLARE EVENT ENGINE_START EVENT;
   DECLARE EVENT LIFTOFF EVENT;
   
   /* Set event */
   SIGNAL ENGINE_START;
   
   /* Wait for event */
   WAIT FOR ENGINE_START;
   
   /* Wait for multiple events */
   WAIT FOR ENGINE_START OR LIFTOFF;    /* Either event */
   WAIT FOR ENGINE_START AND LIFTOFF;   /* Both events */
   
   /* Timed wait */
   WAIT FOR ENGINE_START OR DELTA_TIME(10.0);  /* Event or timeout */

CLOSE EVENT_HANDLING;
```

**Explanation:**
- `DECLARE EVENT name EVENT;` declares an event
- `SIGNAL event;` sets/signals an event
- `WAIT FOR event;` suspends until event is signaled
- `OR` / `AND` combine multiple events
- `DELTA_TIME(seconds)` creates timeout event
- Events are key synchronization primitives

**Key Takeaways:**
- Events coordinate between tasks
- `SIGNAL` sets event, `WAIT FOR` waits for event
- Can combine events with `OR` / `AND`
- `DELTA_TIME` for timeouts

### Task Scheduling

**What this demonstrates:** Scheduling periodic tasks.

**Code:**
```hal/s
/* Task scheduling */
TASK TELEMETRY_TASK PRIORITY(10);
   
   DECLARE TLM_DATA STRUCTURE:
      1 TIME SCALAR,
      1 POSITION VECTOR(3),
      1 VELOCITY VECTOR(3);
   
   /* Schedule periodic execution */
   SCHEDULE TELEMETRY_TASK ON DELTA_TIME(1.0);  /* Execute every 1.0 sec */
   
   /* Task body */
   DO WHILE TRUE;
      /* Collect telemetry */
      CALL READ_SENSORS(TLM_DATA);
      
      /* Transmit */
      CALL SEND_TELEMETRY(TLM_DATA);
      
      /* Wait for next period */
      WAIT;
   END;
   
CLOSE TELEMETRY_TASK;
```

**Explanation:**
- `PRIORITY(level)` sets task priority (higher = more important)
- `SCHEDULE task ON DELTA_TIME(period);` schedules periodic execution
- `WAIT;` suspends until next scheduled time
- Tasks run at specified intervals
- Priority determines execution order when multiple tasks ready

**Key Takeaways:**
- `PRIORITY(level)` sets task priority
- `SCHEDULE ... ON DELTA_TIME` for periodic execution
- `WAIT;` waits for next period
- Priority-based scheduling for real-time systems

### Critical Sections

**What this demonstrates:** Protecting shared data with locks.

**Code:**
```hal/s
/* Critical sections */
PROGRAM CRITICAL_SECTION;

   DECLARE SHARED_COUNTER INTEGER LOCK;
   
   /* Acquire lock */
   UPDATE PRIORITY;
   SHARED_COUNTER = SHARED_COUNTER + 1;
   RELEASE PRIORITY;

CLOSE CRITICAL_SECTION;
```

**Explanation:**
- `LOCK` attribute on variable marks it for mutual exclusion
- `UPDATE PRIORITY;` acquires lock (raises priority to prevent preemption)
- `RELEASE PRIORITY;` releases lock
- Prevents multiple tasks from accessing shared data simultaneously
- Critical sections protect shared resources

**Key Takeaways:**
- `LOCK` attribute marks shared variables
- `UPDATE PRIORITY;` acquires lock
- `RELEASE PRIORITY;` releases lock
- Protects shared data from race conditions

---

## COMPOOLS (Shared Data)

### Overview

COMPOOLs (Common Pools) provide shared memory for inter-program and inter-task communication. Essential for coordinating between multiple programs and tasks in a HAL/S system.

### Key Concepts

- **COMPOOL**: Shared data declaration block
- **USE**: Import COMPOOL into program
- **Shared Memory**: Data accessible across programs/tasks
- **Global State**: System-wide shared variables

### COMPOOL Declaration

**What this demonstrates:** Declaring a COMPOOL for shared data.

**Code:**
```hal/s
/* Global data pool */
COMPOOL MISSION_DATA;

   /* Navigation state */
   DECLARE STATE_VECTOR VECTOR(6);
   DECLARE POSITION VECTOR(3);
   DECLARE VELOCITY VECTOR(3);
   
   /* Time */
   DECLARE MISSION_TIME SCALAR;
   DECLARE GROUND_TIME SCALAR;
   
   /* Status flags */
   DECLARE ENGINE_STATUS BIT(8);
   DECLARE FLIGHT_MODE INTEGER;
   
   /* Constants */
   DECLARE CONST EARTH_RADIUS SCALAR CONSTANT(6371000.0);
   DECLARE CONST EARTH_MU SCALAR CONSTANT(3.986E14);

CLOSE MISSION_DATA;
```

**Explanation:**
- `COMPOOL name;` begins COMPOOL declaration
- Variables declared in COMPOOL are shared globally
- Constants can be declared in COMPOOL
- `CLOSE name;` ends COMPOOL
- COMPOOLs are separate compilation units (like modules)

**Key Takeaways:**
- COMPOOL = shared global data pool
- Variables in COMPOOL accessible to all programs/tasks
- Constants can be shared via COMPOOL
- Separate compilation unit

### Using COMPOOLs

**What this demonstrates:** Accessing COMPOOL data from a program.

**Code:**
```hal/s
/* Using COMPOOL */
PROGRAM USE_COMPOOL;

   USE MISSION_DATA;  /* Import shared data */
   
   /* Access shared variables */
   POSITION$(1) = 7000000.0;
   POSITION$(2) = 0.0;
   POSITION$(3) = 0.0;
   
   MISSION_TIME = 12345.67;

CLOSE USE_COMPOOL;
```

**Explanation:**
- `USE compool_name;` imports COMPOOL into program
- After `USE`, variables from COMPOOL are accessible
- Variables can be read and written
- Changes visible to all programs using the COMPOOL
- Essential for inter-task communication

**Key Takeaways:**
- `USE compool_name;` imports COMPOOL
- Variables accessible after `USE`
- Changes visible to all users
- Essential for shared state

---

## I/O Operations

### Overview

HAL/S provides device-based I/O operations. Device numbers are platform-specific, with standard conventions (5=input, 6=output).

### Key Concepts

- **Device Numbers**: Platform-specific I/O channels
- **WRITE**: Output to device
- **READ**: Input from device
- **FILE**: File operations
- **SEQUENTIAL/DIRECT**: File access modes

### Console I/O

**What this demonstrates:** Basic input/output operations.

**Code:**
```hal/s
PROGRAM IO_OPERATIONS;

   DECLARE X SCALAR;
   DECLARE MESSAGE CHARACTER(80);
   
   /* Output to device 6 (typically console/printer) */
   WRITE(6) 'HELLO WORLD';
   WRITE(6) 'VALUE = ', X;
   
   /* Formatted output */
   FILE(6) = 'FORMAT: F10.3';
   WRITE(6) X;
   
   /* Input from device 5 (typically card reader/keyboard) */
   READ(5) X;
   READ(5) MESSAGE;

CLOSE IO_OPERATIONS;
```

**Explanation:**
- `WRITE(device) values;` outputs to device
- Device 6 = standard output (console/printer)
- Device 5 = standard input (keyboard/card reader)
- Multiple values can be written: `WRITE(6) val1, val2;`
- `FILE(device) = 'FORMAT: ...';` sets output format
- `READ(device) variable;` reads from device

**Key Takeaways:**
- Device 6 = output, Device 5 = input (convention)
- `WRITE(device) values;` for output
- `READ(device) variable;` for input
- Format strings control output format

### File I/O

**What this demonstrates:** File operations with different access modes.

**Code:**
```hal/s
PROGRAM FILE_IO;

   DECLARE X SCALAR;
   
   /* Sequential file I/O */
   FILE(10, SEQUENTIAL, INPUT);   /* Open for reading */
   READ(10) X;
   CLOSE(10);
   
   FILE(11, SEQUENTIAL, OUTPUT);  /* Open for writing */
   WRITE(11) X;
   CLOSE(11);
   
   /* Direct access */
   FILE(12, DIRECT, UPDATE);
   WRITE(12, REC=5) X;            /* Write to record 5 */
   READ(12, REC=5) X;             /* Read from record 5 */
   CLOSE(12);

CLOSE FILE_IO;
```

**Explanation:**
- `FILE(device, mode, access);` opens file
- `SEQUENTIAL` = sequential access (read/write in order)
- `DIRECT` = direct access (random access by record number)
- `INPUT` = read-only, `OUTPUT` = write-only, `UPDATE` = read/write
- `REC=number` specifies record number for direct access
- `CLOSE(device);` closes file

**Key Takeaways:**
- `FILE(device, mode, access);` opens files
- `SEQUENTIAL` vs `DIRECT` access modes
- `REC=number` for direct access record number
- Always `CLOSE` files when done

---

## Error Handling

### Overview

HAL/S provides error detection and recovery mechanisms essential for safety-critical systems. Error handling prevents system failures and enables graceful degradation.

### Key Concepts

- **ON ERROR**: Error handler block
- **SIGNAL ERROR**: Raise error condition
- **ARITHMETIC_ERROR**: Arithmetic exception
- **Error Recovery**: Handling and recovering from errors

### Error Detection & Signaling

**What this demonstrates:** Detecting and signaling errors.

**Code:**
```hal/s
PROGRAM ERROR_HANDLING;

   DECLARE STATUS INTEGER;
   DECLARE ERROR_FLAG BIT(1);
   
   /* Error detection */
   IF SOME_CONDITION THEN
      DO;
         CALL SIGNAL_ERROR('INVALID INPUT');
         ERROR_FLAG = TRUE;
      END;

CLOSE ERROR_HANDLING;
```

**Explanation:**
- `SIGNAL_ERROR(message)` raises an error condition
- Errors can be detected and signaled explicitly
- Error flags track error states
- Error messages provide diagnostic information

**Key Takeaways:**
- `SIGNAL_ERROR` raises errors explicitly
- Use error flags to track error states
- Error messages aid diagnostics

### Error Handlers

**What this demonstrates:** Setting up error handlers for recovery.

**Code:**
```hal/s
PROGRAM ERROR_RECOVERY;

   /* Error recovery */
   ON ERROR SYSTEM;
      DO;
         CALL LOG_ERROR;
         CALL RECOVER;
      END;
   OFF ERROR;
   
   /* Arithmetic overflow detection */
   ON ARITHMETIC_ERROR;
      DO;
         WRITE(6) 'ARITHMETIC OVERFLOW';
         /* Recovery code */
      END;
   OFF ERROR;

CLOSE ERROR_RECOVERY;
```

**Explanation:**
- `ON ERROR SYSTEM;` sets up general error handler
- `ON ARITHMETIC_ERROR;` sets up arithmetic error handler
- Handler block executes when error occurs
- `OFF ERROR;` removes error handler
- Handlers can perform recovery actions

**Key Takeaways:**
- `ON ERROR` sets error handlers
- `OFF ERROR` removes handlers
- Handlers can perform recovery
- Specific error types (ARITHMETIC_ERROR) can be handled

---

## Aerospace Applications

### Overview

HAL/S includes built-in support for aerospace calculations including orbital mechanics, attitude control, and navigation. These examples demonstrate real-world aerospace applications.

### Key Concepts

- **Orbital Mechanics**: Calculations for spacecraft orbits
- **Attitude Control**: Orientation and rotation control
- **Navigation Filters**: State estimation (e.g., Kalman filters)
- **Quaternions**: Attitude representation
- **Coordinate Transformations**: Reference frame conversions

### Orbital Mechanics

**What this demonstrates:** Calculating orbital parameters from position and velocity.

**Code:**
```hal/s
/* Orbital mechanics example */
PROGRAM ORBITAL_MECHANICS;

   USE MISSION_DATA;
   
   DECLARE R SCALAR;              /* Orbital radius */
   DECLARE V SCALAR;              /* Velocity magnitude */
   DECLARE H VECTOR(3);           /* Angular momentum */
   DECLARE E_VEC VECTOR(3);       /* Eccentricity vector */
   DECLARE E SCALAR;              /* Eccentricity */
   DECLARE A SCALAR;              /* Semi-major axis */
   DECLARE PERIOD SCALAR;         /* Orbital period */
   
   /* Calculate orbital radius and velocity */
   R = ABVAL(POSITION);
   V = ABVAL(VELOCITY);
   
   /* Calculate angular momentum */
   H = POSITION CROSS VELOCITY;
   
   /* Calculate eccentricity vector */
   E_VEC = (VELOCITY CROSS H) / EARTH_MU - UNIT(POSITION);
   E = ABVAL(E_VEC);
   
   /* Calculate semi-major axis */
   A = 1.0 / (2.0/R - V*V/EARTH_MU);
   
   /* Calculate orbital period */
   PERIOD = 2.0 * 3.14159 * SQRT(A**3 / EARTH_MU);
   
   WRITE(6) 'ORBITAL PARAMETERS:';
   WRITE(6) 'RADIUS = ', R;
   WRITE(6) 'VELOCITY = ', V;
   WRITE(6) 'ECCENTRICITY = ', E;
   WRITE(6) 'SEMI-MAJOR AXIS = ', A;
   WRITE(6) 'PERIOD = ', PERIOD;

CLOSE ORBITAL_MECHANICS;
```

**Explanation:**
- Orbital mechanics calculations from position and velocity
- Angular momentum: `H = r × v`
- Eccentricity vector: determines orbit shape
- Semi-major axis: determines orbit size
- Orbital period: time for one complete orbit (Kepler's law)
- Uses Earth's gravitational parameter (μ)

**Key Takeaways:**
- HAL/S vector operations ideal for orbital mechanics
- Angular momentum = cross product
- Eccentricity determines orbit shape (0=circle, <1=ellipse)
- Semi-major axis determines orbit size
- Orbital period from Kepler's law

### Attitude Control

**What this demonstrates:** Quaternion-based attitude control.

**Code:**
```hal/s
/* Attitude control example */
PROCEDURE COMPUTE_ATTITUDE_CONTROL(Q_ACTUAL, Q_DESIRED, TORQUE);
   
   /* Quaternion attitude control */
   DECLARE Q_ACTUAL VECTOR(4);      /* Current attitude quaternion */
   DECLARE Q_DESIRED VECTOR(4);     /* Desired attitude quaternion */
   DECLARE TORQUE VECTOR(3) ASSIGN; /* Output: control torque */
   
   DECLARE Q_ERROR VECTOR(4);
   DECLARE AXIS VECTOR(3);
   DECLARE ANGLE SCALAR;
   DECLARE K_P SCALAR CONSTANT(1.0);  /* Proportional gain */
   
   /* Compute quaternion error */
   CALL QUATERNION_ERROR(Q_ACTUAL, Q_DESIRED, Q_ERROR);
   
   /* Extract axis-angle */
   CALL QUATERNION_TO_AXIS_ANGLE(Q_ERROR, AXIS, ANGLE);
   
   /* Compute control torque (proportional control) */
   TORQUE = K_P * ANGLE * AXIS;
   
CLOSE COMPUTE_ATTITUDE_CONTROL;
```

**Explanation:**
- Quaternions represent 3D rotations (4-element vectors)
- Quaternion error = difference between actual and desired attitude
- Axis-angle representation extracted from quaternion
- Proportional control: torque proportional to error
- Control torque applied to rotate spacecraft to desired attitude

**Key Takeaways:**
- Quaternions represent 3D rotations (no gimbal lock)
- Quaternion error for attitude control
- Axis-angle from quaternion
- Proportional control law

### Navigation Filter

**What this demonstrates:** Simplified Kalman filter for navigation state estimation.

**Code:**
```hal/s
/* Navigation filter (simplified Kalman) */
PROCEDURE NAVIGATION_UPDATE(MEASUREMENT, ESTIMATE);
   
   DECLARE MEASUREMENT VECTOR(3);
   DECLARE ESTIMATE VECTOR(6) ASSIGN;
   
   DECLARE INNOVATION VECTOR(3);
   DECLARE GAIN MATRIX(6,3);
   
   /* Compute innovation */
   INNOVATION = MEASUREMENT - ESTIMATE$(1 TO 3);
   
   /* Kalman gain (simplified) */
   /* In real implementation, this would involve */
   /* covariance matrix computations */
   
   /* Update estimate */
   ESTIMATE = ESTIMATE + GAIN * INNOVATION;
   
CLOSE NAVIGATION_UPDATE;
```

**Explanation:**
- Kalman filter combines measurements with estimates
- Innovation = measurement - predicted measurement
- Kalman gain determines how much to trust measurement vs estimate
- State estimate updated based on innovation
- Simplified example (real implementation needs covariance matrices)

**Key Takeaways:**
- Kalman filter combines measurements and estimates
- Innovation = measurement - prediction
- Gain determines weighting
- HAL/S matrix operations support filter implementation

---

## Complete Example - Space Shuttle Abort Modes

### Overview

This complete example demonstrates a real-world HAL/S application: monitoring Space Shuttle engine status and determining appropriate abort modes based on vehicle state and failures.

### Key Concepts

- **Abort Modes**: RTLS (Return to Launch Site), TAL (Transatlantic Abort Landing), ATO (Abort to Orbit), AOA (Abort Once Around)
- **Engine Monitoring**: Tracking engine status
- **Decision Logic**: Selecting abort mode based on conditions
- **Real-Time Monitoring**: Continuous monitoring task
- **Priority-Based**: Highest priority for safety-critical monitoring

### Complete Abort Mode Monitoring System

**What this demonstrates:** Complete Space Shuttle abort mode monitoring system.

**Code:**
```hal/s
COMPOOL SHUTTLE_DATA;

   /* Vehicle state */
   DECLARE ALTITUDE SCALAR;
   DECLARE VELOCITY SCALAR;
   DECLARE FLIGHT_PATH_ANGLE SCALAR;
   
   /* Engine status */
   DECLARE MAIN_ENGINE_STATUS ARRAY(3) BIT(1);
   DECLARE ENGINES_RUNNING INTEGER;
   
   /* Abort modes */
   DECLARE ABORT_MODE INTEGER;
   DECLARE CONST RTLS INTEGER CONSTANT(1);      /* Return to Launch Site */
   DECLARE CONST TAL INTEGER CONSTANT(2);       /* Transatlantic Abort Landing */
   DECLARE CONST ATO INTEGER CONSTANT(3);       /* Abort to Orbit */
   DECLARE CONST AOA INTEGER CONSTANT(4);       /* Abort Once Around */

CLOSE SHUTTLE_DATA;

TASK ABORT_MONITORING PRIORITY(99);  /* Highest priority */

   USE SHUTTLE_DATA;
   
   DECLARE CRITICAL_ALTITUDE SCALAR CONSTANT(100000.0);
   DECLARE CRITICAL_VELOCITY SCALAR CONSTANT(7000.0);
   
   SCHEDULE ABORT_MONITORING ON DELTA_TIME(0.1);  /* Execute every 0.1 sec */
   
   DO WHILE TRUE;
      
      /* Count running engines */
      ENGINES_RUNNING = 0;
      DO FOR I = 1 TO 3;
         IF MAIN_ENGINE_STATUS$(I) THEN
            ENGINES_RUNNING = ENGINES_RUNNING + 1;
      END;
      
      /* Determine abort mode based on failures */
      IF ENGINES_RUNNING < 3 THEN
         DO;
            /* Engine failure detected */
            
            IF ALTITUDE < CRITICAL_ALTITUDE THEN
               DO;
                  /* Low altitude - RTLS required */
                  IF ABORT_MODE ~= RTLS THEN
                     DO;
                        ABORT_MODE = RTLS;
                        CALL INITIATE_RTLS;
                     END;
               END;
            
            ELSE IF VELOCITY < CRITICAL_VELOCITY THEN
               DO;
                  /* Insufficient velocity for orbit */
                  ABORT_MODE = TAL;
                  CALL INITIATE_TAL;
               END;
            
            ELSE
               DO;
                  /* Can reach orbit with remaining engines */
                  ABORT_MODE = ATO;
                  CALL INITIATE_ATO;
               END;
         END;
      
      WAIT;  /* Wait for next cycle */
   END;

CLOSE ABORT_MONITORING;
```

**Explanation:**
- COMPOOL defines shared vehicle state and abort mode
- Task runs at highest priority (99) every 0.1 seconds
- Monitors engine status (3 main engines)
- Determines abort mode based on altitude and velocity:
  - **RTLS** (Return to Launch Site): Low altitude, must return to launch site
  - **TAL** (Transatlantic Abort Landing): Medium altitude, land across Atlantic
  - **ATO** (Abort to Orbit): High enough, can reach orbit with remaining engines
- Calls appropriate abort initiation procedures
- Demonstrates real-time safety-critical system design

**Key Takeaways:**
- Real-world example of HAL/S in Space Shuttle
- Priority 99 = highest priority (safety-critical)
- Continuous monitoring (0.1 sec period)
- Decision logic based on vehicle state
- Abort modes: RTLS, TAL, ATO, AOA
- Demonstrates complete safety-critical system

---

## Bit Manipulation

### Overview

HAL/S provides comprehensive bit manipulation operations essential for hardware interfaces, status flags, and low-level control.

### Key Concepts

- **BIT Types**: Multi-bit fields for flags and status
- **Bit Literals**: Binary (B'...'), Hexadecimal (X'...'), Octal (O'...')
- **Bit Operations**: AND (&), OR (|), NOT (~), CAT (concatenate)
- **Shift Operations**: SHL (shift left), SHR (shift right)
- **Bit Access**: Individual bit access with subscripts

### Bit Operations

**What this demonstrates:** Bit manipulation operations.

**Code:**
```hal/s
PROGRAM BIT_OPERATIONS;

   DECLARE FLAGS BIT(8);
   DECLARE STATUS BIT(16);
   DECLARE MASK BIT(8);
   
   /* Binary constants */
   FLAGS = B'10101010';      /* Binary literal */
   FLAGS = X'AA';            /* Hexadecimal literal */
   FLAGS = O'252';           /* Octal literal */
   
   /* Bit operations */
   FLAGS = FLAGS | B'00001111';     /* OR - set bits */
   FLAGS = FLAGS & B'11110000';     /* AND - mask bits */
   FLAGS = FLAGS CAT B'11110000';   /* Concatenate */
   FLAGS = ~FLAGS;                  /* NOT - complement */
   
   /* Bit extraction */
   DECLARE BIT_VALUE BIT(1);
   BIT_VALUE = FLAGS$(3);           /* Get bit 3 */
   
   /* Bit setting */
   FLAGS$(5) = TRUE;                /* Set bit 5 */
   FLAGS$(2) = FALSE;               /* Clear bit 2 */
   
   /* Shift operations */
   FLAGS = SHL(FLAGS, 2);           /* Shift left 2 bits */
   FLAGS = SHR(FLAGS, 1);           /* Shift right 1 bit */

CLOSE BIT_OPERATIONS;
```

**Explanation:**
- `B'...'` = binary literal (e.g., B'10101010')
- `X'...'` = hexadecimal literal (e.g., X'AA')
- `O'...'` = octal literal (e.g., O'252')
- `|` = OR (sets bits), `&` = AND (masks bits), `~` = NOT (complements)
- `CAT` = concatenate (joins bit fields)
- `FLAGS$(bit)` = access individual bit (1-indexed)
- `SHL(value, count)` = shift left, `SHR(value, count)` = shift right

**Key Takeaways:**
- Multiple literal formats: B'...', X'...', O'...'
- `|` = OR, `&` = AND, `~` = NOT, `CAT` = concatenate
- Subscripts access individual bits
- `SHL` / `SHR` for shifting
- Essential for hardware interfaces

---

## Advanced Matrix Operations

### Overview

HAL/S provides comprehensive matrix operations essential for coordinate transformations, rotations, and linear algebra in aerospace applications.

### Key Concepts

- **Rotation Matrices**: 3D rotation transformations
- **Matrix Transpose**: Row/column swap
- **Matrix Inverse**: For solving linear systems
- **Determinant**: Matrix property
- **Matrix-Vector Multiplication**: Coordinate transformations

### Rotation Matrix Example

**What this demonstrates:** Creating and using rotation matrices.

**Code:**
```hal/s
PROGRAM MATRIX_OPERATIONS;

   DECLARE A MATRIX(3,3);
   DECLARE B MATRIX(3,3);
   DECLARE C MATRIX(3,3);
   DECLARE V VECTOR(3);
   DECLARE DET SCALAR;
   
   /* Initialize rotation matrix (Z-axis, 45 degrees) */
   DECLARE ANGLE SCALAR;
   ANGLE = 45.0 * 3.14159 / 180.0;  /* Convert to radians */
   
   A$(1,1) = COS(ANGLE);
   A$(1,2) = -SIN(ANGLE);
   A$(1,3) = 0.0;
   A$(2,1) = SIN(ANGLE);
   A$(2,2) = COS(ANGLE);
   A$(2,3) = 0.0;
   A$(3,1) = 0.0;
   A$(3,2) = 0.0;
   A$(3,3) = 1.0;
   
   /* Matrix operations */
   B = TRANSPOSE(A);           /* Transpose */
   C = A * B;                  /* Should be identity */
   DET = DETERMINANT(A);       /* Should be 1.0 */
   B = INVERSE(A);             /* Inverse */
   
   /* Rotate vector */
   V = VECTOR(1.0, 0.0, 0.0);
   V = A * V;
   
   WRITE(6) 'ROTATED VECTOR:', V;

CLOSE MATRIX_OPERATIONS;
```

**Explanation:**
- Rotation matrix rotates points around an axis
- Z-axis rotation: rotates around Z-axis (keeps Z unchanged)
- `TRANSPOSE(M)` swaps rows and columns
- `A * TRANSPOSE(A)` = Identity (for rotation matrices)
- `DETERMINANT` = 1.0 for rotation matrices (preserves volume)
- `INVERSE(A)` for rotation matrices = `TRANSPOSE(A)`
- `M * V` rotates vector V by matrix M

**Key Takeaways:**
- Rotation matrices for coordinate transformations
- `TRANSPOSE`, `INVERSE`, `DETERMINANT` built-in functions
- Matrix-vector multiply for transformations
- Rotation matrices: determinant = 1, inverse = transpose

---

## Timing & Synchronization

### Overview

HAL/S provides precise timing and synchronization primitives essential for real-time systems. Timing operations enable periodic execution, delays, and time-based coordination.

### Key Concepts

- **CLOCK**: Current time
- **DELTA_TIME**: Time interval
- **WAIT**: Suspend execution
- **CLOCK_TIME**: Absolute time
- **Timing**: Measuring execution time

### Timing Operations

**What this demonstrates:** Time measurement and delays.

**Code:**
```hal/s
PROGRAM TIMING_DEMO;

   DECLARE START_TIME SCALAR;
   DECLARE END_TIME SCALAR;
   DECLARE ELAPSED SCALAR;
   
   /* Get current time */
   START_TIME = CLOCK;
   
   /* Do some work */
   CALL PROCESS_DATA;
   
   /* Measure elapsed time */
   END_TIME = CLOCK;
   ELAPSED = END_TIME - START_TIME;
   
   WRITE(6) 'ELAPSED TIME:', ELAPSED, 'SECONDS';
   
   /* Delay execution */
   WAIT FOR DELTA_TIME(1.0);  /* Wait 1 second */
   
   /* Synchronize with absolute time */
   WAIT UNTIL CLOCK_TIME(12, 30, 0);  /* Wait until 12:30:00 */

CLOSE TIMING_DEMO;
```

**Explanation:**
- `CLOCK` returns current time (implementation-dependent units, typically seconds)
- `START_TIME = CLOCK;` captures start time
- `ELAPSED = END_TIME - START_TIME;` calculates elapsed time
- `WAIT FOR DELTA_TIME(seconds);` delays for specified duration
- `WAIT UNTIL CLOCK_TIME(hour, minute, second);` waits until absolute time
- Timing essential for real-time systems

**Key Takeaways:**
- `CLOCK` for time measurement
- `WAIT FOR DELTA_TIME` for relative delays
- `WAIT UNTIL CLOCK_TIME` for absolute time synchronization
- Time measurement for performance analysis

---

## Best Practices

### Code Organization

- **Use COMPOOLs for shared data**: Centralize shared state in COMPOOLs
- **Organize by function**: Group related procedures together
- **Use meaningful names**: Clear, descriptive names for variables and procedures
- **Comment complex logic**: Explain non-obvious algorithms
- **Modularize code**: Break complex programs into procedures

### Type Safety

- **Use appropriate types**: SCALAR for floating-point, INTEGER for whole numbers
- **Use constants**: `DECLARE CONST` for magic numbers and physical constants
- **Initialize variables**: Use `INITIAL(value)` when appropriate
- **Range checking**: HAL/S provides automatic range checking

### Real-Time Programming

- **Set appropriate priorities**: Higher priority for critical tasks
- **Use WAIT properly**: Always `WAIT;` in periodic tasks
- **Protect shared data**: Use `LOCK` for shared variables accessed by multiple tasks
- **Event-driven design**: Use events for task coordination
- **Deterministic execution**: Avoid non-deterministic operations in real-time code

### Error Handling

- **Check for errors**: Always check conditions that could fail
- **Use error handlers**: `ON ERROR` for recovery
- **Signal errors explicitly**: `SIGNAL_ERROR` for error conditions
- **Log errors**: Record error information for diagnostics
- **Graceful degradation**: Handle errors without system failure

### Performance

- **Use whole-array operations**: More efficient than loops when possible
- **Minimize task periods**: Don't schedule tasks more frequently than necessary
- **Optimize critical paths**: Profile and optimize frequently executed code
- **Use appropriate precision**: Single precision (SCALAR) vs double precision

---

## Common Patterns

### Periodic Task Pattern

```hal/s
TASK PERIODIC_TASK PRIORITY(50);
   SCHEDULE PERIODIC_TASK ON DELTA_TIME(1.0);
   DO WHILE TRUE;
      /* Do work */
      WAIT;
   END;
CLOSE PERIODIC_TASK;
```

### Event Coordination Pattern

```hal/s
TASK TASK1;
   /* Do work */
   SIGNAL EVENT1;
CLOSE TASK1;

TASK TASK2;
   WAIT FOR EVENT1;
   /* Continue after event */
CLOSE TASK2;
```

### Shared Data Pattern

```hal/s
COMPOOL SHARED;
   DECLARE DATA INTEGER LOCK;
CLOSE SHARED;

TASK TASK1;
   USE SHARED;
   UPDATE PRIORITY;
   DATA = DATA + 1;
   RELEASE PRIORITY;
CLOSE TASK1;
```

---

## Historical Significance

### HAL/S Was Revolutionary For:

1. **Real-Time Safety-Critical Systems**
   - Deterministic execution
   - Priority-based scheduling
   - Built-in error handling

2. **Aerospace Applications**
   - Native vector/matrix operations
   - Quaternion support
   - Numerical precision control

3. **Concurrent Programming**
   - Tasks and events
   - Shared memory (COMPOOL)
   - Synchronization primitives

4. **Verification & Validation**
   - Strong typing
   - Compile-time checks
   - Well-defined semantics

### Space Shuttle Used HAL/S For:

- Guidance, Navigation, and Control (GN&C)
- Flight control system
- Abort mode management
- Orbital maneuvering
- Entry, descent, and landing

### The Language Influenced:

- Ada (DoD standard)
- Modern real-time systems
- Aerospace software standards
- Safety-critical system design

---

## Resources

### Historical Documentation

- **HAL/S Language Reference Manual**: Original Intermetrics documentation
- **Space Shuttle Software Documentation**: NASA technical reports
- **Aerospace Software Standards**: DO-178 (influenced by HAL/S experience)

### Related Languages

- **Ada**: Modern safety-critical language (influenced by HAL/S)
- **SPARK**: Formal verification subset of Ada
- **Rust**: Modern systems language with safety guarantees

### Learning Resources

- **Real-Time Systems**: Study real-time programming concepts
- **Aerospace Engineering**: Understand orbital mechanics and attitude control
- **Safety-Critical Systems**: Learn safety-critical design principles

**Note**: HAL/S is primarily of historical interest. Modern safety-critical systems use Ada, SPARK, or other contemporary languages. However, understanding HAL/S provides valuable insights into the evolution of programming languages and safety-critical system design.

---

*Knowledge Transfer Complete - HAL/S (High-order Assembly Language)*


