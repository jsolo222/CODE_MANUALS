# Fortran - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Program Structure & Basics](#program-structure--basics)
4. [Data Types](#data-types)
5. [Operators & Expressions](#operators--expressions)
6. [Control Flow](#control-flow)
7. [Arrays](#arrays)
8. [Strings](#strings)
9. [Functions & Subroutines](#functions--subroutines)
10. [Modules](#modules)
11. [File I/O](#file-io)
12. [Advanced Features](#advanced-features)
13. [Best Practices](#best-practices)
14. [Common Patterns](#common-patterns)
15. [Resources](#resources)

---

## Introduction

### What is Fortran?

Fortran (FORMula TRANslation) is a general-purpose, compiled programming language that is especially suited to numeric computation and scientific computing. First developed in the 1950s, Fortran has evolved through many versions (FORTRAN 77, Fortran 90/95/2003/2008/2018) and remains one of the most important languages for high-performance computing, scientific simulations, and numerical analysis.

### Why Learn Fortran?

Fortran is valuable for:

1. **Scientific Computing**: Standard language for scientific and engineering applications
2. **High-Performance Computing**: Used in supercomputing and parallel computing
3. **Numerical Methods**: Excellent for numerical analysis and mathematical modeling
4. **Legacy Code**: Many scientific codes written in Fortran
5. **Performance**: Optimized compilers produce very fast code
6. **Parallel Computing**: Built-in support for parallel programming
7. **Academic Research**: Widely used in research institutions
8. **Career Opportunities**: High demand in scientific computing and HPC

### Key Features

- **Array Operations**: Powerful array syntax and operations
- **Numerical Precision**: Excellent support for floating-point arithmetic
- **Performance**: Highly optimized compilers
- **Parallel Computing**: Coarrays and parallel features in modern Fortran
- **Modules**: Modular programming and code organization
- **Type System**: Strong typing with modern features
- **Standards**: ISO/IEC standard (Fortran 2018 latest)

---

## Getting Started

### What is Fortran?

Fortran (FORMula TRANslation) is a programming language designed for scientific and numerical computing. It's widely used in high-performance computing and scientific simulations.

### Tools

- **gfortran**: GNU Fortran compiler (open-source)
- **Intel Fortran**: Commercial compiler with optimizations
- **PGI/NVIDIA HPC SDK**: High-performance computing compiler
- **NAG Fortran**: Numerical Algorithms Group compiler

### Your First Fortran Program

**Code:**
```fortran
program hello
    implicit none
    print *, "Hello, World!"
end program hello
```

---

## Program Structure & Basics

### Overview

Fortran programs have a simple structure: program name, variable declarations, and executable statements. Understanding the basic structure is fundamental.

### Key Concepts

- **program**: Main program unit
- **implicit none**: Require explicit declarations
- **Variable Declarations**: Type and name
- **Constants**: parameter attribute
- **Print/Write**: Output statements
- **Comments**: ! for comments

### Program Structure

**What this demonstrates:** Basic Fortran program structure.

**Code:**
```fortran
program fortran_basics
    implicit none
    
    ! Variable declarations
    integer :: i, j, k
    real :: x, y, z
    double precision :: pi
    complex :: c
    logical :: flag
    character(len=50) :: name
    
    ! Constants
    integer, parameter :: MAX_SIZE = 100
    real, parameter :: GRAVITY = 9.81
    
    ! Simple output
    print *, "Hello, World!"
    
    ! Formatted output
    write(*, '(A)') "Formatted output"
    write(*, '(A, I5)') "Integer:", 42
    write(*, '(A, F8.3)') "Float:", 3.14159
    
    ! Assignment
    i = 10
    x = 3.14
    pi = 3.14159265358979323846d0
    c = (1.0, 2.0)  ! Complex number: 1 + 2i
    flag = .true.
    name = "Commander"
    
end program fortran_basics
```

**Explanation:**
- `program`: Main program unit
- `implicit none`: Require explicit type declarations
- Variable declarations: Type and name (`integer :: i`)
- `parameter`: Constants
- `print *`: Simple output
- `write`: Formatted output
- Comments: `!` for comments

**Key Takeaways:**
- Always use `implicit none`
- Declare variables before use
- Use `parameter` for constants
- `print *` for simple output, `write` for formatted

---

## Data Types

### Overview

Fortran has numeric, logical, and character types. Understanding data types is essential for scientific computing.

### Key Concepts

- **integer**: Integer numbers (various kinds)
- **real**: Floating-point (single precision)
- **double precision**: Double precision floating-point
- **complex**: Complex numbers
- **logical**: Boolean (.true./.false.)
- **character**: Character strings
- **kind**: Specify precision/size

### Data Types

**What this demonstrates:** Fortran data types.

**Code:**
```fortran
subroutine data_types_demo()
    implicit none
    
    ! Integer kinds
    integer(kind=1) :: int8      ! 8-bit integer
    integer(kind=4) :: int32     ! 32-bit integer
    integer(kind=8) :: int64     ! 64-bit integer
    
    ! Real kinds
    real(kind=4) :: real32       ! Single precision
    real(kind=8) :: real64       ! Double precision
    
    ! Modern kind selection
    integer, parameter :: sp = selected_real_kind(6, 37)   ! Single
    integer, parameter :: dp = selected_real_kind(15, 307) ! Double
    real(sp) :: single_var
    real(dp) :: double_var
    
    ! Complex numbers
    complex :: c1
    complex(kind=8) :: c2
    
    c1 = (3.0, 4.0)  ! 3 + 4i
    c2 = cmplx(3.0d0, 4.0d0)
    
    print *, "Real part:", real(c1)
    print *, "Imaginary part:", aimag(c1)
    print *, "Magnitude:", abs(c1)
    
    ! Logical
    logical :: true_val, false_val
    true_val = .true.
    false_val = .false.
    
    ! Character
    character(len=10) :: short_str
    character(len=100) :: long_str
    character(len=:), allocatable :: dynamic_str
    
    short_str = "Hello"
    long_str = "This is a longer string"
    
    ! Allocatable string (Fortran 2003)
    allocate(character(len=20) :: dynamic_str)
    dynamic_str = "Dynamic allocation"
    
end subroutine data_types_demo
```

**Explanation:**
- Integer: Whole numbers (various precisions)
- Real: Floating-point numbers
- Double precision: Higher precision floating-point
- Complex: Complex numbers (real, imaginary)
- Logical: Boolean values (.true./.false.)
- Character: Strings (fixed or allocatable length)
- kind: Specify precision/size
- allocatable: Dynamic allocation

**Key Takeaways:**
- Use appropriate kind for precision
- Complex numbers for mathematical operations
- allocatable for dynamic strings
- Always use `implicit none`

---

## Operators & Expressions

### Overview

Fortran provides arithmetic, relational, and logical operators. Understanding operators is essential for expressions.

### Key Concepts

- **Arithmetic**: +, -, *, /, ** (exponentiation)
- **Relational**: ==, /=, <, >, <=, >=
- **Logical**: .and., .or., .not.
- **Integer Division**: Truncates result
- **Modulo**: mod function

### Operators

**What this demonstrates:** Fortran operators.

**Code:**
```fortran
! Arithmetic
i = 10 + 5      ! 15
i = 10 - 5      ! 5
i = 10 * 5      ! 50
i = 10 / 5      ! 2 (integer division)
i = 10 / 3      ! 3 (truncated)
x = 10.0 / 3.0  ! 3.333...
i = mod(10, 3)  ! 1 (modulo)
x = 2.0 ** 3.0  ! 8.0 (exponentiation)

! Comparison operators
if (5 == 5) print *, "Equal"
if (5 /= 3) print *, "Not equal"
if (5 > 3) print *, "Greater"
if (5 < 10) print *, "Less"
if (5 >= 5) print *, "Greater or equal"
if (5 <= 5) print *, "Less or equal"

! Logical operators
if (.true. .and. .false.) print *, "AND"
if (.true. .or. .false.) print *, "OR"
if (.not. .true.) print *, "NOT"
```

**Explanation:**
- Arithmetic: Standard math operations
- **: Exponentiation
- ==: Equal (not = in comparisons)
- /=: Not equal
- .and., .or., .not.: Logical operators
- Integer division: Truncates result
- mod: Modulo operation

**Key Takeaways:**
- Use == for equality comparison
- Integer division truncates
- Use .and., .or., .not. for logical operations
- ** for exponentiation

---

## Control Flow

### Overview

Fortran provides IF, SELECT CASE, and DO loops for control flow. Understanding control structures is essential for program logic.

### Key Concepts

- **IF-ELSE**: Conditional execution
- **SELECT CASE**: Multi-way selection
- **DO Loop**: Iteration (for loop)
- **DO WHILE**: While loop
- **EXIT**: Exit loop
- **CYCLE**: Skip to next iteration

### Control Flow

**What this demonstrates:** Control flow statements.

**Code:**
```fortran
! IF statement
x = 5.0
if (x > 0.0) then
    print *, "Positive"
else if (x < 0.0) then
    print *, "Negative"
else
    print *, "Zero"
end if

! One-line IF
if (x > 0.0) print *, "Positive (one-line)"

! SELECT CASE (like switch)
day = 3
select case (day)
    case (1)
        print *, "Monday"
    case (2)
        print *, "Tuesday"
    case (3)
        print *, "Wednesday"
    case (4:5)
        print *, "Thursday or Friday"
    case default
        print *, "Weekend"
end select

! DO loop (like for)
do i = 1, 10
    print *, i
end do

! DO loop with step
do i = 0, 20, 2
    print *, i
end do

! DO WHILE loop
i = 1
do while (i <= 5)
    print *, i
    i = i + 1
end do

! EXIT and CYCLE
do i = 1, 10
    if (i == 5) cycle  ! Skip to next iteration
    if (i == 8) exit   ! Exit loop
    print *, i
end do
```

**Explanation:**
- IF-ELSE: Conditional execution
- SELECT CASE: Multi-way selection
- DO: Iteration loop
- DO WHILE: Conditional loop
- EXIT: Exit loop early
- CYCLE: Skip to next iteration
- Case ranges: 4:5 for range

**Key Takeaways:**
- Use IF-ELSE for conditionals
- SELECT CASE for multi-way selection
- DO for iteration
- EXIT and CYCLE for loop control

---

## Arrays

### Overview

Fortran has powerful array syntax and operations. Arrays are fundamental for numerical computing.

### Key Concepts

- **Array Declaration**: dimension or (:) syntax
- **Array Operations**: Element-wise operations
- **Array Sections**: Subarrays
- **Allocatable Arrays**: Dynamic arrays
- **Array Constructors**: Initialization

### Arrays

**What this demonstrates:** Working with arrays.

**Code:**
```fortran
! Array declaration
integer, dimension(10) :: arr1
integer :: arr2(10)
real :: matrix(5, 5)  ! 2D array

! Array initialization
integer :: arr3(5) = (/1, 2, 3, 4, 5/)
integer :: arr4(5) = [(i, i=1,5)]  ! Implied DO

! Array assignment
arr1 = 0           ! All elements to 0
arr1(1:5) = 1      ! First 5 elements to 1
arr1(6:) = 2       ! Elements 6 to end to 2

! Array operations
arr2 = arr1 + 1    ! Element-wise addition
arr2 = arr1 * 2    ! Element-wise multiplication
arr2 = sqrt(real(arr1))  ! Element-wise function

! Array sections
integer :: arr5(10)
arr5(1:5) = arr1(1:5)     ! Copy section
arr5(1:10:2) = 0          ! Every 2nd element

! Allocatable arrays
integer, allocatable :: dynamic_arr(:)
allocate(dynamic_arr(100))
deallocate(dynamic_arr)

! Multi-dimensional
real :: matrix(10, 10)
matrix = 0.0
matrix(1:5, 1:5) = 1.0
```

**Explanation:**
- dimension or (:) syntax for arrays
- Array constructors: (/ ... /) or [ ... ]
- Array sections: arr(1:5)
- Stride: arr(1:10:2)
- Allocatable: Dynamic allocation
- Element-wise operations: Whole-array operations

**Key Takeaways:**
- Fortran arrays are powerful
- Use array sections for subarrays
- Allocatable for dynamic arrays
- Whole-array operations are efficient

---

## Strings

### Overview

Fortran strings are character arrays. Modern Fortran supports allocatable strings for dynamic length.

### Key Concepts

- **character(len=n)**: Fixed-length string
- **character(len=:), allocatable**: Dynamic string
- **String Operations**: Concatenation, slicing
- **String Functions**: len, trim, adjustl, adjustr

### Strings

**What this demonstrates:** Working with strings.

**Code:**
```fortran
! Fixed-length strings
character(len=20) :: str1, str2
str1 = "Hello"
str2 = "World"

! Concatenation
str1 = trim(str1) // " " // trim(str2)  ! "Hello World"

! String slicing
character(len=10) :: substr
substr = str1(1:5)  ! First 5 characters

! Dynamic strings (Fortran 2003)
character(len=:), allocatable :: dynamic_str
allocate(character(len=20) :: dynamic_str)
dynamic_str = "Dynamic string"

! String functions
print *, len(str1)           ! Length
print *, trim(str1)          ! Remove trailing blanks
print *, adjustl(str1)       ! Left adjust
print *, adjustr(str1)       ! Right adjust
print *, index(str1, "lo")   ! Find substring
```

**Explanation:**
- character(len=n): Fixed-length string
- allocatable: Dynamic-length string
- //: Concatenation operator
- trim: Remove trailing blanks
- adjustl/adjustr: Adjust within field
- index: Find substring position
- len: String length

**Key Takeaways:**
- Use fixed-length for simple cases
- allocatable for dynamic strings
- trim for concatenation
- String functions for manipulation

---

## Functions & Subroutines

### Overview

Fortran uses functions (return values) and subroutines (no return value) for code organization. Understanding procedures is essential for modular programming.

### Key Concepts

- **function**: Returns value
- **subroutine**: No return value
- **Intent**: intent(in), intent(out), intent(inout)
- **Optional Arguments**: optional attribute
- **Recursive**: Recursive procedures

### Functions

**What this demonstrates:** Creating and using functions.

**Code:**
```fortran
! Function definition
function add(a, b) result(sum)
    implicit none
    integer, intent(in) :: a, b
    integer :: sum
    sum = a + b
end function add

! Function with optional argument
function multiply(a, b) result(product)
    implicit none
    real, intent(in) :: a
    real, intent(in), optional :: b
    real :: product
    if (present(b)) then
        product = a * b
    else
        product = a * 2.0
    end if
end function multiply

! Using functions
program demo
    implicit none
    integer :: x, y, z
    x = 5
    y = 10
    z = add(x, y)  ! 15
    print *, z
end program
```

**Explanation:**
- function: Returns value
- result: Specify result variable
- intent(in): Input parameter
- intent(out): Output parameter
- intent(inout): Input/output parameter
- optional: Optional parameter
- present: Check if optional argument present

**Key Takeaways:**
- Use intent for clarity
- result for function result
- optional for optional arguments
- Always use implicit none

### Subroutines

**What this demonstrates:** Creating and using subroutines.

**Code:**
```fortran
! Subroutine definition
subroutine swap(a, b)
    implicit none
    integer, intent(inout) :: a, b
    integer :: temp
    temp = a
    a = b
    b = temp
end subroutine swap

! Subroutine with multiple outputs
subroutine divide(a, b, quotient, remainder)
    implicit none
    integer, intent(in) :: a, b
    integer, intent(out) :: quotient, remainder
    quotient = a / b
    remainder = mod(a, b)
end subroutine divide

! Using subroutines
program demo
    implicit none
    integer :: x, y, q, r
    x = 10
    y = 3
    call swap(x, y)
    call divide(10, 3, q, r)
    print *, "Quotient:", q, "Remainder:", r
end program
```

**Explanation:**
- subroutine: No return value
- call: Invoke subroutine
- intent(inout): Modify argument
- intent(out): Output argument
- Multiple outputs: Use intent(out) parameters

**Key Takeaways:**
- Use call for subroutines
- intent for parameter direction
- Multiple outputs with intent(out)
- Always use implicit none

---

## Modules

### Overview

Modules provide code organization, data sharing, and interfaces. They're essential for large programs.

### Key Concepts

- **module**: Code organization unit
- **use**: Import module
- **public/private**: Visibility control
- **contains**: Procedures in module
- **Interface**: Procedure interfaces

### Modules

**What this demonstrates:** Creating and using modules.

**Code:**
```fortran
! Module definition
module math_utils
    implicit none
    private
    public :: add, subtract, multiply
    
    integer, parameter :: pi = 3.14159
    
contains
    
    function add(a, b) result(sum)
        integer, intent(in) :: a, b
        integer :: sum
        sum = a + b
    end function add
    
    function subtract(a, b) result(diff)
        integer, intent(in) :: a, b
        integer :: diff
        diff = a - b
    end function subtract
    
end module math_utils

! Using module
program demo
    use math_utils
    implicit none
    integer :: x, y
    x = 10
    y = 5
    print *, add(x, y)
    print *, subtract(x, y)
end program
```

**Explanation:**
- module: Code organization unit
- use: Import module
- private: Default visibility (hidden)
- public: Explicitly exported
- contains: Procedures in module
- Parameter: Module constants

**Key Takeaways:**
- Use modules for code organization
- private by default, public for exports
- contains for module procedures
- use to import modules

---

## File I/O

### Overview

Fortran provides comprehensive file I/O capabilities. Understanding file operations is essential for data processing.

### Key Concepts

- **open**: Open file
- **read**: Read from file
- **write**: Write to file
- **close**: Close file
- **Formatted I/O**: Formatted data
- **Unformatted I/O**: Binary data

### File I/O

**What this demonstrates:** File operations.

**Code:**
```fortran
! Opening file
integer :: unit_num, iostat
character(len=100) :: line
unit_num = 10

open(unit=unit_num, file='data.txt', status='old', &
     action='read', iostat=iostat)
if (iostat /= 0) then
    print *, "Error opening file"
    stop
end if

! Reading file
do
    read(unit_num, '(A)', iostat=iostat) line
    if (iostat /= 0) exit
    print *, trim(line)
end do

! Writing file
open(unit=11, file='output.txt', status='replace', &
     action='write')
write(11, '(I5, F10.3)') 42, 3.14159
close(11)

! Formatted read/write
integer :: num
real :: value
read(unit_num, '(I5, F10.3)') num, value
write(*, '(A, I5, A, F10.3)') "Number:", num, "Value:", value

! Unformatted (binary) I/O
open(unit=12, file='data.bin', form='unformatted', &
     access='stream')
write(12) num, value
read(12) num, value
close(12)
```

**Explanation:**
- open: Open file (unit, file, status, action)
- read/write: Read/write data
- close: Close file
- Formatted: Text I/O with format
- Unformatted: Binary I/O
- iostat: Error status
- status: 'old', 'new', 'replace', 'scratch'

**Key Takeaways:**
- Always check iostat
- Use appropriate status
- Formatted for text, unformatted for binary
- Close files when done

---

## Advanced Features

### Overview

Modern Fortran includes derived types, pointers, and other advanced features. These enable complex data structures and programming patterns.

### Key Concepts

- **Derived Types**: User-defined types
- **Pointers**: Pointer variables
- **Allocatable**: Dynamic allocation
- **Interface**: Procedure interfaces
- **Generic Procedures**: Multiple procedures, one name

### Derived Types

**What this demonstrates:** Using derived types.

**Code:**
```fortran
! Derived type definition
type :: point
    real :: x, y
end type point

type :: circle
    type(point) :: center
    real :: radius
end type circle

! Using derived types
program demo
    implicit none
    type(point) :: p1, p2
    type(circle) :: c1
    
    p1%x = 1.0
    p1%y = 2.0
    p2 = point(3.0, 4.0)  ! Constructor
    
    c1%center = p1
    c1%radius = 5.0
    
    print *, "Point:", p1%x, p1%y
end program
```

**Explanation:**
- type: Define derived type
- %: Component access
- Constructor: Type constructor syntax
- Nested types: Types within types
- Arrays of types: type(point) :: points(10)

**Key Takeaways:**
- Use derived types for structures
- % for component access
- Constructor for initialization
- Types can contain types

---

## Best Practices

### Code Organization

- **implicit none**: Always use
- **Modules**: Organize code in modules
- **Naming**: Use descriptive names
- **Comments**: Document complex logic
- **Intent**: Always specify intent

### Performance

- **Array Operations**: Use whole-array operations
- **Allocatable**: For dynamic arrays
- **Optimization**: Use compiler optimizations
- **Profiling**: Profile performance-critical code

### Error Handling

- **iostat**: Check I/O status
- **Error Codes**: Handle errors appropriately
- **Validation**: Validate inputs

---

## Common Patterns

### Array Operations

```fortran
! Element-wise operations
arr2 = arr1 + 1
arr2 = sqrt(arr1)
arr2 = arr1 * arr2
```

### File Reading Loop

```fortran
do
    read(unit_num, '(A)', iostat=iostat) line
    if (iostat /= 0) exit
    ! Process line
end do
```

---

## Resources

### Official Documentation

- **Fortran Standard**: ISO/IEC 1539 (Fortran 2018)
- **Fortran Wiki**: https://fortranwiki.org/
- **Fortran.org**: https://fortran-lang.org/

### Learning Resources

- **Fortran Tutorial**: https://fortran-lang.org/learn/
- **Modern Fortran**: https://fortran-lang.org/
- **Fortran Wiki**: Community documentation

### Community

- **Stack Overflow**: Tag: fortran
- **Fortran Discourse**: https://fortran-lang.discourse.group/
- **r/fortran**: Reddit community

### Tools

- **gfortran**: GNU Fortran compiler
- **Intel Fortran**: Commercial Fortran compiler
- **PGI/NVIDIA HPC SDK**: High-performance Fortran compiler
- **NAG Fortran**: Numerical Algorithms Group compiler

---

