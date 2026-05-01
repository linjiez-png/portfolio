---
layout: single
title: "RL-Based Autonomous Driving in CARLA"
permalink: /carla/
---

<a href="/portfolio/assets/files/ML_AI_Project_Course_Phase_3.pdf" target="_blank" class="btn btn--primary">View Full Report</a>

---

## Overview

This project develops a closed-loop simulation framework in CARLA to study autonomous driving in highly interactive scenarios, including unprotected left turns, highway merging, and sudden cut-ins.

We compare a classical rule-based planning pipeline with a reinforcement learning (PPO) planner that generates short-horizon trajectories while keeping the low-level PID controller fixed. :contentReference[oaicite:0]{index=0}

---

## System Architecture

The system follows a hybrid autonomy pipeline:

- Global Planner: A* route planning for long-horizon navigation  
- Local Planner:  
  - Baseline: rule-based waypoint planner  
  - RL: PPO-based short-horizon trajectory generator  
- Controller: fixed PID controller for tracking  

<img src="/portfolio/assets/images/Carla/carla_arch.png" width="700">

This design isolates improvements at the planning level without modifying control behavior.

---

## Scenarios

### Unprotected Left Turn
- Ego must cross oncoming traffic  
- Requires gap selection and commit-or-yield decision  

### Highway Merge
- Ego merges into dense traffic flow  
- Requires coordination of speed and timing  

### Sudden Cut-In
- NPC performs TTC-triggered lane change  
- Tests robustness under abrupt interaction  

---

## Baseline System

The baseline uses a classical modular pipeline:

- A* global routing  
- Rule-based local planning  
- PID tracking  

Two behavior modes were tested:

| Parameter | Normal | Aggressive |
|----------|--------|-----------|
| Max Speed | 50 km/h | 70 km/h |
| Safety Distance | 10 m | 8 m |
| Braking Distance | 5 m | 4 m |

Aggressive mode reduces safety margins and delays braking, leading to riskier behavior.

---

## Key Baseline Findings

- Success rate ranges from 73% to 86% across scenarios  
- Left-turn scenarios are more difficult than highway merging  
- Performance is sensitive to traffic aggressiveness  

A key observation from the cut-in experiment:

- At 70 km/h: safe behavior  
- At 90 km/h: collision  

This indicates that reactive PID-based control fails under high closing speeds.

---

## PPO Planner

We replace the rule-based local planner with a PPO policy:

- Generates short-horizon trajectories and target speed  
- Anchored to a global route  
- Re-plans at every timestep  

### Trajectory Representation

<img src="/portfolio/assets/images/Carla/trajectory.png" width="600">

The policy outputs lateral offsets and a reconnection bias, which are converted into smooth trajectories using spline interpolation. This formulation focuses learning on planning rather than low-level control.

---

## Results

### Highway Merge Performance

<img src="/portfolio/assets/images/Carla/success_rate.png" width="600">

| Method | Success Rate | Crash Rate | P90 Time | P90 Jerk |
|-------|-------------|-----------|----------|---------|
| Baseline (Aggressive) | 83% | 17% | 11.6 s | 446 |
| PPO | 86% | 10% | 17.4 s | 547 |

---

## Interpretation

- PPO improves success rate and reduces crash rate  
- PPO introduces higher jerk, indicating more aggressive corrections  
- There is a clear trade-off between safety, efficiency, and comfort  

---

## Key Insights

- Rule-based planners struggle in highly interactive scenarios due to reactive logic  
- RL improves adaptability but requires structured design  
- Hybrid planning (A* + PPO) provides both stability and flexibility  
- Short-horizon trajectory learning is effective for interaction-heavy driving  

---

## Limitations

- PPO still produces high jerk in challenging scenarios  
- Limited generalization across different tasks  
- Uses simulator ground-truth state instead of perception inputs  

---

## Future Work

- Introduce sensor noise for robustness testing  
- Extend PPO to left-turn and cut-in scenarios  
- Improve smoothness and merge timing  
- Transition toward perception-based inputs  

---

## Takeaway

This project demonstrates a hybrid autonomous driving system combining classical planning and reinforcement learning. It shows how learning-based planners can improve decision-making in complex interactive scenarios while maintaining system stability.
