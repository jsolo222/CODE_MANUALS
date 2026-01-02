# Verilog & SystemVerilog - COMPLETE PROGRAMMING GUIDE

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Basics & Module Structure](#basics--module-structure)
4. [Data Types](#data-types)
5. [Operators](#operators)
6. [Gate-Level Modeling](#gate-level-modeling)
7. [Behavioral Modeling](#behavioral-modeling)
8. [Dataflow Modeling](#dataflow-modeling)
9. [Tasks & Functions](#tasks--functions)
10. [Finite State Machines](#finite-state-machines)
11. [Testbenches](#testbenches)
12. [SystemVerilog Features](#systemverilog-features)
13. [Best Practices](#best-practices)
14. [Common Patterns](#common-patterns)
15. [Resources](#resources)

---

## Introduction

### What is Verilog?

Verilog is a hardware description language (HDL) used to model electronic systems at various levels of abstraction. Verilog is primarily used for designing and verifying digital circuits before they are manufactured. SystemVerilog is an extension of Verilog that adds additional features for design and verification.

### Why Learn Verilog?

Verilog is valuable for:

1. **FPGA Design**: Essential for Field-Programmable Gate Array development
2. **ASIC Design**: Used in Application-Specific Integrated Circuit development
3. **Hardware Verification**: Create testbenches for design verification
4. **Digital Design**: Model and design digital circuits
5. **Industry Standard**: IEEE 1364 standard, widely adopted
6. **Simulation**: Model and simulate digital systems
7. **Synthesis**: Convert descriptions to actual hardware
8. **Career Opportunities**: High demand in hardware design and verification

### Key Features

- **Multiple Abstraction Levels**: Gate, dataflow, behavioral modeling
- **Event-Driven Simulation**: Models hardware concurrency
- **Module-Based Design**: Hierarchical and modular design
- **Synthesizable Subset**: Can be synthesized to hardware
- **Testbenches**: Comprehensive verification capabilities
- **SystemVerilog Extensions**: Classes, interfaces, constraints, assertions

---

## Getting Started

### What is Verilog?

Verilog is a hardware description language for modeling digital circuits. SystemVerilog extends Verilog with additional features.

### Tools

- **Simulators**: ModelSim, VCS, Verilator, Icarus Verilog
- **Synthesis Tools**: Xilinx Vivado, Intel Quartus, Synopsys
- **Waveform Viewers**: GTKWave, ModelSim waveform viewer

### Your First Verilog Module

**Code:**
```verilog
module hello (
    input wire a,
    input wire b,
    output wire y
);

    assign y = a & b;

endmodule
```

---

## Basics & Module Structure

### Overview

Verilog modules are the basic building blocks. Modules define interfaces and behavior of digital circuits.

### Key Concepts

- **Module**: Basic building block
- **Ports**: Input/output declarations
- **Wire**: Connections (net type)
- **Reg**: Register type (holds value)
- **Continuous Assignment**: `assign` statement
- **Procedural Blocks**: `always`, `initial`

### Module Structure

**What this demonstrates:** Basic Verilog module structure.

**Code:**
```verilog
// Basic module structure
module basic_example (
    input wire clk,
    input wire reset,
    input wire [7:0] input_a,
    input wire [7:0] input_b,
    output reg [7:0] output_data
);

    // Internal wire/reg declarations
    wire [7:0] temp;
    
    // Continuous assignment
    assign temp = input_a & input_b;
    
    // Sequential logic
    always @(posedge clk or posedge reset) begin
        if (reset)
            output_data <= 8'h00;
        else
            output_data <= temp;
    end

endmodule
```

**Explanation:**
- `module`: Defines module
- Ports: Input/output declarations
- `wire`: Net type (for connections)
- `reg`: Register type (for variables)
- `assign`: Continuous assignment
- `always`: Procedural block
- `posedge`: Positive clock edge
- `<=`: Non-blocking assignment (sequential)

**Key Takeaways:**
- Modules define circuits
- `wire` for connections, `reg` for variables
- `assign` for combinational logic
- `always` blocks for sequential logic
- Use `<=` for sequential, `=` for combinational

---

## Data Types

### Overview

Verilog has net types (wire) and variable types (reg). Understanding data types is essential for hardware description.

### Key Concepts

- **Wire**: Net type (driven by continuous assignment)
- **Reg**: Variable type (holds value)
- **Integer**: 32-bit signed integer
- **Parameters**: Constants
- **Arrays**: Multi-dimensional arrays
- **Literals**: Binary, decimal, hex, octal

### Data Types

**What this demonstrates:** Verilog data types.

**Code:**
```verilog
module data_types_demo;

    // Net types (driven by continuous assignment)
    wire single_wire;
    wire [7:0] bus_wire;
    wire [0:7] bus_upward;  // Upward range
    
    // Register types (hold values)
    reg single_reg;
    reg [7:0] bus_reg;
    reg signed [7:0] signed_reg;
    
    // Integer (32-bit signed)
    integer int_var;
    
    // Parameters (constants)
    parameter WIDTH = 8;
    parameter DEPTH = 256;
    localparam LOCAL_CONST = 10;  // Local to module
    
    // Arrays
    reg [7:0] memory [0:255];     // Array of 8-bit regs
    wire [3:0] wire_array [0:15]; // Array of wires
    
    // Literals
    initial begin
        bus_reg = 8'b10101010;     // 8-bit binary
        bus_reg = 8'd170;          // 8-bit decimal
        bus_reg = 8'hAA;           // 8-bit hexadecimal
        bus_reg = 8'o252;          // 8-bit octal
        
        signed_reg = -8'd50;       // Negative
        bus_reg = 8'bxxxx_zzzz;    // X and Z
        bus_reg = 8'b1010_1010;    // Underscore for readability
    end

endmodule
```

**Explanation:**
- `wire`: Net type, driven by continuous assignment
- `reg`: Variable type, holds value
- `[7:0]`: Bit range (7 downto 0)
- `parameter`: Module parameter (constant)
- `localparam`: Local constant
- Arrays: `type [width] name [depth]`
- Literals: `size'base value` format

**Key Takeaways:**
- Use `wire` for connections
- Use `reg` for variables in always blocks
- `parameter` for constants
- Arrays: `type [width] name [depth]`
- Literals: `size'base value`

---

## Operators

### Overview

Verilog provides arithmetic, logical, bitwise, relational, and shift operators. Understanding operators is essential for expressions.

### Key Concepts

- **Arithmetic**: +, -, *, /, %, **
- **Bitwise**: &, |, ^, ~, ~&, ~|, ~^
- **Logical**: &&, ||, !
- **Relational**: ==, !=, <, >, <=, >=
- **Shift**: <<, >>, <<<, >>>
- **Concatenation**: { }

### Operators

**What this demonstrates:** Verilog operators.

**Code:**
```verilog
// Arithmetic operators
result_arith = a + b;      // Addition
result_arith = a - b;      // Subtraction
result_arith = a * b;      // Multiplication
result_arith = a / b;      // Division
result_arith = a % b;      // Modulo

// Bitwise operators
result_logic = a & b;      // AND
result_logic = a | b;      // OR
result_logic = a ^ b;      // XOR
result_logic = ~a;         // NOT

// Reduction operators (reduce to single bit)
result_compare = &a;       // AND all bits
result_compare = |a;       // OR all bits
result_compare = ^a;       // XOR all bits (parity)

// Logical operators (return 1 or 0)
result_compare = a && b;   // Logical AND
result_compare = a || b;   // Logical OR
result_compare = !a;       // Logical NOT

// Relational operators
result_compare = a == b;   // Equal
result_compare = a != b;   // Not equal
result_compare = a < b;    // Less than
result_compare = a > b;    // Greater than

// Shift operators
result_logic = a << 2;     // Shift left (fill with 0)
result_logic = a >> 2;     // Shift right (fill with 0)
result_logic = a <<< 2;    // Arithmetic shift left
result_logic = a >>> 2;    // Arithmetic shift right (sign extend)

// Concatenation
result_logic = {a[3:0], b[3:0]};  // Concatenate

// Replication
result_logic = {4{2'b10}};        // {10,10,10,10}

// Conditional (ternary)
result_logic = (a > b) ? a : b;   // Max
```

**Explanation:**
- Arithmetic: Standard math operations
- Bitwise: Operate on each bit
- Reduction: Reduce vector to single bit
- Logical: Return 1 or 0 (true/false)
- Relational: Comparison operators
- Shift: Logical (<<, >>) and arithmetic (<<<, >>>)
- Concatenation: `{}` operator
- Replication: `{count{value}}`

**Key Takeaways:**
- Use bitwise for bit operations
- Reduction operators for vector operations
- Logical operators for boolean logic
- Shift: Logical vs arithmetic
- Concatenation: `{}` operator

---

## Behavioral Modeling

### Overview

Behavioral modeling uses procedural blocks to describe circuit behavior. `always` blocks model sequential and combinational logic.

### Key Concepts

- **always Block**: Procedural block
- **initial Block**: Simulation-only initialization
- **Blocking Assignment**: `=` (combinational)
- **Non-Blocking Assignment**: `<=` (sequential)
- **Sensitivity List**: Triggers execution
- **Combinational vs Sequential**: Different coding styles

### Procedural Blocks

**What this demonstrates:** Using procedural blocks.

**Code:**
```verilog
// always block (combinational)
always @(*) begin
    // Sensitivity list with * (all inputs)
    data_out = data_in ^ 8'hFF;  // Blocking assignment
end

// always block (sequential)
always @(posedge clk) begin
    if (reset)
        data_out <= 8'h00;       // Non-blocking
    else
        data_out <= data_in;     // Non-blocking
end

// always block with async reset
always @(posedge clk or posedge reset) begin
    if (reset)
        data_out <= 8'h00;
    else
        data_out <= data_in;
end

// initial block (simulation only)
initial begin
    data_out = 8'h00;
    #10;  // Wait 10 time units
    data_out = 8'hFF;
end
```

**Explanation:**
- `always`: Procedural block (synthesizable)
- `initial`: Simulation-only initialization
- `@(*)`: Combinational sensitivity (all inputs)
- `@(posedge clk)`: Clocked logic
- `=`: Blocking assignment (combinational)
- `<=`: Non-blocking assignment (sequential)
- `#`: Delay (simulation only)

**Key Takeaways:**
- Use `always @(*)` for combinational
- Use `always @(posedge clk)` for sequential
- Use `=` for combinational, `<=` for sequential
- `initial` block is simulation-only

### Conditional Statements

**What this demonstrates:** Conditional statements in Verilog.

**Code:**
```verilog
// if-else
always @(*) begin
    if (sel == 2'b00)
        out = a;
    else if (sel == 2'b01)
        out = b;
    else
        out = c;
end

// case statement
always @(*) begin
    case (sel)
        2'b00: out = a;
        2'b01: out = b;
        2'b10: out = c;
        default: out = 8'h00;
    endcase
end

// casex (don't care matching)
always @(*) begin
    casex (sel)
        2'b0x: out = a;  // Match 00, 01
        2'b1x: out = b;  // Match 10, 11
        default: out = c;
    endcase
end
```

**Explanation:**
- `if-else`: Conditional execution
- `case`: Multi-way selection
- `default`: Default case (required)
- `casex`: Don't care matching
- Combinational: Use `always @(*)`

**Key Takeaways:**
- Use `if-else` for conditionals
- Use `case` for multi-way selection
- Always include `default` case
- Use `always @(*)` for combinational

---

## Flip-Flops and Registers

### Overview

Flip-flops and registers store state. They're fundamental for sequential circuits.

### Key Concepts

- **D Flip-Flop**: Stores one bit
- **Register**: Multiple flip-flops
- **Asynchronous Reset**: Reset independent of clock
- **Synchronous Reset**: Reset synchronized to clock
- **Enable**: Conditional update
- **Non-Blocking**: Use `<=` for sequential logic

### Flip-Flops

**What this demonstrates:** Creating flip-flops and registers.

**Code:**
```verilog
// D Flip-Flop with asynchronous reset
always @(posedge clk or posedge reset) begin
    if (reset)
        q <= 1'b0;
    else
        q <= d;
end

// D Flip-Flop with synchronous reset
always @(posedge clk) begin
    if (reset)
        q <= 1'b0;
    else
        q <= d;
end

// 8-bit register
always @(posedge clk or posedge reset) begin
    if (reset)
        reg_out <= 8'h00;
    else
        reg_out <= data;
end

// Register with enable
always @(posedge clk or posedge reset) begin
    if (reset)
        reg_out <= 8'h00;
    else if (enable)
        reg_out <= data;
end
```

**Explanation:**
- D Flip-Flop: Stores input on clock edge
- Asynchronous reset: In sensitivity list
- Synchronous reset: Only in clocked section
- Register: Vector of flip-flops
- Enable: Conditional update
- Non-blocking: Always use `<=` for sequential

**Key Takeaways:**
- Use `posedge clk` for clocked logic
- Asynchronous reset in sensitivity list
- Synchronous reset only in clocked section
- Always use `<=` for sequential logic

---

## Counters

### Overview

Counters are sequential circuits that count. They're common in digital design.

### Key Concepts

- **Up Counter**: Increments
- **Down Counter**: Decrements
- **Modulo Counter**: Wraps around
- **Enable**: Conditional counting
- **Reset**: Initialize counter

### Counters

**What this demonstrates:** Creating counters.

**Code:**
```verilog
// Up counter
always @(posedge clk or posedge reset) begin
    if (reset)
        counter <= 8'h00;
    else if (enable)
        counter <= counter + 1;
end

// Down counter
always @(posedge clk or posedge reset) begin
    if (reset)
        counter <= 8'hFF;
    else if (enable)
        counter <= counter - 1;
end

// Modulo counter (0 to 99)
always @(posedge clk or posedge reset) begin
    if (reset)
        counter <= 8'h00;
    else if (counter == 8'd99)
        counter <= 8'h00;
    else
        counter <= counter + 1;
end
```

**Explanation:**
- Up counter: Increments on clock
- Down counter: Decrements on clock
- Modulo: Wraps at maximum value
- Enable: Conditional counting
- Use non-blocking assignment

**Key Takeaways:**
- Use non-blocking assignment (`<=`)
- Modulo counters wrap at maximum
- Enable for conditional counting
- Reset initializes counter

---

## Finite State Machines

### Overview

Finite State Machines (FSMs) model sequential behavior with states and transitions. They're fundamental for control logic.

### Key Concepts

- **States**: Discrete states
- **Transitions**: State changes
- **Moore FSM**: Outputs depend only on state
- **Mealy FSM**: Outputs depend on state and inputs
- **State Register**: Stores current state
- **Next State Logic**: Determines next state

### Finite State Machines

**What this demonstrates:** Creating FSMs.

**Code:**
```verilog
// State encoding
localparam IDLE = 2'b00;
localparam RUNNING = 2'b01;
localparam COMPLETE = 2'b10;
localparam ERROR = 2'b11;

reg [1:0] state, next_state;

// State register (sequential)
always @(posedge clk or posedge reset) begin
    if (reset)
        state <= IDLE;
    else
        state <= next_state;
end

// Next state logic (combinational)
always @(*) begin
    next_state = state;  // Default
    case (state)
        IDLE:
            if (start)
                next_state = RUNNING;
        RUNNING:
            next_state = COMPLETE;
        COMPLETE:
            next_state = IDLE;
        default:
            next_state = IDLE;
    endcase
end

// Output logic (Moore - depends only on state)
always @(*) begin
    case (state)
        IDLE: done = 1'b0;
        RUNNING: done = 1'b0;
        COMPLETE: done = 1'b1;
        default: done = 1'b0;
    endcase
end
```

**Explanation:**
- State encoding: Use `localparam` for states
- State register: Clocked, stores current state
- Next state: Combinational logic
- Output logic: Combinational (Moore or Mealy)
- Moore: Outputs from state only
- Mealy: Outputs from state and inputs

**Key Takeaways:**
- Use `localparam` for state encoding
- Separate state register and next state logic
- Moore FSM: Outputs from state only
- Mealy FSM: Outputs from state and inputs

---

## Memory

### Overview

Memory elements store data. Verilog supports RAM, ROM, and other memory structures.

### Key Concepts

- **RAM**: Random Access Memory
- **ROM**: Read-Only Memory
- **Single-Port**: One read/write port
- **Dual-Port**: Two ports
- **Arrays**: Used to model memory

### Memory Elements

**What this demonstrates:** Creating memory elements.

**Code:**
```verilog
// RAM array
reg [7:0] memory [0:255];

// Single-port RAM
always @(posedge clk) begin
    if (we)
        memory[addr] <= data_in;
    data_out <= memory[addr];
end

// Dual-port RAM
reg [7:0] memory [0:255];
always @(posedge clk) begin
    if (we)
        memory[addr_a] <= data_in;
    data_out_a <= memory[addr_a];
end

always @(posedge clk) begin
    data_out_b <= memory[addr_b];
end

// ROM (initialized)
reg [7:0] rom [0:255];
initial begin
    $readmemh("rom_data.hex", rom);
end
```

**Explanation:**
- RAM: Read/write memory
- Arrays: `reg [width] name [depth]`
- Write enable: Control writes
- Address: Index into array
- ROM: Read-only (initialized)
- `$readmemh`: Initialize from file

**Key Takeaways:**
- Use arrays to model memory
- RAM: Writable memory
- ROM: Initialize with data
- Use `$readmemh` for initialization

---

## Module Instantiation

### Overview

Module instantiation enables hierarchical design. Modules can be instantiated multiple times.

### Key Concepts

- **Instantiation**: Create module instance
- **Port Map**: Connect ports
- **Named Association**: Explicit connections
- **Positional Association**: By position
- **Hierarchical**: Build larger designs

### Module Instantiation

**What this demonstrates:** Instantiating modules.

**Code:**
```verilog
// Module definition
module my_component (
    input clk,
    input [7:0] d,
    output reg [7:0] q
);
    always @(posedge clk)
        q <= d;
endmodule

// Top-level with instantiation
module top_level (
    input clk,
    input [7:0] input_data,
    output [7:0] output_data
);

    wire [7:0] intermediate;
    
    // Named association
    my_component u1 (
        .clk(clk),
        .d(input_data),
        .q(intermediate)
    );
    
    // Positional association
    my_component u2 (
        clk,
        intermediate,
        output_data
    );

endmodule
```

**Explanation:**
- Instantiation: Create module instance
- Named association: `.port(signal)` syntax
- Positional: By position order
- Hierarchical: Modules within modules
- Port map: Connect signals

**Key Takeaways:**
- Use named association (clearer)
- Positional by position order
- Hierarchical design with modules
- Port map connects signals

---

## Generate Statements

### Overview

Generate statements replicate logic. They're useful for parameterized designs.

### Key Concepts

- **Generate**: Replicate logic
- **For Generate**: Loop-based replication
- **If Generate**: Conditional replication
- **Case Generate**: Case-based replication
- **Parameters**: Use with generate

### Generate Statements

**What this demonstrates:** Using generate statements.

**Code:**
```verilog
// For generate
genvar i;
generate
    for (i = 0; i < 8; i = i + 1) begin : gen_loop
        assign out[i] = in[i] & enable[i];
    end
endgenerate

// Conditional generate
parameter USE_FEATURE = 1;
generate
    if (USE_FEATURE) begin
        // Feature included
    end else begin
        // Feature excluded
    end
endgenerate
```

**Explanation:**
- `generate`: Replicate logic
- `genvar`: Generate variable (for loops)
- For generate: Loop-based replication
- If generate: Conditional replication
- Useful: For parameterized designs

**Key Takeaways:**
- Use generate for replication
- `genvar` for generate loops
- For generate: Loop-based
- If generate: Conditional

---

## Tasks and Functions

### Overview

Tasks and functions enable code reuse. Functions return values, tasks perform operations.

### Key Concepts

- **Function**: Returns value (combinational)
- **Task**: Performs operation (can have timing)
- **Automatic**: Automatic storage (recursive)
- **Reusable**: Code reuse
- **Synthesis**: Functions are synthesizable

### Tasks and Functions

**What this demonstrates:** Using tasks and functions.

**Code:**
```verilog
// Function (returns value, combinational)
function [7:0] add_one;
    input [7:0] value;
    begin
        add_one = value + 1;
    end
endfunction

// Usage
wire [7:0] result;
assign result = add_one(8'd42);

// Task (can have timing)
task reset_system;
    begin
        reset <= 1'b1;
        #10;
        reset <= 1'b0;
    end
endtask

// Usage
initial begin
    reset_system;
end
```

**Explanation:**
- Function: Returns value, combinational
- Task: Performs operation, can have timing
- Function: Synthesizable
- Task: Usually simulation-only
- Automatic: For recursive calls

**Key Takeaways:**
- Functions return values
- Tasks perform operations
- Functions are synthesizable
- Tasks usually simulation-only

---

## Testbenches

### Overview

Testbenches verify designs through simulation. They provide stimulus and check responses.

### Key Concepts

- **Testbench**: Verification environment
- **Clock Generation**: Create clock signal
- **Stimulus**: Provide test inputs
- **Monitor**: Display values
- **No Ports**: Testbenches typically have no ports

### Testbenches

**What this demonstrates:** Creating testbenches.

**Code:**
```verilog
module testbench;

    // Testbench signals
    reg clk;
    reg reset;
    reg [7:0] data_in;
    wire [7:0] data_out;
    
    // Clock generation
    always begin
        clk = 0;
        #5;
        clk = 1;
        #5;
    end
    
    // Instantiate DUT (Device Under Test)
    my_module dut (
        .clk(clk),
        .reset(reset),
        .data_in(data_in),
        .data_out(data_out)
    );
    
    // Stimulus
    initial begin
        reset = 1;
        data_in = 8'h00;
        #20;
        
        reset = 0;
        data_in = 8'hAA;
        #20;
        
        $display("Data out: %h", data_out);
        
        $finish;
    end

endmodule
```

**Explanation:**
- Testbench: Verification environment
- Clock process: Generates clock signal
- Stimulus: Provides test inputs
- `$display`: Display values
- `$finish`: End simulation
- `#`: Delay

**Key Takeaways:**
- Generate clock with always block
- Use initial for stimulus
- `$display` for output
- `$finish` to end simulation

---

## SystemVerilog Features

### Overview

SystemVerilog extends Verilog with additional features for design and verification.

### Key Concepts

- **Interfaces**: Bundled port declarations
- **Classes**: Object-oriented programming
- **Assertions**: Property verification
- **Constraints**: Randomization constraints
- **Coverage**: Functional coverage
- **Enhancements**: Improved data types

### SystemVerilog Features

**What this demonstrates:** SystemVerilog enhancements.

**Code:**
```systemverilog
// Interface
interface bus_if;
    logic [7:0] data;
    logic valid;
    logic ready;
endinterface

// Using interface
module my_module (bus_if bus);
    assign bus.data = 8'hAA;
    assign bus.valid = 1'b1;
endmodule

// Always_comb (combinational)
always_comb begin
    out = a & b;
end

// Always_ff (flip-flop)
always_ff @(posedge clk) begin
    if (reset)
        q <= 0;
    else
        q <= d;
end

// Logic type (replaces wire/reg)
logic [7:0] data;

// Packed arrays
logic [7:0] [3:0] packed_array;  // 8 elements of 4 bits
```

**Explanation:**
- Interfaces: Bundle ports together
- Classes: OOP for verification
- Assertions: Property checking
- `always_comb`: Explicit combinational
- `always_ff`: Explicit flip-flop
- `logic`: Unified wire/reg type

**Key Takeaways:**
- Interfaces bundle ports
- `always_comb` for combinational
- `always_ff` for flip-flops
- `logic` replaces wire/reg

---

## Best Practices

### Coding Style

- **Naming**: Use descriptive names
- **Indentation**: Consistent formatting
- **Comments**: Document complex logic
- **Synthesis**: Write synthesizable code
- **Simulation**: Test thoroughly

### Synthesis Guidelines

- **Complete Cases**: Always include default in case
- **Avoid Latches**: Complete if-else statements
- **Reset Strategy**: Consistent reset approach
- **Clocking**: Use standard clocking patterns
- **State Machines**: Use parameter/localparam for states

### Verification

- **Testbenches**: Comprehensive test coverage
- **Stimulus**: Cover all cases
- **Waveforms**: Visualize signals
- **Assertions**: Use SystemVerilog assertions

---

## Common Patterns

### Clock Domain Crossing

```verilog
// Synchronizer
always @(posedge dest_clk) begin
    sync1 <= async_signal;
    sync2 <= sync1;
end
```

### Pipeline

```verilog
// Pipeline stage
always @(posedge clk) begin
    stage2 <= stage1;
    stage3 <= stage2;
end
```

---

## Resources

### Official Documentation

- **IEEE 1364**: Verilog HDL Standard
- **IEEE 1800**: SystemVerilog Standard
- **Verilog.org**: https://www.verilog.org/

### Learning Resources

- **ASIC World Verilog Tutorial**: http://www.asic-world.com/verilog/
- **Verilog HDL**: Various online tutorials
- **SystemVerilog Tutorial**: https://www.chipverify.com/systemverilog/systemverilog-tutorial

### Community

- **Stack Overflow**: Tag: verilog, systemverilog
- **r/FPGA**: Reddit community
- **Verification Academy**: https://verificationacademy.com/

### Tools

- **ModelSim**: Simulation tool
- **VCS**: Synopsys simulator
- **Vivado**: Xilinx FPGA tool suite
- **Quartus**: Intel (Altera) FPGA tool suite
- **Verilator**: Open-source Verilog simulator

---

