# C# - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Fundamentals & Basic Syntax](#fundamentals--basic-syntax)
4. [Data Types & Variables](#data-types--variables)
5. [Operators](#operators)
6. [Control Flow](#control-flow)
7. [Classes & Objects](#classes--objects)
8. [Inheritance & Polymorphism](#inheritance--polymorphism)
9. [Interfaces](#interfaces)
10. [Collections](#collections)
11. [Generics](#generics)
12. [LINQ](#linq)
13. [Exception Handling](#exception-handling)
14. [Async/Await](#asyncawait)
15. [File I/O](#file-io)
16. [Best Practices](#best-practices)
17. [Common Patterns](#common-patterns)
18. [Resources](#resources)

---

## Introduction

### What is C#?

C# (pronounced "C-sharp") is a modern, object-oriented programming language developed by Microsoft as part of the .NET initiative. C# combines the productivity of Visual Basic with the power of C++ and is designed for building a wide range of applications that run on the .NET platform.

### Why Learn C#?

C# is valuable for:

1. **Microsoft Ecosystem**: Primary language for .NET development
2. **Windows Applications**: Desktop, mobile, and web apps
3. **Game Development**: Unity game engine uses C#
4. **Enterprise Software**: Widely used in enterprise applications
5. **Cross-Platform**: .NET Core/.NET 5+ runs on Windows, Linux, macOS
6. **Modern Language**: Continuously evolving with new features
7. **Strong Typing**: Type-safe language with excellent tooling
8. **Career Opportunities**: High demand in enterprise and game development

### Key Features

- **Object-Oriented**: Classes, inheritance, polymorphism, interfaces
- **Type-Safe**: Strong typing prevents many errors
- **Garbage Collected**: Automatic memory management
- **LINQ**: Language Integrated Query for data manipulation
- **Async/Await**: Built-in asynchronous programming support
- **Rich Standard Library**: Comprehensive .NET Framework/.NET Core
- **Modern Features**: Properties, events, delegates, lambda expressions

---

## Getting Started

### Installation

**Install .NET SDK:**
- Download from: https://dotnet.microsoft.com/download
- Or use: `winget install Microsoft.DotNet.SDK` (Windows)

**Verify Installation:**
```bash
dotnet --version
```

**Create First Project:**
```bash
dotnet new console -n HelloWorld
cd HelloWorld
dotnet run
```

### Your First C# Program

**Code:**
```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

---

## Fundamentals & Basic Syntax

### Overview

C# is a statically-typed, object-oriented language. Understanding the basic syntax and structure is essential for C# development.

### Key Concepts

- **Namespaces**: Organize code (`namespace Name`)
- **Classes**: Define objects (`class Name`)
- **Main Method**: Entry point (`static void Main()`)
- **Using Statements**: Import namespaces
- **Case-Sensitive**: C# is case-sensitive
- **Semicolons**: Statements end with `;`

### Basic Syntax

**What this demonstrates:** Basic C# program structure.

**Code:**
```csharp
using System;
using System.Collections.Generic;

namespace CSharpBasics
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
            Console.ReadLine();  // Wait for input
        }
    }
}
```

**Explanation:**
- `using`: Import namespaces
- `namespace`: Organize code
- `class`: Define class
- `static void Main()`: Entry point
- `Console.WriteLine()`: Output text
- Semicolons: End statements

**Key Takeaways:**
- `Main()` is the entry point
- Use `using` to import namespaces
- Semicolons end statements
- Code organized in namespaces and classes

---

## Data Types & Variables

### Overview

C# has value types (stored on stack) and reference types (stored on heap). Understanding types is fundamental to C# programming.

### Key Concepts

- **Value Types**: int, float, bool, char, struct
- **Reference Types**: string, object, arrays, classes
- **Nullable Types**: `type?` for optional values
- **var Keyword**: Type inference
- **Constants**: `const` for immutable values
- **Type Conversion**: Implicit and explicit

### Value Types

**What this demonstrates:** C# value types.

**Code:**
```csharp
// Integer types
byte b = 255;                    // 0 to 255 (8-bit)
int i = 2147483647;              // -2.1B to 2.1B (32-bit)
long l = 9223372036854775807L;   // 64-bit

// Floating-point types
float f = 3.14159f;              // ~7 digits (32-bit)
double d = 3.14159265359;        // ~15-16 digits (64-bit)
decimal m = 123.456789m;         // 28-29 digits (128-bit)

// Boolean
bool isTrue = true;
bool isFalse = false;

// Character
char letter = 'A';
char unicode = '\u0041';         // Unicode
```

**Explanation:**
- Integer types: byte, sbyte, short, ushort, int, uint, long, ulong
- Floating-point: float (f suffix), double, decimal (m suffix)
- Boolean: true or false
- Character: Single character (Unicode)
- Value types: Stored on stack, copied when assigned

**Key Takeaways:**
- Use `int` for most integers
- Use `double` for most floats
- Use `decimal` for financial calculations
- Suffixes: `f` for float, `m` for decimal, `L` for long

### Reference Types

**What this demonstrates:** C# reference types.

**Code:**
```csharp
// String
string text = "Hello, C#!";
string multiline = @"This is a
multiline string";
string interpolated = $"Value: {i}";
string verbatim = @"C:\Users\Path";

// Object (base class)
object obj = 42;
object obj2 = "text";

// Dynamic (runtime type checking)
dynamic dyn = 42;
dyn = "Now a string";
```

**Explanation:**
- String: Text data, immutable
- String interpolation: `$"text {variable}"`
- Verbatim strings: `@"text"` (no escape sequences)
- Object: Base class of all types
- Dynamic: Runtime type checking
- Reference types: Stored on heap, reference copied

**Key Takeaways:**
- Strings are immutable
- Use `$` for string interpolation
- Use `@` for verbatim strings
- `dynamic` bypasses compile-time checking

### Nullable Types and var

**What this demonstrates:** Nullable types and type inference.

**Code:**
```csharp
// Nullable types
int? nullableInt = null;         // Nullable int
nullableInt = 42;
bool hasValue = nullableInt.HasValue;
int value = nullableInt.Value;
int valueOrDefault = nullableInt ?? 0;  // Null-coalescing

// var (type inference)
var number = 42;                 // Inferred as int
var name = "Commander";          // Inferred as string
var array = new[] { 1, 2, 3 };   // Inferred as int[]
```

**Explanation:**
- Nullable: `type?` allows null values
- `HasValue`: Check if has value
- `??`: Null-coalescing operator
- `var`: Type inference (type determined by compiler)
- Use var: When type is obvious from right side

**Key Takeaways:**
- Use `type?` for nullable value types
- `??` provides default for null
- `var` for type inference
- Use var when type is clear

---

## Operators

### Overview

C# provides arithmetic, comparison, logical, bitwise, and other operators. Understanding operators is essential for expressions.

### Key Concepts

- **Arithmetic**: +, -, *, /, %, ++, --
- **Comparison**: ==, !=, >, <, >=, <=
- **Logical**: &&, ||, !
- **Bitwise**: &, |, ^, ~, <<, >>
- **Assignment**: =, +=, -=, etc.
- **Null-Coalescing**: ??, ??=

### Arithmetic and Comparison

**What this demonstrates:** Arithmetic and comparison operators.

**Code:**
```csharp
int a = 10, b = 3;

// Arithmetic
int sum = a + b;                 // 13
int diff = a - b;                // 7
int prod = a * b;                // 30
int quot = a / b;                // 3 (integer division)
int rem = a % b;                 // 1 (modulo)

// Increment/Decrement
int x = 5;
x++;                             // Post-increment
++x;                             // Pre-increment

// Comparison
bool equal = a == b;             // false
bool notEqual = a != b;          // true
bool greater = a > b;            // true
bool less = a < b;               // false
```

**Explanation:**
- Arithmetic: Standard math operations
- Integer division: `/` truncates (no decimal)
- Modulo: `%` returns remainder
- Increment/decrement: `++` and `--` (pre/post)
- Comparison: Returns bool

**Key Takeaways:**
- `/` performs integer division for integers
- `%` for remainder
- `++x` increments before use, `x++` after

### Logical and Null-Coalescing

**What this demonstrates:** Logical and null-coalescing operators.

**Code:**
```csharp
// Logical
bool and = true && false;        // false (short-circuit)
bool or = true || false;         // true (short-circuit)
bool not = !true;                // false

// Null-coalescing
string str = null;
string result = str ?? "default";      // "default"
str ??= "assigned";                     // Assign if null (C# 8.0)

// Conditional (ternary)
int max = (a > b) ? a : b;
```

**Explanation:**
- `&&`: Logical AND (short-circuit)
- `||`: Logical OR (short-circuit)
- `!`: Logical NOT
- `??`: Null-coalescing (returns right if left is null)
- `??=`: Null-coalescing assignment (C# 8.0)
- `?:`: Ternary operator

**Key Takeaways:**
- `&&` and `||` short-circuit
- Use `??` for default values
- `??=` assigns if null

---

## Control Flow

### Overview

Control flow statements determine execution order. C# supports if/else, switch, loops, and jump statements.

### Key Concepts

- **Conditionals**: if/else, switch, ternary
- **Loops**: for, while, do-while, foreach
- **Jump Statements**: break, continue, return, goto
- **Switch Expressions**: Pattern matching (C# 8.0+)

### Conditionals

**What this demonstrates:** Conditional statements.

**Code:**
```csharp
// if/else
int age = 25;

if (age < 13)
{
    Console.WriteLine("Child");
}
else if (age < 20)
{
    Console.WriteLine("Teenager");
}
else
{
    Console.WriteLine("Adult");
}

// Switch
int day = 3;
switch (day)
{
    case 1:
        Console.WriteLine("Monday");
        break;
    case 2:
        Console.WriteLine("Tuesday");
        break;
    default:
        Console.WriteLine("Other");
        break;
}

// Switch expression (C# 8.0+)
string dayName = day switch
{
    1 => "Monday",
    2 => "Tuesday",
    _ => "Other"
};
```

**Explanation:**
- if/else: Conditional execution
- switch: Multiple cases (use `break`)
- Switch expression: Pattern matching (C# 8.0+)
- `default`: Default case
- `_`: Discard pattern in switch expression

**Key Takeaways:**
- Use if/else for conditionals
- Switch expressions (C# 8.0+) are more concise
- Always use `break` in switch cases

### Loops

**What this demonstrates:** Different loop types.

**Code:**
```csharp
// for loop
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(i);
}

// while loop
int count = 0;
while (count < 5)
{
    Console.WriteLine(count);
    count++;
}

// do-while loop
int num = 0;
do
{
    Console.WriteLine(num);
    num++;
} while (num < 5);

// foreach loop
int[] numbers = {1, 2, 3, 4, 5};
foreach (int n in numbers)
{
    Console.WriteLine(n);
}

// Break and continue
for (int i = 0; i < 10; i++)
{
    if (i == 3) continue;  // Skip 3
    if (i == 7) break;     // Exit at 7
    Console.WriteLine(i);
}
```

**Explanation:**
- for: Known number of iterations
- while: Conditional loop
- do-while: Execute once, then check condition
- foreach: Iterate over collections
- break: Exit loop
- continue: Skip to next iteration

**Key Takeaways:**
- Use `foreach` for collections
- `break` exits loop
- `continue` skips to next iteration

---

## Classes & Objects

### Overview

C# is object-oriented. Classes define objects with properties, methods, and constructors. Understanding classes is fundamental to C#.

### Key Concepts

- **Classes**: Define objects
- **Properties**: Get/set accessors
- **Methods**: Functions in classes
- **Constructors**: Initialize objects
- **Inheritance**: `: BaseClass`
- **Polymorphism**: virtual/override
- **Records**: Immutable types (C# 9.0+)

### Classes and Properties

**What this demonstrates:** Creating classes with properties.

**Code:**
```csharp
class Person
{
    // Auto-implemented properties
    public string Name { get; set; }
    public int Age { get; set; }
    
    // Property with backing field
    private double _salary;
    public double Salary
    {
        get { return _salary; }
        set 
        { 
            if (value >= 0)
                _salary = value;
        }
    }
    
    // Read-only property
    public string FullInfo => $"{Name}, {Age} years old";
    
    // Init-only property (C# 9.0)
    public string Id { get; init; }
    
    // Constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
    
    // Method
    public void Introduce()
    {
        Console.WriteLine($"Hi, I'm {Name}, {Age} years old.");
    }
}

// Usage
Person person = new Person("Alice", 25);
person.Name = "Bob";
person.Introduce();
```

**Explanation:**
- Properties: `{ get; set; }` syntax
- Auto-properties: Automatic backing field
- Custom properties: Backing field with logic
- Expression-bodied: `=>` syntax
- Init-only: Can set only during initialization (C# 9.0)
- Constructor: Initializes object

**Key Takeaways:**
- Use properties instead of public fields
- Auto-properties for simple cases
- Constructors initialize objects
- Init-only for immutable properties

### Inheritance and Polymorphism

**What this demonstrates:** Inheritance and polymorphism.

**Code:**
```csharp
// Base class
class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Some sound");
    }
}

// Derived class
class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
}

// Abstract class
abstract class Shape
{
    public abstract double Area();
    
    public void Display()
    {
        Console.WriteLine($"Area: {Area()}");
    }
}

class Circle : Shape
{
    public double Radius { get; set; }
    
    public override double Area()
    {
        return Math.PI * Radius * Radius;
    }
}

// Usage
Animal animal = new Dog();  // Polymorphism
animal.MakeSound();         // Calls Dog.MakeSound()
```

**Explanation:**
- Inheritance: `: BaseClass` syntax
- `virtual`: Can be overridden
- `override`: Overrides base method
- `abstract`: Must be implemented
- Polymorphism: Base class reference to derived object

**Key Takeaways:**
- Use `: BaseClass` for inheritance
- `virtual`/`override` for polymorphism
- `abstract` for base classes
- Polymorphism enables flexible code

### Records

**What this demonstrates:** Records for immutable types (C# 9.0+).

**Code:**
```csharp
// Record (immutable reference type)
record PersonRecord(string Name, int Age);

// Usage
var record1 = new PersonRecord("Alice", 25);
var record2 = new PersonRecord("Alice", 25);
bool areEqual = record1 == record2;  // true (value equality)

// With expression (create copy with modification)
var record3 = record1 with { Age = 26 };
```

**Explanation:**
- Record: Immutable reference type (C# 9.0+)
- Value equality: Records compare by value
- With expression: Create modified copy
- Positional syntax: Constructor parameters

**Key Takeaways:**
- Records for immutable data
- Value equality by default
- Use `with` for modifications

---

## Interfaces

### Overview

Interfaces define contracts that classes must implement. They enable polymorphism and multiple inheritance of behavior.

### Key Concepts

- **Interface**: Defines contract
- **Implementation**: Class implements interface
- **Multiple Interfaces**: Class can implement multiple
- **Default Implementation**: Interface methods (C# 8.0+)
- **Explicit Implementation**: Resolve naming conflicts

### Interfaces

**What this demonstrates:** Creating and using interfaces.

**Code:**
```csharp
// Interface definition
interface IDrawable
{
    void Draw();
    void Erase();
}

interface IResizable
{
    void Resize(double factor);
}

// Class implementing interface
class Rectangle : IDrawable, IResizable
{
    public void Draw()
    {
        Console.WriteLine("Drawing rectangle");
    }
    
    public void Erase()
    {
        Console.WriteLine("Erasing rectangle");
    }
    
    public void Resize(double factor)
    {
        Console.WriteLine($"Resizing by {factor}");
    }
}

// Usage
IDrawable shape = new Rectangle();
shape.Draw();
```

**Explanation:**
- Interface: Defines contract (methods/properties)
- Implementation: Class must implement all members
- Multiple interfaces: Comma-separated
- Interface reference: Can use interface type
- Contract: Ensures class has required members

**Key Takeaways:**
- Interfaces define contracts
- Classes implement interfaces
- Multiple interfaces allowed
- Use interfaces for polymorphism

---

## Collections

### Overview

Collections store multiple items. C# provides arrays, Lists, Dictionaries, and other collection types.

### Key Concepts

- **Arrays**: Fixed-size collections
- **List<T>**: Dynamic-size list
- **Dictionary<TKey, TValue>**: Key-value pairs
- **HashSet<T>**: Unique items
- **Queue<T>**: FIFO collection
- **Stack<T>**: LIFO collection

### Collections

**What this demonstrates:** Using collections.

**Code:**
```csharp
// Arrays
int[] numbers = new int[5];
int[] nums = {1, 2, 3, 4, 5};

// List
List<int> list = new List<int>();
list.Add(1);
list.Add(2);
list.Remove(1);
int count = list.Count;

// Dictionary
Dictionary<string, int> dict = new Dictionary<string, int>();
dict["Alice"] = 25;
dict["Bob"] = 30;
int age = dict["Alice"];

// HashSet
HashSet<int> set = new HashSet<int>();
set.Add(1);
set.Add(2);
bool contains = set.Contains(1);

// Queue (FIFO)
Queue<string> queue = new Queue<string>();
queue.Enqueue("First");
queue.Enqueue("Second");
string first = queue.Dequeue();

// Stack (LIFO)
Stack<string> stack = new Stack<string>();
stack.Push("First");
stack.Push("Second");
string top = stack.Pop();
```

**Explanation:**
- Arrays: Fixed size, zero-indexed
- List: Dynamic size, similar to array
- Dictionary: Key-value pairs, fast lookup
- HashSet: Unique items, fast contains
- Queue: First-in-first-out
- Stack: Last-in-first-out

**Key Takeaways:**
- Use arrays for fixed-size
- Use List for dynamic collections
- Dictionary for key-value pairs
- HashSet for unique items

---

## Generics

### Overview

Generics enable writing reusable, type-safe code. They allow classes, methods, and interfaces to work with multiple types.

### Key Concepts

- **Generic Classes**: `class Name<T>`
- **Generic Methods**: `Method<T>()`
- **Generic Constraints**: `where T : constraint`
- **Type Parameters**: `<T>`, `<TKey, TValue>`
- **Type Safety**: Compile-time type checking

### Generics

**What this demonstrates:** Using generics.

**Code:**
```csharp
// Generic class
class Box<T>
{
    public T Value { get; set; }
    
    public Box(T value)
    {
        Value = value;
    }
}

// Generic method
static void Swap<T>(ref T a, ref T b)
{
    T temp = a;
    a = b;
    b = temp;
}

// Generic constraints
class Processor<T> where T : class
{
    public void Process(T item)
    {
        // Process item
    }
}

// Usage
Box<int> intBox = new Box<int>(42);
Box<string> strBox = new Box<string>("Hello");

int x = 10, y = 20;
Swap(ref x, ref y);
```

**Explanation:**
- Generic syntax: `<T>` for type parameter
- Type parameter: Placeholder for type
- Constraints: `where T : constraint`
- Type safety: Compile-time checking
- Reusable: Same code for multiple types

**Key Takeaways:**
- Generics for type-safe reusable code
- Use constraints to limit types
- Type parameters enable flexibility

---

## LINQ

### Overview

LINQ (Language Integrated Query) provides query capabilities directly in C#. It enables querying collections, databases, and XML.

### Key Concepts

- **Query Syntax**: SQL-like syntax
- **Method Syntax**: Extension methods
- **Deferred Execution**: Queries execute when enumerated
- **Common Operations**: Where, Select, OrderBy, GroupBy
- **Aggregation**: Count, Sum, Average, Max, Min

### LINQ

**What this demonstrates:** Using LINQ.

**Code:**
```csharp
using System.Linq;

List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Method syntax (more common)
var evens = numbers.Where(n => n % 2 == 0);
var doubled = numbers.Select(n => n * 2);
var sorted = numbers.OrderBy(n => n);
var sum = numbers.Sum();
var max = numbers.Max();

// Query syntax
var query = from n in numbers
            where n % 2 == 0
            select n;

// Filtering
var adults = people.Where(p => p.Age >= 18);

// Projection
var names = people.Select(p => p.Name);

// Grouping
var byCity = people.GroupBy(p => p.City);

// Joining
var joined = from p in people
             join o in orders on p.Name equals o.PersonName
             select new { p.Name, o.Product };
```

**Explanation:**
- LINQ: Language Integrated Query
- Method syntax: Extension methods (preferred)
- Query syntax: SQL-like syntax
- Deferred execution: Executes when enumerated
- Common operations: Where, Select, OrderBy, GroupBy

**Key Takeaways:**
- Use method syntax (more common)
- LINQ works with any IEnumerable
- Deferred execution for efficiency
- Powerful query capabilities

---

## Exception Handling

### Overview

Exception handling manages errors and exceptional conditions. C# provides try/catch/finally for exception handling.

### Key Concepts

- **Try/Catch**: Handle exceptions
- **Finally**: Always executes
- **Throw**: Throw exceptions
- **Custom Exceptions**: Create exception classes
- **Multiple Catch**: Catch different exception types

### Exception Handling

**What this demonstrates:** Handling exceptions.

**Code:**
```csharp
// Try-catch
try
{
    int result = 10 / 0;
}
catch (DivideByZeroException ex)
{
    Console.WriteLine($"Error: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"General error: {ex.Message}");
}
finally
{
    Console.WriteLine("Cleanup");
}

// Throwing exceptions
if (value < 0)
{
    throw new ArgumentException("Value must be positive");
}

// Custom exception
class CustomException : Exception
{
    public CustomException(string message) : base(message) { }
}

throw new CustomException("Custom error message");
```

**Explanation:**
- try: Code that might throw
- catch: Handle exceptions
- finally: Always executes (cleanup)
- throw: Throw exception
- Custom exceptions: Extend Exception class

**Key Takeaways:**
- Use try/catch for error handling
- Finally for cleanup
- Throw exceptions for errors
- Custom exceptions for specific errors

---

## Async/Await

### Overview

Async/await enables asynchronous programming in C#. It simplifies asynchronous code and makes it look synchronous.

### Key Concepts

- **async**: Method can use await
- **await**: Wait for async operation
- **Task**: Represents async operation
- **Task<T>**: Async operation with result
- **Async/Await**: Simplifies async code

### Async/Await

**What this demonstrates:** Asynchronous programming.

**Code:**
```csharp
using System.Threading.Tasks;
using System.Net.Http;

// Async method
static async Task<string> DownloadDataAsync(string url)
{
    using (HttpClient client = new HttpClient())
    {
        string result = await client.GetStringAsync(url);
        return result;
    }
}

// Calling async method
static async Task Main()
{
    string data = await DownloadDataAsync("https://example.com");
    Console.WriteLine(data);
    
    // Task.Delay
    await Task.Delay(1000);  // Wait 1 second
    
    // Task.Run (run on thread pool)
    int result = await Task.Run(() => ComputeValue(5));
    
    // Task.WhenAll (parallel execution)
    Task<int> t1 = Task.Run(() => 1);
    Task<int> t2 = Task.Run(() => 2);
    int[] results = await Task.WhenAll(t1, t2);
}
```

**Explanation:**
- `async`: Method can use await
- `await`: Wait for async operation
- `Task`: Represents async operation
- `Task.Run`: Run on thread pool
- `Task.WhenAll`: Wait for multiple tasks
- `Task.Delay`: Async delay

**Key Takeaways:**
- Use async/await for async operations
- `async` method returns Task or Task<T>
- `await` waits for async operation
- Use `Task.WhenAll` for parallel execution

---

## Best Practices

### Code Organization

- **Namespaces**: Organize code with namespaces
- **Classes**: Single responsibility principle
- **Properties**: Use properties instead of public fields
- **Constants**: Use `const` for compile-time constants
- **readonly**: Use for runtime constants

### Error Handling

- **Try/Catch**: Handle exceptions appropriately
- **Specific Exceptions**: Catch specific exceptions first
- **Don't Catch All**: Avoid catching `Exception` unless needed
- **Logging**: Log exceptions appropriately
- **Validation**: Validate input before processing

### Performance

- **StringBuilder**: For string concatenation in loops
- **LINQ**: Use efficiently (avoid multiple enumerations)
- **Async/Await**: Use for I/O operations
- **Collections**: Choose appropriate collection type
- **Dispose**: Dispose IDisposable resources

---

## Common Patterns

### Singleton Pattern

```csharp
public class Singleton
{
    private static Singleton _instance;
    private static readonly object _lock = new object();
    
    private Singleton() { }
    
    public static Singleton Instance
    {
        get
        {
            lock (_lock)
            {
                if (_instance == null)
                    _instance = new Singleton();
                return _instance;
            }
        }
    }
}
```

### Repository Pattern

```csharp
public interface IRepository<T>
{
    T GetById(int id);
    void Add(T entity);
    void Update(T entity);
    void Delete(int id);
}

public class Repository<T> : IRepository<T>
{
    // Implementation
}
```

---

## Resources

### Official Documentation

- **Microsoft C# Documentation**: https://docs.microsoft.com/dotnet/csharp/
- **.NET Documentation**: https://docs.microsoft.com/dotnet/
- **C# Language Specification**: https://docs.microsoft.com/dotnet/csharp/language-reference/language-specification/

### Learning Resources

- **Microsoft Learn C#**: https://docs.microsoft.com/learn/paths/csharp-first-steps/
- **C# Guide**: https://docs.microsoft.com/dotnet/csharp/
- **C# Station Tutorial**: Various tutorials

### Community

- **Stack Overflow**: Tag: c#
- **r/csharp**: Reddit community
- **.NET Community**: https://dotnet.microsoft.com/platform/community

### Tools

- **Visual Studio**: Full-featured IDE
- **Visual Studio Code**: Lightweight editor with C# extension
- **.NET SDK**: Development kit
- **NuGet**: Package manager
- **JetBrains Rider**: Cross-platform IDE

---

