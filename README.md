# Week-2-BabySoC-Fundamentals-Functional-Modelling


# 🎓 BabySoC – Learning-Oriented RISC-V System-on-Chip (SoC)

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

**Key Advantages:**

| Advantage            | Description                                                                 |
| -------------------- | --------------------------------------------------------------------------- |
| **Compact**          | Reduces PCB size, allowing portable devices like smartphones and wearables. |
| **Energy Efficient** | Close proximity of components reduces interconnect energy.                  |
| **High Performance** | Short internal data paths allow faster computation.                         |
| **Cost Effective**   | Manufacturing one chip is cheaper than multiple ICs.                        |
| **Reliable**         | Fewer discrete components mean fewer points of failure.                     |

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

1. **Microcontroller-based SoC** – simple control tasks, low power.
2. **Microprocessor-based SoC** – supports OS and multitasking.
3. **Application-Specific SoC** – optimized for tasks like AI, graphics, or networking.

BabySoC is a **learning-oriented microprocessor-based SoC**, simplified for educational use.

<br>

## 🍼 Introduction to BabySoC

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
<img src="placeholder_for_babysoc_architecture.png" alt="BabySoC Architecture Diagram" width="600"/>
</div>

### RVMYTH CPU

* **Instruction execution & control unit**
* **Register r17** cycles digital data to DAC
* Enables continuous **digital-to-analog conversion**

<br>

### Phase-Locked Loop (PLL)

<div align="center">
<img src="placeholder_for_pll_block.png" alt="PLL Block Diagram" width="500"/>
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
<img src="placeholder_for_dac_block.png" alt="DAC Diagram" width="500"/>
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

## 💻 GitHub Showcase

* Include **block diagrams**, **waveform outputs**, and **timing diagrams**
* Document **simulation results** for DAC outputs
* Showcase **RISC-V instruction tests**

<br>

## 📚 References

* [RISC-V Specifications](https://riscv.org/specifications/)
* [SkyWater Sky130 PDK](https://skywater-pdk.readthedocs.io/)
* Weste & Harris, *CMOS VLSI Design*
* BabySoC GitHub Repository: `[Insert Link]`

<br>

✅ **Notes for Enhancement:**

* Add **colorful GIFs** showing DAC outputs
* Include **interactive diagrams** for CPU, PLL, DAC
* Embed **code snippets** of testbench simulation
* Use **badges for license, build, and coverage**



## 🌟 VSDBabySoC – Fundamentals of System-on-Chip (SoC) Design

Welcome to **VSDBabySoC**, an educational, compact RISC-V SoC designed for learning the core principles of System-on-Chip (SoC) design. This README explains SoC fundamentals, BabySoC’s architecture, simulation workflow, and how it bridges digital and analog domains.

<br>

## 🧐 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** is essentially an entire computer integrated into a single silicon chip. It combines:

* **CPU** – Central Processing Unit
* **Memory** – RAM, ROM/Flash
* **I/O Interfaces** – USB, sensors, displays
* **GPU/DSP** – Graphics & signal processing
* **Power Management** – Efficient energy usage
* **Connectivity** – Wi-Fi, Bluetooth, 5G, secure data links

This integration enables **compact, energy-efficient, high-performance, and cost-effective** devices like smartphones, wearables, IoT gadgets, and embedded systems.

<br>

## 🎯 Why SoCs?

| Feature                  | Benefit                                             |
| ------------------------ | --------------------------------------------------- |
| 📦 **Compactness**       | Ideal for mobile & embedded devices                 |
| 🔋 **Energy Efficiency** | Extends battery life in wearables, IoT, smartphones |
| ⚡ **High Performance**   | Reduced latency with on-chip communication          |
| 💰 **Cost-Effective**    | Single chip replaces multiple discrete components   |

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

<br>

## 🔥 Types of SoCs

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

## 📂 Project Structure

```
VSDBabySoC/
├── src/
│   ├── include/      # Header files (*.vh)
│   ├── module/       # Verilog + TLV modules
│   │   ├── vsdbabysoc.v   # Top-level module
│   │   ├── rvmyth.v       # CPU
│   │   ├── avsdpll.v      # PLL
│   │   ├── avsddac.v      # DAC
│   │   └── testbench.v    # Testbench
└── output/           # Simulation outputs
```

<br>

## 🛠️ Setup & TL-Verilog Conversion

1. **Clone the Project**

```bash
cd ~/VLSI
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
mkdir -p output/pre_synth_sim
iverilog -o output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I src/include -I src/module \
  src/module/testbench.v

cd output/pre_synth_sim
./pre_synth_sim.out
gtkwave pre_synth_sim.vcd
```

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

## 🚀 Future Work

* Enable **firmware execution from memory**
* Python-based tool to convert C programs → hexadecimal → CPU memory
* Dynamic program execution without hardcoded instructions

<br>

### 💡 Summary

**VSDBabySoC** provides a **hands-on, simplified learning platform** for:

* SoC fundamentals (CPU, memory, PLL, DAC)
* Functional modeling → RTL → simulation workflow
* Digital-to-analog interfacing
* Understanding clock synchronization, instruction execution, and SoC integration

This small-scale SoC mimics real-world SoC design flows, making it **ideal for educational purposes** before tackling complex, industrial-scale designs.



Do you want me to do that next?

