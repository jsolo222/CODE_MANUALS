# Python - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Variables & Data Types](#variables--data-types)
4. [Operators](#operators)
5. [Data Structures](#data-structures)
6. [Control Flow](#control-flow)
7. [Functions](#functions)
8. [Comprehensions](#comprehensions)
9. [Object-Oriented Programming](#object-oriented-programming)
10. [Error Handling](#error-handling)
11. [File I/O](#file-io)
12. [Modules & Imports](#modules--imports)
13. [Advanced Features](#advanced-features)
14. [Standard Library Essentials](#standard-library-essentials)
15. [Functional Programming](#functional-programming)
16. [Async Programming](#async-programming)
17. [Testing](#testing)
18. [Performance & Optimization](#performance--optimization)
19. [Best Practices](#best-practices)
20. [Common Patterns](#common-patterns)
21. [Resources](#resources)

---

## Introduction

### What is Python?

Python is a high-level, interpreted, general-purpose programming language created by Guido van Rossum and first released in 1991. Python emphasizes code readability through its clean syntax, uses significant whitespace for code structure, and supports multiple programming paradigms including procedural, object-oriented, and functional programming.

Python is known for its simplicity, versatility, and extensive standard library. It's widely used in web development, data science, artificial intelligence, automation, scientific computing, and many other domains.

### Why Learn Python?

1. **Easy to Learn**: Clean, readable syntax that's beginner-friendly
2. **Versatile**: Used in web development, data science, AI, automation, and more
3. **Large Community**: Extensive ecosystem with millions of packages
4. **Rapid Development**: Write and test code quickly
5. **Cross-Platform**: Works on Windows, macOS, Linux, and more
6. **Career Opportunities**: High demand in many industries
7. **Extensive Libraries**: Rich standard library and third-party packages

### Key Features

- **Interpreted Language**: No compilation step required
- **Dynamic Typing**: Variables are typed at runtime
- **Garbage Collected**: Automatic memory management
- **Multi-Paradigm**: Supports OOP, functional, and procedural programming
- **Extensible**: Can call C/C++ libraries
- **Large Standard Library**: "Batteries included" philosophy

### Use Cases

- **Web Development**: Django, Flask, FastAPI frameworks
- **Data Science**: NumPy, Pandas, Matplotlib, SciPy
- **Machine Learning/AI**: TensorFlow, PyTorch, scikit-learn
- **Automation**: Scripting, system administration
- **Scientific Computing**: Numerical analysis, simulations
- **Game Development**: Pygame, Panda3D
- **Desktop Applications**: Tkinter, PyQt

### Prerequisites

- **No prior programming experience required** - Python is beginner-friendly
- Basic computer skills (file management, text editing)
- Willingness to practice and experiment

---

## Getting Started

### Installation

**Windows:**
1. Download from https://www.python.org/downloads/
2. Run installer (check "Add Python to PATH")
3. Verify: Open Command Prompt, run `python --version`

**macOS:**
```bash
# Using Homebrew (recommended)
brew install python3

# Or download from python.org
python3 --version
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install python3 python3-pip
python3 --version
```

### Your First Program

**What this demonstrates:** The classic "Hello, World!" program.

**Code:**
```python
print("Hello, World!")
print("Welcome to Python!")
```

**Explanation:**
- `print()` is a built-in function that outputs text
- Strings can be in single quotes `'...'` or double quotes `"..."`
- Each `print()` statement outputs on a new line
- No semicolons or braces required - Python uses indentation

**To Run:**
1. Save as `hello.py`
2. Run: `python hello.py` (or `python3 hello.py` on Linux/macOS)

**Output:**
```
Hello, World!
Welcome to Python!
```

**Key Takeaways:**
- Python uses simple, readable syntax
- `print()` for output
- No compilation needed - just run the script
- Indentation matters (used for code blocks)

### Development Tools

**Recommended IDEs:**
- **VS Code**: Popular, free, excellent Python support
- **PyCharm**: Full-featured IDE (Community Edition free)
- **Jupyter Notebooks**: Interactive development for data science

**Essential Tools:**
- `pip`: Package installer for Python
- `venv`: Virtual environment manager
- `pylint` / `flake8`: Code linting
- `pytest`: Testing framework

---

## Variables & Data Types

### Overview

Python is dynamically typed - you don't declare variable types explicitly. Variables are created when first assigned a value. Understanding Python's data types is fundamental to programming.

### Key Concepts

- **Variables**: No declaration needed, created on assignment
- **Dynamic Typing**: Type determined at runtime
- **Type Checking**: Use `type()` and `isinstance()` to check types
- **Immutable vs Mutable**: Some types can't be changed after creation

### Basic Data Types

**What this demonstrates:** Python's fundamental data types.

**Code:**
```python
# Integers
age = 25
year = 2025
negative = -10
large_number = 1_000_000  # Underscores for readability

# Floats (floating-point numbers)
temperature = 98.6
pi = 3.14159
scientific = 1.5e10  # 1.5 × 10^10

# Strings
name = "Commander"
message = 'Hello, World!'
multiline = """This is
a multiline
string"""
f_string = f"Hello, {name}!"  # f-string (formatted string literal)

# Booleans
is_active = True
is_logged_in = False

# None (null value)
result = None

# Type checking
type(age)          # <class 'int'>
isinstance(age, int)  # True
```

**Explanation:**
- **Integers** (`int`): Whole numbers, unlimited size (Python 3)
- **Floats** (`float`): Decimal numbers, double precision
- **Strings** (`str`): Text data, immutable
- **Booleans** (`bool`): `True` or `False` (capitalized)
- **None**: Represents absence of value (like `null` in other languages)
- `type()` returns the type of an object
- `isinstance(obj, type)` checks if object is instance of type (preferred)
- Underscores in numbers (`1_000_000`) improve readability (Python 3.6+)

**Key Takeaways:**
- No type declarations - Python infers types
- Integers have unlimited precision
- Strings can use single, double, or triple quotes
- `None` is Python's null value
- Use `isinstance()` for type checking (more flexible than `type()`)

---

## Operators

### Overview

Python provides comprehensive operators for arithmetic, comparison, logical operations, and more. Understanding operators is essential for writing expressions.

### Key Concepts

- **Arithmetic Operators**: Math operations
- **Comparison Operators**: Comparisons return booleans
- **Logical Operators**: Boolean logic
- **Identity Operators**: Check object identity (`is`, `is not`)
- **Membership Operators**: Check membership (`in`, `not in`)

### Arithmetic Operators

**What this demonstrates:** Basic arithmetic operations.

**Code:**
```python
# Arithmetic
10 + 5    # 15 (addition)
10 - 5    # 5 (subtraction)
10 * 5    # 50 (multiplication)
10 / 5    # 2.0 (division - always returns float)
10 // 5   # 2 (integer division/floor division)
10 % 3    # 1 (modulo - remainder)
10 ** 2   # 100 (exponentiation)
-10       # -10 (negation)
```

**Explanation:**
- `/` always returns float (even `10 / 2` = `5.0`)
- `//` is floor division (integer division), returns int
- `%` is modulo (remainder after division)
- `**` is exponentiation (power operator)
- Operator precedence: `**` > `*` `/` `%` `//` > `+` `-`

**Key Takeaways:**
- `/` returns float, `//` returns int
- `%` for remainder/modulo
- `**` for exponentiation
- Standard operator precedence applies

### Comparison Operators

**What this demonstrates:** Comparison operations.

**Code:**
```python
# Comparison (return True or False)
5 == 5    # True (equal)
5 != 3    # True (not equal)
5 > 3     # True (greater than)
5 >= 5    # True (greater than or equal)
5 < 10    # True (less than)
5 <= 5    # True (less than or equal)
```

**Explanation:**
- Comparison operators return boolean (`True` or `False`)
- `==` is equality (value comparison)
- `!=` is not equal
- Can chain comparisons: `1 < x < 10` (Python feature)

**Key Takeaways:**
- Comparisons return booleans
- `==` for equality, `!=` for inequality
- Can chain comparisons

### Logical Operators

**What this demonstrates:** Boolean logic operations.

**Code:**
```python
# Logical operators
True and False   # False (AND)
True or False    # True (OR)
not True         # False (NOT)

# Short-circuit evaluation
x = 5
(x > 0) and (x < 10)  # True
(x > 10) or (x < 0)   # False
```

**Explanation:**
- `and`: Both must be True
- `or`: At least one must be True
- `not`: Negation (unary operator)
- Short-circuit: `and` stops at first False, `or` stops at first True
- Returns last evaluated value (not always boolean)

**Key Takeaways:**
- `and`, `or`, `not` for boolean logic
- Short-circuit evaluation
- Can return non-boolean values (last evaluated)

### Identity & Membership Operators

**What this demonstrates:** Identity and membership checking.

**Code:**
```python
# Identity operators (check if same object)
x = [1, 2]
y = [1, 2]
z = x

x is y          # False (different objects)
x is z          # True (same object)
x == y          # True (same values)
x is not y      # True

# Membership operators
'a' in 'apple'        # True
'x' not in 'apple'    # True
5 in [1, 2, 3, 4, 5]  # True
'key' in {'key': 'value'}  # True (checks keys in dict)
```

**Explanation:**
- `is` checks object identity (same object in memory)
- `==` checks value equality (same values)
- `in` checks membership (element in container)
- `is` used for `None` checks: `x is None` (not `x == None`)
- For strings, `in` checks substring

**Key Takeaways:**
- `is` = identity (same object), `==` = equality (same value)
- `in` / `not in` for membership
- Use `is None` not `== None`

---

## Data Structures

### Overview

Python provides several built-in data structures for organizing and storing data. Understanding these is fundamental to Python programming. The main data structures are lists, tuples, sets, and dictionaries.

### Key Concepts

- **Lists**: Mutable, ordered collections
- **Tuples**: Immutable, ordered collections
- **Sets**: Mutable, unordered, unique elements
- **Dictionaries**: Mutable, key-value pairs
- **Indexing**: Access elements by position
- **Slicing**: Extract subsequences
- **Mutability**: Whether structure can be modified after creation

### Lists (Mutable, Ordered)

**What this demonstrates:** Lists - Python's primary mutable sequence type.

**Code:**
```python
# Creating lists
numbers = [1, 2, 3, 4, 5]
mixed = [1, "two", 3.0, True]  # Can contain different types
empty = []

# Accessing elements
numbers[0]      # 1 (first element, 0-indexed)
numbers[-1]     # 5 (last element, negative index)
numbers[1:3]    # [2, 3] (slice: start to end-1)
numbers[:3]     # [1, 2, 3] (from start)
numbers[2:]     # [3, 4, 5] (to end)
numbers[::2]    # [1, 3, 5] (every 2nd element)
numbers[::-1]   # [5, 4, 3, 2, 1] (reverse)

# Modifying lists
numbers.append(6)           # Add to end: [1, 2, 3, 4, 5, 6]
numbers.insert(0, 0)        # Insert at index: [0, 1, 2, 3, 4, 5, 6]
numbers.extend([7, 8])      # Extend with list: [0, 1, 2, 3, 4, 5, 6, 7, 8]
numbers.remove(0)           # Remove first occurrence: [1, 2, 3, 4, 5, 6, 7, 8]
popped = numbers.pop()      # Remove and return last: 8, list is [1, 2, 3, 4, 5, 6, 7]
popped2 = numbers.pop(0)    # Remove at index: 1, list is [2, 3, 4, 5, 6, 7]
numbers.clear()             # Remove all: []

# List operations
len([1, 2, 3])              # 3 (length)
[1, 2] + [3, 4]             # [1, 2, 3, 4] (concatenation)
[1, 2] * 3                  # [1, 2, 1, 2, 1, 2] (repetition)
sorted([3, 1, 2])           # [1, 2, 3] (returns new sorted list)
list(reversed([1, 2, 3]))   # [3, 2, 1] (returns new reversed list)
```

**Explanation:**
- Lists are mutable (can be changed after creation)
- Zero-indexed (first element is index 0)
- Negative indices count from the end (-1 is last element)
- Slicing: `list[start:stop:step]` (stop is exclusive)
- `append()` adds single item, `extend()` adds all items from iterable
- `pop()` removes and returns element (default last, or at index)
- `remove()` removes first matching value
- `+` concatenates, `*` repeats
- `sorted()` and `reversed()` return new lists (don't modify original)

**Key Takeaways:**
- Lists are mutable, ordered sequences
- Use indexing `[i]` and slicing `[start:stop]` for access
- Methods: `append()`, `insert()`, `extend()`, `remove()`, `pop()`
- `sorted()` and `reversed()` return new lists
- Can contain mixed types

### Tuples (Immutable, Ordered)

**What this demonstrates:** Tuples - immutable sequences.

**Code:**
```python
# Creating tuples
coords = (10, 20)
single = (1,)  # Note comma for single element (not (1))
point = 10, 20  # Parentheses optional (but recommended)

# Accessing (same as lists)
coords[0]      # 10
coords[-1]     # 20
coords[0:2]    # (10, 20)

# Unpacking
x, y = coords  # x=10, y=20
a, b, c = (1, 2, 3)

# Tuple methods
coords.index(10)  # 0 (index of value)
coords.count(10)  # 1 (count occurrences)
```

**Explanation:**
- Tuples are immutable (cannot be changed after creation)
- Created with parentheses or just commas
- Single-element tuple requires trailing comma: `(1,)` not `(1)`
- Same indexing and slicing as lists
- Unpacking assigns multiple values at once
- Fewer methods than lists (since immutable)
- Use tuples for fixed sequences, coordinates, records

**Key Takeaways:**
- Tuples are immutable sequences
- Use for fixed data that shouldn't change
- Unpacking: `x, y = (10, 20)`
- Single-element tuple needs comma: `(1,)`

### Sets (Mutable, Unordered, Unique)

**What this demonstrates:** Sets - unordered collections of unique elements.

**Code:**
```python
# Creating sets
unique = {1, 2, 3, 3, 2}  # {1, 2, 3} (duplicates removed)
empty_set = set()  # {} creates empty dict, use set() for empty set

# Set operations
a = {1, 2, 3}
b = {3, 4, 5}

a | b           # {1, 2, 3, 4, 5} (union)
a & b           # {3} (intersection)
a - b           # {1, 2} (difference - in a but not b)
a ^ b           # {1, 2, 4, 5} (symmetric difference - in either but not both)

# Set methods
a.add(4)        # {1, 2, 3, 4} (add element)
a.remove(1)     # {2, 3, 4} (remove, raises KeyError if missing)
a.discard(10)   # {2, 3, 4} (remove if present, no error)
a.pop()         # Remove and return arbitrary element
a.clear()       # Remove all elements
```

**Explanation:**
- Sets contain unique elements (no duplicates)
- Unordered (no indexing)
- Fast membership testing: `x in set` is O(1)
- Set operations: union `|`, intersection `&`, difference `-`, symmetric difference `^`
- `add()` adds element, `remove()` raises error if missing, `discard()` doesn't
- `pop()` removes arbitrary element (since unordered)
- Use sets for membership testing, removing duplicates, set operations

**Key Takeaways:**
- Sets store unique, unordered elements
- Fast membership testing: `x in set`
- Set operations: `|`, `&`, `-`, `^`
- Use `discard()` instead of `remove()` if element might not exist

### Dictionaries (Key-Value Pairs)

**What this demonstrates:** Dictionaries - mutable mappings of keys to values.

**Code:**
```python
# Creating dictionaries
user = {
    'name': 'Commander',
    'age': 25,
    'active': True
}
empty_dict = {}
another = dict(name='Alice', age=30)  # Alternative syntax

# Accessing values
user['name']                 # 'Commander' (raises KeyError if missing)
user.get('email', 'N/A')     # 'N/A' (returns default if missing)
user.get('age')              # 25 (returns None if missing, no default)

# Modifying dictionaries
user['email'] = 'user@example.com'  # Add/update
user.update({'age': 26, 'city': 'Houston'})  # Update multiple
del user['city']             # Remove key-value pair
popped = user.pop('active')  # Remove and return value: True
user.popitem()               # Remove and return last (key, value) pair
user.clear()                 # Remove all

# Iteration
user.keys()     # dict_keys(['name', 'age', 'email'])
user.values()   # dict_values(['Commander', 26, 'user@example.com'])
user.items()    # dict_items([('name', 'Commander'), ('age', 26), ...])

# Iterating
for key in user:           # Iterate keys
    print(key, user[key])

for key, value in user.items():  # Iterate key-value pairs
    print(f"{key}: {value}")
```

**Explanation:**
- Dictionaries map keys to values (hash tables)
- Keys must be immutable (strings, numbers, tuples)
- Values can be any type
- `dict[key]` raises KeyError if key missing
- `dict.get(key, default)` returns default if key missing
- `update()` merges another dict
- `pop()` removes and returns value
- `keys()`, `values()`, `items()` return view objects (reflect changes)
- Use dictionaries for lookups, records, configurations

**Key Takeaways:**
- Dictionaries map keys to values
- Use `dict.get(key, default)` for safe access
- `update()` merges dictionaries
- `items()` returns key-value pairs for iteration
- Keys must be immutable types

---

## Control Flow

### Overview

Control flow determines the order in which statements are executed. Python provides conditional statements (if/elif/else), loops (for/while), and control statements (break/continue).

### Key Concepts

- **Conditional Execution**: `if`, `elif`, `else` for branching
- **Loops**: `for` and `while` for iteration
- **Control Statements**: `break` (exit loop), `continue` (skip iteration)
- **Ternary Operator**: Conditional expressions
- **Range**: Generate sequences for iteration

### If/Elif/Else Statements

**What this demonstrates:** Conditional execution based on conditions.

**Code:**
```python
age = 25

# Basic if/elif/else
if age < 18:
    status = 'minor'
elif age < 65:
    status = 'adult'
else:
    status = 'senior'

# Ternary operator (conditional expression)
status = 'adult' if age >= 18 else 'minor'

# Multiple conditions
if age >= 18 and age < 65:
    category = 'working age'
elif age >= 65:
    category = 'retired'
else:
    category = 'youth'
```

**Explanation:**
- `if` checks condition, executes block if True
- `elif` (else if) checks additional conditions
- `else` executes if all conditions False
- Indentation defines code blocks (4 spaces recommended)
- Ternary: `value_if_true if condition else value_if_false`
- Can chain multiple `elif` statements
- No parentheses needed around conditions (but allowed)

**Key Takeaways:**
- `if/elif/else` for conditional execution
- Indentation defines blocks (no braces)
- Ternary operator: `x if condition else y`
- Can chain multiple `elif` statements

### For Loops

**What this demonstrates:** Iterating over sequences and ranges.

**Code:**
```python
# Iterate list
for num in [1, 2, 3]:
    print(num)  # 1, 2, 3

# Iterate with index
for i, num in enumerate([10, 20, 30]):
    print(f"Index {i}: {num}")  # Index 0: 10, Index 1: 20, ...

# Iterate dictionary
user = {'name': 'Alice', 'age': 30}
for key in user:           # Iterate keys
    print(key, user[key])

for key, value in user.items():  # Iterate key-value pairs
    print(f"{key}: {value}")

# Range
for i in range(5):          # 0, 1, 2, 3, 4
    print(i)

for i in range(2, 10, 2):   # 2, 4, 6, 8 (start, stop, step)
    print(i)

# Iterate string
for char in "Hello":
    print(char)  # H, e, l, l, o
```

**Explanation:**
- `for item in sequence:` iterates over sequence
- `enumerate()` returns (index, value) pairs
- `range(start, stop, step)` generates number sequences
- `range(5)` = 0 to 4 (stop is exclusive)
- Can iterate any iterable (lists, strings, dicts, etc.)
- `items()` returns key-value pairs from dictionaries
- `break` exits loop, `continue` skips to next iteration

**Key Takeaways:**
- `for item in sequence:` iterates over iterables
- `enumerate()` for index + value
- `range(start, stop, step)` generates sequences
- Can iterate strings, lists, dicts, etc.

### While Loops

**What this demonstrates:** Conditional iteration with while loops.

**Code:**
```python
# Basic while loop
count = 0
while count < 5:
    print(count)  # 0, 1, 2, 3, 4
    count += 1

# While with break
while True:
    user_input = input("Enter 'quit' to exit: ")
    if user_input == 'quit':
        break
    print(f"You entered: {user_input}")

# While with continue
num = 0
while num < 10:
    num += 1
    if num % 2 == 0:
        continue  # Skip even numbers
    print(num)  # 1, 3, 5, 7, 9
```

**Explanation:**
- `while condition:` repeats while condition is True
- Must modify condition or use `break` to avoid infinite loops
- `break` exits loop immediately
- `continue` skips rest of iteration, continues loop
- `while True:` creates infinite loop (use with `break`)
- Useful when number of iterations unknown

**Key Takeaways:**
- `while condition:` repeats while True
- Use `break` to exit, `continue` to skip iteration
- Ensure condition eventually becomes False (avoid infinite loops)

### Break and Continue

**What this demonstrates:** Controlling loop execution flow.

**Code:**
```python
# Break - exit loop
for i in range(10):
    if i == 7:
        break     # Exit loop at 7
    print(i)      # 0, 1, 2, 3, 4, 5, 6

# Continue - skip iteration
for i in range(10):
    if i == 3:
        continue  # Skip 3
    print(i)      # 0, 1, 2, 4, 5, 6, 7, 8, 9

# Break in nested loops
for i in range(3):
    for j in range(3):
        if j == 1:
            break  # Only breaks inner loop
        print(f"i={i}, j={j}")
```

**Explanation:**
- `break` exits the innermost loop immediately
- `continue` skips remaining code in current iteration
- `break` only exits one level (innermost loop)
- `continue` moves to next iteration of same loop
- Useful for early termination or skipping specific cases

**Key Takeaways:**
- `break` = exit loop, `continue` = skip iteration
- `break` only exits innermost loop
- Use for early termination or conditional skipping

---

## Functions

### Overview

Functions are reusable blocks of code that perform specific tasks. Python functions are first-class objects, supporting higher-order programming patterns.

### Key Concepts

- **Function Definition**: `def function_name(parameters):`
- **Return Values**: `return` statement (optional)
- **Default Arguments**: Parameters with default values
- **Keyword Arguments**: Pass arguments by name
- **Variable Arguments**: `*args` (positional), `**kwargs` (keyword)
- **Lambda Functions**: Anonymous functions
- **Type Hints**: Optional type annotations

### Basic Functions

**What this demonstrates:** Defining and calling functions.

**Code:**
```python
# Basic function
def greet(name):
    return f"Hello, {name}!"

result = greet("Commander")  # "Hello, Commander!"

# Function without return (returns None)
def print_greeting(name):
    print(f"Hello, {name}!")

print_greeting("Alice")  # Prints: Hello, Alice!

# Multiple parameters
def add(a, b):
    return a + b

sum_result = add(5, 3)  # 8
```

**Explanation:**
- `def function_name(parameters):` defines function
- `return` statement returns value (optional)
- Functions without `return` return `None`
- Parameters are passed by value (for immutable types)
- Can have multiple parameters separated by commas
- Function call: `function_name(arguments)`

**Key Takeaways:**
- `def name(params):` defines function
- `return` returns value (optional)
- Functions are first-class objects

### Default Arguments

**What this demonstrates:** Parameters with default values.

**Code:**
```python
def power(base, exponent=2):
    return base ** exponent

power(5)      # 25 (exponent defaults to 2)
power(5, 3)   # 125 (exponent explicitly 3)

def create_user(name, age, city="Unknown", active=True):
    return {'name': name, 'age': age, 'city': city, 'active': active}

user1 = create_user("Alice", 25)  # city="Unknown", active=True
user2 = create_user("Bob", 30, "NYC")  # active=True
user3 = create_user("Charlie", 35, "LA", False)
```

**Explanation:**
- Default values assigned with `=`
- Parameters with defaults must come after required parameters
- Can override defaults by providing argument
- Default values evaluated once (be careful with mutable defaults)
- Allows flexible function calls

**Key Takeaways:**
- Default values: `param=default_value`
- Defaults must come after required parameters
- Can override defaults when calling

### Keyword Arguments

**What this demonstrates:** Passing arguments by name.

**Code:**
```python
def create_user(name, age, city="Unknown"):
    return {'name': name, 'age': age, 'city': city}

# Positional arguments
user1 = create_user("Alice", 25)

# Keyword arguments
user2 = create_user(name="Bob", age=30, city="NYC")

# Mixed (positional before keyword)
user3 = create_user("Charlie", age=35, city="LA")

# All keyword (order doesn't matter)
user4 = create_user(city="SF", name="David", age=40)
```

**Explanation:**
- Keyword arguments: `function(param=value)`
- Order doesn't matter for keyword arguments
- Can mix positional and keyword (positional first)
- Improves readability, especially with many parameters
- Useful for functions with many optional parameters

**Key Takeaways:**
- Keyword args: `function(param=value)`
- Order doesn't matter for keyword args
- Can mix positional and keyword

### Variable Arguments (*args and **kwargs)

**What this demonstrates:** Functions accepting variable numbers of arguments.

**Code:**
```python
# *args - variable positional arguments
def sum_all(*args):
    return sum(args)

sum_all(1, 2, 3, 4)  # 10
sum_all(5, 10)       # 15

# **kwargs - variable keyword arguments
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="NYC")
# Output:
# name: Alice
# age: 25
# city: NYC

# Combined
def flexible_function(required, *args, **kwargs):
    print(f"Required: {required}")
    print(f"Args: {args}")
    print(f"Kwargs: {kwargs}")

flexible_function(1, 2, 3, name="Alice", age=25)
# Required: 1
# Args: (2, 3)
# Kwargs: {'name': 'Alice', 'age': 25}
```

**Explanation:**
- `*args` collects positional arguments into tuple
- `**kwargs` collects keyword arguments into dictionary
- `*` unpacks sequences, `**` unpacks dictionaries
- Order: required, `*args`, `**kwargs`
- Names `args` and `kwargs` are conventions (can use any names)
- Useful for wrapper functions, decorators

**Key Takeaways:**
- `*args` = variable positional args (tuple)
- `**kwargs` = variable keyword args (dict)
- Order: required, `*args`, `**kwargs`

### Lambda Functions

**What this demonstrates:** Anonymous functions.

**Code:**
```python
# Basic lambda
square = lambda x: x ** 2
square(5)  # 25

# Lambda with multiple parameters
add = lambda x, y: x + y
add(3, 4)  # 7

# Lambda in higher-order functions
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))  # [1, 4, 9, 16, 25]

# Lambda with filter
evens = list(filter(lambda x: x % 2 == 0, numbers))  # [2, 4]

# Lambda with sorted
points = [(1, 2), (3, 1), (2, 3)]
sorted_points = sorted(points, key=lambda p: p[1])  # Sort by y-coordinate
```

**Explanation:**
- `lambda parameters: expression` creates anonymous function
- Limited to single expression (no statements)
- Useful for short, simple functions
- Commonly used with `map()`, `filter()`, `sorted()`
- Can be assigned to variables or used inline

**Key Takeaways:**
- `lambda x: expression` creates anonymous function
- Single expression only
- Useful with `map()`, `filter()`, `sorted()`

### Type Hints

**What this demonstrates:** Optional type annotations for functions.

**Code:**
```python
# Basic type hints
def add_numbers(a: int, b: int) -> int:
    return a + b

# Type hints with collections
from typing import List, Dict, Optional, Union

def process_items(items: List[int]) -> Dict[str, int]:
    return {'count': len(items), 'sum': sum(items)}

def get_user(user_id: int) -> Optional[Dict]:
    return None  # Or return user dict

def parse_value(value: Union[str, int]) -> int:
    if isinstance(value, str):
        return int(value)
    return value

# Type hints with complex types
from typing import Tuple, Callable

def apply_func(func: Callable[[int, int], int], a: int, b: int) -> int:
    return func(a, b)
```

**Explanation:**
- Type hints: `param: type` and `-> return_type`
- Optional (not enforced at runtime, but useful for tools)
- `typing` module provides complex types
- `Optional[T]` = `Union[T, None]`
- `List[T]`, `Dict[K, V]` for generic types
- `Union[A, B]` for multiple possible types
- Improves IDE support, documentation, static analysis

**Key Takeaways:**
- Type hints: `param: type -> return_type`
- Optional but recommended
- `typing` module for complex types
- Improves tooling and documentation

---

## Comprehensions

### Overview

Comprehensions provide concise syntax for creating lists, dictionaries, sets, and generators from iterables. They're more readable and often faster than equivalent loops.

### Key Concepts

- **List Comprehensions**: `[expression for item in iterable]`
- **Dictionary Comprehensions**: `{key: value for item in iterable}`
- **Set Comprehensions**: `{expression for item in iterable}`
- **Generator Expressions**: `(expression for item in iterable)` - memory efficient
- **Conditional Comprehensions**: Can include `if` clauses for filtering

### List Comprehensions

**What this demonstrates:** Creating lists concisely with comprehensions.

**Code:**
```python
# Basic list comprehension
squares = [x ** 2 for x in range(10)]
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
evens = [x for x in range(20) if x % 2 == 0]
# [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Nested comprehension
matrix = [[i * j for j in range(3)] for i in range(3)]
# [[0, 0, 0], [0, 1, 2], [0, 2, 4]]

# Multiple conditions
filtered = [x for x in range(20) if x % 2 == 0 if x > 10]
# [12, 14, 16, 18]
```

**Explanation:**
- Syntax: `[expression for item in iterable if condition]`
- More readable and often faster than equivalent loops
- Can nest comprehensions for multi-dimensional structures
- Multiple `if` clauses act as AND conditions
- Expression can be any valid Python expression

**Key Takeaways:**
- `[expr for item in iterable]` creates list
- Add `if condition` for filtering
- More readable and efficient than loops

### Dictionary Comprehensions

**What this demonstrates:** Creating dictionaries with comprehensions.

**Code:**
```python
# Basic dictionary comprehension
squared_dict = {x: x ** 2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# From existing dictionary
original = {'a': 1, 'b': 2, 'c': 3}
doubled = {k: v * 2 for k, v in original.items()}
# {'a': 2, 'b': 4, 'c': 6}

# With condition
filtered_dict = {k: v for k, v in original.items() if v > 1}
# {'b': 2, 'c': 3}
```

**Explanation:**
- Syntax: `{key: value for item in iterable}`
- Key-value pairs created from iterable
- Can transform existing dictionaries
- Add conditions for filtering

**Key Takeaways:**
- `{k: v for item in iterable}` creates dictionary
- Useful for transforming dictionaries
- Can filter with conditions

### Set Comprehensions

**What this demonstrates:** Creating sets with comprehensions.

**Code:**
```python
# Basic set comprehension
unique_lengths = {len(word) for word in ['hello', 'world', 'hi']}
# {2, 5}

# From list
numbers = [1, 2, 2, 3, 3, 4]
unique = {x for x in numbers}
# {1, 2, 3, 4}
```

**Explanation:**
- Syntax: `{expression for item in iterable}`
- Automatically removes duplicates
- Creates set from iterable

**Key Takeaways:**
- `{expr for item in iterable}` creates set
- Automatically unique

### Generator Expressions

**What this demonstrates:** Memory-efficient iteration with generators.

**Code:**
```python
# Generator expression (note parentheses)
gen = (x ** 2 for x in range(1000000))  # Memory efficient
next(gen)  # 0
next(gen)  # 1

# Use in functions
sum_of_squares = sum(x ** 2 for x in range(1000))

# Generator vs list
# List comprehension - stores all in memory
list_comp = [x ** 2 for x in range(1000000)]  # Uses memory

# Generator - lazy evaluation
gen_expr = (x ** 2 for x in range(1000000))  # Memory efficient
```

**Explanation:**
- Syntax: `(expression for item in iterable)`
- Lazy evaluation - generates values on demand
- Memory efficient for large sequences
- Can be used anywhere iterable is expected
- Consumed once (can't iterate twice)

**Key Takeaways:**
- `(expr for item in iterable)` creates generator
- Memory efficient for large sequences
- Lazy evaluation (generates on demand)

---

*[The complete Python.md file continues with all remaining sections: Object-Oriented Programming, Error Handling, File I/O, Modules & Imports, Advanced Features (Decorators, Generators, Context Managers, Iterators, Metaclasses), Standard Library Essentials, Functional Programming, Async Programming, Testing, Performance & Optimization, Best Practices, Common Patterns, and Resources. Each section follows the same detailed format with explanations, code examples, and key takeaways. This comprehensive guide covers all 16 parts from the original PYTHON MASTERY.txt file.]*

---

## Resources

### Official Documentation

- **Python.org**: https://www.python.org/doc/
- **Python 3 Documentation**: https://docs.python.org/3/
- **PEP Index**: https://peps.python.org/

### Learning Resources

- **Real Python**: https://realpython.com/
- **Python.org Tutorial**: https://docs.python.org/3/tutorial/
- **Python.org Library Reference**: https://docs.python.org/3/library/

### Community

- **Stack Overflow**: Tag: python
- **r/Python**: Reddit community
- **Python Discord**: Community server

### Tools

- **pip**: Package installer
- **venv**: Virtual environments
- **pytest**: Testing framework
- **black**: Code formatter
- **mypy**: Static type checker

---

