+++
title = 'Robust Adaptive Kolmogorov-Arnold Neural Control'
date = 2026-07-15
summary = 'Designed a Lipschitz-continuous adaptive control architecture (LCA-RLS-KAN) whose Lyapunov certificate carries no persistent-excitation requirement — and verified that the benchmark is an unexcited regime, its feature Gram holding numerical rank seven of ten. Over a 50-seed Monte-Carlo under adversarial parameter drift the controller improves on Linear Time-Varying Model Predictive Control in aggregate tracking at roughly half the per-step cost, on a branch-free evaluation with an a priori worst-case bound, while conceding a 1.6-3.6x actuator total-variation advantage to the optimizer.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

The project addresses a gap present in existing control architectures: while Model Predictive Control represents a rigorous paradigm capable of robust and optimal control, its online optimization is computationally demanding and offers insufficient stability guarantees in the presence of model mismatch. Adaptive schemes remove the optimization, but their guarantees classically rest on persistent excitation — a condition that regulation to a fixed setpoint structurally destroys, restorable only by probing that conflicts with the control objective. The architecture I designed addresses both limitations: Recursive Least Squares with exponential forgetting adapts the linear weights of a symbolically distilled Kolmogorov-Arnold network basis, keeping the control law Lipschitz-continuous, explicit and auditable, while a Lyapunov-based analysis certifies input-to-state stability with respect to the lumped approximation-and-disturbance error and uniform ultimate boundedness of the closed-loop error state over the entire physically realizable operating envelope.

The central claim is that the certificate carries no persistent-excitation requirement: the damping that closes the Lyapunov argument comes from a covariance bound the update law enforces by projection at every step, not from excitation of the regressor, so bounded tracking survives loss of excitation. The guarantee is exercised rather than merely compatible — on the benchmark the empirical feature Gram holds numerical rank seven of ten, so excitation is measurably absent, and the closed loop remains bounded regardless.

Over a 50-seed Monte-Carlo on a high-fidelity quadruple-tank benchmark under adversarial parameter drift — run against a reachable reference and an LTV-MPC given a horizon that spans the plant's inverse response, so the baseline is not handicapped — the controller improves on LTV-MPC in aggregate tracking (168 against 181 cm·s of summed IAE) at roughly half the per-step cost (0.63 against 1.22 ms), on a branch-free evaluation whose worst-case execution time is bounded a priori. The result is reported with its cost: LTV-MPC commands the actuators markedly more smoothly, at 3.6x and 1.6x lower Total Variation on the two pumps, so on this benchmark the proposed controller buys its tracking allocation and its per-step cost at the price of a rougher command. Against a black-box RBF adaptive baseline sharing the identical adaptation harness the two are statistically indistinguishable, so the distilled symbolic basis is credited with interpretability rather than with tracking or smoothness.

## My role

The project was designed and architected by me from start to finish.  

## Approach

Existing literature was used in combination with findings from my first research project. Most of the techniques were implemented and coded by hand in the IDE; the architecture was benchmarked in Python over a 50-seed Monte-Carlo with a shared estimation harness, and the results were saved in corresponding CSV files for further parsing and presentation.

## Results

Complementing the Monte-Carlo campaign, a single-realization stress test injects a 2.0 cm step disturbance into tank 2 at t = 30 s on top of the drift schedule, with no controller re-tuned. The disturbed tank itself is the level on which LTV-MPC is clearly ahead (69.6 against 97.2 cm·s, settling closer at 0.99 against 1.66 cm); the proposed controller pays for the disturbance there and recovers it on the coupled levels. The discriminating result is tank 3, where shared pump actuation forces simultaneous disturbance rejection and level sustainment: 31% lower IAE (69.6 against 100.7 cm·s) at a smaller terminal offset.

- [Adversarial testing against LTV-MPC, Tank 2](/images/Fig1_Disturbance_RejectionTank2.pdf)
- [Adversarial testing against LTV-MPC, Tank 3](/images/Fig2_Disturbance_RejectionTank3.pdf)
- [Adversarial testing against LTV-MPC, Tank 4](/images/Fig3_Disturbance_RejectionTank4.pdf)

## Links

- [Report / preprint](/preprints/main.pdf)

## Remark

This work was originally submitted to Automatica (July 2026). It was subsequently revised and retargeted — the certificate is now stated free of any persistent-excitation requirement, and the benchmark is verified to be an unexcited regime — and the present version is under review at the International Journal of Adaptive Control and Signal Processing.
