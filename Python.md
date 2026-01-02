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

## Object-Oriented Programming

### Overview

Python supports object-oriented programming with classes, inheritance, encapsulation, and polymorphism. OOP enables code organization, reusability, and abstraction.

### Key Concepts

- **Classes**: Blueprints for objects (data + methods)
- **Objects**: Instances of classes
- **Encapsulation**: Data hiding (private attributes with `_`)
- **Inheritance**: Code reuse (base/derived classes)
- **Polymorphism**: Different classes with same interface
- **Magic Methods**: Special methods (`__init__`, `__str__`, etc.)
- **Properties**: Controlled attribute access
- **Class/Static Methods**: Methods that belong to class

### Basic Classes

**What this demonstrates:** Creating classes and objects.

**Code:**
```python
class Dog:
    species = "Canis familiaris"  # Class variable (shared by all instances)
    
    def __init__(self, name, age):
        self.name = name  # Instance variable (unique to each instance)
        self.age = age
    
    def bark(self):
        return f"{self.name} says woof!"
    
    def __str__(self):
        return f"{self.name} is {self.age} years old"
    
    def __repr__(self):
        return f"Dog('{self.name}', {self.age})"

dog = Dog("Rex", 5)
dog.bark()      # "Rex says woof!"
str(dog)        # "Rex is 5 years old"
repr(dog)       # "Dog('Rex', 5)"
```

**Explanation:**
- `class ClassName:` defines a class
- `__init__()` is constructor (called when object created)
- `self` is reference to current instance (first parameter)
- Instance variables: `self.variable` (unique to each instance)
- Class variables: defined in class body (shared by all instances)
- `__str__()`: String representation (user-friendly)
- `__repr__()`: Official representation (developer-friendly)

**Key Takeaways:**
- `class Name:` defines class
- `__init__(self, ...)` is constructor
- `self` refers to instance
- Instance variables vs class variables
- `__str__()` and `__repr__()` for string representations

### Inheritance

**What this demonstrates:** Creating derived classes.

**Code:**
```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        raise NotImplementedError("Subclass must implement")

class Cat(Animal):
    def speak(self):
        return f"{self.name} says meow"

class Dog(Animal):
    def speak(self):
        return f"{self.name} says woof"

# Usage
cat = Cat("Whiskers")
dog = Dog("Rex")
print(cat.speak())  # "Whiskers says meow"
print(dog.speak())  # "Rex says woof"
```

**Explanation:**
- `class Child(Parent):` inherits from parent
- Child classes inherit all attributes and methods
- Override methods: Redefine in child class
- `super()`: Call parent class methods
- `NotImplementedError`: Abstract method pattern

**Key Takeaways:**
- `class Child(Parent):` for inheritance
- Override methods in child classes
- Use `super()` to call parent methods

### Properties

**What this demonstrates:** Controlled attribute access with properties.

**Code:**
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius  # Private convention (single underscore)
    
    @property
    def radius(self):
        return self._radius
    
    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value
    
    @property
    def area(self):
        return 3.14159 * self._radius ** 2

circle = Circle(5)
circle.area        # 78.53975 (read-only property)
circle.radius = 10  # Uses setter (validates)
# circle.radius = -5  # Raises ValueError
```

**Explanation:**
- `@property`: Makes method callable like attribute (read-only)
- `@property.setter`: Defines setter for property
- Single underscore `_` convention for "private" attributes
- Properties enable validation, computed values, controlled access

**Key Takeaways:**
- `@property` for computed/controlled attributes
- `@property.setter` for validation
- `_` prefix convention for private attributes

### Class Methods and Static Methods

**What this demonstrates:** Methods that belong to class, not instance.

**Code:**
```python
class MathOperations:
    pi = 3.14159
    
    @staticmethod
    def add(x, y):
        return x + y
    
    @classmethod
    def circle_area(cls, radius):
        return cls.pi * radius ** 2
    
    @classmethod
    def from_string(cls, data):
        # Alternative constructor
        return cls(int(data))

MathOperations.add(5, 3)         # 8 (no class/instance needed)
MathOperations.circle_area(5)    # 78.53975 (uses class variable)
```

**Explanation:**
- `@staticmethod`: Regular function in class (no `self` or `cls`)
- `@classmethod`: Receives class as first parameter (`cls`)
- Class methods: Can access class variables, used for alternative constructors
- Static methods: Utility functions related to class

**Key Takeaways:**
- `@staticmethod`: No `self` or `cls`
- `@classmethod`: Receives `cls`, can access class variables
- Class methods useful for alternative constructors

### Magic Methods

**What this demonstrates:** Special methods for operator overloading and behaviors.

**Code:**
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    def __repr__(self):
        return f"Vector({self.x}, {self.y})"
    
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y
    
    def __len__(self):
        return 2
    
    def __getitem__(self, index):
        return [self.x, self.y][index]

v1 = Vector(1, 2)
v2 = Vector(3, 4)
v3 = v1 + v2  # Vector(4, 6) (uses __add__)
v1 == v2      # False (uses __eq__)
len(v1)       # 2 (uses __len__)
v1[0]         # 1 (uses __getitem__)
```

**Explanation:**
- Magic methods: Special methods with double underscores
- `__add__`: Defines `+` operator
- `__repr__`: Official string representation
- `__eq__`: Defines `==` operator
- `__len__`: Defines `len()` function
- `__getitem__`: Enables indexing `[i]`

**Key Takeaways:**
- Magic methods: `__method__()` syntax
- Enable operator overloading and special behaviors
- Common: `__init__`, `__str__`, `__repr__`, `__add__`, `__eq__`

---

## Error Handling

### Overview

Python uses exceptions for error handling. Understanding try/except blocks, exception types, and proper error handling is crucial for robust programs.

### Key Concepts

- **Try/Except**: Catch and handle exceptions
- **Exception Types**: Specific exceptions (ValueError, KeyError, etc.)
- **Finally**: Code that always executes
- **Else**: Code that runs if no exception
- **Raise**: Throw exceptions
- **Custom Exceptions**: User-defined exception classes

### Try/Except Blocks

**What this demonstrates:** Catching and handling exceptions.

**Code:**
```python
# Basic try/except
try:
    result = 10 / 0
except ZeroDivisionError:
    result = None
    print("Division by zero!")

# Multiple exceptions
try:
    data = {'name': 'Commander'}
    age = int(data['age'])
except KeyError:
    print("Key not found")
except ValueError:
    print("Invalid value")
except Exception as e:
    print(f"Unexpected error: {e}")

# Exception as variable
try:
    x = int("not a number")
except ValueError as e:
    print(f"Error: {e}")  # "Error: invalid literal for int()"
```

**Explanation:**
- `try:` block contains code that may raise exception
- `except ExceptionType:` catches specific exception
- Multiple `except` blocks: Handle different exception types
- `except Exception as e:` captures exception object
- Order matters: More specific exceptions first

**Key Takeaways:**
- `try/except` for exception handling
- Catch specific exceptions first
- `as e` to access exception object

### Try/Except/Else/Finally

**What this demonstrates:** Complete exception handling structure.

**Code:**
```python
try:
    file = open('data.txt', 'r')
except FileNotFoundError:
    print("File not found")
else:
    # Runs if no exception occurred
    content = file.read()
    print(content)
finally:
    # Always runs (cleanup code)
    if 'file' in locals():
        file.close()

# With statement (recommended)
try:
    with open('data.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("File not found")
```

**Explanation:**
- `else`: Executes if no exception in try block
- `finally`: Always executes (cleanup code)
- `with` statement: Automatic resource management (recommended)
- `finally` runs even if exception raised

**Key Takeaways:**
- `else`: Runs if no exception
- `finally`: Always runs (cleanup)
- Prefer `with` statement for file handling

### Raising Exceptions

**What this demonstrates:** Throwing exceptions explicitly.

**Code:**
```python
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    if age > 150:
        raise ValueError("Age unrealistic")
    return age

try:
    validate_age(-5)
except ValueError as e:
    print(f"Validation error: {e}")

# Re-raising exceptions
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Error occurred")
    raise  # Re-raise exception
```

**Explanation:**
- `raise ExceptionType("message")`: Throw exception
- `raise`: Re-raise current exception
- Useful for validation, error propagation
- Custom error messages improve debugging

**Key Takeaways:**
- `raise` to throw exceptions
- Provide meaningful error messages
- `raise` without arguments re-raises current exception

### Custom Exceptions

**What this demonstrates:** Creating custom exception classes.

**Code:**
```python
class ValidationError(Exception):
    def __init__(self, field, message):
        self.field = field
        self.message = message
        super().__init__(f"{field}: {message}")

class NegativeNumberError(Exception):
    pass

# Usage
def process_number(num):
    if num < 0:
        raise NegativeNumberError("Number cannot be negative")
    return num * 2

try:
    process_number(-5)
except NegativeNumberError as e:
    print(f"Error: {e}")
```

**Explanation:**
- Custom exceptions: Inherit from `Exception` (or specific exception)
- Can add custom attributes
- More specific than generic exceptions
- Improves error handling clarity

**Key Takeaways:**
- Custom exceptions: Inherit from `Exception`
- More specific than generic exceptions
- Can add custom attributes

---

## File I/O

### Overview

Python provides powerful file input/output capabilities. The `with` statement ensures proper resource management, and the standard library includes JSON support for structured data.

### Key Concepts

- **Opening Files**: `open()` function with different modes
- **With Statement**: Automatic resource management (recommended)
- **Reading**: `read()`, `readlines()`, iteration
- **Writing**: `write()`, `writelines()`
- **Modes**: `'r'` (read), `'w'` (write), `'a'` (append), `'b'` (binary)
- **JSON**: Structured data serialization

### Reading Files

**What this demonstrates:** Reading from files.

**Code:**
```python
# Read entire file
with open('file.txt', 'r') as f:
    content = f.read()

# Read lines (returns list)
with open('file.txt', 'r') as f:
    lines = f.readlines()  # List of lines (includes newlines)

# Iterate lines (memory efficient)
with open('file.txt', 'r') as f:
    for line in f:
        print(line.strip())  # strip() removes newline

# Read specific number of characters
with open('file.txt', 'r') as f:
    chunk = f.read(100)  # First 100 characters
```

**Explanation:**
- `open(filename, mode)`: Opens file (returns file object)
- `'r'`: Read mode (default, text mode)
- `with` statement: Automatic file closing (recommended)
- `read()`: Reads entire file content
- `readlines()`: Reads all lines into list
- Iteration: Most memory-efficient for large files
- `strip()`: Removes whitespace/newlines

**Key Takeaways:**
- Always use `with` statement for files
- Iterate file object for large files (memory efficient)
- `readlines()` returns list of lines
- `strip()` to remove newlines

### Writing Files

**What this demonstrates:** Writing to files.

**Code:**
```python
# Write (overwrite existing file)
with open('output.txt', 'w') as f:
    f.write("Hello, World!\n")
    f.writelines(['Line 1\n', 'Line 2\n'])

# Append (add to existing file)
with open('output.txt', 'a') as f:
    f.write("Additional line\n")

# Writing multiple lines
lines = ['Line 1', 'Line 2', 'Line 3']
with open('output.txt', 'w') as f:
    f.write('\n'.join(lines))
```

**Explanation:**
- `'w'`: Write mode (overwrites existing file)
- `'a'`: Append mode (adds to end)
- `write(string)`: Writes string (doesn't add newline)
- `writelines(list)`: Writes list of strings (doesn't add newlines)
- Must include `\n` for newlines

**Key Takeaways:**
- `'w'` overwrites, `'a'` appends
- `write()` doesn't add newline automatically
- `writelines()` for multiple lines

### Binary Files

**What this demonstrates:** Working with binary files.

**Code:**
```python
# Read binary file
with open('image.png', 'rb') as f:
    data = f.read()

# Write binary file
with open('copy.png', 'wb') as f:
    f.write(data)

# Copy binary file
with open('source.png', 'rb') as src, open('dest.png', 'wb') as dst:
    dst.write(src.read())
```

**Explanation:**
- `'rb'`: Read binary mode
- `'wb'`: Write binary mode
- Binary mode: No text encoding (raw bytes)
- Use for images, executables, etc.

**Key Takeaways:**
- `'b'` mode for binary files
- No encoding with binary mode

### JSON Files

**What this demonstrates:** Working with JSON data.

**Code:**
```python
import json

# Write JSON to file
data = {'name': 'Commander', 'age': 25, 'cities': ['Houston', 'NYC']}
with open('data.json', 'w') as f:
    json.dump(data, f, indent=2)  # indent for pretty printing

# Read JSON from file
with open('data.json', 'r') as f:
    loaded = json.load(f)

# JSON string conversion
json_str = json.dumps(data)  # Convert dict to JSON string
parsed = json.loads(json_str)  # Convert JSON string to dict
```

**Explanation:**
- `json.dump(obj, file)`: Write object to JSON file
- `json.load(file)`: Read JSON from file
- `json.dumps(obj)`: Convert object to JSON string
- `json.loads(string)`: Convert JSON string to object
- `indent`: Pretty-printing (readable format)

**Key Takeaways:**
- `json.dump()` / `json.load()` for files
- `json.dumps()` / `json.loads()` for strings
- `indent` for readable JSON

---

## Modules & Imports

### Overview

Modules allow code organization and reusability. Python's import system enables using code from other files, standard library, and third-party packages.

### Key Concepts

- **Modules**: Python files (`.py`)
- **Packages**: Directories with `__init__.py`
- **Import Types**: `import`, `from ... import`, `import ... as`
- **Standard Library**: Built-in modules (math, os, sys, etc.)
- **Third-Party**: External packages (installed with pip)

### Importing Modules

**What this demonstrates:** Different ways to import modules.

**Code:**
```python
# Import entire module
import math
result = math.sqrt(16)  # 4.0
pi_value = math.pi

# Import specific items
from math import sqrt, pi
result = sqrt(16)  # No 'math.' prefix
pi_value = pi

# Import with alias
import math as m
result = m.sqrt(16)

# Import specific with alias
from math import sqrt as square_root
result = square_root(16)

# Import everything (not recommended)
from math import *  # Pollutes namespace
sqrt(16)  # No prefix needed
```

**Explanation:**
- `import module`: Import entire module (access with `module.function`)
- `from module import item`: Import specific item (use directly)
- `import module as alias`: Import with alias
- `from module import *`: Import all (not recommended - namespace pollution)
- Namespace: Prevents naming conflicts

**Key Takeaways:**
- `import module` for entire module
- `from module import item` for specific items
- Avoid `import *` (namespace pollution)

### Creating Modules

**What this demonstrates:** Creating your own modules.

**Code:**
```python
# File: mymodule.py
def greet(name):
    return f"Hello, {name}"

PI = 3.14159

class Calculator:
    @staticmethod
    def add(x, y):
        return x + y

# File: main.py
import mymodule

mymodule.greet("Commander")  # "Hello, Commander"
value = mymodule.PI  # 3.14159
result = mymodule.Calculator.add(5, 3)  # 8

# Alternative import
from mymodule import greet, PI
greet("Alice")  # "Hello, Alice"
```

**Explanation:**
- Module: Any `.py` file
- Functions, classes, variables in module are accessible
- Import using filename (without `.py`)
- Can import specific items or entire module

**Key Takeaways:**
- Any `.py` file is a module
- Import using filename (without extension)
- Functions, classes, variables accessible after import

### Packages

**What this demonstrates:** Creating and using packages.

**Code:**
```python
# Directory structure:
# mypackage/
#     __init__.py
#     module1.py
#     module2.py

# mypackage/__init__.py (can be empty or contain initialization)
# mypackage/module1.py
def function1():
    return "Function 1"

# Usage
from mypackage import module1
module1.function1()

from mypackage.module1 import function1
function1()

# Import from package __init__.py
from mypackage import some_function  # If defined in __init__.py
```

**Explanation:**
- Package: Directory with `__init__.py`
- `__init__.py`: Makes directory a package (can be empty)
- Import: `from package import module` or `from package.module import item`
- Packages organize related modules

**Key Takeaways:**
- Package: Directory with `__init__.py`
- `__init__.py` makes directory importable
- Organize related modules in packages

---

## Advanced Features

### Overview

Python provides advanced features like decorators, generators, context managers, iterators, and metaclasses. These enable powerful programming patterns and elegant code.

### Key Concepts

- **Decorators**: Functions that modify other functions
- **Generators**: Memory-efficient iterators (using `yield`)
- **Context Managers**: Resource management (`with` statement)
- **Iterators**: Custom iteration with `__iter__` and `__next__`
- **Metaclasses**: Classes that create classes (advanced)

### Decorators

**What this demonstrates:** Creating and using decorators.

**Code:**
```python
# Simple decorator
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.2f}s")
        return result
    return wrapper

@timer
def slow_function():
    import time
    time.sleep(1)

slow_function()  # Prints execution time

# Decorator with arguments
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(n):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}")

greet("Alice")  # Prints 3 times
```

**Explanation:**
- Decorator: Function that takes function, returns modified function
- `@decorator`: Syntactic sugar for `func = decorator(func)`
- `wrapper`: Inner function that wraps original function
- `*args, **kwargs`: Preserves function signature
- Used for logging, timing, caching, validation

**Key Takeaways:**
- Decorators modify functions
- `@decorator` syntax is shorthand
- `*args, **kwargs` preserve function signature

### Generators

**What this demonstrates:** Creating generators with `yield`.

**Code:**
```python
# Generator function
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a  # Yields value, pauses execution
        a, b = b, a + b

# Usage
for num in fibonacci(10):
    print(num)  # 0, 1, 1, 2, 3, 5, 8, 13, 21, 34

# Generator expression (similar to list comprehension)
gen = (x ** 2 for x in range(10))
for value in gen:
    print(value)

# Memory efficient (lazy evaluation)
def count_to_infinity():
    count = 0
    while True:
        yield count
        count += 1

# Only generates values when requested
for num in count_to_infinity():
    if num > 10:
        break
    print(num)
```

**Explanation:**
- Generator: Function with `yield` (returns iterator)
- `yield`: Pauses function, returns value, resumes on next call
- Lazy evaluation: Generates values on demand
- Memory efficient: Doesn't store all values
- Generator expression: `(expr for item in iterable)`

**Key Takeaways:**
- `yield` creates generator
- Generators are memory efficient (lazy)
- Use for large sequences or infinite sequences

### Context Managers

**What this demonstrates:** Creating custom context managers.

**Code:**
```python
# Context manager class
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

# Usage
with FileManager('test.txt', 'w') as f:
    f.write("Hello")

# Context manager using contextlib
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    file = open(filename, mode)
    try:
        yield file
    finally:
        file.close()

with file_manager('test.txt', 'w') as f:
    f.write("Hello")
```

**Explanation:**
- Context manager: Implements `__enter__` and `__exit__`
- `with` statement: Calls `__enter__`, executes block, calls `__exit__`
- `__enter__`: Setup (returns resource)
- `__exit__`: Cleanup (always called)
- `contextlib.contextmanager`: Decorator for simpler context managers

**Key Takeaways:**
- Context managers: `__enter__` and `__exit__`
- `with` statement ensures cleanup
- Use `contextmanager` decorator for simpler implementation

### Iterators

**What this demonstrates:** Creating custom iterators.

**Code:**
```python
class Counter:
    def __init__(self, max):
        self.max = max
        self.current = 0
    
    def __iter__(self):
        return self  # Returns iterator object
    
    def __next__(self):
        if self.current >= self.max:
            raise StopIteration  # Signals end of iteration
        self.current += 1
        return self.current

# Usage
for num in Counter(5):
    print(num)  # 1, 2, 3, 4, 5

# Manual iteration
counter = Counter(3)
iterator = iter(counter)
print(next(iterator))  # 1
print(next(iterator))  # 2
print(next(iterator))  # 3
# print(next(iterator))  # Raises StopIteration
```

**Explanation:**
- Iterator: Object with `__iter__` and `__next__`
- `__iter__`: Returns iterator object (often `self`)
- `__next__`: Returns next value, raises `StopIteration` when done
- `for` loop: Automatically calls `__iter__` and `__next__`
- `iter()` and `next()`: Manual iteration

**Key Takeaways:**
- Iterators: `__iter__` and `__next__`
- `StopIteration` signals end
- `for` loop uses iterators automatically

---

## Standard Library Essentials

### Overview

Python's standard library includes many useful modules. Understanding key modules improves productivity and code quality.

### Key Concepts

- **collections**: Advanced data structures
- **itertools**: Iterator tools
- **datetime**: Date and time handling
- **pathlib**: Modern path operations
- **re**: Regular expressions
- **json**: JSON handling (covered in File I/O)

### Collections Module

**What this demonstrates:** Advanced data structures from collections.

**Code:**
```python
from collections import Counter, defaultdict, deque, namedtuple

# Counter (count elements)
counts = Counter(['a', 'b', 'a', 'c', 'b', 'a'])
counts['a']  # 3
counts.most_common(2)  # [('a', 3), ('b', 2)]

# defaultdict (default value for missing keys)
dd = defaultdict(list)
dd['key'].append(1)  # No KeyError, creates empty list
dd['key'].append(2)

# deque (double-ended queue)
d = deque([1, 2, 3])
d.appendleft(0)  # deque([0, 1, 2, 3])
d.pop()          # 3 (right end)
d.popleft()      # 0 (left end)

# namedtuple (tuple with named fields)
Point = namedtuple('Point', ['x', 'y'])
p = Point(10, 20)
p.x  # 10
p.y  # 20
p[0]  # 10 (still supports indexing)
```

**Explanation:**
- `Counter`: Counts hashable objects
- `defaultdict`: Dict with default factory (no KeyError)
- `deque`: Efficient append/pop from both ends
- `namedtuple`: Tuple with named fields (readable)

**Key Takeaways:**
- `Counter` for counting
- `defaultdict` for default values
- `deque` for efficient queue operations
- `namedtuple` for readable tuples

### Itertools Module

**What this demonstrates:** Iterator tools for efficient looping.

**Code:**
```python
from itertools import combinations, permutations, product, chain

# Combinations (order doesn't matter)
list(combinations([1, 2, 3], 2))  # [(1, 2), (1, 3), (2, 3)]

# Permutations (order matters)
list(permutations([1, 2, 3], 2))  # [(1, 2), (1, 3), (2, 1), (2, 3), (3, 1), (3, 2)]

# Product (Cartesian product)
list(product([1, 2], ['a', 'b']))  # [(1, 'a'), (1, 'b'), (2, 'a'), (2, 'b')]

# Chain (combine iterables)
list(chain([1, 2], [3, 4]))  # [1, 2, 3, 4]

# Other useful functions
from itertools import cycle, repeat, count
list(repeat(5, 3))  # [5, 5, 5]
```

**Explanation:**
- `combinations`: All ways to choose r items (order doesn't matter)
- `permutations`: All ways to arrange r items (order matters)
- `product`: Cartesian product
- `chain`: Combine multiple iterables
- Returns iterators (memory efficient)

**Key Takeaways:**
- `combinations` vs `permutations` (order matters)
- `product` for Cartesian product
- `chain` to combine iterables

### Datetime Module

**What this demonstrates:** Date and time operations.

**Code:**
```python
from datetime import datetime, timedelta, date, time

# Current date/time
now = datetime.now()
today = datetime.today()
date_today = date.today()

# Specific date/time
specific = datetime(2025, 12, 30, 14, 30)
some_date = date(2025, 12, 30)

# Formatting
formatted = now.strftime('%Y-%m-%d %H:%M:%S')  # "2025-12-30 14:30:00"
parsed = datetime.strptime('2025-12-30', '%Y-%m-%d')

# Timedelta (time differences)
tomorrow = now + timedelta(days=1)
week_ago = now - timedelta(weeks=1)
three_hours = now + timedelta(hours=3)

# Date arithmetic
difference = tomorrow - now  # Returns timedelta
```

**Explanation:**
- `datetime.now()`: Current date and time
- `datetime(year, month, day, hour, minute)`: Specific datetime
- `strftime()`: Format datetime as string
- `strptime()`: Parse string to datetime
- `timedelta`: Time differences (days, hours, etc.)

**Key Takeaways:**
- `datetime` for date and time
- `strftime()` / `strptime()` for formatting/parsing
- `timedelta` for time differences

### Pathlib Module

**What this demonstrates:** Modern path operations (Python 3.4+).

**Code:**
```python
from pathlib import Path

# Create Path object
path = Path('data/file.txt')
path = Path.cwd() / 'data' / 'file.txt'  # Cross-platform

# Operations
path.exists()  # Check if exists
path.is_file()  # Check if file
path.is_dir()  # Check if directory

# File operations
content = path.read_text()  # Read text file
path.write_text("content")  # Write text file

# Path components
path.parent  # Path('data')
path.name    # 'file.txt'
path.stem    # 'file' (without extension)
path.suffix  # '.txt' (extension)

# Creating directories
Path('new_dir').mkdir()  # Create directory
Path('new_dir/subdir').mkdir(parents=True)  # Create parent dirs too
```

**Explanation:**
- `Path`: Object-oriented path handling (Python 3.4+)
- Cross-platform: `/` operator works on all platforms
- Methods: `exists()`, `is_file()`, `read_text()`, etc.
- Better than `os.path`: More intuitive API

**Key Takeaways:**
- `Path` for modern path operations
- Cross-platform with `/` operator
- More intuitive than `os.path`

### Regular Expressions

**What this demonstrates:** Pattern matching with `re` module.

**Code:**
```python
import re

# Search (find first match)
pattern = r'\d{3}-\d{3}-\d{4}'  # Phone number pattern
phone = "Call me at 555-123-4567"
match = re.search(pattern, phone)
if match:
    print(match.group())  # "555-123-4567"

# Findall (find all matches)
numbers = re.findall(r'\d+', phone)  # ['555', '123', '4567']

# Sub (replace)
masked = re.sub(r'\d', 'X', phone)  # "Call me at XXX-XXX-XXXX"

# Groups (capture parts)
match = re.search(r'(\d{3})-(\d{3})-(\d{4})', phone)
if match:
    area_code = match.group(1)  # '555'
    prefix = match.group(2)     # '123'
    number = match.group(3)     # '4567'
    all_groups = match.groups()  # ('555', '123', '4567')

# Compile pattern (for reuse)
pattern = re.compile(r'\d+')
matches = pattern.findall("I have 5 apples and 3 oranges")
```

**Explanation:**
- `re.search()`: Find first match
- `re.findall()`: Find all matches
- `re.sub()`: Replace matches
- Groups: `()` capture parts of pattern
- `match.group(n)`: Access captured groups
- Raw strings: `r'...'` recommended (avoids escape issues)
- Compile: `re.compile()` for repeated use

**Key Takeaways:**
- `re.search()`, `re.findall()`, `re.sub()`
- Groups `()` capture parts
- Use raw strings `r'...'`
- Compile patterns for reuse

---

## Functional Programming

### Overview

Python supports functional programming paradigms with functions like `map`, `filter`, `reduce`, and tools from `functools`. Functional style can lead to more concise and readable code.

### Key Concepts

- **Map**: Apply function to all elements
- **Filter**: Select elements matching condition
- **Reduce**: Accumulate values
- **Partial**: Create functions with preset arguments
- **Lambda**: Anonymous functions

### Map, Filter, Reduce

**What this demonstrates:** Functional programming tools.

**Code:**
```python
numbers = [1, 2, 3, 4, 5]

# Map (apply function to all elements)
squared = list(map(lambda x: x ** 2, numbers))
# [1, 4, 9, 16, 25]

# Map with named function
def square(x):
    return x ** 2
squared = list(map(square, numbers))

# Filter (select elements matching condition)
evens = list(filter(lambda x: x % 2 == 0, numbers))
# [2, 4]

# Reduce (accumulate values)
from functools import reduce
total = reduce(lambda x, y: x + y, numbers)
# 15 (sum of all numbers)

product = reduce(lambda x, y: x * y, numbers)
# 120 (product of all numbers)
```

**Explanation:**
- `map(func, iterable)`: Applies function to each element
- `filter(func, iterable)`: Keeps elements where function returns True
- `reduce(func, iterable)`: Accumulates values (requires `functools`)
- Returns iterators (use `list()` to get list)
- Often used with lambdas

**Key Takeaways:**
- `map()` applies function to all elements
- `filter()` selects matching elements
- `reduce()` accumulates values
- Returns iterators (convert with `list()`)

### Partial Functions

**What this demonstrates:** Creating functions with preset arguments.

**Code:**
```python
from functools import partial

def power(base, exponent):
    return base ** exponent

# Create functions with preset arguments
square = partial(power, exponent=2)
cube = partial(power, exponent=3)

square(5)  # 25 (5 ** 2)
cube(5)    # 125 (5 ** 3)

# Partial with multiple arguments
def greet(greeting, name):
    return f"{greeting}, {name}!"

hello = partial(greet, "Hello")
hello("Alice")  # "Hello, Alice!"
```

**Explanation:**
- `partial(func, *args, **kwargs)`: Creates function with preset arguments
- Useful for creating specialized functions
- Reduces repetition

**Key Takeaways:**
- `partial()` creates functions with preset arguments
- Useful for specialization

---

## Async Programming

### Overview

Python's `asyncio` module enables asynchronous programming with `async`/`await` syntax. Async programming is useful for I/O-bound operations and concurrent tasks.

### Key Concepts

- **async/await**: Asynchronous function syntax
- **Coroutines**: Functions defined with `async def`
- **Event Loop**: Manages async execution
- **Tasks**: Concurrent coroutines
- **Async Context Managers**: `async with` statement

### Basic Async

**What this demonstrates:** Creating and running async functions.

**Code:**
```python
import asyncio

# Async function (coroutine)
async def fetch_data(id):
    await asyncio.sleep(1)  # Simulate I/O (non-blocking)
    return f"Data {id}"

# Run async function
async def main():
    result = await fetch_data(1)
    print(result)

asyncio.run(main())

# Concurrent execution
async def main():
    tasks = [fetch_data(i) for i in range(5)]
    results = await asyncio.gather(*tasks)  # Run concurrently
    print(results)  # ['Data 0', 'Data 1', 'Data 2', 'Data 3', 'Data 4']

asyncio.run(main())  # Takes ~1 second (not 5 seconds)
```

**Explanation:**
- `async def`: Defines coroutine (async function)
- `await`: Waits for async operation (non-blocking)
- `asyncio.run()`: Runs async function (creates event loop)
- `asyncio.gather()`: Runs multiple coroutines concurrently
- `asyncio.sleep()`: Non-blocking sleep

**Key Takeaways:**
- `async def` for async functions
- `await` for async operations
- `asyncio.gather()` for concurrency

---

## Testing

### Overview

Testing is crucial for reliable code. Python provides `unittest`, and `pytest` is a popular third-party testing framework.

### Key Concepts

- **Unit Tests**: Test individual functions/classes
- **unittest**: Built-in testing framework
- **pytest**: Popular third-party framework
- **doctest**: Tests in docstrings
- **Test Fixtures**: Setup/teardown code

### unittest Framework

**What this demonstrates:** Writing tests with unittest.

**Code:**
```python
import unittest

def add(a, b):
    return a + b

class TestMath(unittest.TestCase):
    def setUp(self):
        # Run before each test
        self.test_data = [1, 2, 3]
    
    def tearDown(self):
        # Run after each test
        pass
    
    def test_addition(self):
        self.assertEqual(add(2, 2), 4)
        self.assertNotEqual(add(2, 2), 5)
    
    def test_division(self):
        with self.assertRaises(ZeroDivisionError):
            1 / 0
    
    def test_list_operations(self):
        self.assertIn(2, self.test_data)
        self.assertIsInstance(self.test_data, list)

# Run tests
if __name__ == '__main__':
    unittest.main()
```

**Explanation:**
- `unittest.TestCase`: Base class for test cases
- `test_*`: Methods starting with `test_` are test methods
- `setUp()`: Runs before each test
- `tearDown()`: Runs after each test
- Assertions: `assertEqual()`, `assertRaises()`, etc.
- Run: `python -m unittest` or `unittest.main()`

**Key Takeaways:**
- Inherit from `unittest.TestCase`
- Test methods: `test_*`
- `setUp()` / `tearDown()` for fixtures

### pytest Framework

**What this demonstrates:** Writing tests with pytest (simpler syntax).

**Code:**
```python
# Install: pip install pytest

def add(a, b):
    return a + b

# Simple test function
def test_add():
    assert add(2, 3) == 5

def test_add_negative():
    assert add(-1, 1) == 0

def test_add_zero():
    assert add(5, 0) == 5

# Run: pytest test_file.py
```

**Explanation:**
- `pytest`: Third-party framework (simpler than unittest)
- Test functions: Any function starting with `test_`
- `assert`: Simple assertions (no need for special methods)
- Run: `pytest` automatically discovers tests

**Key Takeaways:**
- `pytest` simpler than `unittest`
- Use `assert` statements
- Auto-discovers tests

---

## Performance & Optimization

### Overview

Understanding performance tools helps identify bottlenecks and optimize code. Python provides profiling and timing tools.

### Key Concepts

- **timeit**: Measure execution time
- **cProfile**: Performance profiling
- **Memory Profiling**: Track memory usage
- **Optimization Tips**: Best practices for performance

### Timing Code

**What this demonstrates:** Measuring execution time.

**Code:**
```python
import timeit

# Time a code snippet
code = """
result = sum(range(1000))
"""

time = timeit.timeit(code, number=10000)
print(f"Time: {time:.4f} seconds")

# Compare two approaches
list_comp = timeit.timeit('[x**2 for x in range(100)]', number=10000)
map_func = timeit.timeit('list(map(lambda x: x**2, range(100)))', number=10000)
```

**Explanation:**
- `timeit.timeit()`: Times code execution
- `number`: Number of iterations
- Useful for comparing approaches

**Key Takeaways:**
- `timeit` for timing code
- Useful for optimization

---

## Best Practices

### Code Style (PEP 8)

- **Indentation**: 4 spaces (not tabs)
- **Line Length**: Maximum 79 characters
- **Naming**: `snake_case` for functions/variables, `PascalCase` for classes, `UPPER_CASE` for constants
- **Imports**: One import per line, standard library first, then third-party
- **Whitespace**: Blank lines around functions/classes

### Documentation

- **Docstrings**: Use triple quotes for function/class documentation
- **Type Hints**: Optional but recommended for clarity
- **Comments**: Explain why, not what

### Code Organization

- **Functions**: Single responsibility, small and focused
- **Modules**: Related functionality together
- **Packages**: Organize related modules
- **DRY**: Don't Repeat Yourself

### Error Handling

- **Specific Exceptions**: Catch specific exceptions, not generic `Exception`
- **Fail Fast**: Validate inputs early
- **Logging**: Use logging module for error messages

### Performance

- **Profile First**: Use profiling tools before optimizing
- **Use Built-ins**: Built-in functions are optimized (C implementation)
- **List Comprehensions**: Often faster than loops
- **Generators**: Use for large sequences (memory efficient)

---

## Common Patterns

### Singleton Pattern

```python
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
```

### Factory Pattern

```python
class AnimalFactory:
    @staticmethod
    def create_animal(animal_type, name):
        if animal_type == "dog":
            return Dog(name)
        elif animal_type == "cat":
            return Cat(name)
        raise ValueError(f"Unknown animal type: {animal_type}")
```

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

