# Week-2-BabySoC-Fundamentals-Functional-Modelling

## 🌟 VSDBabySoC – Fundamentals of System-on-Chip (SoC) Design

Welcome to **VSDBabySoC**, an educational, compact RISC-V SoC designed for learning the core principles of System-on-Chip (SoC) design. This README explains SoC fundamentals, BabySoC’s architecture, simulation workflow, and how it bridges digital and analog domains.

---

## 🧐 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** is essentially an entire computer integrated into a single silicon chip. It combines:

* **CPU** – Central Processing Unit
* **Memory** – RAM, ROM/Flash
* **I/O Interfaces** – USB, sensors, displays
* **GPU/DSP** – Graphics & signal processing
* **Power Management** – Efficient energy usage
* **Connectivity** – Wi-Fi, Bluetooth, 5G, secure data links

This integration enables **compact, energy-efficient, high-performance, and cost-effective** devices like smartphones, wearables, IoT gadgets, and embedded systems.

---

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

---

## 🔥 Types of SoCs

1. **Microcontroller-based SoC** → Small-scale, low-power control (IoT nodes, appliances)
2. **Microprocessor-based SoC** → Runs OS, multitasking (smartphones, tablets)
3. **Application-Specific SoC (ASIC)** → Domain-optimized for AI accelerators, automotive, networking

---

## 🌀 SoC Design Flow

SoC design progresses through:

1. **Functional Modeling:** Early validation of system behavior; focuses on *what the system should do* rather than hardware specifics.
2. **RTL Design:** Implementation in Verilog/VHDL; describes registers, datapaths, and control logic.
3. **Physical Design:** Synthesis, placement, routing, and fabrication (e.g., Sky130 process).

Functional modeling is critical for avoiding design errors before committing to silicon.

---

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

---

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

---

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

---

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

---

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

---

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

---

## 🛠️ Troubleshooting

* ⚠️ **Module Redefinition:** Include files only once
* 🛤 **Path Issues:** Use absolute paths if relative paths fail
* ⏱ **Waveform Mismatch:** Verify GTKWave format and signals

---

## 🚀 Future Work

* Enable **firmware execution from memory**
* Python-based tool to convert C programs → hexadecimal → CPU memory
* Dynamic program execution without hardcoded instructions

---

### 💡 Summary

**VSDBabySoC** provides a **hands-on, simplified learning platform** for:

* SoC fundamentals (CPU, memory, PLL, DAC)
* Functional modeling → RTL → simulation workflow
* Digital-to-analog interfacing
* Understanding clock synchronization, instruction execution, and SoC integration

This small-scale SoC mimics real-world SoC design flows, making it **ideal for educational purposes** before tackling complex, industrial-scale designs.



Do you want me to do that next?

