---
title: "RISC-V Single-Cycle CPU Tapeout on Sky130 PDK"
description: "Full RTL-to-GDS tapeout of a single-cycle RV32I RISC-V CPU on SkyWater 130nm open PDK using Cadence Genus, Innovus, and Tempus. Achieved timing closure across FF/SS/TT corners with comprehensive formal verification using JasperGold."
github: "https://github.com/aaryanvdhawan/RISC-V_CPU_RTL_Design_Verification" 
layout: single
order: 1
---

## Project Overview

**Tapeout on SkyWater 130nm PDK (Sky130)**:
- **RTL Design & Verification** : Verilog RTL for full RV32I base ISA (single-cycle architecture)
- **Synthesis & Optimization** : Cadence Genus (timing-driven, multi-corner: FF/SS/TT)
- **Physical Design** : Cadence Innovus (PnR, CTS, power grid) + Tempus (post-layout STA)
- **Cell Count** : 21,817 standard cells
- **Total Area** : 334.9K μm²
- **Power Consumption** : ~15.9 mW (fast corner; ~10–16 mW range across corners)
- **Timing** : Met setup timing at 25 ns clock period (40 MHz target) across all corners
  - Slow (ss_1.62_125): +3.2 ns slack
  - Typical (tt_1.8_25): +13 ns slack
  - Fast (ff_1.98_0): +17 ns slack
- **Formal Verification** : UVM-lite + property-based formal checks (Cadence JasperGold & Xcelium)
  - 40+ RV32I instructions fully proven
  - 100% proof convergence, 98% coverage
  - 80% reduction in debug effort
- **Automation** : Custom Makefile script for C-to-LLVM IR disassembly using riscv64-gcc-elf toolchain (80% flow time reduction)

**Additional Achievements**:
- Instruction and data memories synthesized as flop arrays (no hard macros)
- Critical path dominated by PC → instruction fetch/decode → ALU (32-bit adder chain) → write-back
- Full GDS generated and ready for tapeout submission (e.g., via Tiny Tapeout, Google MPW shuttle, or academic shuttle)
