# Week-2-BabySoC-Fundamentals-Functional-Modelling


## 🎓 BabySoC – Learning-Oriented RISC-V System-on-Chip (SoC)

<div align="center">
  
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![RISC-V](https://img.shields.io/badge/Architecture-RISC--V-orange?style=flat-square)](https://riscv.org/)
[![Sky130](https://img.shields.io/badge/Process-Sky130-green)](https://skywater-pdk.readthedocs.io/)

</div>

## 📜 Table of Contents

1. [Introduction](#introduction)
2. [What is a System-on-Chip (SoC)?](#what-is-a-system-on-chip-soc)
3. [Components of a Typical SoC](#components-of-a-typical-soc)

   * [CPU](#central-processing-unit-cpu)
   * [Memory](#memory-subsystem)
   * [I/O Interfaces](#inputoutput-io-interfaces)
   * [GPU](#graphics-processing-unit-gpu)
   * [DSP](#digital-signal-processor-dsp)
   * [Power Management Units](#power-management-units)
   * [Special Features](#special-features)
4. [Why SoCs Are Important](#why-socs-are-important)
5. [Types of SoCs](#types-of-socs)
6. [Introduction to BabySoC](#introduction-to-babysoc)
7. [BabySoC Architecture](#babysoc-architecture)

   * [RVMYTH CPU](#rvmyth-cpu)
   * [Phase-Locked Loop (PLL)](#phase-locked-loop-pll)
   * [Digital-to-Analog Converter (DAC)](#digital-to-analog-converter-dac)
8. [Functional Modelling in SoC Design](#functional-modelling-in-soc-design)
9. [Learning Outcomes from BabySoC](#learning-outcomes-from-babysoc)
10. [GitHub Showcase](#github-showcase)
11. [References](#references)

<br>

## 🌟 Introduction

**BabySoC** is a **compact, educational System-on-Chip** that simplifies SoC concepts while retaining **real-world functionality**. Designed around the **RISC-V RVMYTH core**, it includes a **Phase-Locked Loop (PLL)** for precise clock control and a **10-bit Digital-to-Analog Converter (DAC)** for analog interfacing.

The project’s primary goal is to provide a **highly documented learning platform**, bridging theoretical concepts of SoC design with practical implementation. BabySoC is perfect for:

* Students exploring digital design and SoC architecture
* Engineers learning functional modelling before RTL and physical design
* Understanding digital-to-analog interfacing

<br>

## 🤔 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** is essentially a **mini-computer integrated into a single silicon die**, combining multiple functional units into one compact design.
It combines:

* **CPU** – Central Processing Unit
* **Memory** – RAM, ROM/Flash
* **I/O Interfaces** – USB, sensors, displays
* **GPU/DSP** – Graphics & signal processing
* **Power Management** – Efficient energy usage
* **Connectivity** – Wi-Fi, Bluetooth, 5G, secure data links

This integration enables **compact, energy-efficient, high-performance, and cost-effective** devices like smartphones, wearables, IoT gadgets, and embedded systems.


## 🎯 Why SoCs?

| Feature                  | Benefit                                             |
| ------------------------ | --------------------------------------------------- |
| 📦 **Compactness**       | Ideal for mobile & embedded devices                 |
| 🔋 **Energy Efficiency** | Extends battery life in wearables, IoT, smartphones |
| ⚡ **High Performance**   | Reduced latency with on-chip communication          |
| 💰 **Cost-Effective**    | Single chip replaces multiple discrete components   |
| **Reliable**         | Fewer discrete components mean fewer points of failure.                     |

💡 **Analogy:** Think of an SoC as a self-sustaining smart city 🏙️

| SoC Component | Analogy                                  |
| ------------- | ---------------------------------------- |
| CPU           | City Hall (decision-making)              |
| Memory        | Library (knowledge storage)              |
| I/O           | Roads & Highways (data transport)        |
| GPU           | Art District (visual creativity)         |
| DSP           | Concert Hall (audio & signal processing) |
| Power Mgmt.   | Power Station (energy supply)            |
| Connectivity  | Airports/Ports (global communication)    |


**Applications:**

* Smartphones & Tablets
* Smartwatches & Wearables
* IoT Devices
* Embedded Systems in Cars, TVs, Home Appliances

**Challenges:**

* Complex design integration
* Thermal management due to dense packing
* Limited post-fabrication flexibility

<div align="center">
  
<img src="https://github.com/user-attachments/assets/ff01a02e-f2ad-40b2-bc79-94aa4f025a2e" alt="generated-image" width="500" height="350"/>


</div>

<br>

## 🛠️ Components of a Typical SoC

A SoC integrates multiple specialized components. Understanding these is crucial for grasping BabySoC’s architecture.

### 1️⃣ Central Processing Unit (CPU)

* **Brain of the SoC** – executes instructions, controls peripherals, and manages memory.
* **Responsibilities:** Instruction execution, arithmetic operations, memory and I/O management.

**BabySoC Implementation:** **RVMYTH CPU**, a simple, open-source RISC-V core for learning CPU design and instruction execution.

<br>

### 2️⃣ Memory Subsystem

* **RAM (Random Access Memory):** Temporary storage for runtime data.
* **ROM / Flash Memory:** Non-volatile storage for program code.

Memory design affects **speed, power, and area**, making it a critical SoC component.

<br>

### 3️⃣ Input/Output (I/O) Interfaces

* Enables communication with **external devices**: USB, SPI, UART, GPIO.
* **Analog I/O:** DACs or ADCs.

**BabySoC** includes a **10-bit DAC**, allowing interaction with external analog devices (TVs, speakers, etc.).

<br>

### 4️⃣ Graphics Processing Unit (GPU)

* Handles **image and video rendering**.
* While BabySoC does not integrate a GPU, understanding GPU roles is essential for multimedia SoCs.

<br>

### 5️⃣ Digital Signal Processor (DSP)

* Optimized for **audio/video signal processing**.
* Performs filtering, Fourier transforms, and noise reduction.

<br>

### 6️⃣ Power Management Units (PMU)

* Efficiently manages **energy consumption**.
* Ensures battery-powered devices maximize lifespan.

<br>

### 7️⃣ Special Features

* Wi-Fi / Bluetooth controllers
* Security modules
* Application-specific accelerators

BabySoC focuses on **core learning**, but these features illustrate modern SoC complexity.

<br>

## 🌈 Why SoCs Are Important

* Integrates multiple functionalities in a single chip
* Reduces cost and size
* Enables portable devices
* Enhances performance and energy efficiency

<br>

## 🧩 Types of SoCs

1. **Microcontroller-based SoC** → Small-scale, low-power control (IoT nodes, appliances)
2. **Microprocessor-based SoC** → Runs OS, multitasking (smartphones, tablets)
3. **Application-Specific SoC (ASIC)** → Domain-optimized for AI accelerators, automotive, networking

<br>

## 🌀 SoC Design Flow

SoC design progresses through:

1. **Functional Modeling:** Early validation of system behavior; focuses on *what the system should do* rather than hardware specifics.
2. **RTL Design:** Implementation in Verilog/VHDL; describes registers, datapaths, and control logic.
3. **Physical Design:** Synthesis, placement, routing, and fabrication (e.g., Sky130 process).

Functional modeling is critical for avoiding design errors before committing to silicon.

BabySoC is a **learning-oriented microprocessor-based SoC**, simplified for educational use.

<br>


## 👶 VSDBabySoC – A Tiny but Powerful RISC-V SoC

### 🌟 Introduction

**VSDBabySoC** is a compact educational SoC built around:

* 🧠 **RVMYTH CPU Core** – A lightweight RISC-V processor
* ⏱️ **8× PLL** – Generates a stable internal clock
* 🎚 **10-bit DAC** – Converts digital values to analog output

It enables hands-on learning of:

* CPU instruction execution
* Clock synchronization using PLL
* Digital-to-analog interfacing

<br>

### 🧩 VSDBabySoC Architecture

**Block Diagram (Conceptual)**

```
[ Instruction Memory ] → [ RVMYTH CPU ] → r17 → [ 10-bit DAC ] → Analog OUT
                                ↑
                                |
                               [PLL]
```

**Component Details:**

| Component  | Role                                             |
| ---------- | ------------------------------------------------ |
| RVMYTH CPU | Executes instructions, drives register r17       |
| PLL        | Generates stable clock for CPU and DAC           |
| DAC        | Converts 10-bit digital values to analog voltage |

💡 **Analogy:** CPU = brain, PLL = heartbeat, DAC = voice

<br>

**VSDBabySoC** integrates:

* **RVMYTH RISC-V CPU**
* **8x Phase-Locked Loop (PLL)** for stable clocking
* **10-bit DAC** for analog output

### Goals:

1. Enable **simultaneous testing** of multiple open-source IPs
2. Validate **clock synchronization** via PLL
3. Demonstrate **digital-to-analog interfacing**

<br>

## 🏗️ BabySoC Architecture

<div align="center">
<img width="2270" height="1260" alt="vsdbabysoc_block_diagram" src="https://github.com/user-attachments/assets/3f59c535-b6dd-4cb6-a823-6861b075678c" />

</div>

### RVMYTH CPU

* **Instruction execution & control unit**
* **Register r17** cycles digital data to DAC
* Enables continuous **digital-to-analog conversion**

<br>

### Phase-Locked Loop (PLL)

<div align="center">
<img width="1205" height="712" alt="image" src="https://github.com/user-attachments/assets/55b1a29f-da13-4f4e-8fc6-6afffe94175e" />

</div>

**PLL Components:**

1. **Phase Detector:** Compares reference and output phase
2. **Loop Filter:** Converts phase error to control voltage
3. **Voltage-Controlled Oscillator (VCO):** Adjusts frequency

**Why PLL?**

* Minimize clock jitter
* Different frequencies for CPU & peripherals
* Compensate for crystal inaccuracies
* Reduce timing errors in high-speed circuits

<br>

### Digital-to-Analog Converter (DAC)

<div align="center">
<img width="934" height="209" alt="image" src="https://github.com/user-attachments/assets/db34c06f-8740-48ac-a88e-1110b7d09935" />
  
  <br>
  
<img width="1344" height="768" alt="generated-image (2)" src="https://github.com/user-attachments/assets/6ef5f85a-99ab-49db-b519-ac398edac059" />

</div>

* Converts **digital CPU output** to **analog signal**
* **10-bit DAC:** Supports 1024 discrete levels
* Interfaces with external devices (speakers, displays)
* Supports **R-2R Ladder or Weighted Resistor DAC topologies**

<br>

## 🧪 Functional Modelling in SoC Design

**Before RTL and physical design**, functional modelling helps:

* Verify system behavior
* Debug data flow & control logic
* Test clock & analog interfacing

**BabySoC Examples:**

* Simulate PLL clock stability
* DAC output waveform verification
* CPU instruction execution and data flow

Functional modelling **reduces errors**, saves design iterations, and improves learning outcomes.

<br>

## 🎯 Learning Outcomes from BabySoC

1. CPU instruction and register manipulation
2. Clock synchronization with PLLs
3. Digital-to-analog conversion fundamentals
4. Integration of heterogeneous SoC components
5. Importance of functional modelling

<br>


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

