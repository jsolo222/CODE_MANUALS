# COBOL - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Program Structure & Divisions](#program-structure--divisions)
4. [Data Types & Picture Clauses](#data-types--picture-clauses)
5. [Control Flow](#control-flow)
6. [File Processing](#file-processing)
7. [String Manipulation](#string-manipulation)
8. [Tables & Arrays](#tables--arrays)
9. [Subroutines & Functions](#subroutines--functions)
10. [Database Access](#database-access)
11. [Modern COBOL Features](#modern-cobol-features)
12. [Best Practices](#best-practices)
13. [Common Patterns](#common-patterns)
14. [Resources](#resources)

---

## Introduction

### What is COBOL?

COBOL (Common Business-Oriented Language) is a high-level programming language designed for business applications. Developed in 1959, COBOL has been used extensively in enterprise systems, particularly in banking, finance, insurance, and government sectors. Despite its age, COBOL remains critical infrastructure, processing trillions of dollars in transactions daily.

### Why Learn COBOL?

COBOL is valuable for:

1. **Legacy Systems**: Maintain and modernize critical business systems
2. **Financial Sector**: Powers banking, insurance, and financial transactions
3. **Mainframe Systems**: Essential for mainframe programming
4. **High Demand**: Shortage of COBOL programmers, high-paying opportunities
5. **Stability**: Long-term career stability in maintaining legacy systems
6. **Modern Features**: Modern COBOL includes object-oriented features
7. **Business Logic**: Excellent for business data processing
8. **Critical Infrastructure**: Many mission-critical systems still use COBOL

### Key Features

- **English-Like Syntax**: Readable, self-documenting code
- **Fixed Format**: Column-based source format (free format also available)
- **Business Focus**: Designed for business data processing
- **File Processing**: Excellent file handling capabilities
- **Decimal Arithmetic**: Precise decimal calculations for financial data
- **Divisions**: Structured program organization (Identification, Environment, Data, Procedure)
- **Modern Extensions**: Object-oriented features in modern COBOL

---

## Getting Started

### What is COBOL?

COBOL is designed for business data processing. It's widely used in financial systems and mainframe applications.

### Tools

- **GnuCOBOL**: Open-source COBOL compiler
- **Micro Focus Visual COBOL**: Commercial COBOL development
- **IBM COBOL**: Mainframe COBOL compiler

### Your First COBOL Program

**Code:**
```cobol
IDENTIFICATION DIVISION.
PROGRAM-ID. HELLO-WORLD.

DATA DIVISION.
WORKING-STORAGE SECTION.
01 WS-MESSAGE PIC X(30) VALUE 'HELLO, WORLD FROM COBOL!'.

PROCEDURE DIVISION.
MAIN-PROCEDURE.
    DISPLAY WS-MESSAGE.
    STOP RUN.
```

---

## Program Structure & Divisions

### Overview

COBOL programs are organized into four divisions: Identification, Environment, Data, and Procedure. This structure is fundamental to COBOL.

### Key Concepts

- **IDENTIFICATION DIVISION**: Program identification
- **ENVIRONMENT DIVISION**: Hardware and file environment
- **DATA DIVISION**: Data definitions
- **PROCEDURE DIVISION**: Program logic
- **Sections**: Within divisions for organization

### Program Structure

**What this demonstrates:** Basic COBOL program structure with all four divisions.

**Code:**
```cobol
IDENTIFICATION DIVISION.
PROGRAM-ID. HELLO-WORLD.
AUTHOR. COMMANDER.
DATE-WRITTEN. 2024-12-30.

ENVIRONMENT DIVISION.
CONFIGURATION SECTION.
SOURCE-COMPUTER. IBM-PC.
OBJECT-COMPUTER. IBM-PC.

INPUT-OUTPUT SECTION.
FILE-CONTROL.
* No files used in this simple example

DATA DIVISION.
FILE SECTION.
* No files defined

WORKING-STORAGE SECTION.
01 WS-MESSAGE PIC X(30) VALUE 'HELLO, WORLD FROM COBOL!'.

PROCEDURE DIVISION.
MAIN-PROCEDURE.
    DISPLAY WS-MESSAGE.
    STOP RUN.
```

**Explanation:**
- IDENTIFICATION DIVISION: Program metadata
- ENVIRONMENT DIVISION: System environment
- DATA DIVISION: Data definitions (FILE SECTION, WORKING-STORAGE)
- PROCEDURE DIVISION: Executable code
- Paragraphs: Named sections of code
- STOP RUN: End program execution

**Key Takeaways:**
- Four divisions structure COBOL programs
- DATA DIVISION defines all data
- PROCEDURE DIVISION contains logic
- Use meaningful paragraph names

---

## Data Types & Picture Clauses

### Overview

COBOL uses Picture (PIC) clauses to define data types and formats. Understanding PIC clauses is essential for COBOL programming.

### Key Concepts

- **PIC 9**: Numeric digits
- **PIC X**: Alphanumeric characters
- **PIC A**: Alphabetic only
- **PIC S**: Signed number
- **PIC V**: Implied decimal point
- **COMP**: Binary storage
- **COMP-3**: Packed decimal
- **Level Numbers**: 01-49 for data hierarchy

### Data Types

**What this demonstrates:** COBOL data types and Picture clauses.

**Code:**
```cobol
DATA DIVISION.
WORKING-STORAGE SECTION.

* NUMERIC DATA TYPES
01 WS-INTEGER PIC 9(5).  * 5 digits, range: 00000-99999
01 WS-SIGNED-NUMBER PIC S9(5).  * Signed number
01 WS-DECIMAL PIC 9(5)V99.  * 99999.99 (V = implied decimal)
01 WS-COMP-NUMBER PIC 9(5) COMP.  * Binary storage
01 WS-COMP-3-NUMBER PIC 9(5) COMP-3.  * Packed decimal

* ALPHANUMERIC DATA TYPES
01 WS-NAME PIC X(30).  * Alphanumeric
01 WS-ADDRESS PIC A(50).  * Alphabetic only

* EDITED PICTURE CLAUSES
01 WS-EDITED-NUMBER PIC ZZZ,ZZ9.99.  * Suppress leading zeros
01 WS-CURRENCY PIC $$$,$$$,$$9.99.  * Currency format
01 WS-CREDIT-BALANCE PIC $$$,$$9.99CR.  * Credit indicator

* LEVEL NUMBERS AND GROUPS
01 WS-EMPLOYEE-RECORD.
   05 WS-EMP-ID PIC 9(6).
   05 WS-EMP-NAME PIC X(30).
   05 WS-EMP-SALARY PIC 9(7)V99.
   05 WS-EMP-ADDRESS.
       10 WS-STREET PIC X(30).
       10 WS-CITY PIC X(20).
       10 WS-STATE PIC XX.
       10 WS-ZIP PIC 9(5).

* CONDITION NAMES (88 LEVEL)
01 WS-STATUS PIC X.
   88 STATUS-ACTIVE VALUE 'A'.
   88 STATUS-INACTIVE VALUE 'I'.
   88 STATUS-PENDING VALUE 'P'.
```

**Explanation:**
- PIC 9: Numeric digits
- PIC X: Alphanumeric characters
- PIC A: Alphabetic only
- PIC S: Signed numbers
- PIC V: Implied decimal point
- COMP: Binary storage (efficient)
- COMP-3: Packed decimal (2 digits/byte)
- Level numbers: 01-49 for hierarchy
- Condition names: 88 level for meaningful values

**Key Takeaways:**
- Use PIC to define data format
- COMP/COMP-3 for efficient numeric storage
- Level numbers create data hierarchy
- Condition names (88 level) improve readability

---

## Control Flow

### Overview

COBOL uses IF-ELSE, EVALUATE, and PERFORM for control flow. Understanding these constructs is essential for program logic.

### Key Concepts

- **IF-ELSE**: Conditional execution
- **EVALUATE**: Case/switch-like construct
- **PERFORM**: Loop and subroutine call
- **Nested IF**: Multiple conditions
- **Compound Conditions**: AND, OR operators

### Control Flow

**What this demonstrates:** COBOL control flow statements.

**Code:**
```cobol
* IF-ELSE
IF WS-AGE >= 18
    DISPLAY 'ADULT'
ELSE
    DISPLAY 'MINOR'
END-IF.

* NESTED IF
IF WS-AGE >= 18
    IF WS-AGE < 65
        DISPLAY 'WORKING AGE'
    ELSE
        DISPLAY 'RETIREE'
    END-IF
ELSE
    DISPLAY 'MINOR'
END-IF.

* COMPOUND CONDITIONS
IF WS-AGE > 18 AND WS-AGE < 65
    DISPLAY 'WORKING AGE'
END-IF.

* EVALUATE (SWITCH/CASE)
EVALUATE WS-GRADE
    WHEN 'A'
        DISPLAY 'EXCELLENT'
    WHEN 'B'
        DISPLAY 'GOOD'
    WHEN 'C'
        DISPLAY 'AVERAGE'
    WHEN OTHER
        DISPLAY 'INVALID GRADE'
END-EVALUATE.

* EVALUATE WITH RANGES
EVALUATE WS-AGE
    WHEN 0 THRU 12
        DISPLAY 'CHILD'
    WHEN 13 THRU 17
        DISPLAY 'TEENAGER'
    WHEN 18 THRU 64
        DISPLAY 'ADULT'
    WHEN OTHER
        DISPLAY 'SENIOR'
END-EVALUATE.

* PERFORM LOOP
PERFORM VARYING WS-COUNTER FROM 1 BY 1
    UNTIL WS-COUNTER > 10
    DISPLAY 'COUNTER: ' WS-COUNTER
END-PERFORM.

* PERFORM CALLING PARAGRAPH
PERFORM PROCESS-RECORD 10 TIMES.

PERFORM PROCESS-RECORD
    VARYING WS-COUNTER FROM 1 BY 1
    UNTIL WS-COUNTER > 10.
```

**Explanation:**
- IF-ELSE: Conditional execution
- Nested IF: Multiple levels of conditions
- Compound: AND, OR operators
- EVALUATE: Multi-way selection (case/switch)
- PERFORM: Loop and subroutine call
- VARYING: Loop with counter
- WHEN OTHER: Default case

**Key Takeaways:**
- Use IF-ELSE for conditionals
- Use EVALUATE for multi-way selection
- PERFORM for loops and subroutines
- Always include WHEN OTHER in EVALUATE

---

## File Processing

### Overview

COBOL excels at file processing. It supports sequential, indexed, and relative file organizations.

### Key Concepts

- **Sequential Files**: Sequential access
- **Indexed Files**: Key-based access
- **Relative Files**: Relative record number access
- **OPEN**: Open file for processing
- **READ**: Read record
- **WRITE**: Write record
- **REWRITE**: Update existing record
- **DELETE**: Delete record
- **CLOSE**: Close file

### File Processing

**What this demonstrates:** Sequential and indexed file operations.

**Code:**
```cobol
ENVIRONMENT DIVISION.
INPUT-OUTPUT SECTION.
FILE-CONTROL.
    SELECT EMPLOYEE-FILE
        ASSIGN TO 'EMPLOYEE.DAT'
        ORGANIZATION IS SEQUENTIAL
        ACCESS MODE IS SEQUENTIAL
        FILE STATUS IS WS-FILE-STATUS.
    
    SELECT CUSTOMER-FILE
        ASSIGN TO 'CUSTOMER.IDX'
        ORGANIZATION IS INDEXED
        ACCESS MODE IS DYNAMIC
        RECORD KEY IS CUST-ID
        FILE STATUS IS WS-CUST-STATUS.

DATA DIVISION.
FILE SECTION.
FD EMPLOYEE-FILE.
01 EMPLOYEE-RECORD.
   05 EMP-ID PIC 9(6).
   05 EMP-NAME PIC X(30).
   05 EMP-SALARY PIC 9(7)V99.

WORKING-STORAGE SECTION.
01 WS-FILE-STATUS PIC XX.
   88 WS-FILE-SUCCESS VALUE '00'.
   88 WS-FILE-EOF VALUE '10'.
   01 WS-EOF-FLAG PIC X VALUE 'N'.
   88 END-OF-FILE VALUE 'Y'.

PROCEDURE DIVISION.
* SEQUENTIAL FILE PROCESSING
OPEN INPUT EMPLOYEE-FILE.
IF NOT WS-FILE-SUCCESS
    DISPLAY 'ERROR OPENING FILE'
    STOP RUN
END-IF.

PERFORM UNTIL END-OF-FILE
    READ EMPLOYEE-FILE
        AT END
            SET END-OF-FILE TO TRUE
        NOT AT END
            DISPLAY EMP-ID ' ' EMP-NAME
    END-READ
END-PERFORM.

CLOSE EMPLOYEE-FILE.

* INDEXED FILE OPERATIONS
OPEN I-O CUSTOMER-FILE.

* WRITE NEW RECORD
MOVE 12345678 TO CUST-ID.
MOVE 'JOHN DOE' TO CUST-NAME.
WRITE CUSTOMER-RECORD
    INVALID KEY
        DISPLAY 'DUPLICATE RECORD'
    NOT INVALID KEY
        DISPLAY 'RECORD WRITTEN'
END-WRITE.

* READ BY PRIMARY KEY
MOVE 12345678 TO CUST-ID.
READ CUSTOMER-FILE
    INVALID KEY
        DISPLAY 'NOT FOUND'
    NOT INVALID KEY
        DISPLAY CUST-NAME
END-READ.

* UPDATE RECORD
REWRITE CUSTOMER-RECORD
    INVALID KEY
        DISPLAY 'UPDATE FAILED'
END-REWRITE.

* DELETE RECORD
DELETE CUSTOMER-FILE
    INVALID KEY
        DISPLAY 'DELETE FAILED'
END-DELETE.

CLOSE CUSTOMER-FILE.
```

**Explanation:**
- FILE-CONTROL: Define files in ENVIRONMENT DIVISION
- ORGANIZATION: Sequential, Indexed, Relative
- ACCESS MODE: Sequential, Random, Dynamic
- OPEN: Open file (INPUT, OUTPUT, I-O, EXTEND)
- READ: Read record (AT END clause)
- WRITE: Write record (INVALID KEY clause)
- REWRITE: Update existing record
- DELETE: Delete record
- FILE STATUS: Two-character status code

**Key Takeaways:**
- Define files in FILE-CONTROL
- Check FILE STATUS after operations
- Use AT END for sequential files
- Use INVALID KEY for indexed files

---

## String Manipulation

### Overview

COBOL provides STRING, UNSTRING, and INSPECT for string manipulation. These are essential for text processing.

### Key Concepts

- **STRING**: Concatenate strings
- **UNSTRING**: Split strings
- **INSPECT**: Replace characters, count occurrences
- **DELIMITED BY**: Delimiter specification
- **POINTER**: Track position

### String Operations

**What this demonstrates:** String manipulation operations.

**Code:**
```cobol
* STRING CONCATENATION
STRING WS-FIRST-NAME DELIMITED BY SPACE
       ' ' DELIMITED BY SIZE
       WS-LAST-NAME DELIMITED BY SPACE
       INTO WS-FULL-NAME
END-STRING.

* UNSTRING (SPLIT)
UNSTRING WS-SOURCE
    DELIMITED BY SPACE
    INTO WS-FIRST-PART
         WS-SECOND-PART
END-UNSTRING.

* INSPECT REPLACING
INSPECT WS-TEXT REPLACING ALL 'OLD' BY 'NEW'.

* INSPECT TALLYING (COUNT)
INSPECT WS-TEXT TALLYING WS-COUNT
    FOR ALL 'A'.
```

**Explanation:**
- STRING: Concatenate strings
- UNSTRING: Split strings by delimiter
- INSPECT REPLACING: Replace characters
- INSPECT TALLYING: Count occurrences
- DELIMITED BY: Specify delimiter
- POINTER: Track position in string

**Key Takeaways:**
- STRING for concatenation
- UNSTRING for splitting
- INSPECT for replacement and counting
- Always use END-STRING/END-UNSTRING

---

## Tables & Arrays

### Overview

COBOL uses OCCURS clause to define tables (arrays). Tables can be one-dimensional or multi-dimensional.

### Key Concepts

- **OCCURS**: Define array/table
- **INDEXED BY**: Use index instead of subscript
- **SEARCH**: Sequential search
- **SEARCH ALL**: Binary search (sorted table)
- **SET**: Manipulate index
- **Subscript**: Numeric position

### Tables & Arrays

**What this demonstrates:** Working with tables and arrays.

**Code:**
```cobol
* SIMPLE TABLE
01 WS-SALES-TABLE.
   05 WS-SALES OCCURS 12 TIMES PIC 9(7)V99.

* TABLE WITH INDEXED BY
01 WS-EMPLOYEE-TABLE.
   05 WS-EMPLOYEE OCCURS 100 TIMES
      INDEXED BY EMP-IDX.
      10 WS-EMP-ID PIC 9(6).
      10 WS-EMP-NAME PIC X(30).
      10 WS-EMP-SALARY PIC 9(7)V99.

* MULTI-DIMENSIONAL TABLE
01 WS-MATRIX.
   05 WS-ROW OCCURS 10 TIMES
      INDEXED BY ROW-IDX.
      10 WS-COL OCCURS 10 TIMES
         INDEXED BY COL-IDX
         PIC 9(3).

* ACCESSING TABLE ELEMENTS
* Using subscript
MOVE 5000.00 TO WS-SALES(1).
ADD WS-SALES(1) TO WS-TOTAL.

* Using index
SET EMP-IDX TO 1.
MOVE 123456 TO WS-EMP-ID(EMP-IDX).

* SEARCH (LINEAR)
SET PROD-IDX TO 1.
SEARCH WS-PRODUCT
    AT END
        DISPLAY 'NOT FOUND'
    WHEN WS-PROD-CODE(PROD-IDX) = WS-SEARCH-CODE
        DISPLAY 'FOUND'
END-SEARCH.

* SEARCH ALL (BINARY - REQUIRES SORTED TABLE)
SEARCH ALL WS-SORTED-ITEM
    AT END
        DISPLAY 'NOT FOUND'
    WHEN WS-ITEM-CODE(SORT-IDX) = 12345
        DISPLAY 'FOUND'
END-SEARCH.
```

**Explanation:**
- OCCURS: Define array/table
- INDEXED BY: Use index for efficient access
- Subscript: Numeric position (1, 2, 3...)
- Index: Named index (SET to manipulate)
- SEARCH: Sequential search
- SEARCH ALL: Binary search (sorted table)
- Multi-dimensional: Nested OCCURS

**Key Takeaways:**
- Use OCCURS to define tables
- INDEXED BY for efficient access
- SEARCH ALL for sorted tables
- Use SET to manipulate indexes

---

## Subroutines & Functions

### Overview

COBOL uses CALL statement for subprograms. Programs can call other programs with parameters.

### Key Concepts

- **CALL**: Call subprogram
- **USING**: Pass parameters
- **BY REFERENCE**: Parameter by reference (default)
- **BY CONTENT**: Parameter by value
- **LINKAGE SECTION**: Parameters in subprogram
- **EXIT PROGRAM**: Return from subprogram

### Subroutines & Functions

**What this demonstrates:** Calling subprograms.

**Code:**
```cobol
* MAIN PROGRAM
DATA DIVISION.
WORKING-STORAGE SECTION.
01 WS-NUM1 PIC 9(5) VALUE 100.
01 WS-NUM2 PIC 9(5) VALUE 50.
01 WS-RESULT PIC 9(6).

PROCEDURE DIVISION.
MAIN-PROCEDURE.
    CALL 'SUBPROG1' USING WS-NUM1 WS-NUM2 WS-RESULT.
    DISPLAY 'RESULT: ' WS-RESULT.
    STOP RUN.

* SUBPROGRAM
IDENTIFICATION DIVISION.
PROGRAM-ID. SUBPROG1.

DATA DIVISION.
LINKAGE SECTION.
01 LS-NUM1 PIC 9(5).
01 LS-NUM2 PIC 9(5).
01 LS-RESULT PIC 9(6).

PROCEDURE DIVISION USING LS-NUM1 LS-NUM2 LS-RESULT.
    ADD LS-NUM1 TO LS-NUM2 GIVING LS-RESULT.
    EXIT PROGRAM.

* CALL BY REFERENCE vs BY CONTENT
* BY REFERENCE - CHANGES AFFECT CALLER
CALL 'SUBPROG2' USING BY REFERENCE WS-VALUE.

* BY CONTENT - CHANGES DON'T AFFECT CALLER
CALL 'SUBPROG2' USING BY CONTENT WS-VALUE.
```

**Explanation:**
- CALL: Call another program
- USING: Pass parameters
- BY REFERENCE: Default, changes affect caller
- BY CONTENT: By value, changes don't affect caller
- LINKAGE SECTION: Parameters in subprogram
- USING in PROCEDURE DIVISION: Receive parameters
- EXIT PROGRAM: Return from subprogram

**Key Takeaways:**
- CALL to invoke subprograms
- LINKAGE SECTION for parameters
- BY REFERENCE (default) vs BY CONTENT
- EXIT PROGRAM to return

---

## Sort and Merge

### Overview

COBOL provides built-in SORT and MERGE capabilities for sorting files and merging sorted files.

### Key Concepts

- **SORT**: Sort file records
- **MERGE**: Merge sorted files
- **USING**: Input file
- **GIVING**: Output file
- **INPUT PROCEDURE**: Custom input selection
- **OUTPUT PROCEDURE**: Custom output processing

### Sort and Merge

**What this demonstrates:** Sorting and merging files.

**Code:**
```cobol
ENVIRONMENT DIVISION.
INPUT-OUTPUT SECTION.
FILE-CONTROL.
    SELECT INPUT-FILE ASSIGN TO 'INPUT.DAT'.
    SELECT OUTPUT-FILE ASSIGN TO 'OUTPUT.DAT'.
    SELECT SORT-WORK ASSIGN TO 'SORTWORK.TMP'.

DATA DIVISION.
FILE SECTION.
FD INPUT-FILE.
01 INPUT-RECORD.
   05 IN-ID PIC 9(6).
   05 IN-NAME PIC X(30).
   05 IN-AMOUNT PIC 9(7)V99.

FD OUTPUT-FILE.
01 OUTPUT-RECORD.
   05 OUT-ID PIC 9(6).
   05 OUT-NAME PIC X(30).
   05 OUT-AMOUNT PIC 9(7)V99.

SD SORT-WORK.
01 SORT-RECORD.
   05 SORT-ID PIC 9(6).
   05 SORT-NAME PIC X(30).
   05 SORT-AMOUNT PIC 9(7)V99.

PROCEDURE DIVISION.
* SIMPLE SORT
SORT SORT-WORK
    ON ASCENDING KEY SORT-AMOUNT
    USING INPUT-FILE
    GIVING OUTPUT-FILE.

* SORT WITH INPUT/OUTPUT PROCEDURES
SORT SORT-WORK
    ON DESCENDING KEY SORT-ID
    INPUT PROCEDURE IS 100-SELECT-RECORDS
    OUTPUT PROCEDURE IS 200-WRITE-SORTED.

* MERGE STATEMENT
MERGE MERGE-WORK
    ON ASCENDING KEY MERGE-KEY
    USING FILE1 FILE2
    GIVING OUTPUT-FILE.
```

**Explanation:**
- SORT: Sort file records
- SD: Sort file description
- ON ASCENDING/DESCENDING KEY: Sort key
- USING: Input file
- GIVING: Output file
- INPUT PROCEDURE: Custom input logic
- OUTPUT PROCEDURE: Custom output logic
- MERGE: Merge sorted files

**Key Takeaways:**
- SORT for sorting files
- MERGE for merging sorted files
- Use INPUT/OUTPUT PROCEDURES for custom logic
- SD for sort work files

---

## Copy Statement and Copybooks

### Overview

COBOL COPY statement includes external code (copybooks). Copybooks enable code reusability.

### Key Concepts

- **COPY**: Include copybook
- **Copybook**: External code file
- **REPLACING**: Text replacement in copybook
- **Code Reusability**: Share common definitions

### Copy Statement

**What this demonstrates:** Using COPY statement.

**Code:**
```cobol
* COPYBOOK: EMPLOYEE-RECORD.CPY
*    05 EMP-ID PIC 9(6).
*    05 EMP-NAME PIC X(30).
*    05 EMP-SALARY PIC 9(7)V99.
*    05 EMP-DEPT PIC X(20).

* USING COPYBOOK IN PROGRAM
DATA DIVISION.
WORKING-STORAGE SECTION.
01 WS-EMPLOYEE-RECORD.
    COPY EMPLOYEE-RECORD.

* COPY WITH REPLACING
COPY EMPLOYEE-RECORD
    REPLACING ==EMP== BY ==CUST==.
```

**Explanation:**
- COPY: Include copybook file
- Copybook: External .CPY file
- REPLACING: Text substitution
- Code reuse: Share definitions
- Common use: Record layouts, constants

**Key Takeaways:**
- COPY for code reuse
- Copybooks for shared definitions
- REPLACING for customization
- Common for record layouts

---

## Report Writer

### Overview

COBOL Report Writer automates report generation with headers, detail lines, and footers.

### Key Concepts

- **REPORT SECTION**: Define report
- **RD**: Report description
- **CONTROLS**: Control breaks
- **TYPE**: Line types (HEADING, DETAIL, FOOTING)
- **GENERATE**: Generate report lines
- **INITIATE/TERMINATE**: Start/end report

### Report Writer

**What this demonstrates:** Creating reports with Report Writer.

**Code:**
```cobol
ENVIRONMENT DIVISION.
INPUT-OUTPUT SECTION.
FILE-CONTROL.
    SELECT INPUT-FILE ASSIGN TO 'INPUT.DAT'.
    SELECT REPORT-FILE ASSIGN TO 'REPORT.TXT'
        REPORT IS SALES-REPORT.

DATA DIVISION.
FILE SECTION.
FD INPUT-FILE.
01 INPUT-RECORD.
   05 REGION PIC X(20).
   05 SALESMAN-NAME PIC X(30).
   05 SALE-AMOUNT PIC 9(7)V99.

FD REPORT-FILE.
01 REPORT-LINE PIC X(132).

REPORT SECTION.
RD SALES-REPORT
    CONTROLS ARE FINAL, REGION
    PAGE LIMIT IS 60 LINES.

01 TYPE IS PAGE HEADING.
   05 LINE NUMBER 1.
      10 COLUMN 30 PIC X(20)
         VALUE 'SALES REPORT'.

01 TYPE IS CONTROL HEADING REGION.
   05 LINE NUMBER PLUS 2.
      10 COLUMN 1 PIC X(8) VALUE 'REGION: '.
      10 COLUMN 10 PIC X(20) SOURCE REGION.

01 DETAIL-LINE TYPE IS DETAIL.
   05 LINE NUMBER PLUS 1.
      10 COLUMN 5 PIC X(30) SOURCE SALESMAN-NAME.
      10 COLUMN 40 PIC $$$,$$$,$$9.99 
         SOURCE SALE-AMOUNT.

01 TYPE IS CONTROL FOOTING REGION.
   05 LINE NUMBER PLUS 2.
      10 COLUMN 20 PIC X(15)
         VALUE 'REGION TOTAL: '.
      10 COLUMN 40 PIC $$$,$$$,$$9.99
         SUM SALE-AMOUNT.

PROCEDURE DIVISION.
OPEN INPUT INPUT-FILE.
OPEN OUTPUT REPORT-FILE.
INITIATE SALES-REPORT.

PERFORM UNTIL END-OF-FILE
    READ INPUT-FILE
        AT END
            SET END-OF-FILE TO TRUE
        NOT AT END
            GENERATE DETAIL-LINE
    END-READ
END-PERFORM.

TERMINATE SALES-REPORT.
CLOSE INPUT-FILE, REPORT-FILE.
```

**Explanation:**
- REPORT SECTION: Define report layout
- RD: Report description
- CONTROLS: Control break fields
- TYPE: Line type (HEADING, DETAIL, FOOTING)
- GENERATE: Generate report line
- INITIATE: Start report generation
- TERMINATE: End report generation
- SUM: Automatic totaling

**Key Takeaways:**
- Report Writer automates reports
- CONTROLS for control breaks
- GENERATE for detail lines
- INITIATE/TERMINATE for report lifecycle

---

## Modern COBOL Features

### Overview

Modern COBOL (COBOL 2002+) includes object-oriented features, XML/JSON support, and other modern capabilities.

### Key Concepts

- **Object-Oriented COBOL**: Classes and methods
- **XML Support**: XML GENERATE, XML PARSE
- **JSON Support**: JSON generation/parsing (recent)
- **Pointers**: Pointer data type
- **Dynamic Allocation**: Dynamic memory

### Modern COBOL Features

**What this demonstrates:** Modern COBOL features.

**Code:**
```cobol
* POINTERS (COBOL 2002)
DATA DIVISION.
WORKING-STORAGE SECTION.
01 WS-POINTER USAGE POINTER.

* XML SUPPORT
01 WS-XML-TEXT PIC X(1000).
01 WS-XML-DOCUMENT.
   05 CUSTOMER.
      10 CUST-ID PIC 9(8).
      10 CUST-NAME PIC X(40).

PROCEDURE DIVISION.
* XML GENERATION
XML GENERATE WS-XML-TEXT FROM WS-XML-DOCUMENT.

* XML PARSING
XML PARSE WS-XML-TEXT
    PROCESSING PROCEDURE IS XML-HANDLER.

* OBJECT-ORIENTED COBOL (COBOL 2002)
CLASS-ID. CUSTOMER-CLASS.

DATA DIVISION.
WORKING-STORAGE SECTION.
01 CUSTOMER-ID PIC 9(8).
01 CUSTOMER-NAME PIC X(40).

PROCEDURE DIVISION.

METHOD-ID. GET-CUSTOMER-NAME.
DATA DIVISION.
LINKAGE SECTION.
01 LS-NAME PIC X(40).

PROCEDURE DIVISION RETURNING LS-NAME.
    MOVE CUSTOMER-NAME TO LS-NAME.
    EXIT METHOD.
END METHOD GET-CUSTOMER-NAME.

END CLASS CUSTOMER-CLASS.
```

**Explanation:**
- Object-Oriented: Classes and methods (COBOL 2002)
- XML GENERATE: Create XML from data
- XML PARSE: Parse XML to data
- Pointers: Memory address type
- Methods: Functions within classes
- Modern: COBOL 2002 and later standards

**Key Takeaways:**
- Modern COBOL supports OOP
- XML generation and parsing available
- Pointers for advanced memory management
- Check compiler support for features

---

## Best Practices

### Naming Conventions

- **WS-**: Working Storage prefix
- **LS-**: Linkage Section prefix
- **FD-**: File Description prefix
- **Level Numbers**: 01-49 for hierarchy
- **Paragraph Names**: Use numeric prefixes (100-, 200-)
- **Meaningful Names**: Descriptive variable names

### Structure

- Use meaningful names
- Consistent indentation (4 spaces)
- Paragraph names with numeric prefixes
- EXIT paragraphs for each section
- Consistent error handling

### Error Handling

- Always check FILE STATUS
- Use ON SIZE ERROR for arithmetic
- Use INVALID KEY clauses
- Handle AT END conditions
- Display error messages

### Performance

- Use COMP-3 for calculations
- Use indexes instead of subscripts
- Use SEARCH ALL for sorted tables
- Minimize file I/O
- Optimize loops

---

## Common Patterns

### File Processing Pattern

```cobol
PERFORM 100-OPEN-FILES.
PERFORM 200-READ-FILE.
PERFORM 300-PROCESS-RECORDS
    UNTIL END-OF-FILE.
PERFORM 900-CLOSE-FILES.
```

### Error Handling Pattern

```cobol
READ FILE-NAME
    AT END
        SET END-OF-FILE TO TRUE
    NOT AT END
        PERFORM PROCESS-RECORD
END-READ.

IF NOT WS-FILE-SUCCESS
    DISPLAY 'ERROR: ' WS-FILE-STATUS
    PERFORM ERROR-HANDLER
END-IF.
```

---

## Resources

### Official Documentation

- **COBOL Standard**: ISO/IEC 1989
- **Micro Focus COBOL**: https://www.microfocus.com/
- **IBM COBOL**: https://www.ibm.com/products/cobol

### Learning Resources

- **COBOL Programming Course**: Various online courses
- **GnuCOBOL Documentation**: https://gnucobol.sourceforge.io/
- **Mainframe COBOL Tutorials**: IBM and vendor documentation

### Community

- **Stack Overflow**: Tag: cobol
- **COBOL Programming Forums**: Various forums
- **Mainframe Communities**: IBM and vendor communities

### Tools

- **GnuCOBOL**: Open-source COBOL compiler
- **Micro Focus Visual COBOL**: Commercial COBOL development
- **IBM COBOL**: Mainframe COBOL compiler
- **OpenCOBOL**: Open-source COBOL compiler (predecessor to GnuCOBOL)

---

