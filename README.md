# ⚙️ 3-Stage Pipelined 16-Bit ALU

A **16-bit 3-stage pipelined Arithmetic Logic Unit (ALU)** designed and implemented using **Verilog HDL**. The project demonstrates RTL design, hardware pipelining, functional simulation, FPGA synthesis, timing analysis, and power estimation.

## 🚀 Features

- 16-bit ALU datapath
- 3-stage pipelined architecture
- Verilog HDL implementation
- Arithmetic and logical operations
- Shift and rotate operations
- RTL simulation and waveform verification
- FPGA synthesis and implementation
- Timing and power analysis
- Resource utilization analysis

## 🏗️ Architecture

The design divides ALU processing into three pipeline stages:

```text
Input
  │
  ▼
┌──────────────────┐
│ Stage 1          │
│ Input / Decode   │
└────────┬─────────┘
         │
      Register
         │
         ▼
┌──────────────────┐
│ Stage 2          │
│ Execute          │
│ Arithmetic/Logic │
└────────┬─────────┘
         │
      Register
         │
         ▼
┌──────────────────┐
│ Stage 3          │
│ Output / Register│
└────────┬─────────┘
         │
         ▼
      ALU Result
```

The pipeline reduces the combinational delay within each clock cycle and enables higher processing throughput.

## 🔢 Supported Operations

- Addition
- Subtraction
- Multiplication
- Division
- Increment / Decrement
- AND / OR / XOR
- NOT / NAND / NOR
- Logical and arithmetic shifts
- Rotate operations

## 📊 Performance Results

| Parameter | Non-Pipelined | 3-Stage Pipelined |
|---|---:|---:|
| LUTs | 70 | 120 |
| Data Path Delay | 9.893 ns | **5.195 ns** |
| Power | 10.264 W | **10.261 W** |

The pipelined implementation achieves approximately **47.5% reduction in reported data-path delay**, with an increase in LUT utilization.

## 🔬 Simulation

The waveform demonstrates the operation of the pipelined ALU with clock, reset, input operands, operation selection, output, and zero-status signals.

![Simulation Waveform](images/simulation-waveform.jpg)

## 🧩 RTL Schematic

### Synthesized RTL

![RTL Schematic](images/rtl-schematic.jpg)

### Detailed ALU Schematic

![ALU Schematic](images/alu-schematic.jpg)

## ⏱️ Timing Analysis

The implemented design was analyzed using Vivado timing reports to evaluate the critical data path and routing delay.

![Timing Report](images/timing-report.jpg)

## ⚡ Power Analysis

The implementation reported a total on-chip power of approximately **10.261 W**.

![Power Analysis](images/power-analysis.jpg)

## 📈 Synthesis & Implementation

The Vivado Design Runs report shows successful synthesis and implementation with:

- **120 LUTs**
- **122 Flip-Flops**
- **0 BRAM**
- **0 URAM**
- **0 DSP**
- **10.261 W reported total power**

![Design Runs](images/design-runs.jpg)

## 🛠️ Tools & Technologies

- **Verilog HDL**
- **Xilinx Vivado**
- **RTL Simulation**
- **FPGA Synthesis**
- **Timing Analysis**
- **Power Analysis**
- **Digital Logic Design**

## 📂 Repository Structure

```text
3-Stage-Pipelined-ALU---Verilog-HDL/
|
├── images/
│   ├── design-runs.jpg
│   ├── rtl-schematic.jpg
│   ├── alu-schematic.jpg
│   ├── timing-report.jpg
│   ├── power-analysis.jpg
│   └── simulation-waveform.jpg
|
├── 3-Stage 16-Bit ALU Project Report.pdf
|
├── ALU_16bit_3SP.rar
│
└── README.md
```

## 🎯 Project Objective

The main objective is to demonstrate how **pipelining can improve ALU performance by reducing critical-path delay**, while analyzing the associated FPGA resource and power trade-offs.

---

⭐ **16-bit ALU | Verilog HDL | 3-Stage Pipeline | RTL Design | FPGA | Vivado**
