**MIPS 32 CPU Core with Hazard Detection and Data Forwarding**
This project implements a 32-bit MIPS CPU core with a 5-stage pipeline architecture, featuring hazard detection and data forwarding units. The MIPS architecture is based on the Reduced Instruction Set Computer (RISC) philosophy, making it highly efficient for embedded systems and various other applications.

![image](https://github.com/user-attachments/assets/8be6a511-17ba-4531-992e-c04a6e1c226c)


**Overview**

The MIPS core is designed to handle R-type, I-type, and J-type instructions, supporting a 32-bit instruction set. The CPU has five main pipeline stages:

-Instruction Fetch (IF)
-Instruction Decode (ID)
-Execution (EX)
-Memory Access (MEM)
-Write Back (WB)
The pipeline stages are connected by registers such as IF/ID, ID/EX, EX/MEM, and MEM/WB. Additionally, the core has hazard detection and data forwarding units to avoid data hazards and enable efficient instruction execution without unnecessary stalls.

**Features**

5-Stage Pipeline: The processor pipeline consists of the following stages: IF, ID, EX, MEM, WB, with corresponding pipeline registers between them.
Hazard Detection Unit: Detects data hazards during pipeline execution and introduces stalls as needed to prevent data corruption.
Data Forwarding Unit: Forwards data from later stages to earlier stages to avoid stalls caused by data hazards when possible.
RISC Architecture: Supports a simplified and efficient instruction set, designed to complete most instructions in a single clock cycle.
Instruction Support: Includes ALU operations (ADD, SUB, AND, OR, etc.), memory operations (LW, SW), branching (BEQZ, BNEQZ), and immediate instructions (ADDI, SUBI, etc.).
Memory and Registers: The design includes 32 general-purpose registers and 1024 memory locations.

**Instruction Set**

The processor supports the following instruction types:

R-Type (Register-Register ALU Operations): ADD, SUB, AND, OR, etc.
I-Type (Immediate ALU and Memory Operations): ADDI, SUBI, ANDI, LW, SW, etc.
Branch Instructions: BEQZ (branch if equal to zero), BNEQZ (branch if not equal to zero).
HLT: Halts the CPU.

**Pipeline Stages**

1. Instruction Fetch (IF)
Fetches the instruction from memory based on the current program counter (PC).
If a branch is taken (resolved in the EX stage), the PC is updated accordingly.
2. Instruction Decode (ID)
Decodes the fetched instruction and retrieves the required operands from the register file.
Sign-extends the immediate value for I-type instructions.
3. Execution (EX)
Executes the instruction using the ALU.
For branch instructions, calculates the target address and sets the condition for branching.
For memory instructions, calculates the memory address.
4. Memory Access (MEM)
For load instructions, retrieves data from memory.
For store instructions, writes data to memory.
ALU results from the EX stage are forwarded directly if no memory access is needed.
5. Write Back (WB)
Writes results back to the register file for R-type and I-type instructions.
Loads data from memory for load instructions.
Hazard Detection and Data Forwarding
Hazard Detection: Detects when an instruction depends on the result of a previous instruction still in the pipeline. In such cases, the pipeline is stalled or forwarded to prevent incorrect execution.
Data Forwarding: Implements a mechanism to forward data directly from the EX or MEM stage to the ID stage if the next instruction depends on the result of the current instruction.


**Testbench**

The design includes a testbench to verify the functionality of the MIPS processor core. It tests:

Arithmetic operations (ADD, SUB, MUL, etc.).
Immediate arithmetic operations (ADDI, SUBI, etc.).
Memory operations (LW, SW).
Branch instructions (BEQZ, BNEQZ).
Forwarding and hazard detection functionality.


**Future Enhancements**

Add more complex instructions (e.g., floating-point operations).
Improve hazard detection for control hazards (branches).
Add support for pipeline flushing during branch misprediction.


**Conclusion**

This MIPS 32 CPU core is an efficient, pipelined processor with hazard detection and data forwarding, making it capable of executing instructions with minimal stalls and high throughput. The design demonstrates the core principles of the RISC architecture and pipelined processor design.
