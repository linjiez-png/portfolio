---
layout: single
title: "# Surface-Adaptive Robotic Foot with Acoustic Terrain Classification"
permalink: /robotic-foot/
---

<a href="/portfolio/assets/files/Bio_inspired_Robot_Final_Report.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

---

## Overview

Legged robots often suffer reduced mobility on mixed terrains because a single fixed foot cannot provide optimal traction across different surfaces. This project develops a terrain-adaptive robotic foot system that dynamically switches sole types based on terrain conditions.

The system integrates mechanical design, acoustic sensing, and machine learning to improve locomotion performance across wood, wet acrylic, and gravel surfaces.

<img src="/portfolio/assets/images/Bio/f1.png" width="700">

*Figure: Overall system setup and experimental platform.*

---

## System Design

The system consists of three major components:

### Mechanical Structure
- Chebyshev linkage-based robotic leg
- Aluminum frame with rolling chassis
- ~100 mm stride length design

### Sole Switching Mechanism
- Triangular rotating plate with 3 interchangeable soles
- Worm gear transmission for non-backdrivable locking
- Motor-driven switching with encoder feedback

### Acoustic Terrain Sensing
- Impact-based excitation mechanism using rack-and-pinion actuation
- Contact microphone for structure-borne vibration
- Signal processing + machine learning classification pipeline

<img src="/portfolio/assets/images/Bio/f2.png" width="600">

*Figure: Sole switching mechanism and mechanical design.*

---

## Control Logic

The terrain-adaptive system operates in a closed-loop manner:

1. Sense terrain through acoustic impact  
2. Classify terrain type  
3. Compare with current sole  
4. Switch sole if mismatch detected  
5. Execute walking steps  
6. Repeat  

<img src="/portfolio/assets/images/Bio/f3.png" width="650">

*Figure: Control logic for terrain-aware sole switching.*

---

## My Contribution

### Mechanical & System Integration
- Contributed to structural design of the robotic platform (frame and chassis)
- Worked on shaft dimensioning, bearing fit, and alignment
- Assisted with press-fit assembly and mechanical integration

### Acoustic Sensing & Machine Learning
- Designed impact-based terrain sensing method
- Developed event-driven signal slicing pipeline
- Extracted MFCC and spectral features
- Trained Random Forest classifier (~93% accuracy)
- Implemented filtering (confidence threshold + voting + gait gating)

### Control Integration
- Integrated classification output into control logic
- Enabled robust terrain-aware switching behavior

---

## Experimental Design

Two-stage evaluation:

### E1: Material Screening
- Tested multiple materials on each terrain
- Selected optimal materials:
  - Wood → Urethane rubber  
  - Wet acrylic → Dragon Skin  
  - Gravel → Polyurethane  

### E2: Adaptive vs Fixed Comparison
- Mixed terrains tested:
  - Wood + acrylic  
  - Wood + gravel  
  - Gravel + acrylic  

Metrics:
- Speed  
- Cycles per distance  
- Slip count  

<img src="/portfolio/assets/images/Bio/f4.png" width="650">

*Figure: Sole morphologies used for different terrains.*

---

## Results

### Locomotion Performance

The adaptive system consistently outperforms the fixed flat-sole baseline:

- Higher average speed  
- Fewer gait cycles per distance  
- Improved locomotion efficiency  

<img src="/portfolio/assets/images/Bio/f5.png" width="750">

*Figure: Performance comparison between adaptive and fixed sole systems.*

---

### Classification Performance

Overall classification accuracy: **93.22%**

| Class   | Recall |
|--------|--------|
| Wood   | 0.98   |
| Acrylic| 0.90   |
| Gravel | 1.00   |
| Sliding| 0.61   |

Limitations:
- Confusion between wood and acrylic  
- Sliding often misclassified as gravel  

---

## Key Insights

- Terrain-adaptive foot design significantly improves locomotion performance  
- Impact-based sensing provides reliable terrain classification  
- Mechanical design + ML integration is essential for real-world robotics  

---

## Future Work

- Add suspension for vertical compliance  
- Integrate sensors into the foot  
- Improve classification under sliding conditions  
- Enable onboard embedded deployment  

---

## Takeaway

This project demonstrates a complete robotic system integrating mechanical design, sensing, control, and machine learning. It highlights how intelligent perception can enhance physical system performance in real-world environments.
