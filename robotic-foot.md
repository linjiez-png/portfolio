---
layout: single
title: "Surface-Adaptive Robotic Foot"
permalink: /portfolio/robotic-foot/
---

# Surface-Adaptive Robotic Foot with Acoustic Terrain Classification

## Overview
Legged robots often suffer reduced mobility on mixed terrains due to non-adaptive foot designs. This project develops a terrain-adaptive robotic foot system that dynamically switches sole types based on terrain conditions.

The system integrates mechanical design, sensing, and machine learning to improve locomotion performance across wood, wet acrylic, and gravel surfaces. :contentReference[oaicite:0]{index=0}

[📄 Download Full Report](assets/files/Bio_inspired_Robot_Final_Report.pdf)

---

## System Design

The system consists of three major components:

### 1. Mechanical Structure
- Chebyshev linkage-based robotic leg
- Aluminum frame with rolling chassis
- ~100 mm stride length design

### 2. Sole Switching Mechanism
- Triangular rotating plate with 3 interchangeable soles
- Worm gear transmission for non-backdrivable locking
- Motor-driven switching with encoder feedback

### 3. Acoustic Terrain Sensing
- Impact-based excitation mechanism (rack & pinion)
- Contact microphone for structure-borne vibration
- Signal processing + ML classification pipeline

👉 The *diagram on page 2* shows the full control loop:
- Sense terrain → Compare → Switch sole → Execute steps → Repeat :contentReference[oaicite:1]{index=1}

---

## My Contribution

### Mechanical & System Integration
- Designed structural layout of robotic platform (frame + chassis)
- Dimensioning and alignment of shafts and bearings
- Assisted in press-fit assembly and system integration

### Acoustic Sensing & ML Pipeline
- Designed impact-based terrain sensing approach
- Developed event-driven signal slicing pipeline
- Extracted acoustic features (MFCC + spectral features)
- Trained Random Forest classifier (~93.22% accuracy)
- Implemented filtering (confidence + voting + gait gating)

### Control Integration
- Integrated classification output into control logic
- Enabled robust terrain-aware sole switching behavior :contentReference[oaicite:2]{index=2}

---

## Experimental Design

Two-stage evaluation:

### E1: Material Screening
- Tested multiple materials per terrain
- Identified optimal materials:
  - Wood → Urethane rubber  
  - Wet acrylic → Dragon Skin  
  - Gravel → Polyurethane  

### E2: Adaptive vs Fixed Comparison
- Mixed terrains:
  - Wood + acrylic  
  - Wood + gravel  
  - Gravel + acrylic  
- Compared adaptive system vs fixed flat sole baseline

Metrics:
- Speed
- Cycles per distance
- Slip count :contentReference[oaicite:3]{index=3}

---

## Results

### Locomotion Performance
- Adaptive system achieved higher speed across all terrain combinations  
- Required fewer gait cycles per distance → improved efficiency  

👉 The *plots on page 4* show consistent improvement across all test cases :contentReference[oaicite:4]{index=4}

---

### Classification Performance
- Overall accuracy: **93.22%**
- High recall:
  - Wood: 0.98  
  - Gravel: 1.00  

Limitations:
- Confusion between wood and acrylic  
- Sliding often misclassified as gravel :contentReference[oaicite:5]{index=5}

---

## Key Insights

- Terrain-adaptive foot design significantly improves locomotion performance  
- Impact-based sensing provides more reliable signals than passive vibration  
- Combining mechanical design with data-driven sensing enables robust system behavior  

---

## Future Work

- Add suspension system for vertical compliance  
- Integrate sensors directly into foot (instead of external probe)  
- Improve classification robustness for sliding conditions  
- Enable fully untethered system with onboard computation :contentReference[oaicite:6]{index=6}

---

## Takeaway

This project demonstrates a complete robotics system integrating:
- Mechanical design  
- Embedded control  
- Signal processing  
- Machine learning  

It highlights how intelligent sensing can enhance physical system performance in real-world environments.

<a href="/portfolio/assets/files/Bio_inspired_Robot_Final_Report.pdf" target="_blank" class="btn btn--primary">View Full Report</a>
