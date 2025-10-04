# 🎓 Understanding SoC Design Fundamentals Through VSDBabySoC

<div align="center">

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![RISC-V](https://img.shields.io/badge/Architecture-RISC--V-orange?style=flat-square)](https://riscv.org/)
[![Sky130](https://img.shields.io/badge/Process-Sky130-green)](https://skywater-pdk.readthedocs.io/)

</div>

<br>

## 📜 Table of Contents

1. [Introduction](#id1)
2. [What is a System-on-Chip (SoC)?](#what-is-a-system-on-chip-soc)
3. [Components of a Typical SoC](#components-of-a-typical-soc)

   * [Central Processing Unit (CPU)](#central-processing-unit-cpu)
   * [Memory Subsystem](#memory-subsystem)
   * [Graphics Processing Unit (GPU)](#graphics-processing-unit-gpu)
   * [Digital Signal Processor (DSP)](#digital-signal-processor-dsp)
   * [I/O Interfaces](#inputoutput-io-interfaces)
   * [Power Management Units](#power-management-units)
   * [Special Features](#special-features)
4. [Why SoCs Are Important](#why-socs-are-important)
5. [Types of SoCs](#types-of-socs)
6. [SoC Design Flow](#soc-design-flow)
7. [Introduction to BabySoC](#introduction-to-babysoc)
8. [VSDBabySoC Architecture](#vsdbabysoc-architecture)

   * [RVMYTH CPU](#rvmyth-cpu)
   * [Phase-Locked Loop (PLL)](#phase-locked-loop-pll)
   * [Digital-to-Analog Converter (DAC)](#digital-to-analog-converter-dac)
     
9. [Functional Modelling in SoC Design](#functional-modelling-in-soc-design)
10. [Learning Outcomes from BabySoC](#learning-outcomes-from-babysoc)
11. [Practical Applications](#practical-applications)
12. [Connection to Professional Practice](#connection-to-professional-practice)
13. [VSDBabySoC – A Tiny RISC-V System-on-Chip](#vsdbabysoc-architecture)
14. [Project Structure](#project-structure)
15. [Setup & TL-Verilog Conversion](#🛠️-setup--tl-verilog-conversion)
16. [Simulation Flow](#🧪-simulation-flow)
17. [Pre-Synthesis Simulation](#pre-synthesis-simulation)
18. [Post-Synthesis Simulation](#post-synthesis-simulation)
19. [Key Signals to Observe](#key-signals-to-observe)
20. [Instruction Program Driving BabySoC](#🔄-instruction-program-driving-babysoc)
21. [Execution Timeline](#execution-timeline)
22. [Troubleshooting](#🛠️-troubleshooting)
23. [Summary](#💡-summary)
24. [References](#📚-references)

<br>

<a id="id1"></a>
## 🌟 Introduction

**VSDBabySoC** is a **compact educational System-on-Chip** designed to teach **fundamental SoC concepts** while retaining **real-world functionality**. It integrates:

* 🧠 **RVMYTH CPU Core** – A synthesizable 32-bit RISC-V processor
* ⏱️ **Phase-Locked Loop (PLL)** – Ensures stable clocking and synchronization
* 🎚 **10-bit DAC** – Bridges digital computation to analog output

The project provides **hands-on experience** with digital, analog, and mixed-signal design, functional modeling, and SoC integration. It is perfect for:

* Students learning **CPU, memory, and peripheral interactions**
* Engineers exploring **functional modeling before RTL and physical design**
* Understanding **clock distribution, analog interfacing, and pipeline design**

<br>

## 🤔 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** integrates all essential computing components into a **single silicon die**, replacing multi-chip board-level designs. Instead of connecting discrete chips for CPU, GPU, memory, I/O, and peripherals, a modern SoC consolidates them, yielding:

* **Compact Size:** Fits complex systems in packages smaller than a fingernail
* **Energy Efficiency:** On-chip communication drastically reduces power
* **High Performance:** Low-latency connections between components
* **Cost Savings:** Fewer parts, simpler boards, lower assembly/test costs
* **Reliability:** Fewer connectors reduce failure points

💡 **Analogy:** An SoC is like a **self-sustaining smart city**:

| SoC Component | City Analogy                          |
| ------------- | ------------------------------------- |
| CPU           | City Hall (decision-making)           |
| Memory        | Library (knowledge storage)           |
| I/O           | Roads & Highways (data transport)     |
| GPU           | Art District (visual creativity)      |
| DSP           | Concert Hall (signal processing)      |
| Power Mgmt.   | Power Station (energy supply)         |
| Connectivity  | Airports/Ports (global communication) |

**Applications:** Smartphones, tablets, wearables, IoT devices, automotive embedded systems.
**Challenges:** Thermal management, design complexity, limited flexibility post-fabrication.

<br>

## 🛠️ Components of a Typical SoC

### Central Processing Unit (CPU)

* **Core of computation:** Executes instructions, handles memory and I/O
* **Heterogeneous architecture:** High-performance + energy-efficient cores
* **BabySoC Implementation:** RVMYTH CPU, a simple, synthesizable 32-bit RISC-V processor for education

**Key Learning:** Instruction execution, register file architecture, pipeline hazards, and I/O interfacing.

<br>

### Memory Subsystem

* **On-chip Cache:** Reduces latency, critical for performance
* **Memory Controllers:** Manage DRAM protocols, refresh cycles, error correction
* **ROM / Flash:** Store bootloader, firmware, and persistent program code

**Key Learning:** Memory hierarchies, access timing, and interface protocols.

<br>

### Graphics Processing Unit (GPU)

* Handles **parallel processing** for image/video rendering
* Useful for general-purpose parallel workloads (AI, physics simulations)
* BabySoC does not include a GPU, but understanding its function is crucial in modern SoCs.

<br>

### Digital Signal Processor (DSP)

* Optimized for **signal processing**: audio, video, communications
* Performs filtering, FFT, noise reduction efficiently
* Exposes students to domain-specific accelerators in SoCs.

<br>

### Input/Output (I/O) Interfaces

* Digital interfaces: UART, SPI, I2C, GPIO
* Analog interfaces: DACs, ADCs for real-world signals
* BabySoC includes a **10-bit DAC** for analog output

<br>

### Power Management Units (PMU)

* Optimizes energy consumption
* Supports **clock gating, dynamic voltage/frequency scaling (DVFS)**
* Ensures battery-powered devices last longer

<br>

### Special Features

* Connectivity: Wi-Fi, Bluetooth
* Security: Encryption, authentication modules
* Accelerators: AI, cryptography, video codecs
* BabySoC focuses on fundamentals, but these features show modern SoC complexity.

<br>

## 🎯 Why SoCs Are Important

| Feature              | Benefit                               |
| -------------------- | ------------------------------------- |
| 📦 Compactness       | Mobile & embedded devices             |
| 🔋 Energy Efficiency | Extended battery life                 |
| ⚡ High Performance   | Reduced latency and faster processing |
| 💰 Cost-Effective    | Replaces multiple discrete components |
| ✅ Reliable           | Fewer points of failure               |

<br>

## 🧩 Types of SoCs

1. **Microcontroller-based:** Low-power, small-scale control
2. **Microprocessor-based:** Runs OS, multitasking (smartphones, tablets)
3. **Application-Specific SoC (ASIC):** Domain-optimized for AI, automotive, networking

<br>

## 🌀 SoC Design Flow

1. **Architectural Specification:** Define system goals, performance, interfaces
2. **Functional Modeling:** High-level behavioral validation (C++, SystemC, Python, MATLAB)
3. **RTL Design:** Synthesizable implementation in Verilog/VHDL
4. **Verification:** Simulation, formal verification, test coverage analysis
5. **Synthesis:** Convert RTL to gate-level netlist
6. **Physical Design:** Placement, routing, timing closure
7. **Fabrication & Testing:** Validate silicon against specs

**Functional Modeling:** Key to validating design early, reducing costly late-stage errors.

<br>

## 👶 Introduction to BabySoC

**VSDBabySoC** is an **educational, simplified RISC-V SoC**, including:

* RVMYTH CPU – a functional 32-bit RISC-V processor
* 8× PLL – stable, high-frequency clock generation
* 10-bit DAC – analog output for tangible results

Designed for **learning-by-doing**, it exposes students to CPU design, clocking, and digital-to-analog conversion in a minimal, manageable platform.

<br>

## 🧩 VSDBabySoC Architecture

```
Reference Clock → [ PLL ] → [ RVMYTH CPU ] → r17 → [ 10-bit DAC ] → Analog Output
```

**Component Roles:**

| Component  | Functionality                                             |
| ---------- | --------------------------------------------------------- |
| RVMYTH CPU | Executes instructions, drives r17 register for DAC output |
| PLL        | Generates high-speed, stable system clock                 |
| DAC        | Converts 10-bit digital values to analog voltage          |

💡 **Analogy:** CPU = brain, PLL = heartbeat, DAC = voice

<br>

### RVMYTH CPU

* **Pipeline-based, 32 registers (RISC-V spec)**
* Executes arithmetic, logic, load/store, branch instructions
* Drives **r17 register** for DAC output
* Demonstrates **instruction execution, register management, and I/O interfacing**

<br>

### Phase-Locked Loop (PLL)

* **Generates stable clock** at 8× reference frequency
* Components: Phase Frequency Detector, Charge Pump, VCO, Frequency Divider
* **Benefits:** Reduces jitter, supports multiple frequencies, compensates for temperature/voltage variations

<br>

### Digital-to-Analog Converter (DAC)

* **10-bit resolution (1024 levels)**
* Implements **R-2R Ladder network** for accurate, scalable conversion
* Converts CPU output into measurable analog signals
* Introduces **mixed-signal design considerations:** noise, reference stability, layout precision

<br>

## 🧪 Functional Modelling in SoC Design

**Purpose:** Early validation before RTL and physical design.

* Verify system behavior
* Analyze CPU instruction execution
* Simulate PLL locking and DAC output
* Identify timing, interface, and data flow issues

**Benefits:** Reduces errors, accelerates learning, provides a **golden reference** for RTL verification.

<br>

## 🎯 Learning Outcomes from BabySoC

1. Understanding **CPU pipeline, registers, and instruction flow**
2. Mastering **clocking and PLL design principles**
3. Exploring **digital-to-analog conversion techniques**
4. Integrating **heterogeneous SoC components**
5. Applying **functional modeling** to validate systems

<br>

## ⚡ Practical Applications

* **Signal Generation:** Test patterns for analog circuits
* **Control Systems:** Generate control voltages
* **Algorithm Development:** DSP, waveform synthesis
* **Research Platform:** Explore PLL/DAC variations, low-power techniques

<br>

## 🏭 Connection to Professional Practice

* Interfacing CPU with peripherals
* Managing **clock distribution**
* Handling **mixed-signal challenges**
* Following **systematic design flows**
* Making **architecture vs. implementation trade-offs**
* Using HDL and **EDA tools** for design, synthesis, and analysis

<br>

## 🏁 Conclusion

VSDBabySoC


provides a **foundational, hands-on platform** for understanding SoC design, spanning **digital, analog, and mixed-signal domains**.

By learning:

* How the **PLL generates stable timing**
* How the **RISC-V CPU executes instructions**
* How the **DAC converts digital output to analog signals**

…students gain insights directly applicable to **real-world SoC design**, from microcontrollers to application processors and specialized accelerators.

Mastering these **fundamental concepts** in a manageable platform prepares learners for the **complex SoCs powering modern technology**.




<br>

## 🧩 VSDBabySoC Architecture

## 📂 Project Structure

```
VSDBabySoC/
├── Makefile
├── output
│   ├── compiled_tlv
│   │   ├── rvmyth_gen.v
│   │   └── rvmyth.v
│   ├── pre_synth_sim
│   │   ├── pre_synth_sim.out
│   │   └── pre_synth_sim.vcd
│   └── synth
│       ├── synth.log
│       └── vsdbabysoc.synth.v
└── src
    ├── gds
    │   ├── avsddac.gds
    │   └── avsdpll.gds
    ├── gls_model
    │   ├── primitives.v
    │   └── sky130_fd_sc_hd.v
    ├── include
    │   ├── sandpiper_gen.vh
    │   ├── sandpiper.vh
    │   ├── sp_default.vh
    │   └── sp_verilog.vh
    ├── layout_conf
    │   ├── rvmyth
    │   │   ├── config.tcl
    │   │   └── pin_order.cfg
    │   └── vsdbabysoc
    │       ├── config.tcl
    │       ├── macro.cfg
    │       └── pin_order.cfg
    ├── lef
    │   ├── avsddac.lef
    │   └── avsdpll.lef
    ├── lib
    │   ├── avsddac.lib
    │   ├── avsdpll.lib
    │   └── sky130_fd_sc_hd__tt_025C_1v80.lib
    ├── module
    │   ├── avsddac.v
    │   ├── avsdpll.v
    │   ├── clk_gate.v
    │   ├── pseudo_rand_gen.sv
    │   ├── pseudo_rand.sv
    │   ├── rvmyth.tlv
    │   ├── testbench.rvmyth.post-routing.v
    │   ├── testbench.v
    │   └── vsdbabysoc.v
    ├── script
    │   ├── sta.conf
    │   ├── verilog_to_lib.pl
    │   └── yosys.ys
    └── sdc
        ├── vsdbabysoc_layout.sdc
        └── vsdbabysoc_synthesis.sdc

```

<br>

## 🛠️ Setup & TL-Verilog Conversion

1. **Clone the Project**

```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC/
```

2. **Install Python Tools**

```bash
sudo apt update
sudo apt install python3-venv python3-pip
python3 -m venv sp_env
source sp_env/bin/activate
pip install pyyaml click sandpiper-saas
```

3. **Convert TL-Verilog to Verilog**

```bash
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```

<br>

## 🧪 Simulation Flow

### Pre-Synthesis Simulation

```bash
make pre_synth_sim
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```
<img width="1920" height="1080" alt="Screenshot from 2025-10-01 11-08-10" src="https://github.com/user-attachments/assets/b5e0c1e7-5ed7-4413-bd85-3929e06f784a" />

This screenshot demonstrates the process of cloning a GitHub repository and running a Verilog simulation workflow for the VSDBabySoC project using a Linux terminal. The terminal shows commands for cloning the repository, changing directories, running the Makefile to invoke synthesis, and launching GTKWave to view simulation results. This setup highlights a typical open-source FPGA/ASIC development flow, featuring source translation and waveform analysis tools for RTL design verification.

<br>


<img width="1920" height="1080" alt="image 2" src="https://github.com/user-attachments/assets/7fd3069f-c739-4694-9f8c-d2e1af601203" />


This screenshot displays simulation results using GTKWave, showcasing various signal waveforms for the VSDBabySoC design. The wave window illustrates digital signals such as clock (CLK), reset, and the output (OUT), as well as a 10-bit bus (RV_TO_DAC[9:0]). It visually confirms the behavior and timing relationships among these signals, aiding in functional verification of the RTL design.


<br>

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-11-54" src="https://github.com/user-attachments/assets/578e6a25-4f93-405e-93c9-cc801aee04ad" />


This image shows the terminal and the GTKWave window side by side. The terminal documents the simulation run and launch of GTKWave, while the GTKWave window displays the resulting signal waveforms of the digital design. This layout provides a clear overview of both command-line workflow steps and simulation outcomes for effective RTL verification.





<br>

### Post-Synthesis Simulation

```bash
make synth
make pre_synth_sim
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-03-11" src="https://github.com/user-attachments/assets/5b69ea7d-2b62-41cd-a337-0140928ddf5f" />

<br>

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-03-27" src="https://github.com/user-attachments/assets/1ad015c2-c55a-472c-baab-fd7302523efc" />

<br>

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-03-57" src="https://github.com/user-attachments/assets/f58de120-7c0a-49a2-8326-0132f453be96" />

This sequence of screenshots collectively documents the synthesis workflow for a chip design using open-source tools on a Linux terminal. It begins with the initial setup and execution of the Yosys Open Synthesis Suite, detailing the licensing information and script launch for Verilog design synthesis. Next, it illustrates the synthesis command running via a scripted flow, utilizing Docker to invoke OpenLane, and demonstrates how the Yosys suite is executed and its output redirected for logging—showcasing integration of open-source tools in ASIC design. Finally, it presents a synthesis summary: the mapping of RTL designs to standard cells such as NANDs, NORs, muxes, and flip-flops, resource statistics, and backend completion details, effectively summarizing logic mapping and usage in the synthesized project

<br>

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-09-54" src="https://github.com/user-attachments/assets/b501aa43-f19e-427c-9cbc-cc02b91fa239" />

This screenshot shows post-synthesis simulation results for the VSDBabySoC design in GTKWave. The waveforms represent key digital signals after the design has been synthesized. The left panel includes signals from the testbench and core module, including clock (CLK), reset, and a 10-bit output bus (OUT[9:0]). The wave window on the right visualizes the transitions and timing of these signals, allowing verification that the synthesized netlist maintains correct functional behavior as in the pre-synthesis RTL. This step is critical to ensure the implementation remains true to the original design specification.


<br>

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-19-13" src="https://github.com/user-attachments/assets/1b905394-1d0e-43be-9452-0f82694c0bbb" />

This screenshot shows the synthesis statistics for the "vsdbabysoc" design after running the synthesis tool. It lists detailed information such as the total number of wires (4737), wire bits (6211), and standard cells (5913) used in the synthesized digital circuit. The breakdown includes a count of each type of cell from the Sky130 standard cell library—such as logic gates, flip-flops, multiplexers, and custom blocks like "avsdac" and "avsdp1." These statistics help understand the hardware resource utilization and logic composition of the final synthesized netlist.



<br>

<img width="1920" height="1080" alt="Screenshot from 2025-10-01 12-09-48" src="https://github.com/user-attachments/assets/d99b7bfe-702f-44cd-94f4-708490735292" />

This screenshot shows the post-synthesis simulation environment for the VSDBabySoC design, with the terminal on the left capturing the synthesis and simulation commands and GTKWave on the right displaying signal waveforms. The layout clearly demonstrates the workflow of running the synthesized netlist simulation and visually verifying signal behavior in GTKWave, validating that the final implementation matches the intended RTL design.


<br>


### Key Signals to Observe

| Signal         | Description          |
| -------------- | -------------------- |
| CLK            | Input clock from PLL |
| reset          | Reset signal         |
| OUT            | DAC output           |
| RV_TO_DAC[9:0] | CPU r17 → DAC input  |

<br>

## 🔄 Instruction Program Driving BabySoC

| #   | Instruction      | Action             |
| --- | ---------------- | ------------------ |
| 0   | ADDI r9, r0, 1   | r9 = 1             |
| 1   | ADDI r10, r0, 43 | Loop limit = 43    |
| 2   | ADDI r11, r0, 0  | Initialize counter |
| 3   | ADDI r17, r0, 0  | DAC input = 0      |
| ... | ...              | ...                |
| 12  | BEQ r0, r0, ...  | Infinite loop      |

### Execution Timeline

| Phase       | r17 Value | Behavior           |
| ----------- | --------- | ------------------ |
| Ramp        | 0 → 903   | Monotonic increase |
| Peak        | 946       | Maximum output     |
| Oscillation | 903 ± r11 | Decaying waveform  |
| Final       | 903       | Steady hold        |

**DAC Conversion Formula:**
[
V_{OUT} = \frac{r17}{1023} \times V_{REF_SPAN} \quad (V_{REF_SPAN}=1.0V)
]

<br>

## 🛠️ Troubleshooting

* ⚠️ **Module Redefinition:** Include files only once
* 🛤 **Path Issues:** Use absolute paths if relative paths fail
* ⏱ **Waveform Mismatch:** Verify GTKWave format and signals

<br>

### 💡 Summary

**VSDBabySoC** provides a **hands-on, simplified learning platform** for:

* SoC fundamentals (CPU, memory, PLL, DAC)
* Functional modeling → RTL → simulation workflow
* Digital-to-analog interfacing
* Understanding clock synchronization, instruction execution, and SoC integration

## 📚 References

* [RISC-V Specifications](https://riscv.org/specifications/)
* [SkyWater Sky130 PDK](https://skywater-pdk.readthedocs.io/)
* Weste & Harris, *CMOS VLSI Design*
* [BabySoC GitHub Repository](https://github.com/manili/VSDBabySoC)


This small-scale SoC mimics real-world SoC design flows, making it **ideal for educational purposes** before tackling complex, industrial-scale designs.

