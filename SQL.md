# SQL - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Database & Table Creation (DDL)](#database--table-creation-ddl)
3. [Data Types](#data-types)
4. [INSERT, UPDATE, DELETE (DML)](#insert-update-delete-dml)
5. [SELECT Queries (Basic)](#select-queries-basic)
6. [Aggregate Functions](#aggregate-functions)
7. [JOINS](#joins)
8. [Subqueries](#subqueries)
9. [Set Operations](#set-operations)
10. [Window Functions](#window-functions)
11. [String Functions](#string-functions)
12. [Date and Time Functions](#date-and-time-functions)
13. [Numeric Functions](#numeric-functions)
14. [Indexes](#indexes)
15. [Transactions](#transactions)
16. [Views](#views)
17. [Stored Procedures & Functions](#stored-procedures--functions)
18. [Triggers](#triggers)
19. [Best Practices](#best-practices)
20. [Common Patterns](#common-patterns)
21. [Resources](#resources)

---

## Introduction

### What is SQL?

SQL (Structured Query Language) is a domain-specific language designed for managing data in relational database management systems (RDBMS). SQL is used for storing, manipulating, and retrieving data from databases. It's a standard language, though different database systems (MySQL, PostgreSQL, SQL Server, Oracle) have their own extensions.

### Why Learn SQL?

SQL is valuable for:

1. **Data Management**: Essential for working with relational databases
2. **Universal Language**: Standard across most database systems
3. **Data Analysis**: Powerful querying capabilities for analytics
4. **Backend Development**: Core skill for web and application development
5. **Data Science**: Essential for data extraction and preprocessing
6. **Business Intelligence**: Foundation for reporting and analytics
7. **Career Opportunities**: Required skill in many technical roles
8. **Foundation**: Understanding databases is fundamental to modern development

### Key Features

- **Declarative Language**: Describe what you want, not how to get it
- **Relational Model**: Works with tables and relationships
- **ACID Properties**: Ensures data integrity (Atomicity, Consistency, Isolation, Durability)
- **Set-Based Operations**: Efficient processing of large datasets
- **Standard Language**: ANSI SQL standard with database-specific extensions
- **Multiple Operations**: Data definition (DDL), manipulation (DML), and query (DQL)

---

## Database & Table Creation (DDL)

### Overview

DDL (Data Definition Language) statements are used to create, modify, and delete database structures. These include CREATE, ALTER, DROP, and TRUNCATE statements.

### Key Concepts

- **CREATE DATABASE**: Create new database
- **CREATE TABLE**: Create new table with columns and constraints
- **ALTER TABLE**: Modify existing table structure
- **DROP TABLE**: Delete table
- **TRUNCATE TABLE**: Delete all data, keep structure
- **Constraints**: PRIMARY KEY, FOREIGN KEY, UNIQUE, CHECK, NOT NULL
- **AUTO_INCREMENT/SERIAL**: Auto-incrementing primary keys

### Creating Databases

**What this demonstrates:** Creating and managing databases.

**Code:**
```sql
-- CREATE DATABASE
CREATE DATABASE company_db;

-- MySQL, PostgreSQL: IF NOT EXISTS
CREATE DATABASE IF NOT EXISTS company_db;

-- MySQL: Specify character set and collation
CREATE DATABASE company_db 
    CHARACTER SET utf8mb4 
    COLLATE utf8mb4_unicode_ci;

-- USE DATABASE (switch to database)
USE company_db;  -- MySQL, SQL Server
-- \c company_db;  -- PostgreSQL

-- DROP DATABASE
DROP DATABASE company_db;
DROP DATABASE IF EXISTS company_db;
```

**Explanation:**
- `CREATE DATABASE name`: Creates new database
- `IF NOT EXISTS`: Prevents error if database exists
- `CHARACTER SET`: Specifies character encoding (MySQL)
- `COLLATE`: Specifies collation rules (MySQL)
- `USE database`: Switches to database context (MySQL, SQL Server)
- `DROP DATABASE`: Deletes database (use with caution)

**Key Takeaways:**
- `CREATE DATABASE` to create database
- `USE` to switch context (MySQL, SQL Server)
- `DROP DATABASE` deletes database

### Creating Tables

**What this demonstrates:** Creating tables with columns and constraints.

**Code:**
```sql
-- Basic CREATE TABLE
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    hire_date DATE,
    salary DECIMAL(10, 2),
    department_id INT
);

-- AUTO_INCREMENT / SERIAL / IDENTITY
CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,  -- MySQL
    -- employee_id SERIAL PRIMARY KEY,           -- PostgreSQL
    -- employee_id INT IDENTITY(1,1) PRIMARY KEY, -- SQL Server
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- CREATE TABLE with all constraints
CREATE TABLE employees (
    employee_id INT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100),
    phone VARCHAR(20),
    hire_date DATE DEFAULT CURRENT_DATE,
    salary DECIMAL(10, 2) CHECK (salary > 0),
    department_id INT,
    manager_id INT,
    
    -- PRIMARY KEY
    PRIMARY KEY (employee_id),
    
    -- UNIQUE CONSTRAINT
    UNIQUE (email),
    
    -- CHECK CONSTRAINT
    CONSTRAINT chk_hire_date CHECK (hire_date <= CURRENT_DATE),
    
    -- FOREIGN KEY
    FOREIGN KEY (department_id) REFERENCES departments(department_id),
    FOREIGN KEY (manager_id) REFERENCES employees(employee_id)
);

-- Composite PRIMARY KEY
CREATE TABLE order_items (
    order_id INT,
    product_id INT,
    quantity INT,
    price DECIMAL(10, 2),
    PRIMARY KEY (order_id, product_id)
);

-- CREATE TABLE FROM EXISTING TABLE
CREATE TABLE employees_backup AS
SELECT * FROM employees;

-- CREATE TEMPORARY TABLE
CREATE TEMPORARY TABLE temp_sales (
    sale_id INT,
    amount DECIMAL(10, 2)
);
```

**Explanation:**
- `CREATE TABLE name (columns)`: Creates new table
- Column definition: `name type [constraints]`
- `PRIMARY KEY`: Uniquely identifies row
- `FOREIGN KEY`: References another table
- `UNIQUE`: Column must have unique values
- `NOT NULL`: Column cannot be NULL
- `CHECK`: Validates condition
- `DEFAULT`: Default value
- `AUTO_INCREMENT/SERIAL/IDENTITY`: Auto-incrementing
- Composite key: Multiple columns as primary key

**Key Takeaways:**
- `CREATE TABLE` defines table structure
- Constraints enforce data integrity
- Primary keys uniquely identify rows
- Foreign keys enforce relationships

### Altering Tables

**What this demonstrates:** Modifying table structure.

**Code:**
```sql
-- ADD COLUMN
ALTER TABLE employees ADD COLUMN middle_name VARCHAR(50);

-- DROP COLUMN
ALTER TABLE employees DROP COLUMN middle_name;

-- MODIFY COLUMN (change type/size)
ALTER TABLE employees MODIFY COLUMN salary DECIMAL(12, 2);  -- MySQL
ALTER TABLE employees ALTER COLUMN salary TYPE DECIMAL(12, 2);  -- PostgreSQL

-- RENAME COLUMN
ALTER TABLE employees RENAME COLUMN email TO email_address;

-- ADD CONSTRAINT
ALTER TABLE employees ADD CONSTRAINT fk_dept 
    FOREIGN KEY (department_id) REFERENCES departments(department_id);

-- DROP CONSTRAINT
ALTER TABLE employees DROP CONSTRAINT fk_dept;
```

**Explanation:**
- `ALTER TABLE`: Modifies table structure
- `ADD COLUMN`: Adds new column
- `DROP COLUMN`: Removes column
- `MODIFY/ALTER COLUMN`: Changes column definition
- `RENAME COLUMN`: Renames column
- `ADD CONSTRAINT`: Adds constraint
- `DROP CONSTRAINT`: Removes constraint

**Key Takeaways:**
- `ALTER TABLE` modifies table structure
- Can add/drop columns and constraints
- Syntax varies by database system

### Dropping and Truncating Tables

**What this demonstrates:** Deleting tables and data.

**Code:**
```sql
-- DROP TABLE (deletes table and data)
DROP TABLE employees;
DROP TABLE IF EXISTS employees;
DROP TABLE employees CASCADE;  -- Also drop dependent objects (PostgreSQL)

-- TRUNCATE TABLE (deletes all data, keeps structure)
TRUNCATE TABLE employees;
```

**Explanation:**
- `DROP TABLE`: Deletes table completely (structure and data)
- `IF EXISTS`: Prevents error if table doesn't exist
- `CASCADE`: Also drops dependent objects
- `TRUNCATE TABLE`: Deletes all rows, keeps table structure
- Faster than DELETE: Truncate is faster for deleting all rows

**Key Takeaways:**
- `DROP TABLE` deletes table
- `TRUNCATE TABLE` deletes all data
- `CASCADE` drops dependent objects

---

## Data Types

### Overview

SQL supports various data types for different kinds of data. Understanding data types is crucial for proper database design and data storage.

### Key Concepts

- **Numeric Types**: Integers and floating-point numbers
- **String Types**: Fixed and variable-length strings
- **Date/Time Types**: Date and time values
- **Boolean**: True/false values
- **JSON**: JSON data (modern databases)
- **UUID**: Universally unique identifiers

### Numeric Types

**What this demonstrates:** Numeric data types.

**Code:**
```sql
CREATE TABLE numeric_types (
    -- Integers
    tiny_int TINYINT,           -- -128 to 127 (MySQL)
    small_int SMALLINT,         -- -32,768 to 32,767
    medium_int MEDIUMINT,       -- -8,388,608 to 8,388,607 (MySQL)
    int_val INT,                -- -2 billion to 2 billion
    big_int BIGINT,             -- Very large integers
    
    -- Decimal (exact)
    decimal_val DECIMAL(10, 2), -- 10 digits, 2 after decimal
    numeric_val NUMERIC(10, 2), -- Same as DECIMAL
    
    -- Floating point (approximate)
    float_val FLOAT,            -- Single precision
    double_val DOUBLE,          -- Double precision
    real_val REAL               -- Implementation-specific
);
```

**Explanation:**
- Integers: `TINYINT`, `SMALLINT`, `INT`, `BIGINT` (various sizes)
- Decimal: `DECIMAL(p, s)` or `NUMERIC(p, s)` (exact, p=precision, s=scale)
- Float: `FLOAT`, `DOUBLE`, `REAL` (approximate, for scientific data)
- Use DECIMAL: For money and exact values
- Use FLOAT: For scientific/approximate values

**Key Takeaways:**
- Multiple integer sizes available
- `DECIMAL` for exact values (money)
- `FLOAT/DOUBLE` for approximate values

### String Types

**What this demonstrates:** String data types.

**Code:**
```sql
CREATE TABLE string_types (
    -- Fixed length
    char_fixed CHAR(10),        -- Fixed length, padded
    
    -- Variable length
    varchar_var VARCHAR(255),   -- Variable length, up to max
    
    -- Large text
    text_val TEXT,              -- Large text
    tiny_text TINYTEXT,         -- Up to 255 chars (MySQL)
    medium_text MEDIUMTEXT,     -- Up to 16MB (MySQL)
    long_text LONGTEXT,         -- Up to 4GB (MySQL)
    
    -- Binary
    binary_fixed BINARY(16),    -- Fixed binary
    varbinary_var VARBINARY(255), -- Variable binary
    blob_val BLOB               -- Binary large object
);
```

**Explanation:**
- `CHAR(n)`: Fixed length, padded with spaces
- `VARCHAR(n)`: Variable length, up to n characters
- `TEXT`: Large text data
- `BINARY/VARBINARY`: Binary data
- `BLOB`: Binary large object
- Use CHAR: For fixed-length strings (codes, IDs)
- Use VARCHAR: For variable-length strings (names, descriptions)

**Key Takeaways:**
- `CHAR` for fixed-length strings
- `VARCHAR` for variable-length strings
- `TEXT` for large text data

### Date and Time Types

**What this demonstrates:** Date and time data types.

**Code:**
```sql
CREATE TABLE datetime_types (
    date_val DATE,              -- 'YYYY-MM-DD'
    time_val TIME,              -- 'HH:MM:SS'
    datetime_val DATETIME,      -- 'YYYY-MM-DD HH:MM:SS'
    timestamp_val TIMESTAMP,    -- Unix timestamp (auto-updates)
    year_val YEAR               -- Year (MySQL)
);
```

**Explanation:**
- `DATE`: Date only (YYYY-MM-DD)
- `TIME`: Time only (HH:MM:SS)
- `DATETIME`: Date and time (YYYY-MM-DD HH:MM:SS)
- `TIMESTAMP`: Unix timestamp (often auto-updates)
- Format: Standard format is ISO 8601 (YYYY-MM-DD)
- TIMESTAMP: Often used for created/updated timestamps

**Key Takeaways:**
- `DATE`, `TIME`, `DATETIME`, `TIMESTAMP` available
- Standard format: YYYY-MM-DD HH:MM:SS
- TIMESTAMP often auto-updates

### Boolean and Special Types

**What this demonstrates:** Boolean and other special types.

**Code:**
```sql
-- Boolean (implementation varies)
CREATE TABLE boolean_types (
    is_active BOOLEAN,          -- PostgreSQL
    -- is_active TINYINT(1),    -- MySQL (0 or 1)
    -- is_active BIT,           -- SQL Server
    status ENUM('active', 'inactive')  -- MySQL ENUM
);

-- JSON (modern databases)
CREATE TABLE json_types (
    data JSON,                  -- MySQL, PostgreSQL
    metadata JSONB              -- PostgreSQL (binary JSON, faster)
);

-- UUID
CREATE TABLE uuid_types (
    id UUID PRIMARY KEY         -- PostgreSQL
    -- id CHAR(36)              -- MySQL alternative
);
```

**Explanation:**
- Boolean: Implementation varies (`BOOLEAN`, `TINYINT(1)`, `BIT`)
- ENUM: List of allowed values (MySQL)
- JSON: JSON data type (MySQL 5.7+, PostgreSQL 9.4+)
- JSONB: Binary JSON (PostgreSQL, faster)
- UUID: Universally unique identifier (PostgreSQL)

**Key Takeaways:**
- Boolean implementation varies by database
- JSON type available in modern databases
- UUID for unique identifiers

---

## INSERT, UPDATE, DELETE (DML)

### Overview

DML (Data Manipulation Language) statements are used to insert, update, and delete data in tables. These are essential for data management.

### Key Concepts

- **INSERT**: Add new rows to table
- **UPDATE**: Modify existing rows
- **DELETE**: Remove rows from table
- **WHERE Clause**: Condition for UPDATE and DELETE
- **Bulk Operations**: Insert/update/delete multiple rows

### INSERT Statements

**What this demonstrates:** Inserting data into tables.

**Code:**
```sql
-- INSERT single row
INSERT INTO employees (first_name, last_name, email, hire_date, salary)
VALUES ('John', 'Doe', 'john@example.com', '2024-01-15', 75000.00);

-- INSERT multiple rows
INSERT INTO employees (first_name, last_name, email, salary)
VALUES 
    ('Alice', 'Smith', 'alice@example.com', 80000.00),
    ('Bob', 'Johnson', 'bob@example.com', 72000.00),
    ('Charlie', 'Brown', 'charlie@example.com', 78000.00);

-- INSERT with SELECT (copy data)
INSERT INTO employees_backup
SELECT * FROM employees
WHERE department_id = 5;

-- INSERT with specific columns
INSERT INTO employees (first_name, last_name)
VALUES ('Jane', 'Doe');

-- INSERT IGNORE (skip duplicates - MySQL)
INSERT IGNORE INTO employees (email, first_name, last_name)
VALUES ('john@example.com', 'John', 'Doe');

-- INSERT ... ON DUPLICATE KEY UPDATE (MySQL)
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (1, 'John', 'Doe')
ON DUPLICATE KEY UPDATE 
    first_name = VALUES(first_name),
    last_name = VALUES(last_name);

-- INSERT ... ON CONFLICT (PostgreSQL)
INSERT INTO employees (employee_id, first_name, last_name)
VALUES (1, 'John', 'Doe')
ON CONFLICT (employee_id) DO UPDATE
SET first_name = EXCLUDED.first_name,
    last_name = EXCLUDED.last_name;
```

**Explanation:**
- `INSERT INTO table (columns) VALUES (values)`: Insert single row
- Multiple rows: Multiple value sets in one statement
- `INSERT ... SELECT`: Insert from query results
- Partial columns: Only specify some columns (others get defaults/NULL)
- `INSERT IGNORE`: Skip on duplicate (MySQL)
- `ON DUPLICATE KEY UPDATE`: Update if duplicate (MySQL)
- `ON CONFLICT`: Handle conflicts (PostgreSQL)

**Key Takeaways:**
- `INSERT INTO ... VALUES` for single/multiple rows
- `INSERT ... SELECT` to copy data
- Handle duplicates with IGNORE or ON CONFLICT

### UPDATE Statements

**What this demonstrates:** Updating existing data.

**Code:**
```sql
-- UPDATE single column
UPDATE employees
SET salary = 80000.00
WHERE employee_id = 1;

-- UPDATE multiple columns
UPDATE employees
SET 
    salary = 85000.00,
    department_id = 3
WHERE employee_id = 1;

-- UPDATE with subquery
UPDATE employees
SET salary = salary * 1.10
WHERE department_id IN (
    SELECT department_id 
    FROM departments 
    WHERE location = 'New York'
);

-- UPDATE all rows (be careful!)
UPDATE employees
SET last_updated = CURRENT_TIMESTAMP;
```

**Explanation:**
- `UPDATE table SET column = value WHERE condition`: Update rows
- Multiple columns: Comma-separated assignments
- WHERE clause: Specifies which rows to update (important!)
- Subquery: Can use subquery in WHERE or SET
- Without WHERE: Updates ALL rows (use with caution!)

**Key Takeaways:**
- `UPDATE ... SET ... WHERE` for updating rows
- Always use WHERE clause (unless updating all rows intentionally)
- Can update multiple columns at once

### DELETE Statements

**What this demonstrates:** Deleting data from tables.

**Code:**
```sql
-- DELETE specific rows
DELETE FROM employees
WHERE employee_id = 1;

-- DELETE with condition
DELETE FROM employees
WHERE department_id = 5;

-- DELETE with subquery
DELETE FROM employees
WHERE employee_id IN (
    SELECT employee_id 
    FROM employees 
    WHERE hire_date < '2020-01-01'
);

-- DELETE all rows (be careful!)
DELETE FROM employees;

-- TRUNCATE (faster for deleting all rows)
TRUNCATE TABLE employees;
```

**Explanation:**
- `DELETE FROM table WHERE condition`: Delete rows
- WHERE clause: Specifies which rows to delete (important!)
- Subquery: Can use subquery in WHERE
- Without WHERE: Deletes ALL rows (use with caution!)
- TRUNCATE: Faster than DELETE for all rows (but can't rollback)

**Key Takeaways:**
- `DELETE FROM ... WHERE` for deleting rows
- Always use WHERE clause (unless deleting all rows intentionally)
- `TRUNCATE TABLE` is faster for deleting all rows

---

## SELECT Queries (Basic)

### Overview

SELECT statements are used to retrieve data from tables. They form the foundation of SQL querying, allowing filtering, sorting, and formatting of results.

### Key Concepts

- **SELECT**: Retrieve columns from table
- **WHERE**: Filter rows
- **ORDER BY**: Sort results
- **LIMIT/OFFSET**: Pagination
- **DISTINCT**: Remove duplicates
- **Aliases**: Rename columns
- **CASE**: Conditional logic
- **NULL Handling**: IS NULL, IS NOT NULL, COALESCE

### Basic SELECT

**What this demonstrates:** Basic SELECT statements.

**Code:**
```sql
-- SELECT all columns
SELECT * FROM employees;

-- SELECT specific columns
SELECT first_name, last_name, salary FROM employees;

-- SELECT with aliases
SELECT 
    first_name AS "First Name",
    last_name AS "Last Name",
    salary * 12 AS annual_salary
FROM employees;

-- SELECT DISTINCT (unique values)
SELECT DISTINCT department_id FROM employees;
```

**Explanation:**
- `SELECT *`: Select all columns
- `SELECT column1, column2`: Select specific columns
- `AS alias`: Rename column in result
- `DISTINCT`: Remove duplicate rows
- Expressions: Can use expressions in SELECT (salary * 12)

**Key Takeaways:**
- `SELECT *` or `SELECT column1, column2`
- `AS` for column aliases
- `DISTINCT` removes duplicates

### WHERE Clause

**What this demonstrates:** Filtering rows with WHERE.

**Code:**
```sql
-- Comparison operators
SELECT * FROM employees WHERE salary > 70000;
SELECT * FROM employees WHERE salary >= 70000;
SELECT * FROM employees WHERE salary < 70000;
SELECT * FROM employees WHERE salary <= 70000;
SELECT * FROM employees WHERE salary = 70000;
SELECT * FROM employees WHERE salary != 70000;
SELECT * FROM employees WHERE salary <> 70000;

-- BETWEEN
SELECT * FROM employees WHERE salary BETWEEN 60000 AND 80000;

-- IN
SELECT * FROM employees WHERE department_id IN (1, 2, 3);

-- LIKE (pattern matching)
SELECT * FROM employees WHERE last_name LIKE 'S%';     -- Starts with S
SELECT * FROM employees WHERE last_name LIKE '%son';   -- Ends with son
SELECT * FROM employees WHERE last_name LIKE '%mit%';  -- Contains mit
SELECT * FROM employees WHERE first_name LIKE 'J___';  -- J followed by 3 chars

-- IS NULL / IS NOT NULL
SELECT * FROM employees WHERE manager_id IS NULL;
SELECT * FROM employees WHERE email IS NOT NULL;

-- AND, OR, NOT
SELECT * FROM employees WHERE salary > 70000 AND department_id = 3;
SELECT * FROM employees WHERE salary > 80000 OR department_id = 1;
SELECT * FROM employees WHERE NOT (department_id = 5);
```

**Explanation:**
- WHERE clause: Filters rows
- Comparison: `=`, `!=`, `<>`, `>`, `<`, `>=`, `<=`
- `BETWEEN`: Range (inclusive)
- `IN`: Match any value in list
- `LIKE`: Pattern matching (`%` = any, `_` = single char)
- `IS NULL`/`IS NOT NULL`: NULL checks
- `AND`, `OR`, `NOT`: Logical operators

**Key Takeaways:**
- WHERE filters rows
- `LIKE` for pattern matching
- `IS NULL` for NULL checks
- Use `AND`/`OR` for multiple conditions

### ORDER BY and LIMIT

**What this demonstrates:** Sorting and pagination.

**Code:**
```sql
-- ORDER BY
SELECT * FROM employees ORDER BY salary;               -- Ascending (default)
SELECT * FROM employees ORDER BY salary ASC;           -- Ascending
SELECT * FROM employees ORDER BY salary DESC;          -- Descending
SELECT * FROM employees ORDER BY last_name, first_name;  -- Multiple columns

-- LIMIT / OFFSET (pagination)
SELECT * FROM employees LIMIT 10;                      -- First 10 rows
SELECT * FROM employees LIMIT 10 OFFSET 20;            -- Skip 20, take 10

-- SQL Server uses TOP
SELECT TOP 10 * FROM employees;
SELECT TOP 10 PERCENT * FROM employees;
```

**Explanation:**
- `ORDER BY`: Sorts results
- `ASC`/`DESC`: Ascending/descending (ASC is default)
- Multiple columns: Sorts by first, then second, etc.
- `LIMIT n`: Returns first n rows
- `OFFSET m`: Skips m rows
- `TOP n`: SQL Server equivalent (no OFFSET in older versions)

**Key Takeaways:**
- `ORDER BY` sorts results
- `LIMIT`/`OFFSET` for pagination
- `TOP` in SQL Server

### CASE Expression

**What this demonstrates:** Conditional logic in queries.

**Code:**
```sql
-- CASE expression
SELECT 
    first_name,
    last_name,
    salary,
    CASE
        WHEN salary >= 90000 THEN 'High'
        WHEN salary >= 70000 THEN 'Medium'
        ELSE 'Low'
    END AS salary_grade
FROM employees;

-- Simple CASE
SELECT 
    first_name,
    department_id,
    CASE department_id
        WHEN 1 THEN 'Engineering'
        WHEN 2 THEN 'Sales'
        WHEN 3 THEN 'Marketing'
        ELSE 'Other'
    END AS department_name
FROM employees;

-- COALESCE (return first non-null value)
SELECT 
    first_name,
    COALESCE(phone, email, 'No contact') AS contact
FROM employees;
```

**Explanation:**
- `CASE`: Conditional logic
- Searched CASE: `CASE WHEN condition THEN value ... END`
- Simple CASE: `CASE value WHEN match THEN ... END`
- `COALESCE`: Returns first non-NULL value
- Useful for: Data transformation, NULL handling

**Key Takeaways:**
- `CASE` for conditional logic
- `COALESCE` for NULL handling
- Useful for data transformation

---

## Aggregate Functions

### Overview

Aggregate functions perform calculations on a set of rows and return a single value. They're essential for summary statistics and reporting.

### Key Concepts

- **COUNT**: Count rows or non-null values
- **SUM**: Sum of values
- **AVG**: Average of values
- **MIN/MAX**: Minimum/maximum values
- **GROUP BY**: Group rows for aggregation
- **HAVING**: Filter groups (after GROUP BY)

### Aggregate Functions

**What this demonstrates:** Common aggregate functions.

**Code:**
```sql
-- COUNT
SELECT COUNT(*) FROM employees;                        -- All rows
SELECT COUNT(email) FROM employees;                    -- Non-null emails
SELECT COUNT(DISTINCT department_id) FROM employees;   -- Unique departments

-- SUM
SELECT SUM(salary) FROM employees;

-- AVG
SELECT AVG(salary) FROM employees;

-- MIN / MAX
SELECT MIN(salary), MAX(salary) FROM employees;

-- Multiple aggregates
SELECT 
    COUNT(*) AS employee_count,
    AVG(salary) AS avg_salary,
    MIN(salary) AS min_salary,
    MAX(salary) AS max_salary,
    SUM(salary) AS total_salary
FROM employees;
```

**Explanation:**
- `COUNT(*)`: Counts all rows
- `COUNT(column)`: Counts non-NULL values
- `COUNT(DISTINCT column)`: Counts unique values
- `SUM`, `AVG`, `MIN`, `MAX`: Mathematical aggregates
- Aggregate functions: Return single value from multiple rows

**Key Takeaways:**
- Aggregate functions return single value
- `COUNT(*)` counts all rows
- `COUNT(DISTINCT)` counts unique values

### GROUP BY

**What this demonstrates:** Grouping data for aggregation.

**Code:**
```sql
-- GROUP BY
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;

-- GROUP BY multiple columns
SELECT department_id, manager_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id, manager_id;

-- GROUP BY with aggregates
SELECT 
    department_id,
    COUNT(*) AS employee_count,
    AVG(salary) AS avg_salary,
    MAX(salary) AS max_salary
FROM employees
GROUP BY department_id;

-- HAVING (filter groups)
SELECT department_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 70000;
```

**Explanation:**
- `GROUP BY`: Groups rows by column values
- Aggregate functions: Applied to each group
- All non-aggregate columns: Must be in GROUP BY
- `HAVING`: Filters groups (after aggregation)
- `WHERE` vs `HAVING`: WHERE filters rows, HAVING filters groups

**Key Takeaways:**
- `GROUP BY` groups rows for aggregation
- All non-aggregate columns must be in GROUP BY
- `HAVING` filters groups (after aggregation)

---

## JOINS

### Overview

JOINs combine rows from multiple tables based on related columns. Understanding JOINs is crucial for working with relational databases.

### Key Concepts

- **INNER JOIN**: Matching rows from both tables
- **LEFT JOIN**: All rows from left table, matching from right
- **RIGHT JOIN**: All rows from right table, matching from left
- **FULL OUTER JOIN**: All rows from both tables
- **CROSS JOIN**: Cartesian product
- **SELF JOIN**: Join table to itself

### JOIN Types

**What this demonstrates:** Different types of JOINs.

**Code:**
```sql
-- INNER JOIN (matching rows from both tables)
SELECT 
    e.first_name,
    e.last_name,
    d.name AS department_name
FROM employees e
INNER JOIN departments d ON e.department_id = d.department_id;

-- LEFT JOIN (all from left, matching from right)
SELECT 
    e.first_name,
    e.last_name,
    d.name AS department_name
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id;

-- RIGHT JOIN (all from right, matching from left)
SELECT 
    e.first_name,
    e.last_name,
    d.name AS department_name
FROM employees e
RIGHT JOIN departments d ON e.department_id = d.department_id;

-- FULL OUTER JOIN (all from both)
SELECT 
    e.first_name,
    e.last_name,
    d.name AS department_name
FROM employees e
FULL OUTER JOIN departments d ON e.department_id = d.department_id;

-- CROSS JOIN (Cartesian product)
SELECT e.first_name, d.name
FROM employees e
CROSS JOIN departments d;

-- SELF JOIN (join table to itself)
SELECT 
    e.first_name AS employee,
    m.first_name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id;

-- Multiple joins
SELECT 
    e.first_name,
    e.last_name,
    d.name AS department,
    p.name AS project
FROM employees e
INNER JOIN departments d ON e.department_id = d.department_id
INNER JOIN projects p ON d.department_id = p.department_id;
```

**Explanation:**
- INNER JOIN: Only matching rows
- LEFT JOIN: All left rows, matching right (NULL if no match)
- RIGHT JOIN: All right rows, matching left (NULL if no match)
- FULL OUTER JOIN: All rows from both (NULL if no match)
- CROSS JOIN: Every row from left with every row from right
- SELF JOIN: Join table to itself (uses aliases)
- ON clause: Join condition

**Key Takeaways:**
- INNER JOIN for matching rows only
- LEFT JOIN to include all left rows
- Use aliases for table names
- Multiple JOINs can be chained

---

## Subqueries

### Overview

Subqueries (nested queries) are queries within other queries. They're powerful for complex filtering and data retrieval.

### Key Concepts

- **Scalar Subquery**: Returns single value
- **Row Subquery**: Returns single row
- **Table Subquery**: Returns table
- **EXISTS**: Check if subquery returns rows
- **IN/ANY/ALL**: Compare with subquery results

### Subqueries

**What this demonstrates:** Using subqueries.

**Code:**
```sql
-- Subquery in WHERE clause
SELECT first_name, last_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- Subquery with IN
SELECT first_name, last_name
FROM employees
WHERE department_id IN (
    SELECT department_id 
    FROM departments 
    WHERE location = 'New York'
);

-- Subquery with EXISTS
SELECT first_name, last_name
FROM employees e
WHERE EXISTS (
    SELECT 1 
    FROM projects p 
    WHERE p.department_id = e.department_id
);

-- Subquery with ANY
SELECT first_name, salary
FROM employees
WHERE salary > ANY (
    SELECT salary 
    FROM employees 
    WHERE department_id = 3
);

-- Subquery with ALL
SELECT first_name, salary
FROM employees
WHERE salary > ALL (
    SELECT salary 
    FROM employees 
    WHERE department_id = 3
);

-- Correlated subquery
SELECT first_name, last_name, salary
FROM employees e1
WHERE salary > (
    SELECT AVG(salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```

**Explanation:**
- Subquery: Query within another query
- Scalar subquery: Returns single value (used in WHERE, SELECT)
- EXISTS: Returns true if subquery returns rows
- IN: Match any value in subquery result
- ANY/ALL: Compare with subquery results
- Correlated: Subquery references outer query

**Key Takeaways:**
- Subqueries for complex filtering
- EXISTS for existence checks
- Correlated subqueries reference outer query

---

## Set Operations

### Overview

Set operations combine results from multiple SELECT statements. They're useful for comparing and combining datasets.

### Key Concepts

- **UNION**: Combine results, remove duplicates
- **UNION ALL**: Combine results, keep duplicates
- **INTERSECT**: Common rows
- **EXCEPT/MINUS**: Rows in first but not second

### Set Operations

**What this demonstrates:** Set operations.

**Code:**
```sql
-- UNION (remove duplicates)
SELECT first_name, last_name FROM employees WHERE department_id = 1
UNION
SELECT first_name, last_name FROM employees WHERE department_id = 2;

-- UNION ALL (keep duplicates)
SELECT first_name, last_name FROM employees WHERE department_id = 1
UNION ALL
SELECT first_name, last_name FROM employees WHERE department_id = 2;

-- INTERSECT (common rows)
SELECT first_name, last_name FROM employees WHERE salary > 70000
INTERSECT
SELECT first_name, last_name FROM employees WHERE hire_date > '2024-01-01';

-- EXCEPT / MINUS (rows in first but not second)
SELECT first_name, last_name FROM employees WHERE salary > 70000
EXCEPT
SELECT first_name, last_name FROM employees WHERE department_id = 5;
```

**Explanation:**
- UNION: Combines results, removes duplicates
- UNION ALL: Combines results, keeps duplicates (faster)
- INTERSECT: Returns common rows
- EXCEPT/MINUS: Returns rows in first but not second
- Requirements: Same number of columns, compatible types
- MySQL: Doesn't support INTERSECT/EXCEPT (use JOINs)

**Key Takeaways:**
- UNION combines results
- UNION ALL is faster (no duplicate removal)
- INTERSECT/EXCEPT not in MySQL

---

## Window Functions

### Overview

Window functions perform calculations across a set of rows related to the current row. They're powerful for analytics and ranking.

### Key Concepts

- **ROW_NUMBER**: Sequential numbers
- **RANK/DENSE_RANK**: Ranking with/without gaps
- **PARTITION BY**: Separate groups
- **LAG/LEAD**: Access previous/next rows
- **Window Frames**: Define range of rows

### Window Functions

**What this demonstrates:** Using window functions.

**Code:**
```sql
-- ROW_NUMBER
SELECT 
    first_name,
    last_name,
    salary,
    ROW_NUMBER() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;

-- RANK (with gaps for ties)
SELECT 
    first_name,
    last_name,
    salary,
    RANK() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;

-- DENSE_RANK (without gaps)
SELECT 
    first_name,
    last_name,
    salary,
    DENSE_RANK() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;

-- PARTITION BY (separate rankings per group)
SELECT 
    first_name,
    last_name,
    department_id,
    salary,
    RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS dept_rank
FROM employees;

-- LAG / LEAD (access previous/next row)
SELECT 
    first_name,
    salary,
    LAG(salary, 1) OVER (ORDER BY hire_date) AS previous_salary,
    LEAD(salary, 1) OVER (ORDER BY hire_date) AS next_salary
FROM employees;

-- Running total
SELECT 
    hire_date,
    salary,
    SUM(salary) OVER (ORDER BY hire_date) AS running_total
FROM employees;
```

**Explanation:**
- Window functions: Perform calculations over window of rows
- OVER clause: Defines window
- PARTITION BY: Separate groups
- ORDER BY: Order within window
- ROW_NUMBER: Sequential numbers
- RANK: Ranking with gaps for ties
- DENSE_RANK: Ranking without gaps
- LAG/LEAD: Access previous/next rows

**Key Takeaways:**
- Window functions use OVER clause
- PARTITION BY for separate groups
- RANK vs DENSE_RANK (gaps vs no gaps)

---

## String Functions

### Overview

String functions manipulate text data. They're essential for data cleaning, formatting, and extraction.

### Key Concepts

- **CONCAT**: Combine strings
- **SUBSTRING**: Extract substring
- **UPPER/LOWER**: Case conversion
- **TRIM**: Remove whitespace
- **REPLACE**: Replace text
- **LENGTH**: String length
- **Pattern Matching**: Regular expressions

### String Functions

**What this demonstrates:** Common string functions.

**Code:**
```sql
-- CONCAT
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;

-- UPPER / LOWER
SELECT UPPER(first_name), LOWER(last_name) FROM employees;

-- LENGTH
SELECT LENGTH(first_name) FROM employees;  -- MySQL, PostgreSQL
SELECT LEN(first_name) FROM employees;     -- SQL Server

-- SUBSTRING
SELECT SUBSTRING(email, 1, 5) FROM employees;
SELECT SUBSTR(email, 1, 5) FROM employees;  -- MySQL, Oracle

-- LEFT / RIGHT
SELECT LEFT(first_name, 3) FROM employees;
SELECT RIGHT(last_name, 4) FROM employees;

-- TRIM
SELECT TRIM(first_name) FROM employees;
SELECT LTRIM(first_name) FROM employees;
SELECT RTRIM(first_name) FROM employees;

-- REPLACE
SELECT REPLACE(email, 'gmail.com', 'company.com') FROM employees;

-- Position functions
SELECT POSITION('@' IN email) FROM employees;  -- PostgreSQL
SELECT CHARINDEX('@', email) FROM employees;   -- SQL Server
SELECT INSTR(email, '@') FROM employees;       -- MySQL, Oracle
```

**Explanation:**
- CONCAT: Combines strings
- UPPER/LOWER: Case conversion
- LENGTH/LEN: String length
- SUBSTRING/SUBSTR: Extract substring
- LEFT/RIGHT: Extract from start/end
- TRIM: Remove whitespace
- REPLACE: Replace text
- Position functions: Find position of substring

**Key Takeaways:**
- Many string functions available
- Syntax varies by database
- Useful for data cleaning

---

## Date and Time Functions

### Overview

Date and time functions manipulate temporal data. They're essential for date calculations, formatting, and extraction.

### Key Concepts

- **CURRENT_DATE/TIMESTAMP**: Current date/time
- **EXTRACT**: Extract date parts
- **Date Arithmetic**: Add/subtract intervals
- **Date Formatting**: Format dates
- **Age Calculations**: Calculate differences

### Date and Time Functions

**What this demonstrates:** Working with dates and times.

**Code:**
```sql
-- Current date/time
SELECT CURRENT_DATE;
SELECT CURRENT_TIMESTAMP;
SELECT NOW();  -- MySQL, PostgreSQL

-- Extract parts
SELECT YEAR(hire_date), MONTH(hire_date), DAY(hire_date) FROM employees;
SELECT EXTRACT(YEAR FROM hire_date) FROM employees;  -- PostgreSQL

-- Date arithmetic
SELECT DATE_ADD(hire_date, INTERVAL 1 YEAR) FROM employees;  -- MySQL
SELECT hire_date + INTERVAL '1 year' FROM employees;         -- PostgreSQL

-- Date difference
SELECT DATEDIFF(CURRENT_DATE, hire_date) AS days_employed FROM employees;  -- MySQL
SELECT CURRENT_DATE - hire_date AS days_employed FROM employees;           -- PostgreSQL

-- Format dates
SELECT DATE_FORMAT(hire_date, '%Y-%m-%d') FROM employees;  -- MySQL
SELECT TO_CHAR(hire_date, 'YYYY-MM-DD') FROM employees;    -- PostgreSQL

-- Age calculation
SELECT 
    first_name,
    TIMESTAMPDIFF(YEAR, hire_date, CURRENT_DATE) AS years_employed
FROM employees;  -- MySQL
```

**Explanation:**
- CURRENT_DATE/TIMESTAMP: Get current date/time
- EXTRACT: Extract year, month, day, etc.
- Date arithmetic: Add/subtract intervals
- DATEDIFF: Calculate difference
- Date formatting: Format dates as strings
- Syntax varies: Different syntax for different databases

**Key Takeaways:**
- Many date functions available
- Syntax varies by database
- Useful for date calculations

---

## Numeric Functions

### Overview

Numeric functions perform mathematical operations. They're useful for calculations and data transformation.

### Key Concepts

- **ROUND/CEIL/FLOOR**: Rounding functions
- **ABS**: Absolute value
- **POWER/SQRT**: Power and roots
- **Trigonometry**: SIN, COS, TAN
- **LOG**: Logarithms
- **RANDOM**: Random numbers

### Numeric Functions

**What this demonstrates:** Common numeric functions.

**Code:**
```sql
-- Basic math
SELECT ABS(-10);           -- 10
SELECT CEIL(4.3);          -- 5
SELECT FLOOR(4.8);         -- 4
SELECT ROUND(4.567, 2);    -- 4.57
SELECT TRUNCATE(4.567, 2); -- 4.56  (MySQL)

-- Power and roots
SELECT POWER(2, 3);        -- 8
SELECT SQRT(16);           -- 4

-- Logarithms
SELECT LN(10);             -- Natural log
SELECT LOG(10);            -- Log base 10
SELECT LOG(2, 8);          -- Log base 2 of 8 = 3

-- Trigonometry
SELECT SIN(PI());
SELECT COS(0);
SELECT TAN(PI()/4);

-- Random
SELECT RAND();             -- MySQL (0 to 1)
SELECT RANDOM();           -- PostgreSQL (0 to 1)

-- Modulo
SELECT MOD(10, 3);         -- 1
SELECT 10 % 3;             -- 1
```

**Explanation:**
- ABS: Absolute value
- CEIL/FLOOR: Round up/down
- ROUND: Round to decimal places
- POWER/SQRT: Power and square root
- Trigonometry: SIN, COS, TAN
- Logarithms: LN, LOG
- Random: Generate random numbers
- Modulo: Remainder operation

**Key Takeaways:**
- Standard mathematical functions available
- Useful for calculations
- Syntax consistent across databases

---

## Indexes

### Overview

Indexes improve query performance by creating data structures that allow faster data retrieval. Understanding indexes is crucial for database optimization.

### Key Concepts

- **CREATE INDEX**: Create index on column
- **UNIQUE INDEX**: Enforce uniqueness
- **Composite Index**: Index on multiple columns
- **Partial Index**: Index with condition
- **Full-Text Index**: For text search
- **Covering Index**: Include additional columns

### Indexes

**What this demonstrates:** Creating and using indexes.

**Code:**
```sql
-- CREATE INDEX
CREATE INDEX idx_employee_last_name ON employees(last_name);

-- CREATE UNIQUE INDEX
CREATE UNIQUE INDEX idx_employee_email ON employees(email);

-- COMPOSITE INDEX
CREATE INDEX idx_employee_name ON employees(last_name, first_name);

-- PARTIAL INDEX (PostgreSQL)
CREATE INDEX idx_high_earners ON employees(salary) 
WHERE salary > 100000;

-- FULL-TEXT INDEX (MySQL)
CREATE FULLTEXT INDEX idx_employee_notes ON employees(notes);

-- DROP INDEX
DROP INDEX idx_employee_last_name ON employees;  -- MySQL
DROP INDEX idx_employee_last_name;               -- PostgreSQL
```

**Explanation:**
- Index: Data structure for faster lookups
- CREATE INDEX: Creates index on column(s)
- UNIQUE INDEX: Enforces uniqueness
- Composite: Index on multiple columns
- Partial: Index with WHERE condition
- Full-text: For text search
- Trade-off: Faster reads, slower writes

**Key Takeaways:**
- Indexes speed up queries
- Index frequently queried columns
- Balance between read and write performance

---

## Transactions

### Overview

Transactions ensure data integrity by grouping operations that must succeed or fail together. They're essential for maintaining ACID properties.

### Key Concepts

- **START TRANSACTION**: Begin transaction
- **COMMIT**: Save changes
- **ROLLBACK**: Undo changes
- **SAVEPOINT**: Intermediate rollback point
- **ACID Properties**: Atomicity, Consistency, Isolation, Durability
- **Isolation Levels**: Control transaction isolation

### Transactions

**What this demonstrates:** Working with transactions.

**Code:**
```sql
-- START TRANSACTION
START TRANSACTION;  -- MySQL, PostgreSQL
BEGIN;              -- PostgreSQL, SQL Server

-- COMMIT (save changes)
COMMIT;

-- ROLLBACK (undo changes)
ROLLBACK;

-- SAVEPOINT
START TRANSACTION;
INSERT INTO employees (first_name, last_name) VALUES ('John', 'Doe');
SAVEPOINT sp1;
INSERT INTO employees (first_name, last_name) VALUES ('Jane', 'Smith');
ROLLBACK TO sp1;  -- Undo second insert, keep first
COMMIT;

-- Transaction example
START TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;
COMMIT;

-- Isolation levels
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```

**Explanation:**
- Transaction: Group of operations that succeed or fail together
- START TRANSACTION/BEGIN: Begin transaction
- COMMIT: Save all changes
- ROLLBACK: Undo all changes
- SAVEPOINT: Intermediate rollback point
- ACID: Atomicity, Consistency, Isolation, Durability
- Isolation levels: Control how transactions interact

**Key Takeaways:**
- Transactions ensure data integrity
- COMMIT saves changes
- ROLLBACK undoes changes
- ACID properties guarantee reliability

---

## Views

### Overview

Views are virtual tables based on the result of a SELECT query. They simplify complex queries and provide abstraction.

### Key Concepts

- **CREATE VIEW**: Create view
- **Updatable Views**: Views that can be updated
- **Materialized Views**: Cached views (PostgreSQL, Oracle)
- **WITH CHECK OPTION**: Ensure updates meet conditions

### Views

**What this demonstrates:** Creating and using views.

**Code:**
```sql
-- CREATE VIEW
CREATE VIEW employee_summary AS
SELECT 
    e.employee_id,
    e.first_name,
    e.last_name,
    d.name AS department,
    e.salary
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id;

-- USE VIEW
SELECT * FROM employee_summary WHERE salary > 70000;

-- CREATE OR REPLACE VIEW
CREATE OR REPLACE VIEW employee_summary AS
SELECT 
    e.employee_id,
    CONCAT(e.first_name, ' ', e.last_name) AS full_name,
    d.name AS department,
    e.salary
FROM employees e
LEFT JOIN departments d ON e.department_id = d.department_id;

-- UPDATABLE VIEW
CREATE VIEW high_earners AS
SELECT * FROM employees WHERE salary > 80000
WITH CHECK OPTION;

UPDATE high_earners SET salary = 85000 WHERE employee_id = 1;

-- MATERIALIZED VIEW (PostgreSQL)
CREATE MATERIALIZED VIEW sales_summary AS
SELECT 
    product_id,
    SUM(quantity) AS total_quantity,
    SUM(total_price) AS total_revenue
FROM sales
GROUP BY product_id;

REFRESH MATERIALIZED VIEW sales_summary;

-- DROP VIEW
DROP VIEW employee_summary;
```

**Explanation:**
- View: Virtual table based on query
- CREATE VIEW: Creates view
- Views simplify: Complex queries
- Updatable: Can INSERT/UPDATE/DELETE (if simple)
- Materialized: Cached results (PostgreSQL, Oracle)
- WITH CHECK OPTION: Ensures updates meet WHERE condition

**Key Takeaways:**
- Views simplify complex queries
- Updatable views can be modified
- Materialized views cache results

---

## Stored Procedures & Functions

### Overview

Stored procedures and functions are reusable database code. They're useful for encapsulating business logic and improving performance.

### Key Concepts

- **Stored Procedure**: Reusable code block
- **Function**: Returns value
- **Parameters**: IN, OUT, INOUT
- **Variables**: Local variables
- **Control Flow**: IF, WHILE, LOOP
- **Error Handling**: Exception handling

### Stored Procedures

**What this demonstrates:** Creating stored procedures.

**Code:**
```sql
-- Stored Procedure (MySQL)
DELIMITER //
CREATE PROCEDURE get_employee_by_id(IN emp_id INT)
BEGIN
    SELECT * FROM employees WHERE employee_id = emp_id;
END //
DELIMITER ;

-- CALL PROCEDURE
CALL get_employee_by_id(1);

-- Procedure with OUT parameter
DELIMITER //
CREATE PROCEDURE get_employee_count(OUT emp_count INT)
BEGIN
    SELECT COUNT(*) INTO emp_count FROM employees;
END //
DELIMITER ;

CALL get_employee_count(@count);
SELECT @count;
```

**Explanation:**
- Stored procedure: Reusable code block
- Parameters: IN (input), OUT (output), INOUT (both)
- CALL: Execute procedure
- Benefits: Performance, security, code reuse
- Syntax varies: Different syntax for different databases

**Key Takeaways:**
- Stored procedures for reusable code
- Parameters: IN, OUT, INOUT
- CALL to execute
- Syntax varies by database

---

## Triggers

### Overview

Triggers are automatic actions that execute when specific events occur. They're useful for audit trails, data validation, and automation.

### Key Concepts

- **BEFORE/AFTER**: Trigger timing
- **INSERT/UPDATE/DELETE**: Trigger events
- **NEW/OLD**: Access new/old row values
- **Row-level Triggers**: Execute for each row
- **Statement-level Triggers**: Execute once per statement

### Triggers

**What this demonstrates:** Creating triggers.

**Code:**
```sql
-- BEFORE INSERT TRIGGER (MySQL)
DELIMITER //
CREATE TRIGGER before_employee_insert
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    SET NEW.created_at = NOW();
    SET NEW.email = LOWER(NEW.email);
END //
DELIMITER ;

-- AFTER UPDATE TRIGGER
DELIMITER //
CREATE TRIGGER after_salary_update
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
    IF NEW.salary != OLD.salary THEN
        INSERT INTO salary_history (employee_id, old_salary, new_salary, changed_at)
        VALUES (NEW.employee_id, OLD.salary, NEW.salary, NOW());
    END IF;
END //
DELIMITER ;

-- DROP TRIGGER
DROP TRIGGER before_employee_insert;
```

**Explanation:**
- Trigger: Automatic action on event
- BEFORE/AFTER: Timing
- INSERT/UPDATE/DELETE: Events
- NEW/OLD: Access new/old row values
- Row-level: Execute for each row
- Use cases: Audit trails, validation, automation

**Key Takeaways:**
- Triggers execute automatically
- BEFORE/AFTER timing
- NEW/OLD for row values
- Useful for audit trails

---

## Best Practices

### Database Design

- **Normalization**: Normalize to reduce redundancy
- **Indexes**: Index frequently queried columns
- **Constraints**: Use constraints for data integrity
- **Naming Conventions**: Consistent naming
- **Documentation**: Document schema

### Query Performance

- **Use Indexes**: Index WHERE and JOIN columns
- **Avoid SELECT \***: Select only needed columns
- **Limit Results**: Use LIMIT for large result sets
- **Explain Plans**: Use EXPLAIN to analyze queries
- **Avoid Functions in WHERE**: Can prevent index usage

### Security

- **Parameterized Queries**: Prevent SQL injection
- **Least Privilege**: Grant minimum required permissions
- **Encryption**: Encrypt sensitive data
- **Backups**: Regular backups
- **Audit Logs**: Track database changes

---

## Common Patterns

### Pagination

```sql
SELECT * FROM employees
ORDER BY employee_id
LIMIT 10 OFFSET 20;
```

### Top N per Group

```sql
SELECT * FROM (
    SELECT *,
        ROW_NUMBER() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rn
    FROM employees
) ranked
WHERE rn <= 3;
```

### Recursive Queries (CTE)

```sql
WITH RECURSIVE employee_hierarchy AS (
    SELECT employee_id, manager_id, 1 AS level
    FROM employees WHERE manager_id IS NULL
    UNION ALL
    SELECT e.employee_id, e.manager_id, eh.level + 1
    FROM employees e
    JOIN employee_hierarchy eh ON e.manager_id = eh.employee_id
)
SELECT * FROM employee_hierarchy;
```

---

## Resources

### Official Documentation

- **SQL Standard**: ISO/IEC 9075
- **PostgreSQL Documentation**: https://www.postgresql.org/docs/
- **MySQL Documentation**: https://dev.mysql.com/doc/
- **SQL Server Documentation**: https://docs.microsoft.com/sql/

### Learning Resources

- **SQL Tutorial**: https://www.w3schools.com/sql/
- **SQLBolt**: Interactive SQL tutorial
- **Mode Analytics SQL Tutorial**: https://mode.com/sql-tutorial/

### Community

- **Stack Overflow**: Tag: sql
- **Database Administrators Stack Exchange**: https://dba.stackexchange.com/
- **r/SQL**: Reddit community

### Tools

- **MySQL**: Open-source relational database
- **PostgreSQL**: Advanced open-source database
- **SQLite**: Lightweight embedded database
- **pgAdmin**: PostgreSQL administration tool
- **MySQL Workbench**: MySQL administration tool

---

