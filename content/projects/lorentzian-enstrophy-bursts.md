+++
title = 'A Lorentzian Law for the Enstrophy Bursts of Reconnecting Vortex Tubes'
date = 2026-11-12
summary = 'Direct numerical simulations of a reconnecting antiparallel pair of vortex tubes, at circulation Reynolds numbers 1500–9000, find that every enstrophy burst has the same shape in time: a smooth switch-on followed by a half-Lorentzian relaxation, (1 + τ²)⁻¹, onto a slowly decaying background. Because the arctangent saturates, the energy one burst dissipates is fixed in closed form by its height and width. A kinematic mechanism is proposed for the τ⁻² tail. Every test was registered before its data were read, and the paper keeps registered results apart from descriptive fits.'
tags = ['research', 'topic']
draft = false
# featured_image = 'images/project-one.jpg'   # optional: put the image in /static/images/
+++

## Overview

When two antiparallel vortex tubes reconnect, they annihilate part of their circulation in a thin contact sheet and recede as bridges and threads, with a sharp burst of enstrophy and dissipation. The published accounts report the burst's peak values, its time scales, the separation of the tubes and the growth of enstrophy before the peak. None of them gives the shape of the burst in time after its peak, a law for that shape across Reynolds numbers, or a relation between the enstrophy and the separation. How a burst relaxes decides what the event costs in energy and how long it overlaps with the next reconnection in a sequence.

The paper asks a narrow, measurable question — what is the shape in time of the enstrophy burst? — and finds one shape at every Reynolds number tested, in two observables. The shape has a physical consequence: a burst's dissipation is fixed in closed form by two numbers read off the curve. It does not claim that the law holds at arbitrary Reynolds number (the ladder ends at 9000), or that every burst in every flow is of this kind.

## My role

Single-author paper, and the paper's acknowledgement states how it was made: it was carried out with substantial help from a generative AI system (Claude, Anthropic). I set the direction and the hypotheses; the AI searched the literature, carried out derivations and computations, wrote and ran the simulation code, and drafted the text. Responsibility for the content is mine.

## Approach

The incompressible Navier–Stokes equations are solved in a triply periodic box with a Fourier pseudo-spectral method (two-thirds dealiasing, a low-storage third-order Runge–Kutta scheme with the viscous term treated exactly), in single precision on a single GPU. The main flow is an antiparallel pair of Lamb–Oseen tubes with a small broadband seed, run at circulation Reynolds numbers 1500, 3000, 4500, 6000 and 9000; a bent pair and Taylor–Green flow test whether the result carries over.

Every run is gated on its spectral tail, and three of the four Reynolds numbers in the ladder were run on two grids (448³ and 576³) from the same initial field: the enstrophy history and the fitted burst law are grid-converged at all four, while the peak vorticity is not converged at Re_Γ = 9000 and is used for nothing beyond a resolution estimate.

Each test was registered — hypothesis, statistic and pass rule frozen in a dated log — before its data were read, and verdicts are reported as registered, including the ones that failed or were found to be invalid by design. Fits that were never registered are labelled descriptive, and an appendix lists every test.

## Results

- **One shape.** A Friedrichs-mollified half-Lorentzian on a linear background is the best of four candidate shapes at every Reynolds number from 3000 to 9000, with residuals of 1.3–2.1% of the peak and the lowest information criterion at each (descriptive). Beyond about one width the four bursts fall on one curve, and the fitted width levels off as the Reynolds number grows.
- **The switch-on is timed by the vortex lines.** The burst begins when the vortex lines reach an isotropic orientation, tan θ = √2, after a linear rise over one width — tested on a fresh Re_Γ = 6000 run against a low-Reynolds-number control (registered, passed).
- **A second observable.** The circulation exchanged across the symmetry plane wears the same shape, peaking 2.6–2.8 time units after the enstrophy and relaxing more slowly (registered, on in-sample data; passed two of three criteria).
- **Other flows and a held-out Reynolds number.** The relaxation carries over to Taylor–Green flow and to a bent pair, where the plain Lorentzian fits best and the switch-on does not hold (both mixed verdicts). At Re_Γ = 1500, held out from all fitting, the shape survives to 2.3% of the burst's height, but the parameter relations fitted on the ladder do not carry over.
- **The cost of one burst.** Because the arctangent saturates, the energy a burst dissipates in excess of the background is (π/2)νHw, independent of the switch-on. This reproduces the simulations to within 0.4%: 10–13% of the initial kinetic energy, saturating with Reynolds number. A (1 + τ)⁻¹ tail would make that integral diverge, so the shape decides whether a burst's cost is finite.
- **A kinematic mechanism, partly supported.** At Re_Γ = 4500 the tubes recede on a hyperbola, d⁴ ∝ 1 + τ² (registered, passed), and the excess enstrophy falls close to d⁻⁴ (fitted exponent −4.4, descriptive); together these give the Lorentzian envelope. The registered prediction that enstrophy follows the square of the partner strain failed (exponent 1.25, not 2), and a registered test of how the shed debris pushes the cores apart was not supported. The paper reports the mechanism as a kinematic reduction, not a derivation.

## Links

- [Report / preprint](/preprints/POF_entry.pdf)

## Remark

Submitted to Physics of Fluids, where it is under review. The study is numerical and stops where its data stop: the hyperbolic recession was tested at one Reynolds number, the finest local scale is marginal at Re_Γ ≥ 4500, and a run near Re_Γ = 2 × 10⁴ is named as the test the law has not yet faced. It makes no claim about the regularity of the Navier–Stokes equations.
