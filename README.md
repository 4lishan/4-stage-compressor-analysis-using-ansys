# Static and Modal Analysis of a 4-Stage Axial Compressor

## Overview
This repository documents the numerical analysis of a multistage axial compressor, performed using Ansys Mechanical. The study includes **static analysis** (stress and deformation distribution), **modal analysis** (natural frequencies and mode shapes), and **prestressed modal analysis** under cyclic symmetry conditions.

The compressor comprises four axial stages modeled as a multistage cyclic symmetric system to reduce computational effort. The study aims to evaluate the structural performance under operational loads, identify mode shapes, and assess the influence of prestress conditions on natural frequencies.

---

## Model Description

### Geometry and Cyclic Symmetry
The compressor model includes **4 axial stages**, each modeled with sector counts as follows:

| Stage | Sector Count |
|-------|--------------|
| 1     | 43           |
| 2     | 48           |
| 3     | 54           |
| 4     | 30           |

- **Cyclic symmetry** was used to investigate sector-level behavior and minimize computational resources.
- Stage 4 is **fixed** (boundary condition), while stages 1–3 were subjected to mechanical and thermal loads.

### Loading and Boundary Conditions
- **Rotational Speed**: 1000 rad/s applied globally to the assembly.
- **Pressure Loads**:
  - Stage 1: 1 MPa.
  - Stage 2: 1.5 MPa.
  - Stage 3: 2 MPa.
- **Thermal Loads**:
  - Stage 1: 200°C.
  - Stage 2: 250°C.
  - Stage 3: 300°C.

---

## Analysis Methodology

### 1. Static Analysis
- **Objective**: Identify stress and deformation patterns under applied loads.
- **Solver**: Ansys Static Structural.
- **Outputs**: 
  - Von Mises stress distribution.
  - Total deformation magnitude.

### 2. Modal Analysis
- **Objective**: Extract natural frequencies and mode shapes for harmonic indices 0, 1, and 2.
- **Method**: Determines resonant frequencies for different cyclic symmetry constraints.
- **Harmonic Indices**: 0, 1, 2.
- **Outputs**: Natural frequencies and deformed mode shapes.

### 3. Prestressed Modal Analysis (Upcoming)
- **Objective**: Evaluate the influence of prestress conditions (from static analysis) on natural frequencies/mode shapes.
- **Method**: Apply static analysis results as preload conditions.
- **Harmonic Indices**: 0, 1, 2.
- **Outputs (Upcoming)**: Preloaded natural frequencies and mode shapes.

---

## Static Analysis Results

### Stress Distribution
![Stress Distribution](./results/static_analysis_stress.png)

- **Maximum Stress**: 2452.8 MPa, observed at critical regions near blade roots and interstage boundaries.
- Stress values are cyclically periodic due to applied symmetric constraints, matching the expected physical behavior of the system.
- Concentrations are typical in regions under combined loading of rotational forces, thermal gradients, and pressure.

### Total Deformation
![Total Deformation](./results/static_analysis_deformation.png)

- **Maximum Deformation**: 1.86 mm, predominantly observed at the leading blade tips of stage 1.
- Deformation decreases towards the fixed boundary (stage 4 rim), with minimal displacement at the hub regions.
- These results confirm structural stability with acceptable deformation limits under the prescribed loading conditions.

---

## Modal Analysis Results

### Natural Frequencies and Mode Shapes
#### Harmonic Index = 0
![Mode Shapes - HI 0](./results/modal_analysis_hi_0.png)

- **Mode 1 Frequency**: 1004.7 Hz.
- **Mode 6 Frequency**: 1989.9 Hz.
- Deformation patterns primarily involve axial and bending modes, indicative of blade flexibility across all 4 stages.

#### Harmonic Index = 1
![Mode Shapes - HI 1](./results/modal_analysis_hi_1.png)

- **Mode 1 Frequency**: 1060.2 Hz.
- **Mode 6 Frequency**: 1349.4 Hz.
- Higher harmonic indices reveal mixed axial-bending motion with more complex deformation patterns in the blade and hub geometry.

#### Harmonic Index = 2
![Mode Shapes - HI 2](./results/modal_analysis_hi_2.png)

- **Mode 1 Frequency**: 829.63 Hz.
- **Mode 6 Frequency**: 1570.4 Hz.
- The higher harmonic behavior highlights interstage vibrational coupling and resonance, with deformation increasingly concentrated near blade tips.

### Observations
- The natural frequencies and mode shapes progressively increase with higher harmonic indices, reflecting the expected structural characteristics of multistage systems.
- The results underscore the importance of evaluating differing harmonic indices to fully capture the vibrational behavior of cyclic symmetric systems.

---

## Repository Structure
- `/models`: CAD files and Ansys project setup.
- `/results`: 
  - `static_analysis`: Stress and deformation plots.
  - `modal_analysis`: Frequency tables and harmonic index mode shapes.
  - `prestressed_modal`: Results will be added soon.
- `/docs`: Additional technical notes and references.

---

## Next Steps and Updates
- Incorporate prestressed modal analysis results.
- Discuss the impact of prestress on natural frequencies (comparison with baseline modal analysis).
- Validate simulation predictions with experimental data (if available).

---

*Last Updated: [Insert Date]*  
*Author: [Your Name/Team Name]*  
*Software: Ansys Mechanical 2023*
