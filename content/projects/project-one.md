+++
title = 'Structural Guarantees in the Approximation of Model Predictive Control Laws: A Shape-Constrained Polynomial Read-Out'
date = 2026-04-24
summary = 'Argues that what can be guaranteed about a distilled Model Predictive Control law is decided by how the learned term is embedded and what function class it is drawn from, not by the approximator, and tests this on the Johansson quadruple-tank benchmark in both minimum- and non-minimum-phase regimes. A setpoint gate makes zero offset and local exponential stability hold for any learned term; imposing negative feedback as an affine inequality inside a convex read-out suppresses a failure mode occurring on up to 11% of the operating box; and the symbolic extraction, rather than the network, dominates the approximation error. Reports the negative result that the KAN-selected monomial support is no better than orthogonal matching pursuit at a matched budget, and worse in the non-minimum-phase regime.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

Approximating a Model Predictive Control policy offline removes the online optimizer from the loop, but it also removes the guarantees that motivated using MPC in the first place. The paper's argument is that what can be recovered afterwards is decided less by which approximator is used than by two structural choices. The first is the parameterization: a learned term embedded behind a gate that vanishes quadratically at the setpoint leaves zero steady-state offset and local exponential stability to the architecture, whatever was learned. The second is the read-out class: a control law linear in its own coefficients admits convex shape constraints and an identifiability analysis, neither of which is available for a dense network of comparable accuracy. Symbolic Kolmogorov–Arnold Networks (KANs) are one route into that class, and this work asks what that route actually contributes.

The study is deliberately self-critical: it reports where the method fails as carefully as where it succeeds, and it states the boundary of its own claim — that it establishes a method validated on a benchmark which cannot by itself justify the method's use, since the LTV-MPC teacher outperforms a well-tuned gain-scheduled LQR on this plant by only 6-9%. Demonstrating that distillation pays for itself requires a plant on which optimization-based control earns a large margin, such as one with active state constraints or short sampling periods.

## My role

Single-author work; conceptualization, methodology, software, validation and formal analysis were carried out by me from start to finish.

## Approach

Existing literature was used to design the LTV-MPC teacher; the distillation, the two-step convex read-out, the certification analysis and the matched-budget baseline comparisons (against sparse polynomial regression, a multi-layer perceptron, a DeepONet and a gain-scheduled LQR) were implemented by hand. The study is entirely software-in-the-loop, and makes no measured claims about execution time on any particular processor: the computational claim is structural and established by counting operations.

## Results

- **Error decomposition.** An off-the-shelf symbolic extraction turns a 2.4% imitation error into 7.7% of the actuator range in the minimum-phase regime (4.6% into 11.2% in the non-minimum-phase one). Re-estimating the coefficients on the KAN-selected support by convex least squares recovers most of the loss. Reporting the network and symbolization errors separately, which prior work does not do, is necessary for any claim about symbolic controllers.
- **Shape constraints.** An unconstrained symbolic read-out violates the elementary negative-feedback condition on up to 11% of realizable operating points; the pathology is traced to a rank-deficient distillation design on which 18% of random seeds produce the wrong sign. Imposing the condition as an affine inequality inside the convex read-out reduces this to at most 0.6%, with no human in the loop, for 0.3-1.7 percentage points of accuracy — and at the small term budget deployed in the minimum-phase regime it improves accuracy instead.
- **Structural guarantees.** Embedding the learned term behind a gate that vanishes quadratically at the setpoint makes zero steady-state offset and local exponential stability properties of the architecture rather than of the fit: substituting random coefficients leaves the closed-loop spectral radius unchanged to 10^-10. A level fade that hands authority back to the linear core near the overflow limit is admitted by the same argument at no cost to either property, and removes the only constraint violation observed inside the training envelope.
- **Deterministic cost.** The deployed law is a fixed chain of 38-211 multiply-accumulate operations with no data-dependent control flow, so its worst-case cost equals its average cost by construction.
- **The network is not load-bearing.** At a matched arithmetic budget the KAN-selected support is no better than choosing the same number of monomials by orthogonal matching pursuit, and in the non-minimum-phase regime it is worse by up to 1.36 percentage points; a dense multi-layer perceptron imitates the teacher at least as closely as any symbolic form. What the polynomial form buys is a low arithmetic cost and a closed form that can be audited, not accuracy.
- **Robustness, and what is not guaranteed.** The law remains stable under ±20% parameter perturbation in 96.5-100% of Monte-Carlo trials, with closed-loop performance within 14.5% of the MPC and comparable to a well-tuned gain-scheduled LQR. Unlike the MPC, it carries no state-constraint guarantee: outside the training envelope it violates the level limit, as does every controller in the comparison except the MPC, which the paper quantifies rather than asserts.

## Links

- [Report / preprint](/preprints/JPC_entry.pdf)
- [Code and data](https://github.com/cl0sure6/QuadTank_KAN_and_LTV-MPC) (Apache 2.0; running the numbered stage scripts in order regenerates every number, figure and table in the paper)

## Remark

This work was originally submitted to IEEE ICCA 2026 and, upon feedback, re-routed to Engineering Applications of Artificial Intelligence. It was subsequently rewritten substantially — the scope narrowed from an embedded-deployment claim to a certification study — and the present version, having passed a major revision at the Journal of Process Control, received a minor-revision decision there; the preprint linked above is the revised manuscript prepared in response.
