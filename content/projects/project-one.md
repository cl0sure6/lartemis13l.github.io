+++
title = 'Symbolic Kolmogorov-Arnold Networks as a Constant-Time Alternative to Linear Time-Varying Model Predictive Control for Embedded Control of Non-Minimum Phase Systems'
date = 2026-04-24
summary = 'Model Predictive Control (MPC) is the gold standard for constrained multi-variable control, yet its computational burden often precludes deployment on low-cost embedded hardware. As a primary contribution to artificial intelligence, this work proposes distilling complex control policies into a symbolic Kolmogorov-Arnold network (KAN), creating a computationally efficient, explicit neural controller.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

The project addresses a gap present in existing control architectures: while Model Predictive Control represents a rigorous paradigm capable of robust and optimal control, it is also computationally demanding. The paper proposes a symbolic distillation of the MPC control law into a lightweight polynomial via Kolmogorov-Arnold Networks (KANs), reducing inference latency by up to 5 orders of magnitude — from 19 ms with stochastic jitter down to 1 µs of constant-time execution — alongside an order-of-magnitude reduction in memory footprint. The extracted symbolic law also permits a systematic Jacobian evaluation to formally rule out unsafe positive feedback topologies prior to deployment in C.

## My role

The project was designed and architected by me from start to finish.  

## Approach

Existing literature was used to design the MPC control law. The distillation was performed by me, providing a basis for future research; the distilled controller was validated through hardware-in-the-loop experiments on an STM32H7 microcontroller against structural boundary handovers, unmodeled actuator degradation, and previously unseen reference trajectories. 

## Results

- [Latency](/images/Fig3_Latency.pdf)

## Links

- [Report / preprint](/preprints/EAAI_entry.pdf)

## Remark

Even though this project is minted with a later date, it had been finished earlier and had been originally sent to IEEE ICCA 2026. Upon feedback, it was instead re-routed to Engineering Applications of Artificial Intelligence and is currently under review there.
