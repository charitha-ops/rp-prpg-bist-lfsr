# rp-prpg-bist-lfsr
Verilog implementation of a 16-bit low-power reconfigurable pseudorandom pattern generator for BIST.
# Design of a 16-bit Low-Power Reconfigurable LFSR for BIST

## Overview

This project implements a Reconfigurable Pseudorandom Pattern Generator (RP-PRPG) for Built-In Self-Test (BIST) applications. The design aims to reduce switching activity during digital circuit testing using dual LFSRs, controller-based selection, zero-forcing logic, and an eight-stage pipeline.

The design is developed in Verilog/SystemVerilog and verified through simulation in Vivado.

## Key Features

- Dual-source LFSR architecture.
- Controller-based switching between LFSR sources.
- Zero-forcing mechanism to reduce output transitions.
- Eight-stage pipeline for pattern propagation.
- Fault injection and fault detection logic.
- Simulation-based comparison against a conventional LFSR.

## Architecture

The system includes two LFSRs, selection logic, a controller, a zero-forcing block, an eight-stage pipeline, a fault injector, and a fault detector.

See `docs/architecture.png` for the system block diagram.

## Simulation Results

The following results are reported in the project simulation:

| Metric                | Conventional LFSR | RP-PRPG           |
|                       |                   |                   |
| Toggle count          | 196               | 149               |
| Relative toggle count | 100%              | Approximately 76% |

The reported reduction in toggle count is approximately 24%, calculated as:

`((196 - 149) / 196) × 100 ≈ 23.98%`

The fault-detection test reported detection in 20 out of 20 tested cycles.

These are simulation results under the project's test conditions. Toggle-count reduction is not, by itself, a direct measurement of total FPGA or silicon power savings.

## Tools Used

- Verilog/SystemVerilog
- AMD Xilinx Vivado
- HDL simulation and waveform analysis

## Repository Structure

- `rtl/` — RTL design modules
- `testbench/` — simulation testbench
- `results/waveforms/` — simulation waveforms
- `results/reports/` — result screenshots and reports
- `docs/` — block diagram and documentation

## How to Run

1. Open AMD Xilinx Vivado.
2. Create or open an RTL project for the target device.
3. Add the design source files from `rtl/`.
4. Add the testbench from `testbench/` as a simulation source.
5. Set the testbench as the simulation top module.
6. Run behavioral simulation.
7. Inspect the output waveforms and compare switching activity.

The exact top-module name and any additional setup depend on the uploaded source files.

## Limitations

- Results depend on the simulation length, initial conditions, and toggle-counting method.
- Lower output toggle count does not guarantee the same percentage reduction in total power.
- The reported fault-detection result applies to the tested fault scenarios; comprehensive fault coverage requires further testing.
- FPGA resource and power measurements should be reported separately when available.

## Team

- Charitha S Jain
- Kirti Giriraju
- Krisha Arveti
- Manasa

## Future Scope

- Validate the design on physical FPGA hardware.
- Measure implementation-level power and resource utilization.
- Evaluate additional fault models and fault coverage.
- Explore further switching-activity optimization.

