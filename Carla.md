---
layout: single
title: "RL-Based Autonomous Driving in CARLA"
permalink: /carla/
---

<a href="/portfolio/assets/files/ML_AI_Project_Course_Phase_3.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

---

## Overview

This project develops a closed-loop autonomous driving system in CARLA for highly interactive scenarios, including unprotected left turns, highway merging, and sudden cut-ins.

The core objective is to compare a classical rule-based planner with a reinforcement learning (PPO) planner, while keeping the low-level controller fixed. This isolates the impact of learning-based decision making in complex driving interactions.

---

## My Contribution

### PPO Reward Design and Tuning
- Designed and refined the PPO reward function to balance safety, efficiency, and progress  
- Tuned reward components for collision avoidance, trajectory tracking, and task completion  
- Diagnosed training issues such as idling and unstable behavior, and improved convergence through reward shaping  

### Scenario and Baseline Design
- Contributed to the design of evaluation scenarios, including left-turn, merging, and cut-in cases  
- Configured traffic parameters such as aggressiveness, density, and headway  
- Evaluated baseline Behavior Agent performance under different configurations  

### System Integration
- Integrated PPO planner into the CARLA pipeline with a fixed PID controller  
- Assisted debugging simulation setup and evaluation scripts  

---

## System Architecture

The system follows a hybrid autonomy pipeline:

- **Global Planner**: A* route planning for long-horizon navigation  
- **Local Planner**:  
  - Baseline: rule-based waypoint planner  
  - RL: PPO-based short-horizon trajectory generator  
- **Controller**: fixed PID controller for trajectory tracking  

<p align="center">
  <img src="/portfolio/assets/images/Carla/carla_arch.png" width="700">
</p>

This design isolates improvements at the planning level without modifying control behavior.

---

## Scenarios

The system is evaluated under three interactive driving scenarios:

- **Unprotected Left Turn**  
  Ego vehicle must cross oncoming traffic, requiring gap selection and yield decisions  

- **Highway Merge**  
  Ego vehicle merges into dense traffic flow, requiring coordination of speed and timing  

- **Sudden Cut-In**  
  NPC performs a TTC-triggered lane change, testing robustness under abrupt interactions  

---

## Baseline vs RL Planner

The baseline system uses a classical modular pipeline with rule-based planning, while the RL system replaces the local planner with a PPO policy that generates short-horizon trajectories.

The PPO planner:
- Outputs trajectory adjustments and target speed  
- Re-plans at every timestep  
- Is anchored to the global route  

<p align="center">
  <img src="/portfolio/assets/images/Carla/trajectory.png" width="600">
</p>

---

## Results

### Highway Merge Performance

<p align="center">
  <img src="/portfolio/assets/images/Carla/success_rate.png" width="600">
</p>

| Method | Success Rate | Crash Rate | P90 Time | P90 Jerk |
|--------|-------------|-----------|----------|----------|
| Baseline (Aggressive) | 83% | 17% | 11.6 s | 446 |
| PPO | 86% | 10% | 17.4 s | 547 |

---

## Key Insights

- RL improves success rate and reduces crash rate in interactive scenarios  
- Learning-based planners adapt better than rule-based systems under uncertainty  
- There is a trade-off between safety, efficiency, and comfort (higher jerk in PPO)  
- Hybrid architecture (A* + PPO + PID) balances stability and adaptability  

---

## Takeaway

This project demonstrates a hybrid autonomous driving system that integrates classical planning and reinforcement learning. It shows that learning-based planners can significantly improve decision-making in complex, interaction-heavy environments while maintaining overall system stability.
