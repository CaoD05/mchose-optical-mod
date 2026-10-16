# 🖱️ Mchose Optical Switch Mod (A7 RE PCB)

[![Hardware](https://img.shields.io/badge/Hardware-PCB%20Mod-blue.svg)](#)
[![Status](https://img.shields.io/badge/Status-Tested%20%26%20Working-brightgreen.svg)](#)
[![Switches](https://img.shields.io/badge/Switches-TTC%20Optical%20v2-orange.svg)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An optical switch conversion and power-management mod for the **Mchose A7 (RE PCB)**, featuring automatic LED power cut-off in sleep mode to optimize battery life.

---

<p align="center">
  <img src="https://i.imgur.com/Ur4guqs.jpeg" alt="Mchose A7 Mod Preview" width="700"/>
</p>

---

## 📖 Overview

Optical mouse switches (such as **TTC Optical v2**) require infrared LEDs to detect actuations. Unlike standard mechanical switches, optical switch LEDs consume constant current if left powered. 

This circuit taps into the MCU sleep line (which drops from 1.9V to 0V upon sleep) to automatically gate power to the optical LEDs using an NPN transistor and P-channel MOSFET, conserving battery life when the mouse goes idle.

> [!TIP]
> **TL;DR Logic:**
> - **Awake:** When active, the 1.9V signal at `R5` drives the **J3Y** (NPN) base, which pulls the gate of the **A1SHB** (P-MOSFET) low, turning it ON to power the optical switch LEDs (`LED (A)`).
> - **Sleep:** When the mouse sleeps, the 1.9V signal at `R5` turns off. The **J3Y** turns off, allowing the pull-up to deactivate the **A1SHB**, completely cutting power to the LEDs to save battery.

---

## 🔌 Circuit Schematic

<p align="center">
  <img src="https://i.imgur.com/JAfFd3w.png" alt="Mchose Schematic Diagram" width="850"/>
</p>

---

## 📦 Bill of Materials (BOM)

| Designator | Component | Package / Footprint | Value / Part Number | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Q1** | P-Channel MOSFET | SOT-23 | **SI2301 (A1SHB)** | 2.3A / 20V P-MOSFET |
| **Q2** | NPN Transistor | SOT-23 | **S8050 (J3Y / MBT8050LT1G)** | 0.5A / 40V NPN |
| **R1** | SMD Resistor | 0402 | **750Ω – 1kΩ** | 750Ω or 1kΩ works (within range) |
| **R2** | SMD Resistor | 0402 | **10kΩ** | Pull resistor |
| **R3** | SMD Resistor | 0402 | **1kΩ** | Base resistor |
| **R4** | SMD Resistor | 0402 | **10kΩ** | Pull resistor |
| **R5** | SMD Resistor | 0402 | **4.75kΩ** | Sleep signal line sensing |
| **R6** | SMD Resistor | 0402 | **10kΩ** | Pull-down resistor |
| **L5** | Inductor / Ferrite Bead | 0603 | **0Ω jumper or bridge** | Solder bridge or 0603 0R resistor |

---

## 🛠️ PCB Installation & Trace Guide

### 1. Board Layout & Trace Reference
<p align="center">
  <img src="https://i.imgur.com/R4Dd6Vx.jpeg" alt="PCB Layout Overview" width="450"/>
  <img src="https://i.imgur.com/DBJXHll.jpeg" alt="Component Placement" width="450"/>
</p>

### 2. Component Soldering Details
<p align="center">
  <img src="https://i.imgur.com/vXB5xtI.jpeg" alt="Wiring and Soldering Close-up" width="450"/>
  <img src="https://i.imgur.com/RFcVmiz.jpeg" alt="L5 Inductor Bridge Detail" width="450"/>
</p>

> [!NOTE]
> **Inductor / Ferrite Bead Note (`L5`):**  
> `L` is marked for an inductor or ferrite bead. For this modification, you can simply **bridge the pads with solder** or install an **0603 0Ω** resistor.

---

## 🎥 Testing & Verification

Tested and confirmed working with **TTC Optical v2** switches on the **A7 RE PCB**.

[![Watch Test Video](https://img.shields.io/badge/Demo%20Video-Watch%20on%20Imgur-red?style=for-the-badge&logo=youtube)](https://i.imgur.com/q8pM4Rr.mp4)

> 📹 **Video Demo:** [Click here to view the video demonstration](https://i.imgur.com/q8pM4Rr.mp4)

---

## ⚠️ Disclaimer

- This modification involves soldering tiny **0402** SMD passives and **SOT-23** transistors. A fine-tip soldering iron, flux, tweezers, and magnification are recommended.
- Disconnecting the mouse battery before soldering is required to prevent accidental shorts.
- Proceed at your own risk; modifying your mouse PCB will void your factory warranty.

---

## 🤝 Credits & Acknowledgements

- Mod designed and documented by **[NeverWiNToP](https://imgur.com/user/NeverWiNToP)**.
- Original album: [I do it for you Mchose (Imgur)](https://imgur.com/a/1EWqT6a).
