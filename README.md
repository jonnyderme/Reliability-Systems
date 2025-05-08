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
-------------------------------------------------------------------------------------
| **Freescale MRAM**   | SEU        | 2.5 mm            | 4.56E-03    | 4.42E-03    |
|                      | SEL        | 2.5 mm            | 0           | 0           |
|                      | DSEE       | 2.5 mm            | 3.00E-04    | 3.58E-04    |
------------------------------------------------------------------------------------
| **Atmel ATC18RHA**   | SEU (IU)   | 2.5 mm            | 5.82E+02    | 7.94E+02    |
|                      | SEU (APB)  | 2.5 mm            | 6.15E-01    | 8.39E-01    |
|                      | SEU (FPU)  | 2.5 mm            | 1.84E-01    | 2.51E-01    |

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

## 📁 Repository Structure

