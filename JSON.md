# JSON - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Fundamentals](#fundamentals)
4. [Data Types](#data-types)
5. [Usage in JavaScript](#usage-in-javascript)
6. [Usage in Python](#usage-in-python)
7. [Usage in Other Languages](#usage-in-other-languages)
8. [Validation](#validation)
9. [Best Practices](#best-practices)
10. [Common Patterns](#common-patterns)
11. [Advanced Topics](#advanced-topics)
12. [Alternatives](#alternatives)
13. [Resources](#resources)

---

## Introduction

### What is JSON?

JSON (JavaScript Object Notation) is a lightweight data-interchange format that is easy for humans to read and write, and easy for machines to parse and generate. JSON is a text format that is completely language independent but uses conventions familiar to programmers of the C-family of languages.

### Why Learn JSON?

JSON is valuable for:

1. **Data Interchange**: Standard format for API communication
2. **Configuration Files**: Used in many applications for config
3. **Web APIs**: Most REST APIs use JSON
4. **NoSQL Databases**: MongoDB, CouchDB store JSON documents
5. **Universal Format**: Supported by virtually all programming languages
6. **Human Readable**: Easy to read and debug
7. **Lightweight**: More compact than XML
8. **Industry Standard**: Widely adopted across the industry

### Key Features

- **Language Independent**: Works with any programming language
- **Human Readable**: Easy to read and write
- **Lightweight**: Minimal syntax overhead
- **Structured Data**: Represents objects and arrays
- **Widely Supported**: Native support in JavaScript, Python, Java, C#, etc.
- **No Comments**: Simple format without comment syntax
- **UTF-8**: Supports international characters

---

## Getting Started

### What is JSON?

JSON (JavaScript Object Notation) is a lightweight data-interchange format. It's easy for humans to read and write, and easy for machines to parse and generate. JSON is language-independent and widely used for APIs, configuration files, and data storage.

### Your First JSON

**Example:**
```json
{
  "name": "Alice",
  "age": 25,
  "city": "New York",
  "active": true
}
```

---

## Fundamentals

### Overview

JSON is a text format that represents structured data using JavaScript object syntax. It's used for data interchange between systems, APIs, and applications.

### Key Concepts

- **Data Format**: Text-based, human-readable
- **Structure**: Objects and arrays
- **Syntax**: Name-value pairs, separated by commas
- **Keys**: Must be strings (double quotes)
- **Values**: String, number, object, array, boolean, null
- **No Comments**: JSON doesn't support comments

### Basic Syntax

**What this demonstrates:** JSON syntax rules.

**Rules:**
- Data is in name/value pairs
- Data is separated by commas
- Curly braces `{}` hold objects
- Square brackets `[]` hold arrays
- Keys must be strings (double quotes)
- Values can be: string, number, object, array, boolean, null

**Example:**
```json
{
  "name": "Commander",
  "age": 25,
  "active": true,
  "skills": ["Python", "JavaScript", "C++"],
  "address": {
    "city": "Houston",
    "state": "Texas",
    "country": "USA"
  },
  "salary": null
}
```

**Explanation:**
- Object: Wrapped in curly braces `{}`
- Key-value pairs: `"key": value`
- Arrays: Wrapped in square brackets `[]`
- Nested objects: Objects within objects
- Null: Represents absence of value

**Key Takeaways:**
- Keys must be in double quotes
- Values can be various types
- Objects use `{}`, arrays use `[]`
- JSON is case-sensitive

---

## Data Types

### Overview

JSON supports six data types: string, number, boolean, null, object, and array. Understanding these types is essential for working with JSON.

### Key Concepts

- **String**: Text in double quotes
- **Number**: Integer or floating-point
- **Boolean**: true or false (lowercase)
- **Null**: null (lowercase)
- **Object**: Collection of key-value pairs
- **Array**: Ordered list of values

### String

**What this demonstrates:** JSON strings.

**Code:**
```json
"Hello, World!"
"Commander"
"123 Main St"
"line1\\nline2"
"Quote: \\\"text\\\""
"Unicode: \\u0048\\u0065\\u006C\\u006C\\u006F"
```

**Escape Sequences:**
- `\"` - Double quote
- `\\` - Backslash
- `\/` - Forward slash
- `\b` - Backspace
- `\f` - Form feed
- `\n` - Newline
- `\r` - Carriage return
- `\t` - Tab
- `\uXXXX` - Unicode character

**Explanation:**
- Strings: Must be in double quotes
- Escape sequences: Special characters with backslash
- Unicode: `\uXXXX` format for Unicode characters
- No single quotes: Only double quotes are valid

**Key Takeaways:**
- Always use double quotes for strings
- Escape special characters with backslash
- Use Unicode escape sequences when needed

### Number

**What this demonstrates:** JSON numbers.

**Code:**
```json
42
-17
3.14159
-0.5
2.99e8
1.23e-10
```

**Rules:**
- No leading zeros (except `0.x`)
- Can be negative
- Scientific notation supported (`e` or `E`)
- No NaN or Infinity (use null instead)
- No hexadecimal or octal

**Key Takeaways:**
- Numbers can be integer or float
- Scientific notation is supported
- No special number values (NaN, Infinity)

### Boolean and Null

**What this demonstrates:** Boolean and null values.

**Code:**
```json
true
false
null
```

**Rules:**
- Boolean: `true` or `false` (lowercase only)
- Null: `null` (lowercase only)
- Not strings: Don't quote boolean/null
- Not other values: Not `True`, `FALSE`, `Null`, etc.

**Key Takeaways:**
- Use lowercase: `true`, `false`, `null`
- Don't quote boolean/null values
- `null` represents absence of value

### Object

**What this demonstrates:** JSON objects.

**Code:**
```json
{
  "firstName": "John",
  "lastName": "Doe",
  "age": 30,
  "isEmployed": true,
  "spouse": null,
  "children": ["Alice", "Bob"]
}
```

**Rules:**
- Keys must be strings (double quotes)
- Keys must be unique
- Order is not guaranteed (though most parsers preserve it)
- Can be nested
- Comma-separated key-value pairs

**Key Takeaways:**
- Objects use curly braces `{}`
- Keys must be unique strings
- Can contain any JSON value type
- Can be nested

### Array

**What this demonstrates:** JSON arrays.

**Code:**
```json
[
  "string",
  42,
  true,
  null,
  {"key": "value"},
  [1, 2, 3]
]
```

**Rules:**
- Maintains order
- Can contain mixed types
- Can be nested
- Comma-separated values
- Zero-indexed in most languages

**Key Takeaways:**
- Arrays use square brackets `[]`
- Can contain mixed types
- Maintains order
- Can be nested

---

## Usage in JavaScript

### Overview

JavaScript has built-in JSON support with `JSON.parse()` and `JSON.stringify()`. These methods convert between JSON strings and JavaScript objects.

### Key Concepts

- **JSON.parse()**: Convert JSON string to JavaScript object
- **JSON.stringify()**: Convert JavaScript object to JSON string
- **Replacer**: Filter/transform during stringification
- **Reviver**: Transform during parsing
- **Pretty Print**: Format with indentation

### Parsing JSON

**What this demonstrates:** Converting JSON string to JavaScript object.

**Code:**
```javascript
// Parse JSON string
const jsonString = '{"name":"Alice","age":25}';
const obj = JSON.parse(jsonString);
console.log(obj.name);  // "Alice"
console.log(obj.age);   // 25

// Parse with reviver (transform values)
const text = '{"date":"2024-12-30"}';
const data = JSON.parse(text, (key, value) => {
  return key === 'date' ? new Date(value) : value;
});
```

**Explanation:**
- `JSON.parse()`: Parses JSON string to object
- Reviver function: Optional callback to transform values
- Error handling: Throws error for invalid JSON
- Common use: Parse API responses

**Key Takeaways:**
- `JSON.parse()` converts string to object
- Use try/catch for error handling
- Reviver function can transform values

### Stringifying

**What this demonstrates:** Converting JavaScript object to JSON string.

**Code:**
```javascript
// Stringify object
const obj = {name: 'Alice', age: 25};
const json = JSON.stringify(obj);
// Result: '{"name":"Alice","age":25}'

// Pretty print (indented)
const pretty = JSON.stringify(obj, null, 2);
// Result: Formatted with 2-space indentation

// With replacer (filter properties)
const filtered = JSON.stringify(obj, ['name']);  // Only include 'name'
// Result: '{"name":"Alice"}'

// With replacer function
const transformed = JSON.stringify(obj, (key, value) => {
  return typeof value === 'string' ? value.toUpperCase() : value;
});
```

**Explanation:**
- `JSON.stringify()`: Converts object to JSON string
- Replacer: Filter or transform values (array or function)
- Space: Number or string for indentation
- Returns: JSON string

**Key Takeaways:**
- `JSON.stringify()` converts object to string
- Use `null, 2` for pretty printing
- Replacer can filter/transform values

---

## Usage in Python

### Overview

Python's `json` module provides functions for encoding and decoding JSON. It's part of the standard library and widely used.

### Key Concepts

- **json.loads()**: Parse JSON string
- **json.dumps()**: Convert to JSON string
- **json.load()**: Read from file
- **json.dump()**: Write to file
- **Options**: indent, sort_keys, ensure_ascii

### Parsing and Encoding

**What this demonstrates:** Working with JSON in Python.

**Code:**
```python
import json

# Parse JSON string
json_string = '{"name": "Alice", "age": 25}'
data = json.loads(json_string)
print(data['name'])  # "Alice"

# Convert to JSON string
obj = {'name': 'Alice', 'age': 25}
json_str = json.dumps(obj)
# Result: '{"name": "Alice", "age": 25}'

# Pretty print
pretty = json.dumps(obj, indent=2, sort_keys=True)

# File operations
# Read from file
with open('data.json', 'r') as f:
    data = json.load(f)

# Write to file
with open('data.json', 'w') as f:
    json.dump(obj, f, indent=2)
```

**Explanation:**
- `json.loads()`: Parse JSON string to Python dict
- `json.dumps()`: Convert Python object to JSON string
- `json.load()`: Read JSON from file
- `json.dump()`: Write JSON to file
- Options: `indent`, `sort_keys`, `ensure_ascii`

**Key Takeaways:**
- `json.loads()` for strings, `json.load()` for files
- `json.dumps()` for strings, `json.dump()` for files
- Use `indent` for pretty printing
- `sort_keys=True` for sorted keys

---

## Validation

### Overview

JSON validation ensures data conforms to JSON syntax rules. JSON Schema provides structure validation and data constraints.

### Key Concepts

- **Syntax Validation**: Valid JSON format
- **JSON Schema**: Structure and constraint validation
- **Common Errors**: Trailing commas, single quotes, etc.
- **Validators**: Tools and libraries for validation

### Valid vs Invalid JSON

**Valid JSON:**
```json
{}
[]
{"key": "value"}
[1, 2, 3]
null
true
42
"string"
```

**Invalid JSON (Common Errors):**
```json
// Trailing comma (invalid)
{"name": "Alice",}

// Single quotes (invalid)
{'name': 'Alice'}

// Unquoted keys (invalid)
{name: "Alice"}

// Undefined (invalid - JavaScript only)
{"value": undefined}

// NaN (invalid)
{"value": NaN}

// Comments (invalid)
{"name": "Alice" /* comment */}

// Trailing decimal (invalid)
{"value": 42.}
```

**Explanation:**
- Valid: Proper syntax with double quotes, correct structure
- Invalid: Common mistakes like trailing commas, single quotes
- No comments: JSON doesn't support comments
- No undefined: JavaScript-only concept

**Key Takeaways:**
- No trailing commas
- Use double quotes (not single)
- Keys must be quoted
- No comments allowed
- No undefined/NaN/Infinity

### JSON Schema

**What this demonstrates:** Using JSON Schema for validation.

**Code:**
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "minLength": 1,
      "maxLength": 100
    },
    "age": {
      "type": "integer",
      "minimum": 0,
      "maximum": 150
    },
    "email": {
      "type": "string",
      "format": "email"
    },
    "skills": {
      "type": "array",
      "items": {
        "type": "string"
      },
      "minItems": 1,
      "uniqueItems": true
    }
  },
  "required": ["name", "email"],
  "additionalProperties": false
}
```

**Explanation:**
- JSON Schema: Defines structure and constraints
- Properties: Define allowed properties
- Types: string, number, integer, boolean, object, array
- Constraints: minLength, maxLength, minimum, maximum, etc.
- Required: List of required properties

**Key Takeaways:**
- JSON Schema validates structure
- Define types and constraints
- Use `required` for mandatory fields
- `additionalProperties: false` prevents extra fields

---

## Best Practices

### Naming Conventions

- Use camelCase for keys (JavaScript convention)
- Or use snake_case (Python/Ruby convention)
- Be consistent within a project
- Use descriptive names
- Avoid special characters in keys

### Structure

- Keep structure flat when possible
- Limit nesting depth (3-4 levels max)
- Use arrays for lists of similar items
- Use objects for structured data
- Consider pagination for large datasets

### Data Types

- Use `null` for missing/unknown values
- Use empty string `""` for empty text
- Use empty array `[]` for no items
- Store dates as ISO 8601 strings
- Store large numbers as strings if needed

### Performance

- Minimize file size (remove whitespace in production)
- Use compression (gzip) for transfer
- Stream large JSON files
- Consider alternatives for very large data
- Cache parsed results when possible

### Security

- Validate input before parsing
- Set limits on JSON size
- Sanitize data before display
- Use HTTPS for transmission
- Don't store sensitive data in plain JSON
- Beware of prototype pollution attacks (JavaScript)

---

## Common Patterns

### API Response Pattern

```json
{
  "status": "success",
  "code": 200,
  "message": "Data retrieved successfully",
  "data": {
    "users": [...]
  },
  "timestamp": "2024-12-30T12:00:00Z"
}
```

### Pagination Pattern

```json
{
  "page": 1,
  "per_page": 20,
  "total": 100,
  "total_pages": 5,
  "data": [...],
  "links": {
    "first": "/api/items?page=1",
    "prev": null,
    "next": "/api/items?page=2",
    "last": "/api/items?page=5"
  }
}
```

### Error Response Pattern

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": [
      {
        "field": "email",
        "message": "Invalid email format"
      }
    ],
    "timestamp": "2024-12-30T12:00:00Z",
    "request_id": "abc123"
  }
}
```

---

## Advanced Topics

### JSON Pointer

**What this demonstrates:** Referencing values in JSON.

**Examples:**
- `/` - Root document
- `/name` - Top-level 'name' property
- `/users/0` - First item in 'users' array
- `/users/0/name` - 'name' property of first user
- `/a~1b` - Property 'a/b' (escaped)

### JSON Patch

**What this demonstrates:** Modifying JSON documents.

**Operations:**
- `add` - Add property
- `remove` - Remove property
- `replace` - Replace value
- `move` - Move property
- `copy` - Copy property
- `test` - Test value

### JSON Lines (NDJSON)

**What this demonstrates:** Newline-delimited JSON.

**Format:** One JSON object per line

**Use Cases:**
- Log files
- Streaming data
- Large datasets
- Line-by-line processing

---

## Alternatives

### Comparison

- **XML**: Verbose, schema validation, namespaces
- **YAML**: Human-readable, comments, indentation-sensitive
- **TOML**: Simple, clear syntax, good for config
- **Protocol Buffers**: Compact, fast, binary, schema-based
- **MessagePack**: Compact, fast, binary
- **Avro**: Compact, schema evolution, binary

**When to use alternatives:**
- Protocol Buffers: High performance, large scale
- YAML: Configuration files, human-edited
- XML: When you need schema/namespaces
- JSON: APIs, web services, general data interchange

---

## Resources

### Official Documentation

- **JSON.org**: https://www.json.org/
- **RFC 8259**: JSON Standard Specification
- **ECMA-404**: JSON Data Interchange Standard

### Learning Resources

- **JSON.org Introduction**: https://www.json.org/json-en.html
- **MDN JSON Guide**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON
- **JSON Schema**: https://json-schema.org/

### Validation Tools

- **JSONLint**: Online JSON validator
- **JSON Formatter**: Format and validate JSON
- **JSON Schema Validator**: Validate against schemas

### Tools

- **jq**: Command-line JSON processor
- **JSON Formatter**: Browser extensions
- **Postman**: API testing with JSON
- **JSON Viewer**: Visualize JSON structures

---

