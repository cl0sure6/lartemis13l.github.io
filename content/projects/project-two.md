+++
title = 'Robust Adaptive Kolmogorov-Arnold Neural Control'
date = 2026-04-16
summary = 'Designed an adaptive control architecture achieving a significant speedup and reduction of upwards of 1.5x in actuator Total Variation compared to Linear Time-Varying Model Predictive Control. Features rigorous experimental validation and proof of Lyapunov stability by ISS/GUUB and LaSalle-Yoshizawa Theorem.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

The project addresses a gap present in existing control architectures: while Model Predictive Control represents a rigorous paradigm capable of robust and optimal control, it is also computationally demanding and produces a control law that is only piecewise continuous (Bemporad, 2003). The architecture I designed addresses both limitations: by designing the control law to be Lipschitz, that is differentiable a.e. (Rademacher's Theorem), I managed to reduce the Total Variation of Input by upwards of 1.5x; additionally, the architecture only performs linear matrix operations (Recursive Least Squares with a forgetting factor), which provided me with a runtime considerably reduced compared to the competing controllers. 

## My role

The project was designed and architected by me from start to finish.  

## Approach

Existing literature was used in combination with findings from my first research project. Most of the techniques were implemented and coded by hand in the IDE; the techniques featured has been simulated in Python and saved in corresponding CSV files for further parsing and presentation.

## Results

- [Adversarial testing against LTV-MPC, Tank 2](/images/Fig1_Disturbance_RejectionTank2.pdf)
- [Adversarial testing against LTV-MPC, Tank 3](/images/Fig2_Disturbance_RejectionTank3.pdf)
- [Adversarial testing against LTV-MPC, Tank 4](/images/Fig3_Disturbance_RejectionTank4.pdf)

## Links

- [Report / preprint](/preprints/main.pdf)
