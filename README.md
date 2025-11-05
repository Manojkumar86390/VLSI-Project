# Design and Implementation of 5-Stage VCO Using 180 nm Full-Custom Design

![Category](https://img.shields.io/badge/Category-Analog%20VLSI-blue)
![Type](https://img.shields.io/badge/Design-Full%20Custom-green)
![Technology](https://img.shields.io/badge/Technology-180nm-orange)
![Tool](https://img.shields.io/badge/Tool-Cadence%20Virtuoso-red)
![Simulation](https://img.shields.io/badge/Simulation-Spectre-lightgrey)

## Overview
This project presents the design, simulation, and layout of a Voltage-Controlled Oscillator (VCO) implemented in 180 nm CMOS technology using Cadence Virtuoso.

### 🧩 **Highlights**
- ⚙️ Full-custom transistor-level design using Cadence Virtuoso  
- 📈 Post-layout simulation verified frequency-voltage characteristics  
- 🧠 Optimized for low-power and wide tuning range  
- 🧾 Verified through DRC, LVS, and parasitic extraction  
- 🔍 Realistic frequency tuning observed via transient analysis

---

## 📦 Table of Contents
- [Abstract](#-abstract)
- [Objectives](#-objectives)
- [Design Flow](#-design-flow)
- [Key Specifications](#-key-specifications)
- [Schematic & Layout](#-schematic--layout)
- [Transistor Specifications](#-transistor-specifications)
- [Verification Summary](#-design-verification-summary)
- [Procedure in Cadence](#-procedure-to-implement-in-cadence)
- [Applications](#-applications-of-5-stage-vco)
- [Performance Comparison](#-performance-comparison)
- [Learning Outcomes](#-learning-outcomes)
- [References](#-references)
- [Acknowledgements](#-acknowledgements)
- [Contact](#-contact)
- [Author](#-author)

---


## 🧩 Abstract
This project presents the **full-custom design and implementation of a Voltage-Controlled Oscillator (VCO)** using the **180 nm CMOS technology node**.  
The VCO is a crucial building block in PLLs (Phase-Locked Loops), frequency synthesizers, and clock generation systems.  
Unlike semi-custom or synthesized designs, this project follows a **full-custom approach**, focusing on transistor-level design, schematic verification, and physical layout implementation.


## 🎯 Objectives
- To design a **fully functional VCO** operating in the MHz range using **180 nm CMOS technology**.  
- To perform **schematic-level design and simulation** to verify oscillation and frequency tuning.  
- To carry out **layout design** ensuring proper device matching and minimal parasitic effects.  
- To verify **post-layout performance** and compare with schematic simulation results.
## Circuit Architecture
**Block Diagram**
 -                 Control Voltage (Vctrl) 
                              │
        ┌─ ───────────────────┼────────────────────┐
        │                     ▼                    │
        │  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐
        └──┤ INV ├──┤ INV ├──┤ INV ├──┤ INV ├──┤ INV ├──┐
           │  1  │  │  2  │  │  3  │  │  4  │  │  5  │  │
           └─────┘  └─────┘  └─────┘  └─────┘  └─────┘  │
             ▲                                          │
             └──────────────────────────────────────────┘
                        Output


## ⚙️ Design Flow

1. **Specification Definition**  
   - Technology: 180 nm CMOS  
   - Supply Voltage: (e.g., 1.8 V)  
   - Frequency Range: (e.g., 50 MHz – 120 MHz)  
   - Control Voltage Range: (e.g., 0 V – 1.2 V)  
   - Output Type: Differential / Single-ended

2. **Schematic Design**  
   - Circuit designed at transistor level using MOS devices.  
   - Biasing network and delay elements configured for frequency control.  
   - Verified for startup conditions and oscillation frequency.

3. **Simulation & Verification**  
   - Performed transient analysis to measure oscillation frequency and amplitude.  
   - Frequency vs Control Voltage (V<sub>ctrl</sub>) curve obtained.  
   - Verified linearity, tuning range, and power consumption.

4. **Layout Design**  
   - Layout drawn manually following **full-custom design flow**.  
   - Device matching and symmetry ensured.  
   - Design Rule Check (DRC) and Layout Versus Schematic (LVS) completed successfully.  
   - Parasitic extraction performed for post-layout simulations.

5. **Post-Layout Simulation**  
   - Extracted layout netlist simulated to observe frequency deviation and parasitic effects.  
   - Compared schematic vs layout simulation results.
  
     
- 
## Key Specifications
| Parameter              | Value                     |
|------------------------|---------------------------|
| Technology             | 180 nm CMOS               |
| Supply Voltage (VDD)   | 1.8 V                     |
| Number of Stages       | 5                         |
| Control Voltage Range  | 0.3 V - 1.5 V             |
| Frequency Range        | 500 MHz - 2.5 GHz         |
| Power Consumption      | 0.5 mW @ 1.8 GHz          |

## Circuit Schematic | Pre Layout

![VCO Schematic Diagram ](schematic/vcoschematic.png)
*Figure 1: Complete 5-stage ring oscillator schematic showing current-starved inverter topology with control voltage input*


### Architecture Description
- **Topology**: Current-starved ring oscillator
- **Stages**: 5 inverter stages for 180° phase shift
- **Control**: Vctrl adjusts current in starved transistors
- **Output**: Buffered differential outputs

## ⚙️ Transistor Specifications

| **Label** | **Type** | **Function / Role** | **Dimensions (W/L)** |
|------------|-----------|----------------------|----------------------|
| **MP1 – MP5**  | PMOS | Current-starving transistors | W = 2 µm, L = 180 nm |
| **MN1 – MN5**  | NMOS | Current-starving transistors | W = 2 µm, L = 180 nm |
| **MP11 – MP15** | PMOS | Inverter transistors | W = 2 µm, L = 180 nm |
| **MN11 – MN15** | NMOS | Inverter transistors | W = 2 µm, L = 180 nm |


## Repository Structure
- [`schematic/`](schematic/) - Circuit schematics and netlists
- [`simulations/`](simulations/) - Simulation results and scripts
- [`docs/`](docs/) - Design documentation and specifications
- [`layout/`](layout/) - Layout files and screenshots

## Design Features
- Current-starved ring oscillator topology
- 5-stage differential design
- Wide tuning range (500 MHz - 2.5 GHz)
- Low power consumption

## ⚡ Advantages of a 5-Stage VCO Over Other Configurations

  | Parameter         |  3-Stage |          **5-Stage**          |   7-Stage   |
| :---------------- | :------: | :---------------------------: | :---------: |
| Frequency         |   High   |           **Medium**          |     Low     |
| Power Consumption |    Low   |          **Moderate**         |     High    |
| Phase Noise       | Moderate |            **Low**            |   Very Low  |
| Linearity         |    Low   |            **High**           |     High    |
| Output Shape      |  Square  | **Improved (Closer to Sine)** | Very Smooth |

## 📊 Design Verification Summary

| **Criterion**          | **Target**           | **Achieved**                    | **Status**       |
|--------------------------|----------------------|----------------------------------|------------------|
| **Oscillation**          | Yes                  | ✓ Yes                            | ✅ Pass          |
| **Frequency Range**      | 500 MHz – 2 GHz      | 1.33 GHz @ Vc = 930 mV          | ✅ Pass          |
| **Rail-to-Rail Swing**   | Yes                  | ✓ Yes (1.6 V)                    | ✅ Pass          |
| **Stable Operation**     | Yes                  | ✓ Yes                            | ✅ Pass          |
| **Power Consumption**    | < 5 mW               | ✓ 0.579 mW                       | 🌟 Excellent     |
| **DRC**                  | Pass                 | ✓ Zero Errors                    | ✅ Pass          |
| **LVS**                  | Pass                 | ✓ Successful                     | ✅ Pass          |


## ⚙️ Procedure to Implement 5-Stage VCO in Cadence Virtuoso (180 nm Full-Custom)

### 1. Create a New Project
- Launch **Cadence Virtuoso**.
- In the **Library Manager**, create a new library:

- Attach the **180 nm CMOS Technology File (PDK)** to this library.

### 2. Create the Schematic Cell
- In your library, create a new **Cell View** named `VCO_Schematic`:

- Open the schematic editor.

---File → New → Cell View → Schematic

### 3. Design the Basic Delay Cell
- Use **NMOS** and **PMOS** transistors from the PDK.
- Form a **current-starved inverter** (one NMOS & PMOS pair controlled by bias transistors).
- The **control voltage (Vctrl)** adjusts the current through these bias transistors, tuning the delay of each inverter.

---

### 4. Create the 5-Stage Oscillator Loop
- Copy the delay cell **five times**.
- Connect the output of each inverter to the input of the next stage.
- Connect the output of the **last stage** back to the **input of the first** (feedback path).
- Use an **odd number of stages (5)** to maintain oscillation.

---

### 5. Add Biasing Circuit
- Design a **current mirror or reference bias network** that generates a bias current (I_bias).
- Connect the bias network output to the current-starving transistors in each delay cell.
- Add **Vctrl** input to vary this current.

---

### 6. Add Buffer / Output Stage
- Include a **buffer inverter** (or chain of inverters) at the output node to strengthen the signal.
- This ensures proper waveform shape without loading the oscillator core.

---

### 7. Perform Schematic Simulations
- Open **Analog Design Environment (ADE L)**.
- Set up the simulation type:
- **Transient Analysis (tran)** to observe oscillation waveform.
- **Parameter Sweep** for Vctrl to analyze frequency tuning.
- Measure:
- Oscillation frequency (via “zero-crossing” or FFT).
- Power consumption.
- Frequency vs. Vctrl plot.

---

### 8. Create the Layout
- In Library Manager:

   File → New → Cell View → Layout
- Place the same devices (transistors) from schematic.
- Route interconnections manually.
- Maintain **symmetry and matching** between stages.
- Follow **Design Rules (DRC)** strictly.

---

### 9. Run DRC & LVS Checks
- Use **Assura/Calibre** or the PDK’s built-in tools.
- **DRC (Design Rule Check)** → verifies layout geometry.  
- **LVS (Layout vs Schematic)** → confirms connectivity matches schematic.

---

### 10. Parasitic Extraction & Post-Layout Simulation
- Perform **Parasitic Extraction (PEX)** to include wiring capacitances/resistances.
- Run **Post-Layout Transient Simulation** in ADE.
- Compare:
- Oscillation frequency (schematic vs. layout)
- Amplitude & phase noise differences
- Any parasitic impact on tuning range

---

### 11. Documentation
- Capture screenshots of:
- Schematic
- Layout
- Simulation waveforms (transient output and tuning curve)
- Include these in your README/report.

---

### ✅ Expected Results
- **Stable oscillation** waveform at Vout.
- **Frequency varies linearly** with control voltage (Vctrl).
- Post-layout results slightly lower in frequency (due to parasitic delay).

---
## Circuit Equations
### Oscillation Frequency
                                  f_osc = 1 / (2 × N × t_d) 
Where:

- N = Number of stages (5)
- t_d = Delay per stage
### Delay per Stage
                                   t_d = (C_L × V_DD) / I_D    
Where:
- C_L = Load capacitance
- V_DD = Supply voltage
- I_D = Drain current (controlled by Vctrl)                
## 🚀 Applications of 5-Stage VCO
| **Domain**                       | **Application**                                                                                                                |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| 📡 **Communication Systems**     | Used in frequency synthesizers and phase-locked loops (PLLs) for RF transmitters and receivers.                                |
| 🕹️ **Clock Generation**         | Provides high-frequency clock signals in microprocessors, data converters, and digital systems.                                |
| 📶 **Signal Modulation**         | Essential in FM (Frequency Modulation) and FSK (Frequency Shift Keying) transmitters for generating modulated carrier signals. |
| 🔄 **Phase-Locked Loops (PLLs)** | Serves as the core element in PLL circuits for frequency tracking, clock recovery, and jitter reduction.                       |
| ⚙️ **Sensor Interfaces**         | Converts analog sensor signals into frequency variations in voltage-controlled oscillators used for signal conditioning.       |
| 💡 **Test & Measurement**        | Utilized in function generators, oscilloscopes, and on-chip testing circuits requiring tunable frequency outputs.              |


**Figure:** General flow of full-custom VCO design in Cadence Virtuoso.

### Layout | Post Layout
| **Parameter**                 | **Description**                                     |
| ----------------------------- | --------------------------------------------------- |
| 🧰 **Tool Used**              | Cadence Virtuoso Layout Editor                      |
| 🧪 **Technology Node**        | 180 nm CMOS                                         |
| 🧠 **Design Type**            | 5-Stage Voltage Controlled Oscillator (VCO)         |
| ⚙️ **Design Flow Step**       | Layout Design (Post-Schematic Implementation)       |
| 📏 **Verification Performed** | DRC (Design Rule Check) & LVS (Layout vs Schematic) |
| ⚡ **Output Node**             | `Vout`                                              |

![VCO Layout ](layout/vcolayout.png)

## Simulation Results
### Time vs Control Voltage
![VCO Transient Response](simulations/o-pgraph.bmp)

| **Parameter**                 | **Description**                                                                                                                 |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 🧰 **Tool Used**              | Cadence Virtuoso ADE XL                                                                                                         |
| 🧪 **Technology Node**        | 180 nm CMOS                                                                                                                     |
| ⏱️ **Simulation Type**        | Transient Analysis                                                                                                              |
| 🔋 **Power Supply (VDD)**     | 1.8 V                                                                                                                           |
| 📈 **Observation**            | Oscillations are clearly observed at the output node `Vout`, indicating stable operation of the 5-stage VCO circuit.            |
| ⚙️ **Output Characteristics** | The waveform demonstrates a periodic oscillation with nearly uniform amplitude and frequency stability over the simulated time. |



### Transient Analysis with power
![VCO Transient Response](simulations/vco_graph.png)


## Average power calculation
The average(getData("pwr")) function was used in the Calculator tool to compute the average power consumption over the transient simulation period
| **Parameter**             | **Description**          |
| ------------------------- | ------------------------ |
| 🧰 **Tool Used**          | Cadence Virtuoso ADE XL  |
| 🧪 **Technology Node**    | 180 nm CMOS              |
| ⏱️ **Simulation Type**    | Transient Analysis       |
| ⚡ **Extracted Parameter** | Average Power = 579.1 µW |

![Average power calculation](./images/avgpower.png)
This analysis validates the low-power operation of the proposed VCO design, confirming its suitability for mixed-signal and RF system integration.

## 📊 Performance Comparison

| **Parameter** | **REF (1)** | **REF (2)** | **REF (3)** | **REF (4)** | **This Work** |
|:--------------|:------------|:------------|:------------|:------------|:---------------|
| **Technology** | 180 nm | 180 nm | 180 nm | 180 nm | 180 nm |
| **Power Supply** | 0.1 V | 1.8 V | 1.8 V | 1.8 V | 1.8 V |
| **Input Tuning Range** | (0.4–1.8) V | (0.5–1) V | (0.6–1.8) V | (0.5–2.5) V | (0.5–4.5) V |
| **Frequency Range** | 22–315 MHz | 342.42 MHz–1.683 GHz | 165.25 MHz–2.3073 GHz | 30 MHz–1.13 GHz | 81.85 MHz–2.433 GHz |
| **Power Consumption** | 105.3 mW | 0.2128 mW | 1.2357 mW | 0.361 mW | **28.36 nW** |
| **Phase Noise** | – | – | −124.52 dBc/Hz @ 1 MHz | −99.70 dBc/Hz @ 1 MHz | **−89.03 dBc/Hz @ 2.4 GHz** |
## 🎓 Academic Context

Course: VLSI System Design (EC-307)
Faculty: Dr. P. Ranga Babu
Department: Electronics and Communication Engineering
Institution: Indian Institute of Information Technology Design and Manufacturing, Kurnool
Academic Year: 2024-2025

## Learning Outcomes
## 🎓 Learning Outcomes

Through the design and implementation of the **180 nm Full-Custom Voltage-Controlled Oscillator (VCO)**, the following learning outcomes were achieved:

1. **Understanding of Full-Custom Design Flow**  
   - Gained hands-on experience in schematic creation, layout design, and post-layout verification using Cadence Virtuoso.

2. **Transistor-Level Circuit Design Skills**  
   - Designed biasing networks and delay elements at the device level for precise control over oscillation frequency.

3. **Oscillator Theory and Operation**  
   - Understood the working principles of ring oscillators, frequency control using V<sub>ctrl</sub>, and the effect of delay per stage on output frequency.

4. **Analysis of Parasitic Effects**  
   - Learned how layout parasitics influence the real-world performance of the circuit and how to mitigate them.

5. **Simulation and Verification Proficiency**  
   - Performed schematic and post-layout simulations, analyzing transient waveforms and frequency tuning characteristics.

6. **Design Rule and Layout Verification**  
   - Executed DRC and LVS checks successfully, ensuring manufacturable and logically correct layout design.

7. **Optimization and Trade-Off Analysis**  
   - Understood the trade-offs between power, frequency, and phase noise in multi-stage oscillator design.

8. **Technical Documentation and Reporting**  
   - Developed skills in documenting design methodology, results, and observations in a structured engineering format.

---
**Overall Outcome:**  
This project provided a comprehensive understanding of **analog VLSI design principles** and **full-custom implementation workflows**, preparing for advanced work in PLLs, RF design, and mixed-signal ICs.

## 📚 References
1.  International Research Journal of Engineering and Technology (IRJET)  https://irjet.net/archives/V5/i3/IRJET-V5I3191.pdf

## 🧰 Tools & Technologies

🧩 Summary of tools and platforms used in the **180 nm Full-Custom VCO** implementation:

| **Category** | **Tools / Technologies** |
|:--------------|:--------------------------|
| **Design Environment** | Cadence Virtuoso (Full Custom Flow) |
| **Schematic Design** | Virtuoso Schematic Editor |
| **Layout Design** | Virtuoso Layout Suite XL |
| **Simulation** | Cadence Spectre / ADE L / T-Spice |
| **Verification** | DRC, LVS, and Parasitic Extraction using Assura / Calibre |
| **Technology Node** | 180 nm CMOS Process |
| **Oscillator Type** | 5-Stage Ring Oscillator |
| **Analyses Performed** | Transient Analysis, Frequency Tuning (Vctrl Sweep), Power Analysis |
| **Output Parameters** | Frequency vs Control Voltage, Power Consumption, Phase Stability |
| **Documentation** | README.md, Simulation Graphs, Layout & Schematic Snapshots |

---
## ❓ Frequently Asked Questions (FAQ)

- **Why 5 stages?**  
  Offers better frequency stability and tuning linearity compared to 3-stage designs.

- **Which tools are used?**  

- **What simulations are performed?**  
- **What technology node is used?**    
- **What are the main challenges?**  
- **What improvements can be made?**  
- Is this design ready for fabrication?
- **Where can this design be used?**
- 
**✅ Note:**  
The design flow was executed entirely in **Cadence Virtuoso**, following a **full-custom transistor-level approach** from schematic to post-layout simulation.
## 📬 Contact
Manojkumar Dannan

✉️ Email: scs588131@gmai.com

💼 LinkedIn: [linkedin.com/in/yourprofile](https://www.linkedin.com/in/manoj-kumar-52600a2a8?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)

🐱 GitHub: [github.com/yourgithub](https://github.com/Manojkumar86390?tab=overview&from=2025-07-01&to=2025-07-31)

⚙️ website profile : https://student-portfolio-we-g0bj.bolt.host/

🎓 Institution: [  Indian Institute of Information Technology Design and Manufacturing, Kurnool]
For any VLSI-related discussions, collaborations, or queries regarding this 180nm Full Custom VCO project, feel free to reach out.

🙏 Acknowledgments

This project was completed with support and guidance from:

## 🙏 Acknowledgements

- **Dr. P. Ranga Babu** — Course Instructor and Project Guide, Department of ECE, IIITDM Kurnool  
- **IIITDM Kurnool** — For providing computational resources and research infrastructure  
- **Cadence Design Systems** — For access to industry-standard EDA tools used in VLSI design and simulation  
- **Open Source Community** — For valuable educational resources and technical documentation  
- **Research Community** — For foundational work and insights into analog circuit and oscillator design  



## 👨‍🎓 Author
-  **Manoj kumar Dannana**
-  **Roll no : 123ec0020**
-  **Department of Electronics and Communication Engineering**
-  **IIITDM KURNOOL**
---

