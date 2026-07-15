+++
title = 'Robust Adaptive Kolmogorov-Arnold Neural Control'
date = 2026-07-15
summary = 'Designed a Lipschitz-continuous adaptive control architecture (LCA-RLS-KAN) that matches Linear Time-Varying Model Predictive Control on aggregate tracking while holding the cross-coupled non-minimum phase tank approximately 23% closer to setpoint, with the lowest actuator Total Variation of all benchmarked controllers. Features a 50-seed Monte-Carlo validation and a Lyapunov-based proof of ISS/GUUB stability, robust to the lack of persistent excitation.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

The project addresses a gap present in existing control architectures: while Model Predictive Control represents a rigorous paradigm capable of robust and optimal control, its online optimization is computationally demanding and offers insufficient stability guarantees in the presence of model mismatch. The architecture I designed addresses both limitations: Recursive Least Squares with exponential forgetting adapts the linear weights of a symbolically distilled Kolmogorov-Arnold network basis, keeping the control law Lipschitz-continuous, explicit and auditable, while a Lyapunov-based analysis proves input-to-state stability with respect to the lumped approximation-and-disturbance error and global uniform ultimate boundedness of the closed-loop error state — including robustness under lack of persistent excitation.

Over a 50-seed Monte-Carlo on a high-fidelity quadruple-tank benchmark under adversarial parameter drift, the controller matches the aggregate tracking of LTV-MPC (warm- and cold-restarted) and an RBF adaptive baseline while holding the cross-coupled, non-minimum phase tank approximately 23% closer to setpoint than LTV-MPC. It also produces the smoothest actuator command of all four controllers (a prediction-horizon LTV-MPC chatters at 1.6-3.4x the Total Variation of the KAN) and attains the lowest median per-step cost (1.20 ms) at a branch-free, worst-case-bounded evaluation — an architecture particularly suited to resource-constrained real-time embedded platforms.

## My role

The project was designed and architected by me from start to finish.  

## Approach

Existing literature was used in combination with findings from my first research project. Most of the techniques were implemented and coded by hand in the IDE; the architecture was benchmarked in Python over a 50-seed Monte-Carlo with a shared estimation harness, and the results were saved in corresponding CSV files for further parsing and presentation.

## Results

- [Adversarial testing against LTV-MPC, Tank 2](/images/Fig1_Disturbance_RejectionTank2.pdf)
- [Adversarial testing against LTV-MPC, Tank 3](/images/Fig2_Disturbance_RejectionTank3.pdf)
- [Adversarial testing against LTV-MPC, Tank 4](/images/Fig3_Disturbance_RejectionTank4.pdf)

## Links

- [Report / preprint](/preprints/main.pdf)

## Remark

The paper has been submitted to Automatica (July 2026).
