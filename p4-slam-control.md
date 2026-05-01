---
layout: single
title: "EKF-SLAM Vehicle Control in Webots"
permalink: /p4-slam-control/
---

<a href="/portfolio/assets/files/P4_Report.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

---

## Overview

This project builds a closed-loop autonomous driving system that integrates **state estimation (EKF-SLAM)** with **trajectory tracking control (LQR + PID)** under noisy sensing conditions.

The key challenge is that control depends on accurate state estimation, while real-world sensor measurements are noisy and incomplete. This project demonstrates how estimation and control must work together to achieve stable vehicle behavior.

---

## System Architecture

The system consists of three tightly coupled components:

- **State Estimation**: EKF-SLAM estimates vehicle pose (X, Y, ψ) and landmark positions  
- **Lateral Control**: LQR controller for trajectory tracking  
- **Longitudinal Control**: PID controller for speed regulation  

<img src="/portfolio/assets/images/p4_arch.png" width="700">

This pipeline forms a fully closed-loop system where estimated states are directly used for control.

---

## Estimation: EKF-SLAM

The vehicle does not have access to perfect global position. Instead, it estimates its state using:

- Motion model from vehicle kinematics  
- Noisy range and bearing measurements to landmarks  

The EKF maintains a joint state:

- Vehicle pose: (X, Y, ψ)  
- Landmark positions  

<img src="/portfolio/assets/images/p4_ekf.png" width="650">

The filter performs:

- **Prediction**: propagate state using vehicle motion  
- **Correction**: update using landmark observations  

This enables consistent localization under uncertainty.

---

## Control Design

### Lateral Control (LQR)

- State: lateral error, heading error, and their derivatives  
- Control: steering angle  
- Gain computed from linearized bicycle model  

The controller stabilizes trajectory tracking using optimal feedback.

---

### Longitudinal Control (PID)

- Tracks a target velocity  
- Combines proportional, integral, and derivative terms  
- Outputs longitudinal force command  

---

## Simulation Setup

- Platform: Webots  
- Sensors:
  - GPS (position)  
  - Gyro (angular velocity)  
  - Compass (heading)  
- Landmark grid used for SLAM updates  
- Reference trajectory: predefined path with varying curvature  

---

## Results

### Trajectory Tracking

<img src="/portfolio/assets/images/p4_traj.png" width="700">

- Using raw measurements leads to drift and unstable tracking  
- EKF-SLAM significantly improves state estimation  
- The vehicle is able to follow the reference trajectory reliably  

---

### Estimation Accuracy

<img src="/portfolio/assets/images/p4_error.png" width="650">

- EKF reduces noise in position and heading estimates  
- Errors converge after initial transient  
- Stable estimation enables consistent control performance  

---

## Key Insights

- Control performance is highly sensitive to state estimation quality  
- EKF-SLAM enables reliable tracking under noisy sensing  
- Estimation and control must be designed jointly, not independently  
- Simple controllers (LQR + PID) perform well when state estimates are accurate  

---

## Limitations

- Linearized model limits performance at high curvature  
- EKF assumes Gaussian noise and known landmark association  
- Simulation uses idealized sensing compared to real-world conditions  

---

## Future Work

- Replace EKF with nonlinear filters (UKF or particle filter)  
- Integrate perception-based landmark detection  
- Extend to dynamic environments with moving obstacles  
- Combine with learning-based planning methods  

---

## Takeaway

This project demonstrates a complete perception–control pipeline, showing how state estimation and control must work together to achieve stable autonomous driving under uncertainty.
