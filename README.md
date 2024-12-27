# RISC-V Single-Cycle Processor with CSR and 5-Stage Pipelined Processor

This repository contains the implementation of a RISC-V Single-Cycle Processor with CSR (Control and Status Register), which was later extended into a RISC-V 5-Stage Pipelined Processor. The project demonstrates the evolution from a basic single-cycle architecture to a high-performance pipelined architecture with CSR support.

## Features

### Single-Cycle Processor with CSR
- **Architecture:**
  - Executes all instructions in one clock cycle.
- **Control and Status Register (CSR):**
  - Implements system-level control, interrupts, and exception handling.
- **Instruction Set:**
  - Arithmetic, Logical, Load/Store, Branch, and CSR instructions.
- **Key Design:**
  - Simple architecture with a focus on control and CSR features.

### 5-Stage Pipelined Processor
- **Pipeline Stages:**
  - Instruction Fetch (IF)
  - Instruction Decode (ID)
  - Execute (EX)
  - Memory Access (MEM)
  - Write Back (WB)
- **Performance Features:**
  - Implements forwarding and stalls to handle data hazards.
  - Control hazards are managed using branch prediction and pipeline flushing.
- **CSR Integration:**
  - Retains CSR functionality in the pipelined architecture.
- **Enhanced Efficiency:**
  - Higher throughput compared to the single-cycle design.

## File Overview

### Core Components
- `processor.sv`: Top module for the processor.
- `alu.sv`: Arithmetic and Logic Unit (ALU) for executing instructions.
- `csr.sv`: Control and Status Registers for handling system-level operations.
- `controller.sv`: Central control unit for generating control signals.
- `data_memory.sv`: Module for accessing data memory.
- `instruction_memory.sv`: Instruction memory module for fetching instructions.
- `register_file.sv`: Module for storing and accessing general-purpose registers.

### Pipeline Buffers (For Pipelined Processor)
- `IR_buffer{1-5}.sv`: Instruction Register buffers for each pipeline stage.
- `controller_buffer{1-3}.sv`: Control signal buffers for pipeline stages.
- `ALU_buffer{1-2}.sv`: Buffers for ALU results between pipeline stages.
- `pc_buffer{1-3}.sv`: Buffers for program counter values across pipeline stages.

### Supporting Modules
- `branch_condition.sv`: Handles branch condition evaluation.
- `immediate_gen.sv`: Generates immediate values for instructions.
- `mux_to_alu.sv`: Multiplexer module to select ALU inputs.
- `pc_mux.sv`: Multiplexer module for program counter selection.
- `data_mem.sv`: Interface for memory access in the single-cycle processor.

### Testbenches
- `tb_processor.sv`: Testbench for verifying processor functionality.

## Instruction Set and Working

### Supported Instructions
- **Arithmetic and Logical Instructions:** ADD, SUB, AND, OR, XOR, SLT, etc.
- **Load/Store Instructions:** LB, LH, LW, SB, SH, SW, etc.
- **Branch Instructions:** BEQ, BNE, BLT, BGE, etc.
- **CSR Instructions:** CSRRW, CSRRS, CSRRC, MRET, etc.

### Functionality Overview
1. **Fetch:** Instruction is fetched from the instruction memory.
2. **Decode:** Instruction is decoded, and operands are read from the register file.
3. **Execute:** ALU performs the operation or evaluates branch conditions.
4. **Memory Access:** Data memory is accessed for load/store instructions.
5. **Write Back:** Results are written back to the register file or CSR.

## Simulation and Testing

1. **Clone the repository:**
   ```sh
   git clone https://github.com/kashifmuneer1085/Risc_V_5_stage_pipelined_Processor.git
   cd riscv-processor
   
2. **Compile and simulate using Questa Sim:**
    1. vlog ./*.sv
    2. vsim -c tb_processor -voptargs=+acc -do "run -all"
    3. gtkwave processor.vcd



## Future Work
  - Floating-Point Operations: Expand support for floating-point operations.
  - Hazard Handling and Branch Prediction: Optimize hazard handling and branch prediction logic.
  - Cache Memory: Integrate cache memory to improve performance.
  - RISC-V Extensions: Add support for more RISC-V extensions, such as vector instructions.


## Acknowledgments
  This project is part of my academic learning as a Computer Engineering student at UET Lahore. It reflects my journey in understanding 
  RISC-V architecture and building efficient processors.
    




   
