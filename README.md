# SINGLE-CYCLE RISC-V PROCESSOR

## Overview

This project implements a single-cycle RISC-V processor designed for the EN1640 Design of Computing Systems course at Brown University. The processor supports a comprehensive instruction set including arithmetic, logical, memory, branch, and jump operations.

## Features

- **Single-cycle execution** for all supported instructions
- **32-bit RISC-V architecture** with 32 general-purpose registers
- **Comprehensive instruction support** including R-type, I-type, S-type, B-type, U-type, and J-type instructions
- **Maximum clock frequency**: 70 MHz (factorial 6), 65 MHz (factorial 12)
- **FPGA implementation** with optimized design for timing performance

## Supported Instructions

### Arithmetic Operations
- `ADD` - Add registers
- `ADDI` - Add immediate
- `SUB` - Subtract registers
- `MUL` - Multiply registers

### Logical Operations
- `AND` - Bitwise AND
- `OR` - Bitwise OR
- `SLLI` - Shift left logical immediate

### Memory Operations
- `LW` - Load word from memory
- `SW` - Store word to memory

### Control Flow
- `BEQ` - Branch if equal
- `BNE` - Branch if not equal
- `JAL` - Jump and link
- `JALR` - Jump and link register

### System
- `HALT` - Stop execution (custom opcode: 11111111)

## Architecture Components

### Core Modules
1. **Control Unit** - Generates control signals for instruction execution
2. **ALU (Arithmetic Logic Unit)** - Performs arithmetic and logical operations
3. **Register File** - 32 general-purpose registers with stack pointer initialization
4. **Immediate Generator** - Extracts and sign-extends immediate values
5. **Program Counter** - Tracks instruction execution sequence
6. **Memory Unit** - 1024-byte data memory for load/store operations

### Key Design Features
- **Optimized immediate generation** - Bits are omitted during generation rather than shifted, improving timing
- **Phase-shifted RAM clocking** - Enables single-cycle memory access
- **Comprehensive testing** - All modules verified with ModelSim testbenches

## Performance Metrics

- **Resource Utilization**:
  - 629 ALMs (Adaptive Logic Modules)
  - 593 DLRs (Dedicated Logic Registers)
  - 2 DSPs (Digital Signal Processors)
  - 1 PLL (Phase-Locked Loop)

- **Clock Frequencies**:
  - Factorial 6: 70 MHz maximum
  - Factorial 12: 65 MHz maximum (reduced due to multiplication complexity)

## Test Programs

### 1. Factorial Program
Calculates factorial of a given number using recursive function calls with proper stack management.

### 2. Verification Program
Custom test program exercising all instruction types including:
- Register operations
- Memory access
- Branch conditions
- Jump instructions

## Getting Started

### Prerequisites
- Intel Quartus Prime (for FPGA synthesis)
- ModelSim (for simulation)
- Venus RISC-V simulator (for reference)
- Compatible FPGA board

### Setup Instructions
1. Extract the `.qar` file in Quartus Prime
2. Compile the project to generate the FPGA bitstream
3. Program the FPGA board
4. Load test programs into instruction memory
5. Monitor execution using In-System Memory Content Editor

### Running Test Programs
1. Convert assembly code to machine code using Venus
2. Load machine code into the instruction register array
3. Set appropriate clock frequency using PLL
4. Execute program and verify results in memory

## Verification

All modules have been thoroughly tested with:
- **Unit tests** for individual components
- **Integration tests** with complete programs
- **Timing analysis** for frequency optimization
- **Memory verification** using In-System Memory Content Editor

Expected results are documented in the project report with comparison to Venus simulator output.

## Performance Optimization

Key optimizations implemented:
- **Immediate value preprocessing** - Eliminates shifting delays
- **Phase-shifted memory clocking** - Enables single-cycle memory access
- **Streamlined ALU datapath** - Optimized for multiplication operations
- **Removal of debug circuitry** - Reduces footprint and improves timing

## Limitations

- **Single-cycle design** - No pipelining (by design requirement)
- **Limited instruction set** - Subset of full RISC-V specification
- **Fixed memory size** - 1024 bytes data memory
- **No cache** - Direct memory access only

## Future Enhancements

Potential improvements for extended versions:
- Pipeline implementation for higher performance
- Branch prediction for better control flow handling
- Cache memory for improved memory access
- Extended instruction set support
- Floating-point unit integration
