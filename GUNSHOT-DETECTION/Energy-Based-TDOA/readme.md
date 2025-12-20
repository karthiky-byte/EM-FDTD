
# Distributed Acoustic Event Detection & TDOA Localization (Energy-Based)

This project implements a **distributed acoustic sensing and localization system** using multiple simulated MCU nodes and a centralized MATLAB server.  
The system detects high-energy acoustic events (e.g., gunshot-like impulses) and estimates the source location using **Time Difference of Arrival (TDOA)**.

The complete pipeline—from sensor node packet generation to central server localization—is simulated in **MATLAB and Simulink**, making the project suitable for academic validation without physical hardware.

---

## 🧠 Core Components

### 1. MCU Node Simulation (`MCU_NODE_fn_snip.txt`)

Each MCU node simulates:

- Acoustic signal acquisition
- Energy-based event detection
- Local timestamp generation
- Node ID assignment

Each node acts independently, mimicking spatially separated sensors.

---

### 2. Packet Assembly (`PacketAssembler.txt`)

Detected events are packed into structured packets containing:

- Node ID
- Detection timestamp
- Energy metric
- Sequence / validity flags

These packets represent what a real embedded system would transmit wirelessly.

---

### 3. Central Server Processing (`Central_Server_fn.txt`)

The central server:

- Receives packets from all MCU nodes
- Aligns timestamps
- Computes **Δt (time differences)**
- Rejects invalid / low-energy detections
- Performs TDOA-based localization

This logic mirrors a real backend or edge server.

---

### 4. MATLAB Simulation Driver (`model.m`)

This script:

- Initializes parameters
- Simulates acoustic propagation delays
- Calls MCU node functions
- Collects packets
- Invokes central server logic
- Prepares variables required by Simulink

✅ **This file must be run before opening Simulink**

---

### 5. Simulink Model (`tdoa_sim_energy.slx`)

The Simulink model provides:

- Energy-based detection visualization
- Timestamp alignment
- TDOA block implementation
- 2D position estimation
- Real-time signal flow observation

This model demonstrates the **end-to-end signal processing chain**.

---

## 🚀 How to Run the Project

### Prerequisites

- MATLAB R2023a or later (Recommended)
- Simulink
- DSP System Toolbox

---
---

## CRITICAL: Read Before Running 

**Do not run the Simulink model directly before running the required MATLAB scripts.**

The Simulink model depends on:
- Predefined workspace variables
- Packet structures
- Function handles used by MATLAB Function blocks

If these are not initialized, the model will throw errors or fail to run.

---


