---
layout: single
title: "Autonomous Fish Feeding System for High-Humidity Environments"
permalink: /fish-feeder/
---

<a href="/portfolio/assets/files/Feeding_Nemo_Report.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

---

## Overview

This project develops a **low-cost, battery-powered autonomous fish feeder** designed for high-humidity laboratory environments.

Conventional feeders fail in these settings due to:
- condensation and corrosion
- bulky size for small tanks
- high cost and maintenance requirements  

This system addresses these issues through a **compact, modular, and moisture-resistant design**, enabling reliable daily feeding for research applications involving sensitive fish species.

---

## Design Requirements

Key constraints defined by the Fish Conservation Physiology Lab:

- Operate in **near 100% humidity environments** :contentReference[oaicite:0]{index=0}  
- Fully **sanitizable and corrosion-resistant materials**  
- **Battery-powered operation (24h minimum)**  
- Compact size for **small tanks (~2 ft diameter)**  
- Support **microdiet feed sizes (920–1800 µm)**  
- Cost under **$250**  

---

## System Architecture

The system consists of three subsystems:

- **Food Storage & Screw Transport**
- **Motor & Power System**
- **Control Interface (OLED + Buttons)**  

<img src="/portfolio/assets/images/feeder_arch.png" width="700">

Food is dispensed using a **motor-driven screw mechanism**, enabling controlled mass delivery over time.

---

## Mechanical Design

- 3D-printed structural components (PETG)
- Stainless steel fasteners for corrosion resistance
- Modular housing for easy cleaning and maintenance  

Prototype specifications:

- Size: 18.2 × 11 × 18.8 cm  
- Weight: 751 g :contentReference[oaicite:1]{index=1}  

<img src="/portfolio/assets/images/feeder_prototype.png" width="650">

---

## Control System

### Power

- Two battery packs (6V each, AA-based)
- Fully off-grid operation (no external power)

### User Interface

- OLED display
- Two-button control:
  - ON/OFF + manual dispense
  - Feed amount selection (1–100 g)

---

## Testing and Evaluation

### 1. Short-Term Functional Test

- 2-minute accelerated test simulating 24-hour operation  
- System successfully distributes feed across intervals  
- Minor issue: first interval skipped (non-critical)

---

### 2. Corrosion Resistance Test

- 120 hours at 25°C, 100% humidity  
- No rust or oxidation observed on stainless steel components :contentReference[oaicite:2]{index=2}  

---

### 3. Real Environment Feeding Test

| Day | Target (g) | Dispensed (g) | Result |
|-----|-----------|--------------|--------|
| 1   | 20        | 17.4         | OK     |
| 2   | 20        | 14.5         | OK     |
| 3   | 20        | 2.5          | Error  |
| 4   | 20        | 15.5         | OK     |
| 5   | 20        | 25.0         | OK     |

Key observations:

- Moisture causes **feed clumping**
- Dispensing accuracy varies due to humidity effects
- System remains functional but requires calibration  

---

## Key Engineering Insights

- Humidity fundamentally changes material and flow behavior  
- Mechanical dispensing systems are sensitive to **moisture-induced aggregation**  
- Reliable operation requires both **mechanical design and environmental mitigation**  
- Modular design significantly improves maintainability  

---

## Limitations

- Motor torque insufficient for loads >100 g  
- Not fully airtight → moisture ingress over time  
- Bulky battery system increases size and weight  
- Limited long-term durability validation :contentReference[oaicite:3]{index=3}  

---

## Future Work

- Integrated PCB to reduce system size  
- Improved sealing and moisture isolation  
- Alternative materials or coatings for durability  
- Mobile app for remote monitoring and control  
- Long-term reliability testing under lab conditions  

---

## Takeaway

This project demonstrates a practical mechatronic system designed under real-world constraints, highlighting the interaction between **mechanical design, environmental effects, and system reliability** in autonomous hardware systems.
