# PHP - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Fundamentals & Setup](#fundamentals--setup)
4. [Variables & Data Types](#variables--data-types)
5. [Operators](#operators)
6. [Strings](#strings)
7. [Arrays](#arrays)
8. [Control Flow](#control-flow)
9. [Functions](#functions)
10. [Classes & Objects (OOP)](#classes--objects-oop)
11. [Error Handling](#error-handling)
12. [File I/O](#file-io)
13. [Database (PDO)](#database-pdo)
14. [Sessions & Cookies](#sessions--cookies)
15. [Modern PHP Features](#modern-php-features)
16. [Best Practices](#best-practices)
17. [Common Patterns](#common-patterns)
18. [Resources](#resources)

---

## Introduction

### What is PHP?

PHP (PHP: Hypertext Preprocessor) is a server-side scripting language designed for web development. Originally created by Rasmus Lerdorf in 1994, PHP has evolved into a powerful, general-purpose language that's especially well-suited for server-side web development. PHP code is executed on the server, generating HTML that is sent to the client browser.

### Why Learn PHP?

PHP is valuable for:

1. **Web Development**: Powers millions of websites including WordPress, Facebook, Wikipedia
2. **Server-Side Scripting**: Ideal for dynamic web pages and web applications
3. **Ease of Learning**: Simple syntax, great for beginners
4. **Large Ecosystem**: Extensive frameworks (Laravel, Symfony, CodeIgniter)
5. **Database Integration**: Excellent database support (MySQL, PostgreSQL, etc.)
6. **Content Management**: Powers WordPress, Drupal, Joomla
7. **Career Opportunities**: High demand in web development
8. **Modern Features**: PHP 8+ brings performance improvements and modern language features

### Key Features

- **Server-Side Execution**: Runs on server, generates HTML
- **Dynamic Typing**: Flexible variable types
- **Embedded in HTML**: PHP code can be embedded directly in HTML
- **Database Support**: Native support for many databases
- **Session Management**: Built-in session and cookie handling
- **Large Standard Library**: Extensive built-in functions
- **Cross-Platform**: Runs on Windows, Linux, macOS

---

## Getting Started

### Installation

**Install PHP:**
- Windows: Download from php.net or use XAMPP/WAMP
- macOS: `brew install php`
- Linux: `sudo apt install php` (Ubuntu/Debian)

**Verify Installation:**
```bash
php -v
```

**Run PHP:**
```bash
php script.php          # Run PHP script
php -S localhost:8000   # Built-in development server
```

### Your First PHP Program

**Code:**
```php
<?php
echo "Hello, World!";
?>
```

**PHP in HTML:**
```php
<!DOCTYPE html>
<html>
<body>
    <h1><?php echo "Hello from PHP!"; ?></h1>
</body>
</html>
```

---

## Fundamentals & Setup

### Overview

PHP fundamentals include syntax, output statements, comments, and embedding PHP in HTML. Understanding these basics is essential for PHP development.

### Key Concepts

- **PHP Tags**: `<?php ... ?>`
- **Output**: `echo`, `print`, `print_r`, `var_dump`
- **Comments**: `//`, `/* */`, `#`
- **Semicolons**: Statements end with `;`
- **Embedded in HTML**: PHP can be mixed with HTML

### PHP Syntax

**What this demonstrates:** Basic PHP syntax and output.

**Code:**
```php
<?php
// PHP files start with <?php tag
// Statements end with semicolon ;

// Output statements
echo "Hello";           // Output text
print "World";          // Output text (returns 1)
print_r($array);        // Print human-readable array
var_dump($variable);    // Print type and value
var_export($variable);  // Export valid PHP code

// Comments
// Single-line comment
# Also single-line comment

/* 
   Multi-line comment
   Spans multiple lines
*/

/**
 * Documentation comment (PHPDoc)
 * @param string $name
 * @return string
 */
?>
```

**Explanation:**
- PHP tags: `<?php ... ?>` delimit PHP code
- Semicolons: Required to end statements
- `echo`: Most common output statement
- `print`: Alternative to echo (returns 1)
- `print_r`: Human-readable array/object output
- `var_dump`: Type and value information
- Comments: Single-line (`//`, `#`) and multi-line (`/* */`)

**Key Takeaways:**
- PHP code in `<?php ... ?>` tags
- Statements end with semicolons
- Use `echo` for output
- Comments for documentation

---

## Variables & Data Types

### Overview

PHP variables start with `$` and are dynamically typed. PHP supports various data types including scalars, arrays, objects, and resources.

### Key Concepts

- **Variables**: Start with `$`, case-sensitive
- **Data Types**: String, integer, float, boolean, array, object, NULL, resource
- **Type Checking**: `gettype()`, `is_*()` functions
- **Type Casting**: Explicit type conversion
- **Type Juggling**: Automatic type conversion
- **Constants**: `define()` or `const`

### Variables

**What this demonstrates:** Working with variables.

**Code:**
```php
<?php
// Variables (case-sensitive, start with $)
$name = "Alice";
$age = 25;
$salary = 75000.50;
$isActive = true;

// Variable variables
$var = "name";
$$var = "Bob";  // Same as $name = "Bob"

// Variable scope
function test() {
    global $name;  // Access global variable
    $local = "local";  // Local variable
}
?>
```

**Explanation:**
- Variable syntax: `$variableName`
- Case-sensitive: `$name` and `$Name` are different
- Dynamic typing: Type determined by value
- Variable variables: `$$var` uses value of `$var` as variable name
- Scope: Global vs local (inside functions)

**Key Takeaways:**
- Variables start with `$`
- Case-sensitive names
- Dynamically typed

### Data Types

**What this demonstrates:** PHP data types.

**Code:**
```php
<?php
// String
$str1 = "Hello";
$str2 = 'World';
$str3 = "Hello, $name!";  // Double quotes interpolate
$str4 = 'Hello, $name!';  // Single quotes don't: "Hello, $name!"

// Integer
$int = 42;
$hex = 0x1A;
$octal = 0123;
$binary = 0b1010;

// Float (double)
$float = 3.14;
$scientific = 1.5e3;  // 1500

// Boolean
$true = true;
$false = false;

// Array
$colors = array("Red", "Green", "Blue");
$fruits = ["Apple", "Banana", "Cherry"];  // PHP 5.4+

// Associative array
$person = [
    "name" => "Alice",
    "age" => 25,
    "email" => "alice@example.com"
];

// NULL
$var = null;

// Type checking
var_dump($name);         // string(5) "Alice"
echo gettype($age);      // integer
is_int($age);           // true
is_string($name);       // true
is_array($colors);      // true
?>
```

**Explanation:**
- String: Text data (single or double quotes)
- Integer: Whole numbers (decimal, hex, octal, binary)
- Float: Floating-point numbers
- Boolean: `true` or `false`
- Array: Ordered map (indexed or associative)
- NULL: Represents no value
- Type checking: `gettype()`, `is_*()` functions

**Key Takeaways:**
- PHP has dynamic types
- Strings: Single quotes (literal) vs double quotes (interpolation)
- Arrays: Indexed or associative
- Use `gettype()` and `is_*()` for type checking

### Type Casting

**What this demonstrates:** Converting between types.

**Code:**
```php
<?php
// Type casting
$str = "123";
$int = (int)$str;       // 123
$float = (float)$str;   // 123.0
$bool = (bool)$str;     // true
$array = (array)$str;   // ["123"]

// Type juggling (automatic conversion)
$result = "10" + 5;     // 15 (string converted to int)
$result = "10" . 5;     // "105" (concatenation with .)

// Constants
define("PI", 3.14159);
echo PI;

const MAX_SIZE = 100;  // PHP 5.3+
?>
```

**Explanation:**
- Type casting: `(type)$variable`
- Type juggling: Automatic conversion in expressions
- Concatenation: `.` operator (not `+`)
- Constants: `define()` or `const` keyword
- Constants: Case-sensitive, can't be redefined

**Key Takeaways:**
- Use `(type)` for explicit casting
- `.` for string concatenation
- `define()` or `const` for constants

---

## Operators

### Overview

PHP provides arithmetic, comparison, logical, string, and other operators. Understanding operators is essential for writing expressions.

### Key Concepts

- **Arithmetic**: `+`, `-`, `*`, `/`, `%`, `**`
- **Comparison**: `==`, `===`, `!=`, `<>`, `!==`, `>`, `<`, `>=`, `<=`
- **Logical**: `&&`, `||`, `!`, `and`, `or`, `xor`
- **Spaceship**: `<=>` (PHP 7+)
- **Null Coalescing**: `??` (PHP 7+)
- **Null Safe**: `?->` (PHP 8+)

### Arithmetic Operators

**What this demonstrates:** Arithmetic operations.

**Code:**
```php
<?php
$a = 10;
$b = 3;

$sum = $a + $b;         // 13
$diff = $a - $b;        // 7
$prod = $a * $b;        // 30
$quot = $a / $b;        // 3.333...
$mod = $a % $b;         // 1
$power = $a ** $b;      // 1000 (PHP 5.6+)

// Increment/Decrement
$x = 5;
$x++;   // Post-increment (6)
++$x;   // Pre-increment (7)
?>
```

**Explanation:**
- Standard arithmetic: `+`, `-`, `*`, `/`, `%`
- Exponentiation: `**` (PHP 5.6+)
- Increment/decrement: `++`, `--` (pre and post)
- Division: Always returns float (even if result is integer)

**Key Takeaways:**
- Standard arithmetic operators
- `**` for exponentiation
- `++`/`--` pre vs post matters

### Comparison Operators

**What this demonstrates:** Comparing values.

**Code:**
```php
<?php
$a = 10;
$b = "10";

$equal = ($a == $b);        // true (value equality, type coercion)
$identical = ($a === $b);   // false (type and value)
$notEqual = ($a != $b);     // false
$notIdentical = ($a !== $b); // true

// Spaceship operator (PHP 7+)
echo 1 <=> 1;  // 0 (equal)
echo 1 <=> 2;  // -1 (less than)
echo 2 <=> 1;  // 1 (greater than)
?>
```

**Explanation:**
- `==`: Loose equality (type coercion)
- `===`: Strict equality (type and value)
- `!=`/`<>`: Not equal
- `!==`: Not identical
- `<=>`: Spaceship operator (PHP 7+)
- Always use `===` and `!==` for strict comparison

**Key Takeaways:**
- Always use `===` and `!==` (strict)
- Avoid `==` and `!=` (loose, type coercion)
- Spaceship `<=>` for three-way comparison

### Logical and Other Operators

**What this demonstrates:** Logical and special operators.

**Code:**
```php
<?php
$t = true;
$f = false;

$and = $t && $f;    // false (short-circuit)
$or = $t || $f;     // true (short-circuit)
$not = !$t;         // false

// NULL coalescing (PHP 7+)
$username = $_GET['user'] ?? 'Guest';
$name = $firstName ?? $defaultName ?? 'Unknown';

// NULL safe operator (PHP 8+)
$country = $user?->getAddress()?->getCountry();

// Ternary
$age = 20;
$status = ($age >= 18) ? "Adult" : "Minor";

// String concatenation
$str1 = "Hello";
$str2 = "World";
$concat = $str1 . " " . $str2;  // "Hello World"
?>
```

**Explanation:**
- Logical: `&&`, `||`, `!` (short-circuit)
- `??`: Null coalescing (returns left if not null, else right)
- `?->`: Null safe operator (PHP 8+, safe method/property access)
- Ternary: `condition ? trueValue : falseValue`
- String concat: `.` operator

**Key Takeaways:**
- Use `&&` and `||` for logical operations
- `??` for default values
- `?->` for safe null access (PHP 8+)
- `.` for string concatenation

---

## Strings

### Overview

Strings are sequences of characters. PHP provides many string functions for manipulation, searching, and formatting.

### Key Concepts

- **String Creation**: Single quotes, double quotes, heredoc, nowdoc
- **String Interpolation**: Variable interpolation in double quotes
- **String Functions**: Many built-in functions
- **String Concatenation**: `.` operator
- **Escape Sequences**: Special characters

### String Operations

**What this demonstrates:** Working with strings.

**Code:**
```php
<?php
// String creation
$str1 = 'Single quotes';
$str2 = "Double quotes";
$name = "Alice";

// String interpolation (double quotes)
$greeting = "Hello, $name!";  // "Hello, Alice!"
$greeting2 = "Hello, {$name}!";  // Same, explicit variable

// Heredoc
$text = <<<EOT
This is a heredoc string
It can span multiple lines
Variable $name is interpolated
EOT;

// Nowdoc (no interpolation)
$text2 = <<<'EOT'
This is a nowdoc string
$name is not interpolated
EOT;

// String functions
$str = "Hello World";
strlen($str);                    // 11 (length)
strtoupper($str);                // "HELLO WORLD"
strtolower($str);                // "hello world"
substr($str, 0, 5);              // "Hello"
str_replace("World", "PHP", $str); // "Hello PHP"
strpos($str, "World");           // 6 (position)
?>
```

**Explanation:**
- Single quotes: Literal (no interpolation)
- Double quotes: Interpolate variables
- Heredoc: Multi-line with interpolation
- Nowdoc: Multi-line without interpolation
- String functions: Many built-in functions
- Concatenation: `.` operator

**Key Takeaways:**
- Single quotes for literals
- Double quotes for interpolation
- Use string functions for manipulation

---

## Arrays

### Overview

Arrays in PHP are ordered maps that can hold multiple values. PHP arrays can be indexed, associative, or multidimensional.

### Key Concepts

- **Indexed Arrays**: Numeric keys
- **Associative Arrays**: String keys
- **Multidimensional**: Arrays within arrays
- **Array Functions**: Many built-in functions
- **Array Syntax**: `array()` or `[]`

### Arrays

**What this demonstrates:** Working with arrays.

**Code:**
```php
<?php
// Indexed array
$colors = array("Red", "Green", "Blue");
$fruits = ["Apple", "Banana", "Cherry"];  // PHP 5.4+

// Associative array
$person = [
    "name" => "Alice",
    "age" => 25,
    "email" => "alice@example.com"
];

// Accessing elements
echo $colors[0];        // "Red"
echo $person["name"];   // "Alice"

// Adding elements
$colors[] = "Yellow";   // Add to end
$person["city"] = "NYC"; // Add key-value

// Array functions
count($colors);                    // 4 (length)
in_array("Red", $colors);          // true
array_push($colors, "Purple");     // Add to end
array_pop($colors);                // Remove from end
array_merge($arr1, $arr2);         // Merge arrays
?>
```

**Explanation:**
- Array syntax: `array()` or `[]` (PHP 5.4+)
- Indexed: Numeric keys (0, 1, 2, ...)
- Associative: String keys
- Adding: `$array[] = value` or `$array["key"] = value`
- Functions: Many array manipulation functions

**Key Takeaways:**
- Arrays can be indexed or associative
- Use `[]` syntax (PHP 5.4+)
- Many array functions available

---

## Control Flow

### Overview

Control flow statements determine execution order. PHP supports if/else, switch, loops, and control statements.

### Key Concepts

- **Conditionals**: if/else, switch, match (PHP 8+)
- **Loops**: while, do-while, for, foreach
- **Control Statements**: break, continue, return, exit
- **Alternative Syntax**: Template-friendly syntax

### Conditionals

**What this demonstrates:** Conditional statements.

**Code:**
```php
<?php
// if/else
$age = 25;

if ($age < 13) {
    echo "Child";
} elseif ($age < 20) {
    echo "Teenager";
} elseif ($age < 65) {
    echo "Adult";
} else {
    echo "Senior";
}

// Switch
$day = 3;
switch ($day) {
    case 1:
        echo "Monday";
        break;
    case 2:
        echo "Tuesday";
        break;
    default:
        echo "Other";
}

// Match expression (PHP 8+)
$result = match($day) {
    1 => "Monday",
    2 => "Tuesday",
    3 => "Wednesday",
    default => "Other"
};
?>
```

**Explanation:**
- if/else: Conditional execution
- switch: Multiple cases (use `break`)
- match: PHP 8+ expression (returns value)
- Alternative syntax: Template-friendly `if(): ... endif;`

**Key Takeaways:**
- Use `if/else` for conditionals
- `match` (PHP 8+) returns value
- Use `break` in switch cases

### Loops

**What this demonstrates:** Different loop types.

**Code:**
```php
<?php
// while loop
$count = 0;
while ($count < 5) {
    echo $count;
    $count++;
}

// do-while loop
$num = 0;
do {
    echo $num;
    $num++;
} while ($num < 5);

// for loop
for ($i = 0; $i < 5; $i++) {
    echo $i;
}

// foreach loop
$colors = ["Red", "Green", "Blue"];
foreach ($colors as $color) {
    echo $color;
}

foreach ($colors as $index => $color) {
    echo "$index: $color";
}

// Break and continue
for ($i = 0; $i < 10; $i++) {
    if ($i == 3) continue;  // Skip 3
    if ($i == 7) break;     // Exit at 7
    echo $i;
}
?>
```

**Explanation:**
- while: Loop while condition true
- do-while: Execute once, then loop
- for: Traditional for loop
- foreach: Iterate over arrays
- break: Exit loop
- continue: Skip to next iteration

**Key Takeaways:**
- `foreach` for arrays
- `break` and `continue` for control
- Alternative syntax for templates

---

## Functions

### Overview

Functions are reusable blocks of code. PHP supports regular functions, type declarations, default parameters, and variadic functions.

### Key Concepts

- **Function Declaration**: `function name() { }`
- **Parameters**: Type declarations (PHP 7+)
- **Return Types**: Type declarations (PHP 7+)
- **Default Parameters**: `param = value`
- **Variadic Functions**: `...$params`
- **Anonymous Functions**: Closures

### Functions

**What this demonstrates:** Creating and using functions.

**Code:**
```php
<?php
// Basic function
function greet() {
    echo "Hello!";
}

// Parameters
function add($a, $b) {
    return $a + $b;
}

// Type declarations (PHP 7+)
function addNumbers(int $a, int $b): int {
    return $a + $b;
}

// Default parameters
function greetUser($name = "Guest") {
    return "Hello, $name!";
}

// Variadic functions (PHP 5.6+)
function sum(...$numbers) {
    return array_sum($numbers);
}

// Anonymous functions (closures)
$greet = function($name) {
    return "Hello, $name!";
};

// Arrow functions (PHP 7.4+)
$add = fn($a, $b) => $a + $b;
?>
```

**Explanation:**
- Function syntax: `function name(params) { }`
- Type declarations: Parameter and return types (PHP 7+)
- Default parameters: `param = value`
- Variadic: `...$params` collects arguments
- Closures: Anonymous functions
- Arrow functions: Short syntax (PHP 7.4+)

**Key Takeaways:**
- Use type declarations (PHP 7+)
- Default parameters for optional values
- Closures for anonymous functions

---

## Classes & Objects (OOP)

### Overview

PHP supports object-oriented programming with classes, objects, inheritance, interfaces, traits, and more. OOP enables code organization and reuse.

### Key Concepts

- **Classes**: `class Name { }`
- **Objects**: Instances of classes
- **Properties**: Class variables
- **Methods**: Class functions
- **Visibility**: public, private, protected
- **Inheritance**: extends
- **Interfaces**: Contracts
- **Traits**: Code reuse

### Classes

**What this demonstrates:** Creating and using classes.

**Code:**
```php
<?php
// Basic class
class Person {
    // Properties
    public $name;
    public $age;
    private $email;
    protected $phone;
    
    // Constructor
    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }
    
    // Methods
    public function greet() {
        return "Hello, I'm {$this->name}";
    }
    
    // Getters and Setters
    public function getEmail() {
        return $this->email;
    }
    
    public function setEmail($email) {
        $this->email = $email;
    }
    
    // Static members
    public static $species = "Homo Sapiens";
    
    public static function getSpecies() {
        return self::$species;
    }
}

// Creating objects
$person = new Person("Alice", 25);
echo $person->greet();

// Constructor Property Promotion (PHP 8+)
class User {
    public function __construct(
        public string $name,
        public int $age,
        private string $email
    ) {}
}
```

**Explanation:**
- Class: `class Name { }`
- Properties: Class variables
- Methods: Class functions
- Constructor: `__construct()`
- Visibility: public, private, protected
- Static: Class-level members
- Property promotion: PHP 8+ shorthand

**Key Takeaways:**
- Use classes for OOP
- Visibility modifiers for encapsulation
- Static members for class-level data

### Inheritance and Interfaces

**What this demonstrates:** Inheritance and interfaces.

**Code:**
```php
<?php
// Inheritance
class Employee extends Person {
    public $company;
    public $position;
    
    public function __construct($name, $age, $company, $position) {
        parent::__construct($name, $age);
        $this->company = $company;
        $this->position = $position;
    }
    
    // Override method
    public function greet() {
        return parent::greet() . " from {$this->company}";
    }
}

// Abstract classes
abstract class Shape {
    protected $color;
    
    abstract public function area();
    
    public function getColor() {
        return $this->color;
    }
}

class Circle extends Shape {
    private $radius;
    
    public function area() {
        return pi() * $this->radius * $this->radius;
    }
}

// Interfaces
interface Drawable {
    public function draw();
}

class Rectangle implements Drawable {
    public function draw() {
        echo "Drawing rectangle";
    }
}
```

**Explanation:**
- `extends`: Inheritance
- `parent::`: Call parent class
- `abstract`: Abstract classes and methods
- `interface`: Defines contracts
- `implements`: Implement interface

**Key Takeaways:**
- `extends` for inheritance
- `abstract` for base classes
- `interface` for contracts

### Traits

**What this demonstrates:** Code reuse with traits.

**Code:**
```php
<?php
// Traits (code reuse)
trait Logger {
    public function log($message) {
        echo "[LOG] $message\n";
    }
}

trait Timestampable {
    public $createdAt;
    public $updatedAt;
    
    public function updateTimestamps() {
        $this->updatedAt = time();
    }
}

class User {
    use Logger, Timestampable;
    
    public function save() {
        $this->log("Saving user");
        $this->updateTimestamps();
    }
}
```

**Explanation:**
- Traits: Code reuse without inheritance
- `trait Name { }`: Define trait
- `use TraitName;`: Use trait in class
- Multiple traits: Comma-separated
- Useful for: Horizontal code reuse

**Key Takeaways:**
- Traits for code reuse
- `use` keyword to include traits
- Multiple traits allowed

---

## Error Handling

### Overview

PHP provides error handling mechanisms including try/catch blocks, exceptions, and error reporting. Proper error handling is essential for robust applications.

### Key Concepts

- **Try/Catch**: Exception handling
- **Exceptions**: Throw and catch exceptions
- **Error Types**: Errors, warnings, notices
- **Error Reporting**: Configure error display
- **Custom Exceptions**: Create exception classes

### Error Handling

**What this demonstrates:** Handling errors and exceptions.

**Code:**
```php
<?php
// Try/catch
try {
    $result = riskyOperation();
} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
} finally {
    echo "Cleanup";
}

// Throwing exceptions
function divide($a, $b) {
    if ($b == 0) {
        throw new Exception("Division by zero");
    }
    return $a / $b;
}

// Custom exceptions
class ValidationException extends Exception {
    public function __construct($message, $code = 0, Exception $previous = null) {
        parent::__construct($message, $code, $previous);
    }
}

// Error reporting
error_reporting(E_ALL);
ini_set('display_errors', 1);
?>
```

**Explanation:**
- `try/catch`: Handle exceptions
- `throw`: Throw exception
- `finally`: Always executes
- Custom exceptions: Extend Exception class
- Error reporting: Configure error display

**Key Takeaways:**
- Use try/catch for exceptions
- Throw exceptions for errors
- Custom exceptions for specific error types

---

## File I/O

### Overview

PHP provides functions for reading and writing files. File I/O is essential for data persistence and processing.

### Key Concepts

- **File Operations**: Read, write, append
- **File Functions**: `fopen()`, `fread()`, `fwrite()`, `fclose()`
- **File Modes**: r, w, a, x, etc.
- **File Functions**: `file_get_contents()`, `file_put_contents()`
- **Directory Operations**: Directory functions

### File I/O

**What this demonstrates:** Reading and writing files.

**Code:**
```php
<?php
// Reading file
$content = file_get_contents("file.txt");

// Writing file
file_put_contents("file.txt", "Hello, World!");

// File handle operations
$file = fopen("file.txt", "r");
$content = fread($file, filesize("file.txt"));
fclose($file);

// Writing with file handle
$file = fopen("file.txt", "w");
fwrite($file, "Hello, World!");
fclose($file);

// Reading line by line
$file = fopen("file.txt", "r");
while (($line = fgets($file)) !== false) {
    echo $line;
}
fclose($file);

// File modes
// r: Read only
// w: Write only (truncates)
// a: Append
// x: Exclusive write
// r+: Read and write
?>
```

**Explanation:**
- `file_get_contents()`: Read entire file
- `file_put_contents()`: Write entire file
- `fopen()`: Open file handle
- `fread()`/`fwrite()`: Read/write operations
- `fclose()`: Close file handle
- File modes: Control file access

**Key Takeaways:**
- Use `file_get_contents`/`file_put_contents` for simple operations
- Use file handles for large files
- Always close file handles

---

## Database (PDO)

### Overview

PDO (PHP Data Objects) provides a database abstraction layer. It supports prepared statements and multiple database systems.

### Key Concepts

- **PDO**: Database abstraction layer
- **Prepared Statements**: Prevent SQL injection
- **Connections**: Connect to databases
- **Queries**: SELECT, INSERT, UPDATE, DELETE
- **Transactions**: Ensure data integrity
- **Fetch Modes**: Different data formats

### Database Operations

**What this demonstrates:** Working with databases using PDO.

**Code:**
```php
<?php
// Connect to database
try {
    $pdo = new PDO('mysql:host=localhost;dbname=mydb', 'username', 'password');
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    die("Connection failed: " . $e->getMessage());
}

// SELECT query
$stmt = $pdo->query("SELECT * FROM users");
$users = $stmt->fetchAll(PDO::FETCH_ASSOC);

// Prepared statements (prevent SQL injection)
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = ?");
$stmt->execute([$email]);
$user = $stmt->fetch();

// Named parameters
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email AND age > :age");
$stmt->execute(['email' => $email, 'age' => 18]);

// INSERT
$stmt = $pdo->prepare("INSERT INTO users (name, email, age) VALUES (?, ?, ?)");
$stmt->execute(['Alice', 'alice@example.com', 25]);
$lastId = $pdo->lastInsertId();

// UPDATE
$stmt = $pdo->prepare("UPDATE users SET age = ? WHERE id = ?");
$stmt->execute([26, 1]);
$affectedRows = $stmt->rowCount();

// Transactions
try {
    $pdo->beginTransaction();
    $pdo->exec("INSERT INTO users (name) VALUES ('Alice')");
    $pdo->exec("INSERT INTO orders (user_id) VALUES (1)");
    $pdo->commit();
} catch (Exception $e) {
    $pdo->rollBack();
    throw $e;
}
?>
```

**Explanation:**
- PDO: Database abstraction layer
- Prepared statements: Prevent SQL injection
- Placeholders: `?` (positional) or `:name` (named)
- Transactions: `beginTransaction()`, `commit()`, `rollBack()`
- Fetch modes: `FETCH_ASSOC`, `FETCH_OBJ`, etc.

**Key Takeaways:**
- Always use prepared statements
- Use transactions for related operations
- Set error mode to exception

---

## Sessions & Cookies

### Overview

Sessions and cookies enable state management in web applications. Sessions store data on the server, while cookies store data on the client.

### Key Concepts

- **Sessions**: Server-side state management
- **Cookies**: Client-side data storage
- **Session Functions**: `session_start()`, `$_SESSION`
- **Cookie Functions**: `setcookie()`, `$_COOKIE`
- **Security**: Secure session and cookie handling

### Sessions and Cookies

**What this demonstrates:** Working with sessions and cookies.

**Code:**
```php
<?php
// Sessions
session_start();

// Set session variable
$_SESSION['username'] = 'Alice';
$_SESSION['user_id'] = 123;

// Get session variable
$username = $_SESSION['username'];

// Destroy session
session_destroy();
unset($_SESSION);

// Cookies
setcookie('username', 'Alice', time() + 3600);  // 1 hour
setcookie('username', 'Alice', time() + 3600, '/', '', true, true);  // Secure, HTTP-only

// Get cookie
$username = $_COOKIE['username'] ?? 'Guest';

// Delete cookie
setcookie('username', '', time() - 3600);
?>
```

**Explanation:**
- Sessions: Server-side storage
- `session_start()`: Start session
- `$_SESSION`: Session superglobal
- Cookies: Client-side storage
- `setcookie()`: Set cookie
- `$_COOKIE`: Cookie superglobal
- Security: Use secure, HTTP-only cookies

**Key Takeaways:**
- Use sessions for server-side state
- Use cookies for client-side data
- Always use secure, HTTP-only cookies

---

## Modern PHP Features

### Overview

PHP 8+ introduced many modern features including match expressions, nullsafe operator, union types, named arguments, attributes, and more.

### Key Concepts

- **Match Expression**: PHP 8+ switch alternative
- **Nullsafe Operator**: `?->` (PHP 8+)
- **Union Types**: Multiple types (PHP 8+)
- **Named Arguments**: Specify by name (PHP 8+)
- **Attributes**: Metadata (PHP 8+)
- **Constructor Property Promotion**: PHP 8+ shorthand

### Modern PHP Features

**What this demonstrates:** PHP 8+ features.

**Code:**
```php
<?php
// Match expression (PHP 8+)
$result = match($status) {
    'active' => 'User is active',
    'inactive' => 'User is inactive',
    default => 'Unknown status'
};

// Nullsafe operator (PHP 8+)
$country = $user?->getAddress()?->getCountry();

// Union types (PHP 8+)
function processValue(string|int $value): string|int {
    return $value;
}

// Named arguments (PHP 8+)
function createUser(string $name, int $age, string $email) {
    // ...
}

createUser(name: "Alice", age: 25, email: "alice@example.com");

// Attributes (PHP 8+)
#[Route('/api/users')]
class UserController {
    #[Get('/{id}')]
    public function getUser(int $id) {
        // ...
    }
}
?>
```

**Explanation:**
- Match: Expression-based switch (PHP 8+)
- Nullsafe: `?->` safe method/property access (PHP 8+)
- Union types: `type1|type2` (PHP 8+)
- Named arguments: Specify by name (PHP 8+)
- Attributes: Metadata (PHP 8+)
- Modern: PHP 8+ brings many improvements

**Key Takeaways:**
- Use match for expressions (PHP 8+)
- Nullsafe operator for safe access (PHP 8+)
- Union types for multiple types (PHP 8+)
- Named arguments improve readability (PHP 8+)

---

## Best Practices

### Security

- **Prepared Statements**: Always use for database queries
- **Input Validation**: Validate and sanitize user input
- **Password Hashing**: Use `password_hash()` and `password_verify()`
- **XSS Prevention**: Use `htmlspecialchars()` for output
- **CSRF Protection**: Use tokens for forms
- **Secure Cookies**: Use secure, HTTP-only cookies

### Code Organization

- **PSR Standards**: Follow PSR-1, PSR-2, PSR-4
- **Autoloading**: Use Composer autoloading
- **Namespaces**: Organize code with namespaces
- **Type Declarations**: Use type hints (PHP 7+)
- **Error Handling**: Use exceptions, not errors

### Performance

- **OpCache**: Enable OpCache for production
- **Caching**: Use caching when appropriate
- **Avoid N+1**: Optimize database queries
- **Lazy Loading**: Load data only when needed

---

## Common Patterns

### Singleton Pattern

```php
class Database {
    private static $instance = null;
    
    private function __construct() {}
    
    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }
}
```

### Factory Pattern

```php
class UserFactory {
    public static function create($type) {
        switch ($type) {
            case 'admin':
                return new Admin();
            case 'user':
                return new User();
            default:
                throw new Exception("Invalid type");
        }
    }
}
```

### Dependency Injection

```php
class UserService {
    private $repository;
    
    public function __construct(UserRepository $repository) {
        $this->repository = $repository;
    }
}
```

---

## Resources

### Official Documentation

- **PHP.net**: https://www.php.net/
- **PHP Manual**: https://www.php.net/manual/en/
- **PHP RFC**: https://wiki.php.net/rfc

### Learning Resources

- **PHP The Right Way**: https://phptherightway.com/
- **PHP.net Tutorial**: https://www.php.net/manual/en/tutorial.php
- **Laravel Documentation**: https://laravel.com/docs

### Community

- **Stack Overflow**: Tag: php
- **r/PHP**: Reddit community
- **PHP User Groups**: Worldwide PHP communities

### Tools

- **Composer**: Dependency manager
- **PHPUnit**: Testing framework
- **Xdebug**: Debugger and profiler
- **PHPStan**: Static analysis
- **Laravel**: Popular framework
- **Symfony**: Enterprise framework

---

