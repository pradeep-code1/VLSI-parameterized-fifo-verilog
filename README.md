# VLSI-parameterized-fifo-verilog
Design and simulation of a parameterized synchronous FIFO memory using Verilog HDL and AMD Vivado 2025.1.

# Parameterized FIFO Memory Design Using Verilog HDL

## Project Overview

This project implements a Parameterized First-In, First-Out (FIFO) memory using Verilog HDL and behavioral modeling.

FIFO is a memory structure in which the first data entered is the first data removed. It is commonly used in digital systems for temporary data storage and data transfer between different modules.

The FIFO design has a default data width of 8 bits and a depth of 16 entries. The design was simulated and synthesized using AMD Vivado 2025.1.

## Objectives

- To design a synchronous FIFO using Verilog HDL.
- To understand FIFO read and write operations.
- To implement read and write pointers.
- To generate FIFO full and empty status flags.
- To verify the design using a Verilog testbench and simulation waveforms.

## Tools and Technologies

- **Hardware Description Language:** Verilog HDL
- **Design Methodology:** Behavioral Modeling
- **Simulation Tool:** Vivado XSim
- **Development Tool:** AMD Vivado ML Edition 2025.1
- **Target Device:** Artix-7 (xc7a35tcpg236-1)

## FIFO Design Specifications

| Parameter | Description | Value |
|---|---|---|
| DATA_WIDTH | Width of data | 8 bits |
| FIFO_DEPTH | Number of entries | 16 |
| Clock | Operation trigger | Rising edge |
| Reset | Clears FIFO status | Active high |
| Full | FIFO is completely occupied | 1 |
| Empty | FIFO has no stored data | 1 |

## Working Principle

The FIFO design contains the following main components:

1. **Memory Array:** Stores the input data.
2. **Write Pointer:** Selects the memory location where new data is stored.
3. **Read Pointer:** Selects the memory location from which data is read.
4. **Counter:** Keeps track of the number of stored data items.
5. **Full Flag:** Indicates that all memory locations are occupied.
6. **Empty Flag:** Indicates that no data is available to read.

Data is written when `wr_en` is enabled and the FIFO is not full. Data is read when `rd_en` is enabled and the FIFO is not empty.

## Simulation and Verification

A separate Verilog testbench (`fifo_tb.v`) was created to verify FIFO functionality.

The following tests were performed:

| Test | Verification |
|---|---|
| Reset Test | Checked whether FIFO becomes empty after reset. |
| Write Test | Wrote 16 data values into FIFO. |
| Full Test | Checked whether the full flag becomes HIGH after 16 writes. |
| Read Test | Read the stored data values. |
| Data Order Test | Verified that data was read in the same order in which it was written (1 to 16). |
| Empty Test | Checked whether FIFO becomes empty after reading all data. |
| Extra Write Attempt | Attempted to write an additional value when FIFO was full. |

## Waveform Verification

Vivado XSim was used to observe the simulation waveforms.

The following signals were observed:

- `clk` – Clock signal
- `rst` – Reset signal
- `wr_en` – Write enable
- `rd_en` – Read enable
- `din` – Input data
- `dout` – Output data
- `full` – FIFO full status
- `empty` – FIFO empty status

The waveform was used to observe the timing of read and write operations, data transfer, and changes in full and empty flags.

The simulation console displayed PASS messages for the reset, full condition, ordered data reading, and empty condition checks.

## Synthesis Results

The design was synthesized using AMD Vivado 2025.1 for an Artix-7 target device.

| Resource | Used | Available | Utilization |
|---|---:|---:|---:|
| LUT | 61 | 20,800 | 0.29% |
| Flip-Flops | 48 | 41,600 | 0.12% |
| I/O Ports | 22 | 106 | 20.75% |

These results are from the recorded Vivado synthesis report.

## Project Structure

```text
VLSI-parameterized-fifo-verilog/
│
├── README.md
│
├── rtl/
│   └── fifo.v
│
├── testbench/
│   └── fifo_tb.v
│
└── reports/
    ├── simulation_waveform.png
    └── utilization_report.png
```

## How to Run the Project

1. Open AMD Vivado.
2. Create a new RTL project.
3. Add `fifo.v` under Design Sources.
4. Add `fifo_tb.v` under Simulation Sources.
5. Set `fifo_tb` as the simulation top module.
6. Run Behavioral Simulation.
7. Observe the simulation waveform and console output.

## Conclusion

This project helped me understand the basic working of FIFO memory and its implementation using Verilog HDL.

I learned about behavioral modeling, memory arrays, read and write pointers, counters, clock-based operations, and testbench development.

The design was successfully simulated and synthesized using Vivado. Physical FPGA hardware testing has not been performed.

## Future Improvements

- Add simultaneous read and write verification.
- Improve overflow and underflow test cases.
- Test FIFO with different data widths and depths.
- Implement and test the design on an FPGA development board.

## Author

**Pradeep Mishra**



