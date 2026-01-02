
## 📖 Overview

This repository contains two distinct applied engineering reports focusing on internal combustion engine analysis. The project is divided into two main sections:
1.  [cite_start]**Flywheel Dimensioning:** Analytical dimensioning of a flywheel for single-cylinder and multi-cylinder engines based on thermodynamic cycle analysis[cite: 17].
2.  [cite_start]**Engine Test Evaluation & HRR Analysis:** Post-processing of steady-state engine test data and Heat Release Rate (HRR) analysis for a turbocharged compression ignition (CI) engine[cite: 757, 758].

---

## 📂 Report 1: Flywheel Dimensioning

### 🎯 Objective
To regularize the crankshaft speed without affecting engine torque or power by dimensioning an appropriate flywheel. [cite_start]The analysis compares a single-cylinder engine against a 4-cylinder engine[cite: 17, 18, 36].

### ⚙️ Methodology
[cite_start]The analysis follows a 6-step computational process[cite: 37]:
1.  [cite_start]**Thermodynamic Cycle Analysis:** Calculation of pressure and temperature at key points (1-4), accounting for losses, polytropic compression/expansion, and diabatic combustion with dissociation [cite: 55-60].
2.  [cite_start]**IMEP & Moment Calculation:** Computation of Indicated Mean Effective Pressure (IMEP) and crankshaft turning moment[cite: 39].
3.  [cite_start]**Pressure Analysis:** Evaluation of gas pressure, inertia pressure (based on reciprocating mass), and effective pressure[cite: 358, 369].
4.  [cite_start]**Flywheel Sizing (Single Cylinder):** Calculation based on a target kinematic irregularity ($\delta = 1\%$) and dynamic irregularity constraints[cite: 541, 542].
5.  [cite_start]**Multi-Cylinder Extension:** Expansion of the analysis to a 4-cylinder engine with a firing order of 1-3-2-4[cite: 636, 637].
6.  [cite_start]**Speed Fluctuation:** Computation of instantaneous crankshaft speed[cite: 598].

### 📊 Key Results
| Parameter | Single Cylinder | Multi-Cylinder (4) |
| :--- | :--- | :--- |
| **IMEP** | [cite_start]11.261 bar [cite: 356] | - |
| **Resistant Pressure ($p_r$)** | [cite_start]1.79 bar [cite: 510] | - |
| **Flywheel Inertia ($J_{flyw}$)** | [cite_start]0.0849 $kg\cdot m^2$ [cite: 576] | - |
| **Flywheel Diameter** | [cite_start]**257 mm** [cite: 593] | [cite_start]**256 mm** [cite: 730] |
| **Dynamic Irregularity ($\xi$)** | - | [cite_start]0.193 [cite: 719] |

---

## 📂 Report 2: Engine Test Evaluation & HRR Analysis

### 🎯 Objective
[cite_start]To characterize the performance of a Turbocharged CI engine using experimental testbed data and perform a detailed combustion diagnostic (HRR)[cite: 758, 777].

### ⚙️ Methodology
1.  **Steady State Analysis:**
    * [cite_start]Correction of torque and power according to **ISO 1585** standards[cite: 804].
    * [cite_start]Calculation of corrected parameters: Power ($P_0$), Torque ($T_0$), and fuel delivery parameters[cite: 809, 810].
    * [cite_start]Evaluation of performance metrics: BSFC, Fuel Conversion Efficiency ($\eta_f$), and Volumetric Efficiency ($\lambda_v$)[cite: 868, 891, 917].
    
2.  **Combustion Diagnostics (HRR):**
    * [cite_start]**Signal Processing:** Referencing raw in-cylinder pressure to manifold pressure and filtering signals using a **Butterworth filter**[cite: 952, 979].
    * [cite_start]**Net Heat Release ($Q_n$):** Calculated using the first law of thermodynamics, accounting for cylinder volume changes and specific heat ratio ($\gamma$) variations[cite: 1004].
    * [cite_start]**Combustion Phases:** Determination of Start of Injection (SOI), Start of Combustion (SOC), Ignition Delay (ID), and Mass Fraction Burned (MFB) percentages[cite: 998].

### 📊 Key Results
* [cite_start]**Performance Maps:** Generated maps for BSFC, $\eta_f$, and $\lambda_v$ across engine speeds (850 - 3850 rpm)[cite: 844, 932].
* **Combustion Timing:**
    * [cite_start]**SOI:** 345.1 °CA [cite: 1030]
    * [cite_start]**SOC:** 349.2 °CA [cite: 1032]
    * [cite_start]**Ignition Delay:** 4.1 °CA [cite: 1033]
* **Mass Fraction Burned (MFB):**
    * [cite_start]**MFB10:** 363.5 °CA [cite: 1058]
    * [cite_start]**MFB50:** 374.3 °CA [cite: 1058]
    * [cite_start]**MFB90:** 388.7 °CA [cite: 1058]

---

## 💻 Technologies & Tools

* **MATLAB:** Used for all numerical computations, signal filtering, and data visualization.
    * [cite_start]*Signal Filtering:* Implementation of `butter` (Butterworth) filter for in-cylinder pressure[cite: 979].
    * [cite_start]*Cycle Simulation:* Integration of pressure curves and inertia forces[cite: 650].
* [cite_start]**Excel:** Used for initial dataset storage (raw pressure signals)[cite: 951].

### Example: MATLAB Filter Implementation
```matlab
[cite_start]% Butterworth filter implementation used in Report 2 [cite: 980-989]
res = 0.1;
fs_filt = n/60*360/res; % sampling frequency
fc = 4000; % cutoff frequency [Hz]
Wn = fc/(fs_filt/2); % ratio between cutoff and Nyquist frequency
n_filt = 2; % order of the filter
[b,a] = butter(n_filt, Wn);
p_cyl_filt = filtfilt(b,a,p_cyl_ref);
