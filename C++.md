# C++ - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Basics & Differences from C](#basics--differences-from-c)
4. [Object-Oriented Programming](#object-oriented-programming)
5. [Templates](#templates)
6. [STL (Standard Template Library)](#stl-standard-template-library)
7. [Lambda Expressions & Functional Programming](#lambda-expressions--functional-programming)
8. [Smart Pointers & Memory Management](#smart-pointers--memory-management)
9. [Exception Handling](#exception-handling)
10. [Modern C++ Features](#modern-c-features)
11. [File I/O](#file-io)
12. [Multithreading](#multithreading)
13. [Best Practices](#best-practices)
14. [Common Patterns](#common-patterns)
15. [Resources](#resources)

---

## Introduction

### What is C++?

C++ is a general-purpose, multi-paradigm programming language developed by Bjarne Stroustrup at Bell Labs in 1979. It was designed as an extension of C with object-oriented programming capabilities. C++ combines the low-level efficiency of C with high-level abstractions, making it suitable for system programming, game development, embedded systems, and performance-critical applications.

### Why Learn C++?

C++ is valuable for:

1. **Performance**: Close to hardware, minimal runtime overhead
2. **System Programming**: Operating systems, device drivers, embedded systems
3. **Game Development**: Many game engines use C++ (Unreal, Unity)
4. **High-Performance Computing**: Scientific computing, simulations
5. **Legacy Code**: Many existing systems are written in C++
6. **Control**: Fine-grained control over memory and resources
7. **Career Opportunities**: High demand in systems, gaming, and embedded domains
8. **Modern Features**: C++11/14/17/20 add powerful modern capabilities

### Key Features

- **Multi-Paradigm**: Supports procedural, OOP, generic, and functional programming
- **Performance**: Compiled language with minimal runtime overhead
- **Memory Management**: Manual control with modern smart pointers (RAII)
- **Standard Library**: Rich STL (containers, algorithms, iterators)
- **Templates**: Generic programming capabilities
- **Backward Compatibility**: Maintains compatibility with C

---

## Getting Started

### Installation

C++ requires a compiler. Popular options:

- **GCC** (GNU Compiler Collection): Linux, Windows (MinGW), macOS
- **Clang**: Linux, macOS, Windows (LLVM-based)
- **MSVC** (Microsoft Visual C++): Windows (Visual Studio)
- **Online**: Compiler Explorer, Repl.it, OnlineGDB

### Your First Program

**What this demonstrates:** Basic C++ program structure.

**Code:**
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

**Explanation:**
- `#include <iostream>`: Include input/output stream library
- `int main()`: Entry point (returns int)
- `std::cout`: Standard output stream
- `<<`: Stream insertion operator
- `std::endl`: End line and flush buffer
- `return 0`: Successful program termination

**Key Takeaways:**
- C++ uses streams for I/O
- `main()` is program entry point
- `std::` namespace for standard library
- Compile: `g++ program.cpp -o program`

---

## Basics & Differences from C

### Overview

C++ extends C with object-oriented features, better type safety, and modern abstractions. Understanding the differences helps leverage C++ effectively.

### Key Concepts

- **References**: Safer alternative to pointers
- **Namespaces**: Avoid naming conflicts
- **Streams**: Type-safe I/O (cout, cin)
- **Auto**: Type deduction
- **Range-based for**: Modern iteration
- **C++ Standard Library**: Rich library vs C's limited library

### I/O Streams

**What this demonstrates:** Stream-based I/O (easier than C's printf/scanf).

**Code:**
```cpp
#include <iostream>
#include <string>

int main() {
    // Output
    std::cout << "Hello, World!" << std::endl;
    std::cout << "Number: " << 42 << std::endl;
    
    // Input
    int age;
    std::cout << "Enter age: ";
    std::cin >> age;
    
    std::string name;
    std::cout << "Enter name: ";
    std::cin >> name;  // Reads single word
    
    std::string line;
    std::getline(std::cin, line);  // Reads entire line
    
    return 0;
}
```

**Explanation:**
- `cout`: Standard output (type-safe, no format strings)
- `cin`: Standard input
- `<<`: Output operator (can chain)
- `>>`: Input operator
- `std::getline()`: Read entire line (handles spaces)
- Type-safe: Compiler checks types (no format mismatches)

**Key Takeaways:**
- Streams are type-safe (no printf format errors)
- `<<` for output, `>>` for input
- `getline()` for reading lines with spaces
- Can chain operators

### References

**What this demonstrates:** References as safer alternative to pointers.

**Code:**
```cpp
int x = 10;

// Reference (must be initialized, cannot be reassigned)
int &ref = x;  // ref is alias for x
ref = 20;      // Modifies x
std::cout << "x: " << x << std::endl;  // 20

// Const reference (read-only)
const int &const_ref = x;
// const_ref = 30;  // Error: cannot modify

// Reference in function parameter (no copy)
void increment(int &n) {
    n++;  // Modifies original
}

int value = 5;
increment(value);
std::cout << value << std::endl;  // 6

// Return reference (be careful - avoid dangling references)
int& get_value(int &n) {
    return n;  // Returns reference to n
}
```

**Explanation:**
- References: Aliases (must initialize, cannot reassign)
- Safer than pointers: Cannot be null, cannot be reassigned
- No dereferencing: Use like regular variable
- Const references: Read-only, efficient for large objects
- Function parameters: Pass by reference (modify original, no copy)

**Key Takeaways:**
- References are safer than pointers
- Must initialize, cannot reassign
- Use for function parameters (avoid copying)
- Const references for read-only access

### Auto Type Deduction

**What this demonstrates:** Automatic type deduction (C++11+).

**Code:**
```cpp
// Auto deduces type from initializer
auto number = 42;        // int
auto pi = 3.14;          // double
auto name = "Commander"; // const char*

// With iterators (simplifies code)
std::vector<int> vec = {1, 2, 3};
for (auto it = vec.begin(); it != vec.end(); ++it) {
    std::cout << *it << " ";
}

// Auto with references
auto &ref = number;  // int&
const auto &const_ref = pi;  // const double&
```

**Explanation:**
- `auto`: Compiler deduces type from initializer
- Simplifies code: Especially with complex types (iterators, lambdas)
- Type still determined: Not dynamic typing (compile-time)
- Use when type is obvious: Improves readability

**Key Takeaways:**
- `auto` for type deduction (compile-time)
- Simplifies complex type declarations
- Not dynamic typing (type still fixed)
- Use when type is obvious from context

### Range-Based For Loop

**What this demonstrates:** Modern iteration over containers (C++11+).

**Code:**
```cpp
#include <vector>
#include <string>

std::vector<int> numbers = {1, 2, 3, 4, 5};

// Range-based for loop
for (int num : numbers) {
    std::cout << num << " ";  // Copies each element
}

// Reference (modify original, no copy)
for (int &num : numbers) {
    num *= 2;  // Modifies original
}

// Const reference (read-only, no copy, efficient)
for (const int &num : numbers) {
    std::cout << num << " ";
}

// Works with arrays
int arr[] = {10, 20, 30};
for (int value : arr) {
    std::cout << value << " ";
}

// Works with strings
std::string text = "Hello";
for (char c : text) {
    std::cout << c << " ";
}
```

**Explanation:**
- Range-based for: Iterate over containers/arrays
- `for (type var : container)`: Simplified syntax
- By value: Copies elements (use for small types)
- By reference: Modifies original (use when modifying)
- Const reference: Read-only, efficient (use for large objects)

**Key Takeaways:**
- Range-based for: Cleaner than traditional for
- Use reference to modify, const reference for efficiency
- Works with arrays, vectors, strings, any container
- Prefer over traditional for when possible

---

## Object-Oriented Programming

### Overview

C++ is an object-oriented language supporting classes, inheritance, polymorphism, and encapsulation. OOP enables code organization, reusability, and abstraction.

### Key Concepts

- **Classes**: Blueprints for objects (data + functions)
- **Objects**: Instances of classes
- **Encapsulation**: Data hiding (private/protected/public)
- **Inheritance**: Code reuse (base/derived classes)
- **Polymorphism**: Virtual functions, dynamic binding
- **Constructors/Destructors**: Object initialization/cleanup
- **Operator Overloading**: Custom operators for classes

### Classes & Objects

**What this demonstrates:** Complete class with constructors, destructors, and methods.

**Code:**
```cpp
#include <iostream>
#include <string>

class Person {
private:
    std::string name;
    int age;
    
public:
    // Constructor
    Person(std::string n, int a) : name(n), age(a) {
        std::cout << "Person created: " << name << std::endl;
    }
    
    // Destructor
    ~Person() {
        std::cout << "Person destroyed: " << name << std::endl;
    }
    
    // Copy constructor
    Person(const Person &other) : name(other.name), age(other.age) {
        std::cout << "Person copied: " << name << std::endl;
    }
    
    // Copy assignment operator
    Person& operator=(const Person &other) {
        if (this != &other) {
            name = other.name;
            age = other.age;
            std::cout << "Person assigned: " << name << std::endl;
        }
        return *this;
    }
    
    // Move constructor (C++11)
    Person(Person &&other) noexcept : name(std::move(other.name)), age(other.age) {
        std::cout << "Person moved: " << name << std::endl;
    }
    
    // Move assignment operator (C++11)
    Person& operator=(Person &&other) noexcept {
        if (this != &other) {
            name = std::move(other.name);
            age = other.age;
            std::cout << "Person move-assigned: " << name << std::endl;
        }
        return *this;
    }
    
    // Getters
    std::string get_name() const { return name; }
    int get_age() const { return age; }
    
    // Setters
    void set_name(const std::string &n) { name = n; }
    void set_age(int a) { 
        if (a >= 0) age = a; 
    }
    
    // Method
    void greet() const {
        std::cout << "Hello, I'm " << name << ", " << age << " years old" << std::endl;
    }
    
    // Static member
    static int population;
    static void show_population() {
        std::cout << "Population: " << population << std::endl;
    }
    
    // Operator overloading
    bool operator==(const Person &other) const {
        return name == other.name && age == other.age;
    }
    
    bool operator<(const Person &other) const {
        return age < other.age;
    }
    
    // Friend function
    friend std::ostream& operator<<(std::ostream &os, const Person &p);
};

// Static member definition
int Person::population = 0;

// Friend function definition
std::ostream& operator<<(std::ostream &os, const Person &p) {
    os << p.name << " (" << p.age << ")";
    return os;
}
```

**Explanation:**
- `private`: Only class can access
- `public`: Anyone can access
- Constructor: Initialize object (member initializer list `: name(n), age(a)`)
- Destructor: Cleanup (`~ClassName()`)
- Copy constructor: Create copy (`Person(const Person &other)`)
- Assignment operator: Copy assignment (`operator=` with self-check)
- Move constructor: Efficient transfer (C++11, `Person(Person &&other)`)
- Move assignment: Move assignment (C++11)
- `const` methods: Don't modify object
- Static members: Shared by all instances
- Operator overloading: Custom operators (`operator==`, `operator<`)
- Friend functions: Access private members

**Key Takeaways:**
- Use access specifiers (private/protected/public)
- Constructors initialize, destructors cleanup
- Rule of 3/5: Copy constructor, copy assignment, destructor (add move versions in C++11)
- Use `const` for methods that don't modify
- Operator overloading for intuitive syntax

### Inheritance

**What this demonstrates:** Inheritance with base and derived classes.

**Code:**
```cpp
// Base class
class Person {
protected:
    std::string name;
    int age;
    
public:
    Person(std::string n, int a) : name(n), age(a) {}
    void greet() const {
        std::cout << "Hello, I'm " << name << std::endl;
    }
};

// Derived class
class Student : public Person {
private:
    std::string school;
    double gpa;
    
public:
    Student(std::string name, int age, std::string s, double g)
        : Person(name, age), school(s), gpa(g) {}
    
    void study() {
        std::cout << name << " is studying at " << school << std::endl;
    }
    
    // Override method
    void greet() const {
        std::cout << "Hi, I'm " << name << ", student at " << school << std::endl;
    }
};
```

**Explanation:**
- Inheritance: `class Derived : public Base`
- `public` inheritance: Public members stay public
- `protected`: Accessible to derived classes
- Constructor: Call base constructor in initializer list
- Override: Derived class redefines base method
- Access: Derived class can access protected members

**Key Takeaways:**
- Use `public` inheritance for "is-a" relationship
- Call base constructor in initializer list
- Protected for derived class access
- Can override methods in derived class

### Polymorphism

**What this demonstrates:** Virtual functions and runtime polymorphism.

**Code:**
```cpp
class Shape {
public:
    virtual ~Shape() {}  // Virtual destructor (important!)
    
    virtual double area() const = 0;  // Pure virtual (abstract)
    virtual void draw() const {
        std::cout << "Drawing shape" << std::endl;
    }
};

class Circle : public Shape {
private:
    double radius;
    
public:
    Circle(double r) : radius(r) {}
    
    double area() const override {
        return 3.14159 * radius * radius;
    }
    
    void draw() const override {
        std::cout << "Drawing circle with radius " << radius << std::endl;
    }
};

class Rectangle : public Shape {
private:
    double width, height;
    
public:
    Rectangle(double w, double h) : width(w), height(h) {}
    
    double area() const override {
        return width * height;
    }
    
    void draw() const override {
        std::cout << "Drawing rectangle " << width << "x" << height << std::endl;
    }
};

void polymorphism_demo() {
    std::vector<std::unique_ptr<Shape>> shapes;
    shapes.push_back(std::make_unique<Circle>(5.0));
    shapes.push_back(std::make_unique<Rectangle>(4.0, 6.0));
    
    for (const auto &shape : shapes) {
        shape->draw();  // Calls correct version
        std::cout << "Area: " << shape->area() << std::endl;
    }
}
```

**Explanation:**
- `virtual`: Enables runtime polymorphism
- Virtual destructor: Required for base classes (ensures derived destructor called)
- Pure virtual (`= 0`): Abstract class (cannot instantiate)
- `override`: Explicitly marks override (C++11, catches errors)
- Runtime binding: Correct function called based on actual object type
- Base pointer: Can point to derived objects

**Key Takeaways:**
- Use `virtual` for runtime polymorphism
- Always virtual destructor in base class
- Pure virtual = abstract class
- `override` keyword catches errors (C++11+)
- Base pointer can call derived methods

---

## Templates

### Overview

Templates enable generic programming in C++. They allow writing code that works with different types, providing type safety and code reuse without runtime overhead.

### Key Concepts

- **Function Templates**: Generic functions
- **Class Templates**: Generic classes
- **Template Specialization**: Custom implementation for specific types
- **Type Deduction**: Compiler infers template parameters
- **Template Parameters**: Type and non-type parameters

### Function Templates

**What this demonstrates:** Generic functions that work with any type.

**Code:**
```cpp
// Function template
template<typename T>
T max_value(T a, T b) {
    return (a > b) ? a : b;
}

// Template with multiple types
template<typename T, typename U>
auto add_different(T a, U b) -> decltype(a + b) {
    return a + b;
}

// Usage
int max_int = max_value(5, 10);
double max_double = max_value(3.14, 2.71);
std::string max_str = max_value(std::string("apple"), std::string("banana"));

auto sum = add_different(5, 3.14);  // Returns double
```

**Explanation:**
- `template<typename T>`: Template parameter
- Generic function: Works with any type T
- Type safety: Compiler checks types
- No runtime cost: Templates are compile-time
- Multiple parameters: `template<typename T, typename U>`
- Auto return: Use `auto` and `decltype` for return type

**Key Takeaways:**
- Templates enable generic programming
- Type-safe (checked at compile time)
- No runtime overhead
- Use `typename` or `class` (same meaning)

### Class Templates

**What this demonstrates:** Generic classes (containers, data structures).

**Code:**
```cpp
template<typename T>
class Stack {
private:
    std::vector<T> elements;
    
public:
    void push(const T &elem) {
        elements.push_back(elem);
    }
    
    void pop() {
        if (!elements.empty()) {
            elements.pop_back();
        }
    }
    
    T top() const {
        if (elements.empty()) {
            throw std::out_of_range("Stack is empty");
        }
        return elements.back();
    }
    
    bool empty() const {
        return elements.empty();
    }
    
    size_t size() const {
        return elements.size();
    }
};

// Usage
Stack<int> int_stack;
int_stack.push(1);
int_stack.push(2);

Stack<std::string> string_stack;
string_stack.push("Hello");
```

**Explanation:**
- Class template: Generic class
- Type parameter: `template<typename T>`
- Usage: `Stack<int>`, `Stack<std::string>`
- Works with any type: As long as operations are valid
- Type-safe: Compiler ensures correct usage

**Key Takeaways:**
- Class templates for generic containers
- Specify type when using: `Stack<int>`
- Type-safe generic programming
- STL containers are class templates

---

## STL (Standard Template Library)

### Overview

The STL provides containers, algorithms, and iterators. It's a powerful library for common data structures and algorithms, all type-safe through templates.

### Key Concepts

- **Containers**: Data structures (vector, list, map, set, etc.)
- **Algorithms**: Generic algorithms (sort, find, transform, etc.)
- **Iterators**: Generalize pointers (access container elements)
- **Function Objects**: Objects that act like functions
- **Adaptors**: Stack, queue, priority_queue

### Containers

**What this demonstrates:** STL containers (vector, list, map, set).

**Code:**
```cpp
#include <vector>
#include <list>
#include <map>
#include <set>
#include <deque>
#include <unordered_map>
#include <unordered_set>

// Vector (dynamic array)
std::vector<int> vec = {1, 2, 3, 4, 5};
vec.push_back(6);
vec.pop_back();
vec.insert(vec.begin(), 0);
vec.erase(vec.begin());

// List (doubly linked list)
std::list<int> lst = {1, 2, 3};
lst.push_front(0);
lst.push_back(4);

// Deque (double-ended queue)
std::deque<int> dq = {1, 2, 3};
dq.push_front(0);
dq.push_back(4);

// Set (ordered, unique)
std::set<int> s = {3, 1, 4, 1, 5, 9};  // {1, 3, 4, 5, 9}
s.insert(2);
s.erase(3);
bool has_five = s.count(5) > 0;

// Map (key-value pairs, ordered)
std::map<std::string, int> ages;
ages["Alice"] = 25;
ages["Bob"] = 30;
ages.insert({"Charlie", 35});

for (const auto &[name, age] : ages) {  // C++17 structured bindings
    std::cout << name << ": " << age << std::endl;
}

// Unordered containers (hash-based, C++11)
std::unordered_map<std::string, int> fast_ages;
fast_ages["Alice"] = 25;

// Pair and Tuple
std::pair<std::string, int> person = std::make_pair("Commander", 25);
std::tuple<std::string, int, double> data = std::make_tuple("Commander", 25, 6.0);
auto [name, age, height] = data;  // Structured binding (C++17)
```

**Explanation:**
- Vector: Dynamic array, fast random access
- List: Doubly-linked list, fast insertions/deletions
- Deque: Double-ended queue
- Set: Sorted, unique elements
- Map: Key-value pairs, sorted by key
- Unordered containers: Hash-based, faster lookups (C++11)
- Pair/Tuple: Hold multiple values

**Key Takeaways:**
- Choose container based on operations needed
- Vector for most cases (best performance)
- Map/set when ordering needed
- Unordered for faster lookups (no ordering needed)

### Algorithms

**What this demonstrates:** STL algorithms (sort, find, transform, etc.).

**Code:**
```cpp
#include <algorithm>
#include <numeric>

std::vector<int> numbers = {5, 2, 8, 1, 9, 3};

// Sort
std::sort(numbers.begin(), numbers.end());

// Reverse
std::reverse(numbers.begin(), numbers.end());

// Find
auto it = std::find(numbers.begin(), numbers.end(), 8);
if (it != numbers.end()) {
    std::cout << "Found: " << *it << std::endl;
}

// Count
int count = std::count_if(numbers.begin(), numbers.end(), 
                         [](int n) { return n > 5; });

// Transform
std::vector<int> squared(numbers.size());
std::transform(numbers.begin(), numbers.end(), squared.begin(),
              [](int n) { return n * n; });

// Accumulate
int sum = std::accumulate(numbers.begin(), numbers.end(), 0);

// For each
std::for_each(numbers.begin(), numbers.end(),
             [](int n) { std::cout << n << " "; });

// Remove if
numbers.erase(
    std::remove_if(numbers.begin(), numbers.end(),
                  [](int n) { return n % 2 == 0; }),
    numbers.end()
);

// Min/Max
auto min_it = std::min_element(numbers.begin(), numbers.end());
auto max_it = std::max_element(numbers.begin(), numbers.end());

// Binary search (requires sorted)
std::sort(numbers.begin(), numbers.end());
bool found = std::binary_search(numbers.begin(), numbers.end(), 5);
```

**Explanation:**
- Algorithms: Generic functions work with iterators
- Range: `[begin, end)` (half-open)
- Iterators: Generalize pointers
- Lambdas: Often used with algorithms (C++11+)
- No container modification: Algorithms don't change container structure
- Return iterators: `find()` returns iterator, `end()` if not found

**Key Takeaways:**
- Algorithms work with iterators
- Range is `[begin, end)` (half-open)
- Use lambdas for predicates/functions
- Algorithms don't modify container structure (except remove/erase pattern)

---

## Lambda Expressions & Functional Programming

### Overview

Lambda expressions (C++11+) enable functional programming style. They're anonymous function objects, useful with STL algorithms and modern C++ code.

### Key Concepts

- **Lambda Syntax**: `[capture](params) -> return_type { body }`
- **Captures**: Capture variables from enclosing scope
- **Generic Lambdas**: Type deduction (C++14)
- **Function Objects**: Objects callable like functions

### Lambda Basics

**What this demonstrates:** Basic lambda expressions.

**Code:**
```cpp
// Basic lambda
auto greet = []() {
    std::cout << "Hello from lambda!" << std::endl;
};
greet();

// Lambda with parameters
auto add = [](int a, int b) {
    return a + b;
};
std::cout << add(5, 3) << std::endl;

// Lambda with return type
auto divide = [](double a, double b) -> double {
    if (b == 0) throw std::invalid_argument("Division by zero");
    return a / b;
};

// Capture by value
int x = 10;
auto capture_value = [x]() {
    std::cout << "Captured x: " << x << std::endl;
};

// Capture by reference
auto capture_ref = [&x]() {
    x += 5;
};
capture_ref();
std::cout << "Modified x: " << x << std::endl;

// Capture all by value
int a = 1, b = 2;
auto capture_all_value = [=]() {
    std::cout << a << ", " << b << std::endl;
};

// Capture all by reference
auto capture_all_ref = [&]() {
    a += 10;
    b += 20;
};

// Mixed capture
auto mixed = [a, &b]() {
    b += a;  // a by value, b by reference
};

// Generic lambda (C++14)
auto generic = [](auto x, auto y) {
    return x + y;
};
std::cout << generic(5, 3) << std::endl;
std::cout << generic(3.14, 2.71) << std::endl;
```

**Explanation:**
- Lambda: Anonymous function object
- Capture: `[capture]` - access variables from enclosing scope
- `[x]`: Capture x by value
- `[&x]`: Capture x by reference
- `[=]`: Capture all by value
- `[&]`: Capture all by reference
- Generic lambda: `auto` parameters (C++14)

**Key Takeaways:**
- Lambdas: Anonymous functions
- Captures: Access enclosing scope variables
- Use with STL algorithms
- Generic lambdas for type flexibility (C++14+)

---

## Smart Pointers & Memory Management

### Overview

Smart pointers (C++11+) manage memory automatically using RAII (Resource Acquisition Is Initialization). They prevent memory leaks and provide exception safety.

### Key Concepts

- **RAII**: Resource management tied to object lifetime
- **unique_ptr**: Exclusive ownership, move-only
- **shared_ptr**: Shared ownership, reference counted
- **weak_ptr**: Non-owning reference to shared_ptr
- **Avoid raw pointers**: Use smart pointers for ownership

### unique_ptr

**What this demonstrates:** Exclusive ownership with unique_ptr.

**Code:**
```cpp
#include <memory>

// unique_ptr (exclusive ownership)
std::unique_ptr<int> ptr1 = std::make_unique<int>(42);
std::cout << *ptr1 << std::endl;

// Cannot copy, but can move
std::unique_ptr<int> ptr2 = std::move(ptr1);
// ptr1 is now nullptr

std::unique_ptr<Person> person = std::make_unique<Person>("Alice", 25);
person->greet();

// Automatically deleted when goes out of scope
```

**Explanation:**
- `unique_ptr`: Exclusive ownership (one owner)
- Cannot copy: Move-only type
- Automatic deletion: Destructor deletes owned object
- `make_unique`: Preferred creation (C++14)
- Exception safe: Even if exception thrown, memory freed

**Key Takeaways:**
- Use `unique_ptr` for exclusive ownership
- Cannot copy, can move
- Automatic memory management
- Prefer `make_unique` over `new`

### shared_ptr and weak_ptr

**What this demonstrates:** Shared ownership with reference counting.

**Code:**
```cpp
// shared_ptr (shared ownership, reference counted)
std::shared_ptr<int> sp1 = std::make_shared<int>(100);
std::shared_ptr<int> sp2 = sp1;  // Both own the same object
std::cout << "Use count: " << sp1.use_count() << std::endl;  // 2

sp2.reset();  // Release ownership
std::cout << "Use count: " << sp1.use_count() << std::endl;  // 1

// weak_ptr (non-owning reference)
std::shared_ptr<int> sp3 = std::make_shared<int>(200);
std::weak_ptr<int> wp = sp3;

if (auto locked = wp.lock()) {  // Convert to shared_ptr
    std::cout << *locked << std::endl;
}

sp3.reset();
if (wp.expired()) {
    std::cout << "Object has been destroyed" << std::endl;
}
```

**Explanation:**
- `shared_ptr`: Shared ownership, reference counted
- Multiple owners: Object deleted when last owner released
- `use_count()`: Number of shared_ptrs
- `weak_ptr`: Non-owning, doesn't affect lifetime
- `lock()`: Convert weak_ptr to shared_ptr (check if valid)
- `expired()`: Check if object destroyed

**Key Takeaways:**
- Use `shared_ptr` for shared ownership
- `weak_ptr` to break circular references
- Reference counting: Automatic deletion
- Prefer `make_shared` over `new`

---

## Exception Handling

### Overview

Exception handling allows programs to handle errors gracefully. C++ provides try-catch blocks, exception types, and RAII ensures cleanup.

### Key Concepts

- **Try-Catch**: Handle exceptions
- **Throw**: Throw exceptions
- **Exception Types**: Standard exceptions (runtime_error, logic_error, etc.)
- **RAII**: Automatic cleanup even with exceptions
- **Noexcept**: Functions that don't throw

### Exception Basics

**What this demonstrates:** Basic exception handling.

**Code:**
```cpp
#include <stdexcept>
#include <exception>

// Custom exception
class CustomException : public std::exception {
private:
    std::string message;
    
public:
    CustomException(const std::string &msg) : message(msg) {}
    
    const char* what() const noexcept override {
        return message.c_str();
    }
};

void exception_demo() {
    try {
        throw std::runtime_error("Something went wrong");
    } catch (const std::runtime_error &e) {
        std::cout << "Caught: " << e.what() << std::endl;
    }
    
    try {
        throw CustomException("Custom error");
    } catch (const CustomException &e) {
        std::cout << "Caught custom: " << e.what() << std::endl;
    } catch (const std::exception &e) {
        std::cout << "Caught general: " << e.what() << std::endl;
    } catch (...) {
        std::cout << "Caught unknown exception" << std::endl;
    }
    
    // RAII ensures cleanup even with exceptions
    try {
        std::unique_ptr<Person> p = std::make_unique<Person>("Bob", 30);
        throw std::runtime_error("Error!");
    } catch (...) {
        // Person destructor called automatically
    }
}
```

**Explanation:**
- `throw`: Throw exception
- `try`: Code that may throw
- `catch`: Handle specific exception type
- Multiple catch: Catch different types (more specific first)
- `catch(...)`: Catch all exceptions
- RAII: Smart pointers, containers automatically cleaned up
- Custom exceptions: Inherit from `std::exception`

**Key Takeaways:**
- Use exceptions for error handling
- Catch specific exceptions first
- RAII ensures cleanup
- Custom exceptions: Inherit from `std::exception`

---

## Modern C++ Features

### Overview

Modern C++ (C++11/14/17/20) adds powerful features: auto, lambdas, smart pointers, ranges, concepts, and more. Understanding modern C++ is essential.

### Key Concepts

- **C++11**: auto, lambdas, smart pointers, move semantics
- **C++14**: Generic lambdas, return type deduction
- **C++17**: structured bindings, optional, variant, if constexpr
- **C++20**: concepts, ranges, coroutines, modules

### Structured Bindings (C++17)

**What this demonstrates:** Decompose objects into variables.

**Code:**
```cpp
// Structured bindings
std::map<std::string, int> ages = {{"Alice", 25}, {"Bob", 30}};

for (const auto &[name, age] : ages) {
    std::cout << name << ": " << age << std::endl;
}

std::pair<int, std::string> data = {42, "answer"};
auto [number, text] = data;

std::tuple<std::string, int, double> person = {"Alice", 25, 5.6};
auto [name, age, height] = person;
```

**Explanation:**
- Structured bindings: Decompose objects
- Works with: pairs, tuples, structs (C++17)
- Cleaner: No need for `.first`, `.second`, `std::get<>()`
- Auto deduction: Types deduced automatically

**Key Takeaways:**
- Structured bindings: Cleaner tuple/pair access
- Works with pairs, tuples, structs
- C++17 feature

### Optional (C++17)

**What this demonstrates:** Optional values (may or may not have value).

**Code:**
```cpp
#include <optional>

std::optional<int> find_value(const std::vector<int> &vec, int target) {
    auto it = std::find(vec.begin(), vec.end(), target);
    if (it != vec.end()) {
        return *it;
    }
    return std::nullopt;
}

void optional_demo() {
    std::vector<int> numbers = {1, 2, 3, 4, 5};
    
    if (auto result = find_value(numbers, 3)) {
        std::cout << "Found: " << *result << std::endl;
    } else {
        std::cout << "Not found" << std::endl;
    }
    
    // Default value
    int value = find_value(numbers, 10).value_or(-1);
}
```

**Explanation:**
- `optional<T>`: May or may not have value
- `nullopt`: No value
- Check: `if (optional)` or `optional.has_value()`
- Access: `*optional` or `optional.value()`
- `value_or()`: Default if no value

**Key Takeaways:**
- Optional: Type-safe alternative to nullptr
- C++17 feature
- Better than returning -1 or nullptr

---

## File I/O

### Overview

C++ provides file I/O through streams (fstream). Files can be read/written in text or binary mode.

### Key Concepts

- **ofstream**: Output file stream (write)
- **ifstream**: Input file stream (read)
- **fstream**: Bidirectional file stream
- **Text vs Binary**: Text mode (formatted), binary mode (raw bytes)
- **String streams**: sstream for string I/O

### File Operations

**What this demonstrates:** Reading and writing files.

**Code:**
```cpp
#include <fstream>
#include <sstream>

// Writing
std::ofstream out("output.txt");
if (out.is_open()) {
    out << "Hello, World!" << std::endl;
    out << "Number: " << 42 << std::endl;
    out.close();
}

// Reading
std::ifstream in("output.txt");
if (in.is_open()) {
    std::string line;
    while (std::getline(in, line)) {
        std::cout << line << std::endl;
    }
    in.close();
}

// Binary I/O
std::ofstream bout("data.bin", std::ios::binary);
if (bout.is_open()) {
    int data[] = {1, 2, 3, 4, 5};
    bout.write(reinterpret_cast<char*>(data), sizeof(data));
    bout.close();
}

// String streams
std::stringstream ss;
ss << "Number: " << 42;
std::string result = ss.str();

int number;
ss >> result >> number;
```

**Explanation:**
- `ofstream`: Write to file
- `ifstream`: Read from file
- `is_open()`: Check if file opened successfully
- `getline()`: Read line (handles newlines)
- Binary mode: `ios::binary` (raw bytes)
- String streams: `stringstream` for string I/O

**Key Takeaways:**
- Use file streams for file I/O
- Check `is_open()` before using
- Binary mode for binary data
- String streams for string manipulation

---

## Multithreading

### Overview

C++11 added threading support. Threads, mutexes, condition variables, and futures enable concurrent programming.

### Key Concepts

- **thread**: Create threads
- **mutex**: Mutual exclusion (protect shared data)
- **lock_guard/unique_lock**: RAII locks
- **condition_variable**: Thread synchronization
- **future/async**: Asynchronous operations

### Threading Basics

**What this demonstrates:** Basic threading with mutex.

**Code:**
```cpp
#include <thread>
#include <mutex>
#include <chrono>
#include <vector>

void worker_function(int id) {
    std::cout << "Thread " << id << " working" << std::endl;
    std::this_thread::sleep_for(std::chrono::seconds(1));
}

std::mutex mtx;
int shared_counter = 0;

void increment_counter() {
    std::lock_guard<std::mutex> lock(mtx);
    shared_counter++;
}

void threading_demo() {
    // Basic thread
    std::thread t1(worker_function, 1);
    std::thread t2(worker_function, 2);
    
    t1.join();
    t2.join();
    
    // Lambda thread
    std::thread t3([]() {
        std::cout << "Lambda thread" << std::endl;
    });
    t3.join();
    
    // Multiple threads with mutex
    std::vector<std::thread> threads;
    for (int i = 0; i < 10; i++) {
        threads.emplace_back(increment_counter);
    }
    
    for (auto &t : threads) {
        t.join();
    }
    
    std::cout << "Counter: " << shared_counter << std::endl;
}
```

**Explanation:**
- `std::thread`: Create thread
- `join()`: Wait for thread to complete
- `mutex`: Protect shared data
- `lock_guard`: RAII lock (automatically unlocks)
- Thread safety: Use mutex for shared data

**Key Takeaways:**
- Use threads for concurrent execution
- Protect shared data with mutex
- Use `lock_guard` for RAII locking
- Call `join()` or `detach()` on threads

---

## Best Practices

### Memory Management

- **Use Smart Pointers**: Prefer `unique_ptr`, `shared_ptr` over raw pointers
- **RAII**: Resource management tied to object lifetime
- **Avoid new/delete**: Use smart pointers or containers
- **Rule of 3/5**: If you need custom copy/move, implement all

### Code Style

- **const correctness**: Use `const` whenever possible
- **auto**: Use when type is obvious
- **Range-based for**: Prefer over traditional for loops
- **Meaningful names**: Clear variable and function names
- **Small functions**: Single responsibility

### Modern C++

- **Use C++11/14/17 features**: Lambdas, auto, smart pointers
- **Prefer algorithms**: Use STL algorithms over loops
- **Move semantics**: Use when appropriate (large objects)
- **nullptr**: Use instead of NULL

### Exceptions

- **RAII**: Ensures cleanup even with exceptions
- **Specific exceptions**: Catch specific types first
- **Noexcept**: Mark functions that don't throw

---

## Common Patterns

### RAII Pattern

```cpp
class Resource {
    int* data;
public:
    Resource() : data(new int[100]) {}
    ~Resource() { delete[] data; }  // Automatic cleanup
    // No copy (or implement Rule of 3)
};
```

### PIMPL (Pointer to Implementation)

```cpp
// Header
class Widget {
    class Impl;
    std::unique_ptr<Impl> pImpl;
public:
    Widget();
    ~Widget();
};
```

### Factory Pattern

```cpp
class Shape {
public:
    virtual ~Shape() = default;
    static std::unique_ptr<Shape> create(const std::string& type);
};
```

---

## Resources

### Official Documentation

- **cppreference.com**: https://en.cppreference.com/
- **C++ Standard**: ISO/IEC 14882
- **ISO C++**: https://isocpp.org/

### Learning Resources

- **Learn C++**: https://www.learncpp.com/
- **cppreference Tutorial**: https://en.cppreference.com/w/cpp/language
- **cplusplus.com**: http://www.cplusplus.com/

### Community

- **Stack Overflow**: Tag: c++
- **r/cpp**: Reddit community
- **ISO C++ Forums**: https://isocpp.org/forums

### Tools

- **GCC**: GNU Compiler Collection
- **Clang**: LLVM-based compiler
- **MSVC**: Microsoft Visual C++
- **CMake**: Build system
- **GDB**: Debugger
- **Valgrind**: Memory profiling

---

