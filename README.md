# Reliability Systems
---

Assignments for the "Reliability Systems" Course Faculty of Engineering, AUTh School of Electrical and Computer Engineering: Reliability of Railway Traffic Control Systems and  Error Rate Output for Electronic Components for HellasSat-4 Satellite

---
# 🛰️ Reliability Systems – Assignments (2024–2025)

Assignments for the **"Reliability Systems"** Course  
Faculty of Engineering, AUTh  
School of Electrical and Computer Engineering  
Department of Electronics & Computers  

📚 *Course:* Reliability Systems  
🏛️ *Faculty:* AUTh - School of Electrical and Computer Engineering  
📅 *Semester:* 9th Semester, 2024–2025  

---

## 📚 Table of Contents
- [Overview](#-overview)
- [Computational Assignment – Satellite Radiation Reliability Analysis (OMERE)](#-)
- [Bibliographical Assignment: ](#-)
- [Repository Structure](#-repository-structure)

---

## 📌 Computational Assignment – Satellite Radiation Reliability Analysis (OMERE)

### 🛰️ Mission Context: Hellas Sat-4  
The project analyzes the **Hellas Sat-4** geostationary satellite using **OMERE** software to evaluate space radiation effects on critical electronic components. Launched in 2019, the satellite operates at 35,786 km altitude, directly within the **Van Allen outer belt**, a harsh environment for COTS electronics.

---

## 🧠 Theoretical Background

### ☢️ Space Radiation Hazards
- **Total Ionizing Dose (TID):** Energy deposited over time — leads to threshold shifts and leakage.
- **Single Event Effects (SEEs):** Faults due to high-LET particles — SEU, SEL, SEFI, etc.
- **LET (Linear Energy Transfer):** Expresses energy lost per unit distance — critical in estimating fault probability.

---

## 🔬 Analysis Goals & Methodology

- Model GEO orbit from TLEs  
- Simulate radiation from trapped protons/electrons, solar events, and GCRs  
- Estimate TID and SEE impact per component  
- Analyze shielding efficiency with dose-depth curves  
- Extract expected fault rates under:
  - **Quiet Solar Conditions**
  - **Worst-Case Solar Flares**

---

## 📊 Simulation Results Summary

### 🧪 Component-Level Fault Rates (1-year mission)

| Component             | Event Type | Shielding (mm Al) | Quiet Solar | Solar Flare |
|----------------------|------------|-------------------|-------------|-------------|
| **MSP430FR5969-SP**  | SEU        | 2.5 mm            | 2.23E-06    | 3.42E-06    |
| **MSP430FR5969-SP**  | SEL        | 2.5 mm            | 0           | 0           |
| **MSP430FR5969-SP**  | SEFI       | 2.5 mm            | 0           | 0           |
| **MSP430FR5969-SP**  | DSEE       | 2.5 mm            | 2.00E-04    | 1.28E-03    |
| **MSP430FR5969-SP**  | TID        | 2.5 mm            | 22.62 krad  | —           |
| **MSP430FR5969-SP**  | DDD        | 2.5 mm            | 3.97E+08 n/cm² | —        |

| Component             | Event Type | Shielding (mm Al) | Quiet Solar | Solar Flare |
|----------------------|------------|-------------------|-------------|-------------|
| **Freescale MRAM**   | SEU        | 2.5 mm            | 4.56E-03    | 4.42E-03    |
| **Freescale MRAM**   | SEL        | 2.5 mm            | 0           | 0           |
| **Freescale MRAM**   | DSEE       | 2.5 mm            | 3.00E-04    | 3.58E-04    |

| Component             | Event Type | Shielding (mm Al) | Quiet Solar | Solar Flare |
|----------------------|------------|-------------------|-------------|-------------|
| **Atmel ATC18RHA**   | SEU (IU)   | 2.5 mm            | 5.82E+02    | 7.94E+02    |
| **Atmel ATC18RHA**   | SEU (APB)  | 2.5 mm            | 6.15E-01    | 8.39E-01    |
| **Atmel ATC18RHA**   | SEU (FPU)  | 2.5 mm            | 1.84E-01    | 2.51E-01    |

> ✅ MSP430: Strong candidate for GEO — negligible SEL/SEFI risk, low SEU rate  
> ⚠️ ATC18RHA: Highly susceptible — fault mitigation (e.g. TMR, ECC) essential  
> ⚠️ MRAM: Stable but needs margin under flaring conditions  

---

## 📘 Conclusions

- **MSP430FR5969-SP** exhibited excellent resilience — suitable for high-radiation applications.
- **Freescale MRAM** maintained robustness, though periodic reprogramming may help counter soft errors.
- **ATC18RHA** units, especially **LEON3 IU**, showed high SEU susceptibility requiring **design-level fault-tolerant techniques**.
- At 2.5 mm Aluminum shielding, **TID ≈ 22.6 krad** and **DDD ≈ 4 × 10⁸ n/cm²** were observed — acceptable for hardened devices.

---

## 📌 Bibliographical Assignment – Reliability of Train Traffic Control Systems

### 🚆 Context: Safety-Critical Railway Infrastructure  
This assignment presents a literature review on **the reliability and fault-tolerant design of train traffic control systems**, where failures may lead to **delays, economic losses, or catastrophic safety events**. These systems lie at the intersection of control engineering, embedded computing, and networked infrastructure.

---

## 🧠 Theoretical Background

### 🛤️ Core Reliability Considerations

- **Fail-safe vs. fault-tolerant design:** Ensures that failure does not propagate or compromise safety.
- **Centralized vs. Distributed Control:** CTC systems must balance throughput, complexity, and failure isolation.
- **Real-time constraints:** Delay-sensitive operations require hard deadlines for control decisions and signaling.
- **Interoperability and standardization:** Especially vital in transnational railway systems (e.g., ERTMS/CTCS).

---

## 🔬 Literature Topics & Methodologies

- **RFAD (Risk evaluation with Fuzzy Axiomatic Design):**  
  Improves prioritization of failure modes under vagueness; combined with FMEA to address multi-criteria hazard analysis.

- **Parallel Simulation & Testing for CTC systems:**  
  Allows concurrent evaluation of multiple scenarios, increasing efficiency of validation pipelines in complex rail networks.

- **Stochastic Colored Petri Nets (SCPNs):**  
  Provide probabilistic behavior modeling of systems such as ATP (Automatic Train Protection) and interlocking subsystems, incorporating timing, concurrency, and failures.

- **Finite-State Machines (FSMs) with Infrastructure Feedback:**  
  Enable real-time dynamic reconfiguration — e.g., stop command on track occupancy, rerouting on signal failure.

---

## 📊 Key Insights & Results

| Framework / Method                  | Contribution / Outcome                                                                 |
|------------------------------------|----------------------------------------------------------------------------------------|
| **RFAD + FMEA**                    | Better resolution than classic RPN in hazard prioritization under uncertain conditions |
| **Parallel Testing of CTC**        | ~50% reduction in test time; coverage improvement using parallel path execution        |
| **CPN-based Reliability Estimation** | Enabled prediction of component-specific MTTF/MTTR, identifying weak failure points     |
| **FSM & Sensor Integration**       | Enabled dynamic train speed control and rerouting in response to infrastructure states |
| **Condition Monitoring (TDM/RARC)** | Fusion of control and diagnostics to enable predictive maintenance strategies           |

> ✅ **Combining formal modeling with runtime adaptivity** is the new frontier of railway control reliability.

---

## 🚀 Future Perspectives

- Integration of **AI/ML for predictive failure diagnosis** in sensors, switches, and signal controllers.
- Use of **digital twins** to simulate and pre-test reconfiguration scenarios in real time.
- Adoption of **IEC 61508 and EN 50126/50129** standards in next-generation interoperable rail systems.
- Enhanced **cybersecurity** for CBTC/ETCS to protect against network-originated failures and tampering.

---

## 📘 Conclusions

- Reliable train control is no longer only about hardware redundancy — it’s increasingly about **smart control, formal verification, and human-aware design**.
- Methods like **RFAD**, **CPNs**, and **real-time FSMs** are essential for modeling and mitigating risks in complex traffic environments.
- By combining **static modeling (e.g., Petri nets)** with **dynamic sensing and actuation**, modern rail systems achieve not only safety but **resilience and maintainability**.

---

## 📁 Repository Structure

```
📁 Repository Structure

├── README.md                          # Project overview and technical documentation for both assignments

├── Computational Assignment/          # Reliability analysis using OMERE for the Hellas Sat-4 satellite
│   ├── Courseworks/                   
│   │   └── Omere_v4.0.pdf             # OMERE software documentation and mission setup details
│   │   └── ra0365.txt                 # Radiation environment input data from OMERE

│   ├── Reports/                       
│   │   └── Report_HellasSat4.pdf      # Final project report: fault analysis, results, and interpretation
│   │   └── Parameter_Table.txt        # Component-specific parameters used in simulation runs

│   ├── Simulations and Results/       
│   │   └── 4_Orbit/                   # TLE-based orbit modeling and GEO configuration
│   │   └── 5_Environment_Simulation/  # Radiation environment and particle flux simulations
│   │   └── 6_LET/                     # LET spectrum analysis and shielding effectiveness
│   │   └── 7_SEE/                     # SEE prediction data: SEU, SEL, SEFI rates for various components

├── Bibliographical Assignment/        # Research on the reliability of train traffic control systems
│   ├── Literature Review/             
│   │   └── trains_paper.pdf           # Final report on railway system reliability, safety, and redundancy

│   ├── Sources/                       
│   │   └── research_refs.bib          # Supporting research articles, standards, and whitepapers

│   ├── Presentation/                 
│   │   └── Trains_Presentation.pptx   # Slide deck summarizing key ideas and architecture insights

│   └── Instructions/                 
│       └── Instructions.pdf           # Official coursework instructions and submission guidelines
```

---
