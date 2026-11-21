# 4-Bit Parity Generator and Checker Using Transmission Gate Logic

## 1. Project Overview

This project focuses on the design and implementation of a **4-Bit Parity Generator and Checker using CMOS Transmission Gate Logic**.

The main objective is to design a digital circuit that generates an even parity bit for 4-bit input data and checks the received data for parity errors.

The complete circuit is designed at the transistor level using NMOS and PMOS transistors in **Cadence Virtuoso IC 6.1.8** with the GPDK 90 nm technology library.

The project includes transistor-level schematic design, XOR gate implementation, transient simulation, physical layout design, and DRC/LVS verification.

---

## 2. Project Objectives

- Design a 4-bit even parity generator.
- Design a parity checker for detecting transmission errors.
- Implement XOR gates using CMOS transmission gate logic.
- Develop transistor-level schematics in Cadence Virtuoso.
- Perform transient analysis to verify circuit functionality.
- Design the physical layout of the complete circuit.
- Perform Design Rule Check (DRC).
- Perform Layout Versus Schematic (LVS) verification.

---

## 3. Software and Technology Used

| Parameter | Description |
|---|---|
| EDA Tool | Cadence Virtuoso |
| Version | IC 6.1.8 |
| Technology Library | GPDK 90 nm |
| Design Type | Full Custom VLSI Design |
| Logic Style | CMOS Transmission Gate Logic |
| Simulation | Transient Analysis |
| Verification | DRC and LVS |

---

## 4. Working Principle

### 4.1 Parity Generator

The parity generator accepts four input bits:

- A
- B
- C
- D

It generates an additional parity bit to make the total number of 1s even.

The Boolean expression for even parity generation is:

**P_GEN = A XOR B XOR C XOR D**

Where:
- P_GEN = Generated parity bit.
- XOR = Exclusive OR operation.

### 4.2 Parity Checker

The parity checker compares the generated parity bit with the received parity bit.

The Boolean expression is:

**ERROR = P_GEN XOR P_RX**

Where:
- P_GEN = Generated parity bit.
- P_RX = Received parity bit.
- ERROR = Error detection output.

| P_GEN | P_RX | ERROR | Result |
|---|---|---|---|
| 0 | 0 | 0 | No parity mismatch |
| 0 | 1 | 1 | Error detected |
| 1 | 0 | 1 | Error detected |
| 1 | 1 | 0 | No parity mismatch |

**Note:** Parity checking detects an odd number of bit errors but cannot detect every possible multiple-bit error.

---

## 5. Block Diagram

The complete circuit consists of two main sections:

1. 4-Bit Parity Generator.
2. Parity Checker.

The design uses four cascaded XOR stages.

---

## 6. Transmission Gate XOR Implementation

The XOR gates are implemented using CMOS transmission gate logic.

A CMOS transmission gate consists of:

- One NMOS transistor.
- One PMOS transistor.

Both transistors are connected in parallel and controlled by complementary signals.

The transmission gate allows both logic HIGH and logic LOW signals to pass effectively.

The XOR function is implemented using transmission gates and CMOS inverters.

### XOR Truth Table

| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

---

## 7. XOR Gate Schematic

The XOR gate was designed at transistor level using CMOS transmission gate logic in Cadence Virtuoso.

The implementation consists of NMOS and PMOS transistors configured to perform the XOR operation.

![XOR Gate Schematic](Images/XOR%20GATE%20Schematic.jpg)

---

## 8. XOR Gate Layout

The physical layout of the XOR gate was created using Cadence Virtuoso Layout Editor.

The layout contains the required transistor structures and interconnections based on the schematic design.

![XOR Gate Layout](Images/XOR_LAYOUT.png)

---

## 9. Complete Parity Generator and Checker Schematic

The complete circuit was constructed by cascading four transmission-gate-based XOR stages.

The first three XOR gates generate the even parity bit, while the fourth XOR gate performs parity checking.

![Complete Parity Generator and Checker Schematic](Images/parity%20generator%20%26%20checker%20schematic.jpg)

---

## 10. Testbench Design

A separate testbench was created to verify the functionality of the complete parity generator and checker circuit.

The testbench provides input combinations to the circuit and allows observation of the generated parity and error detection outputs.

![Parity Generator and Checker Testbench](Images/Parity%20generator%26checker%20TB.jpg)

---

## 11. Transient Simulation Results

Transient analysis was performed in Cadence Virtuoso to verify the functionality of the circuit.

The simulation waveforms are used to observe the input signals, generated parity output, and error detection output.

The expected operation is:

- ERROR = 0 when the generated and received parity bits match.
- ERROR = 1 when the generated and received parity bits differ.

![Parity Generator and Checker Waveform](Images/Parity%20generator%20and%20checker%20waveform.jpg)

---

## 12. Complete Physical Layout

The complete physical layout of the 4-bit parity generator and checker was developed using the individual XOR gate implementation.

The layout represents the complete circuit connectivity, including the generator and checker sections.

![Complete Parity Generator and Checker Layout](Images/partiry%20generator&checker%20layout.jpg)

---

## 13. Design Rule Check (DRC)

Design Rule Check (DRC) was performed to verify that the physical layout follows the manufacturing design rules of the selected technology library.

DRC checks include:

- Minimum spacing requirements.
- Minimum width requirements.
- Contact and via rules.
- Metal routing rules.
- Well and diffusion design rules.

![DRC Check Results](Images/DRC%20Check.jpg)

---

## 14. Layout Versus Schematic (LVS)

Layout Versus Schematic (LVS) verification was performed to compare the physical layout with the corresponding schematic.

It checks whether the layout correctly represents the electrical connections and components of the schematic.

The LVS debugging screenshots are included below for reference.

### LVS Debug Screenshot 1

![LVS Debug 1](Images/LVS%20debug.jpg)

### LVS Debug Screenshot 2

![LVS Debug 2](Images/LVS%20debug_1.jpg)

---

## 15. Timing, Power, and Physical Design Metrics

The repository currently contains a transient waveform screenshot and layout/DRC/LVS screenshots, but it does **not** contain the numerical simulator measurements, supply-current data, or layout dimensions required to report defensible timing, power, and area values. Therefore, unavailable values are marked **Not reported** rather than estimated or fabricated.

### 15.1 Available observation from the transient waveform

The displayed transient plot spans 0–400 ns. The A input toggles at approximately 10 ns intervals (20 ns full period), corresponding to an **input stimulus frequency of approximately 50 MHz**. This is only the applied testbench frequency; it is **not** a measured maximum operating frequency (Fmax).

### 15.2 Timing metrics

| Metric | Result | How it must be measured |
|---|---:|---|
| Propagation delay (t_pd) | Not reported | Measure input-to-output delay at the specified voltage threshold; commonly report the relevant worst-case path |
| Low-to-high delay (t_PLH) | Not reported | Time from the input 50% crossing to output 50% rising crossing |
| High-to-low delay (t_PHL) | Not reported | Time from the input 50% crossing to output 50% falling crossing |
| Contamination delay (t_cd) | Not reported | Minimum input-to-output delay, measured over relevant transitions and input conditions |
| Setup time (t_setup) | N/A for the shown combinational block | The design shown has no clocked storage element; setup time applies to a sequential endpoint |
| Hold time (t_hold) | N/A for the shown combinational block | The design shown has no clocked storage element; hold time applies to a sequential endpoint |
| Clock skew (t_skew) | N/A | No clock network or clocked endpoints are shown |
| Maximum frequency (F_max) | Not determined | Requires a defined synchronous interface/clock constraint or a documented delay-based operating criterion; 50 MHz is only the testbench stimulus |

For a measured path, report both edge delays. A commonly used average propagation delay is:

`t_pd = (t_PLH + t_PHL) / 2`

The worst-case propagation delay should also be stated when comparing timing limits.

### 15.3 Power and energy metrics

| Metric | Result | Required data / calculation |
|---|---:|---|
| Static power | Not reported | Measure leakage supply current with inputs held at defined static states; `P_static = V_DD × I_leak` |
| Dynamic power | Not reported | Measure average switching power from the supply-current waveform, or use `P_dynamic ≈ α × C_eff × V_DD² × f` with justified activity and capacitance |
| Average power | Not reported | Integrate supply power over a representative steady-state interval and divide by the interval |
| Power-delay product (PDP) | Not reported | `PDP = P_average × t_pd` |
| Energy-delay product (EDP) | Not reported | `EDP = P_average × t_pd²` |

PDP and EDP must use power and delay measured under the same supply, process, temperature, load, and input-activity conditions. The current README assets do not include the required supply-current or power-analysis results.

### 15.4 Pre-layout and post-layout simulation

| Simulation stage | Evidence in current repository | Quantitative result |
|---|---|---|
| Pre-layout | One transient waveform screenshot is present, but its simulation stage and measurement setup are not identified | Not reported |
| Post-layout | A complete layout image and DRC/LVS screenshots are present; no post-layout extracted transient/power report is included | Not reported |

A valid comparison requires separate pre-layout and post-layout simulation reports using the same input vectors, supply voltage, load, process corner, and temperature. Post-layout results should use extracted parasitics (PEX).

### 15.5 Layout area and aspect ratio

| Metric | Result | Required data |
|---|---:|---|
| Core/layout width | Not reported | Layout boundary dimensions from Virtuoso |
| Core/layout height | Not reported | Layout boundary dimensions from Virtuoso |
| Layout area | Not reported | `Area = Width × Height` |
| Aspect ratio | Not reported | `Aspect ratio = Width / Height` (state the width/height convention) |

The layout screenshot has no readable dimension annotation or scale, so area and aspect ratio cannot be calculated reliably from the image alone. The DRC screenshot reports no DRC errors, and the LVS screenshots indicate a schematic/layout match; these are verification results, not area measurements.

### 15.6 Data needed to complete the numerical results

To replace the “Not reported” entries with measured values, add the following Cadence Virtuoso outputs to the repository:

1. Transient measurement results (or a CSV waveform export) with input/output 50% crossing times for all relevant transitions.
2. A measurement setup/report for minimum contamination delay and worst-case propagation delay.
3. Supply-current or power-analysis reports for static and switching input conditions.
4. Separate pre-layout and post-layout (PEX) simulation reports.
5. Layout boundary width and height from the Virtuoso ruler or cell properties.
6. The process corner, temperature, supply voltage, output load, and input transition/activity conditions used for each run.

Until these reports are added, the metrics above should be treated as **not characterized**, not as zero.

---

## 16. Applications

- Digital communication systems.
- Data transmission error detection.
- Memory error detection circuits.
- Digital electronic systems.
- VLSI digital circuit design.

---

## 17. Conclusion

The 4-Bit Parity Generator and Checker was designed using CMOS Transmission Gate Logic in Cadence Virtuoso.

The project demonstrates the implementation of XOR-based parity generation and error detection at the transistor level.

The project also provides practical experience in full-custom VLSI design, schematic development, transient simulation, physical layout implementation, and DRC/LVS verification.

---

## 18. Repository Structure

```text
4-Bit-Parity-Generator-and-Checker/
│
├── README.md
│
└── Images/
    ├── DRC Check.jpg
    ├── LVS debug.jpg
    ├── LVS debug_1.jpg
    ├── Parity generator and checker waveform.jpg
    ├── Parity generator&checker TB.jpg
    ├── XOR GATE Schematic.jpg
    ├── XOR_LAYOUT.png
    ├── parity generator & checker schematic.jpg
    └── partity generator&checker layout.jpg
```

---

**Project Title:** 4-Bit Parity Generator and Checker Using Transmission Gate Logic

**EDA Tool:** Cadence Virtuoso IC 6.1.8

**Technology:** GPDK 90 nm

**Domain:** VLSI – Digital IC Design
