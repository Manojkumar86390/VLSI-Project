# VCO Oscillator Design (180 nm CMOS)

## Overview
This project presents the design, simulation, and layout of a Voltage-Controlled Oscillator (VCO) implemented in 180 nm CMOS technology using Cadence Virtuoso.

## 🧩 Abstract
This project presents the **full-custom design and implementation of a Voltage-Controlled Oscillator (VCO)** using the **180 nm CMOS technology node**.  
The VCO is a crucial building block in PLLs (Phase-Locked Loops), frequency synthesizers, and clock generation systems.  
Unlike semi-custom or synthesized designs, this project follows a **full-custom approach**, focusing on transistor-level design, schematic verification, and physical layout implementation.


## 🎯 Objectives
- To design a **fully functional VCO** operating in the MHz range using **180 nm CMOS technology**.  
- To perform **schematic-level design and simulation** to verify oscillation and frequency tuning.  
- To carry out **layout design** ensuring proper device matching and minimal parasitic effects.  
- To verify **post-layout performance** and compare with schematic simulation results.

## 🏗 Architecture
![Block Diagram](./images/block_diagram.png)


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


### Architecture Description
- **Topology**: Current-starved ring oscillator
- **Stages**: 5 inverter stages for 180° phase shift
- **Control**: Vctrl adjusts current in starved transistors
- **Output**: Buffered differential outputs

### Key Components
- **MP1-MP5**: PMOS current starving transistors (W=2μ, L=180n)
- **MN1-MN5**: NMOS current starving transistors (W=1μ, L=180n)  
- **MP11-MP15**: PMOS inverter transistors (W=5μ, L=180n)
- **MN11-MN15**: NMOS inverter transistors (W=2μ, L=180n)
- **Output Buffer**: Enhanced drive strength inverters

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

## Documentation
- [Design Specifications](docs/design_specifications.md)
- [Simulation Data](simulations/vco_output_data.csv)

## Quick Start
1. Open schematic files in `schematic/` folder
2. Run simulation scripts from `simulations/scripts/`
3. View layout files in `layout/` folder
4. 
### Layout | Post Layout
![VCO Layout ](layout/vcolayout.png)

## Simulation Results

### Transient Analysis
![VCO Transient Response](simulations/vco_graph.png)



### Frequency vs Control Voltage
![Frequency Tuning Characteristics](simulations/vco_frequency_vs_vctrl.png)



## Author
**Manojkumar86390**  
VLSI Design Engineer


