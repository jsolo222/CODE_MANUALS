# TypeScript - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Setup & Basics](#setup--basics)
4. [Basic Types](#basic-types)
5. [Type Annotations & Inference](#type-annotations--inference)
6. [Interfaces](#interfaces)
7. [Classes](#classes)
8. [Functions](#functions)
9. [Generics](#generics)
10. [Advanced Types](#advanced-types)
11. [Decorators](#decorators)
12. [Modules](#modules)
13. [Namespaces](#namespaces)
14. [Type Manipulation & Inference](#type-manipulation--inference)
15. [Async/Await](#asyncawait)
16. [Best Practices](#best-practices)
17. [Common Patterns](#common-patterns)
18. [Resources](#resources)

---

## Introduction

### What is TypeScript?

TypeScript is a statically typed superset of JavaScript developed by Microsoft. It adds optional static type annotations to JavaScript, enabling better tooling, catching errors at compile time, and improving code maintainability. TypeScript compiles to plain JavaScript, so it can run anywhere JavaScript runs.

### Why Learn TypeScript?

TypeScript is valuable for:

1. **Type Safety**: Catch errors before runtime with static type checking
2. **Better IDE Support**: Autocomplete, refactoring, navigation
3. **Large-Scale Development**: Easier to maintain large codebases
4. **JavaScript Compatibility**: Superset of JavaScript, gradual adoption
5. **Modern JavaScript**: Access to latest JavaScript features via compilation
6. **Industry Standard**: Used by Angular, React, Vue, Node.js
7. **Documentation**: Types serve as inline documentation
8. **Refactoring**: Safer refactoring with type checking

### Key Features

- **Static Typing**: Type annotations for variables, functions, classes
- **Type Inference**: Automatic type detection where possible
- **Interfaces**: Define contracts for objects
- **Generics**: Write reusable, type-safe code
- **Union Types**: Variables can be one of several types
- **Optional Types**: Gradual typing, can use JavaScript when needed
- **Compiles to JavaScript**: Transpiles to ES5/ES6/ESNext

---

## Getting Started

### Installation

**Install TypeScript:**
```bash
npm install -g typescript
```

**Verify Installation:**
```bash
tsc --version
```

### Your First TypeScript Program

**Code:**
```typescript
function greet(name: string): string {
    return `Hello, ${name}!`;
}

console.log(greet("World"));
```

**Compile and Run:**
```bash
tsc hello.ts          # Compiles to hello.js
node hello.js         # Run JavaScript
```

---

## Setup & Basics

### Overview

TypeScript setup involves installing the compiler and configuring `tsconfig.json`. Understanding the basics helps you get started with TypeScript development.

### Key Concepts

- **TypeScript Compiler**: `tsc` compiles TypeScript to JavaScript
- **tsconfig.json**: Configuration file for compiler options
- **Type Annotations**: Explicit type declarations
- **Type Inference**: Automatic type detection
- **Compilation**: TypeScript compiles to JavaScript

### TypeScript Configuration

**What this demonstrates:** Setting up TypeScript with tsconfig.json.

**Code:**
```json
{
  "compilerOptions": {
    "target": "ES2020",              // JavaScript version to compile to
    "module": "commonjs",            // Module system
    "lib": ["ES2020"],               // Library files to include
    "strict": true,                  // Enable strict type checking
    "esModuleInterop": true,         // Enable ES module interop
    "skipLibCheck": true,            // Skip checking declaration files
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist",              // Output directory
    "rootDir": "./src",              // Root directory
    "declaration": true,             // Generate .d.ts files
    "sourceMap": true                // Generate source maps
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

**Explanation:**
- `target`: ECMAScript version to compile to
- `module`: Module system (commonjs, ES2015, etc.)
- `strict`: Enable all strict type checking options
- `outDir`: Where compiled JavaScript goes
- `rootDir`: Source directory
- `include/exclude`: Files to include/exclude

**Key Takeaways:**
- `tsconfig.json` configures TypeScript compiler
- `strict: true` enables strict type checking (recommended)
- Configure `target` and `module` for your environment

### Compilation

**What this demonstrates:** Compiling TypeScript files.

**Commands:**
```bash
# Compile single file
tsc hello.ts

# Compile with watch mode
tsc --watch

# Compile all files in project
tsc

# Compile with specific config
tsc --project tsconfig.json
```

**Explanation:**
- `tsc filename.ts`: Compile single file
- `tsc --watch`: Watch mode (recompile on changes)
- `tsc`: Compile all files (uses tsconfig.json)
- Output: Generates JavaScript files

**Key Takeaways:**
- `tsc` compiles TypeScript to JavaScript
- Use `--watch` for development
- `tsc` command uses tsconfig.json

---

## Basic Types

### Overview

TypeScript provides a rich set of basic types including primitives, arrays, tuples, enums, and special types. Understanding these types is fundamental to TypeScript programming.

### Key Concepts

- **Primitives**: boolean, number, string
- **Arrays**: `type[]` or `Array<type>`
- **Tuples**: Fixed-length arrays with specific types
- **Enums**: Named constants
- **Any**: Opt-out of type checking
- **Unknown**: Type-safe alternative to any
- **Void**: No return value
- **Never**: Function never returns

### Primitive Types

**What this demonstrates:** Basic primitive types.

**Code:**
```typescript
// Boolean
let isDone: boolean = false;
let isActive: boolean = true;

// Number (all numbers are floats)
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let float: number = 3.14;

// String
let color: string = "blue";
let fullName: string = `Bob Bobbington`;
let sentence: string = `Hello, my name is ${fullName}`;
```

**Explanation:**
- `boolean`: true/false
- `number`: All numbers (no separate int/float)
- `string`: Text data (single quotes, double quotes, template literals)
- Literal types: Can use specific values as types

**Key Takeaways:**
- `boolean`, `number`, `string` are basic types
- All numbers are floats (no separate integer type)
- Template literals supported

### Arrays and Tuples

**What this demonstrates:** Arrays and tuples.

**Code:**
```typescript
// Array (two syntaxes)
let list: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob", "Charlie"];

// Union type array
let mixed: (string | number)[] = [1, "two", 3];

// Tuple (fixed-length array with specific types)
let tuple: [string, number];
tuple = ["hello", 10];  // OK
// tuple = [10, "hello"];  // Error: wrong order

// Accessing tuple elements
console.log(tuple[0]);  // "hello" (string)
console.log(tuple[1]);  // 10 (number)

// Optional tuple elements
let optionalTuple: [string, number?];
optionalTuple = ["hello"];           // OK
optionalTuple = ["hello", 10];       // OK

// Rest in tuples
let restTuple: [string, ...number[]];
restTuple = ["hello", 1, 2, 3, 4];
```

**Explanation:**
- Arrays: `type[]` or `Array<type>` syntax
- Tuples: Fixed-length arrays with specific element types
- Optional elements: `?` makes tuple element optional
- Rest elements: `...type[]` allows variable length
- Type order matters in tuples

**Key Takeaways:**
- Two array syntaxes: `type[]` and `Array<type>`
- Tuples: Fixed-length with specific types
- Optional and rest elements supported in tuples

### Enums

**What this demonstrates:** Enumerations.

**Code:**
```typescript
// Numeric enum (default)
enum Color {
    Red,      // 0
    Green,    // 1
    Blue      // 2
}
let c: Color = Color.Green;  // 1

// Enum with custom values
enum Status {
    Active = 1,
    Inactive = 0,
    Pending = 2
}

// String enum
enum Direction {
    Up = "UP",
    Down = "DOWN",
    Left = "LEFT",
    Right = "RIGHT"
}
let dir: Direction = Direction.Up;  // "UP"
```

**Explanation:**
- Enum: Named constants
- Numeric enum: Auto-increments (starts at 0)
- Custom values: Can set specific values
- String enum: All values must be strings
- Reverse mapping: Numeric enums have reverse mapping

**Key Takeaways:**
- Enums provide named constants
- Numeric enums auto-increment
- String enums require explicit values

### Special Types

**What this demonstrates:** Any, unknown, void, never.

**Code:**
```typescript
// Any (opt-out of type checking)
let notSure: any = 4;
notSure = "maybe a string";  // OK
notSure = false;             // OK
notSure.toFixed();           // OK (no type checking)

// Unknown (type-safe any)
let uncertain: unknown = 4;
// uncertain.toFixed();  // Error: need type narrowing
if (typeof uncertain === "number") {
    uncertain.toFixed();  // OK
}

// Void (no return value)
function warnUser(): void {
    console.log("This is a warning message");
}

// Never (function never returns)
function error(message: string): never {
    throw new Error(message);
}

function infiniteLoop(): never {
    while (true) {}
}

// Null and Undefined
let u: undefined = undefined;
let n: null = null;
```

**Explanation:**
- `any`: Disables type checking (avoid when possible)
- `unknown`: Type-safe any (requires type narrowing)
- `void`: No return value (functions)
- `never`: Function never returns (throws or infinite loop)
- `null`/`undefined`: Can be types or values

**Key Takeaways:**
- Avoid `any`, use `unknown` instead
- `void` for functions with no return
- `never` for functions that never return

---

## Type Annotations & Inference

### Overview

TypeScript supports both explicit type annotations and automatic type inference. Understanding when to use each is important for writing clean TypeScript code.

### Key Concepts

- **Type Inference**: TypeScript automatically infers types
- **Type Annotations**: Explicit type declarations
- **Optional Parameters**: `param?: type`
- **Default Parameters**: `param = value`
- **Rest Parameters**: `...params: type[]`
- **Return Types**: Explicit or inferred

### Type Inference

**What this demonstrates:** Automatic type inference.

**Code:**
```typescript
// Type inference (TypeScript infers type)
let inferredNumber = 42;              // number
let inferredString = "hello";         // string
let inferredBoolean = true;           // boolean
let inferredArray = [1, 2, 3];        // number[]

// Explicit type annotation
let explicitNumber: number = 42;
let explicitString: string = "hello";

// When inference doesn't work
let arr = [];                         // any[] (bad)
let arr2: number[] = [];              // number[] (good)
```

**Explanation:**
- Inference: TypeScript infers types from values
- Explicit: Type annotations when needed
- Empty arrays: Need explicit type (infers `any[]`)
- Best practice: Let TypeScript infer when possible, annotate when needed

**Key Takeaways:**
- TypeScript infers types automatically
- Use explicit types when inference fails
- Empty arrays need explicit types

### Function Types

**What this demonstrates:** Function type annotations.

**Code:**
```typescript
// Function parameter and return types
function add(a: number, b: number): number {
    return a + b;
}

// Optional parameters
function buildName(firstName: string, lastName?: string): string {
    return lastName ? `${firstName} ${lastName}` : firstName;
}

// Default parameters
function greetUser(name: string = "Guest"): string {
    return `Hello, ${name}!`;
}

// Rest parameters
function sum(...numbers: number[]): number {
    return numbers.reduce((acc, n) => acc + n, 0);
}

// Function type
let myAdd: (a: number, b: number) => number;
myAdd = function(x, y) {
    return x + y;
};
```

**Explanation:**
- Parameter types: `param: type`
- Return type: `: returnType`
- Optional: `param?: type`
- Default: `param = defaultValue`
- Rest: `...params: type[]`
- Function type: `(params) => returnType`

**Key Takeaways:**
- Annotate function parameters and return types
- Use `?` for optional parameters
- Function types for variables

---

## Interfaces

### Overview

Interfaces define contracts for objects. They're a powerful way to describe the shape of objects and provide type safety.

### Key Concepts

- **Interface Declaration**: `interface Name { }`
- **Optional Properties**: `property?: type`
- **Readonly Properties**: `readonly property: type`
- **Index Signatures**: `[key: type]: valueType`
- **Extending Interfaces**: `interface extends Interface`
- **Function Types**: Interfaces for functions

### Basic Interfaces

**What this demonstrates:** Creating and using interfaces.

**Code:**
```typescript
// Basic interface
interface Person {
    name: string;
    age: number;
}

let person: Person = {
    name: "Alice",
    age: 25
};

// Optional properties
interface User {
    name: string;
    email: string;
    age?: number;        // Optional
}

let user: User = {
    name: "Bob",
    email: "bob@example.com"
    // age is optional
};

// Readonly properties
interface Point {
    readonly x: number;
    readonly y: number;
}

let point: Point = { x: 10, y: 20 };
// point.x = 30;  // Error: readonly
```

**Explanation:**
- Interface: Defines object shape
- Properties: Required by default
- Optional: `property?: type`
- Readonly: `readonly property: type` (cannot be modified)
- Object must match interface shape

**Key Takeaways:**
- Interfaces define object contracts
- `?` for optional properties
- `readonly` for immutable properties

### Advanced Interfaces

**What this demonstrates:** Advanced interface features.

**Code:**
```typescript
// Index signatures
interface Dictionary {
    [key: string]: number;
}

let dict: Dictionary = {
    "one": 1,
    "two": 2,
    "three": 3
};

// Extending interfaces
interface Animal {
    name: string;
}

interface Dog extends Animal {
    breed: string;
}

let dog: Dog = {
    name: "Buddy",
    breed: "Golden Retriever"
};

// Function interface
interface SearchFunc {
    (source: string, subString: string): boolean;
}

let mySearch: SearchFunc = function(src, sub) {
    return src.search(sub) > -1;
};
```

**Explanation:**
- Index signatures: `[key: type]: valueType`
- Extending: `interface extends Interface`
- Function interfaces: Interfaces for functions
- Multiple inheritance: Interfaces can extend multiple interfaces

**Key Takeaways:**
- Index signatures for dynamic properties
- Interfaces can extend other interfaces
- Function interfaces for function types

---

## Classes

### Overview

TypeScript classes support access modifiers (public, private, protected), inheritance, static members, abstract classes, and more. Classes provide object-oriented programming capabilities.

### Key Concepts

- **Access Modifiers**: public, private, protected
- **Inheritance**: extends keyword
- **Static Members**: Class-level properties and methods
- **Abstract Classes**: Base classes that cannot be instantiated
- **Getters/Setters**: Computed properties
- **Readonly**: Immutable properties
- **Parameter Properties**: Shorthand constructor syntax

### Classes

**What this demonstrates:** Creating and using classes.

**Code:**
```typescript
// Basic class
class Greeter {
    greeting: string;
    
    constructor(message: string) {
        this.greeting = message;
    }
    
    greet(): string {
        return `Hello, ${this.greeting}`;
    }
}

// Access modifiers
class Person {
    public name: string;          // Public (default)
    private age: number;          // Only accessible within class
    protected email: string;      // Accessible in subclasses
    
    constructor(name: string, age: number, email: string) {
        this.name = name;
        this.age = age;
        this.email = email;
    }
    
    getAge(): number {
        return this.age;          // OK: within class
    }
}

// Inheritance
class Employee extends Person {
    private department: string;
    
    constructor(name: string, age: number, email: string, department: string) {
        super(name, age, email);
        this.department = department;
    }
    
    getEmail(): string {
        return this.email;        // OK: protected accessible in subclass
    }
}

// Parameter properties (shorthand)
class PersonShort {
    constructor(
        public name: string,
        private age: number,
        protected email: string
    ) {}
}

// Readonly
class Octopus {
    readonly name: string;
    readonly numberOfLegs: number = 8;
    
    constructor(name: string) {
        this.name = name;
    }
}

// Static members
class Grid {
    static origin = { x: 0, y: 0 };
    
    static calculateDistance(point: { x: number; y: number }): number {
        let xDist = point.x - Grid.origin.x;
        let yDist = point.y - Grid.origin.y;
        return Math.sqrt(xDist * xDist + yDist * yDist);
    }
}

// Abstract classes
abstract class Animal {
    abstract makeSound(): void;
    
    move(): void {
        console.log("Moving...");
    }
}

class Dog extends Animal {
    makeSound(): void {
        console.log("Woof!");
    }
}
```

**Explanation:**
- `public`: Accessible everywhere (default)
- `private`: Only accessible within class
- `protected`: Accessible in class and subclasses
- `extends`: Inheritance
- `super`: Call parent constructor/methods
- `static`: Class-level members
- `abstract`: Base class that cannot be instantiated
- `readonly`: Immutable property

**Key Takeaways:**
- Use access modifiers for encapsulation
- `extends` for inheritance
- `abstract` classes for base classes
- `static` for class-level members

---

## Functions

### Overview

TypeScript functions support type annotations, optional parameters, default parameters, rest parameters, and function overloads. Functions can be declared, expressed, or arrow functions.

### Key Concepts

- **Type Annotations**: Parameter and return types
- **Optional Parameters**: `param?: type`
- **Default Parameters**: `param = value`
- **Rest Parameters**: `...params: type[]`
- **Function Overloads**: Multiple function signatures
- **Function Types**: Type annotations for function variables

### Functions

**What this demonstrates:** Function types and parameters.

**Code:**
```typescript
// Named function
function add(x: number, y: number): number {
    return x + y;
}

// Arrow function
let myAdd = (x: number, y: number): number => x + y;

// Optional parameters
function buildName(firstName: string, lastName?: string): string {
    return lastName ? `${firstName} ${lastName}` : firstName;
}

// Default parameters
function greetUser(name: string = "Guest"): string {
    return `Hello, ${name}!`;
}

// Rest parameters
function sum(...numbers: number[]): number {
    return numbers.reduce((acc, n) => acc + n, 0);
}

// Function overloads
function makeDate(timestamp: number): Date;
function makeDate(year: number, month: number, day: number): Date;
function makeDate(timestampOrYear: number, month?: number, day?: number): Date {
    if (month !== undefined && day !== undefined) {
        return new Date(timestampOrYear, month, day);
    } else {
        return new Date(timestampOrYear);
    }
}
```

**Explanation:**
- Type annotations: Parameters and return types
- Optional: `?` makes parameter optional
- Default: `= value` sets default
- Rest: `...params` collects remaining arguments
- Overloads: Multiple signatures, one implementation

**Key Takeaways:**
- Annotate function parameters and return types
- Use overloads for multiple signatures
- Optional and default parameters for flexibility

---

## Generics

### Overview

Generics enable writing reusable, type-safe code. They allow functions, classes, and interfaces to work with multiple types while maintaining type safety.

### Key Concepts

- **Generic Functions**: `function name<T>(param: T): T`
- **Generic Classes**: `class Name<T> { }`
- **Generic Interfaces**: `interface Name<T> { }`
- **Generic Constraints**: `T extends Constraint`
- **Multiple Type Parameters**: `<T, U>`

### Generics

**What this demonstrates:** Using generics.

**Code:**
```typescript
// Generic function
function identity<T>(arg: T): T {
    return arg;
}

let output1 = identity<string>("myString");
let output2 = identity(42);              // Type inference

// Generic constraints
interface Lengthwise {
    length: number;
}

function loggingIdentity<T extends Lengthwise>(arg: T): T {
    console.log(arg.length);
    return arg;
}

// Generic class
class GenericNumber<T> {
    zeroValue: T;
    add: (x: T, y: T) => T;
}

let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function(x, y) { return x + y; };

// Multiple type parameters
function merge<T, U>(obj1: T, obj2: U): T & U {
    return { ...obj1, ...obj2 };
}
```

**Explanation:**
- Generic syntax: `<T>` for type parameter
- Type inference: TypeScript infers generic type when possible
- Constraints: `T extends Constraint` limits type
- Multiple parameters: `<T, U>` for multiple types
- Reusable: Same code works with multiple types

**Key Takeaways:**
- Generics enable reusable, type-safe code
- Use constraints to limit types
- Type inference works with generics

---

## Advanced Types

### Overview

Advanced TypeScript types include union types, intersection types, type aliases, literal types, conditional types, and mapped types. These enable powerful type manipulations.

### Key Concepts

- **Union Types**: `type1 | type2`
- **Intersection Types**: `type1 & type2`
- **Type Aliases**: `type Name = Type`
- **Literal Types**: Specific values as types
- **Conditional Types**: `T extends U ? X : Y`
- **Mapped Types**: Transform existing types

### Advanced Types

**What this demonstrates:** Advanced type features.

**Code:**
```typescript
// Union types
function printId(id: number | string): void {
    console.log(`ID: ${id}`);
}

// Type guards
function processValue(value: string | number): void {
    if (typeof value === "string") {
        console.log(value.toUpperCase());
    } else {
        console.log(value.toFixed(2));
    }
}

// Intersection types
interface Person {
    name: string;
    age: number;
}

interface Employee {
    employeeId: number;
    department: string;
}

type Staff = Person & Employee;

// Type aliases
type Point = {
    x: number;
    y: number;
};

type ID = number | string;

// Literal types
type Direction = "north" | "south" | "east" | "west";

function move(direction: Direction): void {
    console.log(`Moving ${direction}`);
}
```

**Explanation:**
- Union: `A | B` (A or B)
- Intersection: `A & B` (A and B)
- Type alias: `type Name = Type`
- Literal: Specific value as type
- Type guards: Narrow union types
- Useful for: Complex type scenarios

**Key Takeaways:**
- Union types for multiple possibilities
- Intersection types for combining types
- Literal types for specific values

---

## Decorators

### Overview

Decorators are an experimental feature that allows adding metadata and modifying classes, methods, properties, and parameters. They require enabling `experimentalDecorators` in tsconfig.json.

### Key Concepts

- **Class Decorators**: Applied to classes
- **Method Decorators**: Applied to methods
- **Property Decorators**: Applied to properties
- **Parameter Decorators**: Applied to parameters
- **Experimental**: Requires flag in tsconfig.json

### Decorators

**What this demonstrates:** Using decorators (experimental).

**Code:**
```typescript
// Enable in tsconfig.json: "experimentalDecorators": true

// Class decorator
function sealed(constructor: Function) {
    Object.seal(constructor);
    Object.seal(constructor.prototype);
}

@sealed
class BugReport {
    type = "report";
    title: string;
    
    constructor(t: string) {
        this.title = t;
    }
}

// Method decorator
function enumerable(value: boolean) {
    return function(
        target: any,
        propertyKey: string,
        descriptor: PropertyDescriptor
    ) {
        descriptor.enumerable = value;
    };
}

class Greeter {
    @enumerable(false)
    greet() {
        return "Hello";
    }
}
```

**Explanation:**
- Decorators: Functions that modify classes/members
- Experimental: Requires flag in tsconfig.json
- Class decorators: Modify class constructor
- Method decorators: Modify method descriptor
- Useful for: Frameworks like Angular

**Key Takeaways:**
- Decorators are experimental
- Enable in tsconfig.json
- Used in frameworks like Angular

---

## Modules

### Overview

TypeScript supports ES6 modules for organizing and sharing code. Modules allow exporting and importing types, functions, classes, and values.

### Key Concepts

- **Export**: Export from module
- **Import**: Import from module
- **Default Export**: Single default export
- **Named Export**: Multiple named exports
- **Re-export**: Re-export from other modules

### Modules

**What this demonstrates:** ES6 modules in TypeScript.

**Code:**
```typescript
// Exporting (module.ts)
export interface StringValidator {
    isAcceptable(s: string): boolean;
}

export const numberRegexp = /^[0-9]+$/;

export class ZipCodeValidator implements StringValidator {
    isAcceptable(s: string) {
        return s.length === 5 && numberRegexp.test(s);
    }
}

// Default export
export default class ZipCodeValidator {
    isAcceptable(s: string) {
        return s.length === 5 && numberRegexp.test(s);
    }
}

// Importing
import { ZipCodeValidator } from "./ZipCodeValidator";
import ZipCodeValidator from "./ZipCodeValidator";  // Default import
import * as validator from "./ZipCodeValidator";
```

**Explanation:**
- `export`: Export from module
- `export default`: Default export
- `import`: Import from module
- Named imports: `{ name }` syntax
- Default import: No braces
- Same as JavaScript: TypeScript uses ES6 modules

**Key Takeaways:**
- Use ES6 modules for code organization
- `export` and `import` syntax
- Default exports for single exports

---

## Namespaces

### Overview

Namespaces (also called internal modules) organize code into logical groups. They're an older way to organize code, with ES6 modules being preferred in modern TypeScript.

### Key Concepts

- **Namespace Declaration**: `namespace Name { }`
- **Export**: Export from namespace
- **Nested Namespaces**: Namespaces within namespaces
- **Triple-Slash Directives**: Reference namespaces

### Namespaces

**What this demonstrates:** Using namespaces (legacy).

**Code:**
```typescript
namespace Validation {
    export interface StringValidator {
        isAcceptable(s: string): boolean;
    }
    
    export class ZipCodeValidator implements StringValidator {
        isAcceptable(s: string) {
            return s.length === 5;
        }
    }
}

// Using namespace
let validator = new Validation.ZipCodeValidator();
```

**Explanation:**
- Namespaces: Organize code into groups
- Legacy: Older approach, ES6 modules preferred
- Export: Make namespace members accessible
- Useful for: Legacy code, organizing related code

**Key Takeaways:**
- Namespaces are legacy (use ES6 modules instead)
- `namespace` keyword
- Export for accessibility

---

## Type Manipulation & Inference

### Overview

TypeScript provides powerful type manipulation tools including `typeof`, `keyof`, indexed access types, conditional types, and mapped types. These enable advanced type transformations.

### Key Concepts

- **typeof**: Get type from value
- **keyof**: Get keys of type
- **Indexed Access**: Access property types
- **Conditional Types**: Type-level conditionals
- **Mapped Types**: Transform types
- **Template Literal Types**: String literal types

### Type Manipulation

**What this demonstrates:** Advanced type manipulation.

**Code:**
```typescript
// typeof type operator
let s = "hello";
let n: typeof s;  // string

// keyof type operator
type Point = { x: number; y: number };
type P = keyof Point;  // "x" | "y"

// Indexed access types
type Person = { name: string; age: number; alive: boolean };
type Age = Person["age"];  // number

// Conditional types
type Flatten<T> = T extends Array<infer Item> ? Item : T;
type Str = Flatten<string[]>;  // string
type Num = Flatten<number>;    // number

// Template literal types
type World = "world";
type Greeting = `hello ${World}`;  // "hello world"
```

**Explanation:**
- `typeof`: Get type from value
- `keyof`: Union of property keys
- Indexed access: `Type["key"]` gets property type
- Conditional: `T extends U ? X : Y`
- Template literal: String interpolation in types
- Advanced: Enables complex type transformations

**Key Takeaways:**
- `typeof` and `keyof` for type operations
- Indexed access for property types
- Conditional types for type-level logic

---

## Async/Await

### Overview

TypeScript supports async/await for asynchronous programming. Async functions return Promises and can use await to wait for Promise resolution.

### Key Concepts

- **Async Functions**: `async function name() { }`
- **Await**: `await promise`
- **Promise Types**: `Promise<T>`
- **Error Handling**: try/catch with async/await

### Async/Await

**What this demonstrates:** Async programming in TypeScript.

**Code:**
```typescript
// Async function
async function fetchUserData(): Promise<User> {
    let response = await fetch('https://api.example.com/user');
    let data = await response.json();
    return data;
}

// Error handling
async function processData() {
    try {
        let user = await fetchUserData();
        return user;
    } catch (error) {
        console.error(error);
        throw error;
    }
}

// Promise type
function fetchData(): Promise<string> {
    return fetch('https://api.example.com/data')
        .then(response => response.text());
}
```

**Explanation:**
- `async`: Function returns Promise
- `await`: Wait for Promise resolution
- `Promise<T>`: Type for Promises
- Error handling: try/catch with async
- Type safety: TypeScript ensures Promise types

**Key Takeaways:**
- `async/await` for async programming
- `Promise<T>` for Promise types
- Use try/catch for error handling

---

## Best Practices

### Type Safety

- **Use strict mode**: Enable `strict: true` in tsconfig.json
- **Avoid any**: Use `unknown` instead when type is truly unknown
- **Use type annotations**: When inference fails or improves clarity
- **Prefer interfaces**: For object shapes
- **Use type aliases**: For complex types

### Code Organization

- **Use ES6 modules**: Prefer modules over namespaces
- **Organize imports**: Group and order imports
- **Type definitions**: Use `.d.ts` files for type-only declarations
- **Barrel exports**: Re-export from index files

### Performance

- **Type-only imports**: `import type { Type }` for types
- **Avoid excessive types**: Don't over-engineer types
- **Use const assertions**: `as const` for literal types

---

## Common Patterns

### Type Guards

```typescript
function isString(value: unknown): value is string {
    return typeof value === "string";
}
```

### Utility Types

```typescript
// Partial: Make all properties optional
type Partial<T> = {
    [P in keyof T]?: T[P];
};

// Pick: Select properties
type Pick<T, K extends keyof T> = {
    [P in K]: T[P];
};

// Omit: Exclude properties
type Omit<T, K extends keyof T> = Pick<T, Exclude<keyof T, K>>;
```

### Generic Constraints

```typescript
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}
```

---

## Resources

### Official Documentation

- **TypeScript Handbook**: https://www.typescriptlang.org/docs/handbook/intro.html
- **TypeScript Website**: https://www.typescriptlang.org/
- **TypeScript Compiler API**: https://github.com/Microsoft/TypeScript/wiki/Using-the-Compiler-API

### Learning Resources

- **TypeScript Deep Dive**: https://basarat.gitbook.io/typescript/
- **TypeScript Handbook**: https://www.typescriptlang.org/docs/handbook/
- **Type Challenges**: https://github.com/type-challenges/type-challenges

### Community

- **Stack Overflow**: Tag: typescript
- **r/typescript**: Reddit community
- **TypeScript Discord**: Community server

### Tools

- **TypeScript Compiler (tsc)**: Official compiler
- **ts-node**: Run TypeScript directly
- **tsconfig.json**: Configuration file
- **TypeScript ESLint**: Linting
- **tsx**: TypeScript execution engine

---

