
## 📖 Overview

This repository contains two distinct applied engineering reports focusing on internal combustion engine analysis. The project is divided into two main sections:
1.  **Flywheel Dimensioning:** Analytical dimensioning of a flywheel for single-cylinder and multi-cylinder engines based on thermodynamic cycle analysis.
2.  **Engine Test Evaluation & HRR Analysis:** Post-processing of steady-state engine test data and Heat Release Rate (HRR) analysis for a turbocharged compression ignition (CI) engine.

---

## 📂 Report 1: Flywheel Dimensioning

### 🎯 Objective
To regularize the crankshaft speed without affecting engine torque or power by dimensioning an appropriate flywheel. [cite_start]The analysis compares a single-cylinder engine against a 4-cylinder engine.

### ⚙️ Methodology
The analysis follows a 6-step computational process:
1.  **Thermodynamic Cycle Analysis:** Calculation of pressure and temperature at key points (1-4), accounting for losses, polytropic compression/expansion, and diabatic combustion with dissociation.
2.  **IMEP & Moment Calculation:** Computation of Indicated Mean Effective Pressure (IMEP) and crankshaft turning moment.
3.  **Pressure Analysis:** Evaluation of gas pressure, inertia pressure (based on reciprocating mass), and effective pressure.
4.  **Flywheel Sizing (Single Cylinder):** Calculation based on a target kinematic irregularity ($\delta = 1\%$) and dynamic irregularity constraints.
5.  **Multi-Cylinder Extension:** Expansion of the analysis to a 4-cylinder engine with a firing order of 1-3-2-4.
6.  **Speed Fluctuation:** Computation of instantaneous crankshaft speed.


---

## 📂 Report 2: Engine Test Evaluation & HRR Analysis

### 🎯 Objective
To characterize the performance of a Turbocharged CI engine using experimental testbed data and perform a detailed combustion diagnostic (HRR).

### ⚙️ Methodology
1.  **Steady State Analysis:**
    * Correction of torque and power according to **ISO 1585** standards.
    * Calculation of corrected parameters: Power ($P_0$), Torque ($T_0$), and fuel delivery parameters.
    * Evaluation of performance metrics: BSFC, Fuel Conversion Efficiency ($\eta_f$), and Volumetric Efficiency ($\lambda_v$).
    
2.  **Combustion Diagnostics (HRR):**
    * **Signal Processing:** Referencing raw in-cylinder pressure to manifold pressure and filtering signals using a **Butterworth filter**.
    * **Net Heat Release ($Q_n$):** Calculated using the first law of thermodynamics, accounting for cylinder volume changes and specific heat ratio ($\gamma$) variations.
    * **Combustion Phases:** Determination of Start of Injection (SOI), Start of Combustion (SOC), Ignition Delay (ID), and Mass Fraction Burned (MFB) percentages.

---

## 💻 Technologies & Tools

* **MATLAB:** Used for all numerical computations, signal filtering, and data visualization.
    * *Signal Filtering:* Implementation of `butter` (Butterworth) filter for in-cylinder pressure.
    * *Cycle Simulation:* Integration of pressure curves and inertia forces.
* **Excel:** Used for initial dataset storage (raw pressure signals).

