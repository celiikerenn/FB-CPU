# FB_CPU Verilog Project

## Overview

This project implements a simple **Accumulator-Based CPU** using Verilog HDL, designed for educational and testing purposes. The CPU fetches instructions from memory, decodes them, and executes basic arithmetic and control flow operations. A RAM module and testbench are provided to simulate different execution scenarios.

## Features

- Instruction Fetch-Decode-Execute pipeline (FSM-based)
- 10-bit data width and 6-bit addressing
- Synchronous RAM (64 x 10-bit)
- 3 test cases:
  - Addition
  - Multiplication
  - Loop-based accumulation

## Instruction Set

| Opcode | Mnemonic | Description                    |
|--------|----------|--------------------------------|
| `0000` | `LOD`    | ACC ← RAM[addr]                |
| `0001` | `STO`    | RAM[addr] ← ACC                |
| `0010` | `ADD`    | ACC ← ACC + RAM[addr]          |
| `0011` | `SUB`    | ACC ← ACC - RAM[addr]          |
| `0100` | `MUL`    | ACC ← ACC * RAM[addr]          |
| `0101` | `DIV`    | ACC ← ACC / RAM[addr]          |
| `0110` | `JMP`    | PC ← addr                      |
| `0111` | `JMZ`    | PC ← addr if ACC == 0          |
| `1000` | `HLT`    | Halt execution                 |

## Test Cases

### Test Case 1: Addition

```assembly
LOD 50     ; Load 5
ADD 51     ; Add 10
STO 52     ; Store result (15)
HLT

Test Case 2: Multiplication
assembly
LOD 50     ; Load 5
MUL 51     ; Multiply by 10
STO 52     ; Store result (50)
HLT

Test Case 3: Loop-based Accumulation
assembly
i = 0
temp = 0
while (i != end):
    temp += value
    i++
store temp to address 52
HLT

Modules
fb_cpu: The core CPU implementation.
blram: RAM with preloaded test data.
tb_fb_cpu: Testbench for simulating the CPU with RAM.
top: Wrapper module for FPGA I/O integration.

How to Simulate
Clone this repository.
Open in your Verilog simulator (ModelSim, Icarus Verilog, etc.).
Set the TEST_CASE parameter in tb_fb_cpu to 1, 2, or 3.
Run the simulation.
Observe results in memory (e.g., memory[52]).

├── fb_cpu.v         # CPU module
├── blram.v          # RAM module with test cases
├── tb_fb_cpu.v      # Testbench
├── top.v            # Top-level FPGA wrapper
├── README.md        # Project documentation

License

This project is released for educational and non-commercial use. Feel free to use, modify, and learn from it.
