# 3-Stage Pipelined 16-Bit ALU

A **16-bit 3-stage pipelined Arithmetic Logic Unit (ALU)** designed and implemented using **Verilog HDL**. The project demonstrates the use of pipelining in digital hardware to reduce critical-path delay and improve computational throughput while supporting a comprehensive set of arithmetic, logical, and shift operations.

This project was developed as part of the **Architectural Design of Integrated Circuit (ADIC)** course and focuses on digital logic design, RTL development, simulation, synthesis, timing analysis, and FPGA implementation.

---

## 📌 Project Overview

An Arithmetic Logic Unit (ALU) is a fundamental building block of processors and digital systems. It performs arithmetic, logical, and bit-manipulation operations on binary data.

In this project, a **16-bit ALU** is implemented using a **3-stage pipelined architecture**. The pipelining technique divides the computational path into multiple sequential stages separated by registers, allowing multiple operations to be processed concurrently.

The primary objective is to improve the operating performance of the ALU by reducing the combinational delay within each pipeline stage.

### Key Highlights

* 16-bit data path
* Verilog HDL implementation
* 3-stage pipelined architecture
* Arithmetic, logical, and shift operations
* Modular RTL design
* Comprehensive simulation and verification
* FPGA synthesis and implementation
* Timing and resource utilization analysis
* Comparison between pipelined and non-pipelined architectures

---

## ✨ Features

### Arithmetic Operations

The ALU supports common arithmetic operations including:

* Addition
* Subtraction
* Multiplication
* Division
* Increment
* Decrement

### Logical Operations

The following bitwise operations are supported:

* AND
* OR
* XOR
* NOT
* NAND
* NOR

### Shift and Rotate Operations

The design also supports:

* Logical Shift Left
* Logical Shift Right
* Arithmetic Shift Right
* Rotate Left
* Rotate Right

---

## 🏗️ Architecture

The ALU uses a **three-stage pipelined architecture** to divide the overall computation into smaller sequential stages.

### Pipeline Structure

```text
             ┌────────────────────┐
             │     Stage 1        │
             │ Input / Decode     │
             │                    │
A[15:0] ────►│ Operand & Control  │
B[15:0] ────►│ Processing         │
Opcode ─────►│                    │
             └─────────┬──────────┘
                       │
                    Register
                       │
                       ▼
             ┌────────────────────┐
             │     Stage 2        │
             │     Execute        │
             │                    │
             │ Arithmetic / Logic │
             │ Shift Operations   │
             └─────────┬──────────┘
                       │
                    Register
                       │
                       ▼
             ┌────────────────────┐
             │     Stage 3        │
             │ Output / Writeback │
             │                    │
             │ Result & Flags     │
             └─────────┬──────────┘
                       │
                       ▼
                  ALU Result
```

Each stage performs a portion of the overall computation. Pipeline registers separate the stages and allow successive operations to overlap.

---

## 🔄 Pipeline Operation

The three stages can be broadly described as follows:

### Stage 1 — Input and Control Processing

The input operands and operation code are captured and processed.

Responsibilities include:

* Capturing input operands
* Capturing the operation code
* Decoding the requested operation
* Preparing control information for the execution stage

### Stage 2 — Execute

The selected ALU operation is performed on the operands.

Depending on the operation code, the ALU performs:

* Arithmetic computation
* Logical computation
* Shift operations
* Rotate operations

The intermediate result is then stored in a pipeline register.

### Stage 3 — Output / Writeback

The computed result is transferred to the output through the final pipeline stage.

This stage provides the registered ALU output and associated status information where applicable.

---

## ⏱️ Why Pipelining?

A non-pipelined ALU may contain a long combinational path through multiple logic blocks. This increases the propagation delay and limits the maximum operating frequency.

Pipelining divides the critical path into smaller sections.

### Non-Pipelined

```text
Input
  │
  ▼
Arithmetic / Logic / Shift
  │
  ▼
Output
```

### 3-Stage Pipelined

```text
Input
  │
  ▼
Stage 1
  │
  ▼
Register
  │
  ▼
Stage 2
  │
  ▼
Register
  │
  ▼
Stage 3
  │
  ▼
Output
```

Although pipelining introduces additional registers and therefore increases hardware utilization, it significantly reduces the delay of an individual pipeline stage and enables higher throughput.

---

## 📊 Performance Comparison

The design was evaluated against a non-pipelined 16-bit ALU.

| Parameter       | Non-Pipelined ALU | 3-Stage Pipelined ALU |
| --------------- | ----------------: | --------------------: |
| Slice LUTs      |                70 |                   120 |
| Data Path Delay |          9.893 ns |          **5.195 ns** |
| Power           |          10.264 W |          **10.261 W** |

### Performance Improvement

The reported data-path delay was reduced from:

**9.893 ns → 5.195 ns**

This corresponds to approximately **47.5% reduction in data-path delay**.

The trade-off is an increase in LUT utilization:

**70 LUTs → 120 LUTs**

while the reported power remained approximately unchanged.

---

## 🧮 ALU Data Path

The basic ALU data path consists of:

```text
             ┌─────────────────┐
A[15:0] ────►│                 │
             │   Arithmetic    │
B[15:0] ────►│      Unit       │
             │                 │
             └───────┬─────────┘
                     │
                     │
             ┌───────▼─────────┐
             │                 │
             │   Logic Unit    │
             │                 │
             └───────┬─────────┘
                     │
                     │
             ┌───────▼─────────┐
             │                 │
             │  Shift/Rotate   │
             │      Unit       │
             │                 │
             └───────┬─────────┘
                     │
                     ▼
                Result[15:0]
```

The operation code determines which operation is selected and the corresponding result is passed through the pipeline.

---

## 🛠️ Design Methodology

The project follows a standard RTL-based digital design flow.

```text
Requirements
     │
     ▼
Architecture Design
     │
     ▼
RTL / Verilog Development
     │
     ▼
Testbench Development
     │
     ▼
Functional Simulation
     │
     ▼
Debugging & Verification
     │
     ▼
Synthesis
     │
     ▼
Timing Analysis
     │
     ▼
FPGA Implementation
```

### 1. Requirement Analysis

The required ALU operations, input/output signals, control signals, timing requirements, and status information were identified.

### 2. Architecture Design

The ALU was divided into functional sections and pipeline stages to reduce the critical path.

### 3. RTL Implementation

The architecture was implemented using **Verilog HDL** with a modular hardware design approach.

### 4. Verification

Testbenches were developed to verify the supported operations under different input conditions.

Testing included:

* Normal operating conditions
* Boundary values
* Zero results
* Arithmetic operations
* Logical operations
* Shift and rotate operations
* Overflow and carry conditions

### 5. Synthesis

The RTL design was synthesized to evaluate:

* LUT utilization
* Timing
* Data-path delay
* Power
* FPGA resource utilization

### 6. FPGA Implementation

The synthesized design was targeted for FPGA implementation and evaluated for practical hardware operation.

---

## 🧪 Verification

Functional verification is performed through simulation using dedicated testbench logic.

The testbench evaluates the ALU by applying different:

* Operand combinations
* Operation codes
* Boundary values
* Arithmetic conditions
* Logical conditions
* Shift amounts

The simulated outputs are compared with the expected results to verify functional correctness.

Waveform analysis can be used to observe:

```text
Clock
Input A
Input B
Opcode
Pipeline Stage 1
Pipeline Stage 2
Pipeline Stage 3
ALU Result
```

Because this is a pipelined architecture, the output corresponds to an input operation after the defined pipeline latency.

---

## 📁 Repository Structure

```text
3-Stage-Pipelined-ALU/
│
├── README.md
│
├── ALU_16bit_3SP.rar
│   └── Verilog HDL source and project files
│
└── 3-Stage 16-Bit ALU Project Report.pdf
    └── Detailed project documentation and results
```

---

## 💻 Technologies Used

| Technology           | Purpose                    |
| -------------------- | -------------------------- |
| Verilog HDL          | RTL hardware description   |
| FPGA                 | Hardware implementation    |
| Digital Logic Design | ALU architecture           |
| Pipelining           | Performance optimization   |
| RTL Simulation       | Functional verification    |
| FPGA Synthesis       | Hardware resource analysis |
| Timing Analysis      | Performance evaluation     |

---

## 🎯 Design Objectives

The major objectives of the project are:

1. Design a 16-bit ALU using Verilog HDL.
2. Implement arithmetic, logical, shift, and rotate operations.
3. Develop a 3-stage pipelined architecture.
4. Reduce the critical-path delay.
5. Improve ALU throughput.
6. Verify the design through simulation.
7. Analyze FPGA resource utilization.
8. Perform timing analysis.
9. Compare pipelined and non-pipelined implementations.
10. Demonstrate the practical benefits of hardware pipelining.

---

## 🚀 Advantages

### Higher Throughput

Multiple operations can occupy different pipeline stages simultaneously, increasing the number of operations that can be processed over time.

### Reduced Critical-Path Delay

Dividing the computation into multiple stages reduces the amount of combinational logic that must be traversed within a single clock cycle.

### Higher Operating Frequency

The reduced critical-path delay allows the design to potentially operate at a higher clock frequency.

### Modular Architecture

The pipelined structure provides a modular design that can be extended or optimized for more complex processor architectures.

### Suitable for FPGA Implementation

The RTL-based architecture can be synthesized and implemented on FPGA devices for hardware validation.

---

## 📚 Applications

A pipelined ALU architecture can be used as a building block in:

* Microprocessors
* Microcontrollers
* CPU datapaths
* Digital Signal Processors
* FPGA-based computing systems
* Embedded processors
* Communication systems
* Image and signal processing systems
* Cryptographic hardware
* High-performance digital systems

---

## 📈 Future Improvements

The project can be extended with several additional features:

* Parameterized ALU width such as 32-bit and 64-bit
* Additional arithmetic operations
* Dedicated status flag generation
* Carry-lookahead or carry-select adders
* Improved multiplication and division units
* Deeper pipeline architecture
* Pipeline control and stall handling
* Forwarding and hazard management
* AXI/AMBA interface
* Integration with a RISC-V processor
* FPGA resource and power optimization
* Formal verification
* ASIC synthesis and physical design analysis

---

## 🎓 Academic Project

**Course:** Architectural Design of Integrated Circuit (ADIC)
**Course Code:** 23EECE302
**Project:** 16-Bit 3-Stage Pipelined ALU
**Academic Year:** 2023–24

### Team

* **Amey V. Chougule**
* **Sharwari M. Kale**

**Department of Electronics & Communication Engineering**
**KLE Technological University, Dr. M. S. Sheshgiri Campus, Belagavi**

---

## 📖 References

1. Bhimani, H.S., Patel, H.N. and Davda, A.A., *Design of 32-bit 3-stage pipelined processor based on MIPS in Verilog HDL and implementation on FPGA Virtex7*.
2. Anusha, S., Rao, M.M. and Reddy, N.S., *Design, Analysis, Implementation and Synthesis of 16-bit Reversible ALU*.
3. Swamynathan, S.M. and Banumathi, V., *Design and Analysis of FPGA Based 32-bit ALU Using Reversible Gates*.
4. Kulkarni, R. and Kulkarni, S.Y., *Energy Efficient Implementation of 16-Bit ALU Using Block Enabled Clock Gating Technique*.
5. Pandey, B. et al., *Energy Efficient Design and Implementation of ALU on 40nm FPGA*.

---

## 📜 License

This project is intended primarily for **academic, educational, and research purposes**.

If you use or modify this project, please provide appropriate attribution to the original authors.

---

## ⭐ Project Summary

This project demonstrates how **hardware pipelining can improve the performance of a digital ALU**. By implementing a 16-bit ALU using a three-stage pipeline, the design achieves a significant reduction in reported data-path delay compared with the corresponding non-pipelined implementation.

The project provides practical experience in:

**Digital Logic → Verilog HDL → RTL Design → Simulation → Pipelining → FPGA Synthesis → Timing Analysis → Hardware Implementation**

It serves as a foundation for further exploration of **processor datapaths, FPGA-based computing, CPU architecture, and VLSI digital design**.
