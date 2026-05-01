# PLFM RADAR System
**Author & Lead Hardware Designer:** muham

## Project Overview
This repository contains the complete hardware design, system architecture, and electromagnetic simulations for a custom high-frequency PLFM (Phase-Locked Frequency Modulation) Radar system. Designed from scratch, the system operates in the X-band (around 10.5 GHz) and encompasses all stages from initial RF/Microwave simulations to final PCB layout and Gerber production files.

## Key Subsystems and Architecture
The radar system is highly modular and divided into several dedicated boards to minimize noise and improve RF performance:

1. **Main Board:** Handles the core data processing, ADC/DAC conversion, and overall system control.
2. **Frequency Synthesizer Board:** Responsible for generating precise chirp signals and local oscillator (LO) frequencies for the RF mixer.
3. **Power Amplifier (PA) Board:** Amplifies the modulated RF signal for the transmit antenna.
4. **Power Management Board:** Distributes clean, low-noise power to all sensitive RF and digital components.
5. **Antennas:** Custom-designed 10.5 GHz quartz slotted waveguide antennas optimized for high directivity.

## Tools & Methodologies Used
- **PCB Design & Schematics:** Advanced multilayer stacks with precise impedance matching (RO4350B substrates).
- **EM Simulations:** openEMS for 3D electromagnetic simulations of the slotted waveguide and via fencing.
- **Signal Processing:** Python (NumPy, Pandas, Matplotlib) for baseband analysis, DAC reconstruction, and chirp generation.

## Directory Structure
- `1_Project_Description/`: Detailed system requirements and technical specifications.
- `2_Functional Diagram & Interconnection Matrices/`: System-level block diagrams and pin mappings.
- `3_Power Management/`: Power tree calculations and voltage regulator designs.
- `4_Schematics and Boards Layout/`: Complete circuit schematics, board layouts, and manufacturing files (Gerbers, BOM, Pick & Place).
- `5_Simulations/`: Scripts and data for IF filters, Anti-Aliasing filters, and 3D antenna simulations.

## Running the Simulations
A Python virtual environment is configured to run the signal processing simulations. To generate a multi-ramp DAC chirp signal output, run:
```bash
python 5_Simulations/DAC_ReconstructionFilter/Generate_ChirpcsvFile.py
```

---
*Designed and developed entirely on this workstation by muham.*
