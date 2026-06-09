# PRE-DECODER AND COLUMN DECODER DESIGN

## Project Overview

This project focuses on the **design, implementation, and optimization of a Pre-Decoder and Column Decoder for SRAM memory architecture** as part of the **Memory Design and Test** course. The work involves designing an efficient **3:8 pre-decoder architecture**, a **column decoder for MUX16 configuration**, and validating timing constraints including **negative hold time and setup time requirements** under worst-case PVT corners.

The project emphasizes **high-speed memory addressing, area optimization, logical effort-based transistor sizing, layout implementation, and timing verification** while maintaining low input capacitance and satisfying SRAM decoder specifications.

---

## Problem Statement

The objective of this project was to design a **Pre-Decoder and Column Decoder** satisfying the following specifications:

* **Input capacitance < 10 fF**
* **Output loading for 512 rows**
* **Negative hold time at FF / 1.32V / -40°C**
* **Setup time within 500 ps at SS / 1.08V / 125°C**

The decoder architecture was developed for an **8192 × 32-bit SRAM memory**, requiring **13 address bits (A12–A0)** for complete addressing functionality.

---

## Memory Architecture and Addressing Scheme

The SRAM memory consists of **8192 words**, each storing **32 bits**, requiring **13 address bits**.

### Address Bit Distribution

#### Row Selection (A12–A4)

The higher-order address bits are used for **row decoding** using a hierarchical decoding structure:

* **Pre-decoding stage**
* **Post-decoding stage**

The pre-decoding stage converts grouped address inputs into intermediate decoded outputs for efficient row selection.

#### Column Selection (A3–A0)

The lower-order address bits are utilized for **column decoding** corresponding to the **MUX16 architecture**, enabling bitline selection inside the memory array.

This hierarchical structure reduces routing complexity and improves decoder efficiency in large SRAM architectures.

---

## Pre-Decoder Architecture Selection

Multiple pre-decoding configurations were analyzed to determine the best trade-off between:

* Area
* Power Consumption
* Decoder Complexity
* Routing Efficiency

### Explored Configurations

1. **2 × 3:8 Decoder + 1 × 2:4 Decoder + 1 × 1:2 Decoder**
2. **1 × 3:8 Decoder + 3 × 2:4 Decoder**
3. **1 × 3:8 Decoder + 2 × 2:4 Decoder + 2 × 1:2 Decoder**
4. **3 × 3:8 Decoder**

After evaluating **power and area trade-offs**, the **3 × 3:8 decoder configuration** was selected because it provided:

* Minimum power consumption
* Better scalability
* Efficient decoding
* Acceptable area overhead
* Improved row selection for 512-word loading

---

## 3:8 Pre-Decoder Design

A **3:8 pre-decoder with inverter architecture** was implemented and optimized using **Logical Effort based transistor sizing** to improve speed and drive capability.

### Design Methodology

The decoder schematic was developed at transistor level and optimized for:

* Delay reduction
* Proper driving capability
* Low capacitance
* Efficient switching

Logical effort methodology was used to determine optimum PMOS and NMOS transistor widths for balancing rise/fall delays and ensuring timing closure.

### Features

* Optimized transistor sizing
* Improved switching performance
* Low delay decoding
* Scalable decoder architecture
* Suitable for SRAM row selection

---

## Column Decoder Design

The **column decoder** was designed to support **MUX16 memory organization**, enabling efficient **bitline selection**.

### Functionality

The column decoder:

* Selects appropriate bitlines
* Controls data access from SRAM cells
* Reduces routing complexity
* Improves read/write selection efficiency

A **Bitline Selection Box (BL Selection Box)** was incorporated to improve controlled access and decoder functionality.

---

## Simulation and Functional Verification

The designs were verified using **EZ Wave simulations** to validate:

* Functional correctness
* Decoder outputs
* Switching behavior
* Timing characteristics

Waveforms were analyzed to ensure proper decoding operation across different input conditions.

---

## Layout Design and Optimization

### 3:8 Pre-Decoder Layout

The pre-decoder layout was implemented in multiple iterations to improve area utilization.

#### Iteration 1

* Area = **353.24 µm²**

#### Iteration 2

* Area = **287.01 µm²**

The second iteration achieved significant area reduction through:

* Better diffusion sharing
* Optimized transistor placement
* Improved routing strategy

### Column Decoder Layout

The final column decoder layout occupied:

**Area = 591.661 µm²**

Optimization efforts focused on:

* Compact placement
* Reduced routing congestion
* Better area efficiency
* Manufacturable layout design

---

## DRC and LVS Verification

Physical verification was performed to ensure layout correctness.

### DRC (Design Rule Check)

Verified:

* Minimum spacing constraints
* Width rules
* Metal enclosure requirements
* Fabrication compatibility

### LVS (Layout Versus Schematic)

Ensured:

* Layout matched schematic connectivity
* Correct transistor implementation
* Functional correctness

The final layouts were **DRC and LVS clean**, confirming fabrication readiness.

---

## Setup and Hold Time Analysis

Timing analysis was performed for the **3:8 decoder architecture**.

### Setup Time Results

The measured setup time ranged approximately from:

**198 ps to 264 ps**

which successfully satisfies the required specification of:

**Setup Time < 500 ps at SS / 1.08V / 125°C**

### Hold Time Results

The measured hold times were **negative**, ranging approximately from:

**−59 ps to −88 ps**

which successfully satisfies the requirement of:

**Negative Hold Time at FF / 1.32V / −40°C**

### Clock Delay

Observed clock delays:

* **53 ps at SS / 1.08V / 125°C**
* **42 ps at FF / 1.32V / −40°C**

Additionally, the **Tri-State Latch achieved a hold time of −17.7 ps**, helping improve timing performance.

---

## Challenges Faced

During implementation, several practical challenges were encountered:

* Difficulty in determining the optimal sizing for the column decoder.
* Multiple design iterations were required for timing optimization.
* Debugging **LUP/DUP DRC errors** and **sconnect issues** during layout verification.
* Area optimization challenges while implementing **fingered transistors** in both pre-decoder and column decoder designs.
* Balancing **Power, Performance, and Area (PPA)** trade-offs.

---

## Future Improvements

Planned future enhancements include:

* Further reduction in layout area
* Delay optimization for pre-decoder
* Improved PPA optimization
* Better routing efficiency
* Enhanced scalability for larger SRAM architectures

---

## Tools and Technologies Used

* **Cadence Virtuoso** – Schematic and Layout Design
* **EZ Wave** – Waveform and Timing Analysis
* **DRC/LVS Verification Tools** – Physical Verification
* **Logical Effort Methodology** – Transistor Sizing
* **SRAM Memory Architecture Design**

---

## Key Outcomes

✔ Designed an efficient **3:8 Pre-Decoder for SRAM row selection**
✔ Implemented **MUX16 compatible Column Decoder**
✔ Achieved **Input Capacitance < 10 fF**
✔ Satisfied **Negative Hold Time requirement**
✔ Maintained **Setup Time < 500 ps**
✔ Completed **DRC/LVS clean layouts**
✔ Optimized area through multiple layout iterations
✔ Validated decoder functionality through simulations

This project demonstrates a complete **memory decoder design flow**, covering **architecture selection, transistor sizing, layout optimization, timing analysis, and physical verification** for high-performance SRAM systems.
