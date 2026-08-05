+++
title = 'Certifiable Approximation of Model Predictive Control Laws: A Shape-Constrained Polynomial Read-Out'
date = 2026-04-24
summary = 'Asks what a symbolic Kolmogorov-Arnold read-out actually contributes to the distillation of a Model Predictive Control law, on the Johansson quadruple-tank benchmark in both minimum- and non-minimum-phase regimes. Establishes that the symbolic extraction, rather than the network, dominates the approximation error; that imposing negative feedback as an affine inequality inside a convex read-out removes a failure mode occurring on up to 31% of the operating box by construction; and reports the negative result that the KAN-selected monomial support is statistically indistinguishable from orthogonal matching pursuit.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

Approximating a Model Predictive Control policy offline removes the online optimizer from the loop, but it also removes the guarantees that motivated using MPC in the first place. The paper's argument is that what can be recovered analytically depends less on how well the approximant fits than on the class it belongs to: a control law that is polynomial in the measured state and linear in its own coefficients admits an analytic closed-loop Jacobian, convex shape constraints and an identifiability analysis, none of which is available for a dense network of comparable accuracy. Symbolic Kolmogorov-Arnold Networks (KANs) are one route into that class, and this work asks what that route actually presents.

The study is deliberately self-critical: it reports where the method fails as carefully as where it succeeds, and it states the boundary of its own claim — that it establishes a method validated on a benchmark which cannot by itself justify the method's use, since the LTV-MPC teacher outperforms a well-tuned gain-scheduled LQR on this plant by only 7-9%. Demonstrating that distillation pays for itself requires a plant on which optimization-based control earns a large margin, such as one with active state constraints or short sampling periods.

## My role

Single-author work; conceptualization, methodology, software, validation and formal analysis were carried out by me from start to finish.

## Approach

Existing literature was used to design the LTV-MPC teacher; the distillation, the two-step convex read-out, the certification analysis and the matched-budget baseline comparisons (against sparse polynomial regression, a multi-layer perceptron, a DeepONet and a gain-scheduled LQR) were implemented by hand. The study is entirely software-in-the-loop, and makes no measured claims about execution time on any particular processor: the computational claim is structural and established by counting operations.

## Results

- **Error decomposition.** An off-the-shelf symbolic extraction turns a 2.4% imitation error into 7.8% of the actuator range in the minimum-phase regime (4.4% into 11.0% in the non-minimum-phase one). Re-estimating the coefficients on the KAN-selected support by convex least squares recovers most of the loss. Reporting the network and symbolization errors separately, which prior work does not do, is necessary for any claim about symbolic controllers.
- **Shape constraints.** An unconstrained symbolic read-out violates the elementary negative-feedback condition on up to 31% of the operating box; the pathology is traced to a rank-deficient distillation design on which 18% of random seeds produce the wrong sign. Imposing the condition as an affine inequality inside the convex read-out eliminates it for at most 0.2 percentage points of accuracy, with no human in the loop.
- **Structural guarantees.** Embedding the learned term behind a gate that vanishes quadratically at the setpoint makes zero steady-state offset and local exponential stability properties of the architecture rather than of the fit: substituting random coefficients leaves the closed-loop spectral radius unchanged to 10^-10.
- **Deterministic cost.** The deployed law is a fixed chain of 30-203 multiply-accumulate operations with no data-dependent control flow, so its worst-case cost equals its average cost by construction.
- **Robustness, and what is not guaranteed.** The law remains stable under ±20% parameter perturbation in 97-100% of Monte-Carlo trials, with closed-loop performance within 16% of the MPC. Unlike the MPC, it carries no state-constraint guarantee, which the paper quantifies rather than asserts.

## Links

- [Report / preprint](/preprints/JPC_entry.pdf)
- [Code and data](https://github.com/cl0sure6/QuadTank_KAN_and_LTV-MPC) (Apache 2.0; running the numbered stage scripts in order regenerates every number, figure and table in the paper)

## Remark

This work was originally submitted to IEEE ICCA 2026 and, upon feedback, re-routed to Engineering Applications of Artificial Intelligence. It was subsequently rewritten substantially — the scope narrowed from an embedded-deployment claim to a certification study — and the present version is under review at the Journal of Process Control.
