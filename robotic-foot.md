---
layout: single
title: "Surface-Adaptive Robotic Foot"
permalink: /robotic-foot/
---

# Surface-Adaptive Robotic Foot with Acoustic Terrain Classification

<a href="/portfolio/assets/files/Bio_inspired_Robot_Final_Report.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

## Overview
Legged robots often suffer reduced mobility on mixed terrains due to non-adaptive foot designs. This project develops a terrain-adaptive robotic foot system that dynamically switches sole types based on terrain conditions.

The system integrates mechanical design, sensing, and machine learning to improve locomotion performance across wood, wet acrylic, and gravel surfaces.

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
- Impact-based excitation mechanism using rack-and-pinion actuation
- Contact microphone for structure-borne vibration
- Signal processing and machine learning classification pipeline

The control loop follows this sequence:

Sense terrain → Compare with current sole → Switch sole if needed → Execute steps → Repeat

---

## My Contribution

### Mechanical & System Integration
- Designed the structural layout of the robotic platform, including the aluminum frame and chassis layout
- Contributed to component dimensioning, including shaft length, bearing fit, alignment, and assembly tolerance
- Assisted in press-fit assembly of shafts and bearings
- Supported overall mechanical integration of the robotic leg system

### Acoustic Sensing & Machine Learning Pipeline
- Independently developed the acoustic terrain classification pipeline
- Conducted preliminary feasibility experiments using a free-fall impact setup and contact microphone
- Designed the impact-based terrain sensing mechanism
- Developed event-driven signal slicing with adaptive thresholds
- Extracted acoustic features, including MFCC and spectral features
- Trained a Random Forest classifier with 93.22% test accuracy
- Implemented filtering strategies including confidence thresholds, short-term voting, and gait-cycle-based gating

### Control Integration
- Integrated terrain classification output with the system-level control logic
- Helped refine the decision process for terrain-aware sole switching

---

## Experimental Design

The project used a two-stage evaluation.

### E1: Material Screening
- Tested multiple candidate materials on individual terrains
- Identified final material choices:
  - Wood: Urethane rubber
  - Wet acrylic: Dragon Skin
  - Gravel: Polyurethane

### E2: Adaptive vs. Fixed-Sole Comparison
- Tested three mixed-terrain conditions:
  - Wood + wet acrylic
  - Wood + gravel
  - Gravel + wet acrylic
- Compared adaptive sole switching against a fixed flat-sole baseline

Metrics:
- Average speed
- Cycles per distance
- Slip count

---

## Results

### Locomotion Performance
- The adaptive system achieved higher average speed across all mixed-terrain conditions
- The adaptive system required fewer gait cycles per distance, indicating improved gait efficiency
- The strongest evidence came from the adaptive-versus-fixed mixed-terrain experiments

### Classification Performance
- Overall sliced-dataset classification accuracy: **93.22%**
- Wood recall: **0.98**
- Gravel recall: **1.00**
- Acrylic recall: **0.90**
- Sliding recall: **0.61**

Limitations:
- Some confusion occurred between wood and acrylic
- Sliding signals were often misclassified as gravel because sliding is less transient than impact events

---

## Key Insights

- Terrain-adaptive foot design can improve locomotion speed and gait efficiency on mixed surfaces
- Impact-based acoustic sensing provides more controlled terrain information than passive vibration sensing
- Mechanical design, sensing, and machine learning must be integrated at the system level for reliable adaptive behavior

---

## Future Work

- Add a suspension mechanism for vertical compliance
- Integrate sensing directly into the robot sole
- Improve classification robustness under sliding and gravel conditions
- Extend the test rig to evaluate more terrain combinations
- Explore embedded deployment for untethered operation

---

## Takeaway

This project demonstrates a complete robotic system that integrates mechanical design, embedded control, acoustic signal processing, and machine learning. It shows how intelligent sensing can improve physical interaction with changing terrain.
