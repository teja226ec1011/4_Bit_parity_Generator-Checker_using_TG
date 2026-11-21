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

This section summarizes the numerical information that can be read from the repository waveform and the additional Cadence Virtuoso screenshots supplied with the project. Values that cannot be extracted from the available plots or screenshots are left as **Not available**.

### 15.1 Simulation and input timing

The transient waveform image in the repository shows a simulation time range of approximately 0–400 ns. Input A has an approximately 20 ns full period (about 10 ns between successive toggles).

| Parameter | Result | Basis |
|---|---:|---|
| Transient simulation window | 0–400 ns | Time axis of the waveform screenshot |
| Input A period | ≈20 ns | Approximate interval between equivalent edges |
| Input A frequency | ≈50 MHz | f = 1/T = 1/(20 ns) |
| Input A half-period | ≈10 ns | Approximate interval between successive toggles |
| Supply voltage / logic swing | Not readable with sufficient certainty | Waveform image does not provide a reliable numeric scale in the available copy |

**Important:** 50 MHz is the input stimulus frequency used in the displayed testbench. It is not a measured maximum operating frequency of the parity circuit.

### 15.2 Timing parameters

| Parameter | Result | Explanation |
|---|---:|---|
| Propagation delay (t_pd) | Not available | The waveform image does not provide sufficiently precise, readable input/output threshold-crossing coordinates |
| Low-to-high delay (t_PLH) | Not available | Requires input-to-output 50% crossing measurement for a rising output |
| High-to-low delay (t_PHL) | Not available | Requires input-to-output 50% crossing measurement for a falling output |
| Contamination delay (t_cd) | Not available | Requires the minimum observed input-to-output delay |
| Setup delay (t_setup) | N/A | The implemented parity generator/checker is combinational and has no clocked storage element |
| Hold delay (t_hold) | N/A | The implemented parity generator/checker is combinational and has no clocked storage element |
| Clock skew (t_skew) | N/A | No clock tree or clocked endpoints are part of this design |
| Maximum frequency (F_max) | Not characterized | The 50 MHz testbench input rate does not establish the circuit's maximum reliable operating frequency |

For measured transitions, the average propagation delay is commonly calculated as:

`t_pd = (t_PLH + t_PHL) / 2`

The worst-case propagation delay is the larger of the measured rising and falling delays.

### 15.3 Power, PDP, and EDP

| Parameter | Result | Calculation / measurement requirement |
|---|---:|---|
| Static power | Not available | `P_static = V_DD × I_leak`; requires static supply-current measurements |
| Dynamic power | Not available | Requires transient supply-current integration or justified activity and capacitance data |
| Average power | Not available | `P_avg = (1/T) × ∫ V_DD I_DD(t) dt` over a representative interval |
| Power-delay product (PDP) | Not available | `PDP = P_avg × t_pd` |
| Energy-delay product (EDP) | Not available | `EDP = P_avg × t_pd²` |

The supplied waveform is a logic transient plot, not a supply-current or power waveform. Therefore, static power, dynamic power, PDP, and EDP cannot be numerically extracted from it.

### 15.4 Device parameters visible in the Virtuoso screenshots

The supplied device-property screenshots (PDF pages 9–11) show the GPDK090 NMOS and PMOS instance properties. The readable entries include:

| Device property | NMOS | PMOS |
|---|---:|---:|
| Technology/model library | gpdk090 | gpdk090 |
| Cell | nmos1v | pmos1v |
| Channel length (L) | 100 nm | 100 nm |
| Total width (W) | 120 nm | 120 nm |
| Number of fingers | 1 | 1 |
| W/L ratio | 1.2 | 1.2 |

These are transistor instance dimensions visible in the screenshots; they are not the overall chip dimensions.

### 15.5 Pre-layout and post-layout simulation

| Stage | Available evidence | Result |
|---|---|---|
| Pre-layout simulation | Transient waveform image in the repository | Functional waveform is shown; quantitative delay and power values are not readable |
| Post-layout simulation | Physical layout and DRC/LVS screenshots | Layout verification evidence is present; no extracted post-layout transient or power report is supplied |
| Pre-/post-layout comparison | No paired measurement reports | Delay and power difference cannot be calculated |

A quantitative post-layout result requires parasitic extraction (PEX) followed by transient and power simulation under the same input vectors, supply, load, process corner, and temperature as the pre-layout run.

### 15.6 Layout verification, area, and aspect ratio

The supplied Cadence screenshots show the completed layout and a DRC result dialog reporting **“No DRC errors found.”** The LVS debug screenshots are included as evidence of the schematic-versus-layout verification flow.

| Parameter | Result |
|---|---:|
| DRC violations shown in result dialog | 0 |
| Layout width | Not available |
| Layout height | Not available |
| Layout area | Not available |
| Aspect ratio | Not available |

The layout boundary is visible in the screenshots, but its numeric width and height are not legible. A reliable area cannot be calculated from a screenshot without a readable dimension or scale.

`Layout area = Width × Height`

`Aspect ratio = Width / Height`

### 15.7 Summary of currently extractable results

| Metric | Result |
|---|---:|
| Input A frequency | ≈50 MHz |
| Input A period | ≈20 ns |
| Transient plot time span | 400 ns |
| NMOS channel length | 100 nm |
| NMOS total width | 120 nm |
| PMOS channel length | 100 nm |
| PMOS total width | 120 nm |
| NMOS and PMOS W/L | 1.2 |
| DRC errors shown | 0 |
| t_pd, t_PLH, t_PHL | Not available from readable plot coordinates |
| Contamination delay | Not available |
| F_max | Not characterized |
| Static and dynamic power | Not available |
| PDP and EDP | Not available |
| Setup, hold, clock skew | N/A for this combinational design |
| Post-layout delay/power | Not available |
| Chip area and aspect ratio | Not available |

**Measurement note:** The numerical timing, power, and physical dimensions listed as unavailable require Cadence calculator/measurement outputs, supply-current data, PEX reports, or readable layout boundary dimensions. They are not inferred from the logic waveform or layout appearance.

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
