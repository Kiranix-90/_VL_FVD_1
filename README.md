RTL to GDS Flow – CMOS Inverter using Sky130

This project demonstrates a complete RTL to GDS flow for a CMOS inverter using open-source VLSI tools. The objective of this project is to understand the ASIC design flow starting from Verilog RTL design to layout generation, DRC, and extraction.

This work was done as part of my learning in VLSI design, physical design flow, and open-source EDA tools.

Project Overview

The inverter is designed in Verilog, functionally verified through simulation, synthesized using a standard cell library, and finally verified at the layout level using the Sky130 PDK.

The flow implemented:

RTL Design → Simulation → Synthesis → Layout Verification → Extraction

Tools Used

Icarus Verilog – RTL compilation and simulation

GTKWave – Waveform viewing and functional verification

Yosys – Logic synthesis

Magic VLSI – Layout viewing, DRC, and extraction

Sky130 PDK – Standard cell library and technology files

Linux (Ubuntu) – Development environment

Design Flow
1. RTL Design

A CMOS inverter was implemented using Verilog HDL.

Files:

inverter.v

inverter_tb.v

The testbench applies input stimulus and verifies the output behavior.

2. Simulation

RTL simulation was performed using Icarus Verilog:

Compilation:

iverilog inverter.v inverter_tb.v


Execution:

vvp a.out


Waveform viewing:

gtkwave inverter.vcd


The waveform confirms correct inverter operation.

3. Synthesis

Logic synthesis was performed using Yosys with the Sky130 standard cell library.

Steps:

Read Verilog design

Map logic to standard cells

Generate synthesized netlist

Produce synthesis statistics report

Output files:

Synthesized netlist

Synthesis report

4. Layout and DRC Verification

Layout and verification were performed using Magic VLSI.

Steps:

Load Sky130 technology file

Open inverter layout

Perform DRC check

Fix violations if present

Command used:

magic -T sky130A.tech


Result:

No DRC errors found

5. Extraction

Layout extraction was performed to generate SPICE netlist.

Commands used in Magic:

extract all
ext2spice lvs


This step verifies connectivity and prepares the design for LVS and further verification.

Project Directory Structure

Example structure:

rtl2gds_inverter/
│
├── inverter.v
├── inverter_tb.v
├── inverter.vcd
├── synth.ys
├── inverter_gate.v
├── inverter.spice
├── inverter.mag
├── inverter.gds
└── reports/

Results

Functional simulation successful

Correct synthesis using Sky130 cells

Layout loaded successfully in Magic

DRC passed

Extraction completed

Learning Outcomes

Through this project, I learned:

Basics of ASIC design flow

RTL simulation and verification

Standard cell synthesis

Layout verification using Magic

Working with Sky130 PDK

Open-source RTL to GDS workflow

Future Improvements

Perform LVS verification

Timing analysis

Design larger combinational circuits

Implement full digital blocks

Author

Kiran Gorajanal
