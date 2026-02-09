# RTL to GDS Flow: CMOS Inverter using Sky130

This repository demonstrates a complete **RTL-to-GDSII flow** for a CMOS inverter using open-source VLSI tools and the **Sky130 PDK**. The project covers the end-to-end ASIC design process, from functional Verilog description to physical layout extraction.

---

## 📌 Project Overview
The objective is to implement a fundamental CMOS inverter through a standardized digital design flow. This project validates functional correctness, logic synthesis mapping, and physical design rules using industry-standard open-source tools.

### Design Flow Stages
1. **RTL Design**: Writing the hardware description.
2. **Simulation**: Functional verification of logic.
3. **Synthesis**: Mapping RTL to Sky130 standard cells.
4. **Layout & DRC**: Physical design and design rule checking.
5. **Extraction**: Generating SPICE netlists for post-layout verification.



---

## 🛠 Tools & Technology
| Category | Tool | Description |
| --- | --- | --- |
| **HDL** | Verilog | Hardware Description Language |
| **Simulator** | Icarus Verilog | RTL simulation and compilation |
| **Waveform** | GTKWave | Digital signal visualization |
| **Synthesis** | Yosys | Logic synthesis for Sky130 |
| **Layout** | Magic VLSI | GDSII viewer and DRC tool |
| **PDK** | Sky130 | Google/SkyWater 130nm process |
| **OS** | Ubuntu | Linux-based development environment |

---

## 🚀 Design Implementation

### 1. RTL Design & Simulation
The inverter logic is defined in `inverter.v`. A testbench (`inverter_tb.v`) applies stimulus to verify the truth table.

**Run Simulation:**
```bash
# Compile
iverilog -o inverter_sim inverter.v inverter_tb.v

# Execute
vvp inverter_sim

# View Waveforms
gtkwave inverter.vcd
2. Logic Synthesis
Using Yosys, the high-level Verilog code is converted into a gate-level netlist based on the Sky130 standard cell library.

Key Synthesis Steps:

Read the Verilog file.

Map logic to sky130_fd_sc_hd__inv_1 cells.

Export the synthesized netlist: inverter_gate.v.

3. Physical Layout & DRC
Physical design is performed in Magic VLSI. This ensures the design meets the manufacturing constraints of the 130nm process.

Commands:

Bash
# Open Magic with Sky130 tech file
magic -T sky130A.tech inverter.mag
DRC Check: Run drc check in the Magic console to ensure zero violations.

4. Extraction
Extraction converts the layout back into a netlist format to verify that the physical implementation matches the intended electrical properties.

Magic Commands:

Tcl
extract all
ext2spice lvs
ext2spice
📂 Project Directory Structure
Plaintext
rtl2gds_inverter/
├── src/
│   ├── inverter.v           # RTL source
│   └── inverter_tb.v        # Testbench
├── synth/
│   ├── synth.ys             # Yosys script
│   └── inverter_gate.v      # Synthesized netlist
├── layout/
│   ├── inverter.mag         # Magic layout file
│   └── inverter.spice       # Extracted spice netlist
├── sim/
│   └── inverter.vcd         # Simulation waveforms
└── README.md
🎓 Learning Outcomes
ASIC Flow: Hands-on experience with the complete front-to-back design flow.

PDK Integration: Understanding how to utilize technology files (.tech) and standard cell libraries.

Verification: Mastering DRC (Design Rule Check) and functional verification.

Open Source: Proficiency in using community-driven EDA tools for professional-grade design.

🔮 Future Improvements
LVS (Layout vs Schematic): Implement Netgen to verify the layout against the netlist.

STA (Static Timing Analysis): Use OpenSTA to verify setup/hold times.

P&R: Automate the flow using OpenLane for larger digital blocks.

Author: Kiran Gorajanal
