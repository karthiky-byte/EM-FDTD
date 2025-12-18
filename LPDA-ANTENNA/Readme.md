
# Compact Wideband Log-Periodic Dipole Array (500 MHz - 2 GHz)

##  Project Overview
This contains the design and simulation data for a compact 8-element Log-Periodic Dipole Array (LPDA). The project aims to achieve broadband performance (4:1 bandwidth) within a strictly limited physical footprint.

**Key Design Challenge:**
Balancing a wide frequency range (500 MHz - 2 GHz) with a "sparse" element count (only 8 elements) and a short boom (≤ 600 mm).

---

##  Technical Specifications & Current Status

| Parameter | Target Specification | Current Simulation Results |
| :--- | :--- | :--- |
| **Frequency Range** | 500 MHz – 2 GHz | 500 MHz – 2 GHz |
| **Element Count** | 8 Elements | 8 Elements |
| **Boom Length** | ≤ 600 mm | 600 mm |
| **Max Gain** | ≥ 6 dBi | **8.40 dBi** (@ 0.76 GHz) |
| **Min Gain** | ≥ 6 dBi | **~4.5 dBi** (@ 0.7 GHz & 1.2 GHz) |
| **Return Loss (S11)** | < -10 dB | Violates limit in ~40% of band |
| **Radiation Pattern** | Directional & Stable | Split beam / Side lobes present |

---

##  Simulation Analysis

### 1. Return Loss (S11)
* **Observation:** The antenna shows deep resonances at specific frequencies (0.75, 1.2, 1.45 GHz) where S11 drops below -20 dB.
* **Issue:** Between these resonances, the S11 rises above the -10 dB limit (reaching -2 dB to -3 dB). This indicates the antenna is acting as a series of separate narrow-band dipoles rather than a single broadband travelling-wave structure.

### 2. Realized Gain
* **Observation:** Peak gain is strong (up to 8.4 dBi), but there are sharp "dropouts" where gain falls below 5 dBi.
* **Issue:** These drops coincide with the S11 spikes, confirming that energy is being reflected rather than radiated at those frequencies.

### 3. Radiation Pattern (3D View)
* **Frequency:** 1.25 GHz
* **Observation:** The pattern exhibits a "split main lobe" (butterfly shape) with a null in the forward direction.
* **Root Cause:** This is likely caused by **phase cancellation** due to the spacing between the active elements being too large (low $\sigma$) or the excitation of higher-order modes ($3\lambda/2$) on the rear elements.
