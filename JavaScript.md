# JavaScript - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Fundamentals & Basics](#fundamentals--basics)
4. [Operators](#operators)
5. [Strings](#strings)
6. [Arrays](#arrays)
7. [Objects](#objects)
8. [Functions](#functions)
9. [Control Flow](#control-flow)
10. [Classes & OOP (ES6+)](#classes--oop-es6)
11. [Asynchronous JavaScript](#asynchronous-javascript)
12. [Error Handling](#error-handling)
13. [Modules (ES6)](#modules-es6)
14. [Advanced Topics](#advanced-topics)
15. [DOM Manipulation (Browser)](#dom-manipulation-browser)
16. [Modern JavaScript Patterns](#modern-javascript-patterns)
17. [Testing & Debugging](#testing--debugging)
18. [Best Practices](#best-practices)
19. [Common Patterns](#common-patterns)
20. [Resources](#resources)

---

## Introduction

### What is JavaScript?

JavaScript is a high-level, interpreted programming language that was originally created for web browsers. It's now one of the core technologies of the World Wide Web, alongside HTML and CSS. JavaScript is a dynamic, prototype-based, multi-paradigm language that supports object-oriented, imperative, and functional programming styles.

### Why Learn JavaScript?

JavaScript is valuable for:

1. **Web Development**: Essential for frontend (React, Vue, Angular) and backend (Node.js)
2. **Universal Language**: Runs in browsers, servers, mobile apps (React Native), and desktop apps
3. **Dynamic Ecosystem**: Largest package ecosystem (npm) with millions of packages
4. **Career Opportunities**: High demand across full-stack, frontend, and backend roles
5. **Modern Features**: ES6+ brings powerful modern language features
6. **Interactive Web**: Enables dynamic, interactive web experiences
7. **Real-Time Applications**: WebSockets, real-time collaboration
8. **Progressive Web Apps**: Modern web application capabilities

### Key Features

- **Dynamic Typing**: Types determined at runtime
- **First-Class Functions**: Functions are objects, can be passed as arguments
- **Prototype-Based Inheritance**: Objects inherit from other objects
- **Event-Driven**: Asynchronous programming model
- **Closures**: Functions retain access to outer scope
- **Single-Threaded**: Event loop model for concurrency
- **Interpreted**: Runs directly in browsers and Node.js

---

## Getting Started

### Running JavaScript

**In Browser:**
- Open browser console (F12)
- Create HTML file with `<script>` tag
- Use inline scripts or external .js files

**In Node.js:**
```bash
node script.js
```

**Quick Start:**
```javascript
console.log("Hello, World!");
```

---

## Fundamentals & Basics

### Overview

JavaScript fundamentals include variables, data types, type checking, and type conversion. Understanding these basics is essential for JavaScript programming.

### Key Concepts

- **Variables**: `var`, `let`, `const`
- **Data Types**: Primitives (number, string, boolean, etc.)
- **Type Checking**: `typeof` operator
- **Type Conversion**: String(), Number(), Boolean()
- **Hoisting**: Variable and function hoisting
- **Scope**: Global, function, block scope

### Variables

**What this demonstrates:** Variable declarations in JavaScript.

**Code:**
```javascript
// var (function-scoped, avoid in modern code)
var oldWay = 'avoid using var';

// let (block-scoped, can reassign)
let modernWay = 'use let';
modernWay = 'reassigned';

// const (block-scoped, cannot reassign)
const constant = 'cannot reassign';
// constant = 'error';  // TypeError

// Block scope example
{
    let blockScoped = 'only in block';
    const alsoBlockScoped = 'also in block';
}
// console.log(blockScoped);  // ReferenceError
```

**Explanation:**
- `var`: Function-scoped, hoisted (avoid in modern code)
- `let`: Block-scoped, can be reassigned
- `const`: Block-scoped, cannot be reassigned (immutable binding)
- Block scope: Variables in `{}` are only accessible within block
- Prefer `const` by default, use `let` when reassignment needed

**Key Takeaways:**
- Use `let` and `const` (avoid `var`)
- `const` for values that don't change
- `let` for values that change
- Block scope for `let` and `const`

### Data Types

**What this demonstrates:** JavaScript data types.

**Code:**
```javascript
// Primitives
let number = 42;                      // Number
let bigInt = 9007199254740991n;      // BigInt (arbitrary precision)
let string = 'Hello, World!';         // String
let boolean = true;                   // Boolean
let undef = undefined;                // Undefined
let nothing = null;                   // Null
let sym = Symbol('unique');           // Symbol (unique identifier)

// Type checking
console.log(typeof number);           // "number"
console.log(typeof string);           // "string"
console.log(typeof boolean);          // "boolean"
console.log(typeof undef);            // "undefined"
console.log(typeof nothing);          // "object" (historical bug!)
console.log(typeof sym);              // "symbol"
console.log(typeof {});               // "object"
console.log(typeof []);               // "object" (arrays are objects)
console.log(Array.isArray([]));       // true (check if array)
```

**Explanation:**
- Primitives: number, bigint, string, boolean, undefined, null, symbol
- Objects: Everything else (arrays, functions, objects, dates)
- `typeof`: Returns type as string
- `null` bug: `typeof null` returns "object" (historical bug)
- Arrays: Use `Array.isArray()` to check if array

**Key Takeaways:**
- 7 primitive types + objects
- `typeof` for type checking
- `typeof null` returns "object" (bug)
- Use `Array.isArray()` for arrays

### Type Conversion

**What this demonstrates:** Converting between types.

**Code:**
```javascript
// Explicit conversion
let str = String(42);                 // "42"
let num = Number("42");               // 42
let bool = Boolean(1);                // true

// Parsing
let parsed = parseInt("42px");        // 42
let float = parseFloat("3.14");       // 3.14
parseInt("101", 2);                   // 5 (binary)

// Implicit conversion (type coercion)
"5" + 3;                              // "53" (string)
"5" - 3;                              // 2 (number)
true + 1;                             // 2 (number)

// Falsy values (convert to false)
Boolean("");                          // false
Boolean(0);                           // false
Boolean(null);                        // false
Boolean(undefined);                   // false
Boolean(NaN);                         // false
Boolean(false);                       // false

// Truthy values (everything else)
Boolean("hello");                     // true
Boolean(1);                           // true
Boolean([]);                          // true
Boolean({});                          // true
```

**Explanation:**
- Explicit: `String()`, `Number()`, `Boolean()`
- Parsing: `parseInt()`, `parseFloat()` (parse from string)
- Implicit: Type coercion (be careful!)
- Falsy: Values that convert to false
- Truthy: All other values

**Key Takeaways:**
- Use explicit conversion when needed
- Be aware of type coercion
- Know falsy values

---

## Operators

### Overview

JavaScript provides arithmetic, comparison, logical, bitwise, and other operators. Understanding operators is essential for writing expressions.

### Key Concepts

- **Arithmetic**: `+`, `-`, `*`, `/`, `%`, `**`
- **Comparison**: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`
- **Logical**: `&&`, `||`, `!`
- **Nullish Coalescing**: `??`
- **Optional Chaining**: `?.`
- **Ternary**: `? :`
- **Assignment**: `=`, `+=`, `-=`, etc.

### Arithmetic Operators

**What this demonstrates:** Arithmetic operations.

**Code:**
```javascript
let a = 10 + 5;        // 15
let b = 10 - 5;        // 5
let c = 10 * 5;        // 50
let d = 10 / 5;        // 2
let e = 10 % 3;        // 1 (modulo)
let f = 10 ** 2;       // 100 (exponentiation ES2016)

// Increment/Decrement
a++;                   // Post-increment (returns value, then increments)
++a;                   // Pre-increment (increments, then returns value)
b--;                   // Post-decrement
--b;                   // Pre-decrement
```

**Explanation:**
- Standard arithmetic: `+`, `-`, `*`, `/`
- Modulo: `%` (remainder)
- Exponentiation: `**` (ES2016)
- Increment/decrement: `++`, `--` (pre/post)
- Type coercion: `+` can concatenate strings

**Key Takeaways:**
- Standard arithmetic operators
- `**` for exponentiation
- `++`/`--` pre vs post matters

### Comparison Operators

**What this demonstrates:** Comparing values.

**Code:**
```javascript
// Loose equality (type coercion)
5 == "5";              // true (coerces types)
5 != "6";              // true

// Strict equality (no coercion)
5 === "5";             // false (different types)
5 !== "5";             // true

// Comparison
5 > 3;                 // true
5 < 10;                // true
5 >= 5;                // true
5 <= 5;                // true

// Always use strict equality (===, !==)
```

**Explanation:**
- `==`/`!=`: Loose equality (type coercion)
- `===`/`!==`: Strict equality (no coercion)
- Always use: `===` and `!==` (avoid `==` and `!=`)
- Comparison: `>`, `<`, `>=`, `<=` (numeric comparison)

**Key Takeaways:**
- Always use `===` and `!==`
- Avoid `==` and `!=` (type coercion can cause bugs)

### Logical Operators

**What this demonstrates:** Logical operations.

**Code:**
```javascript
// Logical AND
true && false;         // false
true && true;          // true

// Logical OR
true || false;         // true
false || false;        // false

// Logical NOT
!true;                 // false
!false;                // true

// Short-circuit evaluation
let user = null;
let name = user && user.name;         // null (short-circuits)
let name2 = user?.name || 'Guest';    // 'Guest'

// Truthy/falsy evaluation
"hello" && "world";    // "world" (returns last truthy)
"" || "default";       // "default" (returns first truthy)
```

**Explanation:**
- `&&`: AND (returns first falsy or last truthy)
- `||`: OR (returns first truthy or last falsy)
- `!`: NOT (negates)
- Short-circuit: Stops evaluating once result is known
- Useful for: Default values, conditional execution

**Key Takeaways:**
- `&&` and `||` use short-circuit evaluation
- Useful for default values and conditional execution
- Returns actual values, not just boolean

### Nullish Coalescing and Optional Chaining

**What this demonstrates:** Modern ES2020 operators.

**Code:**
```javascript
// Nullish coalescing (??) - ES2020
let value = null ?? 'default';        // 'default'
let value2 = undefined ?? 'default';  // 'default'
let value3 = 0 ?? 'default';          // 0 (only null/undefined trigger ??)
let value4 = '' ?? 'default';         // '' (empty string is not nullish)

// Optional chaining (?.) - ES2020
let user = { name: 'Alice', address: { city: 'NYC' } };
let city = user?.address?.city;       // 'NYC'
let city2 = user?.address?.zip;       // undefined (no error)

// Optional chaining with functions
let obj = { method: () => 'hello' };
obj.method?.();                       // 'hello'
obj.otherMethod?.();                  // undefined (no error)

// Optional chaining with arrays
let arr = [1, 2, 3];
arr?.[0];                             // 1
null?.[0];                            // undefined (no error)
```

**Explanation:**
- `??`: Nullish coalescing (only null/undefined trigger)
- `?.`: Optional chaining (safe property access)
- Prevents errors: Safe access to nested properties
- Useful for: API responses, optional properties

**Key Takeaways:**
- `??` for default values (only null/undefined)
- `?.` for safe property access
- Prevents errors from undefined/null

### Ternary Operator

**What this demonstrates:** Conditional expressions.

**Code:**
```javascript
let age = 18;
let status = age >= 18 ? 'adult' : 'minor';

// Nested ternary (avoid if complex)
let grade = score >= 90 ? 'A' : 
            score >= 80 ? 'B' : 
            score >= 70 ? 'C' : 'F';

// Use for simple conditionals
let message = isLoggedIn ? 'Welcome back!' : 'Please log in';
```

**Explanation:**
- Syntax: `condition ? valueIfTrue : valueIfFalse`
- Returns: One of two values based on condition
- Use for: Simple conditionals (avoid nested ternaries)

**Key Takeaways:**
- `condition ? trueValue : falseValue`
- Useful for simple conditionals
- Avoid deep nesting

---

## Strings

### Overview

Strings are sequences of characters. JavaScript provides many methods for string manipulation, including template literals for modern string interpolation.

### Key Concepts

- **String Creation**: Single quotes, double quotes, template literals
- **String Methods**: toUpperCase, toLowerCase, trim, slice, etc.
- **Template Literals**: `${expression}` syntax
- **Tagged Templates**: Function calls with template literals
- **String Properties**: length, indexing

### String Creation and Properties

**What this demonstrates:** Creating and accessing strings.

**Code:**
```javascript
// String creation
let str1 = 'Single quotes';
let str2 = "Double quotes";
let str3 = `Template literal ${str1}`;  // ES6 template literals

// Properties
str1.length;                          // 14
str1[0];                              // 'S' (character at index)
str1.charAt(0);                       // 'S'
str1.charCodeAt(0);                   // 83 (Unicode)

// Strings are immutable
let s = 'hello';
s[0] = 'H';                           // Doesn't change s
let s2 = 'H' + s.slice(1);            // 'Hello' (creates new string)
```

**Explanation:**
- Quotes: Single, double, or backticks (template literals)
- Immutable: Strings cannot be changed (create new string)
- Indexing: `str[index]` or `str.charAt(index)`
- Length: `str.length` property

**Key Takeaways:**
- Strings are immutable
- Use template literals for interpolation
- `length` property, indexing with `[]`

### String Methods

**What this demonstrates:** Common string methods.

**Code:**
```javascript
let str = 'Hello World';

// Case conversion
str.toUpperCase();                   // 'HELLO WORLD'
str.toLowerCase();                   // 'hello world'

// Trimming
'  hello  '.trim();                  // 'hello'
'  hello  '.trimStart();             // 'hello  '
'  hello  '.trimEnd();               // '  hello'

// Search
str.indexOf('World');                // 6
str.lastIndexOf('o');                // 7
str.includes('Hello');               // true
str.startsWith('Hello');             // true
str.endsWith('World');               // true

// Extract
str.slice(0, 5);                     // 'Hello'
str.substring(0, 5);                 // 'Hello'
str.substr(0, 5);                    // 'Hello' (deprecated)

// Split and join
str.split(' ');                      // ['Hello', 'World']
['Hello', 'World'].join('-');        // 'Hello-World'

// Replace
str.replace('World', 'Universe');    // 'Hello Universe'
str.replaceAll('l', 'L');            // 'HeLLo WorLd' (ES2021)

// Repeat and pad
'ha'.repeat(3);                      // 'hahaha'
'5'.padStart(3, '0');                // '005'
'5'.padEnd(3, '0');                  // '500'
```

**Explanation:**
- Methods: Strings have many methods for manipulation
- Search: `indexOf`, `includes`, `startsWith`, `endsWith`
- Extract: `slice` (preferred), `substring`, `substr` (deprecated)
- Split: `split()` converts to array
- Replace: `replace()` first match, `replaceAll()` all matches

**Key Takeaways:**
- Many string methods available
- `slice()` preferred over `substring()`
- `split()` and `join()` for string/array conversion

### Template Literals

**What this demonstrates:** ES6 template literals.

**Code:**
```javascript
// Basic interpolation
let name = 'Commander';
let age = 25;
let greeting = `Hello, ${name}! You are ${age} years old.`;

// Expressions
let x = 10;
let y = 20;
let sum = `The sum of ${x} and ${y} is ${x + y}.`;

// Multi-line strings
let multiline = `
    This is
    a multi-line
    string
`;

// Tagged templates
function tag(strings, ...values) {
    console.log(strings);             // Array of string parts
    console.log(values);              // Array of interpolated values
    return strings[0] + values[0].toUpperCase() + strings[1];
}
let result = tag`Hello ${name}!`;     // 'Hello COMMANDER!'
```

**Explanation:**
- Template literals: Use backticks (`)
- Interpolation: `${expression}` syntax
- Multi-line: Preserves line breaks
- Tagged templates: Function call with template literal
- Useful for: String formatting, SQL queries, HTML templates

**Key Takeaways:**
- Template literals with `${}` for interpolation
- Multi-line strings
- Tagged templates for advanced string processing

---

## Arrays

### Overview

Arrays are ordered collections of values. JavaScript arrays are dynamic, can contain mixed types, and have many built-in methods for manipulation.

### Key Concepts

- **Array Creation**: Literals, constructors, Array.from(), Array.of()
- **Array Methods**: push, pop, shift, unshift, splice, slice
- **Iteration Methods**: forEach, map, filter, reduce, find, some, every
- **Array Methods**: sort, reverse, concat, join
- **Spread Operator**: `...array`
- **Destructuring**: Array destructuring
- **Array-like Objects**: Convert to arrays

### Array Creation and Properties

**What this demonstrates:** Creating and accessing arrays.

**Code:**
```javascript
// Array creation
let arr1 = [1, 2, 3, 4, 5];
let arr2 = new Array(5);              // Empty array of length 5
let arr3 = Array.from('hello');       // ['h', 'e', 'l', 'l', 'o']
let arr4 = Array.of(1, 2, 3);         // [1, 2, 3]
let arr5 = Array(3).fill(0);          // [0, 0, 0]

// Properties
arr1.length;                          // 5
arr1[0];                              // 1 (access by index)

// Arrays can contain mixed types
let mixed = [1, 'hello', true, { name: 'Alice' }, [1, 2, 3]];
```

**Explanation:**
- Literal syntax: `[1, 2, 3]` (preferred)
- Constructor: `new Array(length)` or `new Array(...elements)`
- `Array.from()`: Create from iterable/array-like
- `Array.of()`: Create from arguments
- Dynamic: Arrays can grow/shrink
- Mixed types: Can contain any types

**Key Takeaways:**
- Use literal syntax `[]`
- Arrays are dynamic and can contain mixed types
- `length` property reflects array size

### Adding and Removing Elements

**What this demonstrates:** Modifying arrays.

**Code:**
```javascript
let arr = [1, 2, 3];

// Add/remove from end
arr.push(4);                          // [1, 2, 3, 4] (returns new length)
arr.pop();                            // 4, arr is [1, 2, 3] (returns removed element)

// Add/remove from start
arr.unshift(0);                       // [0, 1, 2, 3] (returns new length)
arr.shift();                          // 0, arr is [1, 2, 3] (returns removed element)

// Splice (add/remove at position)
arr.splice(1, 1);                     // Remove 1 element at index 1
arr.splice(1, 0, 10, 20);            // Insert 10, 20 at index 1 (remove 0)
arr.splice(1, 2, 100);                // Remove 2, insert 100

// Slice (extract portion, doesn't modify original)
let sub = arr.slice(1, 3);           // [element1, element2]
let copy = arr.slice();               // Shallow copy
```

**Explanation:**
- `push/pop`: End of array (stack operations)
- `unshift/shift`: Start of array (queue operations)
- `splice`: Add/remove at any position (modifies array)
- `slice`: Extract portion (doesn't modify, creates new array)
- `push`/`unshift` return new length
- `pop`/`shift` return removed element

**Key Takeaways:**
- `push/pop` for end, `unshift/shift` for start
- `splice` for adding/removing at position
- `slice` doesn't modify original array

### Array Iteration Methods

**What this demonstrates:** Iterating and transforming arrays.

**Code:**
```javascript
let arr = [1, 2, 3, 4, 5];

// forEach (iterate)
arr.forEach((value, index, array) => {
    console.log(value, index);
});

// map (transform each element)
let doubled = arr.map(x => x * 2);    // [2, 4, 6, 8, 10]

// filter (select elements)
let evens = arr.filter(x => x % 2 === 0);  // [2, 4]

// reduce (accumulate)
let sum = arr.reduce((acc, val) => acc + val, 0);  // 15
let max = arr.reduce((acc, val) => val > acc ? val : acc, arr[0]);

// find (first matching element)
let found = arr.find(x => x > 3);     // 4

// findIndex (index of first match)
let index = arr.findIndex(x => x > 3);  // 3

// some (any match)
arr.some(x => x > 10);                // false

// every (all match)
arr.every(x => x > 0);                // true
```

**Explanation:**
- `forEach`: Iterate (no return value)
- `map`: Transform each element (returns new array)
- `filter`: Select elements (returns new array)
- `reduce`: Accumulate to single value
- `find/findIndex`: Find first match
- `some/every`: Test condition (return boolean)
- All methods: Don't modify original (except forEach behavior)

**Key Takeaways:**
- `map` transforms, `filter` selects, `reduce` accumulates
- These methods don't modify original array
- Chain methods: `arr.map().filter().reduce()`

### Other Array Methods

**What this demonstrates:** Additional array operations.

**Code:**
```javascript
let arr = [3, 1, 4, 1, 5];

// Sorting
arr.sort();                           // [1, 1, 3, 4, 5] (alphabetical, mutates!)
arr.sort((a, b) => a - b);            // Numeric ascending
arr.sort((a, b) => b - a);            // Numeric descending

// Reverse
arr.reverse();                        // Reverses in place

// Concatenation
let arr2 = [6, 7, 8];
let combined = arr.concat(arr2);      // New array
let combined2 = [...arr, ...arr2];    // Spread operator

// Join
arr.join('-');                        // "3-1-4-1-5" (convert to string)

// Flat and flatMap
let nested = [1, [2, 3], [4, [5, 6]]];
nested.flat();                        // [1, 2, 3, 4, [5, 6]]
nested.flat(2);                       // [1, 2, 3, 4, 5, 6]
[1, 2, 3].flatMap(x => [x, x * 2]);  // [1, 2, 2, 4, 3, 6]
```

**Explanation:**
- `sort`: Sorts in place (mutates!), use compare function for numbers
- `reverse`: Reverses in place
- `concat`: Combines arrays (new array)
- `join`: Converts to string
- `flat`: Flattens nested arrays
- `flatMap`: Map then flatten

**Key Takeaways:**
- `sort` and `reverse` modify array
- Use compare function for numeric sorting
- `flat` and `flatMap` for nested arrays

### Array Destructuring and Spread

**What this demonstrates:** Destructuring and spread operator.

**Code:**
```javascript
let arr = [1, 2, 3, 4, 5];

// Destructuring
let [first, second, third] = arr;     // first=1, second=2, third=3
let [a, , c] = arr;                   // Skip element (a=1, c=3)
let [x, ...rest] = arr;               // x=1, rest=[2,3,4,5]
let [first2, second2 = 10] = [1];     // Default value (second2=10)

// Spread operator
let arr2 = [...arr];                  // Copy array
let arr3 = [0, ...arr, 6];            // [0, 1, 2, 3, 4, 5, 6]
Math.max(...arr);                     // 5 (spread as arguments)

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4);                      // 10
```

**Explanation:**
- Destructuring: Extract values from array
- Skip elements: Leave empty `,`
- Rest: `...rest` collects remaining elements
- Default values: `[a, b = default]`
- Spread: `...array` expands array
- Rest parameters: `...params` in function

**Key Takeaways:**
- Destructuring for extracting values
- Spread operator for copying/combining
- Rest for collecting remaining elements

---

## Objects

### Overview

Objects are collections of key-value pairs. JavaScript objects are fundamental data structures used for storing and organizing data.

### Key Concepts

- **Object Creation**: Literals, constructors, Object.create()
- **Property Access**: Dot notation, bracket notation
- **Object Methods**: keys, values, entries, assign
- **Getters/Setters**: Computed properties
- **Property Descriptors**: Define property behavior
- **Object Methods**: freeze, seal, preventExtensions
- **Destructuring**: Object destructuring
- **Shorthand**: Property and method shorthand

### Object Creation and Access

**What this demonstrates:** Creating and accessing objects.

**Code:**
```javascript
// Object literal (preferred)
let obj = {
    name: 'Alice',
    age: 25,
    city: 'New York'
};

// Constructor
let obj2 = new Object();
obj2.name = 'Bob';

// Accessing properties
obj.name;                              // 'Alice' (dot notation)
obj['age'];                            // 25 (bracket notation)
let prop = 'city';
obj[prop];                             // 'New York' (dynamic)

// Adding/modifying
obj.country = 'USA';
obj['email'] = 'alice@example.com';

// Deleting
delete obj.city;
```

**Explanation:**
- Literal syntax: `{ key: value }` (preferred)
- Dot notation: `obj.property` (static keys)
- Bracket notation: `obj['property']` (dynamic keys)
- Properties: Can be added/modified/deleted dynamically
- Keys: Strings or symbols

**Key Takeaways:**
- Use literal syntax for objects
- Dot notation for static keys, bracket for dynamic
- Properties can be added/modified/deleted

### Object Methods

**What this demonstrates:** Working with object properties.

**Code:**
```javascript
let obj = { name: 'Alice', age: 25, city: 'NYC' };

// Object.keys (property names)
Object.keys(obj);                      // ['name', 'age', 'city']

// Object.values (property values)
Object.values(obj);                    // ['Alice', 25, 'NYC']

// Object.entries (key-value pairs)
Object.entries(obj);                   // [['name', 'Alice'], ['age', 25], ...]

// Object.assign (merge objects)
let merged = Object.assign({}, obj, { country: 'USA' });
let merged2 = { ...obj, country: 'USA' };  // Spread operator

// Checking properties
'name' in obj;                         // true
obj.hasOwnProperty('name');            // true (own property)
obj.name !== undefined;                // true (checks if defined)

// Freezing
Object.freeze(obj);                    // Make immutable
Object.seal(obj);                      // Prevent add/delete (can modify)
Object.preventExtensions(obj);         // Prevent adding properties
```

**Explanation:**
- `Object.keys()`: Array of property names
- `Object.values()`: Array of property values
- `Object.entries()`: Array of [key, value] pairs
- `Object.assign()`: Merge objects (first arg is target)
- Spread: `{ ...obj }` for merging/copying
- `in` operator: Checks if property exists (including inherited)
- `hasOwnProperty()`: Checks own property only

**Key Takeaways:**
- `Object.keys/values/entries` for property operations
- `Object.assign` or spread for merging
- `freeze/seal/preventExtensions` for immutability

### Getters, Setters, and Property Descriptors

**What this demonstrates:** Advanced object properties.

**Code:**
```javascript
// Getters and setters
let user = {
    firstName: 'John',
    lastName: 'Doe',
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    },
    set fullName(value) {
        [this.firstName, this.lastName] = value.split(' ');
    }
};

user.fullName;                         // 'John Doe'
user.fullName = 'Jane Smith';          // Sets firstName and lastName

// Property descriptors
let obj = {};
Object.defineProperty(obj, 'readOnly', {
    value: 42,
    writable: false,
    enumerable: true,
    configurable: false
});

// Shorthand properties (ES6)
let x = 10, y = 20;
let point = { x, y };                  // Same as { x: x, y: y }

// Computed property names
let key = 'dynamic';
let obj2 = {
    [key]: 'value',
    [`${key}2`]: 'value2'
};

// Method shorthand
let obj3 = {
    name: 'Object',
    greet() {                          // Instead of greet: function()
        return `Hello from ${this.name}`;
    }
};
```

**Explanation:**
- Getters: `get property()` - accessed like property
- Setters: `set property(value)` - assigned like property
- Property descriptors: Control property behavior
- Shorthand: `{ x, y }` same as `{ x: x, y: y }`
- Computed names: `[expression]` for dynamic keys
- Method shorthand: `method() { }` instead of `method: function() { }`

**Key Takeaways:**
- Getters/setters for computed properties
- Property descriptors for advanced control
- Shorthand syntax for cleaner code

---

## Functions

### Overview

Functions are first-class citizens in JavaScript. They can be assigned to variables, passed as arguments, and returned from other functions. JavaScript supports multiple function syntaxes.

### Key Concepts

- **Function Declaration**: `function name() { }`
- **Function Expression**: `const fn = function() { }`
- **Arrow Functions**: `const fn = () => { }`
- **Default Parameters**: `function fn(param = default) { }`
- **Rest Parameters**: `function fn(...args) { }`
- **Closures**: Functions capture outer scope
- **Higher-Order Functions**: Functions that take/return functions
- **IIFE**: Immediately Invoked Function Expression

### Function Types

**What this demonstrates:** Different ways to define functions.

**Code:**
```javascript
// Function declaration (hoisted)
function greet(name) {
    return `Hello, ${name}!`;
}

// Function expression
const greet2 = function(name) {
    return `Hello, ${name}!`;
};

// Arrow function (ES6)
const greet3 = (name) => {
    return `Hello, ${name}!`;
};

// Arrow function (single expression, implicit return)
const greet4 = name => `Hello, ${name}!`;
const add = (a, b) => a + b;

// Arrow function (no parameters)
const sayHi = () => 'Hi!';
```

**Explanation:**
- Function declaration: Hoisted (can call before definition)
- Function expression: Not hoisted, assigned to variable
- Arrow function: Shorter syntax, no `this` binding
- Implicit return: Single expression doesn't need `return`
- Parameters: Parentheses optional for single parameter

**Key Takeaways:**
- Function declarations are hoisted
- Arrow functions have no `this` binding
- Use arrow functions for callbacks

### Parameters

**What this demonstrates:** Function parameters.

**Code:**
```javascript
// Default parameters (ES6)
function greet(name = 'Guest') {
    return `Hello, ${name}!`;
}

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4, 5);                   // 15

// Destructuring parameters
function displayUser({ name, age }) {
    console.log(name, age);
}
displayUser({ name: 'Alice', age: 25 });

// Spread operator (calling)
let nums = [1, 2, 3];
Math.max(...nums);                    // 3 (spreads as arguments)
```

**Explanation:**
- Default parameters: `param = defaultValue`
- Rest parameters: `...params` collects remaining arguments
- Destructuring: Extract properties from object parameter
- Spread operator: `...array` spreads array as arguments
- Arguments object: Older way (avoid, use rest parameters)

**Key Takeaways:**
- Default parameters for optional values
- Rest parameters for variable arguments
- Destructuring for object parameters

### Closures and Higher-Order Functions

**What this demonstrates:** Closures and function composition.

**Code:**
```javascript
// Closure (function captures outer scope)
function counter() {
    let count = 0;
    return {
        increment() { return ++count; },
        decrement() { return --count; },
        getCount() { return count; }
    };
}
let myCounter = counter();
myCounter.increment();                // 1
myCounter.increment();                // 2

// Higher-order function
function makeMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}
let double = makeMultiplier(2);
double(5);                            // 10

// Callback function
function processData(data, callback) {
    let result = data * 2;
    callback(result);
}
processData(5, result => console.log(result));

// IIFE (Immediately Invoked Function Expression)
(function() {
    console.log('Executed immediately');
})();
```

**Explanation:**
- Closure: Function retains access to outer scope
- Higher-order function: Takes/returns functions
- Callback: Function passed as argument
- IIFE: Execute function immediately (creates scope)
- Useful for: Data privacy, callbacks, modules (old style)

**Key Takeaways:**
- Closures capture outer scope
- Higher-order functions take/return functions
- IIFE creates private scope

---

## Control Flow

### Overview

Control flow statements determine the order of execution. JavaScript supports if/else, switch, loops (for, while, do-while), and control statements (break, continue).

### Key Concepts

- **Conditionals**: if/else, ternary operator, switch
- **Loops**: for, while, do-while, for...of, for...in
- **Control Statements**: break, continue, labels
- **Loop Variations**: forEach, map, filter (array methods)

### If/Else and Switch

**What this demonstrates:** Conditional statements.

**Code:**
```javascript
// if/else
let age = 18;
if (age >= 18) {
    console.log('Adult');
} else if (age >= 13) {
    console.log('Teenager');
} else {
    console.log('Child');
}

// Switch
let day = 'Monday';
switch (day) {
    case 'Monday':
        console.log('Start of week');
        break;
    case 'Friday':
        console.log('End of week');
        break;
    default:
        console.log('Mid-week');
}
```

**Explanation:**
- `if/else`: Conditional execution
- `switch`: Multiple cases (use `break` to prevent fall-through)
- `default`: Default case in switch
- Ternary operator: `condition ? trueValue : falseValue`

**Key Takeaways:**
- `if/else` for conditionals
- `switch` for multiple cases
- Always use `break` in switch cases

### Loops

**What this demonstrates:** Different loop types.

**Code:**
```javascript
// for loop
for (let i = 0; i < 10; i++) {
    console.log(i);
}

// for...of (iterate values)
let array = [1, 2, 3, 4, 5];
for (let value of array) {
    console.log(value);
}

// for...in (iterate keys)
let obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
    console.log(key, obj[key]);
}

// while loop
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}

// do...while loop
let j = 0;
do {
    console.log(j);
    j++;
} while (j < 5);
```

**Explanation:**
- `for`: Traditional loop with initialization, condition, increment
- `for...of`: Iterate over iterable values (arrays, strings)
- `for...in`: Iterate over object keys (includes inherited)
- `while`: Loop while condition is true
- `do...while`: Execute once, then loop while condition is true

**Key Takeaways:**
- Use `for...of` for arrays
- Use `for...in` for objects (be careful with inherited properties)
- `do...while` executes at least once

---

## Classes & OOP (ES6+)

### Overview

ES6 introduced class syntax to JavaScript, providing a cleaner way to work with object-oriented programming. Classes are syntactic sugar over JavaScript's prototype-based inheritance.

### Key Concepts

- **Class Declaration**: `class Name { }`
- **Constructor**: `constructor() { }`
- **Methods**: Instance and static methods
- **Inheritance**: `extends` keyword
- **Getters/Setters**: Computed properties
- **Private Fields**: `#privateField` (ES2022)
- **Super**: Call parent class methods

### Classes

**What this demonstrates:** Creating and using classes.

**Code:**
```javascript
// Class declaration
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    // Instance method
    greet() {
        return `Hello, I'm ${this.name}`;
    }
    
    // Getter
    get info() {
        return `${this.name}, ${this.age}`;
    }
    
    // Setter
    set info(value) {
        [this.name, this.age] = value.split(', ');
    }
    
    // Static method
    static species() {
        return 'Homo sapiens';
    }
    
    // Private field (ES2022)
    #privateField = 'secret';
    
    getPrivate() {
        return this.#privateField;
    }
}

let person1 = new Person('Alice', 30);
person1.greet();                      // 'Hello, I'm Alice'
Person.species();                     // 'Homo sapiens'

// Inheritance
class Employee extends Person {
    constructor(name, age, company) {
        super(name, age);             // Call parent constructor
        this.company = company;
    }
    
    // Override method
    greet() {
        return `${super.greet()}, I work at ${this.company}`;
    }
}
```

**Explanation:**
- Classes: Syntactic sugar over prototypes
- `constructor`: Initialize instance
- Methods: Defined in class body
- Static methods: Called on class, not instance
- `extends`: Inheritance
- `super`: Call parent class
- Private fields: `#field` syntax (ES2022)

**Key Takeaways:**
- Classes are syntactic sugar over prototypes
- Use `extends` for inheritance
- `super` calls parent class
- Private fields use `#` syntax

---

## Asynchronous JavaScript

### Overview

JavaScript is single-threaded but supports asynchronous operations through callbacks, Promises, and async/await. Understanding async programming is crucial for modern JavaScript.

### Key Concepts

- **Callbacks**: Function passed as argument
- **Promises**: Handle async operations
- **async/await**: Syntactic sugar for Promises
- **Promise Methods**: all, race, allSettled, any
- **Event Loop**: How JavaScript handles async

### Promises

**What this demonstrates:** Working with Promises.

**Code:**
```javascript
// Creating Promise
let promise = new Promise((resolve, reject) => {
    setTimeout(() => {
        let success = true;
        if (success) {
            resolve('Success!');
        } else {
            reject('Error!');
        }
    }, 1000);
});

// Using Promise
promise
    .then(result => console.log(result))
    .catch(error => console.error(error))
    .finally(() => console.log('Done'));

// Promise chaining
fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error(error));

// Promise.all (wait for all)
Promise.all([promise1, promise2, promise3])
    .then(results => console.log(results));

// Promise.race (wait for first)
Promise.race([promise1, promise2])
    .then(result => console.log(result));
```

**Explanation:**
- Promise: Represents async operation
- `resolve`: Successful completion
- `reject`: Error/failure
- `then`: Handle success
- `catch`: Handle errors
- `finally`: Always executes
- `Promise.all`: Wait for all promises
- `Promise.race`: Wait for first promise

**Key Takeaways:**
- Promises handle async operations
- Chain with `then/catch`
- `Promise.all` for parallel operations

### Async/Await

**What this demonstrates:** Modern async syntax.

**Code:**
```javascript
// Async function
async function fetchUserData() {
    try {
        let response = await fetch('https://api.example.com/user');
        let data = await response.json();
        return data;
    } catch (error) {
        console.error(error);
    }
}

// Multiple async operations
async function processData() {
    let [user, posts, comments] = await Promise.all([
        fetchUser(),
        fetchPosts(),
        fetchComments()
    ]);
    return { user, posts, comments };
}
```

**Explanation:**
- `async`: Function returns Promise
- `await`: Wait for Promise to resolve
- `try/catch`: Error handling
- Cleaner syntax: Easier to read than Promise chains
- Parallel: Use `Promise.all` for parallel operations

**Key Takeaways:**
- `async/await` for cleaner async code
- Use `try/catch` for error handling
- `Promise.all` for parallel operations

---

## Error Handling

### Overview

Error handling prevents programs from crashing and provides graceful error recovery. JavaScript uses try/catch/finally blocks and throw statements.

### Key Concepts

- **Try/Catch/Finally**: Error handling blocks
- **Throw**: Throw errors
- **Error Types**: Error, TypeError, ReferenceError, etc.
- **Custom Errors**: Create error classes
- **Error Propagation**: Errors bubble up call stack

### Error Handling

**What this demonstrates:** Handling errors.

**Code:**
```javascript
// Try/catch/finally
try {
    let result = riskyOperation();
} catch (error) {
    console.error('Error:', error.message);
    console.error('Stack:', error.stack);
} finally {
    console.log('Cleanup');
}

// Throwing errors
function divide(a, b) {
    if (b === 0) {
        throw new Error('Division by zero');
    }
    return a / b;
}

// Custom errors
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = 'ValidationError';
    }
}

// Error types
try {
    throw new TypeError('Wrong type');
} catch (e) {
    if (e instanceof TypeError) {
        console.log('Type error');
    }
}
```

**Explanation:**
- `try`: Code that might throw error
- `catch`: Handle errors
- `finally`: Always executes
- `throw`: Throw error
- Error types: Built-in error types
- Custom errors: Extend Error class

**Key Takeaways:**
- Use `try/catch` for error handling
- `finally` always executes
- Create custom error classes

---

## Modules (ES6)

### Overview

ES6 modules provide a standard way to organize and share code. Modules allow code reuse and better organization.

### Key Concepts

- **Export**: Export functions, classes, variables
- **Import**: Import from modules
- **Default Export**: Single default export
- **Named Export**: Multiple named exports
- **Module Scope**: Each module has its own scope

### Modules

**What this demonstrates:** ES6 modules.

**Code:**
```javascript
// Exporting (module.js)
export const PI = 3.14159;
export function add(a, b) {
    return a + b;
}
export class Calculator {
    multiply(a, b) {
        return a * b;
    }
}

// Default export
export default function greet(name) {
    return `Hello, ${name}!`;
}

// Importing (main.js)
import greet, { PI, add, Calculator } from './module.js';

// Import all
import * as utils from './module.js';
utils.add(1, 2);

// Rename imports
import { add as sum } from './module.js';
```

**Explanation:**
- `export`: Export from module
- `export default`: Default export
- `import`: Import from module
- Named imports: `{ name }` syntax
- Default import: No braces
- Modules: Each file is a module

**Key Takeaways:**
- Use ES6 modules for code organization
- `export` for exports, `import` for imports
- Default export is single export

---

## Advanced Topics

### Overview

Advanced JavaScript topics include Symbols, Generators, Proxy, Reflect, Map/Set, WeakMap/WeakSet, and Regular Expressions.

### Key Concepts

- **Symbols**: Unique identifiers
- **Generators**: Functions that yield values
- **Proxy**: Intercept object operations
- **Map/Set**: Alternative data structures
- **WeakMap/WeakSet**: Garbage-collectible collections
- **Regular Expressions**: Pattern matching

### Advanced Features

**What this demonstrates:** Advanced JavaScript features.

**Code:**
```javascript
// Symbols
let sym1 = Symbol('description');
let sym2 = Symbol('description');
sym1 === sym2;                        // false (always unique)

// Generators
function* generatorFunction() {
    yield 1;
    yield 2;
    yield 3;
}
let gen = generatorFunction();
gen.next();                           // { value: 1, done: false }

// Map
let map = new Map();
map.set('key', 'value');
map.get('key');                       // 'value'

// Set
let set = new Set([1, 2, 3, 3, 4]);  // [1, 2, 3, 4]
set.add(5);
set.has(3);                           // true

// Regular Expressions
let regex = /pattern/gi;
text.match(regex);
text.replace(regex, 'replacement');
```

**Explanation:**
- Symbols: Unique identifiers
- Generators: Functions with `yield`
- Map: Key-value pairs (any type as key)
- Set: Unique values
- Regex: Pattern matching

**Key Takeaways:**
- Symbols for unique identifiers
- Generators for iterable sequences
- Map/Set for alternative data structures

---

## DOM Manipulation (Browser)

### Overview

The Document Object Model (DOM) represents HTML documents as objects. DOM manipulation allows JavaScript to interact with web pages.

### Key Concepts

- **Selecting Elements**: getElementById, querySelector, etc.
- **Creating Elements**: createElement
- **Modifying Elements**: textContent, innerHTML, style
- **Event Listeners**: addEventListener
- **Event Handling**: Event objects, propagation

### DOM Basics

**What this demonstrates:** Basic DOM operations.

**Code:**
```javascript
// Selecting elements
let element = document.getElementById('myId');
let elements = document.querySelectorAll('.myClass');

// Creating elements
let div = document.createElement('div');
div.textContent = 'Hello';
div.innerHTML = '<strong>Hello</strong>';

// Modifying styles
div.style.color = 'blue';
div.style.backgroundColor = 'yellow';

// Classes
div.classList.add('active');
div.classList.remove('active');
div.classList.toggle('active');

// Event listeners
element.addEventListener('click', function(event) {
    console.log('Clicked!', event.target);
});
```

**Explanation:**
- DOM: Document Object Model
- Selecting: Various methods to select elements
- Creating: `createElement` creates new elements
- Modifying: Properties and methods to modify elements
- Events: Respond to user interactions

**Key Takeaways:**
- Use `querySelector` for modern selection
- `textContent` safer than `innerHTML`
- Use `addEventListener` for events

---

## Modern JavaScript Patterns

### Overview

Modern JavaScript patterns include module patterns, design patterns, and best practices for organizing code.

### Key Concepts

- **Module Pattern**: Encapsulation
- **Revealing Module**: Public API pattern
- **Factory Pattern**: Object creation
- **Singleton Pattern**: Single instance
- **Observer Pattern**: Event-driven architecture

### Patterns

**What this demonstrates:** Common patterns.

**Code:**
```javascript
// Module Pattern
const Module = (function() {
    let privateVar = 'private';
    
    return {
        publicMethod() {
            return privateVar;
        }
    };
})();

// Factory Pattern
function createUser(name, age) {
    return {
        name,
        age,
        greet() {
            return `Hello, I'm ${this.name}`;
        }
    };
}
```

**Explanation:**
- Patterns: Solutions to common problems
- Module: Encapsulation with private variables
- Factory: Create objects
- Useful for: Code organization, reusability

**Key Takeaways:**
- Patterns solve common problems
- Module pattern for encapsulation
- Use appropriate pattern for situation

---

## Testing & Debugging

### Overview

Testing and debugging are essential for writing reliable code. JavaScript provides various tools and techniques for testing and debugging.

### Key Concepts

- **Console Methods**: log, error, warn, table
- **Debugger**: Breakpoint debugging
- **Unit Testing**: Test individual functions
- **Performance**: Measure execution time

### Testing & Debugging

**What this demonstrates:** Testing and debugging techniques.

**Code:**
```javascript
// Console methods
console.log('Log');
console.error('Error');
console.warn('Warning');
console.table([{name: 'Alice'}, {name: 'Bob'}]);

// Debugger
function buggyFunction() {
    let x = 10;
    debugger;                         // Pause execution
    return x * 2;
}

// Performance
let start = performance.now();
// ... code to measure ...
let end = performance.now();
console.log(`Took ${end - start}ms`);
```

**Explanation:**
- Console: Various methods for output
- Debugger: Breakpoint debugging
- Performance: Measure execution time
- Testing: Write tests for code

**Key Takeaways:**
- Use console methods for debugging
- `debugger` for breakpoints
- Measure performance when needed

---

## Best Practices

### Code Style

- **Use const/let**: Avoid `var`
- **Use arrow functions**: For callbacks
- **Use template literals**: For strings
- **Use strict equality**: `===` not `==`
- **Use meaningful names**: Descriptive variable/function names

### Async Programming

- **Use async/await**: Over raw Promises when possible
- **Handle errors**: Always use try/catch with async
- **Avoid callback hell**: Use Promises or async/await
- **Parallel operations**: Use `Promise.all` when possible

### Performance

- **Avoid premature optimization**: Write clear code first
- **Use appropriate data structures**: Map/Set when needed
- **Minimize DOM access**: Cache DOM elements
- **Debounce/throttle**: For frequent events

---

## Common Patterns

### Default Parameters

```javascript
function greet(name = 'Guest') {
    return `Hello, ${name}!`;
}
```

### Destructuring

```javascript
let { name, age } = user;
let [first, second] = array;
```

### Spread Operator

```javascript
let arr2 = [...arr1];
let obj2 = { ...obj1 };
```

### Optional Chaining

```javascript
let city = user?.address?.city;
```

---

## Resources

### Official Documentation

- **MDN Web Docs**: https://developer.mozilla.org/en-US/docs/Web/JavaScript
- **ECMAScript Specification**: https://tc39.es/ecma262/
- **Node.js Documentation**: https://nodejs.org/docs/

### Learning Resources

- **MDN JavaScript Guide**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide
- **JavaScript.info**: https://javascript.info/
- **Eloquent JavaScript**: https://eloquentjavascript.net/

### Community

- **Stack Overflow**: Tag: javascript
- **r/javascript**: Reddit community
- **JavaScript Weekly**: Newsletter

### Tools

- **Node.js**: JavaScript runtime
- **npm/yarn**: Package managers
- **ESLint**: Code linting
- **Prettier**: Code formatting
- **TypeScript**: Typed superset of JavaScript
- **Babel**: JavaScript compiler/transpiler

---

